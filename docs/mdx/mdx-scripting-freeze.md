---
title: L’instruction FREEZE (MDX) | Documents Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cd652a9f308bd7a564a61d165f9c47875a900737
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34741968"
---
# <a name="mdx-scripting---freeze"></a>Écriture de scripts MDX - FIGER


  Verrouille à leur valeur actuelle les valeurs des cellules d'un sous-cube spécifié. Lorsque les cellules sont verrouillées, les modifications apportées à d'autres cellules n'ont aucun effet sur ces cellules verrouillées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
FREEZE Subcube_Expression   
```  
  
## <a name="arguments"></a>Arguments  
 *Subcube_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un sous-cube.  
  
## <a name="remarks"></a>Notes  
 Le **FIGER** instruction verrouille les valeurs des cellules dans un sous-cube spécifié, en empêchant les instructions suivantes dans MDX passe de script à partir de la modification de leurs valeurs dans le calcul ultérieurs.  
  
 Dans l'exemple suivant, A et B représentent des sous-cubes dans un script de calcul MDX :  
  
```  
B = 2;  
A = B;  
B = 3  
```  
  
 À ce stade, A et B équivalent à 3.  
  
 Nous insérons à présent le **Figer** fonction Verrouiller les cellules dans le sous-cube A :  
  
```  
B = 2;  
A = B;  
FREEZE(A);  
B = 3  
```  
  
 A équivaut désormais à 2 et B à 3.  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de script MDX &#40;MDX&#41;](../mdx/mdx-scripting-statements-mdx.md)  
  
  
