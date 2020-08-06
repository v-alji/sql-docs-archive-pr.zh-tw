---
title: Analysis Services DMX 查詢設計工具使用者介面 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10012"
- sql12.rtp.rptdesigner.dataview.asquerydesigner.f1
helpviewer_keywords:
- Analysis Services [DMX]
- DMX [Analysis Services], user interface
- query designers [DMX]
ms.assetid: 5fd726a4-aed7-4e6c-9404-ccb2db66cf26
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b641423ad9563f252ba89f51fcd8cafb0ed7bbe8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592472"
---
# <a name="analysis-services-dmx-query-designer-user-interface"></a><span data-ttu-id="9e31b-102">Analysis Services DMX 查詢設計工具使用者介面</span><span class="sxs-lookup"><span data-stu-id="9e31b-102">Analysis Services DMX Query Designer User Interface</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="9e31b-103">提供了圖形化查詢設計工具，可用來建立 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 資料來源的資料採礦運算式 (DMX) 查詢和多維度運算式 (MDX) 查詢。</span><span class="sxs-lookup"><span data-stu-id="9e31b-103">provides graphical query designers for building Data Mining Expressions (DMX) queries and Multidimensional Expression (MDX) queries for an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source.</span></span> <span data-ttu-id="9e31b-104">此主題即描述 DMX 查詢設計工具。</span><span class="sxs-lookup"><span data-stu-id="9e31b-104">This topic describes the DMX query designer.</span></span> <span data-ttu-id="9e31b-105">如需 MDX 查詢設計工具的詳細資訊，請參閱 [Analysis Services MDX 查詢設計工具使用者介面](analysis-services-mdx-query-designer-user-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="9e31b-105">For more information about the MDX query designer, see [Analysis Services MDX Query Designer User Interface](analysis-services-mdx-query-designer-user-interface.md).</span></span>  
  
 <span data-ttu-id="9e31b-106">DMX 圖形化查詢設計工具有三種模式：「設計」、「查詢」和「結果」。</span><span class="sxs-lookup"><span data-stu-id="9e31b-106">The DMX graphical query designer has three modes: Design, Query, and Result.</span></span> <span data-ttu-id="9e31b-107">若要切換模式，請以滑鼠右鍵按一下 [查詢設計工具] 窗格並選取模式。</span><span class="sxs-lookup"><span data-stu-id="9e31b-107">To switch modes, right-click on the Query Design pane, and select the mode.</span></span> <span data-ttu-id="9e31b-108">每一種模式都會提供 [中繼資料] 窗格，您可以在這個窗格中，從選取的 Cube 中拖曳成員，以建立 DMX 查詢，在處理報表時為資料集擷取資料。</span><span class="sxs-lookup"><span data-stu-id="9e31b-108">Each mode provides a Metadata pane from which you can drag members from the selected cubes to build a DMX query that retrieves data for a dataset when the report is processed.</span></span>  
  
## <a name="graphical-dmx-query-designer-toolbar"></a><span data-ttu-id="9e31b-109">圖形化 DMX 查詢設計工具工具列</span><span class="sxs-lookup"><span data-stu-id="9e31b-109">Graphical DMX Query Designer Toolbar</span></span>  
 <span data-ttu-id="9e31b-110">查詢設計工具工具列會提供按鈕，協助您使用圖形化介面設計 DMX 查詢。</span><span class="sxs-lookup"><span data-stu-id="9e31b-110">The query designer toolbar provides buttons to help you design DMX queries using the graphical interface.</span></span> <span data-ttu-id="9e31b-111">下表描述這些按鈕及其功能。</span><span class="sxs-lookup"><span data-stu-id="9e31b-111">The following table describes the buttons and their functions.</span></span>  
  
|<span data-ttu-id="9e31b-112">按鈕</span><span class="sxs-lookup"><span data-stu-id="9e31b-112">Button</span></span>|<span data-ttu-id="9e31b-113">描述</span><span class="sxs-lookup"><span data-stu-id="9e31b-113">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="9e31b-114">**當成文字編輯**</span><span class="sxs-lookup"><span data-stu-id="9e31b-114">**Edit As Text**</span></span>|<span data-ttu-id="9e31b-115">這種資料來源類型已停用此選項。</span><span class="sxs-lookup"><span data-stu-id="9e31b-115">Disabled for this data source type.</span></span>|  
|<span data-ttu-id="9e31b-116">**匯入**</span><span class="sxs-lookup"><span data-stu-id="9e31b-116">**Import**</span></span>|<span data-ttu-id="9e31b-117">從檔案系統上的報表定義 (.rdl) 檔案匯入現有的查詢。</span><span class="sxs-lookup"><span data-stu-id="9e31b-117">Import an existing query from a report definition (.rdl) file on the file system.</span></span> <span data-ttu-id="9e31b-118">如需詳細資訊，請參閱 [報表內嵌資料集和共用資料集 &#40;報表產生器及 SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="9e31b-118">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>|  
|<span data-ttu-id="9e31b-119">![變更為 MDX 查詢檢視](../media/rsqdicon-commandtypemdx.gif "變更為 MDX 查詢檢視")</span><span class="sxs-lookup"><span data-stu-id="9e31b-119">![Change to MDX query view](../media/rsqdicon-commandtypemdx.gif "Change to MDX query view")</span></span>|<span data-ttu-id="9e31b-120">切換到 MDX 查詢設計工具模式。</span><span class="sxs-lookup"><span data-stu-id="9e31b-120">Switch to the MDX query designer mode.</span></span>|  
|<span data-ttu-id="9e31b-121">![變更為 DMX 查詢語言檢視](../media/rsqdicon-commandtypedmx.gif "變更為 DMX 查詢語言檢視")</span><span class="sxs-lookup"><span data-stu-id="9e31b-121">![Change to DMX query language view](../media/rsqdicon-commandtypedmx.gif "Change to DMX query language view")</span></span>|<span data-ttu-id="9e31b-122">切換到 DMX 查詢設計工具模式。</span><span class="sxs-lookup"><span data-stu-id="9e31b-122">Switch to the DMX query designer mode.</span></span>|  
|<span data-ttu-id="9e31b-123">![重新整理結果資料](../media/rsqdicon-refresh.gif "重新整理結果資料")</span><span class="sxs-lookup"><span data-stu-id="9e31b-123">![Refresh result data](../media/rsqdicon-refresh.gif "Refresh result data")</span></span>|<span data-ttu-id="9e31b-124">重新整理資料來源中的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="9e31b-124">Refresh metadata from the data source.</span></span>|  
|<span data-ttu-id="9e31b-125">![刪除](../media/rsqdicon-delete.gif "刪除")</span><span class="sxs-lookup"><span data-stu-id="9e31b-125">![Delete](../media/rsqdicon-delete.gif "Delete")</span></span>|<span data-ttu-id="9e31b-126">從查詢中刪除 [資料] 窗格中選取的資料行。</span><span class="sxs-lookup"><span data-stu-id="9e31b-126">Delete the selected column in the Data pane from the query.</span></span>|  
|<span data-ttu-id="9e31b-127">![[查詢參數] 對話方塊圖示](../media/iconqueryparameter.gif "查詢參數對話方塊圖示")</span><span class="sxs-lookup"><span data-stu-id="9e31b-127">![Icon for the Query Parameters dialog box](../media/iconqueryparameter.gif "Icon for the Query Parameters dialog box")</span></span>|<span data-ttu-id="9e31b-128">顯示 **[查詢參數]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9e31b-128">Display the **Query Parameters** dialog box.</span></span> <span data-ttu-id="9e31b-129">當您指派預設值給變數時，就會在您切換到 [報表設計師] 中的 [配置] 檢視時建立對應的報表參數。</span><span class="sxs-lookup"><span data-stu-id="9e31b-129">When you assign a default value to a variable, a corresponding report parameter is created when you switch to the Layout view in Report Designer.</span></span>|  
|<span data-ttu-id="9e31b-130">![執行查詢](../media/rsqdicon-run.gif "執行查詢")</span><span class="sxs-lookup"><span data-stu-id="9e31b-130">![Run the query](../media/rsqdicon-run.gif "Run the query")</span></span>|<span data-ttu-id="9e31b-131">準備查詢。</span><span class="sxs-lookup"><span data-stu-id="9e31b-131">Prepare the query.</span></span>|  
|<span data-ttu-id="9e31b-132">![切換到設計模式](../media/rsqdicon-designmode.gif "切換到設計模式")</span><span class="sxs-lookup"><span data-stu-id="9e31b-132">![Switch to Design mode](../media/rsqdicon-designmode.gif "Switch to Design mode")</span></span>|<span data-ttu-id="9e31b-133">在「設計」模式與「查詢」模式之間切換。</span><span class="sxs-lookup"><span data-stu-id="9e31b-133">Toggle between Design mode and Query mode.</span></span> <span data-ttu-id="9e31b-134">若要變更為結果檢視，請以滑鼠右鍵按一下 [設計] 窗格並選擇 [結果]  。</span><span class="sxs-lookup"><span data-stu-id="9e31b-134">To change to result view, right-click on the Design pane and choose **Result**.</span></span>|  
  
## <a name="graphical-dmx-query-designer-in-design-mode"></a><span data-ttu-id="9e31b-135">設計模式中的圖形化 DMX 查詢設計工具</span><span class="sxs-lookup"><span data-stu-id="9e31b-135">Graphical DMX Query Designer in Design Mode</span></span>  
 <span data-ttu-id="9e31b-136">當您編輯的資料集所使用的 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 資料來源沒有有效的 Cube，但是具有有效的採礦模型時，圖形化查詢設計工具會在 [設計] 模式下開啟。</span><span class="sxs-lookup"><span data-stu-id="9e31b-136">When you edit a dataset that uses an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source that has no valid cubes but that does have valid mining models, the graphical query designer opens in Design mode.</span></span> <span data-ttu-id="9e31b-137">下圖會標示出設計模式的窗格。</span><span class="sxs-lookup"><span data-stu-id="9e31b-137">The following figure labels the panes for Design mode.</span></span>  
  
 <span data-ttu-id="9e31b-138">![Analysis Services MDX 查詢設計工具，設計檢視](../media/rsqd-dsawas-dmx-designmode.gif "Analysis Services DMX 查詢設計工具，設計檢視")</span><span class="sxs-lookup"><span data-stu-id="9e31b-138">![Analysis Services DMX query designer, design view](../media/rsqd-dsawas-dmx-designmode.gif "Analysis Services DMX query designer, design view")</span></span>  
  
 <span data-ttu-id="9e31b-139">下表會描述各個窗格的功能。</span><span class="sxs-lookup"><span data-stu-id="9e31b-139">The following table describes the function of each pane.</span></span>  
  
|<span data-ttu-id="9e31b-140">窗格</span><span class="sxs-lookup"><span data-stu-id="9e31b-140">Pane</span></span>|<span data-ttu-id="9e31b-141">函式</span><span class="sxs-lookup"><span data-stu-id="9e31b-141">Function</span></span>|  
|----------|--------------|  
|<span data-ttu-id="9e31b-142">[查詢設計] 窗格</span><span class="sxs-lookup"><span data-stu-id="9e31b-142">Query Design pane</span></span>|<span data-ttu-id="9e31b-143">使用 [採礦模型]  及 [選取輸入資料表]  對話方塊建立 DMX 查詢。</span><span class="sxs-lookup"><span data-stu-id="9e31b-143">Use the **Mining Model** and **Select Input Table** dialog boxes to build the DMX query.</span></span>|  
|<span data-ttu-id="9e31b-144">[方格] 窗格</span><span class="sxs-lookup"><span data-stu-id="9e31b-144">Grid pane</span></span>|<span data-ttu-id="9e31b-145">針對方格中的每一個資料列，使用 [來源]  下拉式清單選取函式或運算式，並選擇要在 DMX 查詢中使用的欄位、群組和準則或引數。</span><span class="sxs-lookup"><span data-stu-id="9e31b-145">For each row in the grid, use the **Source** drop-down list to select a function or expression, and choose fields, groups, and criteria or arguments to use in your DMX query.</span></span> <span data-ttu-id="9e31b-146">若要查看依據選取項目所產生的 DMX 查詢文字，請按一下工具列上的 [設計模式]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="9e31b-146">To see the DMX query text generated by your selections, click the **Design Mode** button on the toolbar.</span></span>|  
  
 <span data-ttu-id="9e31b-147">若要執行 DMX 查詢並將結果顯示在 [結果] 窗格中，請以滑鼠右鍵按一下 [查詢設計] 窗格並選取 [結果]  。</span><span class="sxs-lookup"><span data-stu-id="9e31b-147">To run the DMX query and show results in the Result pane, right-click on the Query Design pane and select **Result**.</span></span>  
  
## <a name="graphical-dmx-query-designer-in-query-mode"></a><span data-ttu-id="9e31b-148">查詢模式中的圖形化 DMX 查詢設計工具</span><span class="sxs-lookup"><span data-stu-id="9e31b-148">Graphical DMX Query Designer in Query Mode</span></span>  
 <span data-ttu-id="9e31b-149">若要將圖形化查詢設計工具變更為「查詢」模式，請按一下工具列上的 [設計模式]  按鈕，或是以滑鼠右鍵按一下查詢設計介面並從捷徑功能表中選擇 [查詢]  。</span><span class="sxs-lookup"><span data-stu-id="9e31b-149">To change the graphical query designer to Query mode, click the **Design Mode** button on the toolbar or right-click on the query design surface, and choose **Query** from the shortcut menu.</span></span> <span data-ttu-id="9e31b-150">使用這種模式可直接在 [查詢] 窗格中輸入 DMX 文字。</span><span class="sxs-lookup"><span data-stu-id="9e31b-150">Use this mode to enter DMX text directly into the Query pane.</span></span>  
  
 <span data-ttu-id="9e31b-151">下圖會標示出「查詢」模式中的窗格。</span><span class="sxs-lookup"><span data-stu-id="9e31b-151">The following figure labels the panes for Query mode.</span></span>  
  
 <span data-ttu-id="9e31b-152">![Analysis Services DMX 查詢設計工具，查詢檢視](../media/rsqd-dsawas-dmx-querymode.gif "Analysis Services DMX 查詢設計工具，查詢檢視")</span><span class="sxs-lookup"><span data-stu-id="9e31b-152">![Analysis Services DMX query designer, query view](../media/rsqd-dsawas-dmx-querymode.gif "Analysis Services DMX query designer, query view")</span></span>  
  
 <span data-ttu-id="9e31b-153">下表會描述各個窗格的功能。</span><span class="sxs-lookup"><span data-stu-id="9e31b-153">The following table describes the function of each pane.</span></span>  
  
|<span data-ttu-id="9e31b-154">窗格</span><span class="sxs-lookup"><span data-stu-id="9e31b-154">Pane</span></span>|<span data-ttu-id="9e31b-155">函式</span><span class="sxs-lookup"><span data-stu-id="9e31b-155">Function</span></span>|  
|----------|--------------|  
|<span data-ttu-id="9e31b-156">[查詢設計] 窗格</span><span class="sxs-lookup"><span data-stu-id="9e31b-156">Query Design pane</span></span>|<span data-ttu-id="9e31b-157">使用 [採礦模型]  及 [選取輸入資料表]  對話方塊建立 DMX 查詢。</span><span class="sxs-lookup"><span data-stu-id="9e31b-157">Use the **Mining Model** and **Select Input Table** dialog boxes to build the DMX query.</span></span>|  
|<span data-ttu-id="9e31b-158">[查詢] 窗格</span><span class="sxs-lookup"><span data-stu-id="9e31b-158">Query pane</span></span>|<span data-ttu-id="9e31b-159">直接在窗格中檢視或編輯 DMX 查詢文字。</span><span class="sxs-lookup"><span data-stu-id="9e31b-159">View or edit DMX query text directly in the pane.</span></span> <span data-ttu-id="9e31b-160">如果變回 [設計]  模式，則無法保存 DMX 查詢文字的變更。</span><span class="sxs-lookup"><span data-stu-id="9e31b-160">Changes to the DMX query text do not persist if you change back to **Design** mode.</span></span>|  
  
 <span data-ttu-id="9e31b-161">若要執行 DMX 查詢並將結果顯示在 [結果] 窗格中，請以滑鼠右鍵按一下 [查詢設計] 窗格並選取 [結果]  。</span><span class="sxs-lookup"><span data-stu-id="9e31b-161">To run the DMX query and show results in the Result pane, right-click on the Query Design pane and select **Result**.</span></span>  
  
## <a name="graphical-dmx-query-designer-in-result-mode"></a><span data-ttu-id="9e31b-162">結果模式中的圖形化 DMX 查詢設計工具</span><span class="sxs-lookup"><span data-stu-id="9e31b-162">Graphical DMX Query Designer in Result Mode</span></span>  
 <span data-ttu-id="9e31b-163">若要顯示「結果」模式，請以滑鼠右鍵按一下查詢設計介面，然後從捷徑功能表中選擇 [結果]  。</span><span class="sxs-lookup"><span data-stu-id="9e31b-163">To display the Result mode, right-click the query design surface and choose **Result** from the shortcut menu.</span></span> <span data-ttu-id="9e31b-164">當您切換到「結果」模式時，DMX 查詢便會自動執行。</span><span class="sxs-lookup"><span data-stu-id="9e31b-164">When you switch to Result mode, the DMX query runs automatically.</span></span>  
  
 <span data-ttu-id="9e31b-165">下圖會顯示「結果」模式中的查詢設計工具。</span><span class="sxs-lookup"><span data-stu-id="9e31b-165">The following figure shows the query designer in Result mode.</span></span>  
  
 <span data-ttu-id="9e31b-166">![Analysis Services DMX 查詢設計工具，結果檢視](../media/rsqd-dsawas-dmx-resultmode.gif "Analysis Services DMX 查詢設計工具，結果檢視")</span><span class="sxs-lookup"><span data-stu-id="9e31b-166">![Analysis Services DMX query designer, result view](../media/rsqd-dsawas-dmx-resultmode.gif "Analysis Services DMX query designer, result view")</span></span>  
  
 <span data-ttu-id="9e31b-167">若要切換回「設計」模式或「查詢」模式，請以滑鼠右鍵按一下 [結果] 窗格並選取 [設計]  或 [查詢]  。</span><span class="sxs-lookup"><span data-stu-id="9e31b-167">To switch back to Design mode or Query mode, right-click on the Result pane and select **Design** or **Query**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e31b-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e31b-168">See Also</span></span>  
 <span data-ttu-id="9e31b-169">[在 Analysis Services 的 MDX 查詢設計工具中定義參數 &#40;報表產生器及 SSRS&#41;](define-parameters-in-the-mdx-query-designer-for-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="9e31b-169">[Define Parameters in the MDX Query Designer for Analysis Services &#40;Report Builder and SSRS&#41;](define-parameters-in-the-mdx-query-designer-for-analysis-services.md) </span></span>  
 <span data-ttu-id="9e31b-170">[建立共用資料集或內嵌資料集 &#40;報表產生器及 SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9e31b-170">[Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="9e31b-171">[Analysis Services Connection Type for DMX &#40;SSRS&#41;](analysis-services-connection-type-for-dmx-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9e31b-171">[Analysis Services Connection Type for DMX &#40;SSRS&#41;](analysis-services-connection-type-for-dmx-ssrs.md) </span></span>  
 <span data-ttu-id="9e31b-172">[從資料採礦模型擷取資料 &#40;DMX&#41; &#40;SSRS&#41;](retrieve-data-from-a-data-mining-model-dmx-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9e31b-172">[Retrieve Data from a Data Mining Model &#40;DMX&#41; &#40;SSRS&#41;](retrieve-data-from-a-data-mining-model-dmx-ssrs.md) </span></span>  
 <span data-ttu-id="9e31b-173">[RSReportDesigner 組態檔](../report-server/rsreportdesigner-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="9e31b-173">[RSReportDesigner Configuration File](../report-server/rsreportdesigner-configuration-file.md) </span></span>  
 <span data-ttu-id="9e31b-174">[MDX 的 Analysis Services 連接類型 &#40;SSRS&#41;](analysis-services-connection-type-for-mdx-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9e31b-174">[Analysis Services Connection Type for MDX &#40;SSRS&#41;](analysis-services-connection-type-for-mdx-ssrs.md) </span></span>  
 [<span data-ttu-id="9e31b-175">Analysis Services Connection Type for DMX &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9e31b-175">Analysis Services Connection Type for DMX &#40;SSRS&#41;</span></span>](analysis-services-connection-type-for-dmx-ssrs.md)  
  
  
