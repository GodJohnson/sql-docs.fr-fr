---
title: STRING_SPLIT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STRING_SPLIT
- STRING_SPLIT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STRING_SPLIT function
ms.assetid: 3273dbf3-0b4f-41e1-b97e-b4f67ad370b9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: daad1b738030efa48d5a85f91b70ebf747d4702c
ms.sourcegitcommit: 9ece10c2970a4f0812647149d3de2c6b75713e14
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51812524"
---
# <a name="stringsplit-transact-sql"></a>STRING_SPLIT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

> [!div class="nextstepaction"]
> [Participez à l’amélioration de la documentation SQL Server](https://80s3ignv.optimalworkshop.com/optimalsort/36yyw5kq-0)

Fractionne l’expression de caractères à l’aide du séparateur spécifié.  
  
> [!NOTE]  
> La fonction **STRING_SPLIT** est disponible uniquement sous le niveau de compatibilité 130 et supérieur. Si votre niveau de compatibilité de base de données est inférieur à 130, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut pas trouver et exécuter la fonction **STRING_SPLIT**. Pour changer le niveau de compatibilité d’une base de données, consultez [Afficher ou changer le niveau de compatibilité d’une base de données](../../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md).
> Notez que le niveau de compatibilité 120 peut être le niveau par défaut même dans les nouvelles [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STRING_SPLIT ( string , separator )  
```  
  
## <a name="arguments"></a>Arguments  
 *chaîne*  
 [Expression](../../t-sql/language-elements/expressions-transact-sql.md) de n’importe quel type de caractère (par exemple, **nvarchar**, **varchar**, **nchar** ou **char**).  
  
 *separator*  
 [Expression](../../t-sql/language-elements/expressions-transact-sql.md) à caractère unique de n’importe quel type de caractère (par exemple, **nvarchar(1)**, **varchar(1)**, **nchar(1)** ou **char(1)**) qui est utilisée comme séparateur pour les chaînes concaténées.  
  
## <a name="return-types"></a>Types de retour  
 Retourne une table d’une seule colonne avec des fragments. Le nom de la colonne est **value**. Retourne **nvarchar** si un des arguments d’entrée est de type **nvarchar** ou **nchar**. Sinon, retourne **varchar**. La longueur du type de retour est identique à la longueur de l’argument de chaîne.  
  
## <a name="remarks"></a>Notes   
**STRING_SPLIT** accepte une chaîne qui doit être divisée et le séparateur qui sera utilisé pour diviser la chaîne. La fonction retourne une table d’une seule colonne avec des sous-chaînes. Par exemple, l’instruction suivante `SELECT value FROM STRING_SPLIT('Lorem ipsum dolor sit amet.', ' ');` qui utilise l’espace comme séparateur, retourne le tableau de résultats suivant :  
  
|valeur|  
|-----------|  
|Lorem|  
|ipsum|  
|dolor|  
|sit|  
|amet.|  
  
Si la chaîne d’entrée est **NULL**, la fonction table **STRING_SPLIT** retourne une table vide.  
  
**STRING_SPLIT** requiert au moins le mode de compatibilité 130.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-split-comma-separated-value-string"></a>A. Diviser une chaîne de valeurs séparées par des virgules  
Analysez une liste de valeurs séparées par des virgules et renvoyez tous les jetons non vides :  
  
```sql  
DECLARE @tags NVARCHAR(400) = 'clothing,road,,touring,bike'  
  
SELECT value  
FROM STRING_SPLIT(@tags, ',')  
WHERE RTRIM(value) <> '';  
```  
  
STRING_SPLIT retourne une chaîne vide si aucun élément ne figure entre les séparateurs. La condition RTRIM(value) <> '' supprime les jetons vides.  
  
### <a name="b-split-comma-separated-value-string-in-a-column"></a>B. Diviser une chaîne de valeurs séparées par des virgules dans une colonne  
La table de produits a une colonne avec une liste de balises séparées par des virgules, illustrée dans l’exemple suivant :  
  
|ProductId|Nom   |Balises|  
|---------------|----------|----------|  
|1|Full-Finger Gloves|clothing,road,touring,bike|  
|2|LL Headset|bike|  
|3|HL Mountain Frame|bike,mountain|  
  
La requête suivante transforme chaque liste de balises et les joint à la ligne d’origine :  
  
```sql  
SELECT ProductId, Name, value  
FROM Product  
    CROSS APPLY STRING_SPLIT(Tags, ',');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
|ProductId|Nom   |valeur|  
|---------------|----------|-----------|  
|1|Full-Finger Gloves|clothing|  
|1|Full-Finger Gloves|road|  
|1|Full-Finger Gloves|touring|  
|1|Full-Finger Gloves|bike|  
|2|LL Headset|bike|  
|3|HL Mountain Frame|bike|  
|3|HL Mountain Frame|mountain|  
  
### <a name="c-aggregation-by-values"></a>C. Agrégation par valeurs  
Les utilisateurs doivent créer un rapport qui indique le nombre de produits pour chaque balise, classés par nombre de produits, afin de filtrer uniquement les balises avec plus de deux produits.  
  
```sql  
SELECT value as tag, COUNT(*) AS [Number of articles]  
FROM Product  
    CROSS APPLY STRING_SPLIT(Tags, ',')  
GROUP BY value  
HAVING COUNT(*) > 2  
ORDER BY COUNT(*) DESC;  
```  
  
### <a name="d-search-by-tag-value"></a>D. Rechercher par valeur de balise  
Les développeurs doivent créer des requêtes qui recherchent les articles par mots clés. Ils peuvent utiliser les requêtes suivantes :  
  
Pour rechercher les produits avec une seule balise (clothing) :  
  
```sql  
SELECT ProductId, Name, Tags  
FROM Product  
WHERE 'clothing' IN (SELECT value FROM STRING_SPLIT(Tags, ','));  
```  
  
Recherchez les produits avec deux balises spécifiées (clothing et road) :  
  
```sql  
  
SELECT ProductId, Name, Tags  
FROM Product  
WHERE EXISTS (SELECT *  
    FROM STRING_SPLIT(Tags, ',')  
    WHERE value IN ('clothing', 'road');  
```  
  
### <a name="e-find-rows-by-list-of-values"></a>E. Rechercher des lignes par liste de valeurs  
Les développeurs doivent créer une requête qui recherche des articles selon une liste d’ID. Ils peuvent utiliser la requête suivante :  
  
```sql  
SELECT ProductId, Name, Tags  
FROM Product  
JOIN STRING_SPLIT('1,2,3',',')   
    ON value = ProductId;  
```  
  
Ceci constitue un remplacement pour un anti-patron courant, tel que la création d’une chaîne SQL dynamique dans la couche d’application ou [!INCLUDE[tsql](../../includes/tsql-md.md)], à l’aide de l’opérateur LIKE :  
  
```sql  
SELECT ProductId, Name, Tags  
FROM Product  
WHERE ',1,2,3,' LIKE '%,' + CAST(ProductId AS VARCHAR(20)) + ',%';  
```  
  
## <a name="see-also"></a> Voir aussi  
[LEFT &#40;Transact-SQL&#41;](../../t-sql/functions/left-transact-sql.md)     
[LTRIM &#40;Transact-SQL&#41;](../../t-sql/functions/ltrim-transact-sql.md)     
[RIGHT &#40;Transact-SQL&#41;](../../t-sql/functions/right-transact-sql.md)    
[RTRIM &#40;Transact-SQL&#41;](../../t-sql/functions/rtrim-transact-sql.md)     
[SUBSTRING &#40;Transact-SQL&#41;](../../t-sql/functions/substring-transact-sql.md)     
[TRIM &#40;Transact-SQL&#41;](../../t-sql/functions/trim-transact-sql.md)     
[Fonctions de chaîne &#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md)      
  
  
