---
title: DROP COLUMN MASTER KEY (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/20/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DROP COLUMN MASTER KEY
- DROP_COLUMN_MASTER_KEY_TSQL
- DROP COLUMN MASTER
- DROP_COLUMN_MASTER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_master_keys catalog view
ms.assetid: fd5e77c8-a3ae-4795-bb46-b322c0500041
caps.latest.revision: 14
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 0d296c7bdb9c5923a49454c10e23f87a8156aff7
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "37997182"
---
# <a name="drop-column-master-key-transact-sql"></a>DROP COLUMN MASTER KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Entfernt einen Spaltenhauptschlüssel aus einer Datenbank. Dies ist ein Metadatenvorgang.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DROP COLUMN MASTER KEY key_name;  
```  
  
## <a name="arguments"></a>Argumente  
 *key_name*  
 Der Namen des Spaltenhauptschlüssels.  
  
## <a name="remarks"></a>Remarks  
 Der Spaltenhauptschlüssel kann nur gelöscht werden, wenn keine Werte des Spaltenverschlüsselungsschlüssels mit dem Spaltenhauptschlüssel verschlüsselt wurden. Verwenden Sie die Anweisung [DROP COLUMN ENCRYPTION KEY](../../t-sql/statements/drop-column-encryption-key-transact-sql.md), um die Werte des Spaltenverschlüsselungsschlüssels zu löschen.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die **ALTER ANY COLUMN MASTER KEY**-Berechtigung auf die Datenbank.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-dropping-a-column-master-key"></a>A. Löschen eines Spaltenhauptschlüssels  
 Im folgenden Beispiel wird ein Spaltenhauptschlüssel mit der Bezeichnung `MyCMK` entfernt.  
  
```  
DROP COLUMN MASTER KEY MyCMK;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [CREATE COLUMN MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-master-key-transact-sql.md)   
 [CREATE COLUMN ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-encryption-key-transact-sql.md)   
 [DROP COLUMN ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-column-encryption-key-transact-sql.md)   
 
  [Always Encrypted &amp;#40;Datenbank-Engine&amp;#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [sys.column_master_keys &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-master-keys-transact-sql.md)  
  
  
