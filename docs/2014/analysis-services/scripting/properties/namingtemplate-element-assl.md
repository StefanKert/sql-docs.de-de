---
title: NamingTemplate-Element (ASSL) | Microsoft-Dokumentation
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
- NamingTemplate Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- NamingTemplate
helpviewer_keywords:
- NamingTemplate element
ms.assetid: d68d765c-f012-40c1-acd4-32741ee2eadf
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8ba346be8664cf26992143c15789684c503fdf2a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37300840"
---
# <a name="namingtemplate-element-assl"></a>NamingTemplate-Element (ASSL)
  Definiert, wie Ebenen in einer über-/ unterordnungshierarchie aus erstellt benannt werden die [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md) übergeordneten Elements.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DimensionAttribute>  
   ...  
      <NamingTemplate>...</NamingTemplate>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[DimensionAttribute-Objekt](../data-type/dimensionattribute-data-type-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert des der `NamingTemplate` Element wird nur von übergeordneten Attributen verwendet (in anderen Worten: der Wert der die [Nutzung](usage-element-dimensionattribute-assl.md) Element der `DimensionAttribute` übergeordnetes Element festgelegt ist, um *übergeordneten*).  
  
 Wenn ein übergeordnetes Attribut zum Erstellen einer Hierarchie verwendet wird, werden die Ebenen der Hierarchie durch die Über-/Unterordnungsbeziehungen zwischen den Elementen, die im übergeordneten Attribut enthalten sind, bestimmt. Daher können die Ebenennamen nicht wie in anderen Dimensionen von den Attributnamen, die für die Hierarchie verwendet werden, abgeleitet werden.  
  
 Stattdessen wird eine Benennungsvorlage verwendet, um Ebenennamen für Über-/Unterordnungshierarchien zu generieren. Die `NamingTemplate` in übergeordneten Attribut definierte-Element enthält einen Zeichenfolgenausdruck, der verwendet, um Ebenennamen zu definieren. Es gibt zwei Möglichkeiten, eine Benennungsvorlage für ein übergeordnetes Attribut zu definieren. Sie können entweder ein Benennungsmuster entwerfen, oder Sie können eine Namensliste angeben.  
  
 Ein Benennungsmuster enthält ein Sternchen (`*`) als Platzhalterzeichen für einen Indikator, der mit jeder neuen und tieferen Ebene gesteigert und in den Namen eingefügt wird. Beispielsweise führt die Verwendung von `Level *` zu den Ebenennamen `Level 01`, `Level 02`, `Level 03`usw., wenn keine (ALL) Ebene definiert ist. Wenn ein Benennungsmuster kein Platzhalterzeichen enthält, wird es zunächst in seiner ursprünglichen Form verwendet. Danach werden dann alle folgenden Ebenen durch Anhängen eines Leerzeichens und einer Zahl an das Ende des Musters gebildet. Beispielsweise führt die Verwendung von `Level` zu den Ebenennamen `Level`, `Level 01`, `Level 02`usw.  
  
 Verwenden Sie einen bestimmten Satz von Namen für die Benennung, den Wert des der `NamingTemplate` -Elements auf eine durch Semikolons getrennte Liste von Ebenennamen festgelegt. Jeder Name in der Liste wird für einen nachfolgenden Ebenennamen verwendet. Wenn die Anzahl der Ebenen die Anzahl der Namen in der Liste überschreitet, wird der letzte Name in der Liste als Vorlage für etwaige zusätzliche Ebenennamen verwendet, wobei ein Leerzeichen und eine Ordnungszahl gemäß der Beschreibung oben an den letzten Namen angehängt wird. Beispielsweise führt die Verwendung von `Division;Group;Unit` zu den Ebenennamen `Division`, `Group`, `Unit`, `Unit 01`, `Unit 02`usw. Dagegen führt die Verwendung von `Division;Group;Unit *` zu den Ebenennamen `Division`, `Group`, `Unit 03`, `Unit 04`usw.  
  
 Jeder Name in der Liste wird als Vorlage behandelt, um die Eindeutigkeit von Ebenennamen sicherzustellen. Beispielsweise führt die Verwendung von `Manager;Team Lead;Manager;Team Lead;Worker *` zu den Ebenennamen `Manager`, `Team Lead`, `Manager 01`, `Team Lead 01`, `Worker 05`, `Worker 06`.  
  
 Verwenden Sie zwei Sternchen (*), um das Sternchen enthalten (\*) Zeichen in einen Ebenennamen als Teil einer benennungsvorlage.  
  
 Das Element, das dem übergeordneten entspricht `NamingTemplate` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Siehe auch  
 [Namingtemplatetranslation-Element &#40;ASSL&#41;](../collections/translations-element-assl.md)   
 [DimensionAttribute-Datentyp &#40;ASSL&#41;](../data-type/dimensionattribute-data-type-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
