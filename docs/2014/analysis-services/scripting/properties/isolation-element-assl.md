---
title: Isolation-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Isolation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Isolation element
ms.assetid: 28c98c6f-668e-4547-8d25-127cc3995a7d
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a21593d360342dc703e1da45d50b4ddff74241a7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37257226"
---
# <a name="isolation-element-assl"></a>Isolation-Element (ASSL)
  Gibt die Isolationsstufe für ein Element, das von abgeleitet ist die [DataSource](../data-type/datasource-data-type-assl.md) -Datentyp.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DataSource>  
   ...  
   <Isolation>...</Isolation>  
   ...  
</DataSource>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*"ReadCommitted"*|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[DataSource](../data-type/datasource-data-type-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*"ReadCommitted"*|Gibt an, dass Anweisungen Zeilen nicht lesen können, die von anderen Transaktionen geändert wurden, für die jedoch noch kein Commit ausgeführt wurde. Dadurch werden Dirty Reads verhindert. Andere Transaktionen können Daten zwischen einzelnen Anweisungen innerhalb der aktuellen Transaktion ändern. Dies führt zu nicht wiederholbaren Lesevorgängen oder Phantomdaten. Dieser Wert ist der Standardwert für das `Isolation`-Element.|  
|*Momentaufnahme*|Gibt an, dass die von einer beliebigen Anweisung in einer Transaktion gelesenen Daten der im Hinblick auf Transaktionen konsistenten Version der Daten entsprechen, die zu Beginn der Transaktion vorhanden waren. Die Transaktion kann nur Datenänderungen erkennen, für die vor dem Beginn der Transaktion ein Commit ausgeführt wurde. Datenänderungen, die nach dem Start der aktuellen Transaktion durch andere Transaktionen vorgenommen wurden, sind für die Anweisungen, die in der aktuellen Transaktion ausgeführt werden, nicht sichtbar. So entsteht der Eindruck, als ob die Anweisungen in einer Transaktion eine Momentaufnahme der Daten erhalten, für die ein Commit ausgeführt wurde, wie sie zu Beginn der Transaktion vorhanden waren.|  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
