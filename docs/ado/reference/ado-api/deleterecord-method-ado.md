---
title: DeleteRecord-Methode (ADO) | Microsoft Docs
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
- _Record::raw_DeleteRecord
- _Record::DeleteRecord
helpviewer_keywords:
- DeleteRecord method [ADO]
ms.assetid: 2726498c-dbd8-4266-983b-ae7d62c39142
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 168b53d0ad68f55656e005f7523a0c09ba599004
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35277639"
---
# <a name="deleterecord-method-ado"></a>DeleteRecord-Methode (ADO)
Löscht eine Entität, dargestellt durch eine [Datensatz](../../../ado/reference/ado-api/record-object-ado.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Record.DeleteRecord Source, Async  
```  
  
#### <a name="parameters"></a>Parameter  
 *Quelle*  
 Optional. Ein **Zeichenfolge** -Wert enthält eine URL, die zur Identifizierung der Entität (z. B. die Datei oder das Verzeichnis) gelöscht werden soll. Wenn *Quelle* ausgelassen wird, oder gibt eine leere Zeichenfolge, die Entität, die vom aktuellen [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) wird gelöscht. Wenn der Datensatz einen Auflistungsdatensatz ist ([RecordType](../../../ado/reference/ado-api/recordtype-property-ado.md) von **AdCollectionRecord**, z. B. ein Verzeichnis) aller untergeordneten Elemente (z. B. Unterverzeichnissen) werden ebenfalls gelöscht.  
  
 *Async*  
 Optional. Ein **booleschen** -Wert, wenn **"true"**, gibt an, dass der Löschvorgang asychronen ist.  
  
## <a name="remarks"></a>Hinweise  
 Vorgänge für das Objekt dargestellt, die von diesem **Datensatz** kann fehlschlagen, nachdem diese Methode ausgeführt wird. Nach dem Aufruf **DeleteRecord**, die **Datensatz** sollten geschlossen werden, da das Verhalten der **Datensatz** können unvorhersehbare abhängig von der Anbieter beim aktualisiert werden, die **Datensatz** mit der Datenquelle.  
  
 Wenn diese **Datensatz** aus abgerufen wurde eine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md), und klicken Sie dann die Ergebnisse dieses Vorgangs nicht sofort im reflektiert werden die **Recordset**. Aktualisieren der **Recordset** durch Schließen und erneut öffnen, oder durch Ausführen der **Recordset** [Requery](../../../ado/reference/ado-api/requery-method.md) -Methode, die [Update](../../../ado/reference/ado-api/update-method.md) -Methode, oder die [Resync](../../../ado/reference/ado-api/resync-method.md) Methode.  
  
> [!NOTE]
>  URLs, die mit dem HTTP-Schema werden automatisch aufgerufen. der [Microsoft OLE DB-Anbieter für Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Weitere Informationen finden Sie unter [absoluten und relativen URLs](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Gilt für  
 [Record-Objekt (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Delete-Methode (ADO Fields-Auflistung)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Delete-Methode (ADO-Parameters-Auflistung)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Delete-Methode (ADO Recordset)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)
