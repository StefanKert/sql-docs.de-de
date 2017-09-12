---
title: DROP ROUTE (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP ROUTE
- DROP_ROUTE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dropping routes
- DROP ROUTE statement
- deleting routes
- routes [Service Broker], removing
- removing routes
ms.assetid: d8fab0bc-d54a-46ca-9437-552db7477d40
caps.latest.revision: 33
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 037753a9dc22077b2b36158458c1ea98bbe7e0f5
ms.contentlocale: de-de
ms.lasthandoff: 09/01/2017

---
# <a name="drop-route-transact-sql"></a>DROP ROUTE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Löscht eine Route, wobei die Informationen für die Route aus der Routingtabelle der aktuellen Datenbank gelöscht werden.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DROP ROUTE route_name  
[ ; ]  
```  
  
## <a name="arguments"></a>Argumente  
 *route_name*  
 Der Name der zu löschenden Route. Server-, Datenbank- und Schemaname können nicht angegeben werden.  
  
## <a name="remarks"></a>Hinweise  
 Die Routingtabelle, die Routen gespeichert, ist eine Metadatentabelle, die über die Katalogansicht gelesen werden kann **sys.routes**. Die Routingtabelle kann nur mit der CREATE ROUTE-, ALTER ROUTE- und DROP ROUTE-Anweisung aktualisiert werden.  
  
 Eine Route kann unabhängig davon gelöscht werden, ob sie von einer Konversation verwendet wird. Falls jedoch keine andere Route zum Remotedienst verfügbar ist, verbleiben Nachrichten für diese Konversation in der Übertragungswarteschlange, bis eine Route zum Remotedienst erstellt wird oder sich ein Timeout für die Konversation ergibt.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig verfügen der Besitzer der Route, Mitglieder der festen Datenbankrollen db_ddladmin und db_owner sowie Mitglieder der festen Serverrolle sysadmin über die Berechtigung zum Löschen einer Route.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Route `ExpenseRoute` gelöscht.  
  
```  
DROP ROUTE ExpenseRoute ;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [ALTER ROUTE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-route-transact-sql.md)   
 [CREATE ROUTE &#40;Transact-SQL&#41;](../../t-sql/statements/create-route-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [Sys.Routes &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-routes-transact-sql.md)  
  
  