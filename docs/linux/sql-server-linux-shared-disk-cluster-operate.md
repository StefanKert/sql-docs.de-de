---
title: Failoverclusterinstanz – SQL Server unter Linux arbeiten | Microsoft-Dokumentation
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/28/2017
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: d78162f149b96831d61ebcc0960db67887dc853c
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39087252"
---
# <a name="operate-failover-cluster-instance---sql-server-on-linux"></a>Arbeiten Sie Failoverclusterinstanz – SQL Server unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Artikel wird erläutert, wie eine SQL-Server-Failoverclusterinstanz (FCI) unter Linux ausgeführt wird. Wenn Sie eine SQL Server-FCI nicht unter Linux erstellt haben, finden Sie unter [konfigurieren-Failoverclusterinstanz – SQL Server unter Linux](sql-server-linux-shared-disk-cluster-configure.md). 

## <a name="failover"></a>Failover

Failover für FCIs ähnelt einem Windows Server-Failovercluster (WSFC). Wenn der Cluster-Knoten die FCI hostet eine Art von Fehler auftritt, sollte die FCI automatisch ein Failover auf einen anderen Knoten ausgeführt. Im Gegensatz zu einem WSFC besteht keine Möglichkeit, bevorzugter Besitzer festgelegt, sodass Pacemaker auf den Knoten auswählt, die dem neuen Host für die FCI zur Verfügung.

Es gibt Situationen, die Sie ggf. einen anderen Knoten die FCI manuelles Failover. Der Prozess ist nicht derselbe wie FCIs, die auf einem WSFC. Bei einem WSFC wird ein Failover der Ressourcen auf Rollenebene. In Pacemaker Auswahl einer Ressource zu verschieben, und vorausgesetzt, dass alle Einschränkungen richtig sind, alles wird verschieben ebenfalls. 

Die Möglichkeit zum Failover hängt von der Linux-Distribution. Befolgen Sie die Anweisungen für Ihre Linux-Distribution.

- [RHEL oder Ubuntu](#rhelFailover)
- [SLES](#slesFailover)

## <a name = "#rhelFailover"></a> Manuelles Failover (RHEL oder Ubuntu)

Führen Sie zum Ausführen eines manuellen Failovers Onn Red Hat Enterprise Linux (RHEL) oder Ubuntu-Servern die folgenden Schritte aus.
1.  Geben Sie den folgenden Befehl ein: 

   ```bash
   sudo pcs resource move <FCIResourceName> <NewHostNode> 
   ```

   \<FCIResourceName > ist der Name des Pacemaker-Ressourcen für die SQL Server-FCI.

   \<NewHostNode > ist der Name des Clusterknotens, der die FCI gehostet werden soll. 

   Sie erhalten Bestätigung nicht.

2.  Während eines manuellen Failovers erstellt Pacemaker eine speicherorteinschränkung für die Ressource, die Sie ausgewählt wurde, manuell zu verschieben. Führen Sie zum Anzeigen dieser Einschränkung `sudo pcs constraint`.

3.  Nachdem das Failover abgeschlossen ist, entfernen Sie die Einschränkung durch ausgeben `sudo pcs resource clear <FCIResourceName>`. 

\<FCIResourceName > ist der Name des Pacemaker-Ressourcen für die FCI. 

## <a name = "#slesFailover"></a> Manuelles Failover (SLES)


Verwenden Sie in die Suse Linux Enterprise Server (SLES), die `migrate` -Befehl, um ein manuelles Failover eine SQL Server-FCI. Zum Beispiel:

```bash
crm resource migrate <FCIResourceName> <NewHostNode>
```

\<FCIResourceName > ist der Name der Failoverclusterinstanz Teamressourcen. 

\<NewHostNode > ist der Name des neuen Zielhosts. 


<!---
|Distribution |Topic 
|----- |-----
|**Red Hat Enterprise Linux with HA add-on** |[Configure](sql-server-linux-shared-disk-cluster-red-hat-7-configure.md)<br/>[Operate](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
|**SUSE Linux Enterprise Server with HA add-on** |[Configure](sql-server-linux-shared-disk-cluster-sles-configure.md)
--->

## <a name="next-steps"></a>Nächste Schritte

- [Konfigurieren Sie Failoverclusterinstanz – SQL Server unter Linux](sql-server-linux-shared-disk-cluster-configure.md)

<!--Image references-->
