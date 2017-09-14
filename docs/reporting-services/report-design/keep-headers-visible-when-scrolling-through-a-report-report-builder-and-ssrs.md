---
title: "Laisser les en-têtes visibles lors du défilement d’un rapport (Générateur de rapports et SSRS) | Documents Microsoft"
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
ms.assetid: 6d9192a4-fd5c-41ad-b9ef-f88f9496afed
caps.latest.revision: 10
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f2fac57fe0e898a1ccbfbe33fb271eae76da1389
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="keep-headers-visible-when-scrolling-through-a-report-report-builder-and-ssrs"></a>Laisser les en-têtes visibles lors du défilement d'un rapport (Générateur de rapports et SSRS)
  Pour empêcher les étiquettes de lignes et de colonnes de disparaître de l'écran après le rendu d'un rapport, vous pouvez figer les en-têtes de lignes ou de colonnes.  
  
 La façon de contrôler les lignes et les colonnes varie selon que vous disposez d'une table ou d'une matrice. Si vous avez une table, vous configurez les membres statiques (en-têtes de colonnes et de lignes) pour qu'ils restent visibles. Si vous avez une matrice, vous configurez les en-têtes de groupes de colonnes et de lignes pour qu'ils restent visibles.  
  
 Si vous exportez le rapport vers Excel, l'en-tête ne sera pas automatiquement figé. Vous pouvez figer le volet dans Excel. Pour plus d’informations, consultez la **en-têtes et pieds de page** section [exportation vers Microsoft Excel &#40; Le Générateur de rapports et SSRS &#41; ](../../reporting-services/report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  Même si une table possède des groupes de lignes et de colonnes, vous ne pouvez pas conserver ces en-têtes de groupes visibles pendant le défilement  
  
 L'image suivante illustre une table.  
  
 ![Table](../../reporting-services/report-design/media/table.png "Table")  
  
 L'image suivante illustre une matrice.  
  
 ![Matrice](../../reporting-services/report-design/media/matrix.png "matrice")  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-keep-matrix-group-headers-visible-while-scrolling"></a>Pour garder les en-têtes de groupes de matrice visibles pendant le défilement  
  
1.  Cliquez avec le bouton droit sur la ligne, la colonne ou la poignée d’angle d’une région de données de tableau matriciel, puis cliquez sur **Propriétés du tableau matriciel**.  
  
2.  Sous l'onglet **Général** , sous **En-têtes de lignes** ou **En-têtes de colonnes**, sélectionnez **L'en-tête doit rester visible pendant le défilement**.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-keep-a-static-tablix-member-row-or-column-visible-while-scrolling"></a>Pour laisser un membre de tableau matriciel statique (ligne ou colonne) visible pendant le défilement  
  
1.  Sur l'aire de conception, cliquez n'importe où dans la table pour afficher les membres statiques, ainsi que les groupes, dans le volet de regroupement.  
  
     ![Volet de regroupement](../../reporting-services/report-design/media/grouppane-updated.png "volet de regroupement")  
  
     Le volet Groupes de lignes affiche les membres statiques et dynamiques hiérarchiques pour la hiérarchie de groupes de lignes, et le volet Groupes de colonnes affiche une vue semblable pour la hiérarchie de groupes de colonnes.  
  
2.  Dans la partie droite du volet de regroupement, cliquez sur la flèche orientée vers le bas, puis sur **Mode avancé**.  
  
3.  Cliquez sur le membre statique (ligne ou colonne) que vous souhaitez laisser visible pendant le défilement. Le volet Propriétés affiche les propriétés du **membre du tableau matriciel** .  
  
     ![Propriétés de membre de tableau matriciel](../../reporting-services/report-design/media/grouppane-tablixmember-updated.png "propriétés de membre de tableau matriciel")  
  
4.  Dans le volet Propriétés, affectez à **FixedData** la valeur **True**.  
  
5.  Répétez cette étape pour tous les membres adjacents que vous souhaitez laisser visibles pendant le défilement.  
  
6.  Affichez l'aperçu du rapport.  
  
 Lorsque vous faites défiler un rapport verticalement ou horizontalement, les membres de tableau matriciel statiques restent visibles.  
  
## <a name="see-also"></a>Voir aussi  
 [Région de données de tableau matriciel &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/tablix-data-region-report-builder-and-ssrs.md)   
 [Recherche, affichage et la gestion des rapports &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [Exporter des rapports &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-builder/export-reports-report-builder-and-ssrs.md)   
 [Afficher des en-têtes et pieds de page avec un groupe &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/display-headers-and-footers-with-a-group-report-builder-and-ssrs.md)   
 [Afficher des en-têtes de ligne et colonne sur plusieurs Pages &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md)   
 [Volet de regroupement &#40; Le Générateur de rapports &#41;](../../reporting-services/report-design/grouping-pane-report-builder.md)  
  
  