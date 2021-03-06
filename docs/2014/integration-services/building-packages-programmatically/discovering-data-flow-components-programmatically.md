---
title: Programmgesteuertes Auffinden von Datenflusskomponenten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- PipelineComponentInfos collection
- data flow task [Integration Services], components
- discovering data flow components
- components [Integration Services], data flow
- data flow [Integration Services], components
ms.assetid: ff92a96a-8af6-4532-82cc-c0bbff92401b
caps.latest.revision: 41
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: df04c8b47d4f803281e07a5f106b2756c2cc0fce
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37285666"
---
# <a name="discovering-data-flow-components-programmatically"></a>Programmgesteuertes Auffinden von Datenflusskomponenten
  Nachdem Sie einem Paket einen Datenflusstask hinzugefügt haben, besteht der nächste Schritt darin zu bestimmen, welche Datenflusskomponenten für Sie zur Verwendung zur Verfügung stehen. Sie können die Datenflussquellen, Transformationen und Ziele, die auf dem lokalen Computer installiert und verfügbar sind, programmgesteuert auffinden. Informationen zum Hinzufügen eines Datenflusstasks zum Paket finden Sie unter [Programmgesteuertes Hinzufügen des Datenflusstasks](../building-packages-programmatically/adding-the-data-flow-task-programmatically.md).  
  
## <a name="discovering-components"></a>Auffinden von Komponenten  
 Die <xref:Microsoft.SqlServer.Dts.Runtime.Application>-Klasse stellt die <xref:Microsoft.SqlServer.Dts.Runtime.Application.PipelineComponentInfos%2A>-Auflistung bereit, die ein <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo>-Objekt für die einzelnen Komponenten enthält, die korrekt auf dem lokalen Computer installiert sind. <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo> enthält Informationen zu einer Komponente, z. B. ihren Namen, eine Beschreibung und ihren Erstellungsnamen. Sie können den in der <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo.CreationName%2A>-Eigenschaft zurückgegebenen Wert verwenden, um die <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A>-Eigenschaft von <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> festzulegen, wenn Sie einem Paket eine Komponente hinzufügen.  
  
## <a name="next-step"></a>Nächster Schritt  
 Nach dem Auffinden verfügbarer Komponenten besteht der nächste Schritt darin, die Komponenten hinzuzufügen und zu konfigurieren. Dies wird im nächsten Thema – [Programmgesteuertes Hinzufügen von Datenflusskomponenten](../building-packages-programmatically/adding-data-flow-components-programmatically.md) – beschrieben.  
  
## <a name="sample"></a>Beispiel  
 Im folgenden Codebeispiel wird gezeigt, wie die <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfos>-Auflistung des <xref:Microsoft.SqlServer.Dts.Runtime.Application>-Objekts aufgezählt wird, um die auf dem lokalen Computer verfügbaren Datenflusskomponenten programmgesteuert aufzufinden. Für dieses Beispiel ist ein Verweis auf die Microsoft.SqlServer.ManagedDTS-Assembly erforderlich.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Application application = new Application();  
      PipelineComponentInfos componentInfos = application.PipelineComponentInfos;  
  
      foreach (PipelineComponentInfo componentInfo in componentInfos)  
      {  
        Console.WriteLine("Name: " + componentInfo.Name + "\n" +  
          " CreationName: " + componentInfo.CreationName + "\n");  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim application As Application = New Application()  
  
    Dim componentInfos As PipelineComponentInfos = application.PipelineComponentInfos  
  
    For Each componentInfo As PipelineComponentInfo In componentInfos  
      Console.WriteLine("Name: " & componentInfo.Name & vbCrLf & _  
        " CreationName: " & componentInfo.CreationName & vbCrLf)  
    Next  
  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
![Integration Services (kleines Symbol)](../media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben oben, um das Datum mit Integration Services  **<br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Programmgesteuertes Hinzufügen von Datenflusskomponenten](../building-packages-programmatically/adding-data-flow-components-programmatically.md)  
  
  
