---
title: Membres (String) (MDX) | Documents Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 302445cadc829de35eca28db2888aaa01673ca75
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34741898"
---
# <a name="members-string-mdx"></a>Members (String) (MDX)


  Retourne un membre spécifié par une expression de chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Members(Member_Name)   
```  
  
## <a name="arguments"></a>Arguments  
 *Member_Name*  
 Expression de chaîne valide qui spécifie un nom de membre.  
  
## <a name="remarks"></a>Notes  
 Le **membres (String)** fonction retourne un seul membre dont le nom est spécifié. En général, vous utilisez la **membres (String)** fonction avec des fonctions externes, en fournissant à la **membres (String)** fonction d’une chaîne qui identifie un membre, et le **membres (String)** fonction retourne la valeur de ce membre spécifié.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le **membres (String)** de fonction pour convertir la chaîne spécifiée à un membre valide, puis retourne la mesure par défaut pour le membre spécifié dans la chaîne. La chaîne spécifiée est entre guillemets simples. La mesure par défaut correspond à la mesure Reseller Sales Amount.  
  
```  
SELECT Members ('[Geography].[Geography].[Country].&[United States] ') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
