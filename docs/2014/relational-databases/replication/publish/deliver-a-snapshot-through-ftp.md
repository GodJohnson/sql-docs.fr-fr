---
title: Remettre un instantané via FTP | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], FTP snapshots
- FTP snapshots [SQL Server replication]
- snapshot replication [SQL Server], FTP
ms.assetid: 99872c4f-40ce-4405-8fd4-44052d3bd827
caps.latest.revision: 46
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4396b84840deb4a0973e3aae73183a551d54fce3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37331529"
---
# <a name="deliver-a-snapshot-through-ftp"></a>Remettre un instantané via FTP
  Cette rubrique explique comment remettre un instantané via FTP dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Configuration requise](#Prerequisites)  
  
     [Sécurité](#Security)  
  
-   **Pour remettre un instantané via FTP à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   L'Agent d'instantané doit posséder des autorisations en écriture sur le répertoire spécifié et les Agents de distribution et de fusion des autorisations en lecture. Si vous utilisez des abonnements extraits, vous devez définir un répertoire partagé en tant que chemin UNC, par exemple \\\ftpserver\home\snapshots. Pour plus d’informations, consultez [Sécuriser le dossier d’instantanés](../security/secure-the-snapshot-folder.md).  
  
###  <a name="Prerequisites"></a> Conditions préalables  
  
-   Pour transférer des fichiers d'instantanés via FTP (File Transfer Protocol), vous devez avant tout configurer un serveur FTP. Pour plus d'informations, consultez la documentation de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Internet Information Services (IIS).  
  
###  <a name="Security"></a> Sécurité  
 Pour améliorer la sécurité, nous vous recommandons d'implémenter un réseau privé virtuel (VPN) lorsque vous utilisez la remise d'instantanés via FTP sur Internet. Pour plus d’informations, consultez [Publier des données sur Internet à l’aide d’un réseau privé virtuel](../publish-data-over-the-internet-using-vpn.md).  
  
 La méthode de sécurité conseillée consiste à désactiver l'accès anonyme au serveur FTP. L'Agent d'instantané doit posséder des autorisations en écriture sur le répertoire spécifié et les Agents de distribution et de fusion des autorisations en lecture. Si vous utilisez des abonnements extraits, vous devez définir un répertoire partagé en tant que chemin UNC, par exemple \\\ftpserver\home\snapshots. Pour plus d’informations, consultez [Sécuriser le dossier d’instantanés](../security/secure-the-snapshot-folder.md).  
  
 Lorsque cela est possible, invitez les utilisateurs à saisir leurs informations d'identification au moment de l'exécution. Si vous stockez les informations d'identification dans un fichier de script, vous devez sécuriser ce fichier.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Après avoir configuré le serveur FTP, spécifiez des informations de répertoire et de sécurité pour ce serveur dans la boîte de dialogue **Propriétés de la publication - \<Publication>**. Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [Afficher et modifier les propriétés d’un serveur de publication](view-and-modify-publication-properties.md).  
  
#### <a name="to-specify-ftp-information"></a>Pour spécifier des informations FTP  
  
1.  Dans la boîte de dialogue **Propriétés de la publication - \<Publication>**, sélectionnez **Autoriser les Abonnés à télécharger des fichiers d’instantanés via le protocole FTP (File Transfer Protocol)** dans l’une des pages suivantes :  
  
    -   Page **Instantané FTP** , pour les publications transactionnelles et d'instantané ainsi que les publications de fusion pour les serveurs de publication exécutant des versions antérieures à [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
    -   Page **Instantané FTP et Internet** , pour les publications de fusion des serveurs de publication exécutant [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ou ultérieur.  
  
2.  Spécifiez des valeurs dans les zones de texte **Nom du serveur FTP**, **Numéro de port**, **Chemin d'accès au dossier racine FTP**, **Nom de connexion**et **Mot de passe**.  
  
     Si, par exemple la racine du serveur FTP est \\\ftpserver\home et que vous souhaitez stocker les instantanés dans \\\ftpserver\home\snapshots, spécifiez \snapshots\ftp pour la propriété **Chemin d’accès au dossier racine FTP** (la réplication ajoute « ftp » au chemin d’accès au dossier d’instantanés lorsqu’il crée les fichiers d’instantanés).  
  
3.  Spécifiez que l'Agent d'instantané doit écrire les fichiers d'instantanés dans le répertoire défini à l'étape 2. Par exemple, pour que l’Agent d’instantané écrive les fichiers d’instantanés dans \\\ftpserver\home\snapshots\ftp, vous devez définir le chemin \\\ftpserver\home\snapshots dans l’un ou l’autre emplacement :  
  
    -   Emplacement des instantanés par défaut sur le serveur de distribution associé à cette publication.  
  
         Pour plus d’informations sur la spécification de l’emplacement par défaut des instantanés, consultez [Spécifier l’emplacement par défaut des instantanés &#40;SQL Server Management Studio&#41;](../specify-the-default-snapshot-location-sql-server-management-studio.md).  
  
    -   Autre emplacement de dossier d'instantanés pour cette publication. Un autre emplacement est requis si l'instantané est compressé.  
  
         Entrez le chemin dans la zone de texte **Placer les fichiers dans le dossier suivant** dans la page Instantané de la boîte de dialogue **Propriétés de la publication - \<Publication>**. Pour plus d'informations sur la définition d'autres emplacements de dossier d'instantanés, consultez [Alternate Snapshot Folder Locations](../alternate-snapshot-folder-locations.md).  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 L'option permettant de rendre disponibles sur un serveur FTP des fichiers d'instantanés peut être définie et ces paramètres FTP peuvent être modifiés par programme en utilisant des procédures stockées de réplication. La procédure utilisée dépend du type de publication. La remise d'instantanés via FTP est utilisée uniquement avec les abonnements par extraction.  
  
#### <a name="to-enable-ftp-snapshot-delivery-for-a-snapshot-or-transactional-publication"></a>Pour activer la remise d'instantanés via FTP pour une publication transactionnelle ou d'instantané  
  
1.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql). Spécifiez **@publication**, une valeur de `true` pour **@enabled_for_internet**et les valeurs pour les paramètres suivants appropriées :  
  
    -   **@ftp_address** - l'adresse du serveur FTP utilisé pour remettre l'instantané.  
  
    -   (Facultatif) **@ftp_port** - le port utilisé par le serveur FTP.  
  
    -   (Facultatif) **@ftp_subdirectory** - le sous-répertoire du répertoire FTP par défaut affecté à une connexion FTP. Par exemple, si la racine du serveur FTP est \\\ftpserver\home et que vous souhaitez stocker les instantanés dans \\\ftpserver\home\snapshots, spécifiez **\snapshots\ftp** pour **@ftp_subdirectory** (la réplication ajoute « ftp » au chemin du dossier d’instantanés lorsqu’il crée les fichiers d’instantanés).  
  
    -   (Facultatif) **@ftp_login** - un compte de connexion utilisé lors de la connexion au serveur FTP.  
  
    -   (Facultatif) **@ftp_password** - le mot de passe de la connexion FTP.  
  
     Une publication qui utilise FTP est alors créée. Pour plus d’informations, voir [Create a Publication](create-a-publication.md).  
  
#### <a name="to-enable-ftp-snapshot-delivery-for-a-merge-publication"></a>Pour activer la remise d'instantanés via FTP pour une publication de fusion  
  
1.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql). Spécifiez **@publication**, une valeur de `true` pour **@enabled_for_internet** et appropriées des valeurs pour les paramètres suivants :  
  
    -   **@ftp_address** - l'adresse du serveur FTP utilisé pour remettre l'instantané.  
  
    -   (Facultatif) **@ftp_port** - le port utilisé par le serveur FTP.  
  
    -   (Facultatif) **@ftp_subdirectory** - le sous-répertoire du répertoire FTP par défaut affecté à une connexion FTP. Par exemple, si la racine du serveur FTP est \\\ftpserver\home et que vous souhaitez stocker les instantanés dans \\\ftpserver\home\snapshots, spécifiez **\snapshots\ftp** pour **@ftp_subdirectory** (la réplication ajoute « ftp » au chemin du dossier d’instantanés lorsqu’il crée les fichiers d’instantanés).  
  
    -   (Facultatif) **@ftp_login** - un compte de connexion utilisé lors de la connexion au serveur FTP.  
  
    -   (Facultatif) **@ftp_password** - le mot de passe de la connexion FTP.  
  
     Une publication qui utilise FTP est alors créée. Pour plus d’informations, voir [Create a Publication](create-a-publication.md).  
  
#### <a name="to-create-a-pull-subscription-to-a-snapshot-or-transactional-publication-that-uses-ftp-snapshot-delivery"></a>Pour créer un abonnement par extraction vers une publication transactionnelle ou d'instantané qui utilise la remise d'instantanés via FTP  
  
1.  Dans la base de données d'abonnement de l'Abonné, exécutez [sp_addpullsubscription](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql). Spécifiez **@publisher** et **@publication**.  
  
    -   Dans la base de données d'abonnement de l'Abonné, exécutez [sp_addpullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql). Spécifiez **@publisher**, **@publisher_db**, **@publication**, le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] informations d’identification Windows sous lequel l’Agent de Distribution sur le Abonné s’exécute pour **@job_login** et **@job_password**et la valeur `true` pour **@use_ftp**.  
  
2.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) pour inscrire l'abonnement par extraction. Pour plus d’informations, consultez [Créer un abonnement par extraction de données (pull)](../create-a-pull-subscription.md).  
  
#### <a name="to-create-a-pull-subscription-to-a-merge-publication-that-uses-ftp-snapshot-delivery"></a>Pour créer un abonnement par extraction à une publication de fusion qui utilise la remise d'instantanés via FTP  
  
1.  Dans la base de données d'abonnement de l'Abonné, exécutez [sp_addmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql). Spécifiez **@publisher** et **@publication**.  
  
2.  Dans la base de données d'abonnement de l'Abonné, exécutez [sp_addmergepullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql). Spécifiez **@publisher**, **@publisher_db**, **@publication**, les informations d’identification Windows sous lequel l’Agent de Distribution sur l’abonné s’exécute pour **@job_login** et **@job_password**et la valeur `true` pour **@use_ftp**.  
  
3.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_addmergesubscription](/sql/relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql) pour inscrire l'abonnement par extraction. Pour plus d’informations, consultez [Créer un abonnement par extraction de données (pull)](../create-a-pull-subscription.md).  
  
#### <a name="to-change-one-or-more-ftp-snapshot-delivery-settings-for-a-snapshot-or-transactional-publication"></a>Pour modifier un ou plusieurs paramètres de remise d'instantanés sur FTP pour une publication transactionnelle ou d'instantané  
  
1.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql). Affectez l'une des valeurs suivantes à **@property** et une nouvelle valeur de ce paramètre à **@value**:  
  
    -   `ftp_address` -l’adresse du serveur FTP utilisé pour remettre l’instantané.  
  
    -   `ftp_port` -le port utilisé par le serveur FTP.  
  
    -   `ftp_subdirectory` -le sous-répertoire du répertoire FTP par défaut utilisé pour l’instantané FTP.  
  
    -   `ftp_login` - une connexion utilisée pour la connexion au serveur FTP.  
  
    -   `ftp_password` - le mot de passe utilisé pour la connexion FTP.  
  
2.  (Facultatif) Répétez l'étape 1 pour chaque paramètre FTP modifié.  
  
3.  (Facultatif) Pour désactiver la remise d'instantanés via FTP, exécutez [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql) au niveau du serveur de publication dans la base de données de publication. Spécifiez la valeur `enabled_for_internet` pour **@property** et la valeur `false` pour **@value**.  
  
#### <a name="to-change-ftp-snapshot-delivery-settings-for-a-merge-publication"></a>Pour modifier les paramètres de remise d'instantanés via FTP pour une publication de fusion  
  
1.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql). Affectez l'une des valeurs suivantes à **@property** et une nouvelle valeur de ce paramètre à **@value**:  
  
    -   `ftp_address` -l’adresse du serveur FTP utilisé pour remettre l’instantané.  
  
    -   `ftp_port` -le port utilisé par le serveur FTP.  
  
    -   `ftp_subdirectory` -le sous-répertoire du répertoire FTP par défaut utilisé pour l’instantané FTP.  
  
    -   `ftp_login` - une connexion utilisée pour la connexion au serveur FTP.  
  
    -   `ftp_password` - le mot de passe utilisé pour la connexion FTP.  
  
2.  (Facultatif) Répétez l'étape 1 pour chaque paramètre FTP modifié.  
  
3.  (Facultatif) Pour désactiver la remise d'instantanés via FTP, exécutez [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql) au niveau du serveur de publication dans la base de données de publication. Spécifiez la valeur `enabled_for_internet` pour **@property** et la valeur `false` pour **@value**.  
  
###  <a name="TsqlExample"></a> Exemples (Transact-SQL)  
 L'exemple suivant crée une publication de fusion qui permet aux Abonnés d'accéder aux données des  instantanés en utilisant FTP. L'Abonné doit utiliser une connexion VPN sécurisée lors de l'accès au partage FTP. Les variables de script**sqlcmd** sont utilisées pour fournir les valeurs de connexion et de mot de passe. Pour plus d’informations, consultez [Utiliser sqlcmd avec des variables de script](../../scripting/sqlcmd-use-with-scripting-variables.md).  
  
 [!code-sql[HowTo#sp_createmergepub_ftp](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepubftp.sql#sp_createmergepub_ftp)]  
  
 L'exemple suivant crée un abonnement à une publication de fusion, dans lequel l'Abonné obtient l'instantané en utilisant FTP. L'Abonné doit utiliser une connexion VPN sécurisée lors de l'accès au partage FTP. Les variables de script**sqlcmd** sont utilisées pour fournir les valeurs de connexion et de mot de passe. Pour plus d’informations, consultez [Utiliser sqlcmd avec des variables de script](../../scripting/sqlcmd-use-with-scripting-variables.md).  
  
 [!code-sql[HowTo#sp_createmergepullsub_ftp](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepullsubftp.sql#sp_createmergepullsub_ftp)]  
  
 [!code-sql[HowTo#sp_createmergepullsubagent_ftp](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepullsubftp.sql#sp_createmergepullsubagent_ftp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)   
 [Transférer des instantanés via FTP](../transfer-snapshots-through-ftp.md)   
 [Modifier les propriétés des publications et des articles](change-publication-and-article-properties.md)   
 [Initialiser un abonnement avec un instantané](../initialize-a-subscription-with-a-snapshot.md)  
  
  