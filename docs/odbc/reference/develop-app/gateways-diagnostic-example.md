---
title: Beispiel für die Diagnose von Gateways | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], examples
- gateway diagnostic [ODBC]
- error messages [ODBC], diagnostic messages
ms.assetid: e0695fac-4593-4b3d-8675-cb8f73dab966
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d9d77f42b0941cecc8a17fe3b54ee91705af0666
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="gateways-diagnostic-example"></a>Beispiel für die Diagnose von Gateways
In einer gatewayarchitektur sendet ein Treiber Anforderungen auf ein Gateway, die ODBC unterstützt. Das Gateway sendet Anforderungen an ein DBMS. Da es sich um die Komponente, das mit der Treiber-Manager kommuniziert handelt, wird der Treiber formatiert und gibt Argumente für **SQLGetDiagRec**.  
  
 Z. B. kann Oracle basierend ein Gateway Rdb auf Microsoft Open Data Services und wenn der Rdb die EMPLOYEE-Tabelle nicht gefunden wurde, das Gateway diese diagnosemeldung generiert:  
  
```  
"[42S02][-1][DEC][ODS Gateway][Rdb]%SQL-F-RELNOTDEF, Table EMPLOYEE is not defined "  
   "in schema."  
```  
  
 Aufgrund des Fehlers in der Datenquelle mit das Gateway die diagnosemeldung ein Präfix für den datenquellenbezeichner ([Rdb]) hinzugefügt. Wurde das Gateway für die Komponente, die mit der Datenquelle verbunden, werden die diagnosemeldung Präfixe für die Hersteller (Dez) und den Bezeichner ([ODS-Gateway]) hinzugefügt. Es bietet nun auch den SQLSTATE-Wert und der Rdb-Fehlercode an den Anfang der diagnosemeldung. Dies gestattet es um die Semantik der eigenen Nachrichtenstruktur beibehalten, und geben Sie immer noch die ODBC-Diagnoseinformationen an den Treiber. Der Treiber analysiert die Fehlerinformationen an die Error-Anweisung angefügt werden, durch das Gateway.  
  
 Da der Gateway-Treiber die Komponente, das mit der Treiber-Manager kommuniziert ist, würden sie die vorausgehende Nachricht für die Diagnose verwenden, um formatieren und die folgenden Rückgabewerte von **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1  
Diagnostic Msg:   "[DEC][ODS Gateway][Rdb]%SQL-F-RELNOTDEF, Table EMPLOYEE is not "  
                  "defined in schema."  
```
