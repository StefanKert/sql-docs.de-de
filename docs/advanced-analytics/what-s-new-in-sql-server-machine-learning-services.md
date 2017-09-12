---
title: Was &#39; s in Machine Learning-Dienste | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 07/31/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6aff043a-8b37-4f3f-9827-10a671e1ad1c
caps.latest.revision: 36
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8719ec8be1c0f7b7b0dc72093707829c30ebbb3f
ms.contentlocale: de-de
ms.lasthandoff: 09/01/2017

---
# <a name="whats-new-in-machine-learning-services-in-sql-server"></a>Was ist neu in Machine Learning Services in SQL Server

In SQL Server 2016 eingeführt Microsoft SQL Server R Services, eine Funktion, die Enterprise-Skalierung Data Science, durch die Integration von der Sprache "R" mit dem SQL Server-Datenbankmodul unterstützt.

In SQL Server 2017 wird Machine Learning noch leistungsfähiger, durch Hinzufügen der Unterstützung für die beliebten Python-Sprache. Die Unterstützung für neue Sprachen enthalten ist ein neuer Name: **Machine Learning-Services (Datenbankintern)**.

Fangen Sie hier die neueste Ankündigung! [Python in SQL Server-2017: Erweiterte in Datenbank-Machine Learning](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)

## <a name="whats-new-in-sql-server-2017-release-candidate-2"></a>Neuigkeiten in SQL Server 2017 Release Candidate 2

Microsoft Machine Learning-Server in SQL Server bietet jetzt eine umfassende Unterstützung für das Erstellen und Bereitstellen von Machine Learning-Lösungen. Hier sind die wichtigsten dieser Version:

> [!IMPORTANT]
> 
> Machine Learning-Dienste, einschließlich der Verwendung von R oder Python, werden derzeit nicht unterstützt, wenn SQL Server unter Linux oder in Azure SQL-Datenbank ausgeführt. Suchen Sie nach Änderungen in einer späteren Version.
> 
> Allerdings wird native Bewertung mithilfe der PREDICT-Funktion derzeit in der Linux-Edition unterstützt. 
 
### <a name="in-database-python-integration"></a>Python-Integration in der Datenbank

Sie können Python in gespeicherten Prozeduren ausführen oder Python Remote mithilfe von SQL Server-Computers als computekontext auszuführen. Diese Integration eröffnet neue Möglichkeiten für die großen Community von Python Entwicklern und Data Scientists ausnutzen der Leistungsfähigkeit von SQL Server und Innovationen von Microsoft untersuchen, wie z. B. **Revoscalepy** und **Microsoftml**.

SQL Server-Entwickler können Sie zugreifen, die eine umfangreiche Python-Bibliotheken in open-Source-Ökosystem, einschließlich gängigen Frameworks wie Scikit-Tensorflow, Caffe und Theano/Keras finden. 

Aber Python in der Datenbank für den Machine learning wird nicht ausgeführt. Es gibt unzählige andere Anwendungen für die Integration von Python mit SQL "oder" nutzt die Vorteile von den jeweiligen Sprachen aus, um intelligentere, leistungsstarke Lösungen zu übermitteln.

+ **revoscalepy**

    Diese Version enthält die endgültige Version von **Revoscalepy**, die streaming-Algorithmen in "revoscaler" Pythonic äquivalente skalierbar, ausgeben. Sie können die Python-Modelle für linear und logistische Regressionen, Entscheidungsstrukturen, verstärkten Bäumen und zufällige Gesamtstrukturen, alle parallelisiert und kann in remote rechenkontexte ausgeführt erstellen.

    Weitere Informationen finden Sie unter [neuerungen Revoscalepy](python/what-is-revoscalepy.md).

+ Remote rechenkontexte für Python

    Diese Version unterstützt die Verwendung von mehreren Datenquellen und remote rechenkontexte. Der datenanalyst oder Entwickler kann Python-Code auf einem remote-SQL-Server zum Durchsuchen von Daten oder Modelle erstellen, ohne Verschieben von Daten ausführen. Verwendung von remote rechenkontexte erfordert **Revoscalepy**.

+ Python-Unterstützung in Microsoft Machine Learning-Server (eigenständig)

    SQL Server-2017 umfasst die Möglichkeit, eine eigenständige Version von Python und R-Plattformen zu installieren. Mithilfe von Machine Learning-Server können Sie verteilen und Skalieren von R oder Python-Code ohne Verwendung von SQL Server.

    Ein Beispiel für Python-Verwendung in Microsoft Machine Learning-Server, finden Sie unter [veröffentlichen und Nutzen von Python-Code](python/publish-consume-python-code.md).

### <a name="new-algorithms"></a>Neue Algorithmen

Die **MicrosoftML** -Paket für R und Python enthält der Technik Machine Learning-Algorithmen und von remotecomputekontexten Datentransformation, die skalierte oder Ausführen in Remote sein können. Algorithmen sind anpassbare Tiefe neuronale Netzwerke, schnelle Entscheidungsstrukturen und entscheidungswälder, lineare Regression und logistische Regression.

Das Paket MicrosoftML im Lieferumfang von R und Python-Schnittstellen und basiert auf Microsoft Machine Learning Server, Version 9.2.0.

Weitere Informationen finden Sie unter [Einführung in MicrosoftML](using-the-microsoftml-package.md) und [Microsoftml für Python](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package).

### <a name="operationalization"></a>Operationalisierung

Diese Version enthält mehrere Optionen und Features, mit denen Sie die Bereitstellung und Verteilen von Machine Learning-Aufgaben:

+ Operationalisierung mit T-SQL

    Die Integration von Python mit T-SQL bedeutet, dass Sie eine beliebige Python-Code mit aufrufen, können `sp_execute_external_script`. Diese sichere Infrastruktur ermöglicht die Bereitstellung von Enterprise-Grade von Python-Modellen und Skripts, die von einer Anwendung mithilfe einer einfachen gespeicherten Prozedur aufgerufen werden können. Zusätzlicher Leistung wird durch streaming von Daten aus SQL Python-Prozesse und MPI Ring Parallelisierung.

+ **Mrsdeploy** für Python

    Die **Mrsdeploy** -Paket für Microsoft R Server jetzt unterstützt die Bereitstellung von Python-Modellen und Skripts als Webdienste und wird als Option in Machine Learning-Server (eigenständig) verfügbar. Ein Beispiel dafür, wie es funktioniert, finden Sie unter [veröffentlichen und Nutzen von Python-Code](python/publish-consume-python-code.md).

+ Leistung

    Microsoft hat die Grenzen der Leistung für die Bewertung abgelegt. Mit in der Datenbank zu bewerten, die wir verarbeitet eine Million Zeilen, die pro Sekunde, mit der R-Modelle. In dieser Version neue Features für **Echtzeit Bewertung** und **native Bewertung** unterstützen eine bessere Leistung in einzeiligen bewerteten und kleine als auch Batches. 

### <a name="realtime-scoring-and-native-scoring"></a>Echtzeit-Bewertung und systemeigene Bewertung

Echtzeit-Bewertung basiert auf systemeigene C++-Bibliotheken zum Lesen eines Modells in einem optimierten Binärformat gespeichert und anschließend Vorhersagen generieren, ohne die R-Laufzeitversion aufrufen zu müssen. Auf diese Weise bewerteten Vorgänge schneller.

Darüber hinaus enthält diese Version von SQL Server-2017 eine systemeigene T-SQL-Funktion zur schnellen Bewertung, die auf eine beliebige Edition von SQL Server, sogar auf Linux ausgeführt werden kann. Die Funktion erfordert keine Installation von R oder zusätzliche Konfiguration. Dies bedeutet, dass Sie an anderer Stelle ein Modell trainieren, speichern Sie sie in SQL Server und führen Sie bewerten, ohne jemals aufrufen r Diese Funktion wird als bezeichnet _native Bewertung_.

  - Systemeigene Bewertung steht nur in SQL Server-2017. Er verwendet eine T-SQL-Funktion, die in jeder Edition von SQL Server, einschließlich Linux ausgeführt werden kann.
 - Echtzeit-Bewertung wird in SQL Server-2017, und klicken Sie im Microsoft Machine Learning-Server unterstützt. Sie können Runa gespeicherte Prozedur oder Echtzeit-Bewertung von R-Code ausführen.
 - Echtzeit-Bewertung wird auch für SQL Server 2016 verfügbar, wenn die Instanz auf die neueste Version von Microsoft R Server aktualisiert wird.

Weitere Informationen dazu finden Sie in diesen Artikeln:

 + [Echtzeit-Bewertung](real-time-scoring.md)
 + [Systemeigene Bewertung](sql-native-scoring.md)
 + [Zum Ausführen von Realtime Bewertung oder systemeigenen bewerten](r/how-to-do-realtime-scoring.md)

### <a name="upgrade-your-ml-experience-and-get-pre-trained-models"></a>Aktualisieren Sie Ihre Erfahrungen mit ML und abzurufen vorab trainierten Modelle

Wenn Sie eine frühere Version von SQL Server 2016 R Services installiert haben, können Sie nun auf die neueste Version aktualisieren, durch den Wechsel Ihres Servers, sodass die moderne Lifecycle-Richtlinie verwenden. Auf diese Weise können Sie eine schnellere Releasezyklus für R nutzen und alle R-Komponenten automatisch aktualisiert. Weitere Informationen finden Sie unter [Microsoft R Server 9.0.1](https://docs.microsoft.com/r-server/whats-new-in-r-server).

Der Installer bietet außerdem die Möglichkeit, eine Auflistung von Pre-tained Modelle im Binärformat zu installieren. Diese Modelle unterstützen Machine Learning in Szenarien wie z. B. bilderkennung, in denen es Kunden, um große Datasets zum Trainieren eines Modells suchen schwierig sein kann. Nach der Installation eines der Pre-tained Modelle können Sie es für die Vorhersage auf Ihren eigenen Daten ohne den Zeit- und Kostenaufwand beteiligten trainieren ein solches Modell große und komplexe verwenden.

Weitere Informationen finden Sie unter [vorab trainierten Modelle in SQL Server installieren](r/install-pretrained-models-sql-server.md)

### <a name="package-management"></a>Paketverwaltung

Diese Version umfasst viele Verbesserungen bei der paketverwaltung für SQL Server. Dazu gehören:

- Datenbankrollen können Sie den Datenbankadministrator, verwalten und Überwachen von Berechtigungen
- Erstellen Sie EXTERAL LIBRARY-Anweisung in T-SQL
- ein umfangreichen Satz von R-Funktionen zu installieren, entfernen oder eine Liste der Pakete im Besitz des Benutzers.

Weitere Informationen finden Sie unter [Paket Management](r/r-package-management-for-sql-server-r-services.md).

### <a name="get-started"></a>Erste Schritte

+ [Einrichten von Python in SQL Server-Machine Learning-Services](../advanced-analytics/python/setup-python-machine-learning-services.md)

+ [Einrichten von R in SQL Server-Machine Learning-Services](r/set-up-sql-server-r-services-in-database.md)

+ [Machine Learning-Lernprogramme](tutorials/machine-learning-services-tutorials.md)