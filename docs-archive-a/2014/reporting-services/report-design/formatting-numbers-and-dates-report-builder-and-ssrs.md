---
title: 格式化數字和日期 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.placeholderproperties.number.f1
- sql12.rtp.rptdesigner.serieslabelproperties.number.f1
- "10127"
- sql12.rtp.rptdesigner.axisproperties.number.f1
- "10130"
- "10286"
- sql12.rtp.rptdesigner.textboxproperties.number.f1
- "10285"
ms.assetid: 6de1a725-9f06-4708-be26-2d55e442e344
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 597ff535e72bc174cc6f9bd5a226e95641ba8a4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686814"
---
# <a name="formatting-numbers-and-dates-report-builder-and-ssrs"></a><span data-ttu-id="9dc6d-102">格式化數字和日期 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="9dc6d-102">Formatting Numbers and Dates (Report Builder and SSRS)</span></span>
  <span data-ttu-id="9dc6d-103">您可以從對應資料區之 **[屬性]** 對話方塊的 **[數字]** 頁面選取一種格式，藉以格式化資料區中的數字和日期。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-103">You can format numbers and dates in data regions by selecting a format from the **Number** page of the corresponding data region's **Properties** dialog box.</span></span>  
  
 <span data-ttu-id="9dc6d-104">若要在文字方塊報表項目中指定格式字串，您需要選取要格式化的項目，按一下滑鼠右鍵，選取 **[文字方塊屬性]** ，然後按一下 **[數字]** 。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-104">To specify format strings within a text box report item, you need to select the item that you want to format, right-click, select **Text Box Properties**, and then click **Number**.</span></span> <span data-ttu-id="9dc6d-105">您可以使用相同的方式格式化資料表或矩陣資料區中的個別資料格，因為資料表或矩陣資料區中的資料格為個別的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-105">You can format individual cells in a table or matrix data region in the same manner, because cells in a table or matrix are individual text boxes.</span></span>  
  
 <span data-ttu-id="9dc6d-106">圖表資料區通常會顯示類別目錄 (x) 軸上的日期，以及值 (y) 軸上的值。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-106">A chart data region commonly shows dates along the category (x) axis, and values along the value (y) axis.</span></span> <span data-ttu-id="9dc6d-107">若要指定圖表中的格式，請以滑鼠右鍵按一下軸，然後選取 **[軸屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-107">To specify formatting in a chart, right-click an axis and select **Axis Properties**.</span></span> <span data-ttu-id="9dc6d-108">在值軸上，您僅能指定數字的格式。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-108">On the value axis, you can specify formats only for numbers.</span></span> <span data-ttu-id="9dc6d-109">如需詳細資訊，請參閱[格式化圖表上的軸標籤 &#40;報表產生器及 SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-109">For more information, see [Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="9dc6d-110">若要指定量測計資料區中的格式，以滑鼠右鍵按一下量測計的標尺，然後選取 **[星形標尺屬性]** 或 **[線性標尺屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-110">To specify formatting in a Gauge data region, right-click the scale of the gauge and select **Radial Scale Properties** or **Linear Scale Properties**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9dc6d-111">如果您想要使用的部分格式選項呈現灰色，這表示那些格式選項與資料來源中所設定之欄位的資料類型不相容。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-111">If some formatting options you want to use are grayed out, it means that those formatting options are not compatible the field's data type, which is set in the data source.</span></span> <span data-ttu-id="9dc6d-112">例如，如果該欄位包含數值，但是欄位的資料類型為「字串」，則無法套用數值資料格式選項，例如貨幣或十進位。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-112">For example, if the field contains number values but the field's data type is String, you cannot apply numerical data formatting options such as currency or decimals.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="considerations-for-formatting-numbers-and-dates"></a><span data-ttu-id="9dc6d-113">格式化數字和日期的考量</span><span class="sxs-lookup"><span data-stu-id="9dc6d-113">Considerations for Formatting Numbers and Dates</span></span>  
 <span data-ttu-id="9dc6d-114">格式化報表中的數字和日期之前，請考慮下列事項：</span><span class="sxs-lookup"><span data-stu-id="9dc6d-114">Before you format numbers and dates in your report, consider the following:</span></span>  
  
-   <span data-ttu-id="9dc6d-115">根據預設，數字會經過格式化以反映用戶端電腦上的文化特性設定。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-115">By default, numbers are formatted to reflect the cultural settings on the client computer.</span></span> <span data-ttu-id="9dc6d-116">使用格式字串來指定顯示數字的方式，因此不管檢視報表的人身在何處，格式都是一致的。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-116">Use formatting strings to specify how numbers are displayed so that formatting is consistent regardless of where the person who is viewing the report is located.</span></span>  
  
-   <span data-ttu-id="9dc6d-117">在 **[數字]** 頁面上提供的格式為 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 標準數值格式字串的子集。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-117">The formats provided on the **Number** page are a subset of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] standard numeric format strings.</span></span> <span data-ttu-id="9dc6d-118">若要使用對話方塊中沒有顯示的自訂格式來格式化數字或日期，您可以針對數字或日期使用任何 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 格式字串。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-118">To format a number or date using a custom format that is not shown in the dialog box, you can use any [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] format strings for numbers or dates.</span></span> <span data-ttu-id="9dc6d-119">如需有關自訂格式字串的詳細資訊，請參閱 MSDN 上的＜ [格式化型別](https://go.microsoft.com/fwlink/?LinkId=112024) ＞主題。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-119">For more information about custom format strings, see the [Formatting Types](https://go.microsoft.com/fwlink/?LinkId=112024) topic on MSDN.</span></span>  
  
-   <span data-ttu-id="9dc6d-120">如果已經指定自訂格式字串，其優先順序會高於文化專用的預設值。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-120">If a custom format string has been specified, it has a higher priority over default settings that are culture-specific.</span></span> <span data-ttu-id="9dc6d-121">例如，假設您設定 "#,###" 的自訂格式字串，將數字 1234 顯示為 1,234。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-121">For example, suppose you set a custom format string of "#,###" to show the number 1234 as 1,234.</span></span> <span data-ttu-id="9dc6d-122">這對於美國的使用者與歐洲的使用者可能代表不同的意義。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-122">This may have different meaning to users in the United States than it does to users in Europe.</span></span> <span data-ttu-id="9dc6d-123">在您指定自訂格式之前，請考慮您選擇的格式影響不同文化的使用者檢視報表的方式。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-123">Before you specify a custom format, consider how the format you choose will affect users of different cultures who may view the report.</span></span>  
  
-   <span data-ttu-id="9dc6d-124">如果您指定無效的格式字串，格式化的文字會解譯為覆寫格式的常值字串。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-124">If you specify an invalid format string, the formatted text is interpreted as a literal string which overrides the formatting.</span></span>  
  
-   <span data-ttu-id="9dc6d-125">如果您要在相同的文字方塊中格式化數字和字串的混合時，請考慮使用預留位置來分別格式化數字與其餘文字。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-125">If you are formatting a mix of numbers and characters in the same text box, consider using a placeholder to format the number separately from the rest of the text.</span></span> <span data-ttu-id="9dc6d-126">如需詳細資訊，請參閱 [格式化文字和預留位置 &#40;報表產生器及 SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md)(建立發票和表單的清單)。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-126">For more information, see [Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md).</span></span> <span data-ttu-id="9dc6d-127">如果在文字方塊上針對 Format 屬性指定的格式字串無效，則會略過該格式字串。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-127">If an invalid format string is specified for the Format property on the text box, the format string is ignored.</span></span> <span data-ttu-id="9dc6d-128">如果在圖表或量測計上針對 Format 屬性指定的格式字串無效，您所指定的格式字串會解譯為字串，而且不會套用該格式。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-128">If an invalid format string is specified for the Format property on the chart or gauge, the format string that you specified is interpreted as a string and formatting is not applied.</span></span>  
  
-   <span data-ttu-id="9dc6d-129">如果您選取 **[類別目錄]** 底下的 **[貨幣]** ，並核取 **[值的顯示單位]** ，您可以選取 **[千]** 、 **[百萬]** 或 **[十億]** 來使用財務格式顯示數值。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-129">If you select **Currency** under **Category** and you check **Show values in**, you can select **Thousands**, **Millions**, or **Billions** to display numbers using financial formats.</span></span> <span data-ttu-id="9dc6d-130">例如，如果欄位值為 1,789,905,394，而且您選取 **[十億]** 並指定 2 位小數位數，顯示在報表中的值為 1.78。</span><span class="sxs-lookup"><span data-stu-id="9dc6d-130">For example, if the field value is 1,789,905,394 and you select **Billions** and specify 2 decimal places, the value displayed in the report is 1.78.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dc6d-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9dc6d-131">See Also</span></span>  
 <span data-ttu-id="9dc6d-132">[格式化文字和預留位置 &#40;報表產生器及 SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9dc6d-132">[Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="9dc6d-133">[格式化線條、色彩和影像 &#40;報表產生器及 SSRS&#41;](images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9dc6d-133">[Formatting Lines, Colors, and Images &#40;Report Builder and SSRS&#41;](images-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="9dc6d-134">[格式化圖表 &#40;報表產生器和 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9dc6d-134">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="9dc6d-135">[將軸標籤格式化成日期或貨幣 &#40;報表產生器及 SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9dc6d-135">[Format Axis Labels as Dates or Currencies &#40;Report Builder and SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="9dc6d-136">格式化量測計上的標尺 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9dc6d-136">Formatting Scales on a Gauge &#40;Report Builder and SSRS&#41;</span></span>](formatting-scales-on-a-gauge-report-builder-and-ssrs.md)  
  
  
