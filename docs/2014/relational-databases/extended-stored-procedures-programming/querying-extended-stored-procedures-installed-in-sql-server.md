---
title: Interrogation des procédures stockées étendues installées dans SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], querying
ms.assetid: e02348e6-dba6-438a-98b6-684244bb034d
caps.latest.revision: 30
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 0714011cb2ba76220517c02fe3d946556610869e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37298319"
---
# <a name="querying-extended-stored-procedures-installed-in-sql-server"></a>Interrogation des procédures stockées étendues installées dans SQL Server
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 Un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisateur authentifié peut afficher actuellement défini les procédures stockées étendues et le nom de la DLL à laquelle chacune appartient en exécutant la **sp_helpextendedproc** procédure système. Par exemple, l’exemple suivant retourne la DLL à laquelle **xp_hello** appartient :  
  
```  
sp_helpextendedproc 'xp_hello'  
```  
  
 Si **sp_helpextendedproc** est exécutée sans spécifier une procédure stockée étendue, toutes les procédures stockées étendues et leurs DLL est affichés.  
  
> [!IMPORTANT]  
>  Des informations sont retournées uniquement pour les procédures stockées étendues qui appartiennent à l'utilisateur connecté ou sur lesquelles il possède des autorisations. Seuls les membres de la **sysadmin** rôle serveur fixe et le **db_owner**, **db_securityadmin**et le **db_ddladmin** base de données fixe rôles d’afficher des informations pour toutes les procédures stockées étendues.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_helpextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql)   
 [sp_addextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql)   
 [sp_dropextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql)  
  
  