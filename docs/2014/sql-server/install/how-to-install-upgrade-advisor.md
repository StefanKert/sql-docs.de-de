---
title: 'Vorgehensweise: Installieren des Upgrade Advisors | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- Setup [Upgrade Advisor]
- SQL Server Upgrade Advisor, installing
- Upgrade Advisor [SQL Server], installing
ms.assetid: 481b0704-ce79-4543-b141-67306128aa2b
caps.latest.revision: 24
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 241bae15e3d4edf548e12cfcb06ca09cab8c8a89
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37216440"
---
# <a name="how-to-install-upgrade-advisor"></a>Vorgehensweise: Installieren des Upgrade Advisors
  Upgrade Advisor unterstützt die Remoteanalyse aller unterstützten Komponenten mit Ausnahme von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Wenn Sie keine Instanzen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] scannen, können Sie den Upgrade Advisor auf einem beliebigen Computer installieren, der eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen kann. Der Computer muss zudem die Voraussetzungen für den Upgrade Advisor erfüllen. Wenn Sie Instanzen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] scannen, müssen Sie den Upgrade Advisor auf dem Berichtsserver installieren.  
  
 Weitere Informationen finden Sie unter [Installation von Upgrade Advisor](../../../2014/sql-server/install/installing-upgrade-advisor.md).  
  
### <a name="to-install-upgrade-advisor"></a>So installieren Sie den Upgrade Advisor  
  
1.  Starten Sie die Installation mithilfe einer der folgenden Methoden:  
  
    -   Bei der Installation von der [!INCLUDE[msCoName](../../includes/msconame-md.md)] -Website, klicken Sie auf die **herunterladen** verknüpfen, und klicken Sie dann auf die **ausführen** Schaltfläche, um die Installation zu starten.  
  
    -   Wenn Sie vom Produktdatenträger installieren, öffnen Sie die **Redist** Ordner die **Upgrade Advisor** Ordner, und doppelklicken Sie dann auf **SQLUA.msi**.  
  
    > [!NOTE]  
    >  Für Upgrade Advisor ist [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 4 erforderlich. Wenn die Anwendung nicht installiert ist oder Sie eine Vorabversion verwenden, wird eine Fehlermeldung angezeigt. Deinstallieren Sie frühere Versionen von [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], und installieren Sie dann die aktuelle Version von .NET Framework 4.  
    >   
    >  Die [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom ist eine Voraussetzung für die Installation von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor, und Setup von Upgrade Advisor nicht installiert ist. Beim Setup müssen Sie zum Herunterladen und Installieren der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom aus dem [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Feature Pack.  
  
2.  Auf der **Willkommen bei der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Setup für Upgrade Advisor** auf **Weiter**.  
  
3.  Auf der **-Software-Lizenzbedingungen** Seite lesen Sie die Lizenzbedingungen. Wenn Sie zustimmen, wählen Sie **ich nehme den Lizenzvertrag** , und klicken Sie dann auf **Weiter**.  
  
4.  Auf der **Registrierungsinformationen** geben Ihre Namen und das Unternehmen.  
  
5.  Auf der **Funktionsauswahl** überprüfen Sie die **Installationspfad** Wert. Verwenden Sie bei Bedarf die **Durchsuchen** Schaltfläche, um den Speicherort zu ändern. Klicken Sie auf **Weiter**.  
  
6.  Auf der **bereit zum Installieren des Programms** auf **installieren** , Upgrade Advisor installieren.  
  
7.  Klicken Sie auf **Fertig stellen** , um den Assistenten zu beenden.  
  
## <a name="see-also"></a>Siehe auch  
 [Voraussetzungen für den Upgrade Advisor](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md)  
  
  
