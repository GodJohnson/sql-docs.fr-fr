---
title: Présentation de prise en charge de Java EE | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a9448b80-b7a3-49cf-8bb4-322c73676005
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 76032ffa6737e39556a9047e91b0d2666ddea39b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47702137"
---
# <a name="understanding-java-ee-support"></a>Fonctionnement de la prise en charge Java EE

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Les sections suivantes expliquent comment le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] assure la prise en charge de la plateforme Java, d’Enterprise Edition (Java EE) et des fonctionnalités d’API JDBC 3.0 facultatives. Les exemples de code source fournis dans ce système d'aide constituent une bonne référence pour débuter avec ces fonctionnalités.  
  
En premier lieu, assurez-vous que votre environnement Java (JDK, JRE) inclut le package javax.sql. Il s'agit d'un package requis pour toute application JDBC qui utilise l'API facultative. JDK 1.5 et les versions ultérieures contiennent déjà ce package ; il n’est donc pas nécessaire de l’installer séparément.  
  
## <a name="driver-name"></a>Nom du pilote

Le nom de la classe du pilote est **com.microsoft.sqlserver.jdbc.SQLServerDriver**. Pour les pilotes JDBC Driver 4.1, 4.2 et 6.0, le pilote est contenu dans le fichier **sqljdbc.jar**, **sqljdbc4.jar**, **sqljdbc41.jar** ou **sqljdbc42.jar**.

Pour JDBC Driver 6.2, le pilote est contenu dans **mssql-jdbc-6.2.2.jre7.jar** ou **mssql-jdbc-6.2.2.jre8.jar**.

Pour JDBC Driver 6.4, le pilote est contenu dans **mssql-jdbc-6.4.0.jre7.jar**, **mssql-jdbc-6.4.0.jre8.jar**, ou **mssql-jdbc-6.4.0.jre9.jar**.

Pour 7.0 du pilote JDBC, le pilote est contenu dans **mssql-jdbc-7.0.0.jre8.jar**, ou **mssql-jdbc-7.0.0.jre10.jar**.
  
Le nom de la classe est utilisé chaque fois que le pilote est chargé avec la classe DriverManager JDBC. Il sert également chaque fois que le nom de la classe du pilote doit être spécifié, quelle que soit la configuration du pilote. Par exemple, la configuration d'une source de données dans un serveur d'applications Java EE peut imposer d’entrer le nom de la classe du pilote.  
  
## <a name="data-sources"></a>Sources de données

Le pilote JDBC assure la prise en charge des sources de données Java EE / JDBC 3.0. Le pilote JDBC [SQLServerXADataSource](../../connect/jdbc/reference/sqlserverxadatasource-class.md) classe est implémentée par `com.microsoft.sqlserver.jdbc.SQLServerXADataSource`.  
  
### <a name="datasource-names"></a>Noms de sources de données

Vous pouvez établir des connexions de base de données à l'aide de sources de données. Les sources de données disponibles avec le pilote JDBC sont décrites dans le tableau suivant :  
  
|Type DataSource|Nom de la classe et description|  
|---------------|--------------------------|  
|DataSource|`com.microsoft.sqlserver.jdbc.SQLServerDataSource` <br/> <br/> Source de données sans regroupement.|  
|ConnectionPoolDataSource|`com.microsoft.sqlserver.jdbc.SQLServerConnectionPoolDataSource` <br/> <br/> Source de données pour configurer des regroupements de connexions de serveur d'applications JAVA EE. Utilisée en général lorsque l'application s'exécute sur un serveur d'applications JAVA EE.|  
|XADataSource|`com.microsoft.sqlserver.jdbc.SQLServerXADataSource` <br/> <br/> Source de données pour configurer des sources de données JAVA EE XA. Utilisée en général lorsque l'application s'exécute sur un serveur d'applications JAVA EE et un gestionnaire de transactions XA.|  
  
### <a name="data-source-properties"></a>Propriétés de la source de données

Toutes les sources de données prennent en charge la capacité à définir et à obtenir toute propriété associée à l'ensemble des propriétés du pilote sous-jacent.  
  
Exemples :  
  
`setServerName("localhost");`  
`setDatabaseName("AdventureWorks");`  
  
L'exemple suivant montre comment une application se connecte en utilisant une source de données :  

```java
//initialize JNDI ..  
Context ctx = new InitialContext(System.getProperties());
...
DataSource ds = (DataSource) ctx.lookup("MyDataSource");
Connection c = ds.getConnection("user", "pwd");  
```

Pour plus d’informations sur les propriétés de source de données, consultez [définissant les propriétés de Source de données](../../connect/jdbc/setting-the-data-source-properties.md).  
  
## <a name="see-also"></a> Voir aussi

[Vue d’ensemble du pilote JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
