---
title: sp_add_notification (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_add_notification_TSQL
- sp_add_notification
dev_langs: TSQL
helpviewer_keywords: sp_add_notification
ms.assetid: 0525e0a2-ed0b-4e69-8a4c-a9e3e3622fbd
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c5bd95d4aee45046410211e77213fe4dcbc43fc3
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="spaddnotification-transact-sql"></a>sp_add_notification (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Définit une notification pour une alerte.  
  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_add_notification [ @alert_name = ] 'alert' ,   
    [ @operator_name = ] 'operator' ,   
    [ @notification_method = ] notification_method  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@alert_name=** ] **'***alerte***'**  
 Alerte pour cette notification. *alerte* est **sysname**, sans valeur par défaut.  
  
 [  **@operator_name=** ] **'***opérateur***'**  
 Opérateur à prévenir lorsque l'alerte se déclenche. *opérateur* est **sysname**, sans valeur par défaut.  
  
 [  **@notification_method=** ] *méthode_de_notification*  
 Méthode utilisée pour avertir l'opérateur. *méthode_de_notification* est **tinyint**, sans valeur par défaut. *méthode_de_notification* peut être une ou plusieurs des valeurs suivantes associées à un **OR** opérateur logique.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**1**|E-mail|  
|**2**|Récepteur de radiomessagerie|  
|**4**|**net send**|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucune  
  
## <a name="remarks"></a>Notes  
 **sp_add_notification** doit être exécuté à partir de la **msdb** base de données.  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] est un outil simple, basé sur une interface graphique, qui permet de gérer le système d'alertes dans sa totalité. L’utilisation de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] est recommandée pour configurer l’infrastructure d’alertes.  
  
 Pour envoyer une notification en réponse à une alerte, vous devez d'abord configurer l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour l'envoi de messages électroniques.  
  
 En cas d’échec au moment de l’envoi d’un message par e-mail ou d’une notification par radiomessagerie, l’échec est consigné dans le journal des erreurs du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** du rôle serveur fixe peuvent exécuter **sp_add_notification**.  
  
## <a name="examples"></a>Exemples  
 Cet exemple ajoute une notification envoyée par courrier électronique pour l'alerte spécifiée (`Test Alert`).  
  
> **Remarque :** cet exemple suppose que `Test Alert` existe déjà et que `François Ajenstat` est un nom d’opérateur valide.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_notification  
 @alert_name = N'Test Alert',  
 @operator_name = N'François Ajenstat',  
 @notification_method = 1 ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_delete_notification &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-delete-notification-transact-sql.md)   
 [sp_help_notification &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-help-notification-transact-sql.md)   
 [sp_update_notification &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-update-notification-transact-sql.md)   
 [sp_add_operator &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-add-operator-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  