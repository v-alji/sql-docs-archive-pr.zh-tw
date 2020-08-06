---
title: '[ (動作] 索引標籤、Cube 設計工具)  (Analysis Services-多維度資料) | 中的 [動作表單編輯器]Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.actionexpression.drillthroughaction.f1
ms.assetid: 225fd818-b5ea-494f-b67b-66e09798274a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 546448bd05f3af45b7093acb2dbb9d1e1a8f1bd5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599247"
---
# <a name="drillthrough-action-form-editor-actions-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="b99dd-102">鑽研動作表單編輯器 (動作索引標籤，設計師) (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="b99dd-102">Drillthrough Action Form Editor (Actions Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="b99dd-103">在 Cube 設計師中，使用 **[動作]** 索引標籤的 **[鑽研動作表單編輯器]** 窗格，即可修改 **[動作組合管理]** 窗格中選取的鑽研動作。</span><span class="sxs-lookup"><span data-stu-id="b99dd-103">Use the **Drillthrough Action Form Editor** pane on the **Actions** tab in Cube Designer to modify the drillthrough action selected in the **Action Organizer** pane.</span></span> <span data-ttu-id="b99dd-104">如需鑽研動作的詳細資訊，請參閱[動作 &#40;Analysis Services - 多維度資料&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="b99dd-104">For more information about drillthrough actions, see [Actions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b99dd-105">鑽研動作不再向下鑽研至基礎資料存放區。</span><span class="sxs-lookup"><span data-stu-id="b99dd-105">Drillthrough actions no longer drill down to the underlying data store.</span></span> <span data-ttu-id="b99dd-106">鑽研動作存取的資訊，必須是使用維度或階層成員包含在 Cube 模型中的資訊。</span><span class="sxs-lookup"><span data-stu-id="b99dd-106">The information that drillthrough actions access must be modeled within the cube by using dimension or hierarchy members.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b99dd-107">選項</span><span class="sxs-lookup"><span data-stu-id="b99dd-107">Options</span></span>  
 <span data-ttu-id="b99dd-108">**name**</span><span class="sxs-lookup"><span data-stu-id="b99dd-108">**name**</span></span>  
 <span data-ttu-id="b99dd-109">鍵入動作的名稱。</span><span class="sxs-lookup"><span data-stu-id="b99dd-109">Type the name of the action.</span></span>  
  
 <span data-ttu-id="b99dd-110">**動作目標**</span><span class="sxs-lookup"><span data-stu-id="b99dd-110">**Action Target**</span></span>  
 <span data-ttu-id="b99dd-111">展開即可檢視 [量值群組成員]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="b99dd-111">Expand to view the **Measure group members** option.</span></span>  
  
 <span data-ttu-id="b99dd-112">**量值群組成員**</span><span class="sxs-lookup"><span data-stu-id="b99dd-112">**Measure group members**</span></span>  
 <span data-ttu-id="b99dd-113">選取要與鑽研動作建立關聯的量值群組。</span><span class="sxs-lookup"><span data-stu-id="b99dd-113">Select the measure group to which the drillthrough action is to be associated.</span></span>  
  
 <span data-ttu-id="b99dd-114">**條件 (選擇性)**</span><span class="sxs-lookup"><span data-stu-id="b99dd-114">**Condition (Optional)**</span></span>  
 <span data-ttu-id="b99dd-115">輸入描述選擇性條件的多維度運算式 (MDX) 運算式，搭配 [量值群組成員]\*\*\*\* 一起使用，進一步限制何時可以使用動作。</span><span class="sxs-lookup"><span data-stu-id="b99dd-115">Enter the Multidimensional Expressions (MDX) expression that describes an optional condition, used in conjunction with **Measure group members**, which further restricts when the action is available.</span></span> <span data-ttu-id="b99dd-116">此運算式必須傳回布林值，如果此值為 True，則表示可使用該動作。</span><span class="sxs-lookup"><span data-stu-id="b99dd-116">The expression must return a Boolean value that, if true, indicates the action is available.</span></span>  
  
 <span data-ttu-id="b99dd-117">從 **[計算工具]** 窗格中，將選取的元素拖曳到這個選項，以包括所選元素的 MDX 語法。</span><span class="sxs-lookup"><span data-stu-id="b99dd-117">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="b99dd-118">**鑽研資料行**</span><span class="sxs-lookup"><span data-stu-id="b99dd-118">**Drillthrough Columns**</span></span>  
 <span data-ttu-id="b99dd-119">展開即可顯示方格，以指出使用者執行此動作時傳回的屬性。</span><span class="sxs-lookup"><span data-stu-id="b99dd-119">Expand to display a grid in which to indicate the attributes that are returned when the user runs this action.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b99dd-120">您可以選取一個以上的維度，但維度在一個鑽研動作中不能使用一次以上。</span><span class="sxs-lookup"><span data-stu-id="b99dd-120">You can select more than one dimension, but no dimension can be used more than once in a drillthrough action.</span></span>  
  
 <span data-ttu-id="b99dd-121">方格包含下列資料行：</span><span class="sxs-lookup"><span data-stu-id="b99dd-121">The grid contains the following columns:</span></span>  
  
|<span data-ttu-id="b99dd-122">資料行</span><span class="sxs-lookup"><span data-stu-id="b99dd-122">Column</span></span>|<span data-ttu-id="b99dd-123">描述</span><span class="sxs-lookup"><span data-stu-id="b99dd-123">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b99dd-124">**維度**</span><span class="sxs-lookup"><span data-stu-id="b99dd-124">**Dimensions**</span></span>|<span data-ttu-id="b99dd-125">選取衍生所傳回屬性的維度。</span><span class="sxs-lookup"><span data-stu-id="b99dd-125">Select the dimension from which the returned attribute is derived.</span></span> <span data-ttu-id="b99dd-126">選取 MEASURES 即可在量值上進行鑽研。</span><span class="sxs-lookup"><span data-stu-id="b99dd-126">Select MEASURES to drillthrough on measures.</span></span>|  
|<span data-ttu-id="b99dd-127">**傳回資料行**</span><span class="sxs-lookup"><span data-stu-id="b99dd-127">**Return Columns**</span></span>|<span data-ttu-id="b99dd-128">從選取的維度中選取執行動作時要傳回的屬性或量值。</span><span class="sxs-lookup"><span data-stu-id="b99dd-128">Select the attribute or measure from the selected dimension to be returned when the action is run.</span></span>|  
  
 <span data-ttu-id="b99dd-129">**其他屬性**</span><span class="sxs-lookup"><span data-stu-id="b99dd-129">**Additional Properties**</span></span>  
 <span data-ttu-id="b99dd-130">展開以檢視 [預設值]\*\*\*\*、[最大資料列數]\*\*\*\*、[引動過程]\*\*\*\*、[應用程式]\*\*\*\*、[描述]\*\*\*\*、[標題]\*\*\*\* 及 [標題是 MDX]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="b99dd-130">Expand to view the **Default**, **Maximum rows**, **Invocation**, **Application**, **Description**, **Caption**, and **Caption Is MDX** options.</span></span>  
  
 <span data-ttu-id="b99dd-131">**預設值**</span><span class="sxs-lookup"><span data-stu-id="b99dd-131">**Default**</span></span>  
 <span data-ttu-id="b99dd-132">選取 [True]\*\*\*\* 以包含此鑽研動作作為預設鑽研動作，否則，請選取 [False]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b99dd-132">Select **True** to include this drillthrough action as a default drillthrough action, otherwise, select **False**.</span></span>  
  
 <span data-ttu-id="b99dd-133">如果 `RETURN` 從 `DRILLTHROUGH` 用戶端應用程式所執行的 MDX 語句中省略子句，實例就會 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 評估所有預設的鑽取動作，並執行第一個傳回非空白集合的預設「鑽取」動作。</span><span class="sxs-lookup"><span data-stu-id="b99dd-133">If the `RETURN` clause is omitted from an MDX `DRILLTHROUGH` statement executed by a client application, the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance evaluates all default drillthrough actions and runs the first default drillthrough action that returns a non-empty set.</span></span> <span data-ttu-id="b99dd-134">如需 MDX 語句的詳細資訊 `DRILLTHROUGH` ，請參閱[&#40;mdx&#41;](/sql/mdx/mdx-data-manipulation-drillthrough)的「鑽看」語句。</span><span class="sxs-lookup"><span data-stu-id="b99dd-134">For more information about the MDX `DRILLTHROUGH` statement, see [DRILLTHROUGH Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-drillthrough).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b99dd-135">此選項用於回溯相容性用途。</span><span class="sxs-lookup"><span data-stu-id="b99dd-135">This option is used for backwards compatibility purposes.</span></span>  
  
 <span data-ttu-id="b99dd-136">**最大資料列數**</span><span class="sxs-lookup"><span data-stu-id="b99dd-136">**Maximum rows**</span></span>  
 <span data-ttu-id="b99dd-137">鍵入鑽研動作要傳回的最大資料列數。</span><span class="sxs-lookup"><span data-stu-id="b99dd-137">Type the maximum number of rows to be returned by the drillthrough action.</span></span> <span data-ttu-id="b99dd-138">將此選項設定為零或空的值，表示鑽研動作將會傳回該動作擷取的所有資料列給用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="b99dd-138">Setting this option to zero or an empty value indicates that the drillthrough action returns all rows retrieved by the action to the client application.</span></span>  
  
 <span data-ttu-id="b99dd-139">**引動過程**</span><span class="sxs-lookup"><span data-stu-id="b99dd-139">**Invocation**</span></span>  
 <span data-ttu-id="b99dd-140">選取設定，以指出何時該執行此動作。</span><span class="sxs-lookup"><span data-stu-id="b99dd-140">Select the setting that indicates when the action should be carried out.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b99dd-141">此選項只提供用戶端應用程式何時要執行動作的建議，並不會直接控制動作的叫用。</span><span class="sxs-lookup"><span data-stu-id="b99dd-141">This option only provides a recommendation to a client application as to when to execute an action, and does not directly control the invocation of the action.</span></span>  
  
 <span data-ttu-id="b99dd-142">下表描述可用的設定。</span><span class="sxs-lookup"><span data-stu-id="b99dd-142">The following table describes the available settings.</span></span>  
  
|<span data-ttu-id="b99dd-143">值</span><span class="sxs-lookup"><span data-stu-id="b99dd-143">Value</span></span>|<span data-ttu-id="b99dd-144">描述</span><span class="sxs-lookup"><span data-stu-id="b99dd-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b99dd-145">Batch</span><span class="sxs-lookup"><span data-stu-id="b99dd-145">Batch</span></span>|<span data-ttu-id="b99dd-146">此動作應該當作批次作業的一部份或 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 工作來執行。</span><span class="sxs-lookup"><span data-stu-id="b99dd-146">The action should run as part of a batch operation or an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] task.</span></span>|  
|<span data-ttu-id="b99dd-147">互動式</span><span class="sxs-lookup"><span data-stu-id="b99dd-147">Interactive</span></span>|<span data-ttu-id="b99dd-148">此動作會在使用者叫用動作時執行。</span><span class="sxs-lookup"><span data-stu-id="b99dd-148">The action runs when the user invokes the action.</span></span>|  
|<span data-ttu-id="b99dd-149">開啟時</span><span class="sxs-lookup"><span data-stu-id="b99dd-149">On Open</span></span>|<span data-ttu-id="b99dd-150">此動作會在第一次開啟 Cube 時執行。</span><span class="sxs-lookup"><span data-stu-id="b99dd-150">The action runs when the cube is first opened.</span></span>|  
  
 <span data-ttu-id="b99dd-151">**應用程式**</span><span class="sxs-lookup"><span data-stu-id="b99dd-151">**Application**</span></span>  
 <span data-ttu-id="b99dd-152">鍵入可以執行鑽研動作的應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="b99dd-152">Type the name of the application that can execute the drillthrough action.</span></span>  
  
 <span data-ttu-id="b99dd-153">您也可以使用此選項來識別哪一個用戶端應用程式最常使用這個動作，以及在快顯功能表的該動作旁邊顯示適當的圖示。</span><span class="sxs-lookup"><span data-stu-id="b99dd-153">You can also use this option to identify which client application most commonly uses this action, as well as to display appropriate icons next to the action in a pop-up menu.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b99dd-154">此選項只提供用戶端應用程式應該執行哪些動作的建議，並不會直接控制動作的存取。</span><span class="sxs-lookup"><span data-stu-id="b99dd-154">This option only provides a recommendation to a client application as to what client application should execute an action, and does not directly control access to the action.</span></span> <span data-ttu-id="b99dd-155">用戶端應用程式應隱藏與其他用戶端應用程式相關聯的動作。</span><span class="sxs-lookup"><span data-stu-id="b99dd-155">Client applications should hide any actions that are associated with other client applications.</span></span>  
  
 <span data-ttu-id="b99dd-156">**說明**</span><span class="sxs-lookup"><span data-stu-id="b99dd-156">**Description**</span></span>  
 <span data-ttu-id="b99dd-157">鍵入動作的選擇性描述。</span><span class="sxs-lookup"><span data-stu-id="b99dd-157">Type the optional description of the action.</span></span>  
  
 <span data-ttu-id="b99dd-158">**Caption**</span><span class="sxs-lookup"><span data-stu-id="b99dd-158">**Caption**</span></span>  
 <span data-ttu-id="b99dd-159">如果 [標題是 MDX]\*\*\*\* 設為 [False]\*\*\*\*，則請鍵入要顯示在用戶端應用程式中的動作標題。</span><span class="sxs-lookup"><span data-stu-id="b99dd-159">Type the caption to be displayed for the action in the client application if **Caption Is MDX** is set to **False**.</span></span>  
  
 <span data-ttu-id="b99dd-160">如果 [標題是 MDX]\*\*\*\* 設定為 [True]\*\*\*\*，則請鍵入會傳回標題字串的多維度運算式 (MDX) 運算式。</span><span class="sxs-lookup"><span data-stu-id="b99dd-160">Type the Multidimensional Expressions (MDX) expression that returns a string for the caption if **Caption Is MDX** is set to **True**.</span></span>  
  
 <span data-ttu-id="b99dd-161">**標題是 MDX**</span><span class="sxs-lookup"><span data-stu-id="b99dd-161">**Caption Is MDX**</span></span>  
 <span data-ttu-id="b99dd-162">選取 [False]\*\*\*\* 以指出 [標題]\*\*\*\* 包含一個常值字串，代表要顯示在用戶端應用程式中的動作標題。</span><span class="sxs-lookup"><span data-stu-id="b99dd-162">Select **False** to indicate that **Caption** contains a literal string representing a caption to be displayed for the action in the client application.</span></span>  
  
 <span data-ttu-id="b99dd-163">選取 **[True]** 以指出 **[標題]** 包含一個會傳回字串的 MDX 運算式，字串代表要顯示在用戶端應用程式中的動作標題。</span><span class="sxs-lookup"><span data-stu-id="b99dd-163">Select **True** to indicate that **Caption** contains an MDX expression that returns a string representing a caption to be displayed for the action in the client application.</span></span> <span data-ttu-id="b99dd-164">在動作傳回至用戶端應用程式之前，必須先解析 MDX 運算式。</span><span class="sxs-lookup"><span data-stu-id="b99dd-164">The MDX expression must be resolved before the action is returned to the client application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b99dd-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b99dd-165">See Also</span></span>  
 <span data-ttu-id="b99dd-166">[&#40;MDX&#41; 參考的多維度運算式](/sql/mdx/multidimensional-expressions-mdx-reference) </span><span class="sxs-lookup"><span data-stu-id="b99dd-166">[Multidimensional Expressions &#40;MDX&#41; Reference](/sql/mdx/multidimensional-expressions-mdx-reference) </span></span>  
 <span data-ttu-id="b99dd-167">[&#40;Cube 設計師的動作&#41; &#40;Analysis Services 多維度資料&#41;](actions-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="b99dd-167">[Actions &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](actions-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="b99dd-168">[工具列 &#40;動作] 索引標籤，Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="b99dd-168">[Toolbar &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="b99dd-169">[動作召集人 &#40;動作] 索引標籤、Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="b99dd-169">[Action Organizer &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="b99dd-170">[[計算工具] &#40;[動作] 索引標籤、[Cube 設計師]&#41; &#40;Analysis Services 多維度資料&#41;](calculation-tools-actions-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="b99dd-170">[Calculation Tools &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculation-tools-actions-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="b99dd-171">[[操作表單編輯器] &#40;[動作] 索引標籤、[Cube 設計師]&#41; &#40;Analysis Services 多維度資料&#41;](action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="b99dd-171">[Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="b99dd-172">[報表操作表單編輯器 &#40;動作] 索引標籤、Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](report-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="b99dd-172">[Report Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](report-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)</span></span>  
  
  
