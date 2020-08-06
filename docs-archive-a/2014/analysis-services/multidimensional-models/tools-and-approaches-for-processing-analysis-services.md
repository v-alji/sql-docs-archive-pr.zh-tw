---
title: 處理 (Analysis Services) 的工具和方法 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- process [Analysis Services]
- processing [Analysis Services]
ms.assetid: 82347a16-4145-4655-8adf-2a300f1fdf99
author: minewiskan
ms.author: owend
ms.openlocfilehash: d2b28ecf29adc8240f76ec9888f9d4cb06dda887
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596353"
---
# <a name="tools-and-approaches-for-processing-analysis-services"></a><span data-ttu-id="de41d-102">處理的工具和方式 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="de41d-102">Tools and Approaches for Processing (Analysis Services)</span></span>
  <span data-ttu-id="de41d-103">處理是 Analysis Services 查詢關聯式資料來源，然後使用該資料來擴展 Analysis Services 物件的作業。</span><span class="sxs-lookup"><span data-stu-id="de41d-103">Processing is an operation in which Analysis Services queries a relational data source and populates Analysis Services objects using that data.</span></span>  
  
 <span data-ttu-id="de41d-104">身為 Analysis Services 系統管理員的您，可以使用這些方法執行及監視 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 物件的處理：</span><span class="sxs-lookup"><span data-stu-id="de41d-104">As an Analysis Services system administrator, you can execute and monitor the processing of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects using these approaches:</span></span>  
  
-   <span data-ttu-id="de41d-105">執行影響分析，以了解物件相依性和作業範圍</span><span class="sxs-lookup"><span data-stu-id="de41d-105">Run Impact Analysis to understand object dependencies and scope of operations</span></span>  
  
-   <span data-ttu-id="de41d-106">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de41d-106">Process individual objects in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span></span>  
  
-   <span data-ttu-id="de41d-107">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de41d-107">Process individual or multiple objects in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]</span></span>  
  
-   <span data-ttu-id="de41d-108">執行影響分析，以檢閱將會因為目前動作而取消處理之相關物件的清單。</span><span class="sxs-lookup"><span data-stu-id="de41d-108">Run Impact Analysis to review a list of related objects that will be unprocessed as result of the current action.</span></span>  
  
-   <span data-ttu-id="de41d-109">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的 [ [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] XMLA 查詢] 視窗中，產生及執行指令碼，以處理個別或多個物件</span><span class="sxs-lookup"><span data-stu-id="de41d-109">Generate and run a script in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] XMLA Query window in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to process individual or multiple objects</span></span>  
  
-   <span data-ttu-id="de41d-110">使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] PowerShell 指令程式</span><span class="sxs-lookup"><span data-stu-id="de41d-110">Use [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] PowerShell cmdlets</span></span>  
  
-   <span data-ttu-id="de41d-111">使用 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 封裝中的控制流程和工作</span><span class="sxs-lookup"><span data-stu-id="de41d-111">Use control flows and tasks in [!INCLUDE[ssIS](../../includes/ssis-md.md)] packages</span></span>  
  
-   <span data-ttu-id="de41d-112">使用 SQL Server Profiler 來監視處理</span><span class="sxs-lookup"><span data-stu-id="de41d-112">Monitor processing with SQL Server Profiler</span></span>  
  
-   <span data-ttu-id="de41d-113">使用 AMO 進行自訂方案程式設計。</span><span class="sxs-lookup"><span data-stu-id="de41d-113">Program a custom solution using AMO.</span></span> <span data-ttu-id="de41d-114">如需相關資訊，請參閱 [Programming AMO OLAP Basic Objects](https://docs.microsoft.com/bi-reference/amo/programming-amo-olap-basic-objects)。</span><span class="sxs-lookup"><span data-stu-id="de41d-114">For more information, see [Programming AMO OLAP Basic Objects](https://docs.microsoft.com/bi-reference/amo/programming-amo-olap-basic-objects).</span></span>  
  
 <span data-ttu-id="de41d-115">處理是可高度設定的作業，由決定在物件層級上發生完整處理或累加式處理的一組處理選項所控制。</span><span class="sxs-lookup"><span data-stu-id="de41d-115">Processing is a highly configurable operation, controlled by a set of processing options that determine whether full or incremental processing occurs at the object level.</span></span> <span data-ttu-id="de41d-116">如需處理選項和物件的詳細資訊，請參閱[處理選項和設定 &#40;Analysis Services&#41;](processing-options-and-settings-analysis-services.md) 和[處理 Analysis Services 物件](processing-analysis-services-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="de41d-116">For more information about processing options and objects, see [Processing Options and Settings &#40;Analysis Services&#41;](processing-options-and-settings-analysis-services.md) and [Processing Analysis Services Objects](processing-analysis-services-objects.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="de41d-117">此主題描述用於處理多維度模型的工具和方法。</span><span class="sxs-lookup"><span data-stu-id="de41d-117">This topic describes the tools and approaches for processing multidimensional models.</span></span> <span data-ttu-id="de41d-118">如需有關處理表格式模型的詳細資訊，請參閱[處理資料庫、資料表或資料分割](../tabular-models/process-database-table-or-partition-analysis-services.md)和[處理資料 &#40;SSAS 表格式&#41;](../process-data-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="de41d-118">For more information about processing tabular models, see [Process Database, Table, or Partition](../tabular-models/process-database-table-or-partition-analysis-services.md) and [Process Data &#40;SSAS Tabular&#41;](../process-data-ssas-tabular.md).</span></span>  
  
### <a name="processing-objects-in-sql-server-management-studio"></a><span data-ttu-id="de41d-119">在 SQL Server Management Studio 中處理物件</span><span class="sxs-lookup"><span data-stu-id="de41d-119">Processing objects in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="de41d-120">啟動 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 並連接到 Analysis Services。</span><span class="sxs-lookup"><span data-stu-id="de41d-120">Start [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and connect to Analysis Services.</span></span>  
  
2.  <span data-ttu-id="de41d-121">以滑鼠右鍵按一下您要處理的 Analysis Services 物件，然後按一下 [處理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="de41d-121">Right-click the Analysis Services object you want to process and then click **Process**.</span></span> <span data-ttu-id="de41d-122">您可以在這些任何層級處理資料：</span><span class="sxs-lookup"><span data-stu-id="de41d-122">You can process data at any of these levels:</span></span>  
  
    -   <span data-ttu-id="de41d-123">資料庫</span><span class="sxs-lookup"><span data-stu-id="de41d-123">Databases</span></span>  
  
    -   <span data-ttu-id="de41d-124">Cube</span><span class="sxs-lookup"><span data-stu-id="de41d-124">Cubes</span></span>  
  
    -   <span data-ttu-id="de41d-125">量值群組或量值群組中的個別分割區</span><span class="sxs-lookup"><span data-stu-id="de41d-125">Measure Groups or individual partitions in the measure group</span></span>  
  
    -   <span data-ttu-id="de41d-126">維度</span><span class="sxs-lookup"><span data-stu-id="de41d-126">Dimensions</span></span>  
  
    -   <span data-ttu-id="de41d-127">採礦模型</span><span class="sxs-lookup"><span data-stu-id="de41d-127">Mining Models</span></span>  
  
    -   <span data-ttu-id="de41d-128">採礦結構</span><span class="sxs-lookup"><span data-stu-id="de41d-128">Mining Structures</span></span>  
  
     <span data-ttu-id="de41d-129">Analysis Services 物件是階層式。</span><span class="sxs-lookup"><span data-stu-id="de41d-129">Analysis Services objects are hierarchical.</span></span> <span data-ttu-id="de41d-130">如果您選擇資料庫，資料庫中包含的所有物件都可以進行處理。</span><span class="sxs-lookup"><span data-stu-id="de41d-130">If you choose database, processing can occur for all of the objects contained in the database.</span></span> <span data-ttu-id="de41d-131">實際上是否進行處理會依您選取的處理選項和物件的狀態而有所不同。</span><span class="sxs-lookup"><span data-stu-id="de41d-131">Whether processing actually occurs will vary depending on the process option you select and the state of the object.</span></span> <span data-ttu-id="de41d-132">明確地說，如果物件未經過處理，處理其父系將會導致該物件進行處理。</span><span class="sxs-lookup"><span data-stu-id="de41d-132">Specifically, if an object is unprocessed, processing its parent will result in that object getting processed.</span></span> <span data-ttu-id="de41d-133">如需有關物件相依性的詳細資訊，請參閱＜ [Processing Analysis Services Objects](processing-analysis-services-objects.md)＞。</span><span class="sxs-lookup"><span data-stu-id="de41d-133">For more information about object dependencies, see [Processing Analysis Services Objects](processing-analysis-services-objects.md).</span></span>  
  
3.  <span data-ttu-id="de41d-134">在 **[處理]** 對話方塊的 **[處理選項]** 中，使用提供的預設值或從清單選取不同的選項。</span><span class="sxs-lookup"><span data-stu-id="de41d-134">In the **Process** dialog box, in **Process Options**, use the default value provided or select a different option from the list.</span></span> <span data-ttu-id="de41d-135">如需每個選項的詳細資訊，請參閱[處理選項和設定 &#40;Analysis Services&#41;](processing-options-and-settings-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="de41d-135">For more information about each option, see [Processing Options and Settings &#40;Analysis Services&#41;](processing-options-and-settings-analysis-services.md).</span></span>  
  
4.  <span data-ttu-id="de41d-136">如果 [處理] 對話方塊中所列出的物件已經處理，請按一下 **[影響分析]** 來識別及選擇性地處理受影響的相依物件。</span><span class="sxs-lookup"><span data-stu-id="de41d-136">Click **Impact Analysis** to identify and optionally process dependent objects that are affected if the objects listed in the Process dialog box are processed.</span></span>  
  
5.  <span data-ttu-id="de41d-137">或者，按一下 **[變更設定]** 來修改處理順序、相對於特定類型錯誤的處理行為，以及其他設定。</span><span class="sxs-lookup"><span data-stu-id="de41d-137">Optionally, click **Change Settings** to modify the processing order, processing behavior relative to specific types of errors, and other settings.</span></span>  
  
6.  <span data-ttu-id="de41d-138">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="de41d-138">Click **OK**.</span></span>  
  
     <span data-ttu-id="de41d-139">[處理進度] 對話方塊會提供每個命令的進行中狀態。</span><span class="sxs-lookup"><span data-stu-id="de41d-139">The Process Progress dialog box provides ongoing status for each command.</span></span> <span data-ttu-id="de41d-140">如果狀態訊息遭到截斷，您可以按一下 **[檢視詳細資料]** 來讀取完整訊息。</span><span class="sxs-lookup"><span data-stu-id="de41d-140">If a status message is truncated, you can click **View Details** to read the entire message.</span></span>  
  
### <a name="processing-objects-in-sql-server-data-tools"></a><span data-ttu-id="de41d-141">在 SQL Server 資料工具中處理物件</span><span class="sxs-lookup"><span data-stu-id="de41d-141">Processing Objects in SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="de41d-142">啟動 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 並開啟已部署的專案。</span><span class="sxs-lookup"><span data-stu-id="de41d-142">Start [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and open a project that has been deployed.</span></span>  
  
2.  <span data-ttu-id="de41d-143">在 [方案總管] 中，已部署的專案之下，展開 **[維度]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="de41d-143">In Solution Explorer, under the deployed project, expand the **Dimensions** folder.</span></span>  
  
3.  <span data-ttu-id="de41d-144">以滑鼠右鍵按一下維度，然後按一下 [處理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="de41d-144">Right-click a dimension, and then click **Process**.</span></span> <span data-ttu-id="de41d-145">您可以用滑鼠右鍵按一下多個維度，一次處理多個物件。</span><span class="sxs-lookup"><span data-stu-id="de41d-145">You can right-click multiple dimensions to process multiple objects at once.</span></span> <span data-ttu-id="de41d-146">如需詳細資訊，請參閱 [批次處理 &#40;Analysis Services&#41;](batch-processing-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="de41d-146">For more information, see [Batch Processing &#40;Analysis Services&#41;](batch-processing-analysis-services.md).</span></span>  
  
4.  <span data-ttu-id="de41d-147">在 **[處理維度]** 對話方塊中，於 **[物件清單]** 下的 **[處理選項]** 資料行中，確認這個資料行的選項是 **[完整處理]**。</span><span class="sxs-lookup"><span data-stu-id="de41d-147">In the **Process Dimension** dialog box, in the **Process Options** column under **Object list**, verify that the option for this column is **Process Full**.</span></span> <span data-ttu-id="de41d-148">如果不是，請在 [處理選項]\*\*\*\* 之下，按一下選項，然後從下拉式清單中選取 [完整處理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="de41d-148">If it is not, under **Process Options**, click the option, and select **Process Full** from the drop-down list.</span></span>  
  
5.  <span data-ttu-id="de41d-149">按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="de41d-149">Click **Run**.</span></span>  
  
6.  <span data-ttu-id="de41d-150">當處理完成時，請按一下 **[關閉]**。</span><span class="sxs-lookup"><span data-stu-id="de41d-150">When processing is finished, click **Close**.</span></span>  
  
##  <a name="run-impact-analysis-to-identify-object-dependencies-and-scope-of-operations"></a><a name="bkmk_impactanalysis"></a><span data-ttu-id="de41d-151">執行影響分析以識別物件相依性和作業範圍</span><span class="sxs-lookup"><span data-stu-id="de41d-151">Run Impact Analysis to identify object dependencies and scope of operations</span></span>  
  
1.  <span data-ttu-id="de41d-152">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 或 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 中處理 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]物件之前，您可以按一下其中一個 **[處理物件]** 對話方塊中的 **[影響分析]** ，來分析對相關物件的影響。</span><span class="sxs-lookup"><span data-stu-id="de41d-152">Before you process an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object in either [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] or [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], you can analyze the effect on related objects by clicking **Impact Analysis** in one of the **Process Objects** dialog boxes.</span></span>  
  
2.  <span data-ttu-id="de41d-153">以滑鼠右鍵按一下維度、Cube、量值群組或分割區，開啟 [處理物件]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="de41d-153">Right-click a dimension, cube, measure group, or partition to open a **Process Objects** dialog box.</span></span>  
  
3.  <span data-ttu-id="de41d-154">按一下 **[影響分析]**。</span><span class="sxs-lookup"><span data-stu-id="de41d-154">Click **Impact Analysis**.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="de41d-155">就會掃描模型，並報告與已選取進行處理物件相關之物件的重新處理需求。</span><span class="sxs-lookup"><span data-stu-id="de41d-155">scans the model and reports on reprocessing requirements for objects that are related to the one you selected for processing.</span></span>  
  
### <a name="processing-objects-using-xmla"></a><span data-ttu-id="de41d-156">使用 XMLA 處理物件</span><span class="sxs-lookup"><span data-stu-id="de41d-156">Processing objects using XMLA</span></span>  
  
1.  <span data-ttu-id="de41d-157">啟動 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 並連接到 Analysis Services。</span><span class="sxs-lookup"><span data-stu-id="de41d-157">Start [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and connect to Analysis Services.</span></span>  
  
2.  <span data-ttu-id="de41d-158">以滑鼠右鍵按一下要處理的物件，然後按一下 [處理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="de41d-158">Right-click the object to be processed and then click **Process**.</span></span>  
  
3.  <span data-ttu-id="de41d-159">在 **[處理]** 對話方塊中，選取要使用的處理選項。</span><span class="sxs-lookup"><span data-stu-id="de41d-159">In the **Process** dialog box, select the process option you want to use.</span></span> <span data-ttu-id="de41d-160">修改其他任何設定。</span><span class="sxs-lookup"><span data-stu-id="de41d-160">Modify any other settings.</span></span> <span data-ttu-id="de41d-161">執行 [影響分析] 來識別您可能需要進行的所有變更。</span><span class="sxs-lookup"><span data-stu-id="de41d-161">Run Impact Analysis to identify any changes you might need to make.</span></span>  
  
4.  <span data-ttu-id="de41d-162">按一下 **[處理物件]** 畫面上的 **[指令碼]** 。</span><span class="sxs-lookup"><span data-stu-id="de41d-162">Click **Script** on the **Process Objects** screen.</span></span>  
  
     <span data-ttu-id="de41d-163">如此即可產生 XMLA 指令碼，並開啟 [ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] XMLA 查詢] 視窗。</span><span class="sxs-lookup"><span data-stu-id="de41d-163">This generates an XMLA script and opens an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] XMLA Query window.</span></span>  
  
5.  <span data-ttu-id="de41d-164">關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="de41d-164">Close the dialog box.</span></span> <span data-ttu-id="de41d-165">該指令碼包含在對話方塊中指定的處理命令和選項。</span><span class="sxs-lookup"><span data-stu-id="de41d-165">The script contains the processing command and options that were specified in the dialog box.</span></span>  
  
6.  <span data-ttu-id="de41d-166">(選擇性) 如果您要在同一個批次中處理其他物件，可以繼續加入至指令碼。</span><span class="sxs-lookup"><span data-stu-id="de41d-166">Optionally, you can continue adding to the script if you want to process additional objects in the same batch.</span></span> <span data-ttu-id="de41d-167">若要繼續，請重複先前步驟附加產生的指令碼，以便在單一指令碼中包含所有處理作業。</span><span class="sxs-lookup"><span data-stu-id="de41d-167">To continue, repeat the previous steps, appending the generated script so that you have a single script for all processing operations.</span></span> <span data-ttu-id="de41d-168">若要檢視範例，請參閱＜ [Schedule SSAS Administrative Tasks with SQL Server Agent](../instances/schedule-ssas-administrative-tasks-with-sql-server-agent.md)＞。</span><span class="sxs-lookup"><span data-stu-id="de41d-168">To view an example, see [Schedule SSAS Administrative Tasks with SQL Server Agent](../instances/schedule-ssas-administrative-tasks-with-sql-server-agent.md).</span></span>  
  
7.  <span data-ttu-id="de41d-169">從功能表列中按一下 **[查詢]**，然後按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="de41d-169">From the menu bar, click **Query**, and then click **Execute**.</span></span>  
  
### <a name="processing-objects-using-powershell"></a><span data-ttu-id="de41d-170">使用 PowerShell 處理物件</span><span class="sxs-lookup"><span data-stu-id="de41d-170">Processing objects using PowerShell</span></span>  
  
1.  <span data-ttu-id="de41d-171">從這個版本的 SQL Server 開始，您可以使用 Analysis Services PowerShell 指令程式處理物件。</span><span class="sxs-lookup"><span data-stu-id="de41d-171">Starting in this release of SQL Server, you can use Analysis Services PowerShell cmdlets to process objects.</span></span> <span data-ttu-id="de41d-172">下列指令程式可以以互動方式或指令碼執行：</span><span class="sxs-lookup"><span data-stu-id="de41d-172">The following cmdlets can be run interactively or in script:</span></span>  
  
    -   [<span data-ttu-id="de41d-173">Invoke-ProcessCube 指令程式</span><span class="sxs-lookup"><span data-stu-id="de41d-173">Invoke-ProcessCube cmdlet</span></span>](/powershell/module/sqlserver/invoke-processcube)  
  
    -   [<span data-ttu-id="de41d-174">Invoke-ProcessDimension 指令程式</span><span class="sxs-lookup"><span data-stu-id="de41d-174">Invoke-ProcessDimension cmdlet</span></span>](/powershell/module/sqlserver/invoke-processdimension)  
  
    -   [<span data-ttu-id="de41d-175">Invoke-ProcessPartition 指令程式</span><span class="sxs-lookup"><span data-stu-id="de41d-175">Invoke-ProcessPartition cmdlet</span></span>](/powershell/module/sqlserver/invoke-processpartition)  
  
    -   <span data-ttu-id="de41d-176">[Invoke-ASCmd Cmdlet](/powershell/module/sqlserver/invoke-ascmd)，可用來執行包含處理命令的 XMLA、MDX 或 DMX 指令碼。</span><span class="sxs-lookup"><span data-stu-id="de41d-176">[Invoke-ASCmd cmdlet](/powershell/module/sqlserver/invoke-ascmd), which can be used to execute XMLA, MDX, or DMX script that includes processing commands.</span></span>  
  
### <a name="monitoring-object-processing-using-sql-server-profiler"></a><span data-ttu-id="de41d-177">使用 SQL Server Profiler 監視物件處理</span><span class="sxs-lookup"><span data-stu-id="de41d-177">Monitoring object processing using SQL Server Profiler</span></span>  
  
1.  <span data-ttu-id="de41d-178">在 SQL Server Profiler 中連接到 Analysis Services 執行個體。</span><span class="sxs-lookup"><span data-stu-id="de41d-178">Connect to an Analysis Services instance in SQL Server Profiler.</span></span>  
  
2.  <span data-ttu-id="de41d-179">在 [事件選取範圍] 中，按一下 **[顯示所有事件]** 將所有事件加入至清單。</span><span class="sxs-lookup"><span data-stu-id="de41d-179">In Events Selection, click **Show all events** to add all events to the list.</span></span>  
  
3.  <span data-ttu-id="de41d-180">選擇下列事件：</span><span class="sxs-lookup"><span data-stu-id="de41d-180">Choose the following events:</span></span>  
  
    -   <span data-ttu-id="de41d-181">**[命令開始]** 和 **[命令結束]** 以顯示何時處理啟動和停止</span><span class="sxs-lookup"><span data-stu-id="de41d-181">**Command Begin** and **Command End** to show when processing starts and stops</span></span>  
  
    -   <span data-ttu-id="de41d-182">**[錯誤]** 以擷取任何錯誤</span><span class="sxs-lookup"><span data-stu-id="de41d-182">**Error** to capture any errors</span></span>  
  
    -   <span data-ttu-id="de41d-183">**[進度報表開始]**、 **[目前的進度報表]** 和 **[進度報表結束]** 以報告處理狀態並顯示用來擷取資料的 SQL 查詢</span><span class="sxs-lookup"><span data-stu-id="de41d-183">**Progress Report Begin**, **Progress Report Current**, and **Progress Report End** to report on process status and show the SQL queries used to retrieve the data</span></span>  
  
    -   <span data-ttu-id="de41d-184">**[執行 MDX 指令碼開始]** 和 **[執行 MDX 指令碼結束]** 以顯示 Cube 計算</span><span class="sxs-lookup"><span data-stu-id="de41d-184">**Execute MDX Script Begin** and **Execute MDX Script End** to show the cube calculations</span></span>  
  
    -   <span data-ttu-id="de41d-185">(選擇性) 如果您要診斷處理相關的效能問題，可加入鎖定事件</span><span class="sxs-lookup"><span data-stu-id="de41d-185">Optionally, add lock events if you are diagnosing performance problems related to processing</span></span>  
  
### <a name="process-analysis-services-objects-using-integration-services"></a><span data-ttu-id="de41d-186">使用 Integration Services 來處理 Analysis Services 物件</span><span class="sxs-lookup"><span data-stu-id="de41d-186">Process Analysis Services objects using Integration Services</span></span>  
  
1.  <span data-ttu-id="de41d-187">在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]中建立封裝，當您定期更新來源關聯式資料庫時，它會使用 Analysis Services 處理工作自動以新資訊擴展物件。</span><span class="sxs-lookup"><span data-stu-id="de41d-187">In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], create a package that uses the Analysis Services Processing Task to automatically populate objects with new data when you make regular updates to your source relational database.</span></span>  
  
2.  <span data-ttu-id="de41d-188">在 SSIS 工具箱\*\*\*\*，按兩下 [Analysis Services 處理]\*\*\*\* 將其加入到封裝。</span><span class="sxs-lookup"><span data-stu-id="de41d-188">In the **SSIS Toolbox**, double-click **Analysis Services Processing** to add it to the package.</span></span>  
  
3.  <span data-ttu-id="de41d-189">編輯工作，以指定資料庫連接、要處理的物件和處理選項。</span><span class="sxs-lookup"><span data-stu-id="de41d-189">Edit the task to specify a connection to the database, which objects to process, and the process option.</span></span> <span data-ttu-id="de41d-190">如需有關如何實作這項工作的詳細資訊，請參閱＜ [Analysis Services Processing Task](../../integration-services/control-flow/analysis-services-processing-task.md)＞。</span><span class="sxs-lookup"><span data-stu-id="de41d-190">For more information about how to implement this task, see [Analysis Services Processing Task](../../integration-services/control-flow/analysis-services-processing-task.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de41d-191">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de41d-191">See Also</span></span>  
 [<span data-ttu-id="de41d-192">多維度模型物件處理</span><span class="sxs-lookup"><span data-stu-id="de41d-192">Multidimensional Model Object Processing</span></span>](processing-a-multidimensional-model-analysis-services.md)  
  
  
