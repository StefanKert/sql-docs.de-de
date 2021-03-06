---
title: Datentypunterstützung für ODBC-Datum und Uhrzeit-Verbesserungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- date/time [ODBC], data type support
- ODBC, date/time improvements
ms.assetid: 8e0d9ba2-3ec1-4680-86e3-b2590ba8e2e9
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c255e46c3aab112f6b2db92f364b95c23743e6fc
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43062401"
---
# <a name="data-type-support-for-odbc-date-and-time-improvements"></a>Datentypunterstützung für ODBC-Verbesserungen bei Datum und Uhrzeit
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Dieses Thema liefert Informationen über ODBC-Typen, die die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen date und time unterstützen.  
  
## <a name="data-type-mapping-in-parameters-and-resultsets"></a>Datentypzuordnung in Parametern und Resultsets  
 Neben den ODBC-Datentypen (SQL_TYPE_TIMESTAMP und SQL_TIMESTAMP) wurden in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC zwei neue Datentypen hinzugefügt, um die neuen Servertypen verfügbar zu machen:  
  
-   SQL_SS_TIME2  
  
-   SQL_SS_TIMESTAMPOFFSET  
  
 Die folgende Tabelle zeigt die vollständige Servertypzuordnung. Beachten Sie, dass einige Zellen der Tabelle zwei Einträge enthalten. In diesen Fällen ist der erste der ODBC 3.0-Wert und der zweite der ODBC 2.0-Wert.  
  
|SQL Server-Datentyp|SQL-Datentyp|value|  
|--------------------------|-------------------|-----------|  
|DATETIME|SQL_TYPE_TIMESTAMP<br /><br /> SQL_TIMESTAMP|93 (sql.h)<br /><br /> 11 (sqlext.h)|  
|Smalldatetime|SQL_TYPE_TIMESTAMP<br /><br /> SQL_TIMESTAMP|93 (sql.h)<br /><br /> 11 (sqlext.h)|  
|date|SQL_TYPE_DATE<br /><br /> SQL_DATE|91 (sql.h)<br /><br /> 9 (sqlext.h)|  
|Uhrzeit|SQL_SS_TIME2|-154 (SQLNCLI.h)|  
|DatetimeOFFSET|SQL_SS_TIMESTAMPOFFSET|-155 (sqlncli.h)|  
|Datetime2|SQL_TYPE_TIMESTAMP<br /><br /> SQL_TIMESTAMP|93 (sql.h)<br /><br /> 11 (sqlext.h)|  
  
 In der folgenden Tabelle sind die entsprechenden Strukturen und ODBC C-Typen aufgeführt. Da ODBC keine treiberdefinierten C-Typen zulässt, wird SQL_C_BINARY als Binärstrukturen für time und datetimeoffset verwendet.  
  
|SQL-Datentyp|Speicherlayout|Standardmäßiger C-Datentyp|Wert (sqlext.h)|  
|-------------------|-------------------|-------------------------|------------------------|  
|SQL_TYPE_TIMESTAMP<br /><br /> SQL_TIMESTAMP|SQL_TIMESTAMP_STRUCT<br /><br /> TIMESTAMP_STRUCT|SQL_C_TYPE_TIMESTAMP<br /><br /> SQL_C_TIMESTAMP|SQL_TYPE_TIMESTAMP<br /><br /> SQL_TIMESTAMP|  
|SQL_TYPE_DATE<br /><br /> SQL_DATE|SQL_DATE_STRUCT<br /><br /> DATE_STRUCT|SQL_C_TYPE_DATE<br /><br /> SQL_C_DATE|SQL_TYPE_DATE<br /><br /> SQL_DATE|  
|SQL_SS_TIME2|SQL_SS_TIME2_STRUCT|SQL_C_SS_TIME2<br /><br /> SQL_C_BINARY (ODBC 3.5 und früher)|0x4000 (sqlncli.h)<br /><br /> SQL_BINARY (-2)|  
|SQL_SS_TIMESTAMPOFFSET|SQL_SS_TIMESTAMPOFFSET_STRUCT|SQL_C_SS_TIMESTAMPOFFSET<br /><br /> SQL_C_BINARY (ODBC 3.5 und früher)|0x4001 (sqlncli.h)<br /><br /> SQL_BINARY (-2)|  
  
 Wenn die SQL_C_BINARY-Bindung angegeben wird, wird die Ausrichtungsüberprüfung ausgeführt und ein eventueller Fehler berichtet. Der SQLSTATE für diesen Fehler ist IM016, mit der Meldung "Falsche Strukturausrichtung".  
  
## <a name="data-formats-strings-and-literals"></a>Datenformate: Zeichenfolgen und Literale  
 Die folgende Tabelle stellt die Zuordnungen zwischen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen, ODBC-Datentypen und ODBC-Zeichenfolgenliteralen dar.  
  
|SQL Server-Datentyp|ODBC-Datentyp|Zeichenfolgenformat für Clientkonvertierungen|  
|--------------------------|--------------------|------------------------------------------|  
|DATETIME|SQL_TYPE_TIMESTAMP<br /><br /> SQL_TIMESTAMP|'yyyy-mm-dd hh:mm:ss[.999]'<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt bis zu drei Sekundenbruchteilziffern für Datetime.|  
|Smalldatetime|SQL_TYPE_TIMESTAMP<br /><br /> SQL_TIMESTAMP|'yyyy-mm-dd hh:hh:ss'<br /><br /> Dieser Datentyp verfügt über eine Genauigkeit von einer Minute. Die zweite Komponente ist 0 (null) auf Ausgabe und wird auf Eingabe vom Server gerundet.|  
|date|SQL_TYPE_DATE<br /><br /> SQL_DATE|'yyyy-mm-dd'|  
|Uhrzeit|SQL_SS_TIME2|'hh:mm:ss[.9999999]'<br /><br /> Sekundenbruchteile können optional mit bis zu sieben Ziffern angegeben werden.|  
|Datetime2|SQL_TYPE_TIMESTAMP<br /><br /> SQL_TIMESTAMP|'Yyyy-mm-Dd hh: mm: [.9999999]'<br /><br /> Sekundenbruchteile können optional mit bis zu sieben Ziffern angegeben werden.|  
|DatetimeOFFSET|SQL_SS_TIMESTAMPOFFSET|'yyyy-mm-dd hh:mm:ss[.9999999] +/- hh:mm'<br /><br /> Sekundenbruchteile können optional mit bis zu sieben Ziffern angegeben werden.|  
  
 Für date/time-Literale gibt es keine Änderungen der ODBC-Escapesequenzen.  
  
 Sekundenbruchteile in Ergebnissen immer verwenden Sie einen Punkt (.), und keinen Doppelpunkt (:).  
  
 Für Anwendungen zurückgegebene Zeichenfolgenwerte sind immer die gleiche Länge für eine bestimmte Spalte. Die Komponenten Jahr, Monat, Tag, Stunde, Minute und Sekunde werden mit führenden Nullen bis zur maximalen Breite aufgefüllt. Zudem befindet sich zwischen Datum und Uhrzeit in datetime-Werten ein Leerzeichen. Auch zwischen dem Uhrzeit- und Zeitzonenoffset in einem datetimeoffset-Wert steht ein Leerzeichen. Einem Zeitzonenoffset wird immer ein Zeichen vorangestellt. Wenn der Offset 0 (null) ist, ist das Zeichen ein Plus (+). Sekundenbruchteile werden bei Bedarf bis zur definierten Genauigkeit für die Spalte mit nachfolgenden Nullen aufgefüllt. Für datetime-Spalten gibt es drei Ziffern für Sekundenbruchteile. Für smalldatetime-Spalten gibt es keine Ziffern für Sekundenbruchteile, und die Sekunden sind immer 0 (null).  
  
 Eine leere Zeichenfolge ist kein gültiges Datum-/Uhrzeitliteral und stellt keinen NULL-Wert dar. Der Versuch, eine leere Zeichenfolge in einen date/time-Wert zu konvertieren, führt zum Fehler SQLSTATE 22018 und der Meldung "Ungültiger Zeichenwert für Konvertierungsangabe".  
  
 Konvertierungen aus Zeichenfolgenparametern setzen Zeichenfolgen im selben Format voraus. Ausnahmen: Das Zeichen einer Zeitzone mit 0 (null) Stunden und 0 (null) Minuten kann entweder Plus oder Minus sein, und nachfolgende Nullen sind für Sekundenbruchteile bis zu maximal 9 Ziffern zulässig. Eine Zeitkomponente kann mit einem Dezimaltrennzeichen und keinen Ziffern für Sekundenbruchteile enden.  
  
 Aktuell lässt der Treiber zusätzliche Leerzeichen um Satzzeichen zu, und das Leerzeichen zwischen dem Uhrzeit- und dem Zeitzonenoffset ist optional. Aber dies könnte sich in einer zukünftigen Version ändern; Anwendungen sollten das aktuelle Verhalten nicht bedingen.  
  
## <a name="data-formats-data-structures"></a>Datenformate: Datenstrukturen  
 In den nachfolgend beschriebenen Strukturen gibt ODBC die folgenden Einschränkungen an, die auf den gregorianischen Kalender zurückgehen:  
  
-   Der Bereich für den Monat liegt zwischen 1 und 12.  
  
-   Der Bereich für das Tagfeld liegt zwischen 1 und der Anzahl Tage in dem Monat und muss mit den Feldern für Jahr und Monat konsistent sein unter Berücksichtigung von Schaltjahren.  
  
-   Der Bereich für die Stunden liegt zwischen 0 und 23.  
  
-   Der Bereich für die Minuten liegt zwischen 0 und 59.  
  
-   Der Sekundenbereich reicht von 0 bis 61.9(n). Es sind bis zu zwei Schaltsekunden erlaubt, um die Synchronisierung mit der Sideralzeit zu gewährleisten.  
  
     Beachten Sie, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] keine Schaltsekunden zulässt. Sekundenwerte über 59 führen zu einem Serverfehler.  
  
 Implementierungen für die folgenden bestehenden ODBC-Strukturen wurden geändert, um die Unterstützung der neuen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen date und date sicherzustellen. Die Definitionen haben sich jedoch nicht geändert.  
  
-   DATE_STRUCT  
  
-   TIME_STRUCT  
  
-   TIMESTAMP_STRUCT  
  
 Es gibt zudem zwei neue Strukturen:  
  
-   SQL_SS_TIME2_STRUCT  
  
-   SQL_SS_TIMESTAMPOFFSET_STRUCT  
  
### <a name="sqlsstime2struct"></a>SQL_SS_TIME2_STRUCT  
 Diese Struktur wird auf beiden Betriebssystemen (32 Bit und 64 Bit) bis 12 Byte aufgefüllt.  
  
```  
typedef struct tagSS_TIME2_STRUCT {  
   SQLUSMALLINT hour;  
   SQLUSMALLINT minute;  
   SQLUSMALLINT second;  
   SQLUINTEGER fraction;  
} SQL_SS_TIME2_STRUCT;  
```  
  
### <a name="sqlsstimestampoffsetstruct"></a>SQL_SS_TIMESTAMPOFFSET_STRUCT  
  
```  
typedef struct tagSS_TIMESTAMPOFFSET_STRUCT {  
   SQLSMALLINT year;  
   SQLUSMALLINT month;  
   SQLUSMALLINT day;  
   SQLUSMALLINT hour;  
   SQLUSMALLINT minute;  
   SQLUSMALLINT second;  
   SQLUINTEGER fraction;  
   SQLSMALLINT timezone_hour;  
   SQLSMALLINT timezone_minute;  
} SQL_SS_TIMESTAMPOFFSET_STRUCT;  
```  
  
 Wenn die **Timezone_hour** negativ ist, die **Timezone_minute** darf negativ sein oder 0 (null). Wenn die **Timezone_hour** positiv ist, werden die **Timezone_minute** muss positiv sein oder 0 (null). Wenn die **Timezone_hour** ist 0 (null), s**Timezone_minute** möglicherweise einen beliebigen Wert im Bereich von-59 bis + 59 annehmen.  
  
## <a name="see-also"></a>Siehe auch  
 [Datums- / Uhrzeitverbesserungen &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
  
