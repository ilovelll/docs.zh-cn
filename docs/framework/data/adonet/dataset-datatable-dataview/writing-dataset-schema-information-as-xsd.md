---
title: "写入数据集架构信息作为 XSD"
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
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: bea961310c838068a54f15f7b05186ab56721dc2
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="writing-dataset-schema-information-as-xsd"></a>写入数据集架构信息作为 XSD
您可以用 XML 架构定义语言 (XSD) 架构的形式来编写 <xref:System.Data.DataSet> 的架构，以便在 XML 文档中传输包含或不包含相关数据的架构。 XML 架构可以写入文件、 流， <xref:System.Xml.XmlWriter>，或字符串，它可用于生成强类型**数据集**。 有关详细信息强类型**数据集**对象，请参阅[类型化数据集](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)。  
  
 你可以指定如何在 XML 架构中表示表的列使用**ColumnMapping**属性<xref:System.Data.DataColumn>对象。 详细信息，请参阅"将列映射到 XML 元素、 属性和文本"在[以 XML 数据形式编写数据集内容](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)。  
  
 若要写入的架构**数据集**作为 XML 架构，写入文件流，或**XmlWriter**，使用**WriteXmlSchema**方法**数据集**。 **WriteXmlSchema**采用一个参数以指定生成的 XML 架构的目标。 下面的代码示例演示如何编写 XML 架构的**数据集**到通过传递包含文件名的字符串的文件和一个<xref:System.IO.StreamWriter>对象。  
  
```vb  
dataSet.WriteXmlSchema("Customers.xsd")  
```  
  
```csharp  
dataSet.WriteXmlSchema("Customers.xsd");  
```  
  
```vb  
Dim writer As System.IO.StreamWriter = New System.IO.StreamWriter("Customers.xsd")  
dataSet.WriteXmlSchema(writer)  
writer.Close()  
```  
  
```csharp  
System.IO.StreamWriter writer = new System.IO.StreamWriter("Customers.xsd");  
dataSet.WriteXmlSchema(writer);  
writer.Close();  
```  
  
 若要获取的架构**数据集**并将其保存为 XML 架构字符串，请使用**GetXmlSchema**方法，如下面的示例中所示。  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a>请参阅  
 [在数据集中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [以 XML 数据的形式编写数据集内容](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 [类型化数据集](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [数据集、数据表和数据视图](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET 托管提供程序和数据集开发人员中心](http://go.microsoft.com/fwlink/?LinkId=217917)
