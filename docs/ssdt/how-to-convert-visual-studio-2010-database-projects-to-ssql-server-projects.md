---
title: 'Gewusst wie: Konvertieren von Visual Studio 2010-Datenbankprojekten in SQL Server-Datenbankprojekte und Neuzuweisen zu einer anderen Plattform | Microsoft-Dokumentation'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql.data.tools.projectconversion.dialog
- sql.data.tools.ImportDAC
ms.assetid: 7e5acf94-5c46-44c7-9ff5-ca7926f5332a
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9e9a42da76b60e891b123196cc6d38c436f92541
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39085636"
---
# <a name="how-to-convert-a-visual-studio-2010-database-projects-to-sql-server-database-projects-and-retarget-to-a-different-platform"></a>Vorgehensweise: Konvertieren von Visual Studio 2010-Datenbankprojekten in SQL Server-Datenbankprojekte und Umleiten auf eine andere Plattform
In SQL Server Data Tools (SSDT) können Sie vorhandene, in Visual Studio 2010 erstellte SQL Server-Datenbank-, CLR- und Datenschichtanwendungs-Projekte in das neue SQL Server-Datenbankprojekt konvertieren. Dadurch können Sie die Vorteile der neuen Datenbankentwicklungsfunktionen von SSDT nutzen, z.B. verbesserte Transact\-SQL-Bearbeitungsfunktionen sowie die Möglichkeit, ein Projekt in Microsoft SQL Server 2012 und SQL Azure mit Codeüberprüfung neu zuzuweisen. Bei diesem Prozess werden Objekte (Tabellen, Sichten, gespeicherte Prozeduren, Eigenschaftendateien oder Skripts), die über einen entsprechenden Typ in SSDT verfügen, einschließlich ihrer Berechtigungen und DAC-Richtliniendateien, konvertiert. Artefakte, die nicht konvertiert werden können, werden in einem Konvertierungsprotokollbericht markiert.  
  
In der folgenden Tabelle sind alle Projektartefakte aufgelistet, die von SSDT konvertiert bzw. nicht konvertiert werden können.  
  
|Projektartefakte, die konvertiert werden können|Projektartefakte, die nicht konvertiert werden können|  
|-------------------------------------------|----------------------------------------------|  
|Projektdateien<br /><br />DBPROJ (Visual Studio 2010-Datenbank- und -Serverprojekte, Anwendungsprojekte auf Datenebene)-Projektdateien<br /><br />CSPROJ- und VBPROJ-CLR-Projektdateien können konvertiert werden, möglicherweise führt dies jedoch zu einem Datenverlust|Datenbankkomponententest-Projekte<br /><br />Teilprojekte, z. B. FILES-Elemente|  
|Eigenschaftendateien<br /><br />SQLDEPLOYMENT-, SQLSETTINGS- und SQLPOLICY-Dateien werden in ihre entsprechenden Projekteigenschaftenseiten konvertiert<br /><br />SQLPERMISSIONS-Dateien werden in Transact\-SQL-Skripts konvertiert|Projekteigenschaften<br /><br />Server.sqlsettings<br /><br />In SQLCMD-Dateien definierte SQLCMD-Variablen|  
|SQL-Dateien werden mit ihrer vorhandenen Ordnerstruktur importiert.|Erweiterungsdateien.|  
|Skripts vor und nach der Bereitstellung|Datenbankverweise müssen nach der Projektkonvertierung neu eingerichtet werden.|  
|Schemavergleichsdateien|Datengenerierungsdateien|  
  
### <a name="to-convert-a-project"></a>So konvertieren Sie ein Projekt  
  
1.  Öffnen Sie ein SQL Server 2005- oder 2008-Datenbankprojekt.  
  
2.  Der Assistent **In SQL Server-Datenbankprojekt konvertieren** wird automatisch geöffnet. Aktivieren Sie die Option **In SQL Server-Datenbankprojekt konvertieren**, und klicken Sie auf **OK**. Die Standardeinstellung zum Sichern von vorhandenen Dateien muss aktiviert sein.  
  
3.  Ein Konvertierungsbericht wird automatisch generiert. In diesem werden alle Dateien aufgelistet, die konvertiert wurden. Um weitere Informationen zum Konvertierungsprozess zu erhalten, klicken Sie auf das **+**-Zeichen neben dem Projektdateinamen.  
  
4.  Sie werden im **Projektmappen-Explorer** feststellen, dass alle Projektdateien, Eigenschaftendateien und Schemaobjekten konvertiert wurden.  
  
### <a name="to-change-a-projects-target-platform"></a>So ändern Sie die Zielplattform eines Projekts  
  
1.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das neu konvertierte Projekt, und wählen Sie die Option **Eigenschaften** aus, um das Dialogfeld **Projekteinstellungen** zu öffnen.  
  
2.  Wählen Sie in der Dropdownliste **Zielplattform** eine der von SSDT unterstützten Plattformen aus.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Gewusst wie: Ändern der Zielplattform und Veröffentlichen eines Datenbankprojekts](../ssdt/how-to-change-target-platform-and-publish-a-database-project.md)  
  
