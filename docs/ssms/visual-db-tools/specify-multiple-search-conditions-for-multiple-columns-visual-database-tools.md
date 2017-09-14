---
title: "Spécifier plusieurs conditions de recherche pour plusieurs colonnes (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- search criteria [SQL Server], multiple conditions
- multiple search conditions
- search conditions [SQL Server], multiple
- OR operator
- AND, Criteria pane
ms.assetid: 06617729-0d0b-4da2-9890-b7e2f5cdbc7b
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 041d9a3c2a204d8413d755ec69946859195b5c0a
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="specify-multiple-search-conditions-for-multiple-columns-visual-database-tools"></a>Spécifier plusieurs conditions de recherche pour plusieurs colonnes (Visual Database Tools)
Vous pouvez élargir ou restreindre l'étendue de votre requête en incluant plusieurs colonnes de données à votre condition de recherche. Vous pouvez, par exemple, souhaiter effectuer les opérations suivantes :  
  
-   Rechercher des employés travaillant depuis plus de cinq ans dans la société ou occupant certains postes  
  
-   Rechercher un livre qui est publié par un éditeur spécifique et qui appartient au domaine de la cuisine  
  
Pour créer une requête recherchant des valeurs dans l'une des deux colonnes (voire plus), spécifiez la condition OR. Pour créer une requête répondant à l'ensemble des conditions dans deux colonnes (voire plus), spécifiez la condition AND.  
  
## <a name="specifying-an-or-condition"></a>Spécification d'une condition OR  
Pour créer plusieurs conditions reliées à l'aide de l'opérateur OR, indiquez chacune des conditions dans une colonne différente du volet Critères.  
  
#### <a name="to-specify-an-or-condition-for-two-different-columns"></a>Pour spécifier une condition OR pour deux colonnes différentes  
  
1.  Dans le [volet Critères](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md), ajoutez les colonnes dans lesquelles vous souhaitez effectuer la recherche.  
  
2.  Dans la colonne **Filtre** de la première colonne dans laquelle vous souhaitez effectuer la recherche, spécifiez la première condition.  
  
3.  Dans la colonne **Ou...** de la deuxième colonne de données dans laquelle vous souhaitez effectuer la recherche, spécifiez la deuxième condition, tout en laissant la colonne **Filtre** vide.  
  
    Le Concepteur de requêtes et de vues crée une clause WHERE comportant une condition OR de ce type :  
  
    ```  
    SELECT job_lvl, hire_date  
    FROM employee  
    WHERE (job_lvl >= 200) OR   
      (hire_date < '01/01/1998')  
    ```  
  
4.  Répétez les étapes 2 et 3 pour chacune des autres conditions que vous souhaitez ajouter. Utilisez une colonne **Ou...** différente pour chaque nouvelle condition.  
  
## <a name="specifying-an-and-condition"></a>Spécification d'une condition AND  
Pour effectuer une recherche dans différentes colonnes de données reliées à l’aide de l’opérateur AND, définissez toutes les conditions dans la colonne **Filtre** de la grille.  
  
#### <a name="to-specify-an-and-condition-for-two-different-columns"></a>Pour spécifier une condition AND pour deux colonnes différentes  
  
1.  Dans le [volet Critères](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md), ajoutez les colonnes dans lesquelles vous souhaitez effectuer la recherche.  
  
2.  Dans la colonne **Filtre** de la première colonne de données dans laquelle vous souhaitez effectuer la recherche, spécifiez la première condition.  
  
3.  Dans la colonne **Filtre** de la deuxième colonne de données, spécifiez la deuxième condition.  
  
    Le Concepteur de requêtes et de vues crée une clause WHERE comportant une condition AND de ce type :  
  
    ```  
    SELECT pub_id, title  
    FROM titles  
    WHERE (pub_id = '0877') AND (title LIKE '%Cook%')  
    ```  
  
4.  Répétez les étapes 2 et 3 pour chacune des autres conditions que vous souhaitez ajouter.  
  
## <a name="see-also"></a>Voir aussi  
[Associer des conditions avec priorité à l'opérateur AND (Visual Database Tools)](../../ssms/visual-db-tools/combine-conditions-when-and-has-precedence-visual-database-tools.md)  
[Associer des conditions avec priorité à l'opérateur OR (Visual Database Tools)](../../ssms/visual-db-tools/combine-conditions-when-or-has-precedence-visual-database-tools.md)  
[Conventions pour la combinaison de conditions de recherche dans le volet Critères (Visual Database Tools)](../../ssms/visual-db-tools/conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md)  
[Spécifier des critères de recherche (Visual Database Tools)](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
  
