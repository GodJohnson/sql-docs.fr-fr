---
title: SQLEndTran (bibliothèque de curseurs) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLEndTran function [ODBC], Cursor Library
ms.assetid: 92340b87-9084-4838-a509-e9ca22d5fd5c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e2e218035473d1ebb980aa5f44da8cc7b8ef843d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47827037"
---
# <a name="sqlendtran-cursor-library"></a>SQLEndTran (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Cette rubrique explique comment utiliser le **SQLEndTran** fonction dans la bibliothèque de curseurs. Pour des informations générales sur **SQLEndTran**, consultez [SQLEndTran, fonction](../../../odbc/reference/syntax/sqlendtran-function.md).  
  
 Ne prend pas en charge les transactions de la bibliothèque de curseurs et passe des appels aux **SQLEndTran** directement au pilote. Toutefois, la bibliothèque de curseurs ne prend pas en charge les comportements de curseur commit et rollback tel que retourné par la source de données avec les types d’informations SQL_CURSOR_ROLLBACK_BEHAVIOR et SQL_CURSOR_COMMIT_BEHAVIOR :  
  
-   Pour les sources de données qui conservent les curseurs entre les transactions, les modifications sont restaurées dans la source de données ne sont pas restaurées dans le cache de la bibliothèque de curseurs. Pour rendre le cache correspondent aux données dans la source de données, l’application doit fermer et rouvrir le curseur.  
  
-   Sources de données qui ferment les curseurs des limites de transaction, la bibliothèque de curseurs ferme les curseurs et supprime les caches pour toutes les instructions sur la connexion.  
  
-   Pour les sources de données qui suppriment des instructions préparées au niveau des limites de transaction, l’application doit reprepare toutes les instructions préparées sur la connexion avant de les réexécuter.
