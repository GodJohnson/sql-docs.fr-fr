---
title: Sys.pdw_loader_backup_runs (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 2b72034c-6a11-46b9-a76c-7a88b2bea360
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: d8675de8ff7931753d20e99d5c0d61151192e5b2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47751587"
---
# <a name="syspdwloaderbackupruns-transact-sql"></a>Sys.pdw_loader_backup_runs (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contient des informations sur la sauvegarde en cours et terminée et les opérations de restauration dans [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], ainsi que sur la sauvegarde en cours et terminée, restauration et les opérations de chargement dans [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Ces informations sont conservées après le redémarrage du système.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|run_id|**Int**|Identificateur unique pour une sauvegarde spécifique, la restauration ou la charge s’exécuter.<br /><br /> Clé pour cette vue.||  
|NAME|**nvarchar(255)**|NULL pour la charge. Nom facultatif pour la sauvegarde ou de restauration.||  
|submit_time|**datetime**|Heure de que la demande a été soumise.||  
|start_time|**datetime**|Heure à laquelle l'opération a commencé.||  
|end_time|**datetime**|Heure de l’opération terminée, a échoué ou a été annulée.||  
|total_elapsed_time|**Int**|Temps total écoulé entre start_time et l’heure actuelle, ou entre start_time et end_time pour terminé, annulées ou ayant échouées exécutions.|Si total_elapsed_time dépasse la valeur maximale d’un entier (24,8 jours en millisecondes), cela entraînera l’échec de matérialisation en raison d’un dépassement de capacité.<br /><br /> La valeur maximale en millisecondes est équivalente à 24,8 jours environ.|  
|operation_type|**nvarchar(16)**|Le type de charge.|« BACKUP », « CHARGEMENT »', 'RESTORE'|  
|mode|**nvarchar(16)**|Le mode dans le type de la série.|Pour operation_type = **sauvegarde**<br />**SAUVEGARDE DIFFÉRENTIELLE**<br />**FULL**<br /><br /> Pour operation_type = **charge**<br />**AJOUTER**<br />**RECHARGER**<br />**UPSERT**<br /><br /> Pour operation_type = **restaurer**<br />**DATABASE**<br />**HEADER_ONLY**|  
|database_name|**nvarchar(255)**|Nom de la base de données qui est le contexte de cette opération||  
|table_name|**nvarchar(255)**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|Principal_id|**Int**|ID de l’utilisateur qui demande l’opération.||  
|session_id|**nvarchar(32)**|ID de la session de l’opération.|Consultez session_id dans [sys.dm_pdw_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).|  
|request_id|**nvarchar(32)**|ID de la demande d’exécution de l’opération. Pour les charges, il s’agit de la demande actuelle ou la dernière associée à cette charge...|Consultez request_id dans [sys.dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|status|**nvarchar(16)**|État de l’exécution.|« ANNULÉ », « TERMINÉE », « ÉCHEC », « QUEUED », « RUNNING »|  
|Progression|**Int**|Pourcentage effectué.|0 à 100.|  
|commande|**nvarchar(4000)**|Texte complet de la commande envoyée par l’utilisateur.|Sera tronqué si plus de 4000 caractères (compter les espaces).|  
|rows_processed|**bigint**|Nombre de lignes traitées dans le cadre de cette opération.||  
|rows_rejected|**bigint**|Nombre de lignes rejetées dans le cadre de cette opération.||  
|rows_inserted|**bigint**|Nombre de lignes insérées dans l’ou les tables de base de données dans le cadre de cette opération.||  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Data Warehouse et les vues de catalogue Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
