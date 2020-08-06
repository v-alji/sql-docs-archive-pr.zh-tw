---
title: SAP NetWeaver BI 查詢設計工具使用者介面 (報表產生器) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10014"
helpviewer_keywords:
- query designers, SAP
ms.assetid: 8edda06d-1608-498b-bd50-10905e54f6ce
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 69a009322bd2d4dcd7211e6b21aa3ecd7c9466e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593279"
---
# <a name="sap-netweaver-bi-query-designer-user-interface-report-builder"></a><span data-ttu-id="f4581-102">SAP NetWeaver BI 查詢設計工具使用者介面 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="f4581-102">SAP NetWeaver BI Query Designer User Interface (Report Builder)</span></span>
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="f4581-103">提供了圖形化查詢設計工具，可用來建立適用於 SAP NetWeaver® Business Intelligence 資料來源的多維度運算式 (MDX) 查詢。</span><span class="sxs-lookup"><span data-stu-id="f4581-103">provides a graphical query designer for building Multidimensional Expression (MDX) queries for a SAP NetWeaver® Business Intelligence data source.</span></span> <span data-ttu-id="f4581-104">MDX 圖形化查詢設計工具有兩種模式：「設計」模式和「查詢」模式。</span><span class="sxs-lookup"><span data-stu-id="f4581-104">The MDX graphical query designer has two modes: Design mode and Query mode.</span></span> <span data-ttu-id="f4581-105">每一種模式都會提供 [中繼資料] 窗格，您可以在這個窗格中，從資料來源上定義的 InfoCube、MultiProvider 或 Web 查詢中拖曳成員，從而建立 MDX 查詢，在處理報表時擷取資料。</span><span class="sxs-lookup"><span data-stu-id="f4581-105">Each mode provides a Metadata pane from which you can drag members from an InfoCube, MultiProvider, or Web-enabled query defined on the data source to build an MDX query that retrieves data when the report is processed.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="f4581-106">當使用者建立與執行查詢時，可以存取資料來源。</span><span class="sxs-lookup"><span data-stu-id="f4581-106">Users access data sources when they create and run queries.</span></span> <span data-ttu-id="f4581-107">您應該授與資料來源的最小權限，例如唯讀權限。</span><span class="sxs-lookup"><span data-stu-id="f4581-107">You should grant minimal permissions on the data sources, such as read-only permissions.</span></span>

 <span data-ttu-id="f4581-108">本節會針對圖形化查詢設計工具的各種模式，描述其中的工具列按鈕和查詢設計工具窗格。</span><span class="sxs-lookup"><span data-stu-id="f4581-108">This section describes the toolbar buttons and query designer panes for each mode of the graphical query designer.</span></span>

## <a name="graphical-query-designer-in-design-mode"></a><span data-ttu-id="f4581-109">設計模式中的圖形化查詢設計工具</span><span class="sxs-lookup"><span data-stu-id="f4581-109">Graphical Query Designer in Design Mode</span></span>
 <span data-ttu-id="f4581-110">當您編輯的資料集查詢使用了 [!INCLUDE[SAP_DPE_BW_1](../includes/sap-dpe-bw-1-md.md)] 資料來源時，圖形化查詢設計工具會在設計模式下開啟。</span><span class="sxs-lookup"><span data-stu-id="f4581-110">When you edit a dataset query that uses a [!INCLUDE[SAP_DPE_BW_1](../includes/sap-dpe-bw-1-md.md)] data source, the graphical query designer opens in the Design mode.</span></span>

 <span data-ttu-id="f4581-111">![在設計模式下使用 MDX 的查詢設計工具](media/rsqd-dssapbw-mdx-designmode.gif "在設計模式下使用 MDX 的查詢設計工具")</span><span class="sxs-lookup"><span data-stu-id="f4581-111">![Query Designer using MDX in Design Mode](media/rsqd-dssapbw-mdx-designmode.gif "Query Designer using MDX in Design Mode")</span></span>

 <span data-ttu-id="f4581-112">下表列出此模式下的窗格。</span><span class="sxs-lookup"><span data-stu-id="f4581-112">The following table lists the panes in this mode.</span></span>

|<span data-ttu-id="f4581-113">窗格</span><span class="sxs-lookup"><span data-stu-id="f4581-113">Pane</span></span>|<span data-ttu-id="f4581-114">函式</span><span class="sxs-lookup"><span data-stu-id="f4581-114">Function</span></span>|
|----------|--------------|
|<span data-ttu-id="f4581-115">[選取 Cube] 按鈕</span><span class="sxs-lookup"><span data-stu-id="f4581-115">Select Cube button</span></span>|<span data-ttu-id="f4581-116">顯示目前選取的 InfoCube、MultiProvider 或 Web 查詢。</span><span class="sxs-lookup"><span data-stu-id="f4581-116">Displays the currently selected InfoCube, MultiProvider, or Web-enabled query.</span></span>|
|<span data-ttu-id="f4581-117">[中繼資料] 窗格</span><span class="sxs-lookup"><span data-stu-id="f4581-117">Metadata pane</span></span>|<span data-ttu-id="f4581-118">顯示 InfoCube、MultiProvider 和查詢的階層式清單。</span><span class="sxs-lookup"><span data-stu-id="f4581-118">Displays a hierarchical list of InfoCubes, MultiProviders, and queries.</span></span> <span data-ttu-id="f4581-119">在資料來源建立的查詢可能會顯示在對應的 Cube 底下。</span><span class="sxs-lookup"><span data-stu-id="f4581-119">Queries created at the data source may appear under the corresponding cube.</span></span>|
|<span data-ttu-id="f4581-120">[導出成員] 窗格</span><span class="sxs-lookup"><span data-stu-id="f4581-120">Calculated Members pane</span></span>|<span data-ttu-id="f4581-121">顯示目前已定義，可在查詢中使用的導出成員。</span><span class="sxs-lookup"><span data-stu-id="f4581-121">Displays the currently defined calculated members available for use in the query.</span></span>|
|<span data-ttu-id="f4581-122">[資料] 窗格</span><span class="sxs-lookup"><span data-stu-id="f4581-122">Data pane</span></span>|<span data-ttu-id="f4581-123">顯示執行查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="f4581-123">Displays the results of running the query.</span></span>|

 <span data-ttu-id="f4581-124">您可以將 [中繼資料] 窗格中的維度和重要數據以及 [導出成員] 窗格中的導出成員，拖曳至 [資料] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="f4581-124">You can drag dimensions and key figures from the Metadata pane, and calculated members from the Calculated Member pane onto the Data pane.</span></span> <span data-ttu-id="f4581-125">如果工具列上的 **[自動執行]** 切換按鈕為開啟狀態，則每次您將物件放到 [資料] 窗格中時，查詢設計工具便會執行查詢。</span><span class="sxs-lookup"><span data-stu-id="f4581-125">If the **AutoExecute** toggle button on the toolbar is on, the query designer runs the query every time you drop an object onto the Data pane.</span></span> <span data-ttu-id="f4581-126">如果 **[自動執行]** 為關閉狀態，則當您對 [資料] 窗格進行變更時，查詢設計工具不會執行查詢。</span><span class="sxs-lookup"><span data-stu-id="f4581-126">If **AutoExecute** is off, the query designer does not run the query as you make changes to the Data pane.</span></span> <span data-ttu-id="f4581-127">您可以使用工具列上的 **[執行]** 按鈕，以手動方式執行查詢。</span><span class="sxs-lookup"><span data-stu-id="f4581-127">You can manually run the query using the **Run** button on the toolbar.</span></span>

### <a name="toolbar-for-the-graphical-query-designer-in-design-mode-toolbar"></a><span data-ttu-id="f4581-128">設計模式中的圖形化查詢設計工具工具列</span><span class="sxs-lookup"><span data-stu-id="f4581-128">Toolbar for the Graphical Query Designer in Design Mode Toolbar</span></span>
 <span data-ttu-id="f4581-129">查詢設計工具工具列會提供按鈕，協助您使用圖形化介面設計 MDX 查詢。</span><span class="sxs-lookup"><span data-stu-id="f4581-129">The query designer toolbar provides buttons to help you design MDX queries using the graphical interface.</span></span> <span data-ttu-id="f4581-130">下表描述這些按鈕及其功能。</span><span class="sxs-lookup"><span data-stu-id="f4581-130">The following table describes the buttons and their functions.</span></span>

|<span data-ttu-id="f4581-131">按鈕</span><span class="sxs-lookup"><span data-stu-id="f4581-131">Button</span></span>|<span data-ttu-id="f4581-132">描述</span><span class="sxs-lookup"><span data-stu-id="f4581-132">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="f4581-133">**當成文字編輯**</span><span class="sxs-lookup"><span data-stu-id="f4581-133">**Edit As Text**</span></span>|<span data-ttu-id="f4581-134">在以文字為基礎的查詢設計工具和圖形化查詢設計工具之間切換。</span><span class="sxs-lookup"><span data-stu-id="f4581-134">Toggle between the text-based query designer and the graphical query designer.</span></span> <span data-ttu-id="f4581-135">無法用於這種資料來源類型。</span><span class="sxs-lookup"><span data-stu-id="f4581-135">Not available for this data source type.</span></span>|
|<span data-ttu-id="f4581-136">**匯入**</span><span class="sxs-lookup"><span data-stu-id="f4581-136">**Import**</span></span>|<span data-ttu-id="f4581-137">從檔案系統上的報表定義 (.rdl) 檔案匯入現有的查詢。</span><span class="sxs-lookup"><span data-stu-id="f4581-137">Import an existing query from a report definition (.rdl) file on the file system.</span></span>|
|<span data-ttu-id="f4581-138">![重新整理資料集欄位](media/rsqdicon-refreshfields.gif "重新整理資料集欄位")</span><span class="sxs-lookup"><span data-stu-id="f4581-138">![Refresh dataset fields](media/rsqdicon-refreshfields.gif "Refresh dataset fields")</span></span>|<span data-ttu-id="f4581-139">重新整理資料來源中的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="f4581-139">Refresh metadata from the data source.</span></span>|
|<span data-ttu-id="f4581-140">![新增導出成員](../analysis-services/media/rsqdicon-addcalculatedmember.gif "加入導出成員")</span><span class="sxs-lookup"><span data-stu-id="f4581-140">![Add calculated member](../analysis-services/media/rsqdicon-addcalculatedmember.gif "Add calculated member")</span></span>|<span data-ttu-id="f4581-141">顯示 **[導出成員產生器]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f4581-141">Display the **Calculated Member Builder** dialog box.</span></span>|
|<span data-ttu-id="f4581-142">![切換以顯示空資料格](../analysis-services/media/rsqdicon-showemptycells.gif "切換以顯示空資料格")</span><span class="sxs-lookup"><span data-stu-id="f4581-142">![Toggle for show empty cells](../analysis-services/media/rsqdicon-showemptycells.gif "Toggle for show empty cells")</span></span>|<span data-ttu-id="f4581-143">在顯示或隱藏 [資料] 窗格中的空白資料格之間切換</span><span class="sxs-lookup"><span data-stu-id="f4581-143">Switch between showing and not showing empty cells in the Data pane.</span></span> <span data-ttu-id="f4581-144">(這相當於使用 MDX 中的 NON EMPTY 子句)。</span><span class="sxs-lookup"><span data-stu-id="f4581-144">(This is the equivalent to using the NON EMPTY clause in MDX).</span></span>|
|<span data-ttu-id="f4581-145">![自動執行查詢](../analysis-services/media/rsqdicon-autoexecute.gif "自動執行查詢")</span><span class="sxs-lookup"><span data-stu-id="f4581-145">![AutoExecute the query](../analysis-services/media/rsqdicon-autoexecute.gif "AutoExecute the query")</span></span>|<span data-ttu-id="f4581-146">每次進行變更 (例如刪除 [資料] 窗格中的資料行) 時自動執行查詢並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="f4581-146">Automatically run the query and show the result every time a change is made, for example, deleting a column in the Data pane.</span></span> <span data-ttu-id="f4581-147">結果會顯示在 [資料] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="f4581-147">Results are shown in the Data pane.</span></span>|
|<span data-ttu-id="f4581-148">![刪除](../analysis-services/media/rsqdicon-delete.gif "刪除")</span><span class="sxs-lookup"><span data-stu-id="f4581-148">![Delete](../analysis-services/media/rsqdicon-delete.gif "Delete")</span></span>|<span data-ttu-id="f4581-149">從查詢中刪除 [資料] 窗格中選取的資料行。</span><span class="sxs-lookup"><span data-stu-id="f4581-149">Delete the selected column in the Data pane from the query.</span></span>|
|<span data-ttu-id="f4581-150">![[查詢參數] 對話方塊圖示](../analysis-services/media/iconqueryparameter.gif "[查詢參數] 對話方塊圖示")</span><span class="sxs-lookup"><span data-stu-id="f4581-150">![Icon for the Query Parameters dialog box](../analysis-services/media/iconqueryparameter.gif "Icon for the Query Parameters dialog box")</span></span>|<span data-ttu-id="f4581-151">顯示 **[變數]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f4581-151">Display the **Variables** dialog box.</span></span> <span data-ttu-id="f4581-152">只有當選取的 Cube 是查詢 Cube 時，才會啟用這個按鈕 (因為只有查詢 Cube 才支援變數)。</span><span class="sxs-lookup"><span data-stu-id="f4581-152">This button is enabled only when the selected cube is a Query cube (because only query cubes support variables).</span></span> <span data-ttu-id="f4581-153">當您指派預設值給變數時，就會建立對應的報表參數。</span><span class="sxs-lookup"><span data-stu-id="f4581-153">When you assign a default value to a variable, a corresponding report parameter is created.</span></span>|
|<span data-ttu-id="f4581-154">![執行查詢](../analysis-services/media/rsqdicon-run.gif "執行查詢")</span><span class="sxs-lookup"><span data-stu-id="f4581-154">![Run the query](../analysis-services/media/rsqdicon-run.gif "Run the query")</span></span>|<span data-ttu-id="f4581-155">執行查詢並將結果顯示在 [資料] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="f4581-155">Run the query and display the results in the Data pane.</span></span>|
|<span data-ttu-id="f4581-156">![取消查詢](../analysis-services/media/rsqdicon-cancel.gif "取消查詢")</span><span class="sxs-lookup"><span data-stu-id="f4581-156">![Cancel the query](../analysis-services/media/rsqdicon-cancel.gif "Cancel the query")</span></span>|<span data-ttu-id="f4581-157">取消查詢。</span><span class="sxs-lookup"><span data-stu-id="f4581-157">Cancel the query.</span></span>|
|<span data-ttu-id="f4581-158">![切換到設計模式](../analysis-services/media/rsqdicon-designmode.gif "切換到設計模式")</span><span class="sxs-lookup"><span data-stu-id="f4581-158">![Switch to Design mode](../analysis-services/media/rsqdicon-designmode.gif "Switch to Design mode")</span></span>|<span data-ttu-id="f4581-159">在「設計」模式與「查詢」模式之間切換。</span><span class="sxs-lookup"><span data-stu-id="f4581-159">Switch between Design mode and Query mode.</span></span>|

## <a name="graphical-query-designer-in-query-mode"></a><span data-ttu-id="f4581-160">查詢模式中的圖形化查詢設計工具</span><span class="sxs-lookup"><span data-stu-id="f4581-160">Graphical Query Designer in Query Mode</span></span>
 <span data-ttu-id="f4581-161">若要將圖形化查詢設計工具變更為「查詢」模式，請按一下工具列上的 **[設計模式]** 切換按鈕。</span><span class="sxs-lookup"><span data-stu-id="f4581-161">To change the graphical query designer to Query mode, click the **Design Mode** toggle button on the toolbar.</span></span>

 <span data-ttu-id="f4581-162">下圖會指出查詢設計工具在「查詢」模式中的各個部分。</span><span class="sxs-lookup"><span data-stu-id="f4581-162">The following figure indicates the parts of the query designer in Query mode.</span></span>

 <span data-ttu-id="f4581-163">![查詢檢視中的 SAP BW MDX 查詢設計工具](media/rsqd-dssapbw-mdx-querymode.gif "查詢檢視中的 SAP BW MDX 查詢設計工具")</span><span class="sxs-lookup"><span data-stu-id="f4581-163">![SAP BW MDX query designer in query view](media/rsqd-dssapbw-mdx-querymode.gif "SAP BW MDX query designer in query view")</span></span>

 <span data-ttu-id="f4581-164">下表會描述各個窗格的功能。</span><span class="sxs-lookup"><span data-stu-id="f4581-164">The following table describes the function of each pane.</span></span>

|<span data-ttu-id="f4581-165">窗格</span><span class="sxs-lookup"><span data-stu-id="f4581-165">Pane</span></span>|<span data-ttu-id="f4581-166">函式</span><span class="sxs-lookup"><span data-stu-id="f4581-166">Function</span></span>|
|----------|--------------|
|<span data-ttu-id="f4581-167">[選取 Cube] 按鈕</span><span class="sxs-lookup"><span data-stu-id="f4581-167">Select Cube button</span></span>|<span data-ttu-id="f4581-168">顯示目前選取的 InfoCube、MultiProvider 或其他 Cube。</span><span class="sxs-lookup"><span data-stu-id="f4581-168">Displays the currently selected InfoCube, MultiProvider, or other cube.</span></span>|
|<span data-ttu-id="f4581-169">[中繼資料/函數] 窗格</span><span class="sxs-lookup"><span data-stu-id="f4581-169">Metadata/Functions pane</span></span>|<span data-ttu-id="f4581-170">顯示索引標籤式的視窗，列出可用來建立查詢文字的可用中繼資料或函數清單。</span><span class="sxs-lookup"><span data-stu-id="f4581-170">Displays a tabbed window that shows a list of available metadata or functions that can be used to build the query text.</span></span>|
|<span data-ttu-id="f4581-171">[變數] 窗格</span><span class="sxs-lookup"><span data-stu-id="f4581-171">Variables pane</span></span>|<span data-ttu-id="f4581-172">顯示目前已定義，可在查詢中使用的變數。</span><span class="sxs-lookup"><span data-stu-id="f4581-172">Displays the currently defined variables available for use in the query.</span></span>|
|<span data-ttu-id="f4581-173">[查詢] 窗格</span><span class="sxs-lookup"><span data-stu-id="f4581-173">Query pane</span></span>|<span data-ttu-id="f4581-174">顯示目前的查詢文字。</span><span class="sxs-lookup"><span data-stu-id="f4581-174">Displays the current query text.</span></span>|
|<span data-ttu-id="f4581-175">結果窗格</span><span class="sxs-lookup"><span data-stu-id="f4581-175">Result pane</span></span>|<span data-ttu-id="f4581-176">顯示查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="f4581-176">Displays the results of the query.</span></span>|

 <span data-ttu-id="f4581-177">在 [中繼資料] 窗格中，您可以將 **[中繼資料]** 索引標籤上的重要數據和維度拖曳至 [MDX 查詢] 窗格中；中繼資料的技術名稱會插入於游標所在的位置。</span><span class="sxs-lookup"><span data-stu-id="f4581-177">From the Metadata pane, you can drag key figures and dimensions from the **Metadata** tab onto the MDX Query pane; the technical name for the metadata is inserted at the cursor.</span></span> <span data-ttu-id="f4581-178">您也可以將 **[函數]** 索引標籤上的函數拖曳至 [MDX 查詢] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="f4581-178">You can drag functions from the **Functions** tab onto the MDX Query pane.</span></span> <span data-ttu-id="f4581-179">當您執行查詢時，[結果] 窗格便會顯示目前 MDX 查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="f4581-179">When you execute the query, the Result pane displays the results for the current MDX query.</span></span>

 <span data-ttu-id="f4581-180">如果您選取的 Cube 是 Web 查詢，則會提示您為現有的變數設定靜態預設值，</span><span class="sxs-lookup"><span data-stu-id="f4581-180">If your selected cube is a Web-enabled query, you will be prompted to set static default values for the existing variables.</span></span> <span data-ttu-id="f4581-181">然後您就可以將變數拖曳至 [MDX 查詢] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="f4581-181">You can then drag variables onto the MDX Query pane.</span></span>

 <span data-ttu-id="f4581-182">[中繼資料] 窗格和 [變數] 窗格會顯示易記名稱。</span><span class="sxs-lookup"><span data-stu-id="f4581-182">The Metadata and Variable panes display friendly names.</span></span> <span data-ttu-id="f4581-183">當您將物件放到 [MDX 查詢] 窗格中時，就可以看到資料來源所需的技術名稱已輸入到 MDX 查詢中。</span><span class="sxs-lookup"><span data-stu-id="f4581-183">When you drop the objects onto the MDX Query pane, you see the technical names needed by the data source entered into the MDX query.</span></span>

### <a name="toolbar-for-the-graphical-query-designer-in-query-mode"></a><span data-ttu-id="f4581-184">查詢模式中的圖形化查詢設計工具工具列</span><span class="sxs-lookup"><span data-stu-id="f4581-184">Toolbar for the Graphical Query Designer in Query Mode</span></span>
 <span data-ttu-id="f4581-185">查詢設計工具工具列會提供按鈕，協助您使用圖形化介面設計 MDX 查詢。</span><span class="sxs-lookup"><span data-stu-id="f4581-185">The query designer toolbar provides buttons to help you design MDX queries using the graphical interface.</span></span> <span data-ttu-id="f4581-186">「設計」模式與「查詢」模式的工具列按鈕完全相同，唯一不同的是在「查詢」模式中未啟用下列按鈕：</span><span class="sxs-lookup"><span data-stu-id="f4581-186">The toolbar buttons are identical between Design mode and Query mode, but the following buttons are not enabled for Query mode:</span></span>

-   <span data-ttu-id="f4581-187">**當成文字編輯**</span><span class="sxs-lookup"><span data-stu-id="f4581-187">**Edit As Text**</span></span>

-   <span data-ttu-id="f4581-188">**新增導出成員** (![新增導出成員](../analysis-services/media/rsqdicon-addcalculatedmember.gif "加入導出成員"))</span><span class="sxs-lookup"><span data-stu-id="f4581-188">**Add Calculated Member** (![Add calculated member](../analysis-services/media/rsqdicon-addcalculatedmember.gif "Add calculated member"))</span></span>

-   <span data-ttu-id="f4581-189">**顯示空資料格** (![切換以顯示空資料格](../analysis-services/media/rsqdicon-showemptycells.gif "切換以顯示空資料格"))</span><span class="sxs-lookup"><span data-stu-id="f4581-189">**Show Empty Cells** (![Toggle for show empty cells](../analysis-services/media/rsqdicon-showemptycells.gif "Toggle for show empty cells"))</span></span>

-   <span data-ttu-id="f4581-190">**自動執行** (![自動執行查詢](../analysis-services/media/rsqdicon-autoexecute.gif "自動執行查詢"))</span><span class="sxs-lookup"><span data-stu-id="f4581-190">**AutoExecute** (![AutoExecute the query](../analysis-services/media/rsqdicon-autoexecute.gif "AutoExecute the query"))</span></span>

-   <span data-ttu-id="f4581-191">**刪除** (![刪除](../analysis-services/media/rsqdicon-delete.gif "刪除"))</span><span class="sxs-lookup"><span data-stu-id="f4581-191">**Delete** (![Delete](../analysis-services/media/rsqdicon-delete.gif "Delete"))</span></span>

## <a name="see-also"></a><span data-ttu-id="f4581-192">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4581-192">See Also</span></span>
 [<span data-ttu-id="f4581-193">查詢設計工具 &#40;報表產生器&#41;</span><span class="sxs-lookup"><span data-stu-id="f4581-193">Query Designers &#40;Report Builder&#41;</span></span>](../../2014/reporting-services/query-designers-report-builder.md)


