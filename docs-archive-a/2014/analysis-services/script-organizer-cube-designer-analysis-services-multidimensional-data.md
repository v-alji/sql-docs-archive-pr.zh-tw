---
title: 腳本召集人 (計算] 索引標籤、Cube 設計工具)  (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.calculationsview.scriptorganizerpane.f1
ms.assetid: 92624ca4-de67-4ebd-aab2-8adb527d327e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4ee8ccb491995176dc56da90e4cbf48961e30e98
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592911"
---
# <a name="script-organizer-calculations-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="face7-102">指令碼組合管理 (計算索引標籤，Cube 設計師) (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="face7-102">Script Organizer (Calculations Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="face7-103">在 Cube 設計師的 [計算]\*\*\*\* 索引標籤上，使用 [指令碼組合管理]\*\*\*\* 窗格，即可存取和重新排列包含在指定 Cube 之 Cube 指令碼中的導出成員、命名集以及指令碼命令。</span><span class="sxs-lookup"><span data-stu-id="face7-103">Use the **Script Organizer** pane on the **Calculations** tab in Cube Designer to access and reorder the calculated members, named sets, and script commands contained in the cube script for the specified cube.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="face7-104">表單檢視中不會顯示這個窗格。</span><span class="sxs-lookup"><span data-stu-id="face7-104">This pane is not displayed in form view.</span></span>  
  
## <a name="options"></a><span data-ttu-id="face7-105">選項</span><span class="sxs-lookup"><span data-stu-id="face7-105">Options</span></span>  
 <span data-ttu-id="face7-106">**Step**</span><span class="sxs-lookup"><span data-stu-id="face7-106">**Step**</span></span>  
 <span data-ttu-id="face7-107">顯示 Cube 指令碼中的導出成員、命名集和指令碼命令的執行順序。</span><span class="sxs-lookup"><span data-stu-id="face7-107">Displays the execution order of the calculated members, named sets, and script commands within the cube script.</span></span>  
  
 <span data-ttu-id="face7-108">在 [工具列]\*\*\*\* 窗格或內容功能表中，按一下 [上移]\*\*\*\* 或 [下移]\*\*\*\*，即可變更計算的執行順序。</span><span class="sxs-lookup"><span data-stu-id="face7-108">Click **Move Up** or **Move Down** in the **Toolbar** pane or context menu to change the execution order of the calculations.</span></span>  
  
 <span data-ttu-id="face7-109">**型別**</span><span class="sxs-lookup"><span data-stu-id="face7-109">**Type**</span></span>  
 <span data-ttu-id="face7-110">顯示識別計算為導出成員、命名集或指令碼命令的圖示。</span><span class="sxs-lookup"><span data-stu-id="face7-110">Displays an icon that identifies the calculation as a calculated member, a named set, or a script command.</span></span>  
  
 <span data-ttu-id="face7-111">**命令**</span><span class="sxs-lookup"><span data-stu-id="face7-111">**Command**</span></span>  
 <span data-ttu-id="face7-112">顯示命令的名稱 (適用於導出成員和命名集) 或計算的第一行 (適用於指令碼命令)。</span><span class="sxs-lookup"><span data-stu-id="face7-112">Displays the name of the command (for calculated members and named sets) or the first line of the calculation (for script commands.)</span></span>  
  
 <span data-ttu-id="face7-113">選取命令即可顯示適用於該命令的 [指令碼編輯器]\*\*\*\*、[導出成員表單編輯器]\*\*\*\* 或 [命名集表單編輯器]\*\*\*\* (在表單檢視中)，或將 [指令碼編輯器]\*\*\*\* 窗格的內容捲動到 Cube 指令碼中、命令所在的位置 (在指令碼檢視中)。</span><span class="sxs-lookup"><span data-stu-id="face7-113">Select a command to display the **Script Editor**, **Calculated Member Form Editor**, or **Named Set Form Editor** as appropriate for that command (in form view) or to scroll the contents of the **Script Editor** pane to the location of the command in the cube script (in script view).</span></span>  
  
## <a name="context-menu"></a><span data-ttu-id="face7-114">操作功能表</span><span class="sxs-lookup"><span data-stu-id="face7-114">Context Menu</span></span>  
 <span data-ttu-id="face7-115">以滑鼠右鍵按一下 [指令碼組合管理]\*\*\*\* 窗格中的命令，即可顯示提供下列選項的內容功能表：</span><span class="sxs-lookup"><span data-stu-id="face7-115">The following options are available in the context menu displayed by right-clicking a command in the **Script Organizer** pane:</span></span>  
  
|<span data-ttu-id="face7-116">選項</span><span class="sxs-lookup"><span data-stu-id="face7-116">Option</span></span>|<span data-ttu-id="face7-117">定義</span><span class="sxs-lookup"><span data-stu-id="face7-117">Definition</span></span>|  
|------------|----------------|  
|<span data-ttu-id="face7-118">**新增導出成員**</span><span class="sxs-lookup"><span data-stu-id="face7-118">**New Calculated Member**</span></span>|<span data-ttu-id="face7-119">選取即可顯示 [導出成員表單編輯器]\*\*\*\*，並建立新的導出成員。</span><span class="sxs-lookup"><span data-stu-id="face7-119">Select to display the **Calculated Member Form Editor** and create a new calculated member.</span></span> <span data-ttu-id="face7-120">如需 [匯出**成員表單編輯器**] 的詳細資訊，請參閱匯出[成員表單編輯器 &#40;計算] 索引標籤、Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="face7-120">For more information about the **Calculated Member Form Editor**, see [Calculated Member Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="face7-121">**新增命名集**</span><span class="sxs-lookup"><span data-stu-id="face7-121">**New Named Set**</span></span>|<span data-ttu-id="face7-122">選取即可顯示 [命名集表單編輯器]\*\*\*\*，並建立新的命名集。</span><span class="sxs-lookup"><span data-stu-id="face7-122">Select to display the **Named Set Form Editor** and create a new named set.</span></span> <span data-ttu-id="face7-123">如需 [**命名集表單編輯器**] 的詳細資訊，請參閱[命名集表單編輯器 &#40;計算] 索引標籤，Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="face7-123">For more information about the **Named Set Form Editor**, see [Named Set Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="face7-124">**新增指令碼命令**</span><span class="sxs-lookup"><span data-stu-id="face7-124">**New Script Command**</span></span>|<span data-ttu-id="face7-125">選取即可顯示 [指令碼編輯器]\*\*\*\*，並建立新的指令碼命令。</span><span class="sxs-lookup"><span data-stu-id="face7-125">Select to display the **Script Editor** and create a new script command.</span></span> <span data-ttu-id="face7-126">如需**腳本編輯器**的詳細資訊，請參閱[腳本編輯器 &#40;計算] 索引標籤、Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="face7-126">For more information about the **Script Editor**, see [Script Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="face7-127">**上移**</span><span class="sxs-lookup"><span data-stu-id="face7-127">**Move Up**</span></span>|<span data-ttu-id="face7-128">選取即可將選取的計算向上移動一個位置。</span><span class="sxs-lookup"><span data-stu-id="face7-128">Select to move the selected calculation up one place.</span></span><br /><br /> <span data-ttu-id="face7-129">注意：如果選取的計算無法再移動，此選項會停用。</span><span class="sxs-lookup"><span data-stu-id="face7-129">Note: This option is disabled if the selected calculation cannot be moved further.</span></span>|  
|<span data-ttu-id="face7-130">**下移**</span><span class="sxs-lookup"><span data-stu-id="face7-130">**Move Down**</span></span>|<span data-ttu-id="face7-131">選取即可將選取的計算向下移動一個位置。</span><span class="sxs-lookup"><span data-stu-id="face7-131">Select to move the selected calculation down one place.</span></span><br /><br /> <span data-ttu-id="face7-132">注意：如果選取的計算無法再移動，此選項會停用。</span><span class="sxs-lookup"><span data-stu-id="face7-132">Note: This option is disabled if the selected calculation cannot be moved further.</span></span>|  
|<span data-ttu-id="face7-133">**刪除**</span><span class="sxs-lookup"><span data-stu-id="face7-133">**Delete**</span></span>|<span data-ttu-id="face7-134">選取即可刪除選取的計算。</span><span class="sxs-lookup"><span data-stu-id="face7-134">Select to delete the selected calculation.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="face7-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="face7-135">See Also</span></span>  
 <span data-ttu-id="face7-136">[Cube 設計工具 &#40;Analysis Services-多維度資料&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="face7-136">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="face7-137">[工具列 &#40;計算] 索引標籤，Cube 設計師&#41; &#40;Analysis Services 多維度資料&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="face7-137">[Toolbar &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="face7-138">[計算工具 &#40;計算] 索引標籤，Cube 設計師&#41; &#40;Analysis Services 多維度資料&#41;](calculation-tools-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="face7-138">[Calculation Tools &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculation-tools-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="face7-139">[匯出成員表單編輯器 &#40;計算] 索引標籤、Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="face7-139">[Calculated Member Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="face7-140">[命名集表單編輯器 &#40;計算] 索引標籤，Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="face7-140">[Named Set Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="face7-141">[腳本編輯器 &#40;[計算] 索引標籤、Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="face7-141">[Script Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="face7-142">&#40;Cube 設計師的計算&#41; &#40;Analysis Services 多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="face7-142">Calculations &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](calculations-cube-designer-analysis-services-multidimensional-data.md)  
  
  
