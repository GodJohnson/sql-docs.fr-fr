---
title: Relire des Traces | Documents Microsoft
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
- SQL Server Profiler, replaying traces
- Run to Cursor option
- Toggle Breakpoint option
- traces [SQL Server], replaying
- replaying traces
- playback engine [SQL Server Profiler]
- events [SQL Server], replaying traces
- Profiler [SQL Server Profiler], replaying traces
ms.assetid: da958d3c-7f3e-44c9-aecc-8a9493bea7c0
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 09eb93462d990d374c4e38ecdaea1918cb832f11
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="replay-traces"></a>Relire des traces
  La relecture est la capacité de reproduire une activité capturée dans une trace. Lorsque vous créez ou modifiez une trace, vous pouvez enregistrer cette trace dans un fichier pour la relire ultérieurement. Vous pouvez utiliser le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] pour relire l’activité de trace d’un ordinateur unique. Pour les charges de travail importantes, utilisez Distributed Replay Utility pour relire les données de trace de plusieurs ordinateurs.  
  
 Cette section décrit comment utiliser les fonctionnalités de relecture du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Pour plus d’informations sur Distributed Replay Utility, consultez [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md).  
  
 Le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] contient un moteur de lecture à plusieurs threads capable de simuler les connexions utilisateur et l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La relecture est utile pour résoudre les problèmes d'applications ou de processus. Lorsque vous avez identifié le problème et mis en œuvre les corrections, exécutez la trace qui a détecté le problème potentiel sur l'application ou le processus corrigé. Relisez ensuite la trace d'origine et comparez les résultats.  
  
 La relecture de trace prend en charge le débogage à l’aide des options **Basculer le point d’arrêt** et **Exécuter jusqu’au curseur** du menu [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **de** . Ces options améliorent en particulier l'analyse des scripts longs, car elles peuvent diviser la relecture de la trace en segments courts de façon à pouvoir les analyser de manière incrémentielle.  
  
 Pour plus d’informations sur les autorisations nécessaires pour relire des traces, consultez [Autorisations nécessaires pour exécuter SQL Server Profiler](../../tools/sql-server-profiler/permissions-required-to-run-sql-server-profiler.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Conditions préalables de relecture](../../tools/sql-server-profiler/replay-requirements.md)|Décrit les événements qui doivent être inclus dans la définition d'une trace pour qu'elle puisse être relue à l'aide du [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].|  
|[Options de relecture &#40; SQL Server Profiler &#41;](../../tools/sql-server-profiler/replay-options-sql-server-profiler.md)|Décrit les options que vous pouvez définir dans la boîte de dialogue **Configuration de la relecture** de [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].|  
|[Considérations sur la relecture des Traces &#40; SQL Server Profiler &#41;](../../tools/sql-server-profiler/considerations-for-replaying-traces-sql-server-profiler.md)|Décrit les événements de trace qui ne peuvent pas être relus avec le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] et les effets de la relecture des traces sur les performances du serveur.|  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md)  
  
  