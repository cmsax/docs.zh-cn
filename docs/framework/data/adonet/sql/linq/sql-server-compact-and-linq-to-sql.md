---
title: SQL Server Compact 与 LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: 74b8a7a6dfc9a4050dbba9a8c2f6969dba42656c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355781"
---
# <a name="sql-server-compact-and-linq-to-sql"></a>SQL Server Compact 与 LINQ to SQL
SQL Server Compact 是随 Visual Studio 一起安装的默认数据库。 有关详细信息，请参阅[PAVE 通过使用 SQL Server Compact (Visual Studio)](http://msdn.microsoft.com/library/13320dd1-94e5-4077-bf76-8df253695ccc)。  
  
 本主题概述了在用法、 配置、 功能集和作用域的关键差异[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]支持。  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a>SQL Server Compact 相对于 LINQ to SQL 的特性  
 默认情况下，SQL Server Compact 为所有 Visual Studio 版本，安装，因此用于在开发计算机上可用[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]。 但是部署的应用程序使用 SQL Server Compact 和[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]不同于 SQL Server 应用程序。 SQL Server Compact 不是 .NET Framework 的一部分，因此必须与应用程序一起打包或单独从 Microsoft 网站下载。  
  
 请注意下列特性：  
  
-   SQL Server Compact 打包为可直接对数据库文件（扩展名为 .sdf）使用的 DLL。  
  
-   在与客户端应用程序相同的进程中运行的是 SQL Server Compact。 因此，与 SQL Server Compact 通信的效率可能大大高于与 SQL Server 通信。 另一方面，SQL Server Compact 确实需要带来开销的托管和非托管代码之间的互操作性。  
  
-   SQL Server Compact DLL 的大小很小。 这一特征减小了应用程序的总大小。  
  
-   [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 运行时和 SQLMetal 命令行工具支持 SQL Server Compact。  
  
-   [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] 不支持 SQL Server Compact。  
  
## <a name="feature-set"></a>功能集  
 在可能会影响以下方面中，SQL Server Compact 功能集是 SQL server 功能集相比要简单得[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]应用程序：  
  
-   SQL Server Compact 不支持存储过程或视图。  
  
-   SQL Server Compact 仅支持部分数据类型和 SQL 函数。  
  
-   SQL Server Compact 仅支持部分 SQL 构造。  
  
-   SQL Server Compact 仅提供具有最基本功能的优化器。 有些查询可能会超时。  
  
-   SQL Server Compact 不支持部分信任。  
  
## <a name="see-also"></a>请参阅  
 [参考](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
