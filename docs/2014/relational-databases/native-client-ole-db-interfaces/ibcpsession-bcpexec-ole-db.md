---
title: Ibcpsession (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IBCPSession::BCPExec (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPExec method
ms.assetid: 0f4ebb63-cf03-4e53-846e-6c3021cde007
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eb0c10e4c12bba99225bc5f332a8ad6701de29fd
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37414029"
---
# <a name="ibcpsessionbcpexec-ole-db"></a>IBCPSession::BCPExec (OLE DB)
  Führt den Massenkopiervorgang aus.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT BCPExec(   
DBROWCOUNT *pRowsCopied);  
```  
  
## <a name="remarks"></a>Hinweise  
 Die **BCPExec** Methode kopiert Daten aus einer Benutzerdatei in eine Datenbanktabelle oder umgekehrt, abhängig vom Wert der *eDirection* als Parameter der [ibcpsession:: BCPInit](ibcpsession-bcpinit-ole-db.md)Methode.  
  
 Rufen Sie vor dem Aufruf von **BCPExec**die **BCPInit** -Methode mit einem gültigen Benutzerdateinamen auf. Andernfalls wird ein Fehler ausgelöst. Die einzige Ausnahme besteht darin, wenn eine Abfrage für einen Massenkopiervorgang verwendet werden soll. In diesem Fall geben Sie in der **BCPInit** -Methode NULL für den Tabellennamen an, und dann geben Sie die Abfrage mithilfe der BCP_OPTION_HINTS-Option an.  
  
 Die **BCPExec** -Methode ist die einzige Methode zum Massenkopieren, die wahrscheinlich für einige Zeit nicht zurückkehrt. Es ist deshalb die einzige Massenkopiermethode, die den asynchronen Modus unterstützt. Zur Verwendung des asynchronen Modus legen Sie die anbieterspezifische Sitzungseigenschaft SSPROP_ASYNCH_BULKCOPY vor dem Aufrufen der **BCPExec** -Methode auf VARIANT_TRUE fest. Diese Eigenschaft ist im DBPROPSET_SQLSERVERSESSION-Eigenschaftensatz verfügbar. Rufen Sie die **BCPExec** -Methode mit den gleichen Parametern auf, um den Vorgang auf Vollständigkeit zu überprüfen. Wenn das Massenkopieren noch nicht abgeschlossen wurde, gibt die **BCPExec** -Methode DB_S_ASYNCHRONOUS zurück. Sie gibt überdies im *pRowsCopied* -Argument eine Statuszahl der Anzahl von Zeilen fest, die zum Server gesendet bzw. vom Server empfangen wurden. Für die zum Server gesendeten Zeilen wird erst ein Commit ausgeführt, wenn das Ende eines Batches erreicht wurde.  
  
## <a name="arguments"></a>Argumente  
 *pRowsCopied*[out]  
 Ein Zeiger auf einen DWORD-Wert. Die **BCPExec** -Methode füllt den DWORD-Wert mit der Anzahl von Zeilen, die erfolgreich kopiert wurden. Wenn das *pRowsCopied* -Argument auf NULL festgelegt wurde, wird es von der **BCPExec** -Methode ignoriert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 S_OK  
 Die Methode wurde erfolgreich ausgeführt.  
  
 E_FAIL  
 Ein anbieterspezifischer Fehler ist aufgetreten; Verwenden Sie ausführliche Informationen, die [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) Schnittstelle.  
  
 E_UNEXPECTED  
 Die Methode wurde unerwartet aufgerufen. Die **BCPInit** -Methode wurde beispielsweise erst nach dem Aufruf dieser Methode aufgerufen. Wird auch zurückgegeben, wenn der Vorgang mit der BCP_OPTION_ABORT-Option abgebrochen und danach die **BCPExec** -Methode aufgerufen wurde.  
  
 E_OUTOFMEMORY  
 Fehler aufgrund nicht genügenden Arbeitsspeichers  
  
 DB_S_ENDOFROWSET  
 Der Massenkopiervorgang wurde beendet, und die gesamte Datenübertragung wurde abgeschlossen.  
  
 DB_S_ASYNCHRONOUS  
 Der aktuelle Batch von Zeilen wurde kopiert. Rufen Sie die **BCPExec** -Methode erneut auf, um den nächsten Batch zu übertragen.  
  
 DB_S_ERRORSOCCURRED  
 Während des Massenkopiervorgangs sind Fehler aufgetreten, und einige Zeilen sind möglicherweise nicht kopiert worden. Die Anzahl der Fehler ist immer noch weniger als die maximal zulässige Fehleranzahl.  
  
## <a name="see-also"></a>Siehe auch  
 [IBCPSession &#40;OLE-DB&#41;](ibcpsession-ole-db.md)   
 [Durchführen von Massenkopiervorgängen](../native-client/features/performing-bulk-copy-operations.md)  
  
  
