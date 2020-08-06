---
title: 列出 (報表產生器和 SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c33231a5-b3a8-42e4-95bc-d05bdf2222f5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c9afb0dfabe5ccc3962d43eef30031a728514135
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594419"
---
# <a name="lists-report-builder-and-ssrs"></a><span data-ttu-id="7e69c-102">清單 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="7e69c-102">Lists (Report Builder and SSRS)</span></span>
  <span data-ttu-id="7e69c-103">清單資料區域會隨報表資料集中的每一個群組或資料列重複。</span><span class="sxs-lookup"><span data-stu-id="7e69c-103">A list data region repeats with each group or row in the report dataset.</span></span> <span data-ttu-id="7e69c-104">清單可以用於建立自由形式的報表或表單 (如發票)，也可以與其他資料區域一起使用。</span><span class="sxs-lookup"><span data-stu-id="7e69c-104">A list can be used to create free-form reports or forms, such as invoices, or in conjunction with other data regions.</span></span> <span data-ttu-id="7e69c-105">您可以定義包含任何數目之報表項目的清單。</span><span class="sxs-lookup"><span data-stu-id="7e69c-105">You can define lists that contain any number of report items.</span></span> <span data-ttu-id="7e69c-106">清單可以巢狀放在另一份清單內，以提供多個資料群組。</span><span class="sxs-lookup"><span data-stu-id="7e69c-106">A list can be nested within another list to provide multiple groups of data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7e69c-107">您可以將清單當做報表組件，與報表分開發行。</span><span class="sxs-lookup"><span data-stu-id="7e69c-107">You can publish lists separately from a report as report parts.</span></span> [!INCLUDE[ssRBrptparts](../../includes/ssrbrptparts-md.md)]  
  
 <span data-ttu-id="7e69c-108">若要快速地開始使用清單，請參閱[教學課程：建立自由格式報表 &#40;報表產生器&#41;](../tutorial-creating-a-free-form-report-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="7e69c-108">To quickly get started with lists, see [Tutorial: Creating a Free Form Report &#40;Report Builder&#41;](../tutorial-creating-a-free-form-report-report-builder.md).</span></span>  
  
 <span data-ttu-id="7e69c-109">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 範例報表包含一份使用清單的報表。</span><span class="sxs-lookup"><span data-stu-id="7e69c-109">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sample reports include a report that uses a list.</span></span> <span data-ttu-id="7e69c-110">您可以在報表產生器或報表設計師中瀏覽範例報表的報表定義，或在報表產生器或報表設計師中預覽轉譯的報表，藉以了解清單。</span><span class="sxs-lookup"><span data-stu-id="7e69c-110">You can learn about lists by exploring the report definition of the sample report in Report Builder or Report Designer or by previewing the rendered report in Report Builder or Report Designer.</span></span> <span data-ttu-id="7e69c-111">如需有關下載範例報表的詳細資訊，請參閱＜ [(SSRS) Reporting Services 範例](https://go.microsoft.com/fwlink/?LinkID=198283)＞。</span><span class="sxs-lookup"><span data-stu-id="7e69c-111">For more information about downloading the sample reports, see [(SSRS) Reporting Services Samples](https://go.microsoft.com/fwlink/?LinkID=198283).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="adding-a-list-to-your-report"></a><a name="AddingList"></a><span data-ttu-id="7e69c-112">將清單加入至您的報表</span><span class="sxs-lookup"><span data-stu-id="7e69c-112">Adding a List to Your Report</span></span>  
 <span data-ttu-id="7e69c-113">將清單從功能區上的 [插入] 索引標籤加入至設計介面。</span><span class="sxs-lookup"><span data-stu-id="7e69c-113">Add a list to the design surface from the Insert tab on ribbon.</span></span> <span data-ttu-id="7e69c-114">根據預設，清單一開始在與詳細資料群組相關聯的資料列中有一個單一資料格。</span><span class="sxs-lookup"><span data-stu-id="7e69c-114">By default, the list initially has a single cell in a row associated with the detail group.</span></span>  
  
 <span data-ttu-id="7e69c-115">![設計介面上的新清單報表項目](../media/rs-listtemplatenew.gif "設計介面上的新清單報表項目")</span><span class="sxs-lookup"><span data-stu-id="7e69c-115">![New List report item on the design surface](../media/rs-listtemplatenew.gif "New List report item on the design surface")</span></span>  
  
 <span data-ttu-id="7e69c-116">當您在設計介面上選取清單時，資料列和資料行控點隨即出現，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="7e69c-116">When you select a list on the design surface, row and column handles appear, as shown in the following figure.</span></span>  
  
 <span data-ttu-id="7e69c-117">![從工具箱新增選取的新清單](../media/rs-listtemplatenewselected.gif "從工具箱新增選取的新清單")</span><span class="sxs-lookup"><span data-stu-id="7e69c-117">![New List added from Toolbox, selected](../media/rs-listtemplatenewselected.gif "New List added from Toolbox, selected")</span></span>  
  
 <span data-ttu-id="7e69c-118">您開始使用的清單是以 Tablix 資料區域為基礎的範本。</span><span class="sxs-lookup"><span data-stu-id="7e69c-118">The list you start with is a template based on the tablix data region.</span></span> <span data-ttu-id="7e69c-119">加入清單後，您可以透過指定篩選、排序或群組運算式來變更清單的內容或外觀，或變更清單跨報表頁面顯示的方式，藉以繼續增強設計。</span><span class="sxs-lookup"><span data-stu-id="7e69c-119">After you add a list, you can continue to enhance the design by changing the content or appearance of the list by specifying filter, sort, or group expressions, or changing the way the list displays across report pages.</span></span> <span data-ttu-id="7e69c-120">如需詳細資訊，請參閱 [控制報表頁面上的 Tablix 資料區顯示 &#40;報表產生器及 SSRS&#41;](controlling-the-tablix-data-region-display-on-a-report-page.md)。</span><span class="sxs-lookup"><span data-stu-id="7e69c-120">For more information, see [Controlling the Tablix Data Region Display on a Report Page &#40;Report Builder and SSRS&#41;](controlling-the-tablix-data-region-display-on-a-report-page.md).</span></span> <span data-ttu-id="7e69c-121">雖然清單以單一資料行和資料列開始，但是您可以加入巢狀或相鄰的資料列群組或資料行群組，或加入其他詳細資料列，以便進一步繼續開發您的清單設計。</span><span class="sxs-lookup"><span data-stu-id="7e69c-121">Although the list starts with a single column and row, you can further continue to develop your list design by adding nested or adjacent row groups or column groups, or adding additional detail rows.</span></span> <span data-ttu-id="7e69c-122">如需詳細資訊，請參閱[探索 Tablix 資料區的彈性 &#40;報表產生器及 SSRS&#41;](exploring-the-flexibility-of-a-tablix-data-region-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="7e69c-122">For more information, see [Exploring the Flexibility of a Tablix Data Region &#40;Report Builder and SSRS&#41;](exploring-the-flexibility-of-a-tablix-data-region-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="displaying-data-in-a-free-form-layout"></a><a name="DisplayingLayout"></a> <span data-ttu-id="7e69c-123">以自由形式的配置顯示資料</span><span class="sxs-lookup"><span data-stu-id="7e69c-123">Displaying Data in a Free-form Layout</span></span>  
 <span data-ttu-id="7e69c-124">若要以自由形式配置而非方格組織報表資料，您可以將清單加入到設計介面中。</span><span class="sxs-lookup"><span data-stu-id="7e69c-124">To organize report data in a free-form layout instead of a grid, you can add a list to the design surface.</span></span> <span data-ttu-id="7e69c-125">將欄位從 [報表資料] 窗格拖曳至資料格。</span><span class="sxs-lookup"><span data-stu-id="7e69c-125">Drag fields from the Report Data pane to the cell.</span></span> <span data-ttu-id="7e69c-126">根據預設，資料格包含當做容器使用的矩形。</span><span class="sxs-lookup"><span data-stu-id="7e69c-126">By default, the cell contains a rectangle that acts as a container.</span></span> <span data-ttu-id="7e69c-127">在容器中移動每個欄位，直到擁有所需的設計為止。</span><span class="sxs-lookup"><span data-stu-id="7e69c-127">Move each field in the container until you have the design you want.</span></span> <span data-ttu-id="7e69c-128">當您在矩形容器中拖曳文字方塊時使用對齊線可協助您以垂直和水平方式對齊邊緣。</span><span class="sxs-lookup"><span data-stu-id="7e69c-128">Use the snaplines that appear when you drag text boxes in the rectangle container to help you align edges vertically and horizontally.</span></span> <span data-ttu-id="7e69c-129">調整資料格的大小來移除不想要的空白字元。</span><span class="sxs-lookup"><span data-stu-id="7e69c-129">Remove unwanted white space by adjusting the size of the cell.</span></span> <span data-ttu-id="7e69c-130">如需詳細資訊，請參閱[變更資料列高度或資料行寬度 &#40;報表產生器及 SSRS&#41;](change-row-height-or-column-width-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="7e69c-130">For more information, see [Change Row Height or Column Width &#40;Report Builder and SSRS&#41;](change-row-height-or-column-width-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="7e69c-131">下圖顯示的清單可顯示有關順序的資訊，包括以下欄位：Date、Order、Qty、Product、LineTotal 和影像。</span><span class="sxs-lookup"><span data-stu-id="7e69c-131">The following figure shows a list that displays information about an order, including these fields: Date, Order, Qty, Product, LineTotal, and an image.</span></span>  
  
 <span data-ttu-id="7e69c-132">![設計檢視中的清單，4 個欄位及一個影像](../media/rs-basiclistformdesign.gif "設計檢視中的清單，4 個欄位及一個影像")</span><span class="sxs-lookup"><span data-stu-id="7e69c-132">![List in design view, 4 fields and an image](../media/rs-basiclistformdesign.gif "List in design view, 4 fields and an image")</span></span>  
  
 <span data-ttu-id="7e69c-133">在預覽中，清單會重複以顯示自由形式格式的欄位資料，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="7e69c-133">In Preview, the list repeats to display the field data in the free-form format, as shown in the following figure:</span></span>  
  
 <span data-ttu-id="7e69c-134">![預覽具有 4 個欄位及一個影像的清單](../media/rs-basiclistformpreview.gif "預覽具有 4 個欄位及一個影像的清單")</span><span class="sxs-lookup"><span data-stu-id="7e69c-134">![Preview for List with 4 fields and one image](../media/rs-basiclistformpreview.gif "Preview for List with 4 fields and one image")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7e69c-135">顯示在這些圖表中的虛線也包含在內，以顯示每個欄位值的自由形式配置。</span><span class="sxs-lookup"><span data-stu-id="7e69c-135">The dotted lines displays in these figures are included to show the free-form layout for each field value.</span></span> <span data-ttu-id="7e69c-136">在實際報表中通常不會使用虛線。</span><span class="sxs-lookup"><span data-stu-id="7e69c-136">Typically, you would not use dotted lines in a production report.</span></span>  
  

  
##  <a name="displaying-data-with-one-level-of-grouping"></a><a name="DisplayingGrouping"></a> <span data-ttu-id="7e69c-137">利用一個群組層級顯示資料</span><span class="sxs-lookup"><span data-stu-id="7e69c-137">Displaying Data with One Level of Grouping</span></span>  
 <span data-ttu-id="7e69c-138">清單會自動提供容器，因此您可以使用清單來顯示包含多個檢視的群組資料。</span><span class="sxs-lookup"><span data-stu-id="7e69c-138">Because a list automatically provides a container, you can use a list to display grouped data with multiple views.</span></span> <span data-ttu-id="7e69c-139">若要變更預設清單來指定群組，請編輯詳細資料群組、指定一個新名稱，並指定一個群組運算式。</span><span class="sxs-lookup"><span data-stu-id="7e69c-139">To change the default list to specify a group, edit the Details group, specify a new name, and specify a group expression.</span></span>  
  
 <span data-ttu-id="7e69c-140">例如，您可以內嵌顯示相同資料集之不同檢視的資料表和圖表。</span><span class="sxs-lookup"><span data-stu-id="7e69c-140">For example, you can embed a table and a chart that show different views of the same dataset.</span></span> <span data-ttu-id="7e69c-141">您可以將群組加入到清單中，讓巢狀報表項目針對每個群組值重複一次。</span><span class="sxs-lookup"><span data-stu-id="7e69c-141">You can add a group to the list so that the nested report items will repeat once for every group value.</span></span> <span data-ttu-id="7e69c-142">下圖顯示依產品類別目錄分組的清單。</span><span class="sxs-lookup"><span data-stu-id="7e69c-142">The following figure shows a list grouped by product category.</span></span> <span data-ttu-id="7e69c-143">請注意，其中沒有詳細資料列，</span><span class="sxs-lookup"><span data-stu-id="7e69c-143">Notice that there is no detail row.</span></span> <span data-ttu-id="7e69c-144">而有兩個資料表以巢狀方式，並排在清單中。</span><span class="sxs-lookup"><span data-stu-id="7e69c-144">Two tables are nested side by side in the list.</span></span> <span data-ttu-id="7e69c-145">第一個資料表會顯示包含總銷售額的子類別目錄。</span><span class="sxs-lookup"><span data-stu-id="7e69c-145">The first table displays the subcategories with total sales.</span></span> <span data-ttu-id="7e69c-146">第二個資料表則顯示依地理區域分組的類別目錄，其中包含一個顯示子類別目錄分佈的圖表。</span><span class="sxs-lookup"><span data-stu-id="7e69c-146">The second table displays the category grouped by geographical area, with a chart that shows the distribution of subcategories.</span></span>  
  
 <span data-ttu-id="7e69c-147">![具有 2 個資料表的清單，其中一個資料表具有巢狀圖表](../media/rs-basiclistgroupdesign.gif "具有 2 個資料表的清單，其中一個資料表具有巢狀圖表")</span><span class="sxs-lookup"><span data-stu-id="7e69c-147">![A list with 2 tables, one with nested chart](../media/rs-basiclistgroupdesign.gif "A list with 2 tables, one with nested chart")</span></span>  
  
 <span data-ttu-id="7e69c-148">在預覽中，資料表會顯示自行車所有子類別目錄的總銷售額，而該資料表內部的資料表則顯示每個地理區域的銷售額明細。</span><span class="sxs-lookup"><span data-stu-id="7e69c-148">In Preview, the table displays total sales for all subcategories of bicycles, and the table beside it displays the breakdown of sales per geographical area.</span></span> <span data-ttu-id="7e69c-149">透過使用運算式來指定總計的背景色彩與圖表的自訂調色盤，第一個資料表也提供圖表色彩的圖例。</span><span class="sxs-lookup"><span data-stu-id="7e69c-149">By using an expression to specify the background color for the table and a custom palette for the chart, the first table also provides the legend for the chart colors.</span></span>  
  
 <span data-ttu-id="7e69c-150">![預覽，2 個資料表，其中一個資料表具有巢狀圖表](../media/rs-basiclistgrouppreview.gif "預覽，2 個資料表，其中一個資料表具有巢狀圖表")</span><span class="sxs-lookup"><span data-stu-id="7e69c-150">![Preview, 2 tables, one with nested chart](../media/rs-basiclistgrouppreview.gif "Preview, 2 tables, one with nested chart")</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="7e69c-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e69c-151">See Also</span></span>  
 <span data-ttu-id="7e69c-152">[彙總函式參考 &#40;報表產生器及 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) </span><span class="sxs-lookup"><span data-stu-id="7e69c-152">[Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) </span></span>  
 [<span data-ttu-id="7e69c-153">運算式範例 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="7e69c-153">Expression Examples &#40;Report Builder and SSRS&#41;</span></span>](expression-examples-report-builder-and-ssrs.md)  
  
  
