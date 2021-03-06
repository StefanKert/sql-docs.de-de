---
title: DBSCHEMA_PROVIDER_TYPES-Rowset | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DBSCHEMA_PROVIDER_TYPES
topic_type:
- apiref
helpviewer_keywords:
- DBSCHEMA_PROVIDER_TYPES rowset
ms.assetid: 255e01ba-53a9-478d-9b86-45faba76710e
caps.latest.revision: 30
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7bca2527b77df65dede59878e91ef88ec5f933e0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37250950"
---
# <a name="dbschemaprovidertypes-rowset"></a>DBSCHEMA_PROVIDER_TYPES-Rowset
  Gibt die von dem Datenanbieter unterstützten (Basis-)Datentypen an.  
  
## <a name="rowset-columns"></a>Rowsetspalten  
 Die `DBSCHEMA_PROVIDER_TYPES` Rowset enthält die folgenden Spalten.  
  
|Spaltenname|Typindikator|Länge|Description|  
|-----------------|--------------------|------------|-----------------|  
|`TYPE_NAME`|`DBTYPE_WSTR`||Der anbieterspezifische Datentypname.|  
|`DATA_TYPE`|`DBTYPE_UI2`||Der Indikator des Datentyps.|  
|`COLUMN_SIZE`|`DBTYPE_UI4`||Die Länge einer nicht numerischen Spalte oder eines Parameters, der im Allgemeinen entweder die maximale oder die vom Anbieter definierte Länge für diesen Typ bezeichnet. Bei Zeichendaten ist dies die maximale Länge oder die definierte Länge, angegeben in Zeichen. Bei DateTime-Datentypen ist dies die Länge der Zeichenfolgendarstellung (wobei die maximal zulässige Genauigkeit der Komponente für Sekundenbruchteile vorausgesetzt wird).<br /><br /> Wenn der Datentyp numerisch ist, ist dies die obere Grenze der maximalen Genauigkeit des Datentyps.|  
|`LITERAL_PREFIX`|`DBTYPE_WSTR`||Das Zeichen oder die Zeichen, die in einem Textbefehl als Präfix für ein Literal von diesem Typ verwendet werden.|  
|`LITERAL_SUFFIX`|`DBTYPE_WSTR`||Das Zeichen oder die Zeichen, die in einem Textbefehl als Suffix für ein Literal von diesem Typ verwendet werden.|  
|`CREATE_PARAMS`|`DBTYPE_WSTR`||Die vom Consumer angegebenen Erstellungsparameter beim Erstellen einer Spalte dieses Datentyps. Der SQL-Datentyp `DECIMAL,` erfordert beispielsweise eine Genauigkeit und Dezimalstellen. In diesem Fall könnten die Erstellungsparameter die Zeichenfolge "precision,scale" sein. In einem Textbefehl zum Erstellen einer `DECIMAL` Spalte mit einer Genauigkeit von 10 und einer Dezimalstellenanzahl von 2 ist, den Wert des der `TYPE_NAME` Spalte `DECIMAL()` und die vollständige Typspezifikation wäre `DECIMAL(10,2)`.<br /><br /> Die Erstellungsparameter werden als eine Liste mit durch Trennzeichen getrennten Werten dargestellt, die in der Reihenfolge, in der sie bereitgestellt werden müssen, und ohne umgebende Klammern angegeben sind. Wenn Länge, maximale Länge, Genauigkeit, Dezimalstellen, Ausgangswert oder Inkrement ein Erstellungsparameter ist, verwenden Sie "length", "max length", "precision", "scale", "seed" bzw. "increment". Wenn der Erstellungsparameter ein anderer Wert ist, bestimmt der Anbieter den Text, der zur Beschreibung des Erstellungsparameters verwendet werden soll.<br /><br /> Wenn der Datentyp Erstellungsparameter erfordert, enthält der Typname normalerweise Klammern. Sie geben die Position an, bei der die Erstellungsparameter eingefügt werden müssen. Wenn der Typname keine Klammern enthält, werden die Erstellungsparameter in Klammern gesetzt und an den Datentypnamen angehängt.|  
|`IS_NULLABLE`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob für diesen Datentyp NULL zulässig ist.<br /><br /> `VARIANT_TRUE` gibt an, dass für diesen Datentyp NULL zulässig ist.<br /><br /> `VARIANT_FALSE` Gibt an, dass der Datentyp NULL nicht zulässig ist.<br /><br /> `NULL`– Gibt an, dass nicht bekannt, ob der Datentyp NULL zulässig ist.|  
|`CASE_SENSITIVE`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob der Datentyp ein Zeichentyp ist und die Groß-/Kleinschreibung beachtet.<br /><br /> `VARIANT_TRUE` Gibt an, dass der Datentyp ein Zeichentyp ist und Groß-/Kleinschreibung beachtet wird.<br /><br /> `VARIANT_FALSE` gibt an, dass der Datentyp kein Zeichentyp ist und die Groß-/Kleinschreibung nicht beachtet.|  
|`SEARCHABLE`|`DBTYPE_UI4`||Eine Ganzzahl, die angibt, wie der Datentyp für Suchen verwendet werden kann, wenn der Anbieter `ICommandText` unterstützt; andernfalls lautet der Wert `NULL`.<br /><br /> Diese Spalte kann die folgenden Werte enthalten:<br /><br /> -   `DB_UNSEARCHABLE` Gibt an, dass der Datentyp in verwendet werden, kann keinem `WHERE` Klausel.<br />-   `DB_LIKE_ONLY` Gibt an, dass der Datentyp kann, in verwendet werden einem `WHERE` -Klausel nur mit der `LIKE` Prädikat.<br />-   `DB_ALL_EXCEPT_LIKE` Gibt an, dass der Datentyp kann, in verwendet werden einem `WHERE` -Klausel mit allen Vergleichsoperatoren mit Ausnahme `LIKE`.<br />-   `DB_SEARCHABLE` Gibt an, dass der Datentyp kann, in verwendet werden einem `WHERE` -Klausel mit jedem Vergleichsoperator.|  
|`UNSIGNED_ATTRIBUTE`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob dieser Datentyp ein Vorzeichen aufweist oder nicht.<br /><br /> `VARIANT_TRUE` gibt an, dass der Datentyp kein Vorzeichen aufweist.<br /><br /> `VARIANT_FALSE` Gibt an, dass der Datentyp ein Vorzeichen aufweist.<br /><br /> `NULL` Gibt an, dass dies nicht für den Datentyp zutreffend ist.|  
|`FIXED_PREC_SCALE`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob der Datentyp über eine feste Genauigkeit und Dezimalstellen verfügt.<br /><br /> `VARIANT_TRUE` Gibt an, dass der Datentyp eine feste Genauigkeit und Dezimalstellen verfügt.<br /><br /> `VARIANT_FALSE` Gibt an, dass der Datentyp nicht über eine feste Genauigkeit und Dezimalstellen verfügt.|  
|`AUTO_UNIQUE_VALUE`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob dieser Datentyp eine automatische Inkrementierung aufweist oder nicht.<br /><br /> `VARIANT_TRUE` gibt an, dass Werte dieses Typs automatisch inkrementieren können.<br /><br /> `VARIANT_FALSE` Gibt an, dass Werte dieses Typs automatisch inkrementiert werden können.<br /><br /> Wenn dieser Wert ist `VARIANT_TRUE`, ob eine Spalte dieses Typs stets ist automatische Inkrementierung hängt des Anbieters `DBPROP_COL_AUTOINCREMENT` Column-Eigenschaft. Wenn die `DBPROP_COL_AUTOINCREMENT` Eigenschaft ist Lese-/Schreibzugriff, und zwar unabhängig davon, ob eine Spalte dieses Typs wird nicht automatisch inkrementieren hängt von der Einstellung der `DBPROP_COL_AUTOINCREMENT` Eigenschaft. Wenn `DBPROP_COL_AUTOINCREMENT` ist eine schreibgeschützte Eigenschaft, werden Sie entweder alle oder keine der Spalten dieses Typs automatisch inkrementiert.|  
|`LOCAL_TYPE_NAME`|`DBTYPE_WSTR`||Die lokalisierte Version der `TYPE_NAME`. Wenn ein lokalisierter Name vom Datenbieter nicht unterstützt wird, wird `NULL` zurückgegeben.|  
|`MINIMUM_SCALE`|`DBTYPE_I2`||Wenn der Typindikator `DBTYPE_VARNUMERIC`, `DBTYPE_DECIMAL`, oder `DBTYPE_NUMERIC`, die minimale Anzahl von Ziffern rechts vom Dezimaltrennzeichen an. Andernfalls `NULL`.|  
|`MAXIMUM_SCALE`|`DBTYPE_I2`||Die maximale Anzahl von Stellen rechts neben dem Dezimalzeichen, wenn der Typindikator `DBTYPE_VARNUMERIC`, `DBTYPE_DECIMAL`, oder `DBTYPE_NUMERIC`; andernfalls N`U`LL.|  
|`GUID`|`DBTYPE_GUID`||(Für zukünftige Verwendung vorgesehen) Die `GUID` des Typs, wenn der Typ in einer Typbibliothek beschrieben ist. Andernfalls `NULL`.|  
|`TYPELIB`|`DBTYPE_WSTR`||(Für zukünftige Verwendung vorgesehen) Die Typbibliothek, die die Beschreibung des Typs enthält, wenn der Typ in einer Typbibliothek beschrieben ist. Andernfalls wird NULL verwendet.|  
|`VERSION`|`DBTYPE_WSTR`||(Für zukünftige Verwendung vorgesehen) Die Version der Typdefinition. Manche Anbieter verwenden möglicherweise Versionstypdefinitionen. Andere Anbieter verwenden möglicherweise andere Versionsschemas, z. B. einen Zeitstempel oder eine Zahl (integer oder float). `NULL` Wenn nicht unterstützt.|  
|`IS_LONG`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob der Datentyp ein BLOB (Binary Large Object) darstellt und sehr lange Daten aufweist.<br /><br /> `VARIANT_TRUE` gibt an, dass der Datentyp ein `BLOB` ist, das sehr lange Daten enthält; die Definition von "sehr lange Daten" ist anbieterspezifisch.<br /><br /> `VARIANT_FALSE` Gibt an, dass der Datentyp ist ein `BLOB` , die keine sehr lange Daten enthält, oder ist keiner `BLOB`.<br /><br /> Dieser Wert bestimmt die Einstellung der `DBCOLUMNFLAGS_ISLONG` Flag zurückgegebenes `GetColumnInfo` in `IColumnsInfo` und `GetParameterInfo` in `ICommandWithParameters`.|  
|`BEST_MATCH`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob dieser Datentyp eine größte Übereinstimmung darstellt oder nicht.<br /><br /> `VARIANT_TRUE` Gibt an, dass der Datentyp die beste Übereinstimmung zwischen allen Datentypen im Datenspeicher und der OLE DB-Datentyp angegeben werden, durch den Wert in der `DATA_TYPE` Spalte.<br /><br /> `VARIANT_FALSE` gibt an, dass der Datentyp nicht die beste Übereinstimmung darstellt.<br /><br /> Für jede Gruppe von Zeilen, in denen der Wert der `DATA_TYPE`-Spalte gleich ist, wird die `BEST_MATCH`-Spalte in nur einer Zeile auf `VARIANT_TRUE` festgelegt.|  
|`IS_FIXEDLENGTH`|`DBTYPE_BOOL`||Ein boolescher Wert, der angibt, ob die Spalte eine feste Länge hat.<br /><br /> `VARIANT_TRUE` gibt an, dass Spalten dieses Typs, die durch die Datendefinitionssprache (DDL) erstellt werden, eine feste Länge haben.<br /><br /> `VARIANT_FALSE` gibt an, dass Spalten dieses Typs, die durch die Datendefinitionssprache (DDL) erstellt werden, eine variable Länge haben.<br /><br /> Wenn das Feld den Wert `NULL` enthält, ist nicht bekannt, ob der Anbieter dieses Feld einer Spalte mit fester oder variabler Länge zuordnet.|  
  
 Das Rowset wird sortiert nach `DATA_TYPE`.  
  
## <a name="restriction-columns"></a>Einschränkungsspalten  
 Die `DBSCHEMA_PROVIDER_TYPES` Rowset kann auf die in der folgenden Tabelle aufgeführten Spalten eingeschränkt werden.  
  
|Spaltenname|Typindikator|Einschränkungsstatus|  
|-----------------|--------------------|-----------------------|  
|`DATA_TYPE`|`DBTYPE_UI2`||  
|`BEST_MATCH`|`DBTYPE_BOOL`||  
  
## <a name="see-also"></a>Siehe auch  
 [OLE DB-Schemarowsets](ole-db-schema-rowsets.md)  
  
  
