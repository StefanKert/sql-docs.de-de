---
title: Übersicht über Übermittlungserweiterungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- subscriptions [Reporting Services], delivery extensions
- delivery extensions [Reporting Services], about extensions
ms.assetid: a30600a9-bbed-4519-9426-3470ff2982e7
caps.latest.revision: 36
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: d465eaa47bcc357c17df5bdaab6dcab4522aa8d9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37168258"
---
# <a name="delivery-extensions-overview"></a>Übersicht über Übermittlungserweiterungen
  Mithilfe von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] können Benutzer Berichte erstellen und veröffentlichen, die nach der Erstellung und Veröffentlichung an diverse Orte übermittelt werden können. Außerdem enthält [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] verschiedene Übermittlungserweiterungen und eine Übermittlungs-API, mit der Entwickler zusätzliche Übermittlungserweiterungen erstellen können, um die Übermittlungsfunktionen in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] noch zu erweitern.  
  
 In folgender Tabelle finden Sie eine Liste der Übermittlungserweiterungen, die in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] enthalten sind.  
  
|Übermittlungserweiterung|Description|  
|------------------------|-----------------|  
|Berichtsserver-E-Mail|Verwendet einen SMTP-Server, um Berichte an einzelne Benutzer oder Gruppen zu senden.|  
|Berichtsserver-Dateifreigabe|Wird verwendet, um Berichte in Ihrer Organisation an Netzwerk-Dateifreigaben zu verteilen. Bietet die Möglichkeit, einen Bericht automatisch nach einem festgelegten Zeitplan in eine Dateifreigabe zu kopieren.|  
  
 ![Reporting Service-Architektur der Übermittlungserweiterungen](../../media/bk-reportservicedelivery.gif "Reporting Services delivery extension architecture")  
Architektur der Übermittlungserweiterungen von Reporting Services  
  
 Übermittlungserweiterungen und Abonnements werden paarweise zugeordnet. Beim Erstellen eines Abonnements kann der Benutzer eine der verfügbaren Übermittlungserweiterungen auswählen, um die Art der Übermittlung des Berichts zu bestimmen. In [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] befinden sich Abonnements in der Berichtsserver-Datenbank. Wenn ein Ereignis auftritt, gleicht [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] das Ereignis mit den in der Berichtsserver-Datenbank enthaltenen Abonnements ab. Für jedes Abonnement, das an das Ergebnis gebunden ist, erstellt der Berichtsserver eine Benachrichtigung. Bei datengesteuerten Abonnements wird eine Benachrichtigung für jeden Empfänger erstellt. Sobald eine Benachrichtigung erstellt wurde, ruft der Berichtsserver eine bestimmte Übermittlungserweiterung auf und übernimmt die in der Benachrichtigung angegebenen Werte für die Erweiterungseinstellungen. Die Übermittlungserweiterung sendet die Benachrichtigung an den Benutzer, wie von der ausgewählten Übermittlungserweiterung angegeben.  
  
 Übermittlungserweiterungen implementieren die [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Übermittlungserweiterungs-API. Da die Übermittlungserweiterungen die [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Übermittlungserweiterungs-API unterstützen, können sie Benachrichtigungen vom Berichtsserver empfangen und den Status der Benachrichtigung angeben.  
  
 Der Berichtsserver verwaltet keine Übermittlungsziele für die Benachrichtigungen und Berichte. Die Zielinformationen werden über den Code gesammelt, den Sie in die Übermittlungserweiterung schreiben.  
  
## <a name="subscriptions-and-delivery-extensions"></a>Abonnements und Übermittlungserweiterungen  
 Clientanwendungen erstellen Abonnements, die Übermittlungserweiterungen mit zwei Methoden des Berichtsserver-Webdiensts verwenden: <xref:ReportService2010.ReportingService2010.CreateSubscription%2A> und <xref:ReportService2010.ReportingService2010.CreateDataDrivenSubscription%2A>. Abonnements, die bereits vorhanden sind, werden mit den Methoden <xref:ReportService2010.ReportingService2010.SetSubscriptionProperties%2A> und <xref:ReportService2010.ReportingService2010.SetDataDrivenSubscriptionProperties%2A> geändert. Wenn Sie ein Abonnement erstellen, wählt der Benutzer außerdem eine Übermittlungserweiterung für das Abonnement aus und gibt Werte für die erforderlichen Erweiterungseinstellungen ein. Wenn ein Benutzer ein Abonnement speichert, wird es in der Berichtsserver-Datenbank gespeichert. Abonnements erstellen die Benachrichtigungen auf der Grundlage eines Zeitplans oder eines Ereignisses. Wenn eine Übermittlung beginnt, lädt die ausgewählte Übermittlungserweiterung zuerst alle Konfigurationsdaten aus der Konfigurationsdatei. Danach werden die Erweiterungseinstellungen für das Abonnement abgerufen, und die Werte werden festgelegt. Zum Schluss wird die <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A>-Methode aufgerufen und die Benachrichtigung versandt.  
  
## <a name="developer-requirements"></a>Anforderungen für die Entwickler  
 Für die Entwicklung einer [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Übermittlungserweiterung benötigen Sie Folgendes:  
  
-   Einen Bereitstellungscomputer, auf dem ein Berichtsserver installiert ist.  
  
-   Einen Entwicklungscomputer, auf dem [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)] oder das [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK installiert ist.  
  
-   Sehr gute Kenntnisse der [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Funktionen und -Fähigkeiten, insbesondere zu Abonnement und Übermittlung.  
  
-   Sehr gute Kenntnisse der [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]- und Websteuerungselemente, wenn Sie eine eigene Abonnementbenutzeroberfläche für den Berichts-Manager implementieren möchten.  
  
-   Entwicklungserfahrung in einer [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]-Sprache, z.B. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# oder [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET.  
  
## <a name="see-also"></a>Siehe auch  
 [Implementieren von Übermittlungserweiterungen](../delivery-extension/implementing-a-delivery-extension.md)   
 [Reporting Services Extension Library (Reporting Services-Erweiterungsbibliothek)](../reporting-services-extension-library.md)  
  
  
