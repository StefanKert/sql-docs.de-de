---
title: BeginTransaction-Element (XMLA) | Microsoft-Dokumentation
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
- BeginTransaction Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#BeginTransaction
- microsoft.xml.analysis.begintransaction
- http://schemas.microsoft.com/analysisservices/2003/engine#BeginTransaction
helpviewer_keywords:
- BeginTransaction command
ms.assetid: fca122fc-b57c-4ba6-849b-ca8c93cf64e9
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1685c1c61c248cf37672cab17ccf3144e7d5e7ec
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37253042"
---
# <a name="begintransaction-element-xmla"></a>BeginTransaction-Element (XMLA)
  Startet eine Transaktion für die aktuelle Sitzung mit einer Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Command>  
   <BeginTransaction />  
</Command>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Befehl](../xml-elements-properties/command-element-xmla.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Die `BeginTransaction` Befehl startet eine aktive Transaktion in der aktuellen Sitzung. Besteht bereits eine aktive Transaktion, inkrementiert die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Instanz den Verweiszähler der Transaktionen für die aktuelle Sitzung. Wenn nicht, startet die Instanz eine neue Transaktion und setzt den Verweiszähler der aktuellen Sitzung auf 1. Wenn eine aktive Transaktion explizit über den `BeginTransaction`-Befehl angegeben wird, werden alle folgenden Befehle innerhalb der explizit angegebenen Transaktion ausgeführt.  
  
 Wenn die aktuelle Sitzung beendet wird und der Verweiszähler der Transaktionen höher als null ist, wird für alle aktiven Transaktionen ein Rollback ausgeführt.  
  
 Wenn es in der aktuellen Sitzung keine explizit angegebenen aktiven Transaktionen gibt, wird jeder in der aktuellen Sitzung ausgegebene Befehl innerhalb einer implizit definierten Transaktion ausgeführt. Ein Commit wird für die implizite Transaktion ausgeführt, wenn der Befehl erfolgreich ist; bei einem Fehlschlagen des Befehls wird ein Rollback ausgeführt.  
  
## <a name="see-also"></a>Siehe auch  
 [Cancel-Element &#40;XMLA&#41;](cancel-element-xmla.md)   
 [CommitTransaction-Element &#40;XMLA&#41;](committransaction-element-xmla.md)   
 [RollbackTransaction-Element &#40;XMLA&#41;](rollbacktransaction-element-xmla.md)   
 [Befehle &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
