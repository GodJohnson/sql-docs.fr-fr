---
title: Utilisation de mots clés de chaîne de connexion avec OLE DB Driver pour SQL Server | Microsoft Docs
description: Utilisation de mots clés de chaîne de connexion avec OLE DB Driver pour SQL Server
ms.custom: ''
ms.date: 07/03/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
f1_keywords:
- sql13.swb.connecttoserver.options.registeredservers.f1
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], connection string keywords
- MSOLEDBSQL, connection string keywords
- connection strings [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, connection string keywords
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: c96a65c3935e91204d562933ba4f5f0de932f3e0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47838299"
---
# <a name="using-connection-string-keywords-with-ole-db-driver-for-sql-server"></a>Utilisation de mots clés de chaîne de connexion avec OLE DB Driver pour SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Certains OLE DB Driver pour SQL Server API utiliser des chaînes de connexion pour spécifier les attributs de connexion. Les chaînes de connexion sont des listes de mots clés et de valeurs associées ; chaque mot clé identifie un attribut de connexion particulier.  
  
> [!NOTE]
> OLE DB Driver pour SQL Server autorise l’ambiguïté dans les chaînes de connexion afin de maintenir la compatibilité descendante (par exemple, certains mots clés peuvent être spécifiés plusieurs fois et des mots clés en conflit peuvent être autorisés avec la résolution en fonction de la position ou de la précédence). Les versions futures du pilote OLE DB pour SQL Server ne permettent pas d’ambiguïté dans les chaînes de connexion. Lors de la modification d’applications, il est conseillé d’utiliser OLE DB Driver pour SQL Server pour éliminer toute dépendance vis-à-vis de l’ambiguïté des chaînes de connexion.  
  
 Les sections suivantes décrivent les mots clés qui peuvent être utilisées avec le pilote OLE DB pour SQL Server et ActiveX Data Objects (ADO) lors de l’utilisation d’OLE DB Driver pour SQL Server en tant que le fournisseur de données.  

  
## <a name="ole-db-driver-connection-string-keywords"></a>Mots clés de chaîne de connexion OLE DB Driver  
 Il existe deux manières pour les applications OLE DB d'initialiser des objets source de données :  
  
-   **IDBInitialize::Initialize**  
  
-   **IDataInitialize::GetDataSource**  
  
 Dans le premier cas, une chaîne du fournisseur peut être utilisée pour initialiser des propriétés de connexion en définissant la propriété DBPROP_INIT_PROVIDERSTRING dans le jeu de propriétés DBPROPSET_DBINIT. Dans le deuxième cas, une chaîne d’initialisation peut être passée à la méthode **IDataInitialize::GetDataSource** pour initialiser des propriétés de connexion. Les deux méthodes initialisent les mêmes propriétés de connexion OLE DB, mais des jeux de mots clés différents sont utilisés. L’ensemble de mots clés utilisé par **IDataInitialize::GetDataSource** est au minimum la description des propriétés présentes dans le groupe de propriétés d’initialisation.  
  
 Lorsqu'un paramètre de chaîne du fournisseur qui a une propriété OLE DB correspondante définie à une certaine valeur par défaut ou explicitement définie avec une valeur, la valeur de la propriété OLE DB remplace le paramètre dans la chaîne du fournisseur.  
  
 Les propriétés booléennes définies dans les chaînes du fournisseur via des valeurs DBPROP_INIT_PROVIDERSTRING sont définies à l'aide des valeurs « yes » et « no ». Les propriétés booléennes définies dans les chaînes d’initialisation à l’aide de **IDataInitialize::GetDataSource** sont définies à l’aide des valeurs « true » et « false ».  
  
 Les applications qui utilisent **IDataInitialize::GetDataSource** peuvent également utiliser les mots clés utilisés par **IDBInitialize::Initialize**, mais uniquement pour les propriétés qui n’ont pas de valeur par défaut. Si une application utilise à la fois le mot clé **IDataInitialize::GetDataSource** et le mot clé **IDBInitialize::Initialize** dans la chaîne d’initialisation, le paramètre de mot clé **IDataInitialize::GetDataSource** est utilisé. Il est fortement recommandé que les applications n’utilisent pas de mots clés **IDBInitialize::Initialize** dans les chaînes de connexion **IDataInitialize:GetDataSource**, car ce comportement peut ne pas être conservé dans les versions ultérieures.  
  
> [!NOTE]  
>  Une chaîne de connexion passée via **IDataInitialize::GetDataSource** est convertie en propriétés et appliquée via **IDBProperties::SetProperties**. Si les services de composants ont trouvé la description de la propriété dans **IDBProperties::GetPropertyInfo**, cette propriété sera appliquée comme une propriété autonome. Sinon, elle sera appliquée par le biais de la propriété DBPROP_PROVIDERSTRING. Par exemple, si vous spécifiez la chaîne de connexion **Data Source = server1 ; Serveur = Serveur2**, **Source de données** est défini en tant que propriété, mais **Server** passera à une chaîne de fournisseur.  
  
 Si vous spécifiez plusieurs instances de la même propriété spécifique au fournisseur, la première valeur de la première propriété est utilisée.  
  
 Les chaînes de connexion utilisées par les applications OLE DB utilisant DBPROP_INIT_PROVIDERSTRING avec **IDBInitialize::Initialize** ont la syntaxe suivante :  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[{]attribute-value[}]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 Les valeurs d'attributs peuvent éventuellement être placées entre accolades, et ceci est d'ailleurs recommandé. Cela évite tout problème lorsque des valeurs d'attributs contiennent des signes non alphanumériques. Il est supposé que la première accolade fermante dans la valeur termine la valeur ; par conséquent, les valeurs ne peuvent pas contenir de caractères d'accolade fermante.  
  
 Un espace après le signe égal (=) d’un mot clé de chaîne de connexion sera interprété comme un littéral, même si la valeur est placée entre guillemets.  
  
 Le tableau suivant décrit les mots clés qui peuvent être utilisés avec DBPROP_INIT_PROVIDERSTRING.  
  
|Mot clé|Propriété d'initialisation|Description|  
|-------------|-----------------------------|-----------------|  
|**Addr**|SSPROP_INIT_NETWORKADDRESS|Synonyme de « Address ».|  
|**Adresse**|SSPROP_INIT_NETWORKADDRESS|Adresse réseau du serveur exécutant une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. **Address** est généralement le nom réseau du serveur, mais il peut s’agir d’autres noms tels qu’un canal, une adresse IP ou un port TCP/IP et une adresse de socket.<br /><br /> Si vous spécifiez une adresse IP, assurez-vous que les protocoles TCP/IP ou de canaux nommés sont activés dans le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> La valeur de **adresse** est prioritaire sur la valeur passée à **Server** dans les chaînes de connexion lors de l’utilisation d’OLE DB Driver pour SQL Server. Notez également que `Address=;` se connecte au serveur spécifié dans le mot clé **Server**, tandis que `Address= ;, Address=.;`, `Address=localhost;` et `Address=(local);` entraîne tous l’établissement d’une connexion au serveur local.<br /><br /> La syntaxe complète du mot clé **Address** est la suivante :<br /><br /> [_protocole_**:**]_adresse_[**,**_port &#124;\pipe\pipename_]<br /><br /> Le_protocole_ peut avoir la valeur **tcp** (TCP/IP), **lpc** (mémoire partagée) ou **np** (canaux nommés). Pour plus d’informations sur les protocoles, consultez [configurer des protocoles clients](../../../database-engine/configure-windows/configure-client-protocols.md).<br /><br /> Si ni _protocole_ ni le **réseau** mot clé est spécifié, le pilote OLE DB pour SQL Server utilisera l’ordre des protocoles spécifié dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager.<br /><br /> *port* est le port auquel se connecter, sur le serveur spécifié. Par défaut, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilise le port 1433.|   
|**APP**|SSPROP_INIT_APPNAME|Chaîne identifiant l'application.|  
|**ApplicationIntent**|SSPROP_INIT_APPLICATIONINTENT|Déclare le type de la charge de travail de l'application lors de la connexion à un serveur. Les valeurs possibles sont **ReadOnly** et **ReadWrite**.<br /><br /> La valeur par défaut est **ReadWrite**. Pour plus d’informations sur le pilote OLE DB pour la prise en charge de SQL Server pour [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], consultez [OLE DB Driver pour SQL Server prend en charge pour la haute disponibilité, récupération d’urgence](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|  
|**AttachDBFileName**|SSPROP_INIT_FILENAME|Nom du fichier primaire (incluez le nom de chemin d'accès complet) d'une base de données pouvant être attachée. Pour utiliser **AttachDBFileName**, vous devez également spécifier le nom de la base de données avec le mot clé Database de chaîne de fournisseur. Si la base de données a été attachée précédemment, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne la rattache pas (il utilise la base de données attachée comme valeur par défaut pour la connexion).|  
|**Traduire automatiquement**|SSPROP_INIT_AUTOTRANSLATE|Synonyme de « AutoTranslate ».|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Configure la traduction de caractères OEM/ANSI. Les valeurs reconnues sont « yes » et « no ».|  
|**Sauvegarde de la base de données**|DBPROP_INIT_CATALOG|Nom de la base de données.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Spécifie le mode de gestion de type de données à utiliser. Les valeurs reconnues sont « 0 » pour les types de données de fournisseur et « 80 » pour les types de données SQL Server 2000.|  
|**Encrypt**|SSPROP_INIT_ENCRYPT|Spécifie si les données doivent être chiffrées avant d'être envoyées sur le réseau. Les valeurs possibles sont « yes » et « no ». La valeur par défaut est « no ».|  
|**FailoverPartner**|SSPROP_INIT_FAILOVERPARTNER|Nom du serveur de basculement utilisé pour la mise en miroir de bases de données.|  
|**FailoverPartnerSPN**|SSPROP_INIT_FAILOVERPARTNERSPN|Nom principal de service du partenaire de basculement. La valeur par défaut est une chaîne vide. Une chaîne vide provoque un pilote OLE DB pour SQL Server à utiliser la valeur par défaut, généré par le fournisseur SPN.|  
|**Langage**|SSPROPT_INIT_CURRENTLANGUAGE|Langue de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**MarsConn**|SSPROP_INIT_MARSCONNECTION|Active ou désactive MARS (Multiple Active Result Set) sur la connexion si le serveur est [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ou version ultérieure. Les valeurs possibles sont « yes » et « no ». La valeur par défaut est « no ».|  
|**MultiSubnetFailover**|SSPROP_INIT_MULTISUBNETFAILOVER|Spécifiez toujours **MultiSubnetFailover=Yes** lors de la connexion à l’écouteur de groupe de disponibilité d’un groupe de disponibilité [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ou d’une instance de cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. **MultiSubnetFailover=Yes** configure OLE DB Driver pour SQL Server pour accélérer la détection du serveur (actuellement) actif et la connexion à ce dernier. Les valeurs possibles sont **Yes** et **No**. La valeur par défaut est **No**. Exemple :<br /><br /> `MultiSubnetFailover=Yes`<br /><br /> Pour plus d’informations sur le pilote OLE DB pour la prise en charge de SQL Server pour [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], consultez [OLE DB Driver pour SQL Server prend en charge pour la haute disponibilité, récupération d’urgence](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|  
|**Net**|SSPROP_INIT_NETWORKLIBRARY|Synonyme de « Network ».|  
|**Network**|SSPROP_INIT_NETWORKLIBRARY|Bibliothèque réseau utilisée pour établir une connexion à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans l'organisation.|  
|**Network Library**|SSPROP_INIT_NETWORKLIBRARY|Synonyme de « Network ».|  
|**PacketSize**|SSPROP_INIT_PACKETSIZE|Taille de paquet réseau. La valeur par défaut est 4096.|  
|**PersistSensitive**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Accepte les chaînes « yes » et « no » comme valeurs. Lorsque « no » est spécifié, l'objet source de données n'est pas autorisé à rendre les informations d'authentification sensibles persistantes|  
|**PWD**|DBPROP_AUTH_PASSWORD|Mot de passe de compte de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Server**|DBPROP_INIT_DATASOURCE|Nom d'une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. La valeur doit être le nom d'un serveur sur le réseau, une adresse IP ou le nom d'un alias du Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> Lorsque cette valeur n'est pas spécifiée, une connexion est établie à l'instance par défaut sur l'ordinateur local.<br /><br /> Le **adresse** mot clé substitue le **Server** mot clé.<br /><br /> Vous pouvez vous connecter à l’instance par défaut sur le serveur local en spécifiant l’un des éléments suivants :<br /><br /> **Server = ;**<br /><br /> **Server =. ;**<br /><br /> **Server=(local) ;**<br /><br /> **Server=(local) ;**<br /><br /> **Server=(localhost) ;**<br /><br /> **Server=(LocalDB)\\**  *instancename* **;**<br /><br /> Pour plus d’informations sur la prise en charge de la base de données locale, consultez [OLE DB Driver pour SQL Server prend en charge pour la base de données locale](../../oledb/features/oledb-driver-for-sql-server-support-for-localdb.md).<br /><br /> Pour spécifier une instance nommée de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], ajouter **\\** _InstanceName_.<br /><br /> Si aucun serveur n'est spécifié, une connexion est établie à l'instance par défaut sur l'ordinateur local.<br /><br /> Si vous spécifiez une adresse IP, assurez-vous que les protocoles TCP/IP ou de canaux nommés sont activés dans le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> La syntaxe complète du mot clé **Server** est la suivante :<br /><br /> **Server =**[_protocole_**:**]*Server*[**,**_port_]<br /><br /> Le_protocole_ peut avoir la valeur **tcp** (TCP/IP), **lpc** (mémoire partagée) ou **np** (canaux nommés).<br /><br /> Voici un exemple de spécification d'un canal nommé :<br /><br /> `np:\\.\pipe\MSSQL$MYINST01\sql\query`<br /><br /> Cette ligne spécifie le protocole de canal nommé, un canal nommé sur l'ordinateur local (`\\.\pipe`), le nom de l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (`MSSQL$MYINST01`) et le nom par défaut du canal nommé (`sql/query`).<br /><br /> Si ni un *protocole* ni le **réseau** mot clé est spécifié, le pilote OLE DB pour SQL Server utilisera l’ordre des protocoles spécifié dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager.<br /><br /> *port* est le port auquel se connecter, sur le serveur spécifié. Par défaut, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilise le port 1433.<br /><br /> Les espaces sont ignorés au début de la valeur passée à **Server** dans les chaînes de connexion lors de l’utilisation d’OLE DB Driver pour SQL Server.|   
|**ServerSPN**|SSPROP_INIT_SERVERSPN|Nom principal de service (SPN) du serveur. La valeur par défaut est une chaîne vide. Une chaîne vide provoque un pilote OLE DB pour SQL Server à utiliser la valeur par défaut, généré par le fournisseur SPN.|  
|**Délai d'expiration**|DBPROP_INIT_TIMEOUT|Durée (en secondes) pendant laquelle attendre que l'initialisation de source de données s'achève.|  
|**Trusted_Connection**|DBPROP_AUTH_INTEGRATED|Lorsque « Oui », indique le pilote OLE DB pour SQL Server pour utiliser le Mode d’authentification Windows pour la validation de la connexion. Autrement, fait en sorte qu’OLE DB Driver pour SQL Server utilise un nom d’utilisateur et un mot de passe [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour la validation de connexion, et les mots clés UID et PWD doivent être spécifiés.|  
|**TrustServerCertificate**|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Accepte les chaînes « yes » et « no » comme valeurs. La valeur par défaut est « no », ce qui signifie que le certificat de serveur sera validé.|  
|**UID**|DBPROP_AUTH_USERID|Nom du compte de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**UseFMTONLY**|SSPROP_INIT_USEFMTONLY|Contrôle la façon dont les métadonnées sont récupérées lors de la connexion à [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] et les versions ultérieures. Les valeurs possibles sont « yes » et « no ». La valeur par défaut est « no ».<br /><br />Par défaut, le pilote OLE DB pour SQL Server utilise [sp_describe_first_result_set](../../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md) et [sp_describe_undeclared_parameters](../../../relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql.md) des procédures stockées pour récupérer des métadonnées. Ces procédures stockées ont certaines limitations (par exemple, ils échoueront lors de l’exploitation sur des tables temporaires). Paramètre **UseFMTONLY** sur « yes » indique au pilote d’utiliser [SET FMTONLY](../../../t-sql/statements/set-fmtonly-transact-sql.md) pour la récupération de métadonnées à la place.|  
|**UseProcForPrepare**|SSPROP_INIT_USEPROCFORPREP|Ce mot clé est déconseillé et sa valeur est ignorée par le pilote OLE DB pour SQL Server.|  
|**WSID**|SSPROP_INIT_WSID|Identificateur de station de travail.|  
  
 Les chaînes de connexion utilisées par les applications OLE DB utilisant **IDataInitialize::GetDataSource** ont la syntaxe suivante :  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[quote]attribute-value[quote]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 `quote ::= " | '`  
  
 L'utilisation des propriétés doit être conforme à la syntaxe autorisée dans l'étendue.  Par exemple, **WSID** utilise des accolades (**{}**) caractères de guillemets et **nom de l’Application** utilise unique (**'**) ou Double (**»**) caractères. Seules les propriétés de chaîne peuvent être mises entre guillemets. Si vous tentez de placer entre guillemets un entier ou une propriété énumérée, une erreur indiquant que la chaîne de connexion n'est pas conforme à la spécification OLE DB sera générée.  
  
 Les valeurs d'attributs peuvent éventuellement être placées entre guillemets simples ou doubles, et ceci est d'ailleurs recommandé. Cela évite tout problème lorsque des valeurs contiennent des caractères non alphanumériques. Le caractère de guillemet utilisé peut également apparaître dans des valeurs, à condition d'être doublé.  
  
 Un espace après le signe égal (=) d’un mot clé de chaîne de connexion sera interprété comme un littéral, même si la valeur est placée entre guillemets.  
  
 Si une chaîne de connexion a plusieurs des propriétés répertoriées dans le tableau suivant, la valeur de la dernière propriété sera utilisée.  
  
 Le tableau suivant décrit les mots clés qui peuvent être utilisés avec **IDataInitialize::GetDataSource** :  
  
|Mot clé|Propriété d'initialisation|Description|  
|-------------|-----------------------------|-----------------|  
|**Application Name**|SSPROP_INIT_APPNAME|Chaîne identifiant l'application.|  
|**Intention de l’application**|SSPROP_INIT_APPLICATIONINTENT|Déclare le type de la charge de travail de l'application lors de la connexion à un serveur. Les valeurs possibles sont **ReadOnly** et **ReadWrite**.<br /><br /> La valeur par défaut est **ReadWrite**. Pour plus d’informations sur le pilote OLE DB pour la prise en charge de SQL Server pour [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], consultez [OLE DB Driver pour SQL Server prend en charge pour la haute disponibilité, récupération d’urgence](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|  
|**Traduire automatiquement**|SSPROP_INIT_AUTOTRANSLATE|Synonyme de « AutoTranslate ».|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Configure la traduction de caractères OEM/ANSI. Les valeurs reconnues sont « true » et « false ».|  
|**Connect Timeout**|DBPROP_INIT_TIMEOUT|Durée (en secondes) pendant laquelle attendre que l'initialisation de source de données s'achève.|  
|**Current Language**|SSPROPT_INIT_CURRENTLANGUAGE|Nom de la langue de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Source de données**|DBPROP_INIT_DATASOURCE|Nom d'une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans l'organisation.<br /><br /> Lorsque cette valeur n'est pas spécifiée, une connexion est établie à l'instance par défaut sur l'ordinateur local.<br /><br /> Pour plus d’informations sur la syntaxe d’adresse valide, consultez la description du mot clé **Server** dans cette rubrique.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Spécifie le mode de gestion de type de données à utiliser. Les valeurs reconnues sont « 0 » pour les types de données de fournisseur et « 80 » pour les types de données [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)].|  
|**Failover Partner**|SSPROP_INIT_FAILOVERPARTNER|Nom du serveur de basculement utilisé pour la mise en miroir de bases de données.|  
|**Failover Partner SPN**|SSPROP_INIT_FAILOVERPARTNERSPN|Nom principal de service du partenaire de basculement. La valeur par défaut est une chaîne vide. Une chaîne vide provoque un pilote OLE DB pour SQL Server à utiliser la valeur par défaut, généré par le fournisseur SPN.|  
|**Catalogue initial**|DBPROP_INIT_CATALOG|Nom de la base de données.|  
|**Nom de fichier initial**|SSPROP_INIT_FILENAME|Nom du fichier primaire (incluez le nom de chemin d'accès complet) d'une base de données pouvant être attachée. Pour utiliser **AttachDBFileName**, vous devez également spécifier le nom de la base de données avec le mot clé DATABASE de chaîne de fournisseur. Si la base de données a été attachée précédemment, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne la rattache pas (il utilise la base de données attachée comme valeur par défaut pour la connexion).|  
|**Sécurité intégrée**|DBPROP_AUTH_INTEGRATED|Accepte la valeur « SSPI » pour l'authentification Windows.|  
|**MARS Connection**|SSPROP_INIT_MARSCONNECTION|Active ou désactive MARS (Multiple Active Result Set) sur la connexion. Les valeurs reconnues sont « true » et « false ». La valeur par défaut est « false ».|  
|**MultiSubnetFailover**|SSPROP_INIT_MULTISUBNETFAILOVER|Spécifiez toujours **MultiSubnetFailover=True** lors de la connexion à l’écouteur de groupe de disponibilité d’un groupe de disponibilité [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ou d’une instance de cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. **MultiSubnetFailover=True** configure OLE DB Driver pour SQL Server pour accélérer la détection du serveur (actuellement) actif et la connexion à ce dernier. Les valeurs possibles sont **True** et **False**. La valeur par défaut est **False**. Exemple :<br /><br /> `MultiSubnetFailover=True`<br /><br /> Pour plus d’informations sur le pilote OLE DB pour la prise en charge de SQL Server pour [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], consultez [OLE DB Driver pour SQL Server prend en charge pour la haute disponibilité, récupération d’urgence](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|  
|**Network Address**|SSPROP_INIT_NETWORKADDRESS|Adresse réseau d'une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans l'organisation.<br /><br /> Pour plus d’informations sur la syntaxe d’adresse valide, consultez la description du mot clé **Address**, dans cette rubrique.|  
|**Network Library**|SSPROP_INIT_NETWORKLIBRARY|Bibliothèque réseau utilisée pour établir une connexion à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans l'organisation.|  
|**Packet Size**|SSPROP_INIT_PACKETSIZE|Taille de paquet réseau. La valeur par défaut est 4096.|  
|**Mot de passe**|DBPROP_AUTH_PASSWORD|Mot de passe de compte de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Persist Security Info**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Accepte les chaînes « true » et « false » comme valeurs. Lorsque « false » est spécifié, l'objet source de données n'est pas autorisé à rendre les informations d'authentification sensibles persistantes|  
|**Fournisseur**||Pour OLE DB Driver pour SQL Server, cela doit être « MSOLEDBSQL ».|  
|**Server SPN**|SSPROP_INIT_SERVERSPN|Nom principal de service (SPN) du serveur. La valeur par défaut est une chaîne vide. Une chaîne vide provoque un pilote OLE DB pour SQL Server à utiliser la valeur par défaut, généré par le fournisseur SPN.|  
|**Faire confiance au certificat de serveur**|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Accepte les chaînes « true » et « false » comme valeurs. La valeur par défaut est « false », ce qui signifie que le certificat de serveur sera validé.|  
|**Use Encryption for Data**|SSPROP_INIT_ENCRYPT|Spécifie si les données doivent être chiffrées avant d'être envoyées sur le réseau. Les valeurs possibles sont « true » et « false ». La valeur par défaut est « false ».|  
|**Use FMTONLY**|SSPROP_INIT_USEFMTONLY|Contrôle la façon dont les métadonnées sont récupérées lors de la connexion à [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] et les versions ultérieures. Les valeurs possibles sont « true » et « false ». La valeur par défaut est « false ».<br /><br />Par défaut, le pilote OLE DB pour SQL Server utilise [sp_describe_first_result_set](../../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md) et [sp_describe_undeclared_parameters](../../../relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql.md) des procédures stockées pour récupérer des métadonnées. Ces procédures stockées ont certaines limitations (par exemple, ils échoueront lors de l’exploitation sur des tables temporaires). Paramètre **FMTONLY utiliser** à « true » indique au pilote d’utiliser [SET FMTONLY](../../../t-sql/statements/set-fmtonly-transact-sql.md) pour la récupération de métadonnées à la place.|  
|**ID d'utilisateur**|DBPROP_AUTH_USERID|Nom du compte de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Workstation ID**|SSPROP_INIT_WSID|Identificateur de station de travail.|  
  
 **Remarque** Dans la chaîne de connexion, la propriété « Ancien Mot de passe » définit SSPROP_AUTH_OLD_PASSWORD, qui correspond au mot de passe actuel (éventuellement périmé) qui n’est pas disponible via une propriété de chaîne de fournisseur.  
  
## <a name="activex-data-objects-ado-connection-string-keywords"></a>Mots clés de chaîne de connexion ActiveX Data Objects (ADO)  
 Les applications ADO définissent la propriété **ConnectionString** des objets **ADODBConnection** ou fournissent une chaîne de connexion comme paramètre à la méthode **Open** des objets **ADODBConnection**.  
  
 Les applications ADO peuvent également utiliser les mots clés utilisés par la méthode OLE DB **IDBInitialize::Initialize**, mais uniquement pour les propriétés qui n’ont pas de valeur par défaut. Si une application utilise à la fois les mots clés ADO et les mots clés **IDBInitialize::Initialize** dans la chaîne d’initialisation, le paramètre de mot clé ADO est utilisé. Il est vivement recommandé que les applications utilisent uniquement des mots clés de chaîne de connexion ADO.  
  
 Les chaînes de connexion utilisées par ADO ont la syntaxe suivante :  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=["]attribute-value["]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 Les valeurs d'attributs peuvent éventuellement être placées entre guillemets doubles, et ceci est d'ailleurs recommandé. Cela évite tout problème lorsque des valeurs contiennent des caractères non alphanumériques. Les valeurs d'attributs ne peuvent pas contenir de guillemets doubles.  
  
 Le tableau suivant décrit les mots clés qui peuvent être utilisés avec une chaîne de connexion ADO :  
  
|Mot clé|Propriété d'initialisation|Description|  
|-------------|-----------------------------|-----------------|  
|**Intention de l’application**|SSPROP_INIT_APPLICATIONINTENT|Déclare le type de la charge de travail de l'application lors de la connexion à un serveur. Les valeurs possibles sont **ReadOnly** et **ReadWrite**.<br /><br /> La valeur par défaut est **ReadWrite**. Pour plus d’informations sur le pilote OLE DB pour la prise en charge de SQL Server pour [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], consultez [OLE DB Driver pour SQL Server prend en charge pour la haute disponibilité, récupération d’urgence](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|  
|**Application Name**|SSPROP_INIT_APPNAME|Chaîne identifiant l'application.|  
|**Traduire automatiquement**|SSPROP_INIT_AUTOTRANSLATE|Synonyme de « AutoTranslate ».|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Configure la traduction de caractères OEM/ANSI. Les valeurs reconnues sont « true » et « false ».|  
|**Connect Timeout**|DBPROP_INIT_TIMEOUT|Durée (en secondes) pendant laquelle attendre que l'initialisation de source de données s'achève.|  
|**Current Language**|SSPROPT_INIT_CURRENTLANGUAGE|Nom de la langue de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Source de données**|DBPROP_INIT_DATASOURCE|Nom d'une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans l'organisation.<br /><br /> Lorsque cette valeur n'est pas spécifiée, une connexion est établie à l'instance par défaut sur l'ordinateur local.<br /><br /> Pour plus d’informations sur la syntaxe d’adresse valide, consultez la description du mot clé **Server** dans cette rubrique.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Spécifie le mode de gestion de type de données qui sera utilisé. Les valeurs reconnues sont « 0 » pour les types de données de fournisseur et « 80 » pour les types de données SQL Server 2000.|  
|**Failover Partner**|SSPROP_INIT_FAILOVERPARTNER|Nom du serveur de basculement utilisé pour la mise en miroir de bases de données.|  
|**Failover Partner SPN**|SSPROP_INIT_FAILOVERPARTNERSPN|Nom principal de service du partenaire de basculement. La valeur par défaut est une chaîne vide. Une chaîne vide provoque un pilote OLE DB pour SQL Server à utiliser la valeur par défaut, généré par le fournisseur SPN.|  
|**Catalogue initial**|DBPROP_INIT_CATALOG|Nom de la base de données.|  
|**Nom de fichier initial**|SSPROP_INIT_FILENAME|Nom du fichier primaire (incluez le nom de chemin d'accès complet) d'une base de données pouvant être attachée. Pour utiliser **AttachDBFileName**, vous devez également spécifier le nom de la base de données avec le mot clé DATABASE de chaîne de fournisseur. Si la base de données a été attachée précédemment, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ne la rattache pas (il utilise la base de données attachée comme valeur par défaut pour la connexion).|  
|**Sécurité intégrée**|DBPROP_AUTH_INTEGRATED|Accepte la valeur « SSPI » pour l'authentification Windows.|  
|**MARS Connection**|SSPROP_INIT_MARSCONNECTION|Active ou désactive MARS (Multiple Active Result Set) sur la connexion si le serveur est [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ou version ultérieure. Les valeurs reconnues sont « true » et « false ». La valeur par défaut est « false ».|  
|**MultiSubnetFailover**|SSPROP_INIT_MULTISUBNETFAILOVER|Spécifiez toujours **MultiSubnetFailover=True** lors de la connexion à l’écouteur de groupe de disponibilité d’un groupe de disponibilité [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ou d’une instance de cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. **MultiSubnetFailover=True** configure OLE DB Driver pour SQL Server pour accélérer la détection du serveur (actuellement) actif et la connexion à ce dernier. Les valeurs possibles sont **True** et **False**. La valeur par défaut est **False**. Exemple :<br /><br /> `MultiSubnetFailover=True`<br /><br /> Pour plus d’informations sur le pilote OLE DB pour la prise en charge de SQL Server pour [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], consultez [OLE DB Driver pour SQL Server prend en charge pour la haute disponibilité, récupération d’urgence](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|  
|**Network Address**|SSPROP_INIT_NETWORKADDRESS|Adresse réseau d'une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans l'organisation.<br /><br /> Pour plus d’informations sur la syntaxe d’adresse valide, consultez la description du mot clé **Address**, dans cette rubrique.|  
|**Network Library**|SSPROP_INIT_NETWORKLIBRARY|Bibliothèque réseau utilisée pour établir une connexion à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans l'organisation.|  
|**Packet Size**|SSPROP_INIT_PACKETSIZE|Taille de paquet réseau. La valeur par défaut est 4096.|  
|**Mot de passe**|DBPROP_AUTH_PASSWORD|Mot de passe de compte de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Persist Security Info**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Accepte les chaînes « true » et « false » comme valeurs. Lorsque « false » est spécifié, l'objet source de données n'est pas autorisé à rendre les informations d'authentification sensibles persistantes.|  
|**Fournisseur**||Pour OLE DB Driver pour SQL Server, cela doit être « MSOLEDBSQL ».|  
|**Server SPN**|SSPROP_INIT_SERVERSPN|Nom principal de service (SPN) du serveur. La valeur par défaut est une chaîne vide. Une chaîne vide provoque un pilote OLE DB pour SQL Server à utiliser la valeur par défaut, généré par le fournisseur SPN.|  
|**Faire confiance au certificat de serveur**|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Accepte les chaînes « true » et « false » comme valeurs. La valeur par défaut est « false », ce qui signifie que le certificat de serveur sera validé.|  
|**Use Encryption for Data**|SSPROP_INIT_ENCRYPT|Spécifie si les données doivent être chiffrées avant d'être envoyées sur le réseau. Les valeurs possibles sont « true » et « false ». La valeur par défaut est « false ».|  
|**Use FMTONLY**|SSPROP_INIT_USEFMTONLY|Contrôle la façon dont les métadonnées sont récupérées lors de la connexion à [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] et les versions ultérieures. Les valeurs possibles sont « true » et « false ». La valeur par défaut est « false ».<br /><br />Par défaut, le pilote OLE DB pour SQL Server utilise [sp_describe_first_result_set](../../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md) et [sp_describe_undeclared_parameters](../../../relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql.md) des procédures stockées pour récupérer des métadonnées. Ces procédures stockées ont certaines limitations (par exemple, ils échoueront lors de l’exploitation sur des tables temporaires). Paramètre **FMTONLY utiliser** à « true » indique au pilote d’utiliser [SET FMTONLY](../../../t-sql/statements/set-fmtonly-transact-sql.md) pour la récupération de métadonnées à la place.|  
|**ID d'utilisateur**|DBPROP_AUTH_USERID|Nom du compte de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Workstation ID**|SSPROP_INIT_WSID|Identificateur de station de travail.|  
  
 **Remarque** Dans la chaîne de connexion, la propriété « Ancien Mot de passe » définit SSPROP_AUTH_OLD_PASSWORD, qui correspond au mot de passe actuel (éventuellement périmé) qui n’est pas disponible via une propriété de chaîne de fournisseur.  
  
## <a name="see-also"></a>Voir aussi  
 [Génération d’applications avec OLE DB Driver pour SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
  
  
