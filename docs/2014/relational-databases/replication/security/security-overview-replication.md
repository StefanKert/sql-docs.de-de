---
title: Sicherheitsübersicht (Replikation) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- authorization [SQL Server replication]
- cryptography [SQL Server replication]
- encryption [SQL Server replication]
- security [SQL Server replication], about security
- authentication [SQL Server replication]
ms.assetid: 27828fe4-3b54-4c33-886e-08e8279e34b5
caps.latest.revision: 44
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 62567dbbb53db61780f002779abb825e19287578
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37148261"
---
# <a name="security-overview-replication"></a>Sicherheitsübersicht (Replikation)
  Grundsätzlich basiert das Sichern der Replikationsumgebung auf den folgenden Faktoren: dem Verständnis der Authentifizierungs- und Autorisierungsoptionen, dem Verständnis der entsprechenden Verwendungsmöglichkeiten der Replikationsfilterfunktionen und dem Erlernen spezieller Maßnahmen zum Sichern der einzelnen Bestandteile einer Replikationsumgebung. Die Replikationsumgebung umfasst den Verteiler, den Verleger, Abonnenten und den Momentaufnahmeordner. Thema dieses Kapitels ist die Replikationssicherheit, die auf der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Sicherheit und Windows-Sicherheit aufbaut. Daher sind Kenntnisse dieser Grundlage und der Bedeutung der Replikationssicherheit unentbehrlich. Weitere Informationen zum Thema Sicherheit finden Sie unter [Überlegungen zur Sicherheit bei SQL Server-Installationen](../../../sql-server/install/security-considerations-for-a-sql-server-installation.md). Weitere Informationen zu den Überlegungen zur Sicherheit bei der Veröffentlichung von Oracle-Daten finden Sie im Abschnitt zum Replikations-Sicherheitsmodell im Thema [Design Considerations and Limitations for Oracle Publishers](../non-sql/design-considerations-and-limitations-for-oracle-publishers.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Mindern von Bedrohungen und Sicherheitsrisiken &#40;Replikation&#41;](threat-and-vulnerability-mitigation-replication.md)  
 Erläutert mögliche Bedrohungen für eine Replikationstopologie und beschreibt Möglichkeiten zum Verringern dieser Bedrohungen.  
  
 [Identität und Zugriffssteuerung &#40;Replikation&#41;](identity-and-access-control-replication.md)  
 Beschreibt das Verwenden von Authentifizierung, Autorisierung und Filtervorgängen zum Sichern einer Replikationstopologie.  
  
 [Sichere Entwicklung &#40;Replikation&#41;](secure-development-replication.md)  
 Beschreibt das Verhalten der Replikationssicherheit, bewährte Methoden für die Replikationssicherheit und Mindestberechtigungen für die Replikation.  
  
 [Sichere Bereitstellung &#40;Replikation&#41;](secure-deployment-replication.md)  
 Beschreibt, wie alle Komponenten einer Replikationstopologie besser gesichert werden können.  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheit und Schutz &#40;Replikation&#41;](security-and-protection-replication.md)  
  
  
