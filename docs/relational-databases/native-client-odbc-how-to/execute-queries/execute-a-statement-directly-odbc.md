---
title: Direktes Ausführen von Anweisungen (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- statement execution
ms.assetid: b690f9de-66e1-4ee5-ab6a-121346fb5f85
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 132ded05edbb6bed88bdef4ad44235e57a811990
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43094147"
---
# <a name="execute-a-statement-directly-odbc"></a>Direktes Ausführen von Anweisungen (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

    
### <a name="to-execute-a-statement-directly-and-one-time-only"></a>So führen Sie eine Anweisung direkt und nur einmal aus  
  
1.  Wenn die Anweisung über parametermarkierungen verfügt, verwenden Sie [SQLBindParameter](../../../relational-databases/native-client-odbc-api/sqlbindparameter.md) jeden Parameter an eine Programmvariable zu binden. Füllen Sie die Programmvariablen mit Datenwerten, und richten Sie dann alle Data-at-Execution-Parameter ein.  
  
2.  Rufen Sie [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399) zum Ausführen der Anweisung.  
  
3.  Wenn Data-at-Execution-Eingabeparameter verwendet werden, [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399) wird SQL_NEED_DATA zurückgegeben. Senden Sie die Daten in Blöcken mit [SQLParamData](http://go.microsoft.com/fwlink/?LinkId=58405) und [SQLPutData](../../../relational-databases/native-client-odbc-api/sqlputdata.md).  
  
### <a name="to-execute-a-statement-multiple-times-by-using-column-wise-parameter-binding"></a>So führen Sie mit der spaltenweisen Parameterbindung eine Anweisung mehrmals aus  
  
1.  Rufen Sie [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) , die folgenden Attribute festzulegen:  
  
     Legen Sie SQL_ATTR_PARAMSET_SIZE auf die Anzahl von Sätzen (S) von Parametern fest.  
  
     Legen Sie SQL_ATTR_PARAM_BIND_TYPE auf SQL_PARAMETER_BIND_BY_COLUMN fest.  
  
     Legen Sie das SQL_ATTR_PARAMS_PROCESSED_PTR-Attribut fest, um auf eine SQLUINTEGER-Variable zu zeigen und die Anzahl der verarbeiteten Parameter zu halten.  
  
     Legen Sie SQL_ATTR_PARAMS_STATUS_PTR fest, um auf ein Array [S] aus SQLUSSMALLINT-Variablen zu zeigen und die Parameterstatusindikatoren zu halten.  
  
2.  Führen Sie folgende Aktionen für jeden Parametermarker durch:  
  
     Weisen Sie ein Array mit S-Parameterpuffern zu, um Datenwerte zu speichern.  
  
     Weisen Sie ein Array mit S-Parameterpuffern zu, um Datenlängen zu speichern.  
  
     Rufen Sie [SQLBindParameter](../../../relational-databases/native-client-odbc-api/sqlbindparameter.md) auf den Parameter Daten Wert und die datenlängenarrays an den Anweisungsparameter zu binden.  
  
     Richten Sie alle Data-at-Execution-Text- oder Imageparameter ein.  
  
     Setzen Sie S-Datenwerte und S-Datenlängen in die gebundenen Parameterarrays ein.  
  
3.  Rufen Sie [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399) zum Ausführen der Anweisung. Der Treiber führt die Anweisung S-mal aus, einmal für jeden Parametersatz.  
  
4.  Wenn Data-at-Execution-Eingabeparameter verwendet werden, [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399) wird SQL_NEED_DATA zurückgegeben. Senden Sie die Daten in Blöcken mit [SQLParamData](http://go.microsoft.com/fwlink/?LinkId=58405) und [SQLPutData](../../../relational-databases/native-client-odbc-api/sqlputdata.md).  
  
### <a name="to-execute-a-statement-multiple-times-by-using-row-wise-parameter-binding"></a>So führen Sie mit der zeilenweisen Parameterbindung eine Anweisung mehrmals aus  
  
1.  Ordnen Sie ein Array [S] von Strukturen zu, wobei S der Anzahl von Parametersätzen entspricht. Die Struktur verfügt über ein Element für jeden Parameter, und jedes Element verfügt über zwei Teile:  
  
     Der erste Teil ist eine Variable des entsprechenden Datentyps zum Speichern der Parameterdaten.  
  
     Der zweite Teil ist eine SQLINTEGER-Variable zum Speichern des Statusindikators.  
  
2.  Rufen Sie [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) , die folgenden Attribute festzulegen:  
  
     Legen Sie SQL_ATTR_PARAMSET_SIZE auf die Anzahl von Sätzen (S) von Parametern fest.  
  
     Legen Sie SQL_ATTR_PARAM_BIND_TYPE auf die Größe der in Schritt 1 zugeordneten Struktur fest.  
  
     Legen Sie das SQL_ATTR_PARAMS_PROCESSED_PTR-Attribut fest, um auf eine SQLUINTEGER-Variable zu zeigen und die Anzahl der verarbeiteten Parameter zu halten.  
  
     Legen Sie SQL_ATTR_PARAMS_STATUS_PTR fest, um auf ein Array [S] aus SQLUSSMALLINT-Variablen zu zeigen und die Parameterstatusindikatoren zu halten.  
  
3.  Rufen Sie für jede parametermarkierung [SQLBindParameter](../../../relational-databases/native-client-odbc-api/sqlbindparameter.md) , zeigen Sie auf die Variablen im ersten Element des Arrays mit Strukturen, die in Schritt 1 zugeordneten Datenwert und den datenlängenzeigern des Parameters. Falls der Parameter ein Data-at-Execution-Parameter ist, richten Sie ihn ein.  
  
4.  Füllen Sie das gebundene Parameterpufferarray mit Datenwerten.  
  
5.  Rufen Sie [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399) zum Ausführen der Anweisung. Der Treiber führt die Anweisung S-mal aus, einmal für jeden Parametersatz.  
  
6.  Wenn Data-at-Execution-Eingabeparameter verwendet werden, [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399) wird SQL_NEED_DATA zurückgegeben. Senden Sie die Daten in Blöcken mit [SQLParamData](http://go.microsoft.com/fwlink/?LinkId=58405) und [SQLPutData](../../../relational-databases/native-client-odbc-api/sqlputdata.md).  
  
 **Beachten Sie** spaltenweise und zeilenweise Bindung wird in der Regel in Verbindung mit [SQLPrepare-Funktion](http://go.microsoft.com/fwlink/?LinkId=59360) und [SQLExecute](http://go.microsoft.com/fwlink/?LinkId=58400) als mit [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399).  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von Abfragen: Themen zur Vorgehensweise &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-how-to/execute-queries/executing-queries-how-to-topics-odbc.md)  
  
  
