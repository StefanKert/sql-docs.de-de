---
title: "Einschränkungen von Clientnamen | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- desktop database drivers [ODBC], column names
- ODBC desktop database drivers [ODBC], column names
ms.assetid: 5a339f61-c52f-40ad-8deb-d785f72753d4
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a5e2fb7cf9f54177ce357058e51e541b6a442379
ms.contentlocale: de-de
ms.lasthandoff: 09/09/2017

---
# <a name="column-name-limitations"></a>Einschränkungen von Clientnamen
Spaltennamen können keine gültigen Zeichen (z. B. Leerzeichen) enthalten. Wenn Spaltennamen alle Zeichen außer Buchstaben, Zahlen und Unterstriche enthalten, muss der Namen getrennt werden, indem Sie es in Back Anführungszeichen (') einschließen.  
  
 Wenn der Microsoft Access oder Microsoft Excel-Treiber verwendet wird, Spaltennamen sind maximal 64 Zeichen umfassen und längere ein Fehler generiert. Wenn der Paradox-Treiber verwendet wird, ist der maximale Spaltenname 25 Zeichen. Wenn der Text-Treiber verwendet wird, wird der maximale Spaltenname beträgt 64 Zeichen, und längere werden abgeschnitten.  
  
 Wenn der Treiber dBASE verwendet wird, werden mit einem ASCII-Wert, der größer als 127 Zeichen in Unterstriche konvertiert.  
  
 Wenn der Microsoft Excel-Treiber verwendet wird, wenn die Spaltennamen vorhanden sind, müssen sie in der ersten Zeile sein. Ein Name, der in Microsoft Excel verwenden, würde die "!" Zeichen in Back Anführungszeichen (') eingeschlossen werden muss. Die "!" Zeichen auf das Zeichen "$" konvertiert werden, da die "!" Zeichen ist nicht in einem ODBC-Namen zulässig, selbst wenn der Name in Back Anführungszeichen eingeschlossen ist. Alle anderen gültigen Microsoft Excel-Zeichen (außer den senkrechten Strich (& #124 ;)) genutzt werden in einem Spaltennamen, einschließlich Leerzeichen. Ein Begrenzungsbezeichner muss für einen Microsoft Excel-Spaltennamen verwendet werden, um ein Leerzeichen enthält. Nicht angegebener Spaltennamen werden vom Treiber generierten Namen, z. B. "Col1" für die erste Spalte ersetzt.  
  
 Einen senkrechten Strich (&#124;) kann nicht in einem Spaltennamen verwendet werden, ob der Name in Back Anführungszeichen eingeschlossen ist.  
  
 Wenn der Text-Treiber verwendet wird, umfasst der Treiber einen Standardnamen, wenn ein Spaltenname nicht angegeben ist. Beispielsweise ruft der Treiber die erste Spalte F1, die zweite Spalte F2 usw.