---
title: 停用資料表或索引的壓縮 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- data compression [SQL Server], disabling
ms.assetid: bda1e452-397b-4757-82a4-181217361589
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 80b5775d3b6f7a3f47ab75c5348b556c17b6e676
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599007"
---
# <a name="disable-compression-on-a-table-or-index"></a><span data-ttu-id="0d475-102">停用資料表或索引的壓縮</span><span class="sxs-lookup"><span data-stu-id="0d475-102">Disable Compression on a Table or Index</span></span>
  <span data-ttu-id="0d475-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中停用資料表或索引的壓縮。</span><span class="sxs-lookup"><span data-stu-id="0d475-103">This topic describes how to disable compression on a table or index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="0d475-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="0d475-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0d475-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="0d475-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0d475-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="0d475-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="0d475-107">安全性</span><span class="sxs-lookup"><span data-stu-id="0d475-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0d475-108">**若要使用下列項目來停用資料表或索引的壓縮：**</span><span class="sxs-lookup"><span data-stu-id="0d475-108">**To disable compression on a table or index, using:**</span></span>  
  
     [<span data-ttu-id="0d475-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0d475-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="0d475-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0d475-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0d475-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="0d475-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="0d475-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="0d475-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="0d475-113">如果資料表是堆積，ONLINE 模式的重建作業將會是單一執行緒。</span><span class="sxs-lookup"><span data-stu-id="0d475-113">If the table is a heap, the rebuild operation for ONLINE mode will be single threaded.</span></span> <span data-ttu-id="0d475-114">請針對多執行緒的堆積重建作業使用 OFFLINE 模式。</span><span class="sxs-lookup"><span data-stu-id="0d475-114">Use OFFLINE mode for a multi-threaded heap rebuild operation.</span></span> <span data-ttu-id="0d475-115">如需資料壓縮的詳細資訊，請參閱 [資料壓縮](data-compression.md)。</span><span class="sxs-lookup"><span data-stu-id="0d475-115">For a more information about data compression, see [Data Compression](data-compression.md).</span></span>  
  
-   <span data-ttu-id="0d475-116">若要評估變更壓縮狀態如何影響資料表、索引或分割區，請使用 [sp_estimate_data_compression_savings](/sql/relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql) 預存程序。</span><span class="sxs-lookup"><span data-stu-id="0d475-116">To evaluate how changing the compression state will affect a table, an index, or a partition, use the [sp_estimate_data_compression_savings](/sql/relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql) stored procedure.</span></span>  
  
-   <span data-ttu-id="0d475-117">您無法在資料表具有非對齊索引時變更單一分割區的壓縮設定。</span><span class="sxs-lookup"><span data-stu-id="0d475-117">You cannot change the compression setting of a single partition if the table has nonaligned indexes.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0d475-118">Security</span><span class="sxs-lookup"><span data-stu-id="0d475-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0d475-119">權限</span><span class="sxs-lookup"><span data-stu-id="0d475-119">Permissions</span></span>  
 <span data-ttu-id="0d475-120">需要資料表或索引的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="0d475-120">Requires ALTER permission on the table or index.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0d475-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0d475-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-disable-compression-on-a-table"></a><span data-ttu-id="0d475-122">若要停用資料表的壓縮</span><span class="sxs-lookup"><span data-stu-id="0d475-122">To disable compression on a table</span></span>  
  
1.  <span data-ttu-id="0d475-123">在 [物件總管] 中，展開包含您想要停用壓縮之資料表的資料庫，然後展開 **[資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0d475-123">In Object Explorer, expand the database that contains the table on which you want to disable compression and then expand the **Tables** folder.</span></span>  
  
2.  <span data-ttu-id="0d475-124">以滑鼠右鍵按一下您想要停用壓縮的資料表或索引，指向 [儲存體]，然後選取 [管理壓縮...]。</span><span class="sxs-lookup"><span data-stu-id="0d475-124">Right-click the table or index on which you want to disable compression, point to **Storage** and select **Manage Compression...**.</span></span>  
  
3.  <span data-ttu-id="0d475-125">若要停用索引的壓縮，請展開包含索引的資料表，然後展開 **[索引]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0d475-125">To disable compression on an index, expand the table that contains the index and then expand the **Indexes** folder.</span></span>  
  
4.  <span data-ttu-id="0d475-126">在 [資料壓縮精靈] 的 **[歡迎使用資料壓縮精靈]** 頁面上，按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="0d475-126">In the Data Compression Wizard, on the **Welcome to the Data Compression Wizard** page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="0d475-127">在 **[選取壓縮類型]** 頁面上，選取 **[無]** 做為要套用至您想要停用壓縮之索引中每個資料分割的壓縮類型。</span><span class="sxs-lookup"><span data-stu-id="0d475-127">On the **Select Compression Type** page, select **None** as the compression type to apply to each partition in the index on which you want to disable compression.</span></span> <span data-ttu-id="0d475-128">完成後，請按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="0d475-128">When finished, click **Next**.</span></span>  
  
     <span data-ttu-id="0d475-129">**[選取壓縮類型]** 頁面提供了下列選項：</span><span class="sxs-lookup"><span data-stu-id="0d475-129">The following options are available on the **Select Compression Type** page:</span></span>  
  
     <span data-ttu-id="0d475-130">[所有分割區使用相同的壓縮類型] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="0d475-130">**Use the same compression type for all partitions** check box</span></span>  
     <span data-ttu-id="0d475-131">選取此選項以針對所有資料分割設定相同的壓縮設定。</span><span class="sxs-lookup"><span data-stu-id="0d475-131">Select to configure the same compression setting for all partitions.</span></span> <span data-ttu-id="0d475-132">如此會啟用選取方塊，並停用方格中的 **[壓縮類型]** 資料行。</span><span class="sxs-lookup"><span data-stu-id="0d475-132">This enables the selection box and disables the **Compression Type** column in the grid.</span></span> <span data-ttu-id="0d475-133">選取之後，相鄰清單中的選項包括 **[無]** 、 **[資料列]** 和 **[頁面]** 。</span><span class="sxs-lookup"><span data-stu-id="0d475-133">When selected, the options in the adjacent list are **None**, **Row**, and **Page**.</span></span>  
  
     <span data-ttu-id="0d475-134">**資料分割編號**</span><span class="sxs-lookup"><span data-stu-id="0d475-134">**Partition Number**</span></span>  
     <span data-ttu-id="0d475-135">列出資料表或索引中的每個資料分割。</span><span class="sxs-lookup"><span data-stu-id="0d475-135">Lists each partition in the table or index.</span></span> <span data-ttu-id="0d475-136">此資料行是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="0d475-136">This column is read-only.</span></span>  
  
     <span data-ttu-id="0d475-137">**[壓縮類型]**</span><span class="sxs-lookup"><span data-stu-id="0d475-137">**Compression Type**</span></span>  
     <span data-ttu-id="0d475-138">選取每個資料分割的壓縮選項。</span><span class="sxs-lookup"><span data-stu-id="0d475-138">Select the compression option for each partition.</span></span> <span data-ttu-id="0d475-139">在選取 **[所有資料分割使用相同的壓縮類型]** 時無法使用。</span><span class="sxs-lookup"><span data-stu-id="0d475-139">Is not available when **Use the same compression type for all partitions** is selected.</span></span> <span data-ttu-id="0d475-140">清單選項包括 **[無]** 、 **[資料列]** 和 **[頁面]** 。</span><span class="sxs-lookup"><span data-stu-id="0d475-140">List options are **None**, **Row**, and **Page**.</span></span>  
  
     <span data-ttu-id="0d475-141">**界限**</span><span class="sxs-lookup"><span data-stu-id="0d475-141">**Boundary**</span></span>  
     <span data-ttu-id="0d475-142">顯示資料分割的界限。</span><span class="sxs-lookup"><span data-stu-id="0d475-142">Displays the partition boundary.</span></span> <span data-ttu-id="0d475-143">此資料行是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="0d475-143">This column is read-only.</span></span>  
  
     <span data-ttu-id="0d475-144">**資料列計數**</span><span class="sxs-lookup"><span data-stu-id="0d475-144">**Row Count**</span></span>  
     <span data-ttu-id="0d475-145">顯示此資料分割中的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="0d475-145">Displays the number of rows in this partition.</span></span> <span data-ttu-id="0d475-146">此資料行是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="0d475-146">This column is read-only.</span></span>  
  
     <span data-ttu-id="0d475-147">**目前空間**</span><span class="sxs-lookup"><span data-stu-id="0d475-147">**Current Space**</span></span>  
     <span data-ttu-id="0d475-148">顯示此資料分割所佔的目前空間 (以 MB 表示)。</span><span class="sxs-lookup"><span data-stu-id="0d475-148">Displays the current space this partition occupies in megabytes (MB).</span></span> <span data-ttu-id="0d475-149">此資料行是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="0d475-149">This column is read-only.</span></span>  
  
     <span data-ttu-id="0d475-150">**要求壓縮的空間**</span><span class="sxs-lookup"><span data-stu-id="0d475-150">**Requested Compressed Space**</span></span>  
     <span data-ttu-id="0d475-151">在按一下 [計算] 之後，此資料行會使用在 [壓縮類型] 資料行中指定的設定顯示壓縮之後每個分割區的估計大小。</span><span class="sxs-lookup"><span data-stu-id="0d475-151">After you click **Calculate**, this column displays the estimated size of each partition after compression by using the setting specified in the **Compression Type** column.</span></span> <span data-ttu-id="0d475-152">此資料行是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="0d475-152">This column is read-only.</span></span>  
  
     <span data-ttu-id="0d475-153">**計算**</span><span class="sxs-lookup"><span data-stu-id="0d475-153">**Calculate**</span></span>  
     <span data-ttu-id="0d475-154">按一下此選項可使用在 [壓縮類型] 資料行中指定的設定，估計壓縮之後每個分割區的大小。</span><span class="sxs-lookup"><span data-stu-id="0d475-154">Click to estimate the size of each partition after compression by using the setting specified in the **Compression Type** column.</span></span>  
  
6.  <span data-ttu-id="0d475-155">在 **[選取輸出選項]** 頁面上，指定要如何完成這項工作。</span><span class="sxs-lookup"><span data-stu-id="0d475-155">In the **Select an Output Option** page, specify how you want to complete this task.</span></span> <span data-ttu-id="0d475-156">選取 **[建立指令碼]** ，根據精靈中先前的步驟建立 SQL 指令碼。</span><span class="sxs-lookup"><span data-stu-id="0d475-156">Select **Create Script** to create a SQL script based the previous pages in the wizard.</span></span> <span data-ttu-id="0d475-157">選取 **[立即執行]** ，在完成精靈中的其餘所有頁面後建立新的分割區資料表。</span><span class="sxs-lookup"><span data-stu-id="0d475-157">Select **Run immediately** to create the new partitioned table after completing all remaining pages in the wizard.</span></span> <span data-ttu-id="0d475-158">選取 **[排程]** ，在預先定義的未來日期建立新的分割區資料表。</span><span class="sxs-lookup"><span data-stu-id="0d475-158">Select **Schedule** to create the new partitioned table at a predetermined time in the future.</span></span>  
  
     <span data-ttu-id="0d475-159">如果您選取 **[建立指令碼]** ，在 **[指令碼選項]** 底下可以使用下列選項：</span><span class="sxs-lookup"><span data-stu-id="0d475-159">If you select **Create script**, the following options are available under **Script options**:</span></span>  
  
     <span data-ttu-id="0d475-160">**編寫指令碼至檔案**</span><span class="sxs-lookup"><span data-stu-id="0d475-160">**Script to file**</span></span>  
     <span data-ttu-id="0d475-161">產生指令碼做為 .sql 檔案。</span><span class="sxs-lookup"><span data-stu-id="0d475-161">Generates the script as a .sql file.</span></span> <span data-ttu-id="0d475-162">在 **[檔案名稱]** 方塊中輸入檔案名稱和位置，或按一下 **[瀏覽]** 開啟 **[指令碼檔案位置]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0d475-162">Enter a file name and location in the **File name** box or click **Browse** to open the **Script File Location** dialog box.</span></span> <span data-ttu-id="0d475-163">從 **[另存新檔]** ，選取 **[Unicode 文字]** 或 **[ANSI 文字]** 。</span><span class="sxs-lookup"><span data-stu-id="0d475-163">From **Save As**, select **Unicode text** or **ANSI text**.</span></span>  
  
     <span data-ttu-id="0d475-164">**編寫指令碼至剪貼簿**</span><span class="sxs-lookup"><span data-stu-id="0d475-164">**Script to Clipboard**</span></span>  
     <span data-ttu-id="0d475-165">將指令碼儲存至剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="0d475-165">Saves the script to the Clipboard.</span></span>  
  
     <span data-ttu-id="0d475-166">**編寫指令碼至新增查詢視窗**</span><span class="sxs-lookup"><span data-stu-id="0d475-166">**Script to New Query Window**</span></span>  
     <span data-ttu-id="0d475-167">產生指令碼至新的 [查詢編輯器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="0d475-167">Generates the script to a new Query Editor window.</span></span> <span data-ttu-id="0d475-168">這是預設選項。</span><span class="sxs-lookup"><span data-stu-id="0d475-168">This is the default selection.</span></span>  
  
     <span data-ttu-id="0d475-169">如果您選取 **[排程]** ，請按一下 **[變更排程]** 。</span><span class="sxs-lookup"><span data-stu-id="0d475-169">If you select **Schedule**, click **Change schedule**.</span></span>  
  
    1.  <span data-ttu-id="0d475-170">在 [新增作業排程] 對話方塊的 [名稱] 方塊中，輸入作業排程的名稱。</span><span class="sxs-lookup"><span data-stu-id="0d475-170">In the **New Job Schedule** dialog box, in the **Name** box, enter the job schedule's name.</span></span>  
  
    2.  <span data-ttu-id="0d475-171">在 **[排程類型]** 清單，選取排程類型：</span><span class="sxs-lookup"><span data-stu-id="0d475-171">On the **Schedule type** list, select the type of schedule:</span></span>  
  
        -   <span data-ttu-id="0d475-172">**當 SQL Server Agent 啟動時自動啟動**</span><span class="sxs-lookup"><span data-stu-id="0d475-172">**Start automatically when SQL Server Agent starts**</span></span>  
  
        -   <span data-ttu-id="0d475-173">**只要 CPU 閒置就啟動**</span><span class="sxs-lookup"><span data-stu-id="0d475-173">**Start whenever the CPUs become idle**</span></span>  
  
        -   <span data-ttu-id="0d475-174">**重複執行**：</span><span class="sxs-lookup"><span data-stu-id="0d475-174">**Recurring**.</span></span> <span data-ttu-id="0d475-175">如果您的新分割區資料表會使用新資訊定期更新，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="0d475-175">Select this option if your new partitioned table updates with new information on a regular basis.</span></span>  
  
        -   <span data-ttu-id="0d475-176">**執行一次**：</span><span class="sxs-lookup"><span data-stu-id="0d475-176">**One time**.</span></span> <span data-ttu-id="0d475-177">這是預設選項。</span><span class="sxs-lookup"><span data-stu-id="0d475-177">This is the default selection.</span></span>  
  
    3.  <span data-ttu-id="0d475-178">選取或清除 **[已停用]** 核取方塊，以啟用或停用排程。</span><span class="sxs-lookup"><span data-stu-id="0d475-178">Select or clear the **Enabled** check box to enable or disable the schedule.</span></span>  
  
    4.  <span data-ttu-id="0d475-179">如果您選取 **[重複執行]** ：</span><span class="sxs-lookup"><span data-stu-id="0d475-179">If you select **Recurring**:</span></span>  
  
        1.  <span data-ttu-id="0d475-180">在 **[頻率]** 底下的 **[發生於]** 清單中，指定發生頻率：</span><span class="sxs-lookup"><span data-stu-id="0d475-180">Under **Frequency**, on the **Occurs** list, specify the frequency of occurrence:</span></span>  
  
            -   <span data-ttu-id="0d475-181">如果您選取 **[每天]** ，在 **[重複頻率]** 方塊中，輸入幾天重複一次作業排程的頻率。</span><span class="sxs-lookup"><span data-stu-id="0d475-181">If you select **Daily**, in the **Recurs every** box, enter how often the job schedule repeats in days.</span></span>  
  
            -   <span data-ttu-id="0d475-182">如果您選取 **[每週]** ，在 **[重複頻率]** 方塊中，輸入幾週重複一次作業排程的頻率。</span><span class="sxs-lookup"><span data-stu-id="0d475-182">If you select **Weekly**, in the **Recurs every** box, enter how often the job schedule repeats in weeks.</span></span> <span data-ttu-id="0d475-183">選取一週中執行作業排程是在星期幾。</span><span class="sxs-lookup"><span data-stu-id="0d475-183">Select the day or days of the week on which the job schedule is run.</span></span>  
  
            -   <span data-ttu-id="0d475-184">如果您選取 **[每月]** ，可以選取 **[天]** 或 **[於]** 。</span><span class="sxs-lookup"><span data-stu-id="0d475-184">If you select **Monthly**, select either **Day** or **The**.</span></span>  
  
                -   <span data-ttu-id="0d475-185">如果您選取 **[天]** ，請輸入執行作業排程的當月日期以及幾個月重複一次作業排程的頻率。</span><span class="sxs-lookup"><span data-stu-id="0d475-185">If you select **Day**, enter both the date of the month you want the job schedule to run and how often the job schedule repeats in months.</span></span> <span data-ttu-id="0d475-186">例如，若要在每兩個月的 15 日執行一次作業排程，請選取 [日]，然後在第一個方塊中輸入 "15"，並在第二個方塊中輸入 "2"。</span><span class="sxs-lookup"><span data-stu-id="0d475-186">For example, if you want the job schedule to run on the 15th day of the month every other month, select **Day** and enter "15" in the first box and "2" in the second box.</span></span> <span data-ttu-id="0d475-187">請注意，在第二個方塊中允許的最大數目是 "99"。</span><span class="sxs-lookup"><span data-stu-id="0d475-187">Please note that the largest number allowed in the second box is "99".</span></span>  
  
                -   <span data-ttu-id="0d475-188">如果您選取 **[於]** ，請選取執行作業排程的當月一週中特定的星期幾，以及幾個月重複一次作業排程的頻率。</span><span class="sxs-lookup"><span data-stu-id="0d475-188">If you select **The**, select the specific day of the week within the month that you want the job schedule to run and how often the job schedule repeats in months.</span></span> <span data-ttu-id="0d475-189">例如，若要在每兩個月的最後一個工作日執行一次作業排程，請選取 [日]，然後從第一個清單中選取 [最後一個]，並從第二個清單中選取 [工作日]，然後在最後一個方塊中輸入 "2"。</span><span class="sxs-lookup"><span data-stu-id="0d475-189">For example, if you want the job schedule to run on the last weekday of the month every other month, select **Day**, select **last** from the first list and **weekday** from the second list, and then enter "2" in the last box.</span></span> <span data-ttu-id="0d475-190">您也可以在前兩個清單中選取 [第一個]、[第二個]、[第三個] 或 [第四個]，以及特定工作日 (例如：星期日或星期三)。</span><span class="sxs-lookup"><span data-stu-id="0d475-190">You can also select **first**, **second**, **third**, or **fourth**, as well as specific weekdays (for example: Sunday or Wednesday) from the first two lists.</span></span> <span data-ttu-id="0d475-191">請注意，在最後一個方塊中允許的最大數目是 "99"。</span><span class="sxs-lookup"><span data-stu-id="0d475-191">Please note that the largest number allowed in the last box is "99".</span></span>  
  
        2.  <span data-ttu-id="0d475-192">在 **[每日頻率]** 底下，指定在執行作業排程當天重複作業排程的頻率：</span><span class="sxs-lookup"><span data-stu-id="0d475-192">Under **Daily frequency**, specify how often the job schedule repeats on the day the job schedule runs:</span></span>  
  
            -   <span data-ttu-id="0d475-193">如果您選取 **[執行一次於]** ，請在 **[執行一次於]** 方塊中輸入執行作業排程的當天特定時間。</span><span class="sxs-lookup"><span data-stu-id="0d475-193">If you select **Occurs once at**, enter the specific time of day when the job schedule should run in the **Occurs once at** box.</span></span> <span data-ttu-id="0d475-194">輸入時、分鐘和秒的時間，以及上午或下午。</span><span class="sxs-lookup"><span data-stu-id="0d475-194">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
            -   <span data-ttu-id="0d475-195">如果您選取 **[重複執行於每]** ，請在 **[頻率]** 底下指定在所選當天執行作業排程的頻率。</span><span class="sxs-lookup"><span data-stu-id="0d475-195">If you select **Occurs every**, specify how often the job schedule runs during the day chosen under **Frequency**.</span></span> <span data-ttu-id="0d475-196">例如，若要在執行作業排程的當天每 2 個小時重複一次作業排程，請選取 [發生間隔]，在第一個方塊中輸入 "2"，然後從清單中選取 [小時]。</span><span class="sxs-lookup"><span data-stu-id="0d475-196">For example, if you want the job schedule to repeat every 2 hours during the day that the job schedule is run, select **Occurs every**, enter "2" in the first box, and then select **hour(s)** from the list.</span></span> <span data-ttu-id="0d475-197">您也可以從這個清單中選取 [分鐘] 和 [秒]。</span><span class="sxs-lookup"><span data-stu-id="0d475-197">From this list you can also select **minute(s)** and **second(s)**.</span></span> <span data-ttu-id="0d475-198">請注意，在第一個方塊中允許的最大數目是 "100"。</span><span class="sxs-lookup"><span data-stu-id="0d475-198">Please note that the largest number allowed in the first box is "100".</span></span>  
  
                 <span data-ttu-id="0d475-199">在 **[開始時間]** 方塊中，輸入作業排程應該開始執行的時間。</span><span class="sxs-lookup"><span data-stu-id="0d475-199">In the **Starting at** box, enter the time that the job schedule should start running.</span></span> <span data-ttu-id="0d475-200">在 **[結束時間]** 方塊中，輸入作業排程應該停止重複的時間。</span><span class="sxs-lookup"><span data-stu-id="0d475-200">In the **Ending at** box, enter the time that the job schedule should stop repeating.</span></span> <span data-ttu-id="0d475-201">輸入時、分鐘和秒的時間，以及上午或下午。</span><span class="sxs-lookup"><span data-stu-id="0d475-201">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
        3.  <span data-ttu-id="0d475-202">在 **[持續時間]** 底下的 **[開始日期]** ，輸入您希望作業排程開始執行的日期。</span><span class="sxs-lookup"><span data-stu-id="0d475-202">Under **Duration**, in **Start date**, enter the date that you want the job schedule to start running.</span></span> <span data-ttu-id="0d475-203">選取 **[結束日期]** 或 **[沒有結束日期]** ，以指示作業排程應該停止執行的日期。</span><span class="sxs-lookup"><span data-stu-id="0d475-203">Select **End date** or **No end date** to indicate when the job schedule should stop running.</span></span> <span data-ttu-id="0d475-204">如果您選取 **[結束日期]** ，請輸入您希望作業排程停止執行的日期。</span><span class="sxs-lookup"><span data-stu-id="0d475-204">If you select **End date**, enter the date that you want to job schedule to stop running.</span></span>  
  
    5.  <span data-ttu-id="0d475-205">如果您選取 [執行一次]，請在 [僅執行一次於] 底下的 [日期] 方塊中，輸入將要執行作業排程的日期。</span><span class="sxs-lookup"><span data-stu-id="0d475-205">If you select **One Time**, under **One-time occurrence**, in the **Date** box, enter the date that the job schedule will be run.</span></span> <span data-ttu-id="0d475-206">在 **[時間]** 方塊中，輸入將要執行作業排程的時間。</span><span class="sxs-lookup"><span data-stu-id="0d475-206">In the **Time** box, enter the time that the job schedule will be run.</span></span> <span data-ttu-id="0d475-207">輸入時、分鐘和秒的時間，以及上午或下午。</span><span class="sxs-lookup"><span data-stu-id="0d475-207">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
    6.  <span data-ttu-id="0d475-208">在 **[摘要]** 底下的 **[描述]** ，確認所有作業排程設定是否都正確。</span><span class="sxs-lookup"><span data-stu-id="0d475-208">Under **Summary**, in **Description**, verify that all job schedule settings are correct.</span></span>  
  
    7.  <span data-ttu-id="0d475-209">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="0d475-209">Click **OK**.</span></span>  
  
     <span data-ttu-id="0d475-210">完成這個頁面之後，請按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="0d475-210">After completing this page, click **Next**.</span></span>  
  
7.  <span data-ttu-id="0d475-211">在 **[檢閱摘要]** 頁面上，展開 **[檢閱您的選取項目]** 底下的所有可用選項，確認所有設定是否都正確。</span><span class="sxs-lookup"><span data-stu-id="0d475-211">On the **Review Summary** page, under **Review your selections**, expand all available options to verify that all settings are correct.</span></span> <span data-ttu-id="0d475-212">如果一切如預期，請按一下 **[完成]** 。</span><span class="sxs-lookup"><span data-stu-id="0d475-212">If everything is as expected, click **Finish**.</span></span>  
  
8.  <span data-ttu-id="0d475-213">在 **[壓縮精靈進度]** 頁面上，監視 [建立資料分割精靈] 動作的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="0d475-213">On the **Compression Wizard Progress** page, monitor status information about the actions of the Create Partition Wizard.</span></span> <span data-ttu-id="0d475-214">根據您在精靈中選取的選項，[進度] 頁面可能會包含一個或多個動作。</span><span class="sxs-lookup"><span data-stu-id="0d475-214">Depending on the options that you selected in the wizard, the progress page might contain one or more actions.</span></span> <span data-ttu-id="0d475-215">頂端的方塊會顯示精靈的整體狀態以及精靈已接收的狀態、錯誤和警告訊息數。</span><span class="sxs-lookup"><span data-stu-id="0d475-215">The top box displays the overall status of the wizard and the number of status, error, and warning messages that the wizard has received.</span></span>  
  
     <span data-ttu-id="0d475-216">**[壓縮精靈進度]** 頁面提供了下列選項：</span><span class="sxs-lookup"><span data-stu-id="0d475-216">The following options are available on the **Compression Wizard Progress** page:</span></span>  
  
     <span data-ttu-id="0d475-217">**詳細資料**</span><span class="sxs-lookup"><span data-stu-id="0d475-217">**Details**</span></span>  
     <span data-ttu-id="0d475-218">提供從精靈所採取的動作傳回的動作、狀態和任何訊息。</span><span class="sxs-lookup"><span data-stu-id="0d475-218">Provides the action, status, and any messages that are returned from action taken by the wizard.</span></span>  
  
     <span data-ttu-id="0d475-219">**動作**</span><span class="sxs-lookup"><span data-stu-id="0d475-219">**Action**</span></span>  
     <span data-ttu-id="0d475-220">指定每個動作的類型和名稱。</span><span class="sxs-lookup"><span data-stu-id="0d475-220">Specifies the type and name of each action.</span></span>  
  
     <span data-ttu-id="0d475-221">**狀態**</span><span class="sxs-lookup"><span data-stu-id="0d475-221">**Status**</span></span>  
     <span data-ttu-id="0d475-222">指出整個精靈動作傳回 [成功] 或 [失敗] 的值。</span><span class="sxs-lookup"><span data-stu-id="0d475-222">Indicates whether the wizard action as a whole returned the value of **Success** or **Failure**.</span></span>  
  
     <span data-ttu-id="0d475-223">**訊息**</span><span class="sxs-lookup"><span data-stu-id="0d475-223">**Message**</span></span>  
     <span data-ttu-id="0d475-224">提供從程序所傳回的任何錯誤或警告訊息。</span><span class="sxs-lookup"><span data-stu-id="0d475-224">Provides any error or warning messages that are returned from the process.</span></span>  
  
     <span data-ttu-id="0d475-225">**Report**</span><span class="sxs-lookup"><span data-stu-id="0d475-225">**Report**</span></span>  
     <span data-ttu-id="0d475-226">建立包含 [建立分割區精靈] 結果的報表。</span><span class="sxs-lookup"><span data-stu-id="0d475-226">Creates a report that contains the results of the Create Partition Wizard.</span></span> <span data-ttu-id="0d475-227">選項為 **[檢視報表]** 、 **[將報表儲存到檔案]** 、 **[複製報表到剪貼簿]** 和 **[以電子郵件傳送報表]** 。</span><span class="sxs-lookup"><span data-stu-id="0d475-227">The options are **View Report**, **Save Report to File**, **Copy Report to Clipboard**, and **Send Report as Email**.</span></span>  
  
     <span data-ttu-id="0d475-228">**檢視報表**</span><span class="sxs-lookup"><span data-stu-id="0d475-228">**View Report**</span></span>  
     <span data-ttu-id="0d475-229">開啟 [檢視報表] 對話方塊，其中包含 [建立分割區精靈] 進度的文字報表。</span><span class="sxs-lookup"><span data-stu-id="0d475-229">Opens the **View Report** dialog box, which contains a text report of the progress of the Create Partition Wizard.</span></span>  
  
     <span data-ttu-id="0d475-230">**將報表儲存到檔案**</span><span class="sxs-lookup"><span data-stu-id="0d475-230">**Save Report to File**</span></span>  
     <span data-ttu-id="0d475-231">開啟 [另存報表] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0d475-231">Opens the **Save Report As** dialog box.</span></span>  
  
     <span data-ttu-id="0d475-232">**複製報表到剪貼簿**</span><span class="sxs-lookup"><span data-stu-id="0d475-232">**Copy Report to Clipboard**</span></span>  
     <span data-ttu-id="0d475-233">將精靈進度報表的結果複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="0d475-233">Copies the results of the wizard's progress report to the Clipboard.</span></span>  
  
     <span data-ttu-id="0d475-234">**[以電子郵件傳送報表]**</span><span class="sxs-lookup"><span data-stu-id="0d475-234">**Send Report as Email**</span></span>  
     <span data-ttu-id="0d475-235">將精靈進度報表的結果複製到電子郵件。</span><span class="sxs-lookup"><span data-stu-id="0d475-235">Copies the results of the wizard's progress report into an email message.</span></span>  
  
     <span data-ttu-id="0d475-236">完成後，請按一下 **[關閉]** 。</span><span class="sxs-lookup"><span data-stu-id="0d475-236">When complete, click **Close**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="0d475-237">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0d475-237">Using Transact-SQL</span></span>  
  
#### <a name="to-disable-compression-on-a-table"></a><span data-ttu-id="0d475-238">若要停用資料表的壓縮</span><span class="sxs-lookup"><span data-stu-id="0d475-238">To disable compression on a table</span></span>  
  
1.  <span data-ttu-id="0d475-239">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0d475-239">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0d475-240">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="0d475-240">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0d475-241">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="0d475-241">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Person.Person REBUILD PARTITION = ALL  
    WITH (DATA_COMPRESSION = NONE);  
    GO  
    ```  
  
#### <a name="to-disable-compression-on-an-index"></a><span data-ttu-id="0d475-242">若要停用索引的壓縮</span><span class="sxs-lookup"><span data-stu-id="0d475-242">To disable compression on an index</span></span>  
  
1.  <span data-ttu-id="0d475-243">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0d475-243">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0d475-244">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="0d475-244">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0d475-245">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="0d475-245">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER INDEX AK_Person_rowguid ON Person.Person REBUILD PARTITION = ALL WITH (DATA_COMPRESSION = NONE);  
    GO  
    ```  
  
 <span data-ttu-id="0d475-246">如需詳細資訊，請參閱 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) 和 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0d475-246">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) and [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
  
