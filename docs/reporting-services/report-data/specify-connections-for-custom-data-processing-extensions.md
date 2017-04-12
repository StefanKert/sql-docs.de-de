---
title: "Angeben von Verbindungen f&#252;r benutzerdefinierte Datenverarbeitungserweiterungen | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Benutzerdefinierte Datenverarbeitungserweiterungen [Reporting Services]"
  - "IDbConnection-Schnittstelle, Verbindungszeichenfolgen"
  - "Identitätswechsel [Reporting Services]"
  - "IDbConnectionExtension-Schnittstelle, Verbindungszeichenfolgen"
  - "Datenquellen [Reporting Services], Sicherheit"
  - "Verbindungszeichenfolgen [Reporting Services]"
  - "Anmeldeinformationen [Reporting Services]"
  - "Authentifizierung [Reporting Services]"
  - "Externe Datenquellen [Reporting Services]"
  - "Datenverarbeitungserweiterungen [Reporting Services], Verbindungen"
ms.assetid: 2cddc9ea-0e28-4350-80ae-332412908e47
caps.latest.revision: 20
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 20
---
# Angeben von Verbindungen f&#252;r benutzerdefinierte Datenverarbeitungserweiterungen
  Sie können benutzerdefinierte Datenverarbeitungserweiterungen von Drittanbietern auf einem Berichtsserver erstellen oder verwenden, um die Datenverarbeitungsfunktionen für unterstützte Datenquellen zu erweitern oder um weitere Typen von Datenquellen zu unterstützen, die in einer standardmäßigen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Installation nicht verfügbar sind. Verbindungen werden abhängig von der Implementierung unterschiedlich behandelt. Die folgenden Implementierungen sind für Datenverarbeitungserweiterungen verfügbar:  
  
-   Benutzerdefinierte [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-Datenanbieter (wenn Sie auf Daten aus DB2.NET-, Oracle-, ODP.NET- oder Teradata-Datenquellen zugreifen, verwenden Sie möglicherweise einen benutzerdefinierten .NET-Datenanbieter)  
  
-   Benutzerdefinierte Datenverarbeitungserweiterungen zur Unterstützung von <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection>  
  
-   Benutzerdefinierte Datenverarbeitungserweiterungen zur Unterstützung von <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension>  
  
> [!NOTE]  
>  Fragen Sie den betreffenden Drittanbieterprovider, wie Ihre benutzerdefinierte Datenverarbeitungserweiterung implementiert ist.  
  
## Identitätswechsel und benutzerdefinierte Datenverarbeitungserweiterungen  
 Falls die benutzerdefinierte Datenverarbeitungserweiterung die Verbindung mit Datenquellen mithilfe eines Identitätswechsels herstellt, müssen Sie die Anforderung mithilfe der Open-Methode an der Schnittstelle <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> oder <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension> stellen. Alternativ können Sie das Benutzeridentitätsobjekt (System.Security.Principal.WindowsIdentity) speichern und anschließend in den APIs der anderen Datenverarbeitungserweiterungen erneut verwenden.  
  
 In früheren Versionen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]wurden alle benutzerdefinierten Datenverarbeitungserweiterungen mit Benutzeridentitätswechsel aufgerufen. In diesem Release wird nur während des Aufrufs der Open-Methode die Identität des Benutzers angenommen. Falls für eine vorhandene Datenverarbeitungserweiterung die integrierte Sicherheit erforderlich ist, müssen Sie den Code so ändern, dass die Open-Methode verwendet wird, oder das Benutzeridentitätsobjekt speichern.  
  
## Verbindungen für benutzerdefinierte .NET Framework-Datenanbieter  
 Beim Konfigurieren eines Berichts für eine bestimmte Datenquelle legen Sie Eigenschaften fest, die den Datenquellentyp, die Verbindungszeichenfolge und die Anmeldeinformationen für den Zugriff auf die Datenquelle bestimmen. In der folgenden Tabelle sind die Anmeldeinformationstypen beschrieben, die für [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] -Datenanbieter unterstützt werden. Weitere Informationen zum Festlegen von Eigenschaften für Berichtsdatenquellen finden Sie unter [Angeben der Anmeldeinformationen und Verbindungsinformationen für Berichtsdatenquellen](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md).  
  
|Anmeldeinformationen|Verbindungen|  
|-----------------|-----------------|  
|Integrierte Sicherheit|Falls dies vom verwendeten Datenanbieter unterstützt wird, können Sie die integrierte Sicherheit von Windows verwenden. Die Anforderung wird mit den Anmeldeinformationen des aktuellen Benutzers gesendet.<br /><br /> Beim Definieren der Verbindungszeichenfolge müssen Sie Argumente einschließen, die die integrierte Sicherheit angeben (z.B. könnte die Verbindungszeichenfolge bei einer Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenquelle **Integrated Security=SSPI** enthalten).|  
|Windows-Authentifizierung|Sofern vom Datenprovider unterstützt, können Sie ein Windows-Domänenbenutzerkonto verwenden. Der Berichtsserver nimmt vor dem Aufruf der Datenverarbeitungserweiterung die Identität des Benutzerkontos an.<br /><br /> Beim Definieren der Verbindungszeichenfolge müssen Sie Argumente einschließen, die die integrierte Sicherheit angeben (z.B. könnte die Verbindungszeichenfolge bei einer Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenquelle **Integrated Security=SSPI** enthalten).|  
|Datenbank-Anmeldeinformationen|Die Datenbankauthentifizierung wird für Verbindungen über einen benutzerdefinierten .NET-Datenanbieter nicht unterstützt. In diesen Fällen kann vom Berichtsserver keine Verbindung hergestellt werden.|  
|Keine Anmeldeinformationen|Die Option zum Verzicht auf Anmeldeinformationen kann bei .NET-Datenanbietern verwendet werden. Falls das Konto für die unbeaufsichtigte Ausführung angegeben ist, werden die verwendeten Anmeldeinformationen durch die Verbindungszeichenfolge bestimmt. Der Berichtsserver nimmt zum Herstellen der Verbindung die Identität des Kontos für die unbeaufsichtigte Ausführung an.<br /><br /> Falls das Konto für die unbeaufsichtigte Ausführung nicht angegeben ist, kann keine Verbindung vom Berichtsserver hergestellt werden. Weitere Informationen zum Definieren des Kontos finden Sie unter [Konfigurieren des Kontos für die unbeaufsichtigte Ausführung &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).|  
  
## Verbindungen für IDbConnection  
 Wenn Sie eine benutzerdefinierte Datenverarbeitungserweiterung verwenden, die nur <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> unterstützt, müssen Sie die Verbindung folgendermaßen angeben:  
  
1.  Konfigurieren Sie das Konto für die unbeaufsichtigte Ausführung. Das Konfigurieren des Kontos ist für Verbindungen erforderlich, die mit **IDbConnection**hergestellt werden. Der Berichtsserver nimmt die Identität des Kontos beim Herstellen der Verbindung an.  
  
2.  Konfigurieren Sie die Datenquelleneigenschaften für den Bericht mit der Option **Keine Anmeldeinformationen**.  
  
3.  Nehmen Sie die Anmeldeinformationen für die Verbindung mit der Datenquelle in die Verbindungszeichenfolge auf.  
  
 Bei Verwendung von **IDbConnection**werden die folgenden Anmeldeinformationstypen nicht unterstützt: integrierte Sicherheit, Windows-Benutzerkonten und Datenbank-Anmeldeinformationen. Wenn diese Optionen für eine Datenquellenverbindung verwendet werden, kann die Verbindung vom Berichtsserver nicht hergestellt werden.  
  
## Verbindungen für IDbConnectionExtension  
 Wenn Sie eine benutzerdefinierte Datenverarbeitungserweiterung verwenden, die <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension> unterstützt, können Sie die Verbindung auf folgende Arten angeben:  
  
|Anmeldeinformationen|Verbindungen|  
|-----------------|-----------------|  
|Integrierte Sicherheit|Falls dies vom Datenanbieter unterstützt wird, können Sie die integrierte Sicherheit von Windows bei benutzerdefinierten Datenverarbeitungserweiterungen verwenden, die **IDbConnectionExtension**verwenden.<br /><br /> Beim Definieren der Verbindungszeichenfolge müssen Sie Argumente einschließen, die die integrierte Sicherheit angeben (z.B. könnte die Verbindungszeichenfolge bei einer Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenquelle **Integrated Security=SSPI** enthalten).|  
|Windows-Authentifizierung|Sofern vom Datenprovider unterstützt, können Sie ein Windows-Domänenbenutzerkonto bei benutzerdefinierten Datenverarbeitungserweiterungen verwenden, die **IDbConnectionExtension**verwenden.<br /><br /> Der Berichtsserver nimmt vor dem Aufruf der Datenverarbeitungserweiterung die Identität des Benutzerkontos an. Beim Definieren der Verbindungszeichenfolge müssen Sie Argumente einschließen, die die integrierte Sicherheit angeben (z.B. könnte die Verbindungszeichenfolge bei einer Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenquelle **Integrated Security=SSPI** enthalten).|  
|Datenbank-Anmeldeinformationen|Sie können Verbindungen mit benutzerdefinierten Datenverarbeitungserweiterungen, die **IDbConnectionExtension**verwenden, mit der Datenbankauthentifizierung konfigurieren.|  
|Keine Anmeldeinformationen|Falls das Konto für die unbeaufsichtigte Ausführung angegeben ist, werden die verwendeten Anmeldeinformationen durch die Verbindungszeichenfolge bestimmt.<br /><br /> Falls das Konto für die unbeaufsichtigte Ausführung nicht angegeben ist, kann keine Verbindung vom Berichtsserver hergestellt werden.|  
  
## Siehe auch  
 [Konfigurieren des Kontos für die unbeaufsichtigte Ausführung &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)   
 [Angeben der Anmeldeinformationen und Verbindungsinformationen für Berichtsdatenquellen](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)   
 [Implementieren von Datenverarbeitungserweiterungen](../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../Topic/Report%20Manager%20%20\(SSRS%20Native%20Mode\).md)   
 [Erstellen, Löschen oder Ändern einer freigegebenen Datenquelle &#40;Berichts-Manager&#41;](../Topic/Create,%20Delete,%20or%20Modify%20a%20Shared%20Data%20Source%20\(Report%20Manager\).md)   
 [Konfigurieren von Datenquelleneigenschaften für einen Bericht &#40;Berichts-Manager&#41;](../../reporting-services/report-data/configure-data-source-properties-for-a-report-report-manager.md)  
  
  