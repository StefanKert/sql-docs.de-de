---
title: "Ein- und Ausschalten eines Breakpoints | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c477ab89-a1cd-4f2c-aa7c-40525041100f
caps.latest.revision: 5
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 5
---
# Ein- und Ausschalten eines Breakpoints
  Das Festlegen eines Haltepunkts für eine [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung wird als Umschalten eines Haltepunkts bezeichnet.  
  
## Breakpoints  
 Sobald der Haltepunkt festgelegt wurde, wird er durch ein Symbol auf der grauen Leiste links von der Anweisung dargestellt. Das Symbol wird als Haltepunktsymbol bezeichnet. [!INCLUDE[tsql](../../includes/tsql-md.md)] -Haltepunkte werden auf eine vollständige [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung angewendet. Wenn ein Breakpoint eingeschaltet ist, hebt der Debugger die zugeordnete [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung hervor.  
  
 Wenn eine Zeile mehrere [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen enthält, können Sie für jede Anweisung einen Breakpoint umschalten. Wenn Sie auf die graue Leiste auf der linken Seite des Fensters klicken, wird ein Breakpoint für die erste Anweisung in der Zeile umgeschaltet. Sie können einen Breakpoint in einer nachfolgenden Anweisung umschalten, indem Sie einen beliebigen Teil der Anweisung markieren oder den Cursor in die Anweisung bewegen und dann F9 drücken. Oder klicken Sie im Menü **Debuggen** auf **Haltepunkt ein/aus** . Wenn eine Zeile mehrere Haltepunkte enthält, befindet sich links auf der grauen Leiste nur ein Haltepunktsymbol.  
  
 Nachdem ein Haltepunkt umgeschaltet wurde, können Sie verschiedene Aktionen für den Haltepunkt durchführen, z. B. seine Eigenschaften bearbeiten oder ihn vorübergehend deaktivieren. Weitere Informationen finden Sie weiter unten unter [Transact-SQL-Breakpoints](../../relational-databases/scripting/transact-sql-breakpoints.md).  
  
## Ein- und Ausschalten eines Breakpoints  
 **So schalten Sie einen Haltepunkt in einer Transact-SQL-Anweisung um**  
  
1.  Klicken Sie auf die graue Leiste auf der linken Seite der [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung.  
  
2.  Alternativ können Sie einen beliebigen Teil der Anweisung markieren oder den Cursor in die Anweisung bewegen, und dann eine der folgenden Aktionen ausführen:  
  
    -   Drücken Sie F9.  
  
    -   Klicken Sie im Menü **Debuggen** auf **Haltepunkt ein/aus**.  
  
  