---
title: Der OLE DB-Anbieter für Internet Publishing | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- OLE DB provider for Internet publishing [ADO]
- ADO, Internet publishing
- publishing to Internet [ADO]
- Internet publishing [ADO]
- providers [ADO], OLE DB provider for Internet publishing
ms.assetid: 4869aafa-7401-4ce1-93ce-45406a60274f
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ee7efbcd02903e8bba38ecfa177ed7e095e0f5e9
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35273029"
---
# <a name="the-ole-db-provider-for-internet-publishing"></a>Der OLE DB-Anbieter für Internet Publishing
Das ADO [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) und [Stream](../../../ado/reference/ado-api/stream-object-ado.md) Objekte können verwendet werden mit der Microsoft OLE DB-Anbieter für Internet Publishing (Internet Publishing-Anbieter) aufrufen und Bearbeiten von Ressourcen, z. B. Web-Ordner oder Dateien von Microsoft FrontPage verwaltet werden. Mit ADO, geben Sie die Quelle eine **Datensatz**, **Stream**, oder [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) eine URL sein. Sie können dann hochladen, herunterladen, verschieben, kopieren, und löschen Sie Ressourcen oder Ressourceneigenschaften direkt bearbeiten.  
  
 Z. B. Code, der verwendet **Datensätze** und **Streams** mit dem Internet Publishing-Anbieter finden Sie unter der [Internet Publishing Szenario](../../../ado/guide/data/internet-publishing-scenario.md).  
  
 Die Publishing Internetanbieter wird mit Microsoft Windows 2000 installiert. Frühere Versionen von Internet Publishing-Anbieters sind auch mit Microsoft Office 2000 und Microsoft Internet Explorer 5.0 verfügbar.  
  
 Es gibt drei Möglichkeiten, um die Publishing Internetanbieter ADO herstellen:  
  
-   Geben Sie "URL =" in der Verbindungszeichenfolge angegeben. Zum Beispiel:  
  
    ```  
    objConn.Open "URL=http://servername"  
    ```  
  
-   Geben Sie Msdaipp.dso für die *Anbieter* -Schlüsselwort der Verbindungszeichenfolge. Zum Beispiel:  
  
    ```  
    objConn.Open "provider=MSDAIPP.DSO;data source=http://servername"  
    ```  
  
-   Geben Sie Msdaipp.dso für die [Anbieter](../../../ado/reference/ado-api/provider-property-ado.md) Eigenschaft der [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Objekt. Zum Beispiel:  
  
    ```  
    objConn.Provider = "MSDAIPP.DSO"  
    objConn.Open "http://servername"  
    ```  
  
> [!NOTE]
>  Wenn Msdaipp.dso explizit angegeben wird, als der Wert des Anbieters, entweder mit der *Anbieter* -Schlüsselwort der Verbindungszeichenfolge oder die **Anbieter** -Eigenschaft, können keine "URL =" in der Verbindungszeichenfolge angegeben. Wenn Sie dies tun, tritt ein Fehler auf. Stattdessen geben Sie einfach die URL wie oben beschrieben.  
  
 Weitere Informationen über die Publishing Internetanbieter finden Sie unter [Microsoft OLE DB-Anbieter für Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md), oder der Anbieterdokumentation mit der Source-Anwendung mit dem der OLE DB-Anbieter für Internet Publishing installiert wurde: Windows 2000, Office 2000 oder Internet Explorer 5.0.
