---
title: Connexion à SQL Server (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- authentication
- instance of SQL Server
- metadata, refreshing
- ports
- refreshing metadata
- spaces in database names
- special characters
- SQL Server
- SQL Server, connecting
- SQL Server, connecting to
- SQL Server, reconnecting
ms.assetid: f84cf007-ddf1-4396-a07c-3e0729abc769
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 0bedb8ba74d7965df34a102fb0d53a0cbdb248dc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47649277"
---
# <a name="connecting-to-sql-server-accesstosql"></a>Connexion à SQL Server (AccessToSQL)
Pour migrer des bases de données Access [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez vous connecter à l’instance cible de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Lorsque vous vous connectez, SSMA Obtient des métadonnées sur les bases de données dans l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et affiche les métadonnées de base de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Explorateur de métadonnées. SSMA stocke des informations sur l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que vous êtes connecté à, mais ne stocke pas les mots de passe.  
  
Votre connexion à SQL Server reste active jusqu'à ce que vous fermiez le projet. Lorsque vous rouvrez le projet, vous devez vous reconnecter à SQL Server si vous souhaitez une connexion active au serveur. Vous pouvez travailler hors connexion jusqu'à ce que vous chargez des objets de base de données dans SQL Server et migrez des données.  
  
Métadonnées relatives à l’instance de SQL Server ne sont pas synchronisée automatiquement. Au lieu de cela, pour mettre à jour les métadonnées dans l’Explorateur de métadonnées SQL Server, vous devez manuellement mettre à jour les métadonnées de SQL Server. Pour plus d’informations, consultez la section « Synchronisation des métadonnées SQL Server » plus loin dans cette rubrique.  
  
## <a name="required-sql-server-permissions"></a>Autorisations requises de SQL Server  
Le compte qui est utilisé pour se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nécessite des autorisations différentes selon les actions effectuées par ce compte.  
  
-   Pour convertir des objets d’accès à [!INCLUDE[tsql](../../includes/tsql-md.md)] syntaxe, actualisation des métadonnées à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ou pour enregistrer la syntaxe converti vers des scripts, le compte doit disposer d’autorisation pour vous connecter à l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Pour charger des objets de base de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et à migrer des données vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l’exigence d’autorisation minimal est l’appartenance à la **db_owner** rôle de base de données dans la base de données cible.  
  
## <a name="establishing-a-sql-server-connection"></a>L’établissement d’une connexion SQL Server  
Avant de convertir des objets de base de données Access à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] syntaxe, vous devez établir une connexion à l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] où vous souhaitez migrer les bases de données Access.  
  
Lorsque vous définissez les propriétés de connexion, vous spécifiez également la base de données où les objets et les données seront migrées. Vous pouvez personnaliser ce mappage au niveau d’accès de base de données après vous être connecté à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [Source de mappage et de bases de données cibles](mapping-source-and-target-databases-accesstosql.md).  
  
> [!IMPORTANT]  
> Avant de vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], assurez-vous que l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est en cours d’exécution et peut accepter les connexions. Pour plus d’informations, consultez « connexion à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] moteur de base de données » dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne.  
  
**Pour vous connecter à SQL Server**  
  
1.  Sur le **fichier** menu, sélectionnez **se connecter à SQL Server**.  
  
    Si vous aviez précédemment connecté à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le nom de la commande sera **reconnexion à SQL Server**.  
  
2.  Dans le **nom du serveur** zone, entrez ou sélectionnez le nom de l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    -   Si vous vous connectez à l’instance par défaut sur l’ordinateur local, vous pouvez entrer **localhost** ou un point (**.**).  
  
    -   Si vous vous connectez à l’instance par défaut sur un autre ordinateur, entrez le nom de l’ordinateur.  
  
    -   Si vous vous connectez à une instance nommée, entrez le nom d’ordinateur, une barre oblique inverse et le nom d’instance. Par exemple : MyServer\MyInstance.  
  
    -   Pour vous connecter à une instance utilisateur active de [!INCLUDE[ssExpress](../../includes/ssexpress_md.md)], se connecter à l’aide de canaux nommés protocole et en spécifiant le nom du canal, tel que \\ \\.\pipe\sql\query. Pour plus d’informations, consultez la documentation de [!INCLUDE[ssExpress](../../includes/ssexpress_md.md)].  
  
3.  Si votre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configuré pour accepter les connexions sur un port non défini par défaut, entrez le numéro de port qui est utilisé pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexions dans le **port du serveur** boîte. L’instance par défaut de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le numéro de port par défaut est 1433. Pour les instances nommées, SSMA essaiera d’obtenir le numéro de port à partir de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Browser.  
  
4.  Dans le **base de données** , entrez le nom de la base de données cible pour la migration de données et des objets.  
  
    Cette option n’est pas disponible lors de la reconnexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    Le nom de la base de données cible ne peut pas contenir des espaces ou des caractères spéciaux. Par exemple, vous pouvez migrer des bases de données Access à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données nommée « abc ». Mais vous ne pouvez pas migrer des bases de données Access à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données nommée « a b-c ».  
  
    Vous pouvez personnaliser ce mappage par base de données une fois que vous vous connectez. Pour plus d’informations, consultez [Source de mappage et de bases de données cibles](mapping-source-and-target-databases-accesstosql.md)  
  
5.  Dans le **authentification** menu déroulant, sélectionnez type d’authentification à utiliser pour la connexion. Pour utiliser le compte Windows actuel, sélectionnez **l’authentification Windows**. Pour utiliser un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion, sélectionnez **l’authentification SQL Server**, puis indiquez un nom d’utilisateur et le mot de passe.  
  
6.  Pour une connexion sécurisée, les deux contrôles sont ajoutés, **chiffrer la connexion** case à cocher et **TrustServerCertificate** case à cocher. Uniquement lorsque **chiffrer la connexion** case à cocher est activée **TrustServerCertificate** case à cocher est visible. Lorsque **chiffrer la connexion** est checked(true) et **TrustServerCertificate** est unchecked(false), validera le certificat SSL SQL Server. La validation du certificat de serveur est une partie de la négociation SSL qui garantit qu'il s'agit du serveur correct avec lequel établir une connexion. Pour ce faire, un certificat doit être installé sur le côté client, ainsi que sur le côté serveur.  
  
7.  Cliquez sur **Se connecter**.  
  
**Compatibilité de version supérieur**  
  
Il est autorisé à se connecter/se reconnecter à des versions ultérieures de SQL Server.  
  
1.  Vous serez en mesure de se connecter à SQL Server 2008 ou SQL Server 2012, lorsque le projet créé est SQL Server 2005.  
  
2.  Vous serez en mesure de se connecter à SQL Server 2012, lorsque le projet créé est SQL Server 2008, mais il n’est pas autorisé à se connecter à des versions inférieures par exemple, SQL Server 2005.  
  
3.  Vous serez en mesure de se connecter à SQL Server 2012 uniquement lorsque le projet créé est SQL Server 2012.  
  
4.  Compatibilité de version supérieur n’est pas valide pour SQL Azure.  
  
||||||||
|-|-|-|-|-|-|-|
|**PROJET Visual Studio TYPE VERSION du serveur cible**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 (version : 9.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 (version : 10.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 (Version:11.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 (Version:12.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 (Version:13.x)|SQL Azure|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005|Oui|Oui|Oui|Oui|Oui||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008||Oui|Oui|Oui|Oui||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012|||Oui|Oui|Oui||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014||||Oui|Oui||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016|||||Oui||
|SQL Azure||||||Oui|
  
> [!IMPORTANT]  
> Conversion des objets de base de données est effectuée selon le type de projet, mais pas conformément à la version de SQL Server connecté à. En cas de projet SQL Server 2005, Conversion est effectuée conformément à SQL Server 2005 même si vous êtes connecté à une version ultérieure de SQL Server (SQL Server 2008/SQL Server 2012/SQL Server 2014/SQL Server 2016).  
  
## <a name="synchronizing-sql-server-metadata"></a>Synchronisation des métadonnées du serveur SQL  
Si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] schémas modifient après vous être connecté, vous pouvez synchroniser les métadonnées avec le serveur.  
  
**Pour synchroniser les métadonnées de SQL Server**  
  
-   Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Explorateur de métadonnées, clic droit **bases de données**, puis sélectionnez **synchroniser avec la base de données**.  
  
## <a name="reconnecting-to-sql-server"></a>Rétablir la connexion à SQL Server  
Votre connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] reste active jusqu'à ce que vous fermez le projet. Lorsque vous rouvrez le projet, vous devez vous reconnecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si vous souhaitez une connexion active au serveur. Vous pouvez travailler hors connexion jusqu'à ce que vous chargez des objets de base de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et migrer les données.  
  
La procédure de reconnexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est identique à la procédure pour établir une connexion.  
  
## <a name="next-steps"></a>Étapes suivantes  
Si vous souhaitez personnaliser le mappage entre les bases de données source et cible, consultez [Source de mappage et de bases de données cibles](mapping-source-and-target-databases-accesstosql.md) dans le cas contraire, l’étape suivante consiste à convertir des objets de base de données à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de la syntaxe [convertir objets de base de données](converting-access-database-objects-accesstosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Migration bases de données Access vers SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
