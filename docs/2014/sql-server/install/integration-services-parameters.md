---
title: Integration Services-Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, parameters
ms.assetid: b1bb3ea3-8097-4e76-b9c2-78a0f46a23bc
caps.latest.revision: 6
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 15d484ffbd513ac8a14f4388cd3cdce897654164
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37282556"
---
# <a name="integration-services-parameters"></a>Integration Services-Parameter
  Für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], können Sie entscheiden, Analysieren [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Pakete auf dem Computer oder [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Paketdateien im Dateisystem. Wenn Sie sich dafür entscheiden, Dateien im Dateisystem zu analysieren, müssen Sie einen Pfad zum Ordner angeben, der die [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Pakete enthält.  
  
## <a name="options"></a>Tastatur  
 **SSIS-Pakete auf Server analysieren**  
 Wählen Sie diese Option zum Analysieren [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Pakete auf dem Computer. Standardmäßig ist diese Option ausgewählt.  
  
 **SSIS-Paketdateien analysieren**  
 Wählen Sie diese Option aus, um [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Pakete im Dateisystem zu analysieren.  
  
 **Pfad zu SSIS-Paketen**  
 Geben Sie einen UNC-Namen oder lokalen Pfad ein, unter dem sich die [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Pakete befinden. Sie müssen keine Dateinamen angeben. Wenn der eingegebene Pfad nicht zugegriffen werden kann, Sie können nicht klicken **Weiter**. Standardmäßig ist der Pfad leer. Dieses Feld ist nur aktiviert, wenn Sie auswählen, **Analysieren von SSIS-Paketdateien**.  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit dem Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [Upgrade Advisor Referenz zur Benutzeroberfläche](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
