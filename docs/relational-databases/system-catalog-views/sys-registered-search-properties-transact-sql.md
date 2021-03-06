---
title: Sys. registered_search_properties (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.registered_search_properties
- registered_search_properties
- sys.registered_search_properties_TSQL
- registered_search_properties_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], search property lists
- search properties [SQL Server]
- property searching [SQL Server], viewing registered properties
- search property lists [SQL Server], viewing registered properties
- sys.registered_search_properties catalog view
ms.assetid: 1b9a7a5c-8c05-4819-83c3-7487dd08fcf7
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 79fddbbaa06dc5486b08a1c7209d5952b1a10dcd
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43107143"
---
# <a name="sysregisteredsearchproperties-transact-sql"></a>sys.registered_search_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Enthält eine Zeile für jede Sucheigenschaft in einer Sucheigenschaftenliste der aktuellen Datenbank.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**property_list_id**|**int**|Die ID der Sucheigenschaftenliste, zu der diese Eigenschaft gehört.|  
|**property_set_guid**|**uniqueidentifier**|Die GUID, mit der der Eigenschaftensatz identifiziert wird, zu dem die Sucheigenschaft gehört.|  
|**property_int_id**|**int**|Ganzzahl, die die Sucheigenschaft innerhalb des Eigenschaftensatzes identifiziert. **Property_int_id** innerhalb des Eigenschaftensatzes eindeutig ist.|  
|**property_name**|**Nvarchar(64)**|Ein Name, mit dem die Sucheigenschaft in der Sucheigenschaftenliste eindeutig identifiziert werden kann.<br /><br /> Hinweis: Um für eine Eigenschaft zu suchen, geben Sie den Eigenschaftsnamen im der [CONTAINS](../../t-sql/queries/contains-transact-sql.md) Prädikat.|  
|**property_description**|**nvarchar(512)**|Beschreibung der Eigenschaft.|  
|**property_id**|**int**|Interne Eigenschaften-ID der Sucheigenschaft in der sucheigenschaftenliste eine Eigenschaft von identifiziert die **Property_list_id** Wert.<br /><br /> Wenn einer Sucheigenschaftenliste eine Eigenschaft hinzugefügt wird, registriert die Volltext-Engine die Eigenschaft und weist ihr eine interne Eigenschaften-ID zu, die für diese Eigenschaftenliste spezifisch ist. Die interne Eigenschaften-ID stellt eine ganze Zahl dar und ist für eine bestimmte Sucheigenschaftenliste eindeutig. Wenn eine bestimmte Eigenschaft für mehrere Sucheigenschaftenlisten registriert wird, kann für jede Sucheigenschaftenliste eine andere interne Eigenschaften-ID zugewiesen werden.<br /><br /> Hinweis: Die interne Eigenschaften-ID unterscheidet sich von den Eigenschaftsbezeichner für die ganze Zahl, der angegeben wird, wenn Sie die Eigenschaft der sucheigenschaftenliste eine Eigenschaft hinzufügen. Weitere Informationen finden Sie unter [Suchen von Dokumenteigenschaften mithilfe von Sucheigenschaftenlisten](../../relational-databases/search/search-document-properties-with-search-property-lists.md).<br /><br /> So zeigen Sie allen eigenschaftsbezogenen Inhalte in den Volltextindex an: <br />                  [sys.dm_fts_index_keywords_by_property &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-property-transact-sql.md)|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zu Sucheigenschaftenlisten finden Sie unter [Suchen von Dokumenteigenschaften mithilfe von Sucheigenschaftenlisten](../../relational-databases/search/search-document-properties-with-search-property-lists.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Die Sichtbarkeit der Metadaten für Sucheigenschaften ist auf Daten in Sucheigenschaftenlisten beschränkt, die Sie besitzen oder für die Sie über eine REFERENCE-Berechtigung verfügen.  
  
> [!NOTE]  
>  REFERENCE- oder CONTROL-Berechtigungen können vom Besitzer einer Sucheigenschaftenliste gewährt werden. Benutzer mit CONTROL-Berechtigung können anderen Benutzern auch eine REFERENCE-Berechtigung erteilen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel sind alle Metadaten für registrierte Sucheigenschaften aufgeführt.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT * FROM sys.registered_search_properties;   
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md)   
 [sys.fulltext_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md)   
 [Suchen von Dokumenteigenschaften mithilfe von Sucheigenschaftenlisten](../../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
  
