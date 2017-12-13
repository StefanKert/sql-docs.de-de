---
title: Sp_grant_proxy_to_subsystem (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_grant_login_to_subsystem_TSQL
- sp_grant_login_to_subsystem
dev_langs: TSQL
helpviewer_keywords: sp_grant_proxy_to_subsystem
ms.assetid: 866aaa27-a1e0-453a-9b1b-af39431ad9c2
caps.latest.revision: "37"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 30b4d86a7700033d64e1288b846156dd4dfbcac3
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2017
---
# <a name="spgrantproxytosubsystem-transact-sql"></a>sp_grant_proxy_to_subsystem (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gewährt einem Subsystem einen Proxyzugriff.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_grant_proxy_to_subsystem  
     { [ @proxy_id = ] proxy_id | [ @proxy_name = ] 'proxy_name' },  
     { [ @subsystem_id = ] subsystem_id | [ @subsystem_name = ] 'subsystem_name' }  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@proxy_id =** ] *Id*  
 Die Proxy-ID des Proxys, dem der Zugriff gewährt werden soll. Die *Proxy_id* ist **Int**, hat den Standardwert NULL. Entweder *Proxy_id* oder *Proxy_name* muss angegeben werden, aber beide können nicht angegeben werden.  
  
 [  **@proxy_name =** ] **"***Proxy_name***"**  
 Der Name des Proxys, für den der Zugriff erteilt werden soll. Die *Proxy_name* ist **Sysname**, hat den Standardwert NULL. Entweder *Proxy_id* oder *Proxy_name* muss angegeben werden, aber beide können nicht angegeben werden.  
  
 [  **@subsystem_id =** ] *Id*  
 Die ID des Subsystems, auf das der Zugriff gewährt werden soll. Die *Subsystem_id* ist **Int**, hat den Standardwert NULL. Entweder *Subsystem_id* oder *Subsystem_name* muss angegeben werden, aber beide können nicht angegeben werden. In der folgenden Tabelle werden die Werte für jedes Subsystem aufgelistet.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**2**|[!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX-Skript<br /><br /> **\*\*Wichtige \* \***  das ActiveX Scripting-Subsystem daraus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents in einer zukünftigen Version von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden.|  
|**3**|Betriebssystem (**CmdExec**)|  
|**4**|Replikationsmomentaufnahme-Agent|  
|**5**|Replikationsprotokolllese-Agent|  
|**6**|Replikationsverteilungs-Agent|  
|**7**|Replikationsmerge-Agent|  
|**8**|Warteschlangenlese-Agent der Microsoft SQL Server-Replikation|  
|**9**|Analysis Services-Abfrage|  
|**10**|Analysis Services-Befehl|  
|**11**|[!INCLUDE[ssIS](../../includes/ssis-md.md)]-Paketausführung|  
|**12**|PowerShell-Skript|  
  
 [  **@subsystem_name =** ] **"***Subsystem_name***"**  
 Der Name des Subsystems, auf das der Zugriff gewährt werden soll. Die **Subsystem_name** ist **Sysname**, hat den Standardwert NULL. Entweder *Subsystem_id* oder *Subsystem_name* muss angegeben werden, aber beide können nicht angegeben werden. In der folgenden Tabelle werden die Werte für jedes Subsystem aufgelistet.  
  
|Wert|Description|  
|-----------|-----------------|  
|**ActiveScripting**|ActiveX-Skript|  
|**CmdExec**|Betriebssystem (**CmdExec**)|  
|**Momentaufnahme**|Replikationsmomentaufnahme-Agent|  
|**LogReader**|Replikationsprotokolllese-Agent|  
|**Distribution**|Replikationsverteilungs-Agent|  
|**Merge**|Replikationsmerge-Agent|  
|**QueueReader**|Warteschlangenlese-Agent der Microsoft SQL Server-Replikation|  
|**ANALYSISQUERY**|Analysis Services-Abfrage|  
|**ANALYSISCOMMAND**|Analysis Services-Befehl|  
|**Dts**|SSIS-Paketausführung|  
|**PowerShell**|PowerShell-Skript|  
  
## <a name="remarks"></a>Hinweise  
 Beim Gewähren eines Proxyzugriffs auf ein Subsystem werden nicht die Berechtigungen für den im Proxy angegebenen Prinzipal geändert.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** -Serverrolle kann ausführen **Sp_grant_proxy_to_subsystem**.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-granting-access-to-a-subsystem-by-id"></a>A. Gewähren von Zugriff auf ein Subsystem nach ID  
 Im folgenden Beispiel wird dem Proxy `Catalog application proxy` der Zugriff auf das ActiveX Scripting-Subsystem gewährt.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_grant_proxy_to_subsystem  
    @proxy_name = 'Catalog application proxy',  
    @subsystem_id = 2;  
GO  
```  
  
### <a name="b-granting-access-to-a-subsystem-by-name"></a>B. Gewähren von Zugriff auf ein Subsystem nach Name  
 Im folgenden Beispiel wird dem Proxy `Catalog application proxy` der Zugriff auf das Subsystem SSIS-Paketausführung gewährt.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_grant_proxy_to_subsystem  
    @proxy_name = N'Catalog application proxy',  
    @subsystem_name = N'Dts' ;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Implementieren von Sicherheit für SQL Server-Agent](http://msdn.microsoft.com/library/d770d35c-c8de-4e00-9a85-7d03f45a0f0d)   
 [Sp_revoke_proxy_from_subsystem &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-revoke-proxy-from-subsystem-transact-sql.md)   
 [Sp_add_proxy &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md)   
 [Sp_delete_proxy &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql.md)   
 [Sp_update_proxy &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-update-proxy-transact-sql.md)  
  
  