---
title: 記憶體最佳化建議程式 | Microsoft Docs
ms.custom: ''
ms.date: 10/26/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
f1_keywords:
- sql12.swb.memoryoptimizationwizard.f1
- swb.memoryoptimizationwizard.f1
ms.assetid: 181989c2-9636-415a-bd1d-d304fc920b8a
author: rothja
ms.author: jroth
ms.openlocfilehash: cd0e08ab6d6a7bb2cfbf1892d6f2e4649e4a9735
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698209"
---
# <a name="memory-optimization-advisor"></a><span data-ttu-id="70aac-102">記憶體最佳化 Advisor</span><span class="sxs-lookup"><span data-stu-id="70aac-102">Memory Optimization Advisor</span></span>
  <span data-ttu-id="70aac-103">交易效能報告工具 (請參閱＜ [Determining if a Table or Stored Procedure Should Be Ported to In-Memory OLTP](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)＞) 會通知您，匯出使用記憶體中 OLTP 時資料庫中哪些資料表有加分效果。</span><span class="sxs-lookup"><span data-stu-id="70aac-103">Transaction performance reports tool (see [Determining if a Table or Stored Procedure Should Be Ported to In-Memory OLTP](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)) informs you about which tables in your database will benefit if ported to use In-Memory OLTP.</span></span> <span data-ttu-id="70aac-104">識別您要匯出使用記憶體中 OLTP 的資料表之後，即可使用 Memory Optimization Advisor，協助您將以磁碟為基礎的資料庫資料表移轉到記憶體中 OLTP。</span><span class="sxs-lookup"><span data-stu-id="70aac-104">After you identify a table that you would like to port to use In-Memory OLTP, you can use the memory optimization advisor to help you migrate the disk-based database table to In-Memory OLTP.</span></span>  
  
 <span data-ttu-id="70aac-105">開始時，請先連接至執行個體，其中包含以磁碟為基礎的資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="70aac-105">To begin, connect to the instance that contains the disk-based database table.</span></span> <span data-ttu-id="70aac-106">您可連接到 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="70aac-106">You can connect to a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] or [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] instance.</span></span> <span data-ttu-id="70aac-107">不過，如果您想要使用 Advisor 執行移轉作業，則必須連接到已啟用 In-Memory OLTP 功能的 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="70aac-107">However, if you wish to perform a migration operation with the advisor, you must connect to a [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] instance on which In-Memory OLTP functionality is enabled.</span></span> <span data-ttu-id="70aac-108">如需有關記憶體中 OLTP 需求的詳細資訊，請參閱＜ [Requirements for Using Memory-Optimized Tables](memory-optimized-tables.md)＞。</span><span class="sxs-lookup"><span data-stu-id="70aac-108">For more information about In-Memory OLTP requirements, see [Requirements for Using Memory-Optimized Tables](memory-optimized-tables.md).</span></span>  
  
 <span data-ttu-id="70aac-109">如需移轉方法的資訊，請參閱 [In-Memory OLTP - 一般工作負載模式和移轉考量](https://msdn.microsoft.com/library/dn673538.aspx)。</span><span class="sxs-lookup"><span data-stu-id="70aac-109">For information about migration methodologies, see [In-Memory OLTP - Common Workload Patterns and Migration Considerations](https://msdn.microsoft.com/library/dn673538.aspx).</span></span>  
  
## <a name="walkthrough-using-the-memory-optimization-advisor"></a><span data-ttu-id="70aac-110">使用記憶體最佳化 Advisor 的逐步解說</span><span class="sxs-lookup"><span data-stu-id="70aac-110">Walkthrough Using the Memory-Optimization Advisor</span></span>  
 <span data-ttu-id="70aac-111">在 **[物件總管]** 中，以滑鼠右鍵按一下您想要轉換的資料表，然後選取 **[記憶體最佳化 Advisor]** 。</span><span class="sxs-lookup"><span data-stu-id="70aac-111">In **Object Explorer**, right click the table you want to convert, and select **Memory-Optimization Advisor**.</span></span> <span data-ttu-id="70aac-112">隨即顯示 **[資料表記憶體最佳化 Advisor]** 的歡迎頁面。</span><span class="sxs-lookup"><span data-stu-id="70aac-112">This will display the welcome page for the **Table Memory Optimization Advisor**.</span></span>  
  
### <a name="memory-optimization-checklist"></a><span data-ttu-id="70aac-113">記憶體最佳化檢查清單</span><span class="sxs-lookup"><span data-stu-id="70aac-113">Memory Optimization Checklist</span></span>  
 <span data-ttu-id="70aac-114">按一下 **[資料表記憶體最佳化 Advisor]** 歡迎頁面中的 **[下一步]** 時，即會看到記憶體最佳化檢查清單。</span><span class="sxs-lookup"><span data-stu-id="70aac-114">When you click **Next** in the welcome page for the **Table Memory Optimization Advisor**, you will see the memory optimization checklist.</span></span> <span data-ttu-id="70aac-115">記憶體最佳化的資料表不支援磁碟資料表的全部功能。</span><span class="sxs-lookup"><span data-stu-id="70aac-115">Memory-optimized tables do not support all the features in a disk-based table.</span></span> <span data-ttu-id="70aac-116">記憶體最佳化檢查清單會報告磁碟資料表是否使用任何與記憶體最佳化資料表不相容的功能。</span><span class="sxs-lookup"><span data-stu-id="70aac-116">The memory optimization checklist reports if the disk-based table uses any features that are incompatible with a memory-optimized table.</span></span> <span data-ttu-id="70aac-117">**資料表記憶體最佳化 Advisor** 並不會修改磁碟資料表，以便將其移轉為使用 In-Memory OLTP。</span><span class="sxs-lookup"><span data-stu-id="70aac-117">The **Table Memory Optimization Advisor** does not modify the disk-based table so that it can be migrated to use In-Memory OLTP.</span></span> <span data-ttu-id="70aac-118">您必須先進行變更才能繼續移轉。</span><span class="sxs-lookup"><span data-stu-id="70aac-118">You must make those changes before continuing migration.</span></span> <span data-ttu-id="70aac-119">針對每個發現的不相容狀況， **資料表記憶體最佳化 Advisor** 會顯示有助於修改以磁碟為基礎的資料表之相關資訊的連結。</span><span class="sxs-lookup"><span data-stu-id="70aac-119">For each incompatibility found, the **Table Memory Optimization Advisor** displays a link to information that can help you modify your disk-based tables.</span></span>  
  
 <span data-ttu-id="70aac-120">如果您想要保留這些不相容狀況的清單以便規劃移轉，請按一下 **[產生報告]** ，即可產生 HTML 清單。</span><span class="sxs-lookup"><span data-stu-id="70aac-120">If you wish to keep a list of these incompatibilities, to plan your migration, click the **Generate Report** to generate a HTML list.</span></span>  
  
 <span data-ttu-id="70aac-121">如果資料表沒有不相容的狀況，而且您已使用記憶體中 OLTP 連接到 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 執行個體，請按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="70aac-121">If your table has no incompatibilities and you are connected to a [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] instance with In-Memory OLTP, click **Next**.</span></span>  
  
### <a name="memory-optimization-warnings"></a><span data-ttu-id="70aac-122">記憶體最佳化警告</span><span class="sxs-lookup"><span data-stu-id="70aac-122">Memory Optimization Warnings</span></span>  
 <span data-ttu-id="70aac-123">在下一頁的記憶體最佳化警告中包含一份問題清單，這些問題對資料表移轉為使用記憶體中 OLTP 並無影響，但卻可能導致其他物件 (例如預存程序或 CLR 函數) 行為失敗或產生非預期的行為。</span><span class="sxs-lookup"><span data-stu-id="70aac-123">The next page, memory optimization warnings, contains a list of issues that do not prevent the table from being migrated to use In-Memory OLTP, but that may cause the behavior of other objects (such as stored procedures or CLR functions) to fail or result in unexpected behavior.</span></span>  
  
 <span data-ttu-id="70aac-124">清單一開始出現的幾個警告都是參考用的，因此可能不適用於您的資料表。</span><span class="sxs-lookup"><span data-stu-id="70aac-124">The first several warnings in the list are informational and may or may not apply to your table.</span></span> <span data-ttu-id="70aac-125">資料表右邊資料行中的連結會帶領您前往詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="70aac-125">Links in the right-hand column of the table will take you to more information.</span></span>  
  
 <span data-ttu-id="70aac-126">這個警告表也會顯示您的資料表中尚未出現的潛在警告狀況。</span><span class="sxs-lookup"><span data-stu-id="70aac-126">The warning table will also display potential warning conditions that are not present in your table.</span></span>  
  
 <span data-ttu-id="70aac-127">可付諸行動的警告會在左邊資料行中出現一個黃色的三角形。</span><span class="sxs-lookup"><span data-stu-id="70aac-127">Actionable warnings will have a yellow triangle in the left-hand column.</span></span> <span data-ttu-id="70aac-128">如果有可付諸行動的警告，您應該結束移轉、解決警告，然後重新啟動程序。</span><span class="sxs-lookup"><span data-stu-id="70aac-128">If there are actionable warnings, you should exit the migration, resolve the warnings, and then restart the process.</span></span> <span data-ttu-id="70aac-129">如果您沒有解決警告，移轉的資料表可能會導致失敗。</span><span class="sxs-lookup"><span data-stu-id="70aac-129">If you do not resolve the warnings, your migrated table may cause a failure.</span></span>  
  
 <span data-ttu-id="70aac-130">按一下 **[產生報告]** 即可產生這些警告的 HTML 報告。</span><span class="sxs-lookup"><span data-stu-id="70aac-130">Click **Generate Report** to generate an HTML report of these warnings.</span></span> <span data-ttu-id="70aac-131">按 [下一步]  繼續進行。</span><span class="sxs-lookup"><span data-stu-id="70aac-131">Click **Next** to proceed.</span></span>  
  
### <a name="review-optimization-options"></a><span data-ttu-id="70aac-132">檢閱最佳化選項</span><span class="sxs-lookup"><span data-stu-id="70aac-132">Review Optimization Options</span></span>  
 <span data-ttu-id="70aac-133">下一個畫面可讓您修改選項以便移轉至 In-Memory OLTP：</span><span class="sxs-lookup"><span data-stu-id="70aac-133">The next screen lets you modify options for the migration to In-Memory OLTP:</span></span>  
  
 <span data-ttu-id="70aac-134">記憶體最佳化的檔案群組</span><span class="sxs-lookup"><span data-stu-id="70aac-134">Memory-optimized filegroup</span></span>  
 <span data-ttu-id="70aac-135">您的記憶體最佳化檔案群組名稱。</span><span class="sxs-lookup"><span data-stu-id="70aac-135">The name for your memory-optimized filegroup.</span></span> <span data-ttu-id="70aac-136">資料庫必須具備一個記憶體最佳化的檔案群組 (其中至少包含一個檔案)，才能建立記憶體最佳化的資料表。</span><span class="sxs-lookup"><span data-stu-id="70aac-136">A database must have a memory-optimized filegroup with at least one file before a memory-optimized table can be created.</span></span>  
  
 <span data-ttu-id="70aac-137">如果您沒有記憶體最佳化的檔案群組，即可變更預設名稱。</span><span class="sxs-lookup"><span data-stu-id="70aac-137">If you do not have a memory-optimized filegroup, you can change the default name.</span></span> <span data-ttu-id="70aac-138">不可刪除記憶體最佳化的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="70aac-138">Memory-optimized filegroups cannot be deleted.</span></span> <span data-ttu-id="70aac-139">記憶體最佳化檔案群組的存在可能會停用某些資料庫層級功能 (例如 AUTO CLOSE 與資料庫鏡像)。</span><span class="sxs-lookup"><span data-stu-id="70aac-139">The existence of a memory-optimized filegroup may disable some database-level features such as AUTO CLOSE and database mirroring.</span></span>  
  
 <span data-ttu-id="70aac-140">如果資料庫中已經有記憶體最佳化的檔案群組，這個欄位就會預先填入它的名稱，而且您無法變更此欄位的值。</span><span class="sxs-lookup"><span data-stu-id="70aac-140">If a database already has a memory-optimized file group, this field will be pre-populated with its name and you will not be able to change the value of this field.</span></span>  
  
 <span data-ttu-id="70aac-141">邏輯檔案名稱和檔案路徑</span><span class="sxs-lookup"><span data-stu-id="70aac-141">Logical file name and File path</span></span>  
 <span data-ttu-id="70aac-142">將會包含記憶體最佳化資料表的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="70aac-142">The name of the file that will contain the memory-optimized table.</span></span> <span data-ttu-id="70aac-143">資料庫必須具備一個記憶體最佳化的檔案群組 (其中至少包含一個檔案)，才能建立記憶體最佳化的資料表。</span><span class="sxs-lookup"><span data-stu-id="70aac-143">A database must have a memory-optimized file group with at least one file before a memory-optimized table can be created.</span></span>  
  
 <span data-ttu-id="70aac-144">如果您不具備現有的記憶體最佳化檔案群組，則可在移轉程序結束時，變更要建立之檔案的預設名稱和路徑。</span><span class="sxs-lookup"><span data-stu-id="70aac-144">If you do not have an existing memory-optimized file group, you can change the default name and path of the file to be created at the end of the migration process.</span></span>  
  
 <span data-ttu-id="70aac-145">如果您具備現有的記憶體最佳化檔案群組，這些欄位會預先填入，而且您無法變更這些欄位的值。</span><span class="sxs-lookup"><span data-stu-id="70aac-145">If you have an existing memory-optimized filegroup, these fields will be pre-populated and you will not be able to change the values.</span></span>  
  
 <span data-ttu-id="70aac-146">將原始資料表重新命名為</span><span class="sxs-lookup"><span data-stu-id="70aac-146">Rename the original table as</span></span>  
 <span data-ttu-id="70aac-147">在移轉程序結束時，會使用資料表目前的名稱建立新的記憶體最佳化資料表。</span><span class="sxs-lookup"><span data-stu-id="70aac-147">At the end of the migration process, a new memory-optimized table will be created with the current name of the table.</span></span> <span data-ttu-id="70aac-148">若要避免名稱衝突，您必須重新命名目前的資料表。</span><span class="sxs-lookup"><span data-stu-id="70aac-148">To avoid a name conflict, the current table must be renamed.</span></span> <span data-ttu-id="70aac-149">您可以在此欄位中變更名稱。</span><span class="sxs-lookup"><span data-stu-id="70aac-149">You may change that name in this field.</span></span>  
  
 <span data-ttu-id="70aac-150">目前估計的記憶體成本 (MB)</span><span class="sxs-lookup"><span data-stu-id="70aac-150">Estimated current memory cost (MB)</span></span>  
 <span data-ttu-id="70aac-151">記憶體最佳化 Advisor 會根據磁碟資料表的中繼資料，評估新的記憶體最佳化資料表將取用的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="70aac-151">The Memory-Optimization Advisor estimates the amount of memory the new memory-optimized table will consume based on metadata of the disk-based table.</span></span> <span data-ttu-id="70aac-152">[記憶體最佳化資料表中的資料表和資料列大小](table-and-row-size-in-memory-optimized-tables.md)中說明資料表大小的計算方式。</span><span class="sxs-lookup"><span data-stu-id="70aac-152">The calculation of the table size is explained in [Table and Row Size in Memory-Optimized Tables](table-and-row-size-in-memory-optimized-tables.md).</span></span>  
  
 <span data-ttu-id="70aac-153">如果未分配足夠的記憶體，移轉程序可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="70aac-153">If sufficient memory is not allotted, the migration process may fail.</span></span>  
  
 <span data-ttu-id="70aac-154">請將資料表的資料複製到新的記憶體最佳化資料表</span><span class="sxs-lookup"><span data-stu-id="70aac-154">Also copy table data to the new memory optimized table</span></span>  
 <span data-ttu-id="70aac-155">如果您想要將目前資料表的資料移至新的記憶體最佳化資料表，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="70aac-155">Select this option if you wish to also move the data in the current table to the new memory-optimized table.</span></span> <span data-ttu-id="70aac-156">如果未選取此選項，建立新的記憶體最佳化資料表時不會有任何資料列。</span><span class="sxs-lookup"><span data-stu-id="70aac-156">If this option is not selected, the new memory-optimized table will be created with no rows.</span></span>  
  
 <span data-ttu-id="70aac-157">根據預設將資料表移轉為持久性資料表</span><span class="sxs-lookup"><span data-stu-id="70aac-157">The table will be migrated as a durable table by default</span></span>  
 <span data-ttu-id="70aac-158">相較於持久性記憶體最佳化資料表，記憶體中 OLTP 可以優越效能支援非持久性資料表。</span><span class="sxs-lookup"><span data-stu-id="70aac-158">In-Memory OLTP supports non-durable tables with superior performance compared to durable memory-optimized tables.</span></span> <span data-ttu-id="70aac-159">不過，在重新啟動伺服器時，非持久性資料表中的資料將會遺失。</span><span class="sxs-lookup"><span data-stu-id="70aac-159">However, data in a non-durable table will be lost upon server restart.</span></span>  
  
 <span data-ttu-id="70aac-160">如果選取此選項，記憶體最佳化 Advisor 將會建立非持久性的資料表 (而不是持久性資料表)。</span><span class="sxs-lookup"><span data-stu-id="70aac-160">If this option is selected, the Memory-Optimization Advisor will create a non-durable table instead of a durable table.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="70aac-161">只有在您了解非持久性資料表的相關資料遺失風險時，才可選取此選項。</span><span class="sxs-lookup"><span data-stu-id="70aac-161">Select this option only if you understand the risk of data loss associated with non-durable tables.</span></span>  
  
 <span data-ttu-id="70aac-162">選取 [下一步] 以繼續操作。</span><span class="sxs-lookup"><span data-stu-id="70aac-162">Click **Next** to continue.</span></span>  
  
### <a name="review-primary-key-conversion"></a><span data-ttu-id="70aac-163">檢閱主索引鍵轉換</span><span class="sxs-lookup"><span data-stu-id="70aac-163">Review Primary Key Conversion</span></span>  
 <span data-ttu-id="70aac-164">下一個畫面是 **[檢閱主索引鍵轉換]** 。</span><span class="sxs-lookup"><span data-stu-id="70aac-164">The next screen is **Review Primary Key Conversion**.</span></span> <span data-ttu-id="70aac-165">記憶體最佳化 Advisor 會偵測資料表中是否有一個或多個主索引鍵，並根據主索引鍵的中繼資料填入資料行的清單。</span><span class="sxs-lookup"><span data-stu-id="70aac-165">The Memory-Optimization Advisor will detect if there are one or more primary keys in the table, and populates the list of columns based on the primary key metadata.</span></span> <span data-ttu-id="70aac-166">否則，如果您想要移轉至持久性記憶體最佳化資料表，就必須建立主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="70aac-166">Otherwise, if you wish to migrate to a durable memory-optimized table, you must create a primary key.</span></span>  
  
 <span data-ttu-id="70aac-167">如果主索引鍵不存在，而且資料表正移轉至非持久性資料表，這個畫面將不會出現。</span><span class="sxs-lookup"><span data-stu-id="70aac-167">If a primary key doesn't exist and the table is being migrated to a non-durable table, this screen will not appear.</span></span>  
  
 <span data-ttu-id="70aac-168">對於文字資料行 (`char`、`nchar`、`varchar` 和 `nvarchar` 類型的資料行)，您必須選取適當的定序。</span><span class="sxs-lookup"><span data-stu-id="70aac-168">For textual columns (columns with types `char`, `nchar`, `varchar`, and `nvarchar`) you must select an appropriate collation.</span></span> <span data-ttu-id="70aac-169">記憶體中 OLTP 只支援記憶體最佳化資料表上的資料行之 BIN2 定序，而不支援附帶補充字元的定序。</span><span class="sxs-lookup"><span data-stu-id="70aac-169">In-Memory OLTP only supports BIN2 collations for columns on a memory-optimized table and it does not support collations with supplementary characters.</span></span> <span data-ttu-id="70aac-170">如需支援的定序及定序變更之潛在影響的詳細資訊，請參閱＜ [Collations and Code Pages](../../database-engine/collations-and-code-pages.md) ＞。</span><span class="sxs-lookup"><span data-stu-id="70aac-170">See [Collations and Code Pages](../../database-engine/collations-and-code-pages.md) for information on the collations supported and the potential impact of a change in collation.</span></span>  
  
 <span data-ttu-id="70aac-171">您可以為主索引鍵設定下列參數：</span><span class="sxs-lookup"><span data-stu-id="70aac-171">You can configure the following parameters for the primary key:</span></span>  
  
 <span data-ttu-id="70aac-172">為主要索引鍵選取新的名稱</span><span class="sxs-lookup"><span data-stu-id="70aac-172">Select a new name for this primary key</span></span>  
 <span data-ttu-id="70aac-173">此資料表的主索引鍵名稱在資料庫內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="70aac-173">The primary key name for this table must be unique inside the database.</span></span> <span data-ttu-id="70aac-174">您可在此處變更主索引鍵的名稱。</span><span class="sxs-lookup"><span data-stu-id="70aac-174">You may change the name of the primary key here.</span></span>  
  
 <span data-ttu-id="70aac-175">選取主索引鍵的類型</span><span class="sxs-lookup"><span data-stu-id="70aac-175">Select the type of this primary key</span></span>  
 <span data-ttu-id="70aac-176">記憶體中 OLTP 支援下列兩種記憶體最佳化資料表上的索引類型：</span><span class="sxs-lookup"><span data-stu-id="70aac-176">In-Memory OLTP supports two types of indexes on a memory-optimized table:</span></span>  
  
-   <span data-ttu-id="70aac-177">非叢集雜湊索引。</span><span class="sxs-lookup"><span data-stu-id="70aac-177">A NONCLUSTERED HASH index.</span></span> <span data-ttu-id="70aac-178">此索引最適合具有許多點查閱的索引。</span><span class="sxs-lookup"><span data-stu-id="70aac-178">This index is best for indexes with many point lookups.</span></span> <span data-ttu-id="70aac-179">您可以在 **[值區計數]** 欄位中設定此索引的值區計數。</span><span class="sxs-lookup"><span data-stu-id="70aac-179">You may configure the bucket count for this index in the **Bucket Count** field.</span></span>  
  
-   <span data-ttu-id="70aac-180">非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="70aac-180">A NONCLUSTERED index.</span></span> <span data-ttu-id="70aac-181">此類型的索引最適合具有許多範圍查詢的索引。</span><span class="sxs-lookup"><span data-stu-id="70aac-181">This type of index is best for indexes with many range queries.</span></span> <span data-ttu-id="70aac-182">您可以在 **[排序資料行和次序]** 清單中設定每個資料行的排序次序。</span><span class="sxs-lookup"><span data-stu-id="70aac-182">You may configure the sort order for each column in the **Sort column and order** list.</span></span>  
  
 <span data-ttu-id="70aac-183">若要了解主索引鍵最適合的索引類型，請參閱 [雜湊索引](../../database-engine/hash-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="70aac-183">To understand the type of index best for your primary key, see [Hash Indexes](../../database-engine/hash-indexes.md).</span></span>  
  
 <span data-ttu-id="70aac-184">選定主索引鍵之後，請按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="70aac-184">Click **Next** after you make your primary key choices.</span></span>  
  
### <a name="review-index-conversion"></a><span data-ttu-id="70aac-185">檢閱索引轉換</span><span class="sxs-lookup"><span data-stu-id="70aac-185">Review Index Conversion</span></span>  
 <span data-ttu-id="70aac-186">下一頁是 **[檢閱索引轉換]** 。</span><span class="sxs-lookup"><span data-stu-id="70aac-186">The next page is **Review Index Conversion**.</span></span> <span data-ttu-id="70aac-187">記憶體最佳化 Advisor 會偵測資料表中是否有一個或多個索引，並填入資料行與資料類型的清單。</span><span class="sxs-lookup"><span data-stu-id="70aac-187">The Memory-Optimization Advisor will detect if there are one or more indexes in the table, and populates the list of columns and data type.</span></span> <span data-ttu-id="70aac-188">您可在 **[檢閱索引轉換]** 頁面中設定的參數，與上一個 **[檢閱主索引鍵轉換]** 頁面類似。</span><span class="sxs-lookup"><span data-stu-id="70aac-188">The parameters you can configure in the **Review Index Conversion** page are similar to the previous, **Review Primary Key Conversion** page.</span></span>  
  
 <span data-ttu-id="70aac-189">如果資料表中僅有主索引鍵，而且資料表正移轉至持久性資料表，這個畫面就不會出現。</span><span class="sxs-lookup"><span data-stu-id="70aac-189">If the table only has a primary key and it's being migrated to a durable table, this screen will not appear.</span></span>  
  
 <span data-ttu-id="70aac-190">決定資料表中的每個索引之後，請按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="70aac-190">After you make a decision for every index in your table, click **Next**.</span></span>  
  
### <a name="verify-migration-actions"></a><span data-ttu-id="70aac-191">確認移轉動作</span><span class="sxs-lookup"><span data-stu-id="70aac-191">Verify Migration Actions</span></span>  
 <span data-ttu-id="70aac-192">下一頁是 **[確認移轉動作]** 。</span><span class="sxs-lookup"><span data-stu-id="70aac-192">The next page is **Verify Migration Actions**.</span></span> <span data-ttu-id="70aac-193">若要編寫移轉作業的指令碼，請按一下 **[指令碼]** 產生 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼。</span><span class="sxs-lookup"><span data-stu-id="70aac-193">To script the migration operation, click **Script** to generate a [!INCLUDE[tsql](../../includes/tsql-md.md)] script.</span></span> <span data-ttu-id="70aac-194">然後您可以修改和執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="70aac-194">You may then modify and execute the script.</span></span> <span data-ttu-id="70aac-195">按一下 **[移轉]** 即可開始資料表移轉。</span><span class="sxs-lookup"><span data-stu-id="70aac-195">Click **Migrate** to begin the table migration.</span></span>  
  
 <span data-ttu-id="70aac-196">程序完成之後，請重新整理 **[物件總管]** 以查看新的記憶體最佳化資料表和舊的磁碟資料表。</span><span class="sxs-lookup"><span data-stu-id="70aac-196">After the process is finished, refresh **Object Explorer** to see the new memory-optimized table and the old disk-based table.</span></span> <span data-ttu-id="70aac-197">您可保留舊資料表或隨時將其刪除。</span><span class="sxs-lookup"><span data-stu-id="70aac-197">You can keep the old table or delete it at your convenience.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70aac-198">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70aac-198">See Also</span></span>  
 [<span data-ttu-id="70aac-199">移轉至 In-Memory OLTP</span><span class="sxs-lookup"><span data-stu-id="70aac-199">Migrating to In-Memory OLTP</span></span>](migrating-to-in-memory-oltp.md)  
  
  
