---
title: '[操作表單編輯器] ([動作] 索引標籤、[Cube 設計師])  (Analysis Services-多維度資料) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.actionexpression.action.f1
ms.assetid: c363a29b-6099-473c-9625-460cc15b3d95
author: minewiskan
ms.author: owend
ms.openlocfilehash: b08ed03e843ba206f22969f9ada0da5a590a5811
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592350"
---
# <a name="action-form-editor-actions-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="8c62d-102">動作表單編輯器 (動作索引標籤，Cube 設計師) (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="8c62d-102">Action Form Editor (Actions Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="8c62d-103">使用 [Cube 設計師] 中之 [動作]\*\*\*\* 索引標籤上的 [Action Form Editor (動作表單編輯器)] 窗格，即可建立和修改標準動作。</span><span class="sxs-lookup"><span data-stu-id="8c62d-103">Use the Action Form Editor pane on the **Actions** tab in Cube Designer to create and modify standard actions.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8c62d-104">選項。</span><span class="sxs-lookup"><span data-stu-id="8c62d-104">Options</span></span>  
 <span data-ttu-id="8c62d-105">**名稱**</span><span class="sxs-lookup"><span data-stu-id="8c62d-105">**Name**</span></span>  
 <span data-ttu-id="8c62d-106">鍵入動作的名稱。</span><span class="sxs-lookup"><span data-stu-id="8c62d-106">Type the name of the action.</span></span>  
  
 <span data-ttu-id="8c62d-107">**動作目標**</span><span class="sxs-lookup"><span data-stu-id="8c62d-107">**Action Target**</span></span>  
 <span data-ttu-id="8c62d-108">展開以檢視 [目標類型]\*\*\*\* 和 [目標物件]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="8c62d-108">Expand to view the **Target type** and **Target object** options.</span></span>  
  
 <span data-ttu-id="8c62d-109">**目標型別**</span><span class="sxs-lookup"><span data-stu-id="8c62d-109">**Target type**</span></span>  
 <span data-ttu-id="8c62d-110">選取要與動作相關聯之物件的類型。</span><span class="sxs-lookup"><span data-stu-id="8c62d-110">Select the type of object to which the action is to be associated.</span></span> <span data-ttu-id="8c62d-111">伺服器只會將套用至指定類型之物件的動作傳回用戶端。</span><span class="sxs-lookup"><span data-stu-id="8c62d-111">The server returns to the client only those actions that apply to the object of the specified type.</span></span> <span data-ttu-id="8c62d-112">如果 [條件]\*\*\*\* 符合，而且選取了下表中指定的物件，用戶端就可以使用動作。</span><span class="sxs-lookup"><span data-stu-id="8c62d-112">The action is available to the client if the **Condition** is met and if the objects specified in the following table are selected.</span></span>  
  
|<span data-ttu-id="8c62d-113">值</span><span class="sxs-lookup"><span data-stu-id="8c62d-113">Value</span></span>|<span data-ttu-id="8c62d-114">選取的物件</span><span class="sxs-lookup"><span data-stu-id="8c62d-114">Selected Object</span></span>|  
|-----------|---------------------|  
|<span data-ttu-id="8c62d-115">屬性成員</span><span class="sxs-lookup"><span data-stu-id="8c62d-115">Attribute members</span></span>|<span data-ttu-id="8c62d-116">依據 [目標物件]\*\*\*\* 中的屬性，從層級選取成員。</span><span class="sxs-lookup"><span data-stu-id="8c62d-116">A member is selected from a level based on the attribute in **Target object**.</span></span>|  
|<span data-ttu-id="8c62d-117">資料格</span><span class="sxs-lookup"><span data-stu-id="8c62d-117">Cells</span></span>|<span data-ttu-id="8c62d-118">選取了 [目標物件]\*\*\*\* 中的命名集。</span><span class="sxs-lookup"><span data-stu-id="8c62d-118">The named set in **Target object** is selected.</span></span> <span data-ttu-id="8c62d-119">選取 [所有資料格]\*\*\*\* 即可選取 Cube 中所有的資料格。</span><span class="sxs-lookup"><span data-stu-id="8c62d-119">Select **All cells** to select all of the cells in the cube.</span></span>|  
|<span data-ttu-id="8c62d-120">Cube</span><span class="sxs-lookup"><span data-stu-id="8c62d-120">Cube</span></span>|<span data-ttu-id="8c62d-121">選取了 [目標物件]\*\*\*\* 中的 Cube。</span><span class="sxs-lookup"><span data-stu-id="8c62d-121">The cube in **Target object** is selected.</span></span> <span data-ttu-id="8c62d-122">選取 CURRENTCUBE 即可使用目前的 Cube。</span><span class="sxs-lookup"><span data-stu-id="8c62d-122">Select CURRENTCUBE to use the current cube.</span></span><br /><br /> <span data-ttu-id="8c62d-123">注意：在 Cube 可能會被重新命名或動作被複製到其他 Cube 的情況下，使用 CURRENTCUBE 可以提供更大彈性。</span><span class="sxs-lookup"><span data-stu-id="8c62d-123">Note: Using CURRENTCUBE provides additional portability in cases where the cube may be renamed or the action copied to other cubes.</span></span> <span data-ttu-id="8c62d-124">建議您使用 CURRENTCUBE 來代表目前的 Cube。</span><span class="sxs-lookup"><span data-stu-id="8c62d-124">It is recommended that you use CURRENTCUBE to represent the current cube.</span></span>|  
|<span data-ttu-id="8c62d-125">維度成員</span><span class="sxs-lookup"><span data-stu-id="8c62d-125">Dimension members</span></span>|<span data-ttu-id="8c62d-126">選取了 [目標物件]\*\*\*\* 中之維度的成員。</span><span class="sxs-lookup"><span data-stu-id="8c62d-126">A member of the dimension in **Target object** is selected.</span></span>|  
|<span data-ttu-id="8c62d-127">階層</span><span class="sxs-lookup"><span data-stu-id="8c62d-127">Hierarchy</span></span>|<span data-ttu-id="8c62d-128">選取了 [目標物件]\*\*\*\* 中的階層。</span><span class="sxs-lookup"><span data-stu-id="8c62d-128">The hierarchy in **Target object** is selected.</span></span>|  
|<span data-ttu-id="8c62d-129">階層成員</span><span class="sxs-lookup"><span data-stu-id="8c62d-129">Hierarchy members</span></span>|<span data-ttu-id="8c62d-130">選取了 [目標物件]\*\*\*\* 中之階層內的成員。</span><span class="sxs-lookup"><span data-stu-id="8c62d-130">A member within the hierarchy in **Target object** is selected.</span></span>|  
|<span data-ttu-id="8c62d-131">層級</span><span class="sxs-lookup"><span data-stu-id="8c62d-131">Level</span></span>|<span data-ttu-id="8c62d-132">選取了 [目標物件]\*\*\*\* 中的層級。</span><span class="sxs-lookup"><span data-stu-id="8c62d-132">The level in **Target object** is selected.</span></span>|  
|<span data-ttu-id="8c62d-133">層級成員</span><span class="sxs-lookup"><span data-stu-id="8c62d-133">Level members</span></span>|<span data-ttu-id="8c62d-134">選取了 [目標物件]\*\*\*\* 中之層級內的成員。</span><span class="sxs-lookup"><span data-stu-id="8c62d-134">A member within the level in **Target object** is selected.</span></span>|  
  
 <span data-ttu-id="8c62d-135">**目標物件**</span><span class="sxs-lookup"><span data-stu-id="8c62d-135">**Target object**</span></span>  
 <span data-ttu-id="8c62d-136">選取要與動作相關聯的物件。</span><span class="sxs-lookup"><span data-stu-id="8c62d-136">Select the object to which the action is to be associated.</span></span> <span data-ttu-id="8c62d-137">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體只會將套用至所選物件的動作傳回用戶端。</span><span class="sxs-lookup"><span data-stu-id="8c62d-137">The [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance returns to the client only those actions that apply to the selected object.</span></span> <span data-ttu-id="8c62d-138">可用物件的清單受到 [目標類型]\*\*\*\* 之選擇的限制。</span><span class="sxs-lookup"><span data-stu-id="8c62d-138">The list of available objects is constrained by the choice of **Target type**.</span></span>  
  
 <span data-ttu-id="8c62d-139">**條件 (選擇性)**</span><span class="sxs-lookup"><span data-stu-id="8c62d-139">**Condition (Optional)**</span></span>  
 <span data-ttu-id="8c62d-140">輸入描述選擇性條件的多維度運算式 (MDX) 運算式，這要配合 [目標物件]\*\*\*\* 使用，也因此將進一步限制動作可用的時機。</span><span class="sxs-lookup"><span data-stu-id="8c62d-140">Enter the Multidimensional Expressions (MDX) expression that describes an optional condition, used in conjunction with **Target object**, which further restricts when the action is available.</span></span> <span data-ttu-id="8c62d-141">此運算式必須傳回布林值，如果此值為 True，則表示可使用該動作。</span><span class="sxs-lookup"><span data-stu-id="8c62d-141">The expression must return a Boolean value that, if true, indicates the action is available.</span></span>  
  
 <span data-ttu-id="8c62d-142">從 **[計算工具]** 窗格中，將選取的元素拖曳到這個選項，以包括所選元素的 MDX 語法。</span><span class="sxs-lookup"><span data-stu-id="8c62d-142">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="8c62d-143">**動作內容**</span><span class="sxs-lookup"><span data-stu-id="8c62d-143">**Action Content**</span></span>  
 <span data-ttu-id="8c62d-144">展開以檢視 [類型]\*\*\*\* 和 [動作運算式]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="8c62d-144">Expand to view the **Type** and **Action expression** options.</span></span>  
  
 <span data-ttu-id="8c62d-145">**型別**</span><span class="sxs-lookup"><span data-stu-id="8c62d-145">**Type**</span></span>  
 <span data-ttu-id="8c62d-146">選取執行動作時要採取的動作類型。</span><span class="sxs-lookup"><span data-stu-id="8c62d-146">Select the type of action to take when the action is run.</span></span> <span data-ttu-id="8c62d-147">下列是可以使用的動作類型：</span><span class="sxs-lookup"><span data-stu-id="8c62d-147">The following action types are available:</span></span>  
  
|<span data-ttu-id="8c62d-148">值</span><span class="sxs-lookup"><span data-stu-id="8c62d-148">Value</span></span>|<span data-ttu-id="8c62d-149">描述</span><span class="sxs-lookup"><span data-stu-id="8c62d-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8c62d-150">資料集</span><span class="sxs-lookup"><span data-stu-id="8c62d-150">Dataset</span></span>|<span data-ttu-id="8c62d-151">傳回用戶端應用程式要執行和顯示的多維度運算式 (MDX) 陳述式 (代表多維度資料集)。</span><span class="sxs-lookup"><span data-stu-id="8c62d-151">Returns a Multidimensional Expressions (MDX) statement, representing a multidimensional dataset, to be run and displayed by the client application.</span></span>|  
|<span data-ttu-id="8c62d-152">專屬</span><span class="sxs-lookup"><span data-stu-id="8c62d-152">Proprietary</span></span>|<span data-ttu-id="8c62d-153">傳回與此動作的 [應用程式]\*\*\*\* 設定相關聯之用戶端應用程式可以解譯的專屬字串。</span><span class="sxs-lookup"><span data-stu-id="8c62d-153">Returns a proprietary string that can be interpreted by client applications associated with the **Application** setting for this action.</span></span>|  
|<span data-ttu-id="8c62d-154">資料列集</span><span class="sxs-lookup"><span data-stu-id="8c62d-154">Rowset</span></span>|<span data-ttu-id="8c62d-155">傳回用戶端應用程式要執行和顯示的多維度運算式 (MDX) 陳述式 (代表表格式資料列集)。</span><span class="sxs-lookup"><span data-stu-id="8c62d-155">Returns a Multidimensional Expressions (MDX) statement, representing a tabular rowset, to be run and displayed by the client application.</span></span>|  
|<span data-ttu-id="8c62d-156">陳述式</span><span class="sxs-lookup"><span data-stu-id="8c62d-156">Statement</span></span>|<span data-ttu-id="8c62d-157">傳回用戶端應用程式要執行的命令字串。</span><span class="sxs-lookup"><span data-stu-id="8c62d-157">Returns a command string to be run by the client application.</span></span>|  
|<span data-ttu-id="8c62d-158">URL</span><span class="sxs-lookup"><span data-stu-id="8c62d-158">URL</span></span>|<span data-ttu-id="8c62d-159">傳回用戶端應用程式要開啟的統一資源定位器 (URL) 字串，通常使用網際網路瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="8c62d-159">Returns a Uniform Resource Location (URL) string to be opened by the client application, typically with an Internet browser.</span></span>|  
  
 <span data-ttu-id="8c62d-160">如需動作類型的詳細資訊，請參閱[動作 &#40;Analysis Services - 多維度資料&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="8c62d-160">For more information about action types, see [Actions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="8c62d-161">**動作運算式**</span><span class="sxs-lookup"><span data-stu-id="8c62d-161">**Action expression**</span></span>  
 <span data-ttu-id="8c62d-162">鍵入傳回用戶端應用程式執行的動作所傳回之字串的多維度運算式 (MDX) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="8c62d-162">Type the Multidimensional Expressions (MDX) expression that returns the string returned by the action to the client application for execution.</span></span>  
  
 <span data-ttu-id="8c62d-163">**其他屬性**</span><span class="sxs-lookup"><span data-stu-id="8c62d-163">**Additional Properties**</span></span>  
 <span data-ttu-id="8c62d-164">展開以檢視 [引動過程]\*\*\*\*、[應用程式]\*\*\*\*、[描述]\*\*\*\*、[標題]\*\*\*\* 和 [標題是 MDX]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="8c62d-164">Expand to view the **Invocation**, **Application**, **Description**, **Caption**, and **Caption Is MDX** options.</span></span>  
  
 <span data-ttu-id="8c62d-165">**引動過程**</span><span class="sxs-lookup"><span data-stu-id="8c62d-165">**Invocation**</span></span>  
 <span data-ttu-id="8c62d-166">選取設定，以指出何時該執行此動作。</span><span class="sxs-lookup"><span data-stu-id="8c62d-166">Select the setting that indicates when the action should be carried out.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8c62d-167">此選項只提供用戶端應用程式何時要執行動作的建議，並不會直接控制動作的叫用。</span><span class="sxs-lookup"><span data-stu-id="8c62d-167">This option only provides a recommendation to a client application as to when to execute an action, and does not directly control the invocation of the action.</span></span>  
  
 <span data-ttu-id="8c62d-168">下表描述可用的設定。</span><span class="sxs-lookup"><span data-stu-id="8c62d-168">The following table describes the available settings.</span></span>  
  
|<span data-ttu-id="8c62d-169">值</span><span class="sxs-lookup"><span data-stu-id="8c62d-169">Value</span></span>|<span data-ttu-id="8c62d-170">描述</span><span class="sxs-lookup"><span data-stu-id="8c62d-170">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8c62d-171">Batch</span><span class="sxs-lookup"><span data-stu-id="8c62d-171">Batch</span></span>|<span data-ttu-id="8c62d-172">此動作應該當作批次作業的一部份或 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 工作來執行。</span><span class="sxs-lookup"><span data-stu-id="8c62d-172">The action should run as part of a batch operation or an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] task.</span></span>|  
|<span data-ttu-id="8c62d-173">互動式</span><span class="sxs-lookup"><span data-stu-id="8c62d-173">Interactive</span></span>|<span data-ttu-id="8c62d-174">此動作會在使用者叫用動作時執行。</span><span class="sxs-lookup"><span data-stu-id="8c62d-174">The action runs when the user invokes the action.</span></span>|  
|<span data-ttu-id="8c62d-175">開啟時</span><span class="sxs-lookup"><span data-stu-id="8c62d-175">On Open</span></span>|<span data-ttu-id="8c62d-176">此動作會在第一次開啟 Cube 時執行。</span><span class="sxs-lookup"><span data-stu-id="8c62d-176">The action runs when the cube is first opened.</span></span>|  
  
 <span data-ttu-id="8c62d-177">**應用程式**</span><span class="sxs-lookup"><span data-stu-id="8c62d-177">**Application**</span></span>  
 <span data-ttu-id="8c62d-178">鍵入可解譯 [動作運算式\*\*\*\* 傳回之字串的應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="8c62d-178">Type the name of the application that can interpret the string returned by **Action expression**.</span></span>  
  
 <span data-ttu-id="8c62d-179">您也可以使用此選項來識別哪一個用戶端應用程式最常使用這個動作，以及在快顯功能表的該動作旁邊顯示適當的圖示。</span><span class="sxs-lookup"><span data-stu-id="8c62d-179">You can also use this option to identify which client application most commonly uses this action, as well as to display appropriate icons next to the action in a pop-up menu.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8c62d-180">此選項只提供用戶端應用程式應該執行哪些動作的建議，並不會直接控制動作的存取。</span><span class="sxs-lookup"><span data-stu-id="8c62d-180">This option only provides a recommendation to a client application as to what client application should execute an action, and does not directly control access to the action.</span></span> <span data-ttu-id="8c62d-181">用戶端應用程式應隱藏與其他用戶端應用程式相關聯的動作。</span><span class="sxs-lookup"><span data-stu-id="8c62d-181">Client applications should hide any actions that are associated with other client applications.</span></span>  
  
 <span data-ttu-id="8c62d-182">**說明**</span><span class="sxs-lookup"><span data-stu-id="8c62d-182">**Description**</span></span>  
 <span data-ttu-id="8c62d-183">鍵入動作的選擇性描述。</span><span class="sxs-lookup"><span data-stu-id="8c62d-183">Type the optional description of the action.</span></span>  
  
 <span data-ttu-id="8c62d-184">**Caption**</span><span class="sxs-lookup"><span data-stu-id="8c62d-184">**Caption**</span></span>  
 <span data-ttu-id="8c62d-185">如果 [標題是 MDX]\*\*\*\* 設為 [False]\*\*\*\*，則請鍵入要顯示在用戶端應用程式中的動作標題。</span><span class="sxs-lookup"><span data-stu-id="8c62d-185">Type the caption to be displayed for the action in the client application if **Caption Is MDX** is set to **False**.</span></span>  
  
 <span data-ttu-id="8c62d-186">如果 [標題是 MDX]\*\*\*\* 設定為 [True]\*\*\*\*，則請鍵入會傳回標題字串的多維度運算式 (MDX) 運算式。</span><span class="sxs-lookup"><span data-stu-id="8c62d-186">Type the Multidimensional Expressions (MDX) expression that returns a string for the caption if **Caption Is MDX** is set to **True**.</span></span>  
  
 <span data-ttu-id="8c62d-187">**標題是 MDX**</span><span class="sxs-lookup"><span data-stu-id="8c62d-187">**Caption is MDX**</span></span>  
 <span data-ttu-id="8c62d-188">選取 [False]\*\*\*\* 以指出 [標題]\*\*\*\* 包含一個常值字串，代表要顯示在用戶端應用程式中的動作標題。</span><span class="sxs-lookup"><span data-stu-id="8c62d-188">Select **False** to indicate that **Caption** contains a literal string representing a caption to be displayed for the action in the client application.</span></span>  
  
 <span data-ttu-id="8c62d-189">選取 **[True]** 以指出 **[標題]** 包含一個會傳回字串的 MDX 運算式，字串代表要顯示在用戶端應用程式中的動作標題。</span><span class="sxs-lookup"><span data-stu-id="8c62d-189">Select **True** to indicate that **Caption** contains an MDX expression that returns a string representing a caption to be displayed for the action in the client application.</span></span> <span data-ttu-id="8c62d-190">在動作傳回至用戶端應用程式之前，必須先解析 MDX 運算式。</span><span class="sxs-lookup"><span data-stu-id="8c62d-190">The MDX expression must be resolved before the action is returned to the client application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c62d-191">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c62d-191">See Also</span></span>  
 <span data-ttu-id="8c62d-192">[&#40;Cube 設計師的動作&#41; &#40;Analysis Services 多維度資料&#41;](actions-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="8c62d-192">[Actions &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](actions-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="8c62d-193">[工具列 &#40;動作] 索引標籤，Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="8c62d-193">[Toolbar &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="8c62d-194">[動作召集人 &#40;動作] 索引標籤、Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="8c62d-194">[Action Organizer &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="8c62d-195">[[計算工具] &#40;[動作] 索引標籤、[Cube 設計師]&#41; &#40;Analysis Services 多維度資料&#41;](calculation-tools-actions-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="8c62d-195">[Calculation Tools &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculation-tools-actions-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="8c62d-196">[[&#40;動作] 索引標籤、Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;的 [動作表單編輯器]](drillthrough-action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="8c62d-196">[Drillthrough Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](drillthrough-action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="8c62d-197">[報表操作表單編輯器 &#40;動作] 索引標籤、Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](report-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="8c62d-197">[Report Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](report-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)</span></span>  
  
  
