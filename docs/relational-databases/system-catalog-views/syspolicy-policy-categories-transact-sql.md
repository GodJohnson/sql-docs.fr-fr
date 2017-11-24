---
title: syspolicy_policy_categories (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- syspolicy_policy_categories
- syspolicy_policy_categories_TSQL
dev_langs: TSQL
helpviewer_keywords: syspolicy_policy_groups view
ms.assetid: 65f080c7-771f-4cf6-a7a0-88882c637f8d
caps.latest.revision: "15"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7f75d3b95c0c37fa9acf2a550651f34308d0e782
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="syspolicypolicycategories-transact-sql"></a>syspolicy_policy_categories (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Affiche une ligne pour chaque catégorie de la stratégie de la Gestion basée sur des stratégies dans l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les catégories de stratégies vous aident à organiser des stratégies lorsque vous disposez de nombreuses stratégies. Le tableau suivant décrit les colonnes dans la vue syspolicy_policy_groups.  
 
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|policy_category_id|**int**|Identificateur de la catégorie de stratégie.|  
|name|**sysname**|Nom de la catégorie de stratégie.|  
|mandate_database_subscriptions|**bit**|Indique si la catégorie de stratégie s'applique à toutes les bases de données dans une instance sans un abonnement explicite (1) ou si la catégorie de stratégie doit être appliquée à une base de données en utilisant un abonnement explicite (0).|  
  
## <a name="remarks"></a>Notes  
 Affiche une liste des groupes de stratégie de la Gestion basée sur des stratégies.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle PolicyAdministratorRole dans la base de données msdb.  
  
## <a name="see-also"></a>Voir aussi  
 [Administrer des serveurs à l'aide de la Gestion basée sur des stratégies](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Vues de la Gestion basée sur des stratégies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  