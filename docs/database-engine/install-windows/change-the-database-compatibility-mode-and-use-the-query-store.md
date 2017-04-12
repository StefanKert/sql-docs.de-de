---
title: "&#196;ndern des Datenbank-Kompatibilit&#228;tsmodus und Verwenden des Abfragespeichers | Microsoft Docs"
ms.custom: ""
ms.date: "09/22/2015"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Abfragepläne [SQL Server], Migrieren"
  - "Upgraden von SQL Server, Migrieren von Abfrageplänen"
  - "Planhinweislisten [SQL Server], Migrieren von Abfrageplänen"
ms.assetid: 7e02a137-6867-4f6a-a45a-2b02674f7e65
caps.latest.revision: 19
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 17
---
# &#196;ndern des Datenbank-Kompatibilit&#228;tsmodus und Verwenden des Abfragespeichers
  In SQL Server 2016 treten einige Änderungen erst in Kraft, nachdem der DATABASE_COMPATIBILITY-Grad für eine Datenbank in 130 geändert wurde.  Dies hat verschiedene Gründe:  
  
-   Da das Upgraden einen unidirektionalen Vorgang darstellt (ein Downgrade des Dateiformats ist nicht möglich), ist es sinnvoll, das Aktivieren neuer Funktionen als separaten Datenbankvorgang durchzuführen.  Es ist möglich, eine Einstellung auf einen früheren DATABASE_COMPATIBILITY-Grad zurückzusetzen.  Das neue Modell reduziert die Anzahl von Vorgängen, die während einer Ausfallzeit durchgeführt werden müssen.  
  
-   Änderungen am Abfrageprozessor können komplexe Auswirkungen haben.  Auch eine „positive“ Systemänderung, die für die meisten Kunden möglicherweise sehr gut ist, könnte an anderer Stelle für eine wichtige Abfrage eine unzulässige Regression verursachen.  Durch die Trennung dieser Logik vom Upgradevorgang können Funktionen, wie z.B. der Abfragespeicher, Planauswahlregressionen auf Produktionsservern schnell abschwächen oder sogar komplett vermeiden.  
  
> [!NOTE]  
>  War der Kompatibilitätsgrad einer Benutzerdatenbank vor dem Upgrade 100 oder höher, wird er nach dem Upgrade beibehalten. War der Kompatibilitätsgrad der aktualisierten Datenbank vor dem Upgrade 90, wird er auf 100 gesetzt, was dem niedrigsten unterstützten Kompatibilitätsgrad in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] entspricht.  
  
 Der Upgradevorgang zum Aktivieren neuer Abfrageprozessorfunktionen steht im Zusammenhang mit dem Wartungsmodell des Produkts nach der Einführung.  Einige dieser Fixes werden unter dem Ablaufverfolgungsflag 4199 zur Verfügung gestellt.  Kunden, die Fixes benötigen, können diese abonnieren, ohne unerwartete Regressionen für andere Kunden zu verursachen.  Das Wartungsmodell für Abfrageprozessor-Hotfixes nach der Einführung ist [hier](https://support.microsoft.com/en-us/kb/974006) dokumentiert. Ab SQL Server 2016 bedeutet das Verschieben in einen neuen Kompatibilitätsgrad, dass das Ablaufverfolgungsflag 4199 nicht mehr benötigt wird, da diese Fixes nun standardmäßig im aktuellsten Kompatibilitätsmodus (130) aktiviert sind.  Im Rahmen des Upgradevorgangs ist es daher wichtig, sich zu vergewissern, dass 4199 nicht aktiviert ist, sobald der Upgradevorgang abgeschlossen ist.  
  
 Der empfohlene Workflow für die Aktualisierung des Abfrageprozessors auf die neueste Version des Codes sieht folgendermaßen aus:  
  
1.  Führen Sie für eine Datenbank ein Upgrade auf SQL Server 2016 durch, ohne den Datenbank-Kompatibilitätsgrad zu ändern (behalten Sie den bisherigen Kompatibilitätsgrad bei).  
  
2.  Aktivieren Sie den Abfragespeicher auf der Datenbank. Weitere Informationen zum Aktivieren und Verwenden des Abfragespeichers finden Sie unter [Überwachen der Leistung mit dem Abfragespeicher](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md).  
  
3.  Warten Sie ausreichend lange, um repräsentative Daten der Arbeitsauslastung zu sammeln.  
  
4.  Ändern Sie den Kompatibilitätsgrad der Datenbank in „130“.  
  
5.  Werten Sie mithilfe von SQL Server Management Studio aus, ob nach dem Ändern des Kompatibilitätsgrads Leistungsregressionen für bestimmte Abfragen aufgetreten sind  
  
6.  Erzwingen Sie für alle Fälle, in denen Regressionen aufgetreten sind, im Abfragespeicher den vorherigen Plan.  
  
7.  Falls Abfragepläne nicht erzwungen werden können oder die Leistung weiterhin unzureichend ist, ziehen Sie in Betracht, die vorherige Einstellung des Kompatibilitätsgrads wiederherzustellen und sich anschließend an den Microsoft-Kundensupport zu wenden.  
  
## Siehe auch  
 [Anzeigen oder Ändern des Kompatibilitätsgrads einer Datenbank](../../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md)  
  
  