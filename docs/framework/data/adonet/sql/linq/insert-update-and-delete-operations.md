---
title: 插入、更新和删除操作
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26a43a4f-83c9-4732-806d-bb23aad0ff6b
ms.openlocfilehash: 29d87ed22f987a09348cde446d2fd6b11a3c1528
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="insert-update-and-delete-operations"></a>插入、更新和删除操作
在 `Insert` 中执行 `Update`、`Delete` 和 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 操作的方法是：向对象模型中添加对象、更改和移除对象模型中的对象。 默认情况下，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 会将您所做的操作转换成 SQL，然后将这些更改提交至数据库。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 在操作和保持对对象所做更改方面有着最大的灵活性。 实体对象可用（通过查询检索它们或通过重新构造它们）后，就可以像应用程序中的典型对象一样更改实体对象。 也就是说，你可以更改其值、 可以将它们添加到集合中，和从集合中移除它们。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 会跟踪您所做的更改，并且在您调用 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 时就可以将这些更改传回数据库。  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 不支持且无法识别级联删除操作。 如果你想要删除的行有约束的表中，你必须设置`ON DELETE CASCADE`规则在数据库中的外键约束中或使用你自己的代码先删除阻止删除父对象的子对象。 否则会引发异常。 有关详细信息，请参阅[如何： 删除数据库中的行](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md)。  
  
 以下摘录会用到 Northwind 示例数据库中的 `Customer` 和 `Order` 类。 为简洁起见，不显示类定义。  
  
 [!code-csharp[DLinqCRUDOps#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCRUDOps/cs/Program.cs#1)]
 [!code-vb[DLinqCRUDOps#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCRUDOps/vb/Module1.vb#1)]  
  
 当您调用 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 时，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 会自动生成并执行它为将您所做的更改传回数据库而必须具备的 SQL 命令。  
  
> [!NOTE]
>  您可以使用自己的自定义逻辑来重写此行为，这通常是通过存储过程来实现的。 有关详细信息，请参阅[开发人员在重写默认行为中的责任](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)。  
>   
>  使用 Visual Studio 的开发人员可以使用[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]来开发用于此目的的存储的过程。  
  
## <a name="see-also"></a>请参阅  
 [下载示例数据库](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [自定义插入、更新和删除操作](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
