---
title: Créer et gérer des Perspectives (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.perspectivedb.f1
ms.assetid: 2a411c2b-2820-4086-ad7f-ce6a941fefc7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b6a8fb56ea065fea1a4077dcc1aae9ebc49d14da
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48121689"
---
# <a name="create-and-manage-perspectives-ssas-tabular"></a>Créer et gérer des perspectives (SSAS Tabulaire)
  Les perspectives définissent des sous-ensembles visualisables d'un modèle et des points de vue du modèle focalisés sur un domaine d'activité ou sur une application. Les tâches de cette rubrique décrivent comment créer et gérer des perspectives à l'aide de la boîte de dialogue **Perspectives** dans le générateur de modèles.  
  
 Cette rubrique inclut les tâches suivantes :  
  
-   [Pour ajouter une perspective](#bkmk_add)  
  
-   [Pour modifier une perspective](#bkmk_edit)  
  
-   [Pour renommer une perspective](#bkmk_rename)  
  
-   [Pour supprimer une perspective](#bkmk_delete)  
  
-   [Pour copier une perspective](#bkmk_copy)  
  
## <a name="tasks"></a>Tâches  
 Pour créer des perspectives, vous allez utiliser la boîte de dialogue **Perspectives** , dans laquelle vous pouvez ajouter, modifier, supprimer, copier et afficher des perspectives. Pour consulter la boîte de dialogue **Perspectives** , dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], cliquez sur le menu **Modèle** , puis sur **Perspectives**.  
  
###  <a name="bkmk_add"></a> Pour ajouter une perspective  
  
-   Pour ajouter une nouvelle perspective, cliquez sur **Nouvelle perspective**. Vous pouvez ensuite activer et désactiver les objets de champ de votre choix pour les inclure ou les exclure et ensuite donner un nom à la nouvelle perspective.  
  
     Si vous créez une perspective vide avec tous les champs d'objet, un utilisateur utilisant cette perspective verra une liste de champs vide. Les perspectives doivent contenir au moins une table et une colonne.  
  
###  <a name="bkmk_edit"></a> Pour modifier une perspective  
  
-   Pour modifier une perspective, activez et désactivez les champs de sa colonne pour ajouter et supprimer les objets correspondants dans la perspective.  
  
###  <a name="bkmk_rename"></a> Pour renommer une perspective  
  
-   Quand vous pointez sur l’en-tête de colonne d’une perspective (le nom de la perspective), le bouton **Renommer** apparaît. Pour renommer la perspective, cliquez sur **Renommer**, puis entrez un nouveau nom ou modifiez le nom existant.  
  
###  <a name="bkmk_delete"></a> Pour supprimer une perspective  
  
-   Quand vous pointez sur l’en-tête de colonne d’une perspective (le nom de la perspective), le bouton **Supprimer** apparaît. Pour supprimer la perspective, cliquez sur le bouton **Supprimer** , puis cliquez sur **Oui** dans la fenêtre de confirmation.  
  
###  <a name="bkmk_copy"></a> Pour copier une perspective  
  
-   Lorsque vous pointez sur l'en-tête de colonne d'une perspective, le bouton **Copier** apparaît. Pour créer une copie de cette perspective, cliquez sur le bouton **Copier** . Une copie de la perspective sélectionnée est ajoutée en tant que nouvelle perspective à droite des perspectives existantes. La nouvelle perspective hérite du nom de la perspective copiée et une annotation *- Copier* est ajoutée à la fin du nom. Par exemple, si une copie de la perspective *Ventes* est créée, la nouvelle perspective est appelée *Ventes – Copie*.  
  
## <a name="see-also"></a>Voir aussi  
 [Perspectives &#40;SSAS tabulaire&#41;](perspectives-ssas-tabular.md)   
 [Hiérarchies &#40;SSAS tabulaire&#41;](hierarchies-ssas-tabular.md)  
  
  
