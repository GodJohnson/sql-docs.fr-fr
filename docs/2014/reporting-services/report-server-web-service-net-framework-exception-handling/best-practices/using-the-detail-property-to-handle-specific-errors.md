---
title: Utilisation de la propriété Detail pour gérer des erreurs spécifiques | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], Detail property
- Detail property
- InnerText property
ms.assetid: 4392633d-b46b-41e6-bc12-efb64e166704
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 1966cd4898731b5176541a8dd0707bf0deef25bf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48222879"
---
# <a name="using-the-detail-property-to-handle-specific-errors"></a>Utilisation de la propriété Detail pour gérer des erreurs spécifiques
  Pour mieux classifier les exceptions, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] retourne des informations supplémentaires sur l’erreur dans la propriété**InnerText** des éléments enfants dans la propriété **Detail** de l’exception SOAP. Dans la mesure où la propriété **Detail** est un objet **XmlNode**, vous pouvez accéder au texte interne de l’élément enfant **Message** à l’aide du code indiqué ci-après.  
  
 Pour obtenir la liste de tous les éléments enfants disponibles dans la propriété **Detail**, consultez [Detail, propriété](../soapexception-class/detail-property.md). Pour plus d’informations, consultez « Detail, propriété » dans la documentation du SDK [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
```vb  
Try  
' Code for accessing the report server  
Catch ex As SoapException  
   ' The exception is a SOAP exception, so use  
   ' the Detail property's Message element.  
   Console.WriteLine(ex.Detail("Message").InnerXml)  
End Try  
```  
  
```csharp  
try  
{  
   // Code for accessing the report server  
}  
catch (SoapException ex)  
{  
   // The exception is a SOAP exception, so use  
   // the Detail property's Message element.  
   Console.WriteLine(ex.Detail["Message"].InnerXml);  
}  
```  
  
```vb  
Try  
' Code for accessing the report server  
Catch ex As SoapException  
   If ex.Detail("ErrorCode").InnerXml = "rsInvalidItemName" Then  
   End If ' Perform an action based on the specific error code  
End Try  
```  
  
```csharp  
try  
{  
   // Code for accessing the report server  
}  
catch (SoapException ex)  
{  
   if (ex.Detail["ErrorCode"].InnerXml == "rsInvalidItemName")  
   {  
      // Perform an action based on the specific error code  
   }  
}  
```  
  
 La ligne de code suivante écrit le code d'erreur spécifique qui est retourné dans l'exception SOAP sur la console. Vous pouvez également évaluer le code d'erreur et effectuer des actions spécifiques.  
  
```vb  
Console.WriteLine(ex.Detail("ErrorCode").InnerXml)  
```  
  
```csharp  
Console.WriteLine(ex.Detail["ErrorCode"].InnerXml);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de la gestion des exceptions dans Reporting Services](../introducing-exception-handling-in-reporting-services.md)   
 [SoapException, classe Reporting Services](../soapexception-class/reporting-services-soapexception-class.md)   
 [Table d'erreurs SoapException](../soapexception-class/soapexception-errors-table.md)  
  
  
