---
title: 流覽 Cube |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 3819946e-d3fa-4c1d-afe3-599c938b1b2e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7cbf35866bb0a1f65074a7e106ecf556e98aa30b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584764"
---
# <a name="browsing-the-cube"></a><span data-ttu-id="78bf6-102">瀏覽 Cube</span><span class="sxs-lookup"><span data-stu-id="78bf6-102">Browsing the Cube</span></span>
  <span data-ttu-id="78bf6-103">部署 Cube 之後，您就可以在 [Cube 設計師] 的 [瀏覽器]\*\*\*\* 索引標籤上檢視 Cube 資料，以及在 [維度設計師] 的 [瀏覽器]\*\*\*\* 索引標籤上檢視維度資料。</span><span class="sxs-lookup"><span data-stu-id="78bf6-103">After you deploy a cube, the cube data is viewable on the **Browser** tab in Cube Designer, and the dimension data is viewable on the **Browser** tab in Dimension Designer.</span></span> <span data-ttu-id="78bf6-104">瀏覽 Cube 和維度資料是累加地檢查工作的一種方式。</span><span class="sxs-lookup"><span data-stu-id="78bf6-104">Browsing cube and dimension data is way to check your work incrementally.</span></span> <span data-ttu-id="78bf6-105">您可以在物件經處理之後，驗證對屬性、關聯性和其他物件所做的細微變更是否達到期望的效果。</span><span class="sxs-lookup"><span data-stu-id="78bf6-105">You can verify that small changes to properties, relationships, and other objects have the desired effect once the object is processed.</span></span> <span data-ttu-id="78bf6-106">由於 [瀏覽器] 索引標籤用於檢視 Cube 和維度資料，因此該索引標籤會根據您要瀏覽的物件，提供不同的功能。</span><span class="sxs-lookup"><span data-stu-id="78bf6-106">While the Browser tab is used to view both cube and dimension data, the tab provides different capabilities based on the object you are browsing.</span></span>  
  
 <span data-ttu-id="78bf6-107">若是維度，[瀏覽器] 索引標籤會提供一種方式，以檢視成員或導覽一直到分葉節點的階層。</span><span class="sxs-lookup"><span data-stu-id="78bf6-107">For dimensions, the Browser tab provides a way to view members or navigate a hierarchy all the way down to the leaf node.</span></span> <span data-ttu-id="78bf6-108">假設您已經將翻譯加入至模型中，便可以不同語言瀏覽維度資料。</span><span class="sxs-lookup"><span data-stu-id="78bf6-108">You can browse dimension data in different languages, assuming you have added the translations to your model.</span></span>  
  
 <span data-ttu-id="78bf6-109">若是 Cube，[瀏覽器] 索引標籤則會提供兩種瀏覽資料的方法。</span><span class="sxs-lookup"><span data-stu-id="78bf6-109">For cubes, the Browser tab provides two approaches for exploring data.</span></span> <span data-ttu-id="78bf6-110">您可以使用內建的 MDX 查詢設計工具，建立從多維度資料庫傳回扁平化資料列集的查詢。</span><span class="sxs-lookup"><span data-stu-id="78bf6-110">You can use the built-in MDX Query Designer to build queries that return a flattened rowset from a multidimensional database.</span></span> <span data-ttu-id="78bf6-111">或者，您可以使用 Excel 捷徑。</span><span class="sxs-lookup"><span data-stu-id="78bf6-111">Alternatively, you can use an Excel shortcut.</span></span> <span data-ttu-id="78bf6-112">如果您從 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中啟動 Excel，當 Excel 開啟時，工作表中已經有一個樞紐分析表，以及一個連至模型工作空間資料庫之預先定義的連接。</span><span class="sxs-lookup"><span data-stu-id="78bf6-112">When you start Excel from within [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], Excel opens with a PivotTable already in the worksheet and a predefined connection to the model workspace database.</span></span>  
  
 <span data-ttu-id="78bf6-113">Excel 通常會提供一個比較好的瀏覽經驗，因為您可以透過互動方式瀏覽 Cube 資料，並使用水平和垂直軸分析資料中的關聯性。</span><span class="sxs-lookup"><span data-stu-id="78bf6-113">Excel generally offers a better browsing experience because you can explore cube data interactively, using horizontal and vertical axes to analyze the relationships in your data.</span></span> <span data-ttu-id="78bf6-114">相較之下，MDX 查詢設計工具限制為單一軸。</span><span class="sxs-lookup"><span data-stu-id="78bf6-114">In contrast, the MDX Query Designer is limited to a single axis.</span></span> <span data-ttu-id="78bf6-115">此外，由於資料列集經過扁平化，因此您不需要使用 Excel 樞紐分析表所提供的向下鑽研功能。</span><span class="sxs-lookup"><span data-stu-id="78bf6-115">Moreover, because the rowset is flattened, you do not get the drilldown that an Excel PivotTable provides.</span></span> <span data-ttu-id="78bf6-116">隨著您在 Cube 中加入更多維度和階層 (您將在後續的課程中進行)，Excel 將是瀏覽資料慣用的解決方案。</span><span class="sxs-lookup"><span data-stu-id="78bf6-116">As you add more dimensions and hierarchies to your cube, which you will do in subsequent lessons, Excel will be the preferred solution for browsing data.</span></span>  
  
### <a name="to-browse-the-deployed-cube"></a><span data-ttu-id="78bf6-117">瀏覽已部署的 Cube</span><span class="sxs-lookup"><span data-stu-id="78bf6-117">To browse the deployed cube</span></span>  
  
1.  <span data-ttu-id="78bf6-118">針對 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中的 [產品] 維度，切換至 [維度設計師]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="78bf6-118">Switch to **Dimension Designer** for the Product dimension in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="78bf6-119">若要這樣做，請在方案總管的 [維度]\*\*\*\* 節點中，按兩下 [產品]\*\*\*\* 維度。</span><span class="sxs-lookup"><span data-stu-id="78bf6-119">To do this, double-click the **Product** dimension in the **Dimensions** node of Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="78bf6-120">按一下 [**瀏覽器**] 索引標籤，顯示內容階層的 [**全部**] 成員 `Product Key` 。</span><span class="sxs-lookup"><span data-stu-id="78bf6-120">Click the **Browser** tab to display the **All** member of the `Product Key` attribute hierarchy.</span></span> <span data-ttu-id="78bf6-121">在第 3 課，您將定義 [產品] 維度的使用者階層，以便瀏覽此維度。</span><span class="sxs-lookup"><span data-stu-id="78bf6-121">In lesson three, you will define a user hierarchy for the Product dimension that will let you browse the dimension.</span></span>  
  
3.  <span data-ttu-id="78bf6-122">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中，切換至 [Cube 設計師]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="78bf6-122">Switch to **Cube Designer** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="78bf6-123">若要這麼做，請在方案總管的 [ **cube** ] 節點中，按兩下 [ **Analysis Services 教學**課程] cube。</span><span class="sxs-lookup"><span data-stu-id="78bf6-123">To do this, double-click the **Analysis Services Tutorial** cube in the **Cubes** node of Solution Explorer.</span></span>  
  
4.  <span data-ttu-id="78bf6-124">選取 [瀏覽器]\*\*\*\* 索引標籤，然後按一下設計師工具列上的重新連接\*\*\*\* 圖示。</span><span class="sxs-lookup"><span data-stu-id="78bf6-124">Select the **Browser** tab, and then click the **Reconnect** icon on the toolbar of the designer.</span></span>  
  
     <span data-ttu-id="78bf6-125">設計師的左窗格會顯示 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube 中的物件。</span><span class="sxs-lookup"><span data-stu-id="78bf6-125">The left pane of the designer shows the objects in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span> <span data-ttu-id="78bf6-126">[瀏覽器]\*\*\*\* 索引標籤的右側具有兩個窗格：上面的窗格是 [篩選]\*\*\*\* 窗格，而下面的窗格是 [資料]\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="78bf6-126">On the right side of the **Browser** tab, there are two panes: the upper pane is the **Filter** pane, and the lower pane is the **Data** pane.</span></span> <span data-ttu-id="78bf6-127">在後續課程中，您將使用 Cube 瀏覽器來進行分析。</span><span class="sxs-lookup"><span data-stu-id="78bf6-127">In an upcoming lesson, you will use the cube browser to do analysis.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="78bf6-128">下一課</span><span class="sxs-lookup"><span data-stu-id="78bf6-128">Next Lesson</span></span>  
 [<span data-ttu-id="78bf6-129">第3課：修改量值、屬性和階層</span><span class="sxs-lookup"><span data-stu-id="78bf6-129">Lesson 3: Modifying Measures, Attributes and Hierarchies</span></span>](lesson-3-modifying-measures-attributes-and-hierarchies.md)  
  
## <a name="see-also"></a><span data-ttu-id="78bf6-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78bf6-130">See Also</span></span>  
 [<span data-ttu-id="78bf6-131">MDX 查詢編輯器 &#40;Analysis Services - 多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="78bf6-131">MDX Query Editor &#40;Analysis Services - Multidimensional Data&#41;</span></span>](mdx-query-editor-analysis-services-multidimensional-data.md)  
  
  
