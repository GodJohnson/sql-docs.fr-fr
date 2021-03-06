---
title: Déclencheurs de connexion | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- logon triggers
- login triggers
helpviewer_keywords:
- triggers [SQL Server], logon
ms.assetid: 2f0ebb2f-de10-482d-9806-1a5de5b312b8
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 867c341443b7ce1c459806eaac5427a06a8bbebe
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48075989"
---
# <a name="logon-triggers"></a>Déclencheurs de connexion
  Les déclencheurs de connexion lancent des procédures stockées en réponse à un événement LOGON. Cet événement est déclenché lorsqu'une session utilisateur est établie avec une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les déclencheurs de connexion sont activés au terme de la phase d'authentification de connexion mais avant l'établissement de la session utilisateur. Par conséquent, tous les messages provenant du corps du déclencheur et habituellement destinés à l'utilisateur, (les messages et les messages d'erreur de l'instruction PRINT, par exemple), sont dirigés vers le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Les déclencheurs de connexion ne sont pas activés si l'authentification échoue.  
  
 Vous pouvez faire appel aux déclencheurs de connexion pour auditer et contrôler les sessions de serveur en effectuant, par exemple, le suivi de l'activité de connexion, en restreignant les connexions à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ou en limitant le nombre des sessions pour une connexion spécifique. Par exemple, dans le code suivant, le déclencheur de connexion refuse une tentative de connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] initiée par la connexion *login_test* si trois sessions utilisateur ont déjà été créées par cette connexion.  
  
 [!code-sql[TriggerDDL#LogonTrigger1](../../snippets/tsql/SQL14/tsql/triggerddl/transact-sql/snippet_create_alter_drop_trigger.sql#logontrigger1)]  
  
 Notez que l’événement LOGON correspond à l’événement de trace SQL AUDIT_LOGIN qui peut être utilisé dans [Notifications d’événements](../service-broker/event-notifications.md). La différence principale entre les déclencheurs et les notifications d'événement est que le lancement des déclencheurs est synchronisé avec celui des événements alors que les notifications d'événement sont asynchrones. Cela signifie, entre autre, que si vous souhaitez arrêter l'établissement d'une session, vous devez faire appel à un déclencheur de connexion. Une notification d'événement sur un événement AUDIT_LOGIN ne peut pas être utilisée à cette fin.  
  
## <a name="specifying-first-and-last-trigger"></a>Spécification du premier et du dernier déclencheurs  
 Il est possible de définir plusieurs déclencheurs sur l'événement LOGON. Ces déclencheurs peuvent être désignés comme le premier ou dernier déclencheur à être activé sur un événement à l’aide de la procédure stockée système [sp_settriggerorder](/sql/relational-databases/system-stored-procedures/sp-settriggerorder-transact-sql) . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne garantit pas l’ordre d’exécution des déclencheurs restants.  
  
## <a name="managing-transactions"></a>Gestion des transactions  
 Avant que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'exécute un déclencheur de connexion, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] crée une transaction implicite qui est indépendante d'une transaction utilisateur. Par conséquent, à l'exécution du premier déclencheur de connexion, le nombre de transactions est 1. Après l'exécution de tous les déclencheurs de connexion, la transaction est validée. En ce qui concerne les autres types de déclencheurs, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne une erreur si l'exécution d'un déclencheur de connexion se termine avec un nombre de transactions de 0. L'instruction ROLLBACK TRANSACTION rétablit le nombre de transactions à 0, même si l'instruction est émise au sein d'une transaction imbriquée. L'instruction COMMIT TRANSACTION peut décrémenter le nombre de transactions jusqu'à 0. Par conséquent, il est déconseillé d'émettre des instructions COMMIT TRANSACTION au sein de déclencheurs de connexion.  
  
 Tenez compte des points suivants lorsque vous utilisez une instruction ROLLBACK TRANSACTION au sein de déclencheurs de connexion :  
  
-   Les modifications de données effectuées jusqu'au point de l'instruction ROLLBACK TRANSACTION sont restaurées. Ces modifications incluent les modifications effectuées par le déclencheur actif et celles effectuées par les déclencheurs précédents qui se sont exécutés sur le même événement. Les déclencheurs restants pour l'événement spécifique ne sont pas exécutés.  
  
-   Le déclencheur actif continue d'exécuter les instructions restantes qui suivent l'instruction ROLLBACK. Si l'une de ces instructions modifie les données, les modifications ne sont pas annulées.  
  
 Une session utilisateur n'est pas établie si une des conditions suivantes se produit au cours de l'exécution d'un déclencheur sur un événement LOGON :  
  
-   La transaction implicite d'origine est restaurée ou échoue.  
  
-   Une erreur dont la gravité est supérieure à 20 est levée dans le corps du déclencheur.  
  
## <a name="disabling-a-logon-trigger"></a>Désactivation d'un déclencheur de connexion  
 Un déclencheur de connexion peut empêcher les connexions au [!INCLUDE[ssDE](../../../includes/ssde-md.md)] pour tous les utilisateurs, notamment les membres du rôle serveur fixe `sysadmin`. Lorsqu'un déclencheur de connexion empêche les connexions, les membres du rôle serveur fixe `sysadmin` peuvent se connecter à l'aide de la connexion administrateur dédiée, ou en démarrant le [!INCLUDE[ssDE](../../../includes/ssde-md.md)] en mode de configuration minimale (-f). Pour plus d’informations, consultez [Options de démarrage du service moteur de base de données](../../database-engine/configure-windows/database-engine-service-startup-options.md).  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Tâche|Rubrique|  
|----------|-----------|  
|Décrit comment créer des déclencheurs de connexion. Ces déclencheurs peuvent être créés à partir de n’importe quelle base de données, mais sont inscrits au niveau du serveur et résident dans la base de données **MASTER** .|[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql)|  
|Décrit comment modifier des déclencheurs de connexion.|[ALTER TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql)|  
|Décrit comment supprimer des déclencheurs de connexion.|[DROP TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql)|  
|Décrit comment retourner des informations sur les déclencheurs de connexion.|[sys.server_triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql)<br /><br /> [sys.server_trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql)|  
|Décrit comment capturer les données d'événement de déclencheur de connexion.||  
  
## <a name="see-also"></a>Voir aussi  
 [Déclencheurs DDL](../triggers/ddl-triggers.md)  
  
  
