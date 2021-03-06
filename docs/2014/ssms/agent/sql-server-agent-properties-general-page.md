---
title: SQL Server-Agent-Eigenschaften (Seite Allgemein)|Microsoft-Dokumente
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.general.f1
ms.assetid: b51601e9-5454-43c6-bb5e-24eb2ff043c8
caps.latest.revision: 19
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 05e256ce957a83e07038ecec453b5b4b8b12f4e5
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43815566"
---
# <a name="sql-server-agent-properties-general-page"></a>SQL Server-Agent-Eigenschaften (Seite Allgemein)
  Mithilfe dieser Seite können Sie die allgemeinen Eigenschaften des [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienstes anzeigen und ändern.  
  
## <a name="options"></a>Tastatur  
 **Dienststatus**  
 Zeigt den aktuellen Status des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienstes an.  
  
 **SQL Server nach unerwartetem Beenden automatisch neu starten**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent startet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] neu, wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unerwartet beendet wird.  
  
 **SQL Server-Agent nach unerwartetem Beenden automatisch neu starten**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] startet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent neu, wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent unerwartet beendet wird.  
  
 **Filename**  
 Geben Sie den Dateinamen für das Fehlerprotokoll an.  
  
 **...**  
 Mit dieser Schaltfläche können Sie nach der Fehlerprotokolldatei suchen.  
  
 **Meldungen zur Ablaufverfolgung einschließen**  
 Meldungen zur Ablaufverfolgung werden in das Fehlerprotokoll eingeschlossen. Meldungen zur Ablaufverfolgung stellen detaillierte Informationen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Vorgängen bereit. Deshalb benötigt die Protokolldatei mehr Datenträgerspeicherplatz, wenn diese Option ausgewählt ist. Diese Option sollte nur bei der Behandlung eines Problems ausgewählt werden, bei dem der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent eine Rolle spielt.  
  
 **OEM-Datei schreiben**  
 Speichert die Fehlerprotokolldatei als Nicht-Unicode-Datei. Dadurch wird der für die Protokolldatei erforderliche Datenträgerspeicherplatz reduziert. Meldungen, die Unicode enthalten, können jedoch schwieriger lesbar sein, wenn diese Option aktiviert ist.  
  
 **NET SEND-Empfänger**  
 Geben Sie den Namen eines Operators ein, der NET SEND-Benachrichtigungen von Meldungen empfängt, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent in die Protokolldatei schreibt.  
  
## <a name="see-also"></a>Siehe auch  
 [Operatoren](operators.md)   
 [SQL Server-Agent-Fehlerprotokoll](sql-server-agent-error-log.md)  
  
  
