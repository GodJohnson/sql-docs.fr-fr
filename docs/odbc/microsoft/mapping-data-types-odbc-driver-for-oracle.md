---
title: Mappage des Types de données (pilote ODBC pour Oracle) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping data types [ODBC]
- data types [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], data types
ms.assetid: a5d9ce12-19da-4943-8493-e3d56fa08348
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ecdd7d7d4b597c4cae218e18b40b0f78e27a6bd5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47775807"
---
# <a name="mapping-data-types-odbc-driver-for-oracle"></a>Mappage des types de données (pilote ODBC pour Oracle)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Le serveur Oracle prend en charge un ensemble de types de données. Le pilote ODBC pour Oracle mappe ces types de données à leurs types de données ODBC SQL appropriés. Le tableau suivant répertorie les types de données Oracle 7.3 Server et leurs types de données ODBC SQL correspondants.  
  
 Le pilote ODBC pour Oracle prend en charge Oracle 7.3 et certains types de données Oracle8. Pour plus d’informations sur les types de données Oracle8 pris en charge, consultez [pris en charge les Types de données](../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md).  
  
|Type de données Oracle Server|Type de données SQL ODBC|  
|-----------------------------|------------------------|  
|CHAR|SQL_CHAR|  
|DATE|SQL_TIMESTAMP|  
|FLOAT|SQL_DOUBLE|  
|INTEGER|SQL_DECIMAL|  
|LONG|SQL_LONGVARCHAR|  
|LONG RAW|SQL_LONGVARBINARY|  
|NUMBER|SQL_DECIMAL|  
|RAW|SQL_VARBINARY|  
|VARCHAR2|SQL_VARCHAR|  
  
> [!NOTE]  
>  Pour plus d’informations sur la taille autorisée de la colonne VARCHAR, consultez [taille des colonnes VARCHAR](../../odbc/microsoft/varchar-column-size-odbc-driver-for-oracle.md) dans ce guide.
