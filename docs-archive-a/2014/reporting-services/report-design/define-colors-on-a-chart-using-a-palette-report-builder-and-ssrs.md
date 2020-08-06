---
title: 使用調色盤定義圖表的色彩 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d95efc22-5a32-43d4-9bd2-12753e7fd395
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7db137ed87b0c84e43577dcf2936a6287abd8e36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595744"
---
# <a name="define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs"></a><span data-ttu-id="627f7-102">使用調色盤定義圖表的色彩 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="627f7-102">Define Colors on a Chart Using a Palette (Report Builder and SSRS)</span></span>
  <span data-ttu-id="627f7-103">您可以選取預先定義的調色盤，或定義自訂調色盤來變更圖表的色彩調色盤。</span><span class="sxs-lookup"><span data-stu-id="627f7-103">You can change the color palette for a chart by selecting a pre-defined palette or defining a custom palette.</span></span> <span data-ttu-id="627f7-104">自訂調色盤是報表專屬的。</span><span class="sxs-lookup"><span data-stu-id="627f7-104">Custom palettes are report-specific.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-colors-on-the-chart-using-a-built-in-color-palette"></a><span data-ttu-id="627f7-105">若要使用內建的色彩調色盤變更圖表的色彩</span><span class="sxs-lookup"><span data-stu-id="627f7-105">To change the colors on the chart using a built-in color palette</span></span>  
  
1.  <span data-ttu-id="627f7-106">開啟 [屬性] 窗格。</span><span class="sxs-lookup"><span data-stu-id="627f7-106">Open the Properties pane.</span></span>  
  
2.  <span data-ttu-id="627f7-107">在設計介面上，按一下圖表。</span><span class="sxs-lookup"><span data-stu-id="627f7-107">On the design surface, click the chart.</span></span> <span data-ttu-id="627f7-108">圖表物件的屬性會顯示在 [屬性] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="627f7-108">The properties for the chart object are displayed in the Properties pane.</span></span>  
  
     <span data-ttu-id="627f7-109">物件名稱 (預設為**Chart1** ) 就會出現在 [屬性] 窗格頂端的下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="627f7-109">The object name (**Chart1** by default) appears in the drop-down list at the top of the Properties pane.</span></span>  
  
3.  <span data-ttu-id="627f7-110">在 [圖表]  區段中，從下拉式清單為 Palette 屬性選取新的調色盤。</span><span class="sxs-lookup"><span data-stu-id="627f7-110">In the **Chart** section, for the Palette property, select a new palette from the drop-down list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="627f7-111">您無法在預先定義的調色盤中變更色彩或順序。</span><span class="sxs-lookup"><span data-stu-id="627f7-111">You cannot change the colors or order in a pre-defined palette.</span></span>  
  
### <a name="to-define-your-own-colors-on-the-chart-using-a-custom-color-palette"></a><span data-ttu-id="627f7-112">若要使用自訂色彩調色盤，在圖表上定義自己的色彩</span><span class="sxs-lookup"><span data-stu-id="627f7-112">To define your own colors on the chart using a custom color palette</span></span>  
  
1.  <span data-ttu-id="627f7-113">開啟 [屬性] 窗格。</span><span class="sxs-lookup"><span data-stu-id="627f7-113">Open the Properties pane.</span></span>  
  
2.  <span data-ttu-id="627f7-114">在設計介面上，按一下圖表。</span><span class="sxs-lookup"><span data-stu-id="627f7-114">On the design surface, click the chart.</span></span> <span data-ttu-id="627f7-115">圖表物件的屬性會顯示在 [屬性] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="627f7-115">The properties for the chart object are displayed in the Properties pane.</span></span>  
  
3.  <span data-ttu-id="627f7-116">在 [**圖表**] 區段中，針對 `Palette` 屬性選取 [**自訂**]。</span><span class="sxs-lookup"><span data-stu-id="627f7-116">In the **Chart** section, for the `Palette` property, select **Custom**.</span></span>  
  
4.  <span data-ttu-id="627f7-117">在 CustomPaletteColors 屬性中，按一下 [編輯集合] \( **...** ) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="627f7-117">In the CustomPaletteColors property, click the Edit Collection (**...**) button.</span></span> <span data-ttu-id="627f7-118">**[ReportColorExpression 集合編輯器]** 便會開啟。</span><span class="sxs-lookup"><span data-stu-id="627f7-118">The **ReportColorExpression Collection Editor** opens.</span></span>  
  
5.  <span data-ttu-id="627f7-119">按一下 **[加入]** 來加入色彩。</span><span class="sxs-lookup"><span data-stu-id="627f7-119">Click **Add** to add a color.</span></span> <span data-ttu-id="627f7-120">從下拉式清單中選取一個色彩，或選取 [運算式]，然後為特定色彩指定一個十六進位值，例如，ff6600 代表「橙色」。</span><span class="sxs-lookup"><span data-stu-id="627f7-120">Select a color from the drop-down list or select Expression and specify a hex value for a specific color, such as ff6600 for "Orange".</span></span>  
  
     <span data-ttu-id="627f7-121">如需有關十六進位值的詳細資訊，請參閱 MSDN 上的 [色彩表](https://go.microsoft.com/fwlink/?linkid=9258) 。</span><span class="sxs-lookup"><span data-stu-id="627f7-121">For more information about hex values, see [Color Table](https://go.microsoft.com/fwlink/?linkid=9258) on MSDN.</span></span>  
  
6.  <span data-ttu-id="627f7-122">按一下 **[加入]** ，將其他色彩加入到調色盤中。</span><span class="sxs-lookup"><span data-stu-id="627f7-122">Click **Add** to add more colors to the palette.</span></span>  
  
7.  <span data-ttu-id="627f7-123">在您完成後，按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="627f7-123">When you are done, click **OK**.</span></span>  
  
 <span data-ttu-id="627f7-124">如果您要使用自訂調色盤，可以藉由變更色彩的順序來變更圖表中不同序列的色彩。</span><span class="sxs-lookup"><span data-stu-id="627f7-124">If you are using a custom palette, you can change the order of the colors to change the color of different series in the chart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="627f7-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="627f7-125">See Also</span></span>  
 <span data-ttu-id="627f7-126">[設定圖表上數列色彩的格式 &#40;報表產生器及 SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="627f7-126">[Formatting Series Colors on a Chart &#40;Report Builder and SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="627f7-127">[圖表 &#40;報表產生器及 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="627f7-127">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="627f7-128">跨多個形狀圖指定一致的色彩 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="627f7-128">Specify Consistent Colors across Multiple Shape Charts &#40;Report Builder and SSRS&#41;</span></span>](shape-charts-report-builder-and-ssrs.md)  
  
  
