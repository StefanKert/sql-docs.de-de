---
title: ToString (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ToString (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- ToString (geometry Data Type)
ms.assetid: 2e55fa98-aa22-4baa-a516-7c233a33e212
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: bdcc07e56799e45fc6e8c84a7b9b9e45bfa0fd07
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "37999332"
---
# <a name="tostring-geometry-data-type"></a>ToString (geometry-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Gibt die Open Geospatial Consortium (OGC) Well-Known Text (WKT)-Darstellung einer geometry-Instanz zurück, die um alle von der Instanz getragenen Z (Höhe)- und M (Measure)-Werte erweitert ist.
  
## <a name="syntax"></a>Syntax  
  
```  
  
.ToString ()  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **nvarchar(max)**  
  
 CLR-Rückgabetyp: **SqlString**  
  
## <a name="remarks"></a>Remarks  
 Diese Methode gibt die Zeichenfolge "NULL" zurück, wenn sie für NULL-Instanzen aufgerufen wird.  
  
 Bei Instanzen, die nicht NULL sind, entspricht diese Methode der Verwendung von `AsTextZM().`.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine `LineString` -Instanz erstellt und mithilfe von `ToString()` eine Textbeschreibung der Instanz abgerufen.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 0 1, 1 0)', 0);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [STAsText &#40;geometry-Datentyp&#41;](../../t-sql/spatial-geometry/stastext-geometry-data-type.md)   
 [Erweiterte Methoden für geometry-Instanzen](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

