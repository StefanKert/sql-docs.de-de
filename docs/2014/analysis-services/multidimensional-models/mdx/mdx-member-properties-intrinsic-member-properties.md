---
title: Integrierte Elementeigenschaften (MDX) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- intrinsic member properties [MDX]
ms.assetid: 84e6fe64-9b37-4e79-bedf-ae02e80bfce8
caps.latest.revision: 41
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9cbfcb8926d8d4b1ae71c5a3b6ed35c3beb7796c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37236030"
---
# <a name="intrinsic-member-properties-mdx"></a>Integrierte Elementeigenschaften (MDX)
  [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] macht systeminterne Eigenschaften für Dimensionselemente verfügbar, die Sie in eine Abfrage einschließen können, um zusätzliche Daten oder Metadaten für eine benutzerdefinierte Anwendung zurückzugeben, oder um die Überprüfung oder Erstellung des Modells zu unterstützen. Wenn Sie die SQL Server-Clienttools verwenden, können Sie die systeminternen Eigenschaften in SQL Server Management Studio (SSMS) anzeigen lassen.  
  
 Systeminterne Eigenschaften sind `ID`, `KEY`, `KEYx` und `NAME` und werden von jedem Element auf beliebigen Ebenen verfügbar gemacht. Sie können auch mit Feldern fester Breite Informationen zurückgeben, z. B. `LEVEL_NUMBER` oder `PARENT_UNIQUE_NAME`, u. a.  
  
 Abhängig davon, wie Sie die Abfrage erstellen und mit welcher Clientanwendung Sie Abfragen auszuführen, sind die Elementeigenschaften im Resultset sichtbar bzw. nicht sichtbar. Wenn Sie SQL Server Management Studio verwenden, um Abfragen zu testen oder auszuführen, können Sie auf ein Element im Resultset doppelklicken, um das Dialogfeld Elementeigenschaften zu öffnen, in dem Werte für jede systeminterne Elementeigenschaft angezeigt werden.  
  
 Eine Einführung dazu, wie Sie Dimensionselementeigenschaften verwenden und anzeigen, finden Sie unter [Anzeigen von SSAS-Elementeigenschaften innerhalb eines MDX-Abfragefensters in SSMS](http://go.microsoft.com/fwlink/?LinkId=317362).  
  
> [!NOTE]  
>  Als Anbieter, der Kompatibilität mit dem OLAP-Abschnitt der OLE DB-Spezifikation vom März 1999 (2.6) gewährleistet, unterstützt [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] die systeminternen Elementeigenschaften, die in diesem Thema aufgeführt sind.  
>   
>  Andere Anbieter als [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] unterstützen möglicherweise weitere systeminterne Elementeigenschaften. Weitere Informationen zu den systeminternen Elementeigenschaften, die von anderen Anbietern unterstützt werden, finden Sie in der Dokumentation des jeweiligen Anbieters.  
  
## <a name="types-of-member-properties"></a>Arten von Elementeigenschaften  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] unterstützt zwei Arten von systeminternen Elementeigenschaften:  
  
 Kontextabhängige Elementeigenschaften  
 Diese Elementeigenschaften müssen im Kontext einer bestimmten Hierarchie oder Ebene verwendet werden und stellen Werte für jedes Element der angegebenen Dimension oder Ebene bereit.  
  
 Im folgenden Beispiel sehen Sie, wie der Pfad für die `KEY`-Eigenschaft eingefügt wird: `MEMBER [Measures].[Parent Member Key] AS [Product].[Product Categories].CurrentMember.Parent.PROPERTIES("KEY")`.  
  
 Nicht kontextabhängige Elementeigenschaften  
 Diese Elementeigenschaften können nicht im Kontext einer bestimmten Dimension oder Ebene verwendet werden und geben Werte für alle Elemente auf einer Achse zurück.  
  
 Nicht kontextabhängige Eigenschaften sind eigenständig und enthalten keine Pfadinformationen. Beachten Sie, wie es ist keine Dimension oder Ebene, die für die angegebene `PARENT_UNIQUE_NAME` im folgenden Beispiel: `DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS`  
  
 Für die Verwendung einer systeminternen Elementeigenschaft gelten unabhängig davon, ob sie kontextabhängig ist oder nicht, folgende Regeln:  
  
-   Sie können nur solche systeminternen Elementeigenschaften angeben, die sich auf Dimensionselemente beziehen, die auf die Achse projiziert werden.  
  
-   Sie können Anforderungen für kontextabhängige Elementeigenschaften in derselben Abfrage mit nicht kontextabhängigen systeminternen Elementeigenschaften mischen.  
  
-   Zum Abfragen der Eigenschaften verwenden Sie das `PROPERTIES`-Schlüsselwort.  
  
 Die folgenden Abschnitte beschreiben sowohl die verschiedenen kontextabhängigen und nicht kontextabhängigen systeminternen Elementeigenschaften in verfügbar [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], und wie Sie mit der `PROPERTIES` -Schlüsselwort mit jeder Art von Eigenschaft.  
  
## <a name="context-sensitive-member-properties"></a>Kontextabhängige Elementeigenschaften  
 Alle Dimensionselemente und Ebenenelemente unterstützen eine Reihe von systeminternen Elementeigenschaften, die kontextabhängig sind. In der folgenden Tabelle sind diese kontextabhängigen Eigenschaften aufgelistet.  
  
|Eigenschaft|Description|  
|--------------|-----------------|  
|`ID`|Die intern verwaltete ID für das Element.|  
|`Key`|Der Wert des Elementschlüssels im ursprünglichen Datentyp. MEMBER_KEY wird für Abwärtskompatibilität verwendet.  MEMBER_KEY hat für nicht zusammengesetzte Schlüssel denselben Wert wie KEY0, und die MEMBER_KEY-Eigenschaft ist für zusammengesetzte Schlüssel NULL.|  
|`KEYx`|Der Schlüssel des Elements, wobei x die nullbasierte Ordnungszahl des Schlüssels ist. KEY0 ist für zusammengesetzte und nicht zusammengesetzte Schlüssel verfügbar, wird jedoch hauptsächlich für zusammengesetzte Schlüssel verwendet.<br /><br /> Bei diesem Schlüsseltyp bilden KEY0, KEY1, KEY2 usw. gemeinsam den zusammengesetzten Schlüssel. Die einzelnen Schlüssel können in einer Abfrage unabhängig voneinander verwendet werden, um den betreffenden Teil des zusammengesetzten Schlüssels zurückzugeben. Beispielsweise wird durch Angabe von KEY0 der erste Teil des zusammengesetzten Schlüssels zurückgegeben und durch Angabe von KEY1 der nächste Teil usw.<br /><br /> Wenn der Schlüssel nicht zusammengesetzt, dann KEY0 gleich ist `Key`.<br /><br /> Beachten Sie, dass `KEYx` im Kontext sowie ohne Kontext verwendet werden kann. Aus diesem Grund wird der Schlüssel in beiden Listen angezeigt.<br /><br /> Ein Beispiel zur Verwendung dieser Elementeigenschaft finden Sie unter [Ein einfacher MDX-Trick: Key0, Key1, Key2](http://go.microsoft.com/fwlink/?LinkId=317364).|  
|`Name`|Der Name des Elements.|  
  
### <a name="properties-syntax-for-context-sensitive-properties"></a>PROPERTIES-Syntax für kontextabhängige Eigenschaften  
 Sie verwenden diese Elementeigenschaften im Kontext einer bestimmten Dimension oder Ebene und stellen Werte für jedes Element der angegebenen Dimension oder Ebene bereit.  
  
 Bei einer Eigenschaft eines Dimensionselements setzen Sie vor den Namen der Eigenschaft den Namen der Dimension, für die die Eigenschaft gilt. Das folgende Beispiel zeigt die entsprechende Syntax:  
  
 `DIMENSION PROPERTIES Dimension.Property_name`  
  
 Bei einer Eigenschaft eines Ebenenelements genügt es, wenn Sie vor den Namen der Eigenschaft den Namen der Ebene setzen. Zur zusätzlichen Spezifikation können Sie dort aber auch den Dimensions- und den Ebenennamen angeben. Das folgende Beispiel zeigt die entsprechende Syntax:  
  
 `DIMENSION PROPERTIES [Dimension.]Level.Property_name`  
  
 Um dies zu verdeutlichen, sollen alle Namen jedes Elements der `[Sales]` -Dimension zurückgegeben werden, auf das verwiesen wird. Zum Zurückgeben dieser Namen verwenden Sie folgende Anweisung in einer MDX-Abfrage (Multidimensional Expressions):  
  
 `DIMENSION PROPERTIES [Sales].Name`  
  
## <a name="non-context-sensitive-member-properties"></a>Nicht kontextabhängige Elementeigenschaften  
 Alle Elemente unterstützen eine Reihe von systeminternen Elementeigenschaften, die unabhängig vom Kontext gleich sind. Diese Eigenschaften stellen zusätzliche Informationen bereit, die in Anwendungen dazu verwendet werden können, die Benutzerfreundlichkeit zu verbessern.  
  
 In der folgenden Tabelle sind die nicht kontextabhängigen systeminternen Eigenschaften aufgelistet, die von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]unterstützt werden.  
  
> [!NOTE]  
>  Die Spalten im MEMBERS-Schemarowset unterstützen die systeminternen Elementeigenschaften, die in der folgenden Tabelle aufgelistet sind. Weitere Informationen zu den `MEMBERS` -Schemarowset finden Sie unter [MDSCHEMA_MEMBERS-Rowset](../../schema-rowsets/ole-db-olap/mdschema-members-rowset.md).  
  
|Eigenschaft|Description|  
|--------------|-----------------|  
|`CATALOG_NAME`|Der Name des Cubes, zu dem dieses Element gehört.|  
|`CHILDREN_CARDINALITY`|Die Anzahl der untergeordneten Elemente des Elements. Dies kann eine Schätzung sein, daher sollten Sie sich nicht darauf verlassen, dass es sich um die exakte Anzahl handelt. Anbieter sollten die bestmögliche Schätzung zurückgeben.|  
|`CUSTOM_ROLLUP`|Der benutzerdefinierte Elementausdruck.|  
|`CUSTOM_ROLLUP_PROPERTIES`|Die benutzerdefinierten Elementeigenschaften.|  
|`DESCRIPTION`|Eine lesbare Beschreibung des Elements.|  
|`DIMENSION_UNIQUE_NAME`|Der eindeutige Name der Dimension, zu der dieses Element gehört. Für Anbieter, die eindeutige Namen durch eine Einschränkung generieren, ist jede Komponente dieses Namens begrenzt.|  
|`HIERARCHY_UNIQUE_NAME`|Der eindeutige Name der Hierarchie. Wenn das Element zu mehreren Hierarchien gehört, gibt es eine Zeile für jede Hierarchie, zu der das Element gehört. Für Anbieter, die eindeutige Namen durch eine Einschränkung generieren, ist jede Komponente dieses Namens begrenzt.|  
|`IS_DATAMEMBER`|Ein boolescher Wert, der angibt, ob das Element ein Datenelement ist.|  
|`IS_PLACEHOLDERMEMBER`|Ein boolescher Wert, der angibt, ob das Element ein Platzhalter ist.|  
|`KEYx`|Der Schlüssel des Elements, wobei x die nullbasierte Ordnungszahl des Schlüssels ist. KEY0 ist für zusammengesetzte und nicht zusammengesetzte Schlüssel verfügbar.<br /><br /> Wenn der Schlüssel nicht zusammengesetzt, dann KEY0 gleich ist `Key`.<br /><br /> Bei diesem Schlüsseltyp bilden KEY0, KEY1, KEY2 usw. gemeinsam den zusammengesetzten Schlüssel. Sie können auf jeden einzelnen Schlüssel in einer Abfrage verweisen, um diesen Teil des zusammengesetzten Schlüssels zurückzugeben. Beispielsweise wird durch Angabe von KEY0 der erste Teil des zusammengesetzten Schlüssels zurückgegeben und durch Angabe von KEY1 der nächste Teil usw.<br /><br /> Beachten Sie, dass `KEYx` im Kontext sowie ohne Kontext verwendet werden kann. Aus diesem Grund wird der Schlüssel in beiden Listen angezeigt.<br /><br /> Ein Beispiel zur Verwendung dieser Elementeigenschaft finden Sie unter [Ein einfacher MDX-Trick: Key0, Key1, Key2](http://go.microsoft.com/fwlink/?LinkId=317364).|  
|`LCID` *x*|Die Übersetzung der Elementbeschriftung in den hexadezimalen Wert der Gebietsschema-ID, wobei *x* der dezimale Wert der Gebietsschema-ID ist (z.B. LCID1009 als Englisch-Kanada). Dies ist nur verfügbar, wenn die Beschriftungsspalte der Übersetzung an die Datenquelle gebunden ist.|  
|`LEVEL_NUMBER`|Der Abstand des Elements vom Stamm der Hierarchie. Die Stammebene entspricht null.|  
|`LEVEL_UNIQUE_NAME`|Der eindeutige Name der Ebene, zu der das Element gehört. Für Anbieter, die eindeutige Namen durch eine Einschränkung generieren, ist jede Komponente dieses Namens begrenzt.|  
|`MEMBER_CAPTION`|Eine Bezeichnung oder Beschriftung, die dem Element zugeordnet ist. Die Beschriftung dient hauptsächlich zu Anzeigezwecken. Ist keine Beschriftung vorhanden, gibt die Abfrage den Wert von `MEMBER_NAME` zurück.|  
|`MEMBER_KEY`|Der Wert des Elementschlüssels im ursprünglichen Datentyp. MEMBER_KEY wird für Abwärtskompatibilität verwendet.  MEMBER_KEY hat für nicht zusammengesetzte Schlüssel denselben Wert wie KEY0, und die MEMBER_KEY-Eigenschaft ist für zusammengesetzte Schlüssel NULL.|  
|`MEMBER_NAME`|Der Name des Elements.|  
|`MEMBER_TYPE`|Der Typ des Elements. Diese Eigenschaft kann einen der folgenden Werte haben: <br />**MDMEMBER_TYPE_REGULAR**<br />**MDMEMBER_TYPE_ALL**<br />**MDMEMBER_TYPE_FORMULA**<br />**MDMEMBER_TYPE_MEASURE**<br />**MDMEMBER_TYPE_UNKNOWN**<br /><br /> <br /><br /> MDMEMBER_TYPE_FORMULA hat Vorrang vor MDMEMBER_TYPE_MEASURE. Aus diesem Grund, wenn es ein Formelelement (berechnetes Element) in der Measures-Dimension, die `MEMBER_TYPE` -Eigenschaft für das berechnete Element MDMEMBER_TYPE_FORMULA.|  
|`MEMBER_UNIQUE_NAME`|Der eindeutige Name des Elements. Für Anbieter, die eindeutige Namen durch eine Einschränkung generieren, ist jede Komponente dieses Namens begrenzt.|  
|`MEMBER_VALUE`|Der Wert des Elements im ursprünglichen Typ.|  
|`PARENT_COUNT`|Die Anzahl der übergeordneten Elemente des Elements.|  
|`PARENT_LEVEL`|Der Abstand des dem Element übergeordneten Elements von der Stammebene der Hierarchie. Die Stammebene entspricht null.|  
|`PARENT_UNIQUE_NAME`|Der eindeutige Name des dem Element übergeordneten Elements. Für sämtliche Elemente auf der Stammebene wird `NULL` zurückgegeben. Für Anbieter, die eindeutige Namen durch eine Einschränkung generieren, ist jede Komponente dieses Namens begrenzt.|  
|`SKIPPED_LEVELS`|Die Anzahl übersprungener Ebenen für das Element.|  
|`UNARY_OPERATOR`|Der unäre Operator für das Element.|  
|`UNIQUE_NAME`|Der vollqualifizierte Name des Elements im folgenden Format: [dimension].[level].[key6.].|  
  
### <a name="properties-syntax-for-non-context-sensitive-properties"></a>PROPERTIES-Syntax für nicht kontextabhängige Eigenschaften  
 Verwenden Sie die folgende Syntax an eine systeminterne nicht kontextabhängige Elementeigenschaft mit dem `PROPERTIES` Schlüsselwort:  
  
 `DIMENSION PROPERTIES Property`  
  
 In dieser Syntax ist es nicht zulässig, die Eigenschaft durch eine Dimension oder Ebene zu qualifizieren. Die Eigenschaft kann nicht qualifiziert werden, weil eine systeminterne Elementeigenschaft, die nicht kontextabhängig ist, für alle Elemente einer Achse gilt.  
  
 Z. B. eine MDX-Anweisung, der angibt, die `DESCRIPTION` systeminterne Elementeigenschaft ist die folgende Syntax:  
  
 `DIMENSION PROPERTIES DESCRIPTION`  
  
 Diese Anweisung gibt die Beschreibung für jedes Element in der Achsendimension zurück. Würden Sie versuchen, die Eigenschaft mit einer Dimension oder einer Ebene zu qualifizieren (wie in *Dimension*`.DESCRIPTION` oder *Level*`.DESCRIPTION`), wäre die Anweisung ungültig.  
  
### <a name="example"></a>Beispiel  
 Die folgenden Beispiele zeigen MDX-Abfragen, die systeminterne Eigenschaften zurückgeben.  
  
 **Beispiel 1: Verwenden kontextabhängiger systeminterner Eigenschaften in Abfragen**  
  
 Im folgenden Beispiel werden die übergeordnete ID, der Schlüssel und der Name jeder Produktkategorie zurückgegeben. Beachten Sie, dass die Eigenschaften als Measures verfügbar gemacht werden. Auf diese Weise können Sie die Eigenschaften bei Ausführen der Abfrage in einem Cellset anzeigen, anstatt das Dialogfeld Elementeigenschaften in SSMS zu öffnen. Sie können eine mit der folgenden Abfrage vergleichbare Abfrage ausführen, um Elementmetadaten aus einem bereits bereitgestellten Cube abzurufen.  
  
```  
WITH  
MEMBER [Measures].[Parent Member ID] AS  
 [Product].[Product Categories].CurrentMember.Parent.PROPERTIES("ID")  
MEMBER [Measures].[Parent Member Key] AS  
 [Product].[Product Categories].CurrentMember.Parent.PROPERTIES("KEY")  
MEMBER [Measures].[Parent Member Name] AS  
 [Product].[Product Categories].CurrentMember.Parent.PROPERTIES("Name")  
SELECT  
 {[Measures].[Parent Member ID], [Measures].[Parent Member Key], [Measures].[Parent Member Name] } on COLUMNS,   
 [Product].[Product Categories].AllMembers on ROWS  
FROM [Adventure Works]  
```  
  
 **Beispiel 2: Nicht kontextabhängige, systeminterne Eigenschaften**  
  
 Das folgende Beispiel enthält eine vollständige Liste der nicht kontextabhängigen, systeminternen Eigenschaften. Nachdem Sie die Abfrage in SSMS ausgeführt haben, klicken Sie auf die einzelnen Elemente, um die Eigenschaften im Dialogfeld Elementeigenschaften anzuzeigen.  
  
```  
SELECT [Measures].[Sales Amount Quota] on COLUMNS,  
[Employee].[Employees].members  
DIMENSION PROPERTIES  
 CATALOG_NAME ,   
 CHILDREN_CARDINALITY ,  
 CUSTOM_ROLLUP ,   
 CUSTOM_ROLLUP_PROPERTIES ,   
 DESCRIPTION ,   
 DIMENSION_UNIQUE_NAME ,   
 HIERARCHY_UNIQUE_NAME ,  
 IS_DATAMEMBER ,   
 IS_PLACEHOLDERMEMBER ,   
 KEY0 ,  
 LCID ,  
 LEVEL_NUMBER ,  
 LEVEL_UNIQUE_NAME ,  
 MEMBER_CAPTION ,   
 MEMBER_KEY ,   
 MEMBER_NAME ,   
 MEMBER_TYPE ,  
 MEMBER_UNIQUE_NAME ,   
 MEMBER_VALUE ,   
 PARENT_COUNT ,   
 PARENT_LEVEL ,   
 PARENT_UNIQUE_NAME ,  
 SKIPPED_LEVELS ,   
 UNARY_OPERATOR ,   
 UNIQUE_NAME    
 ON ROWS  
FROM [Adventure Works]  
WHERE [Employee].[Employee Department].[Department].&[Sales]  
```  
  
 **Beispiel 3: Zurückgeben von Elementeigenschaften als Daten in einem Resultset**  
  
 Im folgenden Beispiel wird die übersetzte Beschriftung für das Product Category-Element in der Product-Dimension im Adventure Works-Cube für bestimmte Gebietsschemas zurückgegeben.  
  
```  
WITH   
MEMBER Measures.CategoryCaption AS Product.Category.CurrentMember.MEMBER_CAPTION  
MEMBER Measures.SpanishCategoryCaption AS Product.Category.CurrentMember.Properties("LCID3082")  
MEMBER Measures.FrenchCategoryCaption AS Product.Category.CurrentMember.Properties("LCID1036")  
SELECT   
{ Measures.CategoryCaption, Measures.SpanishCategoryCaption, Measures.FrenchCategoryCaption } ON 0  
,[Product].[Category].MEMBERS ON 1  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [PeriodsToDate &#40;MDX&#41;](/sql/mdx/periodstodate-mdx)   
 [Untergeordnete Elemente &#40;MDX&#41;](/sql/mdx/children-mdx)   
 [HIERARCHIZE &#40;MDX&#41;](/sql/mdx/hierarchize-mdx)   
 [Anzahl &#40;festgelegt&#41; &#40;MDX&#41;](/sql/mdx/count-set-mdx)   
 [Filter &#40;MDX&#41;](/sql/mdx/filter-mdx)   
 [AddCalculatedMembers &#40;MDX&#41;](/sql/mdx/addcalculatedmembers-mdx)   
 [DrilldownLevel &#40;MDX&#41;](/sql/mdx/drilldownlevel-mdx)   
 [Eigenschaften &#40;MDX&#41;](/sql/mdx/properties-mdx)   
 [PrevMember &#40;MDX&#41;](/sql/mdx/prevmember-mdx)   
 [Verwenden von Elementeigenschaften &#40;MDX&#41;](mdx-member-properties.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)  
  
  
