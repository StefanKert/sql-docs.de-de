---
title: DataSet Properties Dialog Box, Felder | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.datasetproperties.fields.f1
- "10140"
ms.assetid: e1367556-736e-4a6b-b9e7-10432a3e50b5
caps.latest.revision: 36
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ad672dfa5e9161e781d2caf975e5511126924c2d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37274136"
---
# <a name="dataset-properties-dialog-box-fields"></a>Dataseteigenschaften (Dialogfeld), Felder
  Wählen Sie im Dialogfeld **Dataseteigenschaften** die Option **Felder** aus, um die Feldauflistung für das Berichtsdataset zu ändern. Die Felderliste wird automatisch aufgefüllt, Sie können jedoch mithilfe der Option **Felder** Abfragefelder und berechnete Felder hinzufügen, bearbeiten und löschen.  
  
## <a name="options"></a>Tastatur  
 **Hinzufügen**  
 Fügt dem Dataset ein neues Abfragefeld oder berechnetes Feld hinzu.  
  
 **Delete**  
 Löscht das ausgewählte Feld aus dem Dataset.  
  
 **Name des Felds**  
 Geben Sie einen Namen für das Feld ein. Der Name des Felds muss innerhalb des Datasets eindeutig sein. Für jedes vorhandene Feld in der Datasetabfrage ist der Name bereits eingetragen.  
  
 **Feldquelle**  
 Geben Sie einen Wert für das Feld ein.  
  
 Bei einem berechneten Feld muss die Feldquelle dem Namen eines vorhandenen Felds, das von der Datasetabfrage abgerufen wird, oder einem Ausdruck entsprechen, den Sie erstellen. Beispiel: Um ein Feld zu erstellen, das 10 mal den Wert im Abfragefeld Sales darstellt, verwenden Sie folgenden Ausdruck `=10 * Fields!Sales.Value`.  
  
 Bei einem Abfragefeld muss die Feldquelle dem Namen eines vorhandenen Felds entsprechen, das von der Datasetabfrage abgerufen wurde.  
  
 **Ausdruck (fx)**  
 Fügen Sie einen Ausdruck für das berechnete Feld hinzu, oder ändern Sie diesen. Diese Schaltfläche wird nur angezeigt, wenn Sie auf **Hinzufügen** klicken und **Berechnetes Feld**auswählen.  
  
## <a name="see-also"></a>Siehe auch  
 [Datasetfeld-Sammlung &#40;Berichts-Generator und SSRS&#41;](report-data/dataset-fields-collection-report-builder-and-ssrs.md)   
 [Hinzufügen von Daten zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](report-data/report-datasets-ssrs.md)   
 [Ausdrücke &#40;Berichts-Generator und SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md)  
  
  
