---
title: SetPacketSize-Methode (SQLServerDataSource) | Microsoft-Dokumentation
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
- SQLServerDataSource.setPacketSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5d490edc-a223-4870-a838-784952497e5f
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c99c8516c6e38400798921aeae01f2387066e228
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "42784931"
---
# <a name="setpacketsize-method-sqlserverdatasource"></a>setPacketSize-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt die aktuelle Netzwerkpaketgröße (in Bytes) für die Kommunikation mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setPacketSize(int packetSize)  
```  
  
#### <a name="parameters"></a>Parameter  
 *packetSize*  
  
 Ein Wert vom Typ **int** mit der Netzwerkpaketgröße.  
  
## <a name="remarks"></a>Remarks  
 Der akzeptable Wertebereich dieser Eigenschaft lautet "[-1 | 0 | 512..32767]". Wenn diese Eigenschaft auf einen Wert außerhalb des zulässigen Bereichs festgelegt wird, wird eine Ausnahme ausgelöst.  
  
 Von der Anwendung wird unter Umständen versucht, die packetSize-Eigenschaft beim Herstellen einer Verbindung mit SSL (Secure Sockets Layer)-Verschlüsselung festzulegen. Die Paketgröße wird von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] mit dem Server ausgehandelt. Wenn die encrypt-Eigenschaft auf **TRUE** festgelegt ist und die ausgehandelte Paketgröße die SSL-Datensatzgröße des Standardsicherheitsanbieters der Java Virtual Machine (JVM) übersteigt, wird vom Treiber ein Fehler ausgelöst, und die Verbindung wird getrennt.  
  
 Darüber hinaus wird von der Anwendung unter Umständen versucht, die packetSize-Eigenschaft ohne Anforderung der SSL-Verschlüsselung festzulegen. In diesem Fall gilt Folgendes: Wird vom Server vorausgesetzt, dass der Clientcomputer die SSL-Verschlüsselung unterstützt, wird vom Treiber die SSL-Datensatzgröße des Standardsicherheitsanbieters der JVM überprüft. Übersteigt die packetSize-Eigenschaft die Datensatzgröße des Standardsicherheitsanbieters der Java Virtual Machine (JVM), wird vom Treiber ein Fehler ausgelöst, und die Verbindung wird getrennt.  
  
 Weitere Informationen zur Verwendung von SSL finden Sie unter [Using SSL Encryption](../../../connect/jdbc/using-ssl-encryption.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
