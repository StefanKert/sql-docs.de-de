---
title: 'IRowsetFastLoad:: Commit (OLE DB) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IRowsetFastLoad::Commit (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- Commit method
ms.assetid: 19de9128-b91a-4626-847f-af721edaa24e
caps.latest.revision: 34
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 745282c1d1e8fa36c9d0a407ac32171304d05197
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37417169"
---
# <a name="irowsetfastloadcommit-ole-db"></a>IRowsetFastLoad::Commit (OLE DB)
  Markiert das Ende eines Batches eingefügter Zeilen und schreibt die Zeilen in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabelle. Beispiele finden Sie [Bulk Daten mithilfe von IRowsetFastLoad &#40;OLE DB&#41; ](irowsetfastload-ole-db.md) und [Senden von BLOB-Daten zu SQL SERVER mithilfe von IROWSETFASTLOAD und ISEQUENTIALSTREAM &#40;OLE DB&#41;](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT Commit(  
BOOL   
fDone  
);  
  
```  
  
## <a name="arguments"></a>Argumente  
 *fDone*[in]  
 Wenn FALSE angegeben wird, behält das Rowset seine Gültigkeit und kann vom Consumer zum Einfügen zusätzlicher Zeilen verwendet werden. Wird TRUE angegeben, dann verliert das Rowset seine Gültigkeit, und der Consumer kann keine weiteren Einfügungen vornehmen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 S_OK  
 Die Methode wurde erfolgreich ausgeführt, und alle eingefügten Daten wurden in die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle geschrieben.  
  
 E_FAIL  
 Es ist ein anbieterspezifischer Fehler aufgetreten. Rufen Sie Fehlerinformationen für den betreffenden Fehlertext vom Anbieter ab.  
  
 E_UNEXPECTED  
 Die Methode wurde aufgerufen, auf eine zuvor durch ungültig gemacht Rowset für das Massenkopieren der **IRowsetFastLoad:: Commit** Methode.  
  
## <a name="remarks"></a>Hinweise  
 Ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Rowset für Native Client OLE DB-Anbieter das Massenkopieren verhält sich wie ein Rowset verzögerten Updatemodus. Wie der Benutzer Zeilendaten über das Rowset einfügt, werden eingefügte Zeilen auf dieselbe Weise wie ausstehende einfügungen in ein Rowset unterstützender behandelt **IRowsetUpdate**.  
  
 Der Consumer aufrufen, muss die **Commit** Methode für das Rowset für das Massenkopieren eingefügte Zeilen zu schreiben die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabelle in die gleiche Weise wie die **IRowsetUpdate:: Update** Methode verwendet, um ausstehende Zeilen an eine SQL Server-Instanz.  
  
 Wenn der Consumer seinen Verweis auf das Rowset für das Massenkopieren ohne freigibt der **Commit** -Methode, alle noch nicht geschriebene Zeilen gehen verloren.  
  
 Der Consumer kann eingefügten Zeilen als batch durch Aufrufen der **Commit** -Methode mit dem *fDone* -Argument auf "false" festgelegt. Wenn *fDone*ist auf "true" festgelegt, wird das Rowset ungültig. Ein Rowset für das ungültige Massenkopieren unterstützt nur die **ISupportErrorInfo** Schnittstelle und **IRowsetFastLoad:: Release** Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IRowsetFastLoad &#40;OLE-DB&#41;](irowsetfastload-ole-db.md)  
  
  
