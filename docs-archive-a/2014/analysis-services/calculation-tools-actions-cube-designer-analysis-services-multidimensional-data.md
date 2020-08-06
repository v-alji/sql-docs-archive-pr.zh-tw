---
title: 計算工具 ([動作] 索引標籤、Cube 設計師)  (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.actionsview.calculationtoolspane.f1
ms.assetid: a3370370-43cd-4cc2-bb9f-c0d988b96f05
author: minewiskan
ms.author: owend
ms.openlocfilehash: 123fa38ea2decb6af914e93fcefda4508f08545e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593082"
---
# <a name="calculation-tools-actions-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="923b5-102">計算工具 (動作索引標籤，Cube 設計師) (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="923b5-102">Calculation Tools (Actions Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="923b5-103">使用 Cube 設計師之 **[動作]** 索引標籤上的 **[計算工具]** 窗格，即可瀏覽可以在動作、鑽研動作和報表動作中使用的中繼資料、函數以及範本。</span><span class="sxs-lookup"><span data-stu-id="923b5-103">Use the **Calculation Tools** pane on the **Actions** tab in Cube Designer to explore metadata, functions, and templates available for use in actions, drillthrough actions, and report actions.</span></span>  
  
## <a name="options"></a><span data-ttu-id="923b5-104">選項</span><span class="sxs-lookup"><span data-stu-id="923b5-104">Options</span></span>  
 <span data-ttu-id="923b5-105">**中繼資料**</span><span class="sxs-lookup"><span data-stu-id="923b5-105">**Metadata**</span></span>  
 <span data-ttu-id="923b5-106">顯示選取之 Cube 的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="923b5-106">Displays the metadata for the selected cube.</span></span>  
  
 <span data-ttu-id="923b5-107">將選取的元素拖曳至 [動作表單編輯器]\*\*\*\*、[鑽研動作表單編輯器]\*\*\*\* 或 [報表動作表單編輯器]\*\*\*\* 窗格，即可在窗格中選取的位置包含該元素的多維度運算式 (MDX) 語法。</span><span class="sxs-lookup"><span data-stu-id="923b5-107">Drag a selected element to the **Action Form Editor**, **Drillthrough Action Form Editor**, or **Report Action Form Editor** pane to include the Multidimensional Expressions (MDX) syntax for that element at the selected location in the pane.</span></span>  
  
 <span data-ttu-id="923b5-108">**函式**</span><span class="sxs-lookup"><span data-stu-id="923b5-108">**Functions**</span></span>  
 <span data-ttu-id="923b5-109">顯示運算式和條件可用的函數。</span><span class="sxs-lookup"><span data-stu-id="923b5-109">Displays the functions available for expressions and conditions.</span></span>  
  
 <span data-ttu-id="923b5-110">將選取的元素拖曳至 **[動作表單編輯器]**、 **[鑽研動作表單編輯器]** 或 **[報表動作表單編輯器]** 窗格，即可在窗格中選取的位置包含該元素的 MDX 語法。</span><span class="sxs-lookup"><span data-stu-id="923b5-110">Drag a selected element to the **Action Form Editor**, **Drillthrough Action Form Editor**, or **Report Action Form Editor** pane to include the MDX syntax for that element at the selected location in the pane.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="923b5-111">在專案模式中， **[計算工具]** 對話方塊會從名為 MDXFunctions.xml 的 XML 檔案 (包含在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中) 讀取此選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="923b5-111">In project mode, the **Calculation Tools** dialog box reads information for this option from an XML file named MDXFunctions.xml, included with [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="923b5-112">在線上模式中，此選項的資訊是從執行個體的 MDSCHEMA_FUNCTIONS 結構描述資料列集擷取。</span><span class="sxs-lookup"><span data-stu-id="923b5-112">In online mode, information for this option is retrieved from the MDSCHEMA_FUNCTIONS schema rowset for the instance.</span></span>  
  
 <span data-ttu-id="923b5-113">**範本**</span><span class="sxs-lookup"><span data-stu-id="923b5-113">**Templates**</span></span>  
 <span data-ttu-id="923b5-114">顯示動作可用之預先定義的範本。</span><span class="sxs-lookup"><span data-stu-id="923b5-114">Displays the predefined templates available for actions.</span></span>  
  
 <span data-ttu-id="923b5-115">將選取的元素拖曳至 **[動作表單編輯器]**、 **[鑽研動作表單編輯器]** 或 **[報表動作表單編輯器]** 窗格，即可在窗格中選取的位置包含該元素的 MDX 語法。</span><span class="sxs-lookup"><span data-stu-id="923b5-115">Drag a selected element to the **Action Form Editor**, **Drillthrough Action Form Editor**, or **Report Action Form Editor** pane to include the MDX syntax for that element at the selected location in the pane.</span></span>  
  
## <a name="context-menu"></a><span data-ttu-id="923b5-116">操作功能表</span><span class="sxs-lookup"><span data-stu-id="923b5-116">Context Menu</span></span>  
 <span data-ttu-id="923b5-117">以滑鼠右鍵按一下 [計算工具]\*\*\*\* 窗格中的元素，即可顯示提供下列選項的內容功能表：</span><span class="sxs-lookup"><span data-stu-id="923b5-117">The following options are available in the context menu displayed by right-clicking an element in the **Calculation Tools** pane:</span></span>  
  
|<span data-ttu-id="923b5-118">選項</span><span class="sxs-lookup"><span data-stu-id="923b5-118">Option</span></span>|<span data-ttu-id="923b5-119">定義</span><span class="sxs-lookup"><span data-stu-id="923b5-119">Definition</span></span>|  
|------------|----------------|  
|<span data-ttu-id="923b5-120">**複製**</span><span class="sxs-lookup"><span data-stu-id="923b5-120">**Copy**</span></span>|<span data-ttu-id="923b5-121">選取即可將 **[中繼資料]** 或 **[函數]** 中選取的元素複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="923b5-121">Select to copy the selected element in **Metadata** or **Functions** to the Clipboard.</span></span><br /><br /> <span data-ttu-id="923b5-122">請注意，如果已選取 [**範本**]，則不會顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="923b5-122">Note that this option is not displayed if **Templates** is selected.</span></span> <span data-ttu-id="923b5-123">另請注意，如果選取的成員無法複製（例如，在 [**中繼資料**] 中顯示之維度的 [**集**] 資料夾或 **[函數]** 中顯示之函式的函式群組資料夾），則會停用此選項。</span><span class="sxs-lookup"><span data-stu-id="923b5-123">Also note that this option is disabled if the selected member cannot be copied, such as the **Sets** folder of a dimension displayed in **Metadata** or the function group folder for a function displayed in **Functions**.</span></span>|  
|<span data-ttu-id="923b5-124">**篩選成員**</span><span class="sxs-lookup"><span data-stu-id="923b5-124">**Filter Members**</span></span>|<span data-ttu-id="923b5-125">選取即可顯示 **[篩選成員]** 對話方塊，並篩選針對 **[中繼資料]** 中選取之元素顯示的成員。</span><span class="sxs-lookup"><span data-stu-id="923b5-125">Select to display the **Filter Members** dialog box and filter members displayed for the selected element in **Metadata**.</span></span> <span data-ttu-id="923b5-126">如需 [篩選成員]\*\*\*\* 對話方塊的詳細資訊，請參閱[篩選成員對話方塊 &#40;Analysis Services - 多維度資料&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="923b5-126">For more information about the **Filter Members** dialog box, see [Filter Members Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md).</span></span><br /><br /> <span data-ttu-id="923b5-127">請注意，只有在選取 [**中繼資料**] 時，才會顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="923b5-127">Note that this option is displayed only if **Metadata** is selected.</span></span> <span data-ttu-id="923b5-128">另請注意，只有在 [**中繼資料**] 中選取屬性的層級時，才會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="923b5-128">Also note that this option is enabled only if a level for an attribute is selected in **Metadata**.</span></span>|  
|<span data-ttu-id="923b5-129">**新增範本**</span><span class="sxs-lookup"><span data-stu-id="923b5-129">**Add Template**</span></span>|<span data-ttu-id="923b5-130">選取即可根據選取的範本將新動作、鑽研動作或報表動作加入至 Cube，並分別顯示 **[動作表單編輯器]**、 **[鑽研動作表單編輯器]** 或 **[報表動作表單編輯器]**。</span><span class="sxs-lookup"><span data-stu-id="923b5-130">Select to add a new action, drillthrough action, or report action based on the selected template to the cube and display, respectively, the **Action Form Editor**, **Drillthrough Action Form Editor**, or **Report Action Form Editor**.</span></span><br /><br /> <span data-ttu-id="923b5-131">注意：只有在已選取 [**中繼資料**] 時，才會顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="923b5-131">Note: This option is displayed only if **Metadata** is selected.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="923b5-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="923b5-132">See Also</span></span>  
 <span data-ttu-id="923b5-133">[MDX 腳本基礎 &#40;Analysis Services&#41;](multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="923b5-133">[MDX Scripting Fundamentals &#40;Analysis Services&#41;](multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md) </span></span>  
 <span data-ttu-id="923b5-134">[&#40;Cube 設計師的動作&#41; &#40;Analysis Services 多維度資料&#41;](actions-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="923b5-134">[Actions &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](actions-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="923b5-135">[工具列 &#40;動作] 索引標籤，Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="923b5-135">[Toolbar &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="923b5-136">[動作召集人 &#40;動作] 索引標籤、Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="923b5-136">[Action Organizer &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="923b5-137">[[操作表單編輯器] &#40;[動作] 索引標籤、[Cube 設計師]&#41; &#40;Analysis Services 多維度資料&#41;](action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="923b5-137">[Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="923b5-138">[[&#40;動作] 索引標籤、Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;的 [動作表單編輯器]](drillthrough-action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="923b5-138">[Drillthrough Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](drillthrough-action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="923b5-139">[報表操作表單編輯器 &#40;動作] 索引標籤、Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](report-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="923b5-139">[Report Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](report-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)</span></span>  
  
  
