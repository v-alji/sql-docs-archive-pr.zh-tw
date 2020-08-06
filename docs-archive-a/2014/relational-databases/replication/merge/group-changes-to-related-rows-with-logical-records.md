---
title: 使用邏輯記錄分組相關資料列的變更 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication logical records [SQL Server replication]
- articles [SQL Server replication], logical records
- logical records [SQL Server replication]
ms.assetid: ad76799c-4486-4b98-9705-005433041321
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 433e0edbe83d102e6002bd133f967f27a236f66e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584447"
---
# <a name="group-changes-to-related-rows-with-logical-records"></a><span data-ttu-id="678e7-102">使用邏輯記錄分組相關資料列的變更</span><span class="sxs-lookup"><span data-stu-id="678e7-102">Group Changes to Related Rows with Logical Records</span></span>
  
> [!NOTE]
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]

 <span data-ttu-id="678e7-103">依預設，合併式複寫會按資料列逐一處理資料變更。</span><span class="sxs-lookup"><span data-stu-id="678e7-103">By default, merge replication processes data changes on a row-by-row basis.</span></span> <span data-ttu-id="678e7-104">這適用於很多情況，但對於某些應用程式，有必要將相關資料列做為一個單位進行處理。</span><span class="sxs-lookup"><span data-stu-id="678e7-104">In many circumstances this is appropriate, but for some applications, it is essential that related rows be processed as a unit.</span></span> <span data-ttu-id="678e7-105">合併式複寫的邏輯記錄功能可讓您定義不同資料表中相關資料列之間的關聯性，以便將這些資料列做為一個單位進行處理。</span><span class="sxs-lookup"><span data-stu-id="678e7-105">The logical records feature of merge replication allows you to define a relationship between related rows in different tables so that the rows are processed as a unit.</span></span>

> [!NOTE]
>  <span data-ttu-id="678e7-106">邏輯記錄功能可以獨立使用，也可以與聯結篩選結合使用。</span><span class="sxs-lookup"><span data-stu-id="678e7-106">The logical records feature can be used alone or in conjunction with join filters.</span></span> <span data-ttu-id="678e7-107">如需聯結篩選的詳細資訊，請參閱＜ [Join Filters](join-filters.md)＞。</span><span class="sxs-lookup"><span data-stu-id="678e7-107">For more information about join filters, see [Join Filters](join-filters.md).</span></span> <span data-ttu-id="678e7-108">若要使用邏輯記錄，發行集的相容性層級必須至少為 90RTM。</span><span class="sxs-lookup"><span data-stu-id="678e7-108">To use logical records, the compatibility level of the publication must be at least 90RTM.</span></span>

 <span data-ttu-id="678e7-109">設想有以下三個相關資料表：</span><span class="sxs-lookup"><span data-stu-id="678e7-109">Consider these three related tables:</span></span>

 <span data-ttu-id="678e7-110">![三個資料表邏輯記錄，只具有資料行名稱](../media/logical-records-01.gif "三個資料表邏輯記錄，只具有資料行名稱")</span><span class="sxs-lookup"><span data-stu-id="678e7-110">![Three table logical record, with column names only](../media/logical-records-01.gif "Three table logical record, with column names only")</span></span>

 <span data-ttu-id="678e7-111">在此關聯性中， **Customers** 資料表為父資料表，具有一個主索引鍵資料行 **CustID**。</span><span class="sxs-lookup"><span data-stu-id="678e7-111">The **Customers** table is the parent table in this relationship and has a primary key column **CustID**.</span></span> <span data-ttu-id="678e7-112">**Orders** 資料表有一個主索引鍵資料行 **OrderID**，且 **CustID** 資料行上存在外部索引鍵條件約束 (參考 **Customers** 資料表中的 **CustID** 資料行)。</span><span class="sxs-lookup"><span data-stu-id="678e7-112">The **Orders** table has a primary key column **OrderID**, with a foreign key constraint on the **CustID** column that references the **CustID** column in the **Customers** table.</span></span> <span data-ttu-id="678e7-113">同樣地， **OrderItems** 資料表也具有一個主索引鍵資料行 **OrderItemID**，且 **OrderID** 資料行上存在外部索引鍵條件約束 (參考到 **Orders** 資料表中的 **OrderID** 資料行)。</span><span class="sxs-lookup"><span data-stu-id="678e7-113">Similarly, the **OrderItems** table has a primary key column **OrderItemID**, with a foreign key constraint on the **OrderID** column that references the **OrderID** column in the **Orders** table.</span></span>

 <span data-ttu-id="678e7-114">在此範例中，邏輯記錄是由 **Orders** 資料表中與單一 **CustID** 值相關的所有資料列以及 **OrderItems** 資料表中與 **Orders** 資料表中那些資料列相關的所有資料列所組成。</span><span class="sxs-lookup"><span data-stu-id="678e7-114">In this example, a logical record consists of all the rows in the **Orders** table that are related to a single **CustID** value and all of the rows in the **OrderItems** table that are related to those rows in the **Orders** table.</span></span> <span data-ttu-id="678e7-115">下圖顯示 Customer2 之邏輯記錄在三個資料表中的所有資料列：</span><span class="sxs-lookup"><span data-stu-id="678e7-115">This diagram shows all the rows in the three tables that are in the logical record for Customer2:</span></span>

 <span data-ttu-id="678e7-116">![具有值的三個資料表邏輯記錄](../media/logical-records-02.gif "具有值的三個資料表邏輯記錄")</span><span class="sxs-lookup"><span data-stu-id="678e7-116">![Three table logical record with values](../media/logical-records-02.gif "Three table logical record with values")</span></span>

 <span data-ttu-id="678e7-117">若要定義發行項之間的邏輯記錄關聯性，請參閱＜ [定義合併資料表發行項之間的邏輯記錄關聯性](../publish/define-a-logical-record-relationship-between-merge-table-articles.md)＞。</span><span class="sxs-lookup"><span data-stu-id="678e7-117">To define a logical record relationship between articles, see [Define a Logical Record Relationship Between Merge Table Articles](../publish/define-a-logical-record-relationship-between-merge-table-articles.md).</span></span>

## <a name="benefits-of-logical-records"></a><span data-ttu-id="678e7-118">邏輯記錄的優點</span><span class="sxs-lookup"><span data-stu-id="678e7-118">Benefits of Logical Records</span></span>
 <span data-ttu-id="678e7-119">邏輯記錄功能具有兩個主要的優點：</span><span class="sxs-lookup"><span data-stu-id="678e7-119">The logical records feature has two primary benefits:</span></span>

-   <span data-ttu-id="678e7-120">將資料變更做為一個單位。</span><span class="sxs-lookup"><span data-stu-id="678e7-120">Application of data changes as a unit.</span></span>

-   <span data-ttu-id="678e7-121">對多個資料表中的多個資料列同時進行衝突偵測和解決。</span><span class="sxs-lookup"><span data-stu-id="678e7-121">The detection and resolution of conflicts simultaneously on multiple rows from multiple tables.</span></span>

### <a name="the-application-of-changes-as-a-unit"></a><span data-ttu-id="678e7-122">將變更當做一個單位</span><span class="sxs-lookup"><span data-stu-id="678e7-122">The Application of Changes As a Unit</span></span>
 <span data-ttu-id="678e7-123">如果合併處理中斷 (例如出現連接被卸除)，則在使用了邏輯記錄的情況下，部分完成的那組相關複寫變更會回復。</span><span class="sxs-lookup"><span data-stu-id="678e7-123">If merge processing is interrupted, such as in the case of a dropped connection, the partially completed set of related replicated changes is rolled back if logical records are used.</span></span> <span data-ttu-id="678e7-124">例如存在以下情況，「訂閱者」新增了一個新訂單 ( **OrderID** = 6)，並在 **OrderItems** 資料表中新增了兩個新的資料列，即 **OrderID** = 6，其 **OrderItemID** = 10， **OrderItemID** = 11。</span><span class="sxs-lookup"><span data-stu-id="678e7-124">For example, consider the case where a Subscriber adds a new order with **OrderID** = 6 and two new rows in the **OrderItems** table with **OrderItemID** = 10 and **OrderItemID** = 11 for **OrderID** = 6.</span></span>

 <span data-ttu-id="678e7-125">![具有值的三個資料表邏輯記錄](../media/logical-records-04.gif "具有值的三個資料表邏輯記錄")</span><span class="sxs-lookup"><span data-stu-id="678e7-125">![Three table logical record with values](../media/logical-records-04.gif "Three table logical record with values")</span></span>

 <span data-ttu-id="678e7-126">如果複寫處理在 **OrderID** = 6 的 **Orders** 資料列完成後，但在 **OrderItems** 10 和 11 完成之前中斷，並且未使用邏輯記錄，則 **OrderID** = 6 的 **OrderTotal** 值將與 **OrderItems** 資料列之 **OrderAmount** 值的總和不一致。</span><span class="sxs-lookup"><span data-stu-id="678e7-126">If the replication process is interrupted after the **Orders** row for **OrderID** = 6 is complete, but before the **OrderItems** 10 and 11 are completed, and logical records are not used, the **OrderTotal** value for **OrderID** = 6 will not be consistent with the sum of the **OrderAmount** values for the **OrderItems** rows.</span></span> <span data-ttu-id="678e7-127">如果使用了邏輯記錄， **OrderID** = 6 的 **Orders** 資料列不會得到認可，直至複寫了相關的 **OrderItems** 變更。</span><span class="sxs-lookup"><span data-stu-id="678e7-127">If logical records are used, the **Orders** row for **OrderID** = 6 is not committed until the related **OrderItems** changes are replicated.</span></span>

 <span data-ttu-id="678e7-128">另一個實例中，如果使用了邏輯記錄，且當合併處理套用變更時，尚有人在查詢資料表，則使用者將看不到僅部分複寫的變更，直至它們全部完成。</span><span class="sxs-lookup"><span data-stu-id="678e7-128">In a different scenario, if logical records are used, and someone is querying tables when the merge process is applying changes, the user will not see the partially replicated changes until they are all complete.</span></span> <span data-ttu-id="678e7-129">例如，複寫處理上傳了 **OrderID** = 6 的 Orders 資料列，但有使用者在複寫處理對 **OrderItems** 資料列進行複寫之前查詢資料表，則 **OrderTotal** 值將與 **OrderAmount** 值之總和不相同。</span><span class="sxs-lookup"><span data-stu-id="678e7-129">For example, the replication process has uploaded the Orders row for **OrderID** = 6, but a user queries the tables before the replication process has replicated the **OrderItems** rows, the **OrderTotal** value would not be the same as the sum of the **OrderAmount** values.</span></span> <span data-ttu-id="678e7-130">如果使用了邏輯記錄，則在 **OrderItems** 資料列的處理完成，且交易做為一個單位得到認可之前，使用者將看不到 **Orders** 資料列。</span><span class="sxs-lookup"><span data-stu-id="678e7-130">If logical records are used, the **Orders** row would not be visible until the **OrderItems** rows are complete and the transaction has been committed as a unit.</span></span>

### <a name="the-application-of-conflict-handling-to-more-than-one-table"></a><span data-ttu-id="678e7-131">對多個資料表的衝突處理</span><span class="sxs-lookup"><span data-stu-id="678e7-131">The Application of Conflict Handling to More Than One Table</span></span>
 <span data-ttu-id="678e7-132">設想有兩個「訂閱者」包含上述資料設定的情況：</span><span class="sxs-lookup"><span data-stu-id="678e7-132">Consider the case where two Subscribers have the data set above:</span></span>

-   <span data-ttu-id="678e7-133">第一個「訂閱者」端的使用者將 **OrderItemID** 5 的 **OrderAmount** 從 100 變更到 150，將 **OrderID** 3 的 **OrderTotal** 從 200 變更到 250。</span><span class="sxs-lookup"><span data-stu-id="678e7-133">A user at the first Subscriber changes the **OrderAmount** of **OrderItemID** 5 from 100 to 150 and the **OrderTotal** of **OrderID** 3 from 200 to 250.</span></span>

-   <span data-ttu-id="678e7-134">第二個「訂閱者」端的使用者將 **OrderItemID** 6 的 **OrderAmount** 從 25 變更到 125，將 **OrderID** 3 的 **OrderTotal** 從 200 變更到 300。</span><span class="sxs-lookup"><span data-stu-id="678e7-134">A user at the second Subscriber changes the **OrderAmount** of **OrderItemID** 6 from 25 to 125 and the **OrderTotal** of **OrderID** 3 from 200 to 300.</span></span>

 <span data-ttu-id="678e7-135">如果這些變更在未使用邏輯記錄的情況下進行了複寫，則不同的 **OrderTotal** 值會造成衝突，且僅會複寫它們中的一個。</span><span class="sxs-lookup"><span data-stu-id="678e7-135">If these changes are replicated without using logical records, the different **OrderTotal** values would result in a conflict and only one of them would be replicated.</span></span> <span data-ttu-id="678e7-136">但是 **OrderItems** 資料表中的不衝突變更會在沒有衝突的情況下進行複寫，使最終的 **OrderTotal** 值與 **OrderItems** 資料列處於不一致的狀態。</span><span class="sxs-lookup"><span data-stu-id="678e7-136">But the non-conflicting changes in the **OrderItems** table would be replicated without conflict, leaving the final **OrderTotal** values in an inconsistent state with respect to the **OrderItems** rows.</span></span> <span data-ttu-id="678e7-137">如果在此實例中使用了邏輯記錄，與失敗的 **Orders** 資料表變更相關聯的 **OrderItems** 變更也會被回復，且最終的 **OrderTotal** 值會是 **OrderItems** 資料列的精確總和。</span><span class="sxs-lookup"><span data-stu-id="678e7-137">If logical records are used in this scenario, the **OrderItems** change associated with the losing **Orders** table change would also be rolled back, and the final **OrderTotal** value would be an accurate summary of the **OrderItems** rows.</span></span>

 <span data-ttu-id="678e7-138">如需邏輯記錄衝突偵測和解決方法相關選項的詳細資訊，請參閱[偵測和解決邏輯記錄中的衝突](advanced-merge-replication-conflict-resolving-in-logical-record.md)。</span><span class="sxs-lookup"><span data-stu-id="678e7-138">For more information about options related to conflict detection and resolution with logical records, see [Detecting and Resolving Conflicts in Logical Records](advanced-merge-replication-conflict-resolving-in-logical-record.md).</span></span>

## <a name="considerations-for-using-logical-records"></a><span data-ttu-id="678e7-139">使用邏輯記錄的考量</span><span class="sxs-lookup"><span data-stu-id="678e7-139">Considerations for Using Logical Records</span></span>
 <span data-ttu-id="678e7-140">使用邏輯記錄時，請記住下列考量。</span><span class="sxs-lookup"><span data-stu-id="678e7-140">Keep the following considerations in mind when using logical records.</span></span>

### <a name="general-considerations"></a><span data-ttu-id="678e7-141">一般考量</span><span class="sxs-lookup"><span data-stu-id="678e7-141">General Considerations</span></span>

-   <span data-ttu-id="678e7-142">建議盡可能減少邏輯記錄中的資料表數；建議五個或更少。</span><span class="sxs-lookup"><span data-stu-id="678e7-142">It is recommended that you keep the number of tables in a logical record as low as possible; five tables or less is recommended.</span></span>

-   <span data-ttu-id="678e7-143">邏輯記錄無法參考含下列資料類型的資料行：</span><span class="sxs-lookup"><span data-stu-id="678e7-143">Logical records cannot reference columns with any of the following data types:</span></span>

    -   <span data-ttu-id="678e7-144">`varchar(max)` 和 `nvarchar(max)`</span><span class="sxs-lookup"><span data-stu-id="678e7-144">`varchar(max)` and `nvarchar(max)`</span></span>

    -   `varbinary(max)`

    -   <span data-ttu-id="678e7-145">`text` 和 `ntext`</span><span class="sxs-lookup"><span data-stu-id="678e7-145">`text` and `ntext`</span></span>

    -   `image`

    -   `XML`

    -   `UDT`

-   <span data-ttu-id="678e7-146">已發行資料表中的外部索引鍵關聯性無法使用 CASCADE 選項進行定義。</span><span class="sxs-lookup"><span data-stu-id="678e7-146">Foreign key relationships in published tables cannot be defined with the CASCADE option.</span></span> <span data-ttu-id="678e7-147">如需詳細資訊，請參閱 [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) 和 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="678e7-147">For more information, see [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) and [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>

-   <span data-ttu-id="678e7-148">無法更新邏輯關聯性子句中使用的任何資料行。</span><span class="sxs-lookup"><span data-stu-id="678e7-148">You cannot update any columns that are used in the logical relation clause.</span></span>

-   <span data-ttu-id="678e7-149">對於邏輯記錄中包含的發行項，不支援使用商務邏輯處理常式或自訂解析程式進行自訂衝突解決。</span><span class="sxs-lookup"><span data-stu-id="678e7-149">Custom conflict resolution with business logic handlers or custom resolvers is not supported for articles that are included in a logical record.</span></span>

-   <span data-ttu-id="678e7-150">如果在包含了參數化篩選的發行集中使用邏輯記錄，您必須使用「訂閱者」資料分割的快照集來初始化「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="678e7-150">If logical records are used in a publication that includes parameterized filters, you must initialize each Subscriber with a snapshot for its partition.</span></span> <span data-ttu-id="678e7-151">如果您使用其他方法初始化「訂閱者」，「合併代理程式」將失敗。</span><span class="sxs-lookup"><span data-stu-id="678e7-151">If you initialize a Subscriber with another method, the Merge Agent will fail.</span></span> <span data-ttu-id="678e7-152">如需詳細資訊，請參閱 [Snapshots for Merge Publications with Parameterized Filters](../snapshots-for-merge-publications-with-parameterized-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="678e7-152">For more information, see [Snapshots for Merge Publications with Parameterized Filters](../snapshots-for-merge-publications-with-parameterized-filters.md).</span></span>

-   <span data-ttu-id="678e7-153">「衝突檢視器」中不會顯示涉及邏輯記錄的衝突。</span><span class="sxs-lookup"><span data-stu-id="678e7-153">Conflicts that involve logical records are not displayed in Conflict Viewer.</span></span> <span data-ttu-id="678e7-154">若要檢視這些衝突的相關資訊，請使用複寫預存程序。</span><span class="sxs-lookup"><span data-stu-id="678e7-154">To view information about these conflicts, use replication stored procedures.</span></span> <span data-ttu-id="678e7-155">如需詳細資訊，請參閱[檢視合併式發行集的衝突資訊 &#40;複寫 Transact-SQL 程式設計&#41;](../view-conflict-information-for-merge-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="678e7-155">For more information, see [View Conflict Information for Merge Publications &#40;Replication Transact-SQL Programming&#41;](../view-conflict-information-for-merge-publications.md).</span></span>

### <a name="publication-settings"></a><span data-ttu-id="678e7-156">發行集設定</span><span class="sxs-lookup"><span data-stu-id="678e7-156">Publication Settings</span></span>

-   <span data-ttu-id="678e7-157">發行集的相容性層級必須為 90RTM 或更高。</span><span class="sxs-lookup"><span data-stu-id="678e7-157">The publication must have a compatibility level of 90RTM or greater.</span></span> <span data-ttu-id="678e7-158">如需詳細資訊，請參閱[複寫回溯相容性](../replication-backward-compatibility.md)中的＜發行集相容性層級＞一節。</span><span class="sxs-lookup"><span data-stu-id="678e7-158">For more information, see the "Publication Compatibility Level" section of [Replication Backward Compatibility](../replication-backward-compatibility.md).</span></span>

-   <span data-ttu-id="678e7-159">發行集必須使用原生快照集模式。</span><span class="sxs-lookup"><span data-stu-id="678e7-159">The publication must use native snapshot mode.</span></span> <span data-ttu-id="678e7-160">此為預設值，除非您要複寫到不支援邏輯記錄的 [!INCLUDE[ssEW](../../../includes/ssew-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="678e7-160">This is the default unless you are replicating to [!INCLUDE[ssEW](../../../includes/ssew-md.md)], which does not support logical records.</span></span>

-   <span data-ttu-id="678e7-161">發行集不允許 Web 同步處理。</span><span class="sxs-lookup"><span data-stu-id="678e7-161">The publication cannot allow Web synchronization.</span></span> <span data-ttu-id="678e7-162">如需有關 Web 同步處理的詳細資訊，請參閱＜ [Web Synchronization for Merge Replication](../web-synchronization-for-merge-replication.md)＞。</span><span class="sxs-lookup"><span data-stu-id="678e7-162">For more information about Web synchronization, see [Web Synchronization for Merge Replication](../web-synchronization-for-merge-replication.md).</span></span>

-   <span data-ttu-id="678e7-163">為了在篩選的發行集中使用邏輯記錄：</span><span class="sxs-lookup"><span data-stu-id="678e7-163">In order to use logical records on a filtered publication:</span></span>

    -   <span data-ttu-id="678e7-164">必須同時使用預先計算資料分割。</span><span class="sxs-lookup"><span data-stu-id="678e7-164">Precomputed partitions must also be used.</span></span> <span data-ttu-id="678e7-165">對預先計算資料分割的要求也同樣適用於邏輯記錄。</span><span class="sxs-lookup"><span data-stu-id="678e7-165">The requirements of precomputed partitions also apply to logical records.</span></span> <span data-ttu-id="678e7-166">如需詳細資訊，請參閱[使用預先計算的資料分割最佳化參數化篩選效能](parameterized-filters-optimize-for-precomputed-partitions.md)。</span><span class="sxs-lookup"><span data-stu-id="678e7-166">For more information, see [Optimize Parameterized Filter Performance with Precomputed Partitions](parameterized-filters-optimize-for-precomputed-partitions.md).</span></span>

    -   <span data-ttu-id="678e7-167">無法使用不重疊的參數化篩選。</span><span class="sxs-lookup"><span data-stu-id="678e7-167">You cannot use nonoverlapping parameterized filters.</span></span> <span data-ttu-id="678e7-168">如需詳細資訊，請參閱＜ [Parameterized Row Filters](parameterized-filters-parameterized-row-filters.md)＞的「設定資料分割選項」一節。</span><span class="sxs-lookup"><span data-stu-id="678e7-168">For more information, see the "Setting 'partition options'" section of [Parameterized Row Filters](parameterized-filters-parameterized-row-filters.md).</span></span>

-   <span data-ttu-id="678e7-169">如果發行集使用聯結篩選，則對於邏輯記錄關聯性中涉及的所有聯結篩選，其 **聯結唯一索引鍵** 屬性都必須設定為 **true** 。</span><span class="sxs-lookup"><span data-stu-id="678e7-169">If the publication uses join filters, the **join unique key** property must be set to **true** for all join filters that are involved in logical record relationships.</span></span> <span data-ttu-id="678e7-170">如需相關資訊，請參閱 [Join Filters](join-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="678e7-170">For more information, see [Join Filters](join-filters.md).</span></span>

### <a name="relationships-between-tables"></a><span data-ttu-id="678e7-171">資料表之間的關聯性</span><span class="sxs-lookup"><span data-stu-id="678e7-171">Relationships Between Tables</span></span>

-   <span data-ttu-id="678e7-172">透過邏輯記錄相關聯的資料表必須具有主索引鍵與外部索引鍵的關聯性。</span><span class="sxs-lookup"><span data-stu-id="678e7-172">Tables related through logical records must have a primary key-foreign key relationship.</span></span>

-   <span data-ttu-id="678e7-173">無法為外部索引鍵條件約束設定 NOT FOR REPLICATION 選項。</span><span class="sxs-lookup"><span data-stu-id="678e7-173">The NOT FOR REPLICATION option cannot be set for foreign key constraints.</span></span>

-   <span data-ttu-id="678e7-174">多個子資料表可以只有一個父資料表。</span><span class="sxs-lookup"><span data-stu-id="678e7-174">Child tables can have only one parent table.</span></span>

     <span data-ttu-id="678e7-175">例如，追蹤班級和學生的資料庫設計可能類似於：</span><span class="sxs-lookup"><span data-stu-id="678e7-175">For example, a database tracking classes and students might have a design similar to:</span></span>

     <span data-ttu-id="678e7-176">![具有超過一個父系資料表的子系資料表](../media/logical-records-03.gif "具有超過一個父系資料表的子系資料表")</span><span class="sxs-lookup"><span data-stu-id="678e7-176">![Child table with more than one parent table](../media/logical-records-03.gif "Child table with more than one parent table")</span></span>

     <span data-ttu-id="678e7-177">無法使用邏輯記錄來代表此關聯性中的三個資料表，因為 **ClassMembers** 中的資料列並未與單一主索引鍵資料列相關聯。</span><span class="sxs-lookup"><span data-stu-id="678e7-177">You cannot use a logical record to represent the three tables in this relationship, because the rows in **ClassMembers** are not associated with a single primary key row.</span></span> <span data-ttu-id="678e7-178">資料表 **Classes** 和 **ClassMembers** 仍然可以組成邏輯記錄，資料表 **ClassMembers** 和 **Students**也可以，但是三個資料表一起則不行。</span><span class="sxs-lookup"><span data-stu-id="678e7-178">The tables **Classes** and **ClassMembers** could still form a logical record, as could the tables **ClassMembers** and **Students**, but not all three.</span></span>

-   <span data-ttu-id="678e7-179">發行集不能包含循環聯結篩選關聯性。</span><span class="sxs-lookup"><span data-stu-id="678e7-179">The publication cannot contain circular join filter relationships.</span></span>

     <span data-ttu-id="678e7-180">以包含資料表 **Customers**、 **Orders**和 **OrderItems**為例，如果 **Orders** 資料表同樣具有參考到 **OrderItems** 資料表的外部索引鍵條件約束，則無法使用邏輯記錄。</span><span class="sxs-lookup"><span data-stu-id="678e7-180">Using the example with the tables **Customers**, **Orders**, and **OrderItems**, you could not use logical records if the **Orders** table also had a foreign key constraint that referenced the **OrderItems** table.</span></span>

## <a name="performance-implications-of-logical-records"></a><span data-ttu-id="678e7-181">邏輯記錄的效能含意</span><span class="sxs-lookup"><span data-stu-id="678e7-181">Performance implications of logical records</span></span>
 <span data-ttu-id="678e7-182">邏輯記錄功能會帶來效能成本。</span><span class="sxs-lookup"><span data-stu-id="678e7-182">The logical record feature does come with a performance cost.</span></span> <span data-ttu-id="678e7-183">如果不使用邏輯記錄，複寫代理程式可以同時處理給定發行項的所有變更，同時由於變更會按資料列逐一套用，因此套用變更所需的鎖定及交易記錄檔要求便最小。</span><span class="sxs-lookup"><span data-stu-id="678e7-183">If logical records are not used, the replication agent can process all of the changes for a given article at the same time, and because the changes are applied in a row-by-row fashion, the locking and transaction log requirements necessary for applying the changes are minimal.</span></span>

 <span data-ttu-id="678e7-184">如果使用邏輯記錄，「合併代理程式」必須同時處理各完整邏輯記錄的變更。</span><span class="sxs-lookup"><span data-stu-id="678e7-184">If logical records are used, the Merge Agent must process the changes for each entire logical record together.</span></span> <span data-ttu-id="678e7-185">這會影響「合併代理程式」複寫資料列所需的時間。</span><span class="sxs-lookup"><span data-stu-id="678e7-185">This has an effect on the amount of time it takes the Merge Agent to replicate the rows.</span></span> <span data-ttu-id="678e7-186">此外，由於代理程式會為每個邏輯記錄單獨開啟一個交易，因此鎖定的要求也會增加。</span><span class="sxs-lookup"><span data-stu-id="678e7-186">Additionally, because the agent opens a separate transaction for each logical record, locking requirements can increase.</span></span>

## <a name="see-also"></a><span data-ttu-id="678e7-187">另請參閱</span><span class="sxs-lookup"><span data-stu-id="678e7-187">See Also</span></span>
 [<span data-ttu-id="678e7-188">合併式複寫的發行項選項</span><span class="sxs-lookup"><span data-stu-id="678e7-188">Article Options for Merge Replication</span></span>](article-options-for-merge-replication.md)


