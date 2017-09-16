---
title: "Type de curseur et d’accès concurrentiel combinaisons | Documents Microsoft"
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
- ODBC driver for Oracle [ODBC], concurrency options
- cursors [ODBC], ODBC driver for Oracle
- concurrency options [ODBC]
- ODBC driver for Oracle [ODBC], cursor options
ms.assetid: db63d610-f86f-4029-9d66-fed616c8a818
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a20223e272ce2790a8959df3d9f7ed318e700aef
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="cursor-type-and-concurrency-combinations"></a>Type de curseur et les combinaisons d’accès concurrentiel
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Types de curseurs contrôlent les fonctionnalités du curseur à l’utilisateur. Options d’accès concurrentiel contrôlent la mise à jour et le comportement de verrouillage d’un jeu de résultats.  
  
|Type de curseur|Accès concurrentiel (les valeurs autorisées)|  
|-----------------|------------------------------------|  
|SQL_CURSOR_FORWARD_ONLY|SQL_CONCUR_READ_ONLY|  
|SQL_CURSOR_STATIC|SQL_CONCUR_READ_ONLY|  
|SQL_CURSOR_KEYSET_DRIVEN<sup>[1]</sup>|SQL_CONCUR_READ_ONLY SQL_CONCUR_LOCK<sup>[2]</sup> SQL_CONCUR_VALUES|  
  
 <sup>[1] </sup> Consultez [Limitations d’utilisation de curseurs](../../odbc/microsoft/limitations-of-using-keyset-driven-cursors.md).  
  
 <sup>[2] </sup> SQL_CONCUR_LOCK est pris en charge uniquement lorsque l’option de connexion SQL_AUTOCOMMIT a la valeur SQL_AUTOCOMMIT_OFF.  
  
## <a name="see-also"></a>Voir aussi  
 [Les Options de connexion](../../odbc/microsoft/connect-options.md)