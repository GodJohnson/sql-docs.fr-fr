---
title: Effectuer une mise à jour factice pour un Article de fusion (programmation Transact-SQL de la réplication) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_mergedummyupdate
- dummy updates [SQL Server replication]
ms.assetid: 2f339210-4d85-4843-bd94-e86f7100d3ef
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e01d41d9a98b9f5681fa9ff905615468481473c5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48176159"
---
# <a name="perform-a-dummy-update-for-a-merge-article-replication-transact-sql-programming"></a>Exécuter une mise à jour factice pour un article de fusion (programmation Transact-SQL de la réplication)
  La réplication de fusion utilise des déclencheurs dans le cadre du processus de réplication ; lorsqu'une mise à jour est effectuée sur la table publiée, un déclencheur de mise à jour est exécuté. Dans certains cas, les données peuvent être mises à jour sans exécution du déclencheur, comme lors des opérations WRITETEXT et UPDATETEXT. Dans ces cas-là, vous devez ajouter explicitement une instruction UPDATE factice pour répliquer la modification. Vous pouvez ajouter une instruction UPDATE factice à l'aide de procédures stockées de réplication.  
  
### <a name="to-add-a-dummy-update-statement"></a>Pour ajouter une instruction UPDATE factice  
  
1.  Exécutez l'opération (par exemple, UPDATETEXT) sur une ligne d'une table de fusion publiée qui requiert une mise à jour factice.  
  
2.  Sur le serveur (serveur de publication ou Abonné) de la base de données où la modification a été effectuée, exécutez [sp_mergedummyupdate &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-mergedummyupdate-transact-sql). Spécifiez la table sur laquelle la modification a été apportée pour **@source_object**et l'identificateur unique de la ligne modifiée pour **@rowguid**.  
  
3.  Synchronisez l'abonnement pour répliquer la ligne modifiée.  
  
  
