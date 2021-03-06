---
title: À l’aide de la mise en mémoire tampon adaptative | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 92d4e3be-c3e9-4732-9a60-b57f4d0f7cb7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 16ac54c78839df4c5ce911a1258dfa052ac1666c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47625003"
---
# <a name="using-adaptive-buffering"></a>Utilisation de la mise en mémoire tampon adaptative

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

La mise en mémoire tampon adaptative est conçue pour récupérer tout type de données de valeur importante sans la charge mémoire associée aux curseurs côté serveur. Les applications peuvent utiliser la fonctionnalité de mise en mémoire tampon adaptative avec toutes les versions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui sont prises en charge par le pilote.

Normalement, quand le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] exécute une requête, il extrait tous les résultats du serveur dans la mémoire d’application. Bien que cette approche réduise la consommation des ressources sur l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], elle peut lever une exception OutOfMemoryError dans l’application JDBC pour les requêtes qui produisent des résultats très grands.

Pour permettre aux applications de gérer des résultats très volumineux, le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fournit la mise en mémoire tampon adaptative. Avec la mise en mémoire tampon adaptative, le pilote récupère les résultats de l’exécution des instructions à partir du serveur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] chaque fois que l’application en a besoin, et non en une seule fois. Le pilote ignore également les résultats dès que l'application ne peut plus y accéder. Voici quelques exemples de situations où la mise en mémoire tampon adaptative peut être utile :

- **La requête génère un jeu de résultats très volumineux :** l’application peut exécuter une instruction SELECT qui produit plus de lignes que l’application peut stocker en mémoire. Dans les versions précédentes, l’application devait utiliser un curseur côté serveur pour éviter une erreur OutOfMemoryError. La mise en mémoire tampon adaptative permet d'effectuer un passage en lecture seule avant uniquement d'un jeu de résultats arbitrairement volumineux sans nécessiter de curseur côté serveur.

- **La requête produit très volumineux** [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) **colonnes ou** [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) **les valeurs de paramètre :** L’application peut récupérer une valeur unique (colonne ou paramètre de sortie) qui sont trop volumineuses pour tenir entièrement dans la mémoire de l’application. Mise en mémoire tampon adaptative permet à l’application cliente récupérer une telle valeur en tant que flux, en utilisant le getAsciiStream, le getBinaryStream ou les méthodes getCharacterStream. L’application récupère la valeur à partir du serveur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à mesure qu’elle lit le flux.

> [!NOTE]  
> Avec la mise en mémoire tampon adaptative, le pilote JDBC ne met en mémoire tampon que la quantité de données requise. Le pilote ne fournit aucune méthode publique pour contrôler ou limiter la taille de la mémoire tampon.

## <a name="setting-adaptive-buffering"></a>Définition de la mise en mémoire tampon adaptative

À compter de la version 2.0 du pilote JDBC, le comportement par défaut du pilote est « **adaptive** ». En d'autres termes, pour pouvoir obtenir le comportement de mise en mémoire tampon adaptative, votre application n'a pas besoin de requérir explicitement le mode de mise en mémoire tampon adaptative. Toutefois, dans la version 1.2, le mode de mise en mémoire tampon était « **full** » par défaut, et l’application devait demander explicitement le mode de mise en mémoire tampon adaptative.

Il existe trois manières pour une application de demander que l'exécution d'instructions utilise la mise en mémoire tampon adaptative :

- L’application peut définir la propriété de connexion **responseBuffering** « Adaptive ». Pour plus d’informations sur la définition des propriétés de connexion, consultez [définissant les propriétés de connexion](../../connect/jdbc/setting-the-connection-properties.md).

- L’application peut utiliser la méthode [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverdatasource.md) de l’objet [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md) pour définir le mode de mise en mémoire tampon de la réponse pour toutes les connexions créées par le biais de cet objet [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md).

- L’application peut utiliser la méthode [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) de la classe [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) pour définir le mode de mise en mémoire tampon de la réponse pour un objet statement particulier.

Lors de l’utilisation du pilote JDBC version 1.2, les applications devaient effectuer une conversion de type (transtypage) de l’objet statement vers une classe [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) pour pouvoir utiliser la méthode [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md). Les exemples de code dans le [l’échantillon de données volumineux lecture](../../connect/jdbc/reading-large-data-sample.md) et [lecture des données volumineuses avec exemple de procédures stockées](../../connect/jdbc/reading-large-data-with-stored-procedures-sample.md) illustrent cet ancien mode d’utilisation.

Toutefois, avec le pilote JDBC version 2.0, les applications peuvent utiliser les méthodes [isWrapperFor](../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md) et [unwrap](../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md) pour accéder aux fonctionnalités propres aux fournisseurs sans hypothèse relative à la hiérarchie de la classe d’implémentation. Par exemple de code, consultez le [la mise à jour des exemples de données volumineux](../../connect/jdbc/updating-large-data-sample.md) rubrique.

## <a name="retrieving-large-data-with-adaptive-buffering"></a>Récupération de données volumineuses avec la mise en mémoire tampon adaptative

Quand des valeurs élevées sont lues une fois à l’aide des méthodes get\<Type>Stream et que l’accès aux colonnes ResultSet et aux paramètres OUT de CallableStatement s’effectue dans l’ordre retourné par le serveur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la mise en mémoire tampon adaptative réduit l’utilisation de la mémoire de l’application lors du traitement des résultats. Lors de l'utilisation de la mise en mémoire tampon adaptative :

- Les méthodes get\<Type>Stream définies dans les classes [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) et [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) retournent des flux à lecture unique par défaut, bien que les flux puissent être réinitialisés s’ils sont marqués par l’application. Si l’application souhaite effectuer un `reset` du flux, elle doit d’abord appeler la méthode `mark` sur ce flux.

- Les méthodes get\<Type>Stream définies dans les classes [SQLServerClob](../../connect/jdbc/reference/sqlserverclob-class.md) et [SQLServerBlob](../../connect/jdbc/reference/sqlserverblob-class.md) retournent des flux qui peuvent toujours être repositionnés à la position de départ du flux sans appeler la méthode `mark`.

Quand l’application utilise la mise en mémoire tampon adaptative, les valeurs extraites par les méthodes get\<Type>Stream peuvent être extraites une seule fois. Si vous essayez d’appeler toute méthode get\<Type> sur la même colonne ou le même paramètre après avoir appelé la méthode get\<Type>Stream du même objet, une exception est levée avec le message « Un utilisateur a accédé aux données et elles ne sont pas disponibles pour cette colonne ou ce paramètre ».

> [!NOTE]
> Un appel à ResultSet.close() au milieu du traitement d’un jeu de résultats nécessiterait Microsoft JDBC Driver for SQL Server lire et ignorer tous les paquets restants. Cette opération peut prendre de temps si la requête a retourné un jeu de données volumineux et plus particulièrement la connexion réseau est lente.

## <a name="guidelines-for-using-adaptive-buffering"></a>Consignes pour l'utilisation de la mise en mémoire tampon adaptative

Les développeurs doivent respecter les recommandations importantes suivantes afin de réduire l'utilisation de la mémoire par l'application :

- Évitez d’utiliser la propriété de chaîne de connexion **electMethod=cursor** pour permettre à l’application de traiter un jeu de résultats très volumineux. La fonctionnalité de mise en mémoire tampon adaptative permet aux applications de traiter de très grands jeux de résultats avant uniquement en lecture seule sans utiliser de curseur côté serveur. Notez que, quand vous définissez **selectMethod=cursor**, tous les jeux de résultats en lecture seule de type avant produits par cette connexion sont affectés. En d’autres termes, si votre application traite régulièrement des jeux de résultats de petite taille avec peu de lignes, la création, la lecture et la fermeture d’un curseur côté serveur pour chaque jeu de résultats utilisera davantage de ressources à la fois côté client et côté serveur que dans le cas où **selectMethod** n’a pas la valeur **cursor**.

- Lire les grandes valeurs de texte ou binaires sous forme de flux en utilisant le getAsciiStream, le getBinaryStream ou les méthodes getCharacterStream au lieu du getBlob ou les méthodes getClob. À partir de la version 1.2, la classe [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) fournit de nouvelles méthodes get\<Type>Stream à cet effet.

- Vérifiez que les colonnes avec des valeurs potentiellement grandes sont placées en dernier dans la liste de colonnes dans une instruction SELECT et que les méthodes get\<Type>Stream du [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) sont utilisées pour accéder aux colonnes dans l’ordre dans lequel elles sont sélectionnées.

- Vérifiez que les paramètres OUT avec des valeurs potentiellement grandes sont déclarés en dernier dans la liste de paramètres dans le SQL utilisé pour créer le [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md). Vérifiez aussi que les méthodes get\<Type>Stream du [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) sont utilisées pour accéder aux paramètres OUT dans l’ordre dans lequel ils sont déclarés.

- Évitez d'exécuter simultanément plusieurs instructions sur la même connexion. L'exécution d'une autre instruction avant le traitement des résultats de l'instruction précédente peut provoquer la mise en mémoire tampon des résultats non traités dans la mémoire d'application.

- Il existe quelques cas où l’utilisation **selectMethod = cursor** au lieu de **responseBuffering = adaptive** serait plus avantageux, telles que :

  - Si votre application traite avant uniquement, en lecture seule jeu de résultats lentement, par exemple la lecture de chaque ligne après une entrée utilisateur, à l’aide de **selectMethod = cursor** au lieu de **responseBuffering = adaptive** peut aider à réduire l’utilisation des ressources par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

  - Si votre application traite plusieurs jeux de résultats en lecture seule de type avant simultanément sur la même connexion, l’utilisation de **selectMethod=cursor** à la place de **responseBuffering=adaptive** peut aider à réduire la mémoire requise par le pilote lors du traitement de ces jeux de résultats.

  Dans les deux cas, vous devez tenir compte de la surcharge liée à la création, la lecture et la fermeture des curseurs côté serveur.

En outre, la liste suivante fournit quelques recommandations pour les jeux de résultats de type avant uniquement pouvant être mis à jour et déroulables :

- Pour les jeux de résultats déroulables, lors de l’extraction d’un bloc de lignes, le pilote lit toujours en mémoire le nombre de lignes indiqué par la méthode [getFetchSize](../../connect/jdbc/reference/getfetchsize-method-sqlserverresultset.md) de l’objet [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md), même quand la mise en mémoire tampon adaptative est activée. Si le défilement provoque une erreur OutOfMemoryError, vous pouvez réduire le nombre de lignes extraites en appelant la méthode [setFetchSize](../../connect/jdbc/reference/setfetchsize-method-sqlserverresultset.md) de l’objet [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) pour affecter un nombre inférieur de lignes à la taille de l’extraction, voire une seule ligne, si nécessaire. Si cela n’empêche pas l’erreur OutOfMemoryError, évitez d’inclure des colonnes très volumineuses dans les jeux de résultats déroulables.

- Pour les jeux de résultats de type avant uniquement pouvant être mis à jour, lors de l’extraction d’un bloc de lignes, le pilote lit normalement en mémoire le nombre de lignes indiqué par la méthode [getFetchSize](../../connect/jdbc/reference/getfetchsize-method-sqlserverresultset.md) de l’objet [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md), même quand la mise en mémoire tampon adaptative est activée sur la connexion. Si l’appel de la méthode [next](../../connect/jdbc/reference/next-method-sqlserverresultset.md) de l’objet [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) provoque une erreur OutOfMemoryError, vous pouvez réduire le nombre de lignes extraites en appelant la méthode [setFetchSize](../../connect/jdbc/reference/setfetchsize-method-sqlserverresultset.md) de l’objet [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) pour affecter un nombre inférieur de lignes à la taille de l’extraction, voire une seule ligne, si nécessaire. Vous pouvez également forcer le pilote à ne mettre aucune ligne en mémoire en appelant la méthode [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) de l’objet [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) avec le paramètre « **adaptive** » avant d’exécuter l’instruction. Dans la mesure où le jeu de résultats n’est pas déroulable, si l’application accède à une valeur de colonne importante à l’aide de l’une des méthodes get\<Type>Stream, le pilote ignore la valeur dès que l’application la lit comme il le fait pour les jeux de résultats en lecture seule de type avant.

## <a name="see-also"></a> Voir aussi

[Amélioration des performances et de la fiabilité avec le pilote JDBC](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)
