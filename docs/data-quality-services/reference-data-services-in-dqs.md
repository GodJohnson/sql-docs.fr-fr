---
title: Services de données de référence dans DQS | Microsoft Docs
ms.custom: ''
ms.date: 10/01/2012
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology:
- data-quality-services
ms.topic: conceptual
ms.assetid: ef217717-6d05-443e-af26-44dc745a349d
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 75492ffdd6246050c086deea74975921a19156b4
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51702217"
---
# <a name="reference-data-services-in-dqs"></a>Services de données de référence dans DQS

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Les données de référence correspondent à un ensemble précis et complet de données globales associées ou classées (au-delà des limites d'une entreprise) qui sont disponibles pour les domaines publics approuvés ou auprès de fournisseurs de contenu commercial de premier ordre.  
  
 Dans [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS), la fonctionnalité de service de données de référence vous permet de vous abonner à des fournisseurs de données de référence tiers, ainsi que de nettoyer et d'enrichir facilement vos données métier en les validant par rapport à leurs données de grande qualité. Vous pouvez utiliser les services des meilleurs fournisseurs de services de qualité des données à partir de DQS pour normaliser, corriger ou enrichir vos données pendant le processus de nettoyage. Par exemple, vous pouvez confronter une liste d'indicatifs régionaux ou de codes postaux aux données de référence pour valider les adresses de vos clients.  
  
 La fonctionnalité de service de données de référence présente les avantages suivants :  
  
-   Les données de référence vous permettent de garantir la qualité de vos données en les comparant à des données garanties par une société tierce.  
  
-   Le processus de données de référence est incorporé dans la création d'une base de connaissances DQS et un projet de qualité des données, ce qui vous permet d'instituer un processus de qualité des données complet.  
  
-   Elle prend en charge l'utilisation de données de référence provenant de Windows Azure Marketplace, ainsi que de données de référence provenant directement de fournisseurs de données de référence tiers.  
  
##  <a name="Marketplace"></a> Utilisation de données de référence provenant de Windows Azure Marketplace  
 DQS prend en charge l'utilisation de données de référence provenant de Windows Azure Marketplace afin de permettre aux fournisseurs de contenu de fournir des services de données de référence via Marketplace. Marketplace est un service Microsoft qui fournit un canal de remise et de marché unique permettant d'obtenir des données et des applications de haute qualité sous la forme de services en nuage. Pour plus d’informations sur la Place de marché, consultez [Découvrir la Place de marché Microsoft Azure](https://go.microsoft.com/fwlink/?LinkId=211291) (https://go.microsoft.com/fwlink/?LinkId=211291).  
  
 L'intégration transparente entre la Place de marché et DQS simplifie les étapes associées à la découverte, l'exploration et l'acquisition d'informations pour des projets de qualité des données à partir de DQS. Les données sont utilisées à partir de DQS, et permettent aux utilisateurs de DQS d'atteindre une haute qualité de données en rassemblant de façon innovante DQS, Marketplace et des fournisseurs de services de données de référence.  
  
 Pour utiliser des données de référence de marché dans DQS pour l'activité de nettoyage, vous devez disposer d'une clé de compte Marketplace. La création d'une clé de compte Marketplace est gratuite ; vous payez uniquement si vous vous abonnez à des datasets payés. L'abonnement à des datasets gratuits et leur utilisation n'entraînent aucun frais. Pour obtenir des informations détaillées sur la création d’une clé de compte Place de marché, consultez [Créer votre compte](https://go.microsoft.com/fwlink/?LinkId=212936) (https://go.microsoft.com/fwlink/?LinkId=212936).  
  
 En outre, vous pouvez effectuer les activités Marketplace suivantes à partir de DQS :  
  
-   parcourir des jeux de données dans Marketplace ;  
  
-   créer une clé de compte Marketplace ;  
  
-   gérer les détails de votre compte Marketplace, tels que les clés de compte et les abonnements à des fournisseurs de données.  
  
 Vous pouvez effectuer ces activités sous l'onglet **Données de référence** de l'écran **Configuration** dans [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].  
  
##  <a name="Direct"></a> Utilisation de données de référence provenant directement de fournisseurs de données de référence tiers  
 Si vous n'êtes pas connecté à Internet et que vous ne pouvez donc pas utiliser Marketplace, DQS prend également en charge la connexion directe à des fournisseurs de données disponibles dans le réseau de votre organisation. Pour utiliser des données de référence provenant de fournisseurs de données de référence tiers en ligne directs, vous devez créer un enregistrement pour le fournisseur de données dans DQS.  
  
##  <a name="HowToCleanse"></a> Procédure : nettoyer des données à l'aide de données de référence  
 Le nettoyage de vos données dans DQS à l'aide de données de référence inclut les trois étapes suivantes :  
  
1.  **Configuration des détails du fournisseur de données de référence dans DQS**: avant de pouvoir utiliser des données de référence dans DQS, vous devez configurer les détails du service de données de référence dans DQS.  
  
    1.  Si vous utilisez Marketplace, fournissez une clé de compte Marketplace valide, accédez à la catégorie de données [Data Quality Services](https://go.microsoft.com/fwlink/?LinkId=227587) dans Marketplace, et abonnez-vous aux fournisseurs requis.  
  
    2.  Si vous utilisez un fournisseur de données de référence en ligne direct, vous devez ajouter les détails du fournisseur de données de référence direct dans DQS avant de pouvoir l'utiliser.  
  
     La configuration des détails de fournisseur de données de référence dans DQS est une activité qui s'effectue une seule fois pour un fournisseur de données particulier. Seuls les administrateurs DQS peuvent configurer des paramètres de données de référence dans DQS.  
  
2.  **Mappage d'un domaine/domaine composite dans une base de connaissances au service de données de référence**: mappez un domaine/domaine composite au service de données de référence approprié souscrit/ajouté à l'étape 1.  
  
3.  **Utilisation des domaines mappés pour l'activité de nettoyage dans un projet de qualité des données**: lors de la création d'un projet de qualité des données pour l'activité **Nettoyage** , sélectionnez la base de connaissances qui contient des domaines/domaines composites mappés avec des services de données de référence à l'étape 2, puis effectuez l'activité de nettoyage.  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Explique comment configurer DQS pour utiliser des services de données de référence provenant de Marketplace ou de fournisseurs de données tiers en ligne directs.|[Configurer DQS pour utiliser des données de référence](../data-quality-services/configure-dqs-to-use-reference-data.md)|  
|Explique comment mapper un domaine/domaine composite dans une base de connaissances à un service de données de référence.|[Attacher un domaine ou un domaine composite à des données de référence](../data-quality-services/attach-domain-or-composite-domain-to-reference-data.md)|  
|Explique comment nettoyer des données à l'aide d'un service de données de référence.|[Nettoyer des données à l’aide de la connaissance des données de référence &#40;externes&#41;](../data-quality-services/cleanse-data-using-reference-data-external-knowledge.md)|  
  
  
