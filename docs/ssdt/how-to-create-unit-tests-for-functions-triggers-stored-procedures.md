---
title: 'Procédure : créer des tests unitaires SQL Server pour des fonctions, des déclencheurs ou des procédures stockées | Microsoft Docs'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: bda57c10-a1ab-4a1a-8a71-42085a3cb793
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c4ba18b045570c365a53371d0abc54c86582cfd4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47835907"
---
# <a name="how-to-create-sql-server-unit-tests-for-functions-triggers-and-stored-procedures"></a>Procédure : créer des tests unitaires SQL Server pour des fonctions, des déclencheurs ou des procédures stockées
Écrivez des tests unitaires qui évaluent les modifications apportées à un objet de base de données. Toutefois, SQL Server Data Tools inclut la prise en charge supplémentaire de la création des tests de fonctions de base de données, des déclencheurs et des procédures stockées à partir d'un nœud de projet de base de données dans l'Explorateur d'objets SQL Server. Les stubs de code Transact\-SQL peuvent être générés automatiquement pour que vous puissiez les personnaliser.  
  
### <a name="to-create-a-sql-server-unit-test-from-a-function-trigger-or-stored-procedure"></a>Pour créer un test unitaire SQL Server d'une fonction, d'un déclencheur ou d'une procédure stockée  
  
1.  Consultez [Procédure pas à pas : création et exécution d'un test unitaire SQL Server](../ssdt/walkthrough-creating-and-running-a-sql-server-unit-test.md) pour obtenir un exemple d'ajout de test unitaire pour une procédure stockée, dans la section « Pour créer un test unitaire SQL Server pour les procédures stockées ».  
  
    La condition de test Non concluant est la condition par défaut qui est ajoutée à chaque test. Cette condition de test est incluse pour indiquer que la vérification du test n'a pas été implémentée. Supprimez cette condition de test de votre test après avoir ajouté d'autres conditions de test. Pour plus d'informations, consultez [Procédure : ajouter des conditions de test à des tests unitaires SQL Server](../ssdt/how-to-add-test-conditions-to-sql-server-unit-tests.md).  
  
## <a name="see-also"></a> Voir aussi  
[Création et définition de tests unitaires SQL Server](../ssdt/creating-and-defining-sql-server-unit-tests.md)  
[Procédure : créer un test unitaire SQL Server vide](../ssdt/how-to-create-an-empty-sql-server-unit-test.md)  
  
