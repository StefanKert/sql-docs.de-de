---
title: Verweisen auf die ADO-Bibliotheken In Visual C++-Anwendung | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- libraries [ADO]
- referencing libraries in a Visual C++ application[ADO]
- ADO, libraries
ms.assetid: d3ea12ec-bca8-48c3-af57-ce14576108c9
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6a38e5df65def060668e60ee470dc379b873ab35
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35273609"
---
# <a name="referencing-the-ado-libraries-in-a-visual-c-application"></a>Verweisen auf die ADO-Bibliotheken In Visual C++-Anwendung
Um die neueste Version von ADO in einer Visual C++-Anwendung verwenden möchten, verwenden Sie die folgenden `#import` Richtlinie:  
  
```  
#import "msado15.dll" \  
    no_namespace rename("EOF", "EndOfFile")  
```  
  
 Sie müssen zum Verwenden von ADO MD oder ADOX importieren *msadomd.dll* oder *msadox.dll*, mit der oben aufgeführten Syntax.  
  
## <a name="backward-compatibility"></a>Backward Compatibility  
 Ersetzen Sie für die Verwendung eine frühere Version von ADO *"MSADO15.dll"* oben mit einem der folgenden Typbibliotheken.  
  
-   *msado27.tlb*, Version 2.7 ADO-Typbibliothek  
  
-   *msado26.tlb*, ADO 2.6-Typbibliothek  
  
-   *msado25.tlb*, ADO 2.5-Typbibliothek  
  
-   *MSADO21*, 2,1 ADO-Typbibliothek  
  
-   *msado20.tlb*, ADO-2.0-Typbibliothek
