---
title: "Unterstützung für nationale Zeichensätze | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4fceacfd-df4f-40cd-b7a2-5e5e58a5979f
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f143d37911a1375a1eebe9de04c8b509817575ec
ms.contentlocale: de-de
ms.lasthandoff: 09/09/2017

---
# <a name="national-character-set-support"></a>Unterstützung für nationale Zeichensätze
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Der JDBC-Treiber bietet Unterstützung für die JDBC 4.0-API, die neue API-Methoden für die Konvertierung nationaler Zeichensätze enthält. Diese Unterstützung beinhaltet neue Setter, Getter und Updater-Methoden für **NCHAR**, **NVARCHAR**, **LONGNVARCHAR**, und **NCLOB** JDBC-Typen.  
  
 In der folgenden Liste sind die Methoden zum Abrufen, Festlegen und Aktualisieren für die Unterstützung der Konvertierung nationaler Zeichensätze aufgeführt:  
  
-   [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md): [SetNString](../../connect/jdbc/reference/setnstring-method-int-java-lang-string.md), [SetNCharacterStream](../../connect/jdbc/reference/setncharacterstream-method-sqlserverpreparedstatement.md), [SetNClob](../../connect/jdbc/reference/setnclob-method-sqlserverpreparedstatement.md).  
  
-   [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md): [GetNClob](../../connect/jdbc/reference/getnclob-method-sqlservercallablestatement.md), [GetNString](../../connect/jdbc/reference/getnstring-method-sqlservercallablestatement.md), [GetNCharacterStream](../../connect/jdbc/reference/getncharacterstream-method-sqlservercallablestatement.md), [SetNString](../../connect/jdbc/reference/setnstring-method-sqlservercallablestatement.md), [SetNCharacterStream](../../connect/jdbc/reference/setncharacterstream-method-sqlservercallablestatement.md), [SetNClob](../../connect/jdbc/reference/setnclob-method-sqlservercallablestatement.md).  
  
-   [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md): [GetNClob](../../connect/jdbc/reference/getnclob-method-sqlserverresultset.md), [GetNString](../../connect/jdbc/reference/getnstring-method-sqlserverresultset.md), [GetNCharacterStream](../../connect/jdbc/reference/getncharacterstream-method-sqlserverresultset.md), [UpdateNClob](../../connect/jdbc/reference/updatenclob-method-sqlserverresultset.md), [UpdateNString](../../connect/jdbc/reference/updatenstring-method-sqlserverresultset.md), [UpdateNCharacterStream](../../connect/jdbc/reference/updatencharacterstream-method-sqlserverresultset.md).  
  
> [!NOTE]  
>  Um diese Methoden in einer Anwendung verwenden zu können, müssen Sie den Klassenpfad so festlegen, dass die Datei „sqljdbc4.jar“ enthalten ist.  
  
 Damit String-Parameter im Unicode-Format an den Server gesendet werden, sollten die Anwendungen entweder die neuen JDBC 4.0-Methoden für nationale Zeichensätze verwenden. oder legen Sie die **SendStringParametersAsUnicode** Verbindungseigenschaft auf "**" true "**" Wenn Sie die Methoden für nicht nationale Zeichensätze verwenden. Es wird empfohlen, nach Möglichkeit die neuen JDBC 4.0-Methoden für nationale Zeichensätze zu verwenden. Weitere Informationen zu den **SendStringParametersAsUnicode** Verbindungseigenschaft finden Sie unter [Festlegen der Verbindungseigenschaften](../../connect/jdbc/setting-the-connection-properties.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlegendes zu den Datentypen des JDBC-Treiber](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  