---
title: Eingabeaufforderungs-Hilfsprogramme für Berichtsserver (SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- rsconfig utility
- components [Reporting Services], command line utilities
- rs utility
- command prompt utilities [Reporting Services]
- rskeymgmt utility
ms.assetid: 68f2f9f4-f894-40ff-a71c-f9756bf4b68c
caps.latest.revision: 48
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 637b1a53587f8b0405842a7f228ba7a380a1621f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37265736"
---
# <a name="report-server-command-prompt-utilities-ssrs"></a>Eingabeaufforderungs-Hilfsprogramme für Berichtsserver (SSRS)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] enthält mehrere Befehlszeilen-Hilfsprogramme, die Sie zum Verwalten eines Berichtsservers verwenden können. Diese Hilfsprogramme werden beim Installieren eines Berichtsservers automatisch installiert.  
  
|Name|Befehlsdatei|Unterstützter Bereitstellungsmodus|Description|  
|----------|------------------|-------------------------------|-----------------|  
|RSS-Hilfsprogramm|rs.exe|Einheitlicher Modus und SharePoint-Modus. In der [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] -Version wurde die SharePoint-Modusunterstützung eingeführt.|Das [rs-Hilfsprogramm](rs-exe-utility-ssrs.md) ist ein Skripthost, den Sie zum Ausführen von Skriptvorgängen verwenden können. Führen Sie mit diesem Tool [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] -Skripts aus, die Daten zwischen Berichtsserver-Datenbanken kopieren, Berichte veröffentlichen, Elemente in einer Berichtsserver-Datenbank erstellen usw. Weitere Informationen zur Verwendung von Scripts in der Severadministration finden Sie unter [Skripts für Bereitstellungs- und Verwaltungsaufgaben](script-deployment-and-administrative-tasks.md).|  
|PowerShell-Cmdlets||Nur SharePoint|Eine Liste mit den Powershell-Cmdlets finden Sie unter [PowerShell-Cmdlets für SharePoint-Modus von Reporting Services](../powershell-cmdlets-for-reporting-services-sharepoint-mode.md).|  
|rsconfig (Hilfsprogramm)|rsconfig.exe|Nur systemeigen|Die [Rsconfig-Hilfsprogramm](rsconfig-utility-ssrs.md) dient zum Konfigurieren und verwalten eine berichtsserververbindung mit der Berichtsserver-Datenbank. Darüber hinaus können Sie damit ein Benutzerkonto für die unbeaufsichtigte Berichtsverarbeitung angeben. Weitere Informationen finden Sie unter [Reporting Services-Berichtsserver &#40;einheitlicher Modus&#41;](../report-server/reporting-services-report-server-native-mode.md). Weitere Informationen zur Verbindungskonfiguration finden Sie unter [Konfigurieren einer Verbindung mit der Berichtsserver-Datenbank (SSRS-Konfigurations-Manager)](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).|  
|Hilfsprogramm rskeymgmt|rskeymgmt.exe|Nur systemeigen|Die [Rskeymgmt-Hilfsprogramm](rskeymgmt-utility-ssrs.md) ist ein Verwaltungstool für Verschlüsselungsschlüssel. Mit diesem Programm können Sie symmetrische Schlüssel sichern, anwenden, neu erstellen und löschen. Außerdem können Sie mit diesem Tool eine Berichtsserverinstanz an eine freigegebene Berichtsserver-Datenbank anfügen. Rskeymgmt kann bei Wiederherstellungsvorgängen für Datenbanken verwendet werden. Sie können eine vorhandene Datenbank in einer neuen Installation erneut verwenden, indem Sie eine Sicherungskopie des symmetrischen Schlüssels anwenden. Wenn die Schlüssel nicht wiederhergestellt werden können, bietet das Tool eine Möglichkeit zum Löschen nicht mehr benötigter verschlüsselter Inhalte. Weitere Informationen über das Verwalten von Schlüsseln und das Speichern sensibler Daten finden Sie unter [Speichern verschlüsselter Berichtsserverdaten (SSRS-Konfigurations-Manager)](../install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) und [Konfigurieren und Verwalten von Verschlüsselungsschlüsseln (SSRS-Konfigurations-Manager)](../install-windows/ssrs-encryption-keys-manage-encryption-keys.md).|  
  
> [!NOTE]  
>  Wenn Sie ein Tool verwenden, die über eine grafische Benutzeroberfläche verfügt lieber, können Sie den Reporting Services Configuration Manager statt `rsconfig` und `rskeymgmt`.  
  
## <a name="see-also"></a>Siehe auch  
 [Reporting Services-Konfigurations-Manager &#40;im einheitlichen Modus&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)   
 [Reporting Services-Tools](reporting-services-tools.md)   
 [Reporting Services-Berichtsserver (einheitlicher Modus)](../report-server/reporting-services-report-server-native-mode.md)  
  
  
