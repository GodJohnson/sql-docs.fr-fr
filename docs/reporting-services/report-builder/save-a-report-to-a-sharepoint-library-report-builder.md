---
title: Enregistrer un rapport dans une bibliothèque SharePoint (Générateur de rapports) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-builder
ms.topic: conceptual
ms.assetid: 4daa1eee-78b7-43d0-8b22-4a98e8fa66ba
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 9cc5e2018c04b2124a879f4ec2e3d6b947d2f6d5
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52502004"
---
# <a name="save-a-report-to-a-sharepoint-library-report-builder"></a>Enregistrer un rapport dans une bibliothèque SharePoint (Générateur de rapports)
  Pour enregistrer un rapport sur un serveur de rapports configuré pour une intégration SharePoint, vous devez accéder au serveur SharePoint et établir une connexion au serveur de rapports. Dans la définition de rapport, toutes les références aux éléments associés au rapport doivent utiliser des valeurs spécifiques à un serveur de rapports SharePoint. Les éléments associés peuvent consister en des sous-rapports, des rapports d'extraction et des ressources telles que des images Web. Pour plus d’informations, consultez [Spécification de chemins d’accès à des éléments externes &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/specifying-paths-to-external-items-report-builder-and-ssrs.md).  
  
 Vous devez disposer de l’autorisation **Membre** ou **Propriétaire** sur le site SharePoint pour définir les propriétés du projet.  
  
### <a name="to-save-a-report-to-a-sharepoint-site"></a>Pour enregistrer un rapport sur un site SharePoint  
  
1.  À partir du bouton Générateur de rapports, cliquez sur **Enregistrer**. La boîte de dialogue **Enregistrer sous**_\<élément de rapport>_ s’affiche.  
  
    > [!NOTE]  
    >  Si vous réenregistrez un rapport, il est automatiquement stocké à son emplacement précédent. Utilisez l’option **Enregistrer sous** pour modifier l’emplacement.  
  
2.  Cliquez éventuellement sur **Sites et serveurs récents** pour afficher une liste de serveurs de rapports et de sites SharePoint récemment utilisés.  
  
3.  Accédez au site SharePoint, puis cliquez sur **Enregistrer**.  
  
    > [!NOTE]  
    >  Si vous n'enregistrez pas un rapport ayant subi des modifications dans un délai de 10 heures, il est déconnecté du serveur sans être enregistré. Dans ce cas, dans la barre d’état inférieure droite, cliquez sur **Déconnecter**, puis sur **Connecter**. Le serveur le plus récent figurera dans la liste des serveurs disponibles. Sélectionnez-le pour que le rapport soit à nouveau connecté.  
  
## <a name="see-also"></a> Voir aussi  
 [Recherche, affichage et gestion des rapports &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
