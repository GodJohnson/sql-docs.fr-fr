---
title: Exécutez le Conseiller de mise à niveau (Interface utilisateur) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor Report Viewer
- Upgrade Advisor [SQL Server], running
- launching Upgrade Advisor
- Upgrade Advisor Analysis Wizard
- starting Upgrade Advisor
- SQL Server Upgrade Advisor, running
ms.assetid: 7f47c9b3-88d3-43d6-837e-f157b49a55ac
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c402516980f5cf3e1790f8a5fa6d594c93b0e500
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48176105"
---
# <a name="running-upgrade-advisor-user-interface"></a>Exécution du Conseiller de mise à niveau (interface utilisateur)
  Vous pouvez exécuter le Conseiller de mise à niveau pour analyser des composants locaux ou distants à tout moment pendant la planification de la mise à niveau. Conseiller de mise à niveau génère un rapport pour chaque composant et l’instance qui est analysé.  
  
> [!IMPORTANT]  
>  Le Conseiller de mise à niveau n'analyse pas les instances distantes de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Pour analyser une instance de [!INCLUDE[ssRS](../../includes/ssrs.md)], le Conseiller de mise à niveau doit être installé sur l'ordinateur sur lequel [!INCLUDE[ssRS](../../includes/ssrs.md)] est installé.  
>   
>  Pour analyser les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Integration Services, vous devez disposer du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] installé et [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installé sur le même ordinateur.  
  
## <a name="running-the-upgrade-advisor-analysis-wizard"></a>L’Assistant analyse du Conseiller de mise à niveau en cours d’exécution  
 L’Assistant analyse du Conseiller de mise à niveau en cours d’exécution comporte six étapes :  
  
1.  Lancer l'Assistant à partir de la page de démarrage du Conseiller de mise à niveau.  
  
2.  Identifier le serveur et les composants à analyser.  
  
3.  Rassembler des informations d'authentification.  
  
4.  Rassembler des paramètres supplémentaires selon le type de composant.  
  
5.  Analyser les composants sélectionnés.  
  
6.  Générer un rapport sur les problèmes de mise à niveau.  
  
 Pour plus d’informations sur l’Assistant analyse du Conseiller de mise à niveau, consultez [Comment : exécuter l’Assistant analyse du Conseiller de mise à niveau](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md).  
  
 Pour plus d’informations spécifiques qui est requis pour chaque étape, consultez [sur l’Interface utilisateur Conseiller de mise à niveau](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md).  
  
## <a name="running-the-upgrade-advisor-report-viewer"></a>La visionneuse de rapports du Conseiller de mise à niveau en cours d’exécution  
 Vous utilisez la visionneuse de rapports de conseiller de mise à niveau pour afficher les rapports générés par l’Assistant analyse du Conseiller de mise à niveau. Une fois le rapport chargé, vous pouvez filtrer les composants du rapport en fonction des critères suivants :  
  
-   Tous les problèmes  
  
-   Tous les problèmes de mise à niveau  
  
-   Problèmes de pré-mise à niveau  
  
-   Tous les problèmes de migration  
  
-   Problèmes résolus  
  
-   Problèmes non résolus  
  
 Pour obtenir des instructions pas à pas sur l'utilisation de la visionneuse de rapports, consultez les rubriques suivantes :  
  
-   [Guide pratique pour afficher un rapport du Conseiller de mise à niveau](../../../2014/sql-server/install/how-to-view-an-upgrade-advisor-report.md)  
  
-   [Guide pratique pour filtrer des rapports](../../../2014/sql-server/install/how-to-filter-reports.md)  
  
-   [Guide pratique pour exporter des rapports](../../../2014/sql-server/install/how-to-export-reports.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : exécuter l’Assistant analyse du Conseiller de mise à niveau](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md)   
 [Référence de l’Interface utilisateur Conseiller de mise à niveau](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)   
 [Résolution des problèmes de mise à niveau](../../../2014/sql-server/install/resolving-upgrade-issues.md)   
 [Utilisation du Conseiller de mise à niveau](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
