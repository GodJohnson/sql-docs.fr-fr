---
title: Prise en main de SQL Server dans le Cloud | Microsoft Docs
description: Ce démarrage rapide montre comment exécuter le serveur SQL Server sur Linux dans le cloud de votre choix.
author: annashres
ms.author: annashres
manager: craigg
ms.date: 10/25/2017
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: 8c7131f8b4fb9f9b326e2596d53332b9e6bf9248
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47682977"
---
# <a name="quickstart-run-the-sql-server-in-the-cloud"></a>Démarrage rapide : Exécuter le serveur SQL Server dans le cloud

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Dans ce démarrage rapide, vous allez installer SQL Server sur Red Hat Enterprise Linux (RHEL), SUSE Linux Enterprise Server (SLES) ou Ubuntu dans le cloud de votre choix. Accédez à [approvisionner une machine virtuelle de Linux SQL Server dans le portail Azure](https://docs.microsoft.com/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json) pour exécuter SQL Server sur Linux dans Azure.

    > [!NOTE]
    > If you choose to run a paid edition of SQL Server then you need to bring your own license (BYOL)

## <a name="amazon-web-services"></a>Amazon Web Services
1.  Créer un AMI Linux avec au moins 2 Go de mémoire à partir de la place de marché 
    * [RHEL 7.3 +](https://aws.amazon.com/marketplace/pp/B00KWBZVK6)
    * [SLES v12 SP2](https://aws.amazon.com/marketplace/pp/B00PMM99PI)
    * [Ubuntu 16.04](https://aws.amazon.com/marketplace/pp/B01JBL2M0O)
1.  Se connecter à l’AMI avec ssh
1.  Suivez le Guide de démarrage rapide pour la distribution Linux que vous avez choisi : 
    * [RHEL](quickstart-install-connect-red-hat.md)
    * [SLES](quickstart-install-connect-suse.md)
    * [Ubuntu](quickstart-install-connect-ubuntu.md)
1.  Configurer des connexions à distance : 
    * Ouvrez le [console Amazon EC2]( https://console.aws.amazon.com/ec2/)
    * Dans le volet de navigation, choisissez **groupes de sécurité**. 
    * Choisissez **entrant, modifier, ajouter une règle**
    * Ajouter une règle de trafic entrant pour autoriser le trafic sur le port sur lequel SQL Server écoute (port TCP par défaut 1433)

    
## <a name="digital-ocean"></a>Digital Ocean
1. Connectez-vous à la [le panneau de configuration](https://cloud.digitalocean.com/login) , puis cliquez sur Créer un GOUTTELETTE
1. Choisissez une GOUTTELETTE Ubuntu 16.04 au moins 2 Go de mémoire
1. Se connecter à la GOUTTELETTE avec ssh
1. Suivez le [Guide de démarrage rapide Ubuntu](quickstart-install-connect-ubuntu.md)
1. Configurer des connexions à distance :
    * En haut du Panneau de configuration, suivez la **mise en réseau** lier, puis sélectionnez **les pare-feux**
    * Ajouter une règle de trafic entrant pour autoriser le trafic sur le port sur lequel SQL Server écoute (port TCP par défaut 1433)
    
## <a name="google-cloud-platform"></a>Plateforme Cloud de Google
1.  Créer une image Linux au moins 2 Go de mémoire à partir du Lanceur de Cloud 
    * [RHEL 7.3 +](https://console.cloud.google.com/launcher/details/rhel-cloud/rhel-7)
    * [SLES v12 SP2](https://console.cloud.google.com/launcher/details/suse-cloud/sles-12)
    * [Ubuntu 16.04](https://console.cloud.google.com/launcher/details/ubuntu-os-cloud/ubuntu-xenial)
1.  Se connecter à l’image avec ssh
1.  Suivez le Guide de démarrage rapide pour la distribution Linux que vous avez choisi : 
    * [RHEL](quickstart-install-connect-red-hat.md)
    * [SLES](quickstart-install-connect-suse.md)
    * [Ubuntu](quickstart-install-connect-ubuntu.md)
1.  Configurer des connexions à distance : 
    * Accédez à la [règles de pare-feu](https://console.cloud.google.com/networking/firewalls)
    * Ajouter une règle de trafic entrant pour autoriser le trafic sur le port sur lequel écoute SQL Server (par défaut tcp : 1433)
