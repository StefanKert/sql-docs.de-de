---
title: SQL Server, Allgemeine Statistik-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:General Statistics
- General Statistics object
ms.assetid: c738e549-d7e7-4211-9ec3-064ac140af7c
caps.latest.revision: 24
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 48b8df37c64ea017445f1e44cd6e03603708fa86
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43820756"
---
# <a name="sql-server-general-statistics-object"></a>SQL Server, Allgemeine Statistik-Objekt
  Das **SQLServer:Allgemeine Statistiken** -Objekt in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt Leistungsindikatoren bereit, mit denen Sie die allgemeine serverweite Aktivität überwachen können, wie etwa die Anzahl von aktuellen Verbindungen und die Anzahl von Benutzern, die pro Sekunde eine Verbindung mit Computern, die eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausführen, herstellen oder trennen. Dies ist vor allem bei großen OLTP-Systemen (Online Transaction Processing, Onlinetransaktionsverarbeitung) sehr nützlich, wenn viele Clients eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]herstellen oder trennen.  
  
 In dieser Tabelle werden die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **-Leistungsindikatoren von** beschrieben.  
  
|Allgemeine Statistik-Leistungsindikatoren von SQL Server|Description|  
|--------------------------------------------|-----------------|  
|**Aktive temporäre Tabellen**|Anzahl der verwendeten temporären Tabellen/Tabellenvariablen|  
|**Connection Resets/Sek**|Gesamtzahl von Anmeldungen vom Verbindungspool aus.|  
|**Verzögertes Löschen von Ereignisbenachrichtigungen**|Anzahl der Ereignisbenachrichtigungen, die von einem Systemthread gelöscht werden sollen|  
|**Authentifizierte HTTP-Anforderungen**|Anzahl der authentifizierten HTTP-Anforderungen, die pro Sekunde gestartet werden|  
|**Logische Verbindungen**|Anzahl der logischen Verbindungen mit dem System<br /><br /> Der Hauptzweck von logischen Verbindungen besteht darin, MARS-Anforderungen (Multiple Active Result Sets) zu verarbeiten. Bei MARS-Anforderungen können mehrere logische Verbindungen für eine physische Verbindung vorhanden sein, wenn eine Anwendung eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]herstellt.<br /><br /> Wenn MARS nicht verwendet wird, ist das Verhältnis zwischen physischen und logischen Verbindungen 1:1. Daher erhöht sich die Anzahl der logischen Verbindungen um jeweils 1, wenn eine Anwendung eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]herstellt.|  
|**Anmeldungen/Sekunde**|Gesamtanzahl der gestarteten Anmeldungen pro Sekunden. Dieser Leistungsindikator schließt keine Verbindungen in einem Pool ein.|  
|**Abmeldungen/Sekunde**|Gesamtanzahl der Abmeldevorgänge, die pro Sekunde gestartet wurden|  
|**MARS-Deadlocks**|Anzahl der erkannten MARS-Deadlocks|  
|**Nicht atomare Ergebnisrate**|Anzahl der nicht atomaren Ergebnisse pro Sekunde|  
|**Blockierte Prozesse**|Anzahl der zurzeit blockierten Prozesse|  
|**Leere SOAP-Anforderungen**|Anzahl der leeren SOAP-Anforderungen, die pro Sekunde gestartet werden|  
|**SOAP-Methodenaufrufe**|Anzahl der SOAP-Methodenaufrufe, die pro Sekunde gestartet werden|  
|**Initiierungsanforderungen für SOAP-Sitzungen**|Anzahl der pro Sekunde gestarteten Initiierungsanforderungen für SOAP-Sitzungen|  
|**Beendigungsanforderungen für SOAP-Sitzungen**|Anzahl der pro Sekunde gestarteten Beendigungsanforderungen für SOAP-Sitzungen|  
|**SOAP-SQL-Anforderungen**|Anzahl der SOAP-SQL-Anforderungen, die pro Sekunde gestartet werden|  
|**SOAP-WSDL-Anforderungen**|Anzahl der pro Sekunde gestarteten SOAP-WSDL-Anforderungen|  
|**Erstellungsrate für temporäre Tabellen**|Anzahl der temporären Tabellen/Tabellenvariablen, die pro Sekunde erstellt werden|  
|**Temporäre Tabellen zum Löschen**|Anzahl der temporären Tabellen/Tabellenvariablen, die durch den Cleanupsystemthread gelöscht werden|  
|**Benachrichtigungswarteschlange der Ablaufverfolgungsereignisse**|Anzahl der Benachrichtigungsinstanzen von Ablaufverfolgungsereignissen in der internen Warteschlange, die durch Service Broker gesendet werden sollen|  
|**Transaktionen**|Anzahl der Transaktionseintragungen (lokal, über DTC und gebunden)|  
|**Benutzerverbindungen**|Zählt die Anzahl der Benutzer, die zurzeit mit SQL Server verbunden sind|  
  
## <a name="see-also"></a>Siehe auch  
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](monitor-resource-usage-system-monitor.md)  
  
  
