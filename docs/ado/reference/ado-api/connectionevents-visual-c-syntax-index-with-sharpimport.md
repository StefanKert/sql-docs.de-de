---
title: 'ConnectionEvents (Visual C++-Syntax Index mit #import) | Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
dev_langs:
- C++
helpviewer_keywords:
- 'ConnectionEvents collection [ADO], Visual C++ syntax index with #import'
ms.assetid: dd052d36-7730-4400-822b-0544fb1992b4
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4eb2b129efc27ca3c64bf72e8c52702f160488d6
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35276979"
---
# <a name="connectionevents-visual-c-syntax-index-with-import"></a>ConnectionEvents (Visual C++-Syntax Index mit #import)
## <a name="events"></a>Ereignisse  
  
```  
HRESULT InfoMessage( struct Error * pError, enum  
    EventStatusEnum *     adStatus, struct _Connection * pConnection );  
  
HRESULT BeginTransComplete( long TransactionLevel,  
    struct Error * pError, enum EventStatusEnum * adStatus, struct  
    _Connection * pConnection );  
  
HRESULT CommitTransComplete( struct Error *  
    pError, enum EventStatusEnum     * adStatus, struct _Connection *  
    pConnection );  
  
HRESULT RollbackTransComplete( struct Error *  
    pError, enum     EventStatusEnum * adStatus, struct _Connection *  
    pConnection );  
  
HRESULT WillExecute( BSTR * Source, enum  
    CursorTypeEnum * CursorType,  
    enum LockTypeEnum * LockType, long * Options, enum EventStatusEnum *  
    adStatus, struct _Command * pCommand, struct _Recordset * pRecordset,  
    struct _Connection * pConnection );  
  
HRESULT ExecuteComplete( long RecordsAffected, struct  
    Error * pError,     enum EventStatusEnum * adStatus, struct _Command  
    * pCommand, struct     _Recordset * pRecordset, struct _Connection *  
    pConnection );  
  
HRESULT WillConnect( BSTR * ConnectionString, BSTR *  
    UserID, BSTR *     Password, long * Options, enum EventStatusEnum *  
    adStatus, struct     _Connection * pConnection );  
  
HRESULT ConnectComplete( struct Error *  
    pError, enum EventStatusEnum *     adStatus, struct _Connection *  
    pConnection );  
  
HRESULT Disconnect( enum EventStatusEnum *  
    adStatus, struct _Connection *     pConnection );  
```
