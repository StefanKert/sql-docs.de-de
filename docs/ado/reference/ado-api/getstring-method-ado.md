---
title: GetString-Methode (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::raw_GetString
- Recordset20::GetString
helpviewer_keywords:
- GetString method [ADO]
ms.assetid: 92452940-b2a7-456e-94fc-3780c71da33c
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 824ad1a3223538e724e4430186dcf176e86617a2
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35278879"
---
# <a name="getstring-method-ado"></a>GetString-Methode (ADO)
Gibt die [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) als Zeichenfolge.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Variant = recordset.GetString(StringFormat, NumRows, ColumnDelimiter, RowDelimiter, NullExpr)  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt die **Recordset** als eine Zeichenfolge ausgewertet **Variant** (BSTR).  
  
#### <a name="parameters"></a>Parameter  
 *StringFormat*  
 Ein [StringFormatEnum](../../../ado/reference/ado-api/stringformatenum.md) Wert, der angibt, wie die **Recordset** in eine Zeichenfolge konvertiert werden sollen. Die *RowDelimiter*, *ColumnDelimiter*, und *NullExpr* Parameter dienen nur mit einem *StringFormat* von  **AdClipString**.  
  
 *NumRows*  
 Optional. Die Anzahl der Zeilen in konvertiert werden die **Recordset**. Wenn *NumRows* nicht angegeben wird, oder wenn sie größer als die Gesamtzahl der Zeilen in ist die **Recordset**, klicken Sie dann alle Zeilen in der **Recordset** konvertiert werden.  
  
 *columnDelimiter*  
 Optional. Ein Trennzeichen zwischen den Spalten verwendet werden, wenn angegeben, andernfalls das Tabulatorzeichen.  
  
 *RowDelimiter*  
 Optional. Ein Trennzeichen zwischen Zeilen verwendet werden, wenn angegeben, andernfalls das Wagenrücklaufzeichen.  
  
 *NullExpr*  
 Optional. Ein Ausdruck, der anstelle von null-Wert verwendet wird, wenn andernfalls die leere Zeichenfolge angegeben wird.  
  
## <a name="remarks"></a>Hinweise  
 Zeilendaten, aber keine Schemadaten wird in der Zeichenfolge gespeichert. Aus diesem Grund eine **Recordset** kann nicht erneut geöffnet werden, mithilfe dieser Zeichenfolge.  
  
 Diese Methode entspricht dem RDO **GetClipString** Methode.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetString-Methode – Beispiel (VB)](../../../ado/reference/ado-api/getstring-method-example-vb.md)
