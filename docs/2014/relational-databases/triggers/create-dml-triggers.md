---
title: Erstellen von DML-Triggern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- encryption [SQL Server], DML triggers
- deferred name resolution, DML triggers
- WITH ENCRYPTION clause
- IF UPDATE
- SET statement, DML triggers
- DML triggers, programming
- testing column changes
- results [SQL Server], DML triggers
ms.assetid: b2b52258-642b-462e-8e0f-18c09d2eccf4
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 49c1cc49dcb388696d18087dbf6da3ef2e0440a3
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37430469"
---
# <a name="create-dml-triggers"></a>Erstellen von DML-Triggern
  In diesem Thema wird beschrieben, wie ein [!INCLUDE[tsql](../../includes/tsql-md.md)] -DML-Trigger mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] unter Verwendung der [!INCLUDE[tsql](../../includes/tsql-md.md)] - CREATE TRIGGER-Anweisung erstellt wird.  
  
##  <a name="Top"></a> Vorbereitungen  
  
### <a name="limitations-and-restrictions"></a>Einschränkungen  
 Eine Liste der Einschränkungen in Zusammenhang mit der Erstellung von DML-Triggern finden Sie unter [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql).  
  
###  <a name="Permissions"></a> Berechtigungen  
 Es ist die ALTER-Berechtigung für die Tabelle oder Sicht erforderlich, für die der Trigger erstellt wird.  
  
##  <a name="Procedures"></a> So erstellen Sie einen DML-Trigger  
 Sie können eine der folgenden Anwendungen verwenden:  
  
-   [SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact-SQL](#TsqlProcedure)  
  
###  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer Instanz von [!INCLUDE[ssDE](../../../includes/ssde-md.md)] her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **Datenbanken**, die [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank und **Tabellen** , und erweitern Sie dann die Tabelle **Purchasing.PurchaseOrderHeader**.  
  
3.  Klicken Sie mit der rechten Maustaste auf **Trigger**, und wählen Sie **Neuer Trigger**aus.  
  
4.  Klicken Sie im Menü **Abfrage** auf **Werte für Vorlagenparameter angeben**. Alternativ können Sie die Tastenkombination STRG+UMSCHALT+M drücken, um das Dialogfeld **Werte für Vorlagenparameter angeben** zu öffnen.  
  
5.  Geben Sie im Dialogfeld **Werte für Vorlagenparameter angeben** die folgenden Werte für die angezeigten Parameter ein.  
  
    |Parameter|value|  
    |---------------|-----------|  
    |Author|*Ihr Name*|  
    |Erstellt am|*Das heutige Datum*|  
    |Description|Überprüft die Anbieterbonität, bevor eine neue Bestellung mit dem einzufügenden Anbieter zugelassen wird.|  
    |Schema_Name|Purchasing|  
    |Trigger_Name|NewPODetail2|  
    |Table_Name|PurchaseOrderDetail|  
    |Data_Modification_Statement|UPDATE und DELETE aus der Liste entfernen.|  
  
6.  Klicken Sie auf **OK**.  
  
7.  Ersetzen Sie im **Abfrage-Editor**den Kommentar `-- Insert statements for trigger here` durch die folgende Anweisung:  
  
    ```tsql  
    IF @@ROWCOUNT = 1  
    BEGIN  
       UPDATE Purchasing.PurchaseOrderHeader  
       SET SubTotal = SubTotal + LineTotal  
       FROM inserted  
       WHERE PurchaseOrderHeader.PurchaseOrderID = inserted.PurchaseOrderID  
  
    END  
    ELSE  
    BEGIN  
          UPDATE Purchasing.PurchaseOrderHeader  
       SET SubTotal = SubTotal +   
          (SELECT SUM(LineTotal)  
          FROM inserted  
          WHERE PurchaseOrderHeader.PurchaseOrderID  
           = inserted.PurchaseOrderID)  
       WHERE PurchaseOrderHeader.PurchaseOrderID IN  
          (SELECT PurchaseOrderID FROM inserted)  
    END;  
    ```  
  
8.  Zum Überprüfen der Syntax klicken Sie im Menü **Abfrage** auf **Analysieren**. Wenn eine Fehlermeldung zurückgegeben wird, vergleichen Sie die Anweisung mit den Informationen oben, korrigieren diese gegebenenfalls und wiederholen diesen Schritt.  
  
9. Zum Erstellen des DML-Triggers klicken Sie im Menü **Abfrage** auf **Ausführen**. Der DML-Trigger wird als Objekt in der Datenbank erstellt.  
  
10. Zum Anzeigen des DML-Triggers im Objekt-Explorer klicken Sie mit der rechten Maustaste auf **Trigger** und wählen **Aktualisieren**aus.  
  
 [Vorbereitungen](#Top)  
  
###  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer Instanz von [!INCLUDE[ssDE](../../../includes/ssde-md.md)] her, und erweitern Sie dann diese Instanz.  
  
2.  Klicken Sie im Menü **Datei** auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird derselbe gespeicherte DML-Trigger wie oben erstellt.  
  
    ```  
    -- Trigger valid for multirow and single row inserts  
    -- and optimal for single row inserts.  
    USE AdventureWorks2012;  
    GO  
    CREATE TRIGGER NewPODetail3  
    ON Purchasing.PurchaseOrderDetail  
    FOR INSERT AS  
    IF @@ROWCOUNT = 1  
    BEGIN  
       UPDATE Purchasing.PurchaseOrderHeader  
       SET SubTotal = SubTotal + LineTotal  
       FROM inserted  
       WHERE PurchaseOrderHeader.PurchaseOrderID = inserted.PurchaseOrderID  
  
    END  
    ELSE  
    BEGIN  
          UPDATE Purchasing.PurchaseOrderHeader  
       SET SubTotal = SubTotal +   
          (SELECT SUM(LineTotal)  
          FROM inserted  
          WHERE PurchaseOrderHeader.PurchaseOrderID  
           = inserted.PurchaseOrderID)  
       WHERE PurchaseOrderHeader.PurchaseOrderID IN  
          (SELECT PurchaseOrderID FROM inserted)  
    END;  
    ```  
  
##  <a name="PowerShellProcedure"></a> [Vorbereitungen](#Top)  
  
  
