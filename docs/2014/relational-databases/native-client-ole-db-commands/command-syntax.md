---
title: -Befehlssyntax | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, commands
- commands [OLE DB]
- SQL Server Native Client OLE DB provider, stored procedures
- stored procedures [OLE DB], command syntax
ms.assetid: d463d3d7-e5cb-426d-8e92-aa29980356b6
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4c8b0f5c1798d0547bf7a1acc6ef97c93660cd89
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37423489"
---
# <a name="command-syntax"></a>Befehlsyntax
  Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter erkennt vom Makro DBGUID_SQL angegebene Befehlssyntax. Für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter, dem Bezeichner gibt an, dass ein Zusammenschluss von ODBC SQL, ISO und [!INCLUDE[tsql](../../includes/tsql-md.md)] gültige Syntax. Die folgende SQL-Anweisung beispielsweise verwendet eine ODBC SQL-Escapesequenz, um die LCASE-Zeichenfolgenfunktion anzugeben:  
  
```  
SELECT customerid={fn LCASE(CustomerID)} FROM Customers  
```  
  
 LCASE gibt eine Zeichenfolge zurück und konvertiert alle Großbuchstaben in ihre kleingeschriebenen Entsprechungen. Die ISO-Zeichenfolgenfunktion LOWER führt denselben Vorgang durch, daher ist die folgende SQL-Anweisung eine ISO-Entsprechung der oben aufgeführten ODBC-Anweisung:  
  
```  
SELECT customerid=LOWER(CustomerID) FROM Customers  
```  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter verarbeitet beide Formen der Anweisung erfolgreich, wenn Sie als Text für einen Befehl angegeben.  
  
## <a name="stored-procedures"></a>Gespeicherte Prozeduren  
 Beim Ausführen einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gespeicherte Prozedur mit einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter Befehl können Sie die ODBC CALL-Escapesequenz im Befehlstext. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter verwendet dann den remoteprozeduraufrufsmechanismus von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] befehlsverarbeitung zu optimieren. Zum Beispiel ist die folgende ODBC SQL-Anweisung bevorzugter Befehlstext über das [!INCLUDE[tsql](../../includes/tsql-md.md)]-Formular:  
  
-   ODBC SQL  
  
    ```  
    {call SalesByCategory('Produce', '1995')}  
    ```  
  
-   Transact-SQL  
  
    ```  
    EXECUTE SalesByCategory 'Produce', '1995'  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Befehle](commands.md)  
  
  
