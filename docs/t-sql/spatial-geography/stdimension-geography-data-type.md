---
title: STDimension (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STDimension (geography Data Type)
- STDimension_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STDimension method
ms.assetid: 4368b0f6-0678-4ade-87dc-b43d8b2e8d92
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b5e234bfd63ffe6488641206af3ee6a89a076f4c
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36251302"
---
# <a name="stdimension-geography-data-type"></a>STDimension (geography-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt die maximale Dimension einer **geography**-Instanz zurück  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STDimension ( )  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **int**  
  
 CLR-Rückgabetyp: **SqlInt32**  
  
## <a name="remarks"></a>Remarks  
 STDimension() gibt -1 zurück, wenn die **geography**-Instanz leer ist.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird `STDimension()` verwendet, um eine Tabellenvariable zu erstellen, in der `geography`-Instanzen gespeichert werden. Dann werden eine `Point`-, eine `LineString`- und eine `Polygon`-Instanz eingefügt.  
  
```  
DECLARE @temp table ([name] varchar(10), [geom] geography);  
  
INSERT INTO @temp values ('Point', geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326));  
INSERT INTO @temp values ('LineString', geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326));  
INSERT INTO @temp values ('Polygon', geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326));  
  
SELECT [name], [geom].STDimension() as [dim]  
FROM @temp;  
```  
  
 Im Beispiel werden dann die Dimensionen der einzelnen `geography`-Instanzen zurückgegeben.  
  
|NAME|dim|  
|----------|---------|  
|Point|0|  
|LineString|1|  
|Polygon|2|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [OGC-Methoden für geography-Instanzen](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
