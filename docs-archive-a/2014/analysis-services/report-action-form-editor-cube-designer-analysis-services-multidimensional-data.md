---
title: 報表操作表單編輯器 ([動作] 索引標籤、Cube 設計工具)  (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.actionexpression.reportaction.f1
ms.assetid: cebfdd07-e376-46d6-86ef-b6f816a2f360
author: minewiskan
ms.author: owend
ms.openlocfilehash: a6e417f666ec5e6827763257eff19294e21543b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597392"
---
# <a name="report-action-form-editor-actions-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="8ce92-102">報表動作表單編輯器 (動作索引標籤，Cube 設計師) (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="8ce92-102">Report Action Form Editor (Actions Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="8ce92-103">使用 [Cube 設計師] 中 [動作]\*\*\*\* 索引標籤的 [報表動作表單編輯器]\*\*\*\* 窗格，即可修改 [動作組合管理]\*\*\*\* 中選取的報表動作。</span><span class="sxs-lookup"><span data-stu-id="8ce92-103">Use the **Report Action Form Editor** pane on the **Actions** tab in Cube Designer to modify the report action selected in the **Action Organizer** pane.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8ce92-104">選項。</span><span class="sxs-lookup"><span data-stu-id="8ce92-104">Options</span></span>  
 <span data-ttu-id="8ce92-105">**名稱**</span><span class="sxs-lookup"><span data-stu-id="8ce92-105">**Name**</span></span>  
 <span data-ttu-id="8ce92-106">鍵入動作的名稱。</span><span class="sxs-lookup"><span data-stu-id="8ce92-106">Type the name of the action.</span></span>  
  
 <span data-ttu-id="8ce92-107">**動作目標**</span><span class="sxs-lookup"><span data-stu-id="8ce92-107">**Action Target**</span></span>  
 <span data-ttu-id="8ce92-108">展開以檢視 [目標類型]\*\*\*\* 和 [目標物件]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="8ce92-108">Expand to view the **Target type** and **Target object** options.</span></span>  
  
 <span data-ttu-id="8ce92-109">**目標型別**</span><span class="sxs-lookup"><span data-stu-id="8ce92-109">**Target type**</span></span>  
 <span data-ttu-id="8ce92-110">選取要與動作相關聯之物件的類型。</span><span class="sxs-lookup"><span data-stu-id="8ce92-110">Select the type of object to which the action is to be associated.</span></span> <span data-ttu-id="8ce92-111">伺服器只會將套用至指定類型之物件的動作傳回用戶端。</span><span class="sxs-lookup"><span data-stu-id="8ce92-111">The server returns to the client only those actions that apply to the object of the specified type.</span></span> <span data-ttu-id="8ce92-112">如果 [條件]\*\*\*\* 符合，而且選取了下表中指定的物件，用戶端就可以使用動作。</span><span class="sxs-lookup"><span data-stu-id="8ce92-112">The action is available to the client if the **Condition** is met and if the objects specified in the following table are selected.</span></span>  
  
|<span data-ttu-id="8ce92-113">值</span><span class="sxs-lookup"><span data-stu-id="8ce92-113">Value</span></span>|<span data-ttu-id="8ce92-114">選取的物件</span><span class="sxs-lookup"><span data-stu-id="8ce92-114">Selected Object</span></span>|  
|-----------|---------------------|  
|<span data-ttu-id="8ce92-115">屬性成員</span><span class="sxs-lookup"><span data-stu-id="8ce92-115">Attribute members</span></span>|<span data-ttu-id="8ce92-116">依據 [目標物件]\*\*\*\* 中的屬性，從層級選取成員。</span><span class="sxs-lookup"><span data-stu-id="8ce92-116">A member is selected from a level based on the attribute in **Target object**.</span></span><br /><br /> <span data-ttu-id="8ce92-117">注意：使用所選屬性的其他使用者階層，會繼承此報表動作。</span><span class="sxs-lookup"><span data-stu-id="8ce92-117">Note: Other user hierarchies that use the selected attribute inherit the report action.</span></span>|  
|<span data-ttu-id="8ce92-118">資料格</span><span class="sxs-lookup"><span data-stu-id="8ce92-118">Cells</span></span>|<span data-ttu-id="8ce92-119">選取了 [目標物件]\*\*\*\* 中的命名集。</span><span class="sxs-lookup"><span data-stu-id="8ce92-119">The named set in **Target object** is selected.</span></span> <span data-ttu-id="8ce92-120">選取 [所有資料格]\*\*\*\* 即可選取 Cube 中所有的資料格。</span><span class="sxs-lookup"><span data-stu-id="8ce92-120">Select **All cells** to select all of the cells in the cube.</span></span>|  
|<span data-ttu-id="8ce92-121">Cube</span><span class="sxs-lookup"><span data-stu-id="8ce92-121">Cube</span></span>|<span data-ttu-id="8ce92-122">選取了 [目標物件]\*\*\*\* 中的 Cube。</span><span class="sxs-lookup"><span data-stu-id="8ce92-122">The cube in **Target object** is selected.</span></span> <span data-ttu-id="8ce92-123">選取 CURRENTCUBE 即可使用目前的 Cube。</span><span class="sxs-lookup"><span data-stu-id="8ce92-123">Select CURRENTCUBE to use the current cube.</span></span><br /><br /> <span data-ttu-id="8ce92-124">注意：在 Cube 可能會被重新命名或動作被複製到其他 Cube 的情況下，使用 CURRENTCUBE 可以提供更大彈性。</span><span class="sxs-lookup"><span data-stu-id="8ce92-124">Note: Using CURRENTCUBE provides additional portability in cases where the cube may be renamed or the action copied to other cubes.</span></span> <span data-ttu-id="8ce92-125">建議您使用 CURRENTCUBE 來代表目前的 Cube。</span><span class="sxs-lookup"><span data-stu-id="8ce92-125">It is recommended that you use CURRENTCUBE to represent the current cube.</span></span>|  
|<span data-ttu-id="8ce92-126">維度成員</span><span class="sxs-lookup"><span data-stu-id="8ce92-126">Dimension members</span></span>|<span data-ttu-id="8ce92-127">選取了 [目標物件]\*\*\*\* 中之維度的成員。</span><span class="sxs-lookup"><span data-stu-id="8ce92-127">A member of the dimension in **Target object** is selected.</span></span>|  
|<span data-ttu-id="8ce92-128">階層</span><span class="sxs-lookup"><span data-stu-id="8ce92-128">Hierarchy</span></span>|<span data-ttu-id="8ce92-129">選取了 [目標物件]\*\*\*\* 中的階層。</span><span class="sxs-lookup"><span data-stu-id="8ce92-129">The hierarchy in **Target object** is selected.</span></span>|  
|<span data-ttu-id="8ce92-130">階層成員</span><span class="sxs-lookup"><span data-stu-id="8ce92-130">Hierarchy members</span></span>|<span data-ttu-id="8ce92-131">選取了 [目標物件]\*\*\*\* 中之階層內的成員。</span><span class="sxs-lookup"><span data-stu-id="8ce92-131">A member within the hierarchy in **Target object** is selected.</span></span>|  
|<span data-ttu-id="8ce92-132">層級</span><span class="sxs-lookup"><span data-stu-id="8ce92-132">Level</span></span>|<span data-ttu-id="8ce92-133">選取了 [目標物件]\*\*\*\* 中的層級。</span><span class="sxs-lookup"><span data-stu-id="8ce92-133">The level in **Target object** is selected.</span></span>|  
|<span data-ttu-id="8ce92-134">層級成員</span><span class="sxs-lookup"><span data-stu-id="8ce92-134">Level members</span></span>|<span data-ttu-id="8ce92-135">選取了 [目標物件]\*\*\*\* 中之層級內的成員。</span><span class="sxs-lookup"><span data-stu-id="8ce92-135">A member within the level in **Target object** is selected.</span></span>|  
  
 <span data-ttu-id="8ce92-136">**目標物件**</span><span class="sxs-lookup"><span data-stu-id="8ce92-136">**Target object**</span></span>  
 <span data-ttu-id="8ce92-137">選取要與動作相關聯的物件。</span><span class="sxs-lookup"><span data-stu-id="8ce92-137">Select the object to which the action is to be associated.</span></span> <span data-ttu-id="8ce92-138">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體只會將套用至所選物件的動作傳回用戶端。</span><span class="sxs-lookup"><span data-stu-id="8ce92-138">The [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance returns to the client only those actions that apply to the selected object.</span></span> <span data-ttu-id="8ce92-139">可用物件的清單受到 [目標類型]\*\*\*\* 之選擇的限制。</span><span class="sxs-lookup"><span data-stu-id="8ce92-139">The list of available objects is constrained by the choice of **Target type**.</span></span>  
  
 <span data-ttu-id="8ce92-140">**條件 (選擇性)**</span><span class="sxs-lookup"><span data-stu-id="8ce92-140">**Condition (Optional)**</span></span>  
 <span data-ttu-id="8ce92-141">輸入描述選擇性條件的多維度運算式 (MDX) 運算式，這要配合 [目標物件]\*\*\*\* 使用，也因此將進一步限制動作可用的時機。</span><span class="sxs-lookup"><span data-stu-id="8ce92-141">Enter the Multidimensional Expressions (MDX) expression that describes an optional condition, used in conjunction with **Target object**, which further restricts when the action is available.</span></span> <span data-ttu-id="8ce92-142">此運算式必須傳回布林值，如果此值為 True，則表示可使用該動作。</span><span class="sxs-lookup"><span data-stu-id="8ce92-142">The expression must return a Boolean value that, if true, indicates the action is available.</span></span>  
  
 <span data-ttu-id="8ce92-143">從 **[計算工具]** 窗格中，將選取的元素拖曳到這個選項，以包括所選元素的 MDX 語法。</span><span class="sxs-lookup"><span data-stu-id="8ce92-143">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="8ce92-144">**報表伺服器**</span><span class="sxs-lookup"><span data-stu-id="8ce92-144">**Report Server**</span></span>  
 <span data-ttu-id="8ce92-145">展開即可檢視 [伺服器名稱]\*\*\*\*、[伺服器路徑]\*\*\*\* 以及 [報表格式]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="8ce92-145">Expand to view the **Server name**, **Server path**, and **Report format** options.</span></span>  
  
 <span data-ttu-id="8ce92-146">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="8ce92-146">**Server name**</span></span>  
 <span data-ttu-id="8ce92-147">輸入 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 動作執行報表所在的實例名稱。</span><span class="sxs-lookup"><span data-stu-id="8ce92-147">Type the name of the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] instance on which the action runs the report.</span></span>  
  
 <span data-ttu-id="8ce92-148">**伺服器路徑**</span><span class="sxs-lookup"><span data-stu-id="8ce92-148">**Server path**</span></span>  
 <span data-ttu-id="8ce92-149">鍵入 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 執行個體上之報表的路徑。</span><span class="sxs-lookup"><span data-stu-id="8ce92-149">Type the path to the report on the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] instance.</span></span> <span data-ttu-id="8ce92-150">例如，鍵入 **Sales/YearlySalesByCategory**。</span><span class="sxs-lookup"><span data-stu-id="8ce92-150">For example, type **Sales/YearlySalesByCategory**.</span></span>  
  
 <span data-ttu-id="8ce92-151">**報表格式**</span><span class="sxs-lookup"><span data-stu-id="8ce92-151">**Report format**</span></span>  
 <span data-ttu-id="8ce92-152">選取傳回報表時使用的格式。</span><span class="sxs-lookup"><span data-stu-id="8ce92-152">Select the format in which the report is returned.</span></span> <span data-ttu-id="8ce92-153">下表描述可用的格式。</span><span class="sxs-lookup"><span data-stu-id="8ce92-153">The following table describes the available formats.</span></span>  
  
|<span data-ttu-id="8ce92-154">值</span><span class="sxs-lookup"><span data-stu-id="8ce92-154">Value</span></span>|<span data-ttu-id="8ce92-155">描述</span><span class="sxs-lookup"><span data-stu-id="8ce92-155">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8ce92-156">HTML5</span><span class="sxs-lookup"><span data-stu-id="8ce92-156">HTML5</span></span>|<span data-ttu-id="8ce92-157">報表會以 HTML 5.0 相容的格式傳回。</span><span class="sxs-lookup"><span data-stu-id="8ce92-157">Report is returned in an HTML 5.0-compliant format.</span></span>|  
|<span data-ttu-id="8ce92-158">HTML3</span><span class="sxs-lookup"><span data-stu-id="8ce92-158">HTML3</span></span>|<span data-ttu-id="8ce92-159">報表會以 HTML 3.2 相容的格式傳回。</span><span class="sxs-lookup"><span data-stu-id="8ce92-159">Report is returned in an HTML 3.2-compliant format.</span></span>|  
|<span data-ttu-id="8ce92-160">Excel</span><span class="sxs-lookup"><span data-stu-id="8ce92-160">Excel</span></span>|<span data-ttu-id="8ce92-161">報表會以 [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel 活頁簿 (.xls) 檔案的形式傳回。</span><span class="sxs-lookup"><span data-stu-id="8ce92-161">Report is returned as a [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel workbook (.xls) file.</span></span>|  
|<span data-ttu-id="8ce92-162">PDF</span><span class="sxs-lookup"><span data-stu-id="8ce92-162">PDF</span></span>|<span data-ttu-id="8ce92-163">報表會以 Adobe Portable Document Format (.pdf) 檔案傳回。</span><span class="sxs-lookup"><span data-stu-id="8ce92-163">Report is returned as an Adobe Portable Document Format (.pdf) file.</span></span>|  
  
 <span data-ttu-id="8ce92-164">**參數 (選擇性)**</span><span class="sxs-lookup"><span data-stu-id="8ce92-164">**Parameters (Optional)**</span></span>  
 <span data-ttu-id="8ce92-165">展開即可檢視方格，您可以在其中提供 [報表]\*\*\*\* 所指定報表的報表參數。</span><span class="sxs-lookup"><span data-stu-id="8ce92-165">Expand to view a grid in which report parameters can be supplied for the report specified in **Report**.</span></span> <span data-ttu-id="8ce92-166">方格包含下列資料行：</span><span class="sxs-lookup"><span data-stu-id="8ce92-166">The grid contains the following columns:</span></span>  
  
|<span data-ttu-id="8ce92-167">資料行</span><span class="sxs-lookup"><span data-stu-id="8ce92-167">Column</span></span>|<span data-ttu-id="8ce92-168">描述</span><span class="sxs-lookup"><span data-stu-id="8ce92-168">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="8ce92-169">**參數名稱**</span><span class="sxs-lookup"><span data-stu-id="8ce92-169">**Parameter Name**</span></span>|<span data-ttu-id="8ce92-170">鍵入要傳送給報表之報表參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="8ce92-170">Type the name of the report parameter to be passed to the report.</span></span>|  
|<span data-ttu-id="8ce92-171">**參數值**</span><span class="sxs-lookup"><span data-stu-id="8ce92-171">**Parameter Value**</span></span>|<span data-ttu-id="8ce92-172">鍵入要傳送給報表之報表參數的值。</span><span class="sxs-lookup"><span data-stu-id="8ce92-172">Type the value of the report parameter to be passed to the report.</span></span><br /><br /> <span data-ttu-id="8ce92-173">按一下省略符號按鈕 (**...**) 即可顯示 [MDX 產生器]\*\*\*\* 對話方塊，並建立提供報表參數值的 MDX 運算式。</span><span class="sxs-lookup"><span data-stu-id="8ce92-173">Click the ellipsis button (**...**) to display the **MDX Builder** dialog box and create an MDX expression that provides the value of the report parameter.</span></span> <span data-ttu-id="8ce92-174">如需 [MDX 產生器]\*\*\*\* 對話方塊的詳細資訊，請參閱 [MDX 產生器對話方塊 &#40;Analysis Services - 多維度資料&#41;](mdx-builder-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="8ce92-174">For more information about the **MDX Builder** dialog box, see [MDX Builder &#40;Analysis Services - Multidimensional Data&#41;](mdx-builder-analysis-services-multidimensional-data.md).</span></span><br /><br /> <span data-ttu-id="8ce92-175">如果將參數設定為 MDX 運算式，則在執行動作時會評估該運算式，否則會原封不動傳送給報表。</span><span class="sxs-lookup"><span data-stu-id="8ce92-175">If the parameter is set to an MDX expression, then the expression is evaluated when the action is run, otherwise it is passed to the report without modification.</span></span>|  
  
 <span data-ttu-id="8ce92-176">**其他屬性**</span><span class="sxs-lookup"><span data-stu-id="8ce92-176">**Additional Properties**</span></span>  
 <span data-ttu-id="8ce92-177">展開以檢視 [引動過程]\*\*\*\*、[應用程式]\*\*\*\*、[描述]\*\*\*\*、[標題]\*\*\*\* 和 [標題是 MDX]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="8ce92-177">Expand to view the **Invocation**, **Application**, **Description**, **Caption**, and **Caption Is MDX** options.</span></span>  
  
 <span data-ttu-id="8ce92-178">**引動過程**</span><span class="sxs-lookup"><span data-stu-id="8ce92-178">**Invocation**</span></span>  
 <span data-ttu-id="8ce92-179">選取設定，以指出何時該執行此動作。</span><span class="sxs-lookup"><span data-stu-id="8ce92-179">Select the setting that indicates when the action should be carried out.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8ce92-180">此選項只提供用戶端應用程式何時要執行動作的建議，並不會直接控制動作的叫用。</span><span class="sxs-lookup"><span data-stu-id="8ce92-180">This option only provides a recommendation to a client application as to when to execute an action, and does not directly control the invocation of the action.</span></span>  
  
 <span data-ttu-id="8ce92-181">下表描述可用的設定。</span><span class="sxs-lookup"><span data-stu-id="8ce92-181">The following table describes the available settings.</span></span>  
  
|<span data-ttu-id="8ce92-182">值</span><span class="sxs-lookup"><span data-stu-id="8ce92-182">Value</span></span>|<span data-ttu-id="8ce92-183">描述</span><span class="sxs-lookup"><span data-stu-id="8ce92-183">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8ce92-184">Batch</span><span class="sxs-lookup"><span data-stu-id="8ce92-184">Batch</span></span>|<span data-ttu-id="8ce92-185">動作應該當做批次作業或工作的一部分來執行 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8ce92-185">The action should run as part of a batch operation or a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] task.</span></span>|  
|<span data-ttu-id="8ce92-186">互動式</span><span class="sxs-lookup"><span data-stu-id="8ce92-186">Interactive</span></span>|<span data-ttu-id="8ce92-187">此動作會在使用者叫用動作時執行。</span><span class="sxs-lookup"><span data-stu-id="8ce92-187">The action runs when the user invokes the action.</span></span>|  
|<span data-ttu-id="8ce92-188">開啟時</span><span class="sxs-lookup"><span data-stu-id="8ce92-188">On Open</span></span>|<span data-ttu-id="8ce92-189">此動作會在第一次開啟 Cube 時執行。</span><span class="sxs-lookup"><span data-stu-id="8ce92-189">The action runs when the cube is first opened.</span></span>|  
  
 <span data-ttu-id="8ce92-190">**應用程式**</span><span class="sxs-lookup"><span data-stu-id="8ce92-190">**Application**</span></span>  
 <span data-ttu-id="8ce92-191">鍵入可解譯 [動作運算式\*\*\*\* 傳回之字串的應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="8ce92-191">Type the name of the application that can interpret the string returned by **Action expression**.</span></span>  
  
 <span data-ttu-id="8ce92-192">您也可以使用此選項來識別哪一個用戶端應用程式最常使用這個動作，以及在快顯功能表的該動作旁邊顯示適當的圖示。</span><span class="sxs-lookup"><span data-stu-id="8ce92-192">You can also use this option to identify which client application most commonly uses this action, as well as to display appropriate icons next to the action in a pop-up menu.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8ce92-193">此選項只提供用戶端應用程式應該執行哪些動作的建議，並不會直接控制動作的存取。</span><span class="sxs-lookup"><span data-stu-id="8ce92-193">This option only provides a recommendation to a client application as to what client application should execute an action, and does not directly control access to the action.</span></span> <span data-ttu-id="8ce92-194">用戶端應用程式應隱藏與其他用戶端應用程式相關聯的動作。</span><span class="sxs-lookup"><span data-stu-id="8ce92-194">Client applications should hide any actions that are associated with other client applications.</span></span>  
  
 <span data-ttu-id="8ce92-195">**描述**</span><span class="sxs-lookup"><span data-stu-id="8ce92-195">**Description**</span></span>  
 <span data-ttu-id="8ce92-196">鍵入動作的選擇性描述。</span><span class="sxs-lookup"><span data-stu-id="8ce92-196">Type the optional description of the action.</span></span>  
  
 <span data-ttu-id="8ce92-197">**Caption**</span><span class="sxs-lookup"><span data-stu-id="8ce92-197">**Caption**</span></span>  
 <span data-ttu-id="8ce92-198">如果 [標題是 MDX]\*\*\*\* 設為 [False]\*\*\*\*，則請鍵入要顯示在用戶端應用程式中的動作標題。</span><span class="sxs-lookup"><span data-stu-id="8ce92-198">Type the caption to be displayed for the action in the client application if **Caption Is MDX** is set to **False**.</span></span>  
  
 <span data-ttu-id="8ce92-199">如果 [標題是 MDX]\*\*\*\* 設為 [True]\*\*\*\*，請鍵入會傳回標題字串的 MDX 運算式。</span><span class="sxs-lookup"><span data-stu-id="8ce92-199">Type the MDX expression that returns a string for the caption if **Caption Is MDX** is set to **True**.</span></span>  
  
 <span data-ttu-id="8ce92-200">**標題是 MDX**</span><span class="sxs-lookup"><span data-stu-id="8ce92-200">**Caption is MDX**</span></span>  
 <span data-ttu-id="8ce92-201">選取 [False]\*\*\*\* 以指出 [標題]\*\*\*\* 包含一個常值字串，代表要顯示在用戶端應用程式中的動作標題。</span><span class="sxs-lookup"><span data-stu-id="8ce92-201">Select **False** to indicate that **Caption** contains a literal string representing a caption to be displayed for the action in the client application.</span></span>  
  
 <span data-ttu-id="8ce92-202">選取 **[True]** 以指出 **[標題]** 包含一個會傳回字串的 MDX 運算式，字串代表要顯示在用戶端應用程式中的動作標題。</span><span class="sxs-lookup"><span data-stu-id="8ce92-202">Select **True** to indicate that **Caption** contains an MDX expression that returns a string representing a caption to be displayed for the action in the client application.</span></span> <span data-ttu-id="8ce92-203">在動作傳回至用戶端應用程式之前，必須先解析 MDX 運算式。</span><span class="sxs-lookup"><span data-stu-id="8ce92-203">The MDX expression must be resolved before the action is returned to the client application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ce92-204">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ce92-204">See Also</span></span>  
 <span data-ttu-id="8ce92-205">[&#40;Cube 設計師的動作&#41; &#40;Analysis Services 多維度資料&#41;](actions-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="8ce92-205">[Actions &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](actions-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="8ce92-206">[工具列 &#40;動作] 索引標籤，Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="8ce92-206">[Toolbar &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="8ce92-207">[動作召集人 &#40;動作] 索引標籤、Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="8ce92-207">[Action Organizer &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="8ce92-208">[[計算工具] &#40;[動作] 索引標籤、[Cube 設計師]&#41; &#40;Analysis Services 多維度資料&#41;](calculation-tools-actions-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="8ce92-208">[Calculation Tools &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculation-tools-actions-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="8ce92-209">[[操作表單編輯器] &#40;[動作] 索引標籤、[Cube 設計師]&#41; &#40;Analysis Services 多維度資料&#41;](action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="8ce92-209">[Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="8ce92-210">[[&#40;動作] 索引標籤、Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;的 [動作表單編輯器]](drillthrough-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="8ce92-210">[Drillthrough Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](drillthrough-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)</span></span>  
  
  
