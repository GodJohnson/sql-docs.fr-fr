---
title: 'Tâche 2 : Mappage des colonnes Excel aux domaines DQS | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f347cc92-950f-4021-b7af-393640dfe821
caps.latest.revision: 6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 89be07ed1cdd07fc8cd923d9672147b87a165d71
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37202029"
---
# <a name="task-2-mapping-excel-columns-to-dqs-domains"></a>Tâche 2 : Mappage de colonnes d'Excel aux domaines DQS
    
1.  Dans la page **Mapper** , sélectionnez **Fichier Excel** pour **Source de données**.  
  
2.  Cliquez sur **Parcourir**, sélectionnez **Suppliers.xlsx**, puis cliquez sur **Open**.  
  
3.  Sélectionnez **IncomingSuppliers$** pour le **feuille de calcul**.  
  
4.  Mappez les colonnes comme indiqué dans le tableau suivant et dans la capture d'écran. Lors de la création de mappages pour le **état** domaine, cliquez sur **ajouter un mappage de colonnes** dans la barre d’outils située juste au-dessus de la liste.  
  
    > [!TIP]  
    >  Vous n’utilisez pas **ID du fournisseur** colonne/domaine pour le nettoyage. Vous utiliserez le **ID du fournisseur** domaine plus loin dans l’activité de correspondance.  
  
    |Colonne Excel|Domaine DQS|  
    |------------------|----------------|  
    |Nom du fournisseur|Nom du fournisseur|  
    |ContactEmailAddress|Adresse de messagerie|  
    |Adresse|Adresse|  
    |Ville|Ville|  
    |État|État|  
    |Pays (cliquez sur **+ (ajouter un mappage de colonnes)** la barre d’outils pour ajouter une ligne)|Pays|  
    |Code postal|Code postal|  
  
     ![Mappages de colonnes Excel aux domaines](../../2014/tutorials/media/et-mappingexcelcolumnstodqsdomains-01.jpg "mappages des colonnes Excel aux domaines")  
  
5.  Lorsque vous avez mappé tous les domaines individuels au sein de la **Validation d’adresses** domaine composite, le domaine composite participe automatiquement le processus de nettoyage. Cliquez sur **afficher/sélectionner des domaines composites** bouton pour voir que la **Validation d’adresses** domaine composite est automatiquement sélectionné, puis cliquez sur **OK**.  
  
     ![Boîte de dialogue Afficher/sélectionner des domaines composites](../../2014/tutorials/media/et-mappingexcelcolumnstodqsdomains-02.jpg "boîte de dialogue Afficher/sélectionner des domaines composites")  
  
6.  Cliquez sur **suivant** pour basculer vers le **nettoyer** page.  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 3 : Nettoyage des données dans la base de connaissances Fournisseurs](../../2014/tutorials/task-3-cleansing-data-against-the-suppliers-knowledge-base.md)  
  
  