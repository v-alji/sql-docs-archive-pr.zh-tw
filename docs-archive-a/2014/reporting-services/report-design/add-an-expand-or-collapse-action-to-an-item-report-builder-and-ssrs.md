---
title: 將展開或摺疊動作新增項目中 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 49f07ad6-242b-4861-8fc1-91ca78c36d6c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 331c6a14a4a898ffcdf86f274c00e7ad3c801ec7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687465"
---
# <a name="add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs"></a><span data-ttu-id="ede2f-102">將展開或摺疊動作加入項目中 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="ede2f-102">Add an Expand or Collapse Action to an Item (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ede2f-103">您可以讓使用者以互動方式展開或摺疊報表項目，或者針對資料表或矩陣，展開或摺疊與群組關聯的資料列和資料行。</span><span class="sxs-lookup"><span data-stu-id="ede2f-103">You can enable a user to interactively expand or collapse report items, or expand or collapse rows and columns associated with a group for a table or matrix.</span></span> <span data-ttu-id="ede2f-104">若要讓使用者展開或摺疊項目，您可以設定該項目的可見性屬性。</span><span class="sxs-lookup"><span data-stu-id="ede2f-104">To allow users to expand or collapse an item, you set the visibility properties for that item.</span></span> <span data-ttu-id="ede2f-105">設定可見性適用於 HTML 報表檢視器，有時稱為 *「向下鑽研」* (Drilldown) 動作。</span><span class="sxs-lookup"><span data-stu-id="ede2f-105">Setting visibility works in an HTML report viewer, and is sometimes called a *drilldown* action.</span></span>  
  
 <span data-ttu-id="ede2f-106">在報表設計檢視中，請指定要顯示展開和摺疊切換圖示之文字方塊的名稱。</span><span class="sxs-lookup"><span data-stu-id="ede2f-106">In report design view, you specify the name of the text box where you want to display the expand and collapse toggle icons.</span></span> <span data-ttu-id="ede2f-107">在轉譯過的報表中，文字方塊除了其內容之外，還會顯示一個加號 (+) 或一個減號 (-)。</span><span class="sxs-lookup"><span data-stu-id="ede2f-107">In the rendered report, the text box displays a plus (+) or minus (-) sign in addition to its contents.</span></span> <span data-ttu-id="ede2f-108">當使用者按一下切換時，報表顯示會重新整理，根據報表項目的目前可見性設定，顯示或隱藏報表項目。</span><span class="sxs-lookup"><span data-stu-id="ede2f-108">When the user clicks the toggle, the report display is refreshed to show or hide the report item, based on the current visibility settings for items in the report.</span></span>  
  
 <span data-ttu-id="ede2f-109">展開和摺疊動作通常用於一開始只顯示摘要資料，以及讓使用者按一下加號來顯示詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ede2f-109">Typically, the expand and collapse action is used to initially display only summary data and to enable the user to click the plus sign to show detail data.</span></span> <span data-ttu-id="ede2f-110">例如，您一開始可以隱藏顯示圖表值的資料表，或針對包含巢狀資料列或資料行群組的資料表隱藏子群組，如同在向下鑽研報表一樣。</span><span class="sxs-lookup"><span data-stu-id="ede2f-110">For example, you can initially hide a table that displays values for a chart, or hide child groups for a table with nested row or column groups, as in a drilldown report.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-expand-and-collapse-action-to-a-group"></a><span data-ttu-id="ede2f-111">若要將展開和摺疊動作加入至群組中</span><span class="sxs-lookup"><span data-stu-id="ede2f-111">To add expand and collapse action to a group</span></span>  
  
1.  <span data-ttu-id="ede2f-112">在報表設計檢視中，按一下資料表或矩陣即可選取它。</span><span class="sxs-lookup"><span data-stu-id="ede2f-112">In report design view, click the table or matrix to select it.</span></span> <span data-ttu-id="ede2f-113">[群組] 窗格會顯示資料列和資料行群組。</span><span class="sxs-lookup"><span data-stu-id="ede2f-113">The Grouping pane displays the row and column groups.</span></span>  
  
     <span data-ttu-id="ede2f-114">![群組窗格](../media/groupingpane.png "群組窗格")</span><span class="sxs-lookup"><span data-stu-id="ede2f-114">![Grouping Pane](../media/groupingpane.png "Grouping Pane")</span></span>  
  
     <span data-ttu-id="ede2f-115">如果未顯示 [群組] 窗格，請按一下[檢視] \*\*\*\* 功能表，然後按一下 [群組] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ede2f-115">If the Grouping pane does not appear, click the **View** menu and then click **Grouping**.</span></span>  
  
2.  <span data-ttu-id="ede2f-116">以滑鼠右鍵按一下 [群組] 窗格標題列的任意位置，然後按一下 [進階]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ede2f-116">Right-click anywhere in the title bar of the Grouping pane, and then click **Advanced**.</span></span> <span data-ttu-id="ede2f-117">[群組] 窗格模式會切換以便在設計介面上，顯示資料列和資料行的基礎顯示結構。</span><span class="sxs-lookup"><span data-stu-id="ede2f-117">The Grouping pane mode toggles to show the underlying display structure for rows and columns on the design surface.</span></span>  
  
     <span data-ttu-id="ede2f-118">![含 [進階模式] 功能表的 [群組] 窗格](../media/groupingpane-advancedmode.png "含 [進階模式] 功能表的 [群組] 窗格")</span><span class="sxs-lookup"><span data-stu-id="ede2f-118">![Grouping Pane with Advanced Mode menu](../media/groupingpane-advancedmode.png "Grouping Pane with Advanced Mode menu")</span></span>  
  
3.  <span data-ttu-id="ede2f-119">在適當的群組窗格中，按一下您要隱藏相關聯資料列或資料行之資料列群組或資料行群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="ede2f-119">In the appropriate group pane, click the name of the row group or column group for which you want to hide the associated rows or columns.</span></span> <span data-ttu-id="ede2f-120">群組選定之後，[屬性] 窗格會顯示 **[Tablix 成員]** 屬性。</span><span class="sxs-lookup"><span data-stu-id="ede2f-120">The group is selected and the Properties pane shows the **Tablix Member** properties.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ede2f-121"> 如果看不到 [屬性] 窗格，請按一下功能區上的 [檢視]\ \*\*\** ，然後按一下 [屬性]\ \*\*\**。</span><span class="sxs-lookup"><span data-stu-id="ede2f-121">If you do not see the Properties pane, click **View** on the Ribbon and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="ede2f-122">在中 `Hidden` ，選擇下列其中一個選項，以在您第一次執行報表時設定此報表專案的可見度：</span><span class="sxs-lookup"><span data-stu-id="ede2f-122">In `Hidden`, choose one of the following options to set the visibility of this report item the first time you run a report:</span></span>  
  
    -   <span data-ttu-id="ede2f-123">選取 `False` 即可顯示報表專案。</span><span class="sxs-lookup"><span data-stu-id="ede2f-123">Select `False` to display the report item.</span></span>  
  
    -   <span data-ttu-id="ede2f-124">選取 `True` 即可隱藏報表專案。</span><span class="sxs-lookup"><span data-stu-id="ede2f-124">Select `True` to hide the report item.</span></span>  
  
    -   <span data-ttu-id="ede2f-125">選取 **\<Expression>** 即可開啟 [**運算式**] 對話方塊，以建立在執行時間評估的運算式來決定可見度。</span><span class="sxs-lookup"><span data-stu-id="ede2f-125">Select **\<Expression>** to open the **Expression** dialog box to create an expression that is evaluated at run time to determine the visibility.</span></span>  
  
5.  <span data-ttu-id="ede2f-126">在 **ToggleItem**中，從下拉式方塊選取要加入切換影像之目標文字方塊的名稱。</span><span class="sxs-lookup"><span data-stu-id="ede2f-126">In **ToggleItem**, from the drop-down box, select the name of a text box to which to add the toggle image.</span></span>  
  
     <span data-ttu-id="ede2f-127">在下圖中，色彩資料列群組已設定為可讓使用者展開和摺疊相關聯的資料列。</span><span class="sxs-lookup"><span data-stu-id="ede2f-127">In the following image, the Color row group is configured enable users to expand and collapse associated rows.</span></span>  
  
     <span data-ttu-id="ede2f-128">![設定要展開的資料列群組](../media/expandcollapse-confighiddentoggleitemwithnumbers.png "設定要展開的資料列群組")</span><span class="sxs-lookup"><span data-stu-id="ede2f-128">![Configuring a row group to be expanded](../media/expandcollapse-confighiddentoggleitemwithnumbers.png "Configuring a row group to be expanded")</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ede2f-129">具有切換影像的文字方塊不能是您要隱藏相關聯資料列或資料行的資料列或資料行群組。</span><span class="sxs-lookup"><span data-stu-id="ede2f-129">The text box with the toggle image cannot be the row or column group for which you want to hide the associated rows or columns.</span></span> <span data-ttu-id="ede2f-130">它必須在隱藏項目的相同群組中，或在上階群組中。</span><span class="sxs-lookup"><span data-stu-id="ede2f-130">It must either be in the same group as the item that is being hidden or in an ancestor group.</span></span> <span data-ttu-id="ede2f-131">例如，若要切換與子群組相關之資料列的可見性，請選取與父群組有關之資料列中的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="ede2f-131">For example, to toggle visibility of rows associated with a child group, select a text box in a row associated with the parent group.</span></span>  
  
6.  <span data-ttu-id="ede2f-132">若要測試切換，請執行報表，然後按一下包含切換影像的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="ede2f-132">To test the toggle, run the report and click the text box with the toggle image.</span></span> <span data-ttu-id="ede2f-133">報表顯示會重新整理，以顯示包含已切換之可見性的資料列群組和資料行群組。</span><span class="sxs-lookup"><span data-stu-id="ede2f-133">The report display refreshes to show row groups and column groups with their toggled visibility.</span></span>  
  
     <span data-ttu-id="ede2f-134">![執行含可展開資料列群組的報表](../media/expandcollapse-runreport-rowgroup.png "執行含可展開資料列群組的報表")</span><span class="sxs-lookup"><span data-stu-id="ede2f-134">![Running report with expandable row group](../media/expandcollapse-runreport-rowgroup.png "Running report with expandable row group")</span></span>  
  
### <a name="to-add-expand-and-collapse-action-to-a-report-item"></a><span data-ttu-id="ede2f-135">若要將展開和摺疊動作加入至報表項目中</span><span class="sxs-lookup"><span data-stu-id="ede2f-135">To add expand and collapse action to a report item</span></span>  
  
1.  <span data-ttu-id="ede2f-136">在報表設計檢視中，以滑鼠右鍵按一下要顯示或隱藏的報表專案，然後按一下 [ *\<report item>* **屬性**]。</span><span class="sxs-lookup"><span data-stu-id="ede2f-136">In report design view, right-click the report item to show or hide, and then click *\<report item>* **Properties**.</span></span> <span data-ttu-id="ede2f-137">報表專案的 [ *\<report item>* **屬性**] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="ede2f-137">The *\<report item>* **Properties** dialog box for the report item opens.</span></span>  
  
2.  <span data-ttu-id="ede2f-138">按一下 **[可見性]** 。</span><span class="sxs-lookup"><span data-stu-id="ede2f-138">Click **Visibility**.</span></span>  
  
3.  <span data-ttu-id="ede2f-139">在 **[一開始執行報表時]** 中，選擇下列其中一個選項來設定第一次執行報表時，此報表項目的可見性：</span><span class="sxs-lookup"><span data-stu-id="ede2f-139">In **When the report is initially run**, choose one of the following options to set the visibility of this report item the first time you run a report:</span></span>  
  
    -   <span data-ttu-id="ede2f-140">選取 **[顯示]** 來顯示報表項目。</span><span class="sxs-lookup"><span data-stu-id="ede2f-140">Select **Show** to display the report item.</span></span>  
  
    -   <span data-ttu-id="ede2f-141">選取 **[隱藏]** 來隱藏報表項目。</span><span class="sxs-lookup"><span data-stu-id="ede2f-141">Select **Hide** to hide the report item.</span></span>  
  
    -   <span data-ttu-id="ede2f-142">選取 **[依據運算式顯示或隱藏]** ，使用在執行階段評估的運算式來決定可見性。</span><span class="sxs-lookup"><span data-stu-id="ede2f-142">Select **Show or hide based on an expression** to use an expression evaluated at run time to determine the visibility.</span></span> <span data-ttu-id="ede2f-143">按一下 [ (**fx**) 開啟 [**運算式**] 對話方塊，以建立運算式。</span><span class="sxs-lookup"><span data-stu-id="ede2f-143">Click (**fx**) to open the **Expression** dialog box to create an expression.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="ede2f-144">當您指定可見性的運算式時，會設定報表項目的 Hidden 屬性。</span><span class="sxs-lookup"><span data-stu-id="ede2f-144">When you specify an expression for visibility, you are setting the Hidden property of the report item.</span></span> <span data-ttu-id="ede2f-145">運算式會評估為 `Boolean` 值 `True` 來隱藏項目，以及 `False` 來顯示項目。</span><span class="sxs-lookup"><span data-stu-id="ede2f-145">The expression evaluates to a `Boolean` value of `True` to hide the item and `False` to show the item.</span></span>  
  
4.  <span data-ttu-id="ede2f-146">在 [此報表項目可以切換顯示]\*\*\*\* 中，從下拉式方塊鍵入或選取報表中要顯示切換影像的文字方塊名稱；例如 Textbox1。</span><span class="sxs-lookup"><span data-stu-id="ede2f-146">In **Display can be toggled by this report item**, from the drop-down box, type or select the name of a text box in the report in which to display a toggle image; for example, Textbox1.</span></span>  
  
     <span data-ttu-id="ede2f-147">在下圖中，資料表已設定為讓使用者可展開及摺疊該資料表。</span><span class="sxs-lookup"><span data-stu-id="ede2f-147">In the following image, the table is configured to enable users to expand and collapse it.</span></span> <span data-ttu-id="ede2f-148">[Products 資料表] 文字方塊可以切換資料表的顯示。</span><span class="sxs-lookup"><span data-stu-id="ede2f-148">The display of the table is toggled by the Products Table text box.</span></span>  
  
     <span data-ttu-id="ede2f-149">![設定要展開的報表資料表](../media/expandcollapse-reporttable.png "設定要展開的報表資料表")</span><span class="sxs-lookup"><span data-stu-id="ede2f-149">![Configure a report table to be expanded](../media/expandcollapse-reporttable.png "Configure a report table to be expanded")</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ede2f-150">您選擇的文字方塊必須位於此報表項目的目前或包含範圍 (最高至報表主體 (包含))。</span><span class="sxs-lookup"><span data-stu-id="ede2f-150">The text box that you choose must be in the current or containing scope for this report item (up to and including the report body).</span></span> <span data-ttu-id="ede2f-151">例如，若要切換圖表的可見性，請選取與圖表位於相同涵蓋範圍的文字方塊，例如，報表主體或矩形。</span><span class="sxs-lookup"><span data-stu-id="ede2f-151">For example, to toggle visibility of a chart, select a text box that is in the same containing scope as the chart; for example, the report body or a rectangle.</span></span> <span data-ttu-id="ede2f-152">此文字方塊必須位於相同或更高的容器階層中。</span><span class="sxs-lookup"><span data-stu-id="ede2f-152">The text box must be in the same container hierarchy or higher.</span></span>  
  
5.  <span data-ttu-id="ede2f-153">若要測試切換，請執行報表，然後按一下包含切換影像的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="ede2f-153">To test the toggle, run the report and click the text box with the toggle image.</span></span> <span data-ttu-id="ede2f-154">報表顯示會重新整理，以顯示包含已切換之可見性的報表項目。</span><span class="sxs-lookup"><span data-stu-id="ede2f-154">The report display refreshes to show report items with their toggled visibility.</span></span>  
  
     <span data-ttu-id="ede2f-155">![執行含有已展開資料表的報表](../media/expandcollapse-runreport-reporttable.png "執行含有已展開資料表的報表")</span><span class="sxs-lookup"><span data-stu-id="ede2f-155">![Running report with an expanding table](../media/expandcollapse-runreport-reporttable.png "Running report with an expanding table")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ede2f-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ede2f-156">See Also</span></span>  
 <span data-ttu-id="ede2f-157">[&#40;報表產生器和 SSRS 的深入分析動作&#41;](drilldown-action-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ede2f-157">[Drilldown Action &#40;Report Builder and SSRS&#41;](drilldown-action-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ede2f-158">隱藏項目 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ede2f-158">Hide an Item &#40;Report Builder and SSRS&#41;</span></span>](../report-builder/hide-an-item-report-builder-and-ssrs.md)  
  
  
