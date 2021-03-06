---
title: dm_os_sys_memory (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_os_sys_memory
- sys.dm_os_sys_memory_TSQL
- sys.dm_os_sys_memory
- dm_os_sys_memory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_sys_memory dynamic management view
ms.assetid: 1ca58814-1caa-44c1-b307-ff0bdcbbef62
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d7380f47ae405a7fda1bd30cb464cf60bee737a7
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43077083"
---
# <a name="sysdmossysmemory-transact-sql"></a>sys.dm_os_sys_memory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Gibt Arbeitsspeicherinformationen vom Betriebssystem zurück.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] durch begrenzt ist, und reagiert auf externen speicherbedingungen auf der Betriebssystemebene und die physischen Grenzen der zugrunde liegenden Hardware. Die Ermittlung des Gesamtsystemstatus ist deshalb eine wichtige Komponente zur Auswertung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Speicherauslastung.  
  
> [!NOTE]  
>  Aufrufen von [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] oder [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], verwenden Sie den Namen **sys.dm_pdw_nodes_os_sys_memory**.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**total_physical_memory_kb**|**bigint**|Physischer Gesamtspeicher in Kilobytes (KB), der dem Betriebssystem zur Verfügung steht.|  
|**available_physical_memory_kb**|**bigint**|Verfügbarer physischer Arbeitsspeicher in KB.|  
|**total_page_file_kb**|**bigint**|Die vom Betriebssystem gemeldete Commitgrenze in KB.|  
|**available_page_file_kb**|**bigint**|Gesamtangabe für den in der Auslagerungsdatei nicht genutzten Speicher in KB.|  
|**system_cache_kb**|**bigint**|Gesamter Arbeitsspeicher im Systemcache in KB.|  
|**kernel_paged_pool_kb**|**bigint**|Gesamtgröße des ausgelagerten Kernelpools in KB.|  
|**kernel_nonpaged_pool_kb**|**bigint**|Gesamtgröße des nicht ausgelagerten Kernelpools in KB.|  
|**system_high_memory_signal_state**|**bit**|Benachrichtigung zum Systemstatus: Speicherressourcen sind ausreichend. Ein Wert von 1 gibt an, dass das Signal für ausreichende Speicherressourcen von Windows festgelegt wurde. Weitere Informationen finden Sie unter [CreateMemoryResourceNotification](http://go.microsoft.com/fwlink/?LinkId=82427) in der MSDN Library.|  
|**system_low_memory_signal_state**|**bit**|Benachrichtigung zum Systemstatus: Speicherressourcen sind nicht ausreichend. Ein Wert von 1 gibt an, dass das Signal für nicht ausreichende Speicherressourcen von Windows festgelegt wurde. Weitere Informationen finden Sie unter [CreateMemoryResourceNotification](http://go.microsoft.com/fwlink/?LinkId=82427) in der MSDN Library.|  
|**system_memory_state_desc**|**nvarchar(256)**|Beschreibung des Speicherstatus. Siehe Tabelle unten.|  
|**pdw_node_id**|**int**|**Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Der Bezeichner für den Knoten, dem auf diesem Verteilungspunkt befindet.|  
  
|Bedingung|value|  
|---------------|-----------|  
|system_high_memory_signal_state = 1<br /><br /> - und<br /><br /> System_low_memory_signal_state = 0|Ausreichend physischer Speicher verfügbar|  
|System_high_memory_signal_state = 0<br /><br /> - und<br /><br /> system_low_memory_signal_state = 1|Nicht ausreichend physischer Speicher verfügbar|  
|System_high_memory_signal_state = 0<br /><br /> - und<br /><br /> System_low_memory_signal_state = 0|Konstante physische Speicherauslastung|  
|system_high_memory_signal_state = 1<br /><br /> - und<br /><br /> system_low_memory_signal_state = 1|Physischer Speicherstatus befindet sich im Übergang.<br /><br /> Die Signale für ausreichenden und nicht ausreichenden Speicher dürfen nicht gleichzeitig aktiviert sein. Kurzfristige Änderungen auf Betriebssystemebene können jedoch dazu führen, dass eine Benutzermodusanwendung beide Werte als aktiviert betrachtet. Werden beide Signale als aktiviert dargestellt, wird dies als Übergangsstatus interpretiert.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
## <a name="see-also"></a>Siehe auch  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Dynamische Verwaltungssichten in Verbindung mit SQL Server-Betriebssystem &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


