---
title: Optionen (Abfrageausführung – SQL Server Seite Allgemein) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryExecution.SqlServer.SqlExecutionGeneral
ms.assetid: 3f8d59bc-3f97-4e5d-8b86-5ac670d20780
caps.latest.revision: 33
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 2c08ee6ab08fe90ffc075ef3f1ee0fe638d1da4e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37167151"
---
# <a name="options-query-execution-sql-server-general-page"></a>Optionen (Abfrageausführung – SQL Server Seite Allgemein)
  Auf dieser Seite können Sie die Optionen zum Ausführen von Abfragen in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] angeben. Die an diesen Optionen vorgenommenen Änderungen werden nur auf neue [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Abfragen angewendet. Um diese Optionen für eine aktuelle Abfrage zu ändern, klicken Sie entweder im Menü **Abfrage** auf **Abfrageoptionen**, oder klicken Sie mit der rechten Maustaste in ein Abfragefenster von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], und wählen Sie dann **Abfrageoptionen** aus.  
  
## <a name="options"></a>Tastatur  
 **SET ROWCOUNT**  
 Der Standardwert 0 zeigt an, dass [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] so lange auf die Ergebnisse wartet, bis alle Ergebnisse übermittelt sind. Geben Sie einen Wert größer 0 an, wenn die Abfrage von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] nach Übermittlung einer bestimmten Anzahl von Zeilen abgebrochen werden soll. Geben Sie SET ROWCOUNT 0 an, um diese Option zu deaktivieren (sodass alle Zeilen zurückgegeben werden).  
  
 **SET TEXTSIZE**  
 Der Standardwert 2.147.483.647 Bytes zeigt an, dass [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] vollständige Datenfelder bereitstellt, die maximal der Größe von Datenfeldern vom Typ `text` und `ntext` entsprechen. Geben Sie eine kleinere Zahl an, um Ergebnisse mit großen Werten zu beschränken. Spalten, deren Größe die angegebene Zahl übersteigt, werden abgeschnitten.  
  
 **Ausführungstimeout**  
 Legt den Standardwert im Dialogfeld **Neue Verbindung** fest. Mithilfe dieses Drehfelds können Sie angeben, nach wie vielen Sekunden [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] die Abfrage abbrechen soll. Der Wert '0' gibt an, dass der Wartevorgang unbegrenzt ist bzw. kein Timeout erfolgt. Bei einer Neuinstallation wird dieser Wert auf 0 festgelegt.  
  
 **Batchtrennzeichen**  
 Geben Sie ein Wort ein, das verwendet werden soll, um [!INCLUDE[tsql](../includes/tsql-md.md)]-Anweisungen in Batches zu trennen. Der Standardwert ist GO.  
  
 **Standardmäßig öffnen Sie neue Abfragen im SQLCMD-Modus**  
 Aktivieren Sie dieses Kontrollkästchen, um neue Abfragen im SQLCMD-Modus zu öffnen. Weitere Informationen zum SQLCMD-Modus finden Sie unter [Bearbeiten von SQLCMD-Skripts mit dem Abfrage-Editor](../relational-databases/scripting/edit-sqlcmd-scripts-with-query-editor.md).  
  
 Beachten Sie die folgenden Einschränkungen, wenn Sie diese Option auswählen:  
  
-   IntelliSense im [!INCLUDE[ssDE](../includes/ssde-md.md)] -Abfrage-Editor ist deaktiviert.  
  
-   Da der Abfrage-Editor nicht über die Befehlszeile ausgeführt werden kann, ist es nicht möglich, Befehlszeilenparameter, z. B. Variablen, zu übergeben.  
  
-   Da der Abfrage-Editor nicht auf Anforderungen des Betriebssystems reagieren kann, müssen Sie darauf achten, keine interaktiven Anweisungen auszuführen.  
  
 **Auf Standard zurücksetzen**  
 Klicken Sie hier, um alle auf dieser Seite verfügbaren Werte auf die ursprünglichen Standardwerte zurückzusetzen.  
  
## <a name="see-also"></a>Siehe auch  
 [sqlcmd Utility](../tools/sqlcmd-utility.md)  
  
  
