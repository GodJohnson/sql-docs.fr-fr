---
title: "Déplacer une base de données compatible FILESTREAM | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-blob
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FILESTREAM [SQL Server], moving a FILESTREAM-enabled database
ms.assetid: dd4d270d-9283-431a-aa6b-e571fced1893
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7af3800a6e604289944a340cee7f469654c495e2
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="move-a-filestream-enabled-database"></a>Déplacer une base de données compatible FILESTREAM
  Cette rubrique montre comment déplacer une base de données compatible FILESTREAM.  
  
> [!NOTE]  
>  Les exemples de cette rubrique exigent la base de données Archive créée dans [Créer une base de données compatible FILESTREAM](../../relational-databases/blob/create-a-filestream-enabled-database.md).  
  
### <a name="to-move-a-filestream-enabled-database"></a>Pour déplacer une base de données compatible FILESTREAM  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], cliquez sur **Nouvelle requête** pour ouvrir l’Éditeur de requête.  
  
2.  Copiez le script [!INCLUDE[tsql](../../includes/tsql-md.md)] suivant dans l’Éditeur de requête, puis cliquez sur **Exécuter**. Ce script affiche l'emplacement des fichiers de base de données physiques utilisés par la base de données FILESTREAM.  
  
    ```tsql  
    USE Archive  
    GO  
    SELECT type_desc, name, physical_name from sys.database_files  
    ```  
  
3.  Copiez le script [!INCLUDE[tsql](../../includes/tsql-md.md)] suivant dans l’Éditeur de requête, puis cliquez sur **Exécuter**. Ce code met la base de données `Archive` hors connexion.  
  
    ```tsql  
    USE master  
    EXEC sp_detach_db Archive  
    GO  
    ```  
  
4.  Créez le dossier `C:\moved_location`dans lequel vous allez placer les fichiers et les dossiers listés à l'étape 2.  
  
5.  Copiez le script [!INCLUDE[tsql](../../includes/tsql-md.md)] suivant dans l’Éditeur de requête, puis cliquez sur **Exécuter**. Ce script met la base de données `Archive` en ligne.  
  
    ```tsql  
    CREATE DATABASE Archive ON  
    PRIMARY ( NAME = Arch1,  
        FILENAME = 'c:\moved_location\archdat1.mdf'),  
    FILEGROUP FileStreamGroup1 CONTAINS FILESTREAM( NAME = Arch3,  
        FILENAME = 'c:\moved_location\filestream1')  
    LOG ON  ( NAME = Archlog1,  
        FILENAME = 'c:\moved_location\archlog1.ldf')  
    FOR ATTACH  
    GO  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_detach_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md)  
  
  