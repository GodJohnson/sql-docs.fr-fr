---
title: Exploration d’un modèle de prévision | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- forecasting [data mining]
- mining models, viewing
- mining model, time series
- time series [data mining]
ms.assetid: ad35a528-1949-4048-8678-3b9760c1c88c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5176d4e40f0f99810a14ad5ce4298e3a7167d770
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48223199"
---
# <a name="browsing-a-forecasting-model"></a>Exploration d'un modèle de prévision
  Lorsque vous ouvrez un modèle de prévision à l’aide **Parcourir**, le modèle est affiché dans une visionneuse interactive semblable à la visionneuse de modèle de série de temps dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. La visionneuse permet d'explorer les tendances, de comparer les séries, de créer des prédictions et d'obtenir des informations sur le modèle et les données sous-jacentes.  
  
##  <a name="bkmk_Top"></a> Explorer le modèle  
 Le **Parcourir** visionneuse pour les modèles de prévision fournit une vue graphique, qui montre les tendances au fil du temps et vous permet de créer des prédictions et un modèle, qui représente la série chronologique en tant qu’un arbre de décision ou un arbre de régression.  
  
-   [Vue graphique](#bkmk_charts)  
  
-   [Vue du modèle](#bkmk_Model)  
  
 Pour faire des essais avec un modèle de prévision, vous pouvez utiliser les exemples de données sur l’onglet prévision de l’exemple de classeur de données et créez un modèle de série de temps avec le [Assistant prévision &#40;des compléments d’exploration de données pour Excel&#41; ](forecast-wizard-data-mining-add-ins-for-excel.md) dans le  **Exploration de données** ruban, ou [prévision &#40;Table Analysis Tools pour Excel&#41; ](forecast-table-analysis-tools-for-excel.md) dans le **analyser** ruban.  
  
###  <a name="bkmk_charts"></a> Graphique  
 Le **graphique** onglet affiche la tendance de votre série de données au fil du temps, avec les valeurs prévues. L'axe vertical du graphique représente les valeurs de la série et l'axe horizontal le temps.  
  
##### <a name="explore-the-forecasting-chart"></a>Explorer le graphique de prévision  
  
1.  Ce modèle contient plusieurs séries chronologiques, mais pour simplifier le graphique, affichez une seule ou quelques séries associées uniquement.  
  
     ![prédictions historiques dans le modèle de prévision](media/dm13-forecast-chart-historicpredictions.gif "prédictions historiques dans le modèle de prévision")  
  
     Utilisez ces cases à cocher pour sélectionner la prévision pour « North America » seulement, et uniquement pour « Sales Amount ».  
  
2.  Cliquez sur **étapes de prédiction** et tapez une nouvelle valeur pour contrôler les valeurs de combien de temps futures que vous souhaitez voir dans le graphique.  
  
     La valeur par défaut est 5.  
  
3.  Cliquez sur n’importe quel point dans la ligne, passé ou futur, pour voir les valeurs exactes de ce point dans le temps, affichées dans le **légende d’exploration de données**.  
  
4.  Le graphique affiche à la fois les données historiques et les données futures. Notez la ligne en pointillé, avec un arrière-plan ombré. Ces valeurs sont les prédictions futures, en fonction du modèle.  
  
     Les données historiques (que vous avez utilisées pour créer le modèle) sont affichées à gauche du graphique.  
  
5.  Sélectionnez le **afficher les prévisions historiques** option pour faire une idée de la stabilité de la série chronologique.  
  
     ![prévisions pour une série unique dans le modèle](media/dm13-forecast-chart-singleseries.gif "prévisions pour une série unique dans le modèle")  
  
     Les prédictions historiques sont des valeurs prédites en fonction de la série jusqu'à ce point précis, et sont comparées aux valeurs historiques effectives. Si la ligne en pointillé (avec les valeurs prédites) est très éloignée de la ligne continue (les valeurs effectives), cela indique que la première partie de la série ne prédit pas de façon précise les valeurs ultérieures. Vous avez peut être besoin de plus de données, ou bien cela peut simplement indiquer une volatilité dans le cycle.  
  
6.  Sélectionnez le **afficher les écarts** option pour afficher les barres d’erreur dans le graphique.  
  
     Les barres d'erreur vous permettent d'évaluer visuellement la variabilité des prédictions. La qualité des prédictions varie en fonction de vos données sources, mais en augmentant le nombre d'étapes de prédiction, vous devez constater une augmentation stable des déviations.  
  
 **Conseils**  
  
-   Pour afficher ou masquer la **légende d’exploration de données**, avec le bouton droit n’importe quel point dans le graphique.  
  
     Vous pouvez afficher une plage de temps spécifique en cliquant sur le graphique, en faisant glisser une plage de temps dans le graphique, puis en recliquant pour effectuer un zoom avant sur la plage sélectionnée.  
  
-   Pour obtenir une copie du graphique actuel, cliquez sur **copier dans Excel**, puis cliquez sur une feuille de calcul Excel. Un graphique est inséré sur la feuille avec toutes les options définies, y compris la légende.  
  
     Toutefois, ce graphique est statique afin que vous ne pouvez pas modifier la légende ou afficher les données sous-jacentes ; Si vous avez besoin d’une vue graphique plus interactive, utilisez le [visionneuses Visio](viewing-data-mining-models-in-visio-data-mining-add-ins.md).  
  
-   Cliquez sur **Abs** dans la barre de menus de visionneuse pour basculer entre des courbes absolues et relatives.  
  
     Cette option est utile si votre graphique contient plusieurs modèles, mais l'échelle des données pour chaque modèle est très différente.  
  
     Par exemple, si les boutiques de la région Pacifique sont récentes et les ventes sont faibles, et si les valeurs absolues sont utilisées, la ligne indiquant les ventes Pacifique peut paraître plate, ce qui rend difficile de suivre les changements effectifs par rapport à d'autres modèles pouvant être affichés à une échelle plus normale.  
  
     En basculant la vue pour utiliser des valeurs relatives, vous normalisez l'échelle des différents modèles et vous affichez les différences en pourcentage des modifications. Lorsque la modification est relative sur chaque modèle, tous les modèles peuvent être affichés dans le même graphique sans distorsion significative.  
  
 [Explorer le modèle](#bkmk_Top)  
  
###  <a name="bkmk_Model"></a> Modèle  
 Un modèle de prévision peut également être représenté sous la forme d'un arbre de décision, ou bien, si la série est principalement linéaire, sous la forme d'un modèle de régression.  
  
 Par exemple, dans ce modèle il y a une différence dans la formule de régression en fonction d'une certaine condition, par conséquent, l'arbre se ramifie en trois branches, chacune avec une formule de régression différente.  
  
 ![Filtrer une série unique dans le modèle de prévision](media/dm13-forecast-model-northamerica.gif "filtrer une série unique dans le modèle de prévision")  
  
##### <a name="explore-the-forecasting-model-as-a-tree"></a>Explorer le modèle de prévision sous forme d'arborescence  
  
1.  Cliquez sur le **arborescence** liste déroulante liste et choisissez un modèle à afficher.  
  
     Un arbre distinct ou un nœud de régression est affiché pour chaque attribut prédictible. Par exemple, si vos données comprennent les ventes pour l'Europe, l'Amérique du Nord et le Pacifique, il y aura trois modèles différents, un pour chaque série de données.  
  
2.  Faites glisser le **afficher le niveau** curseur pour filtrer des niveaux inférieurs de l’arborescence et vous concentrer sur les principaux fractionnements.  
  
3.  Cliquez sur chaque nœud pour afficher des statistiques descriptives dans le **légende d’exploration de données**.  
  
     Lorsque vous immobilisez la souris sur un nœud, une info-bulle affiche également les mêmes statistiques, ainsi que la formule complète décrivant le nœud.  
  
4.  Si vous souhaitez copier les informations contenues dans le **légende d’exploration de données**, avec le bouton droit le **légende d’exploration de données**, sélectionnez **copie**et cliquez à l’intérieur de votre feuille de calcul Excel. Le **copier dans Excel** option permet de copier le graphique, pas les statistiques.  
  
 [Explorer le modèle](#bkmk_Top)  
  
## <a name="see-also"></a>Voir aussi  
 [Exploration des modèles dans Excel &#40;compléments d’exploration de données SQL Server&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
