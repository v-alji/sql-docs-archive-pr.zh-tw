---
title: 索引磁碟空間範例 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- online index disk space
- disk space [SQL Server], indexes
- index disk space [SQL Server]
- space [SQL Server], indexes
- indexes [SQL Server], disk space requirements
- offline index disk space [SQL Server]
ms.assetid: e5c71f55-0be3-4c93-97e9-7b3455c8f581
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e4a30c6ce986095496a11c41f3102d095e8c632b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595979"
---
# <a name="index-disk-space-example"></a><span data-ttu-id="7120e-102">索引磁碟空間範例</span><span class="sxs-lookup"><span data-stu-id="7120e-102">Index Disk Space Example</span></span>
  <span data-ttu-id="7120e-103">無論何時建立、重建或卸除索引，舊結構 (來源) 和新結構 (目標) 兩者在它們適當的檔案和檔案群組中都需要磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="7120e-103">Whenever an index is created, rebuilt, or dropped, disk space for both the old (source) and new (target) structures is required in their appropriate files and filegroups.</span></span> <span data-ttu-id="7120e-104">舊結構要到索引建立交易認可時才會取消配置。</span><span class="sxs-lookup"><span data-stu-id="7120e-104">The old structure is not deallocated until the index creation transaction commits.</span></span> <span data-ttu-id="7120e-105">此時也可能會需要額外暫存磁碟空間，以供排序作業。</span><span class="sxs-lookup"><span data-stu-id="7120e-105">Additional temporary disk space for sorting operations may also be needed.</span></span> <span data-ttu-id="7120e-106">如需詳細資訊，請參閱 [Disk Space Requirements for Index DDL Operations](disk-space-requirements-for-index-ddl-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="7120e-106">For more information, see [Disk Space Requirements for Index DDL Operations](disk-space-requirements-for-index-ddl-operations.md).</span></span>  
  
 <span data-ttu-id="7120e-107">在此範例中，會決定建立叢集索引的磁碟空間需求。</span><span class="sxs-lookup"><span data-stu-id="7120e-107">In this example, disk space requirements to create a clustered index are determined.</span></span>  
  
 <span data-ttu-id="7120e-108">假設在建立叢集索引之前，發生下列狀況：</span><span class="sxs-lookup"><span data-stu-id="7120e-108">Assume the following conditions are true before creating the clustered index:</span></span>  
  
-   <span data-ttu-id="7120e-109">現有的資料表 (堆積) 包含 1 百萬個資料列。</span><span class="sxs-lookup"><span data-stu-id="7120e-109">The existing table (heap) contains 1 million rows.</span></span> <span data-ttu-id="7120e-110">每一個資料列的長度為 200 位元組。</span><span class="sxs-lookup"><span data-stu-id="7120e-110">Each row is 200 bytes long.</span></span>  
  
-   <span data-ttu-id="7120e-111">非叢集索引 A 包含 1 百萬個資料列。</span><span class="sxs-lookup"><span data-stu-id="7120e-111">Nonclustered index A contains 1 million rows.</span></span> <span data-ttu-id="7120e-112">每一個資料列的長度為 50 位元組。</span><span class="sxs-lookup"><span data-stu-id="7120e-112">Each row is 50 bytes long.</span></span>  
  
-   <span data-ttu-id="7120e-113">非叢集索引 B 包含 1 百萬個資料列。</span><span class="sxs-lookup"><span data-stu-id="7120e-113">Nonclustered index B contains 1 million rows.</span></span> <span data-ttu-id="7120e-114">每一個資料列的長度為 80 位元組。</span><span class="sxs-lookup"><span data-stu-id="7120e-114">Each row is 80 bytes long.</span></span>  
  
-   <span data-ttu-id="7120e-115">index create memory 選項設定為 2 MB。</span><span class="sxs-lookup"><span data-stu-id="7120e-115">The index create memory option is set to 2 MB.</span></span>  
  
-   <span data-ttu-id="7120e-116">所有現有的和新的索引採用 80 的填滿因數值。</span><span class="sxs-lookup"><span data-stu-id="7120e-116">A fill factor value of 80 is used for all existing and new indexes.</span></span> <span data-ttu-id="7120e-117">這表示有 80% 的分頁是滿的。</span><span class="sxs-lookup"><span data-stu-id="7120e-117">This means the pages are 80 percent full.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7120e-118">建立叢集索引之後，必須重建兩個非叢集索引以取代有新的叢集索引鍵的資料列指標。</span><span class="sxs-lookup"><span data-stu-id="7120e-118">As a result of creating a clustered index, the two nonclustered indexes must be rebuilt to replace the row indicator with the new clustered index key.</span></span>  
  
## <a name="disk-space-calculations-for-an-offline-index-operation"></a><span data-ttu-id="7120e-119">離線索引作業的磁碟空間計算</span><span class="sxs-lookup"><span data-stu-id="7120e-119">Disk Space Calculations for an Offline Index Operation</span></span>  
 <span data-ttu-id="7120e-120">下列步驟中，會計算索引作業期間使用的暫存磁碟空間和儲存新索引的永久磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="7120e-120">In the following steps, both temporary disk space to be used during the index operation and permanent disk space to store the new indexes are calculated.</span></span> <span data-ttu-id="7120e-121">顯示的計算是近似值；結果是四捨五入並且只考慮索引分葉層級的大小。</span><span class="sxs-lookup"><span data-stu-id="7120e-121">The calculations shown are approximate; results are rounded up and consider only the size of index leaf level.</span></span> <span data-ttu-id="7120e-122">波浪號 (~) 是用來表示近似的計算。</span><span class="sxs-lookup"><span data-stu-id="7120e-122">The tilde (~) is used to indicate approximate calculations.</span></span>  
  
1.  <span data-ttu-id="7120e-123">決定來源結構的大小。</span><span class="sxs-lookup"><span data-stu-id="7120e-123">Determine the size of the source structures.</span></span>  
  
     <span data-ttu-id="7120e-124">堆積：1 百萬 \* 200 位元組 ~ 200 MB</span><span class="sxs-lookup"><span data-stu-id="7120e-124">Heap: 1 million \* 200 bytes ~ 200 MB</span></span>  
  
     <span data-ttu-id="7120e-125">非叢集索引 A：1 百萬 \* 50 位元組 / 80% ~ 63 MB</span><span class="sxs-lookup"><span data-stu-id="7120e-125">Nonclustered index A: 1 million \* 50 bytes / 80% ~ 63 MB</span></span>  
  
     <span data-ttu-id="7120e-126">非叢集索引 B：1 百萬 \* 80 位元組 / 80% ~ 100 MB</span><span class="sxs-lookup"><span data-stu-id="7120e-126">Nonclustered index B: 1 million \* 80 bytes / 80% ~ 100 MB</span></span>  
  
     <span data-ttu-id="7120e-127">現有結構的總計大小：363 MB</span><span class="sxs-lookup"><span data-stu-id="7120e-127">Total size of existing structures: 363 MB</span></span>  
  
2.  <span data-ttu-id="7120e-128">決定目標索引結構的大小。</span><span class="sxs-lookup"><span data-stu-id="7120e-128">Determine the size of the target index structures.</span></span> <span data-ttu-id="7120e-129">假設新的叢集索引鍵的長度是 24 個位元組，包含唯一識別值。</span><span class="sxs-lookup"><span data-stu-id="7120e-129">Assume that the new clustered key is 24 bytes long including a uniqueifier.</span></span> <span data-ttu-id="7120e-130">兩個非叢集索引的資料列指標 (長度為 8 個位元組) 會以此叢集索引鍵取代。</span><span class="sxs-lookup"><span data-stu-id="7120e-130">The row indicator (8 bytes long) in both nonclustered indexes will be replaced by this clustered key.</span></span>  
  
     <span data-ttu-id="7120e-131">叢集索引：1 百萬 \* 200 位元組 / 80% ~ 250 MB</span><span class="sxs-lookup"><span data-stu-id="7120e-131">Clustered index: 1 million \* 200 bytes / 80% ~ 250 MB</span></span>  
  
     <span data-ttu-id="7120e-132">非叢集索引 A：1 百萬 \* (50 - 8 + 24) 位元組 / 80% ~ 83 MB</span><span class="sxs-lookup"><span data-stu-id="7120e-132">Nonclustered index A: 1 million \* (50 - 8 + 24) bytes / 80% ~ 83 MB</span></span>  
  
     <span data-ttu-id="7120e-133">非叢集索引 B：1 百萬 \* (80 - 8 + 24) 位元組 / 80% ~ 120 MB</span><span class="sxs-lookup"><span data-stu-id="7120e-133">Nonclustered index B: 1 million \* (80 - 8 + 24) bytes / 80% ~ 120 MB</span></span>  
  
     <span data-ttu-id="7120e-134">新結構的總計大小：453 MB</span><span class="sxs-lookup"><span data-stu-id="7120e-134">Total size of new structures: 453 MB</span></span>  
  
     <span data-ttu-id="7120e-135">索引作業期間支援來源和目標結構所需的總磁碟空間是 816 MB (363 + 453)。</span><span class="sxs-lookup"><span data-stu-id="7120e-135">Total disk space required to support both the source and target structures for the duration of the index operation is 816 MB (363 + 453).</span></span> <span data-ttu-id="7120e-136">在索引作業認可之後，將會重新配置目前對來源結構配置的空間。</span><span class="sxs-lookup"><span data-stu-id="7120e-136">The space currently allocated to the source structures will be deallocated after the index operation is committed.</span></span>  
  
3.  <span data-ttu-id="7120e-137">決定額外的暫存磁碟空間以供排序。</span><span class="sxs-lookup"><span data-stu-id="7120e-137">Determine additional temporary disk space for sorting.</span></span>  
  
     <span data-ttu-id="7120e-138">會顯示在 **tempdb** 排序 (SORT_IN_TEMPDB 設為 ON) 和在目標位置排序 (SORT_IN_TEMPDB 設為 OFF) 的空間需求。</span><span class="sxs-lookup"><span data-stu-id="7120e-138">Space requirements are shown for sorting in **tempdb** (with SORT_IN_TEMPDB set to ON) and sorting in the target location (with SORT_IN_TEMPDB set to OFF).</span></span>  
  
    1.  <span data-ttu-id="7120e-139">當 SORT_IN_TEMPDB 設為 ON 時， **tempdb** 必須有足夠的磁碟空間，才能保留最大的索引 (1 百萬 \* 200 位元組 ~ 200 MB)。</span><span class="sxs-lookup"><span data-stu-id="7120e-139">When SORT_IN_TEMPDB is set to ON, **tempdb** must have sufficient disk space to hold the largest index (1 million \* 200 bytes ~ 200 MB).</span></span> <span data-ttu-id="7120e-140">在排序作業中不考慮填滿因數。</span><span class="sxs-lookup"><span data-stu-id="7120e-140">Fill factor is not considered in the sorting operation.</span></span>  
  
         <span data-ttu-id="7120e-141">額外的磁碟空間 (在 **tempdb** 位置) 等於 [設定 index create memory 伺服器組態選項](../../database-engine/configure-windows/configure-the-index-create-memory-server-configuration-option.md) 值 = 2 MB。</span><span class="sxs-lookup"><span data-stu-id="7120e-141">Additional disk space (in the **tempdb** location) equal to the [Configure the index create memory Server Configuration Option](../../database-engine/configure-windows/configure-the-index-create-memory-server-configuration-option.md) value = 2 MB.</span></span>  
  
         <span data-ttu-id="7120e-142">當 SORT_IN_TEMPDB 設為 ON 時，暫存磁碟空間的總計大小 ~ 202 MB。</span><span class="sxs-lookup"><span data-stu-id="7120e-142">Total size of temporary disk space with SORT_IN_TEMPDB set to ON ~ 202 MB.</span></span>  
  
    2.  <span data-ttu-id="7120e-143">當 SORT_IN_TEMPDB 設為 OFF (預設) 時，步驟 2 中為新索引所考慮的 250 MB 磁碟空間是用來排序。</span><span class="sxs-lookup"><span data-stu-id="7120e-143">When SORT_IN_TEMPDB is set to OFF (default), the 250 MB of disk space already considered for the new index in step 2 is used for sorting.</span></span>  
  
         <span data-ttu-id="7120e-144">額外的磁碟空間 (在目標位置) 等於 [設定 index create memory 伺服器組態選項](../../database-engine/configure-windows/configure-the-index-create-memory-server-configuration-option.md) 值 = 2 MB。</span><span class="sxs-lookup"><span data-stu-id="7120e-144">Additional disk space (in the target location) equal to the [Configure the index create memory Server Configuration Option](../../database-engine/configure-windows/configure-the-index-create-memory-server-configuration-option.md) value = 2 MB.</span></span>  
  
         <span data-ttu-id="7120e-145">當 SORT_IN_TEMPDB 設為 OFF 時，暫存磁碟空間的總計大小 = 2 MB。</span><span class="sxs-lookup"><span data-stu-id="7120e-145">Total size of temporary disk space with SORT_IN_TEMPDB set to OFF = 2 MB.</span></span>  
  
 <span data-ttu-id="7120e-146">使用 **tempdb**，建立叢集和非叢集索引會需要總共 1018 MB (816 + 202) 的大小。</span><span class="sxs-lookup"><span data-stu-id="7120e-146">Using **tempdb**, a total of 1018 MB (816 + 202) would be needed to create the clustered and nonclustered indexes.</span></span> <span data-ttu-id="7120e-147">雖然使用 **tempdb** 會增加建立索引所需的暫存磁碟空間數量，但只要 **tempdb** 所在的磁碟集與使用者資料庫不同，就可以減少建立索引所需的時間。</span><span class="sxs-lookup"><span data-stu-id="7120e-147">Although using **tempdb** increases the amount of temporary disk space used to create an index, it may reduce the time that is required to create an index when **tempdb** is on a different set of disks than the user database.</span></span> <span data-ttu-id="7120e-148">如需使用 **tempdb**的詳細資訊，請參閱 [索引的 SORT_IN_TEMPDB 選項](indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="7120e-148">For more information about using **tempdb**, see [SORT_IN_TEMPDB Option For Indexes](indexes.md).</span></span>  
  
 <span data-ttu-id="7120e-149">不使用 **tempdb**，建立叢集和非叢集索引會需要總共 818 MB (816+ 2) 的大小。</span><span class="sxs-lookup"><span data-stu-id="7120e-149">Without using **tempdb**, a total of 818 MB (816+ 2) would be needed to create the clustered and nonclustered indexes.</span></span>  
  
## <a name="disk-space-calculations-for-an-online-clustered-index-operation"></a><span data-ttu-id="7120e-150">線上叢集索引作業的磁碟空間計算</span><span class="sxs-lookup"><span data-stu-id="7120e-150">Disk Space Calculations for an Online Clustered Index Operation</span></span>  
 <span data-ttu-id="7120e-151">當您在線上建立、卸除或重建叢集索引時，需要額外的磁碟空間才能建立並維護暫存的對應索引。</span><span class="sxs-lookup"><span data-stu-id="7120e-151">When you create, drop, or rebuild a clustered index online, additional disk space is required to build and maintain a temporary mapping index.</span></span> <span data-ttu-id="7120e-152">此暫存對應索引包含資料表中每一個資料列的一筆記錄，並且其內容是舊的和新的書籤資料行的聯集。</span><span class="sxs-lookup"><span data-stu-id="7120e-152">This temporary mapping index contains one record for each row in the table, and its contents are the union of the old and new bookmark columns.</span></span>  
  
 <span data-ttu-id="7120e-153">若要計算線上叢集索引作業所需的磁碟空間，請按照離線索引作業的步驟，並且將結果加到下列步驟的結果。</span><span class="sxs-lookup"><span data-stu-id="7120e-153">To calculate the disk space needed for an online clustered index operation, follow the steps shown for an offline index operation and add those results to the results of the following step.</span></span>  
  
-   <span data-ttu-id="7120e-154">決定暫存對應索引的空間。</span><span class="sxs-lookup"><span data-stu-id="7120e-154">Determine space for the temporary mapping index.</span></span>  
  
     <span data-ttu-id="7120e-155">在此範例中，舊的書簽是堆積 (RID) 的資料列識別碼 (8 個位元組) 而新的書簽是叢集索引鍵 (24 個位元組，包括 `uniqueifier`) 。</span><span class="sxs-lookup"><span data-stu-id="7120e-155">In this example, the old bookmark is the row ID (RID) of the heap (8 bytes) and the new bookmark is the clustering key (24 bytes including a `uniqueifier`).</span></span> <span data-ttu-id="7120e-156">舊書籤和新書籤之間沒有重疊的資料行。</span><span class="sxs-lookup"><span data-stu-id="7120e-156">There are no overlapping columns between the old and new bookmarks.</span></span>  
  
     <span data-ttu-id="7120e-157">暫存對應索引大小 = 1 百萬 \* (8 位元組 + 24 位元組) / 80% ~ 40 MB。</span><span class="sxs-lookup"><span data-stu-id="7120e-157">Temporary mapping index size = 1 million \* (8 bytes + 24 bytes) / 80% ~ 40 MB.</span></span>  
  
     <span data-ttu-id="7120e-158">如果 SORT_IN_TEMPDB 設為 OFF，此磁碟空間必須加到目標位置中所需的磁碟空間；如果 SORT_IN_TEMPDB 設為 ON，此磁碟空間必須加到 **tempdb** 。</span><span class="sxs-lookup"><span data-stu-id="7120e-158">This disk space must be added to the required disk space in the target location if SORT_IN_TEMPDB is set to OFF, or to **tempdb** if SORT_IN_TEMPDB is set to ON.</span></span>  
  
 <span data-ttu-id="7120e-159">如需暫存對應索引的詳細資訊，請參閱 [索引 DDL 作業的磁碟空間需求](disk-space-requirements-for-index-ddl-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="7120e-159">For more information about the temporary mapping index, see [Disk Space Requirements for Index DDL Operations](disk-space-requirements-for-index-ddl-operations.md).</span></span>  
  
## <a name="disk-space-summary"></a><span data-ttu-id="7120e-160">磁碟空間摘要</span><span class="sxs-lookup"><span data-stu-id="7120e-160">Disk Space Summary</span></span>  
 <span data-ttu-id="7120e-161">下表摘要出磁碟空間計算的結果。</span><span class="sxs-lookup"><span data-stu-id="7120e-161">The following table summarizes the results of the disk space calculations.</span></span>  
  
|<span data-ttu-id="7120e-162">索引作業</span><span class="sxs-lookup"><span data-stu-id="7120e-162">Index operation</span></span>|<span data-ttu-id="7120e-163">下列結構中，不同位置的磁碟空間需求</span><span class="sxs-lookup"><span data-stu-id="7120e-163">Disk space requirements for the locations of the following structures</span></span>|  
|---------------------|---------------------------------------------------------------------------|  
|<span data-ttu-id="7120e-164">離線索引作業，SORT_IN_TEMPDB = ON</span><span class="sxs-lookup"><span data-stu-id="7120e-164">Offline index operation with SORT_IN_TEMPDB = ON</span></span>|<span data-ttu-id="7120e-165">作業期間的總空間： 1018 MB：</span><span class="sxs-lookup"><span data-stu-id="7120e-165">Total space during the operation: 1018 MB:</span></span><br /><br /> <span data-ttu-id="7120e-166">-現有的資料表和索引：363 MB\*</span><span class="sxs-lookup"><span data-stu-id="7120e-166">-Existing table and indexes: 363 MB\*</span></span><br /><br /> -<br />                    <span data-ttu-id="7120e-167">**tempdb**：202 MB\*</span><span class="sxs-lookup"><span data-stu-id="7120e-167">**tempdb**: 202 MB\*</span></span><br /><br /> <span data-ttu-id="7120e-168">-新的索引：453 MB</span><span class="sxs-lookup"><span data-stu-id="7120e-168">-New indexes: 453 MB</span></span><br /><br /> <span data-ttu-id="7120e-169">作業之後所需的總空間：453 MB</span><span class="sxs-lookup"><span data-stu-id="7120e-169">Total space required after the operation: 453 MB</span></span>|  
|<span data-ttu-id="7120e-170">離線索引作業，SORT_IN_TEMPDB = OFF</span><span class="sxs-lookup"><span data-stu-id="7120e-170">Offline index operation with SORT_IN_TEMPDB = OFF</span></span>|<span data-ttu-id="7120e-171">作業期間的總空間： 816 MB：</span><span class="sxs-lookup"><span data-stu-id="7120e-171">Total space during the operation: 816 MB:</span></span><br /><br /> <span data-ttu-id="7120e-172">-現有的資料表和索引：363 MB\*</span><span class="sxs-lookup"><span data-stu-id="7120e-172">-Existing table and indexes: 363 MB\*</span></span><br /><br /> <span data-ttu-id="7120e-173">-新的索引：453 MB</span><span class="sxs-lookup"><span data-stu-id="7120e-173">-New indexes: 453 MB</span></span><br /><br /> <span data-ttu-id="7120e-174">作業之後所需的總空間：453 MB</span><span class="sxs-lookup"><span data-stu-id="7120e-174">Total space required after the operation: 453 MB</span></span>|  
|<span data-ttu-id="7120e-175">線上索引作業，SORT_IN_TEMPDB = ON</span><span class="sxs-lookup"><span data-stu-id="7120e-175">Online index operation with SORT_IN_TEMPDB = ON</span></span>|<span data-ttu-id="7120e-176">作業期間的總空間： 1058 MB：</span><span class="sxs-lookup"><span data-stu-id="7120e-176">Total space during the operation: 1058 MB:</span></span><br /><br /> <span data-ttu-id="7120e-177">-現有的資料表和索引：363 MB\*</span><span class="sxs-lookup"><span data-stu-id="7120e-177">-Existing table and indexes: 363 MB\*</span></span><br /><br /> <span data-ttu-id="7120e-178">-**tempdb** (包含對應索引) ： 242 MB \*</span><span class="sxs-lookup"><span data-stu-id="7120e-178">-**tempdb** (includes mapping index): 242 MB\*</span></span><br /><br /> <span data-ttu-id="7120e-179">-新的索引：453 MB</span><span class="sxs-lookup"><span data-stu-id="7120e-179">-New indexes: 453 MB</span></span><br /><br /> <span data-ttu-id="7120e-180">作業之後所需的總空間：453 MB</span><span class="sxs-lookup"><span data-stu-id="7120e-180">Total space required after the operation: 453 MB</span></span>|  
|<span data-ttu-id="7120e-181">線上索引作業，SORT_IN_TEMPDB = OFF</span><span class="sxs-lookup"><span data-stu-id="7120e-181">Online index operation with SORT_IN_TEMPDB = OFF</span></span>|<span data-ttu-id="7120e-182">作業期間的總空間： 856 MB：</span><span class="sxs-lookup"><span data-stu-id="7120e-182">Total space during the operation: 856 MB:</span></span><br /><br /> <span data-ttu-id="7120e-183">-現有的資料表和索引：363 MB\*</span><span class="sxs-lookup"><span data-stu-id="7120e-183">-Existing table and indexes: 363 MB\*</span></span><br /><br /> <span data-ttu-id="7120e-184">-暫存對應索引：40 MB\*</span><span class="sxs-lookup"><span data-stu-id="7120e-184">-Temporary mapping index: 40 MB\*</span></span><br /><br /> <span data-ttu-id="7120e-185">-新的索引：453 MB</span><span class="sxs-lookup"><span data-stu-id="7120e-185">-New indexes: 453 MB</span></span><br /><br /> <span data-ttu-id="7120e-186">作業之後所需的總空間：453 MB</span><span class="sxs-lookup"><span data-stu-id="7120e-186">Total space required after the operation: 453 MB</span></span>|  
  
 <span data-ttu-id="7120e-187">\* 此空間在索引作業認可之後會重新配置。</span><span class="sxs-lookup"><span data-stu-id="7120e-187">\*This space is deallocated after the index operation is committed.</span></span>  
  
 <span data-ttu-id="7120e-188">此範例不考慮任何 **tempdb** 中，並行使用者更新及刪除作業建立的版本記錄所需的額外暫存磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="7120e-188">This example does not consider any additional temporary disk space required in **tempdb** for version records created by concurrent user update and delete operations.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="7120e-189">相關內容</span><span class="sxs-lookup"><span data-stu-id="7120e-189">Related Content</span></span>  
 [<span data-ttu-id="7120e-190">Disk Space Requirements for Index DDL Operations</span><span class="sxs-lookup"><span data-stu-id="7120e-190">Disk Space Requirements for Index DDL Operations</span></span>](disk-space-requirements-for-index-ddl-operations.md)  
  
 [<span data-ttu-id="7120e-191">索引作業的交易記錄磁碟空間</span><span class="sxs-lookup"><span data-stu-id="7120e-191">Transaction Log Disk Space for Index Operations</span></span>](transaction-log-disk-space-for-index-operations.md)  
  
  
