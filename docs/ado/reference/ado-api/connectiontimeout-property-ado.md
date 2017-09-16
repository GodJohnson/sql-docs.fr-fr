---
title: "ConnectionTimeout, propriété (ADO) | Documents Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Connection15::ConnectionTimeout
helpviewer_keywords:
- ConnectionTimeout property [ADO]
ms.assetid: 8904a403-1383-4b4b-b53d-5c01d6f5deac
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d00956df35fc6b3f5d6d864ea72d9efdea69fe56
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="connectiontimeout-property-ado"></a>ConnectionTimeout, propriété (ADO)
Indique le délai d’attente lors de l’établissement d’une connexion avant d’abandonner la tentative et de générer une erreur.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un **Long** valeur qui indique, en secondes, la durée d’attente pour la connexion à ouvrir. Valeur par défaut est 15.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **ConnectionTimeout** propriété sur un [connexion](../../../ado/reference/ado-api/connection-object-ado.md) si retards dus au réseau du trafic ou serveur une utilisation intensive rendent nécessaire d’abandonner une tentative de connexion de l’objet. Si l’heure à partir de la **ConnectionTimeout** paramètre de la propriété s’écoule avant l’ouverture de la connexion, une erreur se produit et ADO annule la tentative. Si vous définissez la propriété sur zéro, ADO attend indéfiniment que la connexion est ouverte. Assurez-vous que le fournisseur auquel vous écrivez du code prend en charge la **ConnectionTimeout** fonctionnalité.  
  
 Le **ConnectionTimeout** propriété est en lecture/écriture lorsque la connexion est fermée et en lecture seule lorsqu’il est ouvert.  
  
## <a name="applies-to"></a>S'applique à  
 [Objet de connexion (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [ConnectionString, ConnectionTimeout et propriétés de l’état d’exemple (VB)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [ConnectionString, ConnectionTimeout et l’état d’exemple (VC ++)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
 [CommandTimeout, propriété (ADO)](../../../ado/reference/ado-api/commandtimeout-property-ado.md)
