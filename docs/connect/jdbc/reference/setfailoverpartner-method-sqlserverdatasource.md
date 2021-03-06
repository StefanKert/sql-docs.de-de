---
title: SetFailoverPartner-Methode (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDataSource.setFailoverPartner
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5310b7c2-9d10-474f-ad3a-218fe5da694b
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c6e08b2189e2eca12a44802ded59775b63a0fcb6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="setfailoverpartner-method-sqlserverdatasource"></a>setFailoverPartner-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den Namen des Failoverservers, der verwendet wird, in einer Datenbank-Spiegelungskonfiguration fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setFailoverPartner(java.lang.String serverName)  
```  
  
#### <a name="parameters"></a>Parameter  
 *ServerName*  
  
 Ein **Zeichenfolge** , die dem Namen des Failoverservers enthält.  
  
## <a name="remarks"></a>Hinweise  
 Der von dieser Methode festgelegte Wert wird im Falle eines Fehlers beim erstmaligen Herstellen einer Verbindung mit dem Prinzipalserver verwendet. Sobald die Verbindung hergestellt wurde, wird dieser Wert ignoriert. Die [SetDatabaseName](../../../connect/jdbc/reference/setdatabasename-method-sqlserverdatasource.md) Methode sollte auch in Verbindung mit dieser Methode verwendet werden, oder es wird eine Ausnahme ausgelöst.  
  
 Bei festgelegtem Failoverservernamen wird das Angeben der Portnummer des Failoverservers vom Treiber nicht unterstützt. Bei Aufruf der [SetServerName](../../../connect/jdbc/reference/setservername-method-sqlserverdatasource.md) Methode und die [SetInstanceName](../../../connect/jdbc/reference/setinstancename-method-sqlserverdatasource.md) Methode mit dem [SetFailoverPartner](../../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md) Methode wird unterstützt.  
  
## <a name="see-also"></a>Siehe auch  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
