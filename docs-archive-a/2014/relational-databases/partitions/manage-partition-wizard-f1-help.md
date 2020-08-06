---
title: 管理資料分割精靈 F1 說明 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.managepartition.getstart.f1
- sql12.swb.managepartition.selectoutput.f1
- sql12.swb.managepartition.partitionaction.f1
- sql12.swb.managepartition.switchout.f1
- sql12.swb.managepartition.summary.f1
- sql12.swb.managepartition.createjob.f1
- sql12.swb.managepartition.stagingtable.f1
- sql12.swb.managepartition.progress.f1
- sql12.swb.managepartition.switchin.f1
- sql12.swb.managepartition.selectswitchtables.f1
helpviewer_keywords:
- wizards [SQL Server Management Studio] See Manage Partition Wizard
ms.assetid: e2478d26-dea4-428d-98c5-aad2d2a30da8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 09b3e774168e9a48a0a387c3474b29f96081d875
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687826"
---
# <a name="manage-partition-wizard-f1-help"></a><span data-ttu-id="ed3fd-102">管理資料分割精靈 F1 說明</span><span class="sxs-lookup"><span data-stu-id="ed3fd-102">Manage Partition Wizard F1 Help</span></span>
  <span data-ttu-id="ed3fd-103">使用 [管理資料分割精靈]，即可透過資料分割切換或滑動視窗案例的實作，管理和修改現有的資料分割資料表。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-103">Use the **Manage Partition Wizard** to manage and modify existing partitioned tables through partition switching or the implementation of a sliding window scenario.</span></span> <span data-ttu-id="ed3fd-104">這個精靈可以讓資料分割的管理更方便，並且簡化將資料移轉入和移轉出資料表的一般作業。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-104">This wizard can ease the management of your partitions and simplify the regular migration of data in and out of your tables.</span></span>  
  
### <a name="to-start-the-manage-partition-wizard"></a><span data-ttu-id="ed3fd-105">啟動管理資料分割精靈</span><span class="sxs-lookup"><span data-stu-id="ed3fd-105">To start the Manage Partition Wizard</span></span>  
  
-   <span data-ttu-id="ed3fd-106">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，選取資料庫、以滑鼠右鍵按一下您想要建立資料分割的資料表、指向 [儲存體]，然後按一下 [管理資料分割]。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-106">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], select the database, right-click the table on which you want to create partitions, point to **Storage**, and then click **Manage Partition**.</span></span>  
  
     <span data-ttu-id="ed3fd-107">`Note`如果 [**管理資料分割**] 無法使用，表示您可能選取了不包含資料分割的資料表。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-107">`Note` If **Manage Partition** is unavailable, you may have selected a table that does not contain partitions.</span></span> <span data-ttu-id="ed3fd-108">請在 [儲存體] 子功能表中按一下 [建立資料分割]，然後使用 [建立資料分割精靈] 來建立資料表的資料分割。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-108">Click **Create Partition** on the **Storage** submenu and use the **Create Partition Wizard** to create partitions in your table.</span></span>  
  
 <span data-ttu-id="ed3fd-109">如需資料分割和索引的一般資訊，請參閱 [分割資料表與索引](partitioned-tables-and-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-109">For general information about partitions and indexes, see [Partitioned Tables and Indexes](partitioned-tables-and-indexes.md).</span></span>  
  
 <span data-ttu-id="ed3fd-110">本節提供使用 [管理資料分割精靈] 來管理、修改和實作資料分割的必要資訊。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-110">This section provides the information that is required to manage, modify, and implement partitions using the **Manage Partition Wizard**.</span></span>  
  
##  <a name="in-this-section"></a><a name="Top"></a> <span data-ttu-id="ed3fd-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="ed3fd-111">In This Section</span></span>  
 <span data-ttu-id="ed3fd-112">下列章節提供有關 [管理資料分割精靈] 頁面的說明。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-112">The following sections provide help on the pages of the **Manage Partition Wizard**.</span></span>  
  
 [<span data-ttu-id="ed3fd-113">管理資料分割精靈 (選取資料分割動作頁面)</span><span class="sxs-lookup"><span data-stu-id="ed3fd-113">Manage Partition Wizard (Select Partition Action Page)</span></span>](#SelectPartitionAction)  
  
 [<span data-ttu-id="ed3fd-114">管理資料分割精靈 (切換移入頁面)</span><span class="sxs-lookup"><span data-stu-id="ed3fd-114">Manage Partition Wizard (Switch In Page)</span></span>](#SwitchIn)  
  
 [<span data-ttu-id="ed3fd-115">管理資料分割精靈 (切換移出頁面)</span><span class="sxs-lookup"><span data-stu-id="ed3fd-115">Manage Partition Wizard (Switch Out Page)</span></span>](#SwitchOut)  
  
 [<span data-ttu-id="ed3fd-116">管理資料分割精靈 (選取臨時資料表選項頁面)</span><span class="sxs-lookup"><span data-stu-id="ed3fd-116">Manage Partition Wizard (Select Staging Table Options Page)</span></span>](#StagingTableOptions)  
  
 [<span data-ttu-id="ed3fd-117">管理資料分割精靈 (選取輸出選項頁面)</span><span class="sxs-lookup"><span data-stu-id="ed3fd-117">Manage Partition Wizard (Select Output Option Page)</span></span>](#OutputOption)  
  
 [<span data-ttu-id="ed3fd-118">管理資料分割精靈 (新增作業排程頁面)</span><span class="sxs-lookup"><span data-stu-id="ed3fd-118">Manage Partition Wizard (New Job Schedule Page)</span></span>](#NewJob)  
  
 [<span data-ttu-id="ed3fd-119">管理資料分割精靈 (摘要頁面)</span><span class="sxs-lookup"><span data-stu-id="ed3fd-119">Manage Partition Wizard (Summary Page)</span></span>](#Summary)  
  
 [<span data-ttu-id="ed3fd-120">管理資料分割精靈 (進度頁面)</span><span class="sxs-lookup"><span data-stu-id="ed3fd-120">Manage Partition Wizard (Progress Page)</span></span>](#Progress)  
  
##  <a name="select-partition-action-page"></a><a name="SelectPartitionAction"></a> <span data-ttu-id="ed3fd-121">選取資料分割動作頁面</span><span class="sxs-lookup"><span data-stu-id="ed3fd-121">Select Partition Action Page</span></span>  
 <span data-ttu-id="ed3fd-122">使用 [選取資料分割動作] 頁面，即可選擇您想要針對資料分割執行的動作。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-122">Use the **Select Partition Action** page to choose the action you want to perform on your partition.</span></span>  
  
### <a name="create-a-staging-table"></a><span data-ttu-id="ed3fd-123">建立臨時資料表</span><span class="sxs-lookup"><span data-stu-id="ed3fd-123">Create a Staging Table</span></span>  
 <span data-ttu-id="ed3fd-124">如果您擁有一份定期移轉入或移轉出資料的資料分割資料表，資料分割切換就是常見的資料分割工作。例如，您擁有一份儲存每季最新資料的資料分割資料表，而且您必須在每季結束時移入新資料並封存舊資料。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-124">Partition switching is a common partitioning task if you have a partitioned table that you migrate data into and out of on a regular basis; for example, you have a partitioned table that stores current quarterly data, and you must move in new data and archive older data at the end of each quarter.</span></span>  
  
 <span data-ttu-id="ed3fd-125">此精靈會使用相同的分割資料行、資料表與資料行結構和索引來設計臨時資料表，並且將新的資料表儲存在來源資料分割所在的檔案群組中。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-125">The wizard designs the staging table with the same partitioning column, table and column structure, and indexes, and stores the new table in the filegroup where your source partition is located.</span></span>  
  
 <span data-ttu-id="ed3fd-126">若要建立切換移入或切換移出資料分割資料的臨時資料表，請選取 [建立用於切換資料分割的暫存資料表]。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-126">To create a staging table to switch in or switch out partition data, select **Create a staging table for partition switching**.</span></span>  
  
### <a name="sliding-window-scenario"></a><span data-ttu-id="ed3fd-127">滑動視窗案例</span><span class="sxs-lookup"><span data-stu-id="ed3fd-127">Sliding Window Scenario</span></span>  
 <span data-ttu-id="ed3fd-128">若要以滑動視窗案例管理資料分割，請選取 [以滑動視窗案例管理分割資料]。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-128">To manage your partitions in a sliding-window scenario, select **Manage partitioned data in a sliding window scenario**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="ed3fd-129">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="ed3fd-129">UI element list</span></span>  
 <span data-ttu-id="ed3fd-130">**建立用於切換資料分割的臨時資料表**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-130">**Create a staging table for partition switching**</span></span>  
 <span data-ttu-id="ed3fd-131">針對您要切換移入或切換移出現有資料分割資料表的資料建立臨時資料表。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-131">Creates a staging table for the data you are switching in or switching out of the existing partitioned table.</span></span>  
  
 <span data-ttu-id="ed3fd-132">**切換移出資料分割**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-132">**Switch out partition**</span></span>  
 <span data-ttu-id="ed3fd-133">提供從資料表中移除資料分割時的選項。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-133">Provides options when removing a partition from the table.</span></span>  
  
 <span data-ttu-id="ed3fd-134">**切換移入資料分割**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-134">**Switch in partition**</span></span>  
 <span data-ttu-id="ed3fd-135">提供在資料表中加入資料分割時的選項。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-135">Provides options when adding a partition to the table.</span></span>  
  
 <span data-ttu-id="ed3fd-136">**以滑動視窗案例管理分割資料**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-136">**Manage partitioned data in a sliding window scenario**</span></span>  
 <span data-ttu-id="ed3fd-137">將空白的資料分割附加至可用於切換移入資料的現有資料表。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-137">Appends an empty partition to the existing table that can be used for switching in data.</span></span> <span data-ttu-id="ed3fd-138">此精靈目前支援切換移入最後一個資料分割以及切換移出第一個資料分割。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-138">The wizard currently supports switching into the last partition and switching out the first partition.</span></span>  
  
 <span data-ttu-id="ed3fd-139">![與 [回到頁首] 連結搭配使用的箭頭圖示](../../2014-toc/media/uparrow16x16.gif "與 [回到頁首] 連結搭配使用的箭頭圖示") [本節內容](#Top)</span><span class="sxs-lookup"><span data-stu-id="ed3fd-139">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Section](#Top)</span></span>  
  
##  <a name="select-partition-switching-in-options-page"></a><a name="SwitchIn"></a> <span data-ttu-id="ed3fd-140">選取資料分割切換移入選項頁面</span><span class="sxs-lookup"><span data-stu-id="ed3fd-140">Select Partition Switching-In Options Page</span></span>  
 <span data-ttu-id="ed3fd-141">使用 [選取資料分割切換移入選項] 頁面，選取您想要切換移入資料分割資料表的暫存資料表。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-141">Use the **Select Partition Switching-In options** page to select the staging table you are switching into the partitioned table.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="ed3fd-142">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="ed3fd-142">UI element list</span></span>  
 <span data-ttu-id="ed3fd-143">**顯示所有資料分割**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-143">**Show All Partitions**</span></span>  
 <span data-ttu-id="ed3fd-144">選取此選項可顯示所有資料分割，包括目前在資料分割資料表中的資料分割。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-144">Select to show all partitions, including the partitions currently in the partitioned table.</span></span>  
  
 <span data-ttu-id="ed3fd-145">**資料分割方格**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-145">**Partition grid**</span></span>  
 <span data-ttu-id="ed3fd-146">顯示您所選取之資料分割的資料分割名稱、[左界限]、[右界限]、[檔案群組] 和 [資料列計數]。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-146">Displays the partition name, **Left boundary**, **Right boundary**, **Filegroup**, and **Row count** of the partitions you selected.</span></span>  
  
 <span data-ttu-id="ed3fd-147">**切換移入資料表**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-147">**Switch in table**</span></span>  
 <span data-ttu-id="ed3fd-148">選取包含了您想要加入至資料分割資料表之資料分割的臨時資料表。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-148">Select the staging table that contains the partition that you want to add to your partitioned table.</span></span> <span data-ttu-id="ed3fd-149">您必須先建立此暫存資料表，然後才能使用 [管理資料分割精靈] 來切換移入資料分割。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-149">You must create this staging table before you switch-in partitions with the **Manage PartitionsWizard**.</span></span>  
  
 <span data-ttu-id="ed3fd-150">![與 [回到頁首] 連結搭配使用的箭頭圖示](../../2014-toc/media/uparrow16x16.gif "與 [回到頁首] 連結搭配使用的箭頭圖示") [本節內容](#Top)</span><span class="sxs-lookup"><span data-stu-id="ed3fd-150">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Section](#Top)</span></span>  
  
##  <a name="select-partition-switching-out-options-page"></a><a name="SwitchOut"></a> <span data-ttu-id="ed3fd-151">選取資料分割切換移出選項頁面</span><span class="sxs-lookup"><span data-stu-id="ed3fd-151">Select Partition Switching-Out Options Page</span></span>  
 <span data-ttu-id="ed3fd-152">使用 [選取資料分割切換移出選項] 頁面，選取資料分割和暫存資料表來保存您想要切換移出資料分割資料表的分割資料。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-152">Use the **Select Partition Switching-Out options** page to select the partition and the staging table to hold the partitioned data that you are switching out of the partitioned table.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="ed3fd-153">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="ed3fd-153">UI element list</span></span>  
 <span data-ttu-id="ed3fd-154">**資料分割方格**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-154">**Partition grid**</span></span>  
 <span data-ttu-id="ed3fd-155">顯示您所選取之資料分割的資料分割名稱、[左界限]、[右界限]、[檔案群組] 和 [資料列計數]。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-155">Displays the partition name, **Left boundary**, **Right boundary**, **Filegroup**, and **Row count** of the partitions you selected.</span></span>  
  
 <span data-ttu-id="ed3fd-156">**切換移出資料表**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-156">**Switch out table**</span></span>  
 <span data-ttu-id="ed3fd-157">選擇要將資料切換移出到其中的新資料表或是現有資料表。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-157">Choose a new table or an existing table to switch-out your data to.</span></span>  
  
 <span data-ttu-id="ed3fd-158">**新增**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-158">**New**</span></span>  
 <span data-ttu-id="ed3fd-159">針對您想要用來讓資料分割切換移出目前來源資料表的臨時資料表輸入新的名稱。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-159">Enter a new name for the staging table you want to use for the partition to switch out of the current source table.</span></span>  
  
 <span data-ttu-id="ed3fd-160">**現有的**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-160">**Existing**</span></span>  
 <span data-ttu-id="ed3fd-161">選取您想要用來讓資料分割切換移出目前來源資料表的現有臨時資料表。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-161">Select an existing staging table you want to use for the partition you want to switch out of the current source table.</span></span> <span data-ttu-id="ed3fd-162">如果現有的資料表含有資料，您切換移出的資料就會覆寫這項資料。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-162">If the existing table contains data, this data will be overwritten with the data you are switching out.</span></span>  
  
 <span data-ttu-id="ed3fd-163">![與 [回到頁首] 連結搭配使用的箭頭圖示](../../2014-toc/media/uparrow16x16.gif "與 [回到頁首] 連結搭配使用的箭頭圖示") [本節內容](#Top)</span><span class="sxs-lookup"><span data-stu-id="ed3fd-163">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Section](#Top)</span></span>  
  
##  <a name="select-the-staging-table-options-page"></a><a name="StagingTableOptions"></a> <span data-ttu-id="ed3fd-164">選取暫存資料表選項頁面</span><span class="sxs-lookup"><span data-stu-id="ed3fd-164">Select the Staging Table Options Page</span></span>  
 <span data-ttu-id="ed3fd-165">使用 [選取暫存資料表選項] 頁面，即可建立您想要用來切換分割資料的暫存資料表。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-165">Use the **Select the Staging Table Options** page to create the staging table you want to use for switching your partitioned data.</span></span>  
  
 <span data-ttu-id="ed3fd-166">臨時資料表必須與來源資料表所在的選取資料分割位於相同的檔案群組中。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-166">Staging tables must reside in the same filegroup of the selected partition where the source table is located.</span></span> <span data-ttu-id="ed3fd-167">臨時資料表必須鏡像來源資料表和目的地資料表的設計。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-167">The staging table must mirror the design of both the source table and the destination table.</span></span>  
  
 <span data-ttu-id="ed3fd-168">您也可以在臨時資料表中建立存在來源資料分割內的相同索引。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-168">You can also create the same indexes in the staging table that exist in the source partition.</span></span> <span data-ttu-id="ed3fd-169">臨時資料表會自動包含以來源資料分割元素為基礎的條件約束。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-169">The staging table automatically contains a constraint based on the elements of the source partition.</span></span> <span data-ttu-id="ed3fd-170">這個條件約束通常是根據來源資料分割的界限值產生。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-170">This constraint is typically generated from the boundary value of the source partition.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="ed3fd-171">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="ed3fd-171">UI element list</span></span>  
 <span data-ttu-id="ed3fd-172">**臨時資料表名稱**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-172">**Staging table name**</span></span>  
 <span data-ttu-id="ed3fd-173">為臨時資料表建立名稱，或接受顯示在編輯方塊中的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-173">Create a name for the staging table or accept the default name displayed in the edit box.</span></span>  
  
 <span data-ttu-id="ed3fd-174">**切換資料分割**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-174">**Switch partition**</span></span>  
 <span data-ttu-id="ed3fd-175">選取您想要切換移出目前資料表的來源資料分割。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-175">Select the source partition that you want to switch out of the current table.</span></span>  
  
 <span data-ttu-id="ed3fd-176">**新界限值**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-176">**New boundary value**</span></span>  
 <span data-ttu-id="ed3fd-177">選取或輸入您想要用於臨時資料表之資料分割的界限值。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-177">Select or enter the boundary value you want for the partition in the staging table.</span></span>  
  
 <span data-ttu-id="ed3fd-178">**檔案群組**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-178">**Filegroup**</span></span>  
 <span data-ttu-id="ed3fd-179">為新的資料表選取檔案群組。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-179">Select a filegroup for the new table.</span></span>  
  
 <span data-ttu-id="ed3fd-180">![與 [回到頁首] 連結搭配使用的箭頭圖示](../../2014-toc/media/uparrow16x16.gif "與 [回到頁首] 連結搭配使用的箭頭圖示") [本節內容](#Top)</span><span class="sxs-lookup"><span data-stu-id="ed3fd-180">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Section](#Top)</span></span>  
  
##  <a name="select-output-option-page"></a><a name="OutputOption"></a> <span data-ttu-id="ed3fd-181">選取輸出選項頁面</span><span class="sxs-lookup"><span data-stu-id="ed3fd-181">Select Output Option Page</span></span>  
 <span data-ttu-id="ed3fd-182">使用 [選取輸出選項] 頁面，指定要如何完成資料分割修改。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-182">Use the **Select Output Option** page to specify how you want to complete the modifications to your partitions.</span></span>  
  
### <a name="create-script"></a><span data-ttu-id="ed3fd-183">建立指令碼</span><span class="sxs-lookup"><span data-stu-id="ed3fd-183">Create Script</span></span>  
 <span data-ttu-id="ed3fd-184">當精靈完成時，它會在查詢編輯器中建立指令碼，以便修改資料表中的資料分割。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-184">When the wizard finishes, it creates a script in Query Editor to modify partitions in the table.</span></span> <span data-ttu-id="ed3fd-185">如果您想要檢閱此指令碼，然後手動執行指令碼，請選取 [建立指令碼]。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-185">Select **Create Script** if you want to review the script, and then execute the script manually.</span></span>  
  
 <span data-ttu-id="ed3fd-186">**編寫指令碼至檔案**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-186">**Script to file**</span></span>  
 <span data-ttu-id="ed3fd-187">產生指令碼至 .sql 檔案。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-187">Generate the script to a .sql file.</span></span> <span data-ttu-id="ed3fd-188">指定 [Unicode] 或 [ANSI 文字]。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-188">Specify either **Unicode** or **ANSI text**.</span></span> <span data-ttu-id="ed3fd-189">若要指定檔案的名稱和位置，請按一下 [瀏覽]。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-189">To specify a name and location for the file, click **Browse**.</span></span>  
  
 <span data-ttu-id="ed3fd-190">**編寫指令碼至剪貼簿**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-190">**Script to Clipboard**</span></span>  
 <span data-ttu-id="ed3fd-191">將指令碼儲存至剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-191">Save the script to the Clipboard.</span></span>  
  
 <span data-ttu-id="ed3fd-192">**編寫指令碼至新增查詢視窗**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-192">**Script to New Query Window**</span></span>  
 <span data-ttu-id="ed3fd-193">產生指令碼至 [查詢編輯器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-193">Generate the script to a Query Editor window.</span></span> <span data-ttu-id="ed3fd-194">如果未開啟編輯器視窗，就會開啟新編輯器視窗做為指令碼的目標。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-194">If no editor window is open, a new editor window opens as the target for the script.</span></span>  
  
### <a name="run-immediately"></a><span data-ttu-id="ed3fd-195">立即執行</span><span class="sxs-lookup"><span data-stu-id="ed3fd-195">Run Immediately</span></span>  
 <span data-ttu-id="ed3fd-196">**Run immediately**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-196">**Run immediately**</span></span>  
 <span data-ttu-id="ed3fd-197">當您按 [下一步] 或 [完成] 時，讓精靈完成對資料分割所做的修改。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-197">Have the wizard finish modifications to the partitions when you click **Next** or **Finish**.</span></span>  
  
### <a name="schedule"></a><span data-ttu-id="ed3fd-198">排程</span><span class="sxs-lookup"><span data-stu-id="ed3fd-198">Schedule</span></span>  
 <span data-ttu-id="ed3fd-199">選取此選項即可在排程的日期和時間修改資料表資料分割。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-199">Select to modify the table partitions at a scheduled date and time.</span></span>  
  
 <span data-ttu-id="ed3fd-200">**變更排程**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-200">**Change schedule**</span></span>  
 <span data-ttu-id="ed3fd-201">開啟 [新增作業排程] 對話方塊，以便選取、變更或檢視排程作業的屬性。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-201">Opens the **New Job Schedule** dialog box, where you can select, change, or view the properties of the scheduled job.</span></span>  
  
 <span data-ttu-id="ed3fd-202">![與 [回到頁首] 連結搭配使用的箭頭圖示](../../2014-toc/media/uparrow16x16.gif "與 [回到頁首] 連結搭配使用的箭頭圖示") [本節內容](#Top)</span><span class="sxs-lookup"><span data-stu-id="ed3fd-202">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Section](#Top)</span></span>  
  
##  <a name="new-job-schedule-page"></a><a name="NewJob"></a> <span data-ttu-id="ed3fd-203">新增作業排程頁面</span><span class="sxs-lookup"><span data-stu-id="ed3fd-203">New Job Schedule Page</span></span>  
 <span data-ttu-id="ed3fd-204">使用 [新增作業排程] 頁面，即可檢視和變更排程的屬性。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-204">Use the **New Job Schedule** page to view and change the properties of the schedule.</span></span>  
  
### <a name="options"></a><span data-ttu-id="ed3fd-205">選項。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-205">Options</span></span>  
 <span data-ttu-id="ed3fd-206">選取您想要用於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業的排程類型。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-206">Select the type of schedule you want for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span>  
  
 <span data-ttu-id="ed3fd-207">**名稱**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-207">**Name**</span></span>  
 <span data-ttu-id="ed3fd-208">輸入排程的新名稱。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-208">Type a new name for the schedule.</span></span>  
  
 <span data-ttu-id="ed3fd-209">**排程中的作業**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-209">**Jobs in schedule**</span></span>  
 <span data-ttu-id="ed3fd-210">檢視使用此排程的現有作業。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-210">View the existing jobs that use the schedule.</span></span>  
  
 <span data-ttu-id="ed3fd-211">**排程類型**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-211">**Schedule type**</span></span>  
 <span data-ttu-id="ed3fd-212">選取排程類型。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-212">Select the type of schedule.</span></span>  
  
 <span data-ttu-id="ed3fd-213">**已啟用**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-213">**Enabled**</span></span>  
 <span data-ttu-id="ed3fd-214">啟用或停用排程。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-214">Enable or disable the schedule.</span></span>  
  
### <a name="recurring-schedule-types-options"></a><span data-ttu-id="ed3fd-215">重複執行排程類型選項</span><span class="sxs-lookup"><span data-stu-id="ed3fd-215">Recurring Schedule Types Options</span></span>  
 <span data-ttu-id="ed3fd-216">選取排程作業的頻率。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-216">Select the frequency of the scheduled job.</span></span>  
  
 <span data-ttu-id="ed3fd-217">**發生於**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-217">**Occurs**</span></span>  
 <span data-ttu-id="ed3fd-218">選取排程重複執行的間隔。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-218">Select the interval at which the schedule recurs.</span></span>  
  
 <span data-ttu-id="ed3fd-219">**重複頻率**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-219">**Recurs every**</span></span>  
 <span data-ttu-id="ed3fd-220">選取排程重複執行間隔的日數或週數。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-220">Select the number of days or weeks between recurrences of the schedule.</span></span> <span data-ttu-id="ed3fd-221">每月排程無法使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-221">This option is not available for monthly schedules.</span></span>  
  
 <span data-ttu-id="ed3fd-222">**星期一**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-222">**Monday**</span></span>  
 <span data-ttu-id="ed3fd-223">設定作業於星期一發生。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-223">Set the job to occur on a Monday.</span></span> <span data-ttu-id="ed3fd-224">只有每週排程可以使用。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-224">Only available for weekly schedules.</span></span>  
  
 <span data-ttu-id="ed3fd-225">**星期二**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-225">**Tuesday**</span></span>  
 <span data-ttu-id="ed3fd-226">設定作業於星期二發生。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-226">Set the job to occur on a Tuesday.</span></span> <span data-ttu-id="ed3fd-227">只有每週排程可以使用。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-227">Only available for weekly schedules.</span></span>  
  
 <span data-ttu-id="ed3fd-228">**星期三**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-228">**Wednesday**</span></span>  
 <span data-ttu-id="ed3fd-229">設定作業於星期三發生。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-229">Set the job to occur on a Wednesday.</span></span> <span data-ttu-id="ed3fd-230">只有每週排程可以使用。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-230">Only available for weekly schedules.</span></span>  
  
 <span data-ttu-id="ed3fd-231">**星期四**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-231">**Thursday**</span></span>  
 <span data-ttu-id="ed3fd-232">設定作業於星期四發生。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-232">Set the job to occur on a Thursday.</span></span> <span data-ttu-id="ed3fd-233">只有每週排程可以使用。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-233">Only available for weekly schedules.</span></span>  
  
 <span data-ttu-id="ed3fd-234">**星期五**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-234">**Friday**</span></span>  
 <span data-ttu-id="ed3fd-235">設定作業於星期五發生。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-235">Set the job to occur on a Friday.</span></span> <span data-ttu-id="ed3fd-236">只有每週排程可以使用。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-236">Only available for weekly schedules.</span></span>  
  
 <span data-ttu-id="ed3fd-237">**星期六**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-237">**Saturday**</span></span>  
 <span data-ttu-id="ed3fd-238">設定作業於星期六發生。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-238">Set the job to occur on a Saturday.</span></span> <span data-ttu-id="ed3fd-239">只有每週排程可以使用。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-239">Only available for weekly schedules.</span></span>  
  
 <span data-ttu-id="ed3fd-240">**星期日**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-240">**Sunday**</span></span>  
 <span data-ttu-id="ed3fd-241">設定作業於星期日發生。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-241">Set the job to occur on a Sunday.</span></span> <span data-ttu-id="ed3fd-242">只有每週排程可以使用。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-242">Only available for weekly schedules.</span></span>  
  
 <span data-ttu-id="ed3fd-243">**Day**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-243">**Day**</span></span>  
 <span data-ttu-id="ed3fd-244">請選取排程每月在哪一日發生。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-244">Select the day of the month the schedule occurs.</span></span> <span data-ttu-id="ed3fd-245">只有每月排程可以使用。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-245">Only available for monthly schedules.</span></span>  
  
 <span data-ttu-id="ed3fd-246">**重複間隔**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-246">**of every**</span></span>  
 <span data-ttu-id="ed3fd-247">請選取排程出現間隔的月數。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-247">Select the number of months between occurrences of the schedule.</span></span> <span data-ttu-id="ed3fd-248">只有每月排程可以使用。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-248">Only available for monthly schedules.</span></span>  
  
 <span data-ttu-id="ed3fd-249">**星期**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-249">**The**</span></span>  
 <span data-ttu-id="ed3fd-250">指定排程，選擇月份中特定週數的特定星期幾。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-250">Specify a schedule for a specific day of the week on a specific week within the month.</span></span> <span data-ttu-id="ed3fd-251">只有每月排程可以使用。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-251">Only available for monthly schedules.</span></span>  
  
 <span data-ttu-id="ed3fd-252">**執行一次於**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-252">**Occurs once at**</span></span>  
 <span data-ttu-id="ed3fd-253">請設定作業每日發生的時間。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-253">Set the time for a job to occur daily.</span></span>  
  
 <span data-ttu-id="ed3fd-254">**發生間隔**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-254">**Occurs every**</span></span>  
 <span data-ttu-id="ed3fd-255">設定每隔幾個小時或幾分鐘發生一次。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-255">Set the number of hours or minutes between occurrences.</span></span>  
  
 <span data-ttu-id="ed3fd-256">**開始日期**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-256">**Start date**</span></span>  
 <span data-ttu-id="ed3fd-257">請設定這個排程開始有效的日期。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-257">Set the date when this schedule will become effective.</span></span>  
  
 <span data-ttu-id="ed3fd-258">**結束日期**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-258">**End date**</span></span>  
 <span data-ttu-id="ed3fd-259">請設定排程將不再有效的日期。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-259">Set the date when the schedule will no longer be effective.</span></span>  
  
 <span data-ttu-id="ed3fd-260">**沒有結束日期**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-260">**No end date**</span></span>  
 <span data-ttu-id="ed3fd-261">請指定排程將無限期地保持有效。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-261">Specify that the schedule will remain effective indefinitely.</span></span>  
  
### <a name="one-time-schedule-types-options"></a><span data-ttu-id="ed3fd-262">僅執行一次的排程類型選項</span><span class="sxs-lookup"><span data-stu-id="ed3fd-262">One Time Schedule Types Options</span></span>  
 <span data-ttu-id="ed3fd-263">如果您將作業排程為僅執行一次，就必須選取未來的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-263">If you schedule a job to run once, you must select a date and time in the future.</span></span>  
  
 <span data-ttu-id="ed3fd-264">**日期**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-264">**Date**</span></span>  
 <span data-ttu-id="ed3fd-265">選取作業要執行的日期。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-265">Select the date for the job to run.</span></span>  
  
 <span data-ttu-id="ed3fd-266">**Time**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-266">**Time**</span></span>  
 <span data-ttu-id="ed3fd-267">選取作業要執行的時間。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-267">Select the time for the job to run.</span></span>  
  
 <span data-ttu-id="ed3fd-268">![與 [回到頁首] 連結搭配使用的箭頭圖示](../../2014-toc/media/uparrow16x16.gif "與 [回到頁首] 連結搭配使用的箭頭圖示") [本節內容](#Top)</span><span class="sxs-lookup"><span data-stu-id="ed3fd-268">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Section](#Top)</span></span>  
  
##  <a name="summary-page"></a><a name="Summary"></a> <span data-ttu-id="ed3fd-269">摘要頁面</span><span class="sxs-lookup"><span data-stu-id="ed3fd-269">Summary Page</span></span>  
 <span data-ttu-id="ed3fd-270">使用 [摘要] 頁面，即可檢閱您在先前頁面中選取的選項。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-270">Use the **Summary** page to review the options that you have selected on the previous pages.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="ed3fd-271">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="ed3fd-271">UI element list</span></span>  
 <span data-ttu-id="ed3fd-272">**檢閱您的選取項目**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-272">**Review your selections**</span></span>  
 <span data-ttu-id="ed3fd-273">針對精靈的每一頁，顯示您所選取的項目。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-273">Displays the selections you have made for each page of the wizard.</span></span> <span data-ttu-id="ed3fd-274">按一下節點即可展開並檢視您先前選取的選項。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-274">Click a node to expand and view your previously selected options.</span></span>  
  
 <span data-ttu-id="ed3fd-275">![與 [回到頁首] 連結搭配使用的箭頭圖示](../../2014-toc/media/uparrow16x16.gif "與 [回到頁首] 連結搭配使用的箭頭圖示") [本節內容](#Top)</span><span class="sxs-lookup"><span data-stu-id="ed3fd-275">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Section](#Top)</span></span>  
  
##  <a name="progress-page"></a><a name="Progress"></a> <span data-ttu-id="ed3fd-276">進度頁面</span><span class="sxs-lookup"><span data-stu-id="ed3fd-276">Progress Page</span></span>  
 <span data-ttu-id="ed3fd-277">使用 [進度] 頁面，即可監視有關 [管理資料分割精靈] 動作的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-277">Use the **Progress** page to monitor status information about the actions of the **Manage Partition Wizard**.</span></span> <span data-ttu-id="ed3fd-278">根據您在精靈中選取的選項，[進度] 頁面可能會包含一或多個動作。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-278">Depending on the options that you selected in the wizard, the **Progress** page might contain one or more actions.</span></span> <span data-ttu-id="ed3fd-279">頂端的方塊會顯示精靈的整體狀態以及精靈已接收的狀態、錯誤和警告訊息數。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-279">The top box displays the overall status of the wizard and the number of status, error, and warning messages that the wizard has received.</span></span>  
  
### <a name="options"></a><span data-ttu-id="ed3fd-280">選項。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-280">Options</span></span>  
 <span data-ttu-id="ed3fd-281">**詳細資料**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-281">**Details**</span></span>  
 <span data-ttu-id="ed3fd-282">提供從精靈所採取的動作傳回的動作、狀態和任何訊息。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-282">Provides the action, status, and any messages that are returned from action taken by the wizard.</span></span>  
  
 <span data-ttu-id="ed3fd-283">**動作**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-283">**Action**</span></span>  
 <span data-ttu-id="ed3fd-284">指定每個動作的類型和名稱。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-284">Specifies the type and name of each action.</span></span>  
  
 <span data-ttu-id="ed3fd-285">**狀態**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-285">**Status**</span></span>  
 <span data-ttu-id="ed3fd-286">指出整個精靈動作傳回 [成功] 或 [失敗] 的值。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-286">Indicates whether the wizard action as a whole returned the value of **Success** or **Failure**.</span></span>  
  
 <span data-ttu-id="ed3fd-287">**訊息**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-287">**Message**</span></span>  
 <span data-ttu-id="ed3fd-288">提供從程序所傳回的任何錯誤或警告訊息。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-288">Provides any error or warning messages that are returned from the process.</span></span>  
  
 <span data-ttu-id="ed3fd-289">**停止**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-289">**Stop**</span></span>  
 <span data-ttu-id="ed3fd-290">停止精靈的動作。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-290">Stop the action of the wizard.</span></span>  
  
 <span data-ttu-id="ed3fd-291">**Report**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-291">**Report**</span></span>  
 <span data-ttu-id="ed3fd-292">建立包含 [管理資料分割精靈] 結果的報表。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-292">Create a report that contains the results of the **Manage Partition Wizard**.</span></span> <span data-ttu-id="ed3fd-293">可用選項包括：</span><span class="sxs-lookup"><span data-stu-id="ed3fd-293">The options are:</span></span>  
  
-   <span data-ttu-id="ed3fd-294">**檢視報表**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-294">**View Report**</span></span>  
  
-   <span data-ttu-id="ed3fd-295">**將報表儲存到檔案**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-295">**Save Report to File**</span></span>  
  
-   <span data-ttu-id="ed3fd-296">**複製報表到剪貼簿**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-296">**Copy Report to Clipboard**</span></span>  
  
-   <span data-ttu-id="ed3fd-297">**[以電子郵件傳送報表]**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-297">**Send Report as Email**</span></span>  
  
 <span data-ttu-id="ed3fd-298">**檢視報表**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-298">**View Report**</span></span>  
 <span data-ttu-id="ed3fd-299">開啟 [檢視報表] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-299">Open the **View Report** dialog box.</span></span> <span data-ttu-id="ed3fd-300">這個對話方塊包含 [管理資料分割精靈] 進度的文字報表。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-300">This dialog box contains a text report of the progress of the **Manage Partition Wizard**.</span></span>  
  
 <span data-ttu-id="ed3fd-301">**關閉**</span><span class="sxs-lookup"><span data-stu-id="ed3fd-301">**Close**</span></span>  
 <span data-ttu-id="ed3fd-302">關閉精靈。</span><span class="sxs-lookup"><span data-stu-id="ed3fd-302">Close the wizard.</span></span>  
  
 <span data-ttu-id="ed3fd-303">![與 [回到頁首] 連結搭配使用的箭頭圖示](../../2014-toc/media/uparrow16x16.gif "與 [回到頁首] 連結搭配使用的箭頭圖示") [本節內容](#Top)</span><span class="sxs-lookup"><span data-stu-id="ed3fd-303">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Section](#Top)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed3fd-304">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed3fd-304">See Also</span></span>  
 [<span data-ttu-id="ed3fd-305">分割資料表與索引</span><span class="sxs-lookup"><span data-stu-id="ed3fd-305">Partitioned Tables and Indexes</span></span>](partitioned-tables-and-indexes.md)  
  
  
