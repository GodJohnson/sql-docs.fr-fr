---
title: Utiliser une Expression dans une contrainte de précédence | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- precedence constraints [Integration Services], adding expressions
- expressions [Integration Services], adding
ms.assetid: 601038bb-3b17-42ac-b09d-5b3a82fb6564
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5dd09ba81c6bdf79abdb5d668821442fad7acab0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48114609"
---
# <a name="use-an-expression-in-a-precedence-constraint"></a>Utiliser une expression dans une contrainte de précédence
  Cette procédure explique comment ajouter une expression à une contrainte de précédence via la boîte de dialogue **Éditeur de contrainte de précédence**. Pour pouvoir ajouter une expression à une contrainte de précédence, le package doit inclure au moins deux exécutables (des tâches ou des conteneurs) qui doivent être connectés par une contrainte de précédence.  
  
### <a name="to-add-an-expression-to-a-precedence-constraint"></a>Pour ajouter une expression à une contrainte de précédence  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l'onglet **Flux de contrôle** .  
  
4.  Dans l’aire de conception de l’onglet **Flux de contrôle** , double-cliquez sur la contrainte de précédence. **L’Éditeur de contrainte de précédence** s’ouvre.  
  
5.  Sélectionnez **Expression**, **Expression et contrainte**ou **Expression ou contrainte** dans la liste **Opération d’évaluation** .  
  
6.  Tapez une expression dans la zone de texte **Expression** ou lancez le Générateur d’expressions pour créer une expression.  
  
7.  Pour valider la syntaxe de l’expression, cliquez sur **Tester**.  
  
8.  Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
## <a name="see-also"></a>Voir aussi  
 [Contraintes de précédence](control-flow/precedence-constraints.md)   
 [Connecter des tâches et des conteneurs à l’aide d’une contrainte de précédence par défaut](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md)   
 [Définissez la valeur d’une contrainte de précédence en utilisant le Menu contextuel](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md)   
 [Définir les propriétés d’une contrainte de précédence](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md)   
 [Expressions Integration Services &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md)  
  
  
