---
title: 'Lektion 5: Entwerfen des untergeordneten Berichts mithilfe des Berichts-Assistenten | Microsoft-Dokumentation'
ms.date: 05/18/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.suite: pro-bi
ms.topic: conceptual
applies_to:
- SQL Server 2016
ms.assetid: 19a3f927-ea97-4f40-a5f8-cd5f2598e4da
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 3ffdd8ca24ae99fdbbd6216a4daa53b7ba4f3b3b
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43282642"
---
# <a name="lesson-5-design-the-child-report-using-the-report-wizard"></a>Lektion 5: Entwerfen des untergeordneten Berichts mithilfe des Berichts-Assistenten
Nachdem Sie eine Datenverbindung und eine Datentabelle für den untergeordneten Bericht erstellt haben, entwerfen Sie im nächsten Schritt den untergeordneten Bericht mithilfe des Berichts-Assistenten im Berichts-Designer. Weitere Informationen zum Berichts-Designer finden Sie unter [Entwerfen von Berichten mithilfe des Berichts-Designers (SSRS)](../reporting-services/tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md).  
  
### <a name="to-design-the-child-report-using-the-report-wizard"></a>So entwerfen Sie den untergeordneten Bericht mithilfe des Berichts-Assistenten  
  
1.  Stellen Sie sicher, dass die Website der obersten Ebene im **Projektmappen-Explorer**ausgewählt ist.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Website, und wählen Sie **Neues Element hinzufügen**aus.  
  
3.  Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **Berichts-Assistent**, geben Sie einen Namen für die Berichtsdatei ein, und klicken Sie anschließend auf **Hinzufügen**.  
  
    Daraufhin wird der Berichts-Assistent gestartet.  
  
4.  Wählen Sie auf der Seite **Dataseteigenschaften** im Feld **Datenquelle** **DataSet2**aus.  
  
    Das Feld **Verfügbare Datasets** wird automatisch anhand der erstellen DataTable aktualisiert.  
  
5.  Wählen Sie **Weiter**aus.  
  
6.  Gehen Sie auf der Seite **Felder anordnen** wie folgt vor:  
  
    1.  Ziehen Sie **ProductID**, **PurchaseOrderID**, **PurchaseOrderDetailID**, **OrderQty**, **ReceivedQty**, **RejectedQty**und **StockedQty** aus **Verfügbare Felder** in das Feld **Werte** .  
  
    2.  Klicken Sie auf den Pfeil neben **Sum(ProductID)**, **Sum(PurchaseOrderID)**, **Sum(PurchaseOrderDetailID)**, **Sum(OrderQty)**, **Sum(ReceivedQty)**, **Sum(RejectedQty)** und **Sum(StockedQty)** , und deaktivieren Sie die Auswahl **Sum** .  
  
7.  Klicken Sie zweimal auf **Weiter** und anschließend auf **Fertig stellen** , um den **Berichts-Assistenten**zu schließen.  
  
    Die RDLC-Datei ist jetzt erstellt. Die Datei wird im Berichts-Designer geöffnet. Die entworfene Tablix wird jetzt auf der Entwurfsoberfläche angezeigt.  
  
8.  Fügen Sie bei geöffneter RDLC-Datei auf folgende Weise einen Parameter hinzu:  
  
    1.  Klicken Sie mit der rechten Maustaste im Bereich **Berichtsdaten** auf **Parameter** , und klicken Sie auf **Parameter hinzufügen**.  
  
    2.  Geben Sie im Feld **Name** die Zeichenfolge **productid** ein.  
  
    3.  Vergewissern Sie sich, dass im Listenfeld **Datentyp** der Eintrag **Integer** ausgewählt ist.  
  
    4.  Klicken Sie auf **OK**.  
  
9. Speichern Sie die RDLC-Datei.  
  
## <a name="next-task"></a>Nächste Aufgabe  
Sie haben erfolgreich den untergeordneten Bericht mit dem Berichts-Assistenten entworfen. Als Nächstes fügen Sie der Websiteanwendung ein ReportViewer-Steuerelement hinzu. Informationen hierzu finden Sie unter [Lektion 6: Hinzufügen eines ReportViewer-Steuerelements zur Anwendung](../reporting-services/lesson-6-add-a-reportviewer-control-to-the-application.md).  
  
  
  

