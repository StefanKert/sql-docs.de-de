---
title: CHECK-Einschränkungsausdruck (Dialogfeld) (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.checkconstraintexpression
ms.assetid: beb6ce43-3913-4d66-8826-8e885335b790
caps.latest.revision: 13
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f4ee29da32d79f4c4048323a4b86fd2fbfbe330a
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43812336"
---
# <a name="check-constraint-expression-dialog-box-visual-database-tools"></a>CHECK-Einschränkungsausdruck (Dialogfeld) (Visual Database Tools)
  Wenn Sie eine CHECK-Einschränkung einer Tabelle oder Spalte anfügen, müssen Sie einen SQL-Ausdruck einschließen. Geben Sie den CHECK-Einschränkungsausdruck in das zur Verfügung gestellte Feld ein.  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
 expression  
 Geben Sie den Ausdruck ein.  
  
 Sie können einen einfachen Einschränkungsausdruck erstellen, um Daten auf eine einfache Bedingung zu prüfen. Sie können aber auch einen komplexen Ausdruck mithilfe boolescher Operatoren erstellen, um Daten auf mehrere Bedingungen zu prüfen. Angenommen, die authors-Tabelle enthält eine zip-Spalte, in die nur Zeichenfolgen aus 5 Ziffern eingegeben werden sollen. Der folgende Einschränkungsausdruck stellt sicher, dass nur fünfstellige Zahlen zulässig sind:  
  
```  
zip LIKE '[0-9][0-9][0-9][0-9][0-9]'  
```  
  
 Angenommen, die Tabelle sales enthält die Spalte qty, für die ein Wert größer als 0 erforderlich ist. Die folgende Einschränkung stellt sicher, dass nur positive Werte zulässig sind:  
  
```  
qty > 0  
```  
  
 Ein weiteres Beispiel: Die orders-Tabelle schränkt die Art der Kreditkarten ein, die für Kreditkartenaufträge akzeptiert werden. Die folgende Einschränkung stellt sicher, dass nur Visa-, MasterCard- oder American Express-Kreditkarten akzeptiert werden, wenn als Zahlungsmittel für den Auftrag eine Kreditkarte verwendet wird.  
  
```  
NOT (payment_method = 'credit card') OR  
   (card_type IN ('VISA', 'MASTERCARD', 'AMERICAN EXPRESS'))  
```  
  
## <a name="to-define-a-constraint-expression"></a>So definieren Sie einen Einschränkungsausdruck  
 Geben Sie auf der Registerkarte Einschränkungen überprüfen der Eigenschaftenseiten einen Ausdruck in das Feld Einschränkungsausdruck ein. Verwenden Sie dabei die folgende Syntax:  
  
 `{constant | column_name | function | (subquery)}`  
  
 `[{operator | AND | OR | NOT}`  
  
 `{constant | column_name | function | (subquery)}...]`  
  
 Die SQL-Syntax besteht aus folgenden Parametern:  
  
|Parameter|Description|  
|---------------|-----------------|  
|Konstante|Ein Literalwert, wie numerische Daten oder Zeichendaten. Zeichendaten müssen in einfache Anführungszeichen (') eingeschlossen werden.|  
|column_name|Gibt eine Spalte an.|  
|Funktion|Eine integrierte Funktion.|  
|Operator|Arithmetischer oder bitweiser Operator bzw. ein Vergleichs- oder Zeichenfolgenoperator.|  
|AND|Wird in booleschen Ausdrücken verwendet, um zwei Ausdrücke miteinander zu verbinden. Wenn beide Ausdrücke True sind, werden Ergebnisse zurückgegeben.<br /><br /> Wenn in einer Anweisung sowohl AND als auch OR verwendet werden, wird AND zuerst verarbeitet. Sie können die Reihenfolge der Ausführung ändern, indem Sie Klammern verwenden.|  
|oder|Wird in booleschen Ausdrücken verwendet, um zwei oder mehr Bedingungen miteinander zu verbinden. Wenn eine der beiden Bedingungen True ist, werden Ergebnisse zurückgegeben.<br /><br /> Wenn in einer Anweisung sowohl AND als auch OR verwendet werden, wird zuerst AND und dann OR ausgewertet. Sie können die Reihenfolge der Ausführung ändern, indem Sie Klammern verwenden.|  
|NICHT|Negiert jeden booleschen Ausdruck (auch Schlüsselwörter wie LIKE, NULL, BETWEEN, IN und EXISTS).<br /><br /> Wenn mehrere logische Operatoren in einer Anweisung verwendet werden, wird NOT zuerst verarbeitet. Sie können die Reihenfolge der Ausführung ändern, indem Sie Klammern verwenden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Unique- und Check-Einschränkungen](../../relational-databases/tables/unique-constraints-and-check-constraints.md)   
 [Erstellen von Unique-Einschränkungen](../../relational-databases/tables/create-unique-constraints.md)  
  
  
