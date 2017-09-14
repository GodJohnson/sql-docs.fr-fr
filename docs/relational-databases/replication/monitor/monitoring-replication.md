---
title: "Surveillance (réplication) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- monitoring performance [SQL Server replication], about monitoring replication
- transactional replication, monitoring
- monitoring [SQL Server replication]
- merge replication monitoring [SQL Server replication]
- snapshot replication [SQL Server], monitoring
- replication [SQL Server], monitoring
- administering replication, monitoring
ms.assetid: f182f43a-6af8-45bc-a708-08d5f7a6984a
caps.latest.revision: 39
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8b38dc87277d0b3de4a528b8db807cfe0a6245c0
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="monitoring-replication"></a>Surveillance (réplication)
  L'analyse d'une topologie de réplication est un aspect important du déploiement de la réplication. L'activité de la réplication étant distribuée, il est essentiel de faire le suivi de cette activité et des états à travers tous les ordinateurs impliqués dans la réplication. Les outils suivants peuvent être utilisés pour surveiller la réplication :  
  
-   Moniteur de réplication de[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]   
  
     Le moniteur de réplication est l'outil le plus important pour la surveillance de la réplication ; il donne une vision orientée serveur de publication de toute l'activité de réplication. Pour plus d’informations, voir [Monitoring Replication](../../../relational-databases/replication/monitor/monitoring-replication-overview.md).  
  
-   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]  
  
     [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] donne accès au moniteur de réplication. Il vous permet aussi d'afficher l'état actuel et le dernier message consigné par les agents suivants ; il vous permet également de démarrer et d'arrêter chaque agent : Agent de lecture du journal, Agent d'instantané, Agent de fusion et Agent de distribution. Pour plus d’informations, voir [Monitor Replication Agents](../../../relational-databases/replication/monitor/monitor-replication-agents.md).  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)] et Replication Management Objects  
  
     Les deux interfaces vous permettent de surveiller tous les types de réplication à partir du serveur de distribution. La réplication de fusion donne également la possibilité de surveiller la réplication à partir de l'Abonné.  
  
-   Alertes pour les événements des agents de réplication  
  
     La réplication fournit plusieurs alertes prédéfinies pour les événements des agents de réplication ; vous pouvez si nécessaire créer des alertes supplémentaires. Les alertes peuvent être utilisées pour déclencher une réponse automatisée à un événement et/ou envoyer une notification à un administrateur. Pour plus d’informations, consultez [Utiliser les alertes pour les événements des agents de réplication](../../../relational-databases/replication/agents/use-alerts-for-replication-agent-events.md).  
  
-   Moniteur système  
  
     Le Moniteur système peut être utilisé pour surveiller les performances à travers plusieurs compteurs dédiés à la réplication. Pour plus d’informations, voir [Monitoring Replication with System Monitor](../../../relational-databases/replication/monitor/monitoring-replication-with-system-monitor.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Administration &#40;réplication&#41;](../../../relational-databases/replication/administration/administration-replication.md)   
 [Best Practices for Replication Administration](../../../relational-databases/replication/administration/best-practices-for-replication-administration.md)   
 [Surveillance de la réplication](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  