---
title: 使用解譯的 Transact-SQL 存取記憶體最佳化資料表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 92a44d4d-0e53-4fb0-b890-de264c65c95a
author: rothja
ms.author: jroth
ms.openlocfilehash: af4b3ca7731e7ca13e697f43e76ac3cc3cacb4f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598865"
---
# <a name="accessing-memory-optimized-tables-using-interpreted-transact-sql"></a><span data-ttu-id="57319-102">使用解譯的 Transact-SQL 存取記憶體最佳化的資料表</span><span class="sxs-lookup"><span data-stu-id="57319-102">Accessing Memory-Optimized Tables Using Interpreted Transact-SQL</span></span>
  <span data-ttu-id="57319-103">您可以使用任何 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢或 DML 作業 (SELECT、INSERT、UPDATE 或 DELETE)、特定批次以及 SQL 模組 (例如預存程序、資料表值函數、觸發程序和檢視表) 來存取記憶體最佳化的資料表，僅有一些例外狀況。</span><span class="sxs-lookup"><span data-stu-id="57319-103">With only a few exceptions, you can access memory-optimized tables using any [!INCLUDE[tsql](../../includes/tsql-md.md)] query or DML operation (SELECT, INSERT, UPDATE, or DELETE), ad hoc batches, and SQL modules such as stored procedures, table-value functions, triggers, and views.</span></span>  
  
 <span data-ttu-id="57319-104">解譯的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指的是非原生編譯預存程序的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 批次或預存程序。</span><span class="sxs-lookup"><span data-stu-id="57319-104">Interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] refers to [!INCLUDE[tsql](../../includes/tsql-md.md)] batches or stored procedures other than a natively compiled stored procedure.</span></span> <span data-ttu-id="57319-105">記憶體最佳化資料表的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 解譯存取指的是 Interop 存取。</span><span class="sxs-lookup"><span data-stu-id="57319-105">Interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] access to memory-optimized tables is referred to as interop access.</span></span>  
  
 <span data-ttu-id="57319-106">記憶體最佳化的資料表也可以透過原生編譯的預存程序存取。</span><span class="sxs-lookup"><span data-stu-id="57319-106">Memory-optimized tables can also be accessed using a natively compiled stored procedure.</span></span> <span data-ttu-id="57319-107">建議針對效能嚴重不足的 OLTP 作業使用以原生方式編譯的預存程序。</span><span class="sxs-lookup"><span data-stu-id="57319-107">Natively compiled stored procedures are recommended for performance-critical OLTP operations.</span></span>  
  
 <span data-ttu-id="57319-108">建議在這些案例中使用解譯的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存取：</span><span class="sxs-lookup"><span data-stu-id="57319-108">Interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] access is recommended for these scenarios:</span></span>  
  
-   <span data-ttu-id="57319-109">隨選查詢和管理工作。</span><span class="sxs-lookup"><span data-stu-id="57319-109">Ad hoc queries and administrative tasks.</span></span>  
  
-   <span data-ttu-id="57319-110">報告查詢，通常會使用以原生方式編譯的預存程序中未提供的建構 (例如視窗函數)。</span><span class="sxs-lookup"><span data-stu-id="57319-110">Reporting queries, which typically use constructs not available in natively compiled stored procedures (such as window functions).</span></span>  
  
-   <span data-ttu-id="57319-111">為了將應用程式效能嚴重不足部分移轉至記憶體最佳化資料表，應用程式碼變更需求最低或完全不需要。</span><span class="sxs-lookup"><span data-stu-id="57319-111">To migrate performance-critical parts of your application to memory-optimized tables, with minimal (or no) application code changes.</span></span> <span data-ttu-id="57319-112">您可能會從移轉的資料表看到效能提升。</span><span class="sxs-lookup"><span data-stu-id="57319-112">You can potentially see performance improvements from migrating tables.</span></span> <span data-ttu-id="57319-113">如果您之後將預存程序移轉到以原生方式編譯的預存程序，您可以查看進一步的效能改善情形。</span><span class="sxs-lookup"><span data-stu-id="57319-113">If you then migrate stored procedures to natively compiled stored procedures, you may see further performance improvement.</span></span>  
  
-   <span data-ttu-id="57319-114">當以原生方式編譯的預存程序無法使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式時。</span><span class="sxs-lookup"><span data-stu-id="57319-114">When a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement is not available for natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="57319-115">下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 建構在記憶體最佳化資料表中存取資料的解譯 [!INCLUDE[tsql](../../includes/tsql-md.md)] 預存程序中不受支援。</span><span class="sxs-lookup"><span data-stu-id="57319-115">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] constructs are not supported in interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures that access data in a memory-optimized table.</span></span>  
  
|<span data-ttu-id="57319-116">區域</span><span class="sxs-lookup"><span data-stu-id="57319-116">Area</span></span>|<span data-ttu-id="57319-117">不支援</span><span class="sxs-lookup"><span data-stu-id="57319-117">Unsupported</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="57319-118">存取資料表</span><span class="sxs-lookup"><span data-stu-id="57319-118">Access to tables</span></span>|<span data-ttu-id="57319-119">TRUNCATE TABLE</span><span class="sxs-lookup"><span data-stu-id="57319-119">TRUNCATE TABLE</span></span><br /><br /> <span data-ttu-id="57319-120">MERGE (做為目標之記憶體最佳化的資料表)。</span><span class="sxs-lookup"><span data-stu-id="57319-120">MERGE (memory-optimized table as target)</span></span><br /><br /> <span data-ttu-id="57319-121">動態和索引鍵集資料指標 (這些會自動降級為靜態)。</span><span class="sxs-lookup"><span data-stu-id="57319-121">Dynamic and keyset cursors (these automatically degrade to static).</span></span><br /><br /> <span data-ttu-id="57319-122">使用內容連接從 CLR 模組存取。</span><span class="sxs-lookup"><span data-stu-id="57319-122">Access from CLR modules, using the context connection.</span></span><br /><br /> <span data-ttu-id="57319-123">從索引檢視表參考記憶體最佳化資料表。</span><span class="sxs-lookup"><span data-stu-id="57319-123">Referencing a memory-optimized table from an indexed view.</span></span>|  
|<span data-ttu-id="57319-124">跨資料庫</span><span class="sxs-lookup"><span data-stu-id="57319-124">Cross-database</span></span>|<span data-ttu-id="57319-125">跨資料庫查詢</span><span class="sxs-lookup"><span data-stu-id="57319-125">Cross-database queries</span></span><br /><br /> <span data-ttu-id="57319-126">跨資料庫交易</span><span class="sxs-lookup"><span data-stu-id="57319-126">Cross-database transactions</span></span><br /><br /> <span data-ttu-id="57319-127">連結的伺服器</span><span class="sxs-lookup"><span data-stu-id="57319-127">Linked servers</span></span>|  
  
## <a name="table-hints"></a><span data-ttu-id="57319-128">資料表提示</span><span class="sxs-lookup"><span data-stu-id="57319-128">Table Hints</span></span>  
 <span data-ttu-id="57319-129">如需有關資料表提示的詳細資訊，請參閱。</span><span class="sxs-lookup"><span data-stu-id="57319-129">For more information about table hints, see.</span></span> <span data-ttu-id="57319-130">[資料表提示 &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table)。</span><span class="sxs-lookup"><span data-stu-id="57319-130">[Table Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table).</span></span> <span data-ttu-id="57319-131">新增支援 [!INCLUDE[hek_2](../../includes/hek-2-md.md)]的快 SNAPSHOT 隔離。</span><span class="sxs-lookup"><span data-stu-id="57319-131">SNAPSHOT isolation was added to support [!INCLUDE[hek_2](../../includes/hek-2-md.md)].</span></span>  
  
 <span data-ttu-id="57319-132">使用解譯的 [!INCLUDE[tsql](../../includes/tsql-md.md)]存取記憶體最佳化的資料表時，不支援下列資料表提示。</span><span class="sxs-lookup"><span data-stu-id="57319-132">The following table hints are not supported when accessing a memory-optimized table using interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="57319-133">HOLDLOCK</span><span class="sxs-lookup"><span data-stu-id="57319-133">HOLDLOCK</span></span>|<span data-ttu-id="57319-134">IGNORE_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="57319-134">IGNORE_CONSTRAINTS</span></span>|<span data-ttu-id="57319-135">IGNORE_TRIGGERS</span><span class="sxs-lookup"><span data-stu-id="57319-135">IGNORE_TRIGGERS</span></span>|<span data-ttu-id="57319-136">NOWAIT</span><span class="sxs-lookup"><span data-stu-id="57319-136">NOWAIT</span></span>|  
|<span data-ttu-id="57319-137">PAGLOCK</span><span class="sxs-lookup"><span data-stu-id="57319-137">PAGLOCK</span></span>|<span data-ttu-id="57319-138">READCOMMITTED</span><span class="sxs-lookup"><span data-stu-id="57319-138">READCOMMITTED</span></span>|<span data-ttu-id="57319-139">READCOMMITTEDLOCK</span><span class="sxs-lookup"><span data-stu-id="57319-139">READCOMMITTEDLOCK</span></span>|<span data-ttu-id="57319-140">READPAST</span><span class="sxs-lookup"><span data-stu-id="57319-140">READPAST</span></span>|  
|<span data-ttu-id="57319-141">READUNCOMMITTED</span><span class="sxs-lookup"><span data-stu-id="57319-141">READUNCOMMITTED</span></span>|<span data-ttu-id="57319-142">ROWLOCK</span><span class="sxs-lookup"><span data-stu-id="57319-142">ROWLOCK</span></span>|<span data-ttu-id="57319-143">SPATIAL_WINDOW_MAX_CELLS = *integer*</span><span class="sxs-lookup"><span data-stu-id="57319-143">SPATIAL_WINDOW_MAX_CELLS = *integer*</span></span>|<span data-ttu-id="57319-144">TABLOCK</span><span class="sxs-lookup"><span data-stu-id="57319-144">TABLOCK</span></span>|  
|<span data-ttu-id="57319-145">TABLOCKXX</span><span class="sxs-lookup"><span data-stu-id="57319-145">TABLOCKXX</span></span>|<span data-ttu-id="57319-146">UPDLOCK</span><span class="sxs-lookup"><span data-stu-id="57319-146">UPDLOCK</span></span>|<span data-ttu-id="57319-147">XLOCK</span><span class="sxs-lookup"><span data-stu-id="57319-147">XLOCK</span></span>||  
  
 <span data-ttu-id="57319-148">當您使用解譯的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 從明確或隱含交易存取記憶體最佳化的資料表時，您必須包括隔離等級的資料表提示，例如 SNAPSHOT、REPEATABLEREAD 或 SERIALIZABLE，或者，您可以使用 MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT。</span><span class="sxs-lookup"><span data-stu-id="57319-148">When accessing a memory-optimized table from an explicit or implicit transaction using interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] you must include either an isolation level table hint such as SNAPSHOT, REPEATABLEREAD, or SERIALIZABLE, or you can use MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT.</span></span> <span data-ttu-id="57319-149">如需詳細資訊，請參閱[使用記憶體優化資料表的交易隔離等級方針](memory-optimized-tables.md)和[ALTER database SET 選項 &#40;transact-sql&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)。</span><span class="sxs-lookup"><span data-stu-id="57319-149">For more information, see [Guidelines for Transaction Isolation Levels with Memory-Optimized Tables](memory-optimized-tables.md) and [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="57319-150">在自動認可模式下執行之查詢所存取的記憶體最佳化的資料表不需要隔離等級資料表提示。</span><span class="sxs-lookup"><span data-stu-id="57319-150">An isolation level table hint is not required for memory-optimized tables accessed by queries running in auto-commit mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57319-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57319-151">See Also</span></span>  
 <span data-ttu-id="57319-152">[記憶體中 OLTP 的 Transact-SQL 支援](transact-sql-support-for-in-memory-oltp.md) </span><span class="sxs-lookup"><span data-stu-id="57319-152">[Transact-SQL Support for In-Memory OLTP](transact-sql-support-for-in-memory-oltp.md) </span></span>  
 [<span data-ttu-id="57319-153">移轉至 In-Memory OLTP</span><span class="sxs-lookup"><span data-stu-id="57319-153">Migrating to In-Memory OLTP</span></span>](migrating-to-in-memory-oltp.md)  
  
  
