---
title: Hyperion Essbase 查詢設計工具使用者介面 (報表產生器) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10013"
helpviewer_keywords:
- Hyperion Essbase query designer
- query designers, Hyperion
ms.assetid: d89a6773-dbe5-48e5-bda9-db0e67100696
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 38da75955608d95eb9fe673c7cdef5896bbe2787
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710361"
---
# <a name="hyperion-essbase-query-designer-user-interface-report-builder"></a><span data-ttu-id="e4c15-102">Hyperion Essbase 查詢設計工具使用者介面 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="e4c15-102">Hyperion Essbase Query Designer User Interface (Report Builder)</span></span>
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="e4c15-103">會提供圖形化查詢設計工具，可用以建立 [!INCLUDE[extEssbase](../includes/extessbase-md.md)] 資料來源的多維度運算式 (MDX) 查詢。</span><span class="sxs-lookup"><span data-stu-id="e4c15-103">provides a graphical query designer for building Multidimensional Expression (MDX) queries for a [!INCLUDE[extEssbase](../includes/extessbase-md.md)] data source.</span></span> <span data-ttu-id="e4c15-104">MDX 圖形化查詢設計工具有兩種模式：「設計」模式和「查詢」模式。</span><span class="sxs-lookup"><span data-stu-id="e4c15-104">The MDX graphical query designer has two modes: Design mode and Query mode.</span></span> <span data-ttu-id="e4c15-105">每一種模式都會提供 [中繼資料] 窗格，而且您可以透過這個窗格，從資料來源上定義的 Cube 中拖曳成員，以便建立可在處理報表時擷取資料的 MDX 查詢。</span><span class="sxs-lookup"><span data-stu-id="e4c15-105">Each mode provides a Metadata pane from which you can drag members from a cube defined on the data source to build an MDX query that retrieves data when the report is processed.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="e4c15-106">當使用者建立與執行查詢時，可以存取資料來源。</span><span class="sxs-lookup"><span data-stu-id="e4c15-106">Users access data sources when they create and run queries.</span></span> <span data-ttu-id="e4c15-107">您應該授與資料來源的最小權限，例如唯讀權限。</span><span class="sxs-lookup"><span data-stu-id="e4c15-107">You should grant minimal permissions on the data sources, such as read-only permissions.</span></span>

 <span data-ttu-id="e4c15-108">本節會針對圖形化查詢設計工具的各種模式，描述其中的工具列按鈕和查詢設計工具窗格。</span><span class="sxs-lookup"><span data-stu-id="e4c15-108">This section describes the toolbar buttons and query designer panes for each mode of the graphical query designer.</span></span>

## <a name="graphical-query-designer-in-design-mode"></a><span data-ttu-id="e4c15-109">設計模式中的圖形化查詢設計工具</span><span class="sxs-lookup"><span data-stu-id="e4c15-109">Graphical Query Designer in Design Mode</span></span>
 <span data-ttu-id="e4c15-110">當您為資料集編輯的 MDX 查詢使用了 [!INCLUDE[extEssbase](../includes/extessbase-md.md)] 資料來源時，圖形化查詢設計工具會在設計模式下開啟。</span><span class="sxs-lookup"><span data-stu-id="e4c15-110">When you edit an MDX query for a dataset that uses a [!INCLUDE[extEssbase](../includes/extessbase-md.md)] data source, the graphical query designer opens in Design mode.</span></span> <span data-ttu-id="e4c15-111">下圖會標示出設計模式的窗格。</span><span class="sxs-lookup"><span data-stu-id="e4c15-111">The following figure labels the panes for Design mode.</span></span>

 <span data-ttu-id="e4c15-112">![Hyperion Essbase 查詢設計工具資料來源](media/rsqd-dshyperionessbase-mdx-designmode.gif "Hyperion Essbase 查詢設計工具資料來源")</span><span class="sxs-lookup"><span data-stu-id="e4c15-112">![Query Designer for Hyperion Essbase data source](media/rsqd-dshyperionessbase-mdx-designmode.gif "Query Designer for Hyperion Essbase data source")</span></span>

 <span data-ttu-id="e4c15-113">下表列出此模式下的窗格。</span><span class="sxs-lookup"><span data-stu-id="e4c15-113">The following table lists the panes in this mode.</span></span>

|<span data-ttu-id="e4c15-114">窗格</span><span class="sxs-lookup"><span data-stu-id="e4c15-114">Pane</span></span>|<span data-ttu-id="e4c15-115">函式</span><span class="sxs-lookup"><span data-stu-id="e4c15-115">Function</span></span>|
|----------|--------------|
|<span data-ttu-id="e4c15-116">[選取 Cube] 按鈕</span><span class="sxs-lookup"><span data-stu-id="e4c15-116">Select Cube button</span></span>|<span data-ttu-id="e4c15-117">顯示目前選取的 Cube。</span><span class="sxs-lookup"><span data-stu-id="e4c15-117">Displays the currently selected cube.</span></span>|
|<span data-ttu-id="e4c15-118">[中繼資料] 窗格</span><span class="sxs-lookup"><span data-stu-id="e4c15-118">Metadata pane</span></span>|<span data-ttu-id="e4c15-119">顯示 Cube 的階層式清單。</span><span class="sxs-lookup"><span data-stu-id="e4c15-119">Displays a hierarchical list of cubes.</span></span>|
|<span data-ttu-id="e4c15-120">[導出成員] 窗格</span><span class="sxs-lookup"><span data-stu-id="e4c15-120">Calculated Members pane</span></span>|<span data-ttu-id="e4c15-121">顯示目前已定義，可在查詢中使用的導出成員。</span><span class="sxs-lookup"><span data-stu-id="e4c15-121">Displays the currently defined calculated members available for use in the query.</span></span>|
|<span data-ttu-id="e4c15-122">[篩選] 窗格</span><span class="sxs-lookup"><span data-stu-id="e4c15-122">Filter pane</span></span>|<span data-ttu-id="e4c15-123">顯示要在查詢中套用的篩選。</span><span class="sxs-lookup"><span data-stu-id="e4c15-123">Displays the filters to apply in the query.</span></span>|
|<span data-ttu-id="e4c15-124">[資料] 窗格</span><span class="sxs-lookup"><span data-stu-id="e4c15-124">Data pane</span></span>|<span data-ttu-id="e4c15-125">顯示執行查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="e4c15-125">Displays the results of running the query.</span></span>|

 <span data-ttu-id="e4c15-126">您可以將 [中繼資料] 窗格中的維度和量值以及 [導出成員] 窗格中的導出成員，拖曳至 [資料] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="e4c15-126">You can drag dimensions and measures from the Metadata pane, and calculated members from the Calculated Member pane onto the Data pane.</span></span> <span data-ttu-id="e4c15-127">如果工具列上的 **[自動執行]** 切換按鈕為開啟狀態，則每次您將物件放到 [資料] 窗格中時，查詢設計工具便會執行查詢。</span><span class="sxs-lookup"><span data-stu-id="e4c15-127">If the **AutoExecute** toggle button on the toolbar is on, the query designer runs the query every time you drop an object onto the Data pane.</span></span> <span data-ttu-id="e4c15-128">如果 **[自動執行]** 為關閉狀態，則當您對 [資料] 窗格進行變更時，查詢設計工具不會執行查詢。</span><span class="sxs-lookup"><span data-stu-id="e4c15-128">If **AutoExecute** is off, the query designer does not run the query as you make changes to the Data pane.</span></span> <span data-ttu-id="e4c15-129">您可以使用工具列上的 **[執行]** 按鈕，以手動方式執行查詢。</span><span class="sxs-lookup"><span data-stu-id="e4c15-129">You can manually run the query using the **Run** button on the toolbar.</span></span>

 <span data-ttu-id="e4c15-130">在 [篩選] 窗格中，您可以選取維度值來限制從資料來源擷取的資料。</span><span class="sxs-lookup"><span data-stu-id="e4c15-130">In the Filter pane, you can select dimension values to limit the data retrieved from the data source.</span></span> <span data-ttu-id="e4c15-131">您在「設計」模式中的篩選內定義的值會顯示於「查詢」模式中的 MDX Where 子句。</span><span class="sxs-lookup"><span data-stu-id="e4c15-131">Values you define in the filter in Design mode appear in the MDX Where clause in Query mode.</span></span>

### <a name="toolbar-for-the-graphical-query-designer-in-design-mode-toolbar"></a><span data-ttu-id="e4c15-132">設計模式中的圖形化查詢設計工具工具列</span><span class="sxs-lookup"><span data-stu-id="e4c15-132">Toolbar for the Graphical Query Designer in Design Mode Toolbar</span></span>
 <span data-ttu-id="e4c15-133">查詢設計工具工具列會提供按鈕，協助您使用圖形化介面設計 MDX 查詢。</span><span class="sxs-lookup"><span data-stu-id="e4c15-133">The query designer toolbar provides buttons to help you design MDX queries using the graphical interface.</span></span> <span data-ttu-id="e4c15-134">下表會顯示這些按鈕並描述其功能。</span><span class="sxs-lookup"><span data-stu-id="e4c15-134">The following table shows the buttons and describes their functions.</span></span>

|<span data-ttu-id="e4c15-135">按鈕</span><span class="sxs-lookup"><span data-stu-id="e4c15-135">Button</span></span>|<span data-ttu-id="e4c15-136">描述</span><span class="sxs-lookup"><span data-stu-id="e4c15-136">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="e4c15-137">**當成文字編輯**</span><span class="sxs-lookup"><span data-stu-id="e4c15-137">**Edit As Text**</span></span>|<span data-ttu-id="e4c15-138">在以文字為基礎的查詢設計工具和圖形化查詢設計工具之間切換。</span><span class="sxs-lookup"><span data-stu-id="e4c15-138">Toggle between the text-based query designer and the graphical query designer.</span></span> <span data-ttu-id="e4c15-139">無法用於這種資料來源類型。</span><span class="sxs-lookup"><span data-stu-id="e4c15-139">Not available for this data source type.</span></span>|
|<span data-ttu-id="e4c15-140">**匯入**</span><span class="sxs-lookup"><span data-stu-id="e4c15-140">**Import**</span></span>|<span data-ttu-id="e4c15-141">從檔案系統上的報表定義 (.rdl) 檔案匯入現有的查詢。</span><span class="sxs-lookup"><span data-stu-id="e4c15-141">Import an existing query from a report definition (.rdl) file on the file system.</span></span>|
|<span data-ttu-id="e4c15-142">![重新整理資料集欄位](media/rsqdicon-refreshfields.gif "重新整理資料集欄位")</span><span class="sxs-lookup"><span data-stu-id="e4c15-142">![Refresh dataset fields](media/rsqdicon-refreshfields.gif "Refresh dataset fields")</span></span>|<span data-ttu-id="e4c15-143">重新整理資料來源中的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="e4c15-143">Refresh metadata from the data source.</span></span>|
|<span data-ttu-id="e4c15-144">![新增導出成員](../analysis-services/media/rsqdicon-addcalculatedmember.gif "加入導出成員")</span><span class="sxs-lookup"><span data-stu-id="e4c15-144">![Add calculated member](../analysis-services/media/rsqdicon-addcalculatedmember.gif "Add calculated member")</span></span>|<span data-ttu-id="e4c15-145">顯示 **[導出成員產生器]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e4c15-145">Display the **Calculated Member Builder** dialog box.</span></span> <span data-ttu-id="e4c15-146">您可以使用這個對話方塊來建立或編輯導出成員的運算式，包括設定 **[解決順序]** 屬性。</span><span class="sxs-lookup"><span data-stu-id="e4c15-146">Use this to create or edit expressions for a calculated member, including setting the **Solve Order** property.</span></span>|
|<span data-ttu-id="e4c15-147">![切換以顯示空資料格](../analysis-services/media/rsqdicon-showemptycells.gif "切換以顯示空資料格")</span><span class="sxs-lookup"><span data-stu-id="e4c15-147">![Toggle for show empty cells](../analysis-services/media/rsqdicon-showemptycells.gif "Toggle for show empty cells")</span></span>|<span data-ttu-id="e4c15-148">在顯示或隱藏 [資料] 窗格中的空白資料格之間切換</span><span class="sxs-lookup"><span data-stu-id="e4c15-148">Switch between showing and not showing empty cells in the Data pane.</span></span> <span data-ttu-id="e4c15-149">(這相當於使用 MDX 中的 NON EMPTY 子句)。</span><span class="sxs-lookup"><span data-stu-id="e4c15-149">(This is the equivalent to using the NON EMPTY clause in MDX).</span></span>|
|<span data-ttu-id="e4c15-150">![自動執行查詢](../analysis-services/media/rsqdicon-autoexecute.gif "自動執行查詢")</span><span class="sxs-lookup"><span data-stu-id="e4c15-150">![AutoExecute the query](../analysis-services/media/rsqdicon-autoexecute.gif "AutoExecute the query")</span></span>|<span data-ttu-id="e4c15-151">每次進行變更 (例如刪除 [資料] 窗格中的資料行) 時自動執行查詢並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="e4c15-151">Automatically run the query and show the result every time a change is made, for example, deleting a column in the Data pane.</span></span> <span data-ttu-id="e4c15-152">結果會顯示在 [資料] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="e4c15-152">Results are shown in the Data pane.</span></span>|
|<span data-ttu-id="e4c15-153">![刪除](../analysis-services/media/rsqdicon-delete.gif "刪除")</span><span class="sxs-lookup"><span data-stu-id="e4c15-153">![Delete](../analysis-services/media/rsqdicon-delete.gif "Delete")</span></span>|<span data-ttu-id="e4c15-154">從查詢中刪除選取的項目。</span><span class="sxs-lookup"><span data-stu-id="e4c15-154">Delete the selected item from the query.</span></span> <span data-ttu-id="e4c15-155">您可以使用此按鈕來刪除 [篩選] 窗格中的選取資料列。</span><span class="sxs-lookup"><span data-stu-id="e4c15-155">Use this button to delete selected rows in the Filter pane.</span></span>|
|<span data-ttu-id="e4c15-156">![執行查詢](../analysis-services/media/rsqdicon-run.gif "執行查詢")</span><span class="sxs-lookup"><span data-stu-id="e4c15-156">![Run the query](../analysis-services/media/rsqdicon-run.gif "Run the query")</span></span>|<span data-ttu-id="e4c15-157">執行查詢並將結果顯示在 [資料] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="e4c15-157">Run the query and display the results in the Data pane.</span></span>|
|<span data-ttu-id="e4c15-158">![取消查詢](../analysis-services/media/rsqdicon-cancel.gif "取消查詢")</span><span class="sxs-lookup"><span data-stu-id="e4c15-158">![Cancel the query](../analysis-services/media/rsqdicon-cancel.gif "Cancel the query")</span></span>|<span data-ttu-id="e4c15-159">取消查詢。</span><span class="sxs-lookup"><span data-stu-id="e4c15-159">Cancel the query.</span></span>|
|<span data-ttu-id="e4c15-160">![切換到設計模式](../analysis-services/media/rsqdicon-designmode.gif "切換到設計模式")</span><span class="sxs-lookup"><span data-stu-id="e4c15-160">![Switch to Design mode](../analysis-services/media/rsqdicon-designmode.gif "Switch to Design mode")</span></span>|<span data-ttu-id="e4c15-161">在「設計」模式與「查詢」模式之間切換。</span><span class="sxs-lookup"><span data-stu-id="e4c15-161">Switch between Design mode and Query mode.</span></span>|

## <a name="graphical-query-designer-in-query-mode"></a><span data-ttu-id="e4c15-162">查詢模式中的圖形化查詢設計工具</span><span class="sxs-lookup"><span data-stu-id="e4c15-162">Graphical Query Designer in Query Mode</span></span>
 <span data-ttu-id="e4c15-163">若要將圖形化查詢設計工具變更為「查詢」模式，請按一下工具列上的 **[設計模式]** 切換按鈕。</span><span class="sxs-lookup"><span data-stu-id="e4c15-163">To change the graphical query designer to Query mode, click the **Design Mode** toggle button on the toolbar.</span></span>

 <span data-ttu-id="e4c15-164">![Hyperion 查詢模式中的查詢設計工具](media/rsqd-hyperionessbase-mdx-querymode.gif "Hyperion 查詢模式中的查詢設計工具")</span><span class="sxs-lookup"><span data-stu-id="e4c15-164">![Query Designer in Query Mode for Hyperion](media/rsqd-hyperionessbase-mdx-querymode.gif "Query Designer in Query Mode for Hyperion")</span></span>

 <span data-ttu-id="e4c15-165">下表會描述各個窗格的功能。</span><span class="sxs-lookup"><span data-stu-id="e4c15-165">The following table describes the function of each pane.</span></span>

|<span data-ttu-id="e4c15-166">窗格</span><span class="sxs-lookup"><span data-stu-id="e4c15-166">Pane</span></span>|<span data-ttu-id="e4c15-167">函式</span><span class="sxs-lookup"><span data-stu-id="e4c15-167">Function</span></span>|
|----------|--------------|
|<span data-ttu-id="e4c15-168">[選取 Cube] 按鈕</span><span class="sxs-lookup"><span data-stu-id="e4c15-168">Select Cube button</span></span>|<span data-ttu-id="e4c15-169">顯示目前選取的 Cube。</span><span class="sxs-lookup"><span data-stu-id="e4c15-169">Displays the currently selected cube.</span></span>|
|<span data-ttu-id="e4c15-170">[中繼資料/函數] 窗格</span><span class="sxs-lookup"><span data-stu-id="e4c15-170">Metadata/Functions pane</span></span>|<span data-ttu-id="e4c15-171">顯示索引標籤式的視窗，列出可用來建立查詢文字的可用中繼資料或函數清單。</span><span class="sxs-lookup"><span data-stu-id="e4c15-171">Displays a tabbed window that shows a list of available metadata or functions that can be used to build the query text.</span></span>|
|<span data-ttu-id="e4c15-172">[查詢] 窗格</span><span class="sxs-lookup"><span data-stu-id="e4c15-172">Query pane</span></span>|<span data-ttu-id="e4c15-173">顯示目前的查詢文字。</span><span class="sxs-lookup"><span data-stu-id="e4c15-173">Displays the current query text.</span></span>|
|<span data-ttu-id="e4c15-174">結果窗格</span><span class="sxs-lookup"><span data-stu-id="e4c15-174">Result pane</span></span>|<span data-ttu-id="e4c15-175">顯示查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="e4c15-175">Displays the results of the query.</span></span>|

 <span data-ttu-id="e4c15-176">您可以從 [中繼資料] 窗格，將 **[中繼資料]** 索引標籤中的量值和維度拖曳至 [MDX 查詢] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="e4c15-176">From the Metadata pane, you can drag measures and dimensions from the **Metadata** tab onto the MDX Query pane.</span></span> <span data-ttu-id="e4c15-177">您也可以將 **[函數]** 索引標籤上的函數拖曳至 [MDX 查詢] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="e4c15-177">You can drag functions from the **Functions** tab onto the MDX Query pane.</span></span> <span data-ttu-id="e4c15-178">當您執行查詢時，[結果] 窗格便會顯示目前 MDX 查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="e4c15-178">When you execute the query, the Result pane displays the results for the current MDX query.</span></span>

### <a name="toolbar-for-the-graphical-query-designer-in-query-mode"></a><span data-ttu-id="e4c15-179">查詢模式中的圖形化查詢設計工具工具列</span><span class="sxs-lookup"><span data-stu-id="e4c15-179">Toolbar for the Graphical Query Designer in Query Mode</span></span>
 <span data-ttu-id="e4c15-180">查詢設計工具工具列會提供按鈕，協助您使用圖形化介面設計 MDX 查詢。</span><span class="sxs-lookup"><span data-stu-id="e4c15-180">The query designer toolbar provides buttons to help you design MDX queries using the graphical interface.</span></span> <span data-ttu-id="e4c15-181">「設計」模式與「查詢」模式的工具列按鈕完全相同，唯一不同的是在「查詢」模式中未啟用下列按鈕：</span><span class="sxs-lookup"><span data-stu-id="e4c15-181">The toolbar buttons are identical between Design mode and Query mode, but the following buttons are not enabled for Query mode:</span></span>

-   <span data-ttu-id="e4c15-182">**當成文字編輯**</span><span class="sxs-lookup"><span data-stu-id="e4c15-182">**Edit As Text**</span></span>

-   <span data-ttu-id="e4c15-183">**新增導出成員** (![新增導出成員](../analysis-services/media/rsqdicon-addcalculatedmember.gif "加入導出成員"))</span><span class="sxs-lookup"><span data-stu-id="e4c15-183">**Add Calculated Member** (![Add calculated member](../analysis-services/media/rsqdicon-addcalculatedmember.gif "Add calculated member"))</span></span>

-   <span data-ttu-id="e4c15-184">**顯示空資料格** (![切換以顯示空資料格](../analysis-services/media/rsqdicon-showemptycells.gif "切換以顯示空資料格"))</span><span class="sxs-lookup"><span data-stu-id="e4c15-184">**Show Empty Cells** (![Toggle for show empty cells](../analysis-services/media/rsqdicon-showemptycells.gif "Toggle for show empty cells"))</span></span>

-   <span data-ttu-id="e4c15-185">**自動執行** (![自動執行查詢](../analysis-services/media/rsqdicon-autoexecute.gif "自動執行查詢"))</span><span class="sxs-lookup"><span data-stu-id="e4c15-185">**AutoExecute** (![AutoExecute the query](../analysis-services/media/rsqdicon-autoexecute.gif "AutoExecute the query"))</span></span>

## <a name="see-also"></a><span data-ttu-id="e4c15-186">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4c15-186">See Also</span></span>
 [<span data-ttu-id="e4c15-187">查詢設計工具 &#40;報表產生器&#41;</span><span class="sxs-lookup"><span data-stu-id="e4c15-187">Query Designers &#40;Report Builder&#41;</span></span>](../../2014/reporting-services/query-designers-report-builder.md)


