---
title: Paketbereitstellung (SSIS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, deploying
- deploying packages [Integration Services]
- SQL Server Integration Services packages, deploying
- deploying packages [Integration Services], about deploying packages
- packages [Integration Services], deploying
- SSIS packages, deploying
ms.assetid: 0f5fc7be-e37e-4ecd-ba99-697c8ae3436f
caps.latest.revision: 45
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 26c5f0af58ea602a8a0d5e73512b5fa2df2a013b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37276956"
---
# <a name="package-deployment-ssis"></a>Paketbereitstellung (SSIS)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] enthält Tools und Assistenten, mit denen Sie problemlos Pakete vom Entwicklungscomputer auf dem Produktionsserver oder anderen Computern bereitstellen können.  
  
 Das Paketbereitstellungsverfahren gliedert sich in vier Schritte:  
  
1.  Der erste Schritt ist optional und umfasst das Erstellen von Paketkonfigurationen, die Eigenschaften von Paketelementen zur Laufzeit aktualisieren. Diese Konfigurationen werden beim Bereitstellen der Pakete automatisch mit eingeschlossen.  
  
2.  Im zweiten Schritt wird das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Projekt erstellt, um damit ein Paketbereitstellungshilfsprogramm zu erstellen. Das Bereitstellungshilfsprogramm für das Projekt enthält die Pakete, die Sie bereitstellen möchten.  
  
3.  Im dritten Schritt wird der Bereitstellungsordner, den Sie beim Erstellen des [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Projekts erstellt haben, auf den Zielcomputer kopiert.  
  
4.  Im vierten Schritt wird auf dem Zielcomputer der Paketinstallations-Assistent ausgeführt, um damit die Pakete auf dem Dateisystem oder einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu installieren.  
  
## <a name="related-tasks"></a>Related Tasks  
 Informationen zum Erstellen eines Bereitstellungshilfsprogramms finden Sie unter [Erstellen eines Bereitstellungs-Hilfsprogramms](../create-a-deployment-utility.md).  
  
 Informationen zum Bereitstellen von Paketen mit dem Bereitstellungshilfsprogramm finden Sie unter [Bereitstellen von Paketen mithilfe des Bereitstellungshilfsprogramms](../deploy-packages-by-using-the-deployment-utility.md).  
  
 Informationen zum Erstellen von Paketkonfigurationen finden Sie unter [Erstellen von Paketkonfigurationen](../create-package-configurations.md).  
  
  
