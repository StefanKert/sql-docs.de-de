---
title: Ändern des Systemadministratorkontos (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- administrators [Master Data Services], changing
ms.assetid: cf30312e-4338-49a7-90f0-6e4f7b431ff8
caps.latest.revision: 6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a6d15bf7b140445ca80f23fe22e058a78d6fdce0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37298610"
---
# <a name="change-the-system-administrator-account-master-data-services"></a>Ändern Systemadministratorkontos (Master Data Services)
  Sie können ändern, dass das Benutzerkonto, das als festgelegt ist die [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Systemadministrator.  
  
> [!WARNING]  
>  Wenn Sie diese Prozedur ausführen, wird das Benutzerkonto des vorherigen Systemadministrators gelöscht.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen der Liste Benutzer in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] den Benutzernamen des neuen Administrators hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen eines Benutzers &#40;Master Data Services&#41;](add-a-user-master-data-services.md).  
  
-   Sie müssen berechtigt sein, die Tabelle mdm.tblUser anzuzeigen und die gespeicherte Prozedur mdm.udpSecurityMemberProcessRebuildModel in der [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]-Datenbank auszuführen. Weitere Informationen finden Sie unter [Sicherheit von Datenbankobjekten &#40;Master Data Services&#41;](../../2014/master-data-services/database-object-security-master-data-services.md).  
  
### <a name="to-change-the-administrator-account"></a>So ändern Sie das Administratorkonto  
  
1.  Öffnen Sie [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] , und stellen Sie eine Verbindung mit der [!INCLUDE[ssDE](../includes/ssde-md.md)] -Instanz für die [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank her.  
  
2.  Suchen Sie in mdm.tblUser den Benutzer, die den neuen Administrator und kopieren Sie den Wert in der `SID` Spalte.  
  
3.  Erstellen Sie eine neue Abfrage.  
  
4.  Geben Sie den folgenden Text ein, und Ersetzen Sie dabei *Domäne\Benutzername* mit Benutzernamen des neuen Administrators und *SID* mit den in Schritt 2 kopierten Wert.  
  
    ```  
    EXEC [mdm].[udpSecuritySetAdministrator] @UserName='DOMAIN\user_name', @SID = 'SID', @PromoteNonAdmin = 1  
    ```  
  
5.  Führen Sie die Abfrage aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Administratoren &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md)  
  
  
