---
title: Broker:Message Classify-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Broker:Message Classify event class
ms.assetid: e51f3351-1239-4c41-b87c-1dd86968e027
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6097a06f1a239dc6e3af181ba983c5575567cbbc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37225612"
---
# <a name="brokermessage-classify-event-class"></a>Broker:Message Classify-Ereignisklasse
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generiert ein **Broker:Message Classify** -Ereignis, wenn Service Broker das Routing für eine Nachricht bestimmt.  
  
## <a name="brokermessage-classify-event-class-data-columns"></a>Datenspalten der Broker:Message Classify-Ereignisklasse  
  
|Datenspalte|Datentyp|Description|Spaltennummer|Filterbar|  
|-----------------|---------------|-----------------|-------------------|----------------|  
|**ApplicationName**|**nvarchar**|Der Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|ja|  
|**ClientProcessID**|**int**|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn die Clientprozess-ID durch den Client bereitgestellt wird.|9|ja|  
|**DatabaseID**|**int**|Die ID der Datenbank, die durch die USE *database* -Anweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE *database* -Anweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die **ServerName** -Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|ja|  
|**EventClass**|**int**|Der Typ der aufgezeichneten Ereignisklasse. Für **Broker:Message Classify** lautet der Typ immer **141**.|27|nein|  
|**EventSequence**|**int**|Die Sequenznummer für dieses Ereignis.|51|nein|  
|**EventSubClass**|**nvarchar**|Der Typ der Ereignisunterklasse, der weitere Informationen zu jeder Ereignisklasse liefert. Diese Spalte kann die folgenden Werte enthalten:<br /><br /> **Lokal**: Die ausgewählte Route hat die Adresse LOCAL.<br /><br /> **Remote**: die ausgewählte Route hat eine andere Adresse als LOCAL.<br /><br /> **Verzögert**: die Nachricht wird verzögert, weil die Weiterleitung deaktiviert ist oder weil keine entsprechende Route vorhanden ist.|21|ja|  
|**FileName**|**nvarchar**|Der Dienstname, an den die Nachricht weitergeleitet wird.|36|nein|  
|**GUID**|**uniqueidentifier**|Die Konversations-ID des Dialogs. Dieser Bezeichner wird als Teil der Nachricht übertragen und von beiden Seiten der Konversation gemeinsam verwendet.|54|nein|  
|**HostName**|**nvarchar**|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname durch den Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|ja|  
|**IsSystem**|**int**|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|nein|  
|**LoginSid**|**image**|Die Sicherheits-ID (SID, Security Identification Number) des angemeldeten Benutzers. Die SID ist für jede Anmeldung beim Server eindeutig.|41|ja|  
|**NTDomainName**|**nvarchar**|Die Windows-Domäne, der der Benutzer angehört.|7|ja|  
|**NTUserName**|**nvarchar**|Der Name des Benutzers, der Besitzer der Verbindung ist, die dieses Ereignis generiert hat.|6|ja|  
|**OwnerName**|**nvarchar**|Der Brokerbezeichner, an den die Nachricht weitergeleitet wird.|37|nein|  
|**RoleName**|**nvarchar**|Gibt an, ob die Nachricht aus dem Netzwerk empfangen wurde oder ob sie aus dieser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz stammt.|38|nein|  
|**ServerName**|**nvarchar**|Der Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , für die eine Ablaufverfolgung ausgeführt wird.|26|nein|  
|**SPID**|**int**|Die Serverprozess-ID, die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dem Prozess zugewiesen wurde, der diesem Client zugeordnet ist.|12|ja|  
|**Startzeit**|**datetime**|Der Zeitpunkt, zu dem das Ereignis begonnen hat, falls verfügbar.|14|ja|  
|**TargetUserName**|**nvarchar**|Die Netzwerkadresse des nächsten Hopbrokers.|39|nein|  
|**TransactionID**|**bigint**|Die vom System zugewiesene ID der Transaktion.|4|nein|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
