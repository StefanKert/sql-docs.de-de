---
title: Integrieren von Reporting Services mithilfe der ReportViewer-Steuerelemente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ReportViewer controls
- integrating reports [Reporting Services]
ms.assetid: 3ba47fb4-73a9-4059-89fd-329adebe94a8
caps.latest.revision: 23
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 0d8ecc6116b5000c1db7100abf4ea4db5155ca7f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37317990"
---
# <a name="integrating-reporting-services-using-the-reportviewer-controls"></a>Integrieren von Reporting Services mit den ReportViewer-Steuerelementen
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] bietet zwei ReportViewer-Steuerelemente berichtanzeigefunktionen in Ihre Anwendungen integrieren. Es gibt eine Version für Windows Forms-Anwendungen und eine für WebForms-Anwendungen. Jedes Steuerelement verfügt über ähnliche Funktionen, wurde jedoch im Hinblick auf deren individuelle Umgebung konzipiert. Beide Steuerelemente können Berichte verarbeiten, die auf einem Berichtsserver bereitgestellt (Remoteverarbeitungsmodus) oder auf einen Computer kopiert wurden, auf dem [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nicht installiert ist (lokaler Verarbeitungsmodus).  
  
 DAs ReportViewer-Steuerelement enthält keine integrierte Unterstützung für dynamische Anpassung an verschiedene Geräte mit unterschiedlichen Bildschirmauflösungen.  
  
## <a name="remote-processing-mode"></a>Remoteverarbeitungsmodus  
 Der Remoteverarbeitungsmodus ist die bevorzugte Methode für die Anzeige von Berichten, die auf einen Berichtsserver übertragen wurden. Der Remoteverarbeitungsmodus bietet folgende Vorteile:  
  
-   Remoteverarbeitung ist eine optimierte Lösung für die Ausführung von Berichten, da der Bericht vom Berichtsserver verarbeitet wird.  
  
-   Da die gesamte Verarbeitung vom Berichtsserver gehandhabt wird, kann eine Berichtsanforderung von verschiedenen Berichtsservern in einer Anwendung für horizontales Skalieren oder auf einem Server mit mehreren Prozessoren für zentrales Skalieren verarbeitet werden.  
  
 Außerdem können im Remotemodus ausgeführte Berichte die kompletten Funktionen des Berichtsservers nutzen, einschließlich aller Rendering- und Datenerweiterungen.  
  
> [!NOTE]  
>  Die Liste der Erweiterungen, die für das Steuerelement ReportViewer im Remoteverarbeitungsmodus zur Verfügung stehen, hängt davon ab, welche Ausgabe von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] auf dem Berichtsserver installiert ist.  
  
## <a name="local-processing-mode"></a>Lokaler Verarbeitungsmodus  
 Der lokale Verarbeitungsmodus stellt eine alternative Methode zum Anzeigen und Rendern von Berichten dar, wenn [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nicht installiert ist. Anders als bei der Remoteverarbeitung steht dem Steuerelement nur ein Teil der Funktionen zur Verfügung, die der Berichtsserver eigentlich enthält. Im lokalen Verarbeitungsmodus wird die Datenverarbeitung nicht vom Steuerelement gehandhabt, sondern sie wird von der Hostinganwendung implementiert. Die Berichtsverarbeitung wird jedoch vom Steuerelement selbst gehandhabt. Im lokalen Verarbeitungsmodus stehen nur die PDF-, Excel-, Word- und Bild-Renderingerweiterungen zur Verfügung.  
  
## <a name="see-also"></a>Siehe auch  
 [Integration von Reporting Services in Anwendungen](../application-integration/integrating-reporting-services-into-applications.md)   
 [Erstellen von SSRS-Berichten, die mithilfe von Visual Studio (Curated Answers)](http://go.microsoft.com/fwlink/?LinkId=321991)  
  
  
