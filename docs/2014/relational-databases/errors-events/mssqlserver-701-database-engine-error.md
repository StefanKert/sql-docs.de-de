---
title: MSSQLSERVER_701 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 701 (Database Engine error)
ms.assetid: 3b975000-63a1-43c2-a40f-89d0a8a36bef
caps.latest.revision: 18
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1f54741e4962663b174b9f80bb27f0e52580ec26
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37421879"
---
# <a name="mssqlserver701"></a>MSSQLSERVER_701
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|701|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|NOSYSMEM|  
|Meldungstext|Nicht genügend Systemarbeitsspeicher vorhanden, um diese Abfrage auszuführen.|  
  
## <a name="explanation"></a>Erklärung  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] konnte nicht genügend Arbeitsspeicher zuordnen, um die Abfrage auszuführen. Dies kann mehrere Ursachen haben, einschließlich der Betriebssystemeinstellungen, der Verfügbarkeit des physischen Arbeitsspeichers oder der Arbeitsspeicherbegrenzung der aktuellen Arbeitsauslastung. In den meisten Fällen ist die Transaktion, die den Fehler erzeugt hat, nicht die Ursache für den Fehler.  
  
 Diagnoseabfragen, wie beispielsweise DBCC-Anweisungen, erzeugen möglicherweise einen Fehler, da dem Server nicht genügend Arbeitsspeicher zur Verfügung steht.  
  
 Timeout beim Warten auf die Arbeitsspeicherressourcen für die Abfrageausführung im Ressourcenpool 'default' (257).  
  
## <a name="user-action"></a>Benutzeraktion  
 Wenn Sie keine Ressourcenkontrolle verwenden, empfehlen wir, dass Sie den gesamten Serverstatus und die Auslastung oder die Ressourcenpooleinstellungen bzw. Einstellungen für Arbeitsauslastungsgruppen überprüfen.  
  
 In der folgenden Liste werden allgemeine Schritte erläutert, die bei der Problembehandlung von Arbeitsspeicherfehlern helfen:  
  
1.  Überprüfen Sie, ob andere Anwendungen oder Dienste Arbeitsspeicher auf dem Server beanspruchen. Rekonfigurieren Sie weniger kritische Anwendungen oder Dienste, damit sie weniger Speicher beanspruchen.  
  
2.  Starten Sie die Sammlung der Leistungsindikatoren für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **: Puffer-Manager**, **SQL Server: Speicher-Manager**.  
  
3.  Überprüfen Sie die folgenden SQL Server-Speicherkonfigurationsparameter:  
  
    -   **Max. Serverarbeitsspeicher**  
  
    -   **Min. Serverarbeitsspeicher**  
  
    -   **Min. Arbeitsspeicher pro Abfrage**  
  
     Achten Sie auf ungewöhnliche Einstellungen. Berichtigen Sie sie bei Bedarf. Konto für erhöhte Arbeitsspeicheranforderungen. Die Standardeinstellungen werden unter "Festlegen von Serverkonfigurationsoptionen" in der SQL Server-Onlinedokumentation aufgeführt.  
  
4.  Verfolgen Sie die Ausgabe von DBCC MEMORYSTATUS und deren Veränderungen beim Anzeigen der Fehlermeldungen.  
  
5.  Überprüfen Sie die Arbeitsauslastung (z. B. Anzahl gleichzeitiger Sitzungen, derzeit ausgeführte Abfragen).  
  
 Durch die folgenden Aktionen kann [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mehr Arbeitsspeicher zur Verfügung gestellt werden:  
  
-   Wenn andere Anwendungen als [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Ressourcen verbrauchen, versuchen Sie, diese Anwendungen zu beenden, oder führen Sie sie auf einem separaten Server aus. Dadurch fällt der Mangel an externem Arbeitsspeicher weg.  
  
-   Wenn Sie **Max. Serverarbeitsspeicher**  konfiguriert haben, erhöhen Sie dessen Wert.  
  
 Führen Sie die folgenden DBCC-Befehle aus, um mehrere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Speichercaches freizugeben.  
  
-   DBCC FREESYSTEMCACHE  
  
-   DBCC FREESESSIONCACHE  
  
-   DBCC FREEPROCCACHE  
  
 Wenn das Problem weiterhin besteht, müssen Sie weitere Untersuchungen ausführen und möglicherweise die Arbeitsauslastung reduzieren.  
  
  
