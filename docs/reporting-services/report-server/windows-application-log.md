---
title: "Windows-Anwendungsprotokoll | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Windows-Anwendungsprotokolle [Reporting Services]"
  - "Protokolle [Reporting Services], Windows-Anwendungsprotokolle"
  - "Anwendungsprotokolle [Reporting Services]"
ms.assetid: 742fd00e-aa6c-4c8a-b58f-c03c489b1699
caps.latest.revision: 32
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 32
---
# Windows-Anwendungsprotokoll
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] schreibt Ereignismeldungen in das Windows-Anwendungsprotokoll. Sie können die in das Anwendungsprotokoll geschriebenen Meldungsinformationen verwenden, um sich über Ereignisse zu informieren, die von den auf dem lokalen System ausgeführten Berichtsserveranwendungen generiert werden.  
  
## Anzeigen von Berichtsserverereignissen  
 Mit der Ereignisanzeige können Sie die Protokolldatei anzeigen und die darin enthaltenen Meldungen filtern. Weitere Informationen zu Ereignisnachrichten finden Sie unter [Fehler- und Ereignisreferenz &#40;Reporting Services&#41;](../../reporting-services/troubleshooting/errors-and-events-reference-reporting-services.md). Weitere Informationen zum Windows-Anwendungsprotokoll oder zur Ereignisanzeige finden Sie in der Produktdokumentation zu Windows.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] stellt drei Ereignisquellen bereit:  
  
-   Berichtsserver (Berichtsserver-Dienst von Windows)  
  
-   Berichts-Manager  
  
-   Prozessor für Zeitplanung und Übermittlung  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ist es nicht möglich, die Anwendungsereignisprotokollierung für einen Berichtsserver zu deaktivieren oder zu steuern, welche Ereignisse protokolliert werden. Das Schema zur Beschreibung der Ereignisprotokollierung für den Berichtsserver kann nicht bearbeitet werden. Deshalb kann das Schema nicht um die Unterstützung benutzerdefinierter Ereignisse erweitert werden.  
  
 In der folgenden Tabelle werden die Ereignistypen beschrieben, die der Berichtsserver in das Anwendungsereignisprotokoll schreibt.  
  
|Ereignistyp|Description|  
|----------------|-----------------|  
|Informationen|Ein Ereignis, das einen erfolgreichen Vorgang beschreibt (z. B. das Starten des Berichtsserverdienstes).|  
|Warnung|Ein Ereignis, das auf ein potenzielles Problem hinweist (z. B. unzureichenden Speicherplatz).|  
|Fehler|Ein Ereignis, das ein erhebliches Problem beschreibt (z. B., dass der Dienst nicht gestartet wurde).|  
|Erfolgsüberwachung|Ein Sicherheitsereignis, das eine erfolgreiche Anmeldung beschreibt.|  
|Fehlerüberwachung|Ein Ereignis, das beim Fehlschlagen eines Anmeldeversuchs protokolliert wird.|  
  
## Siehe auch  
 [Reporting Services-Protokolldateien und Quellen](../../reporting-services/report-server/reporting-services-log-files-and-sources.md)   
 [Fehler- und Ereignisreferenz &#40;Reporting Services&#41;](../../reporting-services/troubleshooting/errors-and-events-reference-reporting-services.md)  
  
  