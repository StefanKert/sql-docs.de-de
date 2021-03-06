---
title: Concat-Funktion (XQuery) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.component: xquery
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- fn:concat function
- concat function [XQuery]
ms.assetid: d50afd20-a297-445e-be9e-13b48017e7ca
caps.latest.revision: 32
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 8be65777bb65ad54735ad6bdf43ea88608355c5b
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "37981932"
---
# <a name="functions-on-string-values---concat"></a>Funktionen für Zeichenfolgenwerte – concat
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Nimmt null oder mehr Zeichenfolgen als Argumente an und gibt eine Zeichenfolge zurück, die durch Verketten der Werte der einzelnen Argumente erstellt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
fn:concat ($string as xs:string?  
           ,$string as xs:string?  
           [, ...]) as xs:string  
```  
  
## <a name="arguments"></a>Argumente  
 *$string*  
 Optionale zu verkettende Zeichenfolge.  
  
## <a name="remarks"></a>Hinweise  
 Die Funktion erfordert mindestens zwei Argumente. Wenn ein Argument eine leere Sequenz ist, wird diese als eine Zeichenfolge mit der Länge Null behandelt.  
  
## <a name="supplementary-characters-surrogate-pairs"></a>Ergänzende Zeichen (Ersatzpaare)  
 Das Verhalten von Ersatzzeichenpaaren in XQuery-Funktionen hängt vom Kompatibilitätsgrad der Datenbank ab und in einigen Fällen vom Standardnamespace-URI für Funktionen. Weitere Informationen finden Sie im Abschnitt "XQuery-Funktionen sind Ersatzzeichenabhängig" im Thema [wichtige Änderungen an Funktionen der Datenbank-Engine in SQL Server 2016](../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md). Siehe auch [ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41; ](../t-sql/statements/alter-database-transact-sql-compatibility-level.md) und [Collation and Unicode Support](../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="examples"></a>Beispiele  
 In diesem Thema stellt XQuery-Beispiele für XML-Instanzen, die in verschiedenen gespeichert sind **Xml** Spalten vom Typ, in der AdventureWorks-Beispieldatenbank.  
  
### <a name="a-using-the-concat-xquery-function-to-concatenate-strings"></a>A. Verwenden der concat()-Funktion von XQuery zum Verketten von Zeichenfolgen  
 Diese Abfrage gibt für ein bestimmtes Produktmodell eine Zeichenfolge zurück, die durch Verketten des Garantiezeitraumes und der Garantiebeschreibung erstellt wird. Im Katalogbeschreibungsdokument besteht das <`Warranty`>-Element aus untergeordneten Elementen von <`WarrantyPeriod`> und <`Description`>.  
  
```  
WITH XMLNAMESPACES (  
'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd,  
'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS wm)  
SELECT CatalogDescription.query('  
    <Product   
        ProductModelID= "{ (/pd:ProductDescription/@ProductModelID)[1] }"  
        ProductModelName = "{ sql:column("PD.Name") }" >  
        {   
          concat( string((/pd:ProductDescription/pd:Features/wm:Warranty/wm:WarrantyPeriod)[1]), "-",  
                  string((/pd:ProductDescription/pd:Features/wm:Warranty/wm:Description)[1]))   
         }   
     </Product>  
 ') as Result  
FROM Production.ProductModel PD  
WHERE  PD.ProductModelID=28  
  
```  
  
 Beachten Sie hinsichtlich der vorherigen Abfrage Folgendes:  
  
-   In der SELECT-Klausel ist CatalogDescription eine **Xml** Type-Spalte. Aus diesem Grund die [Query()-Methode (XML-Datentyp)](../t-sql/xml/query-method-xml-data-type.md), Instructions.query() verwendet. Die XQuery-Anweisung wird als Argument der query-Methode angegeben.  
  
-   Das Dokument, für das die Abfrage ausgeführt wird, verwendet Namespaces. Aus diesem Grund die **Namespace** Schlüsselwort wird verwendet, um das Präfix für den Namespace zu definieren. Weitere Informationen finden Sie unter [XQuery-Prolog](../xquery/modules-and-prologs-xquery-prolog.md).  
  
 Dies ist das Ergebnis:  
  
```  
<Product ProductModelID="28" ProductModelName="Road-450">1 year-parts and labor</Product>  
```  
  
 Die vorherige Abfrage ruft Informationen für ein bestimmtes Produkt ab. Die folgende Abfrage ruft die gleichen Informationen für alle Produkte ab, für die XML-Katalogbeschreibungen gespeichert sind. Die **exist()** Methode der **Xml** -Datentyp in die WHERE-Klausel "true" zurück, wenn es sich bei dem XML-Dokument in den Zeilen einer <`ProductDescription`> Element.  
  
```  
WITH XMLNAMESPACES (  
'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd,  
'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS wm)  
  
SELECT CatalogDescription.query('  
    <Product   
        ProductModelID= "{ (/pd:ProductDescription/@ProductModelID)[1] }"   
        ProductName = "{ sql:column("PD.Name") }" >  
        {   
          concat( string((/pd:ProductDescription/pd:Features/wm:Warranty/wm:WarrantyPeriod)[1]), "-",  
                  string((/pd:ProductDescription/pd:Features/wm:Warranty/wm:Description)[1]))   
         }   
     </Product>  
 ') as Result  
FROM Production.ProductModel PD  
WHERE CatalogDescription.exist('//pd:ProductDescription ') = 1  
  
```  
  
 Beachten Sie, die von der boolesche Wert zurückgegeben der **exist()** Methode der **Xml** Typ mit 1 verglichen wird.  
  
### <a name="implementation-limitations"></a>Implementierungseinschränkungen  
 Die folgenden Einschränkungen sind zu beachten:  
  
-   Die **concat()** -Funktion in SQL Server nimmt nur Werte vom Typ xs: String. Andere Werte müssen explizit in xs:string oder xdt:untypedAtomic umgewandelt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [XQuery Functions against the xml Data Type (XQuery-Funktionen für den xml-Datentyp)](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
