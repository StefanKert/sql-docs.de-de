---
title: Benutzerdefinierte Berichte in Management Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.summary.new.custom.report.f1
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], custom reports
ms.assetid: 1ba3f758-f39b-4f5f-91ca-516cedc78979
caps.latest.revision: 12
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9b953b0d6efcd99204fc812dc1d612dfd2d7dc3b
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43814696"
---
# <a name="custom-reports-in-management-studio"></a>Benutzerdefinierte Berichte in Management Studio
  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] wird von vielen Objekt-Explorer-Knoten ein Satz von Standardberichten angezeigt, die von [!INCLUDE[msCoName](../../includes/msconame-md.md)] erstellt werden. In diesen Berichten werden häufig angeforderte Serverinformationen zusammengefasst. Seit [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 können in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] von [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]erstellte benutzerdefinierte Berichte von Administratoren ausgeführt werden.  
  
## <a name="implementation"></a>Implementierung  
 Benutzerdefinierte Berichte werden als RDL-Dateien gespeichert und mithilfe der Berichtsdefinitionssprache (Report Definition Language, RDL) erstellt. In der Berichtsdefinitionssprache sind Informationen zum Datenabruf und Datenlayout für einen Bericht in einem XML-Format enthalten. Die Berichtsdefinitionssprache ist ein offenes Schema. Entwickler können die Berichtsdefinitionssprache mit zusätzlichen Attributen und Elementen erweitern. Jede gültige [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung in einem Bericht kann von Berichten ausgeführt wird.  
  
 Wurde für den Objekt-Explorer eine Verbindung mit einem Server hergestellt, können benutzerdefinierte Berichte im Kontext der aktuellen Objekt-Explorer-Auswahl ausgeführt werden, wenn von den Berichten auf Berichtsparameter dieses Knotens verwiesen wird. Dadurch wird ermöglicht, dass im Bericht der aktuelle Kontext (beispielsweise die aktuelle Datenbank) oder ein konsistenter Kontext (beispielsweise die Angabe einer designierten Datenbank als Teil der im benutzerdefinierten Bericht enthaltenen [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung) verwendet wird.  
  
## <a name="running-a-custom-report"></a>Ausführen eines benutzerdefinierten Berichts  
 Es gibt folgenden Möglichkeiten zum Ausführen eines benutzerdefinierten Berichts in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] :  
  
-   Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf einen Knoten, zeigen Sie auf **Berichte** , und klicken Sie mit der linken Maustaste auf **Benutzerdefinierte Berichte**. Suchen Sie im Dialogfeld **Datei öffnen** einen Ordner mit RDL-Dateien, und öffnen Sie dann die entsprechende Berichtsdatei.  
  
-   Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf einen Knoten, zeigen Sie auf **Berichte**, zeigen Sie auf **Benutzerdefinierte Berichte**, und wählen Sie dann aus der Liste der zuletzt geöffneten Dateien einen benutzerdefinierten Bericht aus.  
  
## <a name="limitations"></a>Einschränkungen  
 Berücksichtigen Sie bei der Verwendung benutzerdefinierter Berichte die folgenden Einschränkungen:  
  
-   Um die unbeabsichtigte Ausführung von bösartigem Code zu verhindern, kann [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] auch dann nicht für das automatische Ausführen eines Berichts konfiguriert werden, wenn das Dateisystem so konfiguriert ist, dass RDL-Dateien [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]zugeordnet werden. In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] können Berichte weder programmgesteuert noch an der Eingabeaufforderung über [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]ausgeführt werden.  
  
-   Benutzerdefinierte Berichte können in einem Kontext ausgeführt werden, in dem die erwarteten Werte nicht erstellt werden. Sie können beispielsweise einen Bericht über die Replikation im Kontext einer Datenbank ausführen, die nicht in der Replikation involviert ist, oder Sie können einen Bericht als ein Benutzer ausführen, der nicht über die Berechtigung für den Zugriff auf Informationen verfügt, die zum Generieren eines präzisen Berichts erforderlich sind. Der Ersteller des benutzerdefinierten Berichts ist für die Gültigkeit der Berichtsstruktur und seines Kontexts verantwortlich.  
  
-   Sie können der Liste der Standardberichte keinen benutzerdefinierten Bericht hinzufügen.  
  
-   Der vom Bericht verarbeitete Code kann möglicherweise Auswirkungen auf die Serverleistung haben.  
  
-   Unterberichte werden von benutzerdefinierten Berichten nicht unterstützt.  
  
-   Der Befehlstext für die einzelnen Abfragen im Bericht darf nicht über einen Ausdruck definiert sein.  
  
-   Mit jedem in einem Befehl (Abfrage) verwendeten Abfrageparameter kann nur auf einen einzelnen Berichtsparameter verwiesen werden. Ausdrucksoperatoren können nicht verwendet werden.  
  
-   Für Berichtsbefehle (Abfragen) werden nur Befehle vom Typ Text und gespeicherte Prozedur unterstützt.  
  
-   Das Berichtsframework bietet keine Parameter zum Erstellen von Escapezeichen für die Abfragen. Abfrageautoren müssen sicherstellen, dass ihre Abfragen frei von SQL Injection-Angriffen sind.  
  
## <a name="managing-custom-reports"></a>Verwalten von benutzerdefinierten Berichten  
 Für Benutzer, die über eine Vielzahl benutzerdefinierter Berichte verfügen, empfiehlt es sich, diese mithilfe der Dateisystemordner zu organisieren, die über entsprechende NTFS-Dateisystemberechtigungen verfügen.  
  
## <a name="permissions"></a>Berechtigungen  
 Benutzerdefinierte Berichte werden mithilfe der Berechtigungen des aktuellen Benutzers ausgeführt. Berechtigungen für den Dateisystemordner mit den Berichtsdateien müssen so festgelegt werden, dass der Zugriff eingeschränkt wird, um das Ändern der vom Bericht ausgeführten Abfragen durch einen böswilligen Benutzer zu verhindern.  
  
 Sowohl für den Benutzer als auch für das vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienst verwendete Konto ist Lesezugriff auf den Dateisystemordner mit den Berichtsdateien erforderlich.  
  
 Jeder gültige [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] -Befehl kann in einen Bericht eingebettet werden, der Befehl wird jedoch nicht ausgeführt.  
  
> [!CAUTION]  
>  Jede gültige [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung kann in einem Bericht eingebettet und von einem Bericht aus ausgeführt werden. Durch das Ausführen eines Berichts unter einem Benutzerkonto mit hohen Privilegien wird die problemlose Ausführung dieser eingebetteten Anweisungen ermöglicht.  
  
## <a name="report-samples"></a>Beispielberichte  
 [Beispielberichte](http://go.microsoft.com/fwlink/?LinkId=81792), einschließlich der Standardberichte, die vom erstellten [!INCLUDE[msCoName](../../includes/msconame-md.md)], sind zum Download zur Verfügung. Diese Beispiele können mithilfe von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]geändert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen eines benutzerdefinierten Berichts zu Management Studio](add-a-custom-report-to-management-studio.md)   
 [Unterdrückung Ausführen von benutzerdefinierten Berichten, Warnungen](unsuppress-run-custom-report-warnings.md)   
 [Verwenden benutzerdefinierter Berichte mit Eigenschaften von Objekt-Explorer-Knoten](use-custom-reports-with-object-explorer-node-properties.md)  
  
  
