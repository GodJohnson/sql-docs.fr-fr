---
title: SET IDENTITY_INSERT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SET IDENTITY_INSERT
- SET_IDENTITY_INSERT_TSQL
- IDENTITY_INSERT_TSQL
- IDENTITY_INSERT
dev_langs:
- TSQL
helpviewer_keywords:
- IDENTITY_INSERT option
- SET IDENTITY_INSERT statement
- identity values [SQL Server], explicit values
- identity columns [SQL Server], explicit values
ms.assetid: a5dd49f2-45c7-44a8-b182-e0a5e5c373ee
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: d9ff472bed80096f0d7e10da2cc5019b3b31c399
ms.sourcegitcommit: b58d514879f182fac74d9819918188f1688889f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50970750"
---
# <a name="set-identityinsert-transact-sql"></a>SET IDENTITY_INSERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

> [!div class="nextstepaction"]
> [Participez à l’amélioration de la documentation SQL Server](https://80s3ignv.optimalworkshop.com/optimalsort/36yyw5kq-0)

Autorise l'insertion de valeurs explicites dans la colonne d'identité d'une table.  

 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET IDENTITY_INSERT [ [ database_name . ] schema_name . ] table_name { ON | OFF }  
```  
  
## <a name="arguments"></a>Arguments  
 *database_name*  
 Nom de la base de données qui contient la table spécifiée.  
  
 *schema_name*  
 Nom du schéma auquel appartient la table.  
  
 *table_name*  
 Nom de la table comportant une colonne d'identité.  
  
## <a name="remarks"></a>Notes   
 À n'importe quel moment, seule une table de la session peut avoir la propriété IDENTITY_INSERT activée (ON). Si la propriété d'une table est déjà activée lorsqu'une instruction SET IDENTITY_INSERT ON est émise pour une autre table, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne un message d'erreur signalant que la propriété SET IDENTITY_INSERT est déjà activée, en spécifiant la table correspondante.  
  
 Si la valeur insérée est supérieure à la valeur d'identité actuelle de la table, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise automatiquement la nouvelle valeur comme valeur d'identité actuelle.  
  
 L'option SET IDENTITY_INSERT est définie lors de l'exécution, et non pas durant l'analyse.  
  
## <a name="permissions"></a>Permissions  
 L'utilisateur doit posséder la table ou l'autorisation ALTER sur la table.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous crée une table comportant une colonne d'identité et montre comment l'option `SET IDENTITY_INSERT` peut être utilisée pour combler un vide dans les valeurs d'identité, résultant d'une instruction `DELETE`.  
  
```  
USE AdventureWorks2012;  
GO  
-- Create tool table.  
CREATE TABLE dbo.Tool(  
   ID INT IDENTITY NOT NULL PRIMARY KEY,   
   Name VARCHAR(40) NOT NULL  
);  
GO  
-- Inserting values into products table.  
INSERT INTO dbo.Tool(Name)   
VALUES ('Screwdriver')  
        , ('Hammer')  
        , ('Saw')  
        , ('Shovel');  
GO  
  
-- Create a gap in the identity values.  
DELETE dbo.Tool  
WHERE Name = 'Saw';  
GO  
  
SELECT *   
FROM dbo.Tool;  
GO  
  
-- Try to insert an explicit ID value of 3;  
-- should return a warning.  
INSERT INTO dbo.Tool (ID, Name) VALUES (3, 'Garden shovel');  
GO  
-- SET IDENTITY_INSERT to ON.  
SET IDENTITY_INSERT dbo.Tool ON;  
GO  
  
-- Try to insert an explicit ID value of 3.  
INSERT INTO dbo.Tool (ID, Name) VALUES (3, 'Garden shovel');  
GO  
  
SELECT *   
FROM dbo.Tool;  
GO  
-- Drop products table.  
DROP TABLE dbo.Tool;  
GO  
```  
  
## <a name="see-also"></a> Voir aussi  
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [IDENTITY, propriété &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql-identity-property.md)   
 [SCOPE_IDENTITY &#40;Transact-SQL&#41;](../../t-sql/functions/scope-identity-transact-sql.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [Instructions SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  
