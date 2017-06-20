---
title: "Choix entre l’accès URL et SOAP | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- SOAP [Reporting Services], vs. URL access
- Report Server Web service, application integration
- URL access [Reporting Services], vs. SOAP
- Web service [Reporting Services], application integration
ms.assetid: bccdc243-4366-4ce5-8e63-3dd6c463fa52
caps.latest.revision: 40
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 6837170f3ebe0e92e7914c3f0f863aa9534e0cb8
ms.contentlocale: fr-fr
ms.lasthandoff: 06/13/2017

---
# <a name="choosing-between-url-access-and-soap"></a>Choix entre l'accès URL et SOAP
  L'intégration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans des applications personnalisées peut s'avérer difficile. Toutefois, la difficulté ne se trouve pas dans la complexité du modèle de programmation ou les API, mais dans les nombreuses méthodes possibles pour l'intégrer. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] a été conçu dès le départ comme une plate-forme de développeur, et en tant que tel, a été créé avec une flexibilité de la programmation à l'esprit. Avec la flexibilité apparaît le besoin de prendre des décisions importantes concernant l'intégration de la navigation entre les rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et les fonctionnalités de gestion dans vos applications de gestion existantes.  
  
 ![Scénarios de programmation de Reporting Services](../../reporting-services/application-integration/media/bk-ext-04.gif "Reporting Services programming scenarios")  
La programmation de Reporting Services prend en charge un large éventail de scénarios.  
  
 Il existe deux manières d'intégrer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans des applications personnalisées : l'accès URL et l'API SOAP de Reporting Services. Celle à utiliser dépend de plusieurs facteurs. Dans certains cas, l'intégration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans vos applications de gestion personnalisées nécessite que vous utilisiez à la fois l'accès URL et SOAP. Vous devez vous poser les questions suivantes :  
  
-   De quel type de fonctionnalités de création de rapports d'entreprise vos utilisateurs finals et vous avez-vous besoin ? Avez-vous besoin d'une manière simple de générer et parcourir des rapports ou de fonctionnalités de gestion de serveur de rapports plus avancées dans votre solution d'entreprise personnalisée ?  
  
-   Dans quel type d'environnement vos utilisateurs travaillent-ils habituellement ? Votre application d'entreprise est-elle une application Web ou une application Windows ? Vos utilisateurs finals peuvent-ils parvenir facilement à basculer d'un environnement Win32 vers un environnement Web ? De quel type de contrôle avez-vous besoin sur l'environnement dans lequel les rapports sont exécutés et gérés ?  
  
 Une fois que vous avez répondu aux questions précédentes, vous pouvez déterminer comment intégrer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans votre infrastructure informatique. En général, l'accès URL est préféré pour consulter et parcourir des rapports individuels. L'accès URL vous permet de parcourir librement et rapidement des rapports sans le traitement du service Web. De plus, l'accès URL est actuellement la seule technique de programmation qui utilise la Visionneuse HTML complète pour la navigation entre les rapports, laquelle inclut la barre d'outils Rapports. En outre, l'accès URL est plus performant que SOAP parce qu'il ignore le marshaling des demandes SOAP vers et depuis le serveur. Dans les scénarios d'intégration qui requièrent un accès rapide et facile aux rapports avec des outils intégrés pour la consultation et la navigation, l'accès URL constitue le meilleur choix.  
  
> [!NOTE]  
>  L'accès URL du serveur de rapports prend en charge la Visionneuse HTML et les fonctionnalités étendues de la barre d'outils Rapports. L'API SOAP ne prend pas en charge ce type de rapport rendu. Vous devez concevoir et développer votre propre barre d'outils Rapports, si vous effectuez le rendu des rapports à l'aide de SOAP.  
  
 Pour plus d’informations sur la barre d’outils rapport, consultez [visionneuse HTML et la barre d’outils rapport](../../reporting-services/html-viewer-and-the-report-toolbar.md).  
  
 Pour plus d’informations sur l’accès URL, consultez [accès URL &#40; SSRS &#41; ](../../reporting-services/url-access-ssrs.md).  
  
 L'accès URL s'avère utile pour consulter des rapports, mais il ne fournit pas de fonctionnalités de gestion de rapports et d'espaces de noms, lesquelles peuvent s'avérer essentielles à tout scénario de création de rapports d'entreprise. Dans ce cas, les riches fonctionnalités générales de l'API SOAP de Reporting Services sont recommandées. Avec l'API SOAP, vous pouvez gérer et déployer des rapports, créer des planifications, configurer des propriétés de serveur, gérer l'espace de noms du serveur de rapports, créer des abonnements, etc. L'API SOAP présente le jeu complet de fonctionnalités de gestion dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. L'API SOAP peut également permettre de consulter et de parcourir des rapports via la méthode <xref:ReportExecution2005.ReportExecutionService.Render%2A> de l'API. Toutefois, la consultation de rapports via l'API SOAP n'active pas les fonctionnalités d'affichage intégrées de la barre d'outils Rapports et ne gère pas automatiquement l'interactivité des rapports que l'accès URL fournit.  
  
 Pour plus d’informations sur l’API SOAP de Reporting Services, consultez [Service Web Report Server](../../reporting-services/report-server-web-service/report-server-web-service.md).  
  
 Dans la majorité des cas, l'accès URL et les appels SOAP sont requis pour satisfaire vos besoins de création de rapports. SOAP est utilisé lors de la connexion initiale à la base de données du serveur de rapports et lors de la présentation de la liste de rapports disponible dans une interface utilisateur tandis que l'accès URL est utilisé pour accéder réellement aux rapports individuels et les parcourir.  
  
 Pour obtenir un exemple de combinaison de l’accès URL et le service Web pour fournir des rapports intégrés, consultez [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Voir aussi  
 [Intégration de Reporting Services dans des Applications](../../reporting-services/application-integration/integrating-reporting-services-into-applications.md)   
 [Intégration de Reporting Services à l’aide de SOAP](../../reporting-services/application-integration/integrating-reporting-services-using-soap.md)   
 [Intégration de Reporting Services à l’aide de l’accès URL](../../reporting-services/application-integration/integrating-reporting-services-using-url-access.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../../reporting-services/technical-reference-ssrs.md)  
  
  