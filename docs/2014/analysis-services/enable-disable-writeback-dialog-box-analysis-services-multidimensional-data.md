---
title: Dialogfeld "Rückschreiben" (Analysis Services – mehrdimensionale Daten) aktivieren und deaktivieren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitiondesigner.writebackenabledisable.f1
ms.assetid: 2d254393-3f0d-4b70-8b98-87159f9f3639
caps.latest.revision: 22
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a7c5265987b846425aff4069a723804f009a013e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37286196"
---
# <a name="enable-disable-writeback-dialog-box-analysis-services---multidimensional-data"></a>Deaktivieren Sie aktivieren und das Rückschreiben Dialogfeld (Analysis Services – mehrdimensionale Daten)
  Im Dialogfeld **Rückschreiben aktivieren/deaktivieren** wird das Rückschreiben für eine Measuregruppe in einem Cube aktiviert oder deaktiviert. Wenn Sie das Rückschreiben für eine Measuregruppe aktivieren, wird eine Rückschreibepartition definiert und eine Rückschreibetabelle für die Measuregruppe erstellt. Wenn Sie das Rückschreiben für eine Measuregruppe deaktivieren, wird die Rückschreibepartition entfernt; die Rückschreibetabelle wird jedoch nicht gelöscht, um einen unerwarteten Datenverlust zu vermeiden. Das Dialogfeld **Rückschreiben aktivieren/deaktivieren** kann folgendermaßen angezeigt werden:  
  
-   Klicken Sie im Cube-Designer auf der Registerkarte **Partitionen** im Bereich **Measuregruppen** auf **Rückschreibeeinstellungen** .  
  
-   Klicken Sie im Cube-Designer auf der Registerkarte **Partitionen** im Bereich **Measuregruppen** im Raster **Partitionen** mit der rechten Maustaste auf eine Partition, und wählen Sie im Kontextmenü **Rückschreibeeinstellungen** aus.  
  
## <a name="options"></a>Tastatur  
 **Tabellenname**  
 Geben Sie den Namen der Rückschreibetabelle ein, die für die ausgewählte Partition erstellt werden soll. Die Rückschreibetabelle speichert die Änderungen, die an der Measuregruppe von einer Clientanwendung aus durchgeführt wurden.  
  
> [!NOTE]  
>  Diese Option ist deaktiviert, wenn das Rückschreiben nicht aktiviert wurde.  
  
 **Datenquelle**  
 Wählen Sie die Datenquelle zum Speichern der Rückschreibetabelle aus.  
  
> [!NOTE]  
>  Diese Option ist deaktiviert, wenn das Rückschreiben nicht aktiviert wurde.  
  
 **Neu**  
 Klicken Sie auf diese Option, um das Dialogfeld **Verbindungs-Manager** anzuzeigen, und definieren Sie eine neue Datenquelle, die die Rückschreibetabelle enthalten soll.  
  
> [!NOTE]  
>  Diese Option ist deaktiviert, wenn das Rückschreiben nicht aktiviert wurde.  
  
  
