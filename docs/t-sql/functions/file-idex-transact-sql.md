---
title: FILE_IDEX (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- FILE_IDEX
- FILE_IDEX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- FILE_IDEX function
- IDs [SQL Server], files
- file IDs [SQL Server]
- names [SQL Server], files
- identification numbers [SQL Server], files
- file names [SQL Server], FILE_IDEX
ms.assetid: 7532fea5-ee5e-4edd-b98b-111a7ba56c8e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 89cd8bfb5a3098151565252e1a1fe5147c8aa6f9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47740667"
---
# <a name="fileidex-transact-sql"></a>FILE_IDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Cette fonction retourne le numéro d'identification (ID) du nom du fichier pour le nom logique spécifié d’un fichier journal, de données ou de texte intégral de la base de données active. 
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
FILE_IDEX ( file_name )  
```  
  
## <a name="arguments"></a>Arguments  
 *file_name*  
Une expression de type **sysname** qui retourne la valeur d’ID de fichier 'FILE_IDEX' pour le nom du fichier. 
  
## <a name="return-types"></a>Types de retour  
**Int**  
  
**NULL** en cas d’erreur  
  
## <a name="remarks"></a>Notes   
*file_name* correspond au nom de fichier logique affiché dans la colonne **name** des affichages catalogue [sys.master_files](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md) ou [sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md).  
  
Utilisez `FILE_IDEX` dans une liste SELECT, une clause WHERE, ou à n’importe quel emplacement prenant en charge une expression. Pour plus d’informations, consultez [Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md).  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-retrieving-the-file-id-of-a-specified-file"></a>A. Extraction de l'ID d'un fichier spécifié  
Cet exemple retourne l'ID du fichier `AdventureWorks_Data`.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT FILE_IDEX('AdventureWorks2012_Data') AS 'File ID';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
File ID   
-------   
1  
(1 row(s) affected)  
```  
  
### <a name="b-retrieving-the-file-id-when-the-file-name-is-not-known"></a>B. Extraction de l'ID d'un fichier dont le nom est inconnu  
Cet exemple retourne l'ID du fichier journal `AdventureWorks`. L’extrait de code Transact-SQL (T-SQL) sélectionne le nom du fichier logique à partir de l’affichage catalogue `sys.database_files`, où le type de fichier est égal à `1` (journal).  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT FILE_IDEX((SELECT TOP (1) name FROM sys.database_files WHERE type = 1)) AS 'File ID';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
File ID   
-------   
2  
```  
  
### <a name="c-retrieving-the-file-id-of-a-full-text-catalog-file"></a>C. Extraction de l'ID d'un fichier de catalogue de texte intégral  
Cet exemple retourne l’ID de fichier pour un fichier de texte intégral. L’extrait de code T-SQL sélectionne le nom du fichier logique à partir de l’affichage catalogue `sys.database_files`, où le type de fichier est égal à `4` (texte intégral). Ce code retourne 'NULL' s'il n'existe pas de catalogue de texte intégral.
  
```sql  
SELECT FILE_IDEX((SELECT name FROM sys.master_files WHERE type = 4))  
AS 'File_ID';  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Fonctions de métadonnées &#40;Transact-SQL&#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
  
