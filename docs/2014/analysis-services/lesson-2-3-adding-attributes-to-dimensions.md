---
title: Hinzufügen von Attributen zu Dimensionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 80551dad-97ac-40d0-90af-b810780321ce
caps.latest.revision: 15
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 19fdf91a124a02da60e91c28a6f6be42fd5f2e42
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37198490"
---
# <a name="adding-attributes-to-dimensions"></a>Hinzufügen von Attributen zu Dimensionen
  Nachdem Sie Dimensionen definiert haben, können Sie sie jetzt mit Attributen auffüllen, die die einzelnen Datenelemente in der Dimension darstellen. Attribute basieren normalerweise auf Feldern einer Datenquellensicht. Wenn Sie einer Dimension Attribute hinzufügen, können Sie Felder einer beliebigen Tabelle in die Datenquellensicht einschließen.  
  
 In dieser Aufgabe verwenden Sie den Dimensions-Designer, um der Customer-Dimension und der Produkt-Dimension Attribute hinzuzufügen. Die Customer-Dimension schließt Attribute ein, die auf Feldern sowohl aus der Customer-Tabelle als auch aus der Geography-Tabelle basieren.  
  
## <a name="adding-attributes-to-the-customer-dimension"></a>Hinzufügen von Attributen zur Customer-Dimension.  
  
#### <a name="to-add-attributes"></a>So fügen Sie Attribute hinzu  
  
1.  Öffnen Sie den Dimensions-Designer für die Customer-Dimension. Doppelklicken Sie dazu auf die Dimension **Customer** im Knoten **Dimensionen** des Projektmappen-Explorers.  
  
2.  Beachten Sie im Bereich **Attribute** die Attribute "Customer Key" und "Geography Key", die vom Cube-Assistenten erstellt wurden.  
  
3.  Verwenden Sie das Symbol zum Vergrößern auf der Symbolleiste der Registerkarte **Dimensionsstruktur** , um die Tabellen im Bereich **Datenquellensicht** in einer 100-Prozent-Darstellung anzuzeigen.  
  
4.  Ziehen Sie die folgenden Spalten von der **Customer** -Tabelle im Bereich **Datenquellensicht** in den Bereich **Attribute** :  
  
    -   **BirthDate**  
  
    -   **MaritalStatus**  
  
    -   **Geschlecht**  
  
    -   **EmailAddress**  
  
    -   **YearlyIncome**  
  
    -   **TotalChildren**  
  
    -   **NumberChildrenAtHome**  
  
    -   **EnglishEducation**  
  
    -   **EnglishOccupation**  
  
    -   **HouseOwnerFlag**  
  
    -   **NumberCarsOwned**  
  
    -   **Phone**  
  
    -   **DateFirstPurchase**  
  
    -   **CommuteDistance**  
  
5.  Ziehen Sie die folgenden Spalten von der **Geography** -Tabelle im Bereich **Datenquellensicht** in den Bereich **Attribute** :  
  
    -   **City**  
  
    -   **StateProvinceName**  
  
    -   **EnglishCountryRegionName**  
  
    -   **PostalCode**  
  
6.  Klicken Sie im Menü Datei auf **Alle speichern**.  
  
## <a name="adding-attributes-to-the-product-dimension"></a>Hinzufügen von Attributen zur Product-Dimension.  
  
#### <a name="to-add-attributes"></a>So fügen Sie Attribute hinzu  
  
1.  Öffnen Sie den Dimensions-Designer für die Product-Dimension. Doppelklicken Sie im Projektmappen-Explorer auf die Dimension **Product** .  
  
2.  Beachten Sie im Bereich **Attribute** das Attribut "Product Key", das vom Cube-Assistenten erstellt wurde.  
  
3.  Verwenden Sie das Symbol zum Vergrößern auf der Symbolleiste der Registerkarte **Dimensionsstruktur** , um die Tabellen im Bereich **Datenquellensicht** in einer 100-Prozent-Darstellung anzuzeigen.  
  
4.  Ziehen Sie die folgenden Spalten von der **Product** -Tabelle im Bereich **Datenquellensicht** in den Bereich **Attribute** :  
  
    -   **StandardCost**  
  
    -   **Farbe**  
  
    -   **SafetyStockLevel**  
  
    -   **ReorderPoint**  
  
    -   **ListPrice**  
  
    -   **Größe**  
  
    -   **SizeRange**  
  
    -   **Weight**  
  
    -   **DaysToManufacture**  
  
    -   **ProductLine**  
  
    -   **DealerPrice**  
  
    -   **Class**  
  
    -   **Style**  
  
    -   **ModelName**  
  
    -   **StartDate**  
  
    -   **EndDate**  
  
    -   **Status**  
  
5.  Klicken Sie im Menü Datei auf **Alle speichern**.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Überprüfen von Cube- und Dimensionseigenschaften](lesson-2-4-reviewing-cube-and-dimension-properties.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Dimensionsattributeigenschaften-Verweis](multidimensional-models/dimension-attribute-properties-reference.md)  
  
  