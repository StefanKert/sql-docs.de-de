---
title: MSdbms_datatype_mapping (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSdbms_datatype_mapping_TSQL
- MSdbms_datatype_mapping
dev_langs:
- TSQL
helpviewer_keywords:
- MSdbms_datatype_mapping system table
ms.assetid: 13289a0b-dfb0-4771-ad80-4c5f83cded99
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 13c950a172ddf9b757f82f2cefe1e9a630728d54
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39102798"
---
# <a name="msdbmsdatatypemapping-transact-sql"></a>MSdbms_datatype_mapping (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSdbms_datatype_mapping** Tabelle enthält die zulässigen datentypzuordnungen vom Datentyp in der Source-Datenbank-Managementsystem (DBMS) für eine oder mehrere bestimmte Datentypen im Ziel-DBMS. Diese Tabelle befindet sich in der **Msdb** Datenbank und wird für heterogene Datenbankreplikation verwendet.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**datatype_mapping_id**|**int**|Identifiziert jede eindeutige Datentypzuordnung.|  
|**map_id**|**int**|Identifiziert den Quelldatentyp.|  
|**dest_datatype_id**|**int**|Identifiziert den Zieldatentyp.|  
|**dest_precision**|**bigint**|Definiert die Genauigkeit des Zieldatentyps, ein Wert von NULL bedeutet, dass die Genauigkeit nicht verwendet wird, und den Wert **-1** bedeutet, dass die Genauigkeit des Quelldatentyps verwendet wird.|  
|**dest_scale**|**int**|Definiert die Dezimalstellen des Zieldatentyps, ein Wert von NULL bedeutet, dass die Dezimalstellen nicht verwendet werden, und den Wert **-1** bedeutet, dass die Dezimalstellen des Quelldatentyps verwendet wird.|  
|**dest_length**|**bigint**|Definiert die Länge des Zieldatentyps, ein Wert von NULL bedeutet, dass die Länge nicht verwendet wird, und den Wert **-1** bedeutet, dass die Länge des Quelldatentyps verwendet wird.|  
|**dest_nullable**|**bit**|Gibt an, ob die Zielspalte in der Zuordnung NULL-Werte zulässt. Ein Wert von NULL bedeutet, dass diese Definition nicht erforderlich ist.|  
|**dest_createparams**|**int**|Die Bitmap, die beschreibt, welche Kombination aus Länge, Genauigkeit und Dezimalstellen für den jeweiligen Datentyp anwendbar sind. Sie beinhaltet Folgendes:<br /><br /> **0 x 1** = mit einfacher Genauigkeit.<br /><br /> **0 x 2** = skalieren.<br /><br /> **0 x 4** = Länge.|  
  
## <a name="see-also"></a>Siehe auch  
 [Heterogene Datenbankreplikation](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Angeben von Datentypzuordnungen für einen Oracle-Verleger](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
