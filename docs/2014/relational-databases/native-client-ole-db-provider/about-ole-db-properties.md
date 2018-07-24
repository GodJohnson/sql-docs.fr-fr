---
title: À propos des propriétés OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, properties
- SQL Server Native Client OLE DB provider, properties
- properties [OLE DB]
- property values [SQL Server Native Client]
ms.assetid: 0b36a61e-b542-400d-a3d2-e6f643caf2c6
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e44a961cb2f4ab39dfba9550024925f141803058
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37422968"
---
# <a name="about-ole-db-properties"></a>À propos des propriétés OLE DB
  Les consommateurs définissent des valeurs de propriétés afin de demander un comportement d'objet spécifique. Par exemple, ils utilisent des propriétés pour spécifier les interfaces à exposer par un ensemble de lignes. Ils obtiennent les valeurs de propriétés afin de déterminer les capacités d'un objet, tel qu'un ensemble de lignes, une session ou un objet source de données.  
  
 Chaque propriété a une valeur, un type, une description et un attribut de lecture/écriture et, pour les propriétés d'ensemble de lignes, un indicateur signalant s'il peut être appliqué sur la base de chaque colonne.  
  
 Une propriété est identifiée par un GUID et un entier représentant l'ID de propriété. Un jeu de propriétés est un jeu de toutes les propriétés qui partagent le même GUID. Outre la propriété OLE DB prédéfinie définit, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif implémente une propriété spécifique au fournisseur définit les propriétés et dans les. Chaque propriété appartient à un ou plusieurs groupes de propriétés. Un groupe de propriétés est le groupe de toutes les propriétés qui s'appliquent à un objet particulier. Parmi les groupes de propriétés, on peut citer le groupe de propriétés d'initialisation, le groupe de propriétés de source de données, le groupe de propriétés de session, le groupe de propriétés d'ensemble de lignes, le groupe de propriétés de table et le groupe des propriétés de colonnes. Il y a des propriétés dans chacun de ces groupes de propriétés.  
  
 La définition de valeurs de propriétés implique les opérations suivantes  
  
1.  Détermination des propriétés pour lesquelles il faut définir des valeurs.  
  
2.  Détermination des jeux de propriétés qui contiennent les propriétés identifiées.  
  
3.  Allocation d'un tableau de structures DBPROPSET, une pour chaque jeu de propriétés identifié.  
  
4.  Allocation d'un tableau de structures DBPROP pour chaque jeu de propriétés. Le nombre d'éléments dans chaque tableau est le nombre de propriétés (identifiées à l'Étape 1) qui appartiennent à ce jeu de propriétés.  
  
5.  Remplissage de la structure DBPROP pour chaque propriété.  
  
6.  Remplissage des informations (GUID de jeu de propriétés, nombre d'éléments et un pointeur vers le tableau DBPROP correspondant) dans la structure DBPROPSET pour chaque jeu de propriétés.  
  
7.  Appel d'une méthode pour définir des propriétés et passer le nombre et le tableau de structures DBPROPSET.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’une Application de fournisseur SQL Server Native Client OLE DB](creating-a-sql-server-native-client-ole-db-provider-application.md)   
 [Propriétés (OLE DB)](http://go.microsoft.com/fwlink/?LinkId=112207)  
  
  