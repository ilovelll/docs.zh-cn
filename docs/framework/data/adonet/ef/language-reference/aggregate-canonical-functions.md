---
title: "聚合规范函数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bcff826-ca90-41b3-a791-04d6ff0e5085
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 4539d73479ed05111f0d59b56403fd98bd311f61
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="aggregate-canonical-functions"></a>聚合规范函数

聚合是缩减一系列输入值（例如，缩减为单个值）的表达式。 聚合通常与 SELECT 表达式的 GROUP BY 子句一起使用，对于可以使用聚合的位置存在一些约束。

下表列出了 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 聚合规范函数。

| 函数 | 描述 |
| -------- | ----------- |
| `Avg(expression)` | 返回非 null 值的平均值。<br><br>**参数**<br><br>`Int32`， `Int64`， `Double`，和`Decimal`。<br><br>**返回值**<br><br>`expression` 的类型。 如果所有输入值均为 `Null` 值，则为 `null`。<br><br>**示例**[!code-csharp [DP EntityServices Concepts#EDM_AVG](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_avg)][!code-sql[DP EntityServices Concepts#EDM_AVG](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_avg)] |
| `BigCount(expression)` | 返回包含 null 值和重复值的聚合的大小。<br><br>**参数**<br><br>任何类型。<br><br>**返回值**<br><br>一个 `Int64`。<br><br>**示例**[!code-csharp [DP EntityServices Concepts#EDM_BIGCOUNT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_bigcount)][!code-sql[DP EntityServices Concepts#EDM_BIGCOUNT](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_bigcount)] |
| `Count(expression)` | 返回包含 null 值和重复值的聚合的大小。<br><br>**参数**<br><br>任何类型。<br><br>**返回值**<br><br>一个 `Int32`。<br><br>**示例**[!code-csharp [DP EntityServices Concepts#EDM_COUNT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_count)][!code-sql[DP EntityServices Concepts#EDM_COUNT](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_count)] |
| `Max(expression)` | 返回非 null 值的最大值。<br><br>**参数**<br><br>`Byte`、`Int16`、`Int32`、`Int64`、`Byte`、`Single`、`Double`、`Decimal`、`DateTime`、`DateTimeOffset`、`Time`、`String`、`Binary`。<br><br>**返回值**<br><br>`expression` 的类型。 如果所有输入值均为 `Null` 值，则为 `null`。<br><br>**示例**[!code-csharp [DP EntityServices Concepts#EDM_MAX](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_max)][!code-sql[DP EntityServices Concepts#EDM_MAX](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_max)] |
| `Min(expression)` | 返回非 null 值的最小值。<br><br>**参数**<br><br>`Byte`、`Int16`、`Int32`、`Int64`、`Byte`、`Single`、`Double`、`Decimal`、`DateTime`、`DateTimeOffset`、`Time`、`String`、`Binary`。<br><br>**返回值**<br><br>`expression` 的类型。 如果所有输入值均为 `Null` 值，则为 `null`。<br><br>**示例**[!code-csharp [DP EntityServices Concepts#EDM_MIN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_min)][!code-sql[DP EntityServices Concepts#EDM_MIN](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_min)] |
| `StDev(expression)` | 返回非 null 值的标准偏差。<br><br>**参数**<br><br>`Int32`、`Int64`、`Double`、`Decimal`。<br><br>**返回值**<br><br>`Double`。 如果所有输入值均为 `Null` 值，则为 `null`。<br><br>**示例**[!code-csharp [DP EntityServices Concepts#EDM_STDEV](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdev)][!code-sql[DP EntityServices Concepts#EDM_STDEV](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdev)] |
| `StDevP(expression)` | 返回所有值的总体标准偏差。<br><br>**参数**<br><br>`Int32`、`Int64`、`Double`、`Decimal`。<br><br>**返回值**<br><br>`Double`。 如果所有输入值均为 `Null` 值，则为 `null`。<br><br>**示例**[!code-csharp [DP EntityServices Concepts#EDM_STDEVP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdevp)][!code-sql[DP EntityServices Concepts#EDM_STDEVP](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdevp)] |
| `Sum(expression)` | 返回非 null 值的总和。<br><br>**参数**<br><br>`Int32`、`Int64`、`Double`、`Decimal`。<br><br>**返回值**<br><br>`Double`。 如果所有输入值均为 `Null` 值，则为 `null`。<br><br>**示例**[!code-csharp [DP EntityServices Concepts#EDM_SUM](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_sum)][!code-sql[DP EntityServices Concepts#EDM_SUM](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_sum)] |
| `Var(expression)` | 返回所有非 Null 值的方差。<br><br>**参数**<br><br>`Int32`、`Int64`、`Double`、`Decimal`。<br><br>**返回值**<br><br>`Double`。 如果所有输入值均为 `Null` 值，则为 `null`。<br><br>**示例**[!code-csharp [DP EntityServices Concepts#EDM_VAR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_var)][!code-sql[DP EntityServices Concepts#EDM_VAR](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_var)] |
| `VarP(expression)` | 返回所有非 Null 值的总体方差。<br><br>**参数**<br><br>`Int32`、`Int64`、`Double`、`Decimal`。<br><br>**返回值**<br><br>`Double`。 如果所有输入值均为 `Null` 值，则为 `null`。<br><br>**示例**[!code-csharp [DP EntityServices Concepts#EDM_VARP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_varp)][!code-sql[DP EntityServices Concepts#EDM_VARP](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_varp)] |

Microsoft SQL 客户端托管提供程序中提供了等效功能。 有关详细信息，请参阅[用于实体框架函数的 SqlClient](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)。

## <a name="collection-based-aggregates"></a>基于集合的聚合

基于集合的聚合（集合函数）针对集合而运行并返回值。 例如如果 ORDERS 是所有订单的集合，则可以计算最早的发货日期，使用以下表达式：

```sql
min(select value o.ShipDate from LOB.Orders as o)
```

将在当前环境名称解析范围内计算基于集合的聚合内的表达式。

## <a name="group-based-aggregates"></a>基于组的聚合

基于组的聚合将按照 GROUP BY 子句定义的方式对组进行计算。 对于结果中的每个组，将使用每个组中的元素作为聚合计算的输入来计算单独的聚合。 当在 select 表达式中使用 group-by 子句时，在投影或 order-by 子句中只存在分组表达式名称、聚合或常量表达式。

以下示例计算每种产品的平均订购数量：

```sql
select p, avg(ol.Quantity) from LOB.OrderLines as ol 
  group by ol.Product as p
```

它是可以在 SELECT 表达式中包含没有显式 group-by 子句基于组的聚合。 在这种情况下，所有元素都视为单个组。 这是等效的指定基于常数的分组。 例如，请看下面的表达式：

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol
```

此表达式等效于以下表达式：

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol group by 1
```

将在 WHERE 子句表达式可见的名称解析范围内计算基于组的聚合中的表达式。

作为 in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]，基于组的聚合也可以指定 ALL 或 DISTINCT 修饰符。 如果指定 DISTINCT 修饰符，则将从聚合输入集合中消除重复项，然后计算聚合。 如果指定 ALL 修饰符（或者未指定修饰符），则不执行重复项消除。  

## <a name="see-also"></a>请参阅

[规范函数](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
