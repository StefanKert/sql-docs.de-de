---
title: "Aktivieren des DirectQuery-Modus in SSDT | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 71fc7ebd-2e86-4a76-994b-66d3a57bcc9b
caps.latest.revision: 16
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 16
---
# Aktivieren des DirectQuery-Modus in SSDT
In diesem Abschnitt wird die Aktivierung des DirectQuery-Modus für ein tabellarisches Modellprojekt in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] erklärt.  
  
Wenn Sie den DirectQuery-Modus für ein tabellarisches Modell aktivieren, entwerfen Sie in SSDT:
-   Funktionen, die mit dem DirectQuery-Modus inkompatibel sind, werden deaktiviert.  
-   Das vorhandene Modell wird überprüft. Warnungen werden angezeigt, wenn Funktionen mit dem DirectQuery-Modus inkompatibel sind.  
-   Wenn die Daten bereits vor der Aktivierung des DirectQuery-Modus importiert wurden, wird der Cache des Arbeitsmodells geleert.  
  
### Aktivieren von DirectQuery  
  
Ändern Sie in SSDT im Bereich **Eigenschaften** für die Datei **Model.bim** die Eigenschaft **DirectQuery-Modus** auf **On**.  

![Aktivieren des DirectQuery-Modus in SSDT](../../analysis-services/tabular-models/media/enable-directquery-mode-in-ssdt.png)
  
Wenn Ihr Modell bereits eine Verbindung zu einer Datenquelle sowie mit vorhandene Daten hergestellt hat, werden Sie aufgefordert, Datenbankanmeldeinformationen zur Verbindung mit der relationalen Datenbank einzugeben. Bereits vorhandene Daten innerhalb des Modells werden aus dem In-Memory-Cache entfernt.  
  
Wenn Ihr Modell vor der Aktivierung des DirectQuery-Modus teilweise oder zu 100 % abgeschlossen ist, erhalten Sie möglicherweise Fehler in Bezug auf nicht kompatible Funktionen. Öffnen Sie in Visual Studio die **Fehlerliste**, und beheben Sie alle Probleme, durch die verhindert werden würde, dass das Modell in den DirectQuery-Modus wechselt.  


### Wie geht es weiter? 
Sie können nun Daten mit dem Tabellenimport-Assistenten zum Abrufen von Metadaten für das Modell importieren. Sie erhalten keine Datenzeilen, aber Tabellen, Spalten und Beziehungen als Grundlage für Ihr Modell. 

Sie können für jede Tabelle eine Beispielpartition erstellen und Beispieldaten hinzufügen, damit Sie Modellverhalten bei der Erstellung überprüfen können. Beispieldaten, die Sie hinzufügen, werden in **Analysieren für Excel** oder in anderen Clienttools verwendet, die eine Verbindung mit der Arbeitsbereichsdatenbank herstellen können. Einzelheiten finden Sie unter [Hinzufügen von Beispieldaten zu einem DirectQuery-Modell im Entwurfsmodus](../../analysis-services/tabular-models/add-sample-data-to-a-directquery-model-in-design-mode.md).  
  
> [!TIP]  
    >  Selbst im DirectQuery-Modus bei einem leeren Modell können Sie sich immer für jede Tabelle ein kleines eingebautes Rowset anzeigen lassen. Klicken Sie in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] auf **Tabelle** > **Tabelleneigenschaften**, um das Dataset mit 50 Zeilen anzuzeigen.  
  
  
## Siehe auch  
[Aktivieren des DirectQuery-Modus in SSMS](../../analysis-services/tabular-models/enable-directquery-mode-in-ssms.md)

[Hinzufügen von Beispieldaten zu einem DirectQuery-Modell im Entwurfsmodus](../../analysis-services/tabular-models/add-sample-data-to-a-directquery-model-in-design-mode.md)
  