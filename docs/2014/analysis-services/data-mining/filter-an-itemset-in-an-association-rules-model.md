---
title: Filtre de modèle de règles d’un jeu d’éléments dans une Association | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- itemsets [Analysis Services]
- filtering itemsets [Analysis Services]
- Mining Model Viewer [Analysis Services], itemsets
ms.assetid: 3ed919ea-8598-45d2-a4a0-b1b3357a4ab1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 42f1ed629413bd68f01abd12679907f58d204a78
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48173539"
---
# <a name="filter-an-itemset-in-an-association-rules-model"></a>Filtrer un jeu d'éléments dans un modèle de règles d'association
  Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vous pouvez filtrer les jeux d’éléments affichés sous l’onglet **Jeux d’éléments** de la visionneuse de l’algorithme MAR ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules).  
  
### <a name="to-filter-an-itemset"></a>Pour filtrer un jeu d'éléments  
  
1.  Sous l’onglet **Visionneuse de modèle d’exploration de données** du Concepteur d’exploration de données dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], cliquez sur l’onglet **Jeux d’éléments** de la **Visionneuse de l’algorithme MAR (Microsoft Association Rules)**.  
  
2.  Entrez une condition de règle dans la zone **Filtrer le jeu d’éléments** . Par exemple, une condition de règle pourrait être « Touring-1000 = existing ».  
  
3.  Cliquez sur **Entrée**.  
  
 Les jeux d'éléments sont filtrés pour afficher uniquement ceux qui contiennent les éléments sélectionnés. La zone ne respecte pas la casse. Les filtres sont stockés en mémoire pour vous permettre de sélectionner un ancien filtre dans la liste.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches et procédures de la visionneuse de modèle d’exploration de données](mining-model-viewer-tasks-and-how-tos.md)  
  
  
