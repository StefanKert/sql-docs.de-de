---
title: Sp_linkedservers (Transact-SQL) | Microsoft-Dokumentation
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
- sp_linkedservers
- sp_linkedservers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_linkedservers
ms.assetid: d8f82f78-8a1f-4831-bcee-7c36c6e7dfbb
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 009131848d6e9cf942737ddc54c3d1b00f6e1163
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43038163"
---
# <a name="splinkedservers-transact-sql"></a>sp_linkedservers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt die Liste von Verbindungsservern zurück, die auf dem lokalen Server definiert sind.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_linkedservers  
```  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder eine Zahl ungleich Null (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**SRV_NAME**|**sysname**|Name des Verbindungsservers|  
|**SRV_PROVIDERNAME**|**Nvarchar (** 128 **)**|Der Anzeigename des OLE DB-Anbieters, der den Zugriff auf den angegebenen Verbindungsserver verwaltet.|  
|**SRV_PRODUCT**|**Nvarchar (** 128 **)**|Der Produktname des Verbindungsservers.|  
|**SRV_DATASOURCE**|**Nvarchar (** 4000 **)**|Die Eigenschaft der OLE DB-Datenquelle für den angegebenen Verbindungsserver.|  
|**SRV_PROVIDERSTRING**|**Nvarchar (** 4000 **)**|Die Zeichenfolgeneigenschaft des OLE DB-Anbieters für den angegebenen Verbindungsserver.|  
|**SRV_LOCATION**|**Nvarchar (** 4000 **)**|Die Eigenschaft des OLE DB-Standorts für den angegebenen Verbindungsserver.|  
|**SRV_CAT**|**sysname**|Die Eigenschaft des OLE DB-Katalogs für den angegebenen Verbindungsserver.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert SELECT-Berechtigung für das Schema.  
  
## <a name="see-also"></a>Siehe auch  
 [Sp_catalogs &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-catalogs-transact-sql.md)   
 [Sp_column_privileges &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-column-privileges-transact-sql.md)   
 [Sp_columns_ex &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-columns-ex-transact-sql.md)   
 [Sp_foreignkeys &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-foreignkeys-transact-sql.md)   
 [Sp_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-indexes-transact-sql.md)   
 [Sp_primarykeys &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-primarykeys-transact-sql.md)   
 [Sp_table_privileges &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [Sp_tables_ex &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-tables-ex-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Verteilte Abfragen, gespeicherten Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)  
  
  
