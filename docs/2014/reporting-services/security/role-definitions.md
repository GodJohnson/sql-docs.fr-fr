---
title: Définitions de rôles | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- roles [Reporting Services], creating
- roles [Reporting Services], security
- security [Reporting Services], role definitions
- role-based security [Reporting Services], role definitions
ms.assetid: d1b8dbf0-4462-402e-92dd-0e4835002b6e
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 18b5d73d3ec4a6bc77a249d66af9b6d22c4e6be1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48107099"
---
# <a name="role-definitions"></a>Définitions de rôles
  Dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], une ***définition de rôle* est une collection nommée de tâches définissant les opérations disponibles sur un serveur de rapports. Elle fournit les règles de sécurité appliquées par le serveur de rapports. Lorsqu'un utilisateur tente d'effectuer une tâche, telle que la publication d'un rapport, le serveur de rapports vérifie l'attribution de rôle de l'utilisateur afin de déterminer si la tâche est incluse dans sa définition de rôle. Si la tâche est incluse dans la définition de rôle, la requête est soumise.  
  
## <a name="using-roles-to-authorize-access-to-a-report-server"></a>Utilisation de rôles pour autoriser l'accès à un serveur de rapports  
 Un rôle devient opérationnel lorsqu'il est utilisé dans le cadre d'une attribution de rôle. Pour plus d’informations sur la façon dont les rôles fournissent la sécurité, consultez [attributions de rôles](role-assignments.md).  
  
## <a name="types-of-role-definitions"></a>Types de définitions de rôles  
 Il existe deux types de définitions de rôles : les définitions au niveau élément et les définitions au niveau système. Une *définition de rôle au niveau élément* décrit les tâches associées aux éléments qui sont stockés et gérés sur un serveur de rapports, comme des rapports, des dossiers et des modèles. Gérer les rapports, Afficher les dossiers et Gérer les abonnements individuels sont des exemples de tâches que vous pouvez inclure dans une définition de rôle au niveau élément. Une *définition de rôle système* inclut les tâches qui s’appliquent au site dans son ensemble. Afficher les propriétés du serveur de rapports est un exemple de tâche que vous pouvez inclure dans un rôle système.  
  
## <a name="predefined-roles"></a>Predefined Roles  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] comprend des rôles prédéfinis qui correspondent à différents niveaux d’interaction de l’utilisateur. Les rôles prédéfinis que vous pouvez utiliser sont répertoriés ci-dessous :  
  
-   Gestionnaire de contenu, Serveur de publication, Lecteur, Générateur de rapports et Mes rapports sont des définitions de rôles au niveau élément que vous pouvez utiliser lors de la création d'attributions de rôles pour accéder au contenu du serveur de rapports.  
  
-   Administrateur système et Utilisateur système sont des définitions de rôles au niveau système que vous pouvez utiliser pour autoriser l'accès aux opérations du site.  
  
 Pour plus d’informations, consultez [rôles prédéfinis](role-definitions-predefined-roles.md).  
  
## <a name="creating-a-role-definition"></a>Création d'une définition de rôle  
 Pour créer un rôle, vous utilisez Management Studio pour spécifier le nom du rôle et les tâches qu'il contient. Vous devez créer des définitions de rôles distinctes pour les tâches au niveau élément et au niveau système. Les rôles comprennent des tâches au niveau élément ou au niveau système, mais pas aux deux en même temps. La création d'une définition de rôle consiste à fournir un nom et à choisir un ensemble de tâches pour la définition. Pour créer une définition de rôle, vous devez être autorisé à effectuer cette opération. La tâche « Définir la sécurité pour des éléments individuels » procure ces autorisations. Par défaut, les administrateurs et les utilisateurs ayant le rôle prédéfini **Gestionnaire de contenu** peuvent effectuer cette tâche.  
  
 Un rôle doit avoir un nom unique. Pour être valide, la définition de rôle doit contenir au moins une tâche. Pour plus d’informations, consultez [tâches et autorisations](tasks-and-permissions.md).  
  
 Pour créer une définition de rôle, utilisez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Pour plus d’informations, consultez [créer, supprimer ou modifier un rôle &#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md).  
  
 Après avoir créé une définition de rôle, vous pouvez l'utiliser en la sélectionnant dans une attribution de rôle. Pour plus d’informations, consultez [Accorder à un utilisateur l’accès à un serveur de rapports &#40;Gestionnaire de rapports&#41;](grant-user-access-to-a-report-server.md).  
  
## <a name="customize-or-delete-a-role-definition"></a>Personnaliser ou supprimer une définition de rôle  
 Les rôles prédéfinis peuvent être modifiés ou remplacés par des rôles personnalisés. Pour modifier un rôle, vous ajoutez ou supprimez des tâches de la définition de rôle. Vous ne pouvez pas renommer un rôle. Toute modification d'une définition de rôle est immédiatement appliquée à toutes les attributions de rôles qui incluent cette définition de rôle.  
  
 Vous pouvez supprimer une définition de rôle si vous ne l'utilisez plus. Vous ne pouvez pas supprimer la définition de rôle qui est sélectionnée pour la fonctionnalité Mes Rapports tant que cette dernière est activée. Avant de pouvoir supprimer la définition de rôle utilisée pour Mes Rapports, vous devez désactiver la fonctionnalité ou sélectionner une autre définition de rôle à utiliser avec elle.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches et autorisations](tasks-and-permissions.md)   
 [Octroi d'autorisations sur un serveur de rapports en mode natif](granting-permissions-on-a-native-mode-report-server.md)   
 [Créer, supprimer ou modifier un rôle &#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md)   
 [Accorder à un utilisateur l’accès à un serveur de rapports &#40;Gestionnaire de rapports&#41;](grant-user-access-to-a-report-server.md)   
 [Modifier ou supprimer une affectation de rôle &#40;Gestionnaire de rapports&#41;](role-assignments-modify-or-delete.md)   
 [Définir des autorisations pour les éléments de serveur de rapports sur un Site SharePoint &#40;Reporting Services dans SharePoint Mode intégré&#41;](set-permissions-for-report-server-items-on-a-sharepoint-site.md)  
  
  
