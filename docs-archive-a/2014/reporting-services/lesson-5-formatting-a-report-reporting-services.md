---
title: 第 5 課：格式化報表 (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ae46efa9-6e04-48ec-afb4-5a2314dcb05a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 00f0d780e957fd9ff995fefb1d033275a7da428d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606082"
---
# <a name="lesson-5-formatting-a-report-reporting-services"></a><span data-ttu-id="b0e91-102">Lesson 5: Formatting a Report (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="b0e91-102">Lesson 5: Formatting a Report (Reporting Services)</span></span>
  <span data-ttu-id="b0e91-103">既然您已經將資料區域和某些欄位加入到銷售訂單報表，您可以格式化日期和貨幣欄位，以及資料行標頭。</span><span class="sxs-lookup"><span data-stu-id="b0e91-103">Now that you've added a data region and some fields to the Sales Orders report, you can format the date and currency fields and the column headers.</span></span>  
  
 <span data-ttu-id="b0e91-104">本主題內容：</span><span class="sxs-lookup"><span data-stu-id="b0e91-104">In this topic:</span></span>  
  
-   [<span data-ttu-id="b0e91-105">格式化日期</span><span class="sxs-lookup"><span data-stu-id="b0e91-105">Format the Date</span></span>](#bkmk_format_date)  
  
-   [<span data-ttu-id="b0e91-106">將貨幣格式化</span><span class="sxs-lookup"><span data-stu-id="b0e91-106">Format the Currency</span></span>](#bkmk_format_currency)  
  
-   [<span data-ttu-id="b0e91-107">變更文字樣式和資料行寬度</span><span class="sxs-lookup"><span data-stu-id="b0e91-107">Change Text Style and Column Widths</span></span>](#bkmk_change_textstyle)  
  
##  <a name="format-the-date"></a><a name="bkmk_format_date"></a><span data-ttu-id="b0e91-108">格式化日期</span><span class="sxs-lookup"><span data-stu-id="b0e91-108">Format the Date</span></span>  
 <span data-ttu-id="b0e91-109">依預設，[Date] 欄位會顯示日期和時間資訊。</span><span class="sxs-lookup"><span data-stu-id="b0e91-109">The Date field displays date and time information by default.</span></span> <span data-ttu-id="b0e91-110">您可以格式化該欄位以便只顯示日期。</span><span class="sxs-lookup"><span data-stu-id="b0e91-110">You can format it to display only the date.</span></span>  
  
#### <a name="to-format-a-date-field"></a><span data-ttu-id="b0e91-111">將日期欄位格式化</span><span class="sxs-lookup"><span data-stu-id="b0e91-111">To format a date field</span></span>  
  
1.  <span data-ttu-id="b0e91-112">按一下 **[設計]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b0e91-112">Click the **Design** tab.</span></span>  
  
2.  <span data-ttu-id="b0e91-113">以滑鼠右鍵按一下含有 `[Date]` 欄位運算式的資料格，然後按一下 [文字方塊屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b0e91-113">Right-click the cell with the `[Date]` field expression and then click **Text Box Properties**.</span></span>  
  
3.  <span data-ttu-id="b0e91-114">按一下 [**數位**]，然後在 [**類別目錄**] 欄位中選取 [] `Date` 。</span><span class="sxs-lookup"><span data-stu-id="b0e91-114">Click **Number**, and then in the **Category** field, select `Date`.</span></span>  
  
4.  <span data-ttu-id="b0e91-115">在 **[類型]** 方塊中，選取 **[January 31, 2000]**。</span><span class="sxs-lookup"><span data-stu-id="b0e91-115">In the **Type** box, select **January 31, 2000**.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="b0e91-116">預覽報表以查看 `[Date]` 欄位的變更，然後變更回設計檢視。</span><span class="sxs-lookup"><span data-stu-id="b0e91-116">Preview the report to see the change to the `[Date]` field and then change back to design view.</span></span>  
  
##  <a name="format-the-currency"></a><a name="bkmk_format_currency"></a><span data-ttu-id="b0e91-117">將貨幣格式化</span><span class="sxs-lookup"><span data-stu-id="b0e91-117">Format the Currency</span></span>  
 <span data-ttu-id="b0e91-118">[LineTotal] 欄位會顯示一般數字。</span><span class="sxs-lookup"><span data-stu-id="b0e91-118">The LineTotal field displays a general number.</span></span> <span data-ttu-id="b0e91-119">格式化該欄位，將數字顯示為貨幣。</span><span class="sxs-lookup"><span data-stu-id="b0e91-119">Format it to display the number as currency.</span></span>  
  
#### <a name="to-format-a-currency-field"></a><span data-ttu-id="b0e91-120">格式化貨幣欄位</span><span class="sxs-lookup"><span data-stu-id="b0e91-120">To format a currency field</span></span>  
  
1.  <span data-ttu-id="b0e91-121">以滑鼠右鍵按一下含有 `[LineTotal]` 欄位運算式的資料格，然後按一下 [文字方塊屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b0e91-121">Right-click the cell with the `[LineTotal]` field expression and then click **Text Box Properties**.</span></span>  
  
2.  <span data-ttu-id="b0e91-122">按一下 **[數字]**，然後在 **[類別目錄]** 欄位中選取 **[貨幣]**。</span><span class="sxs-lookup"><span data-stu-id="b0e91-122">Click **Number**, and in the **Category** field, select **Currency**.</span></span>  
  
3.  <span data-ttu-id="b0e91-123">如果您的地區設定為英文 (美國)，預設值應為：</span><span class="sxs-lookup"><span data-stu-id="b0e91-123">If your regional setting is English (United States), the defaults should be:</span></span>  
  
    -   <span data-ttu-id="b0e91-124">**小數位數：2**</span><span class="sxs-lookup"><span data-stu-id="b0e91-124">**Decimal places: 2**</span></span>  
  
    -   <span data-ttu-id="b0e91-125">**負數：($12345.00)**</span><span class="sxs-lookup"><span data-stu-id="b0e91-125">**Negative numbers: ($12345.00)**</span></span>  
  
    -   <span data-ttu-id="b0e91-126">**符號：$ 英文 (美國)**</span><span class="sxs-lookup"><span data-stu-id="b0e91-126">**Symbol: $ English (United States)**</span></span>  
  
4.  <span data-ttu-id="b0e91-127">選取 [使用千分位 (,) 符號]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b0e91-127">Select **Use 1000 separator (,)**.</span></span>  
  
     <span data-ttu-id="b0e91-128">如果範例文字為：**$12,345.00**，表示您的設定正確。</span><span class="sxs-lookup"><span data-stu-id="b0e91-128">If the sample text is:**$12,345.00**, then your settings are correct.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="b0e91-129">預覽報表以查看 `[LineTotal]` 欄位的變更，然後變更回設計檢視。</span><span class="sxs-lookup"><span data-stu-id="b0e91-129">Preview the report to see the change to the `[LineTotal]` field and then change back to design view.</span></span>  
  
##  <a name="change-text-style-and-column-widths"></a><a name="bkmk_change_textstyle"></a><span data-ttu-id="b0e91-130">變更文字樣式和資料行寬度</span><span class="sxs-lookup"><span data-stu-id="b0e91-130">Change Text Style and Column Widths</span></span>  
 <span data-ttu-id="b0e91-131">您也可以變更標頭資料列的格式，以便與報表中資料的資料列區分。</span><span class="sxs-lookup"><span data-stu-id="b0e91-131">You can also change the formatting of the header row to differentiate it from the rows of data in the report.</span></span> <span data-ttu-id="b0e91-132">最後，您將調整資料行的寬度。</span><span class="sxs-lookup"><span data-stu-id="b0e91-132">Lastly, you will adjust the widths of the columns.</span></span>  
  
#### <a name="to-format-header-rows-and-table-columns"></a><span data-ttu-id="b0e91-133">格式化標頭資料列和資料表資料行</span><span class="sxs-lookup"><span data-stu-id="b0e91-133">To format header rows and table columns</span></span>  
  
1.  <span data-ttu-id="b0e91-134">按一下資料表，使資料行和資料列控點出現在資料表的上面和旁邊。</span><span class="sxs-lookup"><span data-stu-id="b0e91-134">Click the table so that column and row handles appear above and next to the table.</span></span>  
  
     <span data-ttu-id="b0e91-135">![設計具有頁首資料列和詳細資料列的資料表](../../2014/tutorials/media/rs-basictabledetailsdesign.gif "設計具有頁首資料列和詳細資料列的資料表")</span><span class="sxs-lookup"><span data-stu-id="b0e91-135">![Design, Table with header row and detail row](../../2014/tutorials/media/rs-basictabledetailsdesign.gif "Design, Table with header row and detail row")</span></span>  
  
     <span data-ttu-id="b0e91-136">沿著資料表頂端和側邊的灰色長條是資料行和資料列控點。</span><span class="sxs-lookup"><span data-stu-id="b0e91-136">The gray bars along the top and side of the table are the column and row handles.</span></span>  
  
2.  <span data-ttu-id="b0e91-137">指向資料行控點之間的線條，使游標變成雙箭頭。</span><span class="sxs-lookup"><span data-stu-id="b0e91-137">Point to the line between column handles so that the cursor changes into a double arrow.</span></span> <span data-ttu-id="b0e91-138">將資料行拖曳到所需的大小。</span><span class="sxs-lookup"><span data-stu-id="b0e91-138">Drag the columns to the size you want.</span></span>  
  
3.  <span data-ttu-id="b0e91-139">選取資料列包含資料行標頭標籤，然後從 **[格式]** 功能表指向 **[字型]** ，然後按一下 **[粗體]**。</span><span class="sxs-lookup"><span data-stu-id="b0e91-139">Select the row containing column header labels and from the **Format** menu, point to **Font** and then click **Bold**.</span></span>  
  
4.  <span data-ttu-id="b0e91-140">若要預覽報表，請按一下 [**預覽**] 索引標籤。看起來應該像這樣：</span><span class="sxs-lookup"><span data-stu-id="b0e91-140">To preview your report, click the **Preview** tab. It should look something like this:</span></span>  
  
     <span data-ttu-id="b0e91-141">![具有粗體資料行標頭的資料表預覽](../../2014/tutorials/media/rs-basictabledetailsformattedpreview.gif "具有粗體資料行標頭的資料表預覽")</span><span class="sxs-lookup"><span data-stu-id="b0e91-141">![Preview of table with bold column headers](../../2014/tutorials/media/rs-basictabledetailsformattedpreview.gif "Preview of table with bold column headers")</span></span>  
  
5.  <span data-ttu-id="b0e91-142">按一下 **[檔案]** 功能表上的 **[全部儲存]** ，即可儲存報表。</span><span class="sxs-lookup"><span data-stu-id="b0e91-142">On the **File** menu, click **Save All** to save the report.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b0e91-143">後續步驟</span><span class="sxs-lookup"><span data-stu-id="b0e91-143">Next Steps</span></span>  
 <span data-ttu-id="b0e91-144">您已經成功格式化資料行標頭和日期以及貨幣值。</span><span class="sxs-lookup"><span data-stu-id="b0e91-144">You have successfully formatted column headers and date and currency values.</span></span> <span data-ttu-id="b0e91-145">下一步，您會將群組和總計加入至報表。</span><span class="sxs-lookup"><span data-stu-id="b0e91-145">Next, you will add grouping and totals to your report.</span></span> <span data-ttu-id="b0e91-146">請參閱[第 6 課：新增群組和總計 &#40;Reporting Services&#41;](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b0e91-146">See [Lesson 6: Adding Grouping and Totals &#40;Reporting Services&#41;](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0e91-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0e91-147">See Also</span></span>  
 <span data-ttu-id="b0e91-148">[將數位和日期格式化 &#40;報表產生器和 SSRS&#41;](report-design/formatting-numbers-and-dates-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b0e91-148">[Formatting Numbers and Dates &#40;Report Builder and SSRS&#41;](report-design/formatting-numbers-and-dates-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="b0e91-149">轉譯行為 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="b0e91-149">Rendering Behaviors &#40;Report Builder  and SSRS&#41;</span></span>](report-design/rendering-behaviors-report-builder-and-ssrs.md)  
  
  
