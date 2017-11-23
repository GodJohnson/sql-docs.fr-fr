---
title: Sys.sp_rda_set_rpo_duration (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-stretch
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_set_rpo_duration
- sys.sp_rda_set_rpo_duration_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.sp_rda_set_rpo_duration stored procedure
ms.assetid: 95c80c5b-9252-4612-9ea7-544c48834fd2
caps.latest.revision: "16"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f0dad47cf39ac55848d36a05430d21006bc3089e
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="syssprdasetrpoduration-transact-sql"></a>Sys.sp_rda_set_rpo_duration (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Définit le nombre d’heures de données migrées que SQL Server conserve dans une table intermédiaire afin de garantir une restauration complète de la base de données Azure distante si un point de restauration dans le temps est nécessaire.    
    
 Pour plus d’informations, consultez [Stretch Database réduit le risque de perte de données pour vos données Azure tout en conservant temporairement les lignes migrées](../../sql-server/stretch-database/backup-stretch-enabled-databases-stretch-database.md#stretchRPO).  
   
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)    
     
## <a name="syntax"></a>Syntaxe    
    
```    
    
sp_rda_set_rpo_duration [ @duration_hrs = ] duration_hrs    
    
```    
    
## <a name="arguments"></a>Arguments    
 [ @duration_hrs =] *duration_hrs*    
 Est le nombre d’heures (une valeur d’entier non-null) de données migrées que SQL Server pour conserver la base de données prenant en charge Stretch en cours. La valeur par défaut et la valeur minimale est de 8 heures.    
 
 > [!NOTE]
 > Les valeurs élevées nécessitent davantage d’espace de stockage sur SQL Server.
    
## <a name="permissions"></a>Permissions    
 Nécessite les autorisations db_owner.    
    
## <a name="remarks"></a>Notes    
 Obtenir la valeur actuelle en exécutant [sys.sp_rda_get_rpo_duration &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sys-sp-rda-get-rpo-duration-transact-sql.md).    
    
## <a name="see-also"></a>Voir aussi    
 [Sys.sp_rda_get_rpo_duration &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-get-rpo-duration-transact-sql.md)     
 [Restaurer les bases de données Stretch (Stretch Database)](../../sql-server/stretch-database/restore-stretch-enabled-databases-stretch-database.md)     
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)    
    
  