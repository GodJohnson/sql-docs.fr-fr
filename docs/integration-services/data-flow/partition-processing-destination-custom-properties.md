---
title: Propriétés personnalisées de la destination de traitement de partition | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3eac4413-0c90-4b06-8f7e-d0d72f4d869d
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 95fc60d5771d298f118eb97c4ef4083278706ce9
ms.sourcegitcommit: 0638b228980998de9056b177c83ed14494b9ad74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2018
ms.locfileid: "51639416"
---
# <a name="partition-processing-destination-custom-properties"></a>Propriétés personnalisées de la destination de traitement de partition
  La destination de traitement de partition comporte à la fois des propriétés personnalisées et les propriétés communes à l'ensemble des composants de flux de données.  
  
 Le tableau suivant décrit les propriétés personnalisées de la destination de traitement de partition. Toutes les propriétés sont en lecture/écriture.  
  
|Propriété|Type de données|Description|  
|--------------|---------------|-----------------|  
|ASConnectionString|String|Chaîne de connexion d'un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou d'une instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|KeyDuplicate|Integer (énumération)|Quand UseDefaultConfiguration a la valeur **False**, valeur qui indique comment gérer les erreurs de clé en double. Les valeurs possibles sont **IgnoreError** (0), **ReportAndContinue** (1) et **ReportAndStop** (2). La valeur par défaut de cette propriété est **IgnoreError** (0).|  
|KeyErrorAction|Integer (énumération)|Quand UseDefaultConfiguration a la valeur **False**, valeur qui indique comment gérer les erreurs de clé. Les valeurs possibles sont **ConvertToUnknown** (0) et **DiscardRecord** (1). La valeur par défaut de cette propriété est **ConvertToUnknown** (0).|  
|KeyErrorLimit|Entier|Quand UseDefaultConfiguration a la valeur **False**, limite supérieure des erreurs de clé autorisées.|  
|KeyErrorLimitAction|Integer (énumération)|Quand UseDefaultConfiguration a la valeur **False**, valeur qui indique l’action à entreprendre quand la limite **KeyErrorLimit** est atteinte. Les valeurs possibles sont **StopLogging** (1) et **StopProcessing** (0). La valeur par défaut de cette propriété est **StopProcessing** (0).|  
|KeyErrorLogFile|String|Quand UseDefaultConfiguration a la valeur **False**, chemin et nom du fichier journal des erreurs.|  
|KeyNotFound|Integer (énumération)|Quand UseDefaultConfiguration a la valeur **False**, valeur qui indique comment gérer les erreurs de clé manquante. Les valeurs possibles sont **IgnoreError** (0), **ReportAndContinue** (1) et **ReportAndStop** (2). La valeur par défaut de cette propriété est **ReportAndContinue** (1).|  
|NullKeyConvertedToUnknown|Integer (énumération)|Quand UseDefaultConfiguration a la valeur **False**, valeur qui indique comment gérer les clés null converties en valeur inconnue. Les valeurs possibles sont **IgnoreError** (0), **ReportAndContinue** (1) et **ReportAndStop** (2). La valeur par défaut de cette propriété est **IgnoreError** (0).|  
|NullKeyNotAllowed|Integer (énumération)|Quand UseDefaultConfiguration a la valeur **False**, valeur qui indique comment gérer les clés null non autorisées. Les valeurs possibles sont **IgnoreError** (0), **ReportAndContinue** (1) et **ReportAndStop** (2). La valeur par défaut de cette propriété est **ReportAndContinue** (1).|  
|ProcessType|Integer (énumération)|Type de traitement de partition que la transformation utilise. Les valeurs possible sont **ProcessAdd** (1) (incrémentiel), **ProcessFull** (0) et **ProcessUpdate** (2).|  
|UseDefaultConfiguration|Booléen|Valeur qui spécifie si la transformation utilise la configuration d'erreur par défaut. Si cette propriété a la valeur **False**, la transformation utilise les propriétés personnalisées de traitement des erreurs répertoriées dans ce tableau, notamment KeyDuplicate, KeyErrorAction, et ainsi de suite.|  
  
 L'entrée et les colonnes d'entrée de la destination de traitement de partition ne disposent pas de propriétés personnalisées.  
  
 Pour plus d’informations, consultez [Destination de traitement de partition](../../integration-services/data-flow/partition-processing-destination.md).  
  
## <a name="see-also"></a> Voir aussi  
 [Propriétés communes](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
