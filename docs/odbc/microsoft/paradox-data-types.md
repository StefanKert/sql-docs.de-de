---
title: Datentypen Paradox | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], Paradox driver
- desktop database drivers [ODBC], Paradox driver
- Paradox data types [ODBC]
- Jet-based ODBC drivers [ODBC], Paradox driver
- data types [ODBC], Paradox driver
- Paradox driver [ODBC], data types
ms.assetid: 0c9e5d21-9321-49f8-a055-69459e1c9c85
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9099d9a84fb79132249c74d1d24cc240bcf8aae0
ms.contentlocale: de-de
ms.lasthandoff: 09/09/2017

---
# <a name="paradox-data-types"></a>Paradox-Datentypen
Der Paradox ODBC-Treiber ordnet Paradox-Datentypen in ODBC-SQL-Datentypen. Die folgende Tabelle listet alle Paradox-Datentypen und zeigt der ODBC-SQL-Datentypen, denen sie zugeordnet sind.  
  
|Paradox-Datentyp|ODBC-Datentyp|  
|-----------------------|--------------------|  
|ALPHANUMERISCH|SQL_VARCHAR|  
|AUTOINCREMENT [1]|SQL_INTEGER|  
|BCD [1]|SQL_DOUBLE|  
|BYTES [1]|SQL_BINARY|  
|DATE|SQL_DATE|  
|BILD VON [2]|SQL_LONGVARBINARY|  
|LOGISCHE [1]|SQL_BIT|  
|LONG-WERT [1]|SQL_INTEGER|  
|MEMO [2]|SQL_LONGVARCHAR|  
|MONEY [1]|SQL_DOUBLE|  
|NUMBER|SQL_DOUBLE|  
|KURZE|SQL_SMALLINT|  
|ZEIT [1]|SQL_TIMESTAMP|  
|ZEITSTEMPEL [1]|SQL_TIMESTAMP|  
  
 [1] gültig nur für Paradox, Versionen 5. *x*.  
  
 [2] gültig nur für Paradox Versionen 4. *x* und 5.* X*.  
  
> [!NOTE]  
>  **SQLGetTypeInfo** gibt ODBC SQL-Datentypen. Alle Konvertierungen in Anhang D der *ODBC Programmer's Reference* werden für die ODBC-SQL-Datentypen, die weiter oben in diesem Thema aufgeführten unterstützt.  
  
 Die folgende Tabelle zeigt die Einschränkungen für Datentypen Paradox.  
  
|Datentyp|Description|  
|---------------|-----------------|  
|ALPHANUMERISCH|Erstellen eine ALPHANUMERISCHE Spalte 0 (null) oder nicht angegebene Länge gibt tatsächlich eine 255 Byte-Spalte.|  
|BYTES|Wenn Sie NULL in eine binäre Spalte mit dem Treiber Paradox5 einfügen, wird es in 0 geändert.|  
|LONG|Der größte negative Wert vom Treiber Paradox für Long-Datentyp in Paradox 5 unterstützt. *x* ist kein-2 ^ 31 (-2147483648), da er seit lange Zuordnungen in die ODBC-sein sollten, geben Sie SQL_INTEGER. Der Maximalwert der negativen unterstützt, solange ist tatsächlich-2 ^ 31-1 (-2147483647).|  
|timestamp|Wenn ein Wert in eine TIMESTAMP-Spalte werden, vom Treiber Paradox eingefügt, und dann anschließend aus der Spalte abgerufen, abweichen der abgerufene Wert aus der eingefügte Wert durch mehr als 1 Sekunde aufgrund Rundung.|  
  
 Weitere Einschränkungen für Datentypen finden Sie in [Datentyp Einschränkungen](../../odbc/microsoft/data-type-limitations.md).