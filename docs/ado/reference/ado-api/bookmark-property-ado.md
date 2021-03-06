---
title: Bookmark-Eigenschaft (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::Bookmark
helpviewer_keywords:
- Bookmark property [ADO]
ms.assetid: 481dcc93-487b-490e-ac58-a1e9b2ebfd43
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9e645300f604e1880f98fd8d99cea8599062f72f
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35276199"
---
# <a name="bookmark-property-ado"></a>Bookmark-Eigenschaft (ADO)
Gibt ein Lesezeichen, die eindeutig für den aktuellen Datensatz in einer [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt, oder legt den aktuellen Datensatz einer **Recordset** -Objekt, das durch ein gültiges Lesezeichen identifizierten Datensatz.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen **Variant** Ausdruck, der ein gültiges Lesezeichen ergibt.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **Lesezeichen** Eigenschaft zu speichern, die Position des aktuellen Datensatzes an diesen Datensatz zu einem beliebigen Zeitpunkt zurück. Lesezeichen stehen nur in **Recordset** Objekte, die Bookmark-Funktionalität unterstützen.  
  
 Beim Öffnen einer **Recordset** Objekt, jeder Datensatz hat ein eindeutiges Lesezeichen. Um das Lesezeichen für den aktuellen Datensatz zu speichern, weisen Sie den Wert der **Lesezeichen** Eigenschaft einer Variablen. Um schnell an diesen Datensatz zu einem beliebigen Zeitpunkt nach dem Verschieben zu einem anderen Datensatz zurückzugeben, legen Sie die **Recordset** des Objekts **Lesezeichen** -Eigenschaft auf den Wert dieser Variablen.  
  
 Der Benutzer kann möglicherweise nicht den Wert des Lesezeichens anzuzeigen. Darüber hinaus sollten Benutzer nicht erwarten, dass Lesezeichen direkt vergleichbar sein, da zwei Lesezeichen, die auf den gleichen Datensatz verweisen unterschiedliche Werte haben können.  
  
 Bei Verwendung von der [Klon](../../../ado/reference/ado-api/clone-method-ado.md) Methode, um eine Kopie erstellen eine **Recordset** -Objekt, das **Lesezeichen** -eigenschafteneinstellungen für die ursprüngliche und das Duplikat **Recordset**  Objekte identisch sind, und Sie können diese Synonym verwenden. Allerdings können keine Lesezeichen aus verschiedenen **Recordset** Objekte Synonym verwenden lassen, auch wenn sie über die Quelle oder der Befehl erstellt wurden.  
  
> [!NOTE]
>  **Remote Datendienstnutzung** bei Verwendung für eine clientseitige **Recordset** -Objekt, das **Lesezeichen** Eigenschaft ist immer verfügbar.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [BOF, EOF und Lesezeichen-Eigenschaften-Beispiel (VB)](../../../ado/reference/ado-api/bof-eof-and-bookmark-properties-example-vb.md)   
 [BOF, EOF und Lesezeichen Eigenschaften (VC++-Beispiel)](../../../ado/reference/ado-api/bof-eof-and-bookmark-properties-example-vc.md)   
 [Supports-Methode](../../../ado/reference/ado-api/supports-method.md)
