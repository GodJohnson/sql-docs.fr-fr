---
title: Un logiciel antivirus - Analytique Platform System | Microsoft Docs
description: Si votre centre de données requiert un logiciel antivirus, utilisez ces instructions pour installer un logiciel antivirus sur le système de plateforme d’Analytique. Nous vous recommandons de ne pas installer un logiciel antivirus, sauf si elle est une exigence stricte de votre centre de données.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/24/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 2bf94fb04bd6f96de019c7e8543b8a626cebe439
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51699116"
---
# <a name="antivirus-software-for-analytics-platform-system"></a>Logiciel antivirus pour l’Analytique Platform System
Si votre centre de données requiert un logiciel antivirus, utilisez ces instructions pour installer un logiciel antivirus sur le système de plateforme d’Analytique. Nous vous recommandons de ne pas installer un logiciel antivirus, sauf si elle est une exigence stricte de votre centre de données.  
  
> [!WARNING]  
> Nous recommandons vivement que vous individuellement à évaluer les risques de sécurité pour chaque ordinateur et pour l’Analytique Platform System dans sa globalité, et que vous sélectionnez les outils appropriés pour le niveau de risque de sécurité de chaque ordinateur. En outre, nous vous recommandons d’avant de mettre tout projet de protection contre les virus, tester l’ensemble du système sous une charge complète pour mesurer les modifications de stabilité et de performances.  
>   
> Protection antivirus nécessite des ressources système à exécuter. Vous devez effectuer le test avant et après l’installation de votre logiciel antivirus pour déterminer s’il y a aucun effet de performances sur le système de plateforme d’Analytique.  
  
Cette rubrique est basée sur les conseils de [comment choisir un logiciel antivirus s’exécute sur les ordinateurs qui exécutent SQL Server](https://support.microsoft.com/kb/309422) et [961804 de l’Article de base de connaissances](https://support.microsoft.com/kb/961804/en-us).  
  
## <a name="exclusion-list-for-physical-hosts"></a>Liste d’exclusion pour les hôtes physiques  
Pour installer le logiciel antivirus sur les hôtes physiques, exclure la liste suivante des répertoires et des processus. Ils ne doivent pas être analysés par le logiciel antivirus.  
  
**Exclure ces répertoires :**  
  
-   C:\ProgramData\Microsoft\Windows\Hyper-V - répertoire de configuration de machine virtuelle  
  
-   Disques durs C:\Users\Public\Documents\Hyper-V\Virtual - répertoire de disque dur virtuel par défaut  
  
-   C:\clusterStorage - répertoires de disque dur virtuel  
  
**Exclure les processus :**  
  
-   Gestion d’ordinateurs virtuels (Vmms.exe)  
  
-   Processus de travail de machine virtuelle (Vmwp.exe)  
  
## <a name="exclusion-list-for-virtual-machines-vms"></a>Liste d’exclusion pour les Machines virtuelles (VM)  
Pour installer le logiciel antivirus sur les machines virtuelles, exclure la liste suivante des répertoires et fichiers. Ils ne doivent pas être analysés par le logiciel antivirus.  
  
***PDW_region*-CTL01**  
  
-   C:\windows\cluster\  
  
-   G:\  
  
***appliance_domain *-AD01** et ***appliance_domain *-AD02**  
  
-   Aucune restriction  
  
**Machines virtuelles de nœud de calcul**  
  
-   C:\windows\cluster\  
  
-   G:\  
  
***appliance_domain*-VMM**  
  
-   Aucune restriction  
  
***appliance_domain*-WDS**  
  
-   Aucune restriction  
  
***appliance_domain*-ISCSI01**  
  
-   C:\iscsitarget  
  
## <a name="see-also"></a>Voir aussi  
[Tâches de gestion appliance &#40;Analytique Platform System&#41;](appliance-management-tasks.md)  
  
