---
title: Datenformate für Massenimport oder Massenexport (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: data-movement
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data formats [SQL Server], choosing
- bulk importing [SQL Server], data formats
ms.assetid: 73fe6741-9437-4b26-b030-28b863e74399
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4b76f7306ba6c76ff56ce54a7a1f188871cc2e00
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37231230"
---
# <a name="data-formats-for-bulk-import-or-bulk-export-sql-server"></a>Datenformate für Massenimport oder Massenexport (SQL Server)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann Daten in Zeichendatenformat oder systemeigenem binärem Datenformat akzeptieren. Verwenden Sie das Zeichenformat, wenn Sie Daten zwischen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und einer anderen Anwendung (z. B. [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel) bzw. einem anderen Datenbankserver (wie Oracle oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) verschieben. Das systemeigene Format kann nur verwendet werden, wenn Sie Daten zwischen verschiedenen Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verschieben.  
  
 **In diesem Thema:**  
  
-   [Datenformate für Massenimport oder -export](#ComponentsAndConcepts)  
  
-   [Verwandte Aufgaben](#RelatedTasks)  
  
##  <a name="ComponentsAndConcepts"></a> Datenformate für Massenimport oder -export  
 In der folgenden Tabelle ist angegeben, welches Datenformat im Allgemeinen für die Verwendung geeignet ist. Die Wahl hängt von der Darstellung der Daten und von der Quelle bzw. dem Ziel des Vorgangs ab.  
  
|Vorgang|Systemeigenes Format|Systemeigenes Unicode-Format|Zeichen|Unicode-Zeichen|  
|---------------|------------|--------------------|---------------|-----------------------|  
|Massenübertragung von Daten zwischen mehreren Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe einer Datendatei, die keine Sonderzeichen oder Zeichen aus Doppelbyte-Zeichensätzen (Double-Byte Character Set, DBCS) enthält. Sofern keine Formatdatei verwendet wird, müssen diese Tabellen identisch definiert sein.|Ja<sup>1</sup>|—|—|—|  
|Für `sql_variant`-Spalten eignet sich das systemeigene Datenformat am besten, da es im Gegensatz zu Zeichen- und Unicode-Formaten die Metadaten für die einzelnen `sql_variant`-Werte beibehält.|ja|—|—|—|  
|Massenübertragung von Daten zwischen mehreren Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe einer Datendatei, die Sonderzeichen oder DBCS-Zeichen enthält.|—|ja|—|—|  
|Massenimport von Daten aus einer Textdatei, die von einem anderen Programm generiert wurde.|—|—|ja|—|  
|Massenexport von Daten in eine Textdatei, die in einem anderen Programm verwendet werden soll.|—|—|ja|—|  
|Massenübertragung von Daten zwischen mehreren Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe einer Datendatei, die Unicode-Daten, aber keine Sonderzeichen oder DBCS-Zeichen enthält.|—|—|—|ja|  
  
 <sup>1</sup> schnellste Methode für den Massenexport von Daten aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verwendung **Bcp**.  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Verwenden des nativen Formats zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Verwenden des Zeichenformats zum Importieren und Exportieren von Daten &#40;SQL Server&#41;](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Verwenden des nativen Unicode-Formats zum Importieren oder Exportieren von Daten &#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Verwenden des Unicode-Zeichenformats zum Importieren und Exportieren von Daten &#40;SQL Server&#41;](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Importieren von Daten aus früheren SQL Server-Versionen im nativen Format oder im Zeichenformat](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Datentypen &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)   
 [Angeben von Datenformaten für die Kompatibilität bei Verwendung von bcp &#40;SQL Server&#41;](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)  
  
  
