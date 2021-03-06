---
title: Sp_setapprole (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_setapprole
- sp_setapprole_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_setapprole
ms.assetid: cf0901c0-5f90-42d4-9d5b-8772c904062d
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 90007b46558fbe348f1619bbbdcf877faeaf1f7e
ms.sourcegitcommit: c12e41eff37fdfededc9b18ecf2e7e11893eb850
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/14/2018
ms.locfileid: "45599944"
---
# <a name="spsetapprole-transact-sql"></a>sp_setapprole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Aktiviert die Berechtigungen, die mit einer Anwendungsrolle in der aktuellen Datenbank verknüpft sind.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_setapprole [ @rolename = ] 'role',  
    [ @password = ] { encrypt N'password' }   
      |  
        'password' [ , [ @encrypt = ] { 'none' | 'odbc' } ]  
        [ , [ @fCreateCookie = ] true | false ]  
    [ , [ @cookie = ] @cookie OUTPUT ]  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@rolename =** ] **"***Rolle***"**  
 Der Name der Anwendungsrolle, die in der aktuellen Datenbank definiert ist. *Rolle* ist **Sysname**, hat keinen Standardwert. *role* muss in der aktuellen Datenbank vorhanden sein.  
  
 [  **@password =** ] **{verschlüsseln N'***Kennwort***'}**  
 Das für die Aktivierung der Anwendungsrolle erforderliche Kennwort. *Kennwort* ist **Sysname**, hat keinen Standardwert. *Kennwort* können mithilfe der ODBC verborgen werden **verschlüsseln** Funktion. Bei Verwendung der **verschlüsseln** -Funktion, das Kennwort muss in eine Unicode-Zeichenfolge konvertiert werden, indem platzieren **N** vor dem ersten Anführungszeichen.  
  
 Die Encrypt-Option wird für Verbindungen, verwendet wird, nicht unterstützt **SqlClient**.  
  
> [!IMPORTANT]  
>  Die ODBC **verschlüsseln** Funktion stellt keine Verschlüsselung bereit. Diese Funktion ist zum Schützen von Kennwörtern, die über ein Netzwerk übertragen werden, nicht empfehlenswert. Verwenden Sie SSL oder IPSec, um diese Informationen über ein Netzwerk zu übertragen.  
  
 **@encrypt = 'none'**  
 Gibt an, dass keine Verbergung verwendet wird. Das Kennwort wird als Nur-Text an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] übergeben. Dies ist die Standardeinstellung.  
  
 **@encrypt= 'Odbc'**  
 Gibt an, dass ODBC das Kennwort mithilfe der ODBC verbirgt **verschlüsseln** Funktion vor dem Senden des Kennworts für die [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Dies ist nur mit einem ODBC-Client oder dem OLE DB-Anbieter für SQL Server möglich.  
  
 [  **@fCreateCookie =** ] **"true"** | **"false"**  
 Gibt an, ob ein Cookie erstellt werden soll. **"true"** wird implizit in 1 konvertiert. **"false"** wird implizit in 0 konvertiert.  
  
 [  **@cookie =** ]  **@cookie AUSGABE**  
 Gibt einen Ausgabeparameter an, in dem das Cookie enthalten sein soll. Das Cookie wird nur generiert, wenn der Wert des **@fCreateCookie** ist **"true"**. **varbinary(8000)**  
  
> [!NOTE]  
>  Der **OUTPUT** -Cookieparameter für **sp_setapprole** ist zurzeit als **varbinary(8000)** dokumentiert, was der korrekten maximalen Länge entspricht. Die aktuelle Implementierung gibt jedoch **varbinary(50)** zurück. Anwendungen müssen weiterhin **varbinary(8000)** reservieren, damit die Anwendung weiterhin ordnungsgemäß ausgeführt wird, falls die Rückgabegröße des Cookies in einer zukünftigen Version erhöht wird.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Eine durch **sp_setapprole**aktivierte Anwendungsrolle bleibt aktiv, bis der Benutzer die Serververbindung trennt oder bis er **sp_unsetapprole**ausführt. **Sp_setapprole** ausgeführt werden kann, nur durch direkte [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisungen. **Sp_setapprole** kann nicht innerhalb einer anderen gespeicherten Prozedur oder innerhalb einer benutzerdefinierten Transaktion ausgeführt werden.  
  
 Eine Übersicht über Anwendungsrollen, finden Sie unter [Anwendungsrollen](../../relational-databases/security/authentication-access/application-roles.md).  
  
> [!IMPORTANT]  
>  Verwenden Sie immer eine verschlüsselte Verbindung, wenn Sie die Anwendungsrolle aktivieren, um das Kennwort für die Anwendungsrolle zu schützen, wenn es über ein Netzwerk übertragen wird.  
>   
>  Die [!INCLUDE[msCoName](../../includes/msconame-md.md)] ODBC **verschlüsseln** Option wird nicht unterstützt, indem **SqlClient**. Wenn Sie Anmeldeinformationen speichern müssen, verschlüsseln Sie sie mit den CryptoAPI-Funktionen. Der Parameter *Kennwort* wird als unidirektionaler Hash gespeichert. Um die Kompatibilität mit früheren Versionen von beizubehalten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Kennwortrichtlinie zur Komplexität wird nicht erzwungen, indem **Sp_addapprole**. Verwenden Sie zum Erzwingen der Kennwortrichtlinie zur Komplexität [CREATE APPLICATION ROLE](../../t-sql/statements/create-application-role-transact-sql.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in **öffentliche** und Kenntnis des Kennworts für die Rolle.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-activating-an-application-role-without-the-encrypt-option"></a>A. Aktivieren einer Anwendungsrolle ohne die encrypt-Option  
 Im folgenden Beispiel wird eine Anwendungsrolle namens `SalesAppRole` mit dem Nur-Text-Kennwort `AsDeF00MbXX` sowie mit den Berechtigungen aktiviert, die speziell für die vom aktuellen Benutzer verwendete Anwendung entworfen wurden.  
  
```  
EXEC sys.sp_setapprole 'SalesApprole', 'AsDeF00MbXX';  
GO  
```  
  
### <a name="b-activating-an-application-role-with-a-cookie-and-then-reverting-to-the-original-context"></a>B. Aktivieren einer Anwendungsrolle mit einem Cookie und anschließendes Zurücksetzen des ursprünglichen Kontexts  
 Im folgenden Beispiel wird die `Sales11` -Anwendungsrolle mit dem Kennwort `fdsd896#gfdbfdkjgh700mM`aktiviert, und es wird ein Cookie erstellt. Im Beispiel wird der Name des aktuellen Benutzers zurückgegeben, und der Kontext wird anschließend durch Ausführen von `sp_unsetapprole` auf den ursprünglichen Kontext zurückgesetzt.  
  
```  
DECLARE @cookie varbinary(8000);  
EXEC sys.sp_setapprole 'Sales11', 'fdsd896#gfdbfdkjgh700mM'  
    , @fCreateCookie = true, @cookie = @cookie OUTPUT;  
-- The application role is now active.  
SELECT USER_NAME();  
-- This will return the name of the application role, Sales11.  
EXEC sys.sp_unsetapprole @cookie;  
-- The application role is no longer active.  
-- The original context has now been restored.  
GO  
SELECT USER_NAME();  
-- This will return the name of the original user.   
GO   
```  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Security Stored Procedures &#40;Transact-SQL&#41; (Gespeicherte Sicherheitsprozeduren (Transact-SQL))](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE APPLICATION ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-application-role-transact-sql.md)   
 [DROP APPLICATION ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-application-role-transact-sql.md)   
 [Sp_unsetapprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unsetapprole-transact-sql.md)  
  
  
