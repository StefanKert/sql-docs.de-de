---
title: Lesen und Anzeigen der Setupprotokolldateien von SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- viewing logs
- displaying log files
- Setup [SQL Server], logs
- installation log files [SQL Server]
- installing SQL Server, logs
- errors [SQL Server], Setup
- logs [SQL Server], Setup
ms.assetid: 9d77af64-9084-4375-908a-d90f99535062
caps.latest.revision: 50
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 365c5dca84514169082859900a1a3e065770f358
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37163351"
---
# <a name="view-and-read-sql-server-setup-log-files"></a>Lesen und Anzeigen der Setupprotokolldateien von SQL Server
  Jeder Ausführung von Setup erstellt Protokolldateien mit einem neuen Protokollordner unter %Programme% erstellt\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\. Das Namensformat für mit einem Zeitstempel versehene Protokollordner ist JJJJMMTT_hhmmss. Wenn Setup in einem unbeaufsichtigten Modus ausgeführt wird, werden die Protokolle unter %temp%\sqlsetup*.log erstellt. Alle Dateien in den Protokollordnern werden in der Log\*.cab-Datei im jeweiligen Protokollordner archiviert.  
  
 Eine typische Setupanforderung durchläuft drei Ausführungsphasen:  
  
1.  Überprüfung der allgemeinen Regeln  
  
2.  Komponentenupdate  
  
3.  Vom Benutzer angeforderte Aktion  
  
 In jeder dieser Phasen werden Detail- und Zusammenfassungsprotokolle generiert, wobei je nach Bedarf auch noch zusätzliche Protokolldateien generiert werden. Das Setup wird mindestens dreimal pro vom Benutzer angeforderter Setupaktion aufgerufen.  
  
 Datenspeicherdateien enthalten eine Momentaufnahme vom Zustand aller Konfigurationsobjekte, die vom Setupprozess nachverfolgt werden, und sind bei der Behebung von Konfigurationsfehlern nützlich. Für jede Ausführungsphase werden XML-Dateidumps von Datenspeicherobjekten erstellt. Sie werden in einem eigenen Protokollunterordner unter dem mit einem Zeitstempel versehenen Protokollordner wie folgt gespeichert:  
  
-   Datastore_GlobalRules  
  
-   Datastore_ComponentUpdated  
  
-   Datastore  
  
 In den folgenden Abschnitten werden die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setupprotokolldateien beschrieben.  
  
## <a name="summary-text"></a>Zusammenfassungstext  
  
### <a name="overview"></a>Übersicht  
 In dieser Datei werden die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Komponenten, die beim Setup entdeckt wurden, die Betriebssystemumgebung, die Parameterwerte für die Befehlszeile, wenn diese angegeben wurden, und der allgemeine Status jeder MSI-/MSP-Datei, die ausgeführt wurde, angegeben.  
  
 Das Protokoll ist in folgende Abschnitte unterteilt:  
  
-   Eine allgemeine Zusammenfassung der Ausführung  
  
-   Eigenschaften und Konfiguration des Computers, auf dem das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup ausgeführt wurde  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Produktfeatures  
  
-   Die Beschreibung der Installationsversion und der Installationspaketeigenschaften  
  
-   Laufzeiteingabeeinstellungen, die während der Installation angegeben werden  
  
-   Speicherort der Konfigurationsdatei  
  
-   Details zu den Ausführungsergebnissen  
  
-   Globale Regeln  
  
-   Für das Installationsszenario spezifische Regeln  
  
-   Regeln, bei denen Fehler aufgetreten sind  
  
-   Speicherort der Regelberichtdatei  
  
### <a name="location"></a>Speicherort  
 Es befindet sich unter %Programme%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\.  
  
 Um Fehler in der Textdatei zu finden, die die Zusammenfassung enthält, durchsuchen Sie die Datei nach den Schlüsselwörtern "error" oder "failed".  
  
## <a name="summaryengine-baseyyyymmddhhmmsstxt"></a>Summary_engine-base_YYYYMMDD_HHMMss.txt  
  
### <a name="overview"></a>Übersicht  
 Die summary_engine-Basisdatei ähnelt der Zusammenfassungsdatei und wird während des Hauptworkflows generiert.  
  
### <a name="location"></a>Speicherort  
 Es befindet sich unter %Programme%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\< YYYYMMDD_HHMM >\\.  
  
## <a name="summaryengine-baseyyyymmddhhmmsscomponentupdatetxt"></a>Summary_engine-base_JJJJMMTT_HHMMss_ComponentUpdate.txt  
  
### <a name="overview"></a>Übersicht  
 Die Komponentenupdate-Zusammenfassungsprotokolldatei ähnelt der Zusammenfassungsdatei und wird während des Komponentenupdateworkflows generiert.  
  
### <a name="location"></a>Speicherort  
 Es befindet sich unter %Programme%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\< YYYYMMDD_HHMM >\\.  
  
## <a name="summaryengine-baseversionnumbermmddhhmmssglobalrulestxt"></a>Summary_engine-base_\<VersionNumber>MMDD_HHMMss_GlobalRules.txt  
  
### <a name="overview"></a>Übersicht  
 Die Zusammenfassungsprotokolldatei für die globalen Regeln ähnelt der Zusammenfassungsdatei und wird während des Workflows für allgemeine Regeln generiert.  
  
### <a name="location"></a>Speicherort  
 Es befindet sich unter %Programme%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\< YYYYMMDD_HHMM >\\.  
  
## <a name="detailtxt"></a>Detail.txt  
  
### <a name="overview"></a>Übersicht  
 Die Datei Detail.txt wird für den Hauptworkflow wie Installation oder Upgrade generiert und liefert Einzelheiten zur Ausführung. Die Protokolle in der Datei werden basierend auf dem Zeitpunkt generiert, zu dem die Installationsaktionen aufgerufen wurden. Sie zeigen die Reihenfolge, in der die Aktionen ausgeführt wurden, und ihre Abhängigkeiten.  
  
### <a name="location"></a>Speicherort  
 Es befindet sich unter %Programme%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup  
  
 Bootstrap\Log\\<YYYYMMDD_HHMM>\Detail.txt.  
  
 Wenn während des Setupvorgangs ein Fehler auftritt, wird die Ausnahme oder der Fehler am Ende dieser Datei protokolliert. Um die Fehler zu finden, prüfen Sie daher zunächst das Ende der Datei, und suchen Sie dann nach den Schlüsselwörtern "Fehler" oder "Ausnahme".  
  
## <a name="detailcomponentupdatetxt"></a>Detail_ComponentUpdate.txt  
  
### <a name="overview"></a>Übersicht  
 Die Datei Detail_ComponentUpdate.txt wird für den Komponentenupdateworkflow generiert und ähnelt der Datei Detail.txt.  
  
### <a name="location"></a>Speicherort  
 Es befindet sich unter %Programme%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\< YYYYMMDD_HHMM >\\.  
  
## <a name="detailglobalrulestxt"></a>Detail_GlobalRules.txt  
  
### <a name="overview"></a>Übersicht  
 Die Datei Detail_GlobalRules.txt wird für die Ausführung der globalen Regeln generiert und ähnelt der Datei Detail.txt.  
  
### <a name="location"></a>Speicherort  
 Es befindet sich unter %Programme%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\< YYYYMMDD_HHMM >\\.  
  
## <a name="msi-log-files"></a>MSI-Protokolldateien  
  
### <a name="overview"></a>Übersicht  
 Die MSI-Protokolldateien liefern Details zum Installationspaketprozess. Sie werden durch MSIEXEC während der Installation des angegebenen Pakets generiert.  
  
 Typen von MSI-Protokolldateien:  
  
-   \<Feature>\<Architektur>\_\<Interaktion>.log  
  
-   \<Feature>_\<Architektur>\_\<Sprache>\_\<Interaktion>.log  
  
-   \<Feature>_\<Architektur>\_\<Iteration>\_\<Workflow>.log  
  
### <a name="location"></a>Speicherort  
 Die MSI-Protokolldateien befinden sich unter %Programme%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\< YYYYMMDD_HHMM >\\< Name\>. Log.  
  
 Am Ende der Datei ist eine Zusammenfassung der Ausführung zu finden, die Aufschluss über eventuelle Fehler gibt. Um die Fehler in der MSI-Datei zu finden, suchen Sie nach "value 3". In der Regel sind die Fehler in der Nähe dieser Zeichenfolge zu finden.  
  
## <a name="configurationfileini"></a>ConfigurationFile.ini  
  
### <a name="overview"></a>Übersicht  
 Die Konfigurationsdatei enthält die Eingabeeinstellungen, die während der Installation angegeben werden. Sie kann verwendet werden, um eine Installation neu zu starten, ohne die Einstellungen manuell eingeben zu müssen. Kennwörter für die Konten, die PID und einige Parameter werden jedoch nicht in der Konfigurationsdatei gespeichert. Diese Einstellungen können der Datei entweder hinzugefügt oder über die Befehlszeile oder die Setupbenutzeroberfläche angegeben werden. Weitere Informationen finden Sie unter [Installieren von SQL Server 2014 mithilfe einer Konfigurationsdatei](install-sql-server-using-a-configuration-file.md).  
  
### <a name="location"></a>Speicherort  
 Es befindet sich unter %Programme%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\< YYYYMMDD_HHMM >\\.  
  
## <a name="systemconfigurationcheckreporthtm"></a>SystemConfigurationCheck_Report.htm  
  
### <a name="overview"></a>Übersicht  
 Im Bericht zur Systemkonfigurationsprüfung sind eine kurze Beschreibung für jede ausgeführte Regel sowie der Ausführungsstatus enthalten.  
  
### <a name="location"></a>Speicherort  
 Es befindet sich unter %Programme%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\< YYYYMMDD_HHMM >\\.  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst-wie-Themen für die Installation](../../sql-server/install/installation-how-to-topics.md)   
 [Installieren von SQL Server 2014](install-sql-server.md)  
  
  
