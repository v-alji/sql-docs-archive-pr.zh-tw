---
title: 將軸標籤格式化成日期或貨幣 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e9a01a74-2f51-4b35-be3a-a6138568f6cf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ffe9d903a2271db95d4b1c2ef6201d2b0f3edab3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594388"
---
# <a name="format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs"></a><span data-ttu-id="18d64-102">將軸標籤格式化成日期或貨幣 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="18d64-102">Format Axis Labels as Dates or Currencies (Report Builder and SSRS)</span></span>
  <span data-ttu-id="18d64-103">當您在座標軸上顯示適當格式化的日期時間值時，圖表會自動將這些值顯示為天。</span><span class="sxs-lookup"><span data-stu-id="18d64-103">When you show properly formatted DateTime values on an axis, a chart will automatically display these values as days.</span></span> <span data-ttu-id="18d64-104">若要為 X 軸指定日期/時間間隔 (例如月份或小時的間隔)，您必須格式化軸標籤，並將軸間隔的類型設定為有效的日期或時間間隔。</span><span class="sxs-lookup"><span data-stu-id="18d64-104">To specify a date/time interval for the x-axis, such as an interval of months or an interval of hours, you must format the axis labels and set the type of axis interval to a valid date or time interval.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="18d64-105">在直條圖與散佈圖中，水平軸 (即 X 軸」) 是類別目錄軸。</span><span class="sxs-lookup"><span data-stu-id="18d64-105">In column and scatter charts, the horizontal, or x-axis, is the category axis.</span></span> <span data-ttu-id="18d64-106">而在長條圖中，垂直軸 (即 Y 軸) 是類別目錄軸。</span><span class="sxs-lookup"><span data-stu-id="18d64-106">In bar charts, the vertical, or y-axis, is the category axis.</span></span>  
  
 <span data-ttu-id="18d64-107">為了能夠正確格式化時間間隔，X 軸上顯示的值必須評估為 <xref:System.DateTime> 資料類型。</span><span class="sxs-lookup"><span data-stu-id="18d64-107">In order to format time intervals correctly, the values displayed on the x-axis must evaluate to a <xref:System.DateTime> data type.</span></span> <span data-ttu-id="18d64-108">如果您的欄位具有 <xref:System.String>資料類型，圖表不會將間隔計算為日期或時間。</span><span class="sxs-lookup"><span data-stu-id="18d64-108">If your field has a data type of <xref:System.String>, the chart will not calculate intervals as dates or times.</span></span> <span data-ttu-id="18d64-109">如需詳細資訊，請參閱 [圖表 &#40;報表產生器及 SSRS&#41;](charts-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="18d64-109">For more information, see [Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="18d64-110">當數值加入到 Y 軸時，圖表預設不會在顯示數字之前先格式化數字。</span><span class="sxs-lookup"><span data-stu-id="18d64-110">When a numeric value is added to the y-axis, by default, the chart does not format the number before displaying it.</span></span> <span data-ttu-id="18d64-111">如果您的數值欄位是銷售數字，請考慮將數字格式化成貨幣，以增加圖表的可讀性。</span><span class="sxs-lookup"><span data-stu-id="18d64-111">If your numeric field is a sales figure, consider formatting the numbers as currencies to increase the readability of the chart.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-format-x-axis-labels-as-monthly-intervals"></a><span data-ttu-id="18d64-112">將 X 軸標籤格式化成月份間隔</span><span class="sxs-lookup"><span data-stu-id="18d64-112">To format x-axis labels as monthly intervals</span></span>  
  
1.  <span data-ttu-id="18d64-113">以滑鼠右鍵按一下圖表的水平軸 ( X 軸)，然後選取 [水平軸屬性]  。</span><span class="sxs-lookup"><span data-stu-id="18d64-113">Right-click the horizontal, or x-axis, of the chart, and select **HorizontalAxis Properties**.</span></span>  
  
2.  <span data-ttu-id="18d64-114">在 [水平軸屬性]  對話方塊中，選取 [數字]  。</span><span class="sxs-lookup"><span data-stu-id="18d64-114">In the **HorizontalAxis Properties** dialog box, select **Number**.</span></span>  
  
3.  <span data-ttu-id="18d64-115">從 [類別目錄]  清單中，選取 [日期]  。</span><span class="sxs-lookup"><span data-stu-id="18d64-115">From the **Category** list, select **Date**.</span></span> <span data-ttu-id="18d64-116">從 [類型]  清單中，選取要套用到 X 軸標籤的日期格式。</span><span class="sxs-lookup"><span data-stu-id="18d64-116">From the **Type** list, select a date format to apply to the x-axis labels.</span></span>  
  
4.  <span data-ttu-id="18d64-117">選取 [軸選項]  。</span><span class="sxs-lookup"><span data-stu-id="18d64-117">Select **Axis Options.**</span></span>  
  
5.  <span data-ttu-id="18d64-118">在 [間隔]  中，鍵入 **1**。</span><span class="sxs-lookup"><span data-stu-id="18d64-118">In **Interval**, type **1**.</span></span> <span data-ttu-id="18d64-119">在 [間隔類型]  屬性中，選取 [月]  。</span><span class="sxs-lookup"><span data-stu-id="18d64-119">In **Interval type** property, select **Months**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="18d64-120">如果您未指定間隔類型，圖表將會以日來計算間隔。</span><span class="sxs-lookup"><span data-stu-id="18d64-120">If you do not specify an interval type, the chart will calculate intervals in terms of days.</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-format-y-axis-labels-using-a-currency-format"></a><span data-ttu-id="18d64-121">使用貨幣格式格式化 Y 軸標籤</span><span class="sxs-lookup"><span data-stu-id="18d64-121">To format y-axis labels using a currency format</span></span>  
  
1.  <span data-ttu-id="18d64-122">以滑鼠右鍵按一下圖表的垂直軸 (Y 軸)，然後選取 [垂直軸屬性]  。</span><span class="sxs-lookup"><span data-stu-id="18d64-122">Right-click the vertical, or y-axis, of the chart, and select **VerticalAxis Properties**.</span></span>  
  
2.  <span data-ttu-id="18d64-123">在 [垂直軸屬性]  對話方塊中，選取 [數字]  。</span><span class="sxs-lookup"><span data-stu-id="18d64-123">In the **VerticalAxis Properties** dialog box, select **Number**.</span></span>  
  
3.  <span data-ttu-id="18d64-124">從 [類別目錄]  清單中，選取 [貨幣]  。</span><span class="sxs-lookup"><span data-stu-id="18d64-124">From the **Category** list, select **Currency**.</span></span> <span data-ttu-id="18d64-125">從 [符號]  清單中，選取要套用到 Y 軸標籤的貨幣格式。</span><span class="sxs-lookup"><span data-stu-id="18d64-125">From the **Symbol** list, select a currency format to apply to the y-axis labels.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="18d64-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18d64-126">See Also</span></span>  
 <span data-ttu-id="18d64-127">[格式化圖表上的軸標籤 &#40;報表產生器及 SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="18d64-127">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="18d64-128">[格式化圖表 &#40;報表產生器和 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="18d64-128">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="18d64-129">[指定對數刻度 &#40;報表產生器及 SSRS&#41;](specify-a-logarithmic-scale-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="18d64-129">[Specify a Logarithmic Scale &#40;Report Builder and SSRS&#41;](specify-a-logarithmic-scale-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="18d64-130">指定軸間隔 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="18d64-130">Specify an Axis Interval &#40;Report Builder and SSRS&#41;</span></span>](specify-an-axis-interval-report-builder-and-ssrs.md)  
  
  
