---
title: "Verwenden geschachtelter FOR XML-Abfragen in ASP.NET | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-xml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FOR XML-Klausel, geschachtelte FOR XML-Abfragen"
  - "Abfragen [XML in SQL Server], ASP.NET und"
  - "geschachtelten FOR XML-Abfragen in ASP.NET"
  - "ASP.NET [SQL Server]"
ms.assetid: 691ac7dd-afc5-4760-932c-2b1dcd9394ed
caps.latest.revision: 10
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 10
---
# Verwenden geschachtelter FOR XML-Abfragen in ASP.NET
  In diesem Beispiel gibt eine ASP.NET-Anwendung XML-Code an einen Browser zurück, indem sie eine gespeicherte Prozedur in SQL Server ausführt. Die gespeicherte Prozedur generiert mithilfe von geschachtelten Abfragen XML. Eine ähnliche SELECT-Anweisung enthält das Thema [Geschachtelte FOR XML-Abfragen](../../relational-databases/xml/generate-siblings-with-a-nested-auto-mode-query.md). In diesem Beispiel wird eine Möglichkeit veranschaulicht, geschachtelte FOR XML-Abfragen zu verwenden, um elementzentriertes XML in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu generieren.  
  
## Beispiel  
  
```  
CREATE PROC GetSalesOrderInfo AS  
SELECT   
      (SELECT top 2 SalesOrderID, SalesPersonID, CustomerID,  
         (select top 3 SalesOrderID, ProductID, OrderQty, UnitPrice  
           from Sales.SalesOrderDetail  
            WHERE  SalesOrderDetail.SalesOrderID = SalesOrderHeader.SalesOrderID  
            FOR XML AUTO, TYPE)  
      FROM  Sales.SalesOrderHeader  
        WHERE SalesOrderHeader.SalesOrderID = SalesOrder.SalesOrderID  
      for xml auto, type),  
        (SELECT *   
         FROM  (SELECT SalesPersonID, EmployeeID  
              FROM Sales.SalesPerson, HumanResources.Employee  
              WHERE SalesPerson.SalesPersonID = Employee.EmployeeID) As SalesPerson  
         WHERE  SalesPerson.SalesPersonID = SalesOrder.SalesPersonID  
       FOR XML AUTO, TYPE, ELEMENTS)  
FROM (SELECT SalesOrderHeader.SalesOrderID, SalesOrderHeader.SalesPersonID  
      FROM Sales.SalesOrderHeader, Sales.SalesPerson  
      WHERE SalesOrderHeader.SalesPersonID = SalesPerson.SalesPersonID  
     ) as SalesOrder  
ORDER BY SalesOrder.SalesOrderID  
FOR XML AUTO, TYPE  
GO  
```  
  
 Dies ist die ASPX-Anwendung. Sie führt die gespeicherte Prozedur aus und gibt den XML-Code im Browser zurück:  
  
```  
<%@LANGUAGE=C# Debug=true %>  
<%@import Namespace="System.Xml"%>  
<%@import namespace="System.Data.SqlClient" %><%  
Response.Expires = -1;  
Response.ContentType = "text/xml";  
%>  
  
<%  
using(System.Data.SqlClient.SqlConnection c = new System.Data.SqlClient.SqlConnection("Data Source=server;Database=AdventureWorks;Integrated Security=SSPI;"))  
using(System.Data.SqlClient.SqlCommand cmd = c.CreateCommand())  
{  
   cmd.CommandText = "GetSalesOrderInfo";  
   cmd.CommandType = CommandType.StoredProcedure;  
   cmd.Connection.Open();  
   System.Xml.XmlReader r = cmd.ExecuteXmlReader();  
   System.Xml.XmlTextWriter w = new System.Xml.XmlTextWriter(Response.Output);  
   w.WriteStartElement("Root");  
   r.MoveToContent();  
   while(! r.EOF)  
   {  
      w.WriteNode(r, true);  
   }  
   w.WriteEndElement();  
   w.Flush();  
}  
%>  
```  
  
##### So testen Sie die Anwendung  
  
1.  Erstellen Sie die gespeicherte Prozedur in der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]-Datenbank.  
  
2.  Speichern Sie die ASPX-Anwendung in c:\inetpub\wwwroot-Verzeichnis (GetSalesOrderInfo.aspx).  
  
3.  Führen Sie die Anwendung aus (http://server/GetSalesOrderInfo.aspx).  
  
## Siehe auch  
 [Verwenden von geschachtelten FOR XML-Abfragen](../../relational-databases/xml/use-nested-for-xml-queries.md)  
  
  