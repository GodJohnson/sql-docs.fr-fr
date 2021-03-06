---
title: MSSQLSERVER_916 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 916 (Database Engine error)
ms.assetid: 73eb6581-99fe-49a5-9b42-e239d7ffe27f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: aeeda48970696fa3d2f1da22f9aa318910bd53dc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48213255"
---
# <a name="mssqlserver916"></a>MSSQLSERVER_916
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|916|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|NOTUSER|  
|Texte du message|Le principal de serveur « %.*ls » ne peut pas accéder à la base de données « %.\*ls » dans le contexte de sécurité actuel.|  
  
## <a name="explanation"></a>Explication  
 La connexion n'a pas les autorisations suffisantes pour se connecter à la base de données nommée. Les connexions qui peuvent se connecter à cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mais ne disposent pas d'autorisations spécifiques dans une base de données reçoivent les autorisations de l'utilisateur invité. Il s'agit d'une mesure de sécurité pour empêcher les utilisateurs d'une base de données de se connecter à d'autres bases de données où ils n'ont pas de privilèges. Ce message d'erreur peut se produire lorsque l'utilisateur invité n'a pas l'autorisation CONNECT à la base de données nommée et la propriété TRUSTWORTHY n'est pas définie. Ce message d'erreur peut se produire lorsque l'utilisateur invité n'a pas l'autorisation CONNECT à la base de données nommée.  
  
 Quand l’autorisation CONNECT à la base de données msdb est refusée ou révoquée, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] peut recevoir cette erreur quand l’Explorateur d’objets essaie d’afficher l’état de la gestion basée sur des stratégies de chaque base de données. L’Explorateur d’objets utilise les autorisations de la connexion actuelle pour interroger la base de données msdb afin d’obtenir ces informations, ce qui provoque l’erreur. Le message d'erreur suivant est également généré :  
  
 Échec de la récupération de données pour cette demande. (Microsoft.SqlServer.Management.Sdk.Sfc)  
  
## <a name="user-action"></a>Action de l'utilisateur  
  
> [!WARNING]  
>  Avant de contourner cette mesure de sécurité vous devez avoir une vision claire des utilisateurs authentifiés dans diverses bases de données. Les méthodes suivantes peuvent autoriser les utilisateurs qui ont des autorisations dans une base de données à se connecter à d'autres bases de données qui pourraient exposer des données à un utilisateur malveillant. Lorsque des bases de données autonomes sont activées, les étapes suivantes peuvent permettre à des propriétaires de base de données dans une base de données d'octroyer l'accès à une autre base de données sur l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Vous pouvez vous connecter à la base de données de l'une des manières suivantes :  
  
-   Accordez l'accès de connexion spécifique à la base de données nommée. Dans l'exemple ci-dessous, la connexion `Adventure-Works\Larry` se voit accorder l'accès à la base de données `msdb`.  
  
     USE msdb ;  
  
     GO  
  
     GRANT CONNECT TO [Adventure-Works\Larry] ;  
  
-   Accordez l'autorisation CONNECT à la base de données nommée dans le message d'erreur pour l'utilisateur invité. Dans l'exemple ci-dessous, l'autorisation `CONNECT` sur la base de données `msdb` est accordée à l'utilisateur `guest`.  
  
     USE msdb ;  
  
     GO  
  
     GRANT CONNECT TO guest ;  
  
-   Activez la propriété TRUSTWORTHY sur la base de données qui a authentifié l'utilisateur.  
  
     `ALTER DATABASE AdventureWorks SET TRUSTWORTHY ON;`  
  
  
