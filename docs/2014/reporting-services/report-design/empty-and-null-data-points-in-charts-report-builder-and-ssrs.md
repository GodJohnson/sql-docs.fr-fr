---
title: Points de données vides et Null dans les graphiques (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: faddd29d-4cc1-4c2c-8e29-d3d9918fe22a
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 6f6611271a6f8bc637e1fa0032d868a1347b5ef5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48082079"
---
# <a name="empty-and-null-data-points-in-charts-report-builder-and-ssrs"></a>Points de données vides et Null dans les graphiques (Générateur de rapports et SSRS)
  Si vous affichez des champs avec des valeurs vides ou Null dans votre graphique, l'aspect du graphique peut ne pas correspondre à vos attentes. Les graphiques traitent les valeurs vides différemment en fonction du type de graphique spécifié :  
  
-   Si le type de graphique est un type de graphique linéaire (graphique à barres, histogramme, graphique en nuage de points, graphique en courbes, graphique en aires, graphique d'étendue), les valeurs vides sont affichées sous forme d'espaces vides, ou « vides », dans le graphique. Si vous souhaitez spécifier des points vides, vous devez ajouter des espaces réservés à ces points. Pour plus d’informations, consultez [ajouter des Points vides au graphique &#40;Générateur de rapports et SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md).  
  
-   Si le graphique utilisé est un graphique linéaire contigu (graphique à aires, graphique à barres, histogramme, graphique en courbes, graphique à nuages de points), des points de données vides y sont ajoutés pour maintenir la continuité dans les séries.  
  
-   Si le graphique utilisé est un graphique non linéaire (polaire, à secteurs, en anneau, en entonnoir ou en pyramide), les valeurs vides n'y sont pas affichées.  
  
-   Dans les types de graphiques à base de formes, les valeurs Null sont omises.  
  
 Un exemple de graphique avec des points de données vides est disponible sous forme d'exemple de rapport. Pour plus d'informations sur le téléchargement de cet exemple de rapport et d'autres rapports, consultez [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Exemples de rapports du Générateur de rapports et du Concepteur de rapports](http://go.microsoft.com/fwlink/?LinkId=198283).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="removing-empty-or-null-values"></a>Suppression de valeurs vides ou Null  
 Pour éviter de masquer des données importantes, envisagez la suppression des valeurs vides de votre dataset. Pour filtrer les valeurs Null, vous pouvez utiliser la clause NOT IS NULL dans votre requête. Vous pouvez également ajouter une expression de filtrage qui spécifie que vous ne voulez afficher que les valeurs différentes de zéro. Pour plus d’informations, consultez [ajouter des filtres de Dataset, les filtres de régions de données et les filtres de groupe &#40;Générateur de rapports et SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md).  
  
## <a name="fields-with-no-values-in-a-chart"></a>Champs sans valeurs dans un graphique  
 Si un champ ne contient aucune valeur dans le dataset retourné, le graphique affiche un graphique vide sans point de données, mais le nom de la série (en général, le nom du champ) est ajouté en tant qu'élément de légende.  
  
 Ce comportement est différent du cas où il n'y a aucune ligne de données dans le dataset retourné, ce qui peut se produire lorsque le rapport est paramétré et que la valeur sélectionnée retourne un jeu de résultats vide. Si votre requête de dataset retourne zéro ligne de données, un message s'affiche au moment de l'exécution pour indiquer qu'aucune donnée ne peut être présentée. Vous pouvez personnaliser ce message en modifiant la légende NoDataMessage pour le rapport dans le volet **Propriétés** . Pour plus d’informations, consultez [Datasets incorporés dans les rapports et datasets partagés &#40;Générateur de rapports et SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Graphiques &#40;Générateur de rapports et SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Mise en forme d’un graphique &#40;Générateur de rapports et SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)   
 [Ajouter un graphique à un rapport &#40;Générateur de rapports et SSRS&#41;](add-a-chart-to-a-report-report-builder-and-ssrs.md)   
 [Résoudre les problèmes graphiques &#40;Générateur de rapports et SSRS&#41;](troubleshoot-charts-report-builder-and-ssrs.md)  
  
  
