---
title: KPI-Element (ASSL) | Microsoft-Dokumentation
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
- Kpi Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Kpi
helpviewer_keywords:
- Kpi element
ms.assetid: 1979a58f-97a8-4c1a-aa65-dcfb6d2404cf
caps.latest.revision: 32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 27b0bcbe2ddaabcc7b3f9ef16f3fa620a8c2db38
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37235640"
---
# <a name="kpi-element-assl"></a>Kpi-Element (ASSL)
  Definiert einen Key Performance Indicator (KPI) innerhalb einer [Cube](cube-element-assl.md) Element oder ein [Perspektive](perspective-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Kpis>  
   <Kpi> <!-- ancestor: Cube -->  
            <Name>...</Name>  
      <ID>...</ID>  
      <Description>...</Description>  
      <Translations>...</Translations>  
      <DisplayFolder>...</DisplayFolder>  
      <AssociatedMeasureGroupID>...</AssociatedMeasureGroupID>  
      <Value>...</Value>  
            <Goal>...</Goal>  
      <Status>...</Status>  
      <Trend>...</Trend>  
      <TrendGraphic>...</TrendGraphic>  
      <StatusGraphic>...</StatusGraphic>  
      <CurrentTimeMember>...</CurrentTimeMember>  
      <Annotations>...</Annotations>  
   </Kpi>  
   <!-- or -->  
   <Kpi xsi:type="PerspectiveKpi">...</Kpi> <!-- ancestor: Perspective -->  
   </Kpi>  
</Kpis>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
|Vorgänger oder übergeordnetes Element|Datentyp|  
|------------------------|---------------|  
|[Cube](cube-element-assl.md)|InclusionThresholdSetting|  
|[Perspektive](../data-type/perspectivekpi-data-type-assl.md)|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[KPIs](../collections/kpis-element-assl.md)|  
  
## <a name="child-elements"></a>Untergeordnete Elemente  
  
|Vorgänger oder übergeordnetes Element|Untergeordnete Elemente|  
|------------------------|--------------------|  
|[Cube](../collections/annotations-element-assl.md), [AssociatedMeasureGroupID](../properties/id-element-assl.md), [CurrentTimeMember](member-element-assl.md), [Beschreibung](../properties/description-element-assl.md), [DisplayFolder](../properties/displayfolder-element-assl.md), [Ziel](../properties/goal-element-assl.md), [ID](../properties/id-element-assl.md), [Namen](../properties/name-element-assl.md), [Status](../properties/status-element-assl.md), [StatusGraphic](../properties/statusgraphic-element-assl.md), [Übersetzungen ](../collections/translations-element-assl.md), [Trend](../properties/trend-element-assl.md), [TrendGraphic](../properties/trendgraphic-element-assl.md), [Wert](../properties/value-element-assl.md)|  
|[Perspektive](perspective-element-assl.md)|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Die entsprechenden Elemente im Analysis Management Objects (AMO)-Objektmodell sind <xref:Microsoft.AnalysisServices.Kpi> und <xref:Microsoft.AnalysisServices.PerspectiveKpi>.  
  
## <a name="see-also"></a>Siehe auch  
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  
