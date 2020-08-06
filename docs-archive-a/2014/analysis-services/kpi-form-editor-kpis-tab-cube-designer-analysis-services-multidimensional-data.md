---
title: KPI 表單編輯器 (Kpi 索引標籤、Cube 設計工具)  (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.kpidefinitionpane.f1
ms.assetid: 45c6453a-bbe2-4ca5-836e-c7ef11cfcb65
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3c88d6fcec60634f37ddad8b6d0f5cb2124fa1cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592951"
---
# <a name="kpi-form-editor-kpis-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="7a1fc-102">KPI 表單編輯器 (KPI 索引標籤，Cube 設計工具) (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="7a1fc-102">KPI Form Editor (KPIs Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="7a1fc-103">在 Cube 設計師的 [KPI]\*\*\*\* 索引標籤上，使用 [KPI 表單編輯器]\*\*\*\* 窗格來建立或修改選取的關鍵效能指標 (KPI)。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-103">Use the **KPI Form Editor** pane on the **KPIs** tab in Cube Designer to create or modify the selected Key Performance Indicator (KPI).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7a1fc-104">此窗格只會以表單檢視方式顯示。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-104">This pane is displayed only in form view.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7a1fc-105">選項。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-105">Options</span></span>  
 <span data-ttu-id="7a1fc-106">**名稱**</span><span class="sxs-lookup"><span data-stu-id="7a1fc-106">**Name**</span></span>  
 <span data-ttu-id="7a1fc-107">鍵入 KPI 的名稱。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-107">Type the name of the KPI.</span></span>  
  
 <span data-ttu-id="7a1fc-108">**相關聯的量值群組**</span><span class="sxs-lookup"><span data-stu-id="7a1fc-108">**Associated measure group**</span></span>  
 <span data-ttu-id="7a1fc-109">選取與 KPI 相關聯的量值群組。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-109">Select the measure group associated with the KPI.</span></span> <span data-ttu-id="7a1fc-110">用戶端應用程式可以使用此資訊，來決定當使用者瀏覽此 KPI 時可以使用的維度。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-110">The client application can use this information to determine which dimensions are available when the user browses this KPI.</span></span>  
  
 <span data-ttu-id="7a1fc-111">**值運算式**</span><span class="sxs-lookup"><span data-stu-id="7a1fc-111">**Value Expression**</span></span>  
 <span data-ttu-id="7a1fc-112">展開即可檢視或編輯 KPI 值的多維度運算式 (MDX) 運算式。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-112">Expand to view or edit the Multidimensional Expressions (MDX) expression for the value of the KPI.</span></span>  
  
 <span data-ttu-id="7a1fc-113">鍵入會傳回 KPI 值的 MDX 運算式。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-113">Type the MDX expression that returns the value of the KPI.</span></span>  
  
 <span data-ttu-id="7a1fc-114">從 **[計算工具]** 窗格中，將選取的元素拖曳到這個選項，以包括所選元素的 MDX 語法。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-114">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="7a1fc-115">**目標運算式**</span><span class="sxs-lookup"><span data-stu-id="7a1fc-115">**Goal Expression**</span></span>  
 <span data-ttu-id="7a1fc-116">展開即可檢視或編輯 KPI 目標值的 MDX 運算式。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-116">Expand to view or edit the MDX expression for the goal value of the KPI.</span></span>  
  
 <span data-ttu-id="7a1fc-117">鍵入當 KPI 執行時會傳回 KPI 目標值的 MDX 運算式。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-117">Type the MDX expression that returns the goal value of the KPI when the KPI is run.</span></span>  
  
 <span data-ttu-id="7a1fc-118">從 **[計算工具]** 窗格中，將選取的元素拖曳到這個選項，以包括所選元素的 MDX 語法。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-118">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="7a1fc-119">**狀態**</span><span class="sxs-lookup"><span data-stu-id="7a1fc-119">**Status**</span></span>  
 <span data-ttu-id="7a1fc-120">展開即可編輯 [狀態圖形]\*\*\*\* 和 [狀態運算式]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-120">Expand to view the **Status graphic** and **Status expression** options.</span></span>  
  
 <span data-ttu-id="7a1fc-121">**狀態圖形**</span><span class="sxs-lookup"><span data-stu-id="7a1fc-121">**Status graphic**</span></span>  
 <span data-ttu-id="7a1fc-122">選取用戶端應用程式在圖形表單中用來代表狀態值的圖形。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-122">Select the graphic to be used by the client application to represent the status value in graphical form.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7a1fc-123">用戶端應用程式可以支援選取的圖形，或使用適當的替代項目來取代。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-123">The client application can support the selected graphic or replace it with an appropriate alternative.</span></span>  
  
 <span data-ttu-id="7a1fc-124">**狀態運算式**</span><span class="sxs-lookup"><span data-stu-id="7a1fc-124">**Status expression**</span></span>  
 <span data-ttu-id="7a1fc-125">鍵入當 KPI 執行時會傳回 KPI 狀態值的 MDX 運算式。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-125">Type the MDX expression that returns the status value of the KPI when the KPI is run.</span></span>  
  
 <span data-ttu-id="7a1fc-126">從 **[計算工具]** 窗格中，將選取的元素拖曳到這個選項，以包括所選元素的 MDX 語法。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-126">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="7a1fc-127">建議此運算式傳回介於-1 和1之間的十進位數。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-127">It is recommended that this expression returns a decimal number between -1 and 1.</span></span> <span data-ttu-id="7a1fc-128">較低的數字代表負值狀況，而較高的數字代表正值狀況。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-128">A lower number represents a negative situation, while a higher number represents a positive situation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7a1fc-129">低於-1 和以上的值是可能的，但協力廠商用戶端應用程式可能無法正確地加以解讀。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-129">Values below -1 and above 1 are possible but may not be interpreted correctly by third-party client applications.</span></span>  
  
 <span data-ttu-id="7a1fc-130">**趨勢**</span><span class="sxs-lookup"><span data-stu-id="7a1fc-130">**Trend**</span></span>  
 <span data-ttu-id="7a1fc-131">展開即可編輯 [趨勢圖形]\*\*\*\* 和 [趨勢運算式]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-131">Expand to view the **Trend graphic** and **Trend expression** options.</span></span>  
  
 <span data-ttu-id="7a1fc-132">**趨勢圖形**</span><span class="sxs-lookup"><span data-stu-id="7a1fc-132">**Trend graphic**</span></span>  
 <span data-ttu-id="7a1fc-133">選取用戶端應用程式在圖形表單中用來代表趨勢值的圖形。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-133">Select the graphic to be used by the client application to represent the trend value in graphical form.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7a1fc-134">用戶端應用程式可以支援選取的圖形，或使用適當的替代項目來取代。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-134">The client application can support the selected graphic or replace it with an appropriate alternative.</span></span>  
  
 <span data-ttu-id="7a1fc-135">**趨勢運算式**</span><span class="sxs-lookup"><span data-stu-id="7a1fc-135">**Trend expression**</span></span>  
 <span data-ttu-id="7a1fc-136">鍵入會傳回 KPI 趨勢值的 MDX 運算式。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-136">Type the MDX expression that returns the trend value of the KPI.</span></span>  
  
 <span data-ttu-id="7a1fc-137">從 **[計算工具]** 窗格中，將選取的元素拖曳到這個選項，以包括所選元素的 MDX 語法。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-137">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="7a1fc-138">趨勢運算式可以根據給定商務內容中任何有意義、以時間為基礎的準則。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-138">The trend expression can be based on any time-based criteria that makes sense in a given business context.</span></span> <span data-ttu-id="7a1fc-139">建議此運算式傳回介於-1 和1之間的十進位數。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-139">It is recommended that this expression returns a decimal number between -1 and 1.</span></span> <span data-ttu-id="7a1fc-140">較低的數字代表經過一段時間的負值趨勢，而較高的數字代表經過一段時間的正值趨勢。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-140">A lower number represents a negative trend over time; a higher number represents a positive trend over time.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7a1fc-141">低於-1 和以上的值是可能的，但協力廠商用戶端應用程式可能無法正確地加以解讀。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-141">Values below -1 and above 1 are possible but may not be interpreted correctly by third-party client applications.</span></span>  
  
 <span data-ttu-id="7a1fc-142">**其他屬性**</span><span class="sxs-lookup"><span data-stu-id="7a1fc-142">**Additional Properties**</span></span>  
 <span data-ttu-id="7a1fc-143">展開即可檢視 [顯示資料夾]\*\*\*\*、[父 KPI]\*\*\*\*、[目前時間成員]\*\*\*\*、[加權]\*\*\*\* 和 [描述]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-143">Expand to view the **Display folder**, **Parent KPI**, **Current time member**, **Weight**, and **Description** options.</span></span>  
  
 <span data-ttu-id="7a1fc-144">**顯示資料夾**</span><span class="sxs-lookup"><span data-stu-id="7a1fc-144">**Display folder**</span></span>  
 <span data-ttu-id="7a1fc-145">鍵入用戶端應用程式用於顯示用途所使用的 KPI 分類。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-145">Type the categorization of the KPI for use by the client application for display purposes.</span></span>  
  
 <span data-ttu-id="7a1fc-146">在顯示資料夾中使用反斜線 (\\) 來分隔資料夾名稱，並使用分號 (;) 來分隔多個顯示資料夾。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-146">Use a backward slash (\\) to separate folder names in a display folder and a semicolon (;) to separate multiple display folders.</span></span> <span data-ttu-id="7a1fc-147">例如，輸入 `Category\Goal\Scientific;Category\Goal\Metric`。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-147">For example, type `Category\Goal\Scientific;Category\Goal\Metric`.</span></span>  
  
 <span data-ttu-id="7a1fc-148">**父 KPI**</span><span class="sxs-lookup"><span data-stu-id="7a1fc-148">**Parent KPI**</span></span>  
 <span data-ttu-id="7a1fc-149">選取現有的 KPI，在其下分類供用戶端應用程式使用的 KPI。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-149">Select an existing KPI under which to categorize the KPI for use by the client application.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7a1fc-150">如果此選項設定為現有的 KPI，則會忽略 [顯示資料夾]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-150">If this option is set to an existing KPI, **Display folder** is ignored.</span></span>  
  
 <span data-ttu-id="7a1fc-151">**目前時間成員**</span><span class="sxs-lookup"><span data-stu-id="7a1fc-151">**Current time member**</span></span>  
 <span data-ttu-id="7a1fc-152">鍵入會傳回成員的 MDX 運算式，該成員用來識別 KPI 的暫時內容。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-152">Type the MDX expression that returns the member that identifies the temporal context of the KPI.</span></span>  
  
 <span data-ttu-id="7a1fc-153">從 **[計算工具]** 窗格中，將選取的元素拖曳到這個選項，以包括所選元素的 MDX 語法。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-153">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7a1fc-154">MDX 計算式必須傳回成員的唯一名稱，該成員在時間維度內與 [相關聯的量值群組]\*\*\*\* 中所指定的量值群組相關聯。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-154">The MDX expression must return the unique name of a member within a time dimension associated with the measure group specified in **Associated measure group**.</span></span>  
  
 <span data-ttu-id="7a1fc-155">**Weight**</span><span class="sxs-lookup"><span data-stu-id="7a1fc-155">**Weight**</span></span>  
 <span data-ttu-id="7a1fc-156">展開即可檢視或編輯 KPI 加權因數的 MDX 運算式。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-156">Expand to view or edit the MDX expression for the weighting factor of the KPI.</span></span>  
  
 <span data-ttu-id="7a1fc-157">從 **[計算工具]** 窗格中，將選取的元素拖曳到這個選項，以包括所選元素的 MDX 語法。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-157">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="7a1fc-158">**說明**</span><span class="sxs-lookup"><span data-stu-id="7a1fc-158">**Description**</span></span>  
 <span data-ttu-id="7a1fc-159">鍵入 KPI 的選擇性描述。</span><span class="sxs-lookup"><span data-stu-id="7a1fc-159">Type the optional description of the KPI.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a1fc-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a1fc-160">See Also</span></span>  
 [<span data-ttu-id="7a1fc-161">Kpi &#40;Cube 設計師&#41; &#40;Analysis Services-多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="7a1fc-161">KPIs &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](kpis-cube-designer-analysis-services-multidimensional-data.md)  
  
  
