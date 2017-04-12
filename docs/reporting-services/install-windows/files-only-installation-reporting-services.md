---
title: "Ausschlie&#223;liche Datei-Installation (Reporting Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Ausschließliche Installation von Dateien [Reporting Services]"
  - "Installationsoptionen [Reporting Services]"
ms.assetid: bdc74a8f-046c-4aa0-bfbd-4f1711dfb9ce
caps.latest.revision: 22
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 22
---
# Ausschlie&#223;liche Datei-Installation (Reporting Services)
  Die *Nur-Dateien-Installation* bezieht sich auf eine [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Installation, bei der Setup Folgendes ausführt: Die Ordnerstruktur für die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Programmdateien wird erstellt, die Dateien werden auf den Datenträger kopiert, der Berichtsserverdienst wird auf dem lokalen Computer registriert, das Dienstkonto wird konfiguriert, die Dateien erhalten Berechtigungen für das Dienstkonto, und der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI-Anbieter wird registriert.  
  
 Eine Nur-Dateien-Installationsdatei umfasst folgende [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Funktionen: Berichtsserver-Dienst (hostet den Berichtsserver-Webdienst, Hintergrundverarbeitungsanwendung und Berichts-Manager), Berichts-Generator, das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Konfigurationstool und die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Befehlszeilenhilfsprogramme (rsconfig.exe, rskeymgmt.exe und rs.exe). Sie gilt nicht für gemeinsam genutzte Funktionen wie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] oder [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], die im gegebenen Fall bei der Installation als separate Elemente angegeben werden müssen.  
  
 Im Gegensatz zu anderen Installationsarten ist ein Berichtsserver, der ausschließlich mit Dateien installiert wird, nicht funktionsfähig, wenn das Setup beendet ist. Zusätzliche Komponenten müssen konfiguriert werden, damit der Berichtsserver mit dem [Reporting Services-Konfigurations-Manager &#40;einheitlicher Modus&#41;](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md) online geschaltet werden kann.  
  
## Sinnvoller Einsatz einer ausschließlichen Datei-Installation  
 Eine ausschließliche Datei-Installation muss ausgeführt werden, wenn:  
  
-   Sie eine Verbindung zwischen Berichtsserverinstanz und einer Remoteberichtsserver-Datenbank herstellen möchten  
  
-   Sie den Berichtsserver als benannte Instanz installieren möchten.  
  
-   Sie Anwendungserfordernisse haben, die benutzerdefinierte Einstellungen oder Funktionen umfassen, und wenn Sie Zeitpunkt und Art der Serverkonfiguration komplett steuern möchten.  
  
-   Installieren eines [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Failoverclusters, der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] beinhaltet  
  
## Vorgehensweise: Ausführen der ausschließlichen Datei-Installation  
 Die ausschließliche Datei-Installation ist die Standardvorgabe für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 Sie können die ausschließliche Datei-Installation über die Befehlszeile oder im Installations-Assistenten angeben. Folgende Themen enthalten Schritt-für-Schritt-Anweisungen:  
  
-   [Installieren von SQL Server 2016 vom Installations-Assistenten aus &#40;Setup&#41;](../../database-engine/install-windows/install-sql-server-2016-from-the-installation-wizard-setup.md)  
  
-   [Installieren von SQL Server 2016 von der Eingabeaufforderung](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)  
  
#### Beispiel eines Befehlszeilenskripts:  
 Aus Gründen der Klarheit umfasst das Beispiel den /RSINSTALLMODE = "FilesOnlyMode". Da der ausschließliche Dateimodus jedoch als Standardinstallationsmodus verwendet wird, können Sie diesen Schritt weglassen. Es erfolgt trotzdem eine ausschließliche Datei-Installation.  
  
```  
setup /q /ACTION=install /FEATURES=RS /InstanceName=MSSQLSERVER /RSSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /RSINSTALLMODE="FilesOnlyMode"  
```  
  
#### Installations-Assistent  
 Wenn Sie auf der Seite Funktionsauswahl die Option [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] auswählen, öffnet das Setup die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Konfigurationsseite, auf der Sie den Installationsmodus angeben können. Um anzugeben, dass nur Dateien installiert werden, wählen Sie auf der Seite [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Konfiguration die Option **Berichtsserver installieren, aber nicht konfigurieren** aus.  
  
## Siehe auch  
 [Überprüfen einer Installation von Reporting Services](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)   
 [Konfigurieren des Berichtsserver-Dienstkontos &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Konfigurieren von Berichtsserver-URLs &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)   
 [Konfigurieren einer Verbindung mit der Berichtsserver-Datenbank &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
 [Installieren des SharePoint-Modus von Reporting Services](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)   
 [Installieren des Reporting Services-Berichtsservers im einheitlichen Modus](../../reporting-services/install-windows/install-reporting-services-native-mode-report-server.md)   
 [Reporting Services-Tools](../../reporting-services/tools/reporting-services-tools.md)  
  
  