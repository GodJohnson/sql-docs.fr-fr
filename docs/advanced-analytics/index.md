---
title: Documentation sur les extensions de Machine Learning et de programmation SQL Server | Microsoft Docs
description: R et Python dans SQL Server, avec intégration de la modélisation pour la science des données et d’algorithmes de Machine Learning pour l’analyse des données d’entreprise à grande échelle.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/10/2018
ms.topic: overview
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 4c56d49e4cf168c7d1b6b1830caa6c79e237f46c
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2018
ms.locfileid: "46712381"
---
::: moniker range="=sql-server-ver15||=sqlallproducts-allversions"
# <a name="sql-server-machine-learning-and-programming-extensions-documentation"></a>Documentation sur les extensions de Machine Learning et de programmation SQL Server

Découvrez comment utiliser des bibliothèques externes et les langages R et Python sur des données relationnelles résidentes avec nos guides de démarrage rapide, nos tutoriels et nos articles pratiques. Les bibliothèques R et Python du [Machine Learning SQL Server](what-is-sql-server-machine-learning.md) incluent des distributions de base, des modèles pour la science des données, des algorithmes de Machine Learning et des fonctions pour conduire des analytiques hautes performances à grande échelle, sans devoir transférer les données sur le réseau. 

Dans SQL Server 2019, l’exécution du code Java utilise le même framework d’extensibilité que R et Python, mais n’inclut pas de bibliothèques de fonctions de science des données et de Machine Learning. Pour plus d’informations sur les nouvelles fonctionnalités, consultez [Nouveautés de SQL Server Machine Learning Services](what-s-new-in-sql-server-machine-learning-services.md).

|   |   | 
|---|---|-
| ![Logo R](./media/index/logo_r.png) | R open source, étendu avec [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) et algorithmes Microsoft AI dans [MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package). Ces bibliothèques mettent à votre disposition des modèles de prévision et de prédiction, des analyses statistiques, des visualisations et des manipulations de données à grande échelle. <br/>L’intégration de R commence avec [SQL Server 2016](./install/sql-r-services-windows-install.md) et se trouve également dans [SQL Server 2017](./install/sql-machine-learning-services-windows-install.md). | 
| ![Logo Python](./media/index/logo_python.png) | Les développeurs Python peuvent utiliser les bibliothèques [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) et [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) de Microsoft pour l’analytique prédictive et le Machine Learning à grande échelle. Les bibliothèques compatibles avec Anaconda et Python 3.5 sont la distribution de référence. <br/>L’intégration de Python commence avec [SQL Server 2017](./install/sql-machine-learning-services-windows-install.md).  | 
| ![Logo Java](./media/index/logo_java.png) | Les développeurs Java peuvent utiliser [l’extension du langage Java](java/extension-java.md) pour wrapper du code dans des procédures stockées ou à un format binaire accessible via Transact-SQL. <br/>L’intégration de Java commence avec [SQL Server 2019 - Préversion](./install/sql-machine-learning-services-ver15.md). |
::: moniker-end

::: moniker range="=sql-server-2016||=sql-server-2017"
# <a name="sql-server-machine-learning-r-and-python-documentation"></a>Documentation de Python et R pour SQL Server Machine Learning

Découvrez comment utiliser des bibliothèques externes et les langages R et Python sur des données relationnelles résidentes avec nos guides de démarrage rapide, nos tutoriels et nos articles pratiques. Les bibliothèques R et Python du [Machine Learning SQL Server](what-is-sql-server-machine-learning.md) incluent des distributions de base, des modèles pour la science des données, des algorithmes de Machine Learning et des fonctions pour conduire des analytiques hautes performances à grande échelle, sans devoir transférer les données sur le réseau. 

|   |   | 
|---|---|-
| ![Logo R](./media/index/logo_r.png) | R open source, étendu avec [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) et algorithmes Microsoft AI dans [MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package). Ces bibliothèques mettent à votre disposition des modèles de prévision et de prédiction, des analyses statistiques, des visualisations et des manipulations de données à grande échelle. <br/>L’intégration de R commence avec [SQL Server 2016](./install/sql-r-services-windows-install.md) et se trouve également dans [SQL Server 2017](./install/sql-machine-learning-services-windows-install.md). | 
| ![Logo Python](./media/index/logo_python.png) | Les développeurs Python peuvent utiliser les bibliothèques [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) et [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) de Microsoft pour l’analytique prédictive et le Machine Learning à grande échelle. Les bibliothèques compatibles avec Anaconda et Python 3.5 sont la distribution de référence. <br/>L’intégration de Python commence avec [SQL Server 2017](./install/sql-machine-learning-services-windows-install.md).  | 
::: moniker-end

## <a name="5-minute-quickstarts"></a>Démarrages rapides en 5 minutes

+ [Créer un modèle prédictif dans R](./tutorials/rtsql-create-a-predictive-model-r.md)

+ [Prédire et tracer à partir d’un modèle avec R](./tutorials/rtsql-predict-and-plot-from-model.md)


## <a name="step-by-step-tutorials"></a>Tutoriels pas à pas

+ [Guide pratique pour ajouter le framework d’extensibilité et de Machine Learning à SQL Server](install/sql-machine-learning-services-windows-install.md)

+ [Guide pratique pour exécuter R à partir de T-SQL et de procédures stockées](./tutorials/sqldev-in-database-r-for-sql-developers.md)

+ [Guide pratique pour utiliser l’analytique incorporée dans Python](./tutorials/sqldev-in-database-python-for-sql-developers.md)


## <a name="video-introduction"></a>Vidéo de présentation

> [!VIDEO https://www.youtube.com/embed/ACejZ9optCQ]

## <a name="reference"></a>Référence

| Package | Langage | Description | 
|---------|----------|-------------|
| [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) | R | Traitement distribué et parallèle pour les tâches R : transformation des données, exploration, visualisation, analytique statistique et prédictive. |
| [MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) | R | Fonctions basées sur les algorithmes d’intelligence artificielle de Microsoft, adaptées pour R. |
| [olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | R | Importation de données depuis des cubes OLAP |
| [sqlRUtils]() | R | Fonctions helper pour l’encapsulation de R et de T-SQL. |
[revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | Python | Traitement distribué et parallèle pour les tâches Python : transformation des données, exploration, visualisation, analytique statistique et prédictive.  | 
| [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | Python | Fonctions basées sur les algorithmes d’intelligence artificielle de Microsoft, adaptées pour Python.  |