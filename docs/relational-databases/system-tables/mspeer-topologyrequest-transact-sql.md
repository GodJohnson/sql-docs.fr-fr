---
title: MSpeer_topologyrequest (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSpeer_topologyrequest_TSQL
- MSpeer_topologyrequest
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_topologyrequest
ms.assetid: c644814b-4e40-44d7-b6b4-5954b0d4db7c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f638d95416336a3d74eaafbdf7c6fdd25407ce18
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47818877"
---
# <a name="mspeertopologyrequest-transact-sql"></a>MSpeer_topologyrequest (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Permet de suivre les requêtes de statut de topologie pour une publication dans le cadre d'une réplication d'égal à égal. Cette table est stockée dans la base de données de publication.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|id|**Int**|Identifie une demande de statut de topologie. La colonne request_id dans [MSpeer_topologyresponse](../../relational-databases/system-tables/mspeer-topologyresponse-transact-sql.md) utilise cette valeur.|  
|publication|**sysname**|Nom de la publication d'où provient la demande de statut de topologie.|  
|sent_date|**datetime**|Date et heure d'émission de la demande de statut de topologie.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
