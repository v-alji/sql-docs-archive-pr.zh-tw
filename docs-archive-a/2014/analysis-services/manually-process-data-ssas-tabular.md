---
title: 手動處理 (SSAS 表格式) 的資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.datarefreshprogressdb.f1
ms.assetid: 0918c04c-c1e6-45b4-acfa-96fa578e684b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 51bdb1b9535685db4fc35dbdd791e6b4d9bed1b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598628"
---
# <a name="manually-process-data-ssas-tabular"></a><span data-ttu-id="7cce6-102">手動處理資料 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="7cce6-102">Manually Process Data (SSAS Tabular)</span></span>
  <span data-ttu-id="7cce6-103">此主題描述如何手動處理 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中的工作空間資料。</span><span class="sxs-lookup"><span data-stu-id="7cce6-103">This topic describes how to manually process workspace data in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="7cce6-104">當您撰寫使用外部資料的表格式模型時，可以使用處理命令來手動重新整理資料。</span><span class="sxs-lookup"><span data-stu-id="7cce6-104">When you author a tabular model that uses external data, you can manually refresh the data by using the Process command.</span></span> <span data-ttu-id="7cce6-105">您可以處理單一資料表、模型中的所有資料表或是一個或多個資料分割。</span><span class="sxs-lookup"><span data-stu-id="7cce6-105">You can process a single table, all tables in the model, or one or more partitions.</span></span> <span data-ttu-id="7cce6-106">每次處理資料時，您也可能需要重新計算資料。</span><span class="sxs-lookup"><span data-stu-id="7cce6-106">Whenever you process data, you may also need to recalculate data.</span></span>  <span data-ttu-id="7cce6-107">處理資料表示從外部來源取得最新的資料。</span><span class="sxs-lookup"><span data-stu-id="7cce6-107">Processing data means getting the latest data from external sources.</span></span> <span data-ttu-id="7cce6-108">重新計算表示更新使用資料之任何公式的結果。</span><span class="sxs-lookup"><span data-stu-id="7cce6-108">Recalculating means updating the result of any formula that uses the data.</span></span>  
  
 <span data-ttu-id="7cce6-109">本主題的章節：</span><span class="sxs-lookup"><span data-stu-id="7cce6-109">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="7cce6-110">手動處理資料</span><span class="sxs-lookup"><span data-stu-id="7cce6-110">Manually Process Data</span></span>](#bkmk_mahually_process)  
  
-   [<span data-ttu-id="7cce6-111">資料處理進度</span><span class="sxs-lookup"><span data-stu-id="7cce6-111">Data Process Progress</span></span>](#bkmk_data_process_progress)  
  
##  <a name="manually-process-data"></a><a name="bkmk_mahually_process"></a><span data-ttu-id="7cce6-112">手動處理資料</span><span class="sxs-lookup"><span data-stu-id="7cce6-112">Manually Process Data</span></span>  
  
#### <a name="to-process-data-for-a-single-table-or-all-tables-in-a-model"></a><span data-ttu-id="7cce6-113">處理模型中單一資料表或所有資料表的資料</span><span class="sxs-lookup"><span data-stu-id="7cce6-113">To process data for a single table or all tables in a model</span></span>  
  
1.  <span data-ttu-id="7cce6-114">在模型設計師中，按一下要處理的資料表。</span><span class="sxs-lookup"><span data-stu-id="7cce6-114">In the model designer, click the table you want to process.</span></span>  
  
2.  <span data-ttu-id="7cce6-115">按一下 **[模型]** 功能表，然後按一下 **[處理]**，再按一下 **[處理]** 或 **[處理全部]**。</span><span class="sxs-lookup"><span data-stu-id="7cce6-115">Click on the **Model** menu, then click **Process**, and then click **Process** or **Process All**.</span></span>  
  
#### <a name="to-process-data-for-all-tables-using-the-same-connection"></a><span data-ttu-id="7cce6-116">若要使用相同連接處理所有資料表的資料</span><span class="sxs-lookup"><span data-stu-id="7cce6-116">To process data for all tables using the same connection</span></span>  
  
1.  <span data-ttu-id="7cce6-117">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，按一下 **[模型]** 功能表，然後按一下 **[現有連接]**。</span><span class="sxs-lookup"><span data-stu-id="7cce6-117">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click on the **Model** menu, and then click **Existing Connections**.</span></span>  
  
2.  <span data-ttu-id="7cce6-118">在 **[現有連接]** 對話方塊中，選取連接，然後按一下 **[處理]**。</span><span class="sxs-lookup"><span data-stu-id="7cce6-118">In the **Existing Connections** dialog box, select a connection, and then click **Process**.</span></span>  
  
#### <a name="to-process-data-for-one-or-more-partitions"></a><span data-ttu-id="7cce6-119">若要處理一個或多個資料分割的資料</span><span class="sxs-lookup"><span data-stu-id="7cce6-119">To process data for one or more partitions</span></span>  
  
1.  <span data-ttu-id="7cce6-120">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，按一下 **[模型]** 功能表，然後指向 **[處理]**，再按一下 **[處理資料分割]**。</span><span class="sxs-lookup"><span data-stu-id="7cce6-120">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click the **Model** menu, then point to **Process**, and then click **Process Partitions**.</span></span>  
  
2.  <span data-ttu-id="7cce6-121">在 **[處理資料分割]** 對話方塊的 **[模式]** 中，選取下列其中一個處理模式：</span><span class="sxs-lookup"><span data-stu-id="7cce6-121">In the **Process Partitions** dialog box, in **Mode**, select one of the following process modes:</span></span>  
  
    |<span data-ttu-id="7cce6-122">[模式]</span><span class="sxs-lookup"><span data-stu-id="7cce6-122">Mode</span></span>|<span data-ttu-id="7cce6-123">描述</span><span class="sxs-lookup"><span data-stu-id="7cce6-123">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="7cce6-124">**處理預設**</span><span class="sxs-lookup"><span data-stu-id="7cce6-124">**Process Default**</span></span>|<span data-ttu-id="7cce6-125">偵測資料分割物件的處理狀態，並且執行必要的處理，以便將尚未處理或部分處理的資料分割物件傳遞為完整處理的狀態。</span><span class="sxs-lookup"><span data-stu-id="7cce6-125">Detects the process state of a partition object, and performs processing necessary to deliver unprocessed or partially processed partition objects to a fully processed state.</span></span> <span data-ttu-id="7cce6-126">載入空白資料表和資料分割的資料；建立或重新建立階層、導出資料行及關聯性。</span><span class="sxs-lookup"><span data-stu-id="7cce6-126">Data for empty tables and partitions is loaded; hierarchies, calculated columns, and relationships are built or rebuilt.</span></span>|  
    |<span data-ttu-id="7cce6-127">**完整處理**</span><span class="sxs-lookup"><span data-stu-id="7cce6-127">**Process Full**</span></span>|<span data-ttu-id="7cce6-128">處理資料分割物件及其包含的所有物件。</span><span class="sxs-lookup"><span data-stu-id="7cce6-128">Processes a partition object and all the objects that it contains.</span></span> <span data-ttu-id="7cce6-129">對已處理過的物件執行完整處理時， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 會先卸除該物件中的所有資料，然後再處理該物件。</span><span class="sxs-lookup"><span data-stu-id="7cce6-129">When Process Full is run for an object that has already been processed, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] drops all data in the object, and then processes the object.</span></span> <span data-ttu-id="7cce6-130">當物件已進行過任何結構性變更時，就需要這種處理。</span><span class="sxs-lookup"><span data-stu-id="7cce6-130">This kind of processing is required when a structural change has been made to an object.</span></span>|  
    |<span data-ttu-id="7cce6-131">**處理資料**</span><span class="sxs-lookup"><span data-stu-id="7cce6-131">**Process Data**</span></span>|<span data-ttu-id="7cce6-132">將資料載入資料分割或資料表，而不重新建立階層或關聯性，或重新計算導出資料行和量值。</span><span class="sxs-lookup"><span data-stu-id="7cce6-132">Load data into a partition or a table without rebuilding hierarchies or relationships or recalculating calculated columns and measures.</span></span>|  
    |<span data-ttu-id="7cce6-133">**處理清除**</span><span class="sxs-lookup"><span data-stu-id="7cce6-133">**Process Clear**</span></span>|<span data-ttu-id="7cce6-134">移除資料分割中的所有資料。</span><span class="sxs-lookup"><span data-stu-id="7cce6-134">Removes all data from a partition.</span></span>|  
    |<span data-ttu-id="7cce6-135">**處理加入**</span><span class="sxs-lookup"><span data-stu-id="7cce6-135">**Process Add**</span></span>|<span data-ttu-id="7cce6-136">以新資料累加地更新資料分割。</span><span class="sxs-lookup"><span data-stu-id="7cce6-136">Incrementally update partition with new data.</span></span>|  
  
3.  <span data-ttu-id="7cce6-137">在資料分割清單中，選取要處理的資料分割，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="7cce6-137">In the partitions list, select the partitions you want to process, and then click **OK**.</span></span>  
  
##  <a name="data-process-progress"></a><a name="bkmk_data_process_progress"></a><span data-ttu-id="7cce6-138">資料處理進度</span><span class="sxs-lookup"><span data-stu-id="7cce6-138">Data Process Progress</span></span>  
 <span data-ttu-id="7cce6-139">**[資料處理進度]** 對話方塊可讓您監視您已經從外部來源匯入模型之資料的處理作業。</span><span class="sxs-lookup"><span data-stu-id="7cce6-139">The **Data Process Progress** dialog box enables you to monitor the processing of data that you have imported into the model from an external source.</span></span> <span data-ttu-id="7cce6-140">若要存取此對話方塊，請按一下 **[模型]** 功能表，然後按一下 **[處理資料分割]**、 **[處理資料表]** 或 **[處理全部]**。</span><span class="sxs-lookup"><span data-stu-id="7cce6-140">To access this dialog box, click on the **Model** menu, and then click **Process Partitions**, **Process Table** or **Process All**.</span></span>  
  
 <span data-ttu-id="7cce6-141">**狀態**</span><span class="sxs-lookup"><span data-stu-id="7cce6-141">**Status**</span></span>  
 <span data-ttu-id="7cce6-142">指出處理作業是否成功。</span><span class="sxs-lookup"><span data-stu-id="7cce6-142">Indicates whether the process operation was successful or not.</span></span>  
  
 <span data-ttu-id="7cce6-143">**詳細資料**</span><span class="sxs-lookup"><span data-stu-id="7cce6-143">**Details**</span></span>  
 <span data-ttu-id="7cce6-144">列出已匯入的資料表和檢視表、已匯入的資料列數目，並提供任何問題報告的連結。</span><span class="sxs-lookup"><span data-stu-id="7cce6-144">Lists the tables and views that were imported, the number of rows that were imported, and provides a link to a report of any issues.</span></span>  
  
 <span data-ttu-id="7cce6-145">**停止重新整理**</span><span class="sxs-lookup"><span data-stu-id="7cce6-145">**Stop Refresh**</span></span>  
 <span data-ttu-id="7cce6-146">按一下可暫停處理作業。</span><span class="sxs-lookup"><span data-stu-id="7cce6-146">Click to halt the process operation.</span></span> <span data-ttu-id="7cce6-147">如果作業耗費時間過長，或者如果有太多錯誤，這個選項會很有用。</span><span class="sxs-lookup"><span data-stu-id="7cce6-147">This option is useful if the operation is taking too long, or if there are too many errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cce6-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7cce6-148">See Also</span></span>  
 <span data-ttu-id="7cce6-149">[&#40;SSAS 表格式&#41;處理資料](process-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="7cce6-149">[Process Data &#40;SSAS Tabular&#41;](process-data-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="7cce6-150">疑難排解處理資料 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="7cce6-150">Troubleshoot Process Data &#40;SSAS Tabular&#41;</span></span>](troubleshoot-process-data-ssas-tabular.md)  
  
  
