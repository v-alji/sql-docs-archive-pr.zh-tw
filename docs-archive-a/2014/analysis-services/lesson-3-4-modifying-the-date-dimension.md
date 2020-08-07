---
title: 修改日期維度 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4689d780-4bf6-4cf8-8fde-eb3f15dd668a
author: minewiskan
ms.author: owend
ms.openlocfilehash: b4978e9fe3acd93ddfdca707d2c2353bf171ba12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597437"
---
# <a name="modifying-the-date-dimension"></a><span data-ttu-id="e6f24-102">修改 Date 維度</span><span class="sxs-lookup"><span data-stu-id="e6f24-102">Modifying the Date Dimension</span></span>
  <span data-ttu-id="e6f24-103">在這個主題的工作中，您會建立一個使用者定義階層，以及變更針對 [日期]、[月]、[日曆季] 和 [日曆半年] 屬性所顯示的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="e6f24-103">In the tasks in this topic, you create a user-defined hierarchy and change the member names that are displayed for the Date, Month, Calendar Quarter, and Calendar Semester attributes.</span></span> <span data-ttu-id="e6f24-104">您也會定義屬性的複合索引鍵、控制維度成員的排序次序，以及定義屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="e6f24-104">You also define composite keys for attributes, control the sort order of dimension members, and define attribute relationships.</span></span>  
  
## <a name="adding-a-named-calculation"></a><span data-ttu-id="e6f24-105">加入具名計算</span><span class="sxs-lookup"><span data-stu-id="e6f24-105">Adding a Named Calculation</span></span>  
 <span data-ttu-id="e6f24-106">具名計算是以導出資料行表示的 SQL 運算式，您可以將它加入資料來源檢視的資料表中。</span><span class="sxs-lookup"><span data-stu-id="e6f24-106">You can add a named calculation, which is a SQL expression that is represented as a calculated column, to a table in a data source view.</span></span> <span data-ttu-id="e6f24-107">這個運算式以資料表的資料行呈現及運作。</span><span class="sxs-lookup"><span data-stu-id="e6f24-107">The expression appears and behaves as a column in the table.</span></span> <span data-ttu-id="e6f24-108">具名計算可讓您延伸資料來源檢視中現有資料表的關聯式結構描述，而不必修改基礎資料來源中的資料表。</span><span class="sxs-lookup"><span data-stu-id="e6f24-108">Named calculations enable you to extend the relational schema of existing tables in a data source view without modifying the table in the underlying data source.</span></span> <span data-ttu-id="e6f24-109">如需詳細資訊，請參閱[在資料來源 View 中定義指名的計算 &#40;Analysis Services&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)</span><span class="sxs-lookup"><span data-stu-id="e6f24-109">For more information, see [Define Named Calculations in a Data Source View &#40;Analysis Services&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)</span></span>  
  
#### <a name="to-add-a-named-calculation"></a><span data-ttu-id="e6f24-110">加入具名計算</span><span class="sxs-lookup"><span data-stu-id="e6f24-110">To add a named calculation</span></span>  
  
1.  <span data-ttu-id="e6f24-111">若要開啟 [Adventure Works DW 2012]\*\*\*\* 資料來源檢視，請在方案總管的 [資料來源檢視]\*\*\*\* 資料夾中按兩下該檢視。</span><span class="sxs-lookup"><span data-stu-id="e6f24-111">To open the **Adventure Works DW 2012** data source view, double-click it in the **Data Source Views** folder in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="e6f24-112">在靠近 [**資料表**] 窗格底部的地方，以滑鼠右鍵按一下 [] `Date` ，然後按一下 [**新增命名計算**]。</span><span class="sxs-lookup"><span data-stu-id="e6f24-112">Near the bottom of the **Tables** pane, right-click `Date`, and then click **New Named Calculation**.</span></span>  
  
3.  <span data-ttu-id="e6f24-113">在 [**建立命名計算**] 對話方塊中，于 [資料行名稱] 方塊中輸入，然後在 `SimpleDate` [運算式] 方塊中輸入或複製並貼上下列**Column name** `DATENAME` 語句： **Expression**</span><span class="sxs-lookup"><span data-stu-id="e6f24-113">In the **Create Named Calculation** dialog box, type `SimpleDate` in the **Column name** box, and then type or copy and paste the following `DATENAME` statement in the **Expression** box:</span></span>  
  
    ```  
    DATENAME(mm, FullDateAlternateKey) + ' ' +  
    DATENAME(dd, FullDateAlternateKey) + ', ' +  
    DATENAME(yy, FullDateAlternateKey)  
    ```  
  
     <span data-ttu-id="e6f24-114">這個 `DATENAME` 陳述式會從 FullDateAlternateKey 資料行中擷取年份、月份和日期等值。</span><span class="sxs-lookup"><span data-stu-id="e6f24-114">The `DATENAME` statement extracts the year, month, and day values from the FullDateAlternateKey column.</span></span> <span data-ttu-id="e6f24-115">您將使用這個新的資料行當做 FullDateAlternateKey 屬性的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="e6f24-115">You will use this new column as the displayed name for the FullDateAlternateKey attribute.</span></span>  
  
4.  <span data-ttu-id="e6f24-116">按一下 **[確定]**，然後 `Date` 在 [**資料表**] 窗格中展開。</span><span class="sxs-lookup"><span data-stu-id="e6f24-116">Click **OK**, and then expand `Date` in the **Tables** pane.</span></span>  
  
     <span data-ttu-id="e6f24-117">`SimpleDate`已命名的計算會出現在 [日期] 資料表的資料行清單中，並以圖示表示它是名為的計算。</span><span class="sxs-lookup"><span data-stu-id="e6f24-117">The `SimpleDate` named calculation appears in the list of columns in the Date table, with an icon that indicates that it is a named calculation.</span></span>  
  
5.  <span data-ttu-id="e6f24-118">在 [檔案] 功能表上，按一下 [全部儲存]。</span><span class="sxs-lookup"><span data-stu-id="e6f24-118">On the **File** menu, click **Save All**.</span></span>  
  
6.  <span data-ttu-id="e6f24-119">在 [**資料表**] 窗格中，以滑鼠右鍵按一下 [] `Date` ，然後按一下 [**流覽資料**]。</span><span class="sxs-lookup"><span data-stu-id="e6f24-119">In the **Tables** pane, right-click `Date`, and then click **Explore Data**.</span></span>  
  
7.  <span data-ttu-id="e6f24-120">向右捲動以檢閱 [Explore Date Table (瀏覽日期資料表)]\*\*\*\* 檢視中的最後一個資料行。</span><span class="sxs-lookup"><span data-stu-id="e6f24-120">Scroll to the right to review the last column in the **Explore Date Table** view.</span></span>  
  
     <span data-ttu-id="e6f24-121">請注意， `SimpleDate` 資料行會出現在 [資料來源] 視圖中，會正確地從基礎資料來源中的數個數據行串連資料，而不會修改原始資料來源。</span><span class="sxs-lookup"><span data-stu-id="e6f24-121">Notice that the `SimpleDate` column appears in the data source view, correctly concatenating data from several columns from the underlying data source, without modifying the original data source.</span></span>  
  
8.  <span data-ttu-id="e6f24-122">關閉 [Explore Date Table (瀏覽日期資料表)]\*\*\*\* 檢視。</span><span class="sxs-lookup"><span data-stu-id="e6f24-122">Close the **Explore Date Table** view.</span></span>  
  
## <a name="using-the-named-calculation-for-member-names"></a><span data-ttu-id="e6f24-123">針對成員名稱使用具名計算</span><span class="sxs-lookup"><span data-stu-id="e6f24-123">Using the Named Calculation for Member Names</span></span>  
 <span data-ttu-id="e6f24-124">在資料來源檢視中建立具名計算之後，您就可以使用此具名計算當做屬性 (Attribute) 的屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="e6f24-124">After you create a named calculation in the data source view, you can use the named calculation as a property of an attribute.</span></span>  
  
#### <a name="to-use-the-named-calculation-for-member-names"></a><span data-ttu-id="e6f24-125">針對成員名稱使用具名計算</span><span class="sxs-lookup"><span data-stu-id="e6f24-125">To use the named calculation for member names</span></span>  
  
1.  <span data-ttu-id="e6f24-126">針對 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中的 [日期] 維度，開啟 [維度設計師]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6f24-126">Open **Dimension Designer** for the Date dimension in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="e6f24-127">若要這麼做，請 `Date` 在**方案總管**的 [**維度**] 節點中，按兩下維度。</span><span class="sxs-lookup"><span data-stu-id="e6f24-127">To do this, double-click the `Date` dimension in the **Dimensions** node of **Solution Explorer**.</span></span>  
  
2.  <span data-ttu-id="e6f24-128">在 [維度結構]\*\*\*\* 索引標籤的 [屬性]\*\*\*\* 窗格中，按一下 [日期索引鍵]\*\*\*\* 屬性。</span><span class="sxs-lookup"><span data-stu-id="e6f24-128">In the **Attributes** pane of the **Dimension Structure** tab, click the **Date Key** attribute.</span></span>  
  
3.  <span data-ttu-id="e6f24-129">如果 [屬性] 視窗未開啟，請開啟 [屬性] 視窗，然後按一下標題列上的 [自動隱藏]\*\*\*\* 按鈕，如此它就會保持開啟狀態。</span><span class="sxs-lookup"><span data-stu-id="e6f24-129">If the Properties window is not open, open the Properties window, and then click the **Auto Hide** button on the title bar so that it stays open.</span></span>  
  
4.  <span data-ttu-id="e6f24-130">按一下視窗底部附近的 [ **NameColumn** ] 屬性欄位，然後按一下省略號的 [流覽 (**...** ]) ] 按鈕，開啟 [**名稱資料行**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e6f24-130">Click the **NameColumn** property field near the bottom of the window, and then click the ellipsis browse (**...**) button to open the **Name Column** dialog box.</span></span>  
  
5.  <span data-ttu-id="e6f24-131">選取 `SimpleDate` [**來源資料行**] 清單底部的，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e6f24-131">Select `SimpleDate` at the bottom of the **Source column** list, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="e6f24-132">在 [檔案] 功能表上，按一下 [全部儲存]。</span><span class="sxs-lookup"><span data-stu-id="e6f24-132">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="creating-a-hierarchy"></a><span data-ttu-id="e6f24-133">建立階層</span><span class="sxs-lookup"><span data-stu-id="e6f24-133">Creating a Hierarchy</span></span>  
 <span data-ttu-id="e6f24-134">您可以將屬性從 [屬性]\*\*\*\* 窗格拖曳到 [階層]\*\*\*\* 窗格，藉以建立新的階層。</span><span class="sxs-lookup"><span data-stu-id="e6f24-134">You can create a new hierarchy by dragging an attribute from the **Attributes** pane to the **Hierarchies** pane.</span></span>  
  
#### <a name="to-create-a-hierarchy"></a><span data-ttu-id="e6f24-135">若要建立階層</span><span class="sxs-lookup"><span data-stu-id="e6f24-135">To create a hierarchy</span></span>  
  
1.  <span data-ttu-id="e6f24-136">在維度之維度設計師的 [**維度結構**] 索引標籤中 `Date` ，將 [**日曆年度**] 屬性從 [ **Hierarchies** **屬性**] 窗格拖曳到 [階層] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="e6f24-136">In **Dimension Structure** tab of the Dimension Designer for the `Date` dimension, drag the **Calendar Year** attribute from the **Attributes** pane into the **Hierarchies** pane.</span></span>  
  
2.  <span data-ttu-id="e6f24-137">將 [日曆半年度]\*\*\*\* 屬性從 [屬性]\*\*\*\* 窗格拖曳到 [階層]\*\*\*\* 窗格的 [\<new level>]\*\*\*\* 資料格中 (位於 [日曆年度]\*\*\*\* 層級底下)。</span><span class="sxs-lookup"><span data-stu-id="e6f24-137">Drag the **Calendar Semester** attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the **Calendar Year** level.</span></span>  
  
3.  <span data-ttu-id="e6f24-138">將 [日曆季]\*\*\*\* 屬性從 [屬性]\*\*\*\* 窗格拖曳到 [階層]\*\*\*\* 窗格的 [\<new level>]\*\*\*\* 資料格中 (位於 [日曆半年度]\*\*\*\* 層級底下)。</span><span class="sxs-lookup"><span data-stu-id="e6f24-138">Drag the **Calendar Quarter** attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the **Calendar Semester** level.</span></span>  
  
4.  <span data-ttu-id="e6f24-139">將 [英文月份]\*\*\*\* 屬性從 [屬性]\*\*\*\* 窗格拖曳到 [階層]\*\*\*\* 窗格的 [\<new level>]\*\*\*\* 資料格中 (位於 [日曆季]\*\*\*\* 層級底下)。</span><span class="sxs-lookup"><span data-stu-id="e6f24-139">Drag the **English Month Name** attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the **Calendar Quarter** level.</span></span>  
  
5.  <span data-ttu-id="e6f24-140">將 [日期索引鍵]\*\*\*\* 屬性從 [屬性]\*\*\*\* 窗格拖曳到 [階層]\*\*\*\* 窗格的 [\<new level>]\*\*\*\* 資料格中 (位於 [英文月份]\*\*\*\* 層級底下)。</span><span class="sxs-lookup"><span data-stu-id="e6f24-140">Drag the **Date Key** attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the **English Month Name** level.</span></span>  
  
6.  <span data-ttu-id="e6f24-141">**在 [階層] 窗格**中，以滑鼠右鍵按一下階層階層的標題列，**按一下 [** **重新命名**]，然後輸入 `Calendar Date` 。</span><span class="sxs-lookup"><span data-stu-id="e6f24-141">In the **Hierarchies** pane, right-click the title bar of the **Hierarchy** hierarchy, click **Rename**, and then type `Calendar Date`.</span></span>  
  
7.  <span data-ttu-id="e6f24-142">藉由使用滑鼠右鍵操作功能表，在階層中 `Calendar Date` ，將 [**英文月份**] 層級重新命名為 `Calendar Month` ，然後將 [**日期索引鍵**] 層級重新命名為 `Date` 。</span><span class="sxs-lookup"><span data-stu-id="e6f24-142">By using the right-click context menu, in the `Calendar Date` hierarchy, rename the **English Month Name** level to `Calendar Month`, and then rename the **Date Key** level to `Date`.</span></span>  
  
8.  <span data-ttu-id="e6f24-143">從 [屬性]\*\*\*\* 窗格中刪除 [完整日期替代索引鍵]\*\*\*\* 屬性，因為您將不會再使用它。</span><span class="sxs-lookup"><span data-stu-id="e6f24-143">Delete the **Full Date Alternate Key** attribute from the **Attributes** pane because you will not be using it.</span></span> <span data-ttu-id="e6f24-144">在 [刪除物件]\*\*\*\* 確認視窗中按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6f24-144">Click **OK** in the **Delete Objects** confirmation window.</span></span>  
  
9. <span data-ttu-id="e6f24-145">在 [檔案] 功能表上，按一下 [全部儲存]。</span><span class="sxs-lookup"><span data-stu-id="e6f24-145">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="defining-attribute-relationships"></a><span data-ttu-id="e6f24-146">定義屬性關聯性</span><span class="sxs-lookup"><span data-stu-id="e6f24-146">Defining Attribute Relationships</span></span>  
 <span data-ttu-id="e6f24-147">如果基礎資料支援屬性關聯性，您就應該定義屬性之間的屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="e6f24-147">If the underlying data supports it, you should define attribute relationships between attributes.</span></span> <span data-ttu-id="e6f24-148">定義屬性關聯性可加快維度、資料分割和查詢處理的速度。</span><span class="sxs-lookup"><span data-stu-id="e6f24-148">Defining attribute relationships speeds up dimension, partition, and query processing.</span></span>  
  
#### <a name="to-define-attribute-relationships"></a><span data-ttu-id="e6f24-149">定義屬性關聯性</span><span class="sxs-lookup"><span data-stu-id="e6f24-149">To define attribute relationships</span></span>  
  
1.  <span data-ttu-id="e6f24-150">在維度的**維度設計師**中 `Date` ，按一下 [**屬性關聯**性] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e6f24-150">In the **Dimension Designer** for the `Date` dimension, click the **Attribute Relationships** tab.</span></span>  
  
2.  <span data-ttu-id="e6f24-151">在圖表中，以滑鼠右鍵按一下 [英文月份]\*\*\*\* 屬性，然後按一下 [新增屬性關聯性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6f24-151">In the diagram, right-click the **English Month Name** attribute, and then click **New Attribute Relationship**.</span></span>  
  
3.  <span data-ttu-id="e6f24-152">在 [建立屬性關聯性]\*\*\*\* 對話方塊中，[來源屬性]\*\*\*\* 是 [英文月份]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6f24-152">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **English Month Name**.</span></span> <span data-ttu-id="e6f24-153">將 [相關屬性]\*\*\*\* 設定為 [日曆季]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6f24-153">Set the **Related Attribute** to **Calendar Quarter**.</span></span>  
  
4.  <span data-ttu-id="e6f24-154">在 [關聯性類型]\*\*\*\* 清單中，將關聯性類型設定為 [固定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6f24-154">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
     <span data-ttu-id="e6f24-155">此關聯性類型是 [固定]\*\*\*\*，因為成員之間的關聯性不會隨著時間而變更。</span><span class="sxs-lookup"><span data-stu-id="e6f24-155">The relationship type is **Rigid** because relationships between the members will not change over time.</span></span>  
  
5.  <span data-ttu-id="e6f24-156">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="e6f24-156">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="e6f24-157">在圖表中，以滑鼠右鍵按一下 [日曆季]\*\*\*\* 屬性，然後按一下 [新增屬性關聯性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6f24-157">In the diagram, right-click the **Calendar Quarter** attribute, and then click **New Attribute Relationship**.</span></span>  
  
7.  <span data-ttu-id="e6f24-158">在 [建立屬性關聯性]\*\*\*\* 對話方塊中，[來源屬性]\*\*\*\* 是 [日曆季]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6f24-158">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Calendar Quarter**.</span></span> <span data-ttu-id="e6f24-159">將 [相關屬性]\*\*\*\* 設定為 [日曆半年度]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6f24-159">Set the **Related Attribute** to **Calendar Semester**.</span></span>  
  
8.  <span data-ttu-id="e6f24-160">在 [關聯性類型]\*\*\*\* 清單中，將關聯性類型設定為 [固定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6f24-160">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
9. <span data-ttu-id="e6f24-161">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="e6f24-161">Click **OK**.</span></span>  
  
10. <span data-ttu-id="e6f24-162">在圖表中，以滑鼠右鍵按一下 [日曆半年度]\*\*\*\* 屬性，然後按一下 [新增屬性關聯性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6f24-162">In the diagram, right-click the **Calendar Semester** attribute, and then click **New Attribute Relationship**.</span></span>  
  
11. <span data-ttu-id="e6f24-163">在 [建立屬性關聯性]\*\*\*\* 對話方塊中，[來源屬性]\*\*\*\* 是 [日曆半年度]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6f24-163">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Calendar Semester**.</span></span> <span data-ttu-id="e6f24-164">將 [相關屬性]\*\*\*\* 設定為 [日曆年度]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6f24-164">Set the **Related Attribute** to **Calendar Year**.</span></span>  
  
12. <span data-ttu-id="e6f24-165">在 [關聯性類型]\*\*\*\* 清單中，將關聯性類型設定為 [固定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6f24-165">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
13. <span data-ttu-id="e6f24-166">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="e6f24-166">Click **OK**.</span></span>  
  
14. <span data-ttu-id="e6f24-167">在 [檔案] 功能表上，按一下 [全部儲存]。</span><span class="sxs-lookup"><span data-stu-id="e6f24-167">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="providing-unique-dimension-member-names"></a><span data-ttu-id="e6f24-168">提供唯一的維度成員名稱</span><span class="sxs-lookup"><span data-stu-id="e6f24-168">Providing Unique Dimension Member Names</span></span>  
 <span data-ttu-id="e6f24-169">在這項工作中，您將建立 [EnglishMonthName]\*\*\*\*、[CalendarQuarter]\*\*\*\* 和 [CalendarSemester]\*\*\*\* 屬性所使用的使用者易記名稱資料行。</span><span class="sxs-lookup"><span data-stu-id="e6f24-169">In this task, you will create user-friendly name columns that will be used by the **EnglishMonthName**, **CalendarQuarter**, and **CalendarSemester** attributes.</span></span>  
  
#### <a name="to-provide-unique-dimension-member-names"></a><span data-ttu-id="e6f24-170">提供唯一的維度成員名稱</span><span class="sxs-lookup"><span data-stu-id="e6f24-170">To provide unique dimension member names</span></span>  
  
1.  <span data-ttu-id="e6f24-171">若要切換至\*\* [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 2012**資料來源，請在方案總管的**資料來源 Views\*\*資料夾中，按兩下它。</span><span class="sxs-lookup"><span data-stu-id="e6f24-171">To switch to the **[!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 2012** data source view, double-click it in the **Data Source Views** folder in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="e6f24-172">在 [**資料表**] 窗格中，以滑鼠右鍵按一下 [] `Date` ，然後按一下 [**新增命名計算**]。</span><span class="sxs-lookup"><span data-stu-id="e6f24-172">In the **Tables** pane, right-click `Date`, and then click **New Named Calculation**.</span></span>  
  
3.  <span data-ttu-id="e6f24-173">在 [**建立命名計算**] 對話方塊中，于 [資料行名稱] 方塊中輸入，然後在 `MonthName` [**運算式**] 方塊中輸入或複製並貼上下列語句： **Column name**</span><span class="sxs-lookup"><span data-stu-id="e6f24-173">In the **Create Named Calculation** dialog box, type `MonthName` in the **Column name** box, and then type or copy and paste the following statement in the **Expression** box:</span></span>  
  
    ```  
    EnglishMonthName+' '+ CONVERT(CHAR (4), CalendarYear)  
    ```  
  
     <span data-ttu-id="e6f24-174">這個陳述式會將資料表中的每一個月的月份和年份串連成新的資料行。</span><span class="sxs-lookup"><span data-stu-id="e6f24-174">The statement concatenates the month and year for each month in the table into a new column.</span></span>  
  
4.  <span data-ttu-id="e6f24-175">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="e6f24-175">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="e6f24-176">在 [**資料表**] 窗格中，以滑鼠右鍵按一下 [] `Date` ，然後按一下 [**新增命名計算**]。</span><span class="sxs-lookup"><span data-stu-id="e6f24-176">In the **Tables** pane, right-click `Date`, and then click **New Named Calculation**.</span></span>  
  
6.  <span data-ttu-id="e6f24-177">在 [**建立命名計算**] 對話方塊中，于 `CalendarQuarterDesc` [資料**行名稱**] 方塊中輸入，然後在 [**運算式**] 方塊中輸入或複製並貼上下列 SQL 腳本：</span><span class="sxs-lookup"><span data-stu-id="e6f24-177">In the **Create Named Calculation** dialog box, type `CalendarQuarterDesc` in the **Column name** box, and then type or copy and paste the following SQL script in the **Expression** box:</span></span>  
  
    ```  
    'Q' + CONVERT(CHAR (1), CalendarQuarter) +' '+ 'CY ' +  
    CONVERT(CHAR (4), CalendarYear)  
    ```  
  
     <span data-ttu-id="e6f24-178">這個 SQL 指令碼會將資料表中每一季的日曆季和年份串連成新的資料行。</span><span class="sxs-lookup"><span data-stu-id="e6f24-178">This SQL script concatenates the calendar quarter and year for each quarter in the table into a new column.</span></span>  
  
7.  <span data-ttu-id="e6f24-179">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="e6f24-179">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="e6f24-180">在 [**資料表**] 窗格中，以滑鼠右鍵按一下 [] `Date` ，然後按一下 [**新增命名計算**]。</span><span class="sxs-lookup"><span data-stu-id="e6f24-180">In the **Tables** pane, right-click `Date`, and then click **New Named Calculation**.</span></span>  
  
9. <span data-ttu-id="e6f24-181">在 [**建立命名計算**] 對話方塊中，于 `CalendarSemesterDesc` [資料**行名稱**] 方塊中輸入，然後在 [**運算式**] 方塊中輸入或複製並貼上下列 SQL 腳本：</span><span class="sxs-lookup"><span data-stu-id="e6f24-181">In the **Create Named Calculation** dialog box, type `CalendarSemesterDesc` in the **Column name** box, and then type or copy and paste the following SQL script in the **Expression** box:</span></span>  
  
    ```  
    CASE  
    WHEN CalendarSemester = 1 THEN 'H1' + ' ' + 'CY' + ' '   
           + CONVERT(CHAR(4), CalendarYear)  
    ELSE  
    'H2' + ' ' + 'CY' + ' ' + CONVERT(CHAR(4), CalendarYear)  
    END  
    ```  
  
     <span data-ttu-id="e6f24-182">這個 SQL 指令碼會將資料表中每半年度的日曆半年度和年份串連成新的資料行。</span><span class="sxs-lookup"><span data-stu-id="e6f24-182">This SQL script concatenates the calendar semester and year for each semester in the table into a new column.</span></span>  
  
10. <span data-ttu-id="e6f24-183">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="e6f24-183">Click **OK.**</span></span>  
  
11. <span data-ttu-id="e6f24-184">在 [檔案] 功能表上，按一下 [全部儲存]。</span><span class="sxs-lookup"><span data-stu-id="e6f24-184">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="defining-composite-keycolumns-and-setting-the-name-column"></a><span data-ttu-id="e6f24-185">定義複合 KeyColumns 並設定名稱資料行</span><span class="sxs-lookup"><span data-stu-id="e6f24-185">Defining Composite KeyColumns and Setting the Name Column</span></span>  
 <span data-ttu-id="e6f24-186">[KeyColumns]\*\*\*\* 屬性 (property) 包含代表屬性 (attribute) 之索引鍵的一或多個資料行。</span><span class="sxs-lookup"><span data-stu-id="e6f24-186">The **KeyColumns** property contains the column or columns that represent the key for the attribute.</span></span> <span data-ttu-id="e6f24-187">在這項工作中，您將會定義複合 [KeyColumns]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6f24-187">In this task, you will define composite **KeyColumns**.</span></span>  
  
#### <a name="to-define-composite-keycolumns-for-the-english-month-name-attribute"></a><span data-ttu-id="e6f24-188">針對 [英文月份] 屬性定義複合 KeyColumns</span><span class="sxs-lookup"><span data-stu-id="e6f24-188">To define composite KeyColumns for the English Month Name attribute</span></span>  
  
1.  <span data-ttu-id="e6f24-189">針對 [日期] 維度開啟 [維度結構]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e6f24-189">Open the **Dimension Structure** tab for the Date dimension.</span></span>  
  
2.  <span data-ttu-id="e6f24-190">在 [屬性]\*\*\*\* 窗格中，按一下 [英文月份]\*\*\*\* 屬性。</span><span class="sxs-lookup"><span data-stu-id="e6f24-190">In the **Attributes** pane, click the **English Month Name** attribute.</span></span>  
  
3.  <span data-ttu-id="e6f24-191">在 [屬性]\*\*\*\* 視窗的 [KeyColumns]\*\*\*\* 欄位中按一下，然後按一下瀏覽 (**...**) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e6f24-191">In the **Properties** window, click the **KeyColumns** field, and then click the browse (**...**) button.</span></span>  
  
4.  <span data-ttu-id="e6f24-192">在 [索引**鍵資料行**] 對話方塊的 [可用的資料**行**] 清單中，選取資料行**CalendarYear**，然後按一下 **>** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e6f24-192">In the **Key Columns** dialog box, in the **Available Columns** list, select the column **CalendarYear**, and then click the **>** button.</span></span>  
  
5.  <span data-ttu-id="e6f24-193">[EnglishMonthName]\*\*\*\* 和 [CalendarYear]\*\*\*\* 資料行現在會顯示在 [索引鍵資料行]\*\*\*\* 清單中。</span><span class="sxs-lookup"><span data-stu-id="e6f24-193">The **EnglishMonthName** and **CalendarYear** columns are now displayed in the **Key Columns** list.</span></span>  
  
6.  <span data-ttu-id="e6f24-194">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="e6f24-194">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="e6f24-195">若要設定 [EnglishMonthName]\*\*\*\* 屬性 (attribute) 的 [NameColumn]\*\*\*\* 屬性 (property)，請按一下 [屬性] 視窗中的 [NameColumn]\*\*\*\* 欄位，然後按一下瀏覽 (**...**) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e6f24-195">To set the **NameColumn** property of the **EnglishMonthName** attribute, click the **NameColumn** field in the Properties window, and then click the browse (**...**) button.</span></span>  
  
8.  <span data-ttu-id="e6f24-196">在 [**名稱資料行**] 對話方塊的 [**來源資料行**] 清單中，選取 [ `MonthName` ]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e6f24-196">In the **Name Column** dialog box, in the **Source Column** list, select `MonthName`, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="e6f24-197">在 [檔案] 功能表上，按一下 [全部儲存]。</span><span class="sxs-lookup"><span data-stu-id="e6f24-197">On the **File** menu, click **Save All**.</span></span>  
  
#### <a name="to-define-composite-keycolumns-for-the-calendar-quarter-attribute"></a><span data-ttu-id="e6f24-198">若要針對 [日曆季] 屬性定義複合 KeyColumns</span><span class="sxs-lookup"><span data-stu-id="e6f24-198">To define composite KeyColumns for the Calendar Quarter attribute</span></span>  
  
1.  <span data-ttu-id="e6f24-199">在 [屬性]\*\*\*\* 窗格中，按一下 [日曆季]\*\*\*\* 屬性。</span><span class="sxs-lookup"><span data-stu-id="e6f24-199">In the **Attributes** pane, click the **Calendar Quarter** attribute.</span></span>  
  
2.  <span data-ttu-id="e6f24-200">在 [屬性]\*\*\*\* 視窗的 [KeyColumns]\*\*\*\* 欄位中按一下，然後按一下瀏覽 (**...**) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e6f24-200">In the **Properties** window, click the **KeyColumns** field, and then click the browse (**...**) button.</span></span>  
  
3.  <span data-ttu-id="e6f24-201">在 [索引**鍵資料行**] 對話方塊的 [可用的資料**行**] 清單中，選取資料行**CalendarYear**，然後按一下 **>** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e6f24-201">In the **Key Columns** dialog box, in the **Available Columns** list, select the column **CalendarYear**, and then click the **>** button.</span></span>  
  
     <span data-ttu-id="e6f24-202">[CalendarQuarter]\*\*\*\* 和 [CalendarYear]\*\*\*\* 資料行現在會顯示在 [索引鍵資料行]\*\*\*\* 清單中。</span><span class="sxs-lookup"><span data-stu-id="e6f24-202">The **CalendarQuarter** and **CalendarYear** columns are now displayed in the **Key Columns** list.</span></span>  
  
4.  <span data-ttu-id="e6f24-203">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="e6f24-203">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="e6f24-204">若要設定 [日曆季]\*\*\*\* 屬性 (attribute) 的 [NameColumn]\*\*\*\* 屬性 (property)，請按一下 [屬性] 視窗中的 [NameColumn]\*\*\*\* 欄位，然後按一下瀏覽 (**...**) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e6f24-204">To set the **NameColumn** property of the **Calendar Quarter** attribute, click the **NameColumn** field in the Properties window, and then click the browse (**...**) button.</span></span>  
  
6.  <span data-ttu-id="e6f24-205">在 [**名稱資料行**] 對話方塊的 [**來源資料行**] 清單中，選取 [ `CalendarQuarterDesc` ]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e6f24-205">In the **Name Column** dialog box, in the **Source Column** list, select `CalendarQuarterDesc`, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="e6f24-206">在 [檔案] 功能表上，按一下 [全部儲存]。</span><span class="sxs-lookup"><span data-stu-id="e6f24-206">On the **File** menu, click **Save All**.</span></span>  
  
#### <a name="to-define-composite-keycolumns-for-the-calendar-semester-attribute"></a><span data-ttu-id="e6f24-207">若要針對 [日曆半年] 屬性定義複合 KeyColumns</span><span class="sxs-lookup"><span data-stu-id="e6f24-207">To define composite KeyColumns for the Calendar Semester attribute</span></span>  
  
1.  <span data-ttu-id="e6f24-208">在 [屬性]\*\*\*\* 窗格中，按一下 [日曆半年度]\*\*\*\* 屬性。</span><span class="sxs-lookup"><span data-stu-id="e6f24-208">In the **Attributes** pane, click the **Calendar Semester** attribute.</span></span>  
  
2.  <span data-ttu-id="e6f24-209">在 [屬性]\*\*\*\* 視窗的 [KeyColumns]\*\*\*\* 欄位中按一下，然後按一下瀏覽 (**...**) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e6f24-209">In the **Properties** window, click the **KeyColumns** field, and then click the browse (**...**) button.</span></span>  
  
3.  <span data-ttu-id="e6f24-210">在 [索引鍵資料行]\*\*\*\* 對話方塊的 [可用的資料行]\*\*\*\* 清單中，選取 [CalendarYear]\*\*\*\* 資料行，然後按一下 [>]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e6f24-210">In the **Key Columns** dialog box, in the **Available Columns** list, select the column, **CalendarYear**, and then click the **>** button.</span></span>  
  
     <span data-ttu-id="e6f24-211">[CalendarSemester]\*\*\*\* 和 [CalendarYear]\*\*\*\* 資料行現在會顯示在 [索引鍵資料行]\*\*\*\* 清單中。</span><span class="sxs-lookup"><span data-stu-id="e6f24-211">The **CalendarSemester** and **CalendarYear** columns are now displayed in the **Key Columns** list.</span></span>  
  
4.  <span data-ttu-id="e6f24-212">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="e6f24-212">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="e6f24-213">若要設定 [日曆半年度]\*\*\*\* 屬性 (attribute) 的 [NameColumn]\*\*\*\* 屬性 (property)，請按一下 [屬性] 視窗中的 [NameColumn]\*\*\*\* 欄位，然後按一下瀏覽 (**...**) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e6f24-213">To set the **NameColumn** property of the **Calendar Semester** attribute, click the **NameColumn** field in the property window, and then click the browse (**...**) button.</span></span>  
  
6.  <span data-ttu-id="e6f24-214">在 [**名稱資料行**] 對話方塊的 [**來源資料行**] 清單中，選取 [ `CalendarSemesterDesc` ]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e6f24-214">In the **Name Column** dialog box, in the **Source Column** list, select `CalendarSemesterDesc`, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="e6f24-215">在 [檔案] 功能表上，按一下 [全部儲存]。</span><span class="sxs-lookup"><span data-stu-id="e6f24-215">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="deploying-and-viewing-the-changes"></a><span data-ttu-id="e6f24-216">部署和檢視變更</span><span class="sxs-lookup"><span data-stu-id="e6f24-216">Deploying and Viewing the Changes</span></span>  
 <span data-ttu-id="e6f24-217">在變更屬性和階層之後，您必須部署變更及重新處理相關物件，然後才可以檢視變更。</span><span class="sxs-lookup"><span data-stu-id="e6f24-217">After you have changed attributes and hierarchies, you must deploy the changes and reprocess the related objects before you can view the changes.</span></span>  
  
#### <a name="to-deploy-and-view-the-changes"></a><span data-ttu-id="e6f24-218">部署和檢視變更</span><span class="sxs-lookup"><span data-stu-id="e6f24-218">To deploy and view the changes</span></span>  
  
1.  <span data-ttu-id="e6f24-219">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 的 [建立]\*\*\*\* 功能表上，按一下 [部署 Analysis Services 教學課程]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6f24-219">On the **Build** menu of [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="e6f24-220">當您收到 [已**成功完成部署**] 訊息之後，請針對維度按一下**維度設計師**的 [**瀏覽器**] 索引標籤 `Date` ，然後按一下設計師工具列上的 [重新連接] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e6f24-220">After you have received the **Deployment Completed Successfully** message, click the **Browser** tab of **Dimension Designer** for the `Date` dimension, and then click the Reconnect button on the toolbar of the designer.</span></span>  
  
3.  <span data-ttu-id="e6f24-221">從 [階層]\*\*\*\* 清單中，選取 [日曆季]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6f24-221">Select **Calendar Quarter** from the **Hierarchy** list.</span></span> <span data-ttu-id="e6f24-222">檢閱 [日曆季]\*\*\*\* 屬性階層中的成員。</span><span class="sxs-lookup"><span data-stu-id="e6f24-222">Review the members in the **Calendar Quarter** attribute hierarchy.</span></span>  
  
     <span data-ttu-id="e6f24-223">請注意，[日曆季]\*\*\*\* 屬性階層的成員名稱會更清楚且更容易使用，因為您建立了要當作名稱使用的具名計算。</span><span class="sxs-lookup"><span data-stu-id="e6f24-223">Notice that the names of the members of the **Calendar Quarter** attribute hierarchy are clearer and easier to use because you created a named calculation to use as the name.</span></span> <span data-ttu-id="e6f24-224">現在成員位於每個年度中每個季度的 [日曆季]\*\*\*\* 屬性階層中。</span><span class="sxs-lookup"><span data-stu-id="e6f24-224">Members now exist in the **Calendar Quarter** attribute hierarchy for each quarter in each year.</span></span> <span data-ttu-id="e6f24-225">成員不是依時間順序排序。</span><span class="sxs-lookup"><span data-stu-id="e6f24-225">The members are not sorted in chronological order.</span></span> <span data-ttu-id="e6f24-226">而是先按季再按年排序。</span><span class="sxs-lookup"><span data-stu-id="e6f24-226">Instead they are sorted by quarter and then by year.</span></span> <span data-ttu-id="e6f24-227">在這個主題的下一項工作中，您會修改先按季再按年排序這個屬性階層成員的行為。</span><span class="sxs-lookup"><span data-stu-id="e6f24-227">In the next task in this topic, you will modify this behavior to sort the members of this attribute hierarchy by year and then by quarter.</span></span>  
  
4.  <span data-ttu-id="e6f24-228">檢閱 [英文月份]\*\*\*\* 和 [日曆半年度]\*\*\*\* 屬性階層的成員。</span><span class="sxs-lookup"><span data-stu-id="e6f24-228">Review the members of the **English Month Name** and **Calendar Semester** attribute hierarchies.</span></span>  
  
     <span data-ttu-id="e6f24-229">請注意，這些階層的成員也未按照時間順序排列，</span><span class="sxs-lookup"><span data-stu-id="e6f24-229">Notice that the members of these hierarchies are also not sorted in chronological order.</span></span> <span data-ttu-id="e6f24-230">而是分別按月或按半年度再按年來排序。</span><span class="sxs-lookup"><span data-stu-id="e6f24-230">Instead, they are sorted by month or semester, respectively, and then by year.</span></span> <span data-ttu-id="e6f24-231">在這個主題的下一項工作中，您會修改這個行為來變更這種排序順序。</span><span class="sxs-lookup"><span data-stu-id="e6f24-231">In the next task in this topic, you will modify this behavior to change this sort order.</span></span>  
  
## <a name="changing-the-sort-order-by-modifying-composite-key-member-order"></a><span data-ttu-id="e6f24-232">修改複合索引鍵成員順序來變更排序順序</span><span class="sxs-lookup"><span data-stu-id="e6f24-232">Changing the Sort Order by Modifying Composite Key Member Order</span></span>  
 <span data-ttu-id="e6f24-233">在這項工作中，您將會透過變更組成複合索引鍵之索引鍵的順序，變更排序次序。</span><span class="sxs-lookup"><span data-stu-id="e6f24-233">In this task, you will change the sort order by changing the order of the keys that make up the composite key.</span></span>  
  
#### <a name="to-modify-the-composite-key-member-order"></a><span data-ttu-id="e6f24-234">若要修改複合索引鍵成員順序</span><span class="sxs-lookup"><span data-stu-id="e6f24-234">To modify the composite key member order</span></span>  
  
1.  <span data-ttu-id="e6f24-235">針對維度開啟維度設計師的 [**維度結構**] 索引標籤 `Date` ，然後在 [**屬性**] 窗格中選取 [**日曆半**年度]。</span><span class="sxs-lookup"><span data-stu-id="e6f24-235">Open the **Dimension Structure** tab of Dimension Designer for the `Date` dimension, and then select **Calendar Semester** in the **Attributes** pane.</span></span>  
  
2.  <span data-ttu-id="e6f24-236">在 [屬性] 視窗中，檢閱 [OrderBy]\*\*\*\* 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="e6f24-236">In the Properties window, review the value for the **OrderBy** property.</span></span> <span data-ttu-id="e6f24-237">它會設定為 [索引鍵]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6f24-237">It is set to **Key**.</span></span>  
  
     <span data-ttu-id="e6f24-238">[日曆半年度]\*\*\*\* 屬性階層的成員會按照其索引鍵值進行排序。</span><span class="sxs-lookup"><span data-stu-id="e6f24-238">The members of the **Calendar Semester** attribute hierarchy are sorted by their key value.</span></span> <span data-ttu-id="e6f24-239">利用複合索引鍵，成員索引鍵的排序是先依據第一個成員索引鍵的值，再依據第二個成員索引鍵的值。</span><span class="sxs-lookup"><span data-stu-id="e6f24-239">With a composite key, the ordering of the member keys is based first on the value of the first member key, and then on the value of the second member key.</span></span> <span data-ttu-id="e6f24-240">換言之，[日曆半年度]\*\*\*\* 屬性階層的成員是先按半年度再按年度進行排序。</span><span class="sxs-lookup"><span data-stu-id="e6f24-240">In other words, the members of the **Calendar Semester** attribute hierarchy are sorted first by semester and then by year.</span></span>  
  
3.  <span data-ttu-id="e6f24-241">在 [屬性] 視窗中，按一下省略符號瀏覽按鈕 (**...**) 變更 [KeyColumns]\*\*\*\* 屬性值。</span><span class="sxs-lookup"><span data-stu-id="e6f24-241">In the Properties window, click the ellipsis browse button (**...**) to change the **KeyColumns** property value.</span></span>  
  
4.  <span data-ttu-id="e6f24-242">在 [索引鍵資料行]\*\*\*\* 對話方塊的 [索引鍵資料行]\*\*\*\* 清單中，確認已選取 [CalendarSemester]\*\*\*\*，然後按一下向下箭號，讓這個複合索引鍵之成員的順序相反。</span><span class="sxs-lookup"><span data-stu-id="e6f24-242">In the **Key Columns** list of the **Key Columns** dialog box, verify that **CalendarSemester** is selected, and then click the down arrow to reverse the order of the members of this composite key.</span></span> <span data-ttu-id="e6f24-243">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="e6f24-243">Click **OK**.</span></span>  
  
     <span data-ttu-id="e6f24-244">屬性階層的成員現在變成先按年再按半年度排序。</span><span class="sxs-lookup"><span data-stu-id="e6f24-244">The members of the attribute hierarchy are now sorted first by year and then by semester.</span></span>  
  
5.  <span data-ttu-id="e6f24-245">在 [屬性]\*\*\*\* (attribute) 窗格中選取 [日曆季]\*\*\*\*，然後在 [屬性]\*\*\*\* (property) 視窗中按一下 [KeyColumns] 屬性 (property) 的省略符號瀏覽按鈕 (**...**)。</span><span class="sxs-lookup"><span data-stu-id="e6f24-245">Select **Calendar Quarter** in the **Attributes** pane, and then click the ellipsis browse button (**...**) for the **KeyColumns** property in the Properties window.</span></span>  
  
6.  <span data-ttu-id="e6f24-246">在 [索引鍵資料行]\*\*\*\* 對話方塊的 [索引鍵資料行]\*\*\*\* 清單中，確認已選取 [CalendarQuarter]\*\*\*\*，然後按一下向下箭號，讓這個複合索引鍵之成員的順序相反。</span><span class="sxs-lookup"><span data-stu-id="e6f24-246">In the **Key Columns** list of the **Key Columns** dialog box, verify that **CalendarQuarter** is selected, and then click the down arrow to reverse the order of the members of this composite key.</span></span> <span data-ttu-id="e6f24-247">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="e6f24-247">Click **OK**.</span></span>  
  
     <span data-ttu-id="e6f24-248">屬性階層的成員現在變成先按年再按季排序。</span><span class="sxs-lookup"><span data-stu-id="e6f24-248">The members of the attribute hierarchy are now sorted first by year and then by quarter.</span></span>  
  
7.  <span data-ttu-id="e6f24-249">在 [屬性]\*\*\*\* (attribute) 窗格中選取 [英文月份]\*\*\*\*，然後在 [屬性]\*\*\*\* (property) 視窗中按一下 [KeyColumns] 屬性 (property) 的省略符號按鈕 (**...**)。</span><span class="sxs-lookup"><span data-stu-id="e6f24-249">Select **English Month Name** in the **Attributes** pane, and then click the ellipsis button (**...**) for the **KeyColumns** property in the Properties window.</span></span>  
  
8.  <span data-ttu-id="e6f24-250">在 [索引鍵資料行]\*\*\*\* 對話方塊的 [索引鍵資料行]\*\*\*\* 清單中，確認已選取 [EnglishMonthName]\*\*\*\*，然後按一下向下箭號，讓這個複合索引鍵之成員的順序相反。</span><span class="sxs-lookup"><span data-stu-id="e6f24-250">In the **Key Columns** list of the **Key Columns** dialog box, verify that **EnglishMonthName** is selected, and then click the down arrow to reverse the order of the members of this composite key.</span></span> <span data-ttu-id="e6f24-251">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="e6f24-251">Click **OK**.</span></span>  
  
     <span data-ttu-id="e6f24-252">屬性階層的成員現在變成先按年再按月排序。</span><span class="sxs-lookup"><span data-stu-id="e6f24-252">The members of the attribute hierarchy are now sorted first by year and then by month.</span></span>  
  
9. <span data-ttu-id="e6f24-253">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 的 [建立]\*\*\*\* 功能表上，按一下 [部署 Analysis Services 教學課程]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6f24-253">On the **Build** menu of [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click **Deploy Analysis Services Tutorial**.</span></span> <span data-ttu-id="e6f24-254">順利完成部署之後，針對維度，按一下維度設計師中的 [**瀏覽器**] 索引標籤 `Date` 。</span><span class="sxs-lookup"><span data-stu-id="e6f24-254">When deployment has successfully completed, click the **Browser** tab in Dimension Designer for the `Date` dimension.</span></span>  
  
10. <span data-ttu-id="e6f24-255">在 [瀏覽器]\*\*\*\* 索引標籤的工具列上，按一下 [重新連接] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e6f24-255">On the toolbar of the **Browser** tab, click the Reconnect button.</span></span>  
  
11. <span data-ttu-id="e6f24-256">檢閱 [日曆季]\*\*\*\* 和 [日曆半年度]\*\*\*\* 屬性階層的成員。</span><span class="sxs-lookup"><span data-stu-id="e6f24-256">Review the members of the **Calendar Quarter** and **Calendar Semester** attribute hierarchies.</span></span>  
  
     <span data-ttu-id="e6f24-257">請注意，這些階層的成員現在已按照時間順序排列了，它們是先按年再按季或半年度來排序。</span><span class="sxs-lookup"><span data-stu-id="e6f24-257">Notice that the members of these hierarchies are now sorted in chronological order, by year and then by quarter or semester, respectively.</span></span>  
  
12. <span data-ttu-id="e6f24-258">檢閱 [英文月份]\*\*\*\* 屬性階層的成員。</span><span class="sxs-lookup"><span data-stu-id="e6f24-258">Review the members of the **English Month Name** attribute hierarchy.</span></span>  
  
     <span data-ttu-id="e6f24-259">請注意，現在階層的成員會先依年排序，然後依月按字母順序排序。</span><span class="sxs-lookup"><span data-stu-id="e6f24-259">Notice that the members of the hierarchy are now sorted first by year and then alphabetically by month.</span></span> <span data-ttu-id="e6f24-260">這是因為依據關聯式資料庫中的 nvarchar 資料類型，在資料來源檢視中 EnglishCalendarMonth 資料行的資料類型為字串資料行。</span><span class="sxs-lookup"><span data-stu-id="e6f24-260">This is because the data type for the EnglishCalendarMonth column in the data source view is a string column, based on the nvarchar data type in the underlying relational database.</span></span> <span data-ttu-id="e6f24-261">如需如何讓每年的月份按時間順序排序的資訊，請參閱 [依次要屬性來排序屬性成員](lesson-4-5-sorting-attribute-members-based-on-a-secondary-attribute.md)。</span><span class="sxs-lookup"><span data-stu-id="e6f24-261">For information about how to enable the months to be sorted chronologically within each year, see [Sorting Attribute Members Based on a Secondary Attribute](lesson-4-5-sorting-attribute-members-based-on-a-secondary-attribute.md).</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="e6f24-262">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="e6f24-262">Next Task in Lesson</span></span>  
 [<span data-ttu-id="e6f24-263">瀏覽已部署的 Cube</span><span class="sxs-lookup"><span data-stu-id="e6f24-263">Browsing the Deployed Cube</span></span>](lesson-3-5-browsing-the-deployed-cube.md)  
  
## <a name="see-also"></a><span data-ttu-id="e6f24-264">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6f24-264">See Also</span></span>  
 [<span data-ttu-id="e6f24-265">多維度模型中的維度</span><span class="sxs-lookup"><span data-stu-id="e6f24-265">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
