---
title: "Servereigenschaften (Seite Protokollierung) | Microsoft Docs"
ms.custom: ""
ms.date: "06/10/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.reportserver.serverproperties.logging.f1"
ms.assetid: b338deab-4868-4951-9f22-0605add2fc95
caps.latest.revision: 17
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 17
---
# Servereigenschaften (Seite Protokollierung)
  Verwenden Sie diese [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)]-Seite in [!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)], um Grenzwerte für die Berichtsausführungsdaten festzulegen, die von einem Berichtsserver aufgelistet werden. Die Ausführungsdaten werden intern in der Berichtsserverdatenbank gespeichert. Sie können die Berichtsaktivität eines Berichtsservers, der im einheitlichen Modus oder im integrierten SharePoint-Modus ausgeführt wird, nachverfolgen. Ist der Berichtsserver Teil einer Bereitstellung für horizontales Skalieren, zeichnet das Berichtsausführungsprotokoll die Berichtsaktivität der gesamten Bereitstellung in einer einzelnen Protokolldatei auf.  
  
 So öffnen Sie diese Seite
 1) Starten Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]
 2) Stellen Sie eine Verbindung mit einem Berichtsserver her.
 3) Klicken Sie mit der rechten Maustaste auf den Berichtsservernamen, und wählen Sie **Eigenschaften** aus. 
 4) Klicken Sie auf **Protokollierung** , um diese Seite zu öffnen.  
  
## enthalten  
 **Protokollierung der Berichtsausführung aktivieren**  
 Klicken Sie auf diese Schaltfläche, um Informationen über die Berichtsaktivität zu erstellen und zu speichern. Ist diese Option aktiviert, verfolgt der Berichtsserver nach, welche Berichte verwendet werden, die Häufigkeit der Berichtsverarbeitung, der Typ des durchgeführten Berichtsvorgangs, das Ausgabeformat und wer den Bericht ausgeführt hat. Weitere Informationen zu den zusätzlichen Datenpunkten, die im Protokoll erfasst werden, finden Sie unter [Berichtsserver-Sichten ExecutionLog und ExecutionLog3](../../reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view.md).  
  
 **Protokolleinträge entfernen, die älter sind als die folgende Anzahl von Tagen**  
 Geben Sie die Anzahl an Tagen an, nach denen die Protokolleinträge aus dem Berichtsausführungsprotokoll gelöscht werden. Der Standardwert ist 60 Tage.  
  
## Siehe auch  
 [Festlegen von Berichtsservereigenschaften &#40;Management Studio&#41;](../../reporting-services/tools/set-report-server-properties-management-studio.md)   
 [Vorgehensweise: Herstellen einer Verbindung mit einem Berichtsserver in Management Studio](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)   
 [Reporting Services-Protokolldateien und Quellen](../../reporting-services/report-server/reporting-services-log-files-and-sources.md)   
 [Berichtsserver im Management Studio (F1-Hilfe)](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [Berichtsserver-Sichten ExecutionLog und ExecutionLog3](../../reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view.md)  
  
  