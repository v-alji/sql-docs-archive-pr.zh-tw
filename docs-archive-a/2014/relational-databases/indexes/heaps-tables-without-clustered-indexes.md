---
title: 堆積 (無叢集索引的資料表) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- heaps
ms.assetid: df5c4dfb-d372-4d0f-859a-a2d2533ee0d7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2a39bac2e0352f2adc7749e980d5cc91044f8ab2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606306"
---
# <a name="heaps-tables-without-clustered-indexes"></a><span data-ttu-id="03bab-102">堆積 (無叢集索引的資料表)</span><span class="sxs-lookup"><span data-stu-id="03bab-102">Heaps (Tables without Clustered Indexes)</span></span>
  <span data-ttu-id="03bab-103">堆積是一種沒有叢集索引的資料表。</span><span class="sxs-lookup"><span data-stu-id="03bab-103">A heap is a table without a clustered index.</span></span> <span data-ttu-id="03bab-104">一個或多個可以建立在儲存為堆積之資料表上的非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="03bab-104">One or more nonclustered indexes can be created on tables stored as a heap.</span></span> <span data-ttu-id="03bab-105">資料會以無指定順序的方式儲存於堆積中。</span><span class="sxs-lookup"><span data-stu-id="03bab-105">Data is stored in the heap without specifying an order.</span></span> <span data-ttu-id="03bab-106">一般來說，資料一開始是會以資料表中插入資料列的順序儲存，但是 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 會移動堆積中的資料，以有效率地儲存資料列，因此無法預期資料順序。</span><span class="sxs-lookup"><span data-stu-id="03bab-106">Usually data is initially stored in the order in which is the rows are inserted into the table, but the [!INCLUDE[ssDE](../../includes/ssde-md.md)] can move data around in the heap to store the rows efficiently; so the data order cannot be predicted.</span></span> <span data-ttu-id="03bab-107">為確保從堆積中傳回之資料列順序，您必須使用 `ORDER BY` 子句。</span><span class="sxs-lookup"><span data-stu-id="03bab-107">To guarantee the order of rows returned from a heap, you must use the `ORDER BY` clause.</span></span> <span data-ttu-id="03bab-108">若要指定儲存資料列的順序，請於資料表上建立叢集索引，如此一來資料表便不是堆積。</span><span class="sxs-lookup"><span data-stu-id="03bab-108">To specify the order for storage of the rows, create a clustered index on the table, so that the table is not a heap.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="03bab-109">有些時候不建立叢集索引，而讓資料表保持為堆積反而有助於工作，但有效地使用堆積是一項進階的技巧。</span><span class="sxs-lookup"><span data-stu-id="03bab-109">There are sometimes good reasons to leave a table as a heap instead of creating a clustered index, but using heaps effectively is an advanced skill.</span></span> <span data-ttu-id="03bab-110">除非有將資料表保留為堆積的特殊理由，否則大多數的資料表都應該選擇一個適合的叢集索引。</span><span class="sxs-lookup"><span data-stu-id="03bab-110">Most tables should have a carefully chosen clustered index unless a good reason exists for leaving the table as a heap.</span></span>  
  
## <a name="when-to-use-a-heap"></a><span data-ttu-id="03bab-111">使用堆積的時機</span><span class="sxs-lookup"><span data-stu-id="03bab-111">When to Use a Heap</span></span>  
 <span data-ttu-id="03bab-112">如果資料表為堆積且沒有任何非叢集索引，那麼您必須查看整份資料表 (資料表掃描) 才能找到資料列。</span><span class="sxs-lookup"><span data-stu-id="03bab-112">If a table is a heap and does not have any nonclustered indexes, then the entire table must be examined (a table scan) to find any row.</span></span> <span data-ttu-id="03bab-113">當您的資料表很短，例如只是一張您公司 12 處地區性辦公室的清單時，還不算太麻煩。</span><span class="sxs-lookup"><span data-stu-id="03bab-113">This can be acceptable when the table is tiny, such as a list of the 12 regional offices of a company.</span></span>  
  
 <span data-ttu-id="03bab-114">當資料表儲存為堆積時，參照會將各個資料列識別為資料列識別碼 (RID) (由檔案編號、資料頁碼及頁面上的位置所構成)。</span><span class="sxs-lookup"><span data-stu-id="03bab-114">When a table is stored as a heap, individual rows are identified by reference to a row identifier (RID) consisting of the file number, data page number, and slot on the page.</span></span> <span data-ttu-id="03bab-115">資料列識別碼是一個小而高效率的結構。</span><span class="sxs-lookup"><span data-stu-id="03bab-115">The row id is a small and efficient structure.</span></span> <span data-ttu-id="03bab-116">有時候當資料總是透過非叢集索引存取，且 RID 比叢集索引鍵還小時，資料工程師會使用堆積。</span><span class="sxs-lookup"><span data-stu-id="03bab-116">Sometimes data architects use heaps when data is always accessed through nonclustered indexes and the RID is smaller than a clustered index key.</span></span>  
  
## <a name="when-not-to-use-a-heap"></a><span data-ttu-id="03bab-117">切勿使用堆積的情況</span><span class="sxs-lookup"><span data-stu-id="03bab-117">When Not to Use a Heap</span></span>  
 <span data-ttu-id="03bab-118">經常按排序順序傳回資料時，請勿使用堆積。</span><span class="sxs-lookup"><span data-stu-id="03bab-118">Do not use a heap when the data is frequently returned in a sorted order.</span></span> <span data-ttu-id="03bab-119">在排序資料行中的叢集索引，可免去進行排序作業。</span><span class="sxs-lookup"><span data-stu-id="03bab-119">A clustered index on the sorting column could avoid the sorting operation.</span></span>  
  
 <span data-ttu-id="03bab-120">當資料經常組合在一起時，請勿使用堆積。</span><span class="sxs-lookup"><span data-stu-id="03bab-120">Do not use a heap when the data is frequently grouped together.</span></span> <span data-ttu-id="03bab-121">資料組合前必須先排序，而在排序資料行中建立叢集索引，可免去排序作業。</span><span class="sxs-lookup"><span data-stu-id="03bab-121">Data must be sorted before it is grouped, and a clustered index on the sorting column could avoid the sorting operation.</span></span>  
  
 <span data-ttu-id="03bab-122">經常要從資料表中查詢資料範圍時，請勿使用堆積。</span><span class="sxs-lookup"><span data-stu-id="03bab-122">Do not use a heap when ranges of data are frequently queried from the table.</span></span>  <span data-ttu-id="03bab-123">在範圍資料行中若有叢集索引，可以免去排序整個堆積。</span><span class="sxs-lookup"><span data-stu-id="03bab-123">A clustered index on the range column will avoid sorting the entire heap.</span></span>  
  
 <span data-ttu-id="03bab-124">沒有非叢集索引且資料表相當龐大時，請勿使用堆積。</span><span class="sxs-lookup"><span data-stu-id="03bab-124">Do not use a heap when there are no nonclustered indexes and the table is large.</span></span> <span data-ttu-id="03bab-125">在堆積中若要尋找某一資料列，就必須讀取堆積中的所有資料列。</span><span class="sxs-lookup"><span data-stu-id="03bab-125">In a heap, all rows of the heap must be read to find any row.</span></span>  
  
## <a name="managing-heaps"></a><span data-ttu-id="03bab-126">管理堆積</span><span class="sxs-lookup"><span data-stu-id="03bab-126">Managing Heaps</span></span>  
 <span data-ttu-id="03bab-127">若要建立堆積，請建立不含叢集索引的資料表。</span><span class="sxs-lookup"><span data-stu-id="03bab-127">To create a heap, create a table without a clustered index.</span></span> <span data-ttu-id="03bab-128">如果資料表中已有叢集索引，則請卸除叢集索引，將資料表還原為堆積。</span><span class="sxs-lookup"><span data-stu-id="03bab-128">If a table already has a clustered index, drop the clustered index to return the table to a heap.</span></span>  
  
 <span data-ttu-id="03bab-129">若要移除堆積，請在堆積上建立叢集索引。</span><span class="sxs-lookup"><span data-stu-id="03bab-129">To remove a heap, create a clustered index on the heap.</span></span>  
  
 <span data-ttu-id="03bab-130">若要重建堆積以回收浪費掉的空間，請先在堆積上建立叢集索引，然後再卸除該叢集索引。</span><span class="sxs-lookup"><span data-stu-id="03bab-130">To rebuild a heap to reclaim wasted space, create a clustered index on the heap, and then drop that clustered index.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="03bab-131">建立或卸除叢集索引時必須重寫整份資料表。</span><span class="sxs-lookup"><span data-stu-id="03bab-131">Creating or dropping clustered indexes requires rewriting the entire table.</span></span> <span data-ttu-id="03bab-132">若資料表具有非叢集索引，則一旦變更叢集索引之後，所有的非叢集索引都必須重建。</span><span class="sxs-lookup"><span data-stu-id="03bab-132">If the table has nonclustered indexes, all the nonclustered indexes must all be recreated whenever the clustered index is changed.</span></span> <span data-ttu-id="03bab-133">因此，在堆積與叢集索引結構之間的來回往返將會花費許多時間，且需要足夠的磁碟空間，才可在 tempdb 中重新排序資料。</span><span class="sxs-lookup"><span data-stu-id="03bab-133">Therefore, changing from a heap to a clustered index structure or back can take a lot of time and require disk space for reordering data in tempdb.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="03bab-134">相關內容</span><span class="sxs-lookup"><span data-stu-id="03bab-134">Related Content</span></span>  
 [<span data-ttu-id="03bab-135">CREATE INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="03bab-135">CREATE INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-index-transact-sql)  
  
 [<span data-ttu-id="03bab-136">DROP INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="03bab-136">DROP INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-index-transact-sql)  
  
 [<span data-ttu-id="03bab-137">叢集與非叢集索引說明</span><span class="sxs-lookup"><span data-stu-id="03bab-137">Clustered and Nonclustered Indexes Described</span></span>](clustered-and-nonclustered-indexes-described.md)  
  
  
