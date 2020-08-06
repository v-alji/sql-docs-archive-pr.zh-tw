---
title: 在量測計面板中加入指標與量測計 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4dff9b67-b483-4c51-a822-6dbe706a6840
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b1107745f54cd94abd7507a3e9b5a706ca5402de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707154"
---
# <a name="include-indicators-and-gauges-in-a-gauge-panel-report-builder-and-ssrs"></a><span data-ttu-id="69928-102">在量測計面板中加入指標與量測計 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="69928-102">Include Indicators and Gauges in a Gauge Panel (Report Builder and SSRS)</span></span>
  <span data-ttu-id="69928-103">量測計面板是最上層的容器，其中保存一個或多個量測計和指標。</span><span class="sxs-lookup"><span data-stu-id="69928-103">The gauge panel is the top-level container that holds one or more gauges and indicators.</span></span> <span data-ttu-id="69928-104">指標可以內嵌在量測計中，或置於量測計面板旁邊。</span><span class="sxs-lookup"><span data-stu-id="69928-104">Indicators can be embedded in gauges or placed next to them in the gauge panel.</span></span>  
  
 <span data-ttu-id="69928-105">如果指標和量測計在量測計面板中是相鄰的，而且顯示不同欄位中的資料，您可能要加入標籤，讓它清除量測計和指標所傳達的內容。</span><span class="sxs-lookup"><span data-stu-id="69928-105">If the indicator and gauge are adjacent in the gauge panel and show data from different fields, you might want to add labels to make it clear what data the gauge and indicator convey.</span></span>  
  
 <span data-ttu-id="69928-106">量測計和指標選項可以使用運算式來設定。</span><span class="sxs-lookup"><span data-stu-id="69928-106">Gauge and indicator options can be set by using expressions.</span></span> <span data-ttu-id="69928-107">如需詳細資訊，請參閱[運算式 &#40;報表產生器及 SSRS&#41;](expressions-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="69928-107">For more information, see [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-embed-an-indicator-in-a-gauge"></a><span data-ttu-id="69928-108">若要將指標內嵌在量測計中</span><span class="sxs-lookup"><span data-stu-id="69928-108">To embed an indicator in a gauge</span></span>  
  
1.  <span data-ttu-id="69928-109">開啟現有的報表，或建立新的報表，其中包含的資料表和矩陣含有您想要顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="69928-109">Open an existing report or create a new report that contains a table and matrix with the data you want to display.</span></span> <span data-ttu-id="69928-110">如需詳細資訊，請參閱[資料表 &#40;報表產生器及 SSRS&#41;](tables-report-builder-and-ssrs.md) 和[矩陣 &#40;報表產生器及 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="69928-110">For more information, see [Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) or [Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="69928-111">將資料行插入資料表或矩陣中。</span><span class="sxs-lookup"><span data-stu-id="69928-111">Insert a column in your table or matrix.</span></span> <span data-ttu-id="69928-112">如需詳細資訊，請參閱[插入或刪除資料行 &#40;報表產生器及 SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="69928-112">For more information, see [Insert or Delete a Column &#40;Report Builder and SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md).</span></span>  
  
3.  <span data-ttu-id="69928-113">在 [插入]\*\*\*\* 索引標籤的 [資料區]\*\*\*\* 群組中，按一下 [量測計]\*\*\*\*，然後按一下新資料行中的資料格。</span><span class="sxs-lookup"><span data-stu-id="69928-113">On the **Insert** tab, in the **Data Regions** group, click **Gauge**, and then, and then click a cell in the new column.</span></span> <span data-ttu-id="69928-114">**[選取量測計類型]** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="69928-114">The **Select Gauge Type** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="69928-115">按一下 [星形]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="69928-115">Click **Radial**.</span></span> <span data-ttu-id="69928-116">這樣會選取第一個星形量測計。</span><span class="sxs-lookup"><span data-stu-id="69928-116">The first radial gauge is selected.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="69928-117">按一下量測計。</span><span class="sxs-lookup"><span data-stu-id="69928-117">Click the gauge.</span></span> <span data-ttu-id="69928-118">[量測計資料]\*\*\*\* 窗格隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="69928-118">The **Gauge Data** pane opens.</span></span>  
  
7.  <span data-ttu-id="69928-119">在 [值]\*\*\*\* 區域的 [(未指定)]\*\*\*\* 清單方塊中，按一下您希望其值顯示在量測計中的欄位。</span><span class="sxs-lookup"><span data-stu-id="69928-119">In the **Values** area, in the **(Unspecified)** list box, click the field whose values you want to display in the gauge.</span></span> <span data-ttu-id="69928-120">或者，從報表資料集拖曳要使用的欄位。</span><span class="sxs-lookup"><span data-stu-id="69928-120">Alternatively, drag the field to use from the report dataset.</span></span>  
  
8.  <span data-ttu-id="69928-121">以滑鼠右鍵按一下量測計，按一下 [新增指標]\*\*\*\*，然後按一下 [子系]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="69928-121">Right-click the gauge, click **Add Indicator**, and then click **Child**.</span></span> <span data-ttu-id="69928-122">[選取指標樣式]\*\*\*\* 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="69928-122">The **Select Indicator Style** dialog box opens.</span></span>  
  
9. <span data-ttu-id="69928-123">在左窗格的 [Select Indicator Style] (選取指標樣式)\*\*\*\* 對話方塊中，按一下您想要的指標類型，然後按一下指標集合。</span><span class="sxs-lookup"><span data-stu-id="69928-123">In the **Select Indicator Style** dialog box, in the left pane, click the indicator type you want, and then click the indicator set.</span></span>  
  
10. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
11. <span data-ttu-id="69928-124">按一下指標。</span><span class="sxs-lookup"><span data-stu-id="69928-124">Click the indicator.</span></span> <span data-ttu-id="69928-125">[量測計資料]\*\*\*\* 窗格隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="69928-125">The **Gauge Data** pane opens.</span></span>  
  
12. <span data-ttu-id="69928-126">在 [值]\*\*\*\* 區域的 [(未指定)]\*\*\*\* 清單方塊中，按一下您希望其值顯示為指標的欄位。</span><span class="sxs-lookup"><span data-stu-id="69928-126">In the **Values** area, in the **(Unspecified)** list box, click the field whose values you want to display as an indicator.</span></span> <span data-ttu-id="69928-127">或者，從報表資料集拖曳要使用的欄位。</span><span class="sxs-lookup"><span data-stu-id="69928-127">Alternatively, drag the field to use from the report dataset.</span></span>  
  
     <span data-ttu-id="69928-128">此欄位可以與您在量測計中使用的欄位相同或相異。</span><span class="sxs-lookup"><span data-stu-id="69928-128">The field can be the same or a different field from the one you use in the gauge.</span></span>  
  
13. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-show-an-indicator-and-gauge-side-by-side"></a><span data-ttu-id="69928-129">若要並排顯示指標及量測計</span><span class="sxs-lookup"><span data-stu-id="69928-129">To show an indicator and gauge side by side</span></span>  
  
1.  <span data-ttu-id="69928-130">開啟現有的報表，或建立新的報表，其中包含的資料表和矩陣含有您想要顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="69928-130">Open an existing report or create a new report that contains a table and matrix with the data you want to display.</span></span> <span data-ttu-id="69928-131">如需詳細資訊，請參閱[資料表 &#40;報表產生器及 SSRS&#41;](tables-report-builder-and-ssrs.md) 和[矩陣 &#40;報表產生器及 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="69928-131">For more information, see [Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) or [Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="69928-132">將資料行插入資料表或矩陣中。</span><span class="sxs-lookup"><span data-stu-id="69928-132">Insert a column in your table or matrix.</span></span> <span data-ttu-id="69928-133">如需詳細資訊，請參閱[插入或刪除資料行 &#40;報表產生器及 SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="69928-133">For more information, see [Insert or Delete a Column &#40;Report Builder and SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md).</span></span>  
  
3.  <span data-ttu-id="69928-134">在 [插入]\*\*\*\* 索引標籤的 [資料區]\*\*\*\* 群組中，按一下 [量測計]\*\*\*\*，然後按一下您插入之資料行中的資料格。</span><span class="sxs-lookup"><span data-stu-id="69928-134">On the **Insert** tab, in the **Data Regions** group, click **Gauge**, and then click a cell in the column you inserted.</span></span> <span data-ttu-id="69928-135">[選取量測計類型]\*\*\*\* 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="69928-135">The **Select Gauge Type** dialog appears.</span></span>  
  
4.  <span data-ttu-id="69928-136">按一下 [星形]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="69928-136">Click **Radial**.</span></span> <span data-ttu-id="69928-137">這樣會選取第一個星形量測計。</span><span class="sxs-lookup"><span data-stu-id="69928-137">The first radial gauge is selected.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="69928-138">按一下量測計。</span><span class="sxs-lookup"><span data-stu-id="69928-138">Click the gauge.</span></span> <span data-ttu-id="69928-139">[量測計資料]\*\*\*\* 窗格隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="69928-139">The **Gauge Data** pane opens.</span></span>  
  
7.  <span data-ttu-id="69928-140">在 [值]\*\*\*\* 區域的 [(未指定)]\*\*\*\* 清單方塊中，按一下您希望其值顯示在量測計中的欄位。</span><span class="sxs-lookup"><span data-stu-id="69928-140">In the **Values** area, in the **(Unspecified)** list box, click the field whose values you want to display in the gauge.</span></span> <span data-ttu-id="69928-141">或者，從報表資料集拖曳要使用的欄位。</span><span class="sxs-lookup"><span data-stu-id="69928-141">Alternatively, drag the field to use from the report dataset.</span></span>  
  
8.  <span data-ttu-id="69928-142">以滑鼠右鍵按一下量測計，按一下 [新增指標]\*\*\*\*，然後按一下 [相鄰]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="69928-142">Right-click the gauge, click **Add Indicator**, and then click **Adjacent**.</span></span> <span data-ttu-id="69928-143">[選取指標樣式]\*\*\*\* 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="69928-143">The **Select Indicator Style** dialog box opens.</span></span>  
  
9. <span data-ttu-id="69928-144">在左窗格的 [Select Indicator Style] (選取指標樣式)\*\*\*\* 對話方塊中，按一下您想要的指標類型，然後按一下指標集合。</span><span class="sxs-lookup"><span data-stu-id="69928-144">In the **Select Indicator Style** dialog box, in the left pane, click the indicator type you want, and then click the indicator set.</span></span>  
  
10. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
11. <span data-ttu-id="69928-145">按一下指標。</span><span class="sxs-lookup"><span data-stu-id="69928-145">Click the indicator.</span></span> <span data-ttu-id="69928-146">[量測計資料]\*\*\*\* 窗格隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="69928-146">The **Gauge Data** pane opens.</span></span>  
  
12. <span data-ttu-id="69928-147">在 [值]\*\*\*\* 區域的 [(未指定)]\*\*\*\* 清單方塊中，按一下您希望其值顯示為指標的欄位。</span><span class="sxs-lookup"><span data-stu-id="69928-147">In the **Values** area, in the **(Unspecified)** list box, click the field whose values you want to display as an indicator.</span></span> <span data-ttu-id="69928-148">或者，從報表資料集拖曳要使用的欄位。</span><span class="sxs-lookup"><span data-stu-id="69928-148">Alternatively, drag the field to use from the report dataset.</span></span>  
  
     <span data-ttu-id="69928-149">此欄位可以與您在量測計中使用的欄位相同或相異。</span><span class="sxs-lookup"><span data-stu-id="69928-149">The field can be the same or a different field from the one you use in the gauge.</span></span>  
  
13. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
14. <span data-ttu-id="69928-150">以滑鼠右鍵按一下量測計面板，然後按一下 [新增標籤]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="69928-150">Right-click the gauge panel and click **Add Label**.</span></span> <span data-ttu-id="69928-151">標籤就會加入至量測計面板。</span><span class="sxs-lookup"><span data-stu-id="69928-151">A label is added to the gauge panel.</span></span> <span data-ttu-id="69928-152">再重複一次。</span><span class="sxs-lookup"><span data-stu-id="69928-152">Repeat one more time.</span></span>  
  
     <span data-ttu-id="69928-153">量測計面板有兩個標籤。</span><span class="sxs-lookup"><span data-stu-id="69928-153">The gauge panel has two labels.</span></span>  
  
15. <span data-ttu-id="69928-154">將每個標籤拖曳到量測計或指標附近的位置。</span><span class="sxs-lookup"><span data-stu-id="69928-154">Drag each label to a location near the gauge or indicator.</span></span>  
  
16. <span data-ttu-id="69928-155">以滑鼠右鍵按一下量測計附近的標籤，按一下 [標籤屬性]\*\*\*\*，然後在 [文字]\*\*\*\* 方塊中鍵入您想要的文字。</span><span class="sxs-lookup"><span data-stu-id="69928-155">Right-click the label near the gauge, click **Label Properties**,and type the text you want in the **Text** box.</span></span>  
  
17. <span data-ttu-id="69928-156">以滑鼠右鍵按一下指標附近的標籤，按一下 [標籤屬性]\*\*\*\*，然後在 [文字]\*\*\*\* 方塊中鍵入您想要的文字。</span><span class="sxs-lookup"><span data-stu-id="69928-156">Right-click the label near the indicator, click **Label Properties**,and type the text you want in the **Text** box.</span></span>  
  
18. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="69928-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69928-157">See Also</span></span>  
 [<span data-ttu-id="69928-158">指標 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="69928-158">Indicators &#40;Report Builder and SSRS&#41;</span></span>](indicators-report-builder-and-ssrs.md)  
  
  
