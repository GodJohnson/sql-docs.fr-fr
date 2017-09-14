---
title: DROP SCHEMA (Transact-SQL) | Documents Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 05/11/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP SCHEMA
- DROP_SCHEMA_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting schemas
- schemas [SQL Server], removing
- DROP SCHEMA statement
- dropping schemas
- removing schemas
ms.assetid: 874aa29e-c8ad-41e4-a672-900fdc58f1f6
caps.latest.revision: 51
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 584aea443e3263f44367ede24d7a59b8564e92c1
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="drop-schema-transact-sql"></a>DROP SCHEMA (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Permet de supprimer un schéma de la base de données.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
DROP SCHEMA  [ IF EXISTS ] schema_name  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DROP SCHEMA schema_name  
```  
  
## <a name="arguments"></a>Arguments  
 *S’IL EXISTE*  
 **S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Conditionnellement supprime le schéma uniquement s’il existe déjà.  
  
 *schema_name*  
 Nom sous lequel le schéma est connu dans la base de données.  
  
## <a name="remarks"></a>Notes  
 Le schéma à supprimer ne doit contenir aucun objet. Si le schéma contient des objets, l'instruction DROP échoue.  
  
 Informations sur les schémas sont visibles dans le [sys.schemas](../../relational-databases/system-catalog-views/schemas-catalog-views-sys-schemas.md) affichage catalogue.  
  
 **Attention**[!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'autorisation CONTROL sur le schéma ou l'autorisation ALTER ANY SCHEMA sur la base de données.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous commence avec une instruction `CREATE SCHEMA` unique. L'instruction crée le schéma `Sprockets`, qui est la propriété de `Krishna`, et une table `Sprockets.NineProngs`, puis accorde l'autorisation `SELECT` à `Anibal` et refuse l'autorisation `SELECT` à `Hung-Fu`.  
  
```  
CREATE SCHEMA Sprockets AUTHORIZATION Krishna   
    CREATE TABLE NineProngs (source int, cost int, partnumber int)  
    GRANT SELECT TO Anibal   
    DENY SELECT TO Hung-Fu;  
GO  
```  
  
 Les instructions ci-dessous permettent de supprimer le schéma. Notez que vous devez commencer par supprimer la table que contient le schéma.  
  
```  
DROP TABLE Sprockets.NineProngs;  
DROP SCHEMA Sprockets;  
GO  
```  
  
  
## <a name="see-also"></a>Voir aussi  
 [CRÉER des schémas &#40; Transact-SQL &#41;](../../t-sql/statements/create-schema-transact-sql.md)   
 [ALTER SCHEMA &#40; Transact-SQL &#41;](../../t-sql/statements/alter-schema-transact-sql.md)   
 [SUPPRIMER le schéma (Transact-SQL)](../../t-sql/statements/drop-schema-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
