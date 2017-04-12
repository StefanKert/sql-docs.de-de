---
title: "Planen der &#220;bernahme von In-Memory-OLTP-Funktionen in SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "10/05/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine-imoltp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 041b428f-781d-4628-9f34-4d697894e61e
caps.latest.revision: 4
author: "MightyPen"
ms.author: "genemi"
manager: "jhubbard"
caps.handback.revision: 3
---
# Planen der &#220;bernahme von In-Memory-OLTP-Funktionen in SQL Server
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]


Dieser Artikel beschreibt, auf welche Weise sich die Übernahme von In-Memory-Funktionen auf andere Aspekte Ihres Geschäftssystems auswirkt.



## A. Übernahme von In-Memory-OLTP-Funktionen


In den folgenden Unterabschnitten werden die Faktoren erläutert, die Sie berücksichtigen müssen, wenn Sie planen, In-Memory-Funktionen zu übernehmen und zu implementieren. Viele erläuternde Informationen finden Sie unter:

- [Verwenden von In-Memory-OLTP zur Verbesserung der Leistung Ihrer Anwendung in Azure SQL-Datenbank](https://azure.microsoft.com/documentation/articles/sql-database-in-memory-oltp-migration/)



### A.1 Erforderliche Komponenten

Eine erforderliche Komponente für die Verwendung der In-Memory-Funktionen kann die Edition oder Dienstebene des SQL-Produkts umfassen. Diese und andere erforderliche Komponenten finden Sie unter:

- [Anforderungen für die Verwendung von speicheroptimierten Tabellen](../../relational-databases/in-memory-oltp/requirements-for-using-memory-optimized-tables.md)
    - [Editionen und Komponenten von SQL Server 2016](../../sql-server/editions-and-components-of-sql-server-2016.md)
    - [SQL-Datenbank-Tarifempfehlungen](https://azure.microsoft.com/documentation/articles/sql-database-service-tier-advisor/)


### A.2 Prognose der Menge an aktivem Arbeitsspeicher

Verfügt Ihr System über genügend Arbeitsspeicher zur Unterstützung einer neuen speicheroptimierten Tabelle?

#### Microsoft SQL Server

Eine speicheroptimierte Tabelle mit 200 GB Daten erfordert mehr als 200 GB aktiven Arbeitsspeicher für deren Unterstützung. Vor der Implementierung einer speicheroptimierten Tabelle, die eine große Datenmenge enthält, müssen Sie die Menge an zusätzlichem aktiven Arbeitsspeicher prognostizieren, den Sie Ihrem Servercomputer möglicherweise hinzufügen müssen. Einen Leitfaden für die Schätzung finden Sie unter:

- [Schätzen der Arbeitsspeicheranforderungen speicheroptimierter Tabellen](../../relational-databases/in-memory-oltp/estimate-memory-requirements-for-memory-optimized-tables.md)

#### Azure SQL-Datenbank

Bei einer Datenbank, die im Clouddienst von Azure SQL-Datenbank gehostet wird, wirkt sich die ausgewählte Dienstebene auf die Menge an aktivem Arbeitsspeicher aus, die Ihre Datenbank verwenden darf. Sie sollten planen, die Speicherverwendung Ihrer Datenbank mithilfe einer Warnung zu überwachen. Einzelheiten dazu finden Sie unter:

- [Überwachen des In-Memory-OLTP-Speichers](https://azure.microsoft.com/documentation/articles/sql-database-in-memory-oltp-monitoring/)

#### Speicheroptimierte Tabellenvariablen

Eine Tabellenvariable, die als speicheroptimiert gilt, wird manchmal vor einer herkömmlichen #TempTable bevorzugt, die sich in der Datenbank **tempdb** befindet. Solche Tabellenvariablen können ohne das Verwenden signifikanter Mengen an aktivem Arbeitsspeicher erhebliche Leistungssteigerungen bieten.

### A.3 Die Tabelle muss offline sein, um in „speicheroptimiert“ konvertiert zu werden

Einige Funktionen von ALTER TABLE sind für speicheroptimierte Tabellen verfügbar. Sie können jedoch keine ALTER TABLE-Anweisung ausgeben, um eine datenträgerbasierte Tabelle in eine speicheroptimierte Tabelle zu konvertieren. Stattdessen müssen Sie eine manuellere Vorgehensweise verwenden. Im Folgenden werden verschiedene Methoden zum Konvertieren Ihrer datenträgerbasierenden Tabelle in eine speicheroptimierte Tabelle beschrieben.

#### Manuelle Skripterstellung

Eine Möglichkeit, Ihre datenträgerbasierte Tabelle in eine speicheroptimierte Tabelle zu konvertieren, besteht darin, die erforderlichen Transact-SQL-Schritte selbst zu codieren.


1. Halten Sie die Aktivität der Anwendung an.

2. Führen Sie eine vollständige Sicherung durch.

3. Benennen Sie Ihre datenträgerbasierte Tabelle um.

4. Geben Sie eine CREATE TABLE-Anweisung aus, um Ihre neue speicheroptimierte Tabelle zu erstellen.

5. Wählen Sie mithilfe einer untergeordneten SELECT-Anweisung Teilmengen aus Ihrer datenträgerbasierten Tabelle aus, um diese mithilfe von INSERT INTO in Ihre speicheroptimierte Tabelle einzufügen.

6. Führen Sie die DROP-Anweisung für Ihre datenträgerbasierte Tabelle aus.

7. Führen Sie eine weitere vollständige Sicherung durch.

8. Setzen Sie die Aktivität der Anwendung fort.


#### Ratgeber für die Speicheroptimierung

Das Tool „Ratgeber für die Speicheroptimierung“ kann ein Skript generieren, um bei der Implementierung der Umkehrung einer datenträgerbasierten Tabelle in eine speicheroptimierte Tabelle zu helfen. Das Tool ist als Teil der SQL Server Data Tools (SSDT) installiert.

- [Ratgeber für die Speicheroptimierung](../../relational-databases/in-memory-oltp/memory-optimization-advisor.md)
- [Herunterladen von SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx)


#### DACPAC-Datei

Sie können Ihre Datenbank direkt mithilfe einer von SSDT verwalteten DACPAC-Datei aktualisieren. In SSDT können Sie Änderungen an dem Schema angeben, das in der DACPAC-Datei codiert ist.

Sie arbeiten mit DACPAC-Dateien im Kontext eines Visual Studio-Projekts vom Typ *Datenbank*.

- [Datenschichtanwendungen](../../relational-databases/data-tier-applications/data-tier-applications.md) und DACPAC-Dateien



### A.4 Leitfaden, um herauszufinden, ob In-Memory-OLTP-Funktionen für Ihre Anwendung geeignet sind

Einen Leitfaden, um herauszufinden, ob In-Memory-Funktionen die Leistung Ihrer bestimmten Anwendung verbessern können, finden Sie unter:

- [In-Memory OLTP (Arbeitsspeicheroptimierung)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)



## B. Nicht unterstützte Funktionen

Funktionen, die in bestimmten In-Memory-Szenarios nicht unterstützt werden, werden folgendermaßen beschrieben:

- [Nicht unterstützte SQL Server-Funktionen für In-Memory OLTP](../../relational-databases/in-memory-oltp/unsupported-sql-server-features-for-in-memory-oltp.md)


In den folgenden Unterabschnitten werden einige der wichtigeren, nicht unterstützten Funktionen hervorgehoben.


### B.1 SNAPSHOT einer Datenbank

Nachdem eine speicheroptimierte Tabelle oder ein speicheroptimiertes Modul zum ersten Mal in einer gegebenen Datenbank erstellt wurde, kann niemals ein [SNAPSHOT](../../relational-databases/databases/database-snapshots-sql-server.md) (Momentaufnahme) der Datenbank erstellt werden. Der spezifische Grund dafür ist der folgende:

- Das erste speicheroptimierte Element macht es unmöglich, die letzte Datei der speicheroptimierten FILEGROUP je zu verwerfen, und
- keine Datenbank, die eine Datei in der speicheroptimierten FILEGROUP hat, kann einen SNAPSHOT unterstützen.

Normalerweise kann ein SNAPSHOT für schnelle Testiterationen praktisch sein.


### B.2 Datenbankübergreifende Abfragen

Speicheroptimierte Tabellen bieten keine Unterstützung für [datenbankübergreifende](../../relational-databases/in-memory-oltp/cross-database-queries.md) Transaktionen. Innerhalb einer Transaktion oder Abfrage, die auf eine speicheroptimierte Tabelle zugreift, können Sie nicht gleichzeitig auf eine andere Datenbank zugreifen.

Tabellenvariablen sind nicht transaktional. Aus diesem Grund können [speicheroptimierte Tabellenvariablen](../../relational-databases/in-memory-oltp/faster-temp-table-and-table-variable-by-using-memory-optimization.md) in datenbankübergreifenden Abfragen verwendet werden.


### B.3 READPAST-Tabellenhinweis

Keine Abfrage kann den READPAST-[Tabellenhinweis](Table%20Hints%20%28Transact-SQL%29.md) auf speicheroptimierte Tabellen anwenden.

Der READPAST-Hinweis ist hilfreich bei Szenarios, in denen mehrere Sitzungen jeweils auf den gleichen Satz von Zeilen zugreifen und diesen bearbeiten, sowie bei der Verarbeitung einer Warteschlange.


### B.4 RowVersion, Sequence

- In einer speicheroptimierten Tabelle kann keine Spalte für [RowVersion](../../t-sql/data-types/rowversion-transact-sql.md) markiert werden.


- Ein [SEQUENCE](../../t-sql/statements/create-sequence-transact-sql.md)-Objekt kann nicht mit einer speicheroptimierten Tabelle verwendet werden.


## C. Administrative Wartung


Dieser Abschnitt beschreibt die Unterschiede in der Datenbankverwaltung bei der Verwendung von speicheroptimierten Tabellen.


### C.1 Zurücksetzen des ID-Startwerts, Inkrementwert > 1

[DBCC CHECKIDENT](../../t-sql/database-console-commands/dbcc-checkident-transact-sql.md), um den Startwert einer IDENTITY-Spalte zu korrigieren, kann nicht für eine speicheroptimierte Tabelle verwendet werden.

Der Inkrementwert wird für eine IDENTITÄTSSPALTE in einer speicheroptimierten Tabelle auf genau 1 beschränkt.


### C.2 DBCC CHECKDB kann keine speicheroptimierten Tabellen überprüfen

Der Befehl [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) tut nichts, wenn sein Ziel eine speicheroptimierte Tabelle ist. Dies können Sie mithilfe der folgenden Schritte umgehen:


1. [Sichern Sie das Transaktionsprotokoll](Back%20Up%20a%20Transaction%20Log%20%28SQL Server%29.md).

2. Sichern Sie die Dateien in der speicheroptimierten FILEGROUP auf einem NULL-Gerät. Der Sicherungsvorgang ruft die Prüfsummenverifizierung auf.

    Wenn eine Beschädigung gefunden wird, fahren Sie mit den nächsten Schritten fort.

3. Kopieren Sie Daten aus Ihren speicheroptimierten Tabellen in datenträgerbasierte Tabellen für die temporäre Speicherung.

4. Stellen Sie die Dateien der speicheroptimierten FILEGROUP wieder her.

5. Fügen Sie die Daten, die Sie in den datenträgerbasierten Tabellen temporär gespeichert haben, mithilfe der INSERT INTO-Anweisung in die speicheroptimierten Tabellen ein.

6. Führen Sie eine DROP-Anweisung auf die datenträgerbasierten Tabellen aus, in denen die Daten temporär gespeichert waren.



## D. Leistung

Dieser Abschnitt beschreibt Situationen, in denen die ausgezeichnete Leistung von speicheroptimierten Tabellen unterhalb des Gesamtpotenzials bleiben kann.


### D.1 Index-Überlegungen

Alle Indizes für eine speicheroptimierte Tabelle werden von den tabellenbezogenen Anweisungen CREATE TABLE und ALTER TABLE erstellt und verwaltet. Sie können keine CREATE INDEX-Anweisung auf speicheroptimierte Tabellen anwenden.

Der herkömmliche nicht gruppierte Index in B-Struktur ist häufig die sinnvolle und einfache Wahl, wenn Sie zum ersten Mal eine speicheroptimierte Tabelle implementieren. Später, nachdem Sie gesehen haben, wie Ihre Anwendung ausgeführt wird, können Sie in Betracht ziehen, zu einem anderen Indextyp zu wechseln.

Zwei besondere Indextypen erfordern im Kontext einer speicheroptimierten Tabelle eine Erläuterung: Hashindizes und Columnstore-Indizes.

Eine Übersicht über Indizes bei speicheroptimierten Tabellen finden Sie unter:

- [Indizes für speicheroptimierte Tabellen](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md)


#### Hashindizes

Hashindizes können das schnellste Format darstellen, um auf eine bestimmte Zeile mit ihrem exakten Primärschlüssel zuzugreifen, indem der „**=**“-Operator verwendet wird.

- Ungenaue Operatoren, wie z.B. „**!=**“, „**>**“ oder „**BETWEEN**“ würden die Leistung beeinträchtigen, wenn Sie mit einem Hashindex verwendet werden.

- Ein Hashindex stellt möglicherweise nicht die beste Wahl dar, wenn die Rate der Schlüsselwertduplizierung zu hoch wird.

- Schützen Sie sich vor der Unterschätzung, wie viele *Buckets* Ihr Hashindex benötigen könnte, um lange Ketten innerhalb einzelner Buckets zu vermeiden. Einzelheiten dazu finden Sie unter:
    - [Hashindizes für speicheroptimierte Tabellen](../../relational-databases/in-memory-oltp/hash-indexes-for-memory-optimized-tables.md)


#### Nicht gruppierte Columnstore-Indizes

Speicheroptimierte Tabellen bieten einen hohen Durchsatz von typischen Geschäftstransaktionsdaten, die wir im Paradigma als *Onlinetransaktionsverarbeitung* oder *OLTP* bezeichnen. Columnstore-Indizes bieten einen hohen Durchsatz von Aggregationen und ähnlichen Verarbeitungen, die wir als *Analysen* bezeichnen. In den vergangenen Jahren bestand die bestmögliche Methode, dem Bedarf von sowohl OLTP als auch Analysen gerecht zu werden, darin, über getrennte Tabellen mit intensiver Datenverschiebung und mit einem gewissen Grad an Datenduplizierung zu verfügen. Heutzutage ist eine einfachere **Hybridlösung** verfügbar, und zwar das Verfügen über einen Columnstore-Index in einer speicheroptimierten Tabelle.


- Ein [Columnstore-Index](Columnstore%20Indexes%20Guide.md) kann in einer datenträgerbasierten Tabelle erstellt werden, sogar als gruppierter Index. In einer speicheroptimierten Tabelle kann ein Columnstore-Index jedoch nicht gruppiert werden.


- LOB-Spalten oder Spalten außerhalb von Zeilen verhindern in einer speicheroptimierten Tabelle die Erstellung eines Columnstore-Indizes in der Tabelle.


- Es kann keine ALTER TABLE-Anweisung auf eine speicheroptimierte Tabelle ausgeführt werden, während ein Columnstore-Index in der Tabelle vorhanden ist.
    - Ab August 2016 plant Microsoft kurzfristig, die Leistung bei der Neuerstellung des Columnstore-Indizes zu verbessern.



### D.2 LOB-Spalten und Spalten außerhalb von Zeilen

Large Objects (LOBs) sind Spalten von z.B. dem Typ varchar (**max**). Das Verfügen über eine Reihe von LOB-Spalten in einer speicheroptimierten Tabelle beeinträchtigt die Leistung wahrscheinlich nicht so sehr, dass es eine Rolle spielt. Verhindern Sie jedoch, mehr LOB-Spalten zu haben, als Ihre Daten benötigen. Der gleiche Rat gilt für Spalten außerhalb von Zeilen. Definieren Sie eine Spalte nicht als nvarchar(3072), wenn varchar(512) ausreichen würde.


Weitere Informationen zu LOB-Spalten und Spalten außerhalb von Zeilen finden Sie unter:

- [Tabellen- und Zeilengröße in speicheroptimierten Tabellen](../../relational-databases/in-memory-oltp/table-and-row-size-in-memory-optimized-tables.md)
- [Unterstützte Datentypen für In-Memory OLTP](../../relational-databases/in-memory-oltp/supported-data-types-for-in-memory-oltp.md)



## E. Einschränkungen von nativen Prozeduren


Bestimmte Elemente von Transact-SQL werden in nativ kompilierten gespeicherten Prozeduren nicht unterstützt.

Überlegungen zur Migration eines Transact-SQL-Skripts zu einer nativen Prozedur finden Sie unter:

- [Migrationsprobleme bei systemintern kompilierten gespeicherten Prozeduren](../../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md)


### E.1 Kein CASE-Ausdruck in einer nativen Prozedur

Der CASE-Ausdruck in Transact-SQL kann nicht innerhalb einer nativen Prozedur verwendet werden. Sie können dies umgehen:

- [Implementieren eines CASE-Ausdrucks in einer systemintern kompilierten gespeicherten Prozedur](../../relational-databases/in-memory-oltp/implementing-a-case-expression-in-a-natively-compiled-stored-procedure.md)


### E.2 Keine MERGE-Anweisung in einer nativen Prozedur


Die [MERGE-Anweisung](../../t-sql/statements/merge-transact-sql.md) von Transact-SQL ähnelt der oft als *UPSERT* bezeichneten Funktion. Eine native Prozedur kann die MERGE-Anweisung nicht verwenden. Sie können jedoch die gleiche Funktion wie MERGE erreichen, indem Sie eine Kombination aus den Anweisungen SELECT, UPDATE und INSERT verwenden. Ein Codebeispiel finden Sie unter:

- [Implementieren von MERGE-Funktionalität in einer nativ kompilierten gespeicherten Prozedur](../../relational-databases/in-memory-oltp/implementing-merge-functionality-in-a-natively-compiled-stored-procedure.md)



### E.3 Keine Joins in UPDATE- oder DELETE-Anweisungen in einer nativen Prozedur

Transact-SQL-Anweisungen in einer nativen Prozedur können nur auf speicheroptimierte Tabellen zugreifen. In UPDATE- und DELETE-Anweisungen können Sie keine Tabellen verknüpfen. Bei Versuchen in einer nativen Prozedur tritt ein Fehler mit einer Meldung wie z.B. Meldung 12319 auf, die Folgendes erklärt:

- Die FROM-Klausel kann nicht in einer UPDATE-Anweisung verwendet werden.
- Eine Tabellenquelle kann nicht in einer DELETE-Anweisung angegeben werden.

Dies kann mit keinem Unterabfragentyp umgangen werden. Sie können eine speicheroptimierte Tabellenvariable jedoch dazu verwenden, ein Join-Ergebnis über mehrere Anweisungen zu erreichen. Es folgen zwei Codebeispiele:

- DELETE...JOIN... möchten wir in einer nativen Prozedur ausführen, können wir jedoch nicht.
- Eine Reihe von Transact-SQL-Anweisungen zur Umgehung, die das Löschen des Joins erreichen.


*Szenario:* Die Tabelle TabProjectEmployee besitzt einen eindeutigen Schlüssel von zwei Spalten: ProjectId und EmployeeId. Jede Zeile gibt die Zuordnung eines Mitarbeiters zu einem aktiven Projekt an. Wenn ein Mitarbeiter das Unternehmen verlässt, muss der Mitarbeiter aus der Tabelle TabProjectEmployee gelöscht werden.


#### Ungültige T-SQL-, DELETE...JOIN-Anweisungen


Eine native Prozedur kann über keine DELETE...JOIN-Anweisung wie die folgende verfügen.


```tsql
DELETE pe
    FROM
             TabProjectEmployee   AS pe
        JOIN TabEmployee          AS e

            ON pe.EmployeeId = e.EmployeeId
    WHERE
            e.EmployeeStatus = 'Left-the-Company'
;
```


#### Gültige Umgehung, manuelles Ausführen von DELETE...JOIN

Als Nächstes folgt das Codebeispiel für die Umgehung in zwei Teilen:

1. Die CREATE TYPE-Anweisung wird einmal einige Tage vor der ersten Verwendung des Typs durch eine tatsächliche Tabellenvariable ausgeführt.

2. Der Geschäftsprozess verwendet den erstellten Typ. Zunächst wird eine Tabellenvariable des erstellten Tabellentyps deklariert.


```tsql

CREATE TYPE dbo.type_TableVar_EmployeeId
    AS TABLE  
    (
        EmployeeId   bigint   NOT NULL
    );
```


Als Nächstes verwenden Sie den CREATE TABLE-Typ.


```tsql
DECLARE @MyTableVarMo  dbo.type_TableVar_EmployeeId  

INSERT INTO @MyTableVarMo (EmployeeId)
    SELECT
            e.EmployeeId
        FROM
                 TabProjectEmployee  AS pe
            JOIN TabEmployee         AS e  ON e.EmployeeId = pe.EmployeeId
        WHERE
            e.EmployeeStatus = 'Left-the-Company'
;

DECLARE @EmployeeId   bigint;

WHILE (1=1)
BEGIN
    SET @EmployeeId = NULL;

    SELECT TOP 1 @EmployeeId = v.EmployeeId
        FROM @MyTableVarMo  AS v;

    IF (NULL = @Employeed) BREAK;
    
    DELETE TabProjectEmployee
        WHERE EmployeeId = @EmployeeId;

    DELETE @MyTableVarMo
        WHERE EmployeeId = @EmployeeId;
END;
```


### E.4 Abfrageplaneinschränkungen für native Prozeduren


Einige Typen von Abfrageplänen sind für native Prozeduren nicht verfügbar. Viele Details werden im folgenden Artikel erläutert:

- [Anleitung zur Abfrageverarbeitung für speicheroptimierte Tabellen](../../relational-databases/in-memory-oltp/a-guide-to-query-processing-for-memory-optimized-tables.md)


#### Keine parallele Verarbeitung in einer nativen Prozedur

Die Parallele Verarbeitung kann nicht Teil eines Abfrageplans für eine native Prozedur sein. Native Prozeduren sind immer auf einen Thread beschränkt.


#### Join-Typen


Weder ein Hashjoin noch ein Zusammenführungsjoin kann Teil eines Abfrageplans für eine native Prozedur sein. Joins geschachtelter Schleifen werden verwendet.


#### Keine Hashaggregation

Wenn der Abfrageplan für eine native Prozedur eine Aggregationsphase erfordert, steht nur die Stream-Aggregation zur Verfügung. Die Hashaggregation wird in einem Abfrageplan für eine native Prozedur nicht unterstützt.

- Die Hashaggregation ist besser, wenn Daten aus einer großen Anzahl von Zeilen aggregiert werden müssen.



## F. Anwendungsentwurf: Transaktionen und Wiederholungslogik

Eine Transaktion, die eine speicheroptimierte Tabelle umfasst, kann von einer anderen Transaktion abhängig werden, die die gleiche Tabelle umfasst. Wenn die Anzahl von abhängigen Transaktionen den zulässigen Höchstwert überschreitet, tritt bei allen abhängigen Transaktionen ein Fehler auf.

Bei SQL Server 2016:

- beträgt das zulässige Maximum acht abhängige Transaktionen. Acht ist auch der Grenzwert von Transaktionen, von denen alle gegebenen Transaktionen abhängig sein können.
- ist die Fehlernummer 41839 (In SQL Server 2014 ist die Fehlernummer 41301).


Sie können die Transact-SQL-Skripts stabiler gegenüber einem möglichen Transaktionsfehler machen, indem Sie die *Wiederholungslogik* zu Ihren Skripts hinzufügen. Die Wiederholungslogik hilft mit größerer Wahrscheinlichkeit, wenn UPDATE- und DELETE-Aufrufe häufig sind, oder wenn durch einen Fremdschlüssel in einer anderen Tabelle auf die speicheroptimierte Tabelle verwiesen wird. Einzelheiten dazu finden Sie unter:

- [Transaktionen mit speicheroptimierten Tabellen](../../relational-databases/in-memory-oltp/transactions-with-memory-optimized-tables.md)
- [Transaction dependency limits with memory optimized tables – Error 41839 (Transaktionsabhängigkeitsgrenzen bei speicheroptimierten Tabellen – Fehler 41839)](https://blogs.msdn.microsoft.com/sqlcat/2016/07/11/transaction-dependency-limits-with-memory-optimized-tables-error-41839/)



## Verwandte Links

- [In-Memory OLTP (Arbeitsspeicheroptimierung)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)
