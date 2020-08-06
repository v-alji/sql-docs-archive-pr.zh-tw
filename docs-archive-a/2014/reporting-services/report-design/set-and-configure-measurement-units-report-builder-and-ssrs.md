---
title: 設定和設定度量單位 （報表產生器及 SSRS） |Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a15a96c3-7d2c-433e-a440-4ea051e967a9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c01523dad9a96d2d45b96474d36873bac2484343
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585031"
---
# <a name="set-and-configure-measurement-units-report-builder-and-ssrs"></a><span data-ttu-id="c4f92-102">設定度量單位 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="c4f92-102">Set and Configure Measurement Units (Report Builder and SSRS)</span></span>
  <span data-ttu-id="c4f92-103">指標提供兩個度量單位：百分比和數值。</span><span class="sxs-lookup"><span data-stu-id="c4f92-103">Indicators provide two measurement units: percentage and numeric.</span></span> <span data-ttu-id="c4f92-104">根據預設，指標會設定為使用百分比做為度量單位。</span><span class="sxs-lookup"><span data-stu-id="c4f92-104">By default, indicators are configured to use percentages as the measurement unit.</span></span> <span data-ttu-id="c4f92-105">也就是說，指派給指標集合中每個圖示的指標值取決於百分比範圍。</span><span class="sxs-lookup"><span data-stu-id="c4f92-105">This means that the indicator values assigned to each icon in the indicator set are determined by a percentage range.</span></span> <span data-ttu-id="c4f92-106">百分比範圍會在指標集合的圖示中平均分配。</span><span class="sxs-lookup"><span data-stu-id="c4f92-106">The percentage ranges are evenly divided across the icons in the indicator set.</span></span> <span data-ttu-id="c4f92-107">每個圖示代表一個指標狀態。</span><span class="sxs-lookup"><span data-stu-id="c4f92-107">Each icon represents an indicator state.</span></span> <span data-ttu-id="c4f92-108">您可以指定不同的開始與結束百分比來變更指標集合中每個圖示的百分比。</span><span class="sxs-lookup"><span data-stu-id="c4f92-108">You can change the percentages for each icon in the indicator set by specifying different start and end percentages.</span></span> <span data-ttu-id="c4f92-109">指標也會自動偵測資料中的最小值與最大值。</span><span class="sxs-lookup"><span data-stu-id="c4f92-109">Indicators also automatically detect the minimum and maximum values in the data.</span></span>  
  
 <span data-ttu-id="c4f92-110">您可以將度量單位變更為數值。</span><span class="sxs-lookup"><span data-stu-id="c4f92-110">You can change the measurement unit to be a numeric value.</span></span> <span data-ttu-id="c4f92-111">在此情況下，您不用指定資料的最小值與最大值；您只要為每個圖示提供指標所使用的開始值與結束值即可。</span><span class="sxs-lookup"><span data-stu-id="c4f92-111">In this case, you do not specify minimum or maximum for the data; instead, you provide only the start and end values for each icon that the indicator uses.</span></span>  
  
 <span data-ttu-id="c4f92-112">您可以使用運算式來設定選項，如度量單位。</span><span class="sxs-lookup"><span data-stu-id="c4f92-112">Options such as measurement units can be set by using expressions.</span></span> <span data-ttu-id="c4f92-113">如需詳細資訊，請參閱[運算式 &#40;報表產生器及 SSRS&#41;](expressions-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="c4f92-113">For more information, see [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-use-the-numeric-state-measurement-unit"></a><span data-ttu-id="c4f92-114">若要使用數值狀態度量單位</span><span class="sxs-lookup"><span data-stu-id="c4f92-114">To use the numeric state measurement unit</span></span>  
  
1.  <span data-ttu-id="c4f92-115">以滑鼠右鍵按一下您要變更的指標，然後按一下 [指標屬性]  。</span><span class="sxs-lookup"><span data-stu-id="c4f92-115">Right-click the indicator you want to change and click **Indicator Properties**.</span></span>  
  
2.  <span data-ttu-id="c4f92-116">按一下左窗格中的 **[值和狀態]** 。</span><span class="sxs-lookup"><span data-stu-id="c4f92-116">Click **Values and States** in the left pane.</span></span>  
  
3.  <span data-ttu-id="c4f92-117">在 [狀態度量單位]  清單中，按一下 [數值]  。</span><span class="sxs-lookup"><span data-stu-id="c4f92-117">In the **States Measurement Unit** list, click **Numeric**.</span></span>  
  
     <span data-ttu-id="c4f92-118">您可以選擇按一下 [運算式]  \(*fx*) 按鈕來編輯設定選項值的運算式。</span><span class="sxs-lookup"><span data-stu-id="c4f92-118">Optionally, click the **Expression** (*fx*) button to edit an expression that sets the value of the option.</span></span>  
  
4.  <span data-ttu-id="c4f92-119">針對指標集合中的每個圖示，更新 [開始]  與 [結束]  文字方塊中的值。</span><span class="sxs-lookup"><span data-stu-id="c4f92-119">For each icon in the indicator set, update the values in the **Start** and **End** text boxes.</span></span>  
  
     <span data-ttu-id="c4f92-120">您可以選擇按一下 [運算式]  \(*fx*) 按鈕來編輯設定 [開始]  和 [結束]  選項值的運算式。</span><span class="sxs-lookup"><span data-stu-id="c4f92-120">Optionally, click the **Expression** (*fx*) button to edit an expression that sets the values of the **Start** and **End** options.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c4f92-121">[開始]  和 [結束]  文字方塊中的值必須是數值。</span><span class="sxs-lookup"><span data-stu-id="c4f92-121">The values in the **Start** and **End** text boxes must be numeric.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-use-the-percentage-measurement-unit"></a><span data-ttu-id="c4f92-122">若要使用百分比度量單位</span><span class="sxs-lookup"><span data-stu-id="c4f92-122">To use the percentage measurement unit</span></span>  
  
1.  <span data-ttu-id="c4f92-123">以滑鼠右鍵按一下您要變更的指標，然後按一下 [指標屬性]  。</span><span class="sxs-lookup"><span data-stu-id="c4f92-123">Right-click the indicator you want to change and click **Indicator Properties**.</span></span>  
  
2.  <span data-ttu-id="c4f92-124">按一下左窗格中的 **[值和狀態]** 。</span><span class="sxs-lookup"><span data-stu-id="c4f92-124">Click **Values and States** in the left pane.</span></span>  
  
3.  <span data-ttu-id="c4f92-125">在 [狀態度量單位]  清單中，按一下 [百分比]  。</span><span class="sxs-lookup"><span data-stu-id="c4f92-125">In the **States Measurement Unit** list, click **Percentage**.</span></span>  
  
     <span data-ttu-id="c4f92-126">您可以選擇按一下 [運算式]  \(*fx*) 按鈕來編輯設定選項值的運算式。</span><span class="sxs-lookup"><span data-stu-id="c4f92-126">Optionally, click the **Expression** (*fx*) button to edit an expression that sets the value of the option.</span></span>  
  
4.  <span data-ttu-id="c4f92-127">或者，變更 [最小值]  與 [最大值]  選項來使用特定的值，而非自動偵測指標所使用之資料的最小值與最大值。</span><span class="sxs-lookup"><span data-stu-id="c4f92-127">Optionally, change the **Minimum** and **Maximum** options to use specific values instead of automatically detecting the minimum and maximum values of the data that the indicator uses.</span></span> <span data-ttu-id="c4f92-128">[最小值]  的值必須小於 [最大值]  的值。</span><span class="sxs-lookup"><span data-stu-id="c4f92-128">The value of **Minimum** must be smaller than the value of **Maximum**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c4f92-129">如果您明確地設定最小值和最大值，不論資料中實際的最小值和最大值為何，指標都會使用該值範圍。</span><span class="sxs-lookup"><span data-stu-id="c4f92-129">If you explicitly set minimum and maximum values, that value range is used by the indicator regardless of the actual the minimum and maximum values in the data.</span></span> <span data-ttu-id="c4f92-130">也就是說，小於最小值且大於最大值的值會排除在決定報表中顯示之指標圖示的評估之外。</span><span class="sxs-lookup"><span data-stu-id="c4f92-130">This means that values lower than the minimum and higher than the maximum are excluded from the evaluation that determine what indictor icon to show in the report.</span></span>  
  
     <span data-ttu-id="c4f92-131">您可以選擇按一下 [運算式]  \(*fx*) 按鈕來編輯設定選項值的運算式。</span><span class="sxs-lookup"><span data-stu-id="c4f92-131">Optionally, click the **Expression** (*fx*) button to edit an expression that sets the values of the option.</span></span>  
  
5.  <span data-ttu-id="c4f92-132">針對指標集合中的每個圖示，更新 [開始]  與 [結束]  文字方塊中的值。</span><span class="sxs-lookup"><span data-stu-id="c4f92-132">For each icon in the indicator set, update the values in the **Start** and **End** text boxes.</span></span>  
  
     <span data-ttu-id="c4f92-133">您可以選擇按一下 [運算式]  \(*fx*) 按鈕來編輯設定 [開始]  和 [結束]  選項值的運算式。</span><span class="sxs-lookup"><span data-stu-id="c4f92-133">Optionally, click the **Expression** (*fx*) button to edit an expression that sets the values of the **Start** and **End** options.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c4f92-134">[開始]  和 [結束]  文字方塊中的值必須是數值。</span><span class="sxs-lookup"><span data-stu-id="c4f92-134">The values in the **Start** and **End** text boxes must be numeric.</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c4f92-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4f92-135">See Also</span></span>  
 [<span data-ttu-id="c4f92-136">指標 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="c4f92-136">Indicators &#40;Report Builder and SSRS&#41;</span></span>](indicators-report-builder-and-ssrs.md)  
  
  
