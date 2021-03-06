---
title: Ausführen eines inkrementellen Ladens von mehreren Tabellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],multiple tables
ms.assetid: 39252dd5-09c3-46f9-a17b-15208cfd336d
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3e37bc0b02d796d2f29ea21011b632a496f0e5b7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37193560"
---
# <a name="perform-an-incremental-load-of-multiple-tables"></a>Ausführen eines inkrementellen Ladens von mehreren Tabellen
  Im Thema [Verbessern des inkrementellen Ladens mit Change Data Capture](change-data-capture-ssis.md)veranschaulicht das Diagramm ein einfaches Paket, das ein inkrementelles Laden in nur einer Tabelle ausführt. Das Laden einer Tabelle ist jedoch nicht so üblich wie das Ausführen eines inkrementellen Ladens von mehreren Tabellen.  
  
 Wenn Sie ein inkrementelles Laden von mehreren Tabellen ausführen, müssen einige Schritte einmal für alle Tabellen ausgeführt werden, und andere Schritte müssen für jede Quelltabelle wiederholt werden. Sie haben mehr als eine Option zum Implementieren dieser Schritte in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]:  
  
-   Verwenden Sie ein übergeordnetes Paket und untergeordnete Pakete.  
  
-   Verwenden Sie mehrere Datenflusstasks in einem einzelnen Paket.  
  
## <a name="loading-multiple-tables-by-using-a-parent-package-and-multiple-child-packages"></a>Laden von mehreren Tabellen mit einem übergeordneten Paket und mehreren untergeordneten Paketen  
 Sie können ein übergeordnetes Paket verwenden, um jene Schritte auszuführen, die nur einmal gemacht werden müssen. Die untergeordneten Pakete führen jene Schritte aus, die für jede Quelltabelle gemacht werden müssen.  
  
#### <a name="to-create-a-parent-package-that-performs-those-steps-that-only-have-to-be-done-once"></a>So erstellen Sie ein übergeordnetes Paket, das jene Schritte ausführt, die nur einmal gemacht werden müssen  
  
1.  Erstellen eines übergeordneten Pakets.  
  
2.  Verwenden Sie in der Ablaufsteuerung einen Task "SQL ausführen" oder [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Ausdrücke, um die Endpunkte zu berechnen.  
  
     Ein Beispiel zur Berechnung von Endpunkten finden Sie unter [Angeben eines Intervalls von Änderungsdaten](specify-an-interval-of-change-data.md).  
  
3.  Verwenden Sie bei Bedarf einen For-Schleifencontainer, um die Ausführung so lange zu verzögern, bis die Änderungsdaten für den ausgewählten Zeitraum bereit sind.  
  
     Ein Beispiel eines solchen For-Schleifencontainers finden Sie unter [Bestimmen, ob die Änderungsdaten bereit sind](determine-whether-the-change-data-is-ready.md).  
  
4.  Verwenden Sie mehrere Tasks "Paket ausführen", um untergeordnete Pakete für jede zu ladende Tabelle auszuführen. Übergeben Sie die im übergeordneten Paket berechneten Endpunkte an jedes untergeordnete Paket, indem Sie die Variablenkonfiguration für übergeordnete Pakete verwenden.  
  
     Weitere Informationen finden Sie unter [Paket ausführen (Task)](../control-flow/execute-package-task.md) und [Verwenden der Werte von Variablen und Parametern in einem untergeordneten Paket](../use-the-values-of-variables-and-parameters-in-a-child-package.md).  
  
#### <a name="to-create-child-packages-to-perform-those-steps-that-have-to-be-done-for-each-source-table"></a>So erstellen Sie untergeordnete Pakete, um jene Schritte auszuführen, die für jede Quelltabelle gemacht werden müssen  
  
1.  Erstellen Sie für jede Quelltabelle ein untergeordnetes Paket.  
  
2.  Verwenden Sie in der Ablaufsteuerung einen Skripttask oder einen Task "SQL ausführen", um die SQL-Anweisung zusammenzustellen, mit der Änderungen abgefragt werden.  
  
     Ein Beispiel zum Zusammenstellen der Abfrage finden Sie unter [Vorbereiten zur Abfrage der Änderungsdaten](prepare-to-query-for-the-change-data.md).  
  
3.  Verwenden Sie in jedem untergeordneten Paket einen einzelnen Datenflusstask, um die Änderungsdaten zu laden und diese auf das Ziel anzuwenden. Konfigurieren Sie den Datenfluss, wie in den folgenden Stufen beschrieben:  
  
    1.  Verwenden Sie im Datenfluss eine Quellkomponente, um die Änderungstabellen nach den Änderungen abzufragen, die innerhalb der ausgewählten Endpunkte liegen.  
  
         Ein Beispiel zur Abfrage der Änderungstabellen finden Sie unter [Abrufen und Verstehen der Änderungsdaten](retrieve-and-understand-the-change-data.md).  
  
    2.  Verwenden Sie eine Transformation für bedingtes Teilen, um Einfügungen, Updates und Löschungen an andere Ausgaben zur entsprechenden Verarbeitung weiterzuleiten.  
  
         Ein Beispiel für die Konfiguration dieser Transformation zur Weiterleitung einer Ausgabe finden Sie unter [Verarbeiten von Einfügungen, Updates und Löschungen](process-inserts-updates-and-deletes.md).  
  
    3.  Verwenden Sie eine Zielkomponente, um die Einfügungen auf das Ziel anzuwenden. Verwenden Sie Transformationen für OLE DB-Befehl mit parametrisierten UPDATE- und DELETE-Anweisungen, um Updates und Löschungen auf das Ziel anzuwenden.  
  
         Ein Beispiel für die Verwendung dieser Transformation zur Anwendung von Updates und Löschungen finden Sie unter [Anwenden der Änderungen auf das Ziel](apply-the-changes-to-the-destination.md).  
  
## <a name="loading-multiple-tables-by-using-multiple-data-flow-tasks-in-a-single-package"></a>Laden von mehreren Tabellen mit mehreren Datenflusstasks in einem einzelnen Paket  
 Alternativ können Sie ein einzelnes Paket verwenden, das für jede zu ladende Quelltabelle einen separaten Datenflusstask enthält.  
  
#### <a name="to-load-multiple-tables-by-using-multiple-data-flow-tasks-in-a-single-package"></a>So laden Sie mehrere Tabellen mit mehreren Datenflusstasks in einem einzelnen Paket  
  
1.  Erstellen eines einzelnen Pakets.  
  
2.  Verwenden Sie in der Ablaufsteuerung einen Task "SQL ausführen" oder [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Ausdrücke, um die Endpunkte zu berechnen.  
  
     Ein Beispiel zur Berechnung von Endpunkten finden Sie unter [Angeben eines Intervalls von Änderungsdaten](specify-an-interval-of-change-data.md).  
  
3.  Verwenden Sie bei Bedarf einen For-Schleifencontainer, um die Ausführung so lange zu verzögern, bis die Änderungsdaten für das ausgewählte Intervall bereit sind.  
  
     Ein Beispiel eines solchen For-Schleifencontainers finden Sie unter [Bestimmen, ob die Änderungsdaten bereit sind](determine-whether-the-change-data-is-ready.md).  
  
4.  Verwenden Sie einen Skripttask oder einen Task "SQL ausführen", um die SQL-Anweisung zusammenzustellen, mit der Änderungen abgefragt werden.  
  
     Ein Beispiel zum Zusammenstellen der Abfrage finden Sie unter [Vorbereiten zur Abfrage der Änderungsdaten](prepare-to-query-for-the-change-data.md).  
  
5.  Verwenden Sie mehrere Datenflusstasks, um die Änderungsdaten von jeder Quelltabelle zu laden und diese auf das Ziel anzuwenden. Konfigurieren Sie jeden Datenflusstask, wie in den folgenden Schritten beschrieben:  
  
    1.  Verwenden Sie in jedem Datenfluss eine Quellkomponente, um die Änderungstabellen nach den Änderungen abzufragen, die innerhalb der ausgewählten Endpunkte liegen.  
  
         Ein Beispiel zur Abfrage der Änderungstabellen finden Sie unter [Abrufen und Verstehen der Änderungsdaten](retrieve-and-understand-the-change-data.md).  
  
    2.  Verwenden Sie eine Transformation für bedingtes Teilen, um Einfügungen, Updates und Löschungen an andere Ausgaben zur entsprechenden Verarbeitung weiterzuleiten.  
  
         Ein Beispiel für die Konfiguration dieser Transformation zur Weiterleitung einer Ausgabe finden Sie unter [Verarbeiten von Einfügungen, Updates und Löschungen](process-inserts-updates-and-deletes.md).  
  
    3.  Verwenden Sie eine Zielkomponente, um die Einfügungen auf das Ziel anzuwenden. Verwenden Sie Transformationen für OLE DB-Befehl mit parametrisierten UPDATE- und DELETE-Anweisungen, um Updates und Löschungen auf das Ziel anzuwenden.  
  
         Ein Beispiel für die Verwendung dieser Transformation zur Anwendung von Updates und Löschungen finden Sie unter [Anwenden der Änderungen auf das Ziel](apply-the-changes-to-the-destination.md).  
  
  
