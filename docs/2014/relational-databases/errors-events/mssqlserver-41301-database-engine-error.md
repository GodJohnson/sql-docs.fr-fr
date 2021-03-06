---
title: MSSQLSERVER_41301 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41301 (Database Engine error)
ms.assetid: c6127e1e-2846-4ee9-bc42-2d896ea9730e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: eefac3ed02e97aff727c6741190a81a5973c0e15
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48145279"
---
# <a name="mssqlserver41301"></a>MSSQLSERVER_41301
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID d'événement|41301|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|COMMIT_DEPENDENCY_FAILURE|  
|Texte du message|Une transaction précédente à la transaction actuelle a pris une dépendance ou a été abandonnée, et la transaction en cours ne peut plus être validée.|  
  
## <a name="explanation"></a>Explication  
 La transaction a rencontré une erreur de dépendance, et est maintenant vouée à l'échec.  
  
 Cette erreur peut également être causée par un nombre de transactions dépendantes trop important. Les transactions d'écriture ne peuvent avoir qu'un nombre limité de transactions dépendantes. Par exemple, cette erreur peut se produire si trop de transactions de lecture essaient de prendre une dépendance sur la transaction de mise à jour.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 N'effectuez aucune tâche dans la transaction. Appelez ROLLBACK TRAN pour restaurer la transaction. Pour plus d’informations, consultez [OLTP en mémoire &#40;optimisation en mémoire&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Activer et désactiver les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)  
  
  
