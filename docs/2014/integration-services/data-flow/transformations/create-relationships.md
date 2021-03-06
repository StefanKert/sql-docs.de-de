---
title: Beziehungen erstellen | Microsoft Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.createrelationships.f1
ms.assetid: 6ebd305f-ffd2-4a1d-b24c-e28c151b94f5
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f2ca9f48a5f5cc545f89b226b869291ecef54907
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37269396"
---
# <a name="create-relationships"></a>Beziehungen erstellen
  Im Dialogfeld **Beziehungen erstellen** werden Zuordnungen zwischen Quellspalten und den von Ihnen im Transformations-Editor für Fuzzysuche, Transformations-Editor für Suche und Transformations-Editor für Ausdruckssuche konfigurierten Spalten von Nachschlagetabellen bearbeitet.  
  
> [!NOTE]  
>  Im Dialogfeld **Beziehungen erstellen** werden nur die Listen **Eingabespalte** und **Suchspalte** angezeigt, wenn der Aufruf aus dem Transformations-Editor für Ausdruckssuche erfolgt.  
  
 Weitere Informationen zu den Transformationen, die das Dialogfeld **Beziehungen erstellen** verwenden, finden Sie unter [Fuzzy Lookup Transformation](lookup-transformation.md), [Lookup Transformation](lookup-transformation.md)und [Term Lookup Transformation](term-lookup-transformation.md).  
  
## <a name="options"></a>Tastatur  
 **Eingabespalte**  
 Wählen Sie Spalten aus der Liste der verfügbaren Eingabespalten aus.  
  
 **Suchspalte**  
 Wählen Sie eine Option aus der Liste der verfügbaren Suchspalten aus.  
  
 **Zuordnungstyp**  
 Wählen Sie genaue oder Fuzzyübereinstimmungen aus.  
  
 Wenn Sie Fuzzyübereinstimmungen verwenden, werden Zeilen als doppelt erkannt, sobald sie in den Spalten, deren Übereinstimmungstyp Fuzzy lautet, ausreichende Übereinstimmungen aufweisen. Um bei der Fuzzyübereinstimmung bessere Ergebnisse zu erzielen, können Sie angeben, dass für einige Spalten anstelle von Fuzzy die genaue Übereinstimmung verwendet wird. Wenn Ihnen beispielsweise bekannt ist, dass eine bestimmte Spalte weder Fehler noch Inkonsistenzen aufweist, können Sie für diese Spalte die genaue Übereinstimmung angeben, sodass nur Zeilen, deren Werte genau mit Werten in der Spalte übereinstimmen, als mögliche Dopplungen erkannt werden. Dadurch erhöht sich die Genauigkeit der Fuzzyübereinstimmung für andere Spalten.  
  
 **Vergleichsflags**  
 Weitere Informationen zu den Optionen für das Vergleichen von Zeichenfolgen finden Sie unter [Vergleichen von Zeichenfolgendaten](../comparing-string-data.md).  
  
 **Minimale Ähnlichkeit**  
 Legen Sie mithilfe des Schiebereglers den Schwellenwert für die Ähnlichkeit auf Spaltenebene fest. Je näher der Wert an 1 liegt, desto stärker muss die Ähnlichkeit zwischen Suchwert und Quellwert sein, um als Übereinstimmung zu gelten. Durch eine Erhöhung des Schwellenwertes kann die Geschwindigkeit beim Abgleich erhöht werden, weil als Kandidaten dann weniger Datensätze berücksichtigt werden müssen.  
  
 **Ähnlichkeitsausgabealias**  
 Geben Sie den Namen für eine Ausgabespalte an, die die Ähnlichkeitsergebnisse für die ausgewählte Spalte enthält. Wenn Sie diesen Wert nicht angeben, wird die Ausgabespalte nicht erstellt.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Meldungsreferenz von Integration Services-Fehler](../../integration-services-error-and-message-reference.md)   
 [Transformations-Editor für Fuzzysuche &#40;Registerkarte „Spalten“&#41;](../../fuzzy-lookup-transformation-editor-columns-tab.md)   
 [Transformations-Editor für Suche &#40;Seite „Spalten“&#41;](../../lookup-transformation-editor-columns-page.md)   
 [Transformations-Editor Begriff &#40;Registerkarte Ausdruckssuche&#41;](../../term-lookup-transformation-editor-term-lookup-tab.md)  
  
  
