---
title: Définir les options d’une étape de travail Transact-SQL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL job step
- job steps [Transact-SQL]
- SQL Server Agent jobs, Transact-SQL step
ms.assetid: b2a47057-f6fb-432b-a7b6-5d61f33a5d9c
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 04d73a9a17b3ec8c99aa5c97db98913b6009700b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47855757"
---
# <a name="define-transact-sql-job-step-options"></a>Définir les options d'une étape de travail Transact-SQL
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Cette rubrique explique comment définir les options pour les étapes de travail [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  [!INCLUDE[tsql](../../includes/tsql-md.md)] Agent dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de SQL Server Management Objects.  
  
**Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
    [Sécurité](#Security)  
  
-   **Pour définir les options d'une étape de travail Transact-SQL, avec :** ,  
  
    [SQL Server Management Studio](#SSMS)  
  
    [SQL Server Management Objects](#SMO)  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Security"></a>Sécurité  
Pour plus d'informations, consultez [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-define-transact-sql-job-step-options"></a>Pour définir les options d'une étape de travail Transact-SQL  
  
1.  Dans **l'Explorateur d'objets**, développez **Agent SQL Server**, développez **Travaux**, cliquez avec le bouton droit sur le travail que vous voulez modifier, puis cliquez sur **Propriétés**.  
  
2.  Cliquez successivement sur la page **Étapes** , sur une étape de travail et sur **Modifier**.  
  
3.  Dans la boîte de dialogue **Propriétés de l'étape de travail** , confirmez le type de travail **Script Transact-SQL (TSQL)**, puis sélectionnez la page **Avancé** .  
  
4.  Définissez l'action à exécuter si le travail aboutit en sélectionnant l'option appropriée dans la liste **Action en cas de succès** .  
  
5.  Définissez le nombre de tentatives en entrant un nombre compris entre 0 et 9999 dans la zone **Tentatives de reprises** .  
  
6.  Définissez une fréquence de tentative en entrant un nombre de minutes compris entre 0 et 9999 dans la zone **Intervalle de reprise** .  
  
7.  Définissez l'action à exécuter si le travail échoue en sélectionnant l'option appropriée dans la liste **Action en cas d'échec** .  
  
8.  Si le travail est un script [!INCLUDE[tsql](../../includes/tsql-md.md)] , vous pouvez choisir les options suivantes :  
  
    -   Entrez le nom d'un **fichier de sortie**. Par défaut, les données du fichier sont remplacées chaque fois que l'étape de travail s'exécute. Si vous ne voulez pas remplacer les données, activez **Ajouter la sortie au fichier existant**. Cette option est uniquement disponible pour les membres du rôle de serveur fixe **sysadmin** . Notez que [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ne permet pas aux utilisateurs d'afficher les fichiers arbitraires dans le système de fichiers. Vous ne pouvez donc pas utiliser [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] pour afficher les journaux d'étape de travail écrits dans le système de fichiers.  
  
    -   Activez **Enregistrer un journal dans la table** pour enregistrer l'étape de travail dans une table de base de données. Par défaut, le contenu de la table est remplacé chaque fois que l'étape de travail s'exécute. Si vous ne voulez pas remplacer les données, activez **Ajouter la sortie à l'entrée existante dans la table**. Une fois l'étape de travail exécutée, vous pouvez afficher le contenu de la table en cliquant sur **Afficher**.  
  
    -   Activez **Inclure la sortie de l'étape dans l'historique** pour inclure la sortie dans l'historique de l'étape. Le résultat ne sera affiché que s'il n'y a pas d'erreur. De même, le résultat peut être tronqué.  
  
9. Si vous êtes membre du rôle de serveur fixe **sysadmin** et voulez exécuter cette étape de travail avec une connexion SQL différente, sélectionnez la connexion SQL dans la liste **Exécuter en tant qu'utilisateur** .  
  
## <a name="SMO"></a>Utilisation de SQL Server Management Objects  
**Pour définir les options d'une étape de travail Transact-SQL**  
  
Utilisez la classe **JobStep** à l’aide du langage de programmation de votre choix, tel que Visual Basic, Visual C# ou PowerShell.  
  
