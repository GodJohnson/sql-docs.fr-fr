---
title: Effectuer une recherche dans des documents à l’aide des listes de résultats | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- searches [SQL Server Management Studio], result lists
- result list searches [SQL Server Management Studio]
- searches [SQL Server Management Studio], multiple files
- Query Editor [SQL Server Management Studio], search multiple files
ms.assetid: 275e1b6c-fbd0-4408-af77-35903f90657c
caps.latest.revision: 21
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3513f3919772a6f8c89921dfaf8e8120c61e2cfd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37294579"
---
# <a name="search-documents-using-results-lists"></a>Effectuer une recherche dans des documents à l'aide des listes de résultats
  À l’aide de la boîte de dialogue **Rechercher et remplacer** , vous pouvez rechercher et remplacer du texte dans tous les fichiers d’un projet, d’une solution ou d’un dossier du système de fichiers, même s’ils ne sont pas ouverts dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Les occurrences trouvées lors d’une recherche effectuée dans la boîte de dialogue **Rechercher et remplacer** s’affichent dans les fenêtres Résultats de la recherche 1 et Résultats de la recherche 2, ce qui vous permet de voir le texte exact de la ligne contenant le résultat.  
  
### <a name="to-search-in-multiple-files"></a>Pour effectuer une recherche dans plusieurs fichiers  
  
1.  Dans le menu **Edition** , pointez sur **Rechercher et remplacer** , puis cliquez sur **Rechercher dans les fichiers**.  
  
2.  Dans la zone de texte **Rechercher** , entrez le texte à rechercher.  
  
3.  Dans la liste **Regarder dans** , cliquez sur **Tous les documents ouverts**, **Projet en cours**, **Solution complète**ou tapez un chemin de répertoire.  
  
4.  Dans la liste **Types de fichiers** , sélectionnez l’un des jeux d’extensions de fichier répertoriés ou entrez les extensions correspondant aux types de fichiers à analyser en les séparant par des points-virgules. Spécifiez \*.\* pour effectuer la recherche dans tous les fichiers du répertoire sélectionné dans la liste déroulante **Regarder dans** .  
  
5.  Sélectionnez d'autres options pour affiner la recherche.  
  
6.  Cliquez sur **Rechercher** pour commencer la recherche.  
  
 Les résultats de la recherche s'affichent par défaut dans la fenêtre Résultats de la recherche 1. Vous pouvez parcourir les résultats de la recherche en double-cliquant sur chaque entrée de la fenêtre Résultats de la recherche 1. Pour afficher les résultats de la recherche dans une nouvelle fenêtre, cochez la case **Afficher dans Rechercher 2**.  
  
#### <a name="to-replace-across-multiple-files-or-folders"></a>Pour effectuer un remplacement dans plusieurs fichiers ou dossiers  
  
1.  Dans le menu **Edition** , pointez sur **Rechercher et remplacer** , puis cliquez sur **Remplacer dans les fichiers**.  
  
2.  Dans la zone de texte **Rechercher** , entrez le texte à rechercher.  
  
3.  Dans la zone de texte **Remplacer par** , entrez le texte qui doit remplacer le texte recherché.  
  
4.  Dans la liste **Regarder dans** , cliquez sur **Tous les documents ouverts**, **Projet en cours**, **Solution complète**ou tapez un chemin de répertoire.  
  
5.  Cliquez sur **Remplacer** pour remplacer le résultat de la recherche en cours par le texte spécifié dans la zone **Remplacer par** . Vous pouvez ignorer une occurrence isolée en cliquant sur **Suivant** ou l’ensemble d’un fichier en cliquant sur **Ignorer le fichier**.  
  
     \- ou -  
  
     Cliquez sur **Remplacer tout** pour remplacer toutes les occurrences trouvées par le texte spécifié dans la zone **Remplacer par** . Cochez la case **Conserver les fichiers modifiés ouverts après un remplacement global** si vous souhaitez annuler certains remplacements à un autre moment.  
  
    > [!NOTE]  
    >  La commande**Remplacer tout** remplace toutes les occurrences trouvées, notamment celles que vous avez ignouées en cliquant sur le bouton **Ignouer le fichier** ou **Suivant**. Vous pouvez utiliser **Annuler** uniquement pour les remplacements effectués dans des fichiers restant ouverts après cette opération.  
  
 Les informations relatives aux remplacements s'affichent par défaut dans la fenêtre Résultats de la recherche 1. Vous pouvez parcourir les remplacements en double-cliquant sur chaque entrée de la fenêtre Résultats de la recherche 1.  
  
## <a name="see-also"></a>Voir aussi  
 [Recherche et remplacement](search-and-replace.md)   
 [Effectuer une recherche de façon interactive dans des documents](search-documents-interactively.md)   
 [Rechercher du texte avec des caractères génériques](search-text-with-wildcards.md)   
 [Rechercher du texte avec des expressions régulières](search-text-with-regular-expressions.md)  
  
  