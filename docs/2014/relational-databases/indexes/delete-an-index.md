---
title: Supprimer un index | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- removing indexes
- deleting indexes
- dropping indexes
- indexes [SQL Server], dropping
- index deletions [SQL Server]
ms.assetid: fd38a0ed-26c4-4c76-9ef7-e0a16147329d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 8d04911b52239ff9accc5d69ff1e1ddd21e5d50b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48093449"
---
# <a name="delete-an-index"></a>Supprimer un index
  Cette rubrique explique comment supprimer un index dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour supprimer un index, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
 Les index résultant d'une contrainte PRIMARY KEY ou UNIQUE ne peuvent pas être supprimés au moyen de cette méthode. Dans ce cas, c'est la contrainte qui doit être supprimée. Pour supprimer la contrainte et l'index correspondant, utilisez [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) avec la clause DROP CONSTRAINT dans [!INCLUDE[tsql](../../includes/tsql-md.md)]. Pour plus d’informations, consultez [Delete Primary Keys](../tables/delete-primary-keys.md).  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Nécessite une autorisation ALTER sur la table ou la vue. L’autorisation est accordée par défaut au rôle serveur fixe **sysadmin** et aux rôles de base de données fixes **db_ddladmin** et **db_owner** .  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-delete-an-index-by-using-object-explorer"></a>Pour supprimer un index à l'aide de l'Explorateur d'objets  
  
1.  Dans l'Explorateur d'objets, développez la base de données qui contient la table sur laquelle vous souhaitez supprimer un index.  
  
2.  Développez le dossier **Tables** .  
  
3.  Développez la table contenant l'index à supprimer.  
  
4.  Développez le dossier **Index** .  
  
5.  Cliquez avec le bouton droit sur l’index à supprimer, puis sélectionnez **Supprimer**.  
  
6.  Dans la boîte de dialogue **Supprimer un objet** , vérifiez que l'index correct figure dans la grille **Objet à supprimer** , puis cliquez sur **OK**.  
  
#### <a name="to-delete-an-index-using-table-designer"></a>Pour supprimer un index à l'aide du Concepteur de tables  
  
1.  Dans l'Explorateur d'objets, développez la base de données qui contient la table sur laquelle vous souhaitez supprimer un index.  
  
2.  Développez le dossier **Tables** .  
  
3.  Cliquez avec le bouton droit sur la table contenant l'index que vous souhaitez supprimer et cliquez sur Conception.  
  
4.  Dans le menu **Concepteur de tables** , cliquez sur **Index/Clés**.  
  
5.  Dans la boîte de dialogue **Index/Clés** , sélectionnez l’index que vous souhaitez supprimer.  
  
6.  Cliquez sur **Supprimer**.  
  
7.  Cliquez sur **Fermer**.  
  
8.  Dans le menu **Fichier**, sélectionnez **Enregistrer***nom_table*.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-delete-an-index"></a>Pour supprimer un index  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- delete the IX_ProductVendor_BusinessEntityID index  
    -- from the Purchasing.ProductVendor table  
    DROP INDEX IX_ProductVendor_BusinessEntityID   
        ON Purchasing.ProductVendor;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql).  
  
  
