---
title: 创建 AutoIncrement 列
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: 5972d9e3d84a236104e85e17d8df1e9ee7f56122
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="creating-autoincrement-columns"></a>创建 AutoIncrement 列
要确保列值的唯一，可将列值设置为在表中添加新行时自动递增。 若要创建自动递增<xref:System.Data.DataColumn>，将其设置<xref:System.Data.DataColumn.AutoIncrement%2A>到列的属性**true**。 <xref:System.Data.DataColumn>然后开头中定义的值<xref:System.Data.DataColumn.AutoIncrementSeed%2A>属性，并与每个行添加的值**AutoIncrement**列加中定义的值<xref:System.Data.DataColumn.AutoIncrementStep%2A>列属性。  
  
 有关**AutoIncrement**列，我们建议，<xref:System.Data.DataColumn.ReadOnly%2A>属性**DataColumn**设置为**true**。  
  
 以下示例演示了如何创建从值 200 开始并以 3 为增量递增的列。  
  
```vb  
Dim workColumn As DataColumn = workTable.Columns.Add( _  
    "CustomerID", typeof(Int32))  
workColumn.AutoIncrement = true  
workColumn.AutoIncrementSeed = 200  
workColumn.AutoIncrementStep = 3  
```  
  
```csharp  
DataColumn workColumn = workTable.Columns.Add(  
    "CustomerID", typeof(Int32));  
workColumn.AutoIncrement = true;  
workColumn.AutoIncrementSeed = 200;  
workColumn.AutoIncrementStep = 3;  
```  
  
## <a name="see-also"></a>请参阅  
 <xref:System.Data.DataColumn>  
 [数据表架构定义](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [数据表](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [ADO.NET 托管提供程序和数据集开发人员中心](http://go.microsoft.com/fwlink/?LinkId=217917)
