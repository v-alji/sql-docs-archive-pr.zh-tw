---
title: " (Cube 設計師的計算)  (Analysis Services-多維度資料) |Microsoft Docs"
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.calculationsview.f1
ms.assetid: 46e2fbe2-bb41-4eaa-91f8-eb2bd3b8d00d
author: minewiskan
ms.author: owend
ms.openlocfilehash: fdbc35a8e47557923b90cda4e72280c3cca940dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593711"
---
# <a name="calculations-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="113db-102">\*計算 (Cube 設計工具) (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="113db-102">Calculations (Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="113db-103">使用 Cube 設計師中的 [計算]\*\*\*\* 索引標籤來檢視和編輯計算，包含選取之 Cube 的導出成員、命名集和多維度運算式 (MDX) 指令碼命令。</span><span class="sxs-lookup"><span data-stu-id="113db-103">Use the **Calculations** tab in Cube Designer to view and edit calculations, including calculated members, named sets, and Multidimensional Expressions (MDX) script commands for the selected cube.</span></span>  
  
## <a name="form-view-and-script-view"></a><span data-ttu-id="113db-104">表單檢視和指令碼檢視</span><span class="sxs-lookup"><span data-stu-id="113db-104">Form View and Script View</span></span>  
 <span data-ttu-id="113db-105">檢視或編輯計算時， **[計算]** 索引標籤支援兩種不同的檢視方式：</span><span class="sxs-lookup"><span data-stu-id="113db-105">The **Calculations** tab supports two different views when viewing or editing calculations:</span></span>  
  
-   <span data-ttu-id="113db-106">表單檢視</span><span class="sxs-lookup"><span data-stu-id="113db-106">Form view</span></span>  
  
     <span data-ttu-id="113db-107">這種檢視方式顯示與 Cube 相關聯的 MDX 指令碼中所包含的導出成員、命名集和指令碼命令的組織檢視，並提供表單編輯器以檢視和編輯導出成員、命名集，以及顯示 Cube 可以使用的中繼資料、函數和工具。</span><span class="sxs-lookup"><span data-stu-id="113db-107">This view displays an organized view of the calculated members, named sets, and script commands contained in the MDX script associated with the cube and provides form editors to view and edit calculated members and named sets, as well as displaying the metadata, functions, and tools available to the cube.</span></span>  
  
-   <span data-ttu-id="113db-108">指令碼檢視</span><span class="sxs-lookup"><span data-stu-id="113db-108">Script view</span></span>  
  
     <span data-ttu-id="113db-109">針對進階使用者，此檢視方式顯示整個與 Cube 相關聯的 MDX 指令碼，以及顯示 Cube 可以使用的中繼資料、函數和工具。</span><span class="sxs-lookup"><span data-stu-id="113db-109">For advanced users, this view displays the entire MDX script associated with the cube, as well as displaying the metadata, functions, and tools available to the cube.</span></span>  
  
## <a name="panes"></a><span data-ttu-id="113db-110">窗格</span><span class="sxs-lookup"><span data-stu-id="113db-110">Panes</span></span>  
 <span data-ttu-id="113db-111">**工具列**</span><span class="sxs-lookup"><span data-stu-id="113db-111">**Toolbar**</span></span>  
 <span data-ttu-id="113db-112">使用表單檢視和腳本視圖中的工具列，來執行此索引標籤上的一般作業。如需這個窗格的詳細資訊，請參閱[工具列 &#40;計算] 索引標籤、Cube 設計師&#41; &#40;Analysis Services 多維度資料&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="113db-112">Use the toolbar in both form view and script view to perform common operations on this tab. For more information about this pane, see [Toolbar &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="113db-113">**指令碼組合管理**</span><span class="sxs-lookup"><span data-stu-id="113db-113">**Script Organizer**</span></span>  
 <span data-ttu-id="113db-114">使用表單檢視中的 [指令碼組合管理]\*\*\*\* 窗格，依排序的格式來顯示 Cube 指令碼的內容。</span><span class="sxs-lookup"><span data-stu-id="113db-114">Use the **Script Organizer** pane in form view to display the contents of the cube script in an ordered format.</span></span> <span data-ttu-id="113db-115">如需此窗格的詳細資訊，請參閱[指令碼組合管理 &#40;計算索引標籤，Cube 設計師&#41; &#40;Analysis Services - 多維度資料&#41;](script-organizer-cube-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="113db-115">For more information about this pane, see [Script Organizer &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](script-organizer-cube-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="113db-116">**計算工具**</span><span class="sxs-lookup"><span data-stu-id="113db-116">**Calculation Tools**</span></span>  
 <span data-ttu-id="113db-117">在表單檢視和指令碼檢視中，使用 [計算工具]\*\*\*\* 窗格來顯示 Cube 可以使用的中繼資料、函數和工具。</span><span class="sxs-lookup"><span data-stu-id="113db-117">Use the **Calculation Tools** pane in both form view and script view to display metadata, functions, and tools available to the cube.</span></span> <span data-ttu-id="113db-118">如需此窗格的詳細資訊，請參閱[計算工具 &#40;計算索引標籤，Cube 設計師&#41; &#40;Analysis Services - 多維度資料&#41;](calculation-tools-cube-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="113db-118">For more information about this pane, see [Calculation Tools &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculation-tools-cube-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="113db-119">**指令碼編輯器**</span><span class="sxs-lookup"><span data-stu-id="113db-119">**Script Editor**</span></span>  
 <span data-ttu-id="113db-120">使用指令碼檢視中的 [指令碼編輯器]\*\*\*\* 窗格來編輯整個 Cube 指令碼，以及在表單檢視中編輯 Cube 指令碼中所包含的指令碼命令。</span><span class="sxs-lookup"><span data-stu-id="113db-120">Use the **Script Editor** pane in script view to edit the entire cube script and in form view to edit script commands contained in the cube script.</span></span> <span data-ttu-id="113db-121">如需此窗格的詳細資訊，請參閱[指令碼編輯器 &#40;計算索引標籤，Cube 設計師&#41; &#40;Analysis Services - 多維度資料&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="113db-121">For more information about this pane, see [Script Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="113db-122">**導出成員表單編輯器**</span><span class="sxs-lookup"><span data-stu-id="113db-122">**Calculated Member Form Editor**</span></span>  
 <span data-ttu-id="113db-123">使用表單檢視中的 [導出成員表單編輯器]\*\*\*\* 窗格，來編輯 Cube 指令碼中的導出成員。</span><span class="sxs-lookup"><span data-stu-id="113db-123">Use the **Calculated Member Form Editor** pane in form view to edit calculated members in the cube script.</span></span> <span data-ttu-id="113db-124">如需此窗格的詳細資訊，請參閱[導出成員表單編輯器 &#40;計算索引標籤，Cube 設計師&#41; &#40;Analysis Services - 多維度資料&#41;](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="113db-124">For more information about this pane, see [Calculated Member Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="113db-125">**命名集表單編輯器**</span><span class="sxs-lookup"><span data-stu-id="113db-125">**Named Set Form Editor**</span></span>  
 <span data-ttu-id="113db-126">使用表單檢視中的 [命名集表單編輯器]\*\*\*\* 窗格，來編輯 Cube 指令碼中的命名集。</span><span class="sxs-lookup"><span data-stu-id="113db-126">Use the **Named Set Form Editor** pane in form view to edit named sets in the cube script.</span></span> <span data-ttu-id="113db-127">如需此窗格的詳細資訊，請參閱[命名集表單編輯器 &#40;計算索引標籤，Cube 設計師&#41; &#40;Analysis Services - 多維度資料&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="113db-127">For more information about this pane, see [Named Set Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="113db-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="113db-128">See Also</span></span>  
 <span data-ttu-id="113db-129">[Cube 物件 &#40;Analysis Services 多維度資料&#41;](multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="113db-129">[Cube Objects &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="113db-130">[Acwp](multidimensional-models-olap-logical-cube-objects/calculations.md) </span><span class="sxs-lookup"><span data-stu-id="113db-130">[Calculations](multidimensional-models-olap-logical-cube-objects/calculations.md) </span></span>  
 <span data-ttu-id="113db-131">[MDX 腳本基礎 &#40;Analysis Services&#41;](multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="113db-131">[MDX Scripting Fundamentals &#40;Analysis Services&#41;](multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md) </span></span>  
 <span data-ttu-id="113db-132">[Cube 設計工具 &#40;Analysis Services-多維度資料&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="113db-132">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="113db-133">建立命名集</span><span class="sxs-lookup"><span data-stu-id="113db-133">Create Named Sets</span></span>](multidimensional-models/create-named-sets.md)  
  
  
