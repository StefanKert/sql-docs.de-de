---
title: Hierarchy-Datentyp (ASSL) | Microsoft-Dokumentation
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
- Hierarchy Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Hierarchy data type
ms.assetid: 2e05917e-7e5d-4dd1-817b-4ff5647747ff
caps.latest.revision: 17
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b20bed156e97c33a1c9f9df02677ef403767e472
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37230010"
---
# <a name="hierarchy-data-type-assl"></a>Hierarchy-Datentyp (ASSL)
  Definiert einen Grunddatentyp, der eine Hierarchie in einer Dimension darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Hierarchy>  
   <Name>...</Name>  
   <ID>...</ID>  
   <Description>...</Description>  
   <DisplayFolder>...</DisplayFolder>  
   <Translations>...</Translations>  
   <AllMemberName>...</AllMemberName>  
   <AllMemberTranslations>...</AllMemberTranslation>  
   <MemberNamesUnique>...</MemberNamesUnique>  
   <AllowDuplicateNames>...</AllowDuplicateNames>  
   <Levels>...</Levels>  
   <Annotations>...</Annotation>  
</Hierarchy>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|InclusionThresholdSetting|  
|Abgeleitete Datentypen|InclusionThresholdSetting|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|InclusionThresholdSetting|  
|Untergeordnete Elemente|[AllMemberName](../properties/name-element-assl.md), [AllMemberTranslations](../collections/translations-element-assl.md), [AllowDuplicateNames](../properties/allowduplicatenames-element-assl.md), [Annotations](../collections/annotations-element-assl.md), [Description](../properties/description-element-assl.md), [DisplayFolder](../properties/displayfolder-element-assl.md), [ID](../properties/id-element-assl.md), [Levels](../collections/levels-element-assl.md), [MemberNamesUnique](../properties/membernamesunique-element-assl.md), [Name](../properties/name-element-assl.md), [Translations](../collections/translations-element-assl.md)|  
|Abgeleitete Elemente|[Hierarchy](../objects/hierarchy-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das *MemberNamesUnique* -Element wird unter DevelopmentMode 1 und 2 für den SharePoint- bzw. tabellarischen Servermodus nicht unterstützt.  
  
 Das *MemberKeysUnique* -Element wird unter DevelopmentMode 1 und 2 für den SharePoint- bzw. tabellarischen Servermodus nicht unterstützt.  
  
 Das *AllowDuplicateNames* -Element wird unter DevelopmentMode 1 und 2 für den SharePoint- bzw. tabellarischen Servermodus nicht unterstützt.  
  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.Hierarchy>.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
