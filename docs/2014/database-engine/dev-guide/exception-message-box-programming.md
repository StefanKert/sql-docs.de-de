---
title: Ausnahmemeldung Programmierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ExceptionMessageBox class, about ExceptionMessageBox class
- exception message box [SQL Server], about exception message box
- exception message box [SQL Server]
- interfaces [SQL Server]
- exceptions [SQL Server]
- messages [SQL Server], exception message box
ms.assetid: 0b1ba514-6959-4e69-bfd2-3cf3c1ac4b9c
caps.latest.revision: 16
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 21882b1f6bb6233723a0ee7b60c7c7682abd5fa7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37148371"
---
# <a name="exception-message-box-programming"></a>Programmierung eines Ausnahmemeldungsfelds
  Das Ausnahmemeldungsfeld ist eine programmgesteuerte Schnittstelle, die mit installiert wird, und verwendet [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] grafische Komponenten. Das Ausnahmemeldungsfeld ist eine unterstützte verwaltete Assembly, die Sie in Ihren Anwendungen verwenden können, um die Steuerungsmöglichkeiten für Meldungen bedeutend zu erweitern, Benutzern die Möglichkeit zum Speichern von Fehlermeldungen zur späteren Bezugnahme zu geben und Hilfe zu Meldungen abzurufen. Weil das Ausnahmemeldungsfeld von allen Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit Ausnahme von [!INCLUDE[ssEW](../../includes/ssew-md.md)] installiert wird, können Sie es ohne zusätzliche Konfiguration auf jedem Computer verwenden, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Clientkomponenten installiert wurden.  
  
 Die <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox>-Klasse im <xref:Microsoft.SqlServer.MessageBox>-Namespace verfügt über die gesamte Funktionalität der <xref:System.Windows.Forms.MessageBox>-Klasse und mehr. Die <xref:System.Windows.Forms.MessageBox>-Klasse wurde für die Handhabung von Ausnahmen in verwaltetem Code konzipiert und ist somit ideal für alle Aufgaben, für die <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> verwendet werden kann. Durch das Ausnahmemeldungsfeld werden folgende Aktionen ermöglicht:  
  
-   Bereitstellen von benutzerdefiniertem Schaltflächentext für bis zu fünf Schaltflächen. Die Größe von Schaltflächen und Dialogfeldern wird automatisch an verschiedene Textlängen angepasst.  
  
-   Ermöglichen, dass Benutzer den Meldungstitel, den Meldungstext, Schaltflächentexte und Links mit Hilfethemen (sofern vorhanden) in die Zwischenablage kopieren oder diese Informationen in einer E-Mail-Nachricht senden  
  
-   Alle zugrunde liegenden Ausnahmen und Fehlern in einer hierarchischen Beziehungsstruktur angezeigt wird, wenn der Benutzer klicken auf **Zusatzinformationen**.  
  
-   Ermöglichen, dass die Benutzer entscheiden können, ob die Meldung angezeigt werden soll, wenn die gleiche Ausnahme erneut auftritt.  
  
-   Zugriff auf ein Onlinehilfesystem über einen der Ausnahme zugeordneten Hilfelink  
  
 Weitere Informationen finden Sie unter [Programm Ausnahmemeldungsfeld](../../../2014/database-engine/dev-guide/program-exception-message-box.md).  
  
  
