---
title: "Élément LastDataUpdate (XMLA) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- LastDataUpdate Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.lastdataupdate
- http://schemas.microsoft.com/analysisservices/2003/engine#LastDataUpdate
- urn:schemas-microsoft-com:xml-analysis#LastDataUpdate
helpviewer_keywords:
- LastDataUpdate element
ms.assetid: 66e43b17-844f-4ec2-bd1d-35608e7b6524
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 160e0792348cc47ebea64a8b19d0b9e8464900f8
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="lastdataupdate-element-xmla"></a>Élément LastDataUpdate (XMLA)
  Contient la date et l'heure de la dernière mise à jour des données du cube représenté par l'élément [Cube](../../../analysis-services/xmla/xml-elements-properties/cube-element-olapinfo-xmla.md) parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Cube>  
   ...  
   <LastDataUpdate>...</LastDataUpdate>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|dateTime|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Cube](../../../analysis-services/xmla/xml-elements-properties/cube-element-olapinfo-xmla.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  