---
title: 事务支持
ms.date: 03/30/2017
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
ms.openlocfilehash: ff4d65c37e2d7f76c8c9f0de1de9717c8dca7b27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="transaction-support"></a>事务支持
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 支持三种不同的事务模型。 下文按执行检查的顺序列出了这些模型。  
  
## <a name="explicit-local-transaction"></a>显式本地事务  
 调用 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 时，如果 <xref:System.Data.Linq.DataContext.Transaction%2A> 属性设置为 (`IDbTransaction`) 事务，则在同一事务的上下文中执行 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 调用。  
  
 成功执行事务后，要由您来提交或回滚事务。 与事务对应的连接必须与用于构造 <xref:System.Data.Linq.DataContext> 的连接匹配。 如果使用其他连接，则会引发异常。  
  
## <a name="explicit-distributable-transaction"></a>显式可分发事务  
 可以在活动 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的作用域中调用 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> API（包括但不限于 <xref:System.Transactions.Transaction>）。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 检测到调用是在事务范围中并不会创建一个新的事务。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 此外可以避免这种情况下关闭连接。 您可以在此类事务的上下文中执行查询和 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 操作。  
  
## <a name="implicit-transaction"></a>隐式事务  
 当您调用 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 时，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 会检查此调用是否在 <xref:System.Transactions.Transaction> 的作用域内或者 `Transaction` 属性 (`IDbTransaction`) 是否设置为由用户启动的本地事务。 如果这两个事务均未找到，则 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 启动本地事务 (`IDbTransaction`)，并使用此事务执行所生成的 SQL 命令。 当所有 SQL 命令均已成功执行完毕时，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 提交本地事务并返回。  
  
## <a name="see-also"></a>请参阅  
 [背景信息](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [如何：通过使用事务对数据提交进行分类](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)
