---
title: "Défilement et extraction des lignes | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-cursors
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- scrollable cursors [SQL Server]
- SQL Server Native Client ODBC driver, cursors
- SQLFetchScroll function
- ODBC applications, cursors
- cursors [ODBC], fetching rows
- ODBC cursors, fetching rows
- cursors [ODBC], scrolling rows
- fetching [ODBC]
- ODBC cursors, scrolling rows
ms.assetid: 9109f10d-326b-4a6d-8c97-831f60da8c4c
caps.latest.revision: "34"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7e70bf91967d4a2ab19e8c6e37a1b4c816a26a37
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="scrolling-and-fetching-rows"></a>Défilement et extraction de lignes
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Pour utiliser un curseur permettant le défilement, une application ODBC doit :  
  
-   Définir les fonctionnalités de curseur à l’aide de [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
-   Ouvrez le curseur à l’aide de **SQLExecute** ou **SQLExecDirect**.  
  
-   Faire défiler et extraire des lignes à l’aide de **SQLFetch** ou [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md).  
  
 Les deux **SQLFetch** et **SQLFetchScroll** peut extraire des blocs de lignes à la fois. Le nombre de lignes retourné est spécifié à l’aide de **SQLSetStmtAttr** pour définir le paramètre SQL_ATTR_ROW_ARRAY_SIZE.  
  
 Les applications ODBC peuvent utiliser **SQLFetch** pour extraire un curseur avant uniquement.  
  
 **SQLFetchScroll** est utilisé pour faire défiler un curseur. **SQLFetchScroll** prend en charge l’extraction de la suivante, précédente, première et dernière ensembles de lignes en plus de l’extraction relative (extraire l’ensemble de lignes  *n*  lignes à partir du début de l’ensemble de lignes en cours) et l’extraction absolue (extraire l’ensemble de lignes en commençant à la ligne  *n* ). Si  *n*  est négatif dans une extraction absolue, les lignes sont comptées à partir de la fin du jeu de résultats. Une extraction absolue de ligne -1 équivaut à l'extraction de l'ensemble de lignes qui démarre à la dernière ligne du jeu de résultats.  
  
 Les applications qui utilisent **SQLFetchScroll** son bloc des fonctionnalités de curseur, tels que les rapports, sont susceptibles de transmettre le jeu de résultats d’une seule fois, à l’aide de l’option uniquement pour extraire l’ensemble de lignes suivant. Applications basées sur l’écran, en revanche, peuvent tirer parti de toutes les fonctions de **SQLFetchScroll**. Si l’application définit la taille de l’ensemble de lignes sur le nombre de lignes affichées sur l’écran et lie les mémoires tampon d’écran au jeu de résultats, il peut traduire directement à des appels à des opérations de barre de défilement **SQLFetchScroll**.  
  
|Opération de barre de défilement|Option de défilement SQLFetchScroll|  
|--------------------------|-------------------------------------|  
|Page précédente|SQL_FETCH_PRIOR|  
|Pg. suiv|SQL_FETCH_NEXT|  
|Ligne précédente|SQL_FETCH_RELATIVE avec FetchOffset égal à -1|  
|Ligne suivante|SQL_FETCH_RELATIVE avec FetchOffset égal à 1|  
|Case de défilement vers le haut|SQL_FETCH_FIRST|  
|Case de défilement vers le bas|SQL_FETCH_LAST|  
|Position aléatoire de la case de défilement|SQL_FETCH_ABSOLUTE|  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Lignes de signets dans ODBC](../../relational-databases/native-client-odbc-cursors/scrolling-and-fetching-rows-bookmarking-rows-in-odbc.md)  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de curseurs &#40; ODBC &#41;](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  