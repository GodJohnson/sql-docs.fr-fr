---
title: SQLSetScrollOptions (le pilote ODBC Visual FoxPro) | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 693e6e28-a845-41b1-9622-5058b0d87229
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 63efd04bc43855c08a6de02d5396bea45eabbc68
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetscrolloptions-visual-foxpro-odbc-driver"></a>SQLSetScrollOptions (le pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [référence de l’API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : partielle  
  
 Conformité d’API ODBC : Niveau 2  
  
 Définit les options qui contrôlent le comportement des curseurs associé à un descripteur d’instruction, *hstmt*.  
  
 Le pilote ODBC Visual FoxPro prend en charge uniquement la valeur SQL_CONCUR_READ_ONLY ; Il ne prend pas en charge la *fConcurrency* SQL_CONCUR_ROWVER de valeur. Le pilote convertit SQL_KEYSET_SIZE type SQL_CURSOR_DYNAMIC et SQL_CURSOR_KEYSET_DRIVEN SQL_SCROLL_STATIC avec l’avertissement ODBC_01S02.  
  
 Pour plus d’informations, consultez [SQLSetScrollOptions](../../odbc/reference/syntax/sqlsetscrolloptions-function.md) dans les *de référence du programmeur ODBC*.