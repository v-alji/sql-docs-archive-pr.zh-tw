---
title: Cube 結構 (Cube 設計師)  (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.cubebuilderview.f1
ms.assetid: 00f0b605-5352-4b42-84f5-bd6c3e42d3d1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 857dd87c1d638a29adfa11c7de5a4d9f2d006314
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598688"
---
# <a name="cube-structure-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="3ac9e-102">Cube 結構 (Cube 設計師) (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="3ac9e-102">Cube Structure (Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="3ac9e-103">在 **中，請使用** [Cube 設計師] **的** [Cube 結構] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 索引標籤，即可建立和修改量值群組和量值、加入 Cube 維度，以及顯示相關聯資料來源檢視之 Cube 中所包含的物件。</span><span class="sxs-lookup"><span data-stu-id="3ac9e-103">Use the **Cube Structure** tab in **Cube Designer** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to create and modify measure groups and measures, add cube dimensions, and display the objects included in the cube from the associated data source view.</span></span>  
  
 <span data-ttu-id="3ac9e-104">**[Cube 結構]** 索引標籤包含下列窗格：</span><span class="sxs-lookup"><span data-stu-id="3ac9e-104">The **Cube Structure** tab contains the following panes:</span></span>  
  
## <a name="panes"></a><span data-ttu-id="3ac9e-105">窗格</span><span class="sxs-lookup"><span data-stu-id="3ac9e-105">Panes</span></span>  
  
|<span data-ttu-id="3ac9e-106">窗格</span><span class="sxs-lookup"><span data-stu-id="3ac9e-106">Pane</span></span>|<span data-ttu-id="3ac9e-107">定義</span><span class="sxs-lookup"><span data-stu-id="3ac9e-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="3ac9e-108">**工具列**</span><span class="sxs-lookup"><span data-stu-id="3ac9e-108">**Toolbar**</span></span>|<span data-ttu-id="3ac9e-109">使用工具列來執行此索引標籤中的一般動作。如需這個窗格的詳細資訊，請參閱[工具列 &#40;Cube 結構索引標籤、Cube 設計師&#41; &#40;Analysis Services 多維度資料&#41;](toolbar-cube-structure-cube-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="3ac9e-109">Use the toolbar to perform common actions in this tab. For more information about this pane, see [Toolbar &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-cube-structure-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="3ac9e-110">**評估**</span><span class="sxs-lookup"><span data-stu-id="3ac9e-110">**Measures**</span></span>|<span data-ttu-id="3ac9e-111">使用 **[量值]** 窗格即可建立和修改所選取 Cube 的量值群組和量值。</span><span class="sxs-lookup"><span data-stu-id="3ac9e-111">Use the **Measures** pane to create and modify measure groups and measures for the selected cube.</span></span> <span data-ttu-id="3ac9e-112">如需此窗格的詳細資訊，請參閱 [Measures &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](measures-cube-structure-cube-designer-analysis-services-multidimensional-data.md) (量值 ([Cube 結構] 索引標籤，Cube 設計師) (Analysis Services - 多維度資料))。</span><span class="sxs-lookup"><span data-stu-id="3ac9e-112">For more information about this pane, see [Measures &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](measures-cube-structure-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="3ac9e-113">**維度**</span><span class="sxs-lookup"><span data-stu-id="3ac9e-113">**Dimensions**</span></span>|<span data-ttu-id="3ac9e-114">使用 **[維度]** 窗格即可包含和修改所選取 Cube 的 Cube 維度。</span><span class="sxs-lookup"><span data-stu-id="3ac9e-114">Use the **Dimensions** pane to include and modify cube dimensions for the selected cube.</span></span> <span data-ttu-id="3ac9e-115">如需此窗格的詳細資訊，請參閱 [Dimensions &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](dimensions-cube-structure-cube-designer-analysis-services-multidimensional-data.md) (維度 ([Cube 結構] 索引標籤，Cube 設計師) (Analysis Services - 多維度資料))。</span><span class="sxs-lookup"><span data-stu-id="3ac9e-115">For more information about this pane, see [Dimensions &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](dimensions-cube-structure-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="3ac9e-116">**[資料來源檢視]**</span><span class="sxs-lookup"><span data-stu-id="3ac9e-116">**Data Source View**</span></span>|<span data-ttu-id="3ac9e-117">使用 **[資料來源檢視]** 窗格即可檢視和編輯與所選取 Cube 相關聯的資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="3ac9e-117">Use the **Data Source View** pane to view and edit the data source view associated with the selected cube.</span></span> <span data-ttu-id="3ac9e-118">如需此窗格的詳細資訊，請參閱 [Data Source View &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](data-source-view-cube-designer-analysis-services-multidimensional-data.md) (資料來源檢視 ([Cube 結構] 索引標籤，Cube 設計師) (Analysis Services - 多維度資料))。</span><span class="sxs-lookup"><span data-stu-id="3ac9e-118">For more information about this pane, see [Data Source View &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](data-source-view-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3ac9e-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ac9e-119">See Also</span></span>  
 <span data-ttu-id="3ac9e-120">[邏輯架構 &#40;Analysis Services-多維度資料&#41;](multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="3ac9e-120">[Logical Architecture &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md) </span></span>  
 <span data-ttu-id="3ac9e-121">[多維度模型中的 cube](multidimensional-models/cubes-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="3ac9e-121">[Cubes in Multidimensional Models](multidimensional-models/cubes-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="3ac9e-122">[設定量值屬性](multidimensional-models/configure-measure-properties.md) </span><span class="sxs-lookup"><span data-stu-id="3ac9e-122">[Configure Measure Properties](multidimensional-models/configure-measure-properties.md) </span></span>  
 <span data-ttu-id="3ac9e-123">[維度 &#40;Analysis Services 多維資料&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="3ac9e-123">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="3ac9e-124">[多維度模型中的資料來源視圖](multidimensional-models/data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="3ac9e-124">[Data Source Views in Multidimensional Models](multidimensional-models/data-source-views-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="3ac9e-125">Cube 設計工具 &#40;Analysis Services-多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="3ac9e-125">Cube Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](cube-designer-analysis-services-multidimensional-data.md)  
  
  
