---
title: Autorisations de connexion SQL Server requises pour le service CDC | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: d9e968f9-180c-4fa0-a849-98f2b1942330
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c1660144e57fa523b8b0ae1798771b3815228159
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48185419"
---
# <a name="sql-server-connection-required-permissions-for-the-cdc-service"></a>Autorisations de connexion SQL Server requises pour le service de capture de données modifiées
  La console de configuration du service de capture de données modifiées requiert des informations de connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour effectuer ses tâches. Cette rubrique décrit les informations qui peuvent être fournies dans la boîte de dialogue Connexion à SQL Server pour configurer la connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 La boîte de dialogue Connexion à SQL Server s'affiche si nécessaire, par exemple lorsque les informations de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne sont pas disponibles ou lorsque les informations existent mais que la connexion ne dispose pas des autorisations nécessaires.  
  
 Le tableau suivant décrit les différentes tâches nécessitant une connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , ainsi que les autorisations que doit avoir la connexion ou l’utilisateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Tâche|Autorisations minimales|  
|----------|-------------------------|  
|Préparer une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|`dbcreator` rôle serveur fixe|  
|Créer une connexion SQL Server de service de capture de données modifiées Oracle en vue d'une utilisation par le service de capture de données modifiées Oracle.|`public` rôle serveur fixe|  
|Créer une connexion de service de capture de données modifiées Oracle à utiliser pour inscrire le nouveau service dans MSXDBCDC.|`db_datareader` et `db_datawriter` sur MSXDBCDC|  
|Modifier une connexion de service de capture de données modifiées Oracle en vue d'une utilisation pour la mise à jour de l'inscription du service dans MSXDBCDC.|`db_datareader` et `db_datawriter` sur MSXDBCDC|  
|Supprimer une connexion de service de capture de données modifiées Oracle en vue d'une utilisation pour la mise à jour de l'inscription du service dans MSXDBCDC.|`db_datareader` et `db_datawriter` sur MSXDBCDC|  
  
## <a name="see-also"></a>Voir aussi  
 [Connexion à SQL Server](connection-to-sql-server.md)   
 [Connexion à SQL Server pour la suppression](connection-to-sql-server-for-delete.md)  
  
  
