---
title: captured_columns (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- cdc.captured_columns
- cdc.captured_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- cdc.captured_columns
ms.assetid: 7bb4d408-d764-4ef6-802c-f271c8d39c2a
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 144bf49651013b55ec1b515da1ecec156dd375c6
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39103278"
---
# <a name="cdccapturedcolumns-transact-sql"></a>cdc.captured_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt eine Zeile für jede in einer Aufzeichnungsinstanz nachverfolgte Spalte zurück. Standardmäßig werden alle Spalten der Quelltabelle aufgezeichnet. Es können jedoch auch Spalten ein- oder ausgeschlossen werden, wenn die Quelltabelle für Change Data Capture aktiviert ist. Dazu geben Sie eine Spaltenliste an. Weitere Informationen finden Sie unter [Sys. sp_cdc_enable_table &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md).  
  
 Es wird empfohlen, die Sie **die Systemtabellen nicht direkt Abfragen**. Führen Sie stattdessen die [sp_cdc_get_source_columns](../../relational-databases/system-stored-procedures/sys-sp-cdc-get-captured-columns-transact-sql.md) gespeicherte Prozedur.  
   
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID der Quelltabelle, zu der die aufgezeichnete Spalte gehört.|  
|**column_name**|**sysname**|Name der aufgezeichneten Spalte.|  
|**column_id**|**int**|ID der aufgezeichneten Spalte innerhalb der Quelltabelle.|  
|**COLUMN_TYPE**|**sysname**|Typ der aufgezeichneten Spalte.|  
|**column_ordinal**|**int**|Spaltenordnungszahl (1-basiert) in der Änderungstabelle. Die Metadatenspalten in der Änderungstabelle werden ausgeschlossen. Der ersten aufgezeichneten Spalte wird die Ordnungszahl 1 zugewiesen.|  
|**is_computed**|**bit**|Gibt an, dass die aufgezeichnete Spalte eine berechnete Spalte in der Quelltabelle ist.|  
  
## <a name="see-also"></a>Siehe auch  
 [CDC. change_tables &#40;Transact-SQL&#41;](../../relational-databases/system-tables/cdc-change-tables-transact-sql.md)  
  
  
