---
title: Ändern der Eigenschaften einer Miningstruktur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], properties
ms.assetid: 03b16897-2e36-42b8-9f7d-db1b9b898401
caps.latest.revision: 28
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 083133e43355f6f394c18654a23aa5366e3d5731
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37187687"
---
# <a name="change-the-properties-of-a-mining-structure"></a>Ändern der Eigenschaften einer Miningstruktur
  Es gibt zwei Arten von Eigenschaften in einer Miningstruktur, die jeweils geändert werden können:  
  
-   Eigenschaften der Miningstruktur, die die gesamte Struktur betreffen.  
  
-   Eigenschaften in einzelnen Spalten in der Struktur  
  
 Einige Eigenschaften sind von anderen Eigenschafteneinstellungen abhängig. Zum Beispiel können Sie erst Eigenschaften festlegen, die klassifizierendes Verhalten (z. B. <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> oder <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A>) steuern, wenn Sie den Datentyp der Spalte auf `Discretized` festgelegt haben.  
  
 Weitere Informationen zu Miningstruktureigenschaften finden Sie unter [Miningstrukturspalten](mining-structure-columns.md).  
  
### <a name="to-change-the-properties-of-a-mining-structure"></a>So ändern Sie die Eigenschaften einer Miningstruktur  
  
1.  Klicken Sie auf der Registerkarte **Miningstruktur** im Data Mining-Designer mit der rechten Maustaste entweder auf die Miningstruktur oder auf eine Spalte innerhalb der Miningstruktur, und klicken Sie anschließend auf **Eigenschaften**.  
  
     Im rechten Bildschirmbereich wird das **Eigenschaften** -Fenster geöffnet, wenn es nicht bereits sichtbar war.  
  
2.  Wählen Sie im **Eigenschaften** -Fenster den Wert aus, der der Eigenschaft entspricht, die Sie ändern möchten, und geben Sie dann den neuen Wert ein.  
  
     Der neue Wert wird wirksam, wenn Sie ein anderes Element im Designer auswählen.  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks und Anweisungen für Miningstrukturen](mining-structure-tasks-and-how-tos.md)  
  
  
