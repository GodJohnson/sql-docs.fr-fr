---
title: Changer le compte pour la journalisation SSIS Scale Out| Microsoft Docs
description: Cet article explique comment changer le compte d’utilisateur pour la journalisation de SSIS Scale Out.
ms.custom: performance
ms.date: 12/13/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: douglasl
ms.technology: integration-services
ms.topic: conceptual
author: haoqian
ms.author: haoqian
manager: craigg
ms.openlocfilehash: 4bbb7d1fff70060ec0d3cf5878710177a231896e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47727857"
---
# <a name="change-the-account-for-scale-out-logging"></a>Changer le compte pour la journalisation Scale Out
Quand vous exécutez des packages SSIS dans Scale Out, les messages d’événement sont journalisés dans la base de données SSISDB avec un compte d’utilisateur créé automatiquement et nommé **##MS_SSISLogDBWorkerAgentLogin##**. La connexion pour cet utilisateur utilise l’authentification SQL Server.

Si vous souhaitez changer le compte utilisé pour la journalisation Scale Out, effectuez les opérations suivantes :

> [!NOTE]
> Si vous utilisez un compte d’utilisateur Windows pour la journalisation, utilisez le même compte que celui qui exécute le service Scale Out Worker. Sinon, la connexion à SQL Server échoue.

## <a name="1-create-a-user-for-ssisdb"></a>1. Créer un utilisateur pour SSISDB
Pour savoir comment créer un utilisateur de base de données, consultez [Créer un utilisateur de base de données](../../relational-databases/security/authentication-access/create-a-database-user.md).

## <a name="2-add-the-user-to-the-database-role-ssisclusterworker"></a>2. Ajouter l’utilisateur au rôle de base de données ssis_cluster_worker

Pour savoir comment joindre un rôle de base de données, consultez [Joindre un rôle](../../relational-databases/security/authentication-access/join-a-role.md).

## <a name="3-update-the-logging-information-in-ssisdb"></a>3. Mettre à jour les informations de journalisation dans SSISDB
Appelez la procédure stockée `[catalog].[update_logdb_info]` en utilisant le nom SQL Server et la chaîne de connexion comme paramètres, comme indiqué dans l’exemple suivant :

    ```sql
    SET @serverName = CONVERT(sysname, SERVERPROPERTY('servername'))
    SET @connectionString = 'Data Source=' + @serverName + ';Initial Catalog=SSISDB;Integrated Security=SSPI;'
    EXEC [internal].[update_logdb_info] @serverName, @connectionString
    GO
    ```

## <a name="4-restart-the-scale-out-worker-service"></a>4. Redémarrer le service Scale Out Worker
Redémarrez le service Scale Out Worker pour que la modification prenne effet.

## <a name="next-steps"></a>Étapes suivantes
-   [Integration Services Scale Out Manager](integration-services-ssis-scale-out-manager.md)
