---
title: MIN_ACTIVE_ROWVERSION (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- MIN_ACTIVE_ROWVERSION
- MIN_ACTIVE_ROWVERSION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MIN_ACTIVE_ROWVERSION function [Transact-SQL]
ms.assetid: 87c89547-8ea1-4820-b75e-36be683e4e10
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 965a6508eb23cf26cc83be5a08d88b39db3d0068
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47670707"
---
# <a name="minactiverowversion-transact-sql"></a>MIN_ACTIVE_ROWVERSION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne la valeur **rowversion** active la plus basse dans la base de données active. Une valeur **rowversion** est active si elle est utilisée dans une transaction qui n'a pas encore été validée. Pour plus d’informations, consultez [rowversion &#40;Transact-SQL&#41;](../../t-sql/data-types/rowversion-transact-sql.md).  
  
> [!NOTE]  
>  Le type de données **rowversion** est aussi appelé **timestamp**.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
MIN_ACTIVE_ROWVERSION  
```  
  
## <a name="return-types"></a>Types de retour  
 Retourne une valeur **binary(8)**.  
  
## <a name="remarks"></a>Notes   
 MIN_ACTIVE_ROWVERSION est une fonction non déterministe qui retourne la valeur **rowversion** active la plus basse dans la base de données active. Une nouvelle valeur **rowversion** est générée en règle générale lorsqu'une insertion ou une mise à jour est effectuée sur une table qui contient une colonne de type **rowversion**. S’il n’y a pas de valeurs actives dans la base de données, MIN_ACTIVE_ROWVERSION retourne la même valeur que @@DBTS + 1.  
  
 MIN_ACTIVE_ROWVERSION est utile dans certains scénarios, par exemple dans le cadre de la synchronisation de données qui utilise des valeurs **rowversion** pour grouper des jeux de modifications. Si une application utilise @@DBTS au lieu de MIN_ACTIVE_ROWVERSION, il est possible de manquer des modifications qui sont actives au moment de la synchronisation.  
  
 La fonction MIN_ACTIVE_ROWVERSION n'est pas affectée par les modifications apportées aux niveaux d'isolation des transactions.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant retourne des valeurs **rowversion** à l’aide de `MIN_ACTIVE_ROWVERSION` et `@@DBTS`. Notez que les valeurs diffèrent lorsqu'il n'y a pas de transactions actives dans la base de données.  
  
```  
-- Create a table that has a ROWVERSION column in it.  
CREATE TABLE RowVersionTestTable (rv ROWVERSION)  
GO  
  
-- Print the current values for the database.  
PRINT ''  
PRINT 'DBTS'  
PRINT @@DBTS  
PRINT 'MIN_ACTIVE_ROWVERSION'  
PRINT MIN_ACTIVE_ROWVERSION()   
GO  
---------------- Results ----------------  
--DBTS  
--0x00000000000007E2  
--MIN_ACTIVE_ROWVERSION  
--0x00000000000007E3  
  
-- Insert a row.  
INSERT INTO RowVersionTestTable VALUES (DEFAULT)  
SELECT * FROM RowVersionTestTable  
GO  
---------------- Results ----------------  
--rv  
--0x00000000000007E3  
  
-- Print the current values for the database.  
PRINT ''  
PRINT 'DBTS'  
PRINT @@DBTS  
PRINT 'MIN_ACTIVE_ROWVERSION'  
PRINT MIN_ACTIVE_ROWVERSION()  
GO  
---------------- Results ----------------  
--DBTS  
--0x00000000000007E3  
--MIN_ACTIVE_ROWVERSION  
--0x00000000000007E4  
  
-- Insert a new row inside a transaction but do not commit.  
BEGIN TRAN  
INSERT INTO RowVersionTestTable VALUES (DEFAULT)  
SELECT * FROM RowVersionTestTable  
GO  
---------------- Results ----------------  
--rv  
--0x00000000000007E3  
--0x00000000000007E4  
  
-- Print the current values for the database.  
PRINT ''  
PRINT 'DBTS'  
PRINT @@DBTS  
PRINT 'MIN_ACTIVE_ROWVERSION'  
PRINT MIN_ACTIVE_ROWVERSION()   
GO  
---------------- Results ----------------  
--DBTS  
--0x00000000000007E4  
--MIN_ACTIVE_ROWVERSION  
--0x00000000000007E4  
  
-- Commit the transaction.  
COMMIT  
GO  
  
-- Print the current values for the database.  
PRINT ''  
PRINT 'DBTS'  
PRINT @@DBTS  
PRINT 'MIN_ACTIVE_ROWVERSION'  
PRINT MIN_ACTIVE_ROWVERSION()  
GO  
---------------- Results ----------------  
--DBTS  
--0x00000000000007E4  
--MIN_ACTIVE_ROWVERSION  
--0x00000000000007E5  
```  
  
## <a name="see-also"></a> Voir aussi  
 [@@DBTS &#40;Transact-SQL&#41;](../../t-sql/functions/dbts-transact-sql.md)   
 [rowversion &#40;Transact-SQL&#41;](../../t-sql/data-types/rowversion-transact-sql.md)  
  
  
