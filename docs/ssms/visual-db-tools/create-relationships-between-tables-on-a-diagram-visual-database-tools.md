---
title: Créer des relations entre des tables sur un diagramme | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- diagrams [SQL Server], designing
ms.assetid: 28e9630c-dff4-46cc-bb0e-fe77998b6ac2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 657118f6b10b32d85f9020f01d95bf12eecb4498
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51701137"
---
# <a name="create-relationships-between-tables-on-a-diagram-visual-database-tools"></a>Créer des relations entre des tables sur un diagramme (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Vous pouvez créer des relations entre des colonnes dans différentes tables dans le Concepteur de diagrammes en faisant glisser les colonnes entre les tables.  
  
### <a name="to-create-a-relationship-graphically"></a>Pour créer une relation sous forme de graphique  
  
1.  Dans le Concepteur de diagrammes, cliquez sur le sélectionneur de ligne d'une ou de plusieurs colonnes de base de données que vous souhaitez associer à une colonne dans une autre table.  
  
2.  Faites glisser la ou les colonne(s) sélectionnée(s) vers la table associée.  
  
3.  Deux boîtes de dialogue s’ouvre : **Relation de clé étrangère** et **Tables et colonnes**, cette dernière apparaissant au premier plan.  
  
4.  Le**nom de relation** a une nom fourni par le système au format FK_*localtable*_*foreigntable*. Vous pouvez modifier cette valeur.  
  
5.  Vérifiez que la **table de clé primaire** spécifie la bonne table.  
  
6.  La grille affiche les colonnes locales et leurs colonnes étrangères correspondantes. Vous pouvez ajouter ou supprimer des colonnes de table ou modifier les mappages.  
  
7.  Choisissez **OK**.  
  
    La boîte de dialogue **Relation de clé étrangère** s’ouvre. La**Relation sélectionnée** affiche la relation créée.  
  
8.  Modifiez les propriétés de la relation dans la grille.  
  
9. Choisissez **OK** pour créer la relation.  
  
    Le Concepteur de base de données affiche une relation entre les colonnes que vous avez choisies.  
  
## <a name="see-also"></a> Voir aussi  
[Boîte de dialogue Tables et colonnes &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/tables-and-columns-dialog-box-visual-database-tools.md)  
[Utilisation des contraintes (Visual Database Tools)](https://msdn.microsoft.com/637098af-2567-48f8-90f4-b41df059833e)  
[Utiliser des tables dans les schémas de base de données &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/work-with-tables-in-database-diagram-visual-database-tools.md)  
  
