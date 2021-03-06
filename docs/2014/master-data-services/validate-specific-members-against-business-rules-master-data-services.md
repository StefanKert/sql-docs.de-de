---
title: Überprüfen von bestimmten Elementen auf Geschäftsregeln (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- applying business rules [Master Data Services]
- business rules [Master Data Services], applying to select members
ms.assetid: 2288ef43-5392-47ea-b651-ec25e5692a14
caps.latest.revision: 4
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 9f3a3c6f4c812c5fc68479ef8ed3499a9e02b386
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37314060"
---
# <a name="validate-specific-members-against-business-rules-master-data-services"></a>Überprüfen von bestimmten Elementen auf Geschäftsregeln (Master Data Services)
  Wenn Sie Teilmengen von Elementen aktualisieren oder mit Geschäftsregeln abgleichen möchten, können Sie in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]Geschäftsregeln selektiv anwenden.  
  
> [!NOTE]  
>  Wenn Sie Geschäftsregeln auf alle Elemente in einer Version eines Modells anwenden möchten, gehen Sie auf die Seite [Validate a Version against Business Rules &#40;Master Data Services&#41;](validate-a-version-against-business-rules-master-data-services.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung für den Zugriff auf den Funktionsbereich **Explorer** verfügen.  
  
-   Sie müssen mindestens die Berechtigung **Aktualisieren** für das Modellobjekt haben, auf das Sie Geschäftsregeln anwenden möchten.  
  
### <a name="to-apply-business-rules-selectively"></a>So wenden Sie Geschäftsregeln selektiv an  
  
1.  Wählen Sie auf der [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Startseite aus der Liste **Modell** ein Modell aus.  
  
2.  Wählen Sie aus der Liste **Version** eine Version aus.  
  
3.  Klicken Sie auf **Explorer**.  
  
4.  Zeigen Sie in der Menüleiste auf **Entitäten** und klicken Sie auf den Namen der Entität mit den Elementen, auf die Sie Regeln anwenden möchten.  
  
5.  Klicken Sie auf **Geschäftsregeln anwenden**. Die Geschäftsregeln werden nur auf die im Raster angezeigten Elemente angewendet.  
  
## <a name="see-also"></a>Siehe auch  
 [Überprüfen einer Version anhand von Geschäftsregeln &#40;Master Data Services&#41;](validate-a-version-against-business-rules-master-data-services.md)   
 [Geschäftsregeln &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
