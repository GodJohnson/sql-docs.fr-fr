---
title: Boîte de dialogue Tables et colonnes (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.tablesandcolumns
ms.assetid: 8cf27be1-e66d-4735-a428-9ab4b33af4f5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d0eebfee19ff2a110ba829a6ef3b976cc1d75e0e
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51703398"
---
# <a name="tables-and-columns-dialog-box-visual-database-tools"></a>Boîte de dialogue Tables et colonnes (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Utilisez cette boîte de dialogue pour mapper une clé primaire dans une table à une clé étrangère dans une autre. Pour accéder à cette boîte de dialogue, dans le menu **Concepteur de tables** , cliquez sur **Relations**. Dans la boîte de dialogue **Relations de clé étrangère** , cliquez sur le champ **Spécification de tables et colonnes** , puis cliquez sur le bouton de sélection **(…)** situé à droite de la propriété.  
  
> [!NOTE]  
> Si la table est publiée pour réplication, vous devez apporter vos modifications au schéma à l'aide de l'instruction Transact-SQL [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) ou de SMO (SQL Server Management Objects). Lorsque les modifications sont apportées au schéma à l'aide du Concepteur de tables ou du Concepteur de schémas de base de données, celui-ci tente d'abandonner la table et de la recréer. Toutefois, il est impossible d'abandonner les objets publiés, par conséquent les modifications du schéma échoueront.  
  
## <a name="options"></a>Options  
**Nom de la relation**  
Indique le nom de la relation.  
  
**Table de clé primaire**  
Répertorie les tables contenues dans la base de données. Choisissez la table qui se trouvera du côté clé primaire de la relation.  
  
**Table de clé étrangère**  
Affiche la table située du côté clé étrangère de la relation. Il s'agit de la table actuellement sélectionnée dans le Concepteur de tables.  
  
**Grille sous la table de clé primaire**  
Répertorie les colonnes de la table sélectionnées dans la liste **Table de clé primaire** . Entrez les colonnes qui contribuent à la clé primaire de cette table.  
  
**Grille sous la table de clé étrangère**  
Répertorie les colonnes de la table sélectionnées dans la liste **Table de clé étrangère** . Entrez la colonne clé étrangère de la table de clé étrangère qui correspond à la colonne clé primaire.  
  
> [!NOTE]  
> Les colonnes que vous choisissez pour la clé étrangère doivent posséder le même type de données que les colonnes primaires auxquelles elles correspondent. Il doit exister un nombre égal de colonnes dans chacune des clés. Par exemple, si la clé primaire de la table située du côté clé primaire de la relation est composée de deux colonnes, vous devez faire correspondre chacune de ces colonnes à une colonne de la table située du côté clé étrangère de la relation.  
  
## <a name="see-also"></a> Voir aussi  
[Procédure : créer des relations entre tables (Visual Database Tools)](https://msdn.microsoft.com/867a54b8-5be4-46e6-9702-49ae6dabf67c)  
  
