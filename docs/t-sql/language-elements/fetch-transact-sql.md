---
title: FETCH (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FETCH
- FETCH_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- FETCH statement
- cursors [SQL Server], fetching
- Transact-SQL cursors, fetching and scrolling
- retrieving rows
- fetching [SQL Server]
- SCROLL option
- row fetching [SQL Server]
ms.assetid: 5d68dac2-f91b-4342-bb4e-209ee132665f
caps.latest.revision: 43
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1333af6ceba4a4410fefadd1a99d8611fae88a6a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="fetch-transact-sql"></a>FETCH (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Récupère une ligne spécifique d'un curseur côté serveur [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
FETCH   
          [ [ NEXT | PRIOR | FIRST | LAST   
                    | ABSOLUTE { n | @nvar }   
                    | RELATIVE { n | @nvar }   
               ]   
               FROM   
          ]   
{ { [ GLOBAL ] cursor_name } | @cursor_variable_name }   
[ INTO @variable_name [ ,...n ] ]   
```  
  
## <a name="arguments"></a>Arguments  
 NEXT  
 Renvoie la ligne de résultats immédiatement après la ligne courante et incrémente cette dernière sur la ligne renvoyée. Si FETCH NEXT est la première extraction effectuée sur un curseur, cette instruction renvoie la première ligne dans le jeu de résultats. NEXT est l'option d'extraction du curseur par défaut.  
  
 PRIOR  
 Renvoie la ligne de résultats immédiatement avant la ligne courante, et décrémente cette dernière sur la ligne renvoyée. Si FETCH PRIOR est la première extraction effectuée sur un curseur, aucune ligne n'est renvoyée et le curseur reste placé avant la première ligne.  
  
 FIRST  
 Renvoie la première ligne dans le curseur et la transforme en ligne courante.  
  
 LAST  
 Renvoie la dernière ligne dans le curseur et la transforme en ligne courante.  
  
 ABSOLU {  *n* | @*nvar*}  
 Si  *n*  ou @*nvar* est un nombre positif, cela renvoie la ligne  *n*  depuis le début du curseur et transforme la ligne renvoyée à la nouvelle ligne actuelle. Si  *n*  ou @*nvar* est négatif, renvoie la ligne  *n*  avant la fin du curseur et transforme la ligne renvoyée de la nouvelle ligne actuelle. Si  *n*  ou @*nvar* est 0, aucune ligne n’est renvoyée. *n*doit être une constante entière et @*nvar* doit être **smallint**, **tinyint**, ou **int**.  
  
 RELATIF {  *n* | @*nvar*}  
 Si  *n*  ou @*nvar* est un nombre positif, cela renvoie la ligne  *n*  au-delà de la ligne actuelle et transforme la ligne renvoyée de la nouvelle ligne actuelle. Si  *n*  ou @*nvar* est négatif, renvoie la ligne  *n*  avant la ligne actuelle et transforme la ligne renvoyée nouvelle ligne actuelle. Si  *n*  ou @*nvar* est 0, retourne la ligne actuelle. Si FETCH RELATIVE est spécifiée avec  *n*  ou @*nvar* ne défini sur un nombre négatif ou égal à 0 lors de la première extraction effectuée sur un curseur, aucune ligne n’est retournée. *n*doit être une constante entière et @*nvar* doit être **smallint**, **tinyint**, ou **int**.  
  
 GLOBAL  
 Spécifie que *cursor_name* fait référence à un curseur global.  
  
 *tous les autres cas*  
 Nom du curseur ouvert grâce auquel s'effectue l'extraction. Si un global et un curseur local portent *cursor_name* comme leur nom, *cursor_name* au curseur global si GLOBAL est précisé et au curseur local si GLOBAL n’est pas spécifié.  
  
 @*nom_de_variable_de_curseur*  
 Nom d'une variable de curseur qui fait référence au curseur ouvert à partir duquel l'extraction doit être effectuée.  
  
 INTO @*nom_variable*[,...*n*]  
 Permet aux données issues des colonnes d'une extraction d'être placées dans des variables locales. Chaque variable de la liste (de gauche à droite) est associée à la colonne correspondante dans le jeu de résultats du curseur. Le type de données de chaque variable doit correspondre ou être une conversion implicite du type de données de la colonne du jeu de résultats correspondante. Le nombre de variables doit correspondre au nombre de colonnes dans la liste de sélection du curseur.  
  
## <a name="remarks"></a>Notes  
 Si l'option SCROLL n'est pas précisée dans une instruction DECLARE CURSOR de style ISO, NEXT est la seule option FETCH prise en charge. Si SCROLL est précisée dans une instruction DECLARE CURSOR de style ISO, toutes les options FETCH sont prises en charge.  
  
 Lorsque les extensions de curseur [!INCLUDE[tsql](../../includes/tsql-md.md)] DECLARE sont utilisées, les règles suivantes sont respectées :  
  
-   si FORWARD_ONLY ou FAST_FORWARD est précisé, NEXT est la seule option FETCH prise en charge ;  
  
-   si DYNAMIC, FORWARD_ONLY ou FAST_FORWARD ne sont pas précisés, et que KEYSET, STATIC ou SCROLL sont spécifiés, toutes les options FETCH sont prises en charge ;  
  
-   les curseurs DYNAMIC SCROLL prennent en charge toutes les options FETCH sauf ABSOLUTE.  
  
 Le @@FETCH_STATUS fonction signale l’état de la dernière instruction FETCH. Les mêmes informations sont enregistrées dans la colonne fetch_status du curseur renvoyé par sp_describe_cursor. Ces informations d'état doivent être utilisées pour déterminer la validité des données renvoyées par une instruction FETCH avant de tenter toute opération sur ces données. Pour plus d’informations, consultez [@@FETCH_STATUS &#40; Transact-SQL &#41; ](../../t-sql/functions/fetch-status-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Les autorisations FETCH reviennent par défaut à tous les utilisateurs valides.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-fetch-in-a-simple-cursor"></a>A. Utilisation de FETCH dans un curseur simple  
 L'exemple suivant déclare un curseur simple pour les lignes de la table `Person.Person` dont le nom commence par `B`, et il utilise `FETCH NEXT` pour parcourir les lignes. L'instruction `FETCH` renvoie la valeur de la colonne spécifiée dans `DECLARE CURSOR` comme un jeu de résultats sur une seule ligne.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE contact_cursor CURSOR FOR  
SELECT LastName FROM Person.Person  
WHERE LastName LIKE 'B%'  
ORDER BY LastName;  
  
OPEN contact_cursor;  
  
-- Perform the first fetch.  
FETCH NEXT FROM contact_cursor;  
  
-- Check @@FETCH_STATUS to see if there are any more rows to fetch.  
WHILE @@FETCH_STATUS = 0  
BEGIN  
   -- This is executed as long as the previous fetch succeeds.  
   FETCH NEXT FROM contact_cursor;  
END  
  
CLOSE contact_cursor;  
DEALLOCATE contact_cursor;  
GO  
```  
  
### <a name="b-using-fetch-to-store-values-in-variables"></a>B. Utilisation de FETCH pour stocker des valeurs dans des variables  
 L'exemple suivant ressemble au précédent, excepté que le résultat des instructions `FETCH` est stocké dans des variables locales au lieu d'être directement renvoyé au client. L'instruction `PRINT` combine les variables dans une chaîne unique et les renvoie au client.  
  
```  
USE AdventureWorks2012;  
GO  
-- Declare the variables to store the values returned by FETCH.  
DECLARE @LastName varchar(50), @FirstName varchar(50);  
  
DECLARE contact_cursor CURSOR FOR  
SELECT LastName, FirstName FROM Person.Person  
WHERE LastName LIKE 'B%'  
ORDER BY LastName, FirstName;  
  
OPEN contact_cursor;  
  
-- Perform the first fetch and store the values in variables.  
-- Note: The variables are in the same order as the columns  
-- in the SELECT statement.   
  
FETCH NEXT FROM contact_cursor  
INTO @LastName, @FirstName;  
  
-- Check @@FETCH_STATUS to see if there are any more rows to fetch.  
WHILE @@FETCH_STATUS = 0  
BEGIN  
  
   -- Concatenate and display the current values in the variables.  
   PRINT 'Contact Name: ' + @FirstName + ' ' +  @LastName  
  
   -- This is executed as long as the previous fetch succeeds.  
   FETCH NEXT FROM contact_cursor  
   INTO @LastName, @FirstName;  
END  
  
CLOSE contact_cursor;  
DEALLOCATE contact_cursor;  
GO  
```  
  
### <a name="c-declaring-a-scroll-cursor-and-using-the-other-fetch-options"></a>C. Déclaration d'un curseur SCROLL et utilisation des autres options FETCH  
 L'exemple suivant crée un curseur `SCROLL` pour autoriser des capacités de défilement complètes à travers les options `LAST`, `PRIOR`, `RELATIVE` et `ABSOLUTE`.  
  
```  
USE AdventureWorks2012;  
GO  
-- Execute the SELECT statement alone to show the   
-- full result set that is used by the cursor.  
SELECT LastName, FirstName FROM Person.Person  
ORDER BY LastName, FirstName;  
  
-- Declare the cursor.  
DECLARE contact_cursor SCROLL CURSOR FOR  
SELECT LastName, FirstName FROM Person.Person  
ORDER BY LastName, FirstName;  
  
OPEN contact_cursor;  
  
-- Fetch the last row in the cursor.  
FETCH LAST FROM contact_cursor;  
  
-- Fetch the row immediately prior to the current row in the cursor.  
FETCH PRIOR FROM contact_cursor;  
  
-- Fetch the second row in the cursor.  
FETCH ABSOLUTE 2 FROM contact_cursor;  
  
-- Fetch the row that is three rows after the current row.  
FETCH RELATIVE 3 FROM contact_cursor;  
  
-- Fetch the row that is two rows prior to the current row.  
FETCH RELATIVE -2 FROM contact_cursor;  
  
CLOSE contact_cursor;  
DEALLOCATE contact_cursor;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fermer &#40; Transact-SQL &#41;](../../t-sql/language-elements/close-transact-sql.md)   
 [DÉSALLOUER &#40; Transact-SQL &#41;](../../t-sql/language-elements/deallocate-transact-sql.md)   
 [DECLARE CURSOR &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-cursor-transact-sql.md)   
 [Ouvrir &#40; Transact-SQL &#41;](../../t-sql/language-elements/open-transact-sql.md)  
  
  