---
title: Systemanforderungen für die Adresse Book Anwendung | Microsoft Docs
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
- address book application scenario [ADO]
- RDS scenarios [ADO]
ms.assetid: da385405-1c9a-478b-9bf6-fba70015324c
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 063a8d6dd6001c612bb52efa2773deafa546fd86
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35274539"
---
# <a name="system-requirements-for-the-address-book-application"></a>Systemanforderungen für die Adresse Book-Anwendung
Um die beispielanwendung Adressbuch einzurichten, müssen Sie die folgenden Software- und Datenbank-Anforderungen erfüllen:  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in Windows-Betriebssystems enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/en-us/download/details.aspx?id=27416) detailliertere). RDS-Clientkomponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden sollten migrieren [WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="software-requirements"></a>Softwareanforderungen  
 Die Server-Computer-softwareanforderungen für die Ausführung dieser Webanwendung gehören:  
  
-   Microsoft Windows NT® Server 4.0 mit Service Pack 3 oder höher oder Microsoft Windows® 2000 Server.  
  
-   Microsoft IIS (Internetinformationsdienste) Version 3.0 oder höher, mit der Active Server Pages.  
  
 Die Client Computer Software-Anforderungen für die Ausführung dieser Webanwendung umfassen:  
  
-   Microsoft Internet Explorer 4.0 oder höher.  
  
-   Microsoft Windows NT 4.0 Workstation oder Server, Windows 2000 oder Microsoft Windows 98.  
  
## <a name="database-requirements"></a>Datenbankanforderungen  
 Um dieses Beispiel zu verwenden, benötigen Sie Folgendes:  
  
-   Eine operational Microsoft® SQL Server Version 6.5 oder höher-Datenbankserver.  
  
-   Berechtigungen zum Erstellen der Datenbank und mit Beispieldaten aufzufüllen.  
  
-   Überprüfung der aufgefüllten Daten über Enterprise Manager oder die ISQL-Hilfsprogramme (aufgerufene Query Analyzer in SQL Server 7.0).  
  
 Wenn Sie nicht über Berechtigungen verfügen, müssen möglicherweise der Datenbankadministrator richten Sie die System- und erteilen Sie Zugriff auf die Berechtigung für die Datenbank oder die Datenbank für Sie eingerichtet.  
  
## <a name="see-also"></a>Siehe auch  
 [Die Adressbuch SQL-Skript ausführen](../../../ado/guide/remote-data-service/running-the-address-book-sql-script.md)   
 [RDS (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [Ausführen der Adress Book-Beispielanwendung](../../../ado/guide/remote-data-service/running-the-address-book-sample-application.md)


