---
title: Dienstkonten (Assistent zum Konfigurieren der Sicherheit für die Datenbankspiegelung) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.serviceaccounts.f1
ms.assetid: d58d8f93-7888-4d66-af4d-969ef6a2dbee
caps.latest.revision: 32
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d6479097305016d471a2b5434f7cab18a452928d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37182779"
---
# <a name="service-accounts-configure-database-mirroring-security-wizard"></a>Dienstkonten (Assistent zum Konfigurieren der Sicherheit für die Datenbankspiegelung)
  Geben Sie bei Verwendung der Windows-Authentifizierung die Dienstkonten für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]an, wenn die Serverinstanzen verschiedene Konten verwenden. Diese Dienstkonten müssen alle Domänenkonten (in derselben oder vertrauenswürdigen Domäne) sein.  
  
 Wenn alle Serverinstanzen das gleiche Domänenkonto oder die zertifikatbasierte Authentifizierung verwenden, lassen Sie die Felder leer. Klicken Sie einfach auf **Fertig stellen**, und der Assistent konfiguriert automatisch die Konten auf Basis des Kontos des aktuellen Assistenten.  
  
> [!IMPORTANT]  
>  Wenn die Endpunkte für die Datenbankspiegelung der Serverinstanzen für die Verwendung von Zertifikaten konfiguriert sind, müssen Sie die Felder für die Dienstkonten leer lassen.  
  
 **So konfigurieren Sie die Datenbankspiegelung mithilfe von SQL Server Management Studio**  
  
-   [Einrichten einer Datenbank-Spiegelungssitzung mithilfe der Windows-Authentifizierung &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md)  
  
-   [Starten des Assistenten zum Konfigurieren der Sicherheit für die Datenbankspiegelung &#40;SQL Server Management Studio&#41;](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a>Tastatur  
 **Prinzipal**  
 Geben Sie das Dienstkonto der Prinzipalserverinstanz an. Geben Sie den Domänennamen in Großbuchstaben ein:  
  
 *DOMÄNENNAME*\\*Benutzername*  
  
 **Spiegel**  
 Geben Sie das Dienstkonto der Spiegelserverinstanz an. Geben Sie den Domänennamen in Großbuchstaben ein:  
  
 *DOMÄNENNAME*\\*Benutzername*  
  
 **Zeuge**  
 Geben Sie das Dienstkonto der Zeugenserverinstanz an. Geben Sie den Domänennamen in Großbuchstaben ein:  
  
 *DOMÄNENNAME*\\*Benutzername*  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften &#40;Seite „Wird gespiegelt“&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [Starten des Datenbankspiegelungs-Monitors &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)   
 [Datenbankspiegelung &#40;SQL Server&#41;](database-mirroring-sql-server.md)   
 [Einrichten von Anmeldekonten für die Datenbankspiegelung oder AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](set-up-login-accounts-database-mirroring-always-on-availability.md)  
  
  
