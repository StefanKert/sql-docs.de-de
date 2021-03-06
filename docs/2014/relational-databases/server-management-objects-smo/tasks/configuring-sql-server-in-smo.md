---
title: Konfigurieren von SQLServer in SMO | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server, configuring
- configuration options [SMO]
ms.assetid: 0a372643-15cb-45a7-8665-04f1215df8ed
caps.latest.revision: 40
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 56be654635390f824817aaf90b5ab1cdb9d085be
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37260446"
---
# <a name="configuring-sql-server-in-smo"></a>Konfigurieren von SQL Server in SMO
  In SMO werden die <xref:Microsoft.SqlServer.Management.Smo.Information> -Objekt, das <xref:Microsoft.SqlServer.Management.Smo.Settings> -Objekt, die <xref:Microsoft.SqlServer.Management.Smo.UserOptions> -Objekt, und die <xref:Microsoft.SqlServer.Management.Smo.Configuration> Objekt enthalten, Einstellungen und Informationen für die Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verfügt über zahlreiche Eigenschaften, die das Verhalten der installierten Instanz beschreiben. Die Eigenschaften beschreiben die Startoptionen, die Serverstandardwerte, Dateien und Verzeichnisse, System- und Prozessorinformationen, Produkt und Versionen, Verbindungsinformationen, Speicheroptionen, Sprach- und Sortierungsauswahl und den Authentifizierungsmodus.  
  
## <a name="sql-server-configuration"></a>SQL Server-Konfiguration  
 Die <xref:Microsoft.SqlServer.Management.Smo.Information> -Objekteigenschaften enthalten Informationen über die Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], z. B. Prozessor und Plattform.  
  
 Die <xref:Microsoft.SqlServer.Management.Smo.Settings> -Objekteigenschaften enthalten Informationen über die Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Die Standard-Datenbankdatei und das Standardverzeichnis können zusätzlich zum Mailprofil und Serverkonto geändert werden. Diese Eigenschaften bleiben für die Dauer der Verbindung erhalten.  
  
 Die <xref:Microsoft.SqlServer.Management.Smo.UserOptions>-Objekteigenschaften enthalten Informationen über das aktuelle Verbindungsverhalten im Zusammenhang mit Arithmetik, ANSI-Standards und Transaktionen.  
  
 Es gibt auch einen Satz an Konfigurationsoptionen, die durch dargestellt wird die <xref:Microsoft.SqlServer.Management.Smo.Configuration> Objekt. Er enthält eine Eigenschaftengruppe, die die Optionen darstellt, die durch die gespeicherte Prozedur `sp_configure` geändert werden können. Optionen wie z. B. **Priority Boost**, **Wiederherstellungsintervall** und **Network Packet Size**kontrollieren die Leistung der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Viele dieser Optionen können dynamisch geändert werden. In einigen Fällen allerdings wird zunächst der Wert konfiguriert und dann geändert, wenn die Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] neu gestartet wird.  
  
 Es gibt eine <xref:Microsoft.SqlServer.Management.Smo.Configuration> -Objekteigenschaft für jede Konfigurationsoption. Durch die Verwendung des <xref:Microsoft.SqlServer.Management.Smo.ConfigProperty>-Objekts können Sie die globale Konfigurationseinstellung ändern. Viele Eigenschaften verfügen über Maximal- und Minimalwerte, die auch als <xref:Microsoft.SqlServer.Management.Smo.ConfigProperty>-Eigenschaften gespeichert werden. Diese Eigenschaften erfordern die <xref:Microsoft.SqlServer.Management.Smo.ConfigurationBase.Alter%2A> Methode, um die Änderung zu übernehmen, mit der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Alle Konfigurationsoptionen in der <xref:Microsoft.SqlServer.Management.Smo.Configuration> -Objekt müssen vom Systemadministrator geändert werden.  
  
## <a name="examples"></a>Beispiele  
 Für die folgenden Codebeispiele müssen Sie die Programmierungsumgebung, die Programmiervorlage und die Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [erstellen Sie eine Visual Basic-SMO-Projekts in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) und [Erstellen eines Visual C&#35; SMO-Projekts in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="modifying-sql-server-configuration-options-in-visual-basic"></a>Ändern von SQL Server-Konfigurationsoptionen in Visual Basic  
 Im Codebeispiel wird gezeigt, wie eine Konfigurationsoption in Visual Basic .NET aktualisiert wird. Weiterhin ruft es Informationen über Maximal- und Minimalwerte für die angegebene Konfigurationsoption ab und stellt diese dar. Schließlich informiert das Programm des Benutzers, wenn die Änderung dynamisch vorgenommen wurde oder wenn sie, bis die Instanz von gespeichert ist [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] neu gestartet wird.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBConfigure2](SMO How to#SMO_VBConfigure2)]  -->  
  
## <a name="modifying-sql-server-settings-in-visual-basic"></a>Ändern von SQL Server-Einstellungen in Visual Basic  
 Das Codebeispiel zeigt Informationen über die Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in <xref:Microsoft.SqlServer.Management.Smo.Information> und <xref:Microsoft.SqlServer.Management.Smo.Settings>, und ändert die Einstellungen in <xref:Microsoft.SqlServer.Management.Smo.Settings> und <xref:Microsoft.SqlServer.Management.Smo.UserOptions>Objekteigenschaften.  
  
 Im Beispiel verfügen sowohl das <xref:Microsoft.SqlServer.Management.Smo.UserOptions>-Objekt als auch das <xref:Microsoft.SqlServer.Management.Smo.Settings>-Objekt über eine <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A>-Methode. Sie können ausführen, die <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> -Methoden für diese einzeln.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBConfigure1](SMO How to#SMO_VBConfigure1)]  -->  
  
## <a name="modifying-sql-server-settings-in-visual-c"></a>Ändern von SQL Server-Einstellungen in Visual C#  
 Das Codebeispiel zeigt Informationen über die Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in <xref:Microsoft.SqlServer.Management.Smo.Information> und <xref:Microsoft.SqlServer.Management.Smo.Settings>, und ändert die Einstellungen in <xref:Microsoft.SqlServer.Management.Smo.Settings> und <xref:Microsoft.SqlServer.Management.Smo.UserOptions>Objekteigenschaften.  
  
 Im Beispiel verfügen sowohl das <xref:Microsoft.SqlServer.Management.Smo.UserOptions>-Objekt als auch das <xref:Microsoft.SqlServer.Management.Smo.Settings>-Objekt über eine <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A>-Methode. Sie können ausführen, die <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> -Methoden für diese einzeln.  
  
 `//Connect to the local, default instance of SQL Server.`  
  
```  
{  
            Server srv = new Server();  
            //Display all the configuration options.   
  
            foreach (ConfigProperty p in srv.Configuration.Properties)  
            {  
                Console.WriteLine(p.DisplayName);  
            }  
            Console.WriteLine("There are " + srv.Configuration.Properties.Count.ToString() + " configuration options.");  
            //Display the maximum and minimum values for ShowAdvancedOptions.   
            int min = 0;  
            int max = 0;  
            min = srv.Configuration.ShowAdvancedOptions.Minimum;  
            max = srv.Configuration.ShowAdvancedOptions.Maximum;  
            Console.WriteLine("Minimum and Maximum values are " + min + " and " + max + ".");  
            //Modify the value of ShowAdvancedOptions and run the Alter method.   
            srv.Configuration.ShowAdvancedOptions.ConfigValue = 0;  
            srv.Configuration.Alter();  
            //Display when the change takes place according to the IsDynamic property.   
            if (srv.Configuration.ShowAdvancedOptions.IsDynamic == true)  
            {  
                Console.WriteLine("Configuration option has been updated.");  
            }  
            else  
            {  
                Console.WriteLine("Configuration option will be updated when SQL Server is restarted.");  
            }  
        }  
```  
  
## <a name="modifying-sql-server-settings-in-powershell"></a>Ändern von SQL Server-Einstellungen in PowerShell  
 Das Codebeispiel zeigt Informationen über die Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in <xref:Microsoft.SqlServer.Management.Smo.Information> und <xref:Microsoft.SqlServer.Management.Smo.Settings>, und ändert die Einstellungen in <xref:Microsoft.SqlServer.Management.Smo.Settings> und <xref:Microsoft.SqlServer.Management.Smo.UserOptions>Objekteigenschaften.  
  
 Im Beispiel verfügen sowohl das <xref:Microsoft.SqlServer.Management.Smo.UserOptions>-Objekt als auch das <xref:Microsoft.SqlServer.Management.Smo.Settings>-Objekt über eine <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A>-Methode. Sie können ausführen, die <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> -Methoden für diese einzeln.  
  
```  
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\  
$srv = get-item default  
  
#Display information about the instance of SQL Server in Information and Settings.  
"OS Version = " + $srv.Information.OSVersion  
"State = "+ $srv.Settings.State.ToString()  
  
#Display information specific to the current user in UserOptions.  
"Quoted Identifier support = " + $srv.UserOptions.QuotedIdentifier  
  
#Modify server settings in Settings.  
$srv.Settings.LoginMode = [Microsoft.SqlServer.Management.SMO.ServerLoginMode]::Integrated  
  
#Modify settings specific to the current connection in UserOptions.  
$srv.UserOptions.AbortOnArithmeticErrors = $true  
  
#Run the Alter method to make the changes on the instance of SQL Server.  
$srv.Alter()  
```  
  
## <a name="modifying-sql-server-configuration-options-in-powershell"></a>Ändern von SQL Server-Konfigurationsoptionen in PowerShell  
 Im Codebeispiel wird gezeigt, wie eine Konfigurationsoption in Visual Basic .NET aktualisiert wird. Weiterhin ruft es Informationen über Maximal- und Minimalwerte für die angegebene Konfigurationsoption ab und stellt diese dar. Schließlich informiert das Programm des Benutzers, wenn die Änderung dynamisch vorgenommen wurde oder wenn sie, bis die Instanz von gespeichert ist [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] neu gestartet wird.  
  
```  
#Get a server object which corresponds to the default instance replace LocalMachine with the physical server  
cd \sql\LocalMachine  
$svr = get-item default  
  
#enumerate its properties  
foreach ($Item in $Svr.Configuration.Properties)   
{  
 $Item.DisplayName  
}  
  
"There are " + $svr.Configuration.Properties.Count.ToString() + " configuration options."  
  
#Display the maximum and minimum values for ShowAdvancedOptions.  
$min = $svr.Configuration.ShowAdvancedOptions.Minimum  
$max = $svr.Configuration.ShowAdvancedOptions.Maximum  
"Minimum and Maximum values are " + $min.ToString() + " and " + $max.ToString() + "."  
  
#Modify the value of ShowAdvancedOptions and run the Alter method.  
$svr.Configuration.ShowAdvancedOptions.ConfigValue = 0  
$svr.Configuration.Alter()  
  
#Display when the change takes place according to the IsDynamic property.  
If ($svr.Configuration.ShowAdvancedOptions.IsDynamic -eq $true)  
 {    
   "Configuration option has been updated."  
 }  
Else  
{  
    "Configuration option will be updated when SQL Server is restarted."  
}  
```  
  
  
