---
title: "SQL Server-XTP Garbage Collection | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 64ae91e5-b420-44b4-af1a-f8bca83d7f41
caps.latest.revision: 8
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 8
---
# SQL Server-XTP Garbage Collection
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Das SQL Server-XTP-Leistungsobjekt für die Garbage Collection enthält Leistungsindikatoren für die Garbage Collection des In-Memory-OLTP-Moduls.  
  
 In dieser Tabelle werden die Leistungsindikatoren für die **SQL Server XTP Garbage Collection** beschrieben.  
  
|Leistungsindikator|Beschreibung|  
|-------------|-----------------|  
|**Dusty-Corner-Scanwiederholungen/s (durch GC ausgegeben)**|Die durchschnittliche Anzahl von Scanwiederholungen aufgrund von Schreibkonflikten während Dusty-Corner-Sweep-Vorgängen, die pro Sekunde durch die Garbage Collection ausgegeben werden. Dieser Leistungsindikator befindet sich auf einer sehr niedrigen Ebene und dient nicht der Verwendung durch Kunden.|  
|**Arbeitselemente des GC-Hauptthreads/s**|Die Anzahl an Arbeitselementen, die vom GC-Hauptthread verarbeitet werden.|  
|**Parallele GC-Arbeitselemente/s**|Die Häufigkeit, mit der ein paralleler Thread ein GC-Arbeitselement ausgeführt hat.|  
|**Verarbeitete Zeilen/s**|Die durchschnittliche Anzahl von Zeilen, die pro Sekunde von der Garbage Collection verarbeitet werden.|  
|**Verarbeitete Zeilen/s (erste in Bucket und entfernt)**|Die durchschnittliche Anzahl der pro Sekunde von der Garbage Collection verarbeiteten Zeilen, die sich zuerst im entsprechenden Hashbucket befanden und sofort entfernt werden konnten.|  
|**Verarbeitete Zeilen/s (erste in Bucket)**|Die durchschnittliche Anzahl der pro Sekunde verarbeiteten Zeilen, die sich zuerst im entsprechenden Hashbucket befanden.|  
|**Verarbeitete Zeilen/s (zum Aufheben der Verknüpfung markiert)**|Die durchschnittliche Anzahl der pro Sekunde von der Garbage Collection verarbeiteten Zeilen, die bereits für das Aufheben der Verknüpfung markiert waren.|  
|**Verarbeitete Zeilen/s (kein Sweep erforderlich)**|Die durchschnittliche Anzahl der pro Sekunde von der Garbage Collection verarbeiteten Zeilen, für die kein Dusty-Corner-Sweep-Vorgang erforderlich ist.|  
|**Entfernte nach Sweep abgelaufene Zeilen/s**|Die durchschnittliche Anzahl der pro Sekunde abgelaufenen Zeilen, die bei Dusty-Corner-Sweep-Vorgängen entfernt werden.|  
|**Berührte nach Sweep abgelaufene Zeilen/s**|Die durchschnittliche Anzahl der abgelaufenen Zeilen, die pro Sekunde bei Dusty-Corner-Sweep-Vorgängen berührt werden.|  
|**Berührte nach Sweep ablaufende Zeilen/s**|Die durchschnittliche Anzahl ablaufender Zeilen, die pro Sekunde bei Dusty-Corner-Sweep-Vorgängen berührt werden.|  
|**Berührte Sweepzeilen/s**|Die durchschnittliche Anzahl der Zeilen, die pro Sekunde bei Dusty-Corner-Sweep-Vorgängen berührt werden.|  
|**Gestartete Sweep-Scans/s**|Die durchschnittliche Anzahl der pro Sekunde gestarteten Dusty-Corner-Sweep-Scans.|  
  
## Siehe auch  
 [Leistungsindikatoren für SQL Server XTP &#40;In-Memory-OLTP&#41;](../../relational-databases/performance-monitor/sql-server-xtp-in-memory-oltp-performance-counters.md)  
  
  