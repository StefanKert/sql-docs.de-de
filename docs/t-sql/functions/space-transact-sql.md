---
title: SPACE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SPACE_TSQL
- SPACE
dev_langs:
- TSQL
helpviewer_keywords:
- strings [SQL Server], repeated spaces
- repeated spaces
- SPACE function
ms.assetid: b4fac3b8-2d47-4c11-a6a6-009e5a538f40
caps.latest.revision: 38
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: fce89abc555283c22398a35c6877a726a4020280
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43110643"
---
# <a name="space-transact-sql"></a>SPACE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt eine Zeichenfolge aus mehreren Leerzeichen zurück.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
SPACE ( integer_expression )  
```  
  
## <a name="arguments"></a>Argumente  
 *integer_expression*  
 Eine positive ganze Zahl, die die Anzahl von Leerzeichen anzeigt. Wenn *integer_expression* negativ ist, wird eine NULL-Zeichenfolge zurückgegeben.  
  
 Weitere Informationen finden Sie unter [Ausdrücke &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md).  
  
## <a name="return-types"></a>Rückgabetypen  
 **varchar**  
  
## <a name="remarks"></a>Remarks  
 Verwenden Sie REPLICATE anstelle von SPACE, wenn Sie Leerzeichen in Unicode-Daten einfügen oder mehr als 8000 Zeichenstellen zurückgeben möchten.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden die Nachnamen gekürzt und ein Komma, zwei Leerzeichen und die Vornamen der in der `Person`-Tabelle in `AdventureWorks2012` aufgelisteten Personen verkettet.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT RTRIM(LastName) + ',' + SPACE(2) +  LTRIM(FirstName)  
FROM Person.Person  
ORDER BY LastName, FirstName;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
 Im folgenden Beispiel werden die Nachnamen gekürzt und ein Komma, zwei Leerzeichen und die Vornamen der in der `DimCustomer`-Tabelle in `AdventureWorksPDW2012` aufgelisteten Personen verkettet.  
  
```  
-- Uses AdventureWorks  
  
SELECT RTRIM(LastName) + ',' + SPACE(2) +  LTRIM(FirstName)  
FROM dbo.DimCustomer  
ORDER BY LastName, FirstName;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [REPLICATE &#40;Transact-SQL&#41;](../../t-sql/functions/replicate-transact-sql.md)   
 [String Functions &#40;Transact-SQL&#41; (Zeichenfolgenfunktionen (Transact-SQL))](../../t-sql/functions/string-functions-transact-sql.md)   
 [Integrierte Funktionen &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)  
  
  


