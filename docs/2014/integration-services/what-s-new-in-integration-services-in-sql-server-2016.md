---
title: Was&#39;s neue (Integrationsservices) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, what's new
- what's new [Integration Services]
ms.assetid: da6999c7-e5e3-4a59-a284-1da635995af1
caps.latest.revision: 112
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 39b6e64dbf6add0b026e384432059875cf724507
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37221680"
---
# <a name="what39s-new-integration-services"></a>Was&#39;s neue (Integrationsservices)
  [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] wurde gegenüber der Vorgängerversion nicht geändert.  
  
 Weitere Informationen zu anderen [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Produkten und Technologien finden Sie unter [Neuigkeiten in SQL Server 2014](../sql-server/what-s-new-in-sql-server-2016.md).  
  
 Weitere Informationen zu Änderungen in Bezug auf [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Business Intelligence, finden Sie unter [Neuigkeiten in Analysis Services und Business Intelligence](../analysis-services/what-s-new-in-analysis-services.md).  
  
##  <a name="ValidateXML"></a> Umfangreiche Ausgabe der XML-Validierung im XML-Task  
 Überprüfen Sie die XML-Dokumente und erhalten Sie umfangreiche Fehlerausgabe durch die Aktivierung der `ValidationDetails` Eigenschaft von der XML-Task. Bevor Sie die `ValidationDetails` Eigenschaft wurde zur Verfügung, die XML-Validierung durch den XML-Task nur "true" oder "false" hat ein Ergebnis zurückgegeben, ohne Informationen zu Fehlern oder wo diese auftraten. Nun, wenn Sie festlegen, `ValidationDetails` auf "true", die Ausgabe-Datei enthält ausführliche Informationen zu jedem Fehler, einschließlich der Zeilennummer und der Position. Sie können diese Informationen verwenden, um Fehler in XML-Dokumenten zu verstehen, zu finden und zu beheben. Weitere Informationen finden Sie unter [Validate XML with the XML Task](control-flow/xml-task.md).  
  
 [!INCLUDE[ssIS](../includes/ssis-md.md)] eingeführt, die `ValidationDetails` -Eigenschaft in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Service Pack 2. Diese neue Eigenschaft wurde zu diesem Zeitpunkt nicht angekündigt oder dokumentiert. Die `ValidationDetails` Eigenschaft ist auch verfügbar im [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] und in SQL Server 2016.  
  
## <a name="see-also"></a>Siehe auch  
 [Von den SQL Server 2014-Editionen unterstützte Funktionen](../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
  
