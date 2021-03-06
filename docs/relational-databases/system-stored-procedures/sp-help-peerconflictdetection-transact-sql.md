---
title: sp_help_peerconflictdetection (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_help_peerconflictdetection
- sp_help_peerconflictdetection_TSQL
helpviewer_keywords:
- sp_help_peerconflictdetection
ms.assetid: 59e04107-5eaa-44a1-beb6-ac4f2dbbcb28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bb1291cc7defe737a62ea063036db057b6b210a8
ms.sourcegitcommit: a251adad8474b477363df6a121431b837f22bf77
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47864177"
---
# <a name="sphelppeerconflictdetection-transact-sql"></a>sp_help_peerconflictdetection (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne des informations relatives aux paramètres de la détection de conflit pour une publication impliquée dans une topologie de réplication transactionnelle d'égal à égal.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_help_peerconflictdetection [ @publication = ] 'publication'  
    [ ,[ @timeout = ] timeout ]  
```  
  
## <a name="arguments"></a>Arguments  
 [ @publication=] '*publication*'  
 Nom de la publication pour laquelle renvoyer les informations. *publication* est **sysname**, sans valeur par défaut.  
  
 [ @timeout=] *délai d’attente*  
 Spécifie la durée, en secondes, du délai d'expiration de la procédure durant l'attente d'une réponse de chaque nœud dans la topologie. Si la topologie contient un Abonné en lecture seule, spécifier une valeur de délai d'attente n'est pas valide. Les Abonnés en lecture seule ne répondent jamais à un appel de cette procédure. *délai d’attente* est **int**, avec une valeur par défaut de 60.  
  
## <a name="result-sets"></a>Jeux de résultats  
 sp_help_peerconflictdetection retourne trois jeux de résultats. Ces résultats sont décrits dans les rubriques suivantes :  
  
-   [MSpeer_conflictdetectionconfigrequest](../../relational-databases/system-tables/mspeer-conflictdetectionconfigrequest-transact-sql.md)  
  
-   [MSpeer_conflictdetectionconfigresponse](../../relational-databases/system-tables/mspeer-conflictdetectionconfigresponse-transact-sql.md)  
  
-   [Mspeer_originatorid_history](../../relational-databases/system-tables/mspeer-originatorid-history-transact-sql.md)  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 sp_help_peerconflictdetection est utilisé dans la réplication transactionnelle d'égal à égal.  
  
## <a name="permissions"></a>Permissions  
 Requiert l'appartenance au rôle serveur fixe sysadmin ou au rôle de base de données fixe db_owner.  
  
## <a name="see-also"></a>Voir aussi  
 [Détection de conflit dans la réplication d’égal à égal](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)   
 [Réplication transactionnelle d’égal à égal](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)   
 [Procédures stockées de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
