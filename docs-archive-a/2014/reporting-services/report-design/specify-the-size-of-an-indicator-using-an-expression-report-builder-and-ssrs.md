---
title: 使用運算式指定指標的大小 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ab0b86f1-4882-4258-a2b6-c612faecfa4b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b450abb957329b8dbaa4f7f0e4c963c5f63f06b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585008"
---
# <a name="specify-the-size-of-an-indicator-using-an-expression-report-builder-and-ssrs"></a><span data-ttu-id="fafc4-102">使用運算式指定指標的大小 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="fafc4-102">Specify the Size of an Indicator Using an Expression (Report Builder and SSRS)</span></span>
  <span data-ttu-id="fafc4-103">除了色彩、方向和形狀之外，您還可以使用大小，將指標的視覺影像最大化。</span><span class="sxs-lookup"><span data-stu-id="fafc4-103">In addition to color, direction, and shape, you can use size to maximize the visual impact of indicators.</span></span>  
  
 <span data-ttu-id="fafc4-104">指標包含一個名稱為 IndicatorStates 的指標狀態集合。</span><span class="sxs-lookup"><span data-stu-id="fafc4-104">An indicator has a collection of indicator states named IndicatorStates.</span></span> <span data-ttu-id="fafc4-105">IndicatorStates 集合通常有多個狀態。</span><span class="sxs-lookup"><span data-stu-id="fafc4-105">The IndicatorStates collection typically have multiple states.</span></span> <span data-ttu-id="fafc4-106">每個狀態都是集合的成員，而且會以一個圖示表示。</span><span class="sxs-lookup"><span data-stu-id="fafc4-106">Each state is a member of the collection and is represented by an icon.</span></span> <span data-ttu-id="fafc4-107">這些所有狀態就構成 IndicatorsStates 集合。</span><span class="sxs-lookup"><span data-stu-id="fafc4-107">Together the states constitute the IndicatorsStates collection.</span></span>  
  
 <span data-ttu-id="fafc4-108">若要動態設定圖示的大小，您要在報表產生器的 [屬性] 窗格中設定 IndicatorsStates 集合的成員屬性。</span><span class="sxs-lookup"><span data-stu-id="fafc4-108">To dynamically configure the sizes of icons, you set properties of members of the IndicatorsStates collection in the Properties pane of Report Builder.</span></span> <span data-ttu-id="fafc4-109">如果看不到 **[屬性]** 窗格，按一下 **[檢視]** 索引標籤，然後選取 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="fafc4-109">If the **Properties** pane is not visible, click the **View** tab and select **Properties**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fafc4-110">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，您可以使用 **[屬性]** 視窗來設定成員屬性。</span><span class="sxs-lookup"><span data-stu-id="fafc4-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], you use the **Properties** window to set the member properties.</span></span> <span data-ttu-id="fafc4-111">如果 **[屬性]** 視窗未開啟，請按下 F4 鍵。</span><span class="sxs-lookup"><span data-stu-id="fafc4-111">If the **Properties** window is not open, press the F4 key.</span></span>  
  
 <span data-ttu-id="fafc4-112">[屬性]  窗格可存取指標之 IndicatorStates 集合的屬性。</span><span class="sxs-lookup"><span data-stu-id="fafc4-112">The **Properties** pane provides access to the properties of the IndicatorStates collection of an indicator.</span></span> <span data-ttu-id="fafc4-113">您可以使用運算式設定 IndicatorStates 集合成員的 ScaleFactor 屬性，以便將圖示設定為不同的大小。</span><span class="sxs-lookup"><span data-stu-id="fafc4-113">You configure the icons to be different sizes by setting the ScaleFactor property of the IndicatorStates collection members using an expression.</span></span> <span data-ttu-id="fafc4-114">如需詳細資訊，請參閱[運算式 &#40;報表產生器及 SSRS&#41;](expressions-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="fafc4-114">For more information, see [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="fafc4-115">此程序中所使用的運算式也用來產生不同指標大小的報表，如 [指標 &#40;報表產生器及 SSRS&#41;](indicators-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="fafc4-115">The expression used in this procedure was also used to generate the report with different sizes of indicators, shown in [Indicators &#40;Report Builder and SSRS&#41;](indicators-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-the-indicator-icon-size-using-an-expression"></a><span data-ttu-id="fafc4-116">若要使用運算式指定指標圖示大小</span><span class="sxs-lookup"><span data-stu-id="fafc4-116">To specify the indicator icon size using an expression</span></span>  
  
1.  <span data-ttu-id="fafc4-117">按一下您想要變更的指標。</span><span class="sxs-lookup"><span data-stu-id="fafc4-117">Click the indicator you want to change.</span></span>  
  
2.  <span data-ttu-id="fafc4-118">在 [屬性] 窗格中，找出 IndicatorStates 屬性。</span><span class="sxs-lookup"><span data-stu-id="fafc4-118">In the Properties pane, locate the IndicatorStates property.</span></span>  
  
     <span data-ttu-id="fafc4-119">如果 [屬性] 窗格是依類別目錄排列，您將會在 [狀態]  類別目錄中找到 IndicatorStates。</span><span class="sxs-lookup"><span data-stu-id="fafc4-119">If the Properties pane is organized by category, you will find IndicatorStates in the **States** category.</span></span>  
  
3.  <span data-ttu-id="fafc4-120">按一下 IndicatorStates 旁的省略符號 **(...)** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="fafc4-120">Click the ellipsis **(...)** button next to IndicatorStates.</span></span> <span data-ttu-id="fafc4-121">**[IndicatorState 集合編輯器]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="fafc4-121">The **IndicatorState Collection Editor** dialog box opens.</span></span>  
  
     <span data-ttu-id="fafc4-122">選取集合的所有成員。</span><span class="sxs-lookup"><span data-stu-id="fafc4-122">Select all members of the collection.</span></span>  
  
4.  <span data-ttu-id="fafc4-123">在 [複選屬性]  清單中，按一下 ScaleFactor 旁的向下箭頭，然後按一下 [運算式]  。</span><span class="sxs-lookup"><span data-stu-id="fafc4-123">In the **Multi-Select Properties** list, click the down arrow next to ScaleFactor and then click **Expression**.</span></span>  
  
5.  <span data-ttu-id="fafc4-124">在 **[運算式]** 對話方塊中，撰寫運算式。</span><span class="sxs-lookup"><span data-stu-id="fafc4-124">In the **Expression** dialog box write the expression.</span></span>  
  
     <span data-ttu-id="fafc4-125">下列範例運算式會根據 **SalesYTD** 欄位的值，將圖示變成不同的大小。</span><span class="sxs-lookup"><span data-stu-id="fafc4-125">The following sample expression makes the icon a different size based on the value of the **SalesYTD** field.</span></span>  
  
     `=IIF(Fields!SalesYTD.value = 0,0,Fields!SalesYTD.value/Max(Fields!SalesYTD.value,"Indicator"))`  
  
     <span data-ttu-id="fafc4-126">如需詳細資訊，請參閱[運算式範例 &#40;報表產生器及 SSRS&#41;](expression-examples-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="fafc4-126">For more information, see [Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md).</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fafc4-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fafc4-127">See Also</span></span>  
 [<span data-ttu-id="fafc4-128">指標 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="fafc4-128">Indicators &#40;Report Builder and SSRS&#41;</span></span>](indicators-report-builder-and-ssrs.md)  
  
  
