---
title: DATEPART (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], DATEPART
- DATEPART function
ms.assetid: 3e590094-fc49-4144-805f-fdc1bf2fe509
caps.latest.revision: 40
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c8309f3f4292795cebffe94f03e1418bb36d8929
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37209790"
---
# <a name="datepart-ssis-expression"></a>DATEPART (SSIS-Ausdruck)
  Gibt eine ganze Zahl zurück, die einen datepart-Wert eines Datums darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DATEPART(datepart, date)  
```  
  
## <a name="arguments"></a>Argumente  
 *datepart*  
 Der Parameter, der angibt, für welche Datumseinheit ein neuer Wert zurückgegeben werden soll.  
  
 *Datum*  
 Ein Ausdruck, der ein gültiges Datum oder eine Zeichenfolge im Datumsformat zurückgibt.  
  
## <a name="result-types"></a>Ergebnistypen  
 DT_I4  
  
## <a name="remarks"></a>Hinweise  
 DATEPART gibt ein NULL-Ergebnis zurück, wenn das Argument NULL ist.  
  
 Ein Datumsliteral muss explizit in einen der date-Datentypen umgewandelt werden. Weitere Informationen finden Sie unter [Integration Services Datentypen](../data-flow/integration-services-data-types.md).  
  
 In der folgenden Tabelle sind die datepart-Werte und Abkürzungen aufgeführt, die von der Ausdrucksauswertung erkannt werden. Bei datepart-Namen wird die Groß-/Kleinschreibung nicht berücksichtigt.  
  
|datepart|Abkürzungen|  
|--------------|-------------------|  
|Year|yy, yyyy|  
|Quarter|qq, q|  
|Month|mm, m|  
|Dayofyear|dy, y|  
|Day|dd, d|  
|Week|wk, ww|  
|Arbeitstag|dw|  
|Hour|Hh|  
|Minute|mi, n|  
|Zweimal|ss, s|  
|Millisekunde|Ms|  
  
## <a name="ssis-expression-examples"></a>Beispiele für SSIS-Ausdrücke  
 In diesem Beispiel wird die ganze Zahl zurückgegeben, die den Monat in einem Datumsliteral darstellt. Falls das Datum das Format „MM/TT/JJJJ“ aufweist, gibt dieses Beispiel „11“ zurück.  
  
```  
DATEPART("month", (DT_DBTIMESTAMP)"11/04/2002")  
```  
  
 In diesem Beispiel wird die ganze Zahl zurückgegeben, die den Tag in der **ModifiedDate** -Spalte darstellt.  
  
```  
DATEPART("dd", ModifiedDate)  
```  
  
 In diesem Beispiel wird die ganze Zahl zurückgegeben, die das Jahr des aktuellen Datums darstellt.  
  
```  
DATEPART("yy",GETDATE())  
```  
  
## <a name="see-also"></a>Siehe auch  
 [DATEADD &#40;SSIS-Ausdruck&#41;](dateadd-ssis-expression.md)   
 [DATEDIFF &#40;SSIS-Ausdruck&#41;](datediff-ssis-expression.md)   
 [DAY &#40;SSIS-Ausdruck&#41;](day-ssis-expression.md)   
 [MONTH &#40;SSIS-Ausdruck&#41;](month-ssis-expression.md)   
 [YEAR &#40;SSIS-Ausdruck&#41;](year-ssis-expression.md)   
 [Funktionen &#40;SSIS-Ausdruck&#41;](functions-ssis-expression.md)  
  
  
