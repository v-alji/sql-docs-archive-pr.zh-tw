---
title: MSSQLSERVER_41396 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41396 (Database Engine error)
ms.assetid: 4ff04042-8367-46f3-8a16-c94682d6eedb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2386c805b61631c9b843753d74ba6616e7344223
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699619"
---
# <a name="mssqlserver_41396"></a><span data-ttu-id="6228e-102">MSSQLSERVER_41396</span><span class="sxs-lookup"><span data-stu-id="6228e-102">MSSQLSERVER_41396</span></span>
    
## <a name="details"></a><span data-ttu-id="6228e-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6228e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6228e-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="6228e-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="6228e-105">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="6228e-105">Event ID</span></span>|<span data-ttu-id="6228e-106">41396</span><span class="sxs-lookup"><span data-stu-id="6228e-106">41396</span></span>|  
|<span data-ttu-id="6228e-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="6228e-107">Event Source</span></span>|<span data-ttu-id="6228e-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6228e-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6228e-109">元件</span><span class="sxs-lookup"><span data-stu-id="6228e-109">Component</span></span>|<span data-ttu-id="6228e-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="6228e-110">SQLEngine</span></span>|  
|<span data-ttu-id="6228e-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="6228e-111">Symbolic Name</span></span>|<span data-ttu-id="6228e-112">MAX_SORT_ROWS_EXCEEDED</span><span class="sxs-lookup"><span data-stu-id="6228e-112">MAX_SORT_ROWS_EXCEEDED</span></span>|  
|<span data-ttu-id="6228e-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="6228e-113">Message Text</span></span>|<span data-ttu-id="6228e-114">排序作業超過緩衝區限制。</span><span class="sxs-lookup"><span data-stu-id="6228e-114">The sort operation exceeded the buffer limit.</span></span> <span data-ttu-id="6228e-115">已中止預存程序執行。</span><span class="sxs-lookup"><span data-stu-id="6228e-115">The stored procedure execution was aborted.</span></span> <span data-ttu-id="6228e-116">請參閱《SQL Server 線上叢書》以取得詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="6228e-116">Consult SQL Server Books Online for more information.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6228e-117">說明</span><span class="sxs-lookup"><span data-stu-id="6228e-117">Explanation</span></span>  
 <span data-ttu-id="6228e-118">原生編譯的預存程序會在記憶體中執行排序作業。</span><span class="sxs-lookup"><span data-stu-id="6228e-118">Natively compiled stored procedures perform sort operations in memory.</span></span> <span data-ttu-id="6228e-119">排序緩衝區的大小有所限制。</span><span class="sxs-lookup"><span data-stu-id="6228e-119">There is a limit on the size of the sort buffer.</span></span> <span data-ttu-id="6228e-120">此錯誤表示排序緩衝區的大小超出此限制。</span><span class="sxs-lookup"><span data-stu-id="6228e-120">This error means that the size of the sort buffer exceeds this limit.</span></span> <span data-ttu-id="6228e-121">已中止排序作業和預存程序執行。</span><span class="sxs-lookup"><span data-stu-id="6228e-121">The sort operation and the stored procedure execution aborted.</span></span>  
  
 <span data-ttu-id="6228e-122">在排序緩衝區中，每個資料列或項目的大小取決於排序的資料列數目、聯結數目以及查詢中的彙總函式數目和類型。</span><span class="sxs-lookup"><span data-stu-id="6228e-122">The size of each row or entry in the sort buffer is determined by the number of rows sorted as well as the number of joins and the number and type of aggregate functions in the query.</span></span> <span data-ttu-id="6228e-123">藉由簡化查詢，您可以縮減每個資料列的大小，進而在排序緩衝區納入更多資料列。</span><span class="sxs-lookup"><span data-stu-id="6228e-123">By simplifying the query, you can reduce the size of each row thereby fitting more rows in the sort buffer.</span></span> <span data-ttu-id="6228e-124">基底資料表中的資料列大小並不會影響排序緩衝區中每個資料列或項目的大小。</span><span class="sxs-lookup"><span data-stu-id="6228e-124">The size of the rows in the base tables does not affect the size of each row or entry in the sort buffer.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6228e-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="6228e-125">User Action</span></span>  
 <span data-ttu-id="6228e-126">選取較少資料列，或是移除聯結或彙總函式以減少查詢的複雜性。</span><span class="sxs-lookup"><span data-stu-id="6228e-126">Select fewer rows or decrease the complexity of the query by removing joins or aggregate functions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6228e-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6228e-127">See Also</span></span>  
 [<span data-ttu-id="6228e-128">記憶體內部 OLTP &#40;記憶體內部最佳化&#41;</span><span class="sxs-lookup"><span data-stu-id="6228e-128">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
