---
title: HideMemberIf-Element (ASSL) | Microsoft Docs
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
- HideMemberIf Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- HideMemberIf
helpviewer_keywords:
- HideMemberIf element
ms.assetid: ff0e6b19-6216-43ac-ba76-1628da8c333b
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 63e9386cbeb679bef13c87857df9b95a10863099
ms.contentlocale: de-de
ms.lasthandoff: 09/01/2017

---
# <a name="hidememberif-element-assl"></a>HideMemberIf-Element (ASSL)
  Gibt an, ob und wann ein Element auf einer Ebene aus Clientanwendungen ausgeblendet werden sollte.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Level>  
   ...  
   <HideMemberIf>...</HideMemberIf>  
   ...  
</Level>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*Nie*|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[Level](../../../analysis-services/scripting/objects/level-element-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|Wert|Description|  
|-----------|-----------------|  
|*Nie*|Elemente werden nie ausgeblendet.|  
|*OnlyChildWithNoName*|Ein Element wird ausgeblendet, wenn es das einzige untergeordnete Element seines übergeordneten Elements ist und sein Name leer ist.|  
|*OnlyChildWithParentName*|Ein Element wird ausgeblendet, wenn es das einzige untergeordnete Element seines übergeordneten Elements ist und identisch mit seinem übergeordneten Element ist.|  
|*NoName*|Ein Element wird ausgeblendet, wenn sein Name leer ist.|  
|*ParentName*|Ein Element wird ausgeblendet, wenn sein Name dem seines übergeordneten Elements entspricht.|  
  
## <a name="remarks"></a>Hinweise  
 Die Enumeration, die den zulässigen Werten für entspricht **HideMemberIf** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.HideIfValue>.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  