---
title: Changements de comportement apportés à SQL Server Reporting Services dans SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, backward compatibility
- rows [Reporting Services], heights
- leading blanks
- installing Reporting Services, behavior changes with release
- cryptography [Reporting Services]
- Setup [Reporting Services], behavior changes with release
- DefaultValueQueryBased property
- encryption [Reporting Services]
- decryption [Reporting Services]
- blank characters [SQL Server]
- initializing installations [Reporting Services]
- behavior changes [Reporting Services]
ms.assetid: 2a767f0f-84f2-4099-8784-1e37790f858e
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: a8533552a48acd695ca7216ba6881b33369d5b1c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48116371"
---
# <a name="behavior-changes-to-sql-server-reporting-services--in-sql-server-2014"></a>Changements de comportement apportés à SQL Server Reporting Services dans SQL Server 2014
  Cette rubrique décrit les changements de comportement dans [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Les modifications de comportement affectent le mode de fonctionnement ou d'interaction des fonctionnalités de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] par rapport aux versions précédentes de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 Dans cette rubrique :  
  
-   [SQL Server 2014 Reporting Services des changements de comportement](#bkmk_sql14)  
  
-   [SQL Server 2012 Reporting Services des changements de comportement](#bkmk_rc0)  
  
-   [SQL Server 2008 R2 Reporting Services des changements de comportement](#bkmk_kj)  
  
##  <a name="bkmk_sql14"></a> [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Changements de comportement Reporting Services  
 Il y a aucune [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] changements de comportement dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
##  <a name="bkmk_rc0"></a> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Changements de comportement Reporting Services  
 Cette section décrit les changements de comportement en mode [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint.  
  
### <a name="view-items-permission-will-not-download-shared-datasets-sharepoint-mode"></a>L'autorisation d'afficher les éléments ne télécharge pas les datasets partagés (mode SharePoint)  
 **Nouveau comportement :** Les utilisateurs disposant de l'autorisation SharePoint « Afficher les éléments » ne peuvent plus télécharger le contenu des datasets partagés Reporting Services. Ce changement de comportement est maintenant compatible avec les autorisations « Afficher les éléments » pour les rapports, les sources de données et les modèles. Les utilisateurs disposant de l'autorisation « Afficher les éléments » peuvent afficher et exécuter des rapports, des sources de données et des modèles, mais ils ne peuvent pas télécharger leur contenu.  
  
 **Comportement précédent :** Les utilisateurs disposant de l'autorisation SharePoint « Afficher les éléments » peuvent télécharger le contenu des datasets partagés Reporting Services.  
  
 Pour plus d'informations sur les niveaux d'autorisation SharePoint, consultez [Autorisations utilisateur et niveaux d'autorisation](http://technet.microsoft.com/library/cc721640.aspx)  
  
### <a name="report-server-trace-logs-are-in-a-new-location-for-sharepoint-mode-sharepoint-mode"></a>Les journaux de trace du serveur de rapports sont dans un nouvel emplacement en mode SharePoint (mode SharePoint)  
 **Nouveau comportement :** Pour un serveur de rapports installé en mode SharePoint, les journaux de trace du serveur de rapports se trouvent sous le dossier %Programfiles%\Common Files\Microsoft Shared\Web Server Extensions\14\Web Services\ReportServer\LogFiles.  
  
 **Comportement précédent :** journaux de trace de serveur de rapports se trouvaient sous un chemin d’accès semblable au suivant : %Programfilesdir%\Microsoft SQL Server\\< RS_instance > \Reporting Services\LogFiles  
  
### <a name="getserverconfiginfo-soap-api-is-no-longer-supported-sharepoint-mode"></a>L'API SOAP GetServerConfigInfo n'est plus prise en charge (mode SharePoint)  
 **Nouveau comportement**: Applets de commande PowerShell « Get-SPRSServiceApplicationServers »  
  
 **Comportement précédent :** les clients peuvent développer le code client SOAP pour communiquer directement avec le [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] point de terminaison et appeler GetReportServerConfigInfo().  
  
### <a name="report-server-configuration-and-management-tools"></a>Configuration de Report Server et Outils d'administration  
  
#### <a name="configuration-manager-is-not-used-for-sharepoint-mode"></a>Le gestionnaire de configuration n'est pas utilisé pour le mode SharePoint  
 **Nouveau comportement :** le [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Configuration Manager prend en charge n’est plus les serveurs de rapports en SharePoint Mode. Configuration de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] mode SharePoint peut maintenant être réalisée à l’aide de l’administration centrale de SharePoint et par conséquent [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Configuration Manager ne gère plus le mode SharePoint. Le gestionnaire de configuration est maintenant utilisé uniquement pour les serveurs de rapports en mode natif.  
  
#### <a name="you-cannot-change-the-server-from-one-mode-to-another"></a>Vous ne pouvez pas modifier le serveur d'un mode en un autre.  
 **Nouveau comportement :** Vous ne pouvez pas modifier les modes serveur. Si vous installez un serveur de rapports en mode natif, vous ne pouvez pas le reconfigurer ou le modifier en mode SharePoint. Si vous l'installez en mode SharePoint, vous pouvez modifier le serveur de rapports en mode natif.  
  
 **Comportement précédent :** client installe un [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] serveur de rapports en mode SharePoint. Si le client souhaite configurer le serveur de rapports en mode natif, il peut ouvrir le gestionnaire de configuration [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pour passer en mode natif en créant une base de données ou en se connectant à une base de données existante en mode natif. Le client peut également utiliser [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Configuration Manager pour passer du mode SharePoint en mode natif.  
  
##  <a name="bkmk_kj"></a> SQL Server 2008 R2 Reporting Services des changements de comportement  
 Cette section décrit les changements de comportement dans [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
> [!NOTE]  
>  SQL Server 2008 R2 étant une mise à niveau de version secondaire de SQL Server 2008, nous vous recommandons d'examiner également le contenu de la section SQL Server 2008.  
  
### <a name="secureconnectionlevel-property-in-the-reporting-services-wmi-provider-library"></a>Propriété SecureConnectionLevel dans la bibliothèque du fournisseur WMI de Reporting Services  
 Dans la bibliothèque du fournisseur WMI pour [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], le **SecureConnectionLevel** autorisant les valeurs de propriété `0`,`1`,`2`,`3`, avec `0` qui indique que la couche SSL (Secure Socket) n’est pas requis pour une des méthodes de service Web, `3` indiquant que SSL est requis pour toutes les méthodes de service Web, et `1` et `2` indiquer des sous-ensembles de méthodes de service Web qui exiger le protocole SSL. Dans [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], ces valeurs ont deux significations possibles uniquement :  
  
-   `0` indique que le protocole SSL n'est pas obligatoire pour les méthodes de service Web.  
  
-   Un entier positif indique que le protocole SSL est obligatoire pour toutes les méthodes de service Web.  
  
 Cette modification affecte la manière dont le serveur de rapports répond aux appels de service Web. Par exemple, <xref:ReportService2005.ReportingService2005.ListSecureMethods%2A> ne retourne rien maintenant si **SecureConnectionLevel** est définie sur 0 et toutes les méthodes dans <xref:ReportService2005.ReportingService2005> si **SecureConnectionLevel** a la valeur `1`, `2`, ou `3`.  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles sont les nouveautés &#40;Reporting Services&#41;](what-s-new-reporting-services.md)   
 [Fonctionnalités déconseillées dans SQL Server Reporting Services dans SQL Server 2014](deprecated-features-in-sql-server-reporting-services-ssrs.md)   
 [Fonctionnalités supprimées de SQL Server Reporting Services dans SQL Server 2014](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)   
 [Modifications importantes de SQL Server Reporting Services dans SQL Server 2014](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md)  
  
  
