---
title: SQLValidDSN-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLValidDSN
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLValidDSN
helpviewer_keywords:
- SQLValidDSN [ODBC]
ms.assetid: 930d1d89-337a-4429-85a2-84ee10555ac9
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0d3dfd7e2b019626e98f8a93611880411e74b86a
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39082892"
---
# <a name="sqlvaliddsn-function"></a>SQLValidDSN-Funktion
**Übereinstimmung mit Standards**  
 Version eingeführt: ODBC 2.0  
  
 **Zusammenfassung**  
 **SQLValidDSN** überprüft die Länge und die Gültigkeit der Namen der Datenquelle, bevor der Name der Systeminformationen hinzugefügt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
BOOL SQLValidDSN(  
     LPCSTR    lpszDSN);  
```  
  
## <a name="arguments"></a>Argumente  
 *lpszDSN*  
 [Eingabe] Datenquellenname, die überprüft werden.  
  
## <a name="returns"></a>Rückgabewert  
 Die Funktion gibt "true" zurück, wenn der Name der Datenquelle gültig ist. Wenn der Name der Datenquelle ungültig ist, oder der Funktionsaufruf Fehler bei zurückgegeben "false".  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLValidDSN** gibt "false", ein zugeordnetes  *\*PfErrorCode* Wert abgerufen werden kann, durch den Aufruf **SQLInstallerError**. Ein  *\*PfErrorCode* wird zurückgegeben, nur wenn der Funktionsaufruf fehlschlägt, nicht wenn "false" zurückgegeben wurde, weil der Name der Datenquelle ungültig ist. Die folgende Tabelle enthält die  *\*PfErrorCode* Werte, die zurückgegeben werden können **SQLInstallerError** und jeweils im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeine Installer-Fehler|Fehler für die gab es keine bestimmte Installer-Fehlers.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund von unzureichendem Speicher nicht ausgeführt werden.|  
  
## <a name="comments"></a>Kommentare  
 **SQLValidDSN** wird aufgerufen, von eines Treibers der [ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md) um die Länge der Namen der Datenquelle und die Gültigkeit der einzelnen Zeichen im Namen Datenquelle zu überprüfen. Er überprüft, ob die Länge des Namens SQL_MAX_DSN_LENGTH, größer ist, wie in Sqlext.h definiert. (Außerdem wird die Länge der Namen der Datenquelle durch überprüft [SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md).) **SQLValidDSN** überprüft, ob eine der folgenden ungültigen Zeichen im Namen Datenquelle enthalten sind:  
  
 [ ] { } ( ) , ; ? * = ! \@ \  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Hinzufügen, ändern oder Entfernen einer Datenquelle|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md) (in der Setup-DLL)|  
|Hinzufügen, ändern oder Entfernen einer Datenquelle|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Name der Datenquelle schreiben, um die Systeminformationen|[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|
