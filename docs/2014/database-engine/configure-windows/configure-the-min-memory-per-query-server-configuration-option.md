---
title: Configurer l’option de configuration de serveur min memory per query | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- memory [SQL Server], queries
- minimum query memory
- queries [SQL Server], memory
- min memory per query option
ms.assetid: ecd3fb79-b4a6-432f-9ef5-530e0d42d5a6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4d215a40cce00c3cb5d1ea8293506961520fa1f7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48072439"
---
# <a name="configure-the-min-memory-per-query-server-configuration-option"></a>Configurer l'option de configuration de serveur min memory per query
  Cette rubrique explique comment configurer le `min memory per query` option de configuration de serveur dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou [!INCLUDE[tsql](../../includes/tsql-md.md)]. Le `min memory per query` option spécifie la quantité minimale de mémoire (en kilo-octets) allouée pour l’exécution d’une requête. Par exemple, si `min memory per query` est définie à 2 048 Ko, la requête est assurée pour obtenir au moins cette quantité de mémoire. La valeur par défaut est 1 024 Ko. La valeur minimale est de 512 Ko et la valeur maximale de 2 147 483 647 Ko (2 Go).  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Recommandations](#Recommendations)  
  
     [Sécurité](#Security)  
  
-   **Pour configurer l'option min memory per query, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Suivi :**  [Après avoir configuré l'option min memory per query](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Le paramètre de l’option Mémoire minimum par requête prévaut par rapport à celui de l’option [index create memory](configure-the-index-create-memory-server-configuration-option.md). Si vous modifiez ces deux options et que le paramètre index create memory est inférieur au paramètre min memory per query, un message d’avertissement s’affiche, mais la valeur définie est acceptée. Vous obtenez un avertissement similaire lors de l'exécution de requêtes.  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   Cette option avancée ne doit être modifiée que par un administrateur de base de données qualifié ou un technicien agréé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Le processeur de requêtes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tente de déterminer la quantité de mémoire optimale à allouer à une requête. L'option min memory per query permet à l'administrateur de spécifier la quantité minimale de mémoire que reçoit n'importe quelle requête. Les requêtes reçoivent généralement une quantité de mémoire supérieure si elles doivent effectuer des opérations de hachage et de tri sur un volume de données important. L'attribution d'une valeur supérieure à min memory per query peut améliorer les performances pour certaines requêtes de taille petite à moyenne, mais cela risque de donner lieu à une concurrence accrue pour les ressources mémoire. L’option min memory per query inclut la mémoire allouée au tri.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Les autorisations d’exécution de **sp_configure** , sans paramètre ou avec le premier paramètre uniquement, sont accordées par défaut à tous les utilisateurs. Pour exécuter **sp_configure** avec les deux paramètres afin de modifier une option de configuration ou d’exécuter l’instruction RECONFIGURE, un utilisateur doit disposer de l’autorisation de niveau serveur ALTER SETTINGS. L'autorisation ALTER SETTINGS est implicitement détenue par les rôles serveur fixes **sysadmin** et **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-configure-the-min-memory-per-query-option"></a>Pour configurer l'option min memory per query  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur un serveur et sélectionnez **Propriétés**.  
  
2.  Cliquez sur le nœud **Mémoire** .  
  
3.  Dans la zone **Mémoire minimum par requête** , entrez la quantité minimale de mémoire (en kilo-octets) allouée pour l’exécution d’une requête.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-configure-the-min-memory-per-query-option"></a>Pour configurer l'option min memory per query  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple montre comment utiliser [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) pour attribuer à l’option `min memory per query` la valeur `3500` Ko.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'min memory per query', 3500 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
##  <a name="FollowUp"></a> Suivi : Après avoir configuré l'option min memory per query  
 Le paramètre prend effet immédiatement sans redémarrage du serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [Configurer l’option de configuration Création d’index en mémoire.](configure-the-index-create-memory-server-configuration-option.md)  
  
  
