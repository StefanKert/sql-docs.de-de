---
title: "Aktivieren der Data Quality Services-Integration in Master Data Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ab32938d-a80e-4106-80d4-94b2de3d67dc
caps.latest.revision: 5
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 5
---
# Aktivieren der Data Quality Services-Integration in Master Data Services
  Im [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] wird über die Data Quality Services (DQS) eine Abgleichfunktion bereitgestellt. Diese Funktion muss aktiviert werden, damit sie verwendet werden kann.  
  
## Voraussetzungen  
  
-   Es müssen eine [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]-Webanwendung und eine Datenbank vorhanden sein.  
  
-   Die Data Quality Services-Funktion und der Data Quality-Client müssen auf der gleichen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz installiert sein, auf der die MDS-Datenbank gehostet wird. Weitere Informationen finden Sie unter [Install Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md).  
  
### So aktivieren Sie die Data Quality Services-Integration  
  
1.  Öffnen Sie [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
2.  Klicken Sie im linken Bereich auf **Webkonfiguration**.  
  
3.  Wählen Sie auf der Seite **Webkonfiguration** die Website und die Webanwendung aus.  
  
4.  Klicken Sie im Abschnitt **DQS-Integration aktivieren** auf **Integration in Data Quality Services aktivieren**.  
  
5.  Klicken Sie im Bestätigungsdialogfeld auf **OK**.  
  
## Siehe auch  
 [Data Quality-Abgleich im MDS-Add-In für Excel](../../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)   
 [Master Data Services-Add-In für Microsoft Excel](../../master-data-services/microsoft-excel-add-in/master-data-services-add-in-for-microsoft-excel.md)   
 [Installieren von Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)  
  
  