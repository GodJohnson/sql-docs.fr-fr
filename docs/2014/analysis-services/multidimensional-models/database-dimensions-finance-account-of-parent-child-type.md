---
title: Créer un compte Finance de la Dimension de type parent-enfant | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], account
- account dimensions [Analysis Services]
- adding account intelligence
- account intelligence [Analysis Services]
ms.assetid: 2ba74e81-5b4b-407e-acdf-deb2f6accf0a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b92a974604852b8ca4f76c2bf3652a228cca0814
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48212369"
---
# <a name="create-a-finance-account-of-parent-child-type-dimension"></a>Créer un compte Finance de la dimension de type parent-enfant
  Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], une dimension de type compte est une dimension dont les attributs représentent un graphique de comptes utilisé à des fins de génération de rapports financiers.  
  
 Une dimension de comptes permet de gérer dans le temps et de manière sélective le comportement de l'agrégation dans les comptes. Un compte de dimensions permet également d'utiliser un mécanisme standard pour résoudre la plupart des problèmes d'agrégation non standard associés généralement aux solutions décisionnelles qui gèrent des données financières. Si vous ne disposiez pas d'un tel mécanisme standard, la résolution des problèmes d'agrégation non standard nécessiterait des formules de cumul personnalisées, des membres calculés ou des scripts d'expression multidimensionnelle (MDX, Multidimensional Expressions).  
  
 Pour définir une dimension comme une dimension de compte, affectez la `Type` propriété de la dimension à `Accounts`.  
  
## <a name="dimension-structure"></a>Structure de la dimension  
 Une dimension de comptes contient au moins deux attributs :  
  
-   Un attribut clé qui identifie les comptes individuels dans la table de la dimension de comptes.  
  
-   Un attribut de compte, un attribut parent qui décrit comment les comptes sont organisés hiérarchiquement dans la dimension de comptes.  
  
     Pour définir un attribut comme attribut de compte, affectez la `Type` propriété de l’attribut à `Account` et `Usage` propriété `Parent`.  
  
 Les dimensions de comptes peuvent éventuellement contenir les attributs suivants :  
  
-   Un attribut de type de compte qui définit le type de chacun des comptes de la dimension. Les noms des membres de l’attribut de type de compte sont associés aux types de comptes définis pour la base de données ou le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , et indiquent la fonction d’agrégation utilisée par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour ces comptes. Vous pouvez également utiliser des opérateurs unaires ou des formules de cumul personnalisées pour déterminer le comportement d'agrégation des attributs de comptes, mais les types de comptes permettent d'appliquer aisément un comportement cohérent à un graphique de comptes sans avoir à modifier la base de données relationnelle sous-jacente.  
  
     Pour définir un attribut de type de compte, affectez à la propriété `Type` de l'attribut la valeur `AccountType`.  
  
-   Un attribut de nom de compte qui est utilisé pour générer des rapports. Pour définir un attribut de nom de compte, affectez à la propriété `Type` de l'attribut la valeur `AccountName`.  
  
-   Un attribut de numéro de compte qui est utilisé pour générer des rapports. Vous identifiez un attribut de numéro de compte en définissant le `Type` propriété de l’attribut à `AccountNumber`.  
  
 Pour plus d’informations sur les types d’attributs, consultez [Configurer des types d’attributs](attribute-properties-configure-attribute-types.md).  
  
## <a name="adding-account-intelligence-with-the-business-intelligence-wizard"></a>Ajout de l'intelligence comptable avec l'Assistant Business Intelligence  
 Après avoir défini une dimension de comptes et ajouté la dimension à un cube, vous pouvez utiliser l’Assistant Business Intelligence pour ajouter des fonctions d’intelligence comptable, telles que l’identification et le mappage de types de comptes, à la dimension. Pour plus d’informations, consultez [Ajouter de l’intelligence comptable à une dimension](bi-wizard-add-account-intelligence-to-a-dimension.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs et hiérarchies d’attributs](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [L’Assistant Business Intelligence F1](../business-intelligence-wizard-f1-help.md)   
 [Types de dimensions](../multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md)  
  
  
