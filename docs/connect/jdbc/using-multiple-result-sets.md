---
title: À l’aide de plusieurs jeux de résultats | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ab6a3cfa-073b-44e9-afca-a8675cfe5fd1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fd3294eb5ff9d25b6e5d067249d829b21428035a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47814707"
---
# <a name="using-multiple-result-sets"></a>Utilisation de plusieurs jeux de résultats

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Lors de l’utilisation de procédures stockées SQL ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] inline qui retournent plusieurs jeux de résultats, le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fournit la méthode [getResultSet](../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md) de la classe [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) pour récupérer chaque jeu de données retourné. En outre, lors de l’exécution d’une instruction qui retourne plus d’un jeu de résultats, vous pouvez utiliser la méthode [execute](../../connect/jdbc/reference/execute-method-sqlserverstatement.md) de la classe SQLServerStatement car elle retourne une valeur **boolean** qui indique si la valeur retournée est un jeu de résultats ou un nombre de mises à jour.

Si la méthode execute retourne la valeur **true**, l’instruction exécutée a retourné au moins un jeu de résultats. Vous pouvez accéder au premier jeu de résultats en appelant la méthode getResultSet. Pour déterminer si des jeux de résultats supplémentaires sont disponibles, vous pouvez appeler la méthode [getMoreResults](../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md), qui retourne une valeur **boolean** **true** en cas de disponibilité de jeux de résultats supplémentaires. Si des jeux de résultats supplémentaires sont disponibles, vous pouvez appeler la méthode getResultSet pour y accéder, tout en continuant le processus jusqu’à ce que tous les jeux de résultats soient traités. Si la méthode getMoreResults retourne **false**, il existe aucune plusieurs jeux de résultats au processus.

Si la méthode execute retourne la valeur **false**, cela signifie que l’instruction exécutée a retourné un nombre de mises à jour, que vous pouvez extraire en appelant la méthode [getUpdateCount](../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md).

> [!NOTE]  
> Pour plus d’informations sur le nombre de mises à jour, consultez [à l’aide d’une procédure stockée avec un nombre de mettre à jour](../../connect/jdbc/using-a-stored-procedure-with-an-update-count.md).

Dans l’exemple suivant, une connexion ouverte à l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] est transmise à la fonction et une instruction SQL est créée, qui retourne deux jeux de résultats lors de son exécution :

[!code[JDBC#UsingMultipleResultSets1](../../connect/jdbc/codesnippet/Java/using-multiple-result-sets_1.java)]

Dans ce cas, le nombre de jeux de résultats retourné est deux. Cependant, le code est écrit de telle façon que si un nombre inconnu de jeux de résultats est retourné, comme lors de l'appel d'une procédure stockée, tous les jeux de résultats sont traités. Pour découvrir un exemple d’appel de procédure stockée qui retourne plusieurs jeux de résultats avec des valeurs de mise à jour, consultez [Gestion des instructions complexes](../../connect/jdbc/handling-complex-statements.md).

> [!NOTE]  
> Lorsque vous effectuez l’appel à la méthode getMoreResults de la classe SQLServerStatement, le jeu de résultats précédemment retourné est implicitement fermé.

## <a name="see-also"></a> Voir aussi

[Utilisation d’instructions avec le pilote JDBC](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)
