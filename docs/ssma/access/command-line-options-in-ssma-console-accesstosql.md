---
title: Befehlszeilenoptionen in SSMA-Konsole (AccessToSQL) | Microsoft Docs
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: c1f3b3f0-0f3e-4e07-b745-2fbdde85c67e
caps.latest.revision: 11
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 9f50d2b9f83758a604aad2fe0f7aed81c0ecd33f
ms.contentlocale: de-de
ms.lasthandoff: 08/02/2017

---
# <a name="command-line-options-in-ssma-console-accesstosql"></a>Befehlszeilenoptionen in SSMA-Konsole (AccessToSQL)
Microsoft stellt Ihnen eine Reihe robuster Befehlszeilenoptionen zum Ausführen und Steuern von SSMA-Aktivitäten. In den folgenden Abschnitten ausführlich identisch.  
  
## <a name="command-line-options-in-ssma-console"></a>Befehlszeilenoptionen in SSMA-Konsole  
Hierin beschriebenen sind die Konsole die Befehlsoptionen an.  
  
In diesem Abschnitt wird der Begriff "Option" auch als "Switch" bezeichnet.  
  
Optionen Groß-/Kleinschreibung nicht und kann entweder mit starten "**-**'oder'**/**" Zeichen.  
  
Wenn Optionen angegeben sind, wird es erforderlich, um die entsprechende Optionsparameter anzugeben.  
  
Optionsparameter müssen vom Option Zeichen durch ein Leerzeichen voneinander getrennt werden.  
  
**Beispiele für die Abfrageausdruckssyntax:**  
  
`C:\> SSMAforAccessConsole.EXE -s scriptfile`  
  
`C:\> SSMAforAccessConsole.EXE -s “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\AssessmentReportGenerationSample.xml” –v “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\VariableValueFileSample.xml” –c “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ServersConnectionFileSample.xml”`  
  
Ordner oder eine Datei Namen, die Leerzeichen enthalten, sollte in doppelte Anführungszeichen angegeben werden.  
  
Die Ausgabe der Befehlszeile Einträge und Fehlermeldungen werden in "stdout" oder in einer angegebenen Datei gespeichert.  
  
### <a name="script-file-option-sscript"></a>Skript-Dateioption: – s/Skriptberechtigungen  
Ein erforderlicher Parameter, der Pfad/Skriptdateiname gibt das Skript an der Befehlssequenzen SSMA ausgeführt werden soll.  
  
**Beispiele für die Abfrageausdruckssyntax:**  
  
`C:\>SSMAforAccessConsole.EXE –s “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”`  
  
### <a name="variable-value-file-option-vvariable"></a>Variable-Wert-Dateioption: – V/die variable  
Diese Datei besteht aus Variablen, die in der Skriptdatei verwendet. Dies ist ein Optionaler Schalter. Wenn Variablen werden nicht im Oval-Variablendatei deklariert und in der Skriptdatei verwendet, wird die Anwendung generiert einen Fehler und beendet die Ausführung der Konsole.  
  
**Beispiele für die Abfrageausdruckssyntax:**  
  
-   Variablen, die in mehreren Variablenwert-Dateien, z. B. eins hat den Standardwert und eine andere mit einer bestimmten Instanzenwert bei Bedarf definiert werden. Der letzte in die Befehlszeilenargumente angegeben Variablendatei nimmt die Voreinstellung für den Fall, dass eine der Variablen Doppelung:  
  
    `C:\>SSMAforAccessConsole.EXE -s`  
  
    `“C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml” –v c:\migration`  
  
    `projects\global_variablevaluefile.xml –v “c:\migrationprojects\instance_variablevaluefile.xml”`  
  
### <a name="server-connection-file-option-cserverconnection"></a>Serveroption für Verbindung: c: / serverconnection  
Diese Datei enthält die Serververbindungsinformationen für jeden Server. Jede Serverdefinition wird durch eine eindeutige Server-ID identifiziert. Die Server-IDs sind verwiesen wird, in der Skriptdatei für die Verbindung Befehle.  
  
Serverdefinition kann ein Teil des Server-Verbindungsdatei und/oder Skriptdatei sein. Server-Id in der Skriptdatei hat Vorrang vor den Server-Verbindungsdatei, für den Fall, dass eine Duplizierung der Server-Id vorhanden ist.  
  
**Beispiele für die Abfrageausdruckssyntax:**  
  
-   Server-IDs werden in der Skriptdatei verwendet und werden in einem separaten Server Verbindungsdatei definiert, Server-Verbindungsdatei verwendet Variablen, die in der Variablenwert-Datei definiert sind:  
  
    `C:\>SSMAforAccessConsole.EXE –s “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –v`  
  
    `c:\SsmaProjects\myvaluefile1.xml –c`  
  
    `c:\SsmaProjects\myserverconnectionsfile1.xml`  
  
-   Serverdefinition wird in der Skriptdatei eingebettet:  
  
    `C:\>SSMAforAccessConsole.EXE –s “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”`  
  
### <a name="xml-output-option--xxmloutput-xmloutputfile"></a>XML-Output-Option: - X / Xmloutput [Xmloutputfile]  
Mit diesem Befehl wird verwendet, für die Ausgabenachrichten Befehl in einem XML-Format an Konsole oder in eine XML-Datei ausgeben.  
  
Es stehen zwei Optionen für Xmloutput, begrenzt..,:  
  
-   Wenn Filepath, nach dem Wechsel Xmloutput bereitgestellt wird wird die Ausgabe in die Datei umgeleitet.  
  
    **Syntaxbeispiel:**  
  
    `C:\>SSMAforAccessConsole.EXE –s`  
  
    `“C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –x d:\xmloutput\project1output.xml`  
  
-   Wenn keine Filepath, nach dem Wechsel Xmloutput bereitgestellt wird wird die Xmlout auf der Konsole angezeigt.  
  
    **Syntaxbeispiel:**  
  
    `C:\>SSMAforAccessConsole.EXE –s “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –xmloutput`  
  
### <a name="log-file-option-llog"></a>Option für die Protokolldatei: – l/log  
Die SSMA-Vorgänge in der Verwaltungskonsole abrufen in einer Protokolldatei aufgezeichnet. Dies ist ein Optionaler Schalter. Wenn eine Protokolldatei und der zugehörige Pfad in der Befehlszeile angegeben werden, ruft das Protokoll in der angegebenen Position generiert. Andernfalls ruft es an seinem Standardspeicherort generiert.  
  
**Syntaxbeispiel:**  
  
`C:\>SSMAforAccessConsole.EXE`  
  
`“C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –l c:\SsmaProjects\migration1.log`  
  
### <a name="project-environment-folder-option-eprojectenvironment"></a>Ordner Umgebungsoption Projekt: – e/projectenvironment  
Dies kennzeichnet den Projektordner für die Einstellungen von Umgebung für das aktuelle SSMA-Projekt. Diese Option ist optional.  
  
**Syntaxbeispiel:**  
  
`C:\>SSMAforAccessConsole.EXE –s`  
  
`“C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –e c:\SsmaProjects\CommonEnvironment`  
  
||  
|-|  
||  
  
### <a name="secure-password-option-psecurepassword"></a>Secure Password-Option: – p/securepassword  
Diese Option gibt das verschlüsselte Kennwort für den Server-Verbindungen an. Sie unterscheidet sich von allen anderen Optionen: die Option weder führt alle Skripts noch keine Migration-bezogenen Aktivitäten ist hilfreich, sondern hilft verwalten kennwortverschlüsselung für die Server-Verbindungen, die in das Migrationsprojekt verwendet.  
  
Sie können nicht als Parameter über die Befehlszeile andere Option oder ein Kennwort eingeben. Andernfalls führt dies zu einem Fehler. Weitere Informationen finden Sie unter der [Verwalten von Kennwörtern](http://msdn.microsoft.com/en-us/b099d0f9-dd37-4c87-8b6f-ed0177881ea4) Abschnitt.  
  
Die folgenden untergeordneten Optionen werden unterstützt, für `–p/securepassword`:  
  
-   Kennwort zum Hinzufügen geschützter Speicher für eine angegebene ID oder für alle Server-IDs, die in der Server-Verbindung-Datei definiert. -Die Option zum Überschreiben, unten Updates des Kennworts, wenn sie bereits vorhanden ist:  
  
    `-p|-securepassword -a|add    {"<server_id>[, .n]"|all}``-c|-serverconnection <server-connection-file> [-v|variable <variable-value-file>]``[-o|overwrite]`  
  
    `-p|-securepassword -a|add    {"<server_id>[, .n]"|all}``-s|-script <server-connection-file> [-v|variable <variable-value-file>] [-o|overwrite]`  
  
-   So entfernen Sie das verschlüsselte Kennwort aus dem geschützten Speicher, der die angegebene ID für den Server oder für alle Server-IDs:  
  
    `–p/securepassword –r/remove {<server_id> [, …n] | all}`  
  
-   Um eine Liste der Server-IDs anzuzeigen, für die das Kennwort verschlüsselt wird:  
  
    `–p/securepassword –l/list`  
  
-   So exportieren Sie die Kennwörter im geschützten Speicher zu einer verschlüsselten Datei gespeichert. Diese Datei ist mit benutzerdefinierten-Passphrase verschlüsselt.  
  
    `–p/securepassword –e/export {<server-id> [, …n] | all} <encrypted-password -file>`  
  
-   Verschlüsselt-Datei, die zuvor exportierte wird in den lokalen geschützten Speicher, die mit der Passphrase benutzerdefiniertes importiert. Nachdem die Datei entschlüsselt wird, wird es in einer neuen Datei gespeichert, die wiederum auf dem lokalen Computer verschlüsselt ist.  
  
    `–p/securepassword –i/import {<server-id> [, …n] | all} <encrypted-password -file>`  
  
    Mehrere Server-IDs können mithilfe von Kommas – als Trennzeichen angegeben werden.  
  
### <a name="help-option-help"></a>Hilfeoption: –? / Help  
Zeigt eine syntaxzusammenfassung der Optionen SSMA-Konsole:  
  
`C:\>SSMAforAccessConsole.EXE -?`  
  
Einer tabellarischen Ansicht von der Konsole SSMA-Befehlszeilenoptionen finden Sie unter [Anhang - 1 &#40; AccessToSQL &#41; ](../../ssma/access/appendix-1-accesstosql.md).  
  
### <a name="securepassword-help-option-securepassword--help"></a>SecurePassword Help Option: – Securepassword-? / Help  
Zeigt eine syntaxzusammenfassung der Optionen SSMA-Konsole:  
  
`C:\>SSMAforAccessConsole.EXE -securepassword -?`  
  
Einer tabellarischen Ansicht von der Konsole SSMA-Befehlszeilenoptionen finden Sie unter [Anhang - 1 &#40; AccessToSQL &#41;](../../ssma/access/appendix-1-accesstosql.md)  
  
### <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt hängt davon ab, auf die Anforderungen Ihres Projekts:  
  
1.  Zur Angabe eines Kennworts oder einer Exportieren / Importieren von Kennwörtern, finden Sie unter [Verwalten von Kennwörtern &#40; AccessToSQL &#41; ](../../ssma/access/managing-passwords-accesstosql.md).  
  
2.  Generieren von Berichten, finden Sie unter [Generieren von Berichten &#40; AccessToSQL &#41; ](../../ssma/access/generating-reports-accesstosql.md).  
  
3.  Behandlung von Problemen in der Konsole, finden Sie unter [Problembehandlung &#40; AccessToSQL &#41; ](../../ssma/access/troubleshooting-accesstosql.md).  
  
