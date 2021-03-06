---
title: Sicherheitsanforderungen für das Verwalten von Diensten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent service, security
- services [SQL Server], security
- SQL Server services, security
- WMI Providers [SQL Server]
- server configuration [SQL Server]
- security [SQL Server], services
- services [SQL Server], WMI
ms.assetid: 1874a317-ddb2-425d-98d9-b53e1be6fc6a
caps.latest.revision: 27
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0fb5a41efec39b85c0633a3612097a7b643a69e7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37160891"
---
# <a name="security-requirements-for-managing-services"></a>Sicherheitsanforderungen für das Verwalten von Diensten
  Um den [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - und den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst zu verwalten, verwenden Sie entweder den SQL Server-Konfigurations-Manager oder [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Auf gruppierten Servern verwalten Sie die Dienste mit der Clusterverwaltung.  
  
 Um den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienst zu verwalten und die Konfigurationsoptionen für den Server festzulegen, müssen Sie Mitglied der festen Serverrolle **serveradmin** oder der festen Serverrolle **sysadmin** sein. Mitglieder der Windows-Gruppe **Administratoren** können Dienste starten und beenden und die unter Windows verfügbaren Serveroptionen konfigurieren.  
  
> [!NOTE]  
>  Um eine ordnungsgemäße Funktionsweise sicherzustellen, müssen die für die Dienste verwendeten Konten mit der richtigen Domäne, dem richtigen Dateisystem und den richtigen Registrierungsberechtigungen konfiguriert werden. Weitere Informationen zu erforderlichen Berechtigungen finden Sie unter [Konfigurieren von Windows-Dienstkonten und -Berechtigungen](configure-windows-service-accounts-and-permissions.md).  
  
## <a name="windows-management-instrumentation"></a>Windows-Verwaltungsinstrumentation  
 Der SQL Server-Konfigurations-Manager und [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] verwenden zum Anzeigen und Bearbeiten einiger Servereigenschaften die Windows-Verwaltungsinstrumentation (WMI, Windows Management Instrumentation). Um Dienste zu verwalten und den Status der Dienste abzufragen, muss der Benutzer über eine Zugriffsberechtigung für das WMI-Objekt verfügen. In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]wird die WMI auf den folgenden Servereigenschaftenseiten verwendet:  
  
-   Dienste automatisch starten  
  
-   Startparameter  
  
-   Security  
  
-   Sonstige Servereinstellungen  
  
## <a name="related-tasks"></a>Related Tasks  
 [Konfigurieren von WMI zum Anzeigen des Serverstatus in SQL Server-Tools](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [Konzepte des WMI-Anbieters für die Konfigurationsverwaltung](../../relational-databases/wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
  
  
