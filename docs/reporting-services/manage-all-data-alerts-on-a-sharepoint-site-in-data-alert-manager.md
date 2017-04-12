---
title: "Verwalten aller Datenwarnungen auf einer SharePoint-Website im Datenwarnungs-Manager | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Warnungen, verwalten"
  - "Datenwarnungen, verwalten"
ms.assetid: 9c70b0f4-2db8-4c2e-acbf-96e2a55ddc48
caps.latest.revision: 13
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 13
---
# Verwalten aller Datenwarnungen auf einer SharePoint-Website im Datenwarnungs-Manager
  SharePoint-Warnungsadministratoren können eine Liste der von allen Benutzern der Website erstellten Datenwarnungen und Informationen zu den Warnungen anzeigen. Warnungsadministratoren können auch Warnungen löschen. Das folgende Bild zeigt Warnungsadministratoren die verfügbaren Funktionen im Datenwarnungs-Manager.  
  
 ![Warnungs-Manager für SharePoint-Websiteadministratoren](../reporting-services/media/rs-alertmanagersite.gif "Warnungs-Manager für SharePoint-Websiteadministratoren")  
  
### So zeigen Sie eine Liste der von einem Websitebenutzer erstellten Warnungen an  
  
1.  Wechseln Sie zur SharePoint-Website, auf der Datenwarnungsdefinitionen gespeichert sind.  
  
2.  Klicken Sie auf der Startseite auf **Websiteaktionen**.  
  
3.  Führen Sie einen Bildlauf zum Ende der Liste durch, und klicken Sie auf **Siteeinstellungen**.  
  
4.  Klicken Sie unter **Reporting Services**auf **Datenwarnungen verwalten**.  
  
5.  Klicken Sie neben der Liste **Warnungen anzeigen für folgenden Benutzer** auf den Pfeil nach unten, und wählen Sie den Benutzer aus, dessen Warnungen Sie anzeigen möchten.  
  
6.  Klicken Sie neben der Liste **Warnungen anzeigen für folgenden Bericht** auf den Pfeil nach unten, und wählen Sie eine bestimmte anzuzeigende Warnung aus, oder klicken Sie auf **Alle anzeigen** , um alle vom ausgewählten Benutzer erstellten Warnungen anzuzeigen.  
  
     Eine Tabelle umfasst den Namen, Berichtsnamen, Namen der Person, die die Datenwarnung erstellt hat, die Häufigkeit der Übermittlungen einer Datenwarnung, die letzte Änderung der Datenwarnungsdefinition und den Status der Datenwarnung. Wenn die Datenwarnung nicht generiert oder gesendet werden kann, enthält die Statusspalte Informationen zum Fehler und hilft Ihnen bei der Behebung des Problems.  
  
### So löschen Sie eine Warnungsdefinition  
  
-   Klicken Sie mit der rechten Maustaste auf die zu löschende Datenwarnung, und klicken Sie auf **Löschen**.  
  
    > [!NOTE]  
    >  Nach dem Löschen der Warnung werden keine weiteren Warnmeldungen gesendet. Wenn Sie jedoch die Warnungsdatenbank abfragen, stellen Sie möglicherweise fest, dass die Warnungsdefinition immer noch vorhanden ist. Der Warndienst führt den Cleanup nach einem Zeitplan durch. Die Warnungsdefinition wird beim nächsten Cleanup dauerhaft gelöscht. Das Standardintervall für den Cleanup beträgt 20 Minuten. Dieses und andere Cleanupintervalle sind konfigurierbar. Weitere Informationen finden Sie unter [Reporting Services-Datenwarnungen](../reporting-services/reporting-services-data-alerts.md).  
  
## Siehe auch  
 [Datenwarnungs-Manager für Warnungsadministratoren](../reporting-services/data-alert-manager-for-alerting-administrators.md)   
 [Reporting Services-Datenwarnungen](../reporting-services/reporting-services-data-alerts.md)  
  
  