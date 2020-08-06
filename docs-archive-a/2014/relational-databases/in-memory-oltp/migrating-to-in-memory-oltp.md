---
title: 移轉至記憶體內部 OLTP | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 405cdac5-a0d4-47a4-9180-82876b773b82
author: rothja
ms.author: jroth
ms.openlocfilehash: ed764ce52d41d76667213b846cec51b26f634a27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709453"
---
# <a name="migrating-to-in-memory-oltp"></a><span data-ttu-id="503ae-102">移轉至 In-Memory OLTP</span><span class="sxs-lookup"><span data-stu-id="503ae-102">Migrating to In-Memory OLTP</span></span>
  <span data-ttu-id="503ae-103">本節討論如何將資料庫物件移轉為使用記憶體中 OLTP。</span><span class="sxs-lookup"><span data-stu-id="503ae-103">This section discusses how to migrate database objects to use In-Memory OLTP.</span></span>  
  
-   [<span data-ttu-id="503ae-104">判斷是否應將資料表或預存程序移植至記憶體內部 OLTP</span><span class="sxs-lookup"><span data-stu-id="503ae-104">Determining if a Table or Stored Procedure Should Be Ported to In-Memory OLTP</span></span>](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)  
  
-   [<span data-ttu-id="503ae-105">記憶體最佳化 Advisor</span><span class="sxs-lookup"><span data-stu-id="503ae-105">Memory Optimization Advisor</span></span>](memory-optimization-advisor.md)  
  
-   [<span data-ttu-id="503ae-106">原生編譯 Advisor</span><span class="sxs-lookup"><span data-stu-id="503ae-106">Native Compilation Advisor</span></span>](native-compilation-advisor.md)  
  
-   [<span data-ttu-id="503ae-107">記憶體中的 OLTP 不支援 Transact-SQL 建構</span><span class="sxs-lookup"><span data-stu-id="503ae-107">Transact-SQL Constructs Not Supported by In-Memory OLTP</span></span>](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
-   [<span data-ttu-id="503ae-108">在記憶體最佳化資料表中實作 LOB 資料行</span><span class="sxs-lookup"><span data-stu-id="503ae-108">Implementing LOB Columns in a Memory-Optimized Table</span></span>](../../database-engine/implementing-lob-columns-in-a-memory-optimized-table.md)  
  
-   [<span data-ttu-id="503ae-109">在記憶體最佳化資料表中實作 SQL_VARIANT</span><span class="sxs-lookup"><span data-stu-id="503ae-109">Implementing SQL_VARIANT in a Memory-Optimized Table</span></span>](implementing-sql-variant-in-a-memory-optimized-table.md)  
  
-   [<span data-ttu-id="503ae-110">原生編譯預存程序的移轉問題</span><span class="sxs-lookup"><span data-stu-id="503ae-110">Migration Issues for Natively Compiled Stored Procedures</span></span>](migration-issues-for-natively-compiled-stored-procedures.md)  
  
-   [<span data-ttu-id="503ae-111">移轉計算資料行</span><span class="sxs-lookup"><span data-stu-id="503ae-111">Migrating Computed Columns</span></span>](migrating-computed-columns.md)  
  
-   [<span data-ttu-id="503ae-112">移轉觸發程序</span><span class="sxs-lookup"><span data-stu-id="503ae-112">Migrating Triggers</span></span>](migrating-triggers.md)  
  
-   [<span data-ttu-id="503ae-113">跨資料庫查詢</span><span class="sxs-lookup"><span data-stu-id="503ae-113">Cross-Database Queries</span></span>](cross-database-queries.md)  
  
-   [<span data-ttu-id="503ae-114">合併 Check 和外部索引鍵條件約束</span><span class="sxs-lookup"><span data-stu-id="503ae-114">Migrating Check and Foreign Key Constraints</span></span>](../../database-engine/migrating-check-and-foreign-key-constraints.md)  
  
-   [<span data-ttu-id="503ae-115">在記憶體最佳化資料表中實作 IDENTITY</span><span class="sxs-lookup"><span data-stu-id="503ae-115">Implementing IDENTITY in a Memory-Optimized Table</span></span>](implementing-identity-in-a-memory-optimized-table.md)  
  
 <span data-ttu-id="503ae-116">如需移轉方法的資訊，請參閱 [In-Memory OLTP - 一般工作負載模式和移轉考量](https://msdn.microsoft.com/library/dn673538.aspx)。</span><span class="sxs-lookup"><span data-stu-id="503ae-116">For information about migration methodologies, see [In-Memory OLTP - Common Workload Patterns and Migration Considerations](https://msdn.microsoft.com/library/dn673538.aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="503ae-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="503ae-117">See Also</span></span>  
 <span data-ttu-id="503ae-118">[記憶體內部 OLTP &#40;記憶體內部最佳化&#41;](in-memory-oltp-in-memory-optimization.md) </span><span class="sxs-lookup"><span data-stu-id="503ae-118">[In-Memory OLTP &#40;In-Memory Optimization&#41;](in-memory-oltp-in-memory-optimization.md) </span></span>  
 [<span data-ttu-id="503ae-119">估計記憶體最佳化資料表的記憶體需求</span><span class="sxs-lookup"><span data-stu-id="503ae-119">Estimate Memory Requirements for Memory-Optimized Tables</span></span>](memory-optimized-tables.md)  
  
  
