---
title: 建立階梯狀報表 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5933c4f0-c713-4ecb-b521-ff46c9c63fff
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d845993ac1462cef2d39638101e5c7b9fc314b94
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594424"
---
# <a name="create-a-stepped-report-report-builder-and-ssrs"></a><span data-ttu-id="c53a1-102">建立階梯狀報表 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="c53a1-102">Create a Stepped Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="c53a1-103">階梯狀報表會在相同的資料行中，顯示父群組底下縮排的詳細資料列或子群組，如以下範例所示：</span><span class="sxs-lookup"><span data-stu-id="c53a1-103">A stepped report shows detail rows or child groups indented under a parent group in the same column, as shown in the example below:</span></span>  
  
 <span data-ttu-id="c53a1-104">![已轉譯的階梯狀報表](../media/steppedreportrendered.gif "已轉譯的階梯狀報表")</span><span class="sxs-lookup"><span data-stu-id="c53a1-104">![Rendered stepped report](../media/steppedreportrendered.gif "Rendered stepped report")</span></span>  
  
 <span data-ttu-id="c53a1-105">傳統的資料表報表會將父群組放在報表的相鄰資料行中。</span><span class="sxs-lookup"><span data-stu-id="c53a1-105">Traditional table reports place the parent group in an adjacent column on the report.</span></span> <span data-ttu-id="c53a1-106">新的 Tablix 資料區可讓您將群組和詳細資料列或子群組加入到相同的資料行中。</span><span class="sxs-lookup"><span data-stu-id="c53a1-106">The new tablix data region enables you to add a group and detail rows or child groups to the same column.</span></span> <span data-ttu-id="c53a1-107">若要區分群組資料列與詳細資料列或子群組資料列，您可以套用格式 (如字型色彩)，也可以讓詳細資料列縮排。</span><span class="sxs-lookup"><span data-stu-id="c53a1-107">To differentiate the group rows from the detail or child group rows, you can apply formatting such as font color, or you can indent the detail rows.</span></span>  
  
 <span data-ttu-id="c53a1-108">本主題中的程序示範如何手動建立階梯狀報表，但是您也可以使用「新增資料表和矩陣精靈」。</span><span class="sxs-lookup"><span data-stu-id="c53a1-108">The procedures in this topic show you how to manually create a stepped report, but you can also use the New Table and Matrix Wizard.</span></span> <span data-ttu-id="c53a1-109">此精靈會提供階梯狀報表的配置，讓您更容易建立階梯狀報表。</span><span class="sxs-lookup"><span data-stu-id="c53a1-109">It provides the layout for stepped reports, making it easy to create them.</span></span> <span data-ttu-id="c53a1-110">完成精靈後，您可以進一步增強報表。</span><span class="sxs-lookup"><span data-stu-id="c53a1-110">After you complete the wizard, you can further enhance the report.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c53a1-111">您只能在報表產生器中使用此精靈。</span><span class="sxs-lookup"><span data-stu-id="c53a1-111">The wizard is available only in Report Builder.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-create-a-stepped-report"></a><span data-ttu-id="c53a1-112">若要建立階梯狀報表</span><span class="sxs-lookup"><span data-stu-id="c53a1-112">To create a stepped report</span></span>  
  
1.  <span data-ttu-id="c53a1-113">建立資料表報表。</span><span class="sxs-lookup"><span data-stu-id="c53a1-113">Create a table report.</span></span> <span data-ttu-id="c53a1-114">例如，插入 Tablix 資料區，然後將欄位加入到資料列。</span><span class="sxs-lookup"><span data-stu-id="c53a1-114">For example, insert a tablix data region and add fields to the Data row.</span></span>  
  
2.  <span data-ttu-id="c53a1-115">將父群組加入到報表中。</span><span class="sxs-lookup"><span data-stu-id="c53a1-115">Add a parent group to your report.</span></span>  
  
    1.  <span data-ttu-id="c53a1-116">按一下資料表中的任何地方，即可選取它。</span><span class="sxs-lookup"><span data-stu-id="c53a1-116">Click anywhere in the table to select it.</span></span> <span data-ttu-id="c53a1-117">在 [群組] 窗格會顯示 [資料列群組] 窗格中的詳細資料群組。</span><span class="sxs-lookup"><span data-stu-id="c53a1-117">The Grouping pane displays the Details group in the Row Groups pane.</span></span>  
  
    2.  <span data-ttu-id="c53a1-118">在 [群組] 窗格中，以滑鼠右鍵按一下 [詳細資料群組]，然後指向 [新增群組]  ，再按一下 [父群組]  。</span><span class="sxs-lookup"><span data-stu-id="c53a1-118">In the Grouping Pane, right-click the Details Group, point to **Add Group**, and then click **Parent Group**.</span></span>  
  
    3.  <span data-ttu-id="c53a1-119">在 [Tablix 群組]  對話方塊中，為群組提供一個名稱，然後在下拉式清單中鍵入或選取一個群組運算式。</span><span class="sxs-lookup"><span data-stu-id="c53a1-119">In the **Tablix Group** dialog box, provide a name for the group and type or select a group expression from the drop-down list.</span></span> <span data-ttu-id="c53a1-120">此下拉式清單會顯示 [報表資料] 窗格中提供的簡單欄位運算式。</span><span class="sxs-lookup"><span data-stu-id="c53a1-120">The drop-down list displays the simple field expressions that are available in the Report Data pane.</span></span> <span data-ttu-id="c53a1-121">例如，[PostalCode] 是資料集中 PostalCode 欄位的簡單欄位運算式。</span><span class="sxs-lookup"><span data-stu-id="c53a1-121">For example, [PostalCode] is a simple field expression for the PostalCode field in a dataset.</span></span>  
  
    4.  <span data-ttu-id="c53a1-122">選取 [新增群組頁首]  。</span><span class="sxs-lookup"><span data-stu-id="c53a1-122">Select **Add group header**.</span></span> <span data-ttu-id="c53a1-123">這個選項會在群組標籤和群組總計的群組上方加入靜態資料列。</span><span class="sxs-lookup"><span data-stu-id="c53a1-123">This option adds a static row above the group for the group label and group totals.</span></span> <span data-ttu-id="c53a1-124">同樣地，您可以選取 [新增群組頁尾]  在群組底下新增靜態資料列。</span><span class="sxs-lookup"><span data-stu-id="c53a1-124">Likewise, you can select **Add group footer** to add a static row below the group.</span></span> [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     <span data-ttu-id="c53a1-125">您現在擁有一個基本的表格式報表。</span><span class="sxs-lookup"><span data-stu-id="c53a1-125">You now have a basic tabular report.</span></span> <span data-ttu-id="c53a1-126">轉譯報表時，您會看到一個包含群組執行個體值的資料行，以及一個或多個包含群組詳細資料的資料行。</span><span class="sxs-lookup"><span data-stu-id="c53a1-126">When it is rendered, you see one column with the group instance value, and one or more columns with grouped detail data.</span></span> <span data-ttu-id="c53a1-127">下圖顯示資料區可能會在設計介面上呈現的外觀。</span><span class="sxs-lookup"><span data-stu-id="c53a1-127">The following figure shows what the data region might look like on the design surface.</span></span>  
  
     <span data-ttu-id="c53a1-128">![含有群組的資料表資料區域](../media/tabledataregionwithgroup.gif "含有群組的資料表資料區域")</span><span class="sxs-lookup"><span data-stu-id="c53a1-128">![Table data region with group](../media/tabledataregionwithgroup.gif "Table data region with group")</span></span>  
  
     <span data-ttu-id="c53a1-129">下圖顯示當您檢視報表時，轉譯的資料區可能的外觀。</span><span class="sxs-lookup"><span data-stu-id="c53a1-129">The following figure shows how the rendered data region might look when you view the report.</span></span>  
  
     <span data-ttu-id="c53a1-130">![已轉譯的群組報表](../media/tablereportrendered.gif "已轉譯的群組報表")</span><span class="sxs-lookup"><span data-stu-id="c53a1-130">![Rendered grouped report](../media/tablereportrendered.gif "Rendered grouped report")</span></span>  
  
3.  <span data-ttu-id="c53a1-131">如果是階梯狀報表，您不需要第一個顯示群組執行個體的資料行，</span><span class="sxs-lookup"><span data-stu-id="c53a1-131">For a stepped report, you do not need the first column that shows the group instance.</span></span> <span data-ttu-id="c53a1-132">請改為複製群組首資料格中的值、刪除群組資料行，然後貼到群組首資料列中的第一個文字方塊。</span><span class="sxs-lookup"><span data-stu-id="c53a1-132">Instead, copy the value in the group header cell, delete the group column, and paste in the first text box in the group header row.</span></span> <span data-ttu-id="c53a1-133">若要移除群組資料行，請以滑鼠右鍵按一下群組資料行或資料格，然後按一下 [刪除資料行]  。</span><span class="sxs-lookup"><span data-stu-id="c53a1-133">To remove the group column, right-click the group column or cell, and click **Delete Columns**.</span></span> <span data-ttu-id="c53a1-134">下圖顯示資料區可能會在設計介面上呈現的外觀。</span><span class="sxs-lookup"><span data-stu-id="c53a1-134">The following figure shows what the data region might look like on the design surface.</span></span>  
  
     <span data-ttu-id="c53a1-135">![含有群組標頭資料列的資料區域](../media/tabledataregiongroupheader.gif "含有群組標頭資料列的資料區域")</span><span class="sxs-lookup"><span data-stu-id="c53a1-135">![Data region with group header row](../media/tabledataregiongroupheader.gif "Data region with group header row")</span></span>  
  
4.  <span data-ttu-id="c53a1-136">若要將詳細資料列縮排到相同資料行的群組頁首資料列之下，請變更詳細資料資料格的填補。</span><span class="sxs-lookup"><span data-stu-id="c53a1-136">To indent the detail rows under the group header row in the same column, change the padding of the detail data cell.</span></span>  
  
    1.  <span data-ttu-id="c53a1-137">選取包含您要縮排之詳細資料欄位的資料格。</span><span class="sxs-lookup"><span data-stu-id="c53a1-137">Select the cell with the detail field that you want to indent.</span></span> <span data-ttu-id="c53a1-138">該資料格的文字方塊屬性會出現在 [屬性] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="c53a1-138">The text box properties for that cell appear in the Properties pane.</span></span>  
  
    2.  <span data-ttu-id="c53a1-139">在 [屬性] 窗格的 [對齊]  底下，展開 [填補]  的屬性。</span><span class="sxs-lookup"><span data-stu-id="c53a1-139">In the Properties pane, under **Alignment**, expand the properties for **Padding**.</span></span>  
  
    3.  <span data-ttu-id="c53a1-140">在 [**左**] 中，輸入新的填補值，例如 `.5in` 。</span><span class="sxs-lookup"><span data-stu-id="c53a1-140">For **Left**, type a new padding value, such as `.5in`.</span></span> <span data-ttu-id="c53a1-141">填補會將資料格中的文字縮排您所指定的值。</span><span class="sxs-lookup"><span data-stu-id="c53a1-141">Padding indents the text in the cell by the value you specify.</span></span> <span data-ttu-id="c53a1-142">預設填補為 2 點。</span><span class="sxs-lookup"><span data-stu-id="c53a1-142">The default padding is 2 points.</span></span> <span data-ttu-id="c53a1-143">[填補] 屬性的有效值為零或正數，後面接著一個大小指示項。</span><span class="sxs-lookup"><span data-stu-id="c53a1-143">Valid values for the Padding properties are zero or a positive number, followed by a size designator.</span></span>  
  
         <span data-ttu-id="c53a1-144">大小指示項包括：</span><span class="sxs-lookup"><span data-stu-id="c53a1-144">Size designators are:</span></span>  
  
        |||  
        |-|-|  
        |`in`|<span data-ttu-id="c53a1-145">英吋 (1 英吋 = 2.54 公分)</span><span class="sxs-lookup"><span data-stu-id="c53a1-145">Inches (1 inch = 2.54 centimeters)</span></span>|  
        |`cm`|<span data-ttu-id="c53a1-146">公分</span><span class="sxs-lookup"><span data-stu-id="c53a1-146">Centimeters</span></span>|  
        |`mm`|<span data-ttu-id="c53a1-147">公釐</span><span class="sxs-lookup"><span data-stu-id="c53a1-147">Millimeters</span></span>|  
        |`pt`|<span data-ttu-id="c53a1-148">點 (1 點 = 1/72 英吋)</span><span class="sxs-lookup"><span data-stu-id="c53a1-148">Points (1 point = 1/72 inch)</span></span>|  
        |`pc`|<span data-ttu-id="c53a1-149">Picas (1 pica = 12 點)</span><span class="sxs-lookup"><span data-stu-id="c53a1-149">Picas (1 pica = 12 points)</span></span>|  
  
     <span data-ttu-id="c53a1-150">您的資料區域外觀將與下列範例類似。</span><span class="sxs-lookup"><span data-stu-id="c53a1-150">Your data region will look similar to the following example.</span></span>  
  
     <span data-ttu-id="c53a1-151">![階梯狀報表的資料區域](../media/steppedreportdataregion.gif "階梯狀報表的資料區域")</span><span class="sxs-lookup"><span data-stu-id="c53a1-151">![Data region for stepped report](../media/steppedreportdataregion.gif "Data region for stepped report")</span></span>  
  
     <span data-ttu-id="c53a1-152">**階梯狀報表配置的資料區**</span><span class="sxs-lookup"><span data-stu-id="c53a1-152">**Data Region for Stepped Report Layout**</span></span>  
  
     <span data-ttu-id="c53a1-153">在 [主資料夾]\*\*\*\* 索引標籤上，按一下 [執行]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c53a1-153">On the **Home** tab Click **Run**.</span></span> <span data-ttu-id="c53a1-154">報表在顯示群組時，將會包含子群組值的縮排層級。</span><span class="sxs-lookup"><span data-stu-id="c53a1-154">The report displays the group with indented levels for the child group values.</span></span>  
  
### <a name="to-create-a-stepped-report-with-multiple-groups"></a><span data-ttu-id="c53a1-155">若要建立包含多個群組的階梯狀報表</span><span class="sxs-lookup"><span data-stu-id="c53a1-155">To create a stepped report with multiple groups</span></span>  
  
1.  <span data-ttu-id="c53a1-156">如前一個程序所述來建立報表。</span><span class="sxs-lookup"><span data-stu-id="c53a1-156">Create a report as described in the previous procedure.</span></span>  
  
2.  <span data-ttu-id="c53a1-157">將其他群組加入到您的報表中。</span><span class="sxs-lookup"><span data-stu-id="c53a1-157">Add additional groups to your report.</span></span>  
  
    1.  <span data-ttu-id="c53a1-158">在 [資料列群組] 窗格中，以滑鼠右鍵按一下群組，然後按一下 [新增群組]\*\*\*\*，再選擇您想要新增的群組類型。</span><span class="sxs-lookup"><span data-stu-id="c53a1-158">In the Row Groups pane, right-click the group, click **Add Group**, and then choose the type of group you want to add.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="c53a1-159">有幾個方法可以將群組加入到資料區域。</span><span class="sxs-lookup"><span data-stu-id="c53a1-159">There are several ways to add groups to a data region.</span></span> <span data-ttu-id="c53a1-160">如需詳細資訊，請參閱[在資料區域中新增或刪除群組 &#40;報表產生器和 SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="c53a1-160">For more information, see [Add or Delete a Group in a Data Region &#40;Report Builder and SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md).</span></span>  
  
    2.  <span data-ttu-id="c53a1-161">在 [Tablix 群組]\*\*\*\* 對話方塊中，鍵入名稱。</span><span class="sxs-lookup"><span data-stu-id="c53a1-161">In the **Tablix Group** dialog box, type a name.</span></span>  
  
    3.  <span data-ttu-id="c53a1-162">在 [群組運算式]\*\*\*\* 中，鍵入運算式，或是選取分組所依據的資料集欄位。</span><span class="sxs-lookup"><span data-stu-id="c53a1-162">In **Group expression**, type an expression or select a dataset field to group on.</span></span> <span data-ttu-id="c53a1-163">若要建立運算式，請按一下運算式 (**fx**) 按鈕，開啟 [運算式]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c53a1-163">To create an expression, click the expression (**fx**) button to open the **Expression** dialog box.</span></span>  
  
    4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
3.  <span data-ttu-id="c53a1-164">變更顯示群組資料之資料格的填補。</span><span class="sxs-lookup"><span data-stu-id="c53a1-164">Change the padding for the cell that displays the group data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c53a1-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c53a1-165">See Also</span></span>  
 <span data-ttu-id="c53a1-166">[頁首和頁尾 &#40;報表產生器和 SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c53a1-166">[Page Headers and Footers &#40;Report Builder and SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c53a1-167">[將報表專案的格式設定 &#40;報表產生器和 SSRS&#41;](formatting-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c53a1-167">[Formatting Report Items &#40;Report Builder and SSRS&#41;](formatting-report-items-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c53a1-168">[Tablix 資料區 &#40;報表產生器和 SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c53a1-168">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c53a1-169">[資料表 &#40;報表產生器和 SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c53a1-169">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c53a1-170">[&#40;報表產生器和 SSRS&#41;的矩陣](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c53a1-170">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c53a1-171">[列出 &#40;報表產生器和 SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c53a1-171">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="c53a1-172">資料表、矩陣和清單 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="c53a1-172">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
