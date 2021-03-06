---
title: Configurer les paramètres de SQL Server avec les variables d’environnement | Microsoft Docs
description: Cet article décrit comment utiliser des variables d’environnement pour configurer les paramètres spécifiques de SQL Server 2017 sur Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/20/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: 87e4d1ed1bdb1ce78e2f45fcb49019175fcdfefd
ms.sourcegitcommit: a2be75158491535c9a59583c51890e3457dc75d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2018
ms.locfileid: "51269692"
---
# <a name="configure-sql-server-settings-with-environment-variables-on-linux"></a>Configurer les paramètres de SQL Server avec les variables d’environnement sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

Vous pouvez utiliser plusieurs variables d’environnement différent pour configurer SQL Server 2017 sur Linux. Ces variables sont utilisées dans deux scénarios :

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

Vous pouvez utiliser plusieurs variables d’environnement différentes pour configurer la version préliminaire de SQL Server 2019 sur Linux. Ces variables sont utilisées dans deux scénarios :

::: moniker-end

- Pour configurer l’installation initiale avec le `mssql-conf setup` commande.
- Pour configurer un nouveau [conteneur SQL Server dans Docker](quickstart-install-connect-docker.md).

> [!TIP]
> Si vous avez besoin configurer SQL Server après ces scénarios d’installation, consultez [configurer SQL Server sur Linux avec l’outil mssql-conf](sql-server-linux-configure-mssql-conf.md).

## <a name="environment-variables"></a>Variables d'environnement

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

| Variable d'environnement | Description |
|-----|-----|
| **ACCEPT_EULA** | Acceptez le contrat de licence de SQL Server lorsque la valeur à n’importe quelle valeur (par exemple, « Y »). |
| **MSSQL_SA_PASSWORD** | Configurer le mot de passe SA. |
| **MSSQL_PID** | Définissez la clé de produit ou d’édition de SQL Server. Les valeurs possibles sont : </br></br>**Evaluation**</br>**Développeur**</br>**Express**</br>**Web**</br>**Standard**</br>**Enterprise**</br>**Une clé de produit**</br></br>Si vous spécifiez une clé de produit, il doit être sous la forme de ###-###-###-###-###, où « # » est un nombre ou une lettre.|
| **MSSQL_LCID** | Définit l’ID de langue à utiliser pour SQL Server. Par exemple, 1036 est Français. |
| **MSSQL_COLLATION** | Définit le classement par défaut pour SQL Server. Cela remplace le mappage par défaut de l’id de langue (LCID) pour le classement. |
| **MSSQL_MEMORY_LIMIT_MB** | Définit la quantité maximale de mémoire (en Mo) que SQL Server peut utiliser. Par défaut, il est 80 % de la mémoire physique totale. |
| **MSSQL_TCP_PORT** | Configurer le port TCP qui écoute SQL Server (1433 par défaut). |
| **MSSQL_IP_ADDRESS** | Définissez l’adresse IP. Actuellement, l’adresse IP doit être IPv4 style (0.0.0.0). |
| **MSSQL_BACKUP_DIR** | Définissez l’emplacement du répertoire de sauvegarde par défaut. |
| **MSSQL_DATA_DIR** | Accédez au répertoire où les fichiers de données de base de données (.mdf) SQL Server nouveaux sont créés. |
| **MSSQL_LOG_DIR** | Accédez au répertoire où sont créés les nouveaux fichiers de journal (.ldf) de base de données SQL Server. |
| **MSSQL_DUMP_DIR** | Accédez au répertoire où SQL Server déposera les vidages de mémoire et d’autres fichiers de résolution des problèmes par défaut. |
| **MSSQL_ENABLE_HADR** | Activer le groupe de disponibilité. Par exemple, '1' est activé, et « 0 » est désactivé |
| **MSSQL_AGENT_ENABLED** | Activer l’Agent SQL Server. Par exemple, 'true' est activée et 'false' est désactivé. Par défaut, l’agent est désactivé.  |
| **MSSQL_MASTER_DATA_FILE** | Définit l’emplacement du fichier de données de base de données master. Doit être nommé **master.mdf** jusqu'à ce que la première exécution de SQL Server. |
| **MSSQL_MASTER_LOG_FILE** | Définit l’emplacement du fichier de journal de base de données master. Doit être nommé **mastlog.ldf** jusqu'à ce que la première exécution de SQL Server. |
| **MSSQL_ERROR_LOG_FILE** | Définit l’emplacement des fichiers du journal des erreurs. |

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

| Variable d'environnement | Description |
|-----|-----|
| **ACCEPT_EULA** | Acceptez le contrat de licence de SQL Server lorsque la valeur à n’importe quelle valeur (par exemple, « Y »). |
| **MSSQL_SA_PASSWORD** | Configurer le mot de passe SA. |
| **MSSQL_PID** | Définissez la clé de produit ou d’édition de SQL Server. Les valeurs possibles sont : </br></br>**Evaluation**</br>**Développeur**</br>**Express**</br>**Web**</br>**Standard**</br>**Enterprise**</br>**Une clé de produit**</br></br>Si vous spécifiez une clé de produit, il doit être sous la forme de ###-###-###-###-###, où « # » est un nombre ou une lettre.|
| **MSSQL_LCID** | Définit l’ID de langue à utiliser pour SQL Server. Par exemple, 1036 est Français. |
| **MSSQL_COLLATION** | Définit le classement par défaut pour SQL Server. Cela remplace le mappage par défaut de l’id de langue (LCID) pour le classement. |
| **MSSQL_MEMORY_LIMIT_MB** | Définit la quantité maximale de mémoire (en Mo) que SQL Server peut utiliser. Par défaut, il est 80 % de la mémoire physique totale. |
| **MSSQL_TCP_PORT** | Configurer le port TCP qui écoute SQL Server (1433 par défaut). |
| **MSSQL_IP_ADDRESS** | Définissez l’adresse IP. Actuellement, l’adresse IP doit être IPv4 style (0.0.0.0). |
| **MSSQL_BACKUP_DIR** | Définissez l’emplacement du répertoire de sauvegarde par défaut. |
| **MSSQL_DATA_DIR** | Accédez au répertoire où les fichiers de données de base de données (.mdf) SQL Server nouveaux sont créés. |
| **MSSQL_LOG_DIR** | Accédez au répertoire où sont créés les nouveaux fichiers de journal (.ldf) de base de données SQL Server. |
| **MSSQL_DUMP_DIR** | Accédez au répertoire où SQL Server déposera les vidages de mémoire et d’autres fichiers de résolution des problèmes par défaut. |
| **MSSQL_ENABLE_HADR** | Activer le groupe de disponibilité. Par exemple, '1' est activé, et « 0 » est désactivé |
| **MSSQL_AGENT_ENABLED** | Activer l’Agent SQL Server. Par exemple, 'true' est activée et 'false' est désactivé. Par défaut, l’agent est désactivé.  |
| **MSSQL_MASTER_DATA_FILE** | Définit l’emplacement du fichier de données de base de données master. Doit être nommé **master.mdf** jusqu'à ce que la première exécution de SQL Server. |
| **MSSQL_MASTER_LOG_FILE** | Définit l’emplacement du fichier de journal de base de données master. Doit être nommé **mastlog.ldf** jusqu'à ce que la première exécution de SQL Server. |
| **MSSQL_ERROR_LOG_FILE** | Définit l’emplacement des fichiers du journal des erreurs. |

::: moniker-end

## <a name="use-with-initial-setup"></a>Utiliser avec le programme d’installation initiale

Cet exemple exécute `mssql-conf setup` avec configuré des variables d’environnement. Les variables d’environnement suivantes sont spécifiées :

- **ACCEPT_EULA** accepte le contrat de licence utilisateur final.
- **MSSSQL_PID** spécifie les librement sous licence Developer Edition de SQL Server pour une utilisation hors production.
- **MSSQL_SA_PASSWORD** définit un mot de passe fort.
- **MSSQL_TCP_PORT** définit le port TCP que SQL Server écoute à 1234.

```bash
sudo ACCEPT_EULA='Y' MSSQL_PID='Developer' MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' MSSQL_TCP_PORT=1234 /opt/mssql/bin/mssql-conf setup
```

## <a name="use-with-docker"></a>Utilisation avec Docker

Cet exemple de commande docker utilise les variables d’environnement suivantes pour créer un nouveau conteneur de SQL Server :

- **ACCEPT_EULA** accepte le contrat de licence utilisateur final.
- **MSSSQL_PID** spécifie les librement sous licence Developer Edition de SQL Server pour une utilisation hors production.
- **MSSQL_SA_PASSWORD** définit un mot de passe fort.
- **MSSQL_TCP_PORT** définit le port TCP que SQL Server écoute à 1234. Cela signifie que, au lieu du port de mappage 1433 (par défaut) à un port d’hôte, le port TCP personnalisé doit être mappé avec la `-p 1234:1234` commande dans cet exemple.

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

Si vous exécutez Docker sur Linux/Mac OS, utilisez la syntaxe suivante avec des guillemets simples :

```bash
docker run -e ACCEPT_EULA=Y -e MSSQL_PID='Developer' -e MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' -e MSSQL_TCP_PORT=1234 -p 1234:1234 -d mcr.microsoft.com/mssql/server:2017-latest
```

Si vous exécutez Docker sur Windows, utilisez la syntaxe suivante avec des guillemets doubles :

```bash
docker run -e ACCEPT_EULA=Y -e MSSQL_PID="Developer" -e MSSQL_SA_PASSWORD="<YourStrong!Passw0rd>" -e MSSQL_TCP_PORT=1234 -p 1234:1234 -d mcr.microsoft.com/mssql/server:2017-latest
```

> [!NOTE]
> Le processus d’exécution des éditions de production dans des conteneurs est légèrement différent. Pour plus d’informations, consultez [Exécuter des images conteneur de production](sql-server-linux-configure-docker.md#production).

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

Si vous exécutez Docker sur Linux/Mac OS, utilisez la syntaxe suivante avec des guillemets simples :

```bash
docker run -e ACCEPT_EULA=Y -e MSSQL_PID='Developer' -e MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' -e MSSQL_TCP_PORT=1234 -p 1234:1234 -d mcr.microsoft.com/mssql/server:vNext-CTP2.0-ubuntu
```

Si vous exécutez Docker sur Windows, utilisez la syntaxe suivante avec des guillemets doubles :

```bash
docker run -e ACCEPT_EULA=Y -e MSSQL_PID="Developer" -e MSSQL_SA_PASSWORD="<YourStrong!Passw0rd>" -e MSSQL_TCP_PORT=1234 -p 1234:1234 -d mcr.microsoft.com/mssql/server:vNext-CTP2.0-ubuntu
```

::: moniker-end

## <a name="next-steps"></a>Étapes suivantes

Pour les autres paramètres de SQL Server non répertoriés ici, consultez [configurer SQL Server sur Linux avec l’outil mssql-conf](sql-server-linux-configure-mssql-conf.md).

Pour plus d’informations sur la façon d’installer et exécuter SQL Server sur Linux, consultez [installer SQL Server sur Linux](sql-server-linux-setup.md).
