---
title: Installieren und Deinstallieren der OData-Quellkomponente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0a3ae788-e8c8-4a4d-bb15-34c673abcd17
caps.latest.revision: 7
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 039e8dd4f77c0593dcdceb69fbcd53138bc50b91
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37281326"
---
# <a name="install-and-uninstall-odata-source-component"></a>Installieren und Deinstallieren der OData-Quellkomponente
  Dieses Thema enthält Anweisungen zum Installieren oder Entfernen der OData-Quellkomponente auf dem Computer.  
  
## <a name="installation"></a>Installation  
 Die folgenden Komponenten müssen auf dem Computer installiert sein, um die OData-Quellkomponente installieren zu können.  
  
-   SQL Server Data Tools (zum Entwerfen von Paketen)  
  
-   SQL Server Integration Services (zum Ausführen von Paketen außerhalb von Visual Studio)  
  
 Um die OData-Quellkomponente zu installieren, laden [SQL Server 2014 Feature Pack](http://go.microsoft.com/fwlink/p/?LinkId=391999) und führen Sie einen der folgenden MSI-Dateien.  
  
-   ODataSourceForSQLServer2014-amd64.msi für 64-Bit-Plattformen  
  
-   ODataSourceForSQLServer2014-x86.msi für 32-Bit-Plattformen  
  
> [!IMPORTANT]  
>  Mit dem 64-Bit-Installationsprogramm installieren Sie sowohl die 32-Bit- als auch die 64-Bit-Version der OData-Quellkomponente. Das 32-Bit-Installationsprogramm müssen Sie nur ausführen, wenn Sie ein 32-Bit-Betriebssystem verwenden.  
  
## <a name="uninstallation"></a>Deinstallation  
 Die OData-Quellkomponente deinstalliert werden kann, aus der **Programme und Funktionen** Menü. Suchen der **Microsoft SQL Server SSIS OData-Quellkomponente (x64)** Eintrag und klicken Sie auf **Deinstallieren**.  
  
  