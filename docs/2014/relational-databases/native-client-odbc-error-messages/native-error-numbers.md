---
title: Systemeigene Fehlernummern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ODBC error handling, native error numbers
- SQL Server Native Client ODBC driver, errors
- native error numbers [SQL Server Native Client]
- messages [ODBC], native error numbers
- errors [ODBC], native error numbers
ms.assetid: 77cbc826-f47f-4803-8e7a-223d6df069b1
caps.latest.revision: 34
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 394d349e9edab24005244b8442f16623672c93a8
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37407119"
---
# <a name="native-error-numbers"></a>Systemeigene Fehlernummern
  Für Fehler, die in der Datenquelle auftreten (zurückgegebenes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]), wird die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber gibt zurück, die systemeigene Fehlernummer an, indem zurückgegeben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Für Fehler, die vom Treiber erkannt die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber gibt eine systemeigene Fehlernummer 0 zurück. Weitere Informationen über eine Liste mit systemeigenen Fehlernummern finden Sie in der Fehlerspalte der der **Sysmessages** -Systemtabelle in der **master** Datenbank [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Weitere Informationen über die Statusfehlercodes finden Sie unter [SQLSTATE &#40;ODBC-Fehlercodes&#41;](sqlstate-odbc-error-codes.md). Bei Fehlern, die von der Netzwerkbibliothek zurückgegeben werden, stammt die systemeigene Fehlernummer von der zugrunde liegenden Netzwerksoftware.  
  
## <a name="see-also"></a>Siehe auch  
 [Behandlung von Fehlern und Meldungen](handling-errors-and-messages.md)  
  
  
