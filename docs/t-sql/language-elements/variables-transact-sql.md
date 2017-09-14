---
title: Variables (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 09/12/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: f372ae86-a003-40af-92de-fa52e3eea13f
caps.latest.revision: 12
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c77c323f8e9dbb2abc010c3fbc9e6d2b349c8ae1
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="variables-transact-sql"></a>Variables (Transact-SQL)
[!INCLUDE[tsql-appliesto-tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Une variable locale Transact-SQL est un objet qui peut contenir une valeur de données unique d’un type spécifique. Les variables contenues dans les traitements et les scripts sont généralement utilisées : 

* pour compter ou vérifier le nombre de fois qu'une boucle est réalisée ;
* pour retenir une valeur de données à tester par une instruction de contrôle de flux ;
* pour enregistrer une valeur de données que doit retourner le code de retour d'une procédure stockée ou la valeur de retour d'une fonction.

> [!NOTE]
> Les noms de certaines fonctions de système de Transact-SQL commencent par deux *à* signes (@@). Bien que dans les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le @@functions sont désignés comme des variables globales, elles ne sont pas des variables et n’ont pas le comportement en tant que variables. Le @@functions sont des fonctions système et leur syntaxe suit les règles pour les fonctions.

Le script suivant crée une petite table test et lui attribue 26 lignes. Il utilise une variable pour effectuer trois actions : 

* vérifier le nombre de lignes insérées en contrôlant combien de fois la boucle est exécutée ;
* fournir la valeur insérée dans la colonne INT ;
* faire partie de l'expression qui génère les lettres devant être insérées dans la colonne CHAR.  

```sql
-- Create the table.
CREATE TABLE TestTable (cola int, colb char(3));
GO
SET NOCOUNT ON;
GO
-- Declare the variable to be used.
DECLARE @MyCounter int;

-- Initialize the variable.
SET @MyCounter = 0;

-- Test the variable to see if the loop is finished.
WHILE (@MyCounter < 26)
BEGIN;
   -- Insert a row into the table.
   INSERT INTO TestTable VALUES
       -- Use the variable to provide the integer value
       -- for cola. Also use it to generate a unique letter
       -- for each row. Use the ASCII function to get the
       -- integer value of 'a'. Add @MyCounter. Use CHAR to
       -- convert the sum back to the character @MyCounter
       -- characters after 'a'.
       (@MyCounter,
        CHAR( ( @MyCounter + ASCII('a') ) )
       );
   -- Increment the variable to count this iteration
   -- of the loop.
   SET @MyCounter = @MyCounter + 1;
END;
GO
SET NOCOUNT OFF;
GO
-- View the data.
SELECT cola, colb
FROM TestTable;
GO
DROP TABLE TestTable;
GO
```

## <a name="declaring-a-transact-sql-variable"></a>Déclaration d'une variable Transact-SQL
L’instruction DECLARE initialise une variable Transact-SQL par : 
* Affectation d'un nom. Celui-ci doit avoir comme premier caractère un @ unique.
* Affectation d'un type de données système ou défini par l'utilisateur, ainsi que d'une taille. Pour les variables numériques, la précision et l'échelle doivent également être affectées. Pour les variables de type XML, une collection de schéma facultative peut être affectée.
* Affectation de la valeur NULL à la variable.

Par exemple, **DECLARE** instruction crée une variable locale nommée  **@mycounter**  avec un type de données int.  
```sql
DECLARE @MyCounter int;
```
Pour déclarer plusieurs variables locales, utilisez une virgule après la première variable locale définie, puis indiquez le nom et le type de données de la variable locale suivante.

Par exemple, **DECLARE** instruction crée trois variables locales nommées  **@LastName** ,  **@FirstName**  et  **@StateProvince** et la valeur NULL :  
```sql
DECLARE @LastName nvarchar(30), @FirstName nvarchar(20), @StateProvince nchar(2);
```

L’étendue d’une variable est les instructions de la plage de Transact-SQL qui peuvent faire référence à la variable. La portée d'une variable commence au point où elle est déclarée et se termine à la fin du traitement ou de la procédure stockée où elle est déclarée. Le script suivant, par exemple, génère une erreur de syntaxe car la variable est déclarée dans un lot et référencée dans un autre :  
```sql
USE AdventureWorks2014;
GO
DECLARE @MyVariable int;
SET @MyVariable = 1;
-- Terminate the batch by using the GO keyword.
GO 
-- @MyVariable has gone out of scope and no longer exists.

-- This SELECT statement generates a syntax error because it is
-- no longer legal to reference @MyVariable.
SELECT BusinessEntityID, NationalIDNumber, JobTitle
FROM HumanResources.Employee
WHERE BusinessEntityID = @MyVariable;
```

Les variables ont une portée locale et elles ne sont visibles que dans le traitement ou la procédure où elles sont définies. Dans l'exemple suivant, la portée imbriquée créée pour l'exécution de sp_executesql n'a pas accès à la variable déclarée dans la portée supérieure et elle retourne une erreur.  

```sql
DECLARE @MyVariable int;
SET @MyVariable = 1;
EXECUTE sp_executesql N'SELECT @MyVariable'; -- this produces an error
```

## <a name="setting-a-value-in-a-transact-sql-variable"></a>Affectation d'une valeur à une variable Transact-SQL

Quand une variable est déclarée pour la première fois, elle prend la valeur NULL. Pour affecter une valeur à une variable, utilisez l'instruction SET. C'est la méthode recommandée pour affecter une valeur à une variable. Il est également possible d'affecter une valeur à une variable en y faisant référence dans la liste de sélection d'une instruction SELECT.

Pour affecter une valeur à une variable à l'aide de l'instruction SET, indiquez le nom et la valeur à affecter à la variable. C'est la méthode recommandée pour affecter une valeur à une variable. Le lot suivant, par exemple, déclare deux variables, leur affecte une valeur et les utilise dans la clause `WHERE` d'une instruction `SELECT` :  

```sql
USE AdventureWorks2014;
GO
-- Declare two variables.
DECLARE @FirstNameVariable nvarchar(50),
   @PostalCodeVariable nvarchar(15);

-- Set their values.
SET @FirstNameVariable = N'Amy';
SET @PostalCodeVariable = N'BA5 3HX';

-- Use them in the WHERE clause of a SELECT statement.
SELECT LastName, FirstName, JobTitle, City, StateProvinceName, CountryRegionName
FROM HumanResources.vEmployee
WHERE FirstName = @FirstNameVariable
   OR PostalCode = @PostalCodeVariable;
GO
```

Vous pouvez également affecter une valeur à une variable en y faisant référence dans une liste de sélection. Si une variable est référencée dans une liste de sélection, une valeur scalaire doit lui être affectée, sinon l'instruction SELECT ne retournera qu'une seule ligne. Exemple :  

```sql
USE AdventureWorks2014;
GO
DECLARE @EmpIDVariable int;

SELECT @EmpIDVariable = MAX(EmployeeID)
FROM HumanResources.Employee;
GO
```

> [!WARNING]
> S'il y a plusieurs clauses d'affectation dans une seule instruction SELECT, SQL Server ne garantit pas l'ordre d'évaluation des expressions. Notez que les effets ne sont visibles que s'il existe des références parmi les affectations.

Si une instruction SELECT retourne plusieurs lignes et la variable fait référence à une expression non scalaire, la variable est définie à la valeur retournée par l’expression dans la dernière ligne du jeu de résultats. Par exemple, dans le lot suivant  **@EmpIDVariable**  est défini sur le **BusinessEntityID** de la dernière ligne retournée, c'est-à-dire 1 :  

```sql
USE AdventureWorks2014;
GO
DECLARE @EmpIDVariable int;

SELECT @EmpIDVariable = BusinessEntityID
FROM HumanResources.Employee
ORDER BY BusinessEntityID DESC;

SELECT @EmpIDVariable;
GO
```

## <a name="see-also"></a>Voir aussi  
 [Déclarer@local_variable](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
  
 [SET @local_variable](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
  
 [SÉLECTIONNEZ@local_variable](../../t-sql/language-elements/select-local-variable-transact-sql.md)  
  
  
