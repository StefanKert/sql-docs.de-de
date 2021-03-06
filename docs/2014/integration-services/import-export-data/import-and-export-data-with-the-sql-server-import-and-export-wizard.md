---
title: SQL Server-Import / Export-Assistent | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- exporting data
- mapping files [Integration Services]
- SQL Server Import and Export Wizard
- SSIS packages, creating
- packages [Integration Services], copying
- Integration Services packages, creating
- packages [Integration Services], creating
- SQL Server Integration Services packages, creating
- Import and Export Wizard
- copying data [Integration Services]
- importing data, SSIS packages
- sources [Integration Services], copying data
ms.assetid: c0e4d867-b2a9-4b2a-844b-2fe45be88f81
caps.latest.revision: 87
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 89d81ed6f880404771eb242cd0edf309be94f765
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37219690"
---
# <a name="sql-server-import-and-export-wizard"></a>SQL Server-Import/Export-Assistent
  Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Import / Export-Assistent bietet die einfachste Methode zum Erstellen einer [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Paket, das Daten aus einer Quelle in ein Ziel kopiert.  
  
> [!NOTE]  
>  Auf einem 64-Bit-Computer installiert [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] die 64-Bit-Version des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Import/Export-Assistenten (DTSWizard.exe). Jedoch verfügen einige Datenquellen, wie Access oder Excel, nur über einen 32-Bit-Anbieter. Damit Sie diese Datenquellen verwenden können, müssen Sie möglicherweise die 32-Bit-Version des Assistenten installieren und ausführen. Wählen Sie zum Installieren der 32-Bit-Version des Assistenten entweder Clienttools oder [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] während des Setups.  
  
 Den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Import/Export-Assistenten können Sie über das Menü Start in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] sowie über die Eingabeaufforderung aufrufen. Weitere Informationen finden Sie unter [führen Sie die SQL Server-Import / Export-Assistenten](start-the-sql-server-import-and-export-wizard.md).  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Import / Export-Assistenten können Kopieren von Daten in und aus einer beliebigen Datenquelle für die ein verwaltetes [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Datenanbieter oder einen systemeigenen OLE DB-Anbieter zur Verfügung steht. Die Liste verfügbarer Anbieter enthält die folgenden Datenquellen:  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Flatfiles  
  
-   Microsoft Office Access  
  
-   Microsoft Office Excel  
  
 Die Funktionsweise einiger Assistentenfunktionen ist je nach Umgebung, in der der Assistent gestartet wird, unterschiedlich.  
  
-   Wenn Sie starten die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Import / Export-Assistenten in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], Sie das Paket sofort ausführen, durch Auswählen der **werden sofort ausgeführt,** Kontrollkästchen. Standardmäßig ist dieses Kontrollkästchen aktiviert, und das Paket wird sofort ausgeführt.  
  
     Sie können außerdem entscheiden, ob das Paket in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder im Dateisystem gespeichert werden soll. Wenn Sie entscheiden, das Paket zu speichern, müssen Sie darüber hinaus eine Paketschutzebene angeben. Weitere Informationen zu paketschutzebenen finden Sie unter [Zugriffssteuerung für vertrauliche Daten in Paketen](../security/access-control-for-sensitive-data-in-packages.md).  
  
     Nach der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Import / Export-Assistent das Paket erstellt und die Daten kopiert hat, können Sie verwenden die [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer öffnen und das gespeicherte Paket durch das Hinzufügen von Tasks, Transformationen und ereignisgesteuerter Logik ändern.  
  
    > [!NOTE]  
    >  In [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], die Möglichkeit, das vom Assistenten erstellte Paket speichern ist nicht verfügbar.  
  
-   Wenn Sie starten die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Import / Export-Assistenten in eine [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Projekt [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], das Paket kann nicht als Schritt zum Abschließen des Assistenten ausgeführt werden. Stattdessen wird das Paket dem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Projekt hinzugefügt, in dem Sie den Assistenten gestartet haben. Sie können dann das Paket ausführen oder durch Hinzufügen von Tasks, Transformationen und ereignisgesteuerter Logik mithilfe des [!INCLUDE[ssIS](../../includes/ssis-md.md)]-Designers erweitern.  
  
 Weitere Informationen finden Sie unter [führen Sie die SQL Server-Import / Export-Assistenten](start-the-sql-server-import-and-export-wizard.md).  
  
## <a name="permissions-required-by-the-import-and-export-wizard"></a>Erforderliche Berechtigungen für den Import/Export-Assistenten  
 Zum Abschließen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Import / Export-Assistenten erfolgreich, Sie benötigen mindestens die folgenden Berechtigungen:  
  
-   Sie müssen berechtigt sein, Verbindungen mit den Quell- und Zieldatenbanken bzw. Dateifreigaben herzustellen. In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], dies erfordert, dass Server und Datenbank-Anmelderechte.  
  
-   Sie müssen berechtigt sein, Daten aus der Quelldatenbank bzw. -datei zu lesen. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], dies erfordert die SELECT-Berechtigungen für die Quelltabellen und-Sichten.  
  
-   Sie müssen berechtigt sein, Daten in die Zieldatenbank oder -datei zu schreiben. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], dies erfordert, dass INSERT-Berechtigungen für die Zieltabellen.  
  
-   Wenn Sie eine neue Zieldatenbank, -tabelle oder -datei erstellen möchten, müssen Sie über die erforderlichen Berechtigungen zum Erstellen der neuen Datenbank, Tabelle oder Datei verfügen. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sind dafür CREATE DATABASE- bzw. CREATE TABLE-Berechtigungen erforderlich.  
  
-   Wenn das Paket erstellt, die vom Assistenten, über ausreichende Berechtigungen zum Schreiben in die Msdb-Datenbank oder im Dateisystem gespeichert werden sollen. In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], dies erfordert, dass INSERT-Berechtigungen für die Msdb-Datenbank.  
  
## <a name="mapping-data-types-in-the-import-and-export-wizard"></a>Zuordnen von Datentypen im Import/Export-Assistenten  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Import / Export-Assistent stellt minimale Transformationsfunktionen bereit. Mit Ausnahme der Festlegung des Namens, des Datentyps und der Datentypeigenschaften von Spalten in neuen Zieltabellen und -dateien unterstützt der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Import/Export-Assistent keine Transformationen auf Spaltenebene.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Import / Export-Assistenten mithilfe der Zuordnung Dateien, die [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] bereitstellt, um Datentypen aus einer Datenbankversion oder einem System in einen anderen zugeordnet. Zum Beispiel kann eine Zuordnung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu Oracle erfolgen. Standardmäßig werden die Zuordnungsdateien im XML-Format unter C:\Programme\Microsoft SQL Server\100\DTS\MappingFiles installiert. Wenn Ihr Unternehmen verschiedene Zuordnungen zwischen Datentypen erfordert, können Sie die Zuordnungen aktualisieren, um die vom Assistenten durchgeführten Zuordnungen zu beeinflussen. Wenn Sie möchten z. B. die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Nchar** -Datentyp zum Zuordnen von DB2 **GRAFISCHE** Datentyp statt dem DB2 **VARGRAPHIC** -Datentyp beim Übertragen von Daten aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DB2, Sie ändern die **Nchar** Zuordnung in der Zuordnungsdatei SqlClientToIBMDB2.xml verwenden **GRAFISCHE** anstelle von **VARGRAPHIC.**  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] enthält Zuordnungen zwischen vielen häufig verwendeten Quellen- und Zielkombinationen. Darüber hinaus können Sie dem Ordner mit den Zuordnungsdateien neue Zuordnungsdateien hinzufügen, um zusätzliche Quellen und Ziele zu unterstützen. Die neuen Zuordnungsdateien müssen dem veröffentlichten XSD-Schema entsprechen und einer eindeutigen Kombination aus Quelle und Ziel zugeordnet sein.  
  
> [!NOTE]  
>  Wenn Sie eine vorhandene Zuordnungsdatei bearbeiten oder eine neue Zuordnungsdatei zu dem Ordner hinzufügen, müssen Sie Sie schließen und erneut die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Import / Export-Assistenten oder [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] für die neuen oder geänderten Dateien erkannt werden.  
  
## <a name="external-resources"></a>Externe Ressourcen  
  
-   Video [Exportieren von SQL Server-Daten nach Excel (SQL Server-Video)](http://go.microsoft.com/fwlink/?LinkID=200975), auf technet.microsoft.com  
  
-   CodePlex-Beispiel [Export aus ODBC in ein Flat File Using a Wizard Tutorial: Lesson Packages](http://go.microsoft.com/fwlink/?LinkId=217657), auf msftisprodsamples.codeplex.com  
  
  
