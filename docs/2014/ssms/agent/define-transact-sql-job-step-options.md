---
title: So definieren Sie die Optionen für Transact-SQL-Auftragsschritte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL job step
- job steps [Transact-SQL]
- SQL Server Agent jobs, Transact-SQL step
ms.assetid: b2a47057-f6fb-432b-a7b6-5d61f33a5d9c
caps.latest.revision: 32
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3a6921b2f6da22cd5cf81a82bf10538cd002a597
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43815732"
---
# <a name="define-transact-sql-job-step-options"></a>Definieren von Optionen für Transact-SQL-Auftragsschritte
  In diesem Thema wird beschrieben, wie Sie Optionen für [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent [!INCLUDE[tsql](../../includes/tsql-md.md)] -Auftragsschritte in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder SQL Server Management Objects definieren können.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **So definieren Sie die Optionen für Transact-SQL-Auftragsschritte mit**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [SQL Server Management Objects](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Security"></a> Sicherheit  
 Ausführliche Informationen finden Sie unter [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-define-transact-sql-job-step-options"></a>So definieren Sie die Optionen für Transact-SQL-Auftragsschritte  
  
1.  Erweitern Sie in **Objekt-Explorer**die Option **SQL Server-Agent**, und erweitern Sie **Aufträge**. Klicken Sie mit der rechten Maustaste auf den Auftrag, den sie bearbeiten möchten, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Klicken Sie auf die Seite **Schritte** , klicken Sie auf einen Auftragsschritt und dann auf **Bearbeiten**.  
  
3.  Bestätigen Sie im Dialogfeld **Auftragsschritt-Eigenschaften** , ob **Transact-SQL-Skript (TSQL)** als Typ festgelegt ist, und klicken Sie dann auf die Seite **Erweitert** .  
  
4.  Wählen Sie in der Liste **Aktion bei Erfolg** aus, welche Aktion ausgeführt werden soll, wenn der Auftrag erfolgreich ist.  
  
5.  Geben Sie die Anzahl von Wiederholungsversuchen an, indem Sie in das Feld **Wiederholungsversuche** eine Zahl zwischen 0 und 9999 eingeben.  
  
6.  Geben Sie ein Wiederholungsintervall an, indem Sie in das Feld **Wiederholungsintervall** einen Wert zwischen 0 und 9999 Minuten eingeben.  
  
7.  Wählen Sie in der Liste **Aktion bei Fehler** eine Aktion aus, die ausgeführt werden soll, wenn der Auftrag fehlerhaft verläuft.  
  
8.  Handelt es sich bei dem Auftrag um ein [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skript, stehen die folgenden Optionen zur Auswahl:  
  
    -   Geben Sie den Namen einer **Ausgabedatei**ein. Standardmäßig wird die Datei bei jeder Ausführung des Auftragsschrittes überschrieben. Wenn die Ausgabedatei nicht überschrieben werden soll, aktivieren Sie **Ausgabe an vorhandene Datei anfügen**. Diese Option ist nur für Mitglieder der festen Serverrolle **sysadmin** verfügbar. Beachten Sie, dass Benutzer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] nicht beliebige Dateien im Dateisystem anzeigen können. Deshalb können mit [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] keine Auftragsschrittprotokolle angezeigt werden, die in das Dateisystem geschrieben werden.  
  
    -   Aktivieren Sie **In Tabelle protokollieren** , wenn der Auftragsschritt in einer Datenbanktabelle protokolliert werden soll. Standardmäßig wird der Tabelleninhalt bei jeder Ausführung des Auftragsschrittes überschrieben. Wenn der Tabelleninhalt nicht überschrieben werden soll, aktivieren Sie **Ausgabe an vorhandenen Eintrag in Tabelle anfügen**. Nachdem der Auftragsschritt ausgeführt wurde, können Sie den Inhalt dieser Tabelle anzeigen, indem Sie auf **Anzeigen**klicken.  
  
    -   Aktivieren Sie **Schrittausgabe in Verlauf einschließen** , wenn die Ausgabe in den Schrittverlauf eingeschlossen werden soll. Die Ausgabe wird nur angezeigt, wenn keine Fehler auftraten. Es kann auch vorkommen, dass die Ausgabe abgeschnitten wird.  
  
9. Wenn Sie ein Mitglied der festen Serverrolle **sysadmin** sind und diesen Auftragsschritt unter einem anderen SQL-Anmeldenamen ausführen möchten, wählen Sie den SQL-Anmeldenamen in der Liste **Ausführen als Benutzer** aus.  
  
##  <a name="SMO"></a> Verwendung von SQL Server Management Objects  
 **So definieren Sie die Optionen für Transact-SQL-Auftragsschritte**  
  
 Verwenden der `JobStep` Klasse, indem Sie eine Programmiersprache, die Sie, wie z. B. Visual Basic, Visual c# oder PowerShell auswählen.  
  
  
