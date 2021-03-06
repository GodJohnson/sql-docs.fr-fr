---
title: À l’aide de la résolution d’adresses IP réseau Transparent | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d255208f-d486-4ad3-8080-61c6e0261825
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 767e3e17b67a36bca93bd8a85704d50338fdfd58
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47610741"
---
# <a name="using-transparent-network-ip-resolution"></a>Utilisation de la résolution d’adresses IP réseau transparente
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

TransparentNetworkIPResolution est une révision de la fonctionnalité existante MultiSubnetFailover, disponible dans Microsoft ODBC Driver 13.1 for SQL Server, ce qui affecte la séquence de connexion du pilote dans le cas où la première adresse IP résolue du nom d’hôte ne le fait pas répondre et il y a plusieurs adresses IP associée avec le nom d’hôte. Il interagit avec MultiSubnetFailover pour fournir les séquences de trois connexions suivantes :

* 0 : une adresse IP est tentée, suivie de toutes les adresses IP en parallèle
* 1 : toutes les adresses IP sont tentées en parallèle
* 2 : toutes les adresses IP sont tentées une après l’autre

|transparentNetworkIPResolution|MultiSubnetFailover|Comportement|
|:-:|:-:|:-:|
|(par défaut)|(par défaut)|0|
|(par défaut)|Activé|1|
|(par défaut)|Désactivé|0|
|Activé|(par défaut)|0|
|Activé|Activé|1|
|Activé|Désactivé|0|
|Désactivé|(par défaut)|2|
|Désactivé|Activé|1|
|Désactivé|Désactivé|2|

Le `TransparentNetworkIPResolution` chaîne de connexion et DSN mot clé contrôle ce paramètre au niveau de la chaîne de connexion. La valeur par défaut est activée.

Mot clé|Valeurs|Valeur par défaut
-|-|-
`TransparentNetworkIPResolution`|`Yes`, `No`|`Yes`

Le `SQL_COPT_SS_TNIR` attribut de préconnexion permet à une application contrôler ce paramètre par programmation :

Attribut de connexion|   Taille et le Type|  Valeur par défaut| Valeur| Description
-|-|-|-|-
`SQL_COPT_SS_TNIR` (1249)| `SQL_IS_INTEGER` ou `SQL_IS_UINTEGER`| `SQL_IS_ON`(1), `SQL_IS_OFF`(0)|`SQL_IS_ON`|Active ou désactive les TNIR.

<a name="for-more-information-about-multisubnetfailover-see-odbc-driver-on-linux-and-macos---high-availability-and-disaster-recoveryconnectodbclinux-macodbc-driver-on-linux-support-for-high-availability-disaster-recoverymd"></a>Pour plus d’informations sur MultiSubnetFailover, consultez [pilote ODBC sur Linux et macOS - haute disponibilité et récupération d’urgence](../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md)
--------------------------------------------------
## <a name="see-also"></a> Voir aussi  
* [Microsoft ODBC Driver for SQL Server sur Windows](../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)
* [Clustering de sous-réseaux multiples SQL Server (SQL Server)](https://msdn.microsoft.com/library/ff878716.aspx#RelatedContent)
