---
title: Erweiterungen für Reporting Services | Microsoft-Dokumentation
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
- SQL Server Reporting Services, extending
- extensions [Reporting Services], about extensions
- SSIS, extending
- Reporting Services, extending
- extensions [Reporting Services]
ms.assetid: 2bf17ae4-2292-4a58-a1f0-56e99abd9b69
caps.latest.revision: 44
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 67864d393f50fb6fa37ba36e032000d1739d508a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37268496"
---
# <a name="reporting-services-extensions"></a>Erweiterungen für Reporting Services
  Die modulare Architektur von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ermöglicht Erweiterungen. Eine verwaltete Code-API steht zur Verfügung, sodass Sie problemlos Erweiterungen entwickeln, installieren und verwalten können, die von vielen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Komponenten benötigt werden. Sie können private oder freigegebene Assemblys erstellen, indem Sie [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] verwenden und neue [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Funktionen hinzufügen, um den wachsenden Geschäftsanforderungen Ihres Unternehmens gerecht zu werden.  
  
 Durch die besondere Architektur für Erweiterungen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] können spezielle Erweiterungsfunktionen des Produkts und seiner Komponenten entwickelt werden. Momentan wird die Erweiterung der Datenverarbeitungsmöglichkeiten von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in großem Umfang unterstützt. Die Datenverarbeitungs-API enthält bekannte [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-Datenanbieter-Konstrukte und Konventionen, die den Entwicklern die Integration zusätzlicher Datenverarbeitungsmöglichkeiten in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] bieten. Diese Datenverarbeitungserweiterungen fügen sowohl dem Berichtsserver als auch dem Berichts-Designer weitere Funktionen hinzu, sodass eine nahtlose Integration der benutzerdefinierten Daten in die bestehenden Berichte ermöglicht wird.  
  
 Eine weitere unterstützte Erweiterung ist die Übermittlungserweiterung. Die Übermittlungs-API ist komplett in die [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-Architektur integriert und ermöglicht eine Vielzahl von Übermittlungsmechanismen für den Versand von Berichtsbenachrichtigungen an die Benutzer. Sie können den Berichtsserver so erweitern, dass er eine benutzerdefinierte Übermittlung an Benutzer zulässt. Und Sie können die Abonnementverwaltungsseiten des Berichts-Managers so erweitern, dass Abonnements möglich sind, die benutzerdefinierte Übermittlungserweiterungen verwenden.  
  
 Über eine weitere Berichtsservererweiterung, die RDCE-Erweiterung (Report Definition Customization Extension), kann eine Berichtsdefinition dynamisch angepasst werden, bevor Sie an die Verarbeitungs-Engine geleitet wird. Sie können Berichte an verschiedene Faktoren, z. B. an andere Benutzer oder Sprachen, anpassen. Beispielsweise möchten Sie verschiedene Ansichten für verschiedene Benutzer (z. B. Manager oder Mitarbeiter einer Abteilung) implementieren. Oder Sie möchten einen Bericht so anpassen, dass er ein anderes Layout hat, wenn er auf Französisch oder Arabisch ausgegeben wird.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Security Considerations for Extensions (Überlegungen zur Sicherheit von Erweiterungen)](security-considerations-for-extensions.md)  
 Beschreibt Sicherheitsprobleme, die beim Entwickeln und Bereitstellen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Erweiterungen auftreten können.  
  
 [Implementing a Data Processing Extension (Implementieren von Datenverarbeitungserweiterungen)](data-processing/implementing-a-data-processing-extension.md)  
 Beschreibt die Anforderungen und Schritte für die Implementierung von Datenverarbeitungserweiterungen für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 [Implementing a Delivery Extension (Implementieren von Übermittlungserweiterungen)](delivery-extension/implementing-a-delivery-extension.md)  
 Beschreibt die Anforderungen und Schritte für die Implementierung von Übermittlungserweiterungen für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 [Implementing a Rendering Extension (Implementieren von Renderingerweiterungen)](rendering-extension/implementing-a-rendering-extension.md)  
 Enthält eine Einführung zur Entwicklung von Renderingerweiterungen.  
  
 [Implementieren von Sicherheitserweiterungen](security-extension/implementing-a-security-extension.md)  
 Beschreibt die Anforderungen und Schritte für die Implementierung von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Sicherheitserweiterungen.  
  
 [Reporting Services Extension Library (Reporting Services-Erweiterungsbibliothek)](reporting-services-extension-library.md)  
 Enthält die Programmierreferenz für die Erweiterungs-API-Bibliothek für die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Erweiterbarkeitsfunktionen.  
  
  
