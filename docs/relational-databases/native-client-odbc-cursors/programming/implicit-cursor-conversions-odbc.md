---
title: Conversions implicites de curseurs (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC cursors, implicit cursor conversions
- implicit cursor conversions
- cursors [ODBC], implicit cursor conversions
ms.assetid: fe29a58d-8448-4512-9ffd-b414784ba338
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: eebbfcefdf5c4c9e2d6ed1409e3c119f598a22d1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47600644"
---
# <a name="implicit-cursor-conversions-odbc"></a>Conversions de curseurs implicites (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Les applications peuvent demander un type de curseur via [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) , puis exécutez une instruction SQL qui n’est pas pris en charge par les curseurs de serveur du type demandé. Un appel à **SQLExecute** ou **SQLExecDirect** retourne SQL_SUCCESS_WITH_INFO et **SQLGetDiagRec** retourne :  
  
```  
szSqlState = "01S02", *pfNativeError = 0,  
szErrorMsg="[Microsoft][SQL Server Native Client] Cursor type changed"  
```  
  
 L’application peut déterminer quel type de curseur est maintenant utilisé en appelant **SQLGetStmtOption** définie avec la valeur SQL_CURSOR_TYPE. La conversion de type de curseur s'applique à une seule instruction. La prochaine **SQLExecDirect** ou **SQLExecute** sera effectuée en utilisant les paramètres de curseur d’instruction d’origine.  
  
## <a name="see-also"></a>Voir aussi  
 [Détails de programmation de curseurs &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-cursors/programming/cursor-programming-details-odbc.md)  
  
  
