---
title: 修改追蹤結果檢視 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 860a80dc-bac0-4ef0-bf7f-7a9b430d7aa3
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 050c8f179742cf3cef6473b03f062390caf195f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592190"
---
# <a name="modify-the-trace-results-view"></a><span data-ttu-id="eb1be-102">修改追蹤結果檢視</span><span class="sxs-lookup"><span data-stu-id="eb1be-102">Modify the Trace Results View</span></span>
  <span data-ttu-id="eb1be-103">本主題描述如何透過執行下列工作，在 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 中修改擴充事件工作階段的追蹤結果檢視。</span><span class="sxs-lookup"><span data-stu-id="eb1be-103">This topic describes how to modify the trace results view of an Extended Events session in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] by performing the following tasks.</span></span>  
  
1.  [<span data-ttu-id="eb1be-104">新增或移除資料行</span><span class="sxs-lookup"><span data-stu-id="eb1be-104">Add or Remove Columns</span></span>](#AddRemoveColumns)  
  
2.  [<span data-ttu-id="eb1be-105">建立、編輯或刪除合併的資料行</span><span class="sxs-lookup"><span data-stu-id="eb1be-105">Create, Edit, or Delete Merged Columns</span></span>](#ChangeColumns)  
  
3.  [<span data-ttu-id="eb1be-106">排序結果</span><span class="sxs-lookup"><span data-stu-id="eb1be-106">Sort the Results</span></span>](#SortResults)  
  
4.  [<span data-ttu-id="eb1be-107">將結果分組</span><span class="sxs-lookup"><span data-stu-id="eb1be-107">Group the Results</span></span>](#GroupResults)  
  
5.  [<span data-ttu-id="eb1be-108">彙總結果</span><span class="sxs-lookup"><span data-stu-id="eb1be-108">Aggregate the Results</span></span>](#AggregateResults)  
  
6.  [<span data-ttu-id="eb1be-109">篩選結果</span><span class="sxs-lookup"><span data-stu-id="eb1be-109">Filter the Results</span></span>](#Filter)  
  
7.  [<span data-ttu-id="eb1be-110">在資料行中搜尋文字</span><span class="sxs-lookup"><span data-stu-id="eb1be-110">Search for Text in Columns</span></span>](#Search)  
  
8.  [<span data-ttu-id="eb1be-111">變更顯示設定</span><span class="sxs-lookup"><span data-stu-id="eb1be-111">Change the Display Settings</span></span>](#ChangeDisplay)  
  
##  <a name="add-or-remove-columns"></a><a name="AddRemoveColumns"></a><span data-ttu-id="eb1be-112">新增或移除資料行</span><span class="sxs-lookup"><span data-stu-id="eb1be-112">Add or Remove Columns</span></span>  
  
1.  <span data-ttu-id="eb1be-113">開啟 .XEL 檔案以檢視追蹤結果</span><span class="sxs-lookup"><span data-stu-id="eb1be-113">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eb1be-114"> 您也可以用滑鼠右鍵按一下工作階段名稱，然後選取 **[監看即時資料]**。</span><span class="sxs-lookup"><span data-stu-id="eb1be-114">You can also right click the session name, and then select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="eb1be-115">在追蹤結果視窗中，以滑鼠右鍵按一下資料行標頭，然後選取 **[選擇資料行]**。</span><span class="sxs-lookup"><span data-stu-id="eb1be-115">In the trace results window, right-click the column header, and then select **Choose Columns**.</span></span>  
  
3.  <span data-ttu-id="eb1be-116">在 **[選擇資料行]** 對話方塊的 **[可用的資料行]** 區段中，選取要新增的資料行名稱，然後按一下向右箭頭。</span><span class="sxs-lookup"><span data-stu-id="eb1be-116">In the **Choose Columns** dialog box, in the **Available columns** section, select the column names you want to add, and then click the right arrow.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eb1be-117">根據預設，資料行依名稱排列。</span><span class="sxs-lookup"><span data-stu-id="eb1be-117">By default, the columns are arranged by name.</span></span> <span data-ttu-id="eb1be-118">若要依事件顯示資料行，請按一下 **[依事件排列]**。</span><span class="sxs-lookup"><span data-stu-id="eb1be-118">To display the columns by event, click **Arrange by event**.</span></span>  
  
     <span data-ttu-id="eb1be-119">若要移除資料行，請在 **[選取的資料行]** 區段中選取要移除的資料行，然後按一下向左箭頭。</span><span class="sxs-lookup"><span data-stu-id="eb1be-119">To remove columns, in the **Selected columns** section, select the columns you want to remove, and click the left arrow.</span></span>  
  
4.  <span data-ttu-id="eb1be-120">在 **[選取的資料行]** 區段中，若要變更資料行排序顯示，請分別按一下 **[上移]** 或 **[下移]** 。</span><span class="sxs-lookup"><span data-stu-id="eb1be-120">In the **Selected columns** section, to change the column order display, click **Move Up** or **Move Down** respectively.</span></span> <span data-ttu-id="eb1be-121">不能移動多個資料列。</span><span class="sxs-lookup"><span data-stu-id="eb1be-121">You cannot move multiple rows.</span></span>  
  
5.  <span data-ttu-id="eb1be-122">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="eb1be-122">Click **OK**.</span></span>  
  
##  <a name="create-edit-or-delete-merged-columns"></a><a name="ChangeColumns"></a><span data-ttu-id="eb1be-123">建立、編輯或刪除合併的資料行</span><span class="sxs-lookup"><span data-stu-id="eb1be-123">Create, Edit, or Delete Merged Columns</span></span>  
  
#### <a name="to-create-merged-columns"></a><span data-ttu-id="eb1be-124">若要建立合併的資料行</span><span class="sxs-lookup"><span data-stu-id="eb1be-124">To create merged columns</span></span>  
  
1.  <span data-ttu-id="eb1be-125">開啟 .XEL 檔案以檢視追蹤結果</span><span class="sxs-lookup"><span data-stu-id="eb1be-125">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eb1be-126"> 您也可以用滑鼠右鍵按一下工作階段名稱，然後選取 **[監看即時資料]**。</span><span class="sxs-lookup"><span data-stu-id="eb1be-126">You can also right click the session name, and then select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="eb1be-127">在追蹤結果視窗中，以滑鼠右鍵按一下資料行標頭，然後按一下 **[選擇資料行]**。</span><span class="sxs-lookup"><span data-stu-id="eb1be-127">In the trace results window, right-click the column header, and then click **Choose Columns**.</span></span>  
  
3.  <span data-ttu-id="eb1be-128">在 **[選擇資料行]** 對話方塊中，按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="eb1be-128">In the **Choose Columns** dialog box, click **New**.</span></span>  
  
4.  <span data-ttu-id="eb1be-129">在 **[新增合併的資料行]** 對話方塊的 **[合併的資料行名稱]** 方塊中，輸入合併的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="eb1be-129">In the **New Merged Column** dialog box, in the **Merged column name** box, enter a name for the merged columns.</span></span>  
  
5.  <span data-ttu-id="eb1be-130">在 **[要合併的原始資料行]** 方塊中，從下拉式清單中選取兩個以上要合併的資料行。</span><span class="sxs-lookup"><span data-stu-id="eb1be-130">In the **Original columns to merge** box, select two or more columns to merge from the drop-down list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eb1be-131">擴充事件最多只支援合併五個資料行。</span><span class="sxs-lookup"><span data-stu-id="eb1be-131">Extended Events only supports merging up to five columns.</span></span>  
  
6.  <span data-ttu-id="eb1be-132">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="eb1be-132">Click **OK**.</span></span>  
  
#### <a name="to-edit-merged-columns"></a><span data-ttu-id="eb1be-133">編輯合併的資料行</span><span class="sxs-lookup"><span data-stu-id="eb1be-133">To edit merged columns</span></span>  
  
1.  <span data-ttu-id="eb1be-134">開啟 .XEL 檔案以檢視追蹤結果</span><span class="sxs-lookup"><span data-stu-id="eb1be-134">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eb1be-135"> 您也可以用滑鼠右鍵按一下工作階段名稱，然後選取 **[監看即時資料]**。</span><span class="sxs-lookup"><span data-stu-id="eb1be-135">You can also right click the session name, and then select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="eb1be-136">在追蹤結果視窗中，以滑鼠右鍵按一下資料行標頭，然後按一下 **[選擇資料行]**。</span><span class="sxs-lookup"><span data-stu-id="eb1be-136">In the trace results window, right-click the column header, and then click **Choose Columns**.</span></span>  
  
3.  <span data-ttu-id="eb1be-137">在 **[選擇資料行]** 對話方塊中，按一下 **[編輯]**。</span><span class="sxs-lookup"><span data-stu-id="eb1be-137">In the **Choose Columns** dialog box, click **Edit**.</span></span>  
  
4.  <span data-ttu-id="eb1be-138">若要變更合併的資料行名稱，請在 **[新增合併的資料行]** 對話方塊的 **[合併的資料行名稱]** 方塊中輸入新名稱。</span><span class="sxs-lookup"><span data-stu-id="eb1be-138">To change the name of the merged column, in the **New Merged Column** dialog box, in the **Merged column name** box, enter the new name.</span></span>  
  
     <span data-ttu-id="eb1be-139">若要變更要合併的資料行，請在 **[要合併的原始資料行]** 方塊中，從下拉式清單中選取要合併的資料行，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="eb1be-139">To change the columns you want to merge, in the **Original columns to merge** box, select the columns you want to merge from the drop-down list, and then click **OK**.</span></span>  
  
#### <a name="to-delete-merged-columns"></a><span data-ttu-id="eb1be-140">刪除合併的資料行</span><span class="sxs-lookup"><span data-stu-id="eb1be-140">To delete merged columns</span></span>  
  
1.  <span data-ttu-id="eb1be-141">開啟 .XEL 檔案以檢視追蹤結果</span><span class="sxs-lookup"><span data-stu-id="eb1be-141">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eb1be-142"> 您也可以用滑鼠右鍵按一下工作階段名稱，然後選取 **[監看即時資料]**。</span><span class="sxs-lookup"><span data-stu-id="eb1be-142">You can also right click the session name, and then select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="eb1be-143">在追蹤結果視窗中，以滑鼠右鍵按一下資料行標頭，然後按一下 **[選擇資料行]**。</span><span class="sxs-lookup"><span data-stu-id="eb1be-143">In the trace results window, right-click the column header, and then click **Choose Columns**.</span></span>  
  
3.  <span data-ttu-id="eb1be-144">在 **[選擇資料行]** 對話方塊中，選取要刪除之合併資料行的名稱，然後按一下 **[刪除]**。</span><span class="sxs-lookup"><span data-stu-id="eb1be-144">In the **Choose Columns** dialog box, select the name of the merged column you want to delete, and then click **Delete**.</span></span>  
  
##  <a name="sort-the-results"></a><a name="SortResults"></a><span data-ttu-id="eb1be-145">排序結果</span><span class="sxs-lookup"><span data-stu-id="eb1be-145">Sort the Results</span></span>  
  
#### <a name="to-sort-the-results-in-ascending-or-descending-order"></a><span data-ttu-id="eb1be-146">若要以遞增或遞減順序排序結果</span><span class="sxs-lookup"><span data-stu-id="eb1be-146">To sort the results in ascending or descending order</span></span>  
  
-   <span data-ttu-id="eb1be-147">開啟 .XEL 檔案以檢視追蹤結果</span><span class="sxs-lookup"><span data-stu-id="eb1be-147">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eb1be-148"> 您也可以用滑鼠右鍵按一下工作階段名稱、選取 **[監看即時資料]**，然後按一下工具列上的 **[停止資料摘要]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="eb1be-148">You can also right click the session name, select **Watch Live Data**, and then click the **Stop Data Feed** button on the toolbar.</span></span>  
  
-   <span data-ttu-id="eb1be-149">在追蹤結果視窗中，以滑鼠右鍵按一下要排序的資料行標題。</span><span class="sxs-lookup"><span data-stu-id="eb1be-149">In the trace results window, right-click the column heading you want to sort.</span></span> <span data-ttu-id="eb1be-150">按一下 **[遞增排序]** 或 **[遞減排序]** ，分別以遞增或遞減順序排序資料行。</span><span class="sxs-lookup"><span data-stu-id="eb1be-150">Click **Sort Ascending** or **Sort Descending** to sort the column in ascending or descending order respectively.</span></span>  
  
     <span data-ttu-id="eb1be-151">如果已對資料行進行分組，則資料行排序只會對群組中的資料進行排序。</span><span class="sxs-lookup"><span data-stu-id="eb1be-151">If you have grouped columns, sorting the column will only sort data within the group.</span></span>  
  
##  <a name="group-results"></a><a name="GroupResults"></a><span data-ttu-id="eb1be-152">群組結果</span><span class="sxs-lookup"><span data-stu-id="eb1be-152">Group Results</span></span>  
  
#### <a name="to-group-the-results-by-a-single-column"></a><span data-ttu-id="eb1be-153">若要依單一資料行將結果分組</span><span class="sxs-lookup"><span data-stu-id="eb1be-153">To group the results by a single column</span></span>  
  
1.  <span data-ttu-id="eb1be-154">開啟 .XEL 檔案以檢視追蹤結果</span><span class="sxs-lookup"><span data-stu-id="eb1be-154">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eb1be-155"> 您也可以用滑鼠右鍵按一下工作階段名稱，選取 **[監看即時資料]**，然後按一下 [擴充事件] 工具列上的 **[停止資料摘要]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="eb1be-155">You can also right click the session name, select **Watch Live Data**, and then click the **Stop Data Feed** button on the Extended Events toolbar.</span></span>  
  
2.  <span data-ttu-id="eb1be-156">在追蹤結果視窗中，以滑鼠右鍵按一下要分組的資料行標頭，然後按一下 **[依此資料行群組]**。</span><span class="sxs-lookup"><span data-stu-id="eb1be-156">In the trace results window, right-click the column header you want to group, and then click **Group By This Column**.</span></span>  
  
#### <a name="to-group-the-results-by-multiple-columns"></a><span data-ttu-id="eb1be-157">依多個資料行將結果分組</span><span class="sxs-lookup"><span data-stu-id="eb1be-157">To group the results by multiple columns</span></span>  
  
1.  <span data-ttu-id="eb1be-158">開啟 .XEL 檔案以檢視追蹤結果</span><span class="sxs-lookup"><span data-stu-id="eb1be-158">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eb1be-159"> 您也可以用滑鼠右鍵按一下工作階段名稱、選取 **[監看即時資料]**，然後按一下工具列上的 **[停止資料摘要]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="eb1be-159">You can also right click the session name, select **Watch Live Data**, and then click the **Stop Data Feed** button on the toolbar.</span></span>  
  
2.  <span data-ttu-id="eb1be-160">按一下 [擴充事件] 工具列上的 **[群組]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="eb1be-160">Click the **Grouping** button on the Extended Events toolbar.</span></span>  
  
3.  <span data-ttu-id="eb1be-161">在 **[群組]** 對話方塊的 **[可用的資料行]** 方塊中，選取您要分組的資料行，然後按一下向右箭頭。</span><span class="sxs-lookup"><span data-stu-id="eb1be-161">In the **Grouping** dialog box, in the **Available columns** box, select the columns you want to group, and then click the right arrow.</span></span>  
  
     <span data-ttu-id="eb1be-162">若要變更分組順序，請在 **[群組的資料行依據]** 區段中按一下向上箭頭或向下箭頭。</span><span class="sxs-lookup"><span data-stu-id="eb1be-162">To change the grouping order, in the **Columns grouped on** section, click the up or down arrows.</span></span>  
  
     <span data-ttu-id="eb1be-163">若要從群組移除資料行，請在 **[群組的資料行依據]** 方塊中選取要移除的資料行，然後按一下向左箭頭。</span><span class="sxs-lookup"><span data-stu-id="eb1be-163">To remove columns from the grouping, in the **Columns grouped on** box, select the columns you want to remove and then click the left arrow.</span></span>  
  
4.  <span data-ttu-id="eb1be-164">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="eb1be-164">Click **OK**.</span></span>  
  
##  <a name="aggregate-results"></a><a name="AggregateResults"></a><span data-ttu-id="eb1be-165">匯總結果</span><span class="sxs-lookup"><span data-stu-id="eb1be-165">Aggregate Results</span></span>  
 <span data-ttu-id="eb1be-166">擴充事件支援五個彙總函式：</span><span class="sxs-lookup"><span data-stu-id="eb1be-166">Extended Events supports five aggregation functions:</span></span>  
  
-   <span data-ttu-id="eb1be-167">加總</span><span class="sxs-lookup"><span data-stu-id="eb1be-167">Sum</span></span>  
  
-   <span data-ttu-id="eb1be-168">最小值</span><span class="sxs-lookup"><span data-stu-id="eb1be-168">Min</span></span>  
  
-   <span data-ttu-id="eb1be-169">最大值</span><span class="sxs-lookup"><span data-stu-id="eb1be-169">Max</span></span>  
  
-   <span data-ttu-id="eb1be-170">Average</span><span class="sxs-lookup"><span data-stu-id="eb1be-170">Average</span></span>  
  
-   <span data-ttu-id="eb1be-171">計數</span><span class="sxs-lookup"><span data-stu-id="eb1be-171">Count</span></span>  
  
 <span data-ttu-id="eb1be-172">Sum、Min、Max 和 Average 只能搭配可用的數值資料行使用。</span><span class="sxs-lookup"><span data-stu-id="eb1be-172">Sum, Min,  Max, and Average can only be used with available numeric columns.</span></span> <span data-ttu-id="eb1be-173">Count 是群組中所選資料行的非 Null 值數目。</span><span class="sxs-lookup"><span data-stu-id="eb1be-173">Count is the number of non-null values that exist for the selected column in the group.</span></span>  
  
#### <a name="to-aggregate-results"></a><span data-ttu-id="eb1be-174">若要彙總結果</span><span class="sxs-lookup"><span data-stu-id="eb1be-174">To aggregate results</span></span>  
  
1.  <span data-ttu-id="eb1be-175">開啟 .XEL 檔案以檢視追蹤結果</span><span class="sxs-lookup"><span data-stu-id="eb1be-175">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eb1be-176"> 您也可以用滑鼠右鍵按一下工作階段名稱、選取 **[監看即時資料]**，然後按一下工具列上的 **[停止資料摘要]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="eb1be-176">You can also right click the session name, select **Watch Live Data**, and then click the **Stop Data Feed** button on the toolbar.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eb1be-177">由於彙總是對群組執行，因此您必須先將結果分組，然後才能執行彙總。</span><span class="sxs-lookup"><span data-stu-id="eb1be-177">Aggregation is run against a group, so you must group the results before you can perform the aggregation.</span></span>  
  
2.  <span data-ttu-id="eb1be-178">在 [擴充事件] 工具列上，按一下 **[彙總]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="eb1be-178">On the Extended Events toolbar, click the **Aggregate** button.</span></span>  
  
     <span data-ttu-id="eb1be-179">**[彙總]** 對話方塊隨即出現，其中顯示可用於彙總的資料行。</span><span class="sxs-lookup"><span data-stu-id="eb1be-179">The **Aggregation** dialog box appears displaying the columns available for aggregation.</span></span>  
  
3.  <span data-ttu-id="eb1be-180">在 **[彙總類型]** 下，從下拉式清單中選取彙總對應資料行的方式。</span><span class="sxs-lookup"><span data-stu-id="eb1be-180">Under **Aggregation Type**, select how you want to aggregate the corresponding column from the drop-down list.</span></span>  
  
4.  <span data-ttu-id="eb1be-181">在 **[彙總排序依據]** 方塊中，從下拉式清單中選取排序依據的資料行。</span><span class="sxs-lookup"><span data-stu-id="eb1be-181">In the **Sort aggregation by** box, select the column you want to sort by from the drop-down list.</span></span>  
  
5.  <span data-ttu-id="eb1be-182">選取 **[以遞增順序]** 選項，依遞增順序來排序彙總結果。</span><span class="sxs-lookup"><span data-stu-id="eb1be-182">Select the **In ascending order** option to sort the aggregation result in ascending order.</span></span>  
  
6.  <span data-ttu-id="eb1be-183">選取 **[以遞減順序]** 選項，依遞減順序來排序彙總結果。</span><span class="sxs-lookup"><span data-stu-id="eb1be-183">Select the **In descending order** option to sort the aggregation result in descending order.</span></span>  
  
7.  <span data-ttu-id="eb1be-184">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="eb1be-184">Click **OK**.</span></span>  
  
##  <a name="filter-results"></a><a name="Filter"></a><span data-ttu-id="eb1be-185">篩選結果</span><span class="sxs-lookup"><span data-stu-id="eb1be-185">Filter Results</span></span>  
 <span data-ttu-id="eb1be-186">您可以套用篩選以縮小追蹤視窗中顯示的追蹤結果範圍。</span><span class="sxs-lookup"><span data-stu-id="eb1be-186">You can apply filters to narrow down the trace results that are displayed in the trace window.</span></span> <span data-ttu-id="eb1be-187">顯示篩選包含時間篩選和進階篩選。</span><span class="sxs-lookup"><span data-stu-id="eb1be-187">The display filter includes a time filter and an advanced filter.</span></span> <span data-ttu-id="eb1be-188">時間篩選可用來依事件時間戳記篩選追蹤結果，而進階篩選可用來透過事件欄位和動作建構篩選條件。</span><span class="sxs-lookup"><span data-stu-id="eb1be-188">You use the time filter to filter the trace results by event timestamp, and you use the advanced filter to construct filter conditions using the event fields and actions.</span></span> <span data-ttu-id="eb1be-189">時間篩選和進階篩選之間有邏輯 AND 關聯性。</span><span class="sxs-lookup"><span data-stu-id="eb1be-189">There is an logical AND relationship between the Time and Advanced Filters.</span></span>  
  
#### <a name="to-create-a-filter"></a><span data-ttu-id="eb1be-190">若要建立篩選</span><span class="sxs-lookup"><span data-stu-id="eb1be-190">To create a filter</span></span>  
  
1.  <span data-ttu-id="eb1be-191">開啟 .XEL 檔案以檢視追蹤結果</span><span class="sxs-lookup"><span data-stu-id="eb1be-191">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eb1be-192"> 您也可以用滑鼠右鍵按一下工作階段名稱，然後選取 **[監看即時資料]**。</span><span class="sxs-lookup"><span data-stu-id="eb1be-192">You can also right click the session name, and then select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="eb1be-193">在追蹤結果視窗中選取要篩選的結果，然後在擴充事件工具列上按一下 **[篩選]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="eb1be-193">In the trace results window, select the results you want to filter, and then on the Extended Events toolbar, click the **Filters** button.</span></span>  
  
3.  <span data-ttu-id="eb1be-194">在 **[篩選]** 對話方塊中，選取 **[設定時間篩選]** 以透過拖曳滑動軸設定時間表來設定時間篩選。</span><span class="sxs-lookup"><span data-stu-id="eb1be-194">In the **Filters** dialog box, select **Set time filter** to set the time filter by dragging the slider bars to set the timeline.</span></span> <span data-ttu-id="eb1be-195">請注意，在移動滑動軸時，時間方塊會顯示對應的時間值。</span><span class="sxs-lookup"><span data-stu-id="eb1be-195">Note that when you move the slider bars, the time box displays the time value accordingly.</span></span> <span data-ttu-id="eb1be-196">您也可以在時間方塊中輸入時間，或從下拉式清單中選取時間。</span><span class="sxs-lookup"><span data-stu-id="eb1be-196">You can also enter the time in the time boxes, or you select it from the drop-down list.</span></span> <span data-ttu-id="eb1be-197">請注意，在輸入時間時，左側時間滑動軸會隨之移動。</span><span class="sxs-lookup"><span data-stu-id="eb1be-197">Note that when you enter the time, the left time slider will move accordingly.</span></span>  
  
4.  <span data-ttu-id="eb1be-198">在 [**其他篩選**] 區段中，套用篩選準則，**然後按一下 [** 套用]。</span><span class="sxs-lookup"><span data-stu-id="eb1be-198">In the **Additional Filters** section, apply your filter criteria, and then click **Apply**.</span></span> <span data-ttu-id="eb1be-199">完成建立篩選後，按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="eb1be-199">When your finished created the filter, click **OK**.</span></span>  
  
 <span data-ttu-id="eb1be-200">事件欄位與動作具有相同名稱時，則為特殊情況。</span><span class="sxs-lookup"><span data-stu-id="eb1be-200">A special situation is when an event field has the same name as an action.</span></span> <span data-ttu-id="eb1be-201">session_id 即為此情況的範例。</span><span class="sxs-lookup"><span data-stu-id="eb1be-201">An example of this would be session_id.</span></span> <span data-ttu-id="eb1be-202">有幾個事件會包括 session_id 欄位，您也可以加入 session_id 動作。</span><span class="sxs-lookup"><span data-stu-id="eb1be-202">There are several events that include a session_id field and you could also add the session_id action.</span></span> <span data-ttu-id="eb1be-203">已收集這兩項資訊，但擴充事件分析工具顯示方格會使用下列邏輯。</span><span class="sxs-lookup"><span data-stu-id="eb1be-203">Both pieces of information are collected, but the Extended Events profiler display grid uses the following logic.</span></span>  
  
-   <span data-ttu-id="eb1be-204">此顯示方格中只會顯示一個資料行的複本 (在此案例中為 session_id)。</span><span class="sxs-lookup"><span data-stu-id="eb1be-204">Only one copy of the column (session_id in this case) is shown in the grid display.</span></span>  
  
-   <span data-ttu-id="eb1be-205">如果資料中同時存在欄位和動作，則會顯示欄位值。</span><span class="sxs-lookup"><span data-stu-id="eb1be-205">If both fields and action exist in the data, the field value is shown.</span></span>  
  
-   <span data-ttu-id="eb1be-206">如果資料中只存在欄位或動作，則會顯示欄位或動作。</span><span class="sxs-lookup"><span data-stu-id="eb1be-206">If only field or action is exists in the data, the field or action is displayed.</span></span>  
  
-   <span data-ttu-id="eb1be-207">如果動作和欄位都不存在，則顯示 NULL。</span><span class="sxs-lookup"><span data-stu-id="eb1be-207">If neither action nor field exists, display NULL.</span></span>  
  
##  <a name="search-for-text-in-columns"></a><a name="Search"></a><span data-ttu-id="eb1be-208">搜尋資料行中的文字</span><span class="sxs-lookup"><span data-stu-id="eb1be-208">Search for Text in Columns</span></span>  
  
1.  <span data-ttu-id="eb1be-209">開啟 .XEL 檔案以檢視追蹤結果</span><span class="sxs-lookup"><span data-stu-id="eb1be-209">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eb1be-210"> 您也可以用滑鼠右鍵按一下工作階段名稱，然後選取 **[監看即時資料]**。</span><span class="sxs-lookup"><span data-stu-id="eb1be-210">You can also right click the session name, and then select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="eb1be-211">在 [擴充事件] 工具列上，按一下 **[尋找]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="eb1be-211">On the Extended Events toolbar, click the **Find** button.</span></span>  
  
3.  <span data-ttu-id="eb1be-212">在 **[在擴充事件中尋找]** 對話方塊的 **[尋找目標]** 方塊中，輸入要搜尋的文字。</span><span class="sxs-lookup"><span data-stu-id="eb1be-212">In the **Find in Extended Events** dialog box, in the **Find what** box, enter the text you want to search for.</span></span>  
  
     <span data-ttu-id="eb1be-213">您可以從下拉式清單中選取最後 20 個搜尋字串的其中之一。</span><span class="sxs-lookup"><span data-stu-id="eb1be-213">You can select one of your last 20 search strings from the drop-down list.</span></span>  
  
4.  <span data-ttu-id="eb1be-214">在 **[查詢]** 方塊中，從下拉式清單中選取要搜尋指定之文字的位置。</span><span class="sxs-lookup"><span data-stu-id="eb1be-214">In the **Look in** box, select the location in which to search for the specified text from the drop-down list.</span></span> <span data-ttu-id="eb1be-215">使用下列搜尋選項：</span><span class="sxs-lookup"><span data-stu-id="eb1be-215">Use the following options for searching:</span></span>  
  
    -   <span data-ttu-id="eb1be-216">**資料表資料行**。</span><span class="sxs-lookup"><span data-stu-id="eb1be-216">**Table Columns**.</span></span> <span data-ttu-id="eb1be-217">使用此選項可在追蹤視窗中搜尋所有可見資料行。</span><span class="sxs-lookup"><span data-stu-id="eb1be-217">Use this option to search all visible columns in the trace window.</span></span>  
  
    -   <span data-ttu-id="eb1be-218">**詳細資料**。</span><span class="sxs-lookup"><span data-stu-id="eb1be-218">**Details**.</span></span> <span data-ttu-id="eb1be-219">使用此選項，即可在開啟 [**在擴充事件中尋找**] 對話方塊之前選取的追蹤視窗中，搜尋所有資料行 (升級和未升級) 。</span><span class="sxs-lookup"><span data-stu-id="eb1be-219">Use this option to search all columns (promoted and non-promoted) in the trace window that were selected before opening the **Find in Extended Events** dialog box.</span></span>  
  
    -   <span data-ttu-id="eb1be-220">**\<Event column name>**.</span><span class="sxs-lookup"><span data-stu-id="eb1be-220">**\<Event column name>**.</span></span> <span data-ttu-id="eb1be-221">使用此選項可在下拉式清單的特定事件資料行中進行搜尋。</span><span class="sxs-lookup"><span data-stu-id="eb1be-221">Use this option to search in a specific event column from the drop-down list.</span></span>  
  
5.  <span data-ttu-id="eb1be-222">使用下列選項，指定定義搜尋的方式：</span><span class="sxs-lookup"><span data-stu-id="eb1be-222">Use the following options to specify how you want to define the search:</span></span>  
  
    1.  <span data-ttu-id="eb1be-223">**符合大小寫**。</span><span class="sxs-lookup"><span data-stu-id="eb1be-223">**Match case**.</span></span> <span data-ttu-id="eb1be-224">使用此選項可針對您在 [**尋找目標**] 方塊中所輸入的文字，顯示內容和大小寫都相符的搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="eb1be-224">Use this option to display the search results for the text you entered in the **Find what** box that are matched both by content and by case.</span></span>  
  
    2.  <span data-ttu-id="eb1be-225">**全字拼寫相符**。</span><span class="sxs-lookup"><span data-stu-id="eb1be-225">**Match whole word**.</span></span> <span data-ttu-id="eb1be-226">使用此選項即可僅顯示與輸入文字完全相符的搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="eb1be-226">Use this option to display only the search results for the text you entered that match complete words.</span></span>  
  
    3.  <span data-ttu-id="eb1be-227">**向上搜尋**。</span><span class="sxs-lookup"><span data-stu-id="eb1be-227">**Search up**.</span></span> <span data-ttu-id="eb1be-228">使用此選項可從游標位置開始搜尋至結果開頭。</span><span class="sxs-lookup"><span data-stu-id="eb1be-228">Use this option to search from your cursor location to the beginning of the results.</span></span>  
  
    4.  <span data-ttu-id="eb1be-229">**使用**。</span><span class="sxs-lookup"><span data-stu-id="eb1be-229">**Use**.</span></span> <span data-ttu-id="eb1be-230">使用此選項可解譯 **[尋找目標]** 方塊中輸入的特殊字元和規則運算式。</span><span class="sxs-lookup"><span data-stu-id="eb1be-230">Use this option to interpret the special characters and the regular expressions you entered in the **Find what** box.</span></span> <span data-ttu-id="eb1be-231">特殊字元包含萬用字元 (\*) 和 (?)，用於表示一個或多個字元。</span><span class="sxs-lookup"><span data-stu-id="eb1be-231">Special characters include the wildcard characters (\*) and (?) to represent one or more characters.</span></span> <span data-ttu-id="eb1be-232">規則運算式是用於定義搜尋文字模式的特殊標記法。</span><span class="sxs-lookup"><span data-stu-id="eb1be-232">Regular expressions are special notations used to define patterns of search text.</span></span>  
  
6.  <span data-ttu-id="eb1be-233">按一下 **[找下一個]** 可搜尋在 **[尋找目標]** 方塊中輸入的下一個文字。</span><span class="sxs-lookup"><span data-stu-id="eb1be-233">Click **Find Next** to search for the next text that you entered in the **Find what** box.</span></span>  
  
##  <a name="change-the-display-settings"></a><a name="ChangeDisplay"></a><span data-ttu-id="eb1be-234">變更顯示設定</span><span class="sxs-lookup"><span data-stu-id="eb1be-234">Change the Display Settings</span></span>  
 <span data-ttu-id="eb1be-235">您可以儲存資料行資訊 (資料行順序、合併資料行和資料行寬度)，並將追蹤結果的資訊篩選到「擴充事件」顯示設定檔案 (.viewsetting 檔案)。</span><span class="sxs-lookup"><span data-stu-id="eb1be-235">You can save column information (column order, merge column, and column width) and filter information of a trace result into an Extended Events display setting file (.viewsetting file).</span></span> <span data-ttu-id="eb1be-236">在儲存檔案後，您可以將它套用到追蹤結果以變更檢視。</span><span class="sxs-lookup"><span data-stu-id="eb1be-236">After saving the file, you can apply it to your trace results to change the view.</span></span>  
  
#### <a name="to-change-the-display-settings"></a><span data-ttu-id="eb1be-237">若要變更顯示設定</span><span class="sxs-lookup"><span data-stu-id="eb1be-237">To change the display settings</span></span>  
  
1.  <span data-ttu-id="eb1be-238">開啟 .XEL 檔案以檢視追蹤結果</span><span class="sxs-lookup"><span data-stu-id="eb1be-238">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eb1be-239"> 您也可以用滑鼠右鍵按一下工作階段名稱，然後選取 **[監看即時資料]**。</span><span class="sxs-lookup"><span data-stu-id="eb1be-239">You can also right click the session name, and then select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="eb1be-240">在追蹤結果視窗的「擴充事件」工具列或功能表上，選取 **[顯示設定]**。</span><span class="sxs-lookup"><span data-stu-id="eb1be-240">In the trace results window, on the Extended Events toolbar or menu, select **Display Settings**.</span></span>  
  
3.  <span data-ttu-id="eb1be-241">從下拉式清單中，選取下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="eb1be-241">From the drop-down list, select one of the following options:</span></span>  
  
    -   <span data-ttu-id="eb1be-242">**另存**新檔。</span><span class="sxs-lookup"><span data-stu-id="eb1be-242">**Save as**.</span></span> <span data-ttu-id="eb1be-243">將追蹤結果的資料行和篩選資訊儲存為 .viewsetting 檔案。</span><span class="sxs-lookup"><span data-stu-id="eb1be-243">Save the columns and filter information of a trace result to a .viewsetting file.</span></span>  
  
    -   <span data-ttu-id="eb1be-244">**開啟**。</span><span class="sxs-lookup"><span data-stu-id="eb1be-244">**Open**.</span></span> <span data-ttu-id="eb1be-245">開啟現有的 .viewsetting 檔案。</span><span class="sxs-lookup"><span data-stu-id="eb1be-245">Open an existing .viewsetting file.</span></span>  
  
    -   <span data-ttu-id="eb1be-246">**開啟 [最近**]。</span><span class="sxs-lookup"><span data-stu-id="eb1be-246">**Open recent**.</span></span> <span data-ttu-id="eb1be-247">開啟最近儲存的 .viewsetting 檔案。</span><span class="sxs-lookup"><span data-stu-id="eb1be-247">Open a recently saved .viewsetting file.</span></span>  
  
  
