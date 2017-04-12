---
title: "Hinzuf&#252;gen oder Ersetzen eines Datenbank-Spiegelungszeugen (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Zeuge [SQL Server], einrichten"
  - "Datenbankspiegelung [SQL Server], Zeuge"
ms.assetid: 4b5ecffd-f025-4ab7-b69d-8958c6477127
caps.latest.revision: 16
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 16
---
# Hinzuf&#252;gen oder Ersetzen eines Datenbank-Spiegelungszeugen (SQL Server Management Studio)
  Wenn die Endpunkte für die Datenbankspiegelung die Windows-Authentifizierung verwenden, können Sie mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] einen Zeugen hinzufügen oder ersetzen. Beim Hinzufügen eines Zeugen in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] wird auch der Betriebsmodus in den Modus für hohe Sicherheit mit automatischem Failover geändert.  
  
> [!NOTE]  
>  Sie sollten den Zeugen unbedingt auf einem von den Partnern separaten Computer platzieren. Das vom Zeugen verwendete Dienstkonto muss sich in derselben Domäne wie die von der Prinzipalserver- und Spiegelserverinstanz verwendeten Dienstkonten befinden oder in einer vertrauenswürdigen Domäne.  
  
### So fügen Sie einen Zeugen hinzu oder ersetzen ihn  
  
1.  Nachdem Sie eine Verbindung mit der Prinzipalserverinstanz hergestellt haben, klicken Sie im Objekt-Explorer auf den Servernamen, um die Serverstruktur zu erweitern.  
  
2.  Erweitern Sie **Datenbanken**, und wählen Sie die Prinzipaldatenbank der Sitzung aus, für die Sie einen Zeugen hinzufügen oder ersetzen.  
  
3.  Klicken Sie mit der rechten Maustaste auf die Datenbank, wählen Sie **Tasks** aus, und klicken Sie anschließend auf **Spiegeln**. Dadurch wird die Seite **Spiegelung** im Dialogfeld **Datenbankeigenschaften** geöffnet.  
  
4.  Klicken Sie auf **Sicherheit konfigurieren**.  
  
5.  Wenn die Willkommenseite des Assistenten zum Konfigurieren der Sicherheit für die Datenbankspiegelung **** angezeigt wird, klicken Sie auf **Weiter**.  
  
6.  Klicken Sie im Dialogfeld **Zeugenserver einschließen** auf **Ja**, und klicken Sie dann auf **Weiter**.  
  
7.  Im Dialogfeld **Zu konfigurierende Server auswählen** ist das Kontrollkästchen **Zeugenserverinstanz** automatisch aktiviert. Klicken Sie auf **Weiter**.  
  
8.  Behalten Sie im Dialogfeld **Prinzipalserverinstanz** den vorhandenen Port und Endpunkt bei. Klicken Sie auf **Weiter**.  
  
9. Klicken Sie im Dialogfeld **Zeugenserverinstanz** auf **Verbinden**.  
  
10. Geben Sie im Dialogfeld **Verbindung mit Server herstellen** im Textfeld **Servername** die Zeugenserverinstanz an, und verwenden Sie die Windows-Authentifizierung (die Standardeinstellung). Klicken Sie auf **Verbinden**.  
  
11. Sobald eine Verbindung hergestellt ist, werden im Dialogfeld **Zeugenserverinstanz** der Überwachungsport und der Datenbank-Spiegelungsendpunkt der Zeugenserverinstanz angezeigt. Klicken Sie auf **Weiter**.  
  
12. Das Dialogfeld **Dienstkonten** enthält Felder für die Domänendienstkonten der Prinzipal-, Spiegel- und Zeugenserverinstanzen.  
  
    -   Lassen Sie diese Felder leer, wenn alle Serverinstanzen dasselbe Dienstkonto verwenden.  
  
    -   Wenn die Zeugenserverinstanz ein anderes Dienstkonto als einer der Partner verwendet, füllen Sie die Felder **Prinzipal**, **Spiegel**und **Zeuge** mit dem Kontonamen aus:  
  
         *DOMÄNENNAME* **\\** *username*  
  
         Der Domänenname muss in Großbuchstaben eingegeben werden.  
  
     Klicken Sie auf **Weiter**.  
  
13. Überprüfen Sie optional auf der Seite **Assistenten abschließen** die Zeugenkonfiguration, und klicken Sie dann auf **Fertig stellen**.  
  
14. Nach Abschluss des Assistenten wird wieder das Dialogfeld **Datenbankeigenschaften** angezeigt, in dem nun im Feld **Zeuge** die Servernetzwerkadresse des Zeugen angegeben ist. Außerdem ist die für einen Zeugen erforderliche Option **Hohe Sicherheit mit automatischem Failover (synchron)** automatisch ausgewählt.  
  
     Klicken Sie auf **OK**, um den Zeugen zu aktivieren und die Sitzung in den Modus für hohe Sicherheit zu versetzen.  
  
## Siehe auch  
 [Datenbank-Spiegelungszeuge](../../database-engine/database-mirroring/database-mirroring-witness.md)   
 [Datenbankspiegelung &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [Datenbankeigenschaften &#40;Seite Wird gespiegelt&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [Einrichten einer Datenbank-Spiegelungssitzung mithilfe der Windows-Authentifizierung &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/establish database mirroring session - windows authentication.md)   
 [Datenbank-Spiegelungszeuge](../../database-engine/database-mirroring/database-mirroring-witness.md)  
  
  