---
title: Installieren von SMO | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.prod_service: database-engine
ms.component: smo
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- installing SMO
- SMO [SQL Server], installing
- SQL Server Management Objects, installing
ms.assetid: 140e9971-4940-4866-89b9-5cec938e2a16
caps.latest.revision: 46
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1a684d9a7ca41745c2e6ceb51d585e5420ab6740
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43098437"
---
#<a name="installing-smo"></a>Installieren von SMO

[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

Diese Seite enthält Informationen zum Installieren von SMO für die Verwendung von Anwendungen und Systemanforderungen für die Verwendung von SMO.

## <a name="smo-nuget-package"></a>SMO-NuGet-Paket

Beginnend mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2017 SMO wird als verteilt die [Microsoft.SqlServer.SqlManagementObjects](https://www.nuget.org/packages/Microsoft.SqlServer.SqlManagementObjects) NuGet-Paket, dass Benutzer Anwendungen mit SMO zu entwickeln können.

Dies ist ein Ersatz für SharedManagementObjects.msi, die zuvor als Teil der SQL-Feature Pack für jede Version von SQL Server veröffentlicht wurde. Anwendungen, die SMO verwenden sollten aktualisiert werden, um das NuGet-Paket verwenden und dafür verantwortlich, sicherzustellen, dass die Binärdateien installiert sind, mit der Anwendung, die entwickelt werden.

>>[!Important]
>>Wie erwähnt die [Dateien und Versionsnummern](files-and-version-numbers.md) Seite, Sie sollten nicht die SMO-Assemblys im globalen Assemblycache installieren. Auf diese Weise kann dazu führen, dass Probleme mit anderen Anwendungen, die ebenfalls diese Versionen von SMO verwenden (z. B. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio).

##<a name="installing-the-package"></a>Installieren des Pakets

Finden Sie unter [NuGet Schnellstart - Verwenden eines Pakets](https://docs.microsoft.com/nuget/quickstart/use-a-package) Anweisungen und Beispiele für die Installation und Verwendung eines NuGet-Pakets. 
  
## <a name="system-requirements"></a>Systemanforderungen
  
 SMO erfordert [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4.0 ausführen, sodass alle Anwendungen verwenden, sicherstellen müssen, dass Clientcomputer die Version oder höher installiert.
  
