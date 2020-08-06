---
title: 以時間為基礎之資料列篩選的最佳做法 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- best practices
ms.assetid: 773c5c62-fd44-44ab-9c6b-4257dbf8ffdb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ccaafe71d4137fd4b31eec412c1e35595861bdd0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584448"
---
# <a name="best-practices-for-time-based-row-filters"></a><span data-ttu-id="75498-102">以時間為基礎之資料列篩選的最佳做法</span><span class="sxs-lookup"><span data-stu-id="75498-102">Best Practices for Time-Based Row Filters</span></span>
  <span data-ttu-id="75498-103">應用程式使用者通常需要來自資料表中以時間為基礎的資料子集。</span><span class="sxs-lookup"><span data-stu-id="75498-103">Users of applications often require a time-based subset of data from a table.</span></span> <span data-ttu-id="75498-104">例如，業務員可能需要上週的訂單資料，或事件計劃者可能需要未來一週的事件資料。</span><span class="sxs-lookup"><span data-stu-id="75498-104">For instance, a salesperson might require data for orders in the last week, or an event planner might require data for events in the upcoming week.</span></span> <span data-ttu-id="75498-105">許多狀況下，應用程式會使用包含 `GETDATE()` 函數的查詢來達成這個目的。</span><span class="sxs-lookup"><span data-stu-id="75498-105">In many cases, applications use queries containing the `GETDATE()` function to accomplish this.</span></span> <span data-ttu-id="75498-106">請考量下列資料列篩選陳述式：</span><span class="sxs-lookup"><span data-stu-id="75498-106">Consider the following row filter statement:</span></span>  
  
```  
WHERE SalesPersonID = CONVERT(INT,HOST_NAME()) AND OrderDate >= (GETDATE()-6)  
```  
  
 <span data-ttu-id="75498-107">使用這種類型的篩選時，通常假設合併代理程式執行時一律會發生兩件事：滿足這個篩選的資料列會複寫至訂閱者，以及不再滿足這個篩選的資料列會從訂閱者端清除</span><span class="sxs-lookup"><span data-stu-id="75498-107">With a filter of this type, it is usually assumed that two things always occur when the Merge Agent runs: rows that satisfy this filter are replicated to Subscribers; and rows that no longer satisfy this filter are cleaned up at Subscribers.</span></span> <span data-ttu-id="75498-108"> (需使用進行篩選的詳細資訊 `HOST_NAME()` ，請參閱[參數化資料列篩選器](parameterized-filters-parameterized-row-filters.md)。 ) 不過，合併式複寫只會複寫和清除自從上次同步處理之後變更的資料，而不論您如何為該資料定義資料列篩選。</span><span class="sxs-lookup"><span data-stu-id="75498-108">(For more information about filtering with `HOST_NAME()`, see [Parameterized Row Filters](parameterized-filters-parameterized-row-filters.md).) However, merge replication only replicates and cleans up data that has changed since the last synchronization, regardless of how you define a row filter for that data.</span></span>  
  
 <span data-ttu-id="75498-109">若要合併式複寫處理資料列，資料列中的資料必須滿足資料列篩選，並且自上次同步處理後必須已變更。</span><span class="sxs-lookup"><span data-stu-id="75498-109">For merge replication to process a row, the data in the row must satisfy the row filter, and it must have changed since the last synchronization.</span></span> <span data-ttu-id="75498-110">在 **SalesOrderHeader** 資料表的案例中， **OrderDate** 是在插入資料列時所輸入的。</span><span class="sxs-lookup"><span data-stu-id="75498-110">In the case of the **SalesOrderHeader** table, **OrderDate** is entered when a row is inserted.</span></span> <span data-ttu-id="75498-111">資料列會如預期複寫至訂閱者，因為插入動作是資料變更。</span><span class="sxs-lookup"><span data-stu-id="75498-111">Rows are replicated to the Subscriber as expected because the insert is a data change.</span></span> <span data-ttu-id="75498-112">然而，如果訂閱者端有不再滿足篩選的資料列 (超過七天以上的訂單資料列)，除非這些資料列因其他原因而更新，否則不會從訂閱者端移除。</span><span class="sxs-lookup"><span data-stu-id="75498-112">However, if there are rows at the Subscriber that no longer satisfy the filter (they are for orders older than seven days), they are not removed from the Subscriber unless they were updated for some other reason.</span></span>  
  
 <span data-ttu-id="75498-113">事件計劃者的案例更進一步強調這種篩選類型的問題。</span><span class="sxs-lookup"><span data-stu-id="75498-113">The case of the event planner further highlights the issue with this type of filtering.</span></span> <span data-ttu-id="75498-114">請考量 **Events** 資料表的下列篩選：</span><span class="sxs-lookup"><span data-stu-id="75498-114">Consider the following filter for an **Events** table:</span></span>  
  
```  
WHERE EventCoordID = CONVERT(INT,HOST_NAME()) AND EventDate <= (GETDATE()+6)  
```  
  
 <span data-ttu-id="75498-115">對於包含事件的資料表，可能在事件日期前提早進行插入動作。</span><span class="sxs-lookup"><span data-stu-id="75498-115">For a table that contains events, inserts might be made well ahead of the event date.</span></span> <span data-ttu-id="75498-116">如果提前在一個月前進行未來一週事件的插入動作，並且資料列沒有因為其他原因而更新，即使該資料列滿足資料列篩選，也不會複寫至訂閱者。</span><span class="sxs-lookup"><span data-stu-id="75498-116">If the insert for an event in the coming week was made a month ago and the row was not updated for another reason, the row is not replicated to the Subscriber even if it satisfies the row filter.</span></span>  
  
 <span data-ttu-id="75498-117">此外，視發行集的設定方式而定，合併式複寫會在不同時間評估篩選：</span><span class="sxs-lookup"><span data-stu-id="75498-117">In addition, depending on how the publication is configured, merge replication evaluates filters at different times:</span></span>  
  
-   <span data-ttu-id="75498-118">如果發行集使用預先計算的資料分割 (預設值)，篩選會在插入或更新資料列時進行評估。</span><span class="sxs-lookup"><span data-stu-id="75498-118">If a publication uses precomputed partitions (the default), filters are evaluated when a row is inserted or updated.</span></span>  
  
-   <span data-ttu-id="75498-119">如果發行集沒有使用預先計算的資料分割，篩選會在執行 [合併代理程式] 時進行評估。</span><span class="sxs-lookup"><span data-stu-id="75498-119">If the publication does not use precomputed partitions, filters are evaluated when the Merge Agent runs.</span></span>  
  
 <span data-ttu-id="75498-120">如需預先計算之資料分割的詳細資訊，請參閱[使用預先計算的資料分割最佳化參數化篩選效能](parameterized-filters-optimize-for-precomputed-partitions.md)。</span><span class="sxs-lookup"><span data-stu-id="75498-120">For more information about precomputed partitions, see [Optimize Parameterized Filter Performance with Precomputed Partitions](parameterized-filters-optimize-for-precomputed-partitions.md).</span></span> <span data-ttu-id="75498-121">評估篩選的時間會影響哪些資料會滿足篩選。</span><span class="sxs-lookup"><span data-stu-id="75498-121">The time at which the filter is evaluated affects what data satisfies the filter.</span></span> <span data-ttu-id="75498-122">例如，如果發行集使用預先計算的資料分割，並且您每兩天會同步處理資料一次，業務員的資料子集可能會包含比預期早兩天的資料列。</span><span class="sxs-lookup"><span data-stu-id="75498-122">For example, if a publication uses precomputed partitions, and you synchronize data every two days, the subset of data for the salesperson could include rows up to two days older than expected.</span></span>  
  
## <a name="recommendations-for-using-time-based-row-filters"></a><span data-ttu-id="75498-123">以時間為基礎的資料列篩選使用建議</span><span class="sxs-lookup"><span data-stu-id="75498-123">Recommendations for Using Time-Based Row Filters</span></span>  
 <span data-ttu-id="75498-124">下列方法為以時間為基礎的篩選提供了完善直接的作法：</span><span class="sxs-lookup"><span data-stu-id="75498-124">The following method provides a robust and straightforward approach to filtering based on time:</span></span>  
  
-   <span data-ttu-id="75498-125">將資料行加入至 `bit` 資料類型的資料表。</span><span class="sxs-lookup"><span data-stu-id="75498-125">Add a column to the table of data type `bit`.</span></span> <span data-ttu-id="75498-126">這個資料行是用來指出資料列是否應複寫。</span><span class="sxs-lookup"><span data-stu-id="75498-126">This column is used to indicate whether a row should be replicated.</span></span>  
  
-   <span data-ttu-id="75498-127">使用會參考新資料行 (而不是以時間為基礎的資料行) 的資料列篩選。</span><span class="sxs-lookup"><span data-stu-id="75498-127">Use a row filter that references the new column rather than a time-based column.</span></span>  
  
-   <span data-ttu-id="75498-128">建立 SQL Server Agent 作業 (或透過另一個機制排程的作業)，這個作業會在合併代理程式已排程執行之前更新資料行。</span><span class="sxs-lookup"><span data-stu-id="75498-128">Create a SQL Server Agent job (or a job scheduled through another mechanism) that updates the column before the Merge Agent is scheduled to run.</span></span>  
  
 <span data-ttu-id="75498-129">這個作法針對使用 `GETDATE()` 或另一個以時間為基礎之方法的缺點，可避免必須決定何時評估資料分割篩選的問題。</span><span class="sxs-lookup"><span data-stu-id="75498-129">This approach addresses the shortcomings of using `GETDATE()` or another time-based method and avoids the problem of having to determine when filters are evaluated for partitions.</span></span> <span data-ttu-id="75498-130">請考量 **Events** 資料表的下列範例：</span><span class="sxs-lookup"><span data-stu-id="75498-130">Consider the following example of an **Events** table:</span></span>  
  
|<span data-ttu-id="75498-131">**EventID**</span><span class="sxs-lookup"><span data-stu-id="75498-131">**EventID**</span></span>|<span data-ttu-id="75498-132">**EventName**</span><span class="sxs-lookup"><span data-stu-id="75498-132">**EventName**</span></span>|<span data-ttu-id="75498-133">**EventCoordID**</span><span class="sxs-lookup"><span data-stu-id="75498-133">**EventCoordID**</span></span>|<span data-ttu-id="75498-134">**EventDate**</span><span class="sxs-lookup"><span data-stu-id="75498-134">**EventDate**</span></span>|<span data-ttu-id="75498-135">**複寫**</span><span class="sxs-lookup"><span data-stu-id="75498-135">**Replicate**</span></span>|  
|-----------------|-------------------|----------------------|-------------------|-------------------|  
|<span data-ttu-id="75498-136">1</span><span class="sxs-lookup"><span data-stu-id="75498-136">1</span></span>|<span data-ttu-id="75498-137">Reception</span><span class="sxs-lookup"><span data-stu-id="75498-137">Reception</span></span>|<span data-ttu-id="75498-138">112</span><span class="sxs-lookup"><span data-stu-id="75498-138">112</span></span>|<span data-ttu-id="75498-139">2006-10-04</span><span class="sxs-lookup"><span data-stu-id="75498-139">2006-10-04</span></span>|<span data-ttu-id="75498-140">1</span><span class="sxs-lookup"><span data-stu-id="75498-140">1</span></span>|  
|<span data-ttu-id="75498-141">2</span><span class="sxs-lookup"><span data-stu-id="75498-141">2</span></span>|<span data-ttu-id="75498-142">正餐</span><span class="sxs-lookup"><span data-stu-id="75498-142">Dinner</span></span>|<span data-ttu-id="75498-143">112</span><span class="sxs-lookup"><span data-stu-id="75498-143">112</span></span>|<span data-ttu-id="75498-144">2006-10-10</span><span class="sxs-lookup"><span data-stu-id="75498-144">2006-10-10</span></span>|<span data-ttu-id="75498-145">0</span><span class="sxs-lookup"><span data-stu-id="75498-145">0</span></span>|  
|<span data-ttu-id="75498-146">3</span><span class="sxs-lookup"><span data-stu-id="75498-146">3</span></span>|<span data-ttu-id="75498-147">Party</span><span class="sxs-lookup"><span data-stu-id="75498-147">Party</span></span>|<span data-ttu-id="75498-148">112</span><span class="sxs-lookup"><span data-stu-id="75498-148">112</span></span>|<span data-ttu-id="75498-149">2006-10-11</span><span class="sxs-lookup"><span data-stu-id="75498-149">2006-10-11</span></span>|<span data-ttu-id="75498-150">0</span><span class="sxs-lookup"><span data-stu-id="75498-150">0</span></span>|  
|<span data-ttu-id="75498-151">4</span><span class="sxs-lookup"><span data-stu-id="75498-151">4</span></span>|<span data-ttu-id="75498-152">Wedding</span><span class="sxs-lookup"><span data-stu-id="75498-152">Wedding</span></span>|<span data-ttu-id="75498-153">112</span><span class="sxs-lookup"><span data-stu-id="75498-153">112</span></span>|<span data-ttu-id="75498-154">2006-10-12</span><span class="sxs-lookup"><span data-stu-id="75498-154">2006-10-12</span></span>|<span data-ttu-id="75498-155">0</span><span class="sxs-lookup"><span data-stu-id="75498-155">0</span></span>|  
  
 <span data-ttu-id="75498-156">這個資料表的資料列篩選可能如下：</span><span class="sxs-lookup"><span data-stu-id="75498-156">The row filter for this table would then look like this:</span></span>  
  
```  
WHERE EventCoordID = CONVERT(INT,HOST_NAME()) AND Replicate = 1  
```  
  
 <span data-ttu-id="75498-157">SQL Server Agent 作業可在每次合併代理程式執行之前執行 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式，如下：</span><span class="sxs-lookup"><span data-stu-id="75498-157">The SQL Server Agent job could execute [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements similar to the following before each Merge Agent run:</span></span>  
  
```  
UPDATE Events SET Replicate = 0 WHERE Replicate = 1  
GO  
UPDATE Events SET Replicate = 1 WHERE EventDate <= GETDATE()+6  
GO  
```  
  
 <span data-ttu-id="75498-158">第一行會將 **Replicate** 資料行重設為 **0**，而第二行則會針對接下來七天發生的事件將資料行設為 **1** 。</span><span class="sxs-lookup"><span data-stu-id="75498-158">The first line resets the **Replicate** column to **0**, and the second line sets the column to **1** for events that occur in the next seven days.</span></span> <span data-ttu-id="75498-159">如果在 10/07/2006 執行這個 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式，資料表會更新成：</span><span class="sxs-lookup"><span data-stu-id="75498-159">If this [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement runs on 10/07/2006, the table is updated to:</span></span>  
  
|<span data-ttu-id="75498-160">**EventID**</span><span class="sxs-lookup"><span data-stu-id="75498-160">**EventID**</span></span>|<span data-ttu-id="75498-161">**EventName**</span><span class="sxs-lookup"><span data-stu-id="75498-161">**EventName**</span></span>|<span data-ttu-id="75498-162">**EventCoordID**</span><span class="sxs-lookup"><span data-stu-id="75498-162">**EventCoordID**</span></span>|<span data-ttu-id="75498-163">**EventDate**</span><span class="sxs-lookup"><span data-stu-id="75498-163">**EventDate**</span></span>|<span data-ttu-id="75498-164">**複寫**</span><span class="sxs-lookup"><span data-stu-id="75498-164">**Replicate**</span></span>|  
|-----------------|-------------------|----------------------|-------------------|-------------------|  
|<span data-ttu-id="75498-165">1</span><span class="sxs-lookup"><span data-stu-id="75498-165">1</span></span>|<span data-ttu-id="75498-166">Reception</span><span class="sxs-lookup"><span data-stu-id="75498-166">Reception</span></span>|<span data-ttu-id="75498-167">112</span><span class="sxs-lookup"><span data-stu-id="75498-167">112</span></span>|<span data-ttu-id="75498-168">2006-10-04</span><span class="sxs-lookup"><span data-stu-id="75498-168">2006-10-04</span></span>|<span data-ttu-id="75498-169">0</span><span class="sxs-lookup"><span data-stu-id="75498-169">0</span></span>|  
|<span data-ttu-id="75498-170">2</span><span class="sxs-lookup"><span data-stu-id="75498-170">2</span></span>|<span data-ttu-id="75498-171">正餐</span><span class="sxs-lookup"><span data-stu-id="75498-171">Dinner</span></span>|<span data-ttu-id="75498-172">112</span><span class="sxs-lookup"><span data-stu-id="75498-172">112</span></span>|<span data-ttu-id="75498-173">2006-10-10</span><span class="sxs-lookup"><span data-stu-id="75498-173">2006-10-10</span></span>|<span data-ttu-id="75498-174">1</span><span class="sxs-lookup"><span data-stu-id="75498-174">1</span></span>|  
|<span data-ttu-id="75498-175">3</span><span class="sxs-lookup"><span data-stu-id="75498-175">3</span></span>|<span data-ttu-id="75498-176">Party</span><span class="sxs-lookup"><span data-stu-id="75498-176">Party</span></span>|<span data-ttu-id="75498-177">112</span><span class="sxs-lookup"><span data-stu-id="75498-177">112</span></span>|<span data-ttu-id="75498-178">2006-10-11</span><span class="sxs-lookup"><span data-stu-id="75498-178">2006-10-11</span></span>|<span data-ttu-id="75498-179">1</span><span class="sxs-lookup"><span data-stu-id="75498-179">1</span></span>|  
|<span data-ttu-id="75498-180">4</span><span class="sxs-lookup"><span data-stu-id="75498-180">4</span></span>|<span data-ttu-id="75498-181">Wedding</span><span class="sxs-lookup"><span data-stu-id="75498-181">Wedding</span></span>|<span data-ttu-id="75498-182">112</span><span class="sxs-lookup"><span data-stu-id="75498-182">112</span></span>|<span data-ttu-id="75498-183">2006-10-12</span><span class="sxs-lookup"><span data-stu-id="75498-183">2006-10-12</span></span>|<span data-ttu-id="75498-184">1</span><span class="sxs-lookup"><span data-stu-id="75498-184">1</span></span>|  
  
 <span data-ttu-id="75498-185">下一週的事件現在會標幟為複寫準備就緒。</span><span class="sxs-lookup"><span data-stu-id="75498-185">The events for the next week are now flagged as being ready to replicate.</span></span> <span data-ttu-id="75498-186">下次合併代理程式針對事件協調者 112 所使用的訂閱而執行時，資料列 2、3 及 4 將會下載至訂閱者，並且資料列 1 將會從訂閱者移除。</span><span class="sxs-lookup"><span data-stu-id="75498-186">The next time the Merge Agent runs for the subscription that event coordinator 112 uses, rows 2, 3, and 4 will be downloaded to the Subscriber and row 1 will be removed from the Subscriber.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75498-187">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75498-187">See Also</span></span>  
 <span data-ttu-id="75498-188">[GETDATE &#40;Transact-SQL&#41;](/sql/t-sql/functions/getdate-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="75498-188">[GETDATE &#40;Transact-SQL&#41;](/sql/t-sql/functions/getdate-transact-sql) </span></span>  
 <span data-ttu-id="75498-189">[實作作業](../../../ssms/agent/implement-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="75498-189">[Implement Jobs](../../../ssms/agent/implement-jobs.md) </span></span>  
 [<span data-ttu-id="75498-190">參數化資料列篩選器</span><span class="sxs-lookup"><span data-stu-id="75498-190">Parameterized Row Filters</span></span>](parameterized-filters-parameterized-row-filters.md)  
  
  
