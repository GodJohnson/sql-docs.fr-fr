---
title: 'Leçon 3 : Faire correspondre les données à supprimer les doublons de la liste des fournisseurs | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: 059170b6-d62e-4b28-9451-99a0cc7e1f5f
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6c5074a670fa1ab1c6a837f06b5cd27b21707400
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48139591"
---
# <a name="lesson-3-matching-data-to-remove-duplicates-from-supplier-list"></a>Leçon 3 : Faire correspondre les données pour supprimer les doublons de la liste des fournisseurs
  Vous préparez la base de connaissances pour effectuer une activité de correspondance en créant une stratégie de correspondance dans la base de connaissances. Il ne peut exister qu'une seule stratégie de correspondance dans une base de connaissances. Une stratégie de correspondance comprend une ou plusieurs règles de correspondance. Une règle identifie les domaines impliqués dans le processus de correspondance, et spécifie le poids de chaque valeur de domaine dans un jugement de correspondance. Vous spécifiez dans la règle si des valeurs de domaine doivent être une correspondance exacte ou si elles peuvent être semblables, et avec quel degré de similarité. Vous pouvez également spécifier si une correspondance de domaine est requise pour le processus de correspondance. Vous pouvez tester chaque règle séparément, ainsi que l'ensemble de la stratégie, sur des exemples de données. Le processus de test affiche les enregistrements dont les scores correspondants sont supérieurs à la **score d’enregistrement minimal** seuil spécifié dans la configuration de DQS dans un cluster (groupe). Vous pouvez continuer à ajuster les règles de la stratégie jusqu'à ce que vous soyez satisfait.  
  
 Après avoir défini la stratégie, créez un projet de qualité des données pour effectuer l'activité de correspondance. Le projet de correspondance applique les règles de correspondance de la stratégie de correspondance à la source de données à évaluer. Ce processus évalue la probabilité que deux lignes soient des correspondances. Lorsque DQS exécute l'analyse de correspondance, il crée des clusters des enregistrements qu'il considère comme des correspondances. DQS identifie de façon aléatoire l'un des enregistrements comme un enregistrement pivot. Vous pouvez vérifier et refuser tout enregistrement qui n'est pas une correspondance appropriée pour le cluster. Consultez [créer une stratégie de correspondance](http://msdn.microsoft.com/library/hh270290.aspx) rubrique pour plus d’informations.  
  
 Dans cette leçon, vous allez effectuer une activité de correspondance pour supprimer les doublons de la liste des fournisseurs. D'abord, vous allez créer une stratégie de correspondance avec une règle pour identifier les doublons dans la liste des fournisseurs, puis vous allez publier la stratégie dans la base de connaissances. Ensuite, vous allez créer et exécuter un projet de qualité des données pour la correspondance. Enfin, vous allez exporter les résultats de l'activité de correspondance dans un fichier Excel que vous utiliserez plus tard lors du téléchargement des données dans Master Data Services (MDS).  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 1 : Définition d’une stratégie de correspondance](../../2014/tutorials/task-1-defining-a-matching-policy.md)  
  
  
