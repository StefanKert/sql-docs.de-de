---
title: '@@TIMETICKS (Transact-SQL) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- '@@TIMETICKS_TSQL'
- '@@TIMETICKS'
dev_langs:
- TSQL
helpviewer_keywords:
- ticks [SQL Server]
- '@@TIMETICKS function'
- microseconds per tick [SQL Server]
- time [SQL Server], ticks
- number of microseconds per tick
ms.assetid: 9d036633-837f-4309-9c45-3d9600258018
caps.latest.revision: 28
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 76cedb43f90feb68fe2e83136ae064fbdf2ba710
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/04/2018
ms.locfileid: "37785761"
---
# <a name="x40x40timeticks-transact-sql"></a>&#x40;&#x40;TIMETICKS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt die Anzahl von Mikrosekunden pro Takt zurück.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
@@TIMETICKS  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 **integer**  
  
## <a name="remarks"></a>Remarks  
 Die Zeitspanne pro Takt ist computerabhängig. Jeder Takt im Betriebssystem beträgt 31,25 Millisekunden oder 1/32 einer Sekunde.  
  
## <a name="examples"></a>Beispiele  
  
```  
SELECT @@TIMETICKS AS 'Time Ticks';  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [System Statistical Functions &#40;Transact-SQL&#41; (Statistische Systemfunktionen (Transact-SQL))](../../t-sql/functions/system-statistical-functions-transact-sql.md)  
  
  
