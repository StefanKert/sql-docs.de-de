---
title: trace_events (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- trace_events_TSQL
- trace_events
- sys.trace_events
- sys.trace_events_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.trace_events catalog view
ms.assetid: e7d2c5df-0e17-4e94-9d41-d36c7ee60662
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 72ef4773d669017da99ca5c7531f768d7bef2bd6
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43032623"
---
# <a name="systraceevents-transact-sql"></a>sys.trace_events (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **trace_events** -Katalogsicht enthält eine Liste mit allen SQL-Ablaufverfolgungsereignisse. Diese Ablaufverfolgungsereignisse ändern sich für eine bestimmte Version von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] nicht.  
  
> **WICHTIG!** [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwenden Sie stattdessen die Katalogsichten für erweiterte Ereignisse.  
  
 Weitere Informationen zu diesen Ablaufverfolgungsereignissen finden Sie unter [SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md).  
  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**trace_event_id**|**smallint**|Eindeutige ID des Ereignisses. Diese Spalte wird auch in der **trace_event_bindings** und **trace_subclass_values** Katalogsichten.|  
|**category_id**|**smallint**|Kategorie-ID des Ereignisses. Diese Spalte wird auch in der **Sys. trace_categories** -Katalogsicht angezeigt.|  
|**name**|**nvarchar(128)**|Eindeutiger Name dieses Ereignisses. Dieser Parameter ist nicht lokalisiert.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten für Objekte &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [sys.traces &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-traces-transact-sql.md)   
 [sys.trace_categories &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-categories-transact-sql.md)   
 [sys.trace_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-columns-transact-sql.md)   
 [sys.trace_event_bindings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-event-bindings-transact-sql.md)   
 [trace_subclass_values &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-subclass-values-transact-sql.md)  
  
  
