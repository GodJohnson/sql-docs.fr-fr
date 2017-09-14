---
title: "Mapper des paramètres de requête à des Variables dans un composant de flux de données | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- queries [Integration Services], parameter mapping
- parameters [Integration Services]
- mapping query parameters to variables [Integration Services]
- variables [Integration Services], mapping parameters to
ms.assetid: 5e26977c-758c-46d6-acf1-4fd9238f0950
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: da9367a56cefbb37244d4a47543b93586e7e8870
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="map-query-parameters-to-variables-in-a-data-flow-component"></a>Mapper des paramètres de requête à des variables dans un composant de flux de données
  Lorsque vous configurez la source OLE DB pour utiliser des requêtes paramétrables, vous pouvez mapper les paramètres à des variables.  
  
 La source OLE DB utilise des requêtes paramétrables pour filtrer les données lorsqu'elle se connecte à une source de données.  
  
### <a name="to-map-a-query-parameter-to-a-variable"></a>Pour mapper un paramètre de requête à une variable  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l'onglet **Flux de données** , puis dans la **Boîte à outils**, faites glisser la source OLE DB sur l'aire de conception.  
  
4.  Cliquez avec le bouton droit sur la source OLE DB, puis cliquez sur **Modifier**.  
  
5.  Dans l' **Éditeur de source OLE DB**, choisissez un gestionnaire de connexions OLE DB à utiliser pour se connecter à la source de données ou cliquez sur **Nouveau** pour créer un gestionnaire de connexions OLE DB.  
  
6.  Sélectionnez l'option **Commande SQL** comme mode d'accès aux données, puis tapez une requête paramétrable dans le volet **Texte de la commande SQL** .  
  
7.  Cliquez sur **Paramètres**.  
  
8.  Dans le **définition des paramètres de requête** boîte de dialogue zone, mappez chaque paramètre dans le **paramètres** liste à une variable dans le **Variables** liste ou créez une nouvelle variable en cliquant sur  **\<nouvelle variable >**. Cliquez sur **OK**.  
  
    > [!NOTE]  
    >  Seules les variables système et les variables définies par l'utilisateur qui se trouvent dans l'étendue du package, dans un conteneur parent tel qu'une boucle Foreach ou dans la tâche de flux de données contenant le composant de flux de données, peuvent être mappées. La variable doit avoir un type de données compatible avec la colonne de la clause WHERE à laquelle le paramètre est affecté.  
  
9. Vous pouvez cliquer sur **Aperçu** pour afficher jusqu'à 200 lignes de données renvoyées par la requête.  
  
10. Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
## <a name="see-also"></a>Voir aussi  
 [Source OLE DB](../../integration-services/data-flow/ole-db-source.md)   
 [Transformation de recherche](../../integration-services/data-flow/transformations/lookup-transformation.md)  
  
  