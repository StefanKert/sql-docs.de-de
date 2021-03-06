---
title: Mithilfe von Lesezeichen | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- bookmarks [ADO]
- Recordset object [ADO]
ms.assetid: cca244e6-84f8-4394-bca9-f7a819b8f4df
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 643d07d49e2e2ec0e31f9a677796f309fedd0d1d
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35273219"
---
# <a name="using-bookmarks"></a>Mithilfe von Lesezeichen
Es ist oft hilfreich, direkt zu einem bestimmten Datensatz zurück, nachdem verschoben haben, der **Recordset** ohne Blättern Sie in jedem Datensatz und Vergleichen von Werten. Z. B., wenn Sie versuchen, suchen Sie für einen Datensatz mit den **suchen** -Methode, aber die Suche keine Datensätze zurückgibt, werden automatisch an einem Ende der **Recordset**. Wenn Ihr Anbieter unterstützt werden, können Lesezeichen, markieren Sie die Stelle vor dem Verwenden der **suchen** Methode, sodass Sie für Ihre Position zurückkehren können. Ein Lesezeichen ist ein **Variant** Typwert, die eindeutig einen Datensatz in einem **Recordset** Objekt.  
  
 Sie können auch ein variant-Array von Lesezeichen, mit der **Recordset-Filter** Methode, um für eine ausgewählte Gruppe von Datensätzen zu filtern. Ausführliche Informationen zu diesem Verfahren finden Sie unter Filtern der Ergebnisse im Thema [arbeiten mit Recordsets](../../../ado/guide/data/working-with-recordsets.md)weiter unten in diesem Abschnitt.  
  
 Können Sie die **Lesezeichen** Eigenschaft, um ein Lesezeichen für einen Datensatz abzurufen, oder legen Sie den aktuellen Datensatz in einer **Recordset** -Objekt, das durch ein gültiges Lesezeichen identifizierten Datensatz. Der folgende code verwendet die **Lesezeichen** -Eigenschaft zum Festlegen von Lesezeichen und klicken Sie dann mit dem Lesezeichen versehenen Datensatz nach dem Verschieben auf andere Datensätze zurückzugeben. Um festzustellen, ob Ihre **Recordset** unterstützt Lesezeichen, verwenden die **unterstützt** Methode.  
  
```  
'BeginBookmarkEg  
Dim varBookmark As Variant  
Dim blnCanBkmrk As Boolean  
  
objRs.Open strSQL, strConnStr, adOpenStatic, adLockOptimistic, adCmdText  
  
If objRs.RecordCount > 4 Then  
    objRs.Move 4                       ' move to the fifth record  
    blnCanBkmrk = objRs.Supports(adBookmark)  
    If blnCanBkmrk = True Then  
        varBookmark = objRs.Bookmark   ' record the bookmark  
        objRs.MoveLast                 ' move to a different record  
        objRs.Bookmark = varBookmark   ' return to the bookmarked (sixth) record  
    End If  
End If  
'EndBookmarkEg  
```  
  
 Die [unterstützt](../../../ado/reference/ado-api/supports-method.md) Methode wird später ausführlicher behandelt.  
  
 Mit Ausnahme der Groß-/Kleinschreibung geklonten **Recordsets**, Lesezeichen gelten nur für die **Recordset** in dem sie erstellt wurden, auch wenn Sie denselben Befehl verwendet wird. Dies bedeutet, dass Sie nicht verwenden können eine **Lesezeichen** abgerufen, die von einem **Recordset** verschieben auf den gleichen Datensatz in einer Sekunde **Recordset** mit dem gleichen Befehl geöffnet.
