---
title: 估計資料庫的大小 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- space allocation [SQL Server], database size
- calculating database size
- increasing database size
- database size [SQL Server], estimating
- predicting database size
- size [SQL Server], databases
- estimating database size
- designing databases [SQL Server], estimating size
ms.assetid: 5b240161-eba4-44b0-946c-61a8fc00fc8c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6e3a390c4ade2c2dc08f67d2d1461955516e866c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595100"
---
# <a name="estimate-the-size-of-a-database"></a><span data-ttu-id="5c30c-102">估計資料庫的大小</span><span class="sxs-lookup"><span data-stu-id="5c30c-102">Estimate the Size of a Database</span></span>
  <span data-ttu-id="5c30c-103">在設計資料庫時，您可能需要估計資料庫填滿資料時的大小。</span><span class="sxs-lookup"><span data-stu-id="5c30c-103">When you design a database, you may have to estimate how large the database will be when filled with data.</span></span> <span data-ttu-id="5c30c-104">估計資料庫的大小可協助您判斷執行下列事項所需的硬體組態：</span><span class="sxs-lookup"><span data-stu-id="5c30c-104">Estimating the size of the database can help you determine the hardware configuration you will require to do the following:</span></span>  
  
-   <span data-ttu-id="5c30c-105">達到應用程式所需的效能。</span><span class="sxs-lookup"><span data-stu-id="5c30c-105">Achieve the performance required by your applications.</span></span>  
  
-   <span data-ttu-id="5c30c-106">提供需要的適當磁碟空間實際數量來儲存資料和索引。</span><span class="sxs-lookup"><span data-stu-id="5c30c-106">Guarantee the appropriate physical amount of disk space required to store the data and indexes.</span></span>  
  
 <span data-ttu-id="5c30c-107">估計資料庫的大小也可幫助您判斷是否需要調整資料庫設計。</span><span class="sxs-lookup"><span data-stu-id="5c30c-107">Estimating the size of a database can also help you determine whether the database design needs refining.</span></span> <span data-ttu-id="5c30c-108">例如您可判斷估計的資料庫大小是否太大，而導致無法實作於公司之中，並需要進一步地正規化。</span><span class="sxs-lookup"><span data-stu-id="5c30c-108">For example, you may determine that the estimated size of the database is too large to implement in your organization and that more normalization is required.</span></span> <span data-ttu-id="5c30c-109">相反的，估計的大小可能小於預期的大小。</span><span class="sxs-lookup"><span data-stu-id="5c30c-109">Conversely, the estimated size may be smaller than expected.</span></span> <span data-ttu-id="5c30c-110">這樣可讓您取消正規化資料庫進而提升查詢效能。</span><span class="sxs-lookup"><span data-stu-id="5c30c-110">This would allow you to denormalize the database to improve query performance.</span></span>  
  
 <span data-ttu-id="5c30c-111">若要估計資料庫的大小，可先個別地估計每個資料表的大小，然後將得到的數值加總。</span><span class="sxs-lookup"><span data-stu-id="5c30c-111">To estimate the size of a database, estimate the size of each table individually and then add the values obtained.</span></span> <span data-ttu-id="5c30c-112">資料表的大小取決於資料表是否包含索引，若包含索引，則必須判斷索引的類型為何。</span><span class="sxs-lookup"><span data-stu-id="5c30c-112">The size of a table depends on whether the table has indexes and, if they do, what type of indexes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5c30c-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="5c30c-113">In This Section</span></span>  
  
|<span data-ttu-id="5c30c-114">主題</span><span class="sxs-lookup"><span data-stu-id="5c30c-114">Topic</span></span>|<span data-ttu-id="5c30c-115">描述</span><span class="sxs-lookup"><span data-stu-id="5c30c-115">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="5c30c-116">估計資料表的大小</span><span class="sxs-lookup"><span data-stu-id="5c30c-116">Estimate the Size of a Table</span></span>](estimate-the-size-of-a-table.md)|<span data-ttu-id="5c30c-117">定義必要的步驟和計算，來估計將資料儲存於資料表和相關聯索引所需的空間數量。</span><span class="sxs-lookup"><span data-stu-id="5c30c-117">Defines the steps and calculations needed to estimate the amount of space required to store the data in a table and associated indexes.</span></span>|  
|[<span data-ttu-id="5c30c-118">估計堆積的大小</span><span class="sxs-lookup"><span data-stu-id="5c30c-118">Estimate the Size of a Heap</span></span>](estimate-the-size-of-a-heap.md)|<span data-ttu-id="5c30c-119">定義必要的步驟和計算，來估計將資料儲存於堆積所需的空間數量。</span><span class="sxs-lookup"><span data-stu-id="5c30c-119">Defines the steps and calculations needed to estimate the amount of space required to store the data in a heap.</span></span> <span data-ttu-id="5c30c-120">堆積是沒有叢集索引的資料表。</span><span class="sxs-lookup"><span data-stu-id="5c30c-120">A heap is a table that does not have a clustered index.</span></span>|  
|[<span data-ttu-id="5c30c-121">估計叢集索引的大小</span><span class="sxs-lookup"><span data-stu-id="5c30c-121">Estimate the Size of a Clustered Index</span></span>](estimate-the-size-of-a-clustered-index.md)|<span data-ttu-id="5c30c-122">定義必要的步驟和計算，來估計將資料儲存於叢集索引所需的空間數量。</span><span class="sxs-lookup"><span data-stu-id="5c30c-122">Defines the steps and calculations needed to estimate the amount of space required to store the data in a clustered index.</span></span>|  
|[<span data-ttu-id="5c30c-123">估計非叢集索引的大小</span><span class="sxs-lookup"><span data-stu-id="5c30c-123">Estimate the Size of a Nonclustered Index</span></span>](estimate-the-size-of-a-nonclustered-index.md)|<span data-ttu-id="5c30c-124">定義必要的步驟和計算，來估計將資料儲存於非叢集索引所需的空間數量。</span><span class="sxs-lookup"><span data-stu-id="5c30c-124">Defines the steps and calculations needed to estimate the amount of space required to store the data in a nonclustered index.</span></span>|  
  
  
