---
title: "Ouvrir un rapport mobile avec les paramètres de chaîne de requête spécifique | Documents Microsoft"
ms.custom: 
ms.date: 10/25/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4eeb3204-e207-4ac0-aff3-bfc4926e5754
caps.latest.revision: 5
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 959754e0eb23530cb168098e9404273af9f67bba
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="open-a-mobile-report-with-specific-query-string-parameters--reporting-services"></a>Ouvrir un rapport mobile avec les paramètres de chaîne de requête spécifique | Reporting Services
Si vous avez un rapport mobile [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] avec des paramètres et une source de données [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ou [!INCLUDE[ssASnoversion_md](../../includes/ssasnoversion-md.md)] , vous pouvez inclure des paramètres de chaîne de requête dans l’URL du rapport afin qu’il s’ouvre automatiquement avec les valeurs que vous avez spécifiées. 
1.  Créez un [rapport mobiles avec des paramètres](../../reporting-services/mobile-reports/add-parameters-to-a-mobile-report-reporting-services.md).

2. Ouvrez le rapport dans l’Éditeur de rapports mobiles et sélectionnez l’onglet Données. 

2. Recherchez le nom de l’ensemble de données sur l’onglet dans la partie inférieure du tableau, et le nom de champ souhaité. 
    
    ![mobile-report-publisher-parameter-data-view](../../reporting-services/mobile-reports/media/mobile-report-publisher-parameter-data-view.png)
    
2.  La syntaxe de l’URL dépend de votre source de données. 

     **Pour une source de données SQL Server Analysis Services**: générez une URL avec un paramètre de chaîne de requête dans ce format :

    `http://<servername>/reports/<report-folder-name>/<report-name>?<dataset-name>.<field-name>=<parameter-value>`

    Par exemple :
    
    `http://sampleserver/reports/adventureworks-reports/adventureworks-load-on-demand?TimeChartLoD.category=Clothing` 
    
     **Pour une source de données SQL Server**: le paramètre de chaîne de requête est presque identique, mais contient le symbole @ devant le nom du champ :

    `http://<servername>/reports/<report-folder-name>/<report-name>?<dataset-name>.@<field-name>=<parameter-value>`

    Par exemple :
    
      `http://sampleserver/reports/adventureworks-reports/adventureworks-load-on-demand?TimeChartLoD.@category=Clothing` 

    
3.  Cette URL ouvre le rapport sur le serveur, automatiquement filtrée sur la valeur de paramètre spécifiée.

    ![mobile-report-publisher-parameter-web-portal-view](../../reporting-services/mobile-reports/media/mobile-report-publisher-parameter-web-portal-view.png)

### <a name="see-also"></a>Voir aussi

[Ajouter des paramètres à un rapport mobile](../../reporting-services/mobile-reports/add-parameters-to-a-mobile-report-reporting-services.md)

