---
title: Propriétés de la colonne (page Général) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.columnproperties.general.f1
ms.assetid: a745890b-994e-4c23-8028-5c83751e60c4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f73bbec32dc8f5d8d20e443428589a3aa45980ed
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48109897"
---
# <a name="column-properties-general-page"></a>Propriétés de la colonne (page Général)
  Utilisez cette page pour afficher les propriétés de la colonne sélectionnée.  
  
 Les informations de cette page sont en lecture seule. Pour modifier la colonne, fermez la boîte de dialogue **Propriétés de la colonne** , développez la table et les colonnes dans l’Explorateur d’objets, cliquez avec le bouton droit sur la colonne, puis cliquez sur **Conception**.  
  
## <a name="options"></a>Options  
 **Nom**  
 Nom de la colonne.  
  
 **Type de données**  
 Type de données susceptibles d'être contenues dans la colonne. S'il s'agit d'un type de données défini par l'utilisateur, il est affiché. S'il ne s'agit pas d'un type de données défini par l'utilisateur, le type de données système est affiché. Pour plus d’informations, consultez [Types de données &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).  
  
 **Type du système**  
 Type de données susceptibles d'être contenues dans la colonne. S'il s'agit d'un type de données système, il est affiché. S'il s'agit d'un type de données défini par l'utilisateur, le type de données système qui le constitue est affiché.  
  
 **Clé primaire**  
 Indique si la colonne est une clé primaire. Les valeurs possibles sont **True**et **False**.  
  
 **Null autorisé**  
 Indique si la colonne autorise les valeurs NULL. Les valeurs possibles sont **True** et **False**.  
  
 **Est calculé**  
 Indique si la valeur de la colonne est le résultat d'une expression calculée.  
  
 **Texte calculé**  
 Indique l'instruction utilisée pour calculer le texte de la colonne. Pour plus d’informations, consultez [Spécifier les colonnes calculées dans une table](specify-computed-columns-in-a-table.md).  
  
 **Identity**  
 Indique si la colonne est la colonne identité de la table. Les valeurs possibles sont **True** et **False**.  
  
 **Valeur initiale de la propriété identity**  
 Indique la valeur de ligne initiale d'une colonne d'identité.  
  
 **Incrément d'identité**  
 La propriété **Incrément d’identité** spécifie quelle valeur [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ajoute à la valeur d’identité de ligne existante la plus élevée pendant la génération de la valeur d’identité d’une ligne à insérer.  
  
 **Liaison par défaut**  
 Valeur par défaut de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui est liée à la colonne. Cette option est vide si aucune valeur par défaut n'est liée.  
  
 **Schéma par défaut**  
 Identifie le schéma de base de données qui possède la valeur par défaut liée à la colonne référencée. Cette option est vide si aucune valeur par défaut n'est liée.  
  
 **Règle**  
 Identifie la contrainte d'intégrité des données qui est liée à la colonne. Cette option est vide si aucune règle n'est liée.  
  
 **Schéma de règle**  
 Affiche le schéma de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui possède la règle liée à la colonne référencée. Cette option est vide si aucune règle n'est liée.  
  
 **Longueur**  
 Indique le nombre maximal de caractères ou d'octets accepté par la colonne.  
  
 **Classement**  
 Affiche le classement actuel de la colonne. Si cette option est vide, la colonne hérite de la propriété de classement de l'objet.  
  
 **Précision numérique**  
 Indique le nombre maximal de chiffres dans un type de données numériques à précision fixe.  
  
 **Échelle numérique**  
 Indique le nombre de chiffres à droite de la virgule décimale dans un type de données numériques à précision fixe.  
  
 **Espace de noms du schéma XML**  
 Définit le type de la colonne XML en terme de validation XSD (XML Schema Definition Language).  
  
 **Schéma d'espace de noms de schéma XML**  
 Schéma [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui possède l'espace de noms de schéma XML.  
  
> [!NOTE]  
>  Le mot schéma possède plusieurs significations courantes, mais distinctes. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise des schémas pour organiser des objets de base de données. Sa signification est similaire à celle de l'appartenance. XML utilise le schéma pour définir l'organisation des informations XML dans une série d'espaces de noms. Il s'agit d'un mode de regroupement du code XML connexe.  
  
 **Est partiellement alloué**  
 Indique si la colonne est une colonne éparse. Les valeurs possibles sont **True** et **False**. Pour plus d’informations, consultez [Utiliser des colonnes éparses](use-sparse-columns.md).  
  
 **Est un jeu de colonnes**  
 Indique si la colonne est un jeu de colonnes. Les valeurs possibles sont **True** et **False**. Pour plus d’informations, consultez [Utiliser des jeux de colonnes](use-column-sets.md).  
  
 **État de remplissage ANSI**  
 Indique si le remplissage ANSI est activé ou désactivé. Pour plus d’informations, consultez [SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql).  
  
 **Texte complet**  
 Indique si la colonne participe aux requêtes de texte intégral.  
  
 **Sémantique statistique**  
 Indique si la recherche sémantique statistique est activée pour la colonne. Pour plus d’informations, consultez [Recherche sémantique &#40;SQL Server&#41;](../search/semantic-search-sql-server.md).  
  
 **Pas pour la réplication**  
 Indique si la colonne est disponible pour la réplication. Les valeurs possibles sont **True** et **False**.  
  
  
