---
title: 計算工具 (Kpi 索引標籤、Cube 設計師)  (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.kpisview.calculationtoolspane.f1
ms.assetid: c030c725-7763-4c23-9988-4b274a88fc31
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7bb8470173b0a413795fb7b5e3213bb50aa8ee43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593081"
---
# <a name="calculation-tools-kpis-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="342e2-102">計算工具 (KPI 索引標籤，Cube 設計師) (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="342e2-102">Calculation Tools (KPIs Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="342e2-103">使用 [Cube 設計師] 中之 [KPI]\*\*\*\* 索引標籤上的 [計算工具]\*\*\*\* 窗格，即可瀏覽在關鍵效能指標 (KPI) 中可以使用的中繼資料、函數以及範本。</span><span class="sxs-lookup"><span data-stu-id="342e2-103">Use the **Calculation Tools** pane on the **KPIs** tab in Cube Designer to explore metadata, functions, and templates available for use in Key Performance Indicators (KPIs).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="342e2-104">此窗格只會以表單檢視方式顯示。</span><span class="sxs-lookup"><span data-stu-id="342e2-104">This pane is displayed only in form view.</span></span>  
  
## <a name="options"></a><span data-ttu-id="342e2-105">選項</span><span class="sxs-lookup"><span data-stu-id="342e2-105">Options</span></span>  
 <span data-ttu-id="342e2-106">**中繼資料**</span><span class="sxs-lookup"><span data-stu-id="342e2-106">**Metadata**</span></span>  
 <span data-ttu-id="342e2-107">顯示選取之 Cube 的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="342e2-107">Displays the metadata for the selected cube.</span></span>  
  
 <span data-ttu-id="342e2-108">將選取的元素拖曳至 [KPI 表單編輯器]\*\*\*\* 窗格，即可在窗格中選取的位置包含該元素的多維度運算式 (MDX) 語法。</span><span class="sxs-lookup"><span data-stu-id="342e2-108">Drag a selected element to the **KPI Form Editor** pane to include the Multidimensional Expressions (MDX) syntax for that element at the selected location in the pane.</span></span>  
  
 <span data-ttu-id="342e2-109">**函式**</span><span class="sxs-lookup"><span data-stu-id="342e2-109">**Functions**</span></span>  
 <span data-ttu-id="342e2-110">顯示運算式和條件可用的函數。</span><span class="sxs-lookup"><span data-stu-id="342e2-110">Displays the functions available for expressions and conditions.</span></span>  
  
 <span data-ttu-id="342e2-111">將選取的元素拖曳至 **[KPI 表單編輯器]** 窗格，即可在窗格中選取的位置包含該元素的 MDX 語法。</span><span class="sxs-lookup"><span data-stu-id="342e2-111">Drag a selected element to the **KPI Form Editor** pane to include the MDX syntax for that element at the selected location in the pane.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="342e2-112">在專案模式中， **[計算工具]** 對話方塊會從名為 MDXFunctions.xml 的 XML 檔案 (包含在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中) 讀取此選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="342e2-112">In project mode, the **Calculation Tools** dialog box reads information for this option from an XML file named MDXFunctions.xml, included with [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="342e2-113">在線上模式中，此選項的資訊是從執行個體的 MDSCHEMA_FUNCTIONS 結構描述資料列集擷取。</span><span class="sxs-lookup"><span data-stu-id="342e2-113">In online mode, information for this option is retrieved from the MDSCHEMA_FUNCTIONS schema rowset for the instance.</span></span>  
  
 <span data-ttu-id="342e2-114">**範本**</span><span class="sxs-lookup"><span data-stu-id="342e2-114">**Templates**</span></span>  
 <span data-ttu-id="342e2-115">顯示 KPI 可用之預先定義的範本。</span><span class="sxs-lookup"><span data-stu-id="342e2-115">Displays the predefined templates available for KPIs.</span></span>  
  
 <span data-ttu-id="342e2-116">將選取的元素拖曳至 **[KPI 表單編輯器]** 窗格，即可在窗格中選取的位置包含該元素的 MDX 語法。</span><span class="sxs-lookup"><span data-stu-id="342e2-116">Drag a selected element to the **KPI Form Editor** pane to include the MDX syntax for that element at the selected location in the pane.</span></span>  
  
## <a name="context-menu"></a><span data-ttu-id="342e2-117">操作功能表</span><span class="sxs-lookup"><span data-stu-id="342e2-117">Context Menu</span></span>  
 <span data-ttu-id="342e2-118">以滑鼠右鍵按一下 [計算工具]\*\*\*\* 窗格中的元素，即可顯示提供下列選項的內容功能表：</span><span class="sxs-lookup"><span data-stu-id="342e2-118">The following options are available in the context menu displayed by right-clicking an element in the **Calculation Tools** pane:</span></span>  
  
 <span data-ttu-id="342e2-119">**複製**</span><span class="sxs-lookup"><span data-stu-id="342e2-119">**Copy**</span></span>  
 <span data-ttu-id="342e2-120">選取即可將 **[中繼資料]** 或 **[函數]** 中選取的元素複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="342e2-120">Select to copy the selected element in **Metadata** or **Functions** to the Clipboard.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="342e2-121"> 如果已選取 **[範本]** ，則不會顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="342e2-121">This option is not displayed if **Templates** is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="342e2-122"> 如果選取的成員無法複製 (例如 **[中繼資料]** 中顯示之維度的 **[集]** 資料夾或 **[函數]** 中顯示之函數的函數群組資料夾)，則會停用此選項。</span><span class="sxs-lookup"><span data-stu-id="342e2-122">This option is disabled if the selected member cannot be copied, such as the **Sets** folder of a dimension displayed in **Metadata** or the function group folder for a function displayed in **Functions**.</span></span>  
  
 <span data-ttu-id="342e2-123">**篩選成員**</span><span class="sxs-lookup"><span data-stu-id="342e2-123">**Filter Members**</span></span>  
 <span data-ttu-id="342e2-124">選取即可顯示 **[篩選成員]** 對話方塊，並篩選針對 **[中繼資料]** 中選取之元素顯示的成員。</span><span class="sxs-lookup"><span data-stu-id="342e2-124">Select to display the **Filter Members** dialog box and filter members displayed for the selected element in **Metadata**.</span></span> <span data-ttu-id="342e2-125">如需 [篩選成員]\*\*\*\* 對話方塊的詳細資訊，請參閱[篩選成員對話方塊 &#40;Analysis Services - 多維度資料&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="342e2-125">For more information about the **Filter Members** dialog box, see [Filter Members Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="342e2-126"> 只有選取 **[中繼資料]** 時，才會顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="342e2-126">This option is displayed only if **Metadata** is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="342e2-127"> 只有在 **[中繼資料]** 中選取屬性的層級時，才會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="342e2-127">This option is enabled only if a level for an attribute is selected in **Metadata**.</span></span>  
  
 <span data-ttu-id="342e2-128">**新增範本**</span><span class="sxs-lookup"><span data-stu-id="342e2-128">**Add Template**</span></span>  
 <span data-ttu-id="342e2-129">選取即可根據選取的範本將新的導出成員、命名集或指令碼命令加入至 Cube 指令碼，並以表單檢視顯示 [KPI 表單編輯器]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="342e2-129">Select to add a new calculated member, named set, or script command based on the selected template to the cube script and display the **KPI Form Editor** in form view.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="342e2-130"> 只有選取 **[中繼資料]** 時，才會顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="342e2-130">This option is displayed only if **Metadata** is selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="342e2-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="342e2-131">See Also</span></span>  
 <span data-ttu-id="342e2-132">[Cube 設計工具 &#40;Analysis Services-多維度資料&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="342e2-132">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="342e2-133">[Kpi &#40;Cube 設計師&#41; &#40;Analysis Services-多維度資料&#41;](kpis-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="342e2-133">[KPIs &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](kpis-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="342e2-134">[工具列 &#40;Kpi] 索引標籤，Cube 設計師&#41; &#40;Analysis Services 多維度資料&#41;](toolbar-kpis-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="342e2-134">[Toolbar &#40;KPIs Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-kpis-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="342e2-135">[KPI 召集人 &#40;Kpi 索引標籤、Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](kpi-organizer-kpis-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="342e2-135">[KPI Organizer &#40;KPIs Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](kpi-organizer-kpis-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="342e2-136">[KPI 表單編輯器 &#40;Kpi 索引標籤、Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](kpi-form-editor-kpis-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="342e2-136">[KPI Form Editor &#40;KPIs Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](kpi-form-editor-kpis-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="342e2-137">KPI 瀏覽器 &#40;Kpi 索引標籤，Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="342e2-137">KPI Browser &#40;KPIs Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](kpi-browser-kpis-tab-cube-designer-analysis-services-multidimensional-data.md)  
  
  
