---
title: 偵測和解決邏輯記錄中的衝突 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- logical records [SQL Server replication]
- conflict resolution [SQL Server replication], merge replication
ms.assetid: f2e55040-ca69-4ccf-97d1-c362e1633f26
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f9822cd153af67538a36a894de0ec1b4716e54cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584460"
---
# <a name="detecting-and-resolving-conflicts-in-logical-records"></a><span data-ttu-id="8e39d-102">Detecting and Resolving Conflicts in Logical Records</span><span class="sxs-lookup"><span data-stu-id="8e39d-102">Detecting and Resolving Conflicts in Logical Records</span></span>
  <span data-ttu-id="8e39d-103">本主題涵蓋使用邏輯記錄時，可能會用到的衝突偵測和衝突解決方法之不同組合。</span><span class="sxs-lookup"><span data-stu-id="8e39d-103">This topic covers the various combinations of conflict detection and conflict resolution approaches possible when using logical records.</span></span> <span data-ttu-id="8e39d-104">如果多個節點變更了相同的資料，或合併式複寫在複寫變更時遇到某種類型的錯誤 (例如，條件約束違規)，則合併式複寫中就會發生衝突。</span><span class="sxs-lookup"><span data-stu-id="8e39d-104">A conflict in merge replication occurs when more than one node changes the same data, or merge replication encounters certain types of errors, such as a constraint violation, when replicating changes.</span></span> <span data-ttu-id="8e39d-105">如需衝突偵測和解決的詳細資訊，請參閱＜ [Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md)＞。</span><span class="sxs-lookup"><span data-stu-id="8e39d-105">For more information about conflict detection and resolution, see [Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md).</span></span>

 <span data-ttu-id="8e39d-106">若要指定發行項的衝突追蹤與解決層級，請參閱＜ [指定合併發行項的衝突追蹤與解決層級](../publish/specify-merge-replication-properties.md#interactive-conflict-resolution)＞。</span><span class="sxs-lookup"><span data-stu-id="8e39d-106">To specify the conflict tracking and resolution level for an article, see [Specify the Conflict Tracking and Resolution Level for Merge Articles](../publish/specify-merge-replication-properties.md#interactive-conflict-resolution).</span></span>

## <a name="conflict-detection"></a><span data-ttu-id="8e39d-107">衝突偵測</span><span class="sxs-lookup"><span data-stu-id="8e39d-107">Conflict Detection</span></span>
 <span data-ttu-id="8e39d-108">偵測邏輯記錄衝突的方法是由兩個發行項屬性所決定： **column_tracking** 和 **logical_record_level_conflict_detection**。</span><span class="sxs-lookup"><span data-stu-id="8e39d-108">The way in which conflicts are detected for logical records is determined by two article properties: **column_tracking** and **logical_record_level_conflict_detection**.</span></span> [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] <span data-ttu-id="8e39d-109">及更新版本也支援邏輯記錄層級的偵測。</span><span class="sxs-lookup"><span data-stu-id="8e39d-109">and later versions also support logical record-level detection.</span></span>

 <span data-ttu-id="8e39d-110">**logical_record_level_conflict_detection** 發行項屬性可設定為 TRUE 或 FALSE。</span><span class="sxs-lookup"><span data-stu-id="8e39d-110">The **logical_record_level_conflict_detection** article property can be set to TRUE or FALSE.</span></span> <span data-ttu-id="8e39d-111">只應為最上層父發行項設定此值，子發行項會忽略此值。</span><span class="sxs-lookup"><span data-stu-id="8e39d-111">The value should only be set for the top-level parent article and will be ignored by child articles.</span></span> <span data-ttu-id="8e39d-112">如果該值為 FALSE，則合併式複寫會如舊版 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中一樣，僅依據發行項之 **column_tracking** 屬性的值來偵測衝突。</span><span class="sxs-lookup"><span data-stu-id="8e39d-112">If this value is FALSE, merge replication detects conflicts as in previous versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], based solely on the value of the **column_tracking** property for the article.</span></span> <span data-ttu-id="8e39d-113">如果該值為 TRUE，則合併式複寫將忽略發行項的 **column_tracking** 屬性，並且如果在邏輯記錄中任意處進行變更，它便會偵測衝突。</span><span class="sxs-lookup"><span data-stu-id="8e39d-113">If this value is TRUE, merge replication will ignore the **column_tracking** property of the article, and detect a conflict if changes are made anywhere in the logical record.</span></span> <span data-ttu-id="8e39d-114">例如，請考慮以下的狀況：</span><span class="sxs-lookup"><span data-stu-id="8e39d-114">For example, consider this scenario:</span></span>

 <span data-ttu-id="8e39d-115">![具有值的三個資料表邏輯記錄](../media/logical-records-05.gif "具有值的三個資料表邏輯記錄")</span><span class="sxs-lookup"><span data-stu-id="8e39d-115">![Three table logical record with values](../media/logical-records-05.gif "Three table logical record with values")</span></span>

 <span data-ttu-id="8e39d-116">如果兩個使用者變更 **Customers**、 **Orders**或 **OrderItems** 資料表中 Customer2 邏輯記錄的任何值，則會偵測到衝突。</span><span class="sxs-lookup"><span data-stu-id="8e39d-116">A conflict is detected if two users change any values for the Customer2 logical record in the **Customers**, **Orders**, or **OrderItems** tables.</span></span> <span data-ttu-id="8e39d-117">此範例涉及透過 UPDATE 陳述式進行變更，但是也可透過 INSERT 或 DELETE 陳述式所作的變更偵測衝突。</span><span class="sxs-lookup"><span data-stu-id="8e39d-117">This example involves changes made via an UPDATE statement, but the conflict can also be detected by changes made with INSERT or DELETE statements.</span></span>

## <a name="conflict-resolution"></a><span data-ttu-id="8e39d-118">衝突解決</span><span class="sxs-lookup"><span data-stu-id="8e39d-118">Conflict Resolution</span></span>
 <span data-ttu-id="8e39d-119">依預設，合併式複寫使用以優先權為基礎的邏輯來解決衝突。</span><span class="sxs-lookup"><span data-stu-id="8e39d-119">By default, merge replication uses priority-based logic to resolve conflicts.</span></span> <span data-ttu-id="8e39d-120">如果在兩個「訂閱者」資料庫中進行衝突變更，則具有較高訂閱優先權的「訂閱者」變更獲勝，或者如果優先權相同，則第一個到達「發行者」的變更獲勝。</span><span class="sxs-lookup"><span data-stu-id="8e39d-120">If a conflicting change is made in two Subscriber databases, the change for the Subscriber with the higher subscription priority wins, or if the priority is the same, the first change to reach the Publisher wins.</span></span> <span data-ttu-id="8e39d-121">使用資料列層級和資料行層級的偵測，整個獲勝資料列會永遠覆寫失敗資料列。</span><span class="sxs-lookup"><span data-stu-id="8e39d-121">With row-level and column-level detection, the entire winning row always overwrites the losing row.</span></span>

 <span data-ttu-id="8e39d-122">**logical_record_level_conflict_resolution** 發行項屬性可設定為 TRUE 或 FALSE。</span><span class="sxs-lookup"><span data-stu-id="8e39d-122">The **logical_record_level_conflict_resolution** article property can be set to TRUE or FALSE.</span></span> <span data-ttu-id="8e39d-123">只應為最上層父發行項設定此值，子發行項會忽略此值。</span><span class="sxs-lookup"><span data-stu-id="8e39d-123">The value should only be set for the top-level parent article and will be ignored by child articles.</span></span> <span data-ttu-id="8e39d-124">如果該值為 TRUE，則整個獲勝邏輯記錄會覆寫失敗邏輯記錄。</span><span class="sxs-lookup"><span data-stu-id="8e39d-124">If the value is TRUE, the entire winning logical record overwrites the losing logical record.</span></span> <span data-ttu-id="8e39d-125">如果它為 FALSE，則個別獲勝資料列可來自於不同的「訂閱者」或「發行者」。</span><span class="sxs-lookup"><span data-stu-id="8e39d-125">If it is FALSE, individual winning rows can come from different Subscribers or Publishers.</span></span> <span data-ttu-id="8e39d-126">例如，訂閱者 A 可以在 **Orders** 資料表的資料列之衝突中獲勝，而訂閱者 B 則可在 **OrderItems** 資料表的相關資料列之衝突中獲勝。</span><span class="sxs-lookup"><span data-stu-id="8e39d-126">For example, Subscriber A could win a conflict on a row from the **Orders** table, and Subscriber B could win on a related row from the **OrderItems** table.</span></span> <span data-ttu-id="8e39d-127">結果是訂閱者 A 的 **Orders** 資料列和訂閱者 B 的 **OrderItems** 資料列之邏輯記錄。</span><span class="sxs-lookup"><span data-stu-id="8e39d-127">The result is a logical record with the **Orders** row from Subscriber A and the **OrderItems** row from Subscriber B.</span></span>

## <a name="interaction-of-conflict-resolution-and-detection-settings"></a><span data-ttu-id="8e39d-128">衝突解決和偵測設定的互動</span><span class="sxs-lookup"><span data-stu-id="8e39d-128">Interaction of Conflict Resolution and Detection Settings</span></span>
 <span data-ttu-id="8e39d-129">衝突的結果取決於衝突偵測和解決設定之間的互動。</span><span class="sxs-lookup"><span data-stu-id="8e39d-129">The outcome of conflicts depends on the interaction of conflict detection and resolution settings.</span></span> <span data-ttu-id="8e39d-130">下列範例假設使用以優先權為基礎的衝突解決方式。</span><span class="sxs-lookup"><span data-stu-id="8e39d-130">For the examples below, it is assumed that the priority-based conflict resolution is being used.</span></span> <span data-ttu-id="8e39d-131">使用邏輯記錄時，有下列幾種可能性：</span><span class="sxs-lookup"><span data-stu-id="8e39d-131">When using logical records, the possibilities are:</span></span>

-   <span data-ttu-id="8e39d-132">資料列或資料行層級偵測與資料列層級解決</span><span class="sxs-lookup"><span data-stu-id="8e39d-132">Row or column level detection, row level resolution</span></span>

-   <span data-ttu-id="8e39d-133">資料行層級偵測與邏輯記錄解決</span><span class="sxs-lookup"><span data-stu-id="8e39d-133">Column level detection, logical record resolution</span></span>

-   <span data-ttu-id="8e39d-134">資料列層級偵測與邏輯記錄解決</span><span class="sxs-lookup"><span data-stu-id="8e39d-134">Row level detection, logical record resolution</span></span>

-   <span data-ttu-id="8e39d-135">邏輯記錄偵測與邏輯記錄解決</span><span class="sxs-lookup"><span data-stu-id="8e39d-135">Logical record detection, logical record resolution</span></span>

### <a name="row-or-column-level-detection-row-level-resolution"></a><span data-ttu-id="8e39d-136">資料列或資料行層級偵測與資料列層級解決</span><span class="sxs-lookup"><span data-stu-id="8e39d-136">Row or Column Level Detection, Row Level Resolution</span></span>
 <span data-ttu-id="8e39d-137">在這個範例中，發行集是以下列資料設定：</span><span class="sxs-lookup"><span data-stu-id="8e39d-137">In this example, the publication is configured with:</span></span>

-   <span data-ttu-id="8e39d-138">**column_tracking** 為 TRUE 或 FALSE</span><span class="sxs-lookup"><span data-stu-id="8e39d-138">**column_tracking** is TRUE or FALSE</span></span>

-   <span data-ttu-id="8e39d-139">**logical_record_level_conflict_detection** 為 FALSE</span><span class="sxs-lookup"><span data-stu-id="8e39d-139">**logical_record_level_conflict_detection** is FALSE</span></span>

-   <span data-ttu-id="8e39d-140">**logical_record_level_conflict_resolution** 為 FALSE</span><span class="sxs-lookup"><span data-stu-id="8e39d-140">**logical_record_level_conflict_resolution** is FALSE</span></span>

 <span data-ttu-id="8e39d-141">在此情況下，偵測位於資料列或資料行層級，解決則位於資料列層級。</span><span class="sxs-lookup"><span data-stu-id="8e39d-141">In this case, detection is at the row or column level and resolution is at the row level.</span></span> <span data-ttu-id="8e39d-142">使用這些設定以便利用下列方法：將邏輯記錄的所有變更複寫為一個單位，但在邏輯記錄層級中沒有衝突偵測或解決。</span><span class="sxs-lookup"><span data-stu-id="8e39d-142">These settings are used to take advantage of having all changes to a logical record replicate as a unit, but without conflict detection or resolution at the logical record level.</span></span>

### <a name="column-level-detection-logical-record-resolution"></a><span data-ttu-id="8e39d-143">資料行層級偵測與邏輯記錄解決</span><span class="sxs-lookup"><span data-stu-id="8e39d-143">Column Level Detection, Logical Record Resolution</span></span>
 <span data-ttu-id="8e39d-144">在這個範例中，發行集是以下列資料設定：</span><span class="sxs-lookup"><span data-stu-id="8e39d-144">In this example, the publication is configured with:</span></span>

-   <span data-ttu-id="8e39d-145">**column_tracking** 為 TRUE</span><span class="sxs-lookup"><span data-stu-id="8e39d-145">**column_tracking** is TRUE</span></span>

-   <span data-ttu-id="8e39d-146">**logical_record_level_conflict_detection** 為 FALSE</span><span class="sxs-lookup"><span data-stu-id="8e39d-146">**logical_record_level_conflict_detection** is FALSE</span></span>

-   <span data-ttu-id="8e39d-147">**logical_record_level_conflict_resolution** 為 TRUE</span><span class="sxs-lookup"><span data-stu-id="8e39d-147">**logical_record_level_conflict_resolution** is TRUE</span></span>

 <span data-ttu-id="8e39d-148">「發行者」和「訂閱者」以相同的資料集開始，且邏輯記錄在 **orders** 和 **customers** 資料表之間定義。</span><span class="sxs-lookup"><span data-stu-id="8e39d-148">A Publisher and Subscriber start with the same data set, and a logical record is defined between the **orders** and **customers** tables.</span></span> <span data-ttu-id="8e39d-149">「發行者」變更 **customers** 資料表中的 **custcol1** 資料行和 **orders** 資料表中的 **ordercol1** 。</span><span class="sxs-lookup"><span data-stu-id="8e39d-149">The Publisher changes the **custcol1** column in the **customers** table and the **ordercol1** in the **orders** table.</span></span> <span data-ttu-id="8e39d-150">「訂閱者」變更 **customers** 資料表中相同資料列的 **custcol1** 和 **orders** 資料表中相同資料列的 **ordercol2** 資料行。</span><span class="sxs-lookup"><span data-stu-id="8e39d-150">The Subscriber changes **custcol1** in the same row of the **customers** table and the **ordercol2** column in the same row of the **orders** table.</span></span> <span data-ttu-id="8e39d-151">對 **customer** 資料表中相同資料行進行變更會導致衝突，但是對 **orders** 資料表進行變更則不會。</span><span class="sxs-lookup"><span data-stu-id="8e39d-151">The changes to the same column in the **customer** table result in a conflict, but the changes to the **orders** table are not in conflict.</span></span>

 <span data-ttu-id="8e39d-152">由於衝突在邏輯記錄層級解決，因此「發行者」上所作的獲勝變更，會取代複寫處理期間在「訂閱者」資料表中所作的變更。</span><span class="sxs-lookup"><span data-stu-id="8e39d-152">Because the conflicts are resolved at the logical record level, the winning changes made at the Publisher replace the changes made in the Subscriber tables during replication processing.</span></span>

 <span data-ttu-id="8e39d-153">![顯示相關資料列之變更的資料表系列](../media/logical-records-06.gif "顯示相關資料列之變更的資料表系列")</span><span class="sxs-lookup"><span data-stu-id="8e39d-153">![Series of tables showing changes to related rows](../media/logical-records-06.gif "Series of tables showing changes to related rows")</span></span>

### <a name="row-level-detection-logical-record-resolution"></a><span data-ttu-id="8e39d-154">資料列層級偵測與邏輯記錄解決</span><span class="sxs-lookup"><span data-stu-id="8e39d-154">Row Level Detection, Logical Record Resolution</span></span>
 <span data-ttu-id="8e39d-155">在這個範例中，發行集是以下列資料設定：</span><span class="sxs-lookup"><span data-stu-id="8e39d-155">In this example, the publication is configured with:</span></span>

-   <span data-ttu-id="8e39d-156">**column_tracking** 為 FALSE</span><span class="sxs-lookup"><span data-stu-id="8e39d-156">**column_tracking** is FALSE</span></span>

-   <span data-ttu-id="8e39d-157">**logical_record_level_conflict_detection** 為 FALSE</span><span class="sxs-lookup"><span data-stu-id="8e39d-157">**logical_record_level_conflict_detection** is FALSE</span></span>

-   <span data-ttu-id="8e39d-158">**logical_record_level_conflict_resolution** 為 TRUE</span><span class="sxs-lookup"><span data-stu-id="8e39d-158">**logical_record_level_conflict_resolution** is TRUE</span></span>

 <span data-ttu-id="8e39d-159">發行者與訂閱者以相同的資料集開始。</span><span class="sxs-lookup"><span data-stu-id="8e39d-159">A Publisher and Subscriber start with the same data set.</span></span> <span data-ttu-id="8e39d-160">發行者變更 **customers** 資料表中的 **custcol1** 資料行。</span><span class="sxs-lookup"><span data-stu-id="8e39d-160">The Publisher changes the **custcol1** column in the **customers** table.</span></span> <span data-ttu-id="8e39d-161">「訂閱者」變更 **customers** 資料表中的 **custcol2** 和 **orders** 資料表中的 **ordercol2** 資料行。</span><span class="sxs-lookup"><span data-stu-id="8e39d-161">The Subscriber changes **custcol2** in the **customers** table and the **ordercol2** column in the **orders** table.</span></span> <span data-ttu-id="8e39d-162">對 **customers** 資料表中相同資料列所作的變更會導致衝突，但是對 **orders** 資料表所作的「訂閱者」變更則不會衝突。</span><span class="sxs-lookup"><span data-stu-id="8e39d-162">The changes to the same row in the **customers** table result in a conflict, but the Subscriber changes to the **orders** table are not in conflict.</span></span>

 <span data-ttu-id="8e39d-163">由於衝突在邏輯記錄層級解決，因此同步處理期間，在「發行者」上的獲勝變更會取代「訂閱者」資料表中所作的變更。</span><span class="sxs-lookup"><span data-stu-id="8e39d-163">Because the conflicts are resolved at the logical record level, during synchronization the winning changes made at the Publisher replace the changes made in the Subscriber tables.</span></span>

 <span data-ttu-id="8e39d-164">![顯示相關資料列之變更的資料表系列](../media/logical-records-07.gif "顯示相關資料列之變更的資料表系列")</span><span class="sxs-lookup"><span data-stu-id="8e39d-164">![Series of tables showing changes to related rows](../media/logical-records-07.gif "Series of tables showing changes to related rows")</span></span>

### <a name="logical-record-detection-logical-record-resolution"></a><span data-ttu-id="8e39d-165">邏輯記錄偵測與邏輯記錄解決</span><span class="sxs-lookup"><span data-stu-id="8e39d-165">Logical Record Detection, Logical Record Resolution</span></span>
 <span data-ttu-id="8e39d-166">在這個範例中，發行集是以下列資料設定：</span><span class="sxs-lookup"><span data-stu-id="8e39d-166">In this example, the publication is configured with:</span></span>

-   <span data-ttu-id="8e39d-167">**logical_record_level_conflict_detection** 為 TRUE</span><span class="sxs-lookup"><span data-stu-id="8e39d-167">**logical_record_level_conflict_detection** is TRUE</span></span>

-   <span data-ttu-id="8e39d-168">**logical_record_level_conflict_resolution** 為 TRUE</span><span class="sxs-lookup"><span data-stu-id="8e39d-168">**logical_record_level_conflict_resolution** is TRUE</span></span>

 <span data-ttu-id="8e39d-169">發行者與訂閱者以相同的資料集開始。</span><span class="sxs-lookup"><span data-stu-id="8e39d-169">A Publisher and Subscriber start with the same data set.</span></span> <span data-ttu-id="8e39d-170">發行者變更 **customers** 資料表中的 **custcol1** 資料行。</span><span class="sxs-lookup"><span data-stu-id="8e39d-170">The Publisher changes the **custcol1** column in the **customers** table.</span></span> <span data-ttu-id="8e39d-171">「訂閱者」變更 **orders** 資料表中的 **ordercol1** 資料行。</span><span class="sxs-lookup"><span data-stu-id="8e39d-171">The Subscriber changes the **ordercol1** column in the **orders** table.</span></span> <span data-ttu-id="8e39d-172">相同資料列或資料行無變更，但是由於在 **custid**=1 的相同邏輯記錄中進行了變更，因此在邏輯記錄層級變更會被偵測為衝突。</span><span class="sxs-lookup"><span data-stu-id="8e39d-172">There are no changes to the same row or columns, but because the changes are made in the same logical record for **custid**=1, the changes are detected as a conflict at the logical record level.</span></span>

 <span data-ttu-id="8e39d-173">由於衝突也在邏輯記錄層級解決，因此同步處理期間，在「發行者」上所作的獲勝變更會取代「訂閱者」資料表中所作的變更。</span><span class="sxs-lookup"><span data-stu-id="8e39d-173">Because the conflicts are also resolved at the logical record level, during synchronization the winning change made at the Publisher replaces the change made in the Subscriber tables.</span></span>

 <span data-ttu-id="8e39d-174">![顯示相關資料列之變更的資料表系列](../media/logical-records-08.gif "顯示相關資料列之變更的資料表系列")</span><span class="sxs-lookup"><span data-stu-id="8e39d-174">![Series of tables showing changes to related rows](../media/logical-records-08.gif "Series of tables showing changes to related rows")</span></span>

## <a name="see-also"></a><span data-ttu-id="8e39d-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e39d-175">See Also</span></span>
 [<span data-ttu-id="8e39d-176">使用邏輯記錄分組相關資料列的變更</span><span class="sxs-lookup"><span data-stu-id="8e39d-176">Group Changes to Related Rows with Logical Records</span></span>](group-changes-to-related-rows-with-logical-records.md)


