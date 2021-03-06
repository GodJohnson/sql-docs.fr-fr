---
title: Nettoyer les données dans un domaine composite | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 7d1076e0-7710-469a-9107-e293e4bd80ac
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1302a354255c6b98a46cd2c1aef234fe3f1c5f67
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2018
ms.locfileid: "51029257"
---
# <a name="cleanse-data-in-a-composite-domain"></a>Nettoyer les données dans un domaine composite
  Cette rubrique fournit des informations sur le nettoyage des domaines composites dans [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Un domaine composite comprend plusieurs domaines uniques et est mappé à un champ de données qui comprend plusieurs termes connexes. Les différents domaines dans un domaine composite doivent avoir un espace commun de connaissance. Pour plus d'informations sur les domaines composites, consultez [Managing a Composite Domain](../../2014/data-quality-services/managing-a-composite-domain.md).  
  
##  <a name="Mapping"></a> Mappage d'un domaine composite aux données sources  
 Il existe deux façons de mapper vos données sources à un domaine composite :  
  
-   Les données sources sont un champ unique (par exemple, Nom complet), qui est mappé à un domaine composite.  
  
    -   Si le domaine composite est mappé à un service de données de référence, les données sources sont envoyées telles quelles au service de données de référence pour correction et analyse.  
  
    -   Si le domaine composite n'est pas mappé à un service de données de référence, l'analyse est effectuée selon la méthode définie pour le domaine composite. Pour plus d'informations sur la spécification d'une méthode d'analyse pour les domaines composites, consultez [Create a Composite Domain](../../2014/data-quality-services/create-a-composite-domain.md)  
  
-   Les données sources sont constituées de plusieurs champs (par exemple, Prénom, Deuxième prénom et Nom) qui sont mappés à des domaines différents dans un domaine composite.  
  
 Pour obtenir un exemple montrant comment mapper des domaines composites aux données sources, consultez [joindre un domaine ou un domaine Composite aux données de référence](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md).  
  
##  <a name="CDCorrection"></a> Correction des données à l'aide de règles entre domaines définitives  
 Les règles entre domaines dans le domaine composite vous permettent de créer des règles qui indiquent la relation entre différents domaines dans un domaine composite. Les règles entre domaines sont prises en considération lorsque vous exécutez l'activité de nettoyage sur vos données sources impliquant des domaines composites. Outre l'information concernant la validité d'une règle entre domaines, la règle entre domaines *Then* définitive, **La valeur est égale à**, corrige également les données pendant l'activité de nettoyage.  
  
 Prenons l'exemple suivant : il existe un domaine composite, Product, avec trois domaines individuels : ProductName, CompanyName et ProductVersion. Créez la règle entre domaines définitive suivante :  
  
 SI la valeur « CompanyName » du domaine contient *Microsoft* , que la valeur « ProductName » du domaine est égale à *Office* et que la valeur « ProductVersion » est égale à *2010* , ALORS la valeur « ProductName » du domaine est égale à *Microsoft Office 2010*.  
  
 Lorsque cette règle entre domaines s'exécute, les données sources (ProductName) sont remplacées par ce qui suit après l'activité de nettoyage :  
  
 **Données sources**  
  
|ProductName|CompanyName|ProductVersion|  
|-----------------|-----------------|--------------------|  
|Office|Microsoft Inc.|2010|  
  
 **Données de sortie**  
  
|ProductName|CompanyName|ProductVersion|  
|-----------------|-----------------|--------------------|  
|Microsoft Office 2010|Microsoft Inc.|2010|  
  
 Lorsque vous testez la règle entre domaines *Then* définitive, **La valeur est égale à**, la boîte de dialogue **Tester la règle de domaine composite** contient une nouvelle colonne, **Corriger vers**, qui affiche les données correctes. Dans un projet de qualité des données de nettoyage, cette règle entre domaines définitive modifie les données avec un niveau de confiance de 100 % et la colonne **Raison** affiche le message suivant : Corrigé par la règle «*\<Nom de la règle entre domaines>*. Pour plus d'informations sur les règles entre domaines, consultez [Create a Cross-Domain Rule](../../2014/data-quality-services/create-a-cross-domain-rule.md).  
  
> [!NOTE]  
>  La règle entre domaines définitive ne fonctionne pas pour les domaines composites joints au service de données de référence.  
  
##  <a name="DataProfiling"></a> Profilage des données pour les domaines composites  
 Le profilage DQS fournit deux dimensions de qualité des données : l' *exhaustivité* (dans quelle mesure les données sont présentes) et la *précision* (dans quelle mesure les données peuvent être utilisées pour l'usage prévu) pendant l'activité de nettoyage. Le profilage peut ne pas fournir des statistiques d'exhaustivité fiables pour les domaines composites. Si vous avez besoin des statistiques d'exhaustivité, utilisez des domaines simples plutôt que des domaines composites. Si vous souhaitez utiliser les domaines composites, vous pouvez créer une base de connaissances avec des domaines simples pour le profilage, afin de déterminer l'exhaustivité, et créer un autre domaine avec un domaine composite pour l'activité de nettoyage. Par exemple, le profilage peut afficher une exhaustivité de 95 % pour les enregistrements d'adresse à l'aide d'un domaine composite, mais il peut y avoir un niveau bien supérieur de non-exhaustivité pour l'une des colonnes, par exemple, une colonne de code postal. Dans cet exemple, vous pouvez mesurer l'exhaustivité de la colonne de code postal avec un domaine unique.  
  
 Le profilage fournira probablement des statistiques de précision fiables pour les domaines composites, car vous pouvez mesurer la précision de plusieurs colonnes ensemble. Comme la valeur de ces données se trouve dans l'agrégation composite, vous pouvez mesurer la précision avec un domaine composite.  
  
 Pour plus d’informations sur le profilage des données pendant l’activité de nettoyage, consultez [Statistiques du Générateur de profils](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Profiler) dans [Nettoyer des données à l’aide de la base de connaissances DQS &#40 ;interne&#41;](../../2014/data-quality-services/cleanse-data-using-dqs-internal-knowledge.md).  
  
  
