---
title: Verwenden eine SQL-Anweisung mit Parametern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3202b88f-ce13-44dd-982c-c6a3b0260378
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 962b03d93647b5d5972421a0e0fbd8a3384cd787
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "42785100"
---
# <a name="using-an-sql-statement-with-parameters"></a>Verwenden von SQL-Anweisungen mit Parametern

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Wenn Sie Daten in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank mit einer SQL-Anweisung verarbeiten möchten, die IN-Parameter enthält, können Sie mit der [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md)-Methode der [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)-Klasse ein [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)-Element zurückgeben, das die angeforderten Daten enthält. Sie müssen dazu zuerst mit der [prepareStatement](../../connect/jdbc/reference/preparestatement-method-sqlserverconnection.md)-Methode der [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)-Klasse ein SQLServerPreparedStatement-Objekt erstellen.

Beim Erstellen der SQL-Anweisung werden die IN-Parameter mit dem ? (Fragezeichen) angegeben, das als Platzhalter für die Parameterwerte fungiert, die später an die SQL-Anweisung übergeben werden. Um einen Wert für einen Parameter angeben, können Sie eine der Setter-Methoden der SQLServerPreparedStatement-Klasse. Die verwendete Festlegungsmethode hängt vom Datentyp des Werts ab, der an die SQL-Anweisung übergeben werden soll.

Wenn Sie einen Wert an die Festlegungsmethode übergeben, müssen Sie nicht nur den Wert angeben, der in der SQL-Anweisung verwendet werden soll, sondern auch die ordinale Position des Parameters in der SQL-Anweisung. Wenn die SQL-Anweisung einen einzelnen Parameter enthält, wird z. B. ihres Ordinalwerts 1 sein. Wenn die Anweisung zwei Parameter enthält, ist der erste Ordinalwert „1“ und der zweite Ordinalwert „2“.

Im folgenden Beispiel wird eine offene Verbindung zur [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank an die Funktion übergeben, eine vorbereitete SQL-Anweisung wird erstellt und mit einem einzelnen Zeichenfolgenparameterwert ausgeführt, und die Ergebnisse werden aus dem Resultset gelesen.

[!code[JDBC#UsingSQLWithParams1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-w_1_1.java)]

## <a name="see-also"></a>Weitere Informationen finden Sie unter

[Verwenden von Anweisungen mit SQL](../../connect/jdbc/using-statements-with-sql.md)
