---
title: Codezugriffssicherheit für CLR-Integration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- UNSAFE assemblies
- permissions [CLR integration]
- common language runtime [SQL Server], security
- SAFE assemblies
- code access security [CLR integration]
- EXTERNAL_ACCESS assemblies
ms.assetid: 2111cfe0-d5e0-43b1-93c3-e994ac0e9729
caps.latest.revision: 28
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: c2e0d51e1c3268fd7399467f22fb833e77f14131
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37349882"
---
# <a name="clr-integration-code-access-security"></a>CLR-Integration und Codezugriffssicherheit
  Die common Language Runtime (CLR) unterstützt ein Sicherheitsmodell namens Codezugriffssicherheit für verwalteten Code. In diesem Modell werden Assemblys Berechtigungen auf Grundlage der Identität des Codes gewährt. Weitere Informationen finden Sie im Abschnitt "Codezugriffsicherheit" im .NET Framework Software Development Kit.  
  
 Die Sicherheitsrichtlinie, die die Berechtigungen für Assemblys bestimmt, wird an drei verschiedenen Stellen definiert:  
  
-   Computerrichtlinie: Diese Richtlinie gilt für den gesamten verwalteten Code auf dem Computer, auf dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installiert ist.  
  
-   Benutzerrichtlinie: Diese Richtlinie ist für verwalteten Code gültig, der von einem Prozess gehostet wird. Für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Dienst wird ausgeführt.  
  
-   Hostrichtlinie: Diese Richtlinie wird vom Host der CLR (in diesem Fall [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]) eingerichtet, die für den verwalteten Code gültig ist, der auf diesem Host ausgeführt wird.  
  
 Der von der CLR unterstützte Codezugriffs-Sicherheitsmechanismus basiert auf der Annahme, dass die Laufzeit sowohl vollständig vertrauenswürdigen als auch teilweise vertrauenswürdigen Code hosten kann. Die durch die CLR-Codezugriffssicherheit geschützten Ressourcen werden von verwalteten Anwendungsprogrammierschnittstellen kennen, Requirethe für die entsprechende Berechtigung vor dem Zugriff auf die Ressource in der Regel eingeschlossen. Die Demandfor die Berechtigung, die erfüllt wird, nur, wenn alle aufrufenden Prozesse (auf Assemblyebene) in der Aufrufliste über die entsprechende Ressourcenberechtigung verfügen.  
  
 Der Satz von Berechtigungen für die Codezugriffssicherheit, die gewährt werden, verwaltetem Code aus, wenn die Ausführung [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gewährt einen Satz von Berechtigungen geladenen Assembly [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], der Benutzercode "Eventual" Berechtigungssatz ist möglicherweise eingeschränkt mithilfe der Benutzer und -Richtlinien auf Computerebene.  
  
## <a name="sql-server-host-policy-level-permission-sets"></a>Berechtigungssätze auf SQL Server Host-Richtlinienebene  
 Die Menge der Codezugriffsberechtigungen, die Assemblys von der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Hostrichtlinienebene gewährt wird, wird von dem Berechtigungssatz bestimmt, der beim Erstellen der Assembly angegeben wurde. Es gibt drei Berechtigungssätze: `SAFE`, `EXTERNAL_ACCESS` und `UNSAFE` (angegeben mit der **PERMISSION_SET** Option[CREATE ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-assembly-transact-sql)) .  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]installiert haben. Sie ist nicht für die Standardanwendungsdomäne bestimmt, die gültig ist, wenn [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] eine Instanz der CLR erstellt.  
  
 Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Fixedpolicy für Systemassemblys und der benutzerdefinierten Richtlinie für Benutzerassemblys.  
  
 Die feste Richtlinie für CLR-Assemblys und [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Systemassemblys verleiht ihnen volle Vertrauenswürdigkeit.  
  
 Der benutzerdefinierte Teil der Hostrichtlinie von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] basiert darauf, dass der Assemblybesitzer einen von drei Berechtigungsbuckets für jede Assembly angibt. Weitere Informationen über die unten aufgeführten Sicherheitsberechtigungen finden Sie unter .NET Framework SDK.  
  
### <a name="safe"></a>SAFE  
 Nur interne Berechnungen und lokaler Datenzugriff sind zulässig. `SAFE` ist der restriktivste Berechtigungssatz. Code, der von einer Assembly mit `SAFE`-Berechtigungen ausgeführt wird, hat keinen Zugriff auf externe Systemressourcen wie Dateien, das Netzwerk, Umgebungsvariablen oder die Registrierung.  
  
 `SAFE`-Assemblys verfügen über folgende Berechtigungen und Werte:  
  
|Berechtigung|Wert(e)/Beschreibung|  
|----------------|-----------------------------|  
|`SecurityPermission`|`Execution:` Berechtigung zur Ausführung von verwaltetem Code.|  
|`SqlClientPermission`|`Context connection = true`, `context connection = yes`: Es kann nur die Kontextverbindung verwendet werden, und die Verbindungszeichenfolge kann nur den Wert "context connection=true" oder "context connection=yes" angeben.<br /><br /> **AllowBlankPassword = False:** leere Kennwörter sind nicht zulässig.|  
  
### <a name="externalaccess"></a>EXTERNAL_ACCESS  
 EXTERNAL_ACCESS-Assemblys über die gleichen Berechtigungen wie `SAFE` Assemblys, mit der zusätzlichen Fähigkeit, auf externe Systemressourcen wie Dateien, Netzwerke, Webdienste, Umgebungsvariablen und die Registrierung zugreifen.  
  
 `EXTERNAL_ACCESS`-Assemblys verfügen außerdem über folgende Berechtigungen und Werte:  
  
|Berechtigung|Wert(e)/Beschreibung|  
|----------------|-----------------------------|  
|`DistributedTransactionPermission`|`Unrestricted:` Verteilte Transaktionen sind zulässig.|  
|`DNSPermission`|`Unrestricted:` Die Berechtigung zum Anfordern von Informationen von DNS-Servern.|  
|`EnvironmentPermission`|`Unrestricted:` Der vollständige Zugriff auf System- und Benutzerumgebungsvariablen ist zulässig.|  
|`EventLogPermission`|`Administer:` Folgende Aktionen sind zulässig: Erstellen einer Ereignisquelle, Lesen vorhandener Protokolle, Löschen von Ereignisquellen oder -protokollen, Reagieren auf Einträge, Löschen eines Ereignisprotokolls, Überwachen von Ereignissen und Zugreifen auf eine Auflistung sämtlicher Ereignisprotokolle.|  
|`FileIOPermission`|`Unrestricted:` Der vollständige Zugriff auf Dateien und Ordner ist zulässig.|  
|`KeyContainerPermission`|`Unrestricted:` Der vollständige Zugriff auf Schlüsselcontainer ist zulässig.|  
|`NetworkInformationPermission`|`Access:` Die Pingausführung ist zulässig.|  
|`RegistryPermission`|Lässt Leseberechtigungen für `HKEY_CLASSES_ROOT`, `HKEY_LOCAL_MACHINE`, `HKEY_CURRENT_USER`, `HKEY_CURRENT_CONFIG` und `HKEY_USERS.` zu.|  
|`SecurityPermission`|`Assertion:` Die Fähigkeit zu bestätigen, dass alle Aufrufer dieses Codes über die erforderliche Berechtigung für den Vorgang verfügen.<br /><br /> `ControlPrincipal:` Die Fähigkeit zum Verändern des Hauptobjekts.<br /><br /> `Execution:` Berechtigung zur Ausführung von verwaltetem Code.<br /><br /> `SerializationFormatter:` Die Fähigkeit zum Bereitstellen von Serialisierungsdiensten.|  
|**SmtpPermission**|`Access:` Ausgehende Verbindungen an den Anschluss 25 des SMTP-Hosts werden zugelassen.|  
|`SocketPermission`|`Connect:` Ausgehende Verbindungen (alle Ports, alle Protokolle) auf einer Transportadresse werden zugelassen.|  
|`SqlClientPermission`|`Unrestricted:`Der vollständige Zugriff auf die Datenquelle ist zulässig.|  
|`StorePermission`|`Unrestricted:` Der vollständige Zugriff auf X.509-Zertifikatspeicher ist zulässig.|  
|`WebPermission`|`Connect:` Ausgehende Verbindungen an Webressourcen werden zugelassen.|  
  
### <a name="unsafe"></a>UNSAFE  
 UNSAFE ermöglicht Assemblys den uneingeschränkten Zugriff auf Ressourcen innerhalb und außerhalb [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Code, der innerhalb einer `UNSAFE`-Assembly ausgeführt wird, kann außerdem nicht verwalteten Code aufrufen.  
  
 `UNSAFE`-Assemblys erhalten `FullTrust`.  
  
> [!IMPORTANT]  
>  `SAFE` ist die empfohlene Berechtigungseinstellung für Assemblys, die Berechnungs- und Datenverwaltungstasks ausführen, ohne auf Ressourcen außerhalb von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zuzugreifen. `EXTERNAL_ACCESS` Führen Sie die Assemblys werden standardmäßig als die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Dienstkonto und die Berechtigung zum Ausführen von `EXTERNAL_ACCESS` sollten nur vertrauenswürdigen Logins, führen Sie als Dienstkonto erteilt werden. Aus Sicht der Sicherheit sind die `EXTERNAL_ACCESS`-Assembly und die `UNSAFE`-Assembly identisch. `EXTERNAL_ACCESS`-Assemblys bieten gegenüber `UNSAFE`-Assemblys jedoch ein Mehr an Zuverlässigkeit und Stabilität. Angeben von `UNSAFE` kann der Code in der Assembly unzulässige Operationen gegen den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Weitere Informationen zum Erstellen von CLR-Assemblys in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], finden Sie unter [Verwalten von CLR-Integrationsassemblys](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md).  
  
## <a name="accessing-external-resources"></a>Zugreifen auf externe Ressourcen  
 Wenn ein benutzerdefinierter Typ (UDT), eine gespeicherte Prozedur oder eine andere Konstruktassembly mit dem `SAFE`-Berechtigungssatz registriert wird, kann der verwaltete Code, der in dem Konstrukt ausgeführt wird, nicht auf externe Ressourcen zugreifen. Wenn jedoch entweder der `EXTERNAL_ACCESS`-Berechtigungssatz oder der `UNSAFE`-Berechtigungssatz angegeben wird und der verwaltete Code versucht, auf externe Ressourcen zuzugreifen, wendet [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] folgende Regeln an:  
  
|Wenn|Then|  
|--------|----------|  
|Der Ausführungskontext entspricht einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Anmeldung.|Versuche, auf externe Ressourcen zuzugreifen, werden verweigert, und eine Sicherheitsausnahme wird ausgelöst.|  
|Der Ausführungskontext entspricht einer Windows-Anmeldung, und der Ausführungskontext ist der ursprüngliche Aufrufer.|Der Zugriff auf die externe Ressource erfolgt im Sicherheitskontext des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Dienstkontos.|  
|Bei dem Aufrufer handelt es sich nicht um den ursprünglichen Aufrufer.|Der Zugriff wird verweigert, und eine Sicherheitsausnahme wird ausgelöst.|  
|Der Ausführungskontext entspricht einer Windows-Anmeldung und der Ausführungskontext ist der ursprüngliche Aufrufer und der Aufrufer verfügt über dessen Identität angenommen wurde.|Für den Zugriff wird anstelle des Dienstkontos der Sicherheitskontext des Aufrufers verwendet.|  
  
## <a name="permission-set-summary"></a>Zusammenfassung des Berechtigungssatzes  
 Das folgende Diagramm fasst die Einschränkungen und Berechtigungen zusammen, die den Berechtigungssätzen `SAFE`, `EXTERNAL_ACCESS` und `UNSAFE` erteilt werden.  
  
|||||  
|-|-|-|-|  
||`SAFE`|`EXTERNAL_ACCESS`|`UNSAFE`|  
|`Code Access Security Permissions`|Nur ausführen|Ausführen + Zugriff auf externe Ressourcen|Uneingeschränkt (einschließlich P/Invoke)|  
|`Programming model restrictions`|ja|ja|Keine Einschränkungen|  
|`Verifiability requirement`|ja|ja|nein|  
|`Local data access`|ja|ja|ja|  
|`Ability to call native code`|nein|nein|ja|  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheit der CLR-Integration](clr-integration-security.md)   
 [Hostschutzattribute und Programmierung der CLR-Integration](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [CLR-Integration Einschränkungen des Programmiermodells](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)   
 [Gehostete CLR-Umgebung](../clr-integration-architecture-clr-hosted-environment.md)  
  
  
