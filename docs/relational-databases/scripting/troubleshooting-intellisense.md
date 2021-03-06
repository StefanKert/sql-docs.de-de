---
title: Problembehandlung von IntelliSense (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- unavailable options [IntelliSense]
- IntelliSense [SQL Server], troubleshooting
- IntelliSense [SQL Server], unavailable options
- troubleshooting [IntelliSense]
ms.assetid: 4b72ffc6-aea2-4e11-ab36-fa2de4d7bcc5
caps.latest.revision: 41
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6dbbe26d5e6c03f1e7e85ae53ce751a6aac4b3c5
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43065752"
---
# <a name="troubleshooting-intellisense"></a>Problembehandlung bei IntelliSense
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Es gibt bestimmte Fälle, in denen die IntelliSense-Optionen unter Umständen nicht erwartungsgemäß funktionieren.  
  
## <a name="conditions-that-affect-intellisense"></a>Bedingungen, die Auswirkungen auf IntelliSense haben  
 Die folgenden Bedingungen können das Verhalten von IntelliSense beeinflussen:  
  
-   Über dem Cursor wird ein Codefehler angezeigt.  
  
     Wenn sich über der Position der Einfügemarke eine unvollständige Anweisung oder ein anderer Codierungsfehler befindet, kann IntelliSense die Codeelemente möglicherweise nicht analysieren und funktioniert daher nicht. Sie können den verfügbaren Code auskommentieren, um IntelliSense erneut zu aktivieren.  
  
-   Die Einfügemarke befindet sich innerhalb eines Codekommentars.  
  
     Wenn sich die Einfügemarke innerhalb eines Kommentars in der Quelldatei befindet, sind IntelliSense-Optionen nicht verfügbar.  
  
-   Die Einfügemarke befindet sich innerhalb eines Zeichenfolgenliterals.  
  
     Wenn sich die Einfügemarke innerhalb der Anführungszeichen eines Zeichenfolgenliterals befindet, sind IntelliSense-Optionen nicht verfügbar, z. B. in:  
  
     `WHERE FirstName LIKE 'Patri%|'`  
  
-   Die automatischen Optionen sind deaktiviert.  
  
     Viele IntelliSense-Funktionen funktionieren standardmäßig automatisch. Sie können die einzelnen Funktionen deaktivieren.  
  
     Auch wenn die automatische Anweisungsvervollständigung deaktiviert ist, können Sie eine IntelliSense-Funktion verwenden. Weitere Informationen finden Sie unter [Konfigurieren von IntelliSense &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/configure-intellisense-sql-server-management-studio.md).  
  
## <a name="database-engine-query-intellisense"></a>IntelliSense in der Datenbank-Engine-Abfrage  
 Die folgenden Probleme gelten für den [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] -Abfrage-Editor:  
  
-   Die IntelliSense-Funktionalität des [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrage-Editors unterstützt nicht alle [!INCLUDE[tsql](../../includes/tsql-md.md)] -Syntaxelemente. Die Parameterhilfe unterstützt nicht die Parameter in manchen Objekten, z. B. in erweiterten gespeicherten Prozeduren. Weitere Informationen finden Sie unter [Von IntelliSense unterstützte Transact-SQL-Syntax](../../relational-databases/scripting/transact-sql-syntax-supported-by-intellisense.md).  
  
-   IntelliSense ist nur verfügbar, wenn der [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrage-Editor mit einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] oder höher verbunden ist. IntelliSense ist nicht verfügbar, wenn der Abfrage-Editor mit früheren Versionen von [!INCLUDE[ssDE](../../includes/ssde-md.md)]verbunden ist.  
  
-   IntelliSense wird im [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrage-Editor deaktiviert, wenn der SQLCMD-Modus aktiviert wird.  
  
-   Die IntelliSense-Funktionalität deckt keine von einer anderen Verbindung erstellten Datenbankobjekte ab, nachdem das Editorfenster eine Verbindung mit der Datenbank hergestellt hat. Wenn Objekte in IntelliSense-Funktionen, beispielsweise Vervollständigungslisten fehlen, können Sie einen dieser drei Mechanismen auswählen, um den Cache von Objekten für das Editor-Fenster zu aktualisieren:  
  
    -   Wählen Sie das Menü **Bearbeiten** , **IntelliSense**und dann **Lokalen Cache aktualisieren**aus.  
  
    -   Verwenden Sie die Tastenkombination STRG+UMSCHALT+R.  
  
    -   Trennen Sie die Verbindung des Editorfensters von der [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz, und stellen Sie erneut eine Verbindung her.  
  
-   Vervollständigungslisten enthalten keine Datenbankobjekte, für die Sie keine Berechtigungen haben. IntelliSense kennzeichnet Verweise auf Objekte, für die Sie Berechtigungen haben. Wenn Sie z. B. ein Skript öffnen, das von einer anderen Person geschrieben wurde, werden alle Verweise auf Objekte, für die diese Person über Berechtigungen verfügt, Sie dagegen nicht, als inkorrekt gekennzeichnet.  
  
-   Vervollständigungslisten funktionieren möglicherweise nicht mehr, wenn die Verbindung zur Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)]verloren geht. Stellen Sie erneut eine Verbindung zur Instanz her.  
  
  
