---
title: Sys.dm_os_threads (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_threads_TSQL
- sys.dm_os_threads
- dm_os_threads
- sys.dm_os_threads_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_threads dynamic management view
ms.assetid: a5052701-edbf-4209-a7cb-afc9e65c41c1
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bda588201965644089d3918c687095bb97d31d45
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47610207"
---
# <a name="sysdmosthreads-transact-sql"></a>sys.dm_os_threads (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne la liste de tous les threads du système d'exploitation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui s'exécutent sous le processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  À appeler à partir [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilisez le nom **sys.dm_pdw_nodes_os_threads**.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|thread_address|**varbinary(8)**|Adresse mémoire (clé primaire) du thread.|  
|started_by_sqlservr|**bit**|Indique l'initiateur du thread.<br /><br /> 1 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a démarré le thread.<br /><br /> 0 = un autre composant a démarré le thread, par exemple une procédure stockée étendue dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|os_thread_id|**Int**|ID du thread qui est attribué par le système d'exploitation.|  
|status|**Int**|Indicateur d'état interne.|  
|instruction_address|**varbinary(8)**|Adresse de l'instruction qui est en cours d'exécution.|  
|creation_time|**datetime**|Heure de création du thread.|  
|kernel_time|**bigint**|Temps du noyau utilisé par ce thread.|  
|usermode_time|**bigint**|Temps utilisateur utilisé par ce thread.|  
|stack_base_address|**varbinary(8)**|Adresse mémoire haute de la pile de ce thread.|  
|stack_end_address|**varbinary(8)**|Adresse mémoire basse de la pile de ce thread.|  
|stack_bytes_committed|**Int**|Nombre d'octets validés dans la pile.|  
|stack_bytes_used|**Int**|Nombre d'octets actuellement utilisés activement sur le thread.|  
|affinité|**bigint**|Masque d'UC sur lequel s'exécute ce thread. Cela dépend de la valeur configurée par le **ALTER SERVER CONFIGURATION SET PROCESS AFFINITY** instruction. Peut être différent du planificateur en cas d'affinité logicielle.|  
|Priorité|**Int**|Priorité du thread.|  
|Paramètres régionaux|**Int**|Indicateur de paramètres régionaux mis en cache (LCID) pour le thread.|  
|Jeton|**varbinary(8)**|Descripteur du jeton d'emprunt d'identité mis en cache pour le thread.|  
|is_impersonating|**Int**|Indique si ce thread utilise l'emprunt d'identité Win32.<br /><br /> 1 = Le thread utilise des informations d'autorisation sécurisées différentes des informations par défaut du processus. Cela indique que le thread emprunte l'identité d'une entité différente de celle qui a créé le processus.|  
|is_waiting_on_loader_lock|**Int**|État du système d'exploitation qui indique si le thread attend le verrou du chargeur.|  
|fiber_data|**varbinary(8)**|Fibre Win32 actuelle en cours d'exécution sur le thread. S'applique uniquement lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configuré pour le regroupement léger.|  
|thread_handle|**varbinary(8)**|À usage interne uniquement|  
|event_handle|**varbinary(8)**|À usage interne uniquement|  
|scheduler_address|**varbinary(8)**|Adresse mémoire du planificateur associé au thread. Pour plus d’informations, consultez [sys.dm_os_schedulers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md).|  
|worker_address|**varbinary(8)**|Adresse mémoire du thread de travail associé à ce thread. Pour plus d’informations, consultez [sys.dm_os_workers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md).|  
|fiber_context_address|**varbinary(8)**|Adresse interne du contexte de la fibre. S'applique uniquement lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configuré pour le regroupement léger.|  
|self_address|**varbinary(8)**|Pointeur de cohérence interne.|  
|processor_group|**smallint**|**S'applique à**: [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> ID de groupe de processeurs.|  
|pdw_node_id|**Int**|**S’applique aux**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L’identificateur pour le nœud se trouvant sur cette distribution.|  
  
## <a name="permissions"></a>Permissions

Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], nécessite `VIEW SERVER STATE` autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], nécessite le `VIEW DATABASE STATE` autorisation dans la base de données.   

## <a name="examples"></a>Exemples  
 Au démarrage, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] démarre des threads puis leur associe des threads de travail. Cependant, des composants externes (par exemple, une procédure stockée étendue) peuvent démarrer des threads sous le processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne contrôle pas ces threads. Sys.dm_os_threads peut fournir des informations sur les threads non autorisés qui consomment des ressources dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] processus.  
  
 La requête suivante permet de rechercher des threads de travail (ainsi que la durée utilisée pour l'exécution) qui exécutent des threads non démarrés par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Dans un souci de concision, la requête suivante utilise un astérisque (`*`) dans l'instruction `SELECT`. Évitez d'utiliser l'astérique (*), surtout avec des affichages catalogue, des vues de gestion dynamique et des fonctions table système. Futures mises à niveau et les versions de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut ajouter des colonnes et modifier l’ordre des colonnes pour ces fonctions et vues. Ces changements entraveront peut-être le fonctionnement des applications qui attendent un ordre et un nombre de colonnes spécifiques.  
  
```  
SELECT *  
  FROM sys.dm_os_threads  
  WHERE started_by_sqlservr = 0;  
```  
  
## <a name="see-also"></a>Voir aussi  
  [Sys.dm_os_workers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md)   
 [Vues de gestion dynamique liées à système d’exploitation SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


