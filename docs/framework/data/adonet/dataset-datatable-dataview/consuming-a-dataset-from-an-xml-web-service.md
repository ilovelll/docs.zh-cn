---
title: "通过 XML Web 服务使用数据集"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 316bebfec652987351e64368c3b7c0155011fe8e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/19/2018
---
# <a name="consuming-a-dataset-from-an-xml-web-service"></a>通过 XML Web 服务使用数据集
<xref:System.Data.DataSet> 是用断开式设计来构建的，其部分目的是为了便于通过 Internet 来传输数据。 **数据集**在于它可以被指定为的输入或输出而无需任何其他编码的 XML Web 服务所需的内容流处理所显示"可序列化"**数据集**从 XML Web 服务为客户端以及反向。 **数据集**隐式转换为使用 DiffGram 格式的 XML 流，通过网络发送和从 XML 流作为然后重新构造**数据集**在接收端。 它为你使用 XML Web services 传输和返回关系数据提供了非常简单而灵活的方法。 有关 DiffGram 格式的详细信息，请参阅[Diffgram](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)。  
  
 下面的示例演示如何创建 XML Web 服务和客户端使用**数据集**传输关系数据 （包括修改后的数据） 和任何将更新解析回原始数据源。  
  
> [!NOTE]
>  我们建议你在创建 XML Web services 时，应始终考虑到安全问题。 有关保护的 XML Web 服务的信息，请参阅[保护 XML 创建使用 ASP.NET Web 服务](http://msdn.microsoft.com/library/354b2ab1-2782-4542-b32a-dc560178b90c)。  
  
### <a name="to-create-an-xml-web-service-that-returns-and-consumes-a-dataset"></a>创建返回和使用 DataSet 的 XML Web services  
  
1.  创建 XML Web services。  
  
     在示例中，XML Web 服务创建返回数据，在这种情况下从客户列表**Northwind**数据库，并接收**数据集**更新的数据，该 XML Web 服务解析回原始数据源。  
  
     XML Web 服务公开两个方法： **GetCustomers**，则返回的客户，列表和**UpdateCustomers**、 将更新解析回数据源。 XML Web services 存储在 Web 服务器上名为 DataSetSample.asmx 的文件中。 下面的代码概括了 DataSetSample.asmx 的内容。  
  
    ```vb  
    <% @ WebService Language = "vb" Class = "Sample" %>  
    Imports System  
    Imports System.Data  
    Imports System.Data.SqlClient  
    Imports System.Web.Services  
  
    <WebService(Namespace:="http://microsoft.com/webservices/")> _  
    Public Class Sample  
  
    Public connection As SqlConnection = New SqlConnection("Data Source=(local);Integrated Security=SSPI;Initial Catalog=Northwind")  
  
      <WebMethod( Description := "Returns Northwind Customers", EnableSession := False )> _  
      Public Function GetCustomers() As DataSet  
        Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
          "SELECT CustomerID, CompanyName FROM Customers", connection)  
  
        Dim custDS As DataSet = New DataSet()  
        adapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
        adapter.Fill(custDS, "Customers")  
  
        Return custDS  
      End Function  
  
      <WebMethod( Description := "Updates Northwind Customers", EnableSession := False )> _  
      Public Function UpdateCustomers(custDS As DataSet) As DataSet  
        Dim adapter As SqlDataAdapter = New SqlDataAdapter()  
  
        adapter.InsertCommand = New SqlCommand( _  
          "INSERT INTO Customers (CustomerID, CompanyName) " & _  
          "Values(@CustomerID, @CompanyName)", connection)  
        adapter.InsertCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        adapter.InsertCommand.Parameters.Add( _  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
  
        adapter.UpdateCommand = New SqlCommand( _  
          "UPDATE Customers Set CustomerID = @CustomerID, " & _  
          "CompanyName = @CompanyName WHERE CustomerID = " & _  
          @OldCustomerID", connection)  
        adapter.UpdateCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        adapter.UpdateCommand.Parameters.Add( _  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
  
        Dim parameter As SqlParameter = _  
          adapter.UpdateCommand.Parameters.Add( _  
          "@OldCustomerID", SqlDbType.NChar, 5, "CustomerID")  
        parameter.SourceVersion = DataRowVersion.Original  
  
        adapter.DeleteCommand = New SqlCommand( _  
          "DELETE FROM Customers WHERE CustomerID = @CustomerID", _  
          connection)  
        parameter = adapter.DeleteCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        parameter.SourceVersion = DataRowVersion.Original  
  
        adapter.Update(custDS, "Customers")  
  
        Return custDS  
      End Function  
    End Class  
    ```  
  
    ```csharp  
    <% @ WebService Language = "C#" Class = "Sample" %>  
    using System;  
    using System.Data;  
    using System.Data.SqlClient;  
    using System.Web.Services;  
  
    [WebService(Namespace="http://microsoft.com/webservices/")]  
    public class Sample  
    {  
      public SqlConnection connection = new SqlConnection("Data Source=(local);Integrated Security=SSPI;Initial Catalog=Northwind");  
  
      [WebMethod( Description = "Returns Northwind Customers", EnableSession = false )]  
      public DataSet GetCustomers()  
      {  
        SqlDataAdapter adapter = new SqlDataAdapter(  
          "SELECT CustomerID, CompanyName FROM Customers", connection);  
  
        DataSet custDS = new DataSet();  
        adapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
        adapter.Fill(custDS, "Customers");  
  
        return custDS;  
      }  
  
      [WebMethod( Description = "Updates Northwind Customers",  
        EnableSession = false )]  
      public DataSet UpdateCustomers(DataSet custDS)  
      {  
        SqlDataAdapter adapter = new SqlDataAdapter();  
  
        adapter.InsertCommand = new SqlCommand(  
          "INSERT INTO Customers (CustomerID, CompanyName) " +  
          "Values(@CustomerID, @CompanyName)", connection);  
        adapter.InsertCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        adapter.InsertCommand.Parameters.Add(  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName");  
  
        adapter.UpdateCommand = new SqlCommand(  
          "UPDATE Customers Set CustomerID = @CustomerID, " +  
          "CompanyName = @CompanyName WHERE CustomerID = " +  
          "@OldCustomerID", connection);  
        adapter.UpdateCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        adapter.UpdateCommand.Parameters.Add(  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName");  
        SqlParameter parameter = adapter.UpdateCommand.Parameters.Add(  
          "@OldCustomerID", SqlDbType.NChar, 5, "CustomerID");  
        parameter.SourceVersion = DataRowVersion.Original;  
  
        adapter.DeleteCommand = new SqlCommand(  
        "DELETE FROM Customers WHERE CustomerID = @CustomerID",  
         connection);  
        parameter = adapter.DeleteCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        parameter.SourceVersion = DataRowVersion.Original;  
  
        adapter.Update(custDS, "Customers");  
  
        return custDS;  
      }  
    }  
    ```  
  
     在典型方案中， **UpdateCustomers**方法，则会写入来捕获开放式并发冲突。 为了简单起见，以上示例没有包含此方法。 有关开放式并发的详细信息，请参阅[开放式并发](../../../../../docs/framework/data/adonet/optimistic-concurrency.md)。  
  
2.  创建 XML Web services 代理。  
  
     XML Web services 的客户端将需要通过 SOAP 代理来使用公开的方法。 可以使用 Visual Studio 生成此代理。 通过从 Visual Studio 中设置对现有 Web 服务的 Web 引用，此步骤中所述的所有行为均将透明地发生。 如果要自己创建代理类，请继续阅读本讨论。 但是，在大多数情况下，使用 Visual Studio 足以为客户端应用程序创建代理类。  
  
     代理可以使用 Web 服务描述语言工具来创建。 例如，如果 URL http://myserver/data/DataSetSample.asmx 处公开 XML Web 服务时，发出如下命令创建的命名空间的 Visual Basic.NET 代理**WebData.DSSample**并将其存储在文件中sample.vb 中。  
  
    ```  
    wsdl /l:VB /out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     若要在文件 sample.cs 中创建一个 C# 代理，请发出以下命令。  
  
    ```  
    wsdl /l:CS /out:sample.cs http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     然后，可以将该代理编译为库并导入 XML Web services 客户端。 若要将 sample.vb 中存储的 Visual Basic .NET 代理代码编译为 sample.dll，请发出以下命令。  
  
    ```  
    vbc /t:library /out:sample.dll sample.vb /r:System.dll /r:System.Web.Services.dll /r:System.Data.dll /r:System.Xml.dll  
    ```  
  
     若要将 sample.cs 中存储的 C# 代理代码编译为 sample.dll，请发出以下命令。  
  
    ```  
    csc /t:library /out:sample.dll sample.cs /r:System.dll /r:System.Web.Services.dll /r:System.Data.dll /r:System.Xml.dll  
    ```  
  
3.  创建 XML Web services 客户端。  
  
     如果你想要使用 Visual Studio 为你生成的 Web 服务代理类，只需创建客户端项目中，并且，在解决方案资源管理器窗口中，右键单击项目，单击**添加 Web 引用**，并选择从 Web 服务（这可能需要提供 Web 服务终结点地址，如果 Web 服务不在当前解决方案中，或在当前计算机上可用。） 的可用 Web 服务的列表如果自己创建 XML Web services 代理（按照前面的步骤所述），可以将其导入客户端代码并使用 XML Web services 方法。 下面的示例代码导入该代理库，调用**GetCustomers**来获取客户列表，添加新客户，然后返回**数据集**的更新的**UpdateCustomers**.  
  
     请注意，该示例将**数据集**返回**DataSet.GetChanges**到**UpdateCustomers**因为仅修改后的行才需要传递给**UpdateCustomers**。 **UpdateCustomers**返回已解析**数据集**，然后，您可以**合并**到现有**数据集**以合并的已解析的更改和从更新任何行错误信息。 以下代码假定你具有使用 Visual Studio 创建的 Web 引用，并且你已重命名为 DsSample 中的 Web 引用**添加 Web 引用**对话框。  
  
    ```vb  
    Imports System  
    Imports System.Data  
  
    Public Class Client  
  
      Public Shared Sub Main()  
        Dim proxySample As New DsSample.Sample ()  ' Proxy object.  
        Dim customersDataSet As DataSet = proxySample.GetCustomers()  
        Dim customersTable As DataTable = _  
          customersDataSet.Tables("Customers")  
  
        Dim rowAs DataRow = customersTable.NewRow()  
        row("CustomerID") = "ABCDE"  
        row("CompanyName") = "New Company Name"  
        customersTable.Rows.Add(row)  
  
        Dim updateDataSet As DataSet = _  
          proxySample.UpdateCustomers(customersDataSet.GetChanges())  
  
        customersDataSet.Merge(updateDataSet)  
        customersDataSet.AcceptChanges()  
      End Sub  
    End Class  
    ```  
  
    ```csharp  
    using System;  
    using System.Data;  
  
    public class Client  
    {  
      public static void Main()  
      {  
        Sample proxySample = new DsSample.Sample();  // Proxy object.  
        DataSet customersDataSet = proxySample.GetCustomers();  
        DataTable customersTable = customersDataSet.Tables["Customers"];  
  
        DataRow row = customersTable.NewRow();  
        row["CustomerID"] = "ABCDE";  
        row["CompanyName"] = "New Company Name";  
        customersTable.Rows.Add(row);  
  
        DataSet updateDataSet = new DataSet();  
  
        updateDataSet =   
          proxySample.UpdateCustomers(customersDataSet.GetChanges());  
  
        customersDataSet.Merge(updateDataSet);  
        customersDataSet.AcceptChanges();  
      }  
    }  
    ```  
  
     如果决定自己创建代理类，必须执行下列额外的步骤。 若要编译该示例，将需要提供已创建的代理库 (sample.dll) 和相关的 .NET 库。 若要编译该示例的 Visual Basic .NET 版本（存储在文件 client.vb 中），请发出以下命令。  
  
    ```  
    vbc client.vb /r:sample.dll /r:System.dll /r:System.Data.dll /r:System.Xml.dll /r:System.Web.Services.dll  
    ```  
  
     若要编译该示例的 C# 版本（存储在文件 client.cs 中），请发出以下命令。  
  
    ```  
    csc client.cs /r:sample.dll /r:System.dll /r:System.Data.dll /r:System.Xml.dll /r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a>请参阅  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 [数据集、数据表和数据视图](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [数据表](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [从 DataAdapter 填充数据集](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 [使用 DataAdapter 更新数据源](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [DataAdapter 参数](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 [Web 服务描述语言工具 (Wsdl.exe)](http://msdn.microsoft.com/library/b9210348-8bc2-4367-8c91-d1a04b403e88)  
 [ADO.NET 托管提供程序和数据集开发人员中心](http://go.microsoft.com/fwlink/?LinkId=217917)
