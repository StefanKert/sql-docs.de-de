---
title: MSSQLSERVER_17883 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 17883 (Database Engine error)
ms.assetid: adaf1c04-e397-4a69-90b8-9353a37277ea
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8f1c7f6ae0452c34f8739b97cdeb16b363de7471
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
ms.locfileid: "34321561"
---
# <a name="mssqlserver17883"></a>MSSQLSERVER_17883
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|17883|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SRV_SCHEDULER_NONYIELDING|  
|Meldungstext|Prozess %ld:%ld:%ld (0x%lx) Arbeitsthread 0x%p stellt im Zeitplanungsmodul %ld kein Ergebnis bereit. Threaderstellungszeit: %I64d. Ungefähre Thread-CPU-Belegung: Kernel %I64d Millisek., Benutzer %I64d Millisek. Prozessnutzung %d%%. Leerlauf des Systems: %d%%. Intervall: % I64d Millisek.|  
  
## <a name="explanation"></a>Erklärung  
Kennzeichnet ein mögliches Problem mit einem Thread, der in einem Zeitplanungsmodul kein Ergebnis bereitstellt.  Die Ursache könnte ein Programmfehler in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sein. Das Problem kann auch dadurch verursacht werden, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht genug Zyklen für die Ausführung abruft.  Dieser Fehler könnte behoben werden, wenn der Thread Ergebnisse bereitstellt.  
  
## <a name="user-action"></a>Benutzeraktion  
Bei übermäßiger Last im System reduzieren Sie die Last, wenden Sie sich andernfalls an Microsoft Support Services.  
  
