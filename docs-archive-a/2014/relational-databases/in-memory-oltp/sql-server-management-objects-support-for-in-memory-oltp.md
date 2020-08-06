---
title: 記憶體內部 OLTP 的 SQL Server 管理物件支援 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 2b67292d-6d8e-4016-9063-a97461ffe57a
author: CarlRabeler
ms.author: jroth
ms.openlocfilehash: 6560d0f99eecdb0ece3f46e3407636dd2d143742
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585392"
---
# <a name="sql-server-management-objects-support-for-in-memory-oltp"></a><span data-ttu-id="175b0-102">記憶體中 OLTP 的 SQL Server 管理物件支援</span><span class="sxs-lookup"><span data-stu-id="175b0-102">SQL Server Management Objects Support for In-Memory OLTP</span></span>
  <span data-ttu-id="175b0-103">此主題描述適用於記憶體中 OLTP 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理物件 (SMO) 中的變更。</span><span class="sxs-lookup"><span data-stu-id="175b0-103">This topic describes changes in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO) for In-Memory OLTP.</span></span>  
  
 <span data-ttu-id="175b0-104">下列類型和成員支援 In-Memory OLTP：</span><span class="sxs-lookup"><span data-stu-id="175b0-104">The following types and members support In-Memory OLTP:</span></span>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.DurabilityType>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Database.HasMemoryOptimizedObjects%2A>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Database.MemoryAllocatedToMemoryOptimizedObjectsInKB%2A>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Database.MemoryUsedByMemoryOptimizedObjectsInKB%2A>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.FileGroup.FileGroupType%2A>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.FileGroup.%23ctor%2A>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.FileGroupType>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Index.BucketCount%2A>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.IndexType.NonClusteredHashIndex>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Index.IsMemoryOptimized%2A>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Server.IsXTPSupported%2A>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure.IsNativelyCompiled%2A>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure.IsSchemaBound%2A>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Table.Durability%2A>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Table.IsMemoryOptimized%2A>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedTableType.IsMemoryOptimized%2A>  
  
## <a name="code-sample"></a><span data-ttu-id="175b0-105">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="175b0-105">Code Sample</span></span>  
 <span data-ttu-id="175b0-106">此範例會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="175b0-106">This sample does the following:</span></span>  
  
-   <span data-ttu-id="175b0-107">建立具有記憶體最佳化檔案群組和記憶體最佳化檔案的資料庫。</span><span class="sxs-lookup"><span data-stu-id="175b0-107">Creates a database with memory-optimized filegroup and memory-optimized file.</span></span>  
  
-   <span data-ttu-id="175b0-108">建立持久性記憶體最佳化資料表，其中含有主索引鍵、非叢集索引及非叢集雜湊索引。</span><span class="sxs-lookup"><span data-stu-id="175b0-108">Creates a durable memory-optimized table with a primary key, nonclustered index, and a nonclustered hash index.</span></span>  
  
-   <span data-ttu-id="175b0-109">建立資料行及索引。</span><span class="sxs-lookup"><span data-stu-id="175b0-109">Creates columns and indexes.</span></span>  
  
-   <span data-ttu-id="175b0-110">建立使用者定義的記憶體最佳化資料表類型。</span><span class="sxs-lookup"><span data-stu-id="175b0-110">Creates a user-defined memory-optimized table type.</span></span>  
  
-   <span data-ttu-id="175b0-111">建立原生編譯的預存程序。</span><span class="sxs-lookup"><span data-stu-id="175b0-111">Creates a natively compiled stored procedure.</span></span>  
  
 <span data-ttu-id="175b0-112">這個範例需要參考下列組件：</span><span class="sxs-lookup"><span data-stu-id="175b0-112">This sample needs to reference the following assemblies:</span></span>  
  
-   <span data-ttu-id="175b0-113">Microsoft.SqlServer.Smo.dll</span><span class="sxs-lookup"><span data-stu-id="175b0-113">Microsoft.SqlServer.Smo.dll</span></span>  
  
-   <span data-ttu-id="175b0-114">Microsoft.SqlServer.Management.Sdk.Sfc.dll</span><span class="sxs-lookup"><span data-stu-id="175b0-114">Microsoft.SqlServer.Management.Sdk.Sfc.dll</span></span>  
  
-   <span data-ttu-id="175b0-115">Microsoft.SqlServer.ConnectionInfo.dll</span><span class="sxs-lookup"><span data-stu-id="175b0-115">Microsoft.SqlServer.ConnectionInfo.dll</span></span>  
  
-   <span data-ttu-id="175b0-116">Microsoft.SqlServer.SqlEnum.dll</span><span class="sxs-lookup"><span data-stu-id="175b0-116">Microsoft.SqlServer.SqlEnum.dll</span></span>  
  
```sql  
using Microsoft.SqlServer.Management.Smo;  
using System;  
  
public class A {  
   static void Main(string[] args) {  
      Server server = new Server("(local)");  
  
      // Create a database with memory-optimized filegroup and memory-optimized file  
      Database db = new Database(server, "MemoryOptimizedDatabase");  
      db.Create();  
      FileGroup fg = new FileGroup(db, "memOptFilegroup", FileGroupType.MemoryOptimizedDataFileGroup);  
      db.FileGroups.Add(fg);  
      fg.Create();  
      // change this path if needed  
      DataFile file = new DataFile(fg, "memOptFile", @"C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\MSSQLmemOptFileName");  
      file.Create();  
  
      // Create a durable memory-optimized table with primary key, nonclustered index and nonclustered hash index  
      // Define the table as memory optimized and set the durability  
      Table table = new Table(db, "memOptTable");  
      table.IsMemoryOptimized = true;  
      table.Durability = DurabilityType.SchemaAndData;  
  
      // Create columns  
      Column col1 = new Column(table, "col1", DataType.Int);  
      col1.Nullable = false;  
      table.Columns.Add(col1);  
      Column col2 = new Column(table, "col2", DataType.Float);  
      col2.Nullable = false;  
      table.Columns.Add(col2);  
      Column col3 = new Column(table, "col3", DataType.Decimal(2, 10));  
      col3.Nullable = false;  
      table.Columns.Add(col3);  
  
      // Create indexes  
      Index pk = new Index(table, "PK_memOptTable");  
      pk.IndexType = IndexType.NonClusteredIndex;  
      pk.IndexKeyType = IndexKeyType.DriPrimaryKey;  
      pk.IndexedColumns.Add(new IndexedColumn(pk, col1.Name));  
      table.Indexes.Add(pk);  
  
      Index ixNonClustered = new Index(table, "ix_nonClustered");  
      ixNonClustered.IndexType = IndexType.NonClusteredIndex;  
      ixNonClustered.IndexKeyType = IndexKeyType.None;  
      ixNonClustered.IndexedColumns.Add(new IndexedColumn(ixNonClustered, col2.Name));  
      table.Indexes.Add(ixNonClustered);  
  
      Index ixNonClusteredHash = new Index(table, "ix_nonClustered_Hash");  
      ixNonClusteredHash.IndexType = IndexType.NonClusteredHashIndex;  
      ixNonClusteredHash.IndexKeyType = IndexKeyType.None;  
      ixNonClusteredHash.BucketCount = 1024;  
      ixNonClusteredHash.IndexedColumns.Add(new IndexedColumn(ixNonClusteredHash, col3.Name));  
      table.Indexes.Add(ixNonClusteredHash);  
  
      table.Create();  
  
      // Create a user-defined memory-optimized table type  
      UserDefinedTableType uDTT = new UserDefinedTableType(db, "memOptUDTT");  
      uDTT.IsMemoryOptimized = true;  
  
      // Add columns  
      Column udTTCol1 = new Column(uDTT, "udtCol1", DataType.Int);  
      udTTCol1.Nullable = false;  
      uDTT.Columns.Add(udTTCol1);  
      Column udTTCol2 = new Column(uDTT, "udtCol2", DataType.Float);  
      udTTCol2.Nullable = false;  
      uDTT.Columns.Add(udTTCol2);  
      Column udTTCol3 = new Column(uDTT, "udtCol3", DataType.Decimal(2, 10));  
      udTTCol3.Nullable = false;  
      uDTT.Columns.Add(udTTCol3);  
  
      // Add index  
      Index ix = new Index(uDTT, "IX_UDT");  
      ix.IndexType = IndexType.NonClusteredHashIndex;  
      ix.BucketCount = 1024;  
      ix.IndexKeyType = IndexKeyType.DriPrimaryKey;  
      ix.IndexedColumns.Add(new IndexedColumn(ix, udTTCol1.Name));  
      uDTT.Indexes.Add(ix);  
  
      uDTT.Create();  
  
      // Create a natively compiled stored procedure  
      StoredProcedure sProc = new StoredProcedure(db, "nCSProc");  
      sProc.TextMode = false;  
      sProc.TextBody = "--Type body here";  
      sProc.IsNativelyCompiled = true;  
      sProc.IsSchemaBound = true;  
      sProc.ExecutionContext = ExecutionContext.Owner;  
      sProc.Create();  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="175b0-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="175b0-117">See Also</span></span>  
 [<span data-ttu-id="175b0-118">記憶體中 OLTP 的 SQL Server 支援</span><span class="sxs-lookup"><span data-stu-id="175b0-118">SQL Server Support for In-Memory OLTP</span></span>](sql-server-support-for-in-memory-oltp.md)  
  
  
