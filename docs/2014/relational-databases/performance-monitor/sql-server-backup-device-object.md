---
title: SQL Server, objet Backup Device | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Backup Device
- Backup Device object
ms.assetid: 52e7febf-d5e0-4674-945b-aacc40a9ad6e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 286c33ac5314321e69c183cfd1ef336da782bfbe
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48064099"
---
# <a name="sql-server-backup-device-object"></a>SQL Server, objet Backup Device
  L’objet **Unité de sauvegarde** fournit des compteurs permettant de surveiller les unités de sauvegarde de Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisées pour les opérations de sauvegarde et de restauration. Surveillez les unités de sauvegarde lorsque vous voulez déterminer le débit ou la progression et les performances de vos opérations de sauvegarde et de restauration par unité. Pour surveiller le débit de l’opération de sauvegarde et de restauration de l’ensemble de la base de données, utilisez le compteur **Débit de sauvegarde/restauration/s** de l’objet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Databases**. Pour plus d’informations, voir [SQL Server, objet Databases](sql-server-databases-object.md).  
  
 Ce tableau décrit le compteur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Backup Device**.  
  
|Compteurs Unité de sauvegarde de SQL Server|Description|  
|---------------------------------------|-----------------|  
|**Débit d'unité en octets/s**|Débit des opérations de lecture et d'écriture (en octets par seconde) pour une unité de sauvegarde utilisée pour la sauvegarde ou la restauration de bases de données. Ce compteur n'existe que lorsque les opérations de sauvegarde ou de restauration sont en cours d'exécution.|  
  
## <a name="see-also"></a>Voir aussi  
 [Unités de sauvegarde &#40;SQL Server&#41;](../backup-restore/backup-devices-sql-server.md)   
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](monitor-resource-usage-system-monitor.md)  
  
  
