---
title: Überprüfen einer SQL Server-Installation | Microsoft-Dokumentation
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
- validating installations [SQL Server]
ms.assetid: 1689af50-d2b8-4aa6-8f27-cc7127157fc8
caps.latest.revision: 27
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0ba9a0603e97de67c9bb7ad94acffe4a666d1339
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37291376"
---
# <a name="validate-a-sql-server-installation"></a>Überprüfen einer SQL Server-Installation
  Mithilfe des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Ermittlungsberichts können Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Version sowie die auf dem Computer installierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Funktionen überprüfen. Die **installiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Funktionen** zeigt einen Bericht aller [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], und [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Produkte und Funktionen, werden auf dem lokalen Server installiert werden. Der Bericht zur Ermittlung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Funktionen steht im **-Installationscenter auf der Seite** Tools [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bereit.  
  
 **So führen Sie den Bericht zur Ermittlung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Funktionen aus**  
  
 Rufen Sie das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Installationscenter auf. Zeigen Sie dazu im **Startmenü** auf **Alle Programme**, **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<Versionsname>**, **Konfigurationstools**, und klicken Sie auf **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Installationscenter**. Klicken Sie im linken Navigationsbereich des **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Installationscenter** auf **Tools** und anschließend auf **Bericht zur Ermittlung installierter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Funktionen**, um den Bericht zur Ermittlung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Funktionen auszuführen.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Discovery-Bericht wird in % Programme% gespeichert\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\< letzte Setupsitzung\>.  
  
 Sie können den Ermittlungsbericht auch über die Befehlszeile generieren. Führen Sie "Setup.exe/Action = RunDiscovery" über eine Eingabeaufforderung, wenn Sie hinzufügen "/ Q" oben stehenden Befehlszeile keine Benutzeroberfläche wird angezeigt, aber der Bericht wird noch erstellt werden, in "% ProgramFiles%"\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\< letzte Setupsitzung\>.  
  
## <a name="see-also"></a>Siehe auch  
 [Lesen und Anzeigen der Setupprotokolldateien von SQL Server](view-and-read-sql-server-setup-log-files.md)  
  
  
