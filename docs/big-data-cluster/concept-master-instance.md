---
title: Nouveautés pour les clusters de données volumineuses de SQL Server maître instance ? | Microsoft Docs
description: Cet article décrit l’instance principale dans un cluster de données volumineux de SQL Server 2019.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 11/06/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 50955f8c781dcf370aa3f48ed72a0ed993854655
ms.sourcegitcommit: cb73d60db8df15bf929ca17c1576cf1c4dca1780
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2018
ms.locfileid: "51221595"
---
# <a name="what-is-the-sql-server-big-data-cluster-master-instance"></a>Quelles sont les données volumineuses de SQL Server cluster instance principale ?

Cet article décrit le rôle de la *instance principale de SQL Server* dans un cluster big ata de SQL Server 2019. L’instance principale est une instance de SQL Server en cours d’exécution dans un cluster de données volumineux de SQL Server [plan de contrôle](big-data-cluster-overview.md#controlplane).

L’instance principale de SQL Server offre les fonctionnalités suivantes :

## <a name="connectivity"></a>Connectivité

L’instance principale de SQL Server fournit un point de terminaison TDS accessible en externe pour le cluster. Vous pouvez connecter des applications ou outils de SQL Server comme Azure Data Studio ou SQL Server Management Studio pour ce point de terminaison comme vous serait une autre instance de SQL Server.

## <a name="scale-out-query-management"></a>Gestion des requêtes de montée en puissance

L’instance principale de SQL Server contient le moteur de requête de montée en puissance est utilisé pour distribuer les requêtes sur des instances de SQL Server sur les nœuds dans le [pool de calcul](concept-compute-pool.md). Le moteur de requête de montée en puissance permet également d’accéder via Transact-SQL pour toutes les tables Hive dans le cluster sans aucune configuration supplémentaire. (Prise en charge des tables hive n’est pas dans les CTP 2.1)

## <a name="metadata-and-user-databases"></a>Les bases de données utilisateur et de métadonnées

Outre les bases de données de système SQL Server standards, l’instance principale de SQL contient également les éléments suivants :

- Une base de données de métadonnées qui contient les métadonnées de la table de HDFS
- Une carte de partitions de plan de données
- Détails des tables externes qui fournissent l’accès au plan de données de cluster.
- Sources de données externes PolyBase et des tables externes définies dans les bases de données utilisateur.

Vous pouvez également choisir d’ajouter vos propres bases de données utilisateur à l’instance principale de SQL Server.

## <a name="machine-learning-services"></a>Services machine learning

SQL Server services machine learning est une fonctionnalité complémentaire du moteur de base de données, utilisé pour exécuter le code Java, R et Python dans SQL Server. Cette fonctionnalité est basée sur l’infrastructure d’extensibilité de SQL Server, qui isole les processus externes à partir de processus de moteur de base, mais s’intègre entièrement avec les données relationnelles comme des procédures stockées, en tant que script T-SQL qui contient des instructions de R ou Python ou Java, R ou Code Python contenant T-SQL.

En tant que partie d’un cluster de données volumineuses de SQL Server, les services machine learning seront disponibles sur l’instance principale de SQL Serevr par défaut. Cela signifie qu’une fois que l’exécution du script externe est activée sur l’instance principale de SQL Server, il sera possible d’exécuter des scripts R et Python à l’aide de sp_execute_external_script Java.

### <a name="advantages-of-machine-learning-services-in-a-big-data-cluster"></a>Avantages de machine learning services dans un cluster de données volumineux

SQL Server 2019 rend plus facile pour le big data d’être joints à des données dimensionnelles généralement stockées dans la base de données d’entreprise. La valeur de données volumineuses augmente considérablement lorsqu’il n’est pas seulement dans les mains des parties d’une organisation, mais il est également inclus dans les rapports, des tableaux de bord et des applications. En même temps, les scientifiques des données peuvent continuer à utiliser les outils de l’écosystème Spark/HDFS et accéder facilement, en temps réel aux données dans l’instance principale de SQL Server et dans les sources de données externes accessibles _via_ le maître de SQL Server instance.

Avec SQL Server 2019 des clusters de données volumineuses, vous pouvez en faire plus avec votre lacs de données d’entreprise. Les analystes et développeurs SQL Server peuvent :

* Créez des applications consommant des données à partir des lacs de données d’entreprise.
* Raison sur toutes les données des requêtes Transact-SQL.
* Utiliser l’écosystème existant d’applications et des outils SQL Server pour accéder et analyser les données d’entreprise.
* Réduire la nécessité pour le déplacement des données via la virtualisation des données et mini-data warehouses.
* Continuer à utiliser Spark pour les scénarios big data.
* Générer des applications d’entreprise intelligentes à l’aide de Spark ou SQL Server pour l’apprentissage des modèles sur des lacs de données.
* Configurer les modèles dans les bases de données de production pour de meilleures performances.
* Données de Stream directement dans enterprise data warehouses pour l’analytique en temps réel.
* Explorer les données visuellement à l’aide d’une analyse interactive et outils décisionnels.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur les clusters de données volumineuses de SQL Server, consultez la présentation suivante :

- [Quelles sont les clusters SQL Server 2019 big data ?](big-data-cluster-overview.md)
