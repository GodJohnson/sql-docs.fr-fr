---
title: "Fonction First (Générateur de rapports et SSRS) | Documents Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0914520-30c5-4d63-9b59-8d9342ed63b9
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: ce441af4558f4fc61dfa324803aa8c15e7d2abbb
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="report-builder-functions---first-function"></a>-Fonctions du Générateur de rapports First, fonction
  Retourne la première valeur dans l'étendue donnée de l'expression spécifiée.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
First(expression, scope)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *expression*  
 (**Variant** ou **Binaire**) Expression sur laquelle effectuer l’agrégation, par exemple `=Fields!FieldName.Value`.  
  
 *portée*  
 (**Chaîne**) Facultatif. Nom d'un dataset, d'un groupe ou d'une région de données qui contient les éléments de rapport auxquels appliquer la fonction d'agrégation. Si le paramètre *scope* n'est pas spécifié, l'étendue actuelle est utilisée.  
  
## <a name="return-type"></a>Type de retour  
 Déterminé par le type d'expression.  
  
## <a name="remarks"></a>Notes  
 La fonction **First** retourne la première valeur d'un jeu de données après que l'étendue spécifiée a été correctement triée et filtrée.  
  
 La fonction **First** ne peut être utilisée dans les expressions de filtre de groupe qu’avec l’étendue actuelle (par défaut).  
  
 Vous pouvez également utiliser **First** dans un en-tête de page pour retourner la première valeur de la collection **ReportItems** pour une page afin de produire des en-têtes de type dictionnaire qui affichent la première et la dernière entrées d’une page.  
  
 La valeur du paramètre *étendue* doit être une constante de chaîne et ne peut pas être une expression. Pour les agrégats externes ou les agrégats qui ne spécifient pas d'autres agrégats, le paramètre *scope* doit faire référence à l'étendue actuelle ou à une étendue contenante. Pour les agrégats d'agrégats, les agrégats imbriqués peuvent spécifier une étendue enfant.  
  
 *Expression* peut contenir des appels aux fonctions d'agrégation imbriquées avec les exceptions et conditions suivantes :  
  
-   Le paramètre*Scope* des agrégats imbriqués doit être identique à l'étendue de l'agrégat externe ou contenu par celle-ci. Pour toutes les étendues distinctes de l'expression, une étendue doit figurer dans une relation enfant avec toutes les autres étendues.  
  
-   Le paramètre*Scope* des agrégats imbriqués ne peut pas être le nom d'un dataset.  
  
-   *Expression* ne doit pas contenir les fonctions **First**, **Last**, **Previous**ou **RunningValue** .  
  
-   *Expression* ne doit pas contenir les agrégats imbriqués qui spécifient *recursive*.  
  
 Pour plus d’informations, consultez [Informations de référence sur les fonctions d’agrégation &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md) et [Étendue des expressions pour les totaux, les agrégats et les collections intégrées &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
 Pour plus d’informations sur les agrégats récursifs, consultez [Création de groupes de hiérarchies récursives &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## <a name="example"></a>Exemple  
 L'exemple de code ci-dessous retourne le premier numéro de produit du groupe `Category` d'une région de données :  
  
```  
=First(Fields!ProductNumber.Value, "Category")  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’expressions dans les rapports &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Exemples d’expressions &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Types de données dans les Expressions &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Étendue des expressions pour les totaux, les agrégats et les Collections intégrées &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  