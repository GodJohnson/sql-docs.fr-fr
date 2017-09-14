---
title: "Codage d’un énumérateur Foreach personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom foreach enumerators [Integration Services], coding
ms.assetid: 279cf6de-d06f-40e7-b8ca-569310449f36
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 74e6e838c3dcfb18e52a8fbf460a5b71ee25399a
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="coding-a-custom-foreach-enumerator"></a>Codage d'un énumérateur Foreach personnalisé
  Après avoir créé une classe qui hérite de la classe de base <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator>, puis appliqué l'attribut <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute> à cette classe, vous devez substituer l'implémentation des propriétés et des méthodes de la classe de base afin de fournir vos fonctionnalités personnalisées.  
  
 Pour un exemple fonctionnel d’énumérateur personnalisé, consultez [développement d’une Interface utilisateur pour un énumérateur ForEach personnalisé](../../../integration-services/extending-packages-custom-objects/foreach-enumerator/developing-a-user-interface-for-a-custom-foreach-enumerator.md).  
  
## <a name="initializing-the-enumerator"></a>Initialisation de l'énumérateur  
 Vous pouvez substituer la méthode <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.InitializeForEachEnumerator%2A> pour mettre en cache des références aux gestionnaires de connexions définis dans le package et des références à l'interface d'événements qui vous permet de déclencher des erreurs, des avertissements et des messages d'information.  
  
## <a name="validating-the-enumerator"></a>Validation de l'énumérateur  
 Substituez la méthode <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.Validate%2A> pour vérifier que l'énumérateur est correctement configuré. Si la méthode retourne **échec**, l’énumérateur et le package qui contient l’énumérateur ne seront pas exécutés. L'implémentation de cette méthode est propre à chaque énumérateur, mais si l'énumérateur utilise des objets <xref:Microsoft.SqlServer.Dts.Runtime.Variable> ou <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>, vous devez ajouter du code pour vérifier que ces objets existent dans les collections fournies à la méthode.  
  
 L'exemple de code suivant montre une implémentation de <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.Validate%2A> qui recherche une variable spécifiée dans une propriété de l'énumérateur.  
  
```csharp  
private string variableNameValue;  
  
public string VariableName  
{  
    get{ return this.variableNameValue; }  
    set{ this.variableNameValue = value; }  
}  
  
public override DTSExecResult Validate(Connections connections, VariableDispenser variableDispenser, IDTSInfoEvents infoEvents, IDTSLogging log)  
{  
    if (!variableDispenser.Contains(this.variableNameValue))  
    {  
        infoEvents.FireError(0, "MyEnumerator", "The Variable " + this.variableNameValue + " does not exist in the collection.", "", 0);  
            return DTSExecResult.Failure;  
    }  
    return DTSExecResult.Success;  
}  
```  
  
```vb  
Private variableNameValue As String  
  
Public Property VariableName() As String  
    Get   
         Return Me.variableNameValue  
    End Get  
    Set (ByVal Value As String)   
         Me.variableNameValue = value  
    End Set  
End Property  
  
Public Overrides Function Validate(ByVal connections As Connections, ByVal variableDispenser As VariableDispenser, ByVal infoEvents As IDTSInfoEvents, ByVal log As IDTSLogging) As DTSExecResult  
    If Not variableDispenser.Contains(Me.variableNameValue) Then  
        infoEvents.FireError(0, "MyEnumerator", "The Variable " + Me.variableNameValue + " does not exist in the collection.", "", 0)  
            Return DTSExecResult.Failure  
    End If  
    Return DTSExecResult.Success  
End Function  
```  
  
## <a name="returning-the-collection"></a>Retour de la collection  
 Pendant l’exécution, le <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> conteneur appelle le <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> méthode de l’énumérateur personnalisé. Dans cette méthode, l'énumérateur crée et remplit sa collection d'éléments, puis retourne la collection. Le conteneur <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> itère ensuite les éléments dans la collection et exécute son flux de contrôle pour chacun d'eux.  
  
 L'exemple suivant présente une implémentation de <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> qui retourne un tableau d'entiers aléatoires.  
  
```csharp  
public override object GetEnumerator()  
{  
    ArrayList numbers = new ArrayList();  
  
    Random randomNumber = new Random(DateTime.Now);  
  
    for( int x=0; x < 100; x++ )  
        numbers.Add( randomNumber.Next());  
  
    return numbers;  
}  
```  
  
```vb  
Public Overrides Function GetEnumerator() As Object  
    Dim numbers As ArrayList =  New ArrayList()   
  
    Dim randomNumber As Random =  New Random(DateTime.Now)   
  
        Dim x As Integer  
        For  x = 0 To  100- 1  Step  x + 1  
        numbers.Add(randomNumber.Next())  
        Next  
  
    Return numbers  
End Function  
```  
 
## <a name="see-also"></a>Voir aussi  
 [Création d’un énumérateur Foreach personnalisé](../../../integration-services/extending-packages-custom-objects/foreach-enumerator/creating-a-custom-foreach-enumerator.md)   
 [Développement d’une Interface utilisateur pour un énumérateur ForEach personnalisé](../../../integration-services/extending-packages-custom-objects/foreach-enumerator/developing-a-user-interface-for-a-custom-foreach-enumerator.md)  
  
  