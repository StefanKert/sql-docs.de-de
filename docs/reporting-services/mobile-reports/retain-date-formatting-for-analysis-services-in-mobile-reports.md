---
title: "Beibehalten der Datumsformatierung f&#252;r Analysis Services in mobilen Berichten | Reporting Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e9a9a199-40e3-4381-b250-1b99fb83aa62
caps.latest.revision: 3
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 3
---
# Beibehalten der Datumsformatierung f&#252;r Analysis Services in mobilen Berichten | Reporting Services
Fügen Sie im Berichts-Generator einem freigegebenen Dataset ein Measure so hinzu, dass Datumsangaben in [!INCLUDE[ssASnoversion_md](../../includes/ssasnoversion-md.md)]-Datenquellen ihren Datentyp in [!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-short.md)] beibehalten.

Der Standardrückgabetyp für [!INCLUDE[ssASnoversion_md](../../includes/ssasnoversion-md.md)]-Abfragen ist eine Zeichenfolge.  Beim Erstellen eines Datasets im Berichts-Generator von [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] wird der „string“-Datentyp berücksichtigt und auf dem Server gespeichert. 

Wenn jedoch der JSON-Tabellenrenderer das Dataset verarbeitet, liest er den Wert der Spalte als Zeichenfolge und rendert Zeichenfolgen.  Wenn dann [!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-long.md)] die Tabelle abruft, werden auch nur Zeichenfolgen angezeigt.

Um dieses Problem zu umgehen, fügen Sie ein berechnetes Element hinzu, wenn Sie im Berichts-Generator ein freigegebenes Dataset erstellen. Dies funktioniert für mehrdimensionale und tabellarische [!INCLUDE[ssASnoversion_md](../../includes/ssasnoversion-md.md)]-Modelle.

## Erstellen eines Measures zum Beibehalten des Datentyps des Datumsfelds

1. Erstellen Sie ein Measure zum Aufnehmen des Werts des betreffenden Datumsfelds. Wählen Sie im Ausdrucksfeld die Hierarchie/Stufe des Datums, und fügen Sie **.CurrentMember.MemberValue** an. Beispiel:
 
   [Internet Sales].[Ship Date].CurrentMember.MemberValue
   
   ![ssas-calculated-member-report-builder](../../reporting-services/mobile-reports/media/ssas-calculated-member-report-builder.png)
   
2. Sie können nun dieses berechnete Element an die Gruppe der Spalten anfügen, indem Sie es aus der Liste „Berechnete Elemente“ links unten ziehen und im Spaltenraster rechts ablegen.  

   ![ssas-query-designer-calculated-member-report-builder](../../reporting-services/mobile-reports/media/ssas-query-designer-calculated-member-report-builder.png) 
   
### Siehe auch

-  [Daten für mobile Berichte von Reporting Services](../../reporting-services/mobile-reports/data-for-reporting-services-mobile-reports.md)
-  [Vorbereiten von Daten für mobile Berichte von Reporting Services](../../reporting-services/mobile-reports/prepare-data-for-reporting-services-mobile-reports.md)