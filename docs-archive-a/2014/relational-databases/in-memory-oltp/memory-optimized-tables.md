---
title: 記憶體最佳化資料表 | Microsoft Docs
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 14dddf81-b502-49dc-a6b6-d18b1ae32d2b
author: rothja
ms.author: jroth
ms.openlocfilehash: 73430505e55230daf31c492d882eadeb6d35d29f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708358"
---
# <a name="memory-optimized-tables"></a><span data-ttu-id="29072-102">記憶體最佳化的資料表</span><span class="sxs-lookup"><span data-stu-id="29072-102">Memory-Optimized Tables</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="29072-103">記憶體中 OLTP 可透過有效率的記憶體最佳化資料存取、商務邏輯的原生編譯以及不需鎖定與閂鎖的演算法，協助提升 OLTP 應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="29072-103">In-Memory OLTP helps improve performance of OLTP applications through efficient, memory-optimized data access, native compilation of business logic, and lock- and latch free algorithms.</span></span> <span data-ttu-id="29072-104">記憶體中 OLTP 功能包括記憶體最佳化資料表和資料表類型，以及 [!INCLUDE[tsql](../../includes/tsql-md.md)] 預存程序的原生編譯，能夠有效率地存取這些資料表。</span><span class="sxs-lookup"><span data-stu-id="29072-104">The In-Memory OLTP feature includes memory-optimized tables and table types, as well as native compilation of [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures for efficient access to these tables.</span></span>  
  
 <span data-ttu-id="29072-105">如需有關記憶體最佳化的資料表的詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="29072-105">For more information about memory-optimized tables, see:</span></span>  
  
-   [<span data-ttu-id="29072-106">記憶體最佳化的資料表簡介</span><span class="sxs-lookup"><span data-stu-id="29072-106">Introduction to Memory-Optimized Tables</span></span>](memory-optimized-tables.md)  
  
     <span data-ttu-id="29072-107">詳述何謂記憶體最佳化資料表，並提供資料持久性及存取記憶體最佳化資料表中資料的相關資訊，以及效能與延展性的資訊。</span><span class="sxs-lookup"><span data-stu-id="29072-107">Details what memory-optimized tables are and provides information about data durability, accessing data in memory-optimized tables, and performance and scalability.</span></span>  
  
-   [<span data-ttu-id="29072-108">資料表和預存程序的原生編譯</span><span class="sxs-lookup"><span data-stu-id="29072-108">Native Compilation of Tables and Stored Procedures</span></span>](../in-memory-oltp/natively-compiled-stored-procedures.md)  
  
     <span data-ttu-id="29072-109">詳述記憶體最佳化資料表及原生編譯預存程序編譯至 DLL 中的方法，並提供相關安全性考量。</span><span class="sxs-lookup"><span data-stu-id="29072-109">Details how memory-optimized tables and natively compiled stored procedures are compiled into DLLs, and provides related security considerations.</span></span>  
  
-   [<span data-ttu-id="29072-110">改變記憶體最佳化資料表</span><span class="sxs-lookup"><span data-stu-id="29072-110">Altering Memory-Optimized Tables</span></span>](altering-memory-optimized-tables.md)  
  
     <span data-ttu-id="29072-111">升級記憶體最佳化資料表的方針 (包含變更資料行、索引及 bucket_count)。</span><span class="sxs-lookup"><span data-stu-id="29072-111">Guidelines for updating memory-optimized tables (including changing table columns, indexes, and bucket_count).</span></span>  
  
-   [<span data-ttu-id="29072-112">了解經記憶體最佳化的資料表上的交易</span><span class="sxs-lookup"><span data-stu-id="29072-112">Understanding Transactions on Memory-Optimized Tables</span></span>](../../database-engine/understanding-transactions-on-memory-optimized-tables.md)  
  
     <span data-ttu-id="29072-113">本節提供數個有關對記憶體最佳化資料表執行交易的主題，包含交易隔離等級，以及跨容器的交易。</span><span class="sxs-lookup"><span data-stu-id="29072-113">This section provides several topics related to performing transactions on memory-optimized tables including transaction isolation levels, and cross-container transactions.</span></span>  
  
-   [<span data-ttu-id="29072-114">分割記憶體最佳化資料表的應用程式模式</span><span class="sxs-lookup"><span data-stu-id="29072-114">Application Pattern for Partitioning Memory-Optimized Tables</span></span>](application-pattern-for-partitioning-memory-optimized-tables.md)  
  
     <span data-ttu-id="29072-115">詳細的程式碼範例，示範使用記憶體最佳化資料表時，如何模擬資料分割資料表。</span><span class="sxs-lookup"><span data-stu-id="29072-115">Detailed code sample that shows how to emulate partitioned tables when using memory-optimized tables.</span></span>  
  
-   [<span data-ttu-id="29072-116">記憶體最佳化資料表的統計資料</span><span class="sxs-lookup"><span data-stu-id="29072-116">Statistics for Memory-Optimized Tables</span></span>](statistics-for-memory-optimized-tables.md)  
  
     <span data-ttu-id="29072-117">詳述如何為記憶體最佳化資料表編譯統計資料，以及如何為記憶體最佳化資料表維護及手動更新統計資料。</span><span class="sxs-lookup"><span data-stu-id="29072-117">Details how statistics are compiled for memory-optimized tables and how to maintain and manually update statistics for memory-optimized tables.</span></span>  
  
-   [<span data-ttu-id="29072-118">定序和字碼頁</span><span class="sxs-lookup"><span data-stu-id="29072-118">Collations and Code Pages</span></span>](../../database-engine/collations-and-code-pages.md)  
  
     <span data-ttu-id="29072-119">詳述受支援定序的限制，以及記憶體最佳化資料表的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="29072-119">Details the restrictions on supported collations and code pages for memory-optimized tables.</span></span>  
  
-   [<span data-ttu-id="29072-120">記憶體最佳化資料表中的資料表和資料列大小</span><span class="sxs-lookup"><span data-stu-id="29072-120">Table and Row Size in Memory-Optimized Tables</span></span>](table-and-row-size-in-memory-optimized-tables.md)  
  
     <span data-ttu-id="29072-121">詳述記憶體最佳化資料列的 8060 位元組限制，並提供計算資料表與資料列大小的範例。</span><span class="sxs-lookup"><span data-stu-id="29072-121">Details the 8060 byte limit on memory-optimized table rows, and provides an example for calculating table and row sizes.</span></span>  
  
-   [<span data-ttu-id="29072-122">記憶體最佳化資料表的查詢處理指南</span><span class="sxs-lookup"><span data-stu-id="29072-122">A Guide to Query Processing for Memory-Optimized Tables</span></span>](a-guide-to-query-processing-for-memory-optimized-tables.md)  
  
     <span data-ttu-id="29072-123">針對記憶體最佳化資料表與原生編譯的預存程序，提供查詢處理的概觀。</span><span class="sxs-lookup"><span data-stu-id="29072-123">Provides an overview of query processing for both memory-optimized tables, and natively compiled stored procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29072-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29072-124">See Also</span></span>  
 [<span data-ttu-id="29072-125">記憶體內部 OLTP &#40;記憶體內部最佳化&#41;</span><span class="sxs-lookup"><span data-stu-id="29072-125">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](in-memory-oltp-in-memory-optimization.md)  
  
  
