---
title: Cell-Objekt (ADO MD) | Microsoft Docs
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
- Cell
helpviewer_keywords:
- Cell object [ADO MD]
ms.assetid: dcc2f044-b785-4a29-9bc5-b673f66eedf9
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f82bfdf0e1b61d3b6fdab096af77f8b843178384
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35283429"
---
# <a name="cell-object-ado-md"></a>Cell-Objekt (ADO MD)
Stellt die Daten am Schnittpunkt der Achsenkoordinaten enthaltenen im Cellset dar.  
  
## <a name="remarks"></a>Hinweise  
 Ein **Zelle** -Objekt zurück, die [Element](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) Eigenschaft eine [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) Objekt.  
  
 Die Auflistungen und Eigenschaften einer **Zelle** -Objekts können Sie folgende Möglichkeiten:  
  
-   Zurückgeben der Daten in der **Zelle** mit der [Wert](../../../ado/reference/ado-md-api/value-property-ado-md.md) Eigenschaft.  
  
-   Die Zeichenfolge zurückgegeben, die die formatierte Anzeige der darstellt der **Wert** Eigenschaft mit dem [FormattedValue](../../../ado/reference/ado-md-api/formattedvalue-property-ado-md.md) Eigenschaft.  
  
-   Den Ordinalwert des Zurückgeben der **Zelle** innerhalb der **Cellset** mit der [Ordinal](../../../ado/reference/ado-md-api/ordinal-property-ado-md-cell.md) Eigenschaft.  
  
-   Bestimmen Sie die Position des der **Zelle** innerhalb der [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) mit der [Positionen](../../../ado/reference/ado-md-api/positions-collection-ado-md.md) Auflistung.  
  
-   Weitere Informationen zum Abrufen der **Zelle** mit dem standard ADO [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) Auflistung.  
  
 Die **Eigenschaften** Auflistung enthält Eigenschaften, die vom Anbieter bereitgestellt. Die folgende Tabelle enthält Eigenschaften, die möglicherweise zur Verfügung. Die tatsächliche Eigenschaftenliste kann je nach der Implementierung des Anbieters abweichen. Siehe die Dokumentation für Ihren Anbieter für eine vollständige Liste der verfügbaren Eigenschaften.  
  
|Name|Description|  
|----------|-----------------|  
|Hintergrundfarbe|Background-Farbe ab die Zelle angezeigt wird.|  
|FontFlags|Bitmaske, die Auswirkungen auf die Schriftart detailliert angibt.|  
|FontName|Der Wert der Zelle anzuzeigenden verwendete Schriftart.|  
|FontSize|Der Wert der Zelle anzuzeigenden verwendeten Schriftgrad.|  
|ForeColor|Die Vordergrundfarbe ab die Zelle angezeigt wird.|  
|FormatString|Der Wert in eine formatierte Zeichenfolge.|  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Eigenschaften, Methoden und Ereignisse](../../../ado/reference/ado-md-api/cell-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Achse-Beispiel (VBScript)](../../../ado/reference/ado-md-api/axis-example-vbscript.md)   
 [Cellset-Objekt (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)   
 [Positionen-Auflistung (ADO MD)](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)   
 [Properties-Collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
