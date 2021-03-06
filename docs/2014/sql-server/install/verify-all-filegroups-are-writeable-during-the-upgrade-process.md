---
title: Vérifiez que tous les groupes de fichiers sont accessibles en écriture pendant le processus de mise à niveau | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- filegroups [SQL Server], writeable
- writeable filegroups [SQL Server]
ms.assetid: 2985efc1-4b14-46c3-abbd-a656b159f23c
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cc80c3729e905d11284437f35af50cd4959e3ba0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48051932"
---
# <a name="verify-all-filegroups-are-writeable-during-the-upgrade-process"></a>Vérifier que tous les groupes de fichiers sont accessibles en écriture pendant le processus de mise à niveau
  Le Conseiller de mise à niveau a détecté une base de données possédant un ou plusieurs groupes de fichiers en lecture seule. Toutes les bases de données de l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doivent avoir leurs groupes de fichiers définis sur READ_WRITE avant la mise à niveau.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Action corrective  
 Utilisez l'instruction ALTER DATABASE pour définir le groupe de fichiers sur READ_WRITE.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
