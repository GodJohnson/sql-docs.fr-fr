---
title: Annulation de commandes (XMLA) | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: babdafaaa1c507a609760b02895f9438baf21581
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50145015"
---
# <a name="canceling-commands-xmla"></a>Annulation de commandes (XMLA)
  En fonction des autorisations d’administration de l’utilisateur qui émet la commande, le [Annuler](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla) commande au format XML pour Analysis (XMLA) peut annuler une commande sur une session, une session, une connexion, un processus de serveur ou une session associée ou connexion.  
  
## <a name="canceling-commands"></a>Annulation de commandes  
 Un utilisateur peut annuler la commande en cours d’exécution dans le contexte de la session explicite active en envoyant un **Annuler** commande sans aucune propriété spécifiée.  
  
> [!NOTE]  
>  Une commande en cours d'exécution dans une session implicite ne peut pas être annulée par un utilisateur.  
  
### <a name="canceling-batch-commands"></a>Annulation de commandes Batch  
 Si un utilisateur annule une **Batch** commande, puis tous les autres commandes ne sont pas encore exécutées dans le **Batch** commande sont annulées. Si le **Batch** commande était transactionnelle, les commandes qui ont été exécutées avant la **Annuler** commande s’exécute est restaurées.  
  
## <a name="canceling-sessions"></a>Annulation de sessions  
 En spécifiant un identificateur de session pour une session explicite dans le [SessionID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) propriété de la **Annuler** commande, un administrateur de base de données ou un administrateur de serveur peut annuler une session, y compris le en cours d’exécution commande. Un administrateur de base de données ne peut annuler les sessions que pour les bases de données pour lesquelles il dispose d'autorisations administratives.  
  
 Un administrateur de base de données peut récupérer les sessions actives pour une base de données spécifiée en récupérant l'ensemble de lignes de schéma DISCOVER_SESSIONS. Pour récupérer l’ensemble de lignes de schéma DISCOVER_SESSIONS, l’administrateur de base de données utilise le code XMLA **Discover** (méthode) et spécifie l’identificateur de la base de données appropriée pour la valeur de la restriction session_current_database dans la [Restrictions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/restrictions-element-xmla) propriété de la **Discover** (méthode).  
  
## <a name="canceling-connections"></a>Annulation de connexions  
 En spécifiant un identificateur de connexion dans le [ConnectionID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/connectionid-element-xmla) propriété de la **Annuler** commande, un administrateur de serveur peut annuler toutes les sessions associées à une connexion donnée, y compris tous les exécution des commandes et annuler la connexion.  
  
> [!NOTE]  
>  Si l’instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ne peut pas localiser et annuler les sessions associées à une connexion, telles que lorsque la pompe à données ouvre plusieurs sessions en fournissant une connectivité HTTP, l’instance ne peut pas annuler la connexion. Si ce cas est rencontré pendant l’exécution d’un **Annuler** commande, une erreur se produit.  
  
 Un administrateur de serveur peut récupérer les connexions actives pour un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance en récupérant l’ensemble de lignes de schéma DISCOVER_CONNECTIONS à l’aide de XMLA **Discover** (méthode).  
  
## <a name="canceling-server-processes"></a>Annulation de processus serveur  
 En spécifiant un identificateur de processus serveur (SPID) dans le [SPID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) propriété de la **Annuler** commande, un administrateur de serveur peut annuler les commandes associées à un SPID donné.  
  
## <a name="canceling-associated-sessions-and-connections"></a>Annulation de sessions et de connexions associées  
 Vous pouvez définir le [CancelAssociated](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cancelassociated-element-xmla) propriété sur true pour annuler les connexions, les sessions et les commandes associées à la connexion, la session ou le SPID spécifié dans le **Annuler** commande.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode Discover &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover)   
 [Développement avec XMLA dans Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
