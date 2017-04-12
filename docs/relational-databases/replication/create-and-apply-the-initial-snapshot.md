---
title: "Erstellen und Anwenden der Anfangsmomentaufnahme | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Momentaufnahmen [SQL Server-Replikation], erstellen"
  - "Momentaufnahmereplikation [SQL Server], Anfangsmomentaufnahmen"
ms.assetid: 742727a1-5189-44ec-b3ae-6fd7aa1f5347
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# Erstellen und Anwenden der Anfangsmomentaufnahme
  In diesem Thema wird beschrieben, wie die Anfangsmomentaufnahme in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] oder Replikationsverwaltungsobjekten (RMO) erstellt und übernommen wird. Mergeveröffentlichungen, die parametrisierte Filter verwenden, erfordern eine zweiteilige Momentaufnahme. Weitere Informationen finden Sie unter [Create a Snapshot for a Merge Publication with Parameterized Filters](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
 **In diesem Thema**  
  
-   **So erstellen Sie die Anfangsmomentaufnahme und wenden sie an mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Replikationsverwaltungsobjekte (RMO)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
 Wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent ausgeführt wird, wird vom Momentaufnahme-Agent standardmäßig sofort eine Momentaufnahme generiert, nachdem mit dem Assistenten für neue Veröffentlichung eine Veröffentlichung erstellt wurde. Diese Momentaufnahme wird dann standardmäßig vom Verteilungs-Agent (bei der Momentaufnahme- und der Transaktionsreplikation) oder vom Merge-Agent (bei Mergeabonnement) für alle Abonnements angewendet. Eine Momentaufnahme kann auch mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] und dem Replikationsmonitor generiert werden. Informationen zum Starten des Replikationsmonitors finden Sie unter [Starten des Replikationsmonitors](../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
#### So erstellen Sie eine Momentaufnahme in Management Studio  
  
1.  Stellen Sie in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]eine Verbindung mit dem Verleger her, und erweitern Sie dann den Serverknoten.  
  
2.  Erweitern Sie den Ordner **Replikation** , und erweitern Sie dann den Ordner **Lokale Veröffentlichungen** .  
  
3.  Mit der rechten Maustaste in der Veröffentlichung für die Sie eine Momentaufnahme erstellen, und klicken Sie dann auf möchten **Snapshot-Agent-Anzeigestatus**.  
  
4.  In der **Snapshot-Agent-Status anzeigen - \< Veröffentlichung>** im Dialogfeld klicken Sie auf **Start**.  
  
 Nachdem der Momentaufnahme-Agent die Momentaufnahme generiert hat, wird eine Meldung angezeigt, die beispielsweise wie folgt lautet: "[100%] Es wurde eine Momentaufnahme mit 17 Artikel(n) generiert".  
  
#### So erstellen Sie eine Momentaufnahme im Replikationsmonitor  
  
1.  Erweitern Sie im Replikationsmonitor im linken Bereich eine Verlegergruppe, und erweitern Sie dann einen Verleger.  
  
2.  Mit der rechten Maustaste in der Veröffentlichung, für die Sie eine Momentaufnahme generieren, und klicken Sie dann auf möchten **Momentaufnahme generieren**.  
  
3.  Um den Status des Momentaufnahme-Agents anzuzeigen, klicken Sie auf die Registerkarte **Agents** . Detaillierte Informationen, mit der rechten Maustaste im Raster der Snapshot-Agent, und klicken Sie dann auf **Details zum**.  
  
#### So wenden Sie eine Momentaufnahme an  
  
1.  Eine generierte Momentaufnahme wird angewendet, indem das Abonnement mit dem Verteilungs-Agent oder dem Merge-Agent synchronisiert wird:  
  
    -   Wenn der Agent fortlaufend ausgeführt wird (die Standardeinstellung bei der Transaktionsreplikation), wird die Momentaufnahme automatisch nach dem Generieren angewendet.  
  
    -   Wenn der Agent nach einem Zeitplan ausgeführt wird, wird die Momentaufnahme bei der nächsten geplanten Ausführung des Agents angewendet.  
  
    -   Wenn der Agent bedarfsgesteuert ausgeführt wird, wird der Snapshot bei der nächsten Ausführung des Agents angewendet.  
  
     Weitere Informationen zum Synchronisieren von Abonnements finden Sie unter [Synchronisieren eines Abonnements Push](../../relational-databases/replication/synchronize-a-push-subscription.md) und [synchronisieren Sie ein Pullabonnement](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Sie können Anfangsmomentaufnahmen programmgesteuert erstellen, indem Sie entweder einen Momentaufnahme-Agentauftrag erstellen und ausführen oder die ausführbare Datei für den Momentaufnahme-Agent von einer Batchdatei ausführen. Nachdem eine Anfangsmomentaufnahme generiert wurde, wird sie an den Abonnenten übertragen und auf diesen angewendet, sobald die erste Synchronisierung für das Abonnement durchgeführt wird. Wenn Sie den Momentaufnahme-Agent von der Eingabeaufforderung oder einer Batchdatei ausführen, müssen Sie den Agent immer dann erneut ausführen, wenn die bestehende Momentaufnahme ungültig wird.  
  
> [!IMPORTANT]  
>  Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
#### So erstellen Sie einen Momentaufnahme-Agentauftrag und führen ihn aus, um die Anfangsmomentaufnahme zu generieren  
  
1.  Erstellen Sie eine Momentaufnahme-, Transaktions- oder Mergeveröffentlichung. Weitere Informationen finden Sie unter [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
2.  Führen Sie [Sp_addpublication_snapshot & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). Geben Sie **@publication** und die folgenden Parameter an:  
  
    -   **@Job_login, durch Angabe** der Anmeldeinformationen für die Windows-Authentifizierung unter dem der Snapshot-Agent auf dem Verteiler ausgeführt wird.  
  
    -   **@Job_password**, ist das Kennwort für den angegebenen Windows-Anmeldeinformationen.  
  
    -   (Optional) Der Wert **0** für **@publisher_security_mode** Wenn der Agent die SQL Server-Authentifizierung, beim Verbinden mit dem Verleger verwendet wird. In diesem Fall müssen Sie auch die Anmeldeinformationen für SQL Server-Authentifizierung für angeben **@publisher_login** und **@publisher_password**.  
  
    -   (Optional) Einen Synchronisierungszeitplan für den Momentaufnahme-Agentauftrag. Weitere Informationen finden Sie unter [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md).  
  
    > [!IMPORTANT]  
    >  Beim Konfigurieren eines Verlegers mit einem Remoteverteiler werden die angegebenen Werte für alle Parameter einschließlich *Job_login* und *Job_password*, werden als nur-Text an den Verteiler gesendet. Sie sollten die Verbindung zwischen dem Verleger und dem zugehörigen Remoteverteiler verschlüsseln, bevor Sie diese gespeicherte Prozedur ausführen. Weitere Informationen finden Sie unter [Aktivieren von verschlüsselten Verbindungen zum Datenbankmodul & #40; SQL Server-Konfigurations-Manager & #41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
3.  Fügen Sie der Veröffentlichung Artikel hinzu. Weitere Informationen finden Sie unter [Define an Article](../../relational-databases/replication/publish/define-an-article.md).  
  
4.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [Sp_startpublication_snapshot & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-startpublication-snapshot-transact-sql.md), der Wert für **@publication** aus Schritt 1.  
  
#### So führen Sie den Momentaufnahme-Agent zum Generieren der Anfangsmomentaufnahme aus  
  
1.  Erstellen Sie eine Momentaufnahme-, Transaktions- oder Mergeveröffentlichung. Weitere Informationen finden Sie unter [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
2.  Fügen Sie der Veröffentlichung Artikel hinzu. Weitere Informationen finden Sie unter [Define an Article](../../relational-databases/replication/publish/define-an-article.md).  
  
3.  Starten Sie über die Befehlszeile oder in einer Batchdatei die [Replikationsmomentaufnahme-Agent](../../relational-databases/replication/agents/replication-snapshot-agent.md) durch Ausführen von **snapshot.exe**, die folgenden Befehlszeilenargumente angeben:  
  
    -   **-Publication**  
  
    -   **-Publisher**  
  
    -   **-Distributor**  
  
    -   **-PublisherDB**  
  
    -   **-ReplicationType**  
  
     Wenn Sie die SQL Server-Authentifizierung verwenden, müssen Sie auch die folgenden Argumente angeben:  
  
    -   **-DistributorLogin**  
  
    -   **-DistributorPassword**  
  
    -   **-DistributorSecurityMode** = **0**  
  
    -   **-PublisherLogin**  
  
    -   **-PublisherPassword**  
  
    -   **-PublisherSecurityMode** = **0**  
  
###  <a name="TsqlExample"></a> Beispiele (Transact-SQL)  
 Dieses Beispiel zeigt, wie Sie eine Transaktionspublikation erstellen, und fügen einen Snapshot-Agent-Auftrag für die neue Veröffentlichung (mit **Sqlcmd** Skriptvariablen). Im Beispiel wird der Auftrag auch gestartet.  
  
 [!code-sql[HowTo#sp_trangenerate_snapshot](../../relational-databases/replication/codesnippet/tsql/create-and-apply-the-ini_1.sql)]  
  
 In diesem Beispiel wird eine Mergeveröffentlichung erstellt und fügt einen Snapshot-Agent-Auftrag (mit **Sqlcmd** Variablen) für die Veröffentlichung. Im Beispiel wird der Auftrag auch gestartet.  
  
 [!code-sql[HowTo#sp_mergegenerate_snapshot](../../relational-databases/replication/codesnippet/tsql/create-and-apply-the-ini_2.sql)]  
  
 Die folgenden Befehlszeilenargumente starten den Momentaufnahme-Agent, um die Momentaufnahme für eine Mergeveröffentlichung zu generieren.  
  
> [!NOTE]  
>  Zeilenumbrüche wurden hinzugefügt, um die Lesbarkeit zu verbessern. In einer Batchdatei müssen Befehle in einer einzelnen Zeile stehen.  
  
```  
  
REM -- Declare variables  
SET Publisher=%InstanceName%  
SET PublicationDB=AdventureWorks2012   
SET Publication=AdvWorksSalesOrdersMerge   
  
REM --Start the Snapshot Agent to generate the snapshot for AdvWorksSalesOrdersMerge.  
"C:\Program Files\Microsoft SQL Server\120\COM\SNAPSHOT.EXE" -Publication %Publication%   
-Publisher %Publisher% -Distributor %Publisher% -PublisherDB %PublicationDB%   
-ReplicationType 2 -OutputVerboseLevel 1 -DistributorSecurityMode 1  
  
```  
  
##  <a name="RMOProcedure"></a> Verwenden von Replikationsverwaltungsobjekten (RMO)  
 Momentaufnahmen werden nach dem Erstellen einer Veröffentlichung vom Momentaufnahme-Agent generiert. Sie können diese Momentaufnahmen mit Replikationsverwaltungsobjekten (RMO) und dem direkten Zugriff von verwaltetem Code auf Funktionen des Replikations-Agents programmgesteuert generieren. Welche Objekte Sie verwenden, hängt vom Typ der Replikation ab. Der Momentaufnahme-Agent kann synchron mit dem <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> -Objekt oder asynchron mit dem Agentauftrag gestartet werden. Nachdem die Anfangsmomentaufnahme generiert wurde, wird sie an den Abonnenten übertragen und auf diesen angewendet, sobald die erste Synchronisierung für das Abonnement durchgeführt wird. Sie müssen den Agent immer dann erneut ausführen, wenn die vorhandene Momentaufnahme keine gültigen und aktuellen Daten mehr enthält. Weitere Informationen finden Sie unter [Publikationen verwalten](../../relational-databases/replication/publish/maintain-publications.md).  
  
> [!IMPORTANT]  
>  Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Sie Anmeldeinformationen speichern müssen, verwenden Sie die [Kryptografiedienste](http://go.microsoft.com/fwlink/?LinkId=34733) von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows .NET Framework.  
  
#### So generieren Sie die Anfangsmomentaufnahme für eine Momentaufnahme- oder Transaktionsveröffentlichung durch Starten des Auftrags des Momentaufnahme-Agents (asynchron)  
  
1.  Erstellen Sie eine Verbindung mit dem Verleger mithilfe der <xref:Microsoft.SqlServer.Management.Common.ServerConnection> Klasse.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.TransPublication> Klasse. Legen Sie die <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> und <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> Eigenschaften für die Veröffentlichung, und legen die <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> -Eigenschaft auf die in Schritt 1 erstellte Verbindung.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> Methode, um die übrigen Eigenschaften des Objekts zu laden. Wenn diese Methode **false**zurückgibt, sind die Veröffentlichungseigenschaften in Schritt 2 falsch definiert, oder die Veröffentlichung ist nicht vorhanden.  
  
4.  Wenn der Wert der <xref:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists%2A> ist **false**, rufen Sie <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> der Momentaufnahme-Agentauftrag für diese Veröffentlichung zu erstellen.  
  
5.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob%2A> Methode, um den Agent-Auftrag zu starten, die Momentaufnahme für diese Veröffentlichung generiert.  
  
6.  (Optional) Wenn der Wert der <xref:Microsoft.SqlServer.Replication.TransPublication.SnapshotAvailable%2A> ist **true**, des Snapshots für Abonnenten verfügbar ist.  
  
#### So generieren Sie die Anfangsmomentaufnahme für eine Momentaufnahme- oder Transaktionsveröffentlichung durch Ausführen des Momentaufnahme-Agents (synchron)  
  
1.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> -Klasse, und legen Sie die folgenden erforderlichen Eigenschaften fest:  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publisher%2A> - Name des Verlegers  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherDatabase%2A> - Name der Veröffentlichungsdatenbank  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publication%2A> - Name der Veröffentlichung  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Distributor%2A> - Name des Verteilers  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherSecurityMode%2A> -Wert <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> Windows-Authentifizierung verwenden, wenn eine Verbindung mit dem Verleger oder der Wert <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> und Werte für <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherLogin%2A> und <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherPassword%2A> mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung beim Verbinden mit dem Verleger. Die Windows-Authentifizierung wird empfohlen.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorSecurityMode%2A> -Wert <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> auf Windows-Authentifizierung verwenden, wenn eine Verbindung mit dem Verteiler oder einen Wert von <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> und Werte für <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorLogin%2A> und <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorPassword%2A> mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung, wenn die Verbindung zum Verteiler. Die Windows-Authentifizierung wird empfohlen.  
  
2.  Legen Sie den Wert <xref:Microsoft.SqlServer.Replication.ReplicationType.Transactional> oder <xref:Microsoft.SqlServer.Replication.ReplicationType.Snapshot> für <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.ReplicationType%2A>.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.GenerateSnapshot%2A> -Methode auf.  
  
#### So generieren Sie die Anfangsmomentaufnahme für eine Mergeveröffentlichung durch Starten des Auftrags des Momentaufnahme-Agents (asynchron)  
  
1.  Erstellen Sie eine Verbindung mit dem Verleger mithilfe der <xref:Microsoft.SqlServer.Management.Common.ServerConnection> Klasse.  
  
2.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.MergePublication> Klasse. Legen Sie die <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> und <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> Eigenschaften für die Veröffentlichung, und legen die <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> -Eigenschaft auf die in Schritt 1 erstellte Verbindung.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> Methode, um die übrigen Eigenschaften des Objekts zu laden. Wenn diese Methode **false**zurückgibt, sind die Veröffentlichungseigenschaften in Schritt 2 falsch definiert, oder die Veröffentlichung ist nicht vorhanden.  
  
4.  Wenn der Wert der <xref:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists%2A> ist **false**, rufen Sie <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> der Momentaufnahme-Agentauftrag für diese Veröffentlichung zu erstellen.  
  
5.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob%2A> Methode, um den Agent-Auftrag zu starten, die Momentaufnahme für diese Veröffentlichung generiert.  
  
6.  (Optional) Wenn der Wert der <xref:Microsoft.SqlServer.Replication.MergePublication.SnapshotAvailable%2A> ist **true**, des Snapshots für Abonnenten verfügbar ist.  
  
#### So generieren Sie die Anfangsmomentaufnahme für eine Mergeveröffentlichung durch Ausführen des Momentaufnahme-Agents (synchron)  
  
1.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> -Klasse, und legen Sie die folgenden erforderlichen Eigenschaften fest:  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publisher%2A> - Name des Verlegers  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherDatabase%2A> - Name der Veröffentlichungsdatenbank  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publication%2A> - Name der Veröffentlichung  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Distributor%2A> - Name des Verteilers  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherSecurityMode%2A> -Wert <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> Windows-Authentifizierung verwenden, wenn eine Verbindung mit dem Verleger oder der Wert <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> und Werte für <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherLogin%2A> und <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherPassword%2A> mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung beim Verbinden mit dem Verleger. Die Windows-Authentifizierung wird empfohlen.  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorSecurityMode%2A> -Wert <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> auf Windows-Authentifizierung verwenden, wenn eine Verbindung mit dem Verteiler oder einen Wert von <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> und Werte für <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorLogin%2A> und <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorPassword%2A> mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung, wenn die Verbindung zum Verteiler. Die Windows-Authentifizierung wird empfohlen.  
  
2.  Legen Sie den Wert <xref:Microsoft.SqlServer.Replication.ReplicationType.Merge> für <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.ReplicationType%2A>.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.GenerateSnapshot%2A> -Methode auf.  
  
###  <a name="PShellExample"></a> Beispiele (RMO)  
 In diesem Beispiel wird der Momentaufnahme-Agent synchron ausgeführt, um die Anfangsmomentaufnahme für eine Transaktionsveröffentlichung zu generieren.  
  
 [!code-csharp[HowTo#rmo_GenerateSnapshot](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_generatesnapshot)]  
  
 [!code-vb[HowTo#rmo_vb_GenerateSnapshot](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_generatesnapshot)]  
  
 In diesem Beispiel wird der Agentauftrag asynchron ausgeführt, um die Anfangsmomentaufnahme für eine Transaktionsveröffentlichung zu generieren.  
  
 [!code-csharp[HowTo#rmo_GenerateSnapshot_WithJob](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_generatesnapshot_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_GenerateSnapshot_WithJob](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_generatesnapshot_withjob)]  
  
## Siehe auch  
 [Erstellen einer Veröffentlichung](../../relational-databases/replication/publish/create-a-publication.md)   
 [Erstellen eines Pullabonnements](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Erstellen eines Pushabonnements](../../relational-databases/replication/create-a-push-subscription.md)   
 [Angeben von Synchronisierungszeitplänen](../../relational-databases/replication/specify-synchronization-schedules.md)   
 [Erstellen und Anwenden der Momentaufnahme](../../relational-databases/replication/create-and-apply-the-snapshot.md)   
 [Initialisieren eines Abonnements mit einer Momentaufnahme](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [Konzepte für Replikationsverwaltungsobjekte (RMO)](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Bewährte Methoden für die Replikationssicherheit](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Konzepte für gespeicherte Systemprozeduren für die Replikation](../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Verwenden von sqlcmd mit Skriptvariablen](../../relational-databases/scripting/use-sqlcmd-with-scripting-variables.md)  
  
  