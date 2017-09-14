---
title: "Fusionner des cellules dans une région de données (Générateur de rapports et SSRS) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43551300-89b2-4f4e-af09-69084324afaf
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c643b94c86109a99e1448093b4b9744924fcd7f7
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="merge-cells-in-a-data-region-report-builder-and-ssrs"></a>Fusionner des cellules dans une région de données (Générateur de rapports et SSRS)
Dans un rapport paginé [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , vous pouvez fusionner des cellules dans une région de données pour les combiner, améliorer l’apparence de la région de données ou fournir des étiquettes étendues pour les groupes de colonnes et de lignes.  
  
Vous pouvez fusionner les cellules uniquement à l’intérieur de chaque zone d’une région de données : angle, en-têtes de colonne, définition de groupe (ou en-têtes de ligne) et corps. Vous ne pouvez pas fusionner de cellules dépassant les limites de la zone. Par exemple, vous ne pouvez pas fusionner une cellule située dans la zone d’angle de la région de données avec une cellule située dans la zone de groupe de lignes. En savoir plus sur les [Tables, matrices et listes &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-merge-cells-in-a-data-region"></a>Pour fusionner des cellules dans une région de données  
  
1.  Dans la région de données sur l'aire de conception du rapport, cliquez sur la première cellule à fusionner. Tout en maintenant le bouton gauche de la souris enfoncé, faites glisser verticalement ou horizontalement la souris pour sélectionner des cellules adjacentes. Les cellules sélectionnées sont mises en surbrillance.  
  
2.  Cliquez avec le bouton droit sur les cellules sélectionnées, puis sélectionnez **Fusionner les cellules**. Les cellules sélectionnées sont combinées en une seule cellule.  
  
3.  Répétez les étapes 1 et 2 pour fusionner d'autres cellules adjacentes dans une région de données.  
  
## <a name="see-also"></a>Voir aussi  
[Région de données de tableau matriciel](../../reporting-services/report-design/tablix-data-region-report-builder-and-ssrs.md)  
 [Tables &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/tables-report-builder-and-ssrs.md)   
 [Créer une matrice](../../reporting-services/report-design/create-a-matrix-report-builder-and-ssrs.md)   
 [Créer des factures et des formulaires avec des listes](../../reporting-services/report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)  
[Tables, matrices et listes &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  