---
title: "Dialogfeld &#39;Neue Bedingung erstellen&#39; oder &#39;Bedingung &#246;ffnen&#39;, Seite &#39;Allgemein&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.dmf.condition.f1"
ms.assetid: 106954bf-e4ba-412b-9c1a-907d06153dcd
caps.latest.revision: 30
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 30
---
# Dialogfeld &#39;Neue Bedingung erstellen&#39; oder &#39;Bedingung &#246;ffnen&#39;, Seite &#39;Allgemein&#39;
  Mithilfe dieses Dialogfelds können Sie eine richtlinienbasierte Verwaltungsbedingung erstellen oder ändern. Eine Bedingung ist ein boolescher Ausdruck, der einen Satz zulässiger Zustände eines durch die richtlinienbasierte Verwaltung verwalteten Ziels für Facets angibt. Die Eigenschaften, die im Feld **Ausdruck/Feld** ausgewählt werden können, hängen vom verwendeten Facet ab. Weitere Informationen darüber, wie Bedingungen mit Facets und Richtlinien zusammenhängen finden Sie unter [Verwalten von Servern mit der richtlinienbasierten Verwaltung](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md).  
  
## Optionen  
 **Name**  
 Geben Sie für eine Bedingung den Namen der neuen Bedingung ein. Für eine vorhandene Bedingung wird der Name angezeigt.  
  
 **Facet**  
 Das von dieser Bedingung verwendete Facet.  
  
 **And/Or**  
 Wenn Sie mehrere Ausdrücke hinzufügen, wird hiermit angegeben, ob die Ausdrücke mit **Und** oder **Oder** verbunden werden sollen. Bleibt leer, wenn nur ein Ausdruck vorhanden ist.  
  
 **Feld**  
 Jedes Facet macht eine oder mehrere Eigenschaften verfügbar, die festgelegt werden können. Wählen Sie im Feld Feld eine Eigenschaft aus der Liste der verfügbaren Eigenschaften aus, um einen Ausdruck für diese Bedingung zu erstellen.  
  
 **Operator**  
 Wählen Sie einen Vergleichsoperator für diesen Ausdruck aus. Folgende Operatoren sind verfügbar: =, !=, >, >=, <, <=, [NOT]LIKE, [NOT]IN. Für einige Eigenschaften sind nicht alle Operatoren verfügbar.  
  
 **Wert**  
 Die Werteinstellung für diesen Ausdruck. Die zulässigen Werte hängen vom Facet ab. Werte können WAHR/FALSCH, eine Zeichenfolge oder ein numerischer Wert sein. Zeichenfolgenwerte müssen in einfache Anführungszeichen eingeschlossen werden, z. B.: **'AdventureWorks'**. Für einige Eigenschaften sind nicht alle Operatoren verfügbar.  
  
## Klauseln gruppieren  
 Klauseln können gruppiert werden, sodass sie vom Rest der Abfrage getrennt als einzelne Einheit ausgeführt werden. Dies ist mit Klammern um einen Ausdruck in einer mathematischen Gleichung oder einer Logikaussage vergleichbar. Das Gruppieren von Klauseln ist beim Erstellen von komplexen Abfragen hilfreich.  
  
 **So gruppieren Sie Klauseln**  
  
-   Drücken Sie UMSCHALT oder STRG, und klicken Sie dann auf zwei oder mehr Klauseln, um einen Bereich auszuwählen. Klicken Sie mit der rechten Maustaste auf den ausgewählten Bereich, und klicken Sie anschließend auf **Klauseln gruppieren**.  
  
## Siehe auch  
 [Verwalten von Servern mit der richtlinienbasierten Verwaltung](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  