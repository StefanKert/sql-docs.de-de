---
title: Cacheverbindungs-Manager | Microsoft-Dokumentation
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
- Cache connection manager
ms.assetid: bdc92038-3720-4795-8a5c-79b963f2c952
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fd751a2a52d8d4c4ed391e8a5deb16fe0506e33d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37297020"
---
# <a name="cache-connection-manager"></a>Cacheverbindungs-Manager
  Der Cacheverbindungs-Manager liest Daten aus der Cachetransformation oder einer Cachedatei (.caw) und kann die Daten in einer Cachedatei speichern. Unabhängig davon, ob der Cacheverbindungs-Manager für die Verwendung einer Cachedatei konfiguriert ist, werden die Daten stets im Arbeitsspeicher gespeichert.  
  
 Mit der Transformation für Cachetransformation können Daten aus einer verbundenen Datenquelle im Datenfluss in einen Cacheverbindungs-Manager geschrieben werden. Die Transformation für Suche in einem Paket führt Suchvorgänge in den Daten aus.  
  
> [!NOTE]  
>  Der Cacheverbindungs-Manager unterstützt die BLOB-Datentypen (Binary Large Object) DT_TEXT, DT_NTEXT und DT_IMAGE nicht. Wenn das Verweisdataset einen BLOB-Datentyp enthält, schlägt die Komponente fehl, wenn Sie das Paket ausführen. Sie können den **Cacheverbindungs-Manager-Editor** verwenden, um Spaltendatentypen zu ändern. Weitere Informationen finden Sie unter [Cache Connection Manager Editor](../cache-connection-manager-editor.md).  
  
> [!NOTE]  
>  Die Schutzebene des Pakets gilt nicht für die Cachedatei. Wenn die Cachedatei vertrauliche Informationen enthält, schränken Sie den Zugriff auf den Speicherort oder Ordner, in dem Sie die Datei speichern, mithilfe einer Zugriffssteuerungsliste ein. Sie sollten nur bestimmten Konten den Zugriff ermöglichen. Weitere Informationen finden Sie unter [Zugriff auf Dateien, die von Paketen verwendet werden](../access-to-files-used-by-packages.md).  
  
## <a name="configuration-of-the-cache-connection-manager"></a>Konfiguration des Cacheverbindungs-Managers  
 Es gibt folgende Möglichkeiten, um den Cacheverbindungs-Manager zu konfigurieren:  
  
-   Geben Sie an, ob eine Cachedatei verwendet werden soll.  
  
     Wenn Sie den Cacheverbindungs-Manager für die Verwendung einer Cachedatei konfigurieren, führt der Verbindungs-Manager eine der folgenden Aktionen aus:  
  
    -   Speichern der Daten in einer Datei, wenn eine Cachetransformation so konfiguriert ist, dass Daten aus einer Datenquelle im Datenfluss in den Cacheverbindungs-Manager geschrieben werden.  
  
    -   Lesen von Daten aus der Cachedatei  
  
     Weitere Informationen finden Sie unter [Cache Transform](../data-flow/transformations/cache-transform.md).  
  
-   Ändern Sie die Metadaten der im Cache gespeicherten Spalten.  
  
-   Aktualisieren Sie den Cachedateinamen zur Laufzeit mithilfe eines Ausdrucks zum Festlegen der „ConnectionString“-Eigenschaft. Weitere Informationen finden Sie unter [Verwenden von Eigenschaftsausdrücken in Paketen](../expressions/use-property-expressions-in-packages.md).  
  
 Sie können Eigenschaften mit dem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Weitere Informationen zu den Eigenschaften, die Sie im [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Designer festlegen können, finden Sie unter [Cacheverbindungs-Manager-Editor](../cache-connection-manager-editor.md).  
  
 Weitere Informationen zum programmgesteuerten Konfigurieren eines Verbindungs-Managers finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> und unter [Programmgesteuertes Hinzufügen von Verbindungen](../building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="related-tasks"></a>Related Tasks  
 [Implementieren einer Suchtransformation im Vollcachemodus mit der Transformation für Cacheverbindungs-Manager](lookup-transformation-full-cache-mode-ole-db-connection-manager.md)  
  
  
