---
title: Ajouter une image externe (Générateur de rapports et SSRS) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 81fd4a1f-79a9-4967-86d6-6229413c0995
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: c42c413e235abd758d51a76b1726e0c35e3ff758
ms.sourcegitcommit: 9ece10c2970a4f0812647149d3de2c6b75713e14
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51812292"
---
# <a name="add-an-external-image-report-builder-and-ssrs"></a>Ajouter une image externe (Générateur de rapports et SSRS)
  Les images externes peuvent se trouver sur un serveur de rapports en mode natif ou en mode intégré SharePoint, ou sur un autre site Web. Lorsque vous incluez des images externes dans votre rapport, vous devez vous assurer que l'image existe et que le lecteur du rapport a les autorisations nécessaires pour y accéder. Pour plus d’informations, consultez [Images &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/images-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-an-external-image"></a>Pour ajouter une image externe  
  
1.  En mode de conception de rapport, sous l’onglet **Insérer** , cliquez sur **Image**.  
  
2.  Cliquez sur l'aire de conception, puis faites glisser la souris pour créer une zone de la taille voulue pour l'image.  
  
3.  Sous l’onglet **Général** de la boîte de dialogue **Propriétés de l’image** , tapez un nom dans la zone de texte **Nom** ou acceptez le nom par défaut.  
  
4.  (Facultatif) Dans la zone de texte **Info-bulle** , tapez le texte à afficher quand l’utilisateur pointe sur l’image dans un rapport rendu au format HTML.  
  
5.  Dans **Sélectionner la source de l’image**, sélectionnez **Externe**.  
  
     Pour une image située sur un serveur de rapports en mode natif, tapez le chemin d’accès relatif de l’image dans la zone **Utiliser cette image** , par exemple ../images/image1.jpg.  
  
     Pour une image située sur un serveur de rapports en mode intégré SharePoint, ou sur un autre site web, tapez une URL complète pointant vers l’image dans la zone **Utiliser cette image**, par exemple https://\<nom_serveur_SharePoint>/\<site>/Documents/images/image1.jpg.  
  
     Pour plus d’informations, consultez [Spécification de chemins d’accès à des éléments externes &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/specifying-paths-to-external-items-report-builder-and-ssrs.md).  
  
6.  (Facultatif) Cliquez sur **Taille**, **Visibilité**, **Action**ou **Bordure** pour définir des propriétés supplémentaires pour l’élément de rapport de type image.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a> Voir aussi  
 [Incorporer une image dans un rapport &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/embed-an-image-in-a-report-report-builder-and-ssrs.md)   
 [Ajouter une image d’arrière-plan &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/add-a-background-image-report-builder-and-ssrs.md)   
 [Boîte de dialogue Propriétés de l’image, Général &#40;Générateur de rapports et SSRS&#41;](https://msdn.microsoft.com/library/c2218b93-f7fe-46ef-995f-d7dadf9752ec)  
  
  
