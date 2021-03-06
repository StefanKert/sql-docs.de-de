---
title: Parameterwert festlegen (Dialogfeld) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ce9c2201-4e9a-4495-948f-b68deeaa7955
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3559b30e2a8e6feff03dcd9452bd335ea8c4a268
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2018
ms.locfileid: "35329504"
---
# <a name="set-parameter-value-dialog-box"></a>Parameterwert festlegen (Dialogfeld)
  Verwenden Sie das Dialogfeld **Parameterwert festlegen** , um Werte für Parameter und Eigenschaften des Verbindungs-Managers für Projekte und Pakete festzulegen.  
  
 **Was möchten Sie tun?**  
  
-   [Öffnen des Dialogfelds 'Parameterwert festlegen'](#open_dialog)  
  
-   [Konfigurieren der Optionen](#option)  
  
##  <a name="open_dialog"></a> Öffnen des Dialogfelds 'Parameterwert festlegen'  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung zum [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Server her.  
  
     Sie stellen eine Verbindung mit der [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] -Instanz her, die die SSISDB-Datenbank hostet.  
  
2.  Erweitern Sie im Objekt-Explorer die Struktur, um den Knoten **Integration Services-Kataloge** anzuzeigen.  
  
3.  Erweitern Sie den **SSISDB** -Knoten.  
  
4.  Klicken Sie mit der rechten Maustaste auf ein Paket oder ein Projekt, wählen Sie **Konfigurieren**, und klicken Sie dann auf der Registerkarte **Parameter** oder auf der Registerkarte **Verbindungs-Manager** auf die Schaltfläche mit den Auslassungspunkten.  
  
##  <a name="option"></a> Konfigurieren der Optionen  
 **Parameter**  
 Listet den Namen des Parameters auf.  
  
 **Typ**  
 Listet den Datentyp des Parameterwerts auf.  
  
 **Beschreibung**  
 Zeigt eine optionale Beschreibung für den Parameter an.  
  
 **Wert bearbeiten**  
 Verwenden Sie diese Option, um den Parameterwert zu bearbeiten.  
  
 **Standardwert aus Paket verwenden**  
 Aktivieren Sie diese Option, um den im Paket gespeicherten Standardwert für diesen Parameter zu verwenden.  
  
 **Umgebungsvariable verwenden**  
 Aktivieren Sie diese Option, um einen Variablenwert zu verwenden, der in der Umgebung gespeichert wurde, auf die vom Projekt oder Paket verwiesen wird. Um einen Umgebungsverweis zu einem Projekt oder Paket hinzuzufügen, verwenden Sie das Dialogfeld **Konfigurieren** . Weitere Informationen finden Sie unter [Configure Dialog Box](../../integration-services/catalog/configure-dialog-box.md).  
  
  
