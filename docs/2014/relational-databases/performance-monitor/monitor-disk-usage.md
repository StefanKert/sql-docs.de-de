---
title: Überwachen der Datenträgerverwendung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- database monitoring [SQL Server], disk usage
- disks [SQL Server]
- monitoring performance [SQL Server], disk usage
- server performance [SQL Server], disk usage
- monitoring [SQL Server], disk activity
- excess paging [SQL Server]
- tuning databases [SQL Server], disk usage
- I/O [SQL Server], monitoring
- disks [SQL Server], monitoring activity
- isolating disk activity [SQL Server]
- database performance [SQL Server], disk usage
- monitoring server performance [SQL Server], disk usage
ms.assetid: 1525449c-ea7d-4222-b294-1ba1fe99c9ac
caps.latest.revision: 22
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f426010dadac166d1fb946f51d4e48e23b62fe9a
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43817556"
---
# <a name="monitor-disk-usage"></a>Überwachen der Datenträgerverwendung
  Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet Aufrufe für die Microsoft Windows-Betriebssystemeingabe/-ausgabe, um Lese- und Schreibvorgänge auf dem Datenträger auszuführen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwaltet wann und wie Datenträger-E/A ausgeführt wird, aber das Windows-Betriebssystem führt die zugrunde liegenden E/A-Vorgänge aus. Das E/A-Teilsystem umfasst Systembus, Datenträgercontrollerkarten, Datenträger, Bandlaufwerke, CD-ROM-Laufwerk und zahlreiche andere E/A-Geräte. Datenträger-E/A ist häufig die Ursache von Engpässen in einem System.  
  
 Die Überwachung der Datenträgeraktivitäten ist auf zwei Bereiche konzentriert:  
  
-   Überwachen der Datenträger-E/A und Erkennen von zu häufigem Auslagern  
  
-   Isolieren der Datenträgeraktivitäten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
 Weitere Informationen finden Sie unter [Überwachen der Datenträgernutzung](http://social.technet.microsoft.com/wiki/contents/articles/monitoring-disk-usage.aspx)  
  
  
