---
title: Verwenden der Verschlüsselung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- database master key [SMO]
- cryptography [SMO]
- cryptography [SQL Server], SMO
- encryption keys [SMO]
- encryption [SQL Server], SMO
- encryption [SMO]
- certificates [SMO]
- service master key [SMO]
ms.assetid: 405e0ed7-50a9-430e-a343-471f54b4af76
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a0d99702b9b6a48e02fe5acc36abed823718c560
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37236730"
---
# <a name="using-encryption"></a>Verwenden der Verschlüsselung
  In SMO wird der Diensthauptschlüssel durch dargestellt die <xref:Microsoft.SqlServer.Management.Smo.ServiceMasterKey> Objekt. Dies verweist auf die <xref:Microsoft.SqlServer.Management.Smo.Server.ServiceMasterKey%2A> Eigenschaft der <xref:Microsoft.SqlServer.Management.Smo.Server> Objekt. Sie können mithilfe von neu generiert werden die <xref:Microsoft.SqlServer.Management.Smo.ServiceMasterKey.Regenerate%2A> Methode.  
  
 Datenbank-Hauptschlüssels wird dargestellt, durch die <xref:Microsoft.SqlServer.Management.Smo.MasterKey> Objekt. Die <xref:Microsoft.SqlServer.Management.Smo.MasterKey.IsEncryptedByServer%2A> Eigenschaft gibt an, ob die Datenbank-Hauptschlüssel mit dem Diensthauptschlüssel verschlüsselt ist. Die verschlüsselte Kopie in der Hauptdatenbank wird immer dann automatisch aktualisiert, wenn der Datenbank-Hauptschlüssel geändert wird.  
  
 Es ist möglich, die Verschlüsselung mit Schlüsseln mit drop die <xref:Microsoft.SqlServer.Management.Smo.MasterKey.DropServiceKeyEncryption%2A> Methode und die Datenbank-Hauptschlüssel mit einem Kennwort zu verschlüsseln. In diesem Fall müssen Sie den Datenbank-Hauptschlüssel explizit öffnen, bevor Sie auf die privaten Schlüssel zugreifen, die von diesem gesichert wurden.  
  
 Wenn eine Datenbank mit einer Instanz von angehängt wird [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], müssen Sie das Kennwort für Datenbank-Hauptschlüssel bereitstellen oder Ausführen der <xref:Microsoft.SqlServer.Management.Smo.MasterKey.AddServiceKeyEncryption%2A> Methode, um eine unverschlüsselte Kopie des Datenbank-Hauptschlüssels für die Verschlüsselung mit dem Dienst verfügbar machen Hauptschlüssel. Dieser Schritt wird empfohlen, um zu vermeiden, dass der Datenbank-Hauptschlüssel explizit geöffnet werden muss.  
  
 Die <xref:Microsoft.SqlServer.Management.Smo.MasterKey.Regenerate%2A> Methode generiert den Datenbank-Hauptschlüssel neu. Wenn der Datenbank-Hauptschlüssel neu generiert wird, werden alle Schlüssel, die durch den Datenbank-Hauptschlüssel verschlüsselt wurden, entschlüsselt. Daraufhin werden diese mit dem neuen Datenbank-Hauptschlüssel verschlüsselt. Die <xref:Microsoft.SqlServer.Management.Smo.MasterKey.DropServiceKeyEncryption%2A> Methode entfernt die Verschlüsselung des Datenbank-Hauptschlüssels durch den Diensthauptschlüssel. Mit <xref:Microsoft.SqlServer.Management.Smo.MasterKey.AddServiceKeyEncryption%2A> wird eine Kopie des Hauptschlüssels mithilfe des Diensthauptschlüssels verschlüsselt und in der aktuellen Datenbank und in der Masterdatenbank gespeichert.  
  
 In SMO werden Zertifikate durch dargestellt die <xref:Microsoft.SqlServer.Management.Smo.Certificate> Objekt. Die <xref:Microsoft.SqlServer.Management.Smo.Certificate> Objekt verfügt über Eigenschaften, die angeben, den öffentlichen Schlüssel, den Namen des Betreffs, Zeitraum Gültigkeitsdauer und Informationen über den Aussteller. Berechtigung zum Zugriff auf das Zertifikat wird gesteuert durch Verwendung der `Grant`, `Revoke` und `Deny` Methoden.  
  
## <a name="example"></a>Beispiel  
 Für das folgende Codebeispiel müssen Sie die Programmierungsumgebung, die Programmiervorlage und die Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [erstellen Sie eine Visual Basic-SMO-Projekts in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) und [Erstellen eines Visual C&#35; SMO-Projekts in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="adding-a-certificate-in-visual-basic"></a>Hinzufügen eines Zertifikats in Visual Basic  
 Im Codebeispiel wird ein einfaches Zertifikat mit einem Verschlüsselungskennwort erstellt. Im Gegensatz zu anderen Objekten die <xref:Microsoft.SqlServer.Management.Smo.Certificate.Create%2A> -Methode weist mehrere Überladungen. Die im Beispiel verwendete Überladung erstellt ein Zertifikat mit einem Verschlüsselungskennwort.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBCertificate1](SMO How to#SMO_VBCertificate1)]  -->  
  
## <a name="adding-a-certificate-in-visual-c"></a>Hinzufügen eines Zertifikats in Visual C#  
 Im Codebeispiel wird ein einfaches Zertifikat mit einem Verschlüsselungskennwort erstellt. Im Gegensatz zu anderen Objekten die <xref:Microsoft.SqlServer.Management.Smo.Certificate.Create%2A> -Methode weist mehrere Überladungen. Die im Beispiel verwendete Überladung erstellt ein Zertifikat mit einem Verschlüsselungskennwort.  
  
```  
{  
            //Connect to the local, default instance of SQL Server.   
            {  
                Server srv = new Server();  
  
                //Reference the AdventureWorks2012 database.   
                Database db = srv.Databases["AdventureWorks2012"];  
  
                //Define a Certificate object variable by supplying the parent database and name in the constructor.   
                Certificate c = new Certificate(db, "Test_Certificate");  
  
                //Set the start date, expiry date, and description.   
                System.DateTime dt;  
                DateTime.TryParse("January 01, 2010", out dt);  
                c.StartDate = dt;  
                DateTime.TryParse("January 01, 2015", out dt);  
                c.ExpirationDate = dt;  
                c.Subject = "This is a test certificate.";  
                //Create the certificate on the instance of SQL Server by supplying the certificate password argument.   
                c.Create("pGFD4bb925DGvbd2439587y");  
            }  
        }   
```  
  
## <a name="adding-a-certificate-in-powershell"></a>Hinzufügen eines Zertifikats in PowerShell  
 Im Codebeispiel wird ein einfaches Zertifikat mit einem Verschlüsselungskennwort erstellt. Im Gegensatz zu anderen Objekten die <xref:Microsoft.SqlServer.Management.Smo.Certificate.Create%2A> -Methode weist mehrere Überladungen. Die im Beispiel verwendete Überladung erstellt ein Zertifikat mit einem Verschlüsselungskennwort.  
  
```  
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = get-item AdventureWorks2012  
  
#Create a certificate  
  
$c = New-Object -TypeName Microsoft.SqlServer.Management.Smo.Certificate -argumentlist $db, "Test_Certificate"  
$c.StartDate = "January 01, 2010"  
$c.Subject = "This is a test certificate."  
$c.ExpirationDate = "January 01, 2015"  
  
#Create the certificate on the instance of SQL Server by supplying the certificate password argument.  
$c.Create("pGFD4bb925DGvbd2439587y")  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Unter Verwendung eines Verschlüsselungsschlüssels](using-encryption.md)  
  
  
