---
title: LOWER (SSIS-Ausdruck) | Microsoft-Dokumentation
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
- converting uppercase to lowercase
- LOWER function
- uppercase characters [Integration Services]
- lowercase characters
ms.assetid: 109328e1-5604-40ff-895e-f2e7c13fff41
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ed93892fc9157e51453db9fe2cac4d541444db77
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37277016"
---
# <a name="lower-ssis-expression"></a>LOWER (SSIS-Ausdruck)
  Gibt einen Zeichenausdruck zurück, nachdem Großbuchstaben in Kleinbuchstaben konvertiert wurden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
LOWER(character_expression)  
```  
  
## <a name="arguments"></a>Argumente  
 *character_expression*  
 Ein Zeichenausdruck zum Konvertieren in Kleinbuchstaben.  
  
## <a name="result-types"></a>Ergebnistypen  
 DT_WSTR  
  
## <a name="remarks"></a>Hinweise  
 LOWER kann nur mit dem DT_WSTR-Datentyp verwendet werden. Ein *character_expression* -Argument, das ein Zeichenfolgenliteral oder eine Datenspalte mit dem DT_STR-Datentyp ist, wird implizit in den DT_WSTR-Datentyp umgewandelt, bevor LOWER ausgeführt wird. Andere Datentypen müssen explizit in den DT_WSTR-Datentyp umgewandelt werden. Weitere Informationen finden Sie unter [Integration Services-Datentypen](../data-flow/integration-services-data-types.md) und [CAST &#40;SSIS-Ausdruck&#41;](cast-ssis-expression.md).  
  
 LOWER gibt ein NULL-Ergebnis zurück, wenn das Argument NULL ist.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesem Beispiel wird ein Zeichenfolgenliteral in Kleinbuchstaben konvertiert. Als Ergebnis wird "new york" zurückgegeben.  
  
```  
LOWER("New York")  
```  
  
 In diesem Beispiel werden alle Zeichen in der **Color** -Eingabespalte in Kleinbuchstaben konvertiert, außer dem ersten Zeichen. Wenn Color gleich YELLOW ist, wird als Ergebnis "Yellow" zurückgegeben. Weitere Informationen finden Sie unter [SUBSTRING &#40;SSIS-Ausdruck&#41;](substring-ssis-expression.md).  
  
```  
LOWER(SUBSTRING(Color, 2, 15))  
```  
  
 In diesem Beispiel wird der Wert in der **CityName** -Variablen in Kleinbuchstaben konvertiert.  
  
```  
LOWER(@CityName)  
```  
  
## <a name="see-also"></a>Siehe auch  
 [OBERE &#40;SSIS-Ausdruck&#41;](upper-ssis-expression.md)   
 [Funktionen &#40;SSIS-Ausdruck&#41;](functions-ssis-expression.md)  
  
  
