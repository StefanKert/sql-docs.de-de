---
title: "Starten oder Beenden eines Sammlungssatzes | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Sammlungssätze [SQL Server], beenden"
  - "Sammlungssätze [SQL Server], starten"
ms.assetid: 48a7b2fe-6bc3-4278-a7ec-1babc1290345
caps.latest.revision: 20
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 20
---
# Starten oder Beenden eines Sammlungssatzes
  In diesem Thema wird beschrieben, wie ein Sammlungssatz in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]gestartet oder angehalten wird.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Erforderliche Komponenten](#Prerequisites)  
  
     [Empfehlungen](#Recommendations)  
  
     [Sicherheit](#Security)  
  
-   **So starten oder halten Sie einen Sammlungssatz an, und zwar mit**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Gespeicherte Prozeduren für den Datensammler und Katalogsichten werden in der **msdb** -Datenbank gespeichert.  
  
-   Im Gegensatz zu regulären gespeicherten Prozeduren werden die Parameter für die gespeicherten Prozeduren des Datensammlers genau eingegeben und unterstützen die automatische Datentypkonvertierung nicht. Wenn diese Parameter nicht mit den richtigen Datentypen für Eingabeparameter aufgerufen werden, wie in der Argumentbeschreibung angegeben, gibt die gespeicherte Prozedur einen Fehler zurück.  
  
###  <a name="Prerequisites"></a> Erforderliche Komponenten  
  
-   Der SQL Server-Agent muss gestartet werden.  
  
###  <a name="Recommendations"></a> Empfehlungen  
  
-   Fragen Sie die [syscollector_collection_sets](../../relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql.md)-Katalogsicht ab, um Informationen zu Sammlungssätzen abzurufen.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Datenbankrolle **dc_operator**. Wenn der Sammlungssatz über kein Proxykonto verfügt, ist die Mitgliedschaft in der festen Serverrolle **sysadmin** erforderlich. Beispiele  
  
##  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
  
#### So starten Sie einen Sammlungssatz  
  
1.  Erweitern Sie im Objekt-Explorer nacheinander die Knoten **Verwaltung** , **Datensammlung**und dann **Systemdaten-Sammlungssätze**.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Sammlungssatz, den Sie starten möchten, und klicken Sie anschließend auf **Datenauflistsatz starten**.  
  
     Ein Meldungsfeld mit dem Ergebnis des Vorgangs wird angezeigt, und ein grüner Pfeil auf dem Symbol für den Sammlungssatz weist darauf hin, dass der Sammlungssatz gestartet wurde.  
  
#### So beenden Sie einen Sammlungssatz  
  
1.  Erweitern Sie im Objekt-Explorer nacheinander die Knoten **Verwaltung** , **Datensammlung**und dann **Systemdaten-Sammlungssätze**.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Sammlungssatz, den Sie beenden möchten, und klicken Sie anschließend auf **Datensammlungssatz beenden**.  
  
     Ein Meldungsfeld mit den Ergebnissen dieses Vorgangs wird angezeigt, und ein roter Kreis auf dem Symbol für den Sammlungssatz weist darauf hin, dass der Sammlungssatz beendet wurde.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### So starten Sie einen Sammlungssatz  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird [sp_syscollector_start_collection_set](../../relational-databases/system-stored-procedures/sp-syscollector-start-collection-set-transact-sql.md) verwendet, um den Sammlungssatz zu starten, der über die ID von `1` verfügt.  
  
```tsql  
USE msdb;  
GO  
EXEC sp_syscollector_start_collection_set @collection_set_id = 1;  
```  
  
#### So beenden Sie einen Sammlungssatz  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird [sp_syscollector_stop_collection_set](../../relational-databases/system-stored-procedures/sp-syscollector-stop-collection-set-transact-sql.md) verwendet, um den Sammlungssatz anzuhalten, der über die ID von `1` verfügt.  
  
```tsql  
USE msdb;  
GO  
EXEC sp_syscollector_stop_collection_set @collection_set_id = 1;  
```  
  
## Siehe auch  
 [Sichten des Datensammlers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [Datensammlung](../../relational-databases/data-collection/data-collection.md)  
  
  