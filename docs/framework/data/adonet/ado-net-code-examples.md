---
title: ADO.NET 代码示例
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c119657a-9ce6-4940-91e4-ac1d5f0d9584
ms.openlocfilehash: 5b34f93348c43a26f603140f2393389e1bce107a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759135"
---
# <a name="adonet-code-examples"></a>ADO.NET 代码示例
本主题中的代码列表演示如何使用下面的 ADO.NET 技术从数据库中检索数据：

- ADO.NET 数据提供程序：

  - [SqlClient](#sqlclient) (`System.Data.SqlClient`)

  - [OleDb](#oledb) (`System.Data.OleDb`)

  - [Odbc](#odbc) (`System.Data.Odbc`)

  - [OracleClient](#oracleclient) (`System.Data.OracleClient`)

- ADO.NET 实体框架：

  - [LINQ to Entities](#linq-to-entities)

  - [类型化的 ObjectQuery](#typed-objectquery)

  - [EntityClient](#entityclient) (`System.Data.EntityClient`)

- [LINQ to SQL](#linq-to-sql)

## <a name="adonet-data-provider-examples"></a>ADO.NET 数据提供程序示例
以下代码列表演示如何使用 ADO.NET 数据提供程序从数据库中检索数据。 数据在一个 `DataReader` 中返回。 有关详细信息，请参阅[使用 DataReader 检索数据](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)。

### <a name="sqlclient"></a>SqlClient
此示例中的代码假定你可以连接到`Northwind`Microsoft SQL Server 上的示例数据库。 在此情形 5 中，示例代码创建一个 <xref:System.Data.SqlClient.SqlCommand> 以从 Products 表中选择行，并添加 <xref:System.Data.SqlClient.SqlParameter> 来将结果限制为其 UnitPrice 大于指定参数值的行。 <xref:System.Data.SqlClient.SqlConnection>在内部打开`using`块，这将确保关闭和释放在代码退出时会资源。 示例代码使用 <xref:System.Data.SqlClient.SqlDataReader> 执行命令，并在控制台窗口中显示结果。

 [!code-csharp[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/VB/source.vb#1)]

### <a name="oledb"></a>OleDb
此示例中的代码假定您可以连接到 Microsoft Access Northwind 示例数据库。 在此情形 5 中，示例代码创建一个 <xref:System.Data.OleDb.OleDbCommand> 以从 Products 表中选择行，并添加 <xref:System.Data.OleDb.OleDbParameter> 来将结果限制为其 UnitPrice 大于指定参数值的行。 <xref:System.Data.OleDb.OleDbConnection> 在 `using` 块内打开，这将确保在代码退出时会关闭和释放资源。 示例代码使用 <xref:System.Data.OleDb.OleDbDataReader> 执行命令，并在控制台窗口中显示结果。

 [!code-csharp[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/VB/source.vb#1)]

### <a name="odbc"></a>Odbc
此示例中的代码假定您可以连接到 Microsoft Access Northwind 示例数据库。 在此情形 5 中，示例代码创建一个 <xref:System.Data.Odbc.OdbcCommand> 以从 Products 表中选择行，并添加 <xref:System.Data.Odbc.OdbcParameter> 来将结果限制为其 UnitPrice 大于指定参数值的行。 <xref:System.Data.Odbc.OdbcConnection>在内部打开`using`块，这将确保关闭和释放在代码退出时会资源。 示例代码使用 <xref:System.Data.Odbc.OdbcDataReader> 执行命令，并在控制台窗口中显示结果。

[!code-csharp[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/CS/source.cs#1)] 
[!code-vb[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/VB/source.vb#1)] 

### <a name="oracleclient"></a>OracleClient
此示例中的代码假定已建立与 Oracle 服务器上的 DEMO.CUSTOMER 的连接。 您还必须添加对 System.Data.OracleClient.dll 的引用。 示例代码在 <xref:System.Data.OracleClient.OracleDataReader> 中返回数据。

 [!code-csharp[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/VB/source.vb#1)]

## <a name="entity-framework-examples"></a>实体框架示例
以下代码列表演示如何通过查询实体数据模型 (EDM) 中的实体来从数据源检索数据。 这些示例使用[Northwind 模型](http://msdn.microsoft.com/74521f8c-e974-48cb-8858-c08deff52638)。 有关详细信息，请参阅[实体框架概述](../../../../docs/framework/data/adonet/ef/overview.md)。

### <a name="linq-to-entities"></a>LINQ to Entities
此示例中的代码使用 LINQ 查询以 Categories 对象的形式返回数据，这些对象将作为仅包含 CategoryID 和 CategoryName 属性的匿名类型提取。 有关详细信息，请参阅[LINQ to Entities 概述](http://msdn.microsoft.com/86d87a27-c17a-45ac-b28d-72c8500333c6)。

```csharp
using System;
using System.Linq;
using System.Data.Objects;
using NorthwindModel;

class LinqSample
{
    public static void ExecuteQuery()
    {
        using (NorthwindEntities context = new NorthwindEntities())
        {
            try
            {
                var query = from category in context.Categories
                            select new
                            {
                                categoryID = category.CategoryID,
                                categoryName = category.CategoryName
                            };

                foreach (var categoryInfo in query)
                {
                    Console.WriteLine("\t{0}\t{1}",
                        categoryInfo.categoryID, categoryInfo.categoryName);
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex.Message);
            }
        }
    }
}
```

```vb
Option Explicit On
Option Strict On

Imports System
Imports System.Linq
Imports System.Data.Objects
Imports NorthwindModel

Class LinqSample
    Public Shared Sub ExecuteQuery()
        Using context As NorthwindEntities = New NorthwindEntities()
            Try
                Dim query = From category In context.Categories _
                            Select New With _
                            { _
                                .categoryID = category.CategoryID, _
                                .categoryName = category.CategoryName _
                            }

                For Each categoryInfo In query
                    Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                        categoryInfo.categoryID, categoryInfo.categoryName)
                Next
            Catch ex As Exception
                Console.WriteLine(ex.Message)
            End Try
        End Using
    End Sub
End Class
```

### <a name="typed-objectquery"></a>类型化 ObjectQuery
此示例中的代码使用 <xref:System.Data.Objects.ObjectQuery%601> 以 Categories 对象的形式返回数据。 有关详细信息，请参阅[对象查询](http://msdn.microsoft.com/0768033c-876f-471d-85d5-264884349276)。

```csharp
using System;
using System.Data.Objects;
using NorthwindModel;

class ObjectQuerySample
{
    public static void ExecuteQuery()
    {
        using (NorthwindEntities context = new NorthwindEntities())
        {
            ObjectQuery<Categories> categoryQuery = context.Categories;

            foreach (Categories category in 
                categoryQuery.Execute(MergeOption.AppendOnly))
            {
                Console.WriteLine("\t{0}\t{1}",
                    category.CategoryID, category.CategoryName);
            }
        }
    }
}
```

```vb
Option Explicit On
Option Strict On

Imports System
Imports System.Data.Objects
Imports NorthwindModel

Class ObjectQuerySample
    Public Shared Sub ExecuteQuery()
        Using context As NorthwindEntities = New NorthwindEntities()
            Dim categoryQuery As ObjectQuery(Of Categories) = context.Categories

            For Each category As Categories In _
                categoryQuery.Execute(MergeOption.AppendOnly)
                Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                    category.CategoryID, category.CategoryName)
            Next
        End Using
    End Sub
End Class
```

### <a name="entityclient"></a>EntityClient
此示例中的代码使用 <xref:System.Data.EntityClient.EntityCommand> 来执行实体 SQL 查询。 此查询会返回表示 Categories 实体类型的实例的记录的列表。 <xref:System.Data.EntityClient.EntityDataReader> 用于访问结果集中的数据记录。 有关详细信息，请参阅[用于实体框架的 EntityClient 提供程序](../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)。

```csharp
using System;
using System.Data;
using System.Data.Common;
using System.Data.EntityClient;
using NorthwindModel;

class EntityClientSample
{
    public static void ExecuteQuery()
    {
        string queryString =
            @"SELECT c.CategoryID, c.CategoryName 
                FROM NorthwindEntities.Categories AS c";

        using (EntityConnection conn =
            new EntityConnection("name=NorthwindEntities"))
        {
            try
            {
                conn.Open();
                using (EntityCommand query = new EntityCommand(queryString, conn))
                {
                    using (DbDataReader rdr = 
                        query.ExecuteReader(CommandBehavior.SequentialAccess))
                    {
                        while (rdr.Read())
                        {
                            Console.WriteLine("\t{0}\t{1}", rdr[0], rdr[1]);
                        }
                    }
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex.Message);
            }
        }
    }
}
```

```vb
Option Explicit On
Option Strict On

Imports System
Imports System.Data
Imports System.Data.Common
Imports System.Data.EntityClient
Imports NorthwindModel

Class EntityClientSample
    Public Shared Sub ExecuteQuery()
        Dim queryString As String = _
            "SELECT c.CategoryID, c.CategoryName " & _
                "FROM NorthwindEntities.Categories AS c"

        Using conn As EntityConnection = _
            New EntityConnection("name=NorthwindEntities")

            Try
                conn.Open()
                Using query As EntityCommand = _
                New EntityCommand(queryString, conn)
                    Using rdr As DbDataReader = _
                        query.ExecuteReader(CommandBehavior.SequentialAccess)
                        While rdr.Read()
                            Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                                              rdr(0), rdr(1))
                        End While
                    End Using
                End Using
            Catch ex As Exception
                Console.WriteLine(ex.Message)
            End Try
        End Using 
    End Sub
End Class
```

## <a name="linq-to-sql"></a>LINQ to SQL
此示例中的代码使用 LINQ 查询以 Categories 对象的形式返回数据，这些对象将作为仅包含 CategoryID 和 CategoryName 属性的匿名类型提取。 此示例基于 Northwind 数据上下文。 有关详细信息，请参阅[入门](../../../../docs/framework/data/adonet/sql/linq/getting-started.md)。

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Northwind;

    class LinqSqlSample
    {
        public static void ExecuteQuery()
        {
            using (NorthwindDataContext db = new NorthwindDataContext())
            {
                try
                {
                    var query = from category in db.Categories
                                select new
                                {
                                    categoryID = category.CategoryID,
                                    categoryName = category.CategoryName
                                };

                    foreach (var categoryInfo in query)
                    {
                        Console.WriteLine("vbTab {0} vbTab {1}",
                            categoryInfo.categoryID, categoryInfo.categoryName);
                    }
                }
                catch (Exception ex)
                {
                    Console.WriteLine(ex.Message);
                }
            }
        }
    }
```

```vb
Option Explicit On
Option Strict On

Imports System
Imports System.Collections.Generic
Imports System.Linq
Imports System.Text
Imports Northwind

Class LinqSqlSample
    Public Shared Sub ExecuteQuery()
        Using db As NorthwindDataContext = New NorthwindDataContext()
            Try
                Dim query = From category In db.Categories _
                                Select New With _
                                { _
                                    .categoryID = category.CategoryID, _
                                    .categoryName = category.CategoryName _
                                }

                For Each categoryInfo In query
                    Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                            categoryInfo.categoryID, categoryInfo.categoryName)
                Next
            Catch ex As Exception
                Console.WriteLine(ex.Message)
            End Try
            End Using 
    End Sub
End Class
```

## <a name="see-also"></a>请参阅
 [ADO.NET 概述](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [在 ADO.NET 中检索和修改数据](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [创建数据应用程序](http://msdn.microsoft.com/library/ab334d5f-4f49-4346-bce0-3325d6130b3e)  
 [查询实体数据模型 （实体框架任务）](http://msdn.microsoft.com/187f1caa-e4d3-4e31-bd99-5d5c2b329c77)  
 [如何： 执行返回匿名类型的对象的查询](http://msdn.microsoft.com/3b264025-e911-4d73-90ce-992d2b9d189d)  
 [ADO.NET 托管提供程序和数据集开发人员中心](http://go.microsoft.com/fwlink/?LinkId=217917)  
