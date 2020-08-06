---
title: 將互動式排序新增至資料表或矩陣 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10121"
- sql12.rtp.rptdesigner.textboxproperties.intrctvsort.f1
ms.assetid: 05819637-729b-4cf6-82de-91a99f184ec6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c0c453a8ea338ab9a09d7552c064f2eb85add985
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707146"
---
# <a name="add-interactive-sort-to-a-table-or-matrix-report-builder-and-ssrs"></a><span data-ttu-id="c2ebf-102">將互動式排序加入至資料表或矩陣 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="c2ebf-102">Add Interactive Sort to a Table or Matrix (Report Builder and SSRS)</span></span>
  <span data-ttu-id="c2ebf-103">加入互動式排序按鈕，讓使用者變更資料表和矩陣中資料列和資料行的排序次序。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-103">Add interactive sort buttons to enable users to change the sort order of rows and columns in tables and matrices.</span></span> <span data-ttu-id="c2ebf-104">系統僅能以支援使用者互動的轉譯格式支援此功能，例如 HTML。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-104">This feature is supported only in rendering formats that support user interaction, such as HTML.</span></span>  
  
 <span data-ttu-id="c2ebf-105">當您建立互動式排序按鈕時，必須指定要排序的項目、排序的依據，以及套用排序的範圍。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-105">When you create an interactive sort button, you must specify what to sort, what to sort by, and the scope to which to apply the sort.</span></span> <span data-ttu-id="c2ebf-106">例如，您可以依客戶的姓氏排序詳細資料列、依銷售額排序類別目錄群組中的子類別目錄群組值，或者依總計排序合併的類別目錄和子類別目錄群組值。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-106">For example, you can sort detail rows by customer last name, subcategory group values within a category group by sales, or category and subcategory group values combined by totals.</span></span>  
  
 <span data-ttu-id="c2ebf-107">當您檢視報表時，支援互動式排序的資料行，包含可變更為指示排序次序的箭頭圖示。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-107">When you view the report, columns that support interactive sorting have arrow icons that change to indicate the sort order.</span></span> <span data-ttu-id="c2ebf-108">第一次按下互動式排序按鈕時，項目會依遞增順序排序。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-108">The first time you click an interactive sort button, items are sorted in ascending order.</span></span> <span data-ttu-id="c2ebf-109">後續的點選則會在遞增和遞減的順序之間切換排序次序。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-109">Subsequent clicks toggle the sort order between ascending and descending order.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="in-this-article"></a><a name="BackToTop"></a> <span data-ttu-id="c2ebf-110">本文內容</span><span class="sxs-lookup"><span data-stu-id="c2ebf-110">In this Article</span></span>  
 [<span data-ttu-id="c2ebf-111">不使用群組排序資料表的詳細資料列</span><span class="sxs-lookup"><span data-stu-id="c2ebf-111">Sorting Detail Rows for a Table with No Groups</span></span>](#SortingDetailRows)  
  
 [<span data-ttu-id="c2ebf-112">排序資料表或矩陣的最上層父資料列群組</span><span class="sxs-lookup"><span data-stu-id="c2ebf-112">Sorting a Top Level Parent Row Group for a Table or Matrix</span></span>](#SortingTopLevelParent)  
  
 [<span data-ttu-id="c2ebf-113">排序群組的子群組或詳細資料列</span><span class="sxs-lookup"><span data-stu-id="c2ebf-113">Sorting Child Groups or Detail Rows for a Group</span></span>](#SortingChildGroups)  
  
 [<span data-ttu-id="c2ebf-114">根據複雜的群組運算式排序資料列</span><span class="sxs-lookup"><span data-stu-id="c2ebf-114">Sorting Rows Based on a Complex Group Expression</span></span>](#SortingMultipleRowGroups)  
  
 [<span data-ttu-id="c2ebf-115">同步處理多個資料區的排序次序</span><span class="sxs-lookup"><span data-stu-id="c2ebf-115">Synchronizing Sort Order for Multiple Data Regions</span></span>](#SynchronizingSortOrder)  
  
##  <a name="sorting-detail-rows-for-a-table-with-no-groups"></a><a name="SortingDetailRows"></a> <span data-ttu-id="c2ebf-116">不使用群組排序資料表的詳細資料列</span><span class="sxs-lookup"><span data-stu-id="c2ebf-116">Sorting Detail Rows for a Table with No Groups</span></span>  
 <span data-ttu-id="c2ebf-117">將互動式排序按鈕加入到資料行標頭，讓使用者按一下資料行標頭，並依該資料行中顯示的值，排序資料表中的詳細資料列。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-117">Add an interactive sort button to a column header to enable a user to click the column header and sort the details rows in a table by the value displayed in that column.</span></span>  
  
#### <a name="to-add-an-interactive-sort-button-to-a-column-header-to-sort-the-table-by-value"></a><span data-ttu-id="c2ebf-118">若要將互動式排序按鈕加入到資料行標頭以便依值排序資料表</span><span class="sxs-lookup"><span data-stu-id="c2ebf-118">To add an interactive sort button to a column header to sort the table by value</span></span>  
  
1.  <span data-ttu-id="c2ebf-119">在報表設計檢視中，在沒有群組的資料表，以滑鼠右鍵按一下資料行標題中要新增互動式排序按鈕的文字方塊，然後按一下 [文字方塊屬性]  。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-119">In report design view, in a table with no groups, right-click the text box in the column header to which you want to add an interactive sort button, and then click **Text Box Properties**.</span></span>  
  
2.  <span data-ttu-id="c2ebf-120">按一下 **[互動式排序]** 。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-120">Click **Interactive Sorting**.</span></span>  
  
3.  <span data-ttu-id="c2ebf-121">選取 **[啟用此文字方塊上的互動式排序]** 。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-121">Select **Enable interactive sorting on this text box**.</span></span>  
  
4.  <span data-ttu-id="c2ebf-122">在 **[選擇排序依據]** 中，按一下 **[詳細資料列]** 。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-122">In **Choose what to sort**, click **Detail rows**.</span></span>  
  
5.  <span data-ttu-id="c2ebf-123">在 **[排序依據]** 中，指定排序運算式。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-123">In **Sort by**, specify a sort expression.</span></span> <span data-ttu-id="c2ebf-124">從下拉式清單中，選取對應至您要定義排序動作之資料行的欄位 (例如，資料行標題名稱若是 "Title"，請選擇 `[Title]`)。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-124">From the drop-down list, select the field that corresponds to the column for which you are defining a sort action (for example, for a column heading named "Title", choose `[Title]`).</span></span> <span data-ttu-id="c2ebf-125">您必須指定排序運算式。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-125">Specifying a sort expression is required.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="c2ebf-126">針對您要加入互動式排序按鈕的每個資料行重複步驟 1-6。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-126">Repeat steps 1-6 for every column to which you want to add an interactive sort button.</span></span>  
  
 <span data-ttu-id="c2ebf-127">若要驗證排序動作，請按一下 **[執行]** 預覽報表，然後按一下互動式排序按鈕。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-127">To verify the sort action, click **Run** to preview the report, and then click the interactive sort buttons.</span></span>  
  
 <span data-ttu-id="c2ebf-128">![搭配 [回到頁首] 連結使用的箭頭圖示](../../2014-toc/media/uparrow16x16.gif "與 [回到頁首] 連結搭配使用的箭頭圖示") [[回到頁首]](#BackToTop)</span><span class="sxs-lookup"><span data-stu-id="c2ebf-128">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#BackToTop)</span></span>  
  
##  <a name="sorting-a-top-level-parent-row-group-for-a-table-or-matrix"></a><a name="SortingTopLevelParent"></a> <span data-ttu-id="c2ebf-129">排序資料表或矩陣的最上層父資料列群組</span><span class="sxs-lookup"><span data-stu-id="c2ebf-129">Sorting a Top-Level Parent Row Group for a Table or Matrix</span></span>  
 <span data-ttu-id="c2ebf-130">將互動式排序按鈕加入到資料行標頭，讓使用者按一下資料行標頭，並依該資料行中顯示的值，排序資料表或矩陣中的父群組資料列。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-130">Add an interactive sort button to a column header to enable a user to click the column header and sort the parent group rows in a table or matrix by the value displayed in that column.</span></span> <span data-ttu-id="c2ebf-131">子群組的順序會維持不變。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-131">The order of child groups remains unchanged.</span></span>  
  
#### <a name="to-add-an-interactive-sort-button-to-a-column-header-to-sort-groups"></a><span data-ttu-id="c2ebf-132">若要將互動式排序按鈕加入到資料行標頭以便排序群組</span><span class="sxs-lookup"><span data-stu-id="c2ebf-132">To add an interactive sort button to a column header to sort groups</span></span>  
  
1.  <span data-ttu-id="c2ebf-133">在報表設計檢視的資料表或矩陣中，以滑鼠右鍵按一下資料行標題中要新增互動式排序按鈕的群組文字方塊，然後按一下 [文字方塊屬性]  。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-133">In a table or matrix in report design view, right-click the text box in the column header for the group to which you want to add an interactive sort button, and then click **Text Box Properties**.</span></span>  
  
2.  <span data-ttu-id="c2ebf-134">按一下 **[互動式排序]** 。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-134">Click **Interactive Sorting**.</span></span>  
  
3.  <span data-ttu-id="c2ebf-135">選取 **[啟用此文字方塊上的互動式排序]** 。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-135">Select **Enable interactive sorting on this text box**.</span></span>  
  
4.  <span data-ttu-id="c2ebf-136">在 **[選擇排序依據]** 中，按一下 **[群組]** 。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-136">In **Choose what to sort**, click **Groups**.</span></span>  
  
5.  <span data-ttu-id="c2ebf-137">從下拉式清單中，選取您要排序之群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-137">From the drop-down list, select the name of the group that you are sorting.</span></span> <span data-ttu-id="c2ebf-138">針對以單一群組運算式為基礎的群組， **[排序依據]** 值會以群組運算式擴展。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-138">For groups based on simple group expressions, the **Sort by** value is populated with group expression.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c2ebf-139">如需複雜的群組運算式，請手動將 [排序依據]  運算式設定為群組運算式的相同值。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-139">For complex group expressions, manually set the **Sort by** expression to the same value as the group expression.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 <span data-ttu-id="c2ebf-140">若要驗證排序動作，請按一下 **[執行]** 預覽報表，然後按一下互動式排序按鈕。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-140">To verify the sort action, click **Run** to preview the report, and then click the interactive sort buttons.</span></span>  
  
 <span data-ttu-id="c2ebf-141">![搭配 [回到頁首] 連結使用的箭頭圖示](../../2014-toc/media/uparrow16x16.gif "與 [回到頁首] 連結搭配使用的箭頭圖示") [[回到頁首]](#BackToTop)</span><span class="sxs-lookup"><span data-stu-id="c2ebf-141">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#BackToTop)</span></span>  
  
##  <a name="sorting-child-groups-or-detail-rows-for-a-group"></a><a name="SortingChildGroups"></a> <span data-ttu-id="c2ebf-142">排序群組的子群組或詳細資料列</span><span class="sxs-lookup"><span data-stu-id="c2ebf-142">Sorting Child Groups or Detail Rows for a Group</span></span>  
 <span data-ttu-id="c2ebf-143">將互動式排序按鈕加入到群組標題資料列，讓使用者從父群組排序子群組的值，或針對最內部的子群組排序詳細資料列。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-143">Add an interactive sort button to a group header row to enable the user to sort the values of a child group from a parent group or to sort the detail rows for the innermost child group.</span></span>  
  
#### <a name="to-add-an-interactive-sort-button-to-a-text-box-in-a-group-row-header-to-sort-child-groups-or-detail-rows"></a><span data-ttu-id="c2ebf-144">若要將互動式排序按鈕加入到群組資料列標頭中的文字方塊以便排序子群組或詳細資料列</span><span class="sxs-lookup"><span data-stu-id="c2ebf-144">To add an interactive sort button to a text box in a group row header to sort child groups or detail rows</span></span>  
  
1.  <span data-ttu-id="c2ebf-145">在報表設計檢視中，以滑鼠右鍵按一下群組標題資料列中要新增互動式排序按鈕的文字方塊，然後按一下 [文字方塊屬性]  。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-145">In report design view, right-click the text box in the group header row to which you want to add an interactive sort button, and then click **Text Box Properties**.</span></span>  
  
2.  <span data-ttu-id="c2ebf-146">按一下 **[互動式排序]** 。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-146">Click **Interactive Sorting**.</span></span>  
  
3.  <span data-ttu-id="c2ebf-147">選取 **[啟用此文字方塊上的互動式排序]** 。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-147">Select **Enable interactive sorting on this text box**.</span></span>  
  
4.  <span data-ttu-id="c2ebf-148">在 **[選擇排序依據]** 中，按一下下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="c2ebf-148">In **Choose what to sort**, click one of the following options:</span></span>  
  
    -   <span data-ttu-id="c2ebf-149">**詳細資料** ：按一下 **[詳細資料]** 來排序詳細資料列。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-149">**Details** Click **Details** to sort the detail rows.</span></span> <span data-ttu-id="c2ebf-150">從下拉式清單中，選取排序所依據的欄位。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-150">From the drop-down list, select the field to sort by.</span></span> <span data-ttu-id="c2ebf-151">針對此選項，您必須指定排序所依據的值。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-151">For this option, you must specify the value to sort by.</span></span>  
  
    -   <span data-ttu-id="c2ebf-152">**群組** ：按一下 **[群組]** 來排序子群組值。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-152">**Groups** Click **Groups** to sort the child group values.</span></span> <span data-ttu-id="c2ebf-153">針對此選項，系統會從群組運算式自動填入 **[排序依據]** 運算式。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-153">For this option, the **Sort by** expression is automatically filled in from the group expression.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 <span data-ttu-id="c2ebf-154">若要驗證排序動作，請按一下 **[執行]** 預覽報表，然後按一下互動式排序按鈕。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-154">To verify the sort action, click **Run** to preview the report, and then click the interactive sort buttons.</span></span>  
  
 <span data-ttu-id="c2ebf-155">![搭配 [回到頁首] 連結使用的箭頭圖示](../../2014-toc/media/uparrow16x16.gif "與 [回到頁首] 連結搭配使用的箭頭圖示") [[回到頁首]](#BackToTop)</span><span class="sxs-lookup"><span data-stu-id="c2ebf-155">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#BackToTop)</span></span>  
  
##  <a name="sorting-rows-based-on-a-complex-group-expression"></a><a name="SortingMultipleRowGroups"></a> <span data-ttu-id="c2ebf-156">根據複雜的群組運算式排序資料列</span><span class="sxs-lookup"><span data-stu-id="c2ebf-156">Sorting Rows Based on a Complex Group Expression</span></span>  
 <span data-ttu-id="c2ebf-157">將互動式排序按鈕加入到資料行標頭，讓使用者按一下資料行標頭，並排序合併的父群組和子群組。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-157">Add an interactive sort button to a column header to enable a user to click the column header and sort the combined parent and child groups.</span></span> <span data-ttu-id="c2ebf-158">為達到此效果，您必須將群組運算式變更為兩個群組的複合。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-158">To achieve this affect, you must change the group expression to be a composite of both groups.</span></span> <span data-ttu-id="c2ebf-159">例如，假設矩陣會針對同時依色彩和大小分組的項目，顯示商店的存貨總數。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-159">For example, suppose a matrix displays inventory totals for a store for items grouped by both color and size.</span></span> <span data-ttu-id="c2ebf-160">若要根據色彩和大小的組合 (而不是個別針對色彩群組和大小群組) 排序資料列，您可以根據色彩和大小的組合定義群組。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-160">To sort the rows based on the combination of color and size, instead of having a separate group for color and a separate group for size, you can define a group based on the combination of color and size.</span></span> <span data-ttu-id="c2ebf-161">如需定義群組運算式的詳細資訊，請參閱[群組運算式範例 &#40;報表產生器和 SSRS&#41;](expression-examples-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-161">For more information about defining group expressions, see [Group Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="c2ebf-162">在下列程序中，這些條件會指定 Tablix 資料區域。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-162">In the following procedure, terms specify tablix data region areas.</span></span> <span data-ttu-id="c2ebf-163">如需詳細資訊，請參閱 [Tablix 資料區的區域 &#40;報表產生器及 SSRS&#41;](tablix-data-region-areas-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-163">For more information, see [Tablix Data Region Areas &#40;Report Builder and SSRS&#41;](tablix-data-region-areas-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="c2ebf-164">當您根據多個群組排序資料列時，不管資料行群組為何，您通常會想要查看已排序資料列的總數。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-164">Typically, when you sort rows based on multiple groups, you want to see totals for the sorted rows, regardless of column groups.</span></span> <span data-ttu-id="c2ebf-165">在這個程序，不會使用任何資料行群組。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-165">In this procedure, no column groups are used.</span></span> <span data-ttu-id="c2ebf-166">您可以加入矩陣並移除預設的資料行群組來開始。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-166">You start by adding a matrix and removing the default column group.</span></span> <span data-ttu-id="c2ebf-167">或者，您可以加入資料表並移除詳細資料群組來開始。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-167">Alternatively, you could start by adding a table and removing the details group.</span></span>  
  
#### <a name="to-add-an-interactive-sort-button-to-a-column-header-to-sort-multiple-groups"></a><span data-ttu-id="c2ebf-168">若要將互動式排序按鈕加入到資料行標頭以便排序多個群組</span><span class="sxs-lookup"><span data-stu-id="c2ebf-168">To add an interactive sort button to a column header to sort multiple groups</span></span>  
  
1.  <span data-ttu-id="c2ebf-169">在報表設計檢視中，加入矩陣。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-169">In report design view, add a matrix.</span></span>  
  
2.  <span data-ttu-id="c2ebf-170">將數值欄位拖曳到資料格以便將資料集連結到矩陣。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-170">Drag a numeric field to the data cell to link the dataset to the matrix.</span></span>  
  
     <span data-ttu-id="c2ebf-171">下一步，您將利用指定多個欄位的群組運算式建立群組，並建立一個用於顯示群組值的群組標頭。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-171">Next, you will create a group with a group expression that specifies multiple fields, and a group header to use to display the group values.</span></span>  
  
3.  <span data-ttu-id="c2ebf-172">確認已在設計介面上選取矩陣。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-172">Verify that the matrix is selected on the design surface.</span></span> <span data-ttu-id="c2ebf-173">[群組] 窗格會顯示預設的資料列和資料行群組。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-173">The Grouping pane displays a default row and column group.</span></span>  
  
4.  <span data-ttu-id="c2ebf-174">在 [資料列群組] 窗格中，以滑鼠右鍵按一下預設資料列群組，然後按一下 [編輯群組]  。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-174">In the Row Groups pane, right-click the default row group, and then click **Edit Group**.</span></span> <span data-ttu-id="c2ebf-175">**[群組屬性]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-175">The **Group Properties** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="c2ebf-176">在 **[名稱]** 中，將預設名稱取代成指定您分組所依據之多個群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-176">In **Name**, replace the default name with a name that specifies the multiple groups that you want to group by.</span></span>  
  
6.  <span data-ttu-id="c2ebf-177">在 [群組運算式]  的 [群組對象]  中，按一下 [運算式]\(**fx**) 按鈕，開啟 [運算式]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-177">In **Group expressions**, in **Group on**, click the Expression (**fx**) button to open the **Expression** dialog box.</span></span>  
  
7.  <span data-ttu-id="c2ebf-178">輸入指定分組依據之所有欄位的運算式。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-178">Type the expression that specifies all fields that you want to group by.</span></span> <span data-ttu-id="c2ebf-179">例如，下列群組運算式結合名稱為 Color 與名稱為 Size 的欄位： `=Fields!Color.Value & Fields!Size.Value`。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-179">For example, the following group expression combines a field named Color and a field named Size: `=Fields!Color.Value & Fields!Size.Value`.</span></span>  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     <span data-ttu-id="c2ebf-180">現在您已定義群組。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-180">You have now defined the group.</span></span> <span data-ttu-id="c2ebf-181">下一步，拖曳欄位以顯示矩陣的 Tablix 主體區域。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-181">Next, drag the fields to display to the tablix body area of the matrix.</span></span> <span data-ttu-id="c2ebf-182">將您在步驟 7 中選擇之分組依據的欄位加入到 Tablix 主體區域中，而且每個欄位都要加入到自己的資料行中。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-182">Add the fields that you chose to group by in step 7 to the tablix body area, each in its own column.</span></span>  
  
     <span data-ttu-id="c2ebf-183">針對這個狀況，不需要 Tablix 資料列群組區域中的第一個資料行。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-183">For this scenario, the first column in the tablix row groups area is not needed.</span></span> <span data-ttu-id="c2ebf-184">若要刪除資料行，以滑鼠右鍵按一下資料行標題，然後按一下 [刪除資料行]  。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-184">To delete the column, right-click the column header, and then click **Delete Columns**.</span></span> <span data-ttu-id="c2ebf-185">此時會出現一個對話方塊，詢問是否要刪除相關聯的群組。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-185">A dialog box asks whether to delete the associated groups.</span></span> <span data-ttu-id="c2ebf-186">按一下 **[否]** 。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-186">Click **No**.</span></span> <span data-ttu-id="c2ebf-187">資料列群組區域隨即刪除，而且只會保留 Tablix 主體區域。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-187">The row group area is deleted and only the tablix body area remains.</span></span>  
  
     <span data-ttu-id="c2ebf-188">下一步，您將移除預設的資料行群組。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-188">Next, you will remove the default column group.</span></span>  
  
9. <span data-ttu-id="c2ebf-189">在 [資料行群組] 窗格中，以滑鼠右鍵按一下預設資料行群組，然後按一下 [刪除群組]  。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-189">In the Column Groups pane, right-click the default column group, and then click **Delete Group**.</span></span> <span data-ttu-id="c2ebf-190">此時會出現一個對話方塊，詢問要刪除群組和相關的資料列和資料行，還是只刪除群組。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-190">A dialog box asks whether to delete the group and related rows and columns or the group only.</span></span> <span data-ttu-id="c2ebf-191">按一下 **[僅刪除群組]** 。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-191">Click **Delete group only**.</span></span> <span data-ttu-id="c2ebf-192">資料行群組隨即刪除，而且資料行群組區域也會刪除。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-192">The column group is deleted, and the column group area is deleted.</span></span> <span data-ttu-id="c2ebf-193">系統只會保留 Tablix 主體區域。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-193">Only the tablix body area remains.</span></span>  
  
     <span data-ttu-id="c2ebf-194">下一步，您會將互動式排序按鈕加入到跨越矩陣的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-194">Next, you will add an interactive sort button to the text box that spans the matrix.</span></span>  
  
10. <span data-ttu-id="c2ebf-195">按一下第一個資料列中的文字方塊，然後按一下 **[文字方塊屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-195">Click in the text box in the first row and then click **Text Box Properties**.</span></span>  
  
11. <span data-ttu-id="c2ebf-196">按一下 **[互動式排序]** 。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-196">Click **Interactive Sorting**.</span></span>  
  
12. <span data-ttu-id="c2ebf-197">選取 **[啟用此文字方塊上的互動式排序]** 。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-197">Select **Enable interactive sorting on this text box**.</span></span>  
  
13. <span data-ttu-id="c2ebf-198">在 **[選擇排序依據]** 中，按一下 **[群組]** 。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-198">In **Choose what to sort**, click **Groups**.</span></span>  
  
14. <span data-ttu-id="c2ebf-199">從下拉式清單中，選取您在步驟 5 中建立之群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-199">From the drop-down list, select the name of the group you created in step 5.</span></span> <span data-ttu-id="c2ebf-200">群組運算式會自動複製到 **[排序依據]** 文字方塊中。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-200">The group expression is automatically copied to the **Sort by** text box.</span></span>  
  
15. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     <span data-ttu-id="c2ebf-201">您已經將排序按鈕加入到文字方塊中。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-201">You have added the sort button to the text box.</span></span>  
  
16. <span data-ttu-id="c2ebf-202">(選擇性) 您可以在資料行中，隱藏顯示群組值的重複值。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-202">(Optional) You can suppress duplicate values in the columns that display group values.</span></span> <span data-ttu-id="c2ebf-203">在報表設計介面上，按一下顯示您要隱藏重複值之值的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-203">On the report design surface, click the text box that displays the value for which you want to hide repeating values.</span></span> <span data-ttu-id="c2ebf-204">在 [屬性] 窗格中，捲動至 [HideDuplicates]  ，然後從下拉式清單中選取連結至此矩陣的資料集名稱。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-204">In the Properties pane, scroll to **HideDuplicates**, and from the drop-down list, select the name of the dataset that is linked to this matrix.</span></span>  
  
 <span data-ttu-id="c2ebf-205">若要驗證排序動作，請按一下 **[執行]** 預覽報表，然後按一下互動式排序按鈕。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-205">To verify the sort action, click **Run** to preview the report, and then click the interactive sort button.</span></span> <span data-ttu-id="c2ebf-206">即使每個個別值都會顯示在其自己的資料行中，矩陣還是會依群組運算式的合計值排序。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-206">The matrix sorts by the combined values of the group expression, although each individual value displays in its own column.</span></span>  
  
 <span data-ttu-id="c2ebf-207">![搭配 [回到頁首] 連結使用的箭頭圖示](../../2014-toc/media/uparrow16x16.gif "與 [回到頁首] 連結搭配使用的箭頭圖示") [[回到頁首]](#BackToTop)</span><span class="sxs-lookup"><span data-stu-id="c2ebf-207">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#BackToTop)</span></span>  
  
##  <a name="synchronizing-sort-order-for-multiple-data-regions"></a><a name="SynchronizingSortOrder"></a> <span data-ttu-id="c2ebf-208">同步處理多個資料區的排序次序</span><span class="sxs-lookup"><span data-stu-id="c2ebf-208">Synchronizing Sort Order for Multiple Data Regions</span></span>  
 <span data-ttu-id="c2ebf-209">加入互動式排序按鈕，讓使用者按一下其中一個排序按鈕，然後排序多個資料區。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-209">Add an interactive sort button that enables a user to click one sort button and sort multiple data regions.</span></span> <span data-ttu-id="c2ebf-210">當您建立互動式排序按鈕時，可以指定是否要根據相同的報表資料集，同步處理多個資料區域的排序。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-210">When you create an interactive sort button, you can specify whether to synchronize the sort for multiple data regions based on the same report dataset.</span></span> <span data-ttu-id="c2ebf-211">例如，報表可能包含一個矩陣以及一個以圖形方式顯示資料的圖表。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-211">For example, a report might include a matrix and a chart that graphically displays the data.</span></span> <span data-ttu-id="c2ebf-212">當使用者在矩陣中變更資料列的排序次序時，此圖表會自動顯示相同的排序次序。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-212">When a user changes the sort order of the rows in the matrix, the chart automatically displays the same sort order.</span></span>  
  
 <span data-ttu-id="c2ebf-213">若要同步處理排序次序，您必須針對要排序的資料區域或群組使用相同的排序運算式，並將排序的範圍定義為兩個資料區域的互斥上階。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-213">To synchronize the sort order, you must use identical sort expressions for the data regions or groups to sort, and define the scope for the sort to be a mutual ancestor of both data regions.</span></span> <span data-ttu-id="c2ebf-214">互斥上階可以是連結兩個資料區域的資料集，也可以是兩個資料區域所出現的包含資料區域。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-214">The mutual ancestor can be either the dataset to which both data regions are linked or a containing data region within which both data regions appear.</span></span> <span data-ttu-id="c2ebf-215">例如，假設某個報表包含顯示相同資料集之資料，而且包含在清單中的矩陣和圖表。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-215">For example, assume a report has both a matrix and a chart that display data from the same dataset and that are contained in a list.</span></span> <span data-ttu-id="c2ebf-216">若要同步處理排序動作，您必須針對矩陣中的資料行指定互動式排序，並將範圍設定為清單。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-216">To synchronize the sort action, you must specify the interactive sort on a column in the matrix and set the scope to the list.</span></span> <span data-ttu-id="c2ebf-217">當使用者排序矩陣時，圖表也會進行排序。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-217">When the user sorts the matrix, the chart is also sorted.</span></span>  
  
#### <a name="to-synchronize-sort-order-with-a-chart-for-an-interactive-sort-button-on-a-matrix-data-region"></a><span data-ttu-id="c2ebf-218">若要針對矩陣資料區同步處理排序次序與互動式排序按鈕的圖表</span><span class="sxs-lookup"><span data-stu-id="c2ebf-218">To synchronize sort order with a chart for an interactive sort button on a matrix data region</span></span>  
  
1.  <span data-ttu-id="c2ebf-219">在報表設計檢視中，將矩陣加入至報表。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-219">In report design view, add a matrix to the report.</span></span>  
  
2.  <span data-ttu-id="c2ebf-220">將數值資料集欄位加入到矩陣資料格，例如，代表數量或銷售額的欄位。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-220">Add a numeric dataset field to the matrix data cell, for example, a field representing quantity or sales.</span></span>  
  
3.  <span data-ttu-id="c2ebf-221">定義資料列群組。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-221">Define a row group.</span></span> <span data-ttu-id="c2ebf-222">根據預設，群組的排序次序會設定為與群組運算式相同的運算式。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-222">By default, the sort order for the group is set to the same expression as the group expression.</span></span>  
  
4.  <span data-ttu-id="c2ebf-223">將圖表加入至報表，例如，圓形圖。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-223">Add a chart to the report, for example, a pie chart.</span></span>  
  
5.  <span data-ttu-id="c2ebf-224">將您在步驟 2 中選擇的欄位拖曳至 **[圖表資料]** 窗格的 **[值]** 區域。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-224">Drag the field you chose in step 2 to the **Value** area of the **Chart Data** pane.</span></span>  
  
6.  <span data-ttu-id="c2ebf-225">將您選擇用於分組所依據的欄位拖曳至 **[類別目錄群組]** 區域。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-225">Drag the field you chose to group by to the **Category Groups** area.</span></span>  
  
     <span data-ttu-id="c2ebf-226">矩陣資料列群組與圖表類別目錄群組的群組運算式必須相同。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-226">The group expression for the matrix row group and the chart category group must be identical.</span></span>  
  
7.  <span data-ttu-id="c2ebf-227">以滑鼠右鍵按一下類別目錄群組，然後按一下 [類別目錄群組屬性]  。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-227">Right-click the category group, and then click **Category Group Properties**.</span></span>  
  
8.  <span data-ttu-id="c2ebf-228">按一下 **[排序]** 。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-228">Click **Sorting**.</span></span>  
  
9. <span data-ttu-id="c2ebf-229">按一下 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-229">Click **Add**.</span></span> <span data-ttu-id="c2ebf-230">新的排序資料列就會加入到排序選項方格中。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-230">A new sort row is added to the sorting options grid.</span></span>  
  
10. <span data-ttu-id="c2ebf-231">在 [排序依據] 的下拉式清單中，選擇您在步驟 6 中選擇，當做分組依據的相同欄位。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-231">In Sort by, from the drop-down list, choose the same field that you chose in step 6 to group by.</span></span>  
  
11. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
12. <span data-ttu-id="c2ebf-232">在矩陣中，以滑鼠右鍵按一下資料行標題中要新增互動式排序按鈕的文字方塊，然後按一下 [文字方塊屬性]  。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-232">In the matrix, right-click the text box in the column header to which you want to add an interactive sort button, and then click **Text Box Properties**.</span></span>  
  
13. <span data-ttu-id="c2ebf-233">按一下 **[互動式排序]** 。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-233">Click **Interactive Sorting**.</span></span>  
  
14. <span data-ttu-id="c2ebf-234">選取 **[啟用此文字方塊上的互動式排序]** 。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-234">Select **Enable interactive sorting on this text box**.</span></span>  
  
15. <span data-ttu-id="c2ebf-235">在 **[選擇排序依據]** 中，按一下 **[群組]** 。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-235">In **Choose what to sort**, click **Groups**.</span></span>  
  
16. <span data-ttu-id="c2ebf-236">從 [群組]  底下的下拉式清單中，選取您要排序的群組名稱。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-236">From the drop-down list under **Groups**, select the name of the group that you are sorting.</span></span> <span data-ttu-id="c2ebf-237">此群組的群組運算式會針對 **[排序依據]** 值自動設定。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-237">The group expression for this group is automatically set for the **Sort by** value.</span></span>  
  
17. <span data-ttu-id="c2ebf-238">選取 **[同時套用此排序至下列範圍內的其他群組及資料區域]** 。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-238">Select **Also apply this sort to other groups and data regions within**.</span></span> <span data-ttu-id="c2ebf-239">在文字方塊中，輸入資料集的名稱，例如 "SalesData"。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-239">In the text box, type the name of the dataset, for example, "SalesData".</span></span>  
  
18. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 <span data-ttu-id="c2ebf-240">若要驗證排序動作，請按一下 **[執行]** 預覽報表，然後按一下互動式排序按鈕。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-240">To verify the sort action, click **Run** to preview the report, and then click the interactive sort button.</span></span> <span data-ttu-id="c2ebf-241">即使每個個別值都會顯示在其自己的資料行中，矩陣還是會依群組運算式的合計值排序。</span><span class="sxs-lookup"><span data-stu-id="c2ebf-241">The matrix sorts by the combined values of the group expression, although each individual value displays in its own column.</span></span>  
  
 <span data-ttu-id="c2ebf-242">![搭配 [回到頁首] 連結使用的箭頭圖示](../../2014-toc/media/uparrow16x16.gif "與 [回到頁首] 連結搭配使用的箭頭圖示") [[回到頁首]](#BackToTop)</span><span class="sxs-lookup"><span data-stu-id="c2ebf-242">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [Back to Top](#BackToTop)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2ebf-243">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2ebf-243">See Also</span></span>  
 <span data-ttu-id="c2ebf-244">[篩選、分組和排序資料 &#40;報表產生器及 SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c2ebf-244">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c2ebf-245">[互動式排序 &#40;報表產生器及 SSRS&#41;](interactive-sort-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c2ebf-245">[Interactive Sort &#40;Report Builder and SSRS&#41;](interactive-sort-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c2ebf-246">[在資料區中排序資料 &#40;報表產生器及 SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c2ebf-246">[Sort Data in a Data Region &#40;Report Builder and SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="c2ebf-247">探索 Tablix 資料區的彈性 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="c2ebf-247">Exploring the Flexibility of a Tablix Data Region &#40;Report Builder and SSRS&#41;</span></span>](exploring-the-flexibility-of-a-tablix-data-region-report-builder-and-ssrs.md)  
  
  
