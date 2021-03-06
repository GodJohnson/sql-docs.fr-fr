---
title: Boîte de dialogue Propriétés du projet | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.isprojectprop.general.f1
- sql12.ssis.ssms.isprojectprop.permissions.f1
ms.assetid: d5cf52f5-1fe2-438a-98a3-fe117360acf8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d657e1339f454045a4a1e536610a58cd27e94c8d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48054229"
---
# <a name="project-properties-dialog-box"></a>Propriétés du projet, boîte de dialogue
  Un projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est une unité de déploiement. Chaque projet peut contenir des packages, des paramètres et des références d'environnement. Un projet est un objet sécurisable et peut définir des autorisations pour les principaux de base de données. Quand un projet est redéployé, la version précédente du projet peut être stockée dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Les paramètres du projet et les paramètres du package peuvent être utilisés pour affecter des valeurs aux propriétés dans des packages au moment de l'exécution. Certains paramètres requièrent des valeurs avant que le package puisse être exécuté. Les valeurs de paramètre qui référencent des variables d'environnement requièrent que le projet utilise la référence d'environnement correspondante avant l'exécution.  
  
 **Que voulez-vous faire ?**  
  
-   [Ouvrir la boîte de dialogue Propriétés du projet](#open_dialog)  
  
-   [Définir les options sur la page Général](#general)  
  
-   [Définir les options sur la page Autorisations](#permissions)  
  
##  <a name="open_dialog"></a> Ouvrir la boîte de dialogue Propriétés du projet  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connectez-vous au serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
     Vous vous connectez à l'instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] qui héberge la base de données SSISDB.  
  
2.  Dans l'Explorateur d'objets, développez l'arborescence pour afficher le nœud **Integration Services Catalogues** .  
  
3.  Développez le nœud **SSISDB** .  
  
4.  Développez le dossier qui contient le projet dont vous souhaitez définir les propriétés.  
  
5.  Cliquez avec le bouton droit sur le projet, puis cliquez sur **Propriétés**.  
  
##  <a name="general"></a> Définir les options sur la page Général  
 Utilisez la page Général pour afficher les propriétés du projet.  
  
 **Nom**  
 Indique le nom du projet.  
  
 **Identificateur**  
 Indique l'ID de projet.  
  
 **Description**  
 Affiche la description facultative du projet.  
  
 **Version du projet**  
 Indique la version du projet.  
  
 **Date du déploiement**  
 Indique la date et l'heure auxquelles le projet a été déployé ou redéployé.  
  
##  <a name="permissions"></a> Définir les options sur la page Autorisations  
 Utilisez la page **Autorisations** pour afficher et définir les autorisations explicites du projet.  
  
 ...  
 Cliquez sur **Parcourir** pour sélectionner les utilisateurs et les rôles auxquels vous souhaitez affecter des autorisations à l’aide de la boîte de dialogue **Parcourir tous les principaux** .  
  
 **Nom**  
 Indique le nom de l'utilisateur ou du rôle.  
  
 **Type**  
 Indique le type d'utilisateur ou de rôle.  
  
 **Autorisation**  
 Indique les autorisations.  
  
 **Fournisseur d'autorisations**  
 Indique l'utilisateur ou le rôle qui accorde l'autorisation.  
  
 **Octroyer**  
 Si **Accorder** est sélectionné, l’autorisation est accordée à l’utilisateur ou au rôle sélectionné.  
  
 **Refuser**  
 Si **Refuser** est sélectionné, l’autorisation est refusée à l’utilisateur ou au rôle sélectionné.  
  
  
