---
title: OriginalValue et UnderlyingValue, exemple de propriétés (VB) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- UnderlyingValue property [ADO], Visual Basic example
- OriginalValue property [ADO]
ms.assetid: 1750804b-d7ef-47d6-8d73-1f51fa1cbe4a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 95e09a0b3618d88929a0474e7a611d4ea1680793
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47688377"
---
# <a name="originalvalue-and-underlyingvalue-properties-example-vb"></a>OriginalValue et UnderlyingValue, exemple de propriétés (VB)
Cet exemple montre la [OriginalValue](../../../ado/reference/ado-api/originalvalue-property-ado.md) et [UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md) propriétés en affichant un message si les données sous-jacentes d’un enregistrement a changé pendant un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) mise à jour par lots.  
  
```  
'BeginOriginalValueVB  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection string  
  
    Dim Cnxn As ADODB.Connection  
    Dim rstTitles As ADODB.Recordset  
    Dim fldType As ADODB.Field  
    Dim strCnxn As String  
    Dim strSQLTitles As String  
  
    ' Open connection.  
    Set Cnxn = New ADODB.Connection  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    Cnxn.Open strCnxn  
  
    ' Open recordset for batch update  
    ' using object refs to set properties  
    Set rstTitles = New ADODB.Recordset  
    Set rstTitles.ActiveConnection = Cnxn  
    rstTitles.CursorType = adOpenKeyset  
    rstTitles.LockType = adLockBatchOptimistic  
    strSQLTitles = "titles"  
    rstTitles.Open strSQLTitles  
  
    ' Set field object variable for Type field  
    Set fldType = rstTitles!Type  
  
    ' Change the type of psychology titles  
    Do Until rstTitles.EOF  
        If Trim(fldType) = "psychology" Then  
            fldType = "self_help"  
        End If  
        rstTitles.MoveNext  
    Loop  
  
    ' Similate a change by another user by updating  
    ' data using a command string  
    Cnxn.Execute "UPDATE Titles SET type = 'sociology' " & _  
       "WHERE type = 'psychology'"  
  
    'Check for changes  
    rstTitles.MoveFirst  
    Do Until rstTitles.EOF  
        If fldType.OriginalValue <> fldType.UnderlyingValue Then  
            MsgBox "Data has changed!" & vbCr & vbCr & _  
                "  Title ID: " & rstTitles!title_id & vbCr & _  
                "  Current value: " & fldType & vbCr & _  
                "  Original value: " & _  
                fldType.OriginalValue & vbCr & _  
                "  Underlying value: " & _  
                fldType.UnderlyingValue & vbCr  
        End If  
    rstTitles.MoveNext  
    Loop  
  
    ' Cancel the update because this is a demonstration  
    rstTitles.CancelBatch  
  
    ' Restore original values  
    Cnxn.Execute "UPDATE Titles SET type = 'psychology' " & _  
        "WHERE type = 'sociology'"  
  
    ' clean up  
    rstTitles.Close  
    Cnxn.Close  
    Set rstTitles = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not rstTitles Is Nothing Then  
        If rstTitles.State = adStateOpen Then rstTitles.Close  
    End If  
    Set rstTitles = Nothing  
  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then Cnxn.Close  
    End If  
    Set Cnxn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndOriginalValueVB  
```  
  
## <a name="see-also"></a>Voir aussi  
 [OriginalValue, propriété (ADO)](../../../ado/reference/ado-api/originalvalue-property-ado.md)   
 [Objet Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [UnderlyingValue, propriété](../../../ado/reference/ado-api/underlyingvalue-property.md)
