---
title: Retour de données à partir d’une procédure stockée | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], returning data
- returning data from stored procedure
ms.assetid: 7a428ffe-cd87-4f42-b3f1-d26aa8312bf7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6b11f924ce5692378896f1fd7d50186861abf223
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48220529"
---
# <a name="return-data-from-a-stored-procedure"></a>Retour de données à partir d'une procédure stockée
  Il existe deux méthodes permettant de retourner des jeux de résultats ou des données d'une procédure vers un programme appelant : les paramètres de sortie et les codes de retour. Cette rubrique fournit des informations sur ces deux approches.  
  
## <a name="returning-data-using-an-output-parameter"></a>Retour de données à l'aide d'un paramètre de sortie  
 Si vous spécifiez le mot clé OUTPUT pour un paramètre dans la définition de procédure, la procédure peut retourner la valeur actuelle du paramètre au programme appelant lors de la sortie de la procédure. Pour enregistrer la valeur du paramètre dans une variable afin que le programme appelant puisse l'utiliser, ce dernier doit inclure le mot clé OUTPUT lorsqu'il exécute la procédure. Pour plus d’informations sur les types de données qui peuvent être utilisés comme paramètres de sortie, consultez [CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql).  
  
### <a name="examples-of-output-parameter"></a>Exemples de paramètre de sortie  
 L'exemple ci-dessous illustre une procédure avec un paramètre d'entrée et un paramètre de sortie. Le paramètre `@SalesPerson` doit recevoir une valeur d'entrée spécifiée par le programme appelant. L’instruction SELECT utilise la valeur passée dans le paramètre d’entrée pour obtenir la valeur `SalesYTD` correcte. L’instruction SELECT affecte également la valeur au paramètre de sortie `@SalesYTD` , qui retourne la valeur au programme appelant quand la procédure se termine.  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID('Sales.uspGetEmployeeSalesYTD', 'P') IS NOT NULL  
    DROP PROCEDURE Sales.uspGetEmployeeSalesYTD;  
GO  
CREATE PROCEDURE Sales.uspGetEmployeeSalesYTD  
@SalesPerson nvarchar(50),  
@SalesYTD money OUTPUT  
AS    
  
    SET NOCOUNT ON;  
    SELECT @SalesYTD = SalesYTD  
    FROM Sales.SalesPerson AS sp  
    JOIN HumanResources.vEmployee AS e ON e.BusinessEntityID = sp.BusinessEntityID  
    WHERE LastName = @SalesPerson;  
RETURN  
GO  
  
```  
  
 L’exemple suivant appelle la procédure créée dans le premier exemple et enregistre la valeur de sortie retournée par la procédure appelée dans la variable `@SalesYTD` , qui est locale pour le programme appelant.  
  
```  
-- Declare the variable to receive the output value of the procedure.  
DECLARE @SalesYTDBySalesPerson money;  
-- Execute the procedure specifying a last name for the input parameter  
-- and saving the output value in the variable @SalesYTDBySalesPerson  
EXECUTE Sales.uspGetEmployeeSalesYTD  
    N'Blythe', @SalesYTD = @SalesYTDBySalesPerson OUTPUT;  
-- Display the value returned by the procedure.  
PRINT 'Year-to-date sales for this employee is ' +   
    convert(varchar(10),@SalesYTDBySalesPerson);  
GO  
  
```  
  
 Des valeurs d'entrée peuvent également être définies pour les paramètres OUTPUT lorsque la procédure est exécutée. Ainsi, la procédure peut recevoir une valeur du programme appelant, la modifier ou l'utiliser pour exécuter des opérations, puis retourner la nouvelle valeur au programme appelant. Dans l’exemple précédent, la variable `@SalesYTDBySalesPerson` peut recevoir une valeur avant que le programme appelle la procédure `Sales.uspGetEmployeeSalesYTD` . L’instruction d’exécution passe alors la valeur de la variable `@SalesYTDBySalesPerson` au paramètre OUTPUT `@SalesYTD` . Ensuite, dans le corps de la procédure, la valeur peut être utilisée pour des calculs qui génèrent une nouvelle valeur. La nouvelle valeur est repassée hors de la procédure par le paramètre OUTPUT, mettant à jour la valeur dans la variable `@SalesYTDBySalesPerson` quand la procédure se termine. Ce mécanisme est souvent appelé « capacité de passage par référence ».  
  
 Si vous spécifiez OUTPUT pour un paramètre lorsque vous appelez une procédure alors que le paramètre n'est pas défini avec OUTPUT dans la définition de la procédure, vous obtiendrez un message d'erreur. Il est néanmoins possible d'exécuter une procédure avec des paramètres output et de ne pas spécifier OUTPUT lors de l'exécution de la procédure. Aucune erreur n'est retournée, mais vous ne pouvez pas utiliser la valeur de sortie dans le programme appelant.  
  
### <a name="using-the-cursor-data-type-in-output-parameters"></a>Utilisation du type de données Cursor dans des paramètres OUTPUT  
 [!INCLUDE[tsql](../../../includes/tsql-md.md)] les procédures peuvent utiliser le `cursor` uniquement pour les paramètres OUTPUT de type de données. Si le `cursor` type de données est spécifié pour un paramètre, mots clés VARYING et OUTPUT doivent être spécifiés pour ce paramètre dans la définition de procédure. Un paramètre peut être spécifié comme OUTPUT uniquement, mais si le mot clé VARYING est spécifié dans la déclaration de paramètre, le type de données doit être `cursor` et le mot clé OUTPUT doit également être spécifié.  
  
> [!NOTE]  
>  Le `cursor` type de données ne peut pas être lié à des variables d’application via les API comme OLE DB, ODBC, ADO et DB-Library de la base de données. Paramètres de sortie doivent être liés avant qu’une application puisse exécuter une procédure, les procédures avec `cursor` paramètres de sortie ne peut pas être appelées à partir de l’API de base de données. Ces procédures peuvent être appelées à partir de [!INCLUDE[tsql](../../../includes/tsql-md.md)] traitements, procédures, des déclencheurs ou uniquement lorsque le `cursor` variable de sortie est affectée à un [!INCLUDE[tsql](../../../includes/tsql-md.md)] local `cursor` variable.  
  
### <a name="rules-for-cursor-output-parameters"></a>Règles pour les paramètres de sortie de curseur  
 Les règles suivantes régissent `cursor` paramètres de sortie lorsque la procédure est exécutée :  
  
-   Dans le cas d'un curseur avant uniquement, les lignes renvoyées dans le jeu de résultats du curseur sont seulement celles situées au niveau de la position du curseur ou au-delà de celui-ci, à la fin de la procédure, par exemple :  
  
    -   Un curseur ne permettant pas le défilement est ouvert dans une procédure, dans un jeu de résultats de 100 lignes, appelé RS.  
  
    -   La procédure extrait les 5 premières lignes du jeu de résultats RS.  
  
    -   La procédure est renvoyée vers son appelant.  
  
    -   Le jeu de résultats RS renvoyé à l'appelant est constitué des lignes 6 à 100 de RS et le curseur dans l'appelant est placé avant la première ligne de RS.  
  
-   Dans le cas d'un curseur avant uniquement, si le curseur se trouve avant la première ligne lorsque la procédure existe, la totalité du jeu de résultats est renvoyée au traitement d'instructions, à la procédure ou au déclencheur appelant. Lorsqu'elle est renvoyée, la position du curseur est fixée au début de la première ligne.  
  
-   Dans le cas d'un curseur avant uniquement, si le curseur est placé au-delà de la fin de la dernière ligne lorsque la procédure existe, le système renvoie un jeu de résultats vide au traitement d'instructions, à la procédure ou au déclencheur appelant.  
  
    > [!NOTE]  
    >  Un jeu de résultats vide est différent d'une valeur NULL.  
  
-   Dans le cas d'un curseur permettant le défilement, toutes les lignes du jeu de résultats sont renvoyées au traitement d'instructions, à la procédure ou au déclencheur appelant lorsque la procédure existe. Lors du renvoi, la position du curseur est conservée à la position de la dernière extraction exécutée dans la procédure.  
  
-   Pour tous les types de curseur, si le curseur est fermé, une valeur NULL est repassée au traitement d'instructions, à la procédure ou au déclencheur appelant. Cette situation se produit également si un curseur est affecté à un paramètre mais qu'il n'a jamais été ouvert.  
  
    > [!NOTE]  
    >  L'état fermé n'a d'importance qu'au moment du retour. Par exemple, vous pouvez fermer un curseur au cours de l'exécution de la procédure, le rouvrir plus tard dans la procédure et renvoyer le jeu de résultats de ce curseur au traitement d'instructions, à la procédure ou au déclencheur appelant.  
  
### <a name="examples-of-cursor-output-parameters"></a>Exemples de paramètres de sortie de curseur  
 Dans l’exemple suivant, une procédure est créée qui a un paramètre de sortie `@currency`_`cursor` à l’aide de la `cursor` type de données. La procédure stockée est ensuite appelée dans un traitement.  
  
 Commencez par créer la procédure qui déclare puis ouvre un curseur dans la table Currency.  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ( 'dbo.uspCurrencyCursor', 'P' ) IS NOT NULL  
    DROP PROCEDURE dbo.uspCurrencyCursor;  
GO  
CREATE PROCEDURE dbo.uspCurrencyCursor   
    @CurrencyCursor CURSOR VARYING OUTPUT  
AS  
    SET NOCOUNT ON;  
    SET @CurrencyCursor = CURSOR  
    FORWARD_ONLY STATIC FOR  
      SELECT CurrencyCode, Name  
      FROM Sales.Currency;  
    OPEN @CurrencyCursor;  
GO  
  
```  
  
 Ensuite, exécutez un traitement d'instructions qui déclare une variable curseur locale, exécute la procédure pour affecter le curseur à la variable locale et extrait les lignes du curseur.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @MyCursor CURSOR;  
EXEC dbo.uspCurrencyCursor @CurrencyCursor = @MyCursor OUTPUT;  
WHILE (@@FETCH_STATUS = 0)  
BEGIN;  
     FETCH NEXT FROM @MyCursor;  
END;  
CLOSE @MyCursor;  
DEALLOCATE @MyCursor;  
GO  
  
```  
  
## <a name="returning-data-using-a-return-code"></a>Renvoi de données au moyen d'un code de retour  
 Une procédure peut retourner une valeur entière appelée « code de retour » pour indiquer l'état d'exécution d'une procédure. Le code de retour d'une procédure se définit au moyen de l'instruction RETURN. Comme dans le cas des paramètres OUTPUT, vous devez enregistrer le code de retour dans une variable lors de l'exécution de la procédure afin de pouvoir utiliser sa valeur dans le programme appelant. Par exemple, la variable d’attribution `@result` du type de données `int` est utilisé pour stocker le code de retour de la procédure `my_proc`, telles que :  
  
```  
DECLARE @result int;  
EXECUTE @result = my_proc;  
```  
  
 Les codes de retour sont couramment utilisés dans les blocs de contrôle de flux des procédures pour définir la valeur du code de retour pour chaque situation d'erreur possible. Vous pouvez utiliser la fonction @@ERROR après une instruction [!INCLUDE[tsql](../../../includes/tsql-md.md)] pour détecter si une erreur s’est produite pendant l’exécution de l’instruction.  
  
### <a name="examples-of-return-codes"></a>Exemples de codes de retour  
 L'exemple suivant illustre la procédure `usp_GetSalesYTD` de gestion d'erreurs qui définit les valeurs du code de retour pour diverses erreurs. Le tableau suivant montre la valeur entière attribuée par la procédure à chaque erreur possible, et la signification correspondante pour chaque valeur.  
  
|Valeur du code de retour|Signification|  
|-----------------------|-------------|  
|0|Exécution réussie.|  
|1|La valeur du paramètre nécessaire n'est pas spécifiée.|  
|2|Valeur du paramètre spécifiée non valide.|  
|3|Erreur lors de l'obtention de la valeur des ventes.|  
|4|Valeur des ventes NULL trouvée pour le vendeur.|  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID('Sales.usp_GetSalesYTD', 'P') IS NOT NULL  
    DROP PROCEDURE Sales.usp_GetSalesYTD;  
GO  
CREATE PROCEDURE Sales.usp_GetSalesYTD  
@SalesPerson nvarchar(50) = NULL,  -- NULL default value  
@SalesYTD money = NULL OUTPUT  
AS    
  
-- Validate the @SalesPerson parameter.  
IF @SalesPerson IS NULL  
   BEGIN  
       PRINT 'ERROR: You must specify a last name for the sales person.'  
       RETURN(1)  
   END  
ELSE  
   BEGIN  
   -- Make sure the value is valid.  
   IF (SELECT COUNT(*) FROM HumanResources.vEmployee  
          WHERE LastName = @SalesPerson) = 0  
      RETURN(2)  
   END  
-- Get the sales for the specified name and   
-- assign it to the output parameter.  
SELECT @SalesYTD = SalesYTD   
FROM Sales.SalesPerson AS sp  
JOIN HumanResources.vEmployee AS e ON e.BusinessEntityID = sp.BusinessEntityID  
WHERE LastName = @SalesPerson;  
-- Check for SQL Server errors.  
IF @@ERROR <> 0   
   BEGIN  
      RETURN(3)  
   END  
ELSE  
   BEGIN  
   -- Check to see if the ytd_sales value is NULL.  
     IF @SalesYTD IS NULL  
       RETURN(4)   
     ELSE  
      -- SUCCESS!!  
        RETURN(0)  
   END  
-- Run the stored procedure without specifying an input value.  
EXEC Sales.usp_GetSalesYTD;  
GO  
-- Run the stored procedure with an input value.  
DECLARE @SalesYTDForSalesPerson money, @ret_code int;  
-- Execute the procedure specifying a last name for the input parameter  
-- and saving the output value in the variable @SalesYTD  
EXECUTE Sales.usp_GetSalesYTD  
    N'Blythe', @SalesYTD = @SalesYTDForSalesPerson OUTPUT;  
PRINT N'Year-to-date sales for this employee is ' +  
    CONVERT(varchar(10), @SalesYTDForSalesPerson);  
  
```  
  
 L'exemple suivant crée un programme chargé de gérer les codes de retour retournés par la procédure `usp_GetSalesYTD` .  
  
```  
-- Declare the variables to receive the output value and return code   
-- of the procedure.  
DECLARE @SalesYTDForSalesPerson money, @ret_code int;  
  
-- Execute the procedure with a title_id value  
-- and save the output value and return code in variables.  
EXECUTE @ret_code = Sales.usp_GetSalesYTD  
    N'Blythe', @SalesYTD = @SalesYTDForSalesPerson OUTPUT;  
--  Check the return codes.  
IF @ret_code = 0  
BEGIN  
   PRINT 'Procedure executed successfully'  
   -- Display the value returned by the procedure.  
   PRINT 'Year-to-date sales for this employee is ' + CONVERT(varchar(10),@SalesYTDForSalesPerson)  
END  
ELSE IF @ret_code = 1  
   PRINT 'ERROR: You must specify a last name for the sales person.'  
ELSE IF @ret_code = 2   
   PRINT 'EERROR: You must enter a valid last name for the sales person.'  
ELSE IF @ret_code = 3  
   PRINT 'ERROR: An error occurred getting sales value.'  
ELSE IF @ret_code = 4  
   PRINT 'ERROR: No sales recorded for this employee.'     
GO  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql)   
 [PRINT &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/print-transact-sql)   
 [SET @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/set-local-variable-transact-sql)   
 [Curseurs](../cursors.md)   
 [RETURN &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/return-transact-sql)   
 [@@ERROR &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-transact-sql)  
  
  
