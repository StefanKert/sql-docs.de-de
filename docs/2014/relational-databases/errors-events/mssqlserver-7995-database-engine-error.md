---
title: MSSQLSERVER_7995 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 7995 (Database Engine error)
ms.assetid: af6d6322-3cba-43d8-be97-e6ef15f8c933
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 67e6270cdf4f218b90624d510a8ac28255e3da71
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37411409"
---
# <a name="mssqlserver7995"></a>MSSQLSERVER_7995
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|7995|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC2_SYSTEM_CATALOGS_CORRUPT|  
|Meldungstext|'DBNAME'-Datenbank: Konsistenzfehler in Systemkatalogen verhindern die weitere DBCC CHECKNAME-Verarbeitung.|  
  
## <a name="explanation"></a>Erklärung  
 Der DBCC CHECKDB-Prozess umfasst die folgenden drei Phasen:  
  
1.  Zuordnungsprüfungen: Dies entspricht der Ausführung von DBCC CHECKALLOC.  
  
2.  Systemtabellenkonsistenzprüfungen: Dies entspricht der Ausführung von DBCC CHECKTABLE für eine kleine Liste erforderlicher Systembasistabellen.  
  
3.  Vollständige Datenbankkonsistenzprüfungen.  
  
 MSSQLEngine_7995 wird in Phase 2 ausgelöst, um anzugeben, dass von DBCC CHECKDB Fehler gefunden wurden, die vom Befehl nicht repariert werden können, oder dass REPAIR nicht angegeben wurde. DBCC CHECKDB kann Phase 3 nicht fortsetzen, weil entweder in den fraglichen Systembasistabellen die Metadaten für alle Objekte in der Datenbank gespeichert oder die Systembasistabellen beschädigt sind.  
  
## <a name="user-action"></a>Benutzeraktion  
  
### <a name="look-for-hardware-failure"></a>Hardwarefehlersuche  
 Führen Sie eine Hardwarediagnose aus, und beheben Sie alle Probleme. Überprüfen Sie auch das Systemprotokoll und das Anwendungsprotokoll von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows sowie das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlerprotokoll, um festzustellen, ob der Fehler aufgrund eines Hardwarefehlers aufgetreten ist. Beheben Sie alle hardwarebedingten Probleme, die in den Protokollen enthalten sind.  
  
 Lagern Sie verschiedene Hardwarekomponenten aus, um das Problem zu isolieren, falls Beschädigungsprobleme bei permanenten Daten auftreten. Stellen Sie sicher, dass beim System der Schreibcache auf dem Datenträgercontroller nicht aktiviert ist. Wenden Sie sich an Ihren Hardwarehersteller, falls Sie beim Schreibcache das Problem vermuten.  
  
 Letztendlich kann es vorteilhaft sein, wenn Sie zu einem neuen Hardwaresystem wechseln. Der Wechsel kann die Neuformatierung der Laufwerke und eine Neuinstallation des Betriebssystems beinhalten.  
  
### <a name="restore-from-backup"></a>Sicherungswiederherstellung  
 Stellen Sie die Datenbank aus der Sicherung wieder her, wenn das Problem nicht hardwarebezogen ist und eine bekannte intakte Sicherungskopie vorhanden ist.  
  
### <a name="run-dbcc-checkdb"></a>Ausführen von DBCC CHECKDB  
 Führen Sie DBCC CHECKDB ohne eine REPAIR-Klausel aus, um das Ausmaß der Beschädigung festzustellen, falls keine fehlerfreie Sicherung verfügbar ist. DBCC CHECKDB empfiehlt die Verwendung einer REPAIR-Klausel. Führen Sie dann DBCC CHECKDB mit der entsprechenden REPAIR-Klausel aus, um die Beschädigung zu reparieren.  
  
> [!CAUTION]  
>  Wenden Sie sich an Ihren primären Unterstützungsanbieter, bevor Sie diese Anweisung ausführen, wenn Sie nicht sicher sind, inwiefern sich die Verwendung von DBCC CHECKDB mit einer REPAIR-Klausel auf Ihre Daten auswirkt.  
  
 Wenn DBCC CHECKDB mit einer der REPAIR-Klauseln ausgeführt wird und das Problem nicht behebt, wenden Sie sich an Ihren primären Unterstützungsanbieter.  
  
### <a name="results-of-running-repair-options"></a>Ergebnis der Ausführung von REPAIR-Optionen  
 Untersuchen Sie die Liste der Fehler, um festzustellen, was jeweils mit REPAIR erreicht werden kann.  
  
  
