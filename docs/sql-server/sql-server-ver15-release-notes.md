---
title: Notes de publication de SQL Server 2019 | Microsoft Docs
ms.date: 11/06/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: release-landing
ms.topic: article
ms.assetid: 13942af8-5a40-4cef-80f5-918386767a47
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: = sql-server-ver15 || = sqlallproducts-allversions
ms.openlocfilehash: 2c21ac917845b8162348b93fec3b868f1f748592
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51703857"
---
# <a name="sql-server-2019-preview-release-notes"></a>Notes de publication de SQL Server 2019 Preview

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article décrit les limitations et problèmes connus concernant les versions [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] Community Technology Preview (CTP). Pour des informations connexes, consultez :
- [Nouveautés de SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md)

> [!NOTE]
> Les préversions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sont mises à votre disposition pour que vous puissiez découvrir les fonctionnalités de la version à venir. Elles ne sont pas prises en charge ou distribuées sous licence dans le cadre d’une utilisation en production. Les scénarios suivants sont explicitement non pris en charge :
>
> - Installation côte à côte avec d’autres versions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]
> - Mise à niveau d’une instance existante de SQL Server à partir de n’importe quelle version

**Essayez [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] !**
- [![Télécharger à partir du Centre d’évaluation](../includes/media/download2.png)](https://go.microsoft.com/fwlink/?LinkID=862101) [Télécharger [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] en vue de l’installer sur Windows](https://go.microsoft.com/fwlink/?LinkID=862101)
- Installer sur Linux pour [Red Hat Enterprise Server](../linux/quickstart-install-connect-red-hat.md), [SUSE Linux Enterprise Server](../linux/quickstart-install-connect-suse.md) et [Ubuntu](../linux/quickstart-install-connect-ubuntu.md).
- [Exécuter SQL Server 2019 sur Docker](../linux/quickstart-install-connect-docker.md).

## <a name="ctp-21-november-2018"></a>CTP 2.1 (novembre 2018)
[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.1 est la première version publique de [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)].

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.1 est disponible uniquement en version d’évaluation. Aucune autre édition n’est disponible. La prise en charge de CTP 2.1 est décrite dans le fichier license_Eval.rtf qui se trouve sur votre support d’installation.

Une prise en charge limitée peut être disponible aux emplacements suivants :

- Forums
  - [Commentaires SQL Server](https://aka.ms/sqlfeedback)
  - [Prise en main de SQL Server](https://social.msdn.microsoft.com/Forums/sqlserver/en-US/home?forum=sqlgetstarted)
  - [Transact-SQL](https://social.msdn.microsoft.com/Forums/sqlserver/en-US/home?forum=transactsql)
  - [Documentation SQL Server](https://social.msdn.microsoft.com/Forums/sqlserver/en-US/home?forum=sqldocumentation)

- Ou tweetez [@SQLServer](https://twitter.com/SQLServer) avec [#sqlhelp](https://twitter.com/search?q=%23sqlhelp)

### <a name="documentation-ctp-21"></a>Documentation (CTP 2.1)

- **Problème et impact sur le client :** la documentation pour SQL Server 2019 (15.x) est limitée, et le contenu est inclus avec l’ensemble de documentation [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. Dans les articles, le contenu propre à SQL Server 2019 (15.x) est noté avec **S’applique à**.

- **Problème et impact sur le client** : la documentation [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] peut être filtrée par version. Utilisez le contrôle en haut à gauche de chaque page de documentation pour filtrer selon vos besoins. 

- **Problème et impact sur le client :** aucun contenu hors connexion n’est disponible pour SQL Server 2019 (15.x).

### <a name="hardware-and-software-requirements"></a>Configuration matérielle et logicielle requise

- **Problème et impact sur le client** : la configuration matérielle et logicielle requise est en cours d’examen et n’est pas finalisée pour la sortie du produit.

  - **Matériel**
    - [Windows : processeur, mémoire et système d’exploitation requis](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md#pmosr)
    - [Linux : configuration système requise](../linux/sql-server-linux-setup.md#system)
  - **Logiciels**
    - Windows Server 2016 ou version ultérieure. Pour connaître la configuration requise supplémentaire, consultez [Configuration requise pour l’installation de SQL Server](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).
    - Microsoft .NET Framework 4.6.2. Disponible sur le [Centre de téléchargement](https://www.microsoft.com/download/details.aspx?id=53344).
    - Pour Linux, reportez-vous à [Linux : plateformes prises en charge](../linux/sql-server-linux-setup.md#supportedplatforms).

### <a name="floating-point-results"></a>Résultats à virgule flottante

- **Problème et impact sur le client** : la préversion de SQL Server 2019 utilise un compilateur mis à jour pour générer SQL Server. Dans certains cas, le code compilé avec le nouveau compilateur peut retourner des valeurs numériques à virgule flottante différentes de celles des versions précédentes de SQL Server. Le changement de comportement sera limité au nouveau niveau de compatibilité (150) dans une prochaine version de CTP.

- **Solution de contournement** : S/O

- **S’applique à** : SQL Server 2019 CTP 2.1

### <a name="sql-server-integration-services-ssis-page-deployment-after-switching-db-to-single-user-mode-and-then-switching-back"></a>Déploiement de la page SQL Server Integration Services (SSIS) après le basculement de la base de données en mode mono-utilisateur et le rétablissement de l’autre mode

- **Problème et impact sur le client** : une fois que SSISB est revenu du mode mono-utilisateur au mode multi-utilisateur, l’erreur suivante risque d’apparaître lors du déploiement d’un package :

  `Cannot continue the execution because the session is in the kill state.`

- **Solution de contournement** : arrêtez et redémarrez l’instance SQL Server, puis refaites basculer SSISDB en mode multi-utilisateur. 

- **S’applique à :** préversion de SQL Server 2019 CTP 2.1


### <a name="udf-inlining"></a>Inlining de fonctions UDF 

- **Problème et impact sur le client** : il existe des scénarios pathologiques dans lesquels des appels imbriqués à des fonctions définies par l’utilisateur (UDF) inline ne valident pas correctement la sécurité.
  
- **Solution de contournement** : désactivez l’inlining de ces fonctions UDF à l’aide du paramètre `INLINE = OFF`.

- **S’applique à** : SQL Server 2019 CTP 2.1

### <a name="lightweight-query-profiling-infrastructure"></a>Infrastructure du profilage de requête léger

- **Problème et impact sur le client** : l’exécution de la commande `ALTER DATABASE SCOPED CONFIGURATION SET LIGHTWEIGHT_QUERY_PROFILING = ON` retourne une erreur de syntaxe. Les scénarios qui dépendent de l’exécution de cette commande échouent.

  > [!NOTE]
  > L’infrastructure du profilage de requête léger ne peut pas être contrôlée au niveau d’une base de données spécifique et demeure activée pour toutes les bases de données par défaut. Pour plus d’informations sur LWP, voir [Nouveautés de SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

- **Solution de contournement** : aucune pour [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP (toutes versions).

- **S’applique à** : [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.1 et CTP 2.0.

### <a name="utf-8-collations"></a>Classements UTF-8

- **Problème et impact sur le client** : les classements prenant en charge UTF-8 ne peuvent pas être utilisés avec certaines fonctionnalités [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. UTF-8 n’est pas pris en charge quand les fonctionnalités [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] suivantes sont en cours d’utilisation :

  - Réplication SQL Server
  - Serveur lié
  - OLTP en mémoire
  - Table externe pour PolyBase

    En outre, l’interface utilisateur d’Azure Data Studio et de SSDT ne permet pas de choisir des classements prenant en charge UTF-8. Il en va différemment de l’interface utilisateur de la dernière version de SSMS.

- **Solution de contournement** : aucune pour [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP (toutes versions).

- **S’applique à** : [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.1, CTP 2.0.

### <a name="sql-graph"></a>Graph SQL

- **Problème et impact sur le client** : les outils qui ont des dépendances vis-à-vis de DACFx comme l’importation ou l’exportation ne fonctionnent pas pour les nouvelles fonctionnalités de graphe : les contraintes d’arête ou la syntaxe DML de fusion. L’écriture de scripts dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] peut ne pas fonctionner.

- **Solution de contournement** : l’écriture de scripts [!INCLUDE[tsql](../includes/tsql-md.md)] et leur exécution sur le serveur à l’aide de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ou SQLCMD fonctionnent. L’exportation ou l’importation d’objets de base de données qui créent des contraintes d’arête, ont la nouvelle syntaxe DML de fusion ou créent des tables dérivées/vues sur des objets de graphe ne fonctionnent pas. Les utilisateurs doivent créer manuellement ces objets dans leur base de données à l’aide de scripts [!INCLUDE[tsql](../includes/tsql-md.md)]. 

- **S’applique à** : [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.1, 2.0.

### <a name="always-encrypted-with-secure-enclaves"></a>Always Encrypted avec enclaves sécurisées

- **Problème et impact sur le client** : les calculs avancés sont en attente d’une série d’optimisations des performances, incluent des fonctionnalités limitées (aucune indexation, etc.) et sont désactivés par défaut.

- **Solution de contournement** : pour activer les calculs avancés, exécutez `DBCC traceon(127,-1)`. Pour plus d’informations, consultez [Activer les calculs avancés](../relational-databases/security/encryption/configure-always-encrypted-enclaves.md#configure-a-secure-enclave).

- **S’applique à** : [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.1, 2.0.

### <a name="sql-server-integration-service---fuzzy-lookup-transformation"></a>Service d'intégration SQL Server – Transformation de la recherche approximative

- **Problème et impact sur le client** : la transformation de la recherche approximative échoue avec l’erreur suivante si la réutilisation de l’index a été définie :

  `The specified delimiters do not match the delimiters used to build the pre-existing match index "...". This error occurs when the delimiters used to tokenize fields do not match. This can have unknown effects on the matching behavior or results.`

- **Solution de contournement** : S/O

- **Informations complémentaires** : S/O  

- **S'applique à** : [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP2.1

## <a name="ctp-20-september-2018"></a>CTP 2.0 (septembre 2018)

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.0 est la première version publique de [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)].

### <a name="sql-server-integration-services-ssis-transfer-database-task"></a>Tâche de transfert de base de données SSIS (SQL Server Integration Services)

- **Problème et impact sur le client** : quand une `Transfer Database Task` est configurée pour transférer une base de données en mode `Database Online`, elle peut échouer avec l’erreur suivante :

  >La méthode Execute sur la tâche a retourné le code d’erreur 0x80131500 (une erreur s’est produite pendant le transfert des données. Pour en savoir plus, reportez-vous à l’exception interne.). La méthode Execute doit réussir et indiquer le résultat à l'aide d'un paramètre de sortie.

- **Solution de contournement** : exécutez `DBCC TRACEON (7416,-1)` sur le serveur et réessayez.

- **S’applique à** : [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.0.

[!INCLUDE[get-help-options-msft-only](../includes/paragraph-content/get-help-options.md)]

![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)
