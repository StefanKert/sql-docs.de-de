---
title: Bandbreite für Volltextbenachrichtigung (Serverkonfigurationsoption) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- ft notify bandwidth opion
- small memory buffers
- memory [SQL Server], buffers
ms.assetid: 9ca284c5-f3e0-4a67-a132-fff376ff0ffe
caps.latest.revision: 19
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 68b6bda063c9bcbb2eb938c5310b91233ef7a866
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37287906"
---
# <a name="ft-notify-bandwidth-server-configuration-option"></a>Bandbreite für Volltextbenachrichtigung (Serverkonfigurationsoption)
  Mit der **ft notify bandwidth** -Option können Sie angeben, bis zu welcher Größe der Pool mit geringem Arbeitsspeicher anwachsen kann. Kleine Arbeitsspeicherpuffer sind 64 KB groß. Der Parameterwert *max* gibt die maximale Anzahl von Puffern an, die der Volltextspeicher-Manager in einem kleinen Pufferpool verwalten soll. Wenn die `max` Wert ist 0 (null), dann gibt es keine obere Grenze für die Anzahl der Puffer, die in einem kleinen Pufferpool sein können.  
  
 Durch den Parameter **min** wird die minimale Anzahl von Speicherpuffern angegeben, die in einem Pool mit geringem Arbeitsspeicher verwaltet werden müssen. Auf Anforderung vom [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Speicher-Manager werden alle zusätzlichen Pufferpools freigegeben, die Mindestzahl an Puffern wird jedoch beibehalten. Ist der angegebene **min** -Wert jedoch gleich null, werden alle Speicherpuffer freigegeben.  
  
 Unter bestimmten Umständen ist die Pufferanzahl, die aktuell zugeordnet ist, geringer als der durch den Parameter **min** angegebene Wert.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [Bandbreite für Volltextdurchforstung (Serverkonfigurationsoption)](ft-crawl-bandwidth-server-configuration-option.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
