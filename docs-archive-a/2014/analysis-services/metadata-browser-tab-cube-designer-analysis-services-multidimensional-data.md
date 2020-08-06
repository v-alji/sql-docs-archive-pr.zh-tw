---
title: 中繼資料 (瀏覽器索引標籤、Cube 設計工具)  (Analysis Services 多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.browsecube.metadatapane.f1
ms.assetid: a1ace545-488d-4645-8330-56408a5e8abd
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8093ac8cac8e3cd5a609e97b47ede89912897e8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707961"
---
# <a name="metadata-browser-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="b68bb-102">中繼資料 (瀏覽器索引標籤，Cube 設計師) (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="b68bb-102">Metadata (Browser Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="b68bb-103">使用 Cube 設計師中之 [瀏覽器]\*\*\*\* 索引標籤的 [中繼資料]\*\*\*\* 窗格瀏覽 Cube 的結構，以查看相關的量值，並檢視與建立維度。</span><span class="sxs-lookup"><span data-stu-id="b68bb-103">Use the **Metadata** pane on the **Browser** tab in Cube Designer to browse the structure of the cube, to see related measures, and to view and create dimensions.</span></span> <span data-ttu-id="b68bb-104">您可以向下鑽研階層、檢視可用量值與 KPI 的清單，以及複製物件的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="b68bb-104">You can drill down into hierarchies, view a list of available measures and KPIs, and copy the fully qualified names of objects.</span></span>  
  
 <span data-ttu-id="b68bb-105">您也可以將 [中繼資料]\*\*\*\* 窗格中的物件和階層拖曳到查詢建立區域，以建立新查詢或匯出可在 Excel 中瀏覽的資料。</span><span class="sxs-lookup"><span data-stu-id="b68bb-105">You can also drag the objects and hierarchies in the **Metadata** pane to the query building area, to create new queries or export data for browsing in Excel.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b68bb-106">選項</span><span class="sxs-lookup"><span data-stu-id="b68bb-106">Options</span></span>  
 <span data-ttu-id="b68bb-107">**中繼資料**</span><span class="sxs-lookup"><span data-stu-id="b68bb-107">**Metadata**</span></span>  
 <span data-ttu-id="b68bb-108">顯示目前檢視中可用的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="b68bb-108">Displays the metadata available in the current view.</span></span> <span data-ttu-id="b68bb-109">您可以按一下 Cube 圖示，然後使用 [選取 Cube]\*\*\*\* 對話方塊選擇一個新的 Cube 或檢視方塊，藉以變更檢視 (亦即目前選取的檢視方塊或 Cube)。</span><span class="sxs-lookup"><span data-stu-id="b68bb-109">You can change the view (that is, the currently selected perspective or cube) by clicking the cube icon, and then using the **Cube Selection** dialog box to choose a new cube or perspective.</span></span> <span data-ttu-id="b68bb-110">您也可以按一下 [量值群組]\*\*\*\*，然後從下拉式清單中選取一個新的量值群組，以篩選 [中繼資料]\*\*\*\* 窗格中提供的物件。</span><span class="sxs-lookup"><span data-stu-id="b68bb-110">You can also click **Measure Group**, and select a new measure group from the dropdown list to filter the objects that are available in the **Metadata** pane.</span></span>  
  
 <span data-ttu-id="b68bb-111">將選取的項目拖曳至在 [報表]\*\*\*\* 窗格中之 [!INCLUDE[msCoName](../includes/msconame-md.md)] Office 11.0 樞紐分析表控制項的篩選、資料、資料列或資料行區域，即可顯示選取之項目的資料。</span><span class="sxs-lookup"><span data-stu-id="b68bb-111">Drag selected items to the filter, data, row, or column areas of the [!INCLUDE[msCoName](../includes/msconame-md.md)] Office 11.0 PivotTable control in the **Report** pane to display the data for the selected item.</span></span>  
  
 <span data-ttu-id="b68bb-112">**函式**</span><span class="sxs-lookup"><span data-stu-id="b68bb-112">**Functions**</span></span>  
 <span data-ttu-id="b68bb-113">在 [瀏覽器]\*\*\*\* 中顯示可用來建立查詢或資料檢視之所有函數、運算子和常數的清單。</span><span class="sxs-lookup"><span data-stu-id="b68bb-113">Displays a list of all functions, operators, and constants that can be used to create queries or data views in the **Browser**.</span></span> <span data-ttu-id="b68bb-114">若要使用函數，請找出您要的函數，然後將其拖曳到查詢區域中。</span><span class="sxs-lookup"><span data-stu-id="b68bb-114">To use a function, locate the one you want, and drag it into the query area.</span></span> <span data-ttu-id="b68bb-115">語法定義便會加入至文字中</span><span class="sxs-lookup"><span data-stu-id="b68bb-115">The syntax definition is added to the text</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="b68bb-116">當您在圖形設計檢視中作業時，無法使用 [函數]\*\*\*\* 清單。</span><span class="sxs-lookup"><span data-stu-id="b68bb-116">The **Function** list is not available when you are working in graphical design view.</span></span>  
  
 <span data-ttu-id="b68bb-117">當使用表格式模型時，函數清單包含 MDX 函數和 DAX 函數。</span><span class="sxs-lookup"><span data-stu-id="b68bb-117">When working with a tabular model, the list of functions includes both MDX functions and DAX functions.</span></span> <span data-ttu-id="b68bb-118">否則，該清單只包含 MDX。</span><span class="sxs-lookup"><span data-stu-id="b68bb-118">Otherwise, the list includes only MDX.</span></span> <span data-ttu-id="b68bb-119">即使 DAX 運算式可能是物件定義的一部分，多維度模型也無法直接使用 DAX 函數。</span><span class="sxs-lookup"><span data-stu-id="b68bb-119">A multidimensional model cannot use DAX functions directly, although a DAX expression might be included as part of an object definition.</span></span>  
  
 <span data-ttu-id="b68bb-120">提示：包含 DAX 函數的資料夾會以全部大寫字母列出。</span><span class="sxs-lookup"><span data-stu-id="b68bb-120">Tip: The folders that contain DAX functions are listed in all upper-case letters.</span></span> <span data-ttu-id="b68bb-121">其他所有資料夾則包含 MDX 函數。</span><span class="sxs-lookup"><span data-stu-id="b68bb-121">All other folders contain MDX functions.</span></span> <span data-ttu-id="b68bb-122">例如，有兩個統計函數的資料夾： **STATISTICAL** 包含相關的 DAX 函數。</span><span class="sxs-lookup"><span data-stu-id="b68bb-122">For example, there are two folders for statistical functions: **STATISTICAL** contains the related DAX functions.</span></span>  
  
## <a name="context-menu"></a><span data-ttu-id="b68bb-123">操作功能表</span><span class="sxs-lookup"><span data-stu-id="b68bb-123">Context Menu</span></span>  
 <span data-ttu-id="b68bb-124">以滑鼠右鍵按一下 [中繼資料]\*\*\*\* 窗格所顯示的元素，即可顯示提供下列選項的操作功能表：</span><span class="sxs-lookup"><span data-stu-id="b68bb-124">The following options are available in the context menu displayed by right-clicking an element displayed in the **Metadata** pane:</span></span>  
  
|<span data-ttu-id="b68bb-125">選項</span><span class="sxs-lookup"><span data-stu-id="b68bb-125">Option</span></span>|<span data-ttu-id="b68bb-126">描述</span><span class="sxs-lookup"><span data-stu-id="b68bb-126">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b68bb-127">**加入至查詢**</span><span class="sxs-lookup"><span data-stu-id="b68bb-127">**Add to Query**</span></span>|<span data-ttu-id="b68bb-128">按一下可將選取的物件加入至查詢建立區域的下方窗格中。</span><span class="sxs-lookup"><span data-stu-id="b68bb-128">Click to add the selected object to the lower pane of the query building area.</span></span>|  
|<span data-ttu-id="b68bb-129">**加入至篩選**</span><span class="sxs-lookup"><span data-stu-id="b68bb-129">**Add to Filter**</span></span>|<span data-ttu-id="b68bb-130">按一下可將選取的維度、屬性、階層或層級加入 [瀏覽器]\*\*\*\* 的篩選區域。</span><span class="sxs-lookup"><span data-stu-id="b68bb-130">Click to add the selected dimension, attribute, hierarchy, or level to the filter area of the **Browser**.</span></span><br /><br /> <span data-ttu-id="b68bb-131">注意：只有選取維度、屬性、階層或層級時，才會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="b68bb-131">Note: This option is enabled only if a dimension, attribute, hierarchy, or level is selected.</span></span>|  
|<span data-ttu-id="b68bb-132">**複製**</span><span class="sxs-lookup"><span data-stu-id="b68bb-132">**Copy**</span></span>|<span data-ttu-id="b68bb-133">按一下即可將選取的項目加入至剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="b68bb-133">Click to add the selected item to the Clipboard.</span></span><br /><br /> <span data-ttu-id="b68bb-134">注意：此選項會複製物件的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="b68bb-134">Note: This option copies the fully qualified name of the object.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b68bb-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b68bb-135">See Also</span></span>  
 <span data-ttu-id="b68bb-136">[工具列 &#40;瀏覽器索引標籤、Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="b68bb-136">[Toolbar &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="b68bb-137">[[在 Excel 中進行分析] &#40;瀏覽器索引標籤、Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](analyze-in-excel-browser-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="b68bb-137">[Analyze in Excel &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](analyze-in-excel-browser-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="b68bb-138">[查詢和篩選 &#40;瀏覽器索引標籤、Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](query-filter-browser-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="b68bb-138">[Query and Filter &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](query-filter-browser-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="b68bb-139">瀏覽器 &#40;Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="b68bb-139">Browser &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](browser-cube-designer-analysis-services-multidimensional-data.md)  
  
  
