---
title: Sp_repltrans (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_repltrans_TSQL
- sp_repltrans
helpviewer_keywords:
- sp_repltrans
ms.assetid: 738e2322-335b-44fa-820e-f31c02743978
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 827ff7056b25ea3984838b5a4993eea63738920b
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43022605"
---
# <a name="sprepltrans-transact-sql"></a>sp_repltrans (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt ein Resultset aller Transaktionen im Transaktionsprotokoll der Veröffentlichungsdatenbank zurück, die zwar für die Replikation gekennzeichnet, aber noch nicht als verteilt gekennzeichnet sind. Diese gespeicherte Prozedur wird auf dem Verleger für eine Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_repltrans  
```  
  
## <a name="result-sets"></a>Resultsets  
 **Sp_repltrans** gibt Informationen über die Veröffentlichungsdatenbank, die von der es ausgeführt wird, sodass Sie derzeit keine verteilte Transaktionen anzeigen (die Transaktionen im Transaktionsprotokoll, die nicht gesendet wurden, verbleiben die Verteiler). Das Resultset zeigt für jede Transaktion die Protokollfolgenummer des ersten und letzten Datensatzes an. **Sp_repltrans** ähnelt [Sp_replcmds &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md) jedoch nicht die Befehle für die Transaktionen zurück.  
  
## <a name="remarks"></a>Hinweise  
 **Sp_repltrans** wird in Transaktionsreplikationen verwendet.  
  
 **Sp_repltrans** wird nicht unterstützt, für nicht -[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Herausgeber.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder die **Db_owner** feste Datenbankrolle können ausführen **Sp_repltrans**.  
  
## <a name="see-also"></a>Siehe auch  
 [Sp_repldone &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [Sp_replflush &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
