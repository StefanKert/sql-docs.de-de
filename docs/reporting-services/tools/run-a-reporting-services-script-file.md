---
title: "Ausf&#252;hren einer Reporting Services-Skriptdatei | Microsoft Docs"
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
  - "Skripts [Reporting Services], ausführen"
ms.assetid: 0de4995c-85ec-4d4c-aaef-fbd30edfb20f
caps.latest.revision: 36
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 36
---
# Ausf&#252;hren einer Reporting Services-Skriptdatei
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Skriptdateien werden von der Eingabeaufforderung in der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Skriptumgebung (RS.exe) ausgeführt. In RS.exe stehen Ihnen viele Befehlszeileargumente zur Verfügung. Weitere Informationen zu den Befehlszeilenoptionen finden Sie unter [Hilfsprogramm „RS.exe“ &#40;SSRS&#41;](../../reporting-services/tools/rs-exe-utility-ssrs.md). Weitere Skriptbeispiele finden Sie unter [SQL Server Reporting Services-Produktbeispiele](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## Beispielbefehlszeilen  
  
-   Führen Sie Script.rss in der Skriptumgebung für den Zielberichtsserver aus. Standardmäßig wird die Windows-Authentifizierung angewendet:  
  
    ```  
    rs –i Script.rss -s http://servername/reportserver  
    ```  
  
-   Führen Sie Script.rss in der Skriptumgebung unter Angabe eines Benutzernamens und eines Kennworts für die Authentifizierung der Webdienstaufrufe aus:  
  
    ```  
    rs –i Script.rss -s http://servername/reportserver -u myusername -p mypassword  
    ```  
  
-   Führen Sie Script.rss in der Skriptumgebung unter Angabe eines Timeouts von 30 Sekunden für den Server aus:  
  
    ```  
    rs –i Script.rss -s http://servername/reportserver -l 30  
    ```  
  
-   Führen Sie Script.rss in der Skriptumgebung unter Angabe einer globalen Skriptvariablen mit der Bezeichnung *report*aus:  
  
    ```  
    rs –i Script.rss -s http://servername/reportserver -v report="Company Sales"  
    ```  
  
-   Führen Sie Script.rss in der Skriptumgebung aus, und geben Sie dabei an, dass die Webdienstvorgänge in der Skriptdatei als Batch ausgeführt werden.  
  
    ```  
    rs –i Script.rss -s http://servername/reportserver -b  
    ```  
  
## Siehe auch  
 [Technische Referenz &#40;SSRS&#41;](../../reporting-services/technical-reference-ssrs.md)  
  
  