---
title: "Leçon 1 : Création d’un projet Report Server (Reporting Services) | Documents Microsoft"
ms.custom: 
ms.date: 11/30/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: 675671ca-e6c9-48a2-82e9-386778f3a49f
caps.latest.revision: 57
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: bead48dd2f32047b2782a54204bf06a145a7d71d
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="lesson-1-creating-a-report-server-project-reporting-services"></a>Leçon 1 : Création d'un projet Report Server (Reporting Services)

 > Pour obtenir un contenu pour les versions précédentes de SQL Server, consultez [leçon 1 : création d’un projet de serveur de rapports (Reporting Services)](https://msdn.microsoft.com/en-US/library/ms167559(SQL.120).aspx).

Dans cette leçon, vous créez un *projet Report Server* et un fichier de *définition de rapport (.rdl)* dans [!INCLUDE[ssBIDevStudio_md](../includes/ssbidevstudio-md.md)] dans Visual Studio. 

Pour créer un rapport avec [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], vous avez d’abord besoin d’un projet Report Server où vous pouvez enregistrer votre fichier de définition de rapport (.rdl), ainsi que les autres fichiers de ressources dont vous avez besoin pour votre rapport. 

Dans les leçons suivantes, vous définissez une source de données pour votre rapport, un dataset et la mise en page du rapport. Quand vous exécutez le rapport, les données sont extraites et combinées avec la mise en page, puis restituées sur votre écran, à partir duquel vous pouvez les exporter, les imprimer ou les enregistrer.  
  
  
  
## <a name="to-create-a-report-server-project"></a>Pour créer un projet Report Server  
  
1.  Ouvrez [!INCLUDE[ssBIDevStudio_md](../includes/ssbidevstudio-md.md)].  
  
2.  Sur le **fichier** menu > **nouveau** > **projet**.  

    ![ssrs-ssdt-file-01-new-project](../reporting-services/media/ssrs-ssdt-file-01-new-project.png)
  
3.  Sous **Modèles** > **installés** > **Business Intelligence**, cliquez sur **Reporting Services**.

    ![ssrs-ssdt-01-new-rs-project](../reporting-services/media/ssrs-ssdt-01-new-rs-project.png)

5. Cliquez sur **Projet Report Server** ![ssrs_ssdt_report_server_project](../reporting-services/media/ssrs-ssdt-report-server-project.png). 

   >**Remarque**: Si vous ne voyez pas le **Business Intelligence** ou **projet Report Server** options, vous devez mettre à jour de SSDT avec les modèles Business Intelligence. Voir [Télécharger SSDT (SQL Server Data Tools)](https://msdn.microsoft.com/library/mt204009.aspx).  
  
5.  Dans la zone **Nom**, tapez **Didacticiel**.  

    Par défaut, il est créé dans votre dossier Visual Studio 2015\Project, dans un nouveau répertoire.
    
    ![ssrs-ssdt-01-solution-location](../reporting-services/media/ssrs-ssdt-01-solution-location.png)
  
6.  Cliquez sur **OK** pour créer le projet.  
  
    Le projet Didacticiel s’affiche dans l’Explorateur de solutions sur la droite.  
  
## <a name="to-create-a-new-report-definition-file"></a>Pour créer un nouveau fichier de définition de rapport  
  
1.  Dans le volet **Explorateur de solutions** , cliquez avec le bouton droit sur **Rapports** > **Ajouter** > **Nouvel élément**. 

    >**Conseil**: Si vous ne voyez pas le volet **Explorateur de solutions** , dans le menu **Affichage** , cliquez sur **Explorateur de solutions**. 

    ![ssrs_ssdt_add_report](../reporting-services/media/ssrs-ssdt-add-report.png)
  
2.  Dans la fenêtre **Ajouter un nouvel élément** , cliquez sur **Rapport** ![ssrs_ssdt_report](../reporting-services/media/ssrs-ssdt-report.png).  
  
3.  Dans la zone **Nom**, tapez **Sales Orders.rdl** , puis cliquez sur **Ajouter**.  
  
    Le Concepteur de rapports s'ouvre et affiche le nouveau fichier .rdl en mode Conception.  
    
    ![ssrs-ssdt-01-new-report-designer](../reporting-services/media/ssrs-ssdt-01-new-report-designer.png)
  
     Le Concepteur de rapports est un composant [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] qui s'exécute dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Il comporte deux vues : **Conception** et **Aperçu**. Cliquez sur chacun des onglets pour passer d'une vue à une autre.  
  
    Vous définissez vos données dans le volet **Données du rapport** . Vous définissez la mise en page de votre rapport en mode **Conception** . Vous pouvez exécuter le rapport et visualiser son aspect en mode **Aperçu** .  
  
## <a name="next-lesson"></a>Leçon suivante  
Vous avez créé avec succès un projet de rapport appelé « Didacticiel » et ajouté un fichier de définition de rapport (.rdl) au projet de rapport. Vous allez ensuite spécifier la source de données à utiliser pour le rapport. Consultez [leçon 2 : spécification des informations de connexion &#40; Reporting Services &#41; ](../reporting-services/lesson-2-specifying-connection-information-reporting-services.md).  
  
## <a name="see-also"></a>Voir aussi  
[Créer un rapport de tableau de base &#40;Didacticiel SSRS&#41;](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)  
  

