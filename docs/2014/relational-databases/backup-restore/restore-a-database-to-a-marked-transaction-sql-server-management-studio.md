---
title: Wiederherstellen einer Datenbank bis zu einer markierten Transaktion (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.restoretlog.markedtransaction.f1
helpviewer_keywords:
- database restores [SQL Server], marked transactions
- restoring databases [SQL Server], marked transactions
- marked transactions [SQL Server], restoring
ms.assetid: 8f0ea144-1819-4832-905f-e5d0f49b066b
caps.latest.revision: 19
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 489dd128afcae09c7f58114f2329453d479fe95a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37242740"
---
# <a name="restore-a-database-to-a-marked-transaction-sql-server-management-studio"></a>Wiederherstellen einer Datenbank bis zu einer markierten Transaktion (SQL Server Management Studio)
  Wenn sich eine Datenbank im Wiederherstellungsstatus befindet, können Sie das Dialogfeld **Transaktionsprotokoll wiederherstellen** verwenden, um die Datenbank bis zu einer markierten Transaktion in den verfügbaren Protokollsicherungen wiederherzustellen.  
  
> [!NOTE]  
>  Weitere Informationen finden Sie unter [Wiederherstellen von verwandten Datenbanken mithilfe von markierten Transaktionen &#40;vollständiges Wiederherstellungsmodell&#41;](use-marked-transactions-to-recover-related-databases-consistently.md) und [Wiederherstellen verwandter Datenbanken mit einer markierten Transaktion](recovery-of-related-databases-that-contain-marked-transaction.md).  
  
### <a name="to-restore-a-marked-transaction"></a>So stellen Sie eine markierte Transaktion wieder her  
  
1.  Klicken Sie im Objekt-Explorer nach dem Herstellen einer Verbindung mit der entsprechenden Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]auf den Servernamen, um die Serverstruktur zu erweitern.  
  
2.  Erweitern Sie **Datenbanken**, und wählen Sie je nach Datenbank eine Benutzerdatenbank aus, oder erweitern Sie **Systemdatenbanken** , und wählen Sie eine Systemdatenbank aus.  
  
3.  Klicken Sie mit der rechten Maustaste auf die Datenbank, zeigen Sie auf **Tasks**, und klicken Sie dann auf **Wiederherstellen**.  
  
4.  Klicken Sie auf **Transaktionsprotokoll**, um das Dialogfeld **Transaktionsprotokoll wiederherstellen** zu öffnen.  
  
5.  Wählen Sie **Markierte Transaktion** im Abschnitt **Wiederherstellen in** auf der Seite **Allgemein**aus, um das Dialogfeld **Markierte Transaktion auswählen** zu öffnen. Dieses Dialogfeld zeigt ein Raster an, in dem die markierten Transaktionen aufgelistet sind, die in den ausgewählten Transaktionsprotokollsicherungen zur Verfügung stehen.  
  
     Standardmäßig erfolgt die Wiederherstellung bis zur markierten Transaktion (die jedoch nicht eingeschlossen wird). Um die markierte Transaktion ebenfalls wiederherzustellen, wählen Sie **Markierte Transaktion einschließen**aus.  
  
     In der folgenden Tabelle werden die Spaltenheader des Rasters aufgelistet und deren Werte beschrieben.  
  
    |Header|value|  
    |------------|-----------|  
    |\<leer>|Zeigt ein Kontrollkästchen zur Auswahl der Markierung an.|  
    |**Transaktionsmarkierung**|Name der markierten Transaktion, der vom Benutzer zugewiesen wurde, als für die Transaktion der Commit ausgeführt wurde.|  
    |**Datum**|Datum und Uhrzeit, zu der für die Transaktion der Commit ausgeführt wurde. Als Transaktionsdatum und -uhrzeit werden das Datum und die Uhrzeit angezeigt, die in der **msdbgmarkhistory** -Tabelle aufgezeichnet wurden, nicht das Datum und die Uhrzeit des Clientcomputers.|  
    |**Beschreibung**|Die Beschreibung der markierten Transaktion, die der Benutzer angegeben hat, als für die Transaktion ein Commit ausgeführt wurde (sofern zutreffend).|  
    |**LSN**|Die Protokollfolgenummer (LSN, Log Sequence Number) der markierten Transaktion.|  
    |**Datenbank**|Der Name der Datenbank, in der für die markierte Transaktion ein Commit ausgeführt wird.|  
    |**Benutzername**|Der Name des Datenbankbenutzers, der für die markierte Transaktion ein Commit ausgeführt hat.|  
  
## <a name="see-also"></a>Siehe auch  
 [Wiederherstellen einer Datenbanksicherung &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md)   
 [Wiederherstellen einer Transaktionsprotokollsicherung &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md)  
  
  
