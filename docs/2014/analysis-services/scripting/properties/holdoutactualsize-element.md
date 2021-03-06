---
title: HoldoutActualSize-Element | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
f1_keywords:
- HoldoutActualSize
helpviewer_keywords:
- HoldoutActualSize element
ms.assetid: 606a6674-cedb-4cee-82d0-26589f084dd9
caps.latest.revision: 18
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4f74b11b9032285bf45bc8b7705953adf6d58f04
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37297280"
---
# <a name="holdoutactualsize-element"></a>HoldoutActualSize-Element
  Gibt die tatsächliche Größe an, nach der Verarbeitung der zurückhaltungspartition, die den Testsatz enthält eine [MiningStructure](../objects/miningstructure-element-assl.md) Element. Die übrigen Fälle im Datensatz werden zum Training verwendet. Diese Eigenschaft ist schreibgeschützt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MiningStructure>  
   ...  
   <ddl100_100:HoldoutActualSize>...</ddl100_100:HoldoutActualSize>  
   ...  
</MiningStructure  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Schreibgeschützter ganzzahliger Wert.|  
|Standardwert|Nicht verfügbar|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[MiningStructure](../objects/miningstructure-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert für `HoldoutActualSize` hängt von den Quelldaten sowie von den Werten für [HoldoutMaxCases](holdoutmaxcases-element.md), [HoldoutMaxPercent](holdoutmaxpercent-element.md), und [HoldoutSeed](holdoutseed-element.md). Deshalb ist der Wert für `HoldoutActualSize` erst verfügbar, nachdem [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] die Miningstruktur verarbeitet hat.  
  
 Das Element, das dem übergeordneten entspricht `HoldoutActualSize` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
> [!NOTE]  
>  In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] hat nicht die Verwendung von zurückhaltungspartitionen für Miningstrukturen unterstützt. Aus diesem Grund [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Scripting Language (ASSL)-Anweisungen, die einen der zurückhaltungsparameter, enthalten `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed`, oder `HoldoutActualSize`, kann nicht verwendet werden, [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Wenn Sie einen dieser zurückhaltungsparameter in einer ASSL-Anweisung in verwenden [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] einen Fehler zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)   
 [HoldoutMaxCases-Element](holdoutmaxcases-element.md)   
 [HoldoutMaxPercent-Element](holdoutmaxpercent-element.md)   
 [HoldoutSeed-Element](holdoutseed-element.md)  
  
  
