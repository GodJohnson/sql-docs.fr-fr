---
title: MSSQLSERVER_41302 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 41302 (Database Engine error)
ms.assetid: 01e75618-afec-4232-ba68-93ab7bc31003
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 72e2f817ce6a7f569fbf2a62d0bb2d610beefa71
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47625697"
---
# <a name="mssqlserver41302"></a>MSSQLSERVER_41302
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID d'événement|41302|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|WRITE_WRITE_CONFLICT|  
|Texte du message|La transaction en cours a tenté de mettre à jour un enregistrement qui a été mis à jour depuis le début de cette transaction. La transaction a été abandonnée.|  
  
## <a name="explanation"></a>Explication  
La transaction a rencontré un conflit d'écriture/écriture et l'instruction s'est arrêtée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Recommencez l'opération ultérieurement dans une autre transaction. Pour plus d’informations, consultez [OLTP en mémoire &#40;optimisation en mémoire&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a> Voir aussi  
[OLTP en mémoire &#40;Optimisation en mémoire&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
