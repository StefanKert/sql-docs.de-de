---
title: Bestimmen des Servermodus einer Analysis Services-Instanz | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 9e556fb1-ca37-4f06-8f8f-f187cb0fdb37
caps.latest.revision: 31
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bca31a21dda5f03b29456f842afb2d4d7504c608
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37297430"
---
# <a name="determine-the-server-mode-of-an-analysis-services-instance"></a>Bestimmen des Servermodus einer Analysis Services-Instanz
  Analysis Services können in einem von drei Servermodi installiert sein: mehrdimensional und Data Mining (Standard), PowerPivot für SharePoint und tabellarisch. Der Servermodus einer Analysis Services-Instanz wird während des Setups bestimmt, wenn Sie die Optionen zum Installieren des Servers auswählen.  
  
 Der Servermodus bestimmt den Typ der Lösung, die Sie erstellen und bereitstellen. Wenn Sie die Serversoftware nicht installiert haben und Sie wissen möchten, in welchem Modus der Server installiert ist, können Sie die Informationen aus diesem Abschnitt nutzen, um den Modus zu bestimmen. Weitere Informationen zur Verfügbarkeit von Funktionen in einem bestimmten Modus finden Sie unter [Comparing Tabular and Multidimensional Solutions &#40;SSAS&#41;](../comparing-tabular-and-multidimensional-solutions-ssas.md) (Vergleichen tabellarischer und mehrdimensionaler Lösungen (SSAS)).  
  
 Wenn Sie den Servermodus, den Sie installiert haben, nicht verwenden möchten, müssen Sie die Software deinstallieren und anschließend neu installieren. Wählen Sie dann den Modus aus, den Sie bevorzugen. Alternativ können Sie auf demselben Computer eine zusätzliche Instanz von Analysis Services installieren, damit Sie mehrere Instanzen nutzen, die verschiedene Modi ausführen.  
  
## <a name="server-icons-in-object-explorer"></a>Server-Symbole in Objekt-Explorer  
 Die einfachste Art zur Bestimmung des Servermodus besteht darin, in SQL Server Management Studio eine Verbindung mit dem Server herzustellen und das Symbol neben dem Servernamen in Objekt-Explorer zu erfassen. Die folgende Abbildung zeigt drei Instanzen von Analysis Services an, die in mehrdimensionalem, tabellarischem oder PowerPivot-Modus bereitgestellt werden:  
  
 ![Objekt-Explorer-Symbole für jeden Servermodus](../media/ssas-ssms-servermodes.gif "Objekt-Explorer-Symbole für jeden Servermodus")  
  
## <a name="viewing-deploymentmode-property-in-msmdsrvini-file"></a>Anzeigen der DeploymentMode-Eigenschaft in Datei MSMDSRV.INI  
 Alternativ können Sie die `DeploymentMode`-Eigenschaft in der Datei msmdsrv.ini überprüfen, die in jeder Analysis Services-Instanz enthalten ist. Der Wert dieser Eigenschaft erkennt den Servermodus. Gültige Werte betragen 0 (mehrdimensional), 1 (SharePoint) oder 2 (tabellarisch). Sie müssen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Administrator (Mitglied der Serverrolle) sein, um die Datei „msmdsrv.ini“ öffnen zu können. Diese Datei enthält strukturierte XML. Sie können die Datei mithilfe des Editors oder eines alternativen Text-Editors anzeigen.  
  
> [!CAUTION]  
>  Ändern Sie den Wert der nicht der `DeploymentMode` Eigenschaft. Die manuelle Änderung der Eigenschaft nach dem Installieren des Servers wird nicht unterstützt.  
  
## <a name="about-the-deploymentmode-property"></a>Informationen zur DeploymentMode-Eigenschaft  
 Die `DeploymentMode`-Eigenschaft bestimmt den operativen Kontext einer Analysis Services-Serverinstanz. Diese Eigenschaft wird in Dialogfeldern, Meldungen und Dokumentation als "Servermodus" bezeichnet. Diese Eigenschaft wird vom Setup auf Grundlage des Installationsmodus von Analysis Services initialisiert. Diese Eigenschaft sollte nur intern berücksichtigt und immer der vom Setup angegebene Wert verwendet werden.  
  
 Für diese Eigenschaften gibt es u. a. folgende gültige Werte:  
  
|value|Description|  
|-----------|-----------------|  
|0|Dies ist der Standardwert. Der mehrdimensionale Modus wird angegeben. Er dient zur Verwaltung von mehrdimensionalen Datenbanken, die MOLAP, HOLAP und ROLAP-Speicher sowie Data Mining-Modelle verwenden.|  
|1|Gibt Analysis Services-Instanzen an, die als Teil einer PowerPivot für SharePoint-Bereitstellung installiert waren. Ändern Sie die Bereitstellungsmoduseigenschaft der Analysis Services-Instanz nicht, die Teil einer PowerPivot für SharePoint-Installation ist. Wenn Sie den Modus ändern, werden PowerPivot-Daten nicht mehr auf dem Server ausgeführt.|  
|2|Gibt den Tabellenmodus an, der zum Hosten von Tabellenmodelldatenbanken dient, die Speicher im Arbeitsspeicher oder DirectQuery-Speicher verwenden.|  
  
 Die Modi schließen sich gegenseitig aus. Ein Server, der für den Tabellenmodus konfiguriert ist, kann keine Analysis Services-Datenbanken ausführen, die Cubes und Dimensionen enthalten. Bei Unterstützung durch die zugrunde liegende Computerhardware können Sie mehrere Instanzen von Analysis Services auf demselben Computer installieren und jede Instanz für einen anderen Bereitstellungsmodus konfigurieren. Beachten Sie, dass Analysis Services eine ressourcenintensive Anwendung ist. Die Bereitstellung mehrerer Instanzen auf demselben System wird nur für High-End-Server empfohlen.  
  
## <a name="see-also"></a>Siehe auch  
 [Installieren von Analysis Services im tabellarischen Modus](install-windows/install-analysis-services.md)   
 [Installieren von Analysis Services im mehrdimensionalen Modus und im Data Mining-Modus](../../sql-server/install/install-analysis-services-in-multidimensional-and-data-mining-mode.md)   
 [PowerPivot für SharePoint 2010-Installation](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)   
 [Verbinden von Analysis Services](connect-to-analysis-services.md)   
 [Projektmappen für tabellarische Modelle &#40;SSAS – tabellarisch&#41;](../tabular-model-solutions-ssas-tabular.md)   
 [Mehrdimensionale Modelllösungen &#40;SSAS&#41;](../multidimensional-models/multidimensional-model-solutions-ssas.md)   
 [Miningmodelle &#40;Analysis Services – Datamining&#41;](../data-mining/mining-models-analysis-services-data-mining.md)  
  
  
