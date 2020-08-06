---
title: KPI 瀏覽器 (Kpi 索引標籤、Cube 設計工具)  (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.kpibrowserpane.f1
ms.assetid: 2f61bde6-e6ec-4511-8645-c272374014ad
author: minewiskan
ms.author: owend
ms.openlocfilehash: 591dfb7c27842e365b78484153dbbde3713b452e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592954"
---
# <a name="kpi-browser-kpis-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="44c6f-102">KPI 瀏覽器 (KPI 索引標籤，Cube 設計師) (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="44c6f-102">KPI Browser (KPIs Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="44c6f-103">在 Cube 設計師中，使用 [KPI]\*\*\*\* 索引標籤的 [KPI 瀏覽器]\*\*\*\* 窗格，即可檢視和測試關鍵效能指標 (KPI) 的結果。</span><span class="sxs-lookup"><span data-stu-id="44c6f-103">Use the **KPI Browser** pane on the **KPIs** tab in Cube Designer to view and test the results of Key Performance Indicators (KPIs).</span></span> <span data-ttu-id="44c6f-104">流覽之前，kpi 必須先部署至 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 實例。</span><span class="sxs-lookup"><span data-stu-id="44c6f-104">KPIs must first be deployed to a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance before browsing.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="44c6f-105">此窗格只會顯示在瀏覽器檢視中。</span><span class="sxs-lookup"><span data-stu-id="44c6f-105">This pane is displayed only in browser view.</span></span>  
  
## <a name="options"></a><span data-ttu-id="44c6f-106">選項</span><span class="sxs-lookup"><span data-stu-id="44c6f-106">Options</span></span>  
 <span data-ttu-id="44c6f-107">**Subcube 方格**</span><span class="sxs-lookup"><span data-stu-id="44c6f-107">**Subcube grid**</span></span>  
 <span data-ttu-id="44c6f-108">這可用來定義 Subcube 和限制 [結果]\*\*\*\* 窗格中顯示的 KPI 結果。</span><span class="sxs-lookup"><span data-stu-id="44c6f-108">Use to define a subcube and restrict the results of the KPIs to be displayed in the **Results** pane.</span></span> <span data-ttu-id="44c6f-109">方格包含下列資料行：</span><span class="sxs-lookup"><span data-stu-id="44c6f-109">The grid contains the following columns:</span></span>  
  
 <span data-ttu-id="44c6f-110">**維度**</span><span class="sxs-lookup"><span data-stu-id="44c6f-110">**Dimension**</span></span>  
 <span data-ttu-id="44c6f-111">選取要套用此篩選的維度。</span><span class="sxs-lookup"><span data-stu-id="44c6f-111">Select the dimension to which this filter applies.</span></span>  
  
 <span data-ttu-id="44c6f-112">**階層**</span><span class="sxs-lookup"><span data-stu-id="44c6f-112">**Hierarchy**</span></span>  
 <span data-ttu-id="44c6f-113">選取要套用此篩選的階層。</span><span class="sxs-lookup"><span data-stu-id="44c6f-113">Select the hierarchy to which this filter applies.</span></span>  
  
 <span data-ttu-id="44c6f-114">**運算子**</span><span class="sxs-lookup"><span data-stu-id="44c6f-114">**Operator**</span></span>  
 <span data-ttu-id="44c6f-115">選取運算子，定義 [篩選運算式]\*\*\*\* 中的運算式如何套用至所選取階層。</span><span class="sxs-lookup"><span data-stu-id="44c6f-115">Select the operator that defines how the expression in **Filter Expression** is applied to the selected hierarchy.</span></span> <span data-ttu-id="44c6f-116">下表描述可用的運算子。</span><span class="sxs-lookup"><span data-stu-id="44c6f-116">The following table describes the available operators.</span></span>  
  
|<span data-ttu-id="44c6f-117">值</span><span class="sxs-lookup"><span data-stu-id="44c6f-117">Value</span></span>|<span data-ttu-id="44c6f-118">描述</span><span class="sxs-lookup"><span data-stu-id="44c6f-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="44c6f-119">**等於**</span><span class="sxs-lookup"><span data-stu-id="44c6f-119">**Equal**</span></span>|<span data-ttu-id="44c6f-120">結果會限制為 **[篩選運算式]** 中定義的集合。</span><span class="sxs-lookup"><span data-stu-id="44c6f-120">The results are restricted to the set defined in **Filter Expression**.</span></span>|  
|<span data-ttu-id="44c6f-121">**不等於**</span><span class="sxs-lookup"><span data-stu-id="44c6f-121">**Not Equal**</span></span>|<span data-ttu-id="44c6f-122">結果會限制為 **[篩選運算式]** 中定義之集合所排除的成員。</span><span class="sxs-lookup"><span data-stu-id="44c6f-122">The results are restricted to the members excluded by the set defined in **Filter Expression**.</span></span>|  
|<span data-ttu-id="44c6f-123">**在**</span><span class="sxs-lookup"><span data-stu-id="44c6f-123">**In**</span></span>|<span data-ttu-id="44c6f-124">結果會限制為 **[篩選運算式]** 中選擇的命名集。</span><span class="sxs-lookup"><span data-stu-id="44c6f-124">The results are restricted to the named set chosen in **Filter Expression**.</span></span>|  
|<span data-ttu-id="44c6f-125">**不在**</span><span class="sxs-lookup"><span data-stu-id="44c6f-125">**Not In**</span></span>|<span data-ttu-id="44c6f-126">結果會限制為 **[篩選運算式]** 中選擇之命名集所排除的成員。</span><span class="sxs-lookup"><span data-stu-id="44c6f-126">The results are restricted to the members excluded by the named set chosen in **Filter Expression**.</span></span>|  
|<span data-ttu-id="44c6f-127">**Contains**</span><span class="sxs-lookup"><span data-stu-id="44c6f-127">**Contains**</span></span>|<span data-ttu-id="44c6f-128">結果會限制為成員名稱中包含 **[篩選運算式]** 中的字串之成員。</span><span class="sxs-lookup"><span data-stu-id="44c6f-128">The results are restricted to members whose member names contain the string in **Filter Expression**.</span></span>|  
|<span data-ttu-id="44c6f-129">**開頭為**</span><span class="sxs-lookup"><span data-stu-id="44c6f-129">**Begins With**</span></span>|<span data-ttu-id="44c6f-130">結果會限制為成員名稱是以 **[篩選運算式]** 中的字串開頭之成員。</span><span class="sxs-lookup"><span data-stu-id="44c6f-130">The results are restricted to members whose member names begin with the string in **Filter Expression**.</span></span>|  
|<span data-ttu-id="44c6f-131">**Range (Inclusive)**</span><span class="sxs-lookup"><span data-stu-id="44c6f-131">**Range (Inclusive)**</span></span>|<span data-ttu-id="44c6f-132">結果會限制為 **[篩選運算式]** 中選擇的範圍。</span><span class="sxs-lookup"><span data-stu-id="44c6f-132">The results are restricted to the range chosen in **Filter Expression**.</span></span>|  
|<span data-ttu-id="44c6f-133">**Range (Exclusive)**</span><span class="sxs-lookup"><span data-stu-id="44c6f-133">**Range (Exclusive)**</span></span>|<span data-ttu-id="44c6f-134">結果會限制為 **[篩選運算式]** 中選擇之範圍所排除的成員。</span><span class="sxs-lookup"><span data-stu-id="44c6f-134">The results are restricted to the members excluded by the range chosen in **Filter Expression**.</span></span>|  
|<span data-ttu-id="44c6f-135">**MDX**</span><span class="sxs-lookup"><span data-stu-id="44c6f-135">**MDX**</span></span>|<span data-ttu-id="44c6f-136">結果會限制為 [篩選運算式]\*\*\*\* 中的多維度運算式 (MDX) 運算式集合。</span><span class="sxs-lookup"><span data-stu-id="44c6f-136">The results are restricted to the Multidimensional Expressions (MDX) expression set in **Filter Expression**.</span></span>|  
  
 <span data-ttu-id="44c6f-137">**篩選運算式**</span><span class="sxs-lookup"><span data-stu-id="44c6f-137">**Filter Expression**</span></span>  
 <span data-ttu-id="44c6f-138">鍵入要由 [運算子]\*\*\*\* 評估的運算式，以限制要瀏覽的 KPI 結果。</span><span class="sxs-lookup"><span data-stu-id="44c6f-138">Type the expression that is to be evaluated by **Operator**, which restricts the KPI results to be browsed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="44c6f-139">此欄位是一個動態資料輸入元素，外觀會變更以反映選取之運算子所需要的資料類型。</span><span class="sxs-lookup"><span data-stu-id="44c6f-139">This field is a dynamic data entry element, changing appearance to reflect the types of data necessary for the selected operator.</span></span>  
  
 <span data-ttu-id="44c6f-140">**結果方格**</span><span class="sxs-lookup"><span data-stu-id="44c6f-140">**Results grid**</span></span>  
 <span data-ttu-id="44c6f-141">依據 [篩選方格]\*\*\*\* 中定義的篩選，顯示 KPI 的評估值、目標、狀態及趨勢。</span><span class="sxs-lookup"><span data-stu-id="44c6f-141">Displays the evaluated value, goal, status, and trend for the KPIs, based on the filter defined in **Filter grid**.</span></span> <span data-ttu-id="44c6f-142">方格包含下列資料行：</span><span class="sxs-lookup"><span data-stu-id="44c6f-142">The grid contains the following columns:</span></span>  
  
 <span data-ttu-id="44c6f-143">**顯示結構**</span><span class="sxs-lookup"><span data-stu-id="44c6f-143">**Display Structure**</span></span>  
 <span data-ttu-id="44c6f-144">顯示 Cube 包含的 KPI，並根據每一個 KPI 的 [顯示資料夾]\*\*\*\* 或 [父 KPI]\*\*\*\* 值來組織階層。</span><span class="sxs-lookup"><span data-stu-id="44c6f-144">Displays the KPIs contained by the cube, hierarchically organized according to the **Display folder** or **Parent KPI** values for each KPI.</span></span>  
  
 <span data-ttu-id="44c6f-145">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="44c6f-145">**Value**</span></span>  
 <span data-ttu-id="44c6f-146">顯示 KPI 的值。</span><span class="sxs-lookup"><span data-stu-id="44c6f-146">Displays the value of the KPI.</span></span>  
  
 <span data-ttu-id="44c6f-147">**目標**</span><span class="sxs-lookup"><span data-stu-id="44c6f-147">**Goal**</span></span>  
 <span data-ttu-id="44c6f-148">顯示 KPI 的目標值。</span><span class="sxs-lookup"><span data-stu-id="44c6f-148">Displays the goal value of the KPI.</span></span>  
  
 <span data-ttu-id="44c6f-149">**狀態**</span><span class="sxs-lookup"><span data-stu-id="44c6f-149">**Status**</span></span>  
 <span data-ttu-id="44c6f-150">顯示 KPI 的狀態圖形。</span><span class="sxs-lookup"><span data-stu-id="44c6f-150">Displays the status graphic of the KPI.</span></span>  
  
 <span data-ttu-id="44c6f-151">**趨勢**</span><span class="sxs-lookup"><span data-stu-id="44c6f-151">**Trend**</span></span>  
 <span data-ttu-id="44c6f-152">顯示 KPI 的趨勢圖形。</span><span class="sxs-lookup"><span data-stu-id="44c6f-152">Displays the trend graphic of the KPI.</span></span>  
  
 <span data-ttu-id="44c6f-153">**Weight**</span><span class="sxs-lookup"><span data-stu-id="44c6f-153">**Weight**</span></span>  
 <span data-ttu-id="44c6f-154">顯示 KPI 的加權因數。</span><span class="sxs-lookup"><span data-stu-id="44c6f-154">Displays the weight factor of the KPI.</span></span>  
  
 <span data-ttu-id="44c6f-155">\*\* (描述) \*\*</span><span class="sxs-lookup"><span data-stu-id="44c6f-155">**(Description)**</span></span>  
 <span data-ttu-id="44c6f-156">如果有提供 KPI 的描述，則顯示資訊圖示。</span><span class="sxs-lookup"><span data-stu-id="44c6f-156">Displays an information icon if a description is provided for a KPI.</span></span>  
  
 <span data-ttu-id="44c6f-157">將游標停留在資訊圖示上，即可顯示 KPI 的工具提示 (包含描述)。</span><span class="sxs-lookup"><span data-stu-id="44c6f-157">Hover the mouse over the information icon to display a ToolTip containing the description for the KPI.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="44c6f-158">如果在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體上計算 KPI 時發生錯誤，此選項就會顯示錯誤的資訊。</span><span class="sxs-lookup"><span data-stu-id="44c6f-158">If an error occurs while calculating a KPI on the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance, this option displays information associated with the error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44c6f-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44c6f-159">See Also</span></span>  
 [<span data-ttu-id="44c6f-160">Kpi &#40;Cube 設計師&#41; &#40;Analysis Services-多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="44c6f-160">KPIs &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](kpis-cube-designer-analysis-services-multidimensional-data.md)  
  
  
