---
title: MSSQLSERVER_41399 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41399 (Database Engine error)
ms.assetid: 5e5acb07-16ca-4329-8210-cd2bab0c904f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2e134cbc8b39a3c65d9c515183243f0b4caed434
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594575"
---
# <a name="mssqlserver_41399"></a><span data-ttu-id="98695-102">MSSQLSERVER_41399</span><span class="sxs-lookup"><span data-stu-id="98695-102">MSSQLSERVER_41399</span></span>
    
## <a name="details"></a><span data-ttu-id="98695-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="98695-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="98695-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="98695-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="98695-105">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="98695-105">Event ID</span></span>|<span data-ttu-id="98695-106">41399</span><span class="sxs-lookup"><span data-stu-id="98695-106">41399</span></span>|  
|<span data-ttu-id="98695-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="98695-107">Event Source</span></span>|<span data-ttu-id="98695-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="98695-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="98695-109">元件</span><span class="sxs-lookup"><span data-stu-id="98695-109">Component</span></span>|<span data-ttu-id="98695-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="98695-110">SQLEngine</span></span>|  
|<span data-ttu-id="98695-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="98695-111">Symbolic Name</span></span>|<span data-ttu-id="98695-112">MAX_SORT_ROW_WIDTH_EXCEEDED</span><span class="sxs-lookup"><span data-stu-id="98695-112">MAX_SORT_ROW_WIDTH_EXCEEDED</span></span>|  
|<span data-ttu-id="98695-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="98695-113">Message Text</span></span>|<span data-ttu-id="98695-114">排序作業太複雜。</span><span class="sxs-lookup"><span data-stu-id="98695-114">The sort operation is too complex.</span></span> <span data-ttu-id="98695-115">請參閱《SQL Server 線上叢書》以取得詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="98695-115">Consult SQL Server Books Online for more information.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="98695-116">說明</span><span class="sxs-lookup"><span data-stu-id="98695-116">Explanation</span></span>  
 <span data-ttu-id="98695-117">將聯結和彙總作業的結果排序，會因為排序緩衝區中的資料列大小增加，而增加排序作業的複雜性。</span><span class="sxs-lookup"><span data-stu-id="98695-117">Sorting the result of join and aggregation operations increases the complexity of the sort operation by increasing the size of the row in the sort buffer.</span></span> <span data-ttu-id="98695-118">此錯誤表示資料列的大小，超過原生編譯預存程序中排序運算子所支援的大小上限。</span><span class="sxs-lookup"><span data-stu-id="98695-118">This error means that the size of the row is larger than the maximum size supported by the sort operator in natively compiled stored procedures.</span></span> <span data-ttu-id="98695-119">請注意，排序緩衝區中的資料列大小，僅取決於聯結數目及彙總函式的數目和類型。</span><span class="sxs-lookup"><span data-stu-id="98695-119">Note that the size of a row in the sort buffer is determined solely by the number of joins and the number and type of aggregate functions.</span></span> <span data-ttu-id="98695-120">基底資料表中的資料列大小，並不會影響緩衝區中的資料列大小。</span><span class="sxs-lookup"><span data-stu-id="98695-120">The size of the rows in the base tables does not affect the size of the row in the buffer.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="98695-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="98695-121">User Action</span></span>  
 <span data-ttu-id="98695-122">移除聯結或彙總函式以減少查詢的複雜性。</span><span class="sxs-lookup"><span data-stu-id="98695-122">Decrease the complexity of the query by removing joins or aggregate functions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98695-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98695-123">See Also</span></span>  
 [<span data-ttu-id="98695-124">記憶體內部 OLTP &#40;記憶體內部最佳化&#41;</span><span class="sxs-lookup"><span data-stu-id="98695-124">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
