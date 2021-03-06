---
title: Définir des groupes de membres | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- member groups [Analysis Services]
- grouping members
- DiscretizationMethod property
ms.assetid: 006cc915-c499-4781-b9a7-01ad31bebf6a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 389439143ddd5f56d565cdebff42a91e241e16fe
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48219339"
---
# <a name="define-member-groups"></a>Définir des groupes de membres
  Si un attribut possède un grand nombre de membres, vous pouvez décider de grouper ces membres dans des compartiments afin de réduire le nombre de membres visibles lorsque les utilisateurs parcourent les données d'une hiérarchie. Vous pouvez également déterminer le nombre de compartiments dans lesquels sont groupés les membres et définir un schéma d'attribution de noms pour les compartiments. Pour plus d’informations, consultez [Regrouper des membres d’un attribut &#40;discrétisation&#41;](attribute-properties-group-attribute-members.md).  
  
 Pour grouper les membres, vous devez configurer la propriété **DiscretizationMethod** à laquelle vous pouvez accéder par le biais de la fenêtre **Propriétés** dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Lorsque vous créez des groupes de membres, vos modifications ne sont pas mises à la disposition des utilisateurs avant le traitement de la dimension. Pour plus d’informations, consultez [traitement d’un objet de modèle multidimensionnel](processing-a-multidimensional-model-analysis-services.md).  
  
### <a name="to-create-member-groups"></a>Pour créer des groupes de membres  
  
1.  Ouvrez la dimension que vous voulez utiliser. L’onglet **Structure de dimension** s’ouvre par défaut.  
  
2.  Dans **Attributs**, cliquez avec le bouton droit sur l’attribut dont vous voulez grouper les membres, puis cliquez sur **Propriétés**.  
  
3.  Dans la liste déroulante à côté de **DiscretizationMethod**, sélectionnez la méthode à utiliser pour grouper les membres. Pour plus d’informations sur les paramètres de la propriété **DiscretizationMethod**, consultez [Regrouper des membres d’un attribut &#40;discrétisation&#41;](attribute-properties-group-attribute-members.md).  
  
  
