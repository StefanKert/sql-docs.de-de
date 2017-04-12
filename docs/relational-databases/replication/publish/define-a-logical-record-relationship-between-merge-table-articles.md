---
title: "Definieren einer logische Datensatzbeziehung zwischen Mergetabellenartikeln | Microsoft Docs"
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
  - "Logische Datensätze für die Mergereplikation [SQL Server-Replikation]"
  - "Artikel [SQL Server-Replikation], logische Datensätze "
  - "Logische Datensätze [SQL Server-Replikation]"
ms.assetid: ff847b3a-c6b0-4eaf-b225-2ffc899c5558
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# Definieren einer logische Datensatzbeziehung zwischen Mergetabellenartikeln
  In diesem Thema wird beschrieben, wie eine logische Datensatzbeziehung zwischen Mergetabellenartikeln in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] oder Replikationsverwaltungsobjekten (RMO) definiert wird.  
  
 Mergereplikation ermöglicht Ihnen, eine Beziehung zwischen verknüpften Zeilen in verschiedenen Tabellen zu definieren. Diese Zeilen können dann während der Synchronisierung als Transaktionseinheit verarbeitet werden. Eine logische Datensatzbeziehung zwischen zwei Artikeln kann unabhängig davon definiert werden, ob sie über eine Joinfilterbeziehung verfügen oder nicht. Weitere Informationen finden Sie unter [Gruppieren Sie Änderungen an verknüpften Zeilen mithilfe von logischen Datensätzen](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
-   **So definieren Sie eine logische Datensatzbeziehung zwischen Mergetabellenartikeln mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Replikationsverwaltungsobjekte (RMO)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Wenn Sie einen logischen Datensatz hinzufügen, ändern oder löschen, nachdem Abonnements für die Veröffentlichung initialisiert wurden, müssen Sie eine neue Momentaufnahme generieren und alle Abonnements nach vorgenommener Änderung erneut initialisieren. Weitere Informationen zu den Anforderungen für eigenschaftenänderungen finden Sie unter [Ändern von Veröffentlichungs- und Artikeleigenschaften](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
##  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
 Definieren logischer Datensätze in der **Join hinzufügen** Dialogfeld, das im Assistenten für neue Veröffentlichung verfügbar ist und die **Veröffentlichungseigenschaften - \< Veröffentlichung>** (Dialogfeld). Weitere Informationen zum Verwenden des Assistenten sowie Zugriff auf das Dialogfeld finden Sie unter [Erstellen Sie eine Veröffentlichung](../../../relational-databases/replication/publish/create-a-publication.md) und [anzeigen und Ändern von Veröffentlichungseigenschaften](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
 Logische Datensätze können nur dann im Dialogfeld **Join hinzufügen** definiert werden, wenn sie auf einen Joinfilter in einer Mergeveröffentlichung angewendet werden und die Veröffentlichung die Anforderungen für die Verwendung vorausberechneter Partitionen erfüllt. Wenn Sie logische Datensätze definieren möchten, die nicht auf Joinfilter angewendet werden, und die Konflikterkennung und -lösung auf der Ebene des logischen Datensatzes festlegen möchten, müssen Sie gespeicherte Prozeduren verwenden.  
  
#### So definieren Sie eine logische Datensatzbeziehung  
  
1.  Auf der **Tabellenzeilen filtern** Seite des Assistenten für neue Veröffentlichung oder **Filterzeilen** auf der Seite der **Veröffentlichungseigenschaften - \< Veröffentlichung>** Wählen Sie im Dialogfeld einen Zeilenfilter in der **Gefilterte Tabellen** Bereich.  
  
     Logische Datensatzbeziehungen sind mit einem Joinfilter verknüpft, der wiederum einen Zeilenfilter erweitert. Sie müssen daher zuerst einen Zeilenfilter definieren, bevor Sie den Filter mit einem Join erweitern und eine logische Datensatzbeziehung anwenden können. Nach dem Definieren eines Joinfilters können Sie diesen Joinfilter wiederum um einen anderen Joinfilter erweitern. Weitere Informationen zum Definieren von Joinfiltern finden Sie unter [Define and Modify a Join Filter Between Merge Articles](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
2.  Klicken Sie auf **Hinzufügen**und anschließend auf **Join hinzufügen, um den ausgewählten Filter zu erweitern**.  
  
3.  Definieren Sie im Dialogfeld **Join hinzufügen** einen Joinfilter, und aktivieren Sie dann das Kontrollkästchen **Logischer Datensatz**.  
  
4.  Wenn Sie haben die **Veröffentlichungseigenschaften - \< Veröffentlichung>** Klicken Sie im Dialogfeld klicken Sie auf **OK** zum Speichern und schließen das Dialogfeld.  
  
#### So löschen Sie eine logische Datensatzbeziehung  
  
-   Sie können entweder nur die logische Datensatzbeziehung oder die logische Datensatzbeziehung und den zugeordneten Joinfilter gemeinsam löschen.  
  
     So löschen Sie nur die logische Datensatzbeziehung:  
  
    1.  Auf der **Filterzeilen** Seite des Assistenten für neue Veröffentlichung oder **Filterzeilen** auf der Seite der **Veröffentlichungseigenschaften - \< Veröffentlichung>** Wählen Sie im Dialogfeld der Verknüpfungsfilter die logische datensatzbeziehung in zugeordneten der **Gefilterte Tabellen** Bereich, und klicken Sie dann auf **Bearbeiten**.  
  
    2.  Deaktivieren Sie im Dialogfeld **Join bearbeiten** die Option **Logischer Datensatz**.  
  
    3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     So löschen Sie die logische Datensatzbeziehung und den zugeordneten Joinfilter:  
  
    -   Auf der **Filterzeilen** Seite des Assistenten für neue Veröffentlichung oder **Veröffentlichungseigenschaften - \< Veröffentlichung>** Dialogfeld Wählen Sie einen Filter in der **Gefilterte Tabellen** Bereich, und klicken Sie dann auf **Löschen**. Wenn der Joinfilter, den Sie löschen möchten, mit anderen Joins erweitert ist, werden diese Joins beim Löschen des Filters selbst ebenfalls gelöscht.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Sie können logische Datensatzbeziehungen zwischen Artikeln programmgesteuert mithilfe gespeicherter Replikationsprozeduren angeben.  
  
#### So definieren Sie eine logische Datensatzbeziehung ohne einen zugeordneten Joinfilter  
  
1.  Wenn die Veröffentlichung Artikel, die gefiltert werden enthält, führen Sie [Sp_helpmergepublication](../../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md), und notieren Sie sich den Wert der **Use_partition_groups** im Ergebnis festlegen.  
  
    -   Wenn der Wert **1**ist, dann werden bereits vorausberechnete Partitionen verwendet.  
  
    -   Wenn der Wert **0**, führen Sie dann [Sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md) auf dem Verleger für die Veröffentlichungsdatenbank. Geben Sie den Wert **Use_partition_groups** für **@property** und einem Wert von **true** für **@value**.  
  
        > [!NOTE]  
        >  Wenn die Veröffentlichung keine vorausberechneten Partitionen unterstützt, dann können keine logischen Datensätze verwendet werden. Weitere Informationen finden Sie unter Anforderungen für Vorausberechnete Partitionen mithilfe des Themas [parametrisierte Filter Leistung mit Vorausberechnete Partitionen optimieren](../../../relational-databases/replication/merge/optimize-parameterized-filter-performance-with-precomputed-partitions.md).  
  
    -   Ist der Wert NULL, muss der Momentaufnahme-Agent ausgeführt werden, um die Momentaufnahme für die Veröffentlichung zu generieren.  
  
2.  Wenn die Artikel, die den logischen Datensatz umfassen, nicht vorhanden sind, führen [Sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) auf dem Verleger für die Veröffentlichungsdatenbank. Geben Sie eine der folgenden Konflikterkennungs- und -lösungsoptionen für den logischen Datensatz an:  
  
    -   Zum Erkennen und Lösen von Konflikten, die innerhalb verknüpfter Zeilen im logischen Datensatz auftreten, geben Sie den Wert **true** für **@logical_record_level_conflict_detection** und **@logical_record_level_conflict_resolution**.  
  
    -   Um die standardmäßigen Zeilen- oder Spaltenebene Erkennung und Auflösung zu verwenden, geben Sie den Wert **false** für **@logical_record_level_conflict_detection** und **@logical_record_level_conflict_resolution**, dies ist die Standardeinstellung.  
  
3.  Wiederholen Sie Schritt 2 für jeden Artikel, der den logischen Datensatz umfasst. Sie müssen für jeden Artikel im logischen Datensatz die gleiche Konflikterkennung und Konfliktlösungsoption verwenden. Weitere Informationen finden Sie unter [Detecting and Resolving Conflicts in Logical Records](../../../relational-databases/replication/merge/detecting-and-resolving-conflicts-in-logical-records.md).  
  
4.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [Sp_addmergefilter](../../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md). Geben Sie **@publication**, den Namen eines Artikels, der in der Beziehung für **@article**, den Namen des zweiten Artikel für **@join_articlename**, einen Namen für die Beziehung für **@filtername**, eine Klausel, die die Beziehung zwischen den beiden definiert, die für Artikel **@join_filterclause**, die Art der Verknüpfung für **@join_unique_key** und einen der folgenden Werte für **@filter_type**:  
  
    -   **2** -definiert eine logische Beziehung.  
  
    -   **3** -definiert eine logische Beziehung mit einem joinfilter.  
  
    > [!NOTE]  
    >  Wird kein Joinfilter verwendet, ist die Richtung der Beziehung zwischen den beiden Artikeln nicht wichtig.  
  
5.  Wiederholen Sie Schritt 2 für jede weitere logische Datensatzbeziehung in der Veröffentlichung.  
  
#### So ändern Sie die Konflikterkennung und -lösung für logische Datensätze  
  
1.  So erkennen und lösen Sie Konflikte, die innerhalb verknüpfter Zeilen im logischen Datensatz auftreten:  
  
    -   Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [Sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Geben Sie den Wert **Logical_record_level_conflict_detection** für **@property** und einem Wert von **true** für **@value**. Geben Sie den Wert **1** für **@force_invalidate_snapshot** und **@force_reinit_subscription**.  
  
    -   Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [Sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Geben Sie den Wert **Logical_record_level_conflict_resolution** für **@property** und einem Wert von **true** für **@value**. Geben Sie den Wert **1** für **@force_invalidate_snapshot** und **@force_reinit_subscription**.  
  
2.  So verwenden Sie die Standard-Konflikterkennung und -lösung auf Zeilen- oder Spaltenebene:  
  
    -   Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [Sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Geben Sie den Wert **Logical_record_level_conflict_detection** für **@property** und einem Wert von **false** für **@value**. Geben Sie den Wert **1** für **@force_invalidate_snapshot** und **@force_reinit_subscription**.  
  
    -   Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [Sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Geben Sie den Wert **Logical_record_level_conflict_resolution** für **@property** und einem Wert von **false** für **@value**. Geben Sie den Wert **1** für **@force_invalidate_snapshot** und **@force_reinit_subscription**.  
  
#### So entfernen Sie eine logische Datensatzbeziehung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank die folgende Abfrage aus, um alle Informationen über die für die angegebene Veröffentlichung definierten logischen Datensatzbeziehungen zurückzugeben:  
  
     [!code-sql[HowTo#sp_ReturnMergeLogicalRecords](../../../relational-databases/replication/codesnippet/tsql/define-a-logical-record-_1.sql)]  
  
     Achten Sie auf den Namen der zu entfernenden logischen Datensatzbeziehung in der Spalte **filtername** des Resultsets.  
  
    > [!NOTE]  
    >  Diese Abfrage gibt dieselbe Informationen wie [Sp_helpmergefilter](../../../relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql.md)aber diese gespeicherte Prozedur nur gibt Informationen über logische datensatzbeziehungen, die auch joinfilter.  
  
2.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [Sp_dropmergefilter](../../../relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql.md). Geben Sie **@publication**an sowie den Namen eines der an der Beziehung beteiligten Artikel für **@article**und den Namen der Beziehung aus Schritt 1 für **@filtername**.  
  
###  <a name="TsqlExample"></a> Beispiel (Transact-SQL)  
 Im folgenden Beispiel werden vorausberechnete Partitionen für eine vorhandene Veröffentlichung aktiviert und ein logischer Datensatz erstellt, der die zwei neuen Artikel für die Tabellen `SalesOrderHeader` und `SalesOrderDetail` umfasst.  
  
 [!code-sql[HowTo#sp_AddMergeLogicalRecord](../../../relational-databases/replication/codesnippet/tsql/define-a-logical-record-_2.sql)]  
  
##  <a name="RMOProcedure"></a> Verwenden von Replikationsverwaltungsobjekten (RMO)  
  
> [!NOTE]  
>  Bei der Mergereplikation können Sie auch angeben, dass Konflikte auf der Ebene logischer Datensätze nachverfolgt und gelöst werden. Diese Optionen können mit RMO jedoch nicht festgelegt werden.  
  
#### So definieren Sie eine logische Datensatzbeziehung ohne einen zugeordneten Joinfilter  
  
1.  Erstellen Sie eine Verbindung mit dem Verleger mithilfe der <xref:Microsoft.SqlServer.Management.Common.ServerConnection> Klasse.  
  
2.  Erstellen Sie eine Instanz von der <xref:Microsoft.SqlServer.Replication.MergePublication> Klasse, legen die <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> und <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> Eigenschaften für die Veröffentlichung, und legen die <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> -Eigenschaft auf die in Schritt 1 erstellte Verbindung.  
  
3.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> Methode zum Abrufen der Eigenschaften des Objekts. Wenn diese Methode **false**zurückgibt, sind die Veröffentlichungseigenschaften in Schritt 2 falsch definiert, oder die Veröffentlichung ist nicht vorhanden.  
  
4.  Wenn die <xref:Microsoft.SqlServer.Replication.MergePublication.PartitionGroupsOption%2A> -Eigenschaft wird festgelegt, um <xref:Microsoft.SqlServer.Replication.PartitionGroupsOption.False>, legen Sie es auf <xref:Microsoft.SqlServer.Replication.PartitionGroupsOption.True>.  
  
5.  Wenn die Artikel, die den logischen Datensatz umfassen nicht vorhanden sind, erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.MergeArticle> Klasse, und legen Sie die folgenden Eigenschaften:  
  
    -   Der Name des Artikels für <xref:Microsoft.SqlServer.Replication.Article.Name%2A>.  
  
    -   Der Name der Veröffentlichung für <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>.  
  
    -   (Optional) Wenn der Artikel horizontal gefiltert wird, geben Sie die Zeilenfilterklausel für die <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> Eigenschaft. Verwenden Sie diese Eigenschaft, um einen statischen oder parametrisierten Zeilenfilter anzugeben. Weitere Informationen finden Sie unter [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
     Weitere Informationen finden Sie unter [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
6.  Rufen Sie die <xref:Microsoft.SqlServer.Replication.Article.Create%2A> Methode.  
  
7.  Wiederholen Sie die Schritte 5 und 6 für jeden Artikel, der den logischen Datensatz umfasst.  
  
8.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> Klasse, um die logische datensatzbeziehung zwischen Artikeln definieren. Legen Sie dann die folgenden Eigenschaften fest:  
  
    -   Der Name des untergeordneten Artikels in der logischen datensatzbeziehung für die <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.ArticleName%2A> Eigenschaft.  
  
    -   Der Name des bestehenden übergeordneten Artikels in der logischen datensatzbeziehung für die <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.JoinArticleName%2A> Eigenschaft.  
  
    -   Einen Namen für die logische datensatzbeziehung für die <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.FilterName%2A> Eigenschaft.  
  
    -   Der Ausdruck, die Beziehung für definiert, die <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.JoinFilterClause%2A> Eigenschaft.  
  
    -   Der Wert <xref:Microsoft.SqlServer.Replication.FilterTypes.LogicalRecordLink> für die <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.FilterTypes%2A> Eigenschaft. Wenn die logische datensatzbeziehung auch ein joinfilter ist, geben Sie den Wert <xref:Microsoft.SqlServer.Replication.FilterTypes.JoinFilterAndLogicalRecordLink> für diese Eigenschaft. Weitere Informationen finden Sie unter [Gruppieren Sie Änderungen an verknüpften Zeilen mithilfe von logischen Datensätzen](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
9. Rufen Sie die <xref:Microsoft.SqlServer.Replication.MergeArticle.AddMergeJoinFilter%2A> Methode für das Objekt, das den untergeordneten Artikel in der Beziehung darstellt. Übergeben Sie die <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> -Objekt aus Schritt 8, um die Beziehung zu definieren.  
  
10. Wiederholen Sie die Schritte 8 und 9 für jede weitere logische Datensatzbeziehung in der Veröffentlichung.  
  
###  <a name="PShellExample"></a> Beispiel (RMO)  
 In diesem Beispiel wird ein logischer Datensatz erstellt, der die zwei neuen Artikel für die Tabellen `SalesOrderHeader` und `SalesOrderDetail` umfasst.  
  
 [!code-csharp[HowTo#rmo_CreateLogicalRecord](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createlogicalrecord)]  
  
 [!code-vb[HowTo#rmo_vb_CreateLogicalRecord](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createlogicalrecord)]  
  
## Siehe auch  
 [Definieren und Ändern eines Verknüpfungsfilters zwischen Mergeartikeln](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)   
 [Definieren und Ändern eines parametrisierten Zeilenfilters für einen Mergeartikel](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)   
 [Definieren oder Ändern eines statischen Zeilenfilters](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)   
 [Gruppieren von Änderungen an verknüpften Zeilen mithilfe von logischen Datensätzen](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)   
 [Optimieren der Leistung parametrisierter Filter mithilfe vorausberechneter Partitionen](../../../relational-databases/replication/merge/optimize-parameterized-filter-performance-with-precomputed-partitions.md)   
 [Gruppieren von Änderungen an verknüpften Zeilen mithilfe von logischen Datensätzen](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)  
  
  