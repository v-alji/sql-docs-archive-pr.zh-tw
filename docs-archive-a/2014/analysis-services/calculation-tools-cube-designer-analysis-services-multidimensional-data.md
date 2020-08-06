---
title: 計算工具 (計算] 索引標籤、Cube 設計師)  (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.calculationsview.calculationtoolspane.f1
ms.assetid: b1aa8a1a-6532-45d2-8f53-d3e211d7197a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6701a15a7d773a90e48ec39dc976b9ef579c9ec8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593083"
---
# <a name="calculation-tools-calculations-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="98aea-102">計算工具 (計算索引標籤，Cube 設計師) (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="98aea-102">Calculation Tools (Calculations Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="98aea-103">使用 Cube 設計師之 **[計算]** 索引標籤上的 **[計算工具]** 窗格，即可瀏覽可在計算中使用的中繼資料、函數以及範本。</span><span class="sxs-lookup"><span data-stu-id="98aea-103">Use the **Calculation Tools** pane on the **Calculations** tab in Cube Designer to explore metadata, functions, and templates available for use in calculations.</span></span>  
  
## <a name="options"></a><span data-ttu-id="98aea-104">選項</span><span class="sxs-lookup"><span data-stu-id="98aea-104">Options</span></span>  
 <span data-ttu-id="98aea-105">**中繼資料**</span><span class="sxs-lookup"><span data-stu-id="98aea-105">**Metadata**</span></span>  
 <span data-ttu-id="98aea-106">顯示選取之 Cube 的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="98aea-106">Displays the metadata for the selected cube.</span></span>  
  
 <span data-ttu-id="98aea-107">將選取的元素拖曳至 [指令碼編輯器]、[導出成員表單編輯器] 或 [命名集表單編輯器] 窗格，即可在窗格中選取的位置包含該元素的多維度運算式 (MDX) 語法。</span><span class="sxs-lookup"><span data-stu-id="98aea-107">Drag a selected element to the Script Editor, Calculated Member Form Editor, or Named Set Form Editor pane to include the Multidimensional Expressions (MDX) syntax for that element at the selected location in the pane.</span></span>  
  
 <span data-ttu-id="98aea-108">**函式**</span><span class="sxs-lookup"><span data-stu-id="98aea-108">**Functions**</span></span>  
 <span data-ttu-id="98aea-109">顯示運算式和條件可用的函數。</span><span class="sxs-lookup"><span data-stu-id="98aea-109">Displays the functions available for expressions and conditions.</span></span>  
  
 <span data-ttu-id="98aea-110">將選取的元素拖曳至 **[指令碼編輯器]**、 **[導出成員表單編輯器]** 或 **[命名集表單編輯器]** 窗格，即可在窗格中選取的位置包含該元素的 MDX 語法。</span><span class="sxs-lookup"><span data-stu-id="98aea-110">Drag a selected element to the **Script Editor**, **Calculated Member Form Editor**, or **Named Set Form Editor** pane to include the MDX syntax for that element at the selected location in the pane.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="98aea-111">在專案模式中， **[計算工具]** 對話方塊會從名為 MDXFunctions.xml 的 XML 檔案 (包含在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中) 讀取此選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="98aea-111">In project mode, the **Calculation Tools** dialog box reads information for this option from an XML file named MDXFunctions.xml, included with [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="98aea-112">在線上模式中，此選項的資訊是從執行個體的 MDSCHEMA_FUNCTIONS 結構描述資料列集擷取。</span><span class="sxs-lookup"><span data-stu-id="98aea-112">In online mode, information for this option is retrieved from the MDSCHEMA_FUNCTIONS schema rowset for the instance.</span></span>  
  
 <span data-ttu-id="98aea-113">**範本**</span><span class="sxs-lookup"><span data-stu-id="98aea-113">**Templates**</span></span>  
 <span data-ttu-id="98aea-114">顯示導出成員、命名集以及指令碼命令可用之預先定義的範本。</span><span class="sxs-lookup"><span data-stu-id="98aea-114">Displays the predefined templates available for calculated members, named sets, and script commands.</span></span>  
  
 <span data-ttu-id="98aea-115">將選取的元素拖曳至 **[指令碼編輯器]**、 **[導出成員表單編輯器]** 或 **[命名集表單編輯器]** 窗格，即可在窗格中選取的位置包含該元素的 MDX 語法。</span><span class="sxs-lookup"><span data-stu-id="98aea-115">Drag a selected element to the **Script Editor**, **Calculated Member Form Editor**, or **Named Set Form Editor** pane to include the MDX syntax for that element at the selected location in the pane.</span></span>  
  
## <a name="context-menu"></a><span data-ttu-id="98aea-116">操作功能表</span><span class="sxs-lookup"><span data-stu-id="98aea-116">Context Menu</span></span>  
 <span data-ttu-id="98aea-117">以滑鼠右鍵按一下 [計算工具]\*\*\*\* 窗格中的元素，即可顯示提供下列選項的內容功能表：</span><span class="sxs-lookup"><span data-stu-id="98aea-117">The following options are available in the context menu displayed by right-clicking an element in the **Calculation Tools** pane:</span></span>  
  
 <span data-ttu-id="98aea-118">**複製**</span><span class="sxs-lookup"><span data-stu-id="98aea-118">**Copy**</span></span>  
 <span data-ttu-id="98aea-119">選取即可將 **[中繼資料]** 或 **[函數]** 中選取的元素複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="98aea-119">Select to copy the selected element in **Metadata** or **Functions** to the Clipboard.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="98aea-120"> 如果已選取 **[範本]** ，則不會顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="98aea-120">This option is not displayed if **Templates** is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="98aea-121"> 如果選取的成員無法複製 (例如 **[中繼資料]** 中顯示之維度的 **[集]** 資料夾或 **[函數]** 中顯示之函數的函數群組資料夾)，則會停用此選項。</span><span class="sxs-lookup"><span data-stu-id="98aea-121">This option is disabled if the selected member cannot be copied, such as the **Sets** folder of a dimension displayed in **Metadata** or the function group folder for a function displayed in **Functions**.</span></span>  
  
 <span data-ttu-id="98aea-122">**篩選成員**</span><span class="sxs-lookup"><span data-stu-id="98aea-122">**Filter Members**</span></span>  
 <span data-ttu-id="98aea-123">選取即可顯示 **[篩選成員]** 對話方塊，並篩選針對 **[中繼資料]** 中選取之元素顯示的成員。</span><span class="sxs-lookup"><span data-stu-id="98aea-123">Select to display the **Filter Members** dialog box and filter members displayed for the selected element in **Metadata**.</span></span> <span data-ttu-id="98aea-124">如需 [篩選成員]\*\*\*\* 對話方塊的詳細資訊，請參閱[篩選成員對話方塊 &#40;Analysis Services - 多維度資料&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="98aea-124">For more information about the **Filter Members** dialog box, see [Filter Members Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="98aea-125"> 只有選取 **[中繼資料]** 時，才會顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="98aea-125">This option is displayed only if **Metadata** is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="98aea-126"> 只有在 **[中繼資料]** 中選取屬性的層級時，才會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="98aea-126">This option is enabled only if a level for an attribute is selected in **Metadata**.</span></span>  
  
 <span data-ttu-id="98aea-127">**新增範本**</span><span class="sxs-lookup"><span data-stu-id="98aea-127">**Add Template**</span></span>  
 <span data-ttu-id="98aea-128">選取即可根據選取的 Cube 指令碼範本來加入新的導出成員、命名集或指令碼命令，並顯示適合該命令 (以表單檢視) 的 [指令碼編輯器]\*\*\*\*、[導出成員表單編輯器]\*\*\*\* 或 [命名集表單編輯器]\*\*\*\*，或將 [指令碼編輯器]\*\*\*\* 窗格的內容捲動至 Cube 指令碼中命令的位置 (以指令碼檢視)。</span><span class="sxs-lookup"><span data-stu-id="98aea-128">Select to add a new calculated member, named set, or script command based on the selected template to the cube script and display the **Script Editor**, **Calculated Member Form Editor**, or **Named Set Form Editor** as appropriate for that command (in form view) or to scroll the contents of the **Script Editor** pane to the location of the command in the cube script (in script view).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="98aea-129"> 只有選取 **[中繼資料]** 時，才會顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="98aea-129">This option is displayed only if **Metadata** is selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98aea-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98aea-130">See Also</span></span>  
 <span data-ttu-id="98aea-131">[Cube 設計工具 &#40;Analysis Services-多維度資料&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="98aea-131">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="98aea-132">[工具列 &#40;計算] 索引標籤，Cube 設計師&#41; &#40;Analysis Services 多維度資料&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="98aea-132">[Toolbar &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="98aea-133">[腳本召集人 &#40;計算] 索引標籤、Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](script-organizer-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="98aea-133">[Script Organizer &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](script-organizer-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="98aea-134">[匯出成員表單編輯器 &#40;計算] 索引標籤、Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="98aea-134">[Calculated Member Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="98aea-135">[命名集表單編輯器 &#40;計算] 索引標籤，Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="98aea-135">[Named Set Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="98aea-136">[腳本編輯器 &#40;[計算] 索引標籤、Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="98aea-136">[Script Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="98aea-137">&#40;Cube 設計師的計算&#41; &#40;Analysis Services 多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="98aea-137">Calculations &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](calculations-cube-designer-analysis-services-multidimensional-data.md)  
  
  
