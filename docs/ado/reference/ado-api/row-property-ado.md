---
title: Row-Eigenschaft (ADO) | Microsoft Docs
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
f1_keywords:
- ADORecordConstruction::PutRow
- ADORecordConstruction::GetRow
- ADORecordConstruction::get_Row
- ADORecordConstruction::Row
- ADORecordConstruction::put_Row
helpviewer_keywords:
- Row property [ADO]
ms.assetid: 21019d89-2dd1-4a26-ac6f-384b81d66949
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4de19beeb853abb0a6bdc4d517332a812fa43c0e
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35281319"
---
# <a name="row-property-ado"></a>Row-Eigenschaft (ADO)
Ruft ab oder legt einen OLE DB- **Zeile** Objekt aus, oder auf eine [ADORecordConstruction Schnittstelle](../../../ado/reference/ado-api/adorecordconstruction-interface.md) Objekt. Bei Verwendung von **Put_Row** festzulegende eine **Zeile** -Objekt, eine Zeile in einer ADO umgewandelt ist **Datensatz** Objekt.  
  
## <a name="readwritesyntax"></a>Lese-/Schreibzugriff. Syntax  
  
```  
HRESULT get_Row([out, retval] IUnknown** ppRow);  
HRESULT put_Row([in] IUnknown* pRow);  
```  
  
## <a name="parameters"></a>Parameter  
 *ppRow*  
 Zeiger auf einen OLE DB- **Zeile** Objekt.  
  
 *PRow*  
 OLE DB- **Zeile** Objekt.  
  
## <a name="return-values"></a>Rückgabewerte  
 Diese Eigenschaftsmethode gibt die standardmäßige HRESULT-Werte, einschließlich S_OK und E_FAIL zurück.  
  
## <a name="applies-to"></a>Gilt für  
 [ADORecordConstruction-Schnittstelle](../../../ado/reference/ado-api/adorecordconstruction-interface.md)
