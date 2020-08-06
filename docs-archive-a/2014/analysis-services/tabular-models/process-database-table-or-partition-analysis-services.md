---
title: 處理資料庫、資料表或資料分割 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- SQL12.ASVS.SSMS.PARTITIONS.PROCESSINGOPTIONS.IMBI.F1
ms.assetid: 307d69c3-cabb-4dfa-b90c-9852492c1213
author: minewiskan
ms.author: owend
ms.openlocfilehash: b5d3840be43798536f1bb517007a7974a1e08728
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687188"
---
# <a name="process-database-table-or-partition"></a><span data-ttu-id="15eb8-102">處理資料庫、資料表或資料分割</span><span class="sxs-lookup"><span data-stu-id="15eb8-102">Process Database, Table, or Partition</span></span>
  <span data-ttu-id="15eb8-103">本主題中的工作描述如何使用中的 [\*\*處理 \<object> \*\* ] 對話方塊，手動處理表格式模型資料庫、資料表或資料分割 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="15eb8-103">The tasks in this topic describe how to process a tabular model database, table, or partitions manually by using the **Process \<object>** dialog box in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="15eb8-104">如需表格式模型處理的詳細資訊，請參閱[處理資料 &#40;SSAS 表格式&#41;](../process-data-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="15eb8-104">For more information about tabular model processing, see [Process Data &#40;SSAS Tabular&#41;](../process-data-ssas-tabular.md).</span></span>  
  
##  <a name="tasks"></a><a name="bkmk_process_tasks"></a><span data-ttu-id="15eb8-105">任務</span><span class="sxs-lookup"><span data-stu-id="15eb8-105">Tasks</span></span>  
  
###  <a name="to-process-a-database"></a><a name="bkmk_process_db"></a><span data-ttu-id="15eb8-106">若要處理資料庫</span><span class="sxs-lookup"><span data-stu-id="15eb8-106">To process a database</span></span>  
  
1.  <span data-ttu-id="15eb8-107">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，以滑鼠右鍵按一下您想要處理的資料庫，然後按一下 [處理資料庫]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="15eb8-107">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click on the database you want to process, and then click **Process Database**.</span></span>  
  
2.  <span data-ttu-id="15eb8-108">在 **[處理資料庫]** 對話方塊的 **[模式]** 清單方塊中，選取下列其中一個處理模式：</span><span class="sxs-lookup"><span data-stu-id="15eb8-108">In the **Process Database** dialog box, in the **Mode** listbox, select one of the following process modes:</span></span>  
  
    |<span data-ttu-id="15eb8-109">[模式]</span><span class="sxs-lookup"><span data-stu-id="15eb8-109">Mode</span></span>|<span data-ttu-id="15eb8-110">描述</span><span class="sxs-lookup"><span data-stu-id="15eb8-110">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="15eb8-111">**處理預設**</span><span class="sxs-lookup"><span data-stu-id="15eb8-111">**Process Default**</span></span>|<span data-ttu-id="15eb8-112">偵測資料庫物件的處理狀態，並且執行必要的處理，以便將尚未處理或部分處理的物件傳遞為完整處理的狀態。</span><span class="sxs-lookup"><span data-stu-id="15eb8-112">Detects the process state of database objects, and performs processing necessary to deliver unprocessed or partially processed objects to a fully processed state.</span></span> <span data-ttu-id="15eb8-113">載入空白資料表和資料分割的資料；建立或重新建立 (重新計算) 階層、導出資料行及關聯性。</span><span class="sxs-lookup"><span data-stu-id="15eb8-113">Data for empty tables and partitions is loaded; hierarchies, calculated columns, and relationships are built or rebuilt (recalculated).</span></span>|  
    |<span data-ttu-id="15eb8-114">**完整處理**</span><span class="sxs-lookup"><span data-stu-id="15eb8-114">**Process Full**</span></span>|<span data-ttu-id="15eb8-115">處理資料庫及其包含的所有物件。</span><span class="sxs-lookup"><span data-stu-id="15eb8-115">Processes a database and all the objects that it contains.</span></span> <span data-ttu-id="15eb8-116">對已處理過的物件執行完整處理時， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會先卸除該物件中的所有資料，然後再處理該物件。</span><span class="sxs-lookup"><span data-stu-id="15eb8-116">When Process Full is run for an object that has already been processed, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] drops all data in the object, and then processes the object.</span></span> <span data-ttu-id="15eb8-117">當物件已進行過任何結構性變更時，就需要這種處理。</span><span class="sxs-lookup"><span data-stu-id="15eb8-117">This kind of processing is required when a structural change has been made to an object.</span></span> <span data-ttu-id="15eb8-118">此選項需要最多資源。</span><span class="sxs-lookup"><span data-stu-id="15eb8-118">This option requires the most resources.</span></span>|  
    |<span data-ttu-id="15eb8-119">**處理清除**</span><span class="sxs-lookup"><span data-stu-id="15eb8-119">**Process Clear**</span></span>|<span data-ttu-id="15eb8-120">從資料庫物件中移除所有資料。</span><span class="sxs-lookup"><span data-stu-id="15eb8-120">Removes all data from database objects.</span></span>|  
    |<span data-ttu-id="15eb8-121">**處理重新計算**</span><span class="sxs-lookup"><span data-stu-id="15eb8-121">**Process Recalc**</span></span>|<span data-ttu-id="15eb8-122">更新並重新計算階層、關聯性和導出資料行。</span><span class="sxs-lookup"><span data-stu-id="15eb8-122">Updates and recalculates hierarchies, relationships, and calculated columns.</span></span>|  
  
3.  <span data-ttu-id="15eb8-123">在 **[處理]** 核取方塊資料行中，選取您想透過選取的模式處理的資料分割，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="15eb8-123">In the **Process** checkbox column, select the partitions you want to process with the selected mode, and then click **Ok**.</span></span>  
  
###  <a name="to-process-a-table"></a><a name="bkmk_process_table"></a><span data-ttu-id="15eb8-124">若要處理資料表</span><span class="sxs-lookup"><span data-stu-id="15eb8-124">To process a table</span></span>  
  
1.  <span data-ttu-id="15eb8-125">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，於包含您想要處理之資料表的表格式模型資料庫內，展開 [資料表]\*\*\*\* 節點、以滑鼠右鍵按一下您想要處理的資料表，然後按一下 [處理資料表]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="15eb8-125">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], in the tabular model database which contains the table you want to process, expand the **Tables** node, then right-click on the table you want to process, and then click **Process Table**.</span></span>  
  
2.  <span data-ttu-id="15eb8-126">在 **[處理資料表]** 對話方塊的 **[模式]** 清單方塊中，選取下列其中一個處理模式：</span><span class="sxs-lookup"><span data-stu-id="15eb8-126">In the **Process Table** dialog box, in the **Mode** listbox, select one of the following process modes:</span></span>  
  
    |<span data-ttu-id="15eb8-127">[模式]</span><span class="sxs-lookup"><span data-stu-id="15eb8-127">Mode</span></span>|<span data-ttu-id="15eb8-128">描述</span><span class="sxs-lookup"><span data-stu-id="15eb8-128">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="15eb8-129">**處理預設**</span><span class="sxs-lookup"><span data-stu-id="15eb8-129">**Process Default**</span></span>|<span data-ttu-id="15eb8-130">偵測資料表物件的處理狀態，並且執行必要的處理，以便將尚未處理或部分處理的物件傳遞為完整處理的狀態。</span><span class="sxs-lookup"><span data-stu-id="15eb8-130">Detects the process state of a table object, and performs processing necessary to deliver unprocessed or partially processed objects to a fully processed state.</span></span> <span data-ttu-id="15eb8-131">載入空白資料表和資料分割的資料；建立或重新建立 (重新計算) 階層、導出資料行及關聯性。</span><span class="sxs-lookup"><span data-stu-id="15eb8-131">Data for empty tables and partitions is loaded; hierarchies, calculated columns, and relationships are built or rebuilt (recalculated).</span></span>|  
    |<span data-ttu-id="15eb8-132">**完整處理**</span><span class="sxs-lookup"><span data-stu-id="15eb8-132">**Process Full**</span></span>|<span data-ttu-id="15eb8-133">處理資料表物件及其包含的所有物件。</span><span class="sxs-lookup"><span data-stu-id="15eb8-133">Processes a table object and all the objects that it contains.</span></span> <span data-ttu-id="15eb8-134">對已處理過的物件執行完整處理時， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會先卸除該物件中的所有資料，然後再處理該物件。</span><span class="sxs-lookup"><span data-stu-id="15eb8-134">When Process Full is run for an object that has already been processed, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] drops all data in the object, and then processes the object.</span></span> <span data-ttu-id="15eb8-135">當物件已進行過任何結構性變更時，就需要這種處理。</span><span class="sxs-lookup"><span data-stu-id="15eb8-135">This kind of processing is required when a structural change has been made to an object.</span></span> <span data-ttu-id="15eb8-136">此選項需要最多資源。</span><span class="sxs-lookup"><span data-stu-id="15eb8-136">This option requires the most resources.</span></span>|  
    |<span data-ttu-id="15eb8-137">**處理資料**</span><span class="sxs-lookup"><span data-stu-id="15eb8-137">**Process Data**</span></span>|<span data-ttu-id="15eb8-138">將資料載入資料表，而不重新建立階層或關聯性，或重新計算導出資料行和量值。</span><span class="sxs-lookup"><span data-stu-id="15eb8-138">Load data into a table without rebuilding hierarchies or relationships or recalculating calculated columns and measures.</span></span>|  
    |<span data-ttu-id="15eb8-139">**處理清除**</span><span class="sxs-lookup"><span data-stu-id="15eb8-139">**Process Clear**</span></span>|<span data-ttu-id="15eb8-140">從資料表和任何資料表資料分割中移除所有資料。</span><span class="sxs-lookup"><span data-stu-id="15eb8-140">Removes all data from a table and any table partitions.</span></span>|  
    |<span data-ttu-id="15eb8-141">**處理重組**</span><span class="sxs-lookup"><span data-stu-id="15eb8-141">**Process Defrag**</span></span>|<span data-ttu-id="15eb8-142">重組輔助資料表索引。</span><span class="sxs-lookup"><span data-stu-id="15eb8-142">Defragments the auxiliary table indexes.</span></span>|  
  
3.  <span data-ttu-id="15eb8-143">在 [資料表] 核取方塊資料行中，確認資料表並選擇性地選取您想要處理的任何其他資料表，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="15eb8-143">In the table checkbox column, verify the table and optionally select any additional tables you want to process, and then click **Ok**.</span></span>  
  
###  <a name="to-process-one-or-more-partitions"></a><a name="bkmk_process_partition"></a> <span data-ttu-id="15eb8-144">若要處理一個或多個資料分割</span><span class="sxs-lookup"><span data-stu-id="15eb8-144">To process one or more partitions</span></span>  
  
1.  <span data-ttu-id="15eb8-145">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，以滑鼠右鍵按一下含有您要處理之資料分割的資料表，然後按一下 [資料分割]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="15eb8-145">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click on the table that has the partitions you want to process, and then click **Partitions**.</span></span>  
  
2.  <span data-ttu-id="15eb8-146">在 **[資料分割]** 對話方塊的 **[資料分割]** 中，按一下 [處理] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="15eb8-146">In the **Partitions** dialog box, in **Partitions**, click the Process button.</span></span>  
  
3.  <span data-ttu-id="15eb8-147">在 **[處理資料分割]** 對話方塊的 **[模式]** 清單方塊中，選取下列其中一個處理模式：</span><span class="sxs-lookup"><span data-stu-id="15eb8-147">In the **Process Partition** dialog box, in the **Mode** listbox, select one of the following process modes:</span></span>  
  
    |<span data-ttu-id="15eb8-148">[模式]</span><span class="sxs-lookup"><span data-stu-id="15eb8-148">Mode</span></span>|<span data-ttu-id="15eb8-149">描述</span><span class="sxs-lookup"><span data-stu-id="15eb8-149">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="15eb8-150">**處理預設**</span><span class="sxs-lookup"><span data-stu-id="15eb8-150">**Process Default**</span></span>|<span data-ttu-id="15eb8-151">偵測資料分割物件的處理狀態，並且執行必要的處理，以便將尚未處理或部分處理的資料分割物件傳遞為完整處理的狀態。</span><span class="sxs-lookup"><span data-stu-id="15eb8-151">Detects the process state of a partition object, and performs processing necessary to deliver unprocessed or partially processed partition objects to a fully processed state.</span></span> <span data-ttu-id="15eb8-152">載入空白資料表和資料分割的資料；建立或重新建立 (重新計算) 階層、導出資料行及關聯性。</span><span class="sxs-lookup"><span data-stu-id="15eb8-152">Data for empty tables and partitions is loaded; hierarchies, calculated columns, and relationships are built or rebuilt (recalculated).</span></span>|  
    |<span data-ttu-id="15eb8-153">**完整處理**</span><span class="sxs-lookup"><span data-stu-id="15eb8-153">**Process Full**</span></span>|<span data-ttu-id="15eb8-154">處理資料分割物件及其包含的所有物件。</span><span class="sxs-lookup"><span data-stu-id="15eb8-154">Processes a partition object and all the objects that it contains.</span></span> <span data-ttu-id="15eb8-155">對已處理過的物件執行完整處理時， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會先卸除該物件中的所有資料，然後再處理該物件。</span><span class="sxs-lookup"><span data-stu-id="15eb8-155">When Process Full is run for an object that has already been processed, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] drops all data in the object, and then processes the object.</span></span> <span data-ttu-id="15eb8-156">當物件已進行過任何結構性變更時，就需要這種處理。</span><span class="sxs-lookup"><span data-stu-id="15eb8-156">This kind of processing is required when a structural change has been made to an object.</span></span>|  
    |<span data-ttu-id="15eb8-157">**處理資料**</span><span class="sxs-lookup"><span data-stu-id="15eb8-157">**Process Data**</span></span>|<span data-ttu-id="15eb8-158">將資料載入資料分割或資料表，而不重新建立階層或關聯性，或重新計算導出資料行和量值。</span><span class="sxs-lookup"><span data-stu-id="15eb8-158">Load data into a partition or a table without rebuilding hierarchies or relationships or recalculating calculated columns and measures.</span></span>|  
    |<span data-ttu-id="15eb8-159">**處理清除**</span><span class="sxs-lookup"><span data-stu-id="15eb8-159">**Process Clear**</span></span>|<span data-ttu-id="15eb8-160">移除資料分割中的所有資料。</span><span class="sxs-lookup"><span data-stu-id="15eb8-160">Removes all data from a partition.</span></span>|  
    |<span data-ttu-id="15eb8-161">**處理加入**</span><span class="sxs-lookup"><span data-stu-id="15eb8-161">**Process Add**</span></span>|<span data-ttu-id="15eb8-162">以新資料累加地更新資料分割。</span><span class="sxs-lookup"><span data-stu-id="15eb8-162">Incrementally update partition with new data.</span></span>|  
  
4.  <span data-ttu-id="15eb8-163">在 **[處理]** 核取方塊資料行中，選取您想透過選取的模式處理的資料分割，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="15eb8-163">In the **Process** checkbox column, select the partitions you want to process with the selected mode, and then click **Ok**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15eb8-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15eb8-164">See Also</span></span>  
 <span data-ttu-id="15eb8-165">[表格式模型資料分割 &#40;SSAS 表格式&#41;](tabular-model-partitions-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="15eb8-165">[Tabular Model Partitions &#40;SSAS Tabular&#41;](tabular-model-partitions-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="15eb8-166">建立及管理表格式模型資料分割 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="15eb8-166">Create and Manage Tabular Model Partitions &#40;SSAS Tabular&#41;</span></span>](create-and-manage-tabular-model-partitions-ssas-tabular.md)  
  
  
