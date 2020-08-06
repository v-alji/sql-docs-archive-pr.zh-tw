---
title: " (報表產生器和 SSRS) ，跨多個形狀圖指定一致的色彩 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d52f68e9-2ba7-4bff-9053-4089e5164ab4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c2c89f0f8cda3b7d6ef6b2acbd0de66c87170357
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585013"
---
# <a name="specify-consistent-colors-across-multiple-shape-charts-report-builder-and-ssrs"></a><span data-ttu-id="a9be7-102">跨多個形狀圖指定一致的色彩 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="a9be7-102">Specify Consistent Colors across Multiple Shape Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="a9be7-103">在非形狀圖上，您可以根據圖表中的數列索引，從調色盤選取新的色彩。</span><span class="sxs-lookup"><span data-stu-id="a9be7-103">On non-shape charts, a new color is selected from the palette based on the index of series in the chart.</span></span> <span data-ttu-id="a9be7-104">例如，圖表上的第一個數列將會對應到調色盤中的第一個色彩。</span><span class="sxs-lookup"><span data-stu-id="a9be7-104">For example, the first series on your chart will be mapped to the first color in the palette.</span></span> <span data-ttu-id="a9be7-105">不過，對於形狀圖來說，這個行為是不同的。</span><span class="sxs-lookup"><span data-stu-id="a9be7-105">However, this behavior differs for shape charts.</span></span> <span data-ttu-id="a9be7-106">在形狀圖上，調色盤中的每個色彩都會對應到資料集中的資料點。</span><span class="sxs-lookup"><span data-stu-id="a9be7-106">On shape charts, each color in the palette is mapped to a data point in the dataset.</span></span> <span data-ttu-id="a9be7-107">例如，資料點 1 對應到調色盤中的第一個色彩，資料點 2 對應到調色盤中的第二個色彩等等。</span><span class="sxs-lookup"><span data-stu-id="a9be7-107">For example, data point 1 is mapped to the first color in the palette, data point 2 is mapped to the second color palette and so on.</span></span>  
  
 <span data-ttu-id="a9be7-108">如果資料點沒有值，則不會顯示在形狀圖上。</span><span class="sxs-lookup"><span data-stu-id="a9be7-108">If a data point has no value, it is omitted from display on a shape chart.</span></span> <span data-ttu-id="a9be7-109">也就是說，資料點會略過而不顯示任何色彩。</span><span class="sxs-lookup"><span data-stu-id="a9be7-109">This means that the data point is skipped from being colored.</span></span> <span data-ttu-id="a9be7-110">例如，如果點 2 的值為零，點 1 將會對應到調色盤中的第一個色彩，而點 3 將會對應到調色盤中的第二個色彩。</span><span class="sxs-lookup"><span data-stu-id="a9be7-110">For example, if point 2 has a value of zero, point 1 will be mapped to the first color in the palette, and point 3 will be mapped to the second color in the palette.</span></span> <span data-ttu-id="a9be7-111">這個方法相當實用，因為不需要繪製空點時，圓形圖之資料集中的空點不一定要使用調色盤色彩。</span><span class="sxs-lookup"><span data-stu-id="a9be7-111">This approach is useful because the empty points in the dataset of a pie chart do not unnecessarily use a palette color when the empty point does not need to be drawn.</span></span>  
  
 <span data-ttu-id="a9be7-112">副作用是，在報表中顯示多個圓形圖時，圓形圖可能會針對具有相同類別目錄群組的資料點顯示不同的色彩。</span><span class="sxs-lookup"><span data-stu-id="a9be7-112">As a side effect, when multiple pie charts are displayed in a report, the pie charts may display different colors for data points that have the same category grouping.</span></span> <span data-ttu-id="a9be7-113">若要解決這個問題，您需要定義對應到類別目錄群組的個別色彩，而不是個別的資料值。</span><span class="sxs-lookup"><span data-stu-id="a9be7-113">To resolve this, you need to define individual colors that map to a category group instead of individual data values.</span></span> <span data-ttu-id="a9be7-114">做法取決於形狀圖是否為資料表或矩陣中的走勢圖，或它們是否為報表本身中的形狀圖。</span><span class="sxs-lookup"><span data-stu-id="a9be7-114">How you do this depends on if the shape charts are sparklines in a table or matrix, or if they are shape charts in the report itself.</span></span>  
  
 <span data-ttu-id="a9be7-115">圖例會連接到數列，因此，您針對數列指定的任何色彩都會自動顯示在圖例上。</span><span class="sxs-lookup"><span data-stu-id="a9be7-115">The legend is connected to the series, so any color you specify for the series will automatically be shown on the legend.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-consistent-colors-across-multiple-sparkline-shape-charts-in-a-table-or-matrix"></a><span data-ttu-id="a9be7-116">若要在資料表或矩陣中跨多個走勢圖形狀圖指定一致的色彩</span><span class="sxs-lookup"><span data-stu-id="a9be7-116">To specify consistent colors across multiple sparkline shape charts in a table or matrix</span></span>  
  
1.  <span data-ttu-id="a9be7-117">按一下圖表，即可顯示 [圖表資料] 窗格。</span><span class="sxs-lookup"><span data-stu-id="a9be7-117">Click the chart to display the Chart Data pane.</span></span>  
  
2.  <span data-ttu-id="a9be7-118">在 [類別目錄群組]  區域中，以滑鼠右鍵按一下某個類別目錄，然後按一下 [類別目錄群組屬性]  。</span><span class="sxs-lookup"><span data-stu-id="a9be7-118">In the **Category Groups** area, right-click a category and click **Category Group Properties**.</span></span>  
  
3.  <span data-ttu-id="a9be7-119">在 [一般] 索引標籤的 [將群組同步處理於]  方塊中，按一下您要同步處理其色彩之類別目錄的名稱，然後按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="a9be7-119">On the General tab, in the **Synchronize groups in** box, click the name of the category for which you would like to synchronize colors, and then click **OK**.</span></span>  
  
### <a name="to-specify-consistent-colors-across-multiple-shape-charts"></a><span data-ttu-id="a9be7-120">若要跨多個形狀圖指定一致的色彩</span><span class="sxs-lookup"><span data-stu-id="a9be7-120">To specify consistent colors across multiple shape charts</span></span>  
  
1.  <span data-ttu-id="a9be7-121">以滑鼠右鍵按一下報表主體的外面，然後選取 [報表屬性]  。</span><span class="sxs-lookup"><span data-stu-id="a9be7-121">Right-click outside the body of the report, and select **Report Properties**.</span></span>  
  
2.  <span data-ttu-id="a9be7-122">在 [程式碼]  中，將下列程式碼輸入到文字方塊中。</span><span class="sxs-lookup"><span data-stu-id="a9be7-122">In **Code**, type the following code into the textbox.</span></span>  
  
    ```  
    Private colorPalette As String() = {"Color1", "Color2", "Color3"}  
    Private count As Integer = 0  
    Private mapping As New System.Collections.Hashtable()  
    Public Function GetColor(ByVal groupingValue As String) As String  
        If mapping.ContainsKey(groupingValue) Then  
            Return mapping(groupingValue)  
        End If  
        Dim c As String = colorPalette(count Mod colorPalette.Length)  
        count = count + 1  
        mapping.Add(groupingValue, c)  
        Return c  
    End Function  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="a9be7-123">您需要將 "Color1" 字串取代成您自己的色彩。</span><span class="sxs-lookup"><span data-stu-id="a9be7-123">You will need to replace the "Color1" strings with your own colors.</span></span> <span data-ttu-id="a9be7-124">您可以使用具名色彩 (例如 "Red")，或者您可以使用代表色彩的六位數十六進位值 (例如 "#FFFFFF" 代表黑色)。</span><span class="sxs-lookup"><span data-stu-id="a9be7-124">You can use named colors, for example "Red", or you can use six-digit hexadecimal value that represent the color, such as "#FFFFFF" for black.</span></span> <span data-ttu-id="a9be7-125">如果您已經定義三個以上的色彩，您將需要擴充色彩的陣列，讓陣列中的色彩數目符合形狀圖中的點數。</span><span class="sxs-lookup"><span data-stu-id="a9be7-125">If you have more than three colors defined, you will need to extend the array of colors so that the number of colors in the array matches the number of points in your shape chart.</span></span> <span data-ttu-id="a9be7-126">您可以指定包含具名色彩或色彩十六進位表示法之字串值的逗號分隔清單，以便將新的色彩加入到陣列中。</span><span class="sxs-lookup"><span data-stu-id="a9be7-126">You can add new colors to the array by specifying a comma-separated list of string values that contain named colors or hexadecimal representations of colors.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
4.  <span data-ttu-id="a9be7-127">以滑鼠右鍵按一下形狀圖，並選取 [數列屬性]  。</span><span class="sxs-lookup"><span data-stu-id="a9be7-127">Right-click on the shape chart and select **Series Properties**.</span></span>  
  
5.  <span data-ttu-id="a9be7-128">在 [填滿]  中，按一下 [運算式]  \(*fx*) 按鈕來編輯 [色彩]  屬性的運算式。</span><span class="sxs-lookup"><span data-stu-id="a9be7-128">In **Fill**, click the **Expression** (*fx*) button to edit the expression for the **Color** property.</span></span>  
  
6.  <span data-ttu-id="a9be7-129">輸入下列運算式，其中 "MyCategoryField" 是顯示在 [類別目錄群組]  區域中的欄位：</span><span class="sxs-lookup"><span data-stu-id="a9be7-129">Type the following expression, where "MyCategoryField" is the field that is displayed in the **Category Groups** area:</span></span>  
  
    ```  
    =Code.GetColor(Fields!MyCategoryField)  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a9be7-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9be7-130">See Also</span></span>  
 <span data-ttu-id="a9be7-131">[設定圖表上數列色彩的格式 &#40;報表產生器及 SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a9be7-131">[Formatting Series Colors on a Chart &#40;Report Builder and SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a9be7-132">[將斜面、浮凸與紋理樣式加入至圖表 &#40;報表產生器及 SSRS&#41;](chart-effects-add-bevel-emboss-or-texture-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="a9be7-132">[Add Bevel, Emboss, and Texture Styles to a Chart &#40;Report Builder and SSRS&#41;](chart-effects-add-bevel-emboss-or-texture-report-builder.md) </span></span>  
 <span data-ttu-id="a9be7-133">[使用調色盤定義圖表的色彩 &#40;報表產生器及 SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a9be7-133">[Define Colors on a Chart Using a Palette &#40;Report Builder and SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a9be7-134">[將空點加入至圖表 &#40;報表產生器和 SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a9be7-134">[Add Empty Points to the Chart &#40;Report Builder and SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a9be7-135">[形狀圖 &#40;報表產生器及 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a9be7-135">[Shape Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a9be7-136">[將多個資料區連結至相同的資料集 &#40;報表產生器及 SSRS&#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a9be7-136">[Linking Multiple Data Regions to the Same Dataset &#40;Report Builder and SSRS&#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a9be7-137">[巢狀資料區 &#40;報表產生器及 SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a9be7-137">[Nested Data Regions &#40;Report Builder and SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="a9be7-138">走勢圖和資料橫條 &#40;Report Builder and SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="a9be7-138">Sparklines and Data Bars &#40;Report Builder and SSRS&#41;</span></span>](sparklines-and-data-bars-report-builder-and-ssrs.md)  
  
  
