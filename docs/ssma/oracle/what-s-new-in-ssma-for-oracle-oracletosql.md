---
title: Quel &#39; s de SSMA pour Oracle (OracleToSQL) | Documents Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 08/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f305ebb6-7393-4a43-abb3-6332b739d690
caps.latest.revision: 24
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.translationtype: MT
ms.sourcegitcommit: 80642503480add90fc75573338760ab86139694c
ms.openlocfilehash: 690d34e4391bcdbcbf7adfe1d80ed8c503d80895
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---
# <a name="what39s-new-in-ssma--for-oracle-oracletosql"></a>Quel &#39; s de SSMA pour Oracle (OracleToSQL)
Cette rubrique répertorie SSMA pour les modifications d’Oracle dans chaque version.  

## <a name="ssma-v74"></a>SSMA v7.4
La version v7.4 de SSMA pour Oracle contient les modifications suivantes :

- SSMA pour Oracle prend désormais en charge l’entrepôt de données SQL Azure comme plateforme cible pour la migration.

    ![Fenêtre Nouveau projet](../media/new-project.png)
  - Prend en charge les options de stockage de l’entrepôt de données comme indiqué dans l’image suivante :

    ![options de stockage pour l’entrepôt de données](../media/storage-options_red.png)
  - Prend en charge les options de distribution de données comme indiqué dans l’image suivante :

    ![distribution de données pour l’entrepôt de données](../media/data-distribution_red.png)

- Le **délai de requête** option est désormais disponible pendant la détection des objets de schéma à la source et cible.

    ![option de délai d’attente de requête](../media/query-timeout_red.png)

- Les mesures de qualité et de conversion a été améliorée avec des correctifs ciblés, en fonction des commentaires des clients.

> [!IMPORTANT]
> .NET 4.5.2 est requis pour l’installation de SSMA v7.4. En outre, à partir de v7.4, la version 32 bits de SSMA est interrompue.

## <a name="ssma-v73"></a>SSMA v7.3
La version v7.3 de SSMA pour Oracle contient les modifications suivantes :
- Métrique de qualité et de conversion améliorée avec des correctifs ciblés en fonction des commentaires des clients.
- Infrastructure d’extensibilité SSMA exposé via les éléments suivants :
  - Fonctionnalité d’exportation à un projet SQL Server Data Tools (SSDT).
    -   Vous pouvez désormais exporter des scripts de schéma à partir de SSMA pour un projet SSDT. Vous pouvez utiliser les scripts de schéma pour apporter des modifications de schéma supplémentaires et de déployer votre base de données.
![Enregistrer en tant que commande de projet SSDT](../media/export-schema-scripts_red.png)
  - Bibliothèques peuvent être consommées par SSMA pour effectuer des conversions personnalisées.
    - Vous pouvez maintenant construire le code qui peut gérer les conversions de syntaxe personnalisée et les conversions qui n’ont pas été précédemment traitées par SSMA.
      - Obtenir des instructions sur la création d’un convertisseur personnalisé sont disponibles dans ce billet de blog, [fonctions de conversion d’extension Assistant Migration SQL Server](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/).
      - Exemple de projet pour la conversion peut être le télécharger [billet de blog](https://blogs.msdn.microsoft.com/datamigration/ssmafororacleconversionsample/).


## <a name="ssma-v72"></a>SSMA v7.2
La version de v7.2 de SSMA pour Oracle contient les modifications suivantes :
- Métrique de qualité et de conversion améliorée avec des correctifs ciblés en fonction des commentaires des clients.
- Améliorations de télémétrie pour fournir une meilleure points de données pour résoudre les problèmes de client et d’améliorer le taux de conversion de SSMA.

## <a name="ssma-v71"></a>SSMA v7.1
La version de v7.1 de SSMA pour Access contient les modifications suivantes :
- 2017 du serveur SQL sur Windows et Linux CTP1 est désormais une plateforme cible prise en charge pour la migration. Cette fonctionnalité est dans technical preview et permet le déplacement de schéma et les données pour les serveurs de SQL Server cible.
- SSMA prend désormais en charge les mises à jour automatiques pour télécharger la dernière version de SSMA dès qu’elles sont disponibles.
- Fichiers binaires installables de SSMA sont maintenant remis via des fichiers de package Windows installer (.msi).

**Ressources**

[Extension des capacités de SQL Server Migration Assistant conversion](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/)

[Évaluer et migrer des données à partir de plateformes de données non Microsoft pour SQL Server *(avec un exemple d’Oracle)*](https://blogs.msdn.microsoft.com/datamigration/2016/11/16/sql-server-migration-assistant-how-to-assess-and-migrate-databases-from-non-microsoft-data-platforms-to-sql-server/) 

## <a name="may-2016"></a>Mai 2016  
La version de mai 2016 de SSMA pour Oracle contient les modifications suivantes :  

-   Ajout de la prise en charge pour SQL Server 2016.
-   Conversion ajoutée des tables d’archive restauration Oracle aux tables temporelles de SQL Server.
-   Ajout de conversion de la stratégie de VPD Oracle convertir des objets de stratégie de SQL Server (sécurité de niveau ligne pour Oracle).
-   Une diminution des temps de chargement initial pour Oracle.
-   Analyseur amélioré et le programme de résolution.
-   Supprimé vérification du programme d’installation pour .net 2.0.
-   Dépendance Extension Pack mis à jour à partir de .net 3.5 pour .net 4.0.
-   Fixe « enregistrer le projet » et « ouvrir le projet » des commandes pour la Console de SSMA.
-   Commande securepassword « fixe » pour la Console de SSMA.
-   Correction de comptage des objets pour le chargement initial.
-   Correction de la conversion des types de données caractères pour Oracle.
-   Résolution du bogue dans les paramètres globaux.
  
## <a name="march-2016"></a>Mars 2016  
La version préliminaire de mars 2016 de SSMA pour Oracle contient les modifications suivantes :  
  
-   Prise en charge supplémentaire pour la migration vers SQL Server 2016.  
-   Prise en charge supplémentaire pour la migration sécurité au niveau des lignes Oracle (avec certaines limitations toutefois).  
-   Prise en charge pour la migration des tables Oracle dans la mémoire à la banque des colonnes SQL Server.  
  
## <a name="january-2016"></a>Janvier 2016  
Le janvier 2014 mise à jour de SSMA pour Oracle contient les modifications suivantes :  
  
-   Prise en charge supplémentaire pour les index cluster.  
-   Résolution des requêtes de schéma Oracle lentes (RFC 5076207).  
-   Fixe se connecter à Azure à partir de la console.  
-   Élément de Menu ajouté vue journal de SSMA (RFC 5706203). 
-   Ajout de télémétrie.  
  
## <a name="july-2014"></a>Juillet 2014  
La version de juillet 2014 de SSMA pour Oracle contient les modifications suivantes :  
  
-   Prise en charge supplémentaire pour la base de données SQL Azure.  
-   Fonctionnalités du Pack d’extension est déplacé vers le schéma pour prendre en charge de la base de données SQL Azure.  
-   Prise en charge supplémentaire pour les vues matérialisées d’Oracle.  
-   Tables optimisées en la prise en charge pour la mémoire de SQL Server 2014.  
-   Améliorations de performances inclus testé pour les bases de données avec plus de 10k objets.  
-   Améliorations de l’interface utilisateur ajoutées pour le traitement d’un grand nombre d’objets.  
-   Ajouté à la mise en surbrillance des schémas « connues » de LOB.  
-   Améliorations de la vitesse conversion inclus.  
-   Compte de la prise en charge ajoutée pour afficher des objets dans l’interface utilisateur.  
-   Taille de rapport réduite de plus de 25 %.
-   Messages d’erreur améliorés pour les constructions non analysées.  
  
## <a name="april-2014"></a>Avril 2014  
La version d’avril 2014 de SSMA pour Oracle contient les modifications suivantes :  
  
-   Prise en charge de Microsoft SQL Server 2014.  
-   Prise en charge supplémentaire d’optimisation Oracle 12 et la requête.  
-   Bogues résolus concernant la conversion vers Azure.  
-   Bogues résolus en ce qui concerne les pages du rapport invisible dans Internet Explorer 10.  
  
## <a name="january-2012"></a>Janvier 2012  
La version de janvier 2012 de SSMA pour Oracle contient les modifications suivantes :  
  
-   Prise en charge pour les paramètres d’entrée RowType et RecordType NULL comme valeur par défaut.  
  
## <a name="july-2011"></a>Juillet 2011  
La version de juillet 2011 de SSMA pour Oracle contient les modifications suivantes :  
  
-   Prise en charge pour la conversion de séquence Oracle [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Générateur de séquence « Denali ».  
-   Amélioration signalement d’erreurs pendant la migration des données.  
-   Conversion amélioré d’instruction à l’aide des mots réservés.  
-   Amélioration de la conversion implicite de la valeur de date dans une fonction.  
  
## <a name="april-2011"></a>Avril 2011  
La version d’avril 2011 de SSMA pour Oracle contient les modifications suivantes :  
  
-   Produit consolidé « SSMA pour Oracle », qui prend en charge [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008 et [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] « Denali ».  
-   Prise en charge pour la connexion et la migration vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] « Denali ».  
-   Moteur de migration améliorée des données côté client, prise en charge parallèle migration des données.  
-   Performances de migration de données améliorées avec Simple et en bloc connecté des modes de récupération.  
-   Prise en charge supplémentaire pour la compatibilité descendante des projets créés dans les versions antérieures de SSMA (version 4.0 et v4.2).  
-   Ajouté la possibilité d’installer SSMA pour Oracle v5.0 produit côte à côte (SxS) avec les versions antérieures de SSMA (version 4.0 et v4.2).  
-   Prise en charge supplémentaire des Types définis par l’utilisateur (y compris sous-type VARRAY, la TABLE imbriquée, table des objets et affichage d’objets) et leur utilisation dans les blocs de PL/SQL avec des messages d’erreur spéciale de création de rapports.  

## <a name="july-2010"></a>Juillet 2010  
La version de juillet 2010 de SSMA pour Oracle contient les modifications suivantes :  
  
-   Prise en charge supplémentaire pour la migration vers SQL Server 2008 R2.  
-   Ajouter une nouvelle application de Console de SSMA pour l’exécution de ligne de commande.  
-   Prise en charge supplémentaire pour la Migration de données à l’aide à la fois les moteurs de la Migration des données côté Client et côté serveur.  
-   Prise en charge supplémentaire pour l’instruction de « SELECT personnalisée » dans la migration des données.  
-   Prise en charge supplémentaire pour la migration à partir d’Oracle 11g R2.  
  
## <a name="june-2008"></a>Juin 2008  
La version de juin 2008 de SSMA pour Oracle contient les modifications suivantes :  
  
-   Améliorations apportées au rapport d’évaluation, y compris des informations supplémentaires pour les synonymes, de source brute d’objets à analyser, panneaux et la suppression de logo de SQL Server et persistance de disposition.  
-   Améliorations apportées dans la conversion de l’objet :  
    -   Packages DBMS_LOB, conversion DBMS_SQL ajouté.  
    -   Joint la conversion révisée.  
    -   Modification des enregistrements et des collections de conversion, maintenant la conversion d’enregistrements dans les cas simples libérés via des variables distinctes pour chaque champ.  
    -   Améliorations de mise en oeuvre des enregistrements et des regroupements.  
    -   Fonctions d’agrégation de fenêtrage ajoutées.  
    -   Clause ROLLUP/CUBE ajoutée.  
    -   Amélioration de NEXTVAL/CURVAL.  
    -   Colonnes de regroupement dans la clause SET, les jeux de regroupement et l’ID de regroupement ont été ajoutés.  
    -   Ajouté des instructions de fusion.  
    -   Prise en charge de nouveaux types date/heure et la conversion des enregistrements et des collections en tant que types de données CLR ajoutés.  
-   Ajout de nouvelles fonctionnalités de testeur. Tables peuvent maintenant être testées en tant qu’objets à l’aide de Tester un ordre d’appel de plusieurs objets testables dans les cas de test peut être modifié, utilisateur peut tester les procédures et fonctions des enregistrements et des collections en tant que paramètres et retourner des valeurs et un analyseur a été ajouté pour vérifier les dépendances seulement les tables utilisées.  
  
## <a name="august-2007"></a>Août 2007  
La version d’août 2007 de SSMA pour Oracle contient les modifications suivantes :  
  
-   Ajouter qu'un nouveau composant testeur vous permet de créer, gérer et exécuter des cas de test pour vérifier le code SQL converti.  
-   Prise en charge pour la conversion de sous-types Oracle, les collections et les modules locaux ont été ajoutés au convertisseur de SQL.  
-   Ajouter qu'une nouvelle fonctionnalité de synchronisation vous permet de synchroniser des objets spécifiques à la base de données SQL Server.  
-   Nouvelles options de conversion ajouté.  
  
## <a name="april-2007"></a>Avril 2007  
La version d’avril 2007 de SSMA pour Oracle était la version initiale.