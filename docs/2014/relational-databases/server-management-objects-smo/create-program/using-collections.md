---
title: À l’aide de Collections | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQL Server Management Objects, collections
- SMO [SQL Server], collections
- collections [SMO]
ms.assetid: 209eb175-2514-4de1-bc32-b2e6a469d945
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 33c0d43f3be1ca48904a7e4fa130f04ea0cc7445
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48174979"
---
# <a name="using-collections"></a>Utilisation de collections
  Une collection est une liste d'objets construits à partir de la même classe d'objets et qui partagent le même objet parent. L'objet de collection contient toujours le nom du type d'objet avec le suffixe Collection. Par exemple, pour accéder aux colonnes dans une table spécifiée, utilisez le type d'objet <xref:Microsoft.SqlServer.Management.Smo.ColumnCollection>. Il contient tous les objets <xref:Microsoft.SqlServer.Management.Smo.Column> qui appartiennent au même objet <xref:Microsoft.SqlServer.Management.Smo.Table>.  
  
 Le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] `For...Each` instruction ou le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] `foreach` instruction peut être utilisée pour itérer sur chaque membre de la collection.  
  
## <a name="examples"></a>Exemples  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="referencing-an-object-by-using-a-collection-in-visual-basic"></a>Référence d'un objet à l'aide d'une collection en Visual Basic  
 Cet exemple de code montre comment définir une propriété de colonne à l’aide de la <xref:Microsoft.SqlServer.Management.Smo.TableViewTableTypeBase.Columns%2A>, <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A>, et <xref:Microsoft.SqlServer.Management.Smo.Server.Databases%2A> propriétés. Ces propriétés représentent des collections, qui peuvent être utilisées pour identifier un objet particulier lorsqu'elles sont utilisées avec un paramètre qui spécifie le nom de l'objet. Le nom et le schéma sont requis pour le <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> propriété d’objet de collection.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBCollections1](SMO How to#SMO_VBCollections1)]  -->  
  
## <a name="referencing-an-object-by-using-a-collection-in-visual-c"></a>Référence d'un objet à l'aide d'une collection en Visual C#  
 Cet exemple de code montre comment définir une propriété de colonne à l’aide de la <xref:Microsoft.SqlServer.Management.Smo.TableViewTableTypeBase.Columns%2A>, <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A>, et <xref:Microsoft.SqlServer.Management.Smo.Server.Databases%2A> propriétés. Ces propriétés représentent des collections, qui peuvent être utilisées pour identifier un objet particulier lorsqu'elles sont utilisées avec un paramètre qui spécifie le nom de l'objet. Le nom et le schéma sont requis pour le <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> propriété d’objet de collection.  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Modify a property using the Databases, Tables, and Columns collections to reference a column.   
srv.Databases("AdventureWorks2012").Tables("Person", "Person").Columns("LastName").Nullable = true;   
//Call the Alter method to make the change on the instance of SQL Server.   
srv.Databases("AdventureWorks2012").Tables("Person", "Person").Columns("LastName").Alter();   
}  
```  
  
## <a name="iterating-through-the-members-of-a-collection-in-visual-basic"></a>Parcours des membres d'une collection en Visual Basic  
 Cet exemple de code effectue une itération dans le <xref:Microsoft.AnalysisServices.Server.Databases%2A> affiche toutes les connexions à l’instance de base de données et la propriété de collection [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBCollections2](SMO How to#SMO_VBCollections2)]  -->  
  
## <a name="iterating-through-the-members-of-a-collection-in-visual-c"></a>Parcours des membres d'une collection en Visual C#  
 Cet exemple de code effectue une itération dans le <xref:Microsoft.AnalysisServices.Server.Databases%2A> affiche toutes les connexions à l’instance de base de données et la propriété de collection [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```  
//Connect to the local, default instance of SQL Server.   
{   
Server srv = default(Server);   
srv = new Server();   
int count = 0;   
int total = 0;   
//Iterate through the databases and call the GetActiveDBConnectionCount method.   
Database db = default(Database);   
foreach ( db in srv.Databases) {   
  count = srv.GetActiveDBConnectionCount(db.Name);   
  total = total + count;   
  //Display the number of connections for each database.   
  Console.WriteLine(count + " connections on " + db.Name);   
}   
//Display the total number of connections on the instance of SQL Server.   
Console.WriteLine("Total connections =" + total);   
}   
```  
  
  
