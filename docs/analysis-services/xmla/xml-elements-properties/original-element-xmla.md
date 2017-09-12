---
title: Original-Element (XMLA) | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Original Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.original
- http://schemas.microsoft.com/analysisservices/2003/engine#Original
- urn:schemas-microsoft-com:xml-analysis#Original
helpviewer_keywords:
- Original element
ms.assetid: c98a3700-ac19-4341-85d9-5afedf662601
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 75a0345459be5e065a7a737b8036e505f799d549
ms.contentlocale: de-de
ms.lasthandoff: 09/01/2017

---
# <a name="original-element-xmla"></a>Original-Element (XMLA)
  Enthält den ursprünglichen Speicherort im Dateisystem, in einem [Ordner](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Folder>  
   ...  
   <Original>...</Original>  
   ...  
</Folder>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|String|  
|Standardwert|Keine|  
|Kardinalität|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Ordner](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Die **ursprünglichen** -Element enthält einen UNC-Pfad mit dem Wert ersetzt werden die [neu](../../../analysis-services/xmla/xml-elements-properties/new-element-xmla.md) vom übergeordneten Element enthaltenen Elements **Ordner** -Element für alle Objekte wiederhergestellt oder synchronisiert werden, während eine [wiederherstellen](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) oder [Synchronize](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md) Befehl. Der Wert dieses Elements wird verglichen, auf den Wert des der [StorageLocation](../../../analysis-services/scripting/properties/storagelocation-element-assl.md) -Element für jeden Cube, Measuregruppe oder Partition und, wenn eine Übereinstimmung gefunden wird, wird den Wert von der **neu** Element wird verwendet, um die Aktualisieren **StorageLocation** des Objekts während der Wiederherstellung oder Synchronisierung.  
  
 Weitere Informationen zum Sichern und Wiederherstellen von Objekten finden Sie unter [sichern, wiederherstellen, und Synchronisieren von Datenbanken &#40; XMLA &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  