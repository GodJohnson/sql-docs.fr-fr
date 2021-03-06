---
title: Sys.dm_pdw_node_status (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 8e263b65-81d0-49d0-8873-62ef424369d6
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: fef824d594ea77e1c13df2251872b780e21344b7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47796837"
---
# <a name="sysdmpdwnodestatus-transact-sql"></a>Sys.dm_pdw_node_status (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Contient des informations supplémentaires (via [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)) sur les performances et l’état de tous les nœuds d’appliance. Elle répertorie une ligne par nœud dans l’appliance.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**Int**|Id numérique unique associé au nœud.<br /><br /> Clé pour cette vue.|Unique sur l’appliance, quel que soit le type.|  
|process_id|**Int**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|nom_processus|**nvarchar(255)**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|allocated_memory|**bigint**|Mémoire totale allouée sur ce nœud.||  
|available_memory|**bigint**|Mémoire totale disponible sur ce nœud.||  
|process_cpu_usage|**bigint**|Utilisation du processeur de processus totale, en graduations.||  
|total_cpu_usage|**bigint**|Utilisation totale du processeur, en graduations.||  
|Thread_Count|**bigint**|Nombre total de threads en cours d’utilisation sur ce nœud.||  
|handle_count|**bigint**|Nombre total de handles en cours d’utilisation sur ce nœud.||  
|total_elapsed_time|**bigint**|Temps total écoulé depuis le système de démarrer ou redémarrer.|Temps total écoulé depuis le système de démarrer ou redémarrer. Si total_elapsed_time dépasse la valeur maximale d’un entier (24,8 jours en millisecondes), cela entraînera l’échec de matérialisation en raison d’un dépassement de capacité.<br /><br /> La valeur maximale en millisecondes est équivalente à 24,8 jours environ.|  
|is_available|**bit**|Indicateur précisant si ce nœud est disponible.||  
|sent_time|**datetime**|Dernière fois un package de réseau a été envoyé par ce nœud.||  
|received_time|**datetime**|Dernière fois un package de réseau a été reçu par ce nœud.||  
|error_id|**nvarchar(36)**|Identificateur unique de la dernière erreur qui s’est produite sur ce nœud.||  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de gestion dynamique de l’entrepôt SQL Data Warehouse et Parallel Data &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
