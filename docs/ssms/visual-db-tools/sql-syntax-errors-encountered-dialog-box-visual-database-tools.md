---
title: Erreurs de syntaxe SQL, boîte de dialogue (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.sqlsyntaxerrorsencountered
- vdtsql.chm:69641
ms.assetid: bc9e5784-227e-4c5d-8084-24274fa6c14a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4f775e83915f6505e96bcb19205da4823267e1a0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47666773"
---
# <a name="sql-syntax-errors-encountered-dialog-box-visual-database-tools"></a>Erreurs de syntaxe SQL, boîte de dialogue (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Cette boîte de dialogue vous informe que le Concepteur ne peut pas analyser l'instruction SQL dans le volet SQL.  
  
Elle apparaît lorsque vous entrez ou modifiez une instruction SQL dans le volet SQL ; vous passez alors à un autre volet, vérifiez la requête ou tentez d'exécuter la requête, et l'une des conditions suivantes s'applique :  
  
-   L'instruction SQL est incomplète ou contient une ou plusieurs erreurs de syntaxe.  
  
-   L'instruction SQL est valide mais n'est pas prise en charge dans les volets graphiques (par exemple, une requête Union).  
  
-   L'instruction SQL est valide mais contient une syntaxe spécifique à la connexion de données que vous utilisez.  
  
> [!TIP]  
> Vous pouvez vérifier si une instruction est valide à l'aide du bouton **Vérifier la syntaxe SQL** situé dans la barre d'outils **Requête** .  
  
La boîte de dialogue affiche un message expliquant la raison pour laquelle l'instruction SQL ne peut pas être analysée. Cliquez sur **OK** pour continuer.  
  
## <a name="see-also"></a> Voir aussi  
[Rubriques de procédures relatives à la conception de requêtes et de vues &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
