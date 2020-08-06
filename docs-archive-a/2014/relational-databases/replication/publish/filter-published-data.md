---
title: 篩選發行的資料 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server replication]
- filters [SQL Server replication], about filtering
- filtering [SQL Server replication]
- static row filters
- transactional replication, filtering published data
- replication [SQL Server], filtering published data
- filtering published data [SQL Server replication]
- snapshot replication [SQL Server], filtering published data
- column filters [SQL Server replication]
ms.assetid: 8a914947-72dc-4119-b631-b39c8070c71b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 525e90cecbc4cd6ee817b8fd07748abaf651b524
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592611"
---
# <a name="filter-published-data"></a><span data-ttu-id="554b0-102">篩選發行的資料</span><span class="sxs-lookup"><span data-stu-id="554b0-102">Filter Published Data</span></span>
  <span data-ttu-id="554b0-103">篩選資料表發行項可讓您建立即將發行的資料分割。</span><span class="sxs-lookup"><span data-stu-id="554b0-103">Filtering table articles enables you to create partitions of data to be published.</span></span> <span data-ttu-id="554b0-104">利用篩選發行的資料，您可以：</span><span class="sxs-lookup"><span data-stu-id="554b0-104">By filtering published data, you can:</span></span>  
  
-   <span data-ttu-id="554b0-105">將透過網路傳送的資料總量縮減到最少。</span><span class="sxs-lookup"><span data-stu-id="554b0-105">Minimize the amount of data sent over the network.</span></span>  
  
-   <span data-ttu-id="554b0-106">降低訂閱者端所需的儲存空間量。</span><span class="sxs-lookup"><span data-stu-id="554b0-106">Reduce the amount of storage space required at the Subscriber.</span></span>  
  
-   <span data-ttu-id="554b0-107">依照個別的訂閱者需求，自訂發行集和應用程式。</span><span class="sxs-lookup"><span data-stu-id="554b0-107">Customize publications and applications based on individual Subscriber requirements.</span></span>  
  
-   <span data-ttu-id="554b0-108">可以避免或減少訂閱者更新資料時的衝突，因為不同資料分割可以傳送給不同的訂閱者 (不會有兩個訂閱者同時更新相同的資料值)。</span><span class="sxs-lookup"><span data-stu-id="554b0-108">Avoid or reduce conflicts if Subscribers are updating data, because different data partitions can be sent to different Subscribers (no two Subscribers will be updating the same data values).</span></span>  
  
-   <span data-ttu-id="554b0-109">避免傳送機密資料。</span><span class="sxs-lookup"><span data-stu-id="554b0-109">Avoid transmitting sensitive data.</span></span> <span data-ttu-id="554b0-110">資料列篩選與資料行篩選可用於限制訂閱者對資料的存取。</span><span class="sxs-lookup"><span data-stu-id="554b0-110">Row filters and column filters can be used to restrict a Subscriber's access to data.</span></span> <span data-ttu-id="554b0-111">對於合併式複寫，如果使用含有 HOST_NAME() 的參數化篩選，則有安全性考量。</span><span class="sxs-lookup"><span data-stu-id="554b0-111">For merge replication, there are security considerations if you use a parameterized filter that includes HOST_NAME().</span></span> <span data-ttu-id="554b0-112">如需詳細資訊，請參閱＜ [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md)＞中的「使用 HOST_NAME() 進行篩選」一節。</span><span class="sxs-lookup"><span data-stu-id="554b0-112">For more information, see the section "Filtering with HOST_NAME()" in [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
 <span data-ttu-id="554b0-113">複寫提供四種類型的篩選：</span><span class="sxs-lookup"><span data-stu-id="554b0-113">Replication offers four types of filters:</span></span>  
  
-   <span data-ttu-id="554b0-114">靜態資料列篩選，適用於所有類型的複寫。</span><span class="sxs-lookup"><span data-stu-id="554b0-114">Static row filters, which are available with all types of replication.</span></span>  
  
     <span data-ttu-id="554b0-115">靜態資料列篩選可用於選擇要發行的資料列子集。</span><span class="sxs-lookup"><span data-stu-id="554b0-115">Using static row filters, you can choose a subset of rows to be published.</span></span> <span data-ttu-id="554b0-116">所有已篩選發行集的「訂閱者」會收到篩選資料表的相同資料列子集。</span><span class="sxs-lookup"><span data-stu-id="554b0-116">All Subscribers to a filtered publication receive the same subset of rows for the filtered table.</span></span> <span data-ttu-id="554b0-117">如需詳細資訊，請參閱本主題中的「靜態資料列篩選」一節。</span><span class="sxs-lookup"><span data-stu-id="554b0-117">For more information, see the section "Static Row Filters" in this topic.</span></span>  
  
-   <span data-ttu-id="554b0-118">資料行篩選，適用於所有類型的複寫。</span><span class="sxs-lookup"><span data-stu-id="554b0-118">Column filters, which are available with all types of replication.</span></span>  
  
     <span data-ttu-id="554b0-119">資料行篩選可用於選擇要發行的資料行子集。</span><span class="sxs-lookup"><span data-stu-id="554b0-119">Using column filters, you can choose a subset of columns to be published.</span></span> <span data-ttu-id="554b0-120">如需詳細資訊，請參閱本主題中的「資料行篩選」一節。</span><span class="sxs-lookup"><span data-stu-id="554b0-120">For more information, see the section "Column Filters" in this topic.</span></span>  
  
-   <span data-ttu-id="554b0-121">參數化資料列篩選器，僅適用於合併式複寫。</span><span class="sxs-lookup"><span data-stu-id="554b0-121">Parameterized row filters, which are available only with merge replication.</span></span>  
  
     <span data-ttu-id="554b0-122">參數化資料列篩選器可用於選擇要發行的資料列子集。</span><span class="sxs-lookup"><span data-stu-id="554b0-122">Using parameterized row filters, you can choose a subset of rows to be published.</span></span> <span data-ttu-id="554b0-123">靜態篩選是將相同的資料列子集傳送給每位「訂閱者」，參數化資料列篩選器則不同，它使用「訂閱者」提供的資料值，將不同的資料列子集傳送給「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="554b0-123">Unlike static filters that send the same subset of rows to every Subscriber, parameterized row filters use a data value supplied by the Subscriber to send Subscribers different subsets of rows.</span></span> <span data-ttu-id="554b0-124">如需詳細資訊，請參閱＜ [參數化資料列篩選器](../merge/parameterized-filters-parameterized-row-filters.md)＞。</span><span class="sxs-lookup"><span data-stu-id="554b0-124">For more information, see [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
-   <span data-ttu-id="554b0-125">聯結篩選，僅適用於合併式複寫。</span><span class="sxs-lookup"><span data-stu-id="554b0-125">Join filters, which are available only with merge replication.</span></span>  
  
     <span data-ttu-id="554b0-126">聯結篩選可用於將一個發行資料表的資料列篩選擴充到另一個資料表。</span><span class="sxs-lookup"><span data-stu-id="554b0-126">Using join filters, you can extend a row filter from one published table to another.</span></span> <span data-ttu-id="554b0-127">如需相關資訊，請參閱 [Join Filters](../merge/join-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="554b0-127">For more information, see [Join Filters](../merge/join-filters.md).</span></span>  
  
## <a name="static-row-filters"></a><span data-ttu-id="554b0-128">靜態資料列篩選</span><span class="sxs-lookup"><span data-stu-id="554b0-128">Static Row Filters</span></span>  
 <span data-ttu-id="554b0-129">下圖顯示篩選後發行集中僅包含資料列 2、3、6 的發行資料表。</span><span class="sxs-lookup"><span data-stu-id="554b0-129">The following illustration shows a published table that is filtered so that only rows 2, 3, and 6 are included in the publication.</span></span>  
  
 <span data-ttu-id="554b0-130">![資料列篩選](../media/repl-16.gif "資料列篩選")</span><span class="sxs-lookup"><span data-stu-id="554b0-130">![Row filtering](../media/repl-16.gif "Row filtering")</span></span>  
  
 <span data-ttu-id="554b0-131">靜態資料列篩選使用 WHERE 子句選取要發行的適當資料；您可以指定 WHERE 子句的最後部份。</span><span class="sxs-lookup"><span data-stu-id="554b0-131">A static row filter uses a WHERE clause to select the appropriate data to be published; you specify the final part of the WHERE clause.</span></span> <span data-ttu-id="554b0-132">請考慮 Adventure Works 範例資料庫中的 **Product 資料表** ，其中包含 **ProductLine**資料行。</span><span class="sxs-lookup"><span data-stu-id="554b0-132">Consider the **Product Table** in the Adventure Works sample database, which contains the column **ProductLine**.</span></span> <span data-ttu-id="554b0-133">若要只發行包含山地自行車相關產品之資料的資料列，請指定 `ProductLine = 'M'`。</span><span class="sxs-lookup"><span data-stu-id="554b0-133">To publish only the rows with data on products related to mountain bikes, specify `ProductLine = 'M'`.</span></span>  
  
 <span data-ttu-id="554b0-134">靜態資料列篩選會導致每個發行集只有一個資料集。</span><span class="sxs-lookup"><span data-stu-id="554b0-134">A static row filter results in a single set of data for each publication.</span></span> <span data-ttu-id="554b0-135">在上例中，所有「訂閱者」只會收到包含山地自行車相關產品之資料的資料列。</span><span class="sxs-lookup"><span data-stu-id="554b0-135">In the previous example, all Subscribers would receive only the rows with data on products related to mountain bikes.</span></span> <span data-ttu-id="554b0-136">如果有另一「訂閱者」需要只包含公路自行車相關產品之資料的資料列：</span><span class="sxs-lookup"><span data-stu-id="554b0-136">If you have another Subscriber that requires only the rows with data on products related to road bikes:</span></span>  
  
-   <span data-ttu-id="554b0-137">您可以使用快照式或異動複寫建立另一個發行集，將資料表包含在兩個發行集中 (在該發行集中發行項的篩選子句中，指定 `ProductLine = 'R')`。</span><span class="sxs-lookup"><span data-stu-id="554b0-137">With snapshot or transactional replication, you can create another publication and include the table in both publications (in the filter clause for the article in that publication, specify `ProductLine = 'R')`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="554b0-138">交易式發行集的資料列篩選可能會顯著增加負擔，因為已發行資料表的所有寫入記錄資料列都要進行發行項篩選子句評估，以決定是否應複寫資料列。</span><span class="sxs-lookup"><span data-stu-id="554b0-138">Row filters in transactional publications can add significant overhead because the article filter clause is evaluated for each log row written for a published table, to determine whether the row should be replicated.</span></span> <span data-ttu-id="554b0-139">如果每個複寫節點均可支援完全資料載入，且整個資料集非常小，則應避免交易式發行集中的資料列篩選。</span><span class="sxs-lookup"><span data-stu-id="554b0-139">Row filters in transactional publications should be avoided if each replication node can support the full data load, and the overall data set is reasonably small.</span></span>  
  
-   <span data-ttu-id="554b0-140">對於合併式複寫，請使用參數化資料列篩選器，不要使用靜態資料列篩選建立多個發行集。</span><span class="sxs-lookup"><span data-stu-id="554b0-140">With merge replication, use parameterized row filters rather than creating multiple publications with static row filters.</span></span> <span data-ttu-id="554b0-141">如需詳細資訊，請參閱＜ [參數化資料列篩選器](../merge/parameterized-filters-parameterized-row-filters.md)＞。</span><span class="sxs-lookup"><span data-stu-id="554b0-141">For more information, see [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
 <span data-ttu-id="554b0-142">若要定義或修改靜態資料列篩選，請參閱＜ [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md)＞。</span><span class="sxs-lookup"><span data-stu-id="554b0-142">To define or modify a static row filter, see [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md).</span></span>  
  
## <a name="column-filters"></a><span data-ttu-id="554b0-143">資料行篩選</span><span class="sxs-lookup"><span data-stu-id="554b0-143">Column Filters</span></span>  
 <span data-ttu-id="554b0-144">下圖顯示篩選掉資料行 C 的發行集。</span><span class="sxs-lookup"><span data-stu-id="554b0-144">The following illustration shows a publication that filters out column C.</span></span>  
  
 <span data-ttu-id="554b0-145">![資料行篩選](../media/repl-17.gif "資料行篩選")</span><span class="sxs-lookup"><span data-stu-id="554b0-145">![Column filtering](../media/repl-17.gif "Column filtering")</span></span>  
  
 <span data-ttu-id="554b0-146">您也可以同時使用資料列及資料行篩選，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="554b0-146">You can also use row and column filtering together, as illustrated here.</span></span>  
  
 <span data-ttu-id="554b0-147">![資料列和資料行篩選](../media/repl-18.gif "資料列和資料行篩選")</span><span class="sxs-lookup"><span data-stu-id="554b0-147">![Row and column filtering](../media/repl-18.gif "Row and column filtering")</span></span>  
  
 <span data-ttu-id="554b0-148">建立發行集之後，您可以使用資料行篩選從現有發行集中卸除資料行，但在「發行者」端的資料表中保留該資料行，亦可在發行集中包括現有資料行。</span><span class="sxs-lookup"><span data-stu-id="554b0-148">After a publication is created, you can use column filtering to drop a column from an existing publication, but retain the column in the table at the Publisher, and also to include an existing column in the publication.</span></span> <span data-ttu-id="554b0-149">對於其他變更，例如將新的資料行新增至資料表，然後新增至已發行的發行項，請使用結構描述變更複寫。</span><span class="sxs-lookup"><span data-stu-id="554b0-149">For other changes, such as adding a new column to a table and then adding it to the published article, use schema change replication.</span></span> <span data-ttu-id="554b0-150">如需詳細資訊，請參閱[對發行集資料庫進行結構描述變更](make-schema-changes-on-publication-databases.md)主題中的＜新增資料行＞和＜卸除資料行＞一節。</span><span class="sxs-lookup"><span data-stu-id="554b0-150">For more information, see the "Adding Columns" and "Dropping Columns" sections in the topic [Make Schema Changes on Publication Databases](make-schema-changes-on-publication-databases.md).</span></span>  
  
 <span data-ttu-id="554b0-151">下表中列出的資料行類型無法篩選出特定類型的發行集。</span><span class="sxs-lookup"><span data-stu-id="554b0-151">The types of columns listed in the following table cannot be filtered out of certain types of publications.</span></span>  
  
|<span data-ttu-id="554b0-152">資料行類型</span><span class="sxs-lookup"><span data-stu-id="554b0-152">Column type</span></span>|<span data-ttu-id="554b0-153">發行集類型及選項</span><span class="sxs-lookup"><span data-stu-id="554b0-153">Type of publication and options</span></span>|  
|-----------------|-------------------------------------|  
|<span data-ttu-id="554b0-154">主索引鍵資料行</span><span class="sxs-lookup"><span data-stu-id="554b0-154">Primary key column</span></span>|<span data-ttu-id="554b0-155">交易式發行集中的所有資料表均需要主索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="554b0-155">Primary key columns are required for all tables in transactional publications.</span></span> <span data-ttu-id="554b0-156">合併式發行集中的資料表不需要主索引鍵，但如果主索引鍵資料行存在，則無法被篩選。</span><span class="sxs-lookup"><span data-stu-id="554b0-156">Primary keys are not required for tables in merge publications, but if a primary key column is present, it cannot be filtered.</span></span>|  
|<span data-ttu-id="554b0-157">外部索引鍵資料行</span><span class="sxs-lookup"><span data-stu-id="554b0-157">Foreign key column</span></span>|<span data-ttu-id="554b0-158">所有使用「新增發行集精靈」建立的發行集。</span><span class="sxs-lookup"><span data-stu-id="554b0-158">All publications created using the New Publication wizard.</span></span> <span data-ttu-id="554b0-159">您可以使用 Transact-SQL 預存程序篩選外部索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="554b0-159">You can filter foreign key columns using Transact-SQL stored procedures.</span></span> <span data-ttu-id="554b0-160">如需詳細資訊，請參閱＜ [Define and Modify a Column Filter](define-and-modify-a-column-filter.md)＞。</span><span class="sxs-lookup"><span data-stu-id="554b0-160">For more information, [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).</span></span>|  
|<span data-ttu-id="554b0-161">**rowguid** 資料行</span><span class="sxs-lookup"><span data-stu-id="554b0-161">The **rowguid** column</span></span>|<span data-ttu-id="554b0-162">合併式發行集<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="554b0-162">Merge publications<sup>1</sup></span></span>|  
|<span data-ttu-id="554b0-163">**msrepl_tran_version** 資料行</span><span class="sxs-lookup"><span data-stu-id="554b0-163">The **msrepl_tran_version** column</span></span>|<span data-ttu-id="554b0-164">允許可更新訂閱的快照式及交易式發行集</span><span class="sxs-lookup"><span data-stu-id="554b0-164">Snapshot or transactional publications that allow updatable subscriptions</span></span>|  
|<span data-ttu-id="554b0-165">不允許 NULL 以及未設定預設值或 IDENTITY 屬性的資料行。</span><span class="sxs-lookup"><span data-stu-id="554b0-165">Columns that do not allow NULL and do not have default values or the IDENTITY property set.</span></span>|<span data-ttu-id="554b0-166">允許可更新訂閱的快照式及交易式發行集</span><span class="sxs-lookup"><span data-stu-id="554b0-166">Snapshot or transactional publications that allow updatable subscriptions</span></span>|  
|<span data-ttu-id="554b0-167">具有唯一條件約束或索引的資料行</span><span class="sxs-lookup"><span data-stu-id="554b0-167">Columns with unique constraints or indexes</span></span>|<span data-ttu-id="554b0-168">允許可更新訂閱的快照式及交易式發行集</span><span class="sxs-lookup"><span data-stu-id="554b0-168">Snapshot or transactional publications that allow updatable subscriptions</span></span>|  
|<span data-ttu-id="554b0-169">SQL Server 7.0 合併式發行集中的所有資料行</span><span class="sxs-lookup"><span data-stu-id="554b0-169">All columns in a SQL Server 7.0 merge publication</span></span>|<span data-ttu-id="554b0-170">在 SQL Server 7.0 合併式發行集中無法篩選資料行。</span><span class="sxs-lookup"><span data-stu-id="554b0-170">Columns cannot be filtered in SQL Server 7.0 merge publications.</span></span>|  
|<span data-ttu-id="554b0-171">時間戳記</span><span class="sxs-lookup"><span data-stu-id="554b0-171">Timestamp</span></span>|<span data-ttu-id="554b0-172">允許可更新訂閱的 SQL Server 7.0 快照式或交易式發行集</span><span class="sxs-lookup"><span data-stu-id="554b0-172">SQL Server 7.0 snapshot or transactional publications that allow updatable subscriptions</span></span>|  
  
 <span data-ttu-id="554b0-173"><sup>1</sup>如果您要發行合併式發行集中的資料表，且該資料表已包含已設定屬性之資料類型的資料行，則複寫 `uniqueidentifier` `ROWGUIDCOL` 可以使用此資料行，而不是建立名為**rowguid**的其他資料行。</span><span class="sxs-lookup"><span data-stu-id="554b0-173"><sup>1</sup> If you are publishing a table in a merge publication and that table already contains a column of data type `uniqueidentifier` with the `ROWGUIDCOL` property set, replication can use this column instead of creating an additional column named **rowguid**.</span></span> <span data-ttu-id="554b0-174">在此情況下，必須發行現有資料行。</span><span class="sxs-lookup"><span data-stu-id="554b0-174">In this case, the existing column must be published.</span></span>  
  
 <span data-ttu-id="554b0-175">若要定義或修改資料行篩選，請參閱＜ [Define and Modify a Column Filter](define-and-modify-a-column-filter.md)＞中的「使用 HOST_NAME() 進行篩選」一節。</span><span class="sxs-lookup"><span data-stu-id="554b0-175">To define or modify a column filter, see [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).</span></span>  
  
## <a name="filtering-considerations"></a><span data-ttu-id="554b0-176">篩選考量</span><span class="sxs-lookup"><span data-stu-id="554b0-176">Filtering Considerations</span></span>  
 <span data-ttu-id="554b0-177">篩選資料時請考慮以下事項：</span><span class="sxs-lookup"><span data-stu-id="554b0-177">Keep the following considerations in mind when filtering data:</span></span>  
  
-   <span data-ttu-id="554b0-178">資料列篩選中參考的所有資料行必須包括在發行集中。</span><span class="sxs-lookup"><span data-stu-id="554b0-178">All columns referenced in row filters must be included in the publication.</span></span> <span data-ttu-id="554b0-179">換句話說，您必須使用資料行篩選以排除資料列篩選中使用的資料行。</span><span class="sxs-lookup"><span data-stu-id="554b0-179">In other words, you cannot use a column filter to exclude a column that is used in a row filter.</span></span>  
  
-   <span data-ttu-id="554b0-180">如果在訂閱初始化之後新增或變更篩選，則該訂閱必須重新初始化。</span><span class="sxs-lookup"><span data-stu-id="554b0-180">If a filter is added or changed after subscriptions have been initialized, the subscriptions must be reinitialized.</span></span>  
  
-   <span data-ttu-id="554b0-181">篩選中使用的資料行所允許的最大位元組數，對於合併式發行集中的發行項為 1024，對於交易式發行集中的發行項則為 8000。</span><span class="sxs-lookup"><span data-stu-id="554b0-181">The maximum number of bytes allowed for a column used in a filter is 1024 for an article in a merge publication and 8000 for an article in a transactional publication.</span></span>  
  
-   <span data-ttu-id="554b0-182">包含以下資料類型的資料行無法在資料列篩選或聯結篩選中參考：</span><span class="sxs-lookup"><span data-stu-id="554b0-182">Columns with the following data types cannot be referenced in row filters or join filters:</span></span>  
  
    -   `varchar(max) and nvarchar(max)`  
  
    -   `varbinary(max)`  
  
    -   `text and ntext`  
  
    -   `image`  
  
    -   `XML`  
  
    -   `UDT`  
  
-   <span data-ttu-id="554b0-183">異動複寫可讓您將索引檢視複寫為檢視或資料表。</span><span class="sxs-lookup"><span data-stu-id="554b0-183">Transactional replication allows you to replicate an indexed view as a view or as a table.</span></span> <span data-ttu-id="554b0-184">如果將檢視複寫為資料表，則無法從資料表篩選資料行。</span><span class="sxs-lookup"><span data-stu-id="554b0-184">If you replicate the view as a table, you cannot filter columns from the table.</span></span>  
  
 <span data-ttu-id="554b0-185">資料列篩選並非設計為跨資料庫運作。</span><span class="sxs-lookup"><span data-stu-id="554b0-185">Row filters are not designed to work across databases.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="554b0-186">會刻意將 `sp_replcmds` (在底下執行的篩選) 的執行範圍限制為資料庫擁有者 (`dbo`)。</span><span class="sxs-lookup"><span data-stu-id="554b0-186">intentionally restricts the execution of `sp_replcmds` (which filters execute under) to the database owner (`dbo`).</span></span> <span data-ttu-id="554b0-187">`dbo` 沒有跨資料庫權限。</span><span class="sxs-lookup"><span data-stu-id="554b0-187">The `dbo` does not have cross database privileges.</span></span> <span data-ttu-id="554b0-188">透過 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 加入的 CDC (異動資料擷取)，`sp_replcmds` 邏輯會將使用者可以傳回及查詢的資訊填入變更追蹤資料表。</span><span class="sxs-lookup"><span data-stu-id="554b0-188">With the addition of CDC (Change Data Capture) in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] the `sp_replcmds` logic populates the change tracking tables with information that the user can return to and query.</span></span> <span data-ttu-id="554b0-189">基於安全性理由， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會限制這個邏輯的執行，讓惡意的 `dbo` 無法劫持此執行路徑。</span><span class="sxs-lookup"><span data-stu-id="554b0-189">For security reasons, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] restricts the execution of this logic so that a malicious `dbo` can't highjack this execution path.</span></span> <span data-ttu-id="554b0-190">例如，惡意 `dbo` 可能會加入 CDC 資料表的觸發程序，然後這些觸發程序就會在呼叫 `sp_replcmds` 的使用者內容底下執行 (在本例中，即為 Logreader 代理程式)。</span><span class="sxs-lookup"><span data-stu-id="554b0-190">For example, a malicious `dbo` could add triggers on CDC tables which would then get executed under the context of the user calling `sp_replcmds`, in this case the logreader agent.</span></span>  <span data-ttu-id="554b0-191">如果用來執行代理程式的帳戶擁有更高的權限，惡意 `dbo` 可能會提高其權限。</span><span class="sxs-lookup"><span data-stu-id="554b0-191">If the account the agent is running under has higher privilege the malicious `dbo` could escalate his privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="554b0-192">另請參閱</span><span class="sxs-lookup"><span data-stu-id="554b0-192">See Also</span></span>  
 [<span data-ttu-id="554b0-193">發行資料和資料庫物件</span><span class="sxs-lookup"><span data-stu-id="554b0-193">Publish Data and Database Objects</span></span>](publish-data-and-database-objects.md)  
  
  
