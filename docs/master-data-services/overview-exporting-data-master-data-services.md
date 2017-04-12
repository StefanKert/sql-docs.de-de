---
title: "&#220;bersicht: Exportieren von Daten (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Exportieren von Daten [Master Data Services]"
  - "Abonnementsichten [Master Data Services]"
  - "Abonnementsichten [Master Data Services], Informationen zu Abonnementsichten"
ms.assetid: 8b74409a-ea70-45f8-84c7-da6905e4901a
caps.latest.revision: 12
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 12
---
# &#220;bersicht: Exportieren von Daten (Master Data Services)
  In diesem Artikel werden die Abonnementsichtformate vorgestellt und erläutert, wann die Sichten aufgrund von Änderungen an Modellobjekten bearbeitet werden müssen.  
  
 Sie werden eine Abonnementsicht erstellen, um [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]-Daten in ein abonnierendes System wie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] zu exportieren. Sie nutzen das abonnierende System dazu, die Daten in der [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]-Datenbank anzuzeigen.  Informationen zum Erstellen der Abonnementsicht finden Sie unter [Erstellen einer Abonnementsicht zum Exportieren von Daten &#40;Master Data Services&#41;](../master-data-services/create-a-subscription-view-to-export-data-master-data-services.md)  
  
 Weitere Informationen zu Sichten finden Sie unter [Sichten](../relational-databases/views/views.md).  
  
## Abonnementsichtformate  
 Wenn Sie eine Sicht in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]erstellen, steht Ihnen eine Reihe von Standardsichtformaten in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] zur Auswahl. Mithilfe dieser Formate können Sie Sichten mit folgendem Inhalt erstellen:  
  
-   Alle Blattelemente und deren Attribute  
  
-   Alle konsolidierten Elemente und deren Attribute  
  
-   Alle Auflistungen und deren Attribute  
  
-   Die Elemente, die der Auflistung explizit hinzugefügt wurden  
  
-   Elemente in einer abgeleiteten Hierarchie in einem Format mit über- und untergeordneten Elementen oder Ebenen  
  
-   Elemente in allen expliziten Hierarchien für eine Entität in einem Format mit über- und untergeordneten Elementen oder Ebenen  
  
## Abonnementsichten können ihre Aktualität verlieren  
 Nachdem Sie für eine Entität oder eine Hierarchie eine Abonnementsicht erstellt haben, werden Änderungen an den zugeordneten Modellobjekten nicht automatisch in der Sicht widergespiegelt. Sie müssen eine Abonnementsicht in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ggf. erneut generieren, um Änderungen an den Modellobjekten widerzuspiegeln. Die Spalte **Geändert** auf der Seite **Exportieren** wird bei einer Änderung der Modellobjekte in **True** geändert. Der Wert**True** gibt an, dass Sie die Abonnementsicht bearbeiten und speichern sollten, um die Sicht erneut zu generieren.  
  
## Verwandte Aufgaben  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Erstellen Sie eine Abonnementsicht der Masterdaten.|[Erstellen einer Abonnementsicht zum Exportieren von Daten &#40;Master Data Services&#41;](../master-data-services/create-a-subscription-view-to-export-data-master-data-services.md)|  
|Löschen Sie eine vorhandene Abonnementsicht.|[Löschen einer Abonnementsicht &#40;Master Data Services&#41;](../master-data-services/delete-a-subscription-view-master-data-services.md)|  
  
## Verwandte Inhalte  
  
-   [Abonnementsichtformate &#40;Master Data Services&#41;](../master-data-services/subscription-view-formats-master-data-services.md)  
  
-   [Sichten](../relational-databases/views/views.md)  
  
  