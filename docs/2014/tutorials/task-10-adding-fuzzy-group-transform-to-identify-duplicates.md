---
title: 'Aufgabe 10: Hinzufügen der Transformation für Fuzzygruppierung um Duplikate zu identifizieren | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 90b2b323-babd-464a-8914-9dc5e66aca74
caps.latest.revision: 6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8d3e5e71bf32b031552db2a888d17fa222c9f53f
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2018
ms.locfileid: "40396299"
---
# <a name="task-10-adding-fuzzy-group-transform-to-identify-duplicates"></a>Aufgabe 10: Hinzufügen der Transformation für Fuzzygruppierung, um Duplikate zu identifizieren
  In dieser Aufgabe fügen Sie eine Transformation für Fuzzygruppierung zum Datenfluss hinzu. Mit der Transformation für Fuzzygruppierung können Duplikate in den Quelldaten identifiziert werden. Finden Sie unter [Transformation für Fuzzygruppierung](../integration-services/data-flow/transformations/fuzzy-grouping-transformation.md) Weitere Details.  
  
1.  Drag & Drop **Fuzzygruppierung** Transformation **Weitere Transformationen** auf die **SSIS-Toolbox** auf die **Datenfluss** Registerkarte  **Kombinieren Sie die richtige und korrigierte Datensätze**.  
  
2.  Mit der rechten Maustaste **Fuzzygruppierung** transformiert die **Datenfluss** Registerkarte, und klicken Sie auf **umbenennen**. Typ **Gruppenlieferanten mit übereinstimmenden IDs** , und drücken Sie **EINGABETASTE**.  
  
3.  Herstellen einer mit **Combine Correct and Corrected Records** zu **Gruppenlieferanten mit übereinstimmenden IDs** mithilfe des blauen Konnektors.  
  
     ![Gruppenlieferanten mit übereinstimmenden IDs](../../2014/tutorials/media/et-addingfgttoidentifyduplicates-01.jpg "Gruppenlieferanten mit übereinstimmenden IDs")  
  
4.  Doppelklicken Sie auf **Gruppenlieferanten mit übereinstimmenden IDs**.  
  
5.  In der **Transformations-Editor für Fuzzysuche Gruppe**, klicken Sie auf **neu** neben **OLE DB-Verbindungs-Manager-Dropdownliste** starten **Konfigurieren von OLE DB-Verbindung Manager** Dialogfeld.  
  
6.  Klicken Sie im Dialogfeld auf **neu** starten **Verbindungs-Manager** Dialogfeld.  
  
7.  Typ **(local)** oder **Zeitraum** (.) für den Namen des Servers.  
  
8.  Wählen Sie **MDS** für **auswählen oder Eingeben eines Datenbanknamens** Feld. Verwenden Sie die MDS-Datenbank als temporären Speicher für die **Transformation für Fuzzygruppierung**. Die **Fuzzygruppierung** Transformation erfordert eine Verbindung mit einer Instanz von SQL Server, um die temporären SQL Server-Tabellen zu erstellen, die der Transformationsalgorithmus benötigt werden. Sie können eine Datenbank erstellen oder eine andere vorhandene Datenbank zu diesem Zweck verwenden.  
  
9. Klicken Sie auf **Verbindung testen** testen Sie die Verbindung, und klicken Sie auf **OK** im Meldungsfeld auf.  
  
10. In der **Verbindungs-Manager** Dialogfeld klicken Sie auf **OK**.  
  
11. Wählen Sie **(lokal). MDS** (oder **"localhost". MDS**) aus der **Liste der Datenverbindungen** , und klicken Sie auf **OK**.  
  
12. In der **Transformation Editor für Fuzzygruppierung**, überprüfen Sie, ob **(lokal). MDS** oder **"localhost". MDS** ausgewählt ist, für die **OLE DB-Verbindungs-Manager**.  
  
13. Wechseln Sie zu der **Spalten** Registerkarte.  
  
14. Aktivieren (Kontrollkästchen) **SupplierID_Output** aus der Liste der **verfügbare Eingabespalten**. Um die Transformation zu konfigurieren, wählen Sie die Eingabespalten für die Identifizierung von Duplikaten aus. Verwenden Sie in diesem Schritt zur Vereinfachung nur die SupplierID.  
  
     ![Editor für Fuzzygruppierung Transformation](../../2014/tutorials/media/et-addingfgttoidentifyduplicates-02.jpg "Transformation Editor für Fuzzygruppierung")  
  
15. Klicken Sie auf **OK** schließen die **Transformations-Editor für Fuzzysuche Gruppe**.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 11: Hinzufügen der Transformation „Bedingtes Teilen“, um Duplikate zu filtern](../../2014/tutorials/task-11-adding-conditional-split-transform-to-filter-duplicates.md)  
  
  
