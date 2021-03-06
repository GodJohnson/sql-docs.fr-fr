---
title: Comprendre la gestion des fenêtres dans SQL Server Management Studio | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- autohide [SQL Server Management Studio]
- SQL Server Management Studio [SQL Server], tool windows
- push pin [SQL Server Management Studio]
- tool windows [SQL Server Management Studio]
ms.assetid: bebf8383-dcaf-466e-84f5-63b81c9cfe52
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7c63e159490e462a3598b3a19a4f51f900ef3485
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48097759"
---
# <a name="understand-sql-server-management-studio-windows-management"></a>Comprendre la gestion des fenêtres dans SQL Server Management Studio
  Les fenêtres Outil de [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] forment un système très fonctionnel, souple et efficace qui vous permet d’effectuer les tâches suivantes :  
  
-   optimiser l'espace de travail utilisateur pour le développement et la gestion ;  
  
-   réduire le nombre de fenêtres inutilisées, affichées en même temps ;  
  
-   personnaliser facilement l'environnement utilisateur.  
  
 La manipulation des fenêtres joue un rôle essentiel dans l'environnement [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] . Les utilisateurs peuvent accéder facilement aux outils et fenêtres qu'ils utilisent fréquemment. Ils peuvent en outre choisir la quantité d'espace à allouer aux différentes informations, et l'environnement optimise l'espace disponible afin de modifier les requêtes en conséquence. Les fenêtres peuvent être déplacées vers différents endroits de l'écran. Il est également possible d'annuler l'ancrage et de déplacer de nombreuses fenêtres hors du cadre de [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] . Cette possibilité s'avère particulièrement utile lorsque plusieurs moniteurs sont utilisés.  
  
 Vous pouvez agrandir votre espace d'édition et conserver les mêmes fonctionnalités grâce à l'option Masquer automatiquement, disponible dans toutes les fenêtres. Cette option permet d'afficher les fenêtres sous forme d'onglets dans une barre située en bordure de l'environnement [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] principal. Lorsque le pointeur est placé sur un de ces onglets, la fenêtre sous-jacente s'affiche. Vous pouvez activer ou désactiver l’option Masquer automatiquement d’une fenêtre en cliquant sur le bouton **Masquer automatiquement** , qui est représenté sous forme de punaise dans l’angle supérieur droit de la fenêtre. Le menu **Fenêtre** contient également l’option **Masquer tout automatiquement** .  
  
 Certains composants peuvent être configurés en mode avec onglet (les composants s'affichent sous forme d'onglets dans le même emplacement d'ancrage) ou en mode MDI (chaque document possède sa propre fenêtre). Pour configurer cette fonctionnalité, dans le menu **Outils** , cliquez sur **Options**, sur **Environnement**, puis sur **Général**.  
  
> [!IMPORTANT]  
>  Lorsqu'un compte de connexion (ou un utilisateur de base de données autonome) se connecte et est authentifié, la connexion stocke les informations d'identité sur la connexion. Dans le cas d'une connexion d'authentification Windows, ces informations incluent des données sur l'appartenance aux groupes Windows. L'identité de la connexion reste authentifiée tant que la connexion est conservée. Pour imposer des modifications d'identité, une réinitialisation du mot de passe, par exemple, ou la modification de l'appartenance au groupe Windows, le compte de connexion doit fermer une session de l'autorité d'authentification (Windows ou [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]) et ouvrir une nouvelle session. Un membre du rôle serveur fixe **sysadmin** ou tout compte de connexion doté de l’autorisation **ALTER ANY CONNECTION** peut utiliser la commande **KILL** pour mettre fin à une connexion et obliger le compte de connexion à se reconnecter. [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] peut réutiliser les informations de connexion lors de l’ouverture de plusieurs connexions dans les fenêtres de l’Explorateur d’objets et de l’éditeur de requête. Fermez toutes les connexions pour imposer une reconnexion.  
  
> [!IMPORTANT]  
>  Lorsqu'un compte de connexion (ou un utilisateur de base de données autonome) se connecte et est authentifié, la connexion met en cache les informations d'identité sur la connexion. Dans le cas d'une connexion d'authentification Windows, ces informations incluent des données sur l'appartenance aux groupes Windows. L'identité de la connexion reste authentifiée tant que la connexion est conservée. Pour imposer des modifications d'identité, une réinitialisation du mot de passe, par exemple, ou la modification de l'appartenance au groupe Windows, le compte de connexion doit fermer une session de l'autorité d'authentification (Windows ou [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]) et ouvrir une nouvelle session. Un membre du rôle serveur fixe **sysadmin** ou tout compte de connexion doté de l’autorisation **ALTER ANY CONNECTION** peut utiliser la commande **KILL** pour mettre fin à une connexion et obliger le compte de connexion à se reconnecter. [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] peut réutiliser les informations de connexion lors de l’ouverture de plusieurs connexions dans les fenêtres de l’Explorateur d’objets et de l’éditeur de requête. Fermez toutes les connexions pour imposer une reconnexion.  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser SQL Server Management Studio](../database-engine/use-sql-server-management-studio.md)   
 [Environnement SQL Server Management Studio](the-sql-server-management-studio-environment.md)  
  
  
