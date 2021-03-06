---
title: "SQL XML 列值"
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
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c31ec6ae2b50870da7b999e20cd8ae44f1d42e03
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="sql-xml-column-values"></a>SQL XML 列值
[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 支持 `xml` 数据类型，开发人员可以使用 <xref:System.Data.SqlClient.SqlCommand> 类的标准行为检索包括此类型的结果集。 `xml` 列可以像任意列一样进行检索（例如检索到 <xref:System.Data.SqlClient.SqlDataReader> 中），但是如果要以 XML 的形式使用列内容，必须使用 <xref:System.Xml.XmlReader>。  
  
## <a name="example"></a>示例  
 以下控制台应用程序选择两个行，每个包含`xml`列中，从**Sales.Store**表中**AdventureWorks**数据库到<xref:System.Data.SqlClient.SqlDataReader>实例。 对于每一行，`xml` 列的值使用 <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> 的 <xref:System.Data.SqlClient.SqlDataReader> 方法读取。 该值存储在 <xref:System.Xml.XmlReader> 中。 注意，如果要将内容设置为 <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> 变量，必须使用 <xref:System.Data.IDataRecord.GetValue%2A> 方法，而不要使用 <xref:System.Data.SqlTypes.SqlXml> 方法；<xref:System.Data.IDataRecord.GetValue%2A> 以字符串的形式返回 `xml` 列的值。  
  
> [!NOTE]
>  **AdventureWorks**示例数据库未安装默认情况下，当你安装时[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]。 可以通过运行 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 安装程序来安装它。  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a>请参阅  
 <xref:System.Data.SqlTypes.SqlXml>  
 [SQL Server 中的 XML 数据](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 [ADO.NET 托管提供程序和数据集开发人员中心](http://go.microsoft.com/fwlink/?LinkId=217917)
