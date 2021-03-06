---
title: Verwalten von Benutzern, Rollen und Anmeldungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: smo
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- logins [SMO]
- roles [SMO]
- users [SMO]
ms.assetid: 74e411fa-74ed-49ec-ab58-68c250f2280e
caps.latest.revision: 45
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 6df551e9e32dc722cea67adf27eb5eacf6f290e3
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43077397"
---
# <a name="managing-users-roles-and-logins"></a>Verwalten von Benutzern, Rollen und Anmeldungen
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  In SMO werden Anmeldungen durch das <xref:Microsoft.SqlServer.Management.Smo.Login>-Objekt dargestellt. Wenn die Anmeldung in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vorhanden ist, kann sie zu einer Serverrolle hinzugefügt werden. Die Serverrolle wird dargestellt, durch die <xref:Microsoft.SqlServer.Management.Smo.ServerRole> Objekt. Die Datenbankrolle wird durch das <xref:Microsoft.SqlServer.Management.Smo.DatabaseRole>-Objekt und die Anwendungsrolle durch das <xref:Microsoft.SqlServer.Management.Smo.ApplicationRole>-Objekt dargestellt.  
  
 Der Serverebene zugeordnete Berechtigungen sind aufgeführt, als Eigenschaften der <xref:Microsoft.SqlServer.Management.Smo.ServerPermission> Objekt. Berechtigungen können für einzelne Anmeldekonten gewährt, verweigert oder aufgehoben werden.  
  
 Jede <xref:Microsoft.SqlServer.Management.Smo.Database> Objekt verfügt über eine <xref:Microsoft.SqlServer.Management.Smo.UserCollection> -Objekt, das alle Benutzer in der Datenbank angibt. Jeder Benutzer wird einer Anmeldung zugeordnet. Eine Anmeldung kann Benutzern in mehr als einer Datenbank zugeordnet werden. Die <xref:Microsoft.SqlServer.Management.Smo.Login> des Objekts <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> Methode kann verwendet werden, um alle Benutzer in allen Datenbanken aufzulisten, die der Anmeldung zugeordnet sind. Alternativ legt die <xref:Microsoft.SqlServer.Management.Smo.User>-Eigenschaft des <xref:Microsoft.SqlServer.Management.Smo.Login>-Objekts die Anmeldung fest, die dem Benutzer zugeordnet ist.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Datenbanken verfügen auch über Rollen, die einen Satz von Berechtigungen auf Datenbankebene festlegen, mit die einen Benutzer bestimmte Tasks durchführen können. Im Gegensatz zu Serverrollen sind Datenbankrollen variabel. Sie können erstellt, geändert und gelöscht werden. Einer Datenbankrolle können für die Massenverwaltung Berechtigungen und Benutzer zugeordnet werden.  
  
## <a name="example"></a>Beispiel  
 Für die folgenden Codebeispiele müssen Sie die Programmierungsumgebung, die Programmiervorlage und die Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [Erstellen eines Visual C&#35; SMO-Projekts in Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="enumerating-logins-and-associated-users-in-visual-c"></a>Auflisten von Anmeldungen und zugeordneten Benutzern in Visual C#  
 Jeder Benutzer in einer Datenbank ist einer Anmeldung zugeordnet. Die Anmeldung kann Benutzern in mehreren Datenbanken zugeordnet werden. Das Codebeispiel zeigt, wie die <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A>-Methode des <xref:Microsoft.SqlServer.Management.Smo.Login>-Objekts aufgerufen wird, um alle Datenbankbenutzer aufzulisten, die der Anmeldung zugeordnet sind. Das Beispiel erstellt eine Anmeldung und einen Benutzer in der [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] Datenbank stellen Sie sicher, dass Zuordnungsinformationen vorliegen, die aufgelistet werden.  
  
```csharp  
{   
Server srv = new Server();   
//Iterate through each database and display.   
  
foreach ( Database db in srv.Databases) {   
   Console.WriteLine("========");   
   Console.WriteLine("Login Mappings for the database: " + db.Name);   
   Console.WriteLine(" ");   
   //Run the EnumLoginMappings method and return details of database user-login mappings to a DataTable object variable.   
   DataTable d;  
   d = db.EnumLoginMappings();   
   //Display the mapping information.   
   foreach (DataRow r in d.Rows) {   
      foreach (DataColumn c in r.Table.Columns) {   
         Console.WriteLine(c.ColumnName + " = " + r[c]);   
      }   
      Console.WriteLine(" ");   
   }   
}   
}  
```  
  
## <a name="enumerating-logins-and-associated-users-in-powershell"></a>Auflisten von Anmeldungen und zugeordneten Benutzern in PowerShell  
 Jeder Benutzer in einer Datenbank ist einer Anmeldung zugeordnet. Die Anmeldung kann Benutzern in mehreren Datenbanken zugeordnet werden. Das Codebeispiel zeigt, wie die <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A>-Methode des <xref:Microsoft.SqlServer.Management.Smo.Login>-Objekts aufgerufen wird, um alle Datenbankbenutzer aufzulisten, die der Anmeldung zugeordnet sind. Das Beispiel erstellt eine Anmeldung und einen Benutzer in der [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] Datenbank stellen Sie sicher, dass Zuordnungsinformationen vorliegen, die aufgelistet werden.  
  
```powershell  
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\Default\Databases  
  
#Iterate through all databases  
 foreach ($db in Get-ChildItem)  
 {  
 "====="  
 "Login Mappings for the database: "+ $db.Name  
  
 #get the datatable containing the mapping from the smo database oject  
 $dt = $db.EnumLoginMappings()  
  
 #display the results  
 foreach($row in $dt.Rows)  
     {  
        foreach($col in $row.Table.Columns)  
      {  
        $col.ColumnName + "=" + $row[$col]  
       }  
  
     }  
 }  
```  
  
## <a name="managing-roles-and-users"></a>Verwalten von Rollen und Benutzern  
 Im folgenden Beispiel wird die Verwaltung von Rollen und Benutzern gezeigt. Zum Ausführen dieses Beispiels müssen Sie die folgenden Assemblys verweisen:  
  
-   Microsoft.SqlServer.Smo.dll  
  
-   Microsoft.SqlServer.Management.Sdk.Sfc.dll  
  
-   Microsoft.SqlServer.ConnectionInfo.dll  
  
-   Microsoft.SqlServer.SqlEnum.dll  
  
```csharp  
using Microsoft.SqlServer.Management.Smo;  
using System;  
  
public class A {  
   public static void Main() {  
      Server svr = new Server();  
      Database db = new Database(svr, "TESTDB");  
      db.Create();  
  
      // Creating Logins  
      Login login = new Login(svr, "Login1");  
      login.LoginType = LoginType.SqlLogin;  
      login.Create("password@1");  
  
      Login login2 = new Login(svr, "Login2");  
      login2.LoginType = LoginType.SqlLogin;  
      login2.Create("password@1");  
  
      // Creating Users in the database for the logins created  
      User user1 = new User(db, "User1");  
      user1.Login = "Login1";  
      user1.Create();  
  
      User user2 = new User(db, "User2");  
      user2.Login = "Login2";  
      user2.Create();  
  
      // Creating database permission Sets  
      DatabasePermissionSet dbPermSet = new DatabasePermissionSet(DatabasePermission.AlterAnySchema);  
      dbPermSet.Add(DatabasePermission.AlterAnyUser);  
  
      DatabasePermissionSet dbPermSet2 = new DatabasePermissionSet(DatabasePermission.CreateType);  
      dbPermSet2.Add(DatabasePermission.CreateSchema);  
      dbPermSet2.Add(DatabasePermission.CreateTable);  
  
      // Creating Database roles  
      DatabaseRole role1 = new DatabaseRole(db, "Role1");  
      role1.Create();  
  
      DatabaseRole role2 = new DatabaseRole(db, "Role2");  
      role2.Create();  
  
      // Granting Database Permission Sets to Roles  
      db.Grant(dbPermSet, role1.Name);  
      db.Grant(dbPermSet2, role2.Name);  
  
      // Adding members (Users / Roles) to Role  
      role1.AddMember("User1");  
  
      role2.AddMember("User2");  
  
      // Role1 becomes a member of Role2  
      role2.AddMember("Role1");  
  
      // Enumerating through explicit permissions granted to Role1  
      // enumerates all database permissions for the Grantee  
      DatabasePermissionInfo[] dbPermsRole1 = db.EnumDatabasePermissions("Role1");     
      foreach (DatabasePermissionInfo dbp in dbPermsRole1) {  
         Console.WriteLine(dbp.Grantee + " has " + dbp.PermissionType.ToString() + " permission.");  
      }  
      Console.WriteLine(" ");  
   }  
}  
```
  
  
