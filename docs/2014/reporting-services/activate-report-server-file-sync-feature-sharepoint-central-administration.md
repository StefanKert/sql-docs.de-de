---
title: Aktivieren der Synchronisierung Berichtsserverdateien in der SharePoint-Zentraladministration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 32d1988d-07e7-41c2-b636-e65ecfae4677
caps.latest.revision: 8
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: e85c5ff71ba83704752ae55057fb47777becd55b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37258156"
---
# <a name="activate-the-report-server-file-sync-feature-in-sharepoint-central-administration"></a>Aktivieren der Funktion zur Synchronisierung der Berichtsserverdateien in der SharePoint-Zentraladministration
  Die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Funktion zur Synchronisierung der Berichtsserverdateien verwendet SharePoint-Ereignishandler, um den Berichtsserverkatalog mit Elementen in Dokumentbibliotheken zu synchronisieren. Diese Funktion ist nützlich, wenn Benutzer veröffentlichte Berichtselemente häufig direkt in die SharePoint-Dokumentbibliotheken hochladen. Wenn die Dateisynchronisierungsfunktion nicht aktiviert ist, werden Inhalte weiterhin synchronisiert. Dies erfolgt allerdings nicht so häufig.  
  
 Die File Sync-Funktion kann in SharePoint-Websiteverwaltung aktiviert werden, nach der Installation der [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] Add-in für SharePoint-Produkte.  
  
 Die Funktion kann für einzelne Websites manuell aktiviert und deaktiviert werden, jedoch nicht auf Ebene der Websitesammlung.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Das [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Add-In für SharePoint muss installiert sein. Falls das Add-In nicht installiert ist, wird die Dateisynchronisierungsfunktion nicht in der Funktionsliste der Website angezeigt.  
  
 Um die Installation zu überprüfen, zeigen Sie die Liste der installierten Anwendungen in [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows **Systemsteuerung**. Wenn die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Add-in installiert ist, führen Sie die Anweisungen in diesem Thema, um die Synchronisierung der Berichtsserverdateien zu aktivieren.  
  
### <a name="to-activate-or-deactivate-the-reporting-services-file-sync-feature-on-a-site"></a>So aktivieren oder deaktivieren Sie die Funktion zur Synchronisierung der Berichtsserverdateien auf einer Website  
  
1.  Klicken Sie auf der Hauptseite der Website auf das Menü **Websiteaktionen** , und klicken Sie dann auf **Siteeinstellungen**.  
  
2.  Klicken Sie im Bereich **Websiteaktionen** auf **Websitefunktionen verwalten**.  
  
3.  Suchen Sie **Synchronisierung der Berichtsserverdateien** in der Liste.  
  
4.  Klicken Sie auf **Aktivieren**.  
  
> [!NOTE]  
>  Gehen Sie auf die gleiche Weise vor, um die Funktion für die Synchronisierung von Berichtsserverdateien zu deaktivieren. Klicken Sie jedoch auf **Deaktivieren**.  
  
## <a name="see-also"></a>Siehe auch  
 [Problembehandlung bei Berichtsteilen &#40;Berichts-Generator und SSRS&#41;](report-parts-report-builder-and-ssrs.md)   
 [Aktivieren der Berichtsserver- und Power View-Integrationsfunktionen in SharePoint](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)   
 [Installieren oder Deinstallieren des Reporting Services Add-Ins für SharePoint &#40;SharePoint 2010 und SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)   
 [Installieren oder Deinstallieren des Reporting Services Add-Ins für SharePoint &#40;SharePoint 2010 und SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
