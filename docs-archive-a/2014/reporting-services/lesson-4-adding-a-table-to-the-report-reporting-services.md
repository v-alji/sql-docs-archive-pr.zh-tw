---
title: 第 4 課：將資料表新增至報表 (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5ddf2914-bcdd-427d-8cba-0ccb8342f819
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 52694168bd60b8e3807db6204f33a89815573093
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592519"
---
# <a name="lesson-4-adding-a-table-to-the-report-reporting-services"></a><span data-ttu-id="f621e-102">第 4 課：將資料表加入至報表 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="f621e-102">Lesson 4: Adding a Table to the Report (Reporting Services)</span></span>
  <span data-ttu-id="f621e-103">定義資料集之後，您就可以開始設計報表。</span><span class="sxs-lookup"><span data-stu-id="f621e-103">After the dataset is defined, you can start designing the report.</span></span> <span data-ttu-id="f621e-104">您可以將資料區域、文字方塊、影像和您要包含在報表中的其他項目拖放至設計介面來建立報表配置。</span><span class="sxs-lookup"><span data-stu-id="f621e-104">You create a report layout by dragging and dropping data regions, text boxes, images, and other items that you want to include in your report to the design surface.</span></span>  
  
 <span data-ttu-id="f621e-105">包含基礎資料集之重複資料列的項目稱為「資料區域」\*\*。</span><span class="sxs-lookup"><span data-stu-id="f621e-105">Items that contain repeated rows of data from underlying datasets are called *data regions*.</span></span> <span data-ttu-id="f621e-106">基本報表只有一個資料區域，但是您可以加入其他資料區域，例如，當您想要將圖表加入至表格式報表時。</span><span class="sxs-lookup"><span data-stu-id="f621e-106">A basic report will have only one data region, but you can add more, for example, if you want to add a chart to your tabular report.</span></span> <span data-ttu-id="f621e-107">加入資料區域之後，您可以將欄位加入到資料區域中。</span><span class="sxs-lookup"><span data-stu-id="f621e-107">After you add a data region, you can add fields to the data region.</span></span>  
  
### <a name="to-add-a-table-data-region-and-fields-to-a-report-layout"></a><span data-ttu-id="f621e-108">將資料表資料區域和欄位加入到報表配置中</span><span class="sxs-lookup"><span data-stu-id="f621e-108">To add a Table data region and fields to a report layout</span></span>  
  
1.  <span data-ttu-id="f621e-109">在 [工具箱]\*\*\*\* 中，按一下 [資料表]\*\*\*\*，然後按一下設計介面並拖曳滑鼠。</span><span class="sxs-lookup"><span data-stu-id="f621e-109">In the **Toolbox**, click **Table**, and then click on the design surface and drag the mouse.</span></span> <span data-ttu-id="f621e-110">報表設計師會繪製一個資料表資料區域，而且在設計介面的中央包含三個資料行。</span><span class="sxs-lookup"><span data-stu-id="f621e-110">Report Designer draws a table data region with three columns in the center of the design surface.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f621e-111">[工具箱]\*\*\*\* 可能會顯示為 [報表資料]\*\*\*\* 窗格左側的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f621e-111">The **Toolbox** may appear as a tab on the left side of the **Report Data** pane.</span></span> <span data-ttu-id="f621e-112">若要開啟 [**工具箱**]，請將指標移至 [**工具箱**] 索引標籤上。如果看不到 [**工具箱**]，請按一下 [**流覽**] 功能表上的 [**工具箱**]。</span><span class="sxs-lookup"><span data-stu-id="f621e-112">To open the **Toolbox**, move the pointer over the **Toolbox** tab. If the **Toolbox** is not visible, from the **View** menu, click **Toolbox**.</span></span>  
  
2.  <span data-ttu-id="f621e-113">在 [**報表資料**] 窗格中，展開 [ **AdventureWorksDataset** ] 資料集以顯示欄位。</span><span class="sxs-lookup"><span data-stu-id="f621e-113">In the **Report Data** pane, expand the **AdventureWorksDataset** dataset to display the fields.</span></span>  
  
3.  <span data-ttu-id="f621e-114">將 [日期] 欄位從 [報表資料]\*\*\*\* 窗格拖曳到資料表中的第一個資料行。</span><span class="sxs-lookup"><span data-stu-id="f621e-114">Drag the Date field from the **Report Data** pane to the first column in the table.</span></span>  
  
     <span data-ttu-id="f621e-115">當您將欄位放到第一個資料行時，會出現兩種情況。</span><span class="sxs-lookup"><span data-stu-id="f621e-115">When you drop the field into the first column, two things happen.</span></span> <span data-ttu-id="f621e-116">首先，資料將會顯示欄位名稱，也就是所謂的「欄位運算式」\*\*，並以方括弧括住：`[Date]`。</span><span class="sxs-lookup"><span data-stu-id="f621e-116">First, the data cell will display the field name, known as the *field expression*, in brackets: `[Date]`.</span></span> <span data-ttu-id="f621e-117">接著，資料行標頭值會自動加到標頭資料列中，就在欄位運算式的正上方。</span><span class="sxs-lookup"><span data-stu-id="f621e-117">Second, a column header value is automatically added to Header row, just above the field expression.</span></span> <span data-ttu-id="f621e-118">依預設，這個資料行是欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="f621e-118">By default, the column is the name of the field.</span></span> <span data-ttu-id="f621e-119">您可以選取標頭資料列文字，然後輸入新的名稱。</span><span class="sxs-lookup"><span data-stu-id="f621e-119">You can select the Header row text and type a new name.</span></span>  
  
4.  <span data-ttu-id="f621e-120">將 [順序] 欄位從 [報表資料]\*\*\*\* 窗格拖曳到資料表中的第二個資料行。</span><span class="sxs-lookup"><span data-stu-id="f621e-120">Drag the Order field from the **Report Data** pane to the second column in the table.</span></span>  
  
5.  <span data-ttu-id="f621e-121">將 [產品] 欄位從 [報表資料]\*\*\*\* 窗格拖曳到資料表中的第三個資料行。</span><span class="sxs-lookup"><span data-stu-id="f621e-121">Drag the Product field from the **Report Data** pane to the third column in the table.</span></span>  
  
6.  <span data-ttu-id="f621e-122">將 Qty 欄位拖曳到第三個資料行的右邊緣，直到出現垂直游標，而且滑鼠指標有一個加號 [+]。</span><span class="sxs-lookup"><span data-stu-id="f621e-122">Drag the Qty field to the right edge of the third column until you get a vertical cursor and the mouse pointer has a plus sign [+].</span></span> <span data-ttu-id="f621e-123">放開滑鼠按鈕時，就會為 `[Qty]`建立第四個資料行。</span><span class="sxs-lookup"><span data-stu-id="f621e-123">When you release the mouse button, a fourth column is created for `[Qty]`.</span></span>  
  
7.  <span data-ttu-id="f621e-124">以相同的方式加入 LineTotal 欄位，以建立第五個資料行。</span><span class="sxs-lookup"><span data-stu-id="f621e-124">Add the LineTotal field in the same way, creating a fifth column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f621e-125">資料行標頭是 Line Total。</span><span class="sxs-lookup"><span data-stu-id="f621e-125">The column header is Line Total.</span></span> <span data-ttu-id="f621e-126">報表設計師會將 LineTotal 分割成兩個字，藉以自動建立資料行的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="f621e-126">Report Designer automatically creates a friendly name for the column by splitting LineTotal into two words.</span></span>  
  
     <span data-ttu-id="f621e-127">下圖顯示已擴展這些欄位的資料表資料區域：Date、Order、Product、Qty 和 Line Total。</span><span class="sxs-lookup"><span data-stu-id="f621e-127">The following diagram shows a table data region that has been populated with these fields: Date, Order, Product, Qty, and Line Total.</span></span>  
  
     <span data-ttu-id="f621e-128">![設計具有頁首資料列和詳細資料列的資料表](../../2014/tutorials/media/rs-basictabledetailsdesign.gif "設計具有頁首資料列和詳細資料列的資料表")</span><span class="sxs-lookup"><span data-stu-id="f621e-128">![Design, Table with header row and detail row](../../2014/tutorials/media/rs-basictabledetailsdesign.gif "Design, Table with header row and detail row")</span></span>  
  
## <a name="preview-your-report"></a><span data-ttu-id="f621e-129">預覽報表</span><span class="sxs-lookup"><span data-stu-id="f621e-129">Preview Your Report</span></span>  
 <span data-ttu-id="f621e-130">預覽報表讓您不必先將報表發行到報表伺服器，就可以檢視轉譯過的報表。</span><span class="sxs-lookup"><span data-stu-id="f621e-130">Previewing a report enables you to view the rendered report without having to first publish it to a report server.</span></span> <span data-ttu-id="f621e-131">您可能想要時常在設計階段預覽您的報表。</span><span class="sxs-lookup"><span data-stu-id="f621e-131">You will probably want to preview your report frequently during design time.</span></span> <span data-ttu-id="f621e-132">此外，預覽報表也會針對設計和資料連接執行驗證，讓您能夠先更正錯誤和問題，然後再將報表發行至報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="f621e-132">Previewing the report will also run validation on the design and data connections so you can correct errors and issues before publishing the report to a report server.</span></span>  
  
#### <a name="to-preview-a-report"></a><span data-ttu-id="f621e-133">若要預覽報表</span><span class="sxs-lookup"><span data-stu-id="f621e-133">To preview a report</span></span>  
  
-   <span data-ttu-id="f621e-134">按一下 [**預覽**] 索引標籤。報表設計師執行報表，並將其顯示在預覽視圖中。</span><span class="sxs-lookup"><span data-stu-id="f621e-134">Click the **Preview** tab. Report Designer runs the report and displays it in Preview view.</span></span>  
  
     <span data-ttu-id="f621e-135">下圖顯示 [預覽] 檢視中的部分報表。</span><span class="sxs-lookup"><span data-stu-id="f621e-135">The following diagram shows part of the report in Preview view.</span></span>  
  
     <span data-ttu-id="f621e-136">![預覽、具有 5 個資料行的詳細資料列資料表](../../2014/tutorials/media/rs-basictabledetailspreview.gif "預覽、具有 5 個資料行的詳細資料列資料表")</span><span class="sxs-lookup"><span data-stu-id="f621e-136">![Preview, Detail rows of table with 5 columns](../../2014/tutorials/media/rs-basictabledetailspreview.gif "Preview, Detail rows of table with 5 columns")</span></span>  
  
     <span data-ttu-id="f621e-137">請注意，貨幣 (在 Line Total 資料行中) 具有 6 個小數位數，而且日期具有時間戳記。</span><span class="sxs-lookup"><span data-stu-id="f621e-137">Notice that the currency (in the Line Total column) has six places after the decimal, and the date has includes a time stamp.</span></span> <span data-ttu-id="f621e-138">您將在下一課中修正該格式。</span><span class="sxs-lookup"><span data-stu-id="f621e-138">You're going to fix that formatting in the next lesson.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f621e-139">按一下 **[檔案]** 功能表上的 **[全部儲存]** ，即可儲存報表。</span><span class="sxs-lookup"><span data-stu-id="f621e-139">On the **File** menu, click **Save All** to save the report.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f621e-140">後續步驟</span><span class="sxs-lookup"><span data-stu-id="f621e-140">Next Steps</span></span>  
 <span data-ttu-id="f621e-141">您已經成功將資料表資料區域加入到報表中、將欄位加入到資料區域中，並預覽過您的報表。</span><span class="sxs-lookup"><span data-stu-id="f621e-141">You have successfully added a Table data region to your report, added fields to the data region, and previewed your report.</span></span> <span data-ttu-id="f621e-142">下一步，您將格式化資料行標頭和日期以及貨幣值。</span><span class="sxs-lookup"><span data-stu-id="f621e-142">Next, you will format column headers and date and currency values.</span></span> <span data-ttu-id="f621e-143">請參閱[第 5 課：格式化報表 &#40;Reporting Services&#41;](../reporting-services/lesson-5-formatting-a-report-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="f621e-143">See [Lesson 5: Formatting a Report &#40;Reporting Services&#41;](../reporting-services/lesson-5-formatting-a-report-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f621e-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f621e-144">See Also</span></span>  
 <span data-ttu-id="f621e-145">[資料表 &#40;報表產生器和 SSRS&#41;](report-design/tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f621e-145">[Tables &#40;Report Builder  and SSRS&#41;](report-design/tables-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f621e-146">資料集欄位集合 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f621e-146">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](report-data/dataset-fields-collection-report-builder-and-ssrs.md)  
  
  
