---
title: Database-Element zur Arbeitsauslastung (DTA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: dta
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Database element
ms.assetid: 112fca2a-37e5-4162-b2e7-b56eb8ab0c6f
caps.latest.revision: 12
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: faa68d2dd7fa5b1caab9f3ea04e09d873e1a4deb
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38050648"
---
# <a name="database-element-for-workload-dta"></a>Database-Element zur Arbeitsauslastung (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Gibt die Datenbank an, in der sich die Ablaufverfolgungstabelle der Arbeitsauslastung befindet.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<Workload>  
  <Database>  
   ...code removed here...  
  </Database>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|und Beschreibung|  
|--------------------|-----------------|  
|**Datentyp und -länge**|Keine.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Einmalig erforderlich, wenn kein anderer Arbeitsauslastungstyp angegeben ist. Sie müssen ein untergeordnetes **EventString**-, **File**- oder **Database** -Element für das übergeordnete **Workload** -Element angeben. Es kann jedoch nur ein Typ verwendet werden. Wenn Sie beispielsweise eine Arbeitsauslastung mit dem **Database** -Element angeben, können Sie in dieser XML-Eingabedatei keine Arbeitsauslastung mit dem **File** -Element angeben.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[Workload-Element &#40;DTA&#41;](../../tools/dta/workload-element-dta.md)|  
|**Untergeordnete Elemente**|[Name-Element für Datenbank &#40;DTA&#41;](../../tools/dta/name-element-for-database-dta.md)<br /><br /> [Schema-Element für Datenbank &#40;DTA&#41;](../../tools/dta/schema-element-for-database-dta.md)|  
  
## <a name="remarks"></a>Remarks  
 Dieses Element hat den Namen **DatabaseDetailsTypecomplexType** im XML-Schema des Datenbankoptimierungsratgebers. Dieses **Database** -Element ist nicht mit dem identisch, dessen übergeordnetes Stammelement das **Configuration** -Element ist. (Weitere Informationen finden Sie unter [Database-Element für Konfiguration &#40;DTA&#41;](../../tools/dta/database-element-for-configuration-dta.md).)  
  
## <a name="example"></a>Beispiel  
 Ein Beispiel für die Verwendung dieses **Database** -Elements finden Sie im Codebeispiel unter [Workload-Element &#40;DTA&#41;](../../tools/dta/workload-element-dta.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 
  [XML-Eingabedateireferenz &amp;#40;Datenbankoptimierungsratgeber&amp;#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
