---
title: SQRT (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQRT function
- square root of given expression
ms.assetid: 54a75389-c501-4e22-87b8-905f66d6a3a5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 32d755dbf79a57552c73a79a3c8a1daad60dd208
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47608377"
---
# <a name="sqrt-ssis-expression"></a>SQRT (expression SSIS)
  Renvoie la racine carrée d'une expression numérique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SQRT(numeric_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *expression_numérique*  
 Expression numérique d'un type de données numérique. Pour plus d'informations, consultez [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Types des résultats  
 DT_R8  
  
## <a name="remarks"></a>Notes   
 La fonction SQRT renvoie un résultat NULL si l'argument est NULL.  
  
 Elle échoue si l'argument est une valeur négative.  
  
 L'argument est converti vers le type de données DT_R8 avant le calcul de la racine carrée.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L'exemple suivant renvoie la racine carrée d'un littéral numérique. Le résultat obtenu est 12.  
  
```  
SQRT(144)  
```  
  
 L'exemple suivant renvoie la racine carrée d'une expression, en l'occurrence le résultat de la soustraction des valeurs des colonnes **Value1** et **Value2** .  
  
```  
SQRT(Value1 - Value2)  
```  
  
 L'exemple suivant renvoie la longueur du troisième côté d'un triangle rectangle en appliquant la fonction SQUARE à deux variables puis en calculant la racine carrée de leur somme. Si la variable **Side1** a pour valeur 3 et que la variable **Side2** a pour valeur 4, la fonction SQRT renvoie 5.  
  
```  
SQRT(SQUARE(@Side1) + SQUARE(@Side2))  
```  
  
> [!NOTE]  
>  Dans les expressions, les noms de variables comportent toujours le préfixe \@.  
  
## <a name="see-also"></a> Voir aussi  
 [Fonctions &#40;expression SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
