---
title: Diagnoseverbindung für Datenbankadministratoren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- server management [SQL Server], connections
- administrator connections [SQL Server]
- ports [SQL Server], DAC
- DAC
- network connections [SQL Server], dedicated administrator
- diagnostic connections [SQL Server]
- connections [SQL Server], dedicated administrator
- ports [SQL Server]
- dedicated administrator connections [SQL Server]
ms.assetid: 993e0820-17f2-4c43-880c-d38290bf7abc
caps.latest.revision: 62
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c30258edc86afd1a4844580553ce6d059edcb279
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37209820"
---
# <a name="diagnostic-connection-for-database-administrators"></a>Diagnoseverbindung für Datenbankadministratoren
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt eine spezielle Diagnoseverbindung für Administratoren bereit, wenn Standardverbindungen zum Server nicht möglich sind. Mit dieser Diagnoseverbindung kann ein Administrator auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zugreifen, um Diagnoseabfragen auszuführen und Probleme zu behandeln, auch wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf Anforderungen von Standardverbindungen nicht antwortet.  
  
 Diese dedizierte Administratorverbindung unterstützt die Verschlüsselung und andere Sicherheitsfunktionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Die DAC lässt den Wechsel des Benutzerkontexts ausschließlich in den eines anderen Administrators zu.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versucht alles, damit die DAC (Dedicated Administrator Connection, dedizierte Administratorverbindung) erfolgreich eine Verbindung herstellt, doch unter extremen Bedingungen ist dies eventuell nicht möglich.  
  
||  
|-|  
|**Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] bis zur [aktuellen Version](http://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].|  
  
## <a name="connecting-with-dac"></a>Herstellen einer dedizierten Administratorverbindung  
 Standardmäßig ist die Verbindung nur von einem Client aus zulässig, der auf dem Server ausgeführt wird. Netzwerkverbindungen sind nur dann zulässig, wenn sie mithilfe der gespeicherten Prozedur „sp_configure“ mit der Option [remote admin connections](remote-admin-connections-server-configuration-option.md)konfiguriert wurden.  
  
 Nur Mitglieder der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Rolle sysadmin können dedizierte Administratorverbindungen (DAC) herstellen.  
  
 Die DAC steht über das **sqlcmd** -Hilfsprogramm für Eingabeaufforderungen mit einem speziellen Administratorschalter (**-A**) zur Verfügung und wird von diesem unterstützt. Weitere Informationen zum Verwenden von **sqlcmd** finden Sie unter [Verwenden von sqlcmd mit Skriptvariablen](../../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md). Sie können auch verbinden, als Präfix voranstellen `admin:`dem Instanznamen im Format **Sqlcmd - Sadmin: *** < Instance_name >.* Sie können auch initiieren, eine dedizierte Administratorverbindung in einem [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Abfrage-Editor durch Herstellen einer Verbindung mit `admin:` \<* Instanzname * >.  
  
## <a name="restrictions"></a>Restrictions  
 Da die DAC nur zum Diagnostizieren von Serverproblemen in seltenen Fällen gedacht ist, bestehen einige Einschränkungen für die Verbindung:  
  
-   Um sicherzustellen, dass Ressourcen für die Verbindung verfügbar sind, ist nur eine DAC pro Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zulässig. Ist bereits eine dedizierte Administratorverbindung aktiv, wird jede weitere Anforderung einer Verbindung über DAC mit Fehler 17810 abgelehnt.  
  
-   Zur Einsparung von Ressourcen lauscht [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] am DAC-Port nur dann, wenn beim Starten das Ablaufverfolgungsflag 7806 angegeben wird.  
  
-   Die DAC versucht zunächst, eine Verbindung zu der Standarddatenbank herzustellen, die dem Anmeldenamen zugeordnet ist. Nach erfolgreichem Verbindungsaufbau können Sie eine Verbindung mit der master-Datenbank herstellen. Wenn die Standarddatenbank offline oder aus anderen Gründen nicht verfügbar ist, wird von der Verbindung der Fehler 4060 zurückgegeben. Die Verbindung kann jedoch hergestellt werden, wenn Sie die Standarddatenbank überschreiben und stattdessen mithilfe des folgenden Befehls eine Verbindung mit der master-Datenbank herstellen:  
  
     **sqlcmd –A –d master**  
  
     Es wird empfohlen, die dedizierte Administratorverbindung mit der master-Datenbank herzustellen, da diese sicher verfügbar ist, wenn die Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] gestartet ist.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verhindert die Ausführung paralleler Abfragen oder Befehle über die DAC. So wird beispielsweise Fehler 3637 generiert, wenn Sie eine der folgenden Anweisungen über die DAC ausführen:  
  
    -   RESTORE  
  
    -   BACKUP  
  
-   Bei einer DAC ist nur die Verfügbarkeit beschränkter Ressourcen sichergestellt. Führen Sie über die DAC keine ressourcenintensiven Abfragen (z. B. eine komplexe Verknüpfung in einer großen Tabelle) oder Abfragen aus, die eine Blockierung verursachen können. Dies trägt dazu bei, zu verhindern, dass vorhandene Serverprobleme durch die DAC verstärkt werden. Zur Vermeidung möglicher Blockierungssituationen müssen Sie ggf. Abfragen, die eine Blockierung verursachen können, möglichst auf momentaufnahmebasierten Isolationsstufen ausführen. Ist dies nicht möglich, sollten Sie die Transaktionsisolationsstufe auf READ UNCOMMITTED festlegen und/oder den LOCK_TIMEOUT-Wert auf eine kurze Zeitspanne, beispielsweise 2000 Millisekunden, festlegen. Dies verhindert, dass die DAC-Sitzung blockiert wird. Abhängig vom Status von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann die DAC-Sitzung jedoch durch ein Latch blockiert werden. Möglicherweise können Sie die DAC-Sitzung mit STRG-C beenden, dies ist jedoch nicht sichergestellt. In diesem Fall ist unter Umständen der Neustart von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]unumgänglich.  
  
-   Um die Konnektivität und die Problembehandlung mit der DAC sicherzustellen, reserviert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] beschränkte Ressourcen für die Verarbeitung von Befehlen, die in der DAC ausgeführt werden. Diese Ressourcen sind in der Regel nur für einfache Diagnose- und Problembehandlungsfunktionen wie die unten aufgeführten ausreichend.  
  
 Obwohl Sie über die DAC theoretisch jede [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung ausführen können, die nicht parallel ausgeführt werden muss, wird dringend empfohlen, nur die folgenden Diagnose- und Problembehandlungsbefehle zu verwenden:  
  
-   Abfragen von dynamischen Verwaltungssichten für grundlegende Diagnosen, wie z. B. sys.dm_tran_locks für den Sperrstatus, sys.dm_os_memory_cache_counters für die Zustandsüberprüfung der Caches sowie sys.dm_exec_requests und sys.dm_exec_sessions für aktive Sitzungen und Anforderungen. Vermeiden Sie dynamische Verwaltungssichten, die ressourcenintensiv sind (beispielsweise durchsucht sys.dm_tran_version_store den vollständigen Versionsspeicher und kann umfangreiche E/A verursachen) oder komplexe Joins verwenden. Informationen zu den Auswirkungen auf die Leistung finden Sie in der Dokumentation der jeweiligen [dynamischen Verwaltungssicht](../../relational-databases/views/views.md).  
  
-   Abfragen von Katalogsichten.  
  
-   Einfache DBCC-Befehle wie DBCC FREEPROCCACHE, DBCC FREESYSTEMCACHE, DBCC DROPCLEANBUFFERS`,` und DBCC SQLPERF. Führen Sie keine ressourcenintensiven Befehle wie **DBCC** CHECKDB, DBCC DBREINDEX oder DBCC SHRINKDATABASE aus.  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] KILL*\<spid>*-Befehl. Abhängig vom Status von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ist der KILL-Befehl nicht immer erfolgreich; dann ist ein Neustart von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]unumgänglich. Es folgen einige allgemeine Richtlinien:  
  
    -   Überprüfen Sie mit der Abfrage `SELECT * FROM sys.dm_exec_sessions WHERE session_id = <spid>`, ob SPID tatsächlich beendet wurde. Wenn keine Zeilen zurückgegeben werden, wurde die Sitzung beendet.  
  
    -   Ist die Sitzung noch vorhanden, sollten Sie überprüfen, ob der Sitzung Tasks zugewiesen sind. Führen Sie dazu die Abfrage `SELECT * FROM sys.dm_os_tasks WHERE session_id = <spid>`aus. Wird der Task dort angezeigt, wird die Sitzung wahrscheinlich gerade beendet. Beachten Sie, dass die Abfrage möglicherweise erhebliche Zeit in Anspruch nimmt und unter Umständen nicht erfolgreich ist.  
  
    -   Enthält die dieser Sitzung zugeordnete sys.dm_os_tasks-Sicht keine Tasks, während die Sitzung nach der Ausführung des KILL-Befehls in sys.dm_exec_sessions verbleibt, bedeutet dies, dass kein Arbeitsthread verfügbar ist. Wählen Sie einen der aktuell ausgeführten Tasks aus (einen Task in der sys.dm_os_tasks-Sicht mit `sessions_id <> NULL`), und beenden Sie die diesem zugeordnete Sitzung, um den Arbeitsthread freizugeben. Beachten Sie, dass das Beenden einer einzelnen Sitzung möglicherweise nicht ausreicht. Unter Umständen müssen Sie mehrere Sitzungen beenden.  
  
## <a name="dac-port"></a>DAC-Port  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lauscht am TCP-Port 1434 (sofern verfügbar) oder einem TCP-Port, der beim Starten von [!INCLUDE[ssDE](../../includes/ssde-md.md)] dynamisch zugewiesen wurde, auf eine DAC. Das Fehlerprotokoll enthält die Nummer des Ports, der von der DAC überwacht wird. Standardmäßig nimmt die DAC-Überwachung nur am lokalen Port Verbindungen an. Ein Codebeispiel zum Aktivieren von Remoteverwaltungsverbindungen finden Sie unter [Remoteadministratorverbindungen (Serverkonfigurationsoption)](remote-admin-connections-server-configuration-option.md).  
  
 Nachdem die Remoteverwaltungsverbindung konfiguriert wurde, wird die DAC-Überwachung aktiviert, ohne dass ein Neustart von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erforderlich ist. Jetzt kann ein Client remote eine DAC herstellen. Sie können die DAC-Überwachung für die Annahme von Remoteverbindungen auch dann aktivieren, wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht reagiert, indem Sie zunächst unter lokaler Verwendung der DAC eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und dann die gespeicherte Prozedur sp_configure ausführen, sodass Verbindungen über Remoteverbindungen angenommen werden.  
  
 In Clusterkonfigurationen ist die DAC standardmäßig deaktiviert. Benutzer können die remote admin connection-Option von sp_configure verwenden, um den Zugriff der DAC-Überwachung auf eine Remoteverbindung zu aktivieren. Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht reagiert und die DAC-Überwachung nicht aktiviert ist, müssen Sie möglicherweise [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] neu starten, um eine Verbindung mit der DAC herzustellen. Deshalb wird empfohlen, die Konfigurationsoption remote admin connections in Clustersystemen zu aktivieren.  
  
 Der DAC-Port wird dynamisch von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] beim Start zugewiesen. Beim Herstellen der Verbindung mit der Standardinstanz vermeidet die DAC die Verwendung einer SSRP-Anforderung ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Resolution Protocol) an den SQL Server-Browser-Dienst. Zunächst wird eine Verbindung über den TCP-Port 1434 hergestellt. Tritt dabei ein Fehler auf, wird ein SSRP-Aufruf ausgegeben, um den Port abzurufen. Falls der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser SSRP-Anforderungen nicht überwacht, gibt die Verbindungsanforderung einen Fehler zurück. Suchen Sie im Fehlerprotokoll nach der Portnummer, die von der DAC überwacht wird. Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für die Annahme von Remoteverwaltungsverbindungen konfiguriert ist, muss die DAC wie folgt mit einer expliziten Portnummer initiiert werden:  
  
 **sqlcmd–Stcp:** *\<server>,\<port>*  
  
 Im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlerprotokoll ist die Portnummer für die DAC aufgelistet, standardmäßig 1434. Ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausschließlich für die Annahme lokaler DAC konfiguriert, müssen Sie die Verbindung mithilfe des Loopbackadapters herstellen. Verwenden Sie dazu folgenden Befehl:  
  
 **Sqlcmd – S127.0.0.1**,`1434`  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel bemerkt ein Administrator, dass der Server `URAN123` nicht reagiert, und möchte das Problem analysieren. Dazu aktiviert der Benutzer das Eingabeaufforderungs-Hilfsprogramm `sqlcmd` und stellt eine Verbindung mit dem Server `URAN123` her. Dabei gibt er den Schalter `-A` an, um die DAC anzuzeigen.  
  
 `sqlcmd -S URAN123 -U sa -P <xxx> –A`  
  
 Jetzt kann der Administrator Abfragen für eine Problemdiagnose ausführen und möglicherweise die nicht reagierenden Sitzungen beenden.  
  
## <a name="related-tasks"></a>Related Tasks  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [Verwenden von sqlcmd mit Skriptvariablen](../../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md)  
  
 [sqlcmd (Hilfsprogramm)](../../tools/sqlcmd-utility.md)  
  
 [SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql)  
  
 [sp_who &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-who-transact-sql)  
  
 [sp_lock &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-lock-transact-sql)  
  
 [KILL &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/kill-transact-sql)  
  
 [DBCC CHECKALLOC &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkalloc-transact-sql)  
  
 [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)  
  
 [DBCC OPENTRAN &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-opentran-transact-sql)  
  
 [DBCC INPUTBUFFER &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-inputbuffer-transact-sql)  
  
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)  
  
 [Dynamische Verwaltungssichten und Funktionen in Verbindung mit Transaktionen &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql)  
  
 [Ablaufverfolgungsflags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)  
  
  
