---
title: "Référence de classe d’événements SQL Server | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [SQL Server], event classes
- event classes [SQL Server], listed
- event classes [SQL Server]
- SQL Server event classes, listed
- SQL Server event classes
ms.assetid: 0f0fe567-e115-4ace-b63c-73dc3428c0f6
caps.latest.revision: 34
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d88dcea1aee43bc8603bfe25b73a8c5b09cb31ad
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="sql-server-event-class-reference"></a>Référence de classe d'événements SQL Server
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] lets you record events as they occur in an instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Les événements enregistrés sont des instances des classes d'événements présentes dans la définition de trace. Dans [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], les classes d’événements et leurs catégories sont disponibles sous l’onglet **Sélection des événements** de la boîte de dialogue **Propriétés du fichier de suivi** .  
  
 Le tableau suivant décrit les catégories d’événement et énumère leurs classes d’événements associées.  
  
|Catégorie d'événement|Classes d'événements|  
|--------------------|-------------------|  
|La [Catégorie d’événement Broker](../../relational-databases/event-classes/broker-event-category.md) comprend des classes d’événements produites par [!INCLUDE[ssSB](../../includes/sssb-md.md)].|[Classe d'événement Broker:Activation](../../relational-databases/event-classes/broker-activation-event-class.md)<br /><br /> [Classe d'événement Broker:Connection](../../relational-databases/event-classes/broker-connection-event-class.md)<br /><br /> [Classe d'événements Broker:Conversation](../../relational-databases/event-classes/broker-conversation-event-class.md)<br /><br /> [Classe d'événement Broker:Conversation Group](../../relational-databases/event-classes/broker-conversation-group-event-class.md)<br /><br /> [Classe d'événements Broker:Corrupted Message](../../relational-databases/event-classes/broker-corrupted-message-event-class.md)<br /><br /> [Classe d'événements Broker:Forwarded Message Dropped](../../relational-databases/event-classes/broker-forwarded-message-dropped-event-class.md)<br /><br /> [Broker:Forwarded Message Sent (classe d'événements)](../../relational-databases/event-classes/broker-forwarded-message-sent-event-class.md)<br /><br /> [Classe d'événements Broker:Message Classify](../../relational-databases/event-classes/broker-message-classify-event-class.md)<br /><br /> [Classe d'événements Broker:Message Drop](../../relational-databases/event-classes/broker-message-drop-event-class.md)<br /><br /> [Classe d'événements Broker:Remote Message Ack](../../relational-databases/event-classes/broker-remote-message-ack-event-class.md)|  
|La [Catégorie d’événements Cursors](../../relational-databases/event-classes/cursors-event-category.md) comprend des classes d’événements produites par les opérations impliquant le curseur.|[Classe d'événements CursorClose](../../relational-databases/event-classes/cursorclose-event-class.md)<br /><br /> [Classe d'événements CursorExecute](../../relational-databases/event-classes/cursorexecute-event-class.md)<br /><br /> [Classe d'événements CursorImplicitConversion](../../relational-databases/event-classes/cursorimplicitconversion-event-class.md)<br /><br /> [Classe d'événements CursorOpen](../../relational-databases/event-classes/cursoropen-event-class.md)<br /><br /> [Classe d'événements CursorPrepare](../../relational-databases/event-classes/cursorprepare-event-class.md)<br /><br /> [Classe d'événements CursorRecompile](../../relational-databases/event-classes/cursorrecompile-event-class.md)<br /><br /> [Classe d'événements CursorUnprepare](../../relational-databases/event-classes/cursorunprepare-event-class.md)|  
|La [Catégorie d’événement CLR](../../relational-databases/event-classes/clr-event-category.md) inclut les classes d’événements qui sont produites par l’exécution d’objets CLR (Common Language Runtime) .NET.|[Classe d'événements Assembly Load](http://msdn.microsoft.com/library/cfb0b69d-4ce0-4067-a3df-d82775e57886)|  
|La [Catégorie d’événement Base de données](../../relational-databases/event-classes/database-event-category.md) comprend des classes d’événements produits quand la taille de fichiers de données ou de fichiers journaux augmente ou diminue automatiquement.|[Classe d'événements Data File Auto Grow](../../relational-databases/event-classes/data-file-auto-grow-event-class.md)<br /><br /> [Classe d'événements Data File Auto Shrink](../../relational-databases/event-classes/data-file-auto-shrink-event-class.md)<br /><br /> [Classe d'événements Database Mirroring State Change](../../relational-databases/event-classes/database-mirroring-state-change-event-class.md)<br /><br /> [Classe d'événements Log File Auto Grow](../../relational-databases/event-classes/log-file-auto-grow-event-class.md)<br /><br /> [Classe d'événements Log File Auto Shrink](../../relational-databases/event-classes/log-file-auto-shrink-event-class.md)|  
|La [Catégorie d’événement Deprecation](../../relational-databases/event-classes/deprecation-event-category.md) comprend les événements de désapprobation associés.|[Classe d'événements Deprecation Announcement](../../relational-databases/event-classes/deprecation-announcement-event-class.md)<br /><br /> [Classe d'événements Deprecation Final Support](../../relational-databases/event-classes/deprecation-final-support-event-class.md)|  
|La [Catégorie d’événement Erreurs et avertissements&#40;moteur de base de données&#41;](../../relational-databases/event-classes/errors-and-warnings-event-category-database-engine.md) comprend des classes d’événements produites lors du retour d’une erreur ou d’un avertissement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], par exemple si une erreur se produit pendant la compilation d’une procédure stockée ou si une exception se produit dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|[Classe d'événements Attention](../../relational-databases/event-classes/attention-event-class.md)<br /><br /> [Classe d'événements Background Job Error](../../relational-databases/event-classes/background-job-error-event-class.md)<br /><br /> [Classe d'événements Blocked Process Report](../../relational-databases/event-classes/blocked-process-report-event-class.md)<br /><br /> [Classe d'événements CPU Threshold Exceeded](../../relational-databases/event-classes/cpu-threshold-exceeded-event-class.md)<br /><br /> [Classe d'événements ErrorLog](../../relational-databases/event-classes/errorlog-event-class.md)<br /><br /> [Classe d'événements EventLog](../../relational-databases/event-classes/eventlog-event-class.md)<br /><br /> [Classe d'événements Exception](../../relational-databases/event-classes/exception-event-class.md)<br /><br /> [Classe d'événements Exchange Spill](../../relational-databases/event-classes/exchange-spill-event-class.md)<br /><br /> [Classe d'événements Execution Warnings](../../relational-databases/event-classes/execution-warnings-event-class.md)<br /><br /> [Classe d'événements Hash Warning](../../relational-databases/event-classes/hash-warning-event-class.md)<br /><br /> [Classe d'événements Missing Column Statistics](../../relational-databases/event-classes/missing-column-statistics-event-class.md)<br /><br /> [Classe d'événements Missing Join Predicate](../../relational-databases/event-classes/missing-join-predicate-event-class.md)<br /><br /> [Classe d'événements Sort Warnings](../../relational-databases/event-classes/sort-warnings-event-class.md)<br /><br /> [Classe d'événements User Error Message](../../relational-databases/event-classes/user-error-message-event-class.md)|  
|La [Catégorie d’événements Texte intégral](../../relational-databases/event-classes/full-text-event-category.md) comprend des classes d’événements produites lors du démarrage, de l’interruption ou de l’arrêt de recherches en texte intégral.|[Classe d'événements FT:Crawl Aborted](../../relational-databases/event-classes/ft-crawl-aborted-event-class.md)<br /><br /> [Classe d'événements FT:Crawl Started](../../relational-databases/event-classes/ft-crawl-started-event-class.md)<br /><br /> [Classe d'événements FT:Crawl Stopped](../../relational-databases/event-classes/ft-crawl-stopped-event-class.md)|  
|La [Catégorie d’événement Verrous](../../relational-databases/event-classes/locks-event-category.md) comprend des classes d’événements produites quand une action est effectuée sur un verrou (acquisition, annulation, libération, etc.).|[Classe d'événements Deadlock Graph](../../relational-databases/event-classes/deadlock-graph-event-class.md)<br /><br /> [Classe d'événements Lock:Acquired](../../relational-databases/event-classes/lock-acquired-event-class.md)<br /><br /> [Classe d'événements Lock:Cancel](../../relational-databases/event-classes/lock-cancel-event-class.md)<br /><br /> [Classe d'événements Lock:Deadlock Chain](../../relational-databases/event-classes/lock-deadlock-chain-event-class.md)<br /><br /> [Classe d'événements Lock:Deadlock](../../relational-databases/event-classes/lock-deadlock-event-class.md)<br /><br /> [Classe d'événements Lock:Escalation](../../relational-databases/event-classes/lock-escalation-event-class.md)<br /><br /> [Classe d'événements Lock:Released](../../relational-databases/event-classes/lock-released-event-class.md)<br /><br /> [Classe d’événements Lock:Timeout &#40;timeout &#62; 0&#41;](../../relational-databases/event-classes/lock-timeout-timeout-0-event-class.md)<br /><br /> [Classe d'événements Lock:Timeout](../../relational-databases/event-classes/lock-timeout-event-class.md)|  
|La [Catégorie d’événement Objets](../../relational-databases/event-classes/objects-event-category.md) comprend des classes d’événements produites quand des objets de base de données sont créés, ouverts, fermés, détruits ou supprimés.|[Classe d'événements Auto Stats](../../relational-databases/event-classes/auto-stats-event-class.md)<br /><br /> [Classe d'événements : Object:Altered](../../relational-databases/event-classes/object-altered-event-class.md)<br /><br /> [Classe d'événements Object:Created](../../relational-databases/event-classes/object-created-event-class.md)<br /><br /> [Classe d'événements Object:Deleted](../../relational-databases/event-classes/object-deleted-event-class.md)|  
|La [Catégorie d’événement OLEDB](../../relational-databases/event-classes/oledb-event-category.md) comprend des classes d’événements produites par des appels OLE DB.|[Classe d'événements OLEDB Call](../../relational-databases/event-classes/oledb-call-event-class.md)<br /><br /> [Classe d'événements OLEDB DataRead](../../relational-databases/event-classes/oledb-dataread-event-class.md)<br /><br /> [Classe d'événements OLEDB Errors](../../relational-databases/event-classes/oledb-errors-event-class.md)<br /><br /> [Classe d'événements OLEDB Provider Information](../../relational-databases/event-classes/oledb-provider-information-event-class.md)<br /><br /> [Classe d'événements OLEDB QueryInterface](../../relational-databases/event-classes/oledb-queryinterface-event-class.md)|  
|La [Catégorie d’événements Performance](../../relational-databases/event-classes/performance-event-category.md) comprend des classes d’événements produites par l’exécution des opérateurs de manipulation des données SQL (DML, Data Manipulation Language).|[Classe d’événements Degree of Parallelism &#40;7.0 Insert&#41;](../../relational-databases/event-classes/degree-of-parallelism-7-0-insert-event-class.md)<br /><br /> [Classe d'événements Performance Statistics](../../relational-databases/event-classes/performance-statistics-event-class.md)<br /><br /> [Classe d'événements Showplan All](../../relational-databases/event-classes/showplan-all-event-class.md)<br /><br /> [Classe d'événements Showplan All for Query Compile](../../relational-databases/event-classes/showplan-all-for-query-compile-event-class.md)<br /><br /> [Classe d'événements Showplan Statistics Profile](../../relational-databases/event-classes/showplan-statistics-profile-event-class.md)<br /><br /> [Classe d'événements Showplan Text](../../relational-databases/event-classes/showplan-text-event-class.md)<br /><br /> [Classe d’événements Showplan Text &#40;non encodée&#41;](../../relational-databases/event-classes/showplan-text-unencoded-event-class.md)<br /><br /> [Classe d'événements Showplan XML](../../relational-databases/event-classes/showplan-xml-event-class.md)<br /><br /> [Classe d'événements Showplan XML for Query Compile](../../relational-databases/event-classes/showplan-xml-for-query-compile-event-class.md)<br /><br /> [Classe d'événements Showplan XML Statistics Profile](../../relational-databases/event-classes/showplan-xml-statistics-profile-event-class.md)<br /><br /> [Classe d'événements SQL:FullTextQuery](../../relational-databases/event-classes/sql-fulltextquery-event-class.md)|  
|La [Catégorie d’événement de rapport de progression](../../relational-databases/event-classes/progress-report-event-category.md) comprend la classe d’événements **Progress Report: Online Index Operation** .|[Classe d'événements Progress Report: Online Index Operation](../../relational-databases/event-classes/progress-report-online-index-operation-event-class.md)|  
|La [Catégorie d’événements Scans](../../relational-databases/event-classes/scans-event-category.md) comprend des classes d’événements produites lors de l’analyse de tables et d’index.|[Classe d'événements Scan:Started](../../relational-databases/event-classes/scan-started-event-class.md)<br /><br /> [Classe d'événements Scan:Stopped](../../relational-databases/event-classes/scan-stopped-event-class.md)|  
|La [Catégorie d’événement Audit de sécurité](../../relational-databases/event-classes/security-audit-event-category-sql-server-profiler.md) comprend des classes d’événements servant à surveiller l’activité du serveur.|[Classe d'événements Audit Add DB User](../../relational-databases/event-classes/audit-add-db-user-event-class.md)<br /><br /> [Classe d'événements Audit Add Login to Server Role](../../relational-databases/event-classes/audit-add-login-to-server-role-event-class.md)<br /><br /> [Classe d'événements Audit Add Member to DB Role](../../relational-databases/event-classes/audit-add-member-to-db-role-event-class.md)<br /><br /> [Classe d'événements Audit Add Role](../../relational-databases/event-classes/audit-add-role-event-class.md)<br /><br /> [Classe d'événements Audit Addlogin](../../relational-databases/event-classes/audit-addlogin-event-class.md)<br /><br /> [Classe d'événements Audit App Role Change Password](../../relational-databases/event-classes/audit-app-role-change-password-event-class.md)<br /><br /> [Classe d’événements Audit Backup/Restore](../../relational-databases/event-classes/audit-backup-and-restore-event-class.md)<br /><br /> [Classe d'événement Audit Broker Conversation](../../relational-databases/event-classes/audit-broker-conversation-event-class.md)<br /><br /> [Classe d'événements Audit Broker Login](../../relational-databases/event-classes/audit-broker-login-event-class.md)<br /><br /> [Classe d'événements Audit Change Audit](../../relational-databases/event-classes/audit-change-audit-event-class.md)<br /><br /> [Classe d'événements Audit Change Database Owner](../../relational-databases/event-classes/audit-change-database-owner-event-class.md)<br /><br /> [Classe d'événements Audit Database Management](../../relational-databases/event-classes/audit-database-management-event-class.md)<br /><br /> [Classe d'événements Audit Database Object Access](../../relational-databases/event-classes/audit-database-object-access-event-class.md)<br /><br /> [Classe d'événements Audit Database Object GDR](../../relational-databases/event-classes/audit-database-object-gdr-event-class.md)<br /><br /> [Classe d'événements Audit Database Object Management](../../relational-databases/event-classes/audit-database-object-management-event-class.md)<br /><br /> [Classe d'événements Audit Database Object Take Ownership](../../relational-databases/event-classes/audit-database-object-take-ownership-event-class.md)<br /><br /> [Classe d'événements Audit Database Operation](../../relational-databases/event-classes/audit-database-operation-event-class.md)<br /><br /> [Classe d'événements Audit Database Principal Impersonation](../../relational-databases/event-classes/audit-database-principal-impersonation-event-class.md)<br /><br /> [Classe d'événements Audit Database Principal Management](../../relational-databases/event-classes/audit-database-principal-management-event-class.md)<br /><br /> [Classe d'événements Audit Database Scope GDR](../../relational-databases/event-classes/audit-database-scope-gdr-event-class.md)<br /><br /> [Classe d'événements Audit DBCC](../../relational-databases/event-classes/audit-dbcc-event-class.md)<br /><br /> [Classe d'événements Audit Login Change Password](../../relational-databases/event-classes/audit-login-change-password-event-class.md)<br /><br /> [Classe d'événements Audit Login Change Property](../../relational-databases/event-classes/audit-login-change-property-event-class.md)<br /><br /> [Classe d'événements Audit Login](../../relational-databases/event-classes/audit-login-event-class.md)<br /><br /> [Classe d'événements Audit Login Failed](../../relational-databases/event-classes/audit-login-failed-event-class.md)<br /><br /> [Classe d'événements Audit Login GDR](../../relational-databases/event-classes/audit-login-gdr-event-class.md)<br /><br /> [Classe d'événements Audit Logout](../../relational-databases/event-classes/audit-logout-event-class.md)<br /><br /> [Classe d'événements Audit Object Derived Permission](../../relational-databases/event-classes/audit-object-derived-permission-event-class.md)<br /><br /> [Classe d'événements Audit Schema Object Access](../../relational-databases/event-classes/audit-schema-object-access-event-class.md)<br /><br /> [Classe d'événements Audit Schema Object GDR](../../relational-databases/event-classes/audit-schema-object-gdr-event-class.md)<br /><br /> [Classe d'événements Audit Schema Object Management](../../relational-databases/event-classes/audit-schema-object-management-event-class.md)<br /><br /> [Classe d'événements Audit Schema Object Take Ownership](../../relational-databases/event-classes/audit-schema-object-take-ownership-event-class.md)<br /><br /> [Classe d'événements Audit Server Alter Trace](../../relational-databases/event-classes/audit-server-alter-trace-event-class.md)<br /><br /> [Classe d'événements Audit Server Object GDR](../../relational-databases/event-classes/audit-server-object-gdr-event-class.md)<br /><br /> [Classe d'événements Audit Server Object Management](../../relational-databases/event-classes/audit-server-object-management-event-class.md)<br /><br /> [Classe d'événements Audit Server Object Take Ownership](../../relational-databases/event-classes/audit-server-object-take-ownership-event-class.md)<br /><br /> [Classe d'événements Audit Server Operation](../../relational-databases/event-classes/audit-server-operation-event-class.md)<br /><br /> [Classe d'événements Audit Server Principal Impersonation](../../relational-databases/event-classes/audit-server-principal-impersonation-event-class.md)<br /><br /> [Classe d'événements Audit Server Principal Management](../../relational-databases/event-classes/audit-server-principal-management-event-class.md)<br /><br /> [Classe d'événements Audit Server Scope GDR](../../relational-databases/event-classes/audit-server-scope-gdr-event-class.md)<br /><br /> [Classe d'événements Audit Server Starts and Stops](../../relational-databases/event-classes/audit-server-starts-and-stops-event-class.md)<br /><br /> [Classe d'événements Audit Statement Permission](../../relational-databases/event-classes/audit-statement-permission-event-class.md)|  
|La [Catégorie d’événement Serveur](../../relational-databases/event-classes/server-event-category.md) contient des événements généraux relatifs au serveur.|[Classe d'événements Mount Tape](../../relational-databases/event-classes/mount-tape-event-class.md)<br /><br /> [Classe d'événements Server Memory Change](../../relational-databases/event-classes/server-memory-change-event-class.md)<br /><br /> [Classe d'événements Trace File Close](../../relational-databases/event-classes/trace-file-close-event-class.md)|  
|La [Catégorie d’événements Sessions](../../relational-databases/event-classes/sessions-event-category.md) comprend des classes d’événements produites par la connexion et la déconnexion des clients d’une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|[Classe d'événements ExistingConnection](../../relational-databases/event-classes/existingconnection-event-class.md)|  
|La [Catégorie d’événements Procédures stockées](../../relational-databases/event-classes/stored-procedures-event-category.md) comprend des classes d’événements produites par l’exécution de procédures stockées.|[Classe d'événements PreConnect:Completed](../../relational-databases/event-classes/preconnect-completed-event-class.md)<br /><br /> [PreConnect:Starting, classe d'événements](../../relational-databases/event-classes/preconnect-starting-event-class.md)<br /><br /> [Classe d'événements RPC:Completed](../../relational-databases/event-classes/rpc-completed-event-class.md)<br /><br /> [Classe d'événements RPC Output Parameter](../../relational-databases/event-classes/rpc-output-parameter-event-class.md)<br /><br /> [Classe d'événements RPC:Starting](../../relational-databases/event-classes/rpc-starting-event-class.md)<br /><br /> [Classe d'événements SP:CacheHit](../../relational-databases/event-classes/sp-cachehit-event-class.md)<br /><br /> [Classe d'événements SP:CacheInsert](../../relational-databases/event-classes/sp-cacheinsert-event-class.md)<br /><br /> [Classe d'événements SP:CacheMiss](../../relational-databases/event-classes/sp-cachemiss-event-class.md)<br /><br /> [Classe d'événements SP:CacheRemove](../../relational-databases/event-classes/sp-cacheremove-event-class.md)<br /><br /> [Classe d'événements SP:Completed](../../relational-databases/event-classes/sp-completed-event-class.md)<br /><br /> [Classe d'événements SP:Recompile](../../relational-databases/event-classes/sp-recompile-event-class.md)<br /><br /> [Classe d'événements SP:Starting](../../relational-databases/event-classes/sp-starting-event-class.md)<br /><br /> [Classe d'événements SP:StmtCompleted](../../relational-databases/event-classes/sp-stmtcompleted-event-class.md)<br /><br /> [Classe d'événements SP:StmtStarting](../../relational-databases/event-classes/sp-stmtstarting-event-class.md)|  
|La [Catégorie d’événements Transactions](../../relational-databases/event-classes/transactions-event-category.md) comprend des classes d’événements produites par l’exécution de transactions [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator ou par l’écriture dans le journal des transactions.|[Classe d'événements DTCTransaction](../../relational-databases/event-classes/dtctransaction-event-class.md)<br /><br /> [Classe d'événements SQLTransaction](../../relational-databases/event-classes/sqltransaction-event-class.md)<br /><br /> [Classe d'événements TM: Begin Tran Completed](../../relational-databases/event-classes/tm-begin-tran-completed-event-class.md)<br /><br /> [Classe d'événements TM: Begin Tran Starting](../../relational-databases/event-classes/tm-begin-tran-starting-event-class.md)<br /><br /> [Classe d'événements TM: Commit Tran Completed](../../relational-databases/event-classes/tm-commit-tran-completed-event-class.md)<br /><br /> [Classe d'événements TM: Commit Tran Starting](../../relational-databases/event-classes/tm-commit-tran-starting-event-class.md)<br /><br /> [Classe d'événements TM: Promote Tran Completed](../../relational-databases/event-classes/tm-promote-tran-completed-event-class.md)<br /><br /> [Classe d'événements TM: Promote Tran Starting](../../relational-databases/event-classes/tm-promote-tran-starting-event-class.md)<br /><br /> [Classe d'événements TM: Rollback Tran Completed](../../relational-databases/event-classes/tm-rollback-tran-completed-event-class.md)<br /><br /> [Classe d'événements TM: Rollback Tran Starting](../../relational-databases/event-classes/tm-rollback-tran-starting-event-class.md)<br /><br /> [Classe d'événements TM: Save Tran Completed](../../relational-databases/event-classes/tm-save-tran-completed-event-class.md)<br /><br /> [Classe d'événements TM: Save Tran Starting](../../relational-databases/event-classes/tm-save-tran-starting-event-class.md)<br /><br /> [Classe d'événements TransactionLog](../../relational-databases/event-classes/transactionlog-event-class.md)|  
|La [Catégorie d’événements TSQL](../../relational-databases/event-classes/tsql-event-category.md) comprend des classes d’événements produites par l’exécution d’instructions Transact-SQL passées à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par le client.|[Classe d'événements Exec Prepared SQL](../../relational-databases/event-classes/exec-prepared-sql-event-class.md)<br /><br /> [Classe d'événements Prepare SQL](../../relational-databases/event-classes/prepare-sql-event-class.md)<br /><br /> [Classe d'événements SQL:BatchCompleted](../../relational-databases/event-classes/sql-batchcompleted-event-class.md)<br /><br /> [Classe d'événements SQL:BatchStarting](../../relational-databases/event-classes/sql-batchstarting-event-class.md)<br /><br /> [Classe d'événements SQL:StmtCompleted](../../relational-databases/event-classes/sql-stmtcompleted-event-class.md)<br /><br /> [Classe d'événements SQL:StmtRecompile](../../relational-databases/event-classes/sql-stmtrecompile-event-class.md)<br /><br /> [Classe d'événements SQL:StmtStarting](../../relational-databases/event-classes/sql-stmtstarting-event-class.md)<br /><br /> [Classe d'événements Unprepare SQL](../../relational-databases/event-classes/unprepare-sql-event-class.md)<br /><br /> [Classe d'événements XQuery Static Type](../../relational-databases/event-classes/xquery-static-type-event-class.md)|  
|La [Catégorie d’événement Configurables par l’utilisateur](../../relational-databases/event-classes/user-configurable-event-category.md) comprend des classes d’événements que vous pouvez définir.|[Classe d'événements configurables par l'utilisateur](../../relational-databases/event-classes/user-configurable-event-class.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  