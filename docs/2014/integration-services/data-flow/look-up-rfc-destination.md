---
title: RFC-Ziel suchen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: db9404d8-4c42-45e5-a100-c7a84b056109
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: eea7cee81892b7ffb5ce35d747c54b413ceb1d62
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37252622"
---
# <a name="look-up-rfc-destination"></a>RFC-Ziel suchen
  Verwenden Sie das Dialogfeld **RFC-Ziel suchen** , um ein RFC-Ziel zu suchen, das im SAP NetWeaver BW-System definiert ist. Wenn die Liste der verfügbaren RFC-Ziele angezeigt wird, wählen Sie das gewünschte Ziel aus. Daraufhin werden die zugehörigen Optionen von der Komponente mit den erforderlichen Werten aufgefüllt.  
  
 Sowohl die SAP BW-Quelle als auch das SAP BW-Ziel verwenden das Dialogfeld **RFC-Ziel suchen** . Weitere Informationen zu den Komponenten von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW finden Sie unter [SAP BW-Quelle](sap-bw-source.md) und [SAP BW-Ziel](sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  Die Dokumentation für Microsoft Connector 1.1 for SAP BW setzt Kenntnisse der SAP NetWeaver BW-Umgebung voraus. Weitere Informationen zu SAP NetWeaver BW oder Informationen zur Konfiguration von SAP NetWeaver BW-Objekten und -Prozessen finden Sie in der SAP-Dokumentation.  
  
 **So öffnen Sie das Dialogfeld "RFC-Ziel suchen"**  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paket, das die SAP BW-Quelle oder das SAP BW-Ziel enthält.  
  
2.  Doppelklicken Sie auf der Registerkarte **Datenfluss** auf die SAP BW-Quelle oder das SAP BW-Ziel.  
  
3.  Klicken Sie im **Quellen-Editor für SAP BW** oder im **Ziel-Editor für SAP BW**auf **Verbindungs-Manager** , um die Seite **Verbindungs-Manager** des Editors zu öffnen.  
  
4.  Klicken Sie auf der Seite **Verbindungs-Manager** im Gruppenfeld **RFC-Ziel** auf **Suchen** , um das Dialogfeld **RFC-Ziel suchen** anzuzeigen.  
  
     Das Gruppenfeld **RFC-Ziel**wird im **Quellen-Editor für SAP BW** nur angezeigt, wenn der Wert für **Ausführungsmodus** **P - Prozesskette auslösen** oder **W - Benachrichtigung abwarten**lautet.  
  
## <a name="options"></a>Tastatur  
 **Ziel**  
 Zeigt den Namen des RFC-Ziels an, das im SAP NetWeaver BW-System definiert ist.  
  
 **Gatewayhost**  
 Zeigt den Servernamen oder die IP-Adresse des Gatewayhosts an. Normalerweise ist der Name oder die IP-Adresse identisch mit dem SAP-Anwendungsserver.  
  
 **Gatewaydienst**  
 Zeigt den Namen des Gatewaydiensts im Format `sapgwNN`, wobei `NN` der Systemnummer entspricht.  
  
 **Programm-ID**  
 Zeigt die Programm-ID an, die dem RFC-Ziel zugeordnet ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellen-Editor für SAP BW &#40;Seite Verbindungs-Manager&#41;](sap-bw-source-editor-connection-manager-page.md)   
 [Ziel-Editor für SAP BW &#40;Seite Verbindungs-Manager&#41;](sap-bw-destination-editor-connection-manager-page.md)   
 [F1-Hilfe zu Microsoft Connector 1.1 für SAP BW](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
