---
title: Sys.pdw_table_distribution_properties (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 639a7475-7c92-41e0-a8ab-ad630eb5aea3
caps.latest.revision: "9"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4b0c8b3b637fbf46edb599e6ab39804ec16bac8b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2017
---
# <a name="syspdwtabledistributionproperties-transact-sql"></a>Sys.pdw_table_distribution_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Enthält Verteilungsinformationen zur für Tabellen.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|**object_id**|**int**|Die ID der Tabelle, für welche, die drei Eigenschaften angegeben wurden.||  
|**distribution_policy**|**tinyint**|0 = NICHT DEFINIERT<br /><br /> 1 = KEINE<br /><br /> 2 = HASH<br /><br /> 3 = REPLIZIERT<br /><br /> 4 = ROUND_ROBIN|REPLICATE gilt nur für [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].|  
|**distribution_policy_desc**|**nvarchar(60)**|NICHT DEFINIERT IST, NONE, WIRD DER HASHWERT REPLIZIEREN, SEGMENTED_HEAP|[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]Gibt zurück, HASH oder REPLICATE.|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Datawarehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  