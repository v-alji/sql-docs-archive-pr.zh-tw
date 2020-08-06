---
title: Cube 資料格 (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- storing data [Analysis Services], cells
- hierarchies [Analysis Services], cells
- OLAP objects [Analysis Services], cells
- data members [Analysis Services]
- cubes [Analysis Services], cells
- empty cells [Analysis Services]
- nonleaf members
- cubes [Analysis Services], examples
- storage [Analysis Services], cells
- nonleaf cells
- calculated cells [Analysis Services]
- dimensions [Analysis Services], cells
- cells [Analysis Services]
- leaf members
- leaf cells
ms.assetid: 9945773c-a43b-40d4-91cf-3d2ebc90bca5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0b55e940f75319a965fb1441520a7e16ce7ab2f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592321"
---
# <a name="cube-cells-analysis-services---multidimensional-data"></a><span data-ttu-id="69d34-102">Cube 資料格 (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="69d34-102">Cube Cells (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="69d34-103">Cube 是由資料格所組成，而依據量值群組和維度來進行組織。</span><span class="sxs-lookup"><span data-stu-id="69d34-103">A cube is composed of cells, organized by measure groups and dimensions.</span></span> <span data-ttu-id="69d34-104">資料格代表 Cube 內每個維度之某個成員於 Cube 內的唯一邏輯交集。</span><span class="sxs-lookup"><span data-stu-id="69d34-104">A cell represents the unique logical intersection in a cube of one member from every dimension in the cube.</span></span> <span data-ttu-id="69d34-105">例如，下圖所描述的 Cube 包含一個具有兩個量值的量值群組，並依 Source、Route 和 Time 這三個維度來進行組織。</span><span class="sxs-lookup"><span data-stu-id="69d34-105">For example, the cube described by the following diagram contains one measure group that has two measures, organized along three dimensions named Source, Route, and Time.</span></span>  
  
 <span data-ttu-id="69d34-106">![識別單一資料格的 Cube 圖表](../../analysis-services/dev-guide/media/as-cubeintro5.gif "識別單一資料格的 Cube 圖表")</span><span class="sxs-lookup"><span data-stu-id="69d34-106">![Cube diagram identifying a single cell](../../analysis-services/dev-guide/media/as-cubeintro5.gif "Cube diagram identifying a single cell")</span></span>  
  
 <span data-ttu-id="69d34-107">在這個圖表中具有陰影的單一資料格是下列成員的交集：</span><span class="sxs-lookup"><span data-stu-id="69d34-107">The single shaded cell in this diagram is the intersection of the following members:</span></span>  
  
-   <span data-ttu-id="69d34-108">Route 維度的 air 成員。</span><span class="sxs-lookup"><span data-stu-id="69d34-108">The air member of the Route dimension.</span></span>  
  
-   <span data-ttu-id="69d34-109">Source 維度的 Africa 成員。</span><span class="sxs-lookup"><span data-stu-id="69d34-109">The Africa member of the Source dimension.</span></span>  
  
-   <span data-ttu-id="69d34-110">Time 維度的 4th quarter 成員。</span><span class="sxs-lookup"><span data-stu-id="69d34-110">The 4th quarter member of the Time dimension.</span></span>  
  
-   <span data-ttu-id="69d34-111">封裝量值。</span><span class="sxs-lookup"><span data-stu-id="69d34-111">The Packages measure.</span></span>  
  
## <a name="leaf-and-nonleaf-cells"></a><span data-ttu-id="69d34-112">分葉資料格與非分葉資料格</span><span class="sxs-lookup"><span data-stu-id="69d34-112">Leaf and Nonleaf Cells</span></span>  
 <span data-ttu-id="69d34-113">Cube 中資料格的值可以使用下列方式之一取得。</span><span class="sxs-lookup"><span data-stu-id="69d34-113">The value for a cell in a cube can be obtained in one of several ways.</span></span> <span data-ttu-id="69d34-114">在上述範例中，您可以從 cube 的事實資料表直接抓取資料格中的值，因為用來識別該儲存格的所有成員都是分*葉成員*。</span><span class="sxs-lookup"><span data-stu-id="69d34-114">In the previous example, the value in the cell can be directly retrieved from the fact table of the cube, because all the members used to identify that cell are *leaf members*.</span></span> <span data-ttu-id="69d34-115">依階層而言，分葉成員沒有子成員，而且通常會參考維度資料表中的單一記錄。</span><span class="sxs-lookup"><span data-stu-id="69d34-115">A leaf member has no child members, hierarchically speaking, and typically references a single record in a dimension table.</span></span> <span data-ttu-id="69d34-116">這種資料格稱為分*葉資料格*。</span><span class="sxs-lookup"><span data-stu-id="69d34-116">This kind of cell is referred to as a *leaf cell*.</span></span>  
  
 <span data-ttu-id="69d34-117">不過，也可以使用*非分葉成員*來識別資料格。</span><span class="sxs-lookup"><span data-stu-id="69d34-117">However, a cell can also be identified by using *nonleaf members*.</span></span> <span data-ttu-id="69d34-118">非分葉成員是擁有一或多個子成員的成員。</span><span class="sxs-lookup"><span data-stu-id="69d34-118">A nonleaf member is a member that has one or more child members.</span></span> <span data-ttu-id="69d34-119">在此狀況下，資料格的值通常是從與非分葉成員相關聯之子成員的彙總衍生。</span><span class="sxs-lookup"><span data-stu-id="69d34-119">In this case, the value of the cell is typically derived from the aggregation of child members associated with the nonleaf member.</span></span> <span data-ttu-id="69d34-120">例如，以下成員與維度的交叉點引用由彙總提供數值的資料格：</span><span class="sxs-lookup"><span data-stu-id="69d34-120">For example, the intersection of the following members and dimensions refers to a cell whose value is supplied by aggregation:</span></span>  
  
-   <span data-ttu-id="69d34-121">Route 維度的 air 成員。</span><span class="sxs-lookup"><span data-stu-id="69d34-121">The air member of the Route dimension.</span></span>  
  
-   <span data-ttu-id="69d34-122">Source 維度的 Africa 成員。</span><span class="sxs-lookup"><span data-stu-id="69d34-122">The Africa member of the Source dimension.</span></span>  
  
-   <span data-ttu-id="69d34-123">Time 維度的 2nd half 成員。</span><span class="sxs-lookup"><span data-stu-id="69d34-123">The 2nd half member of the Time dimension.</span></span>  
  
-   <span data-ttu-id="69d34-124">封裝成員。</span><span class="sxs-lookup"><span data-stu-id="69d34-124">The Packages member.</span></span>  
  
 <span data-ttu-id="69d34-125">Time 維度的 2nd half 成員就是非分葉成員。</span><span class="sxs-lookup"><span data-stu-id="69d34-125">The 2nd half member of the Time dimension is a nonleaf member.</span></span> <span data-ttu-id="69d34-126">因此，與它相關的所有值都必須是彙總值，如下列圖表所示。</span><span class="sxs-lookup"><span data-stu-id="69d34-126">Therefore, all of values associated with it must be aggregated values, as shown in the following diagram.</span></span>  
  
 <span data-ttu-id="69d34-127">![下半年成員的第三季和第四季資料格](../../analysis-services/dev-guide/media/as-cubeintro6.gif "下半年成員的第三季和第四季資料格")</span><span class="sxs-lookup"><span data-stu-id="69d34-127">![3rd and 4th quarter cells for 2nd half member](../../analysis-services/dev-guide/media/as-cubeintro6.gif "3rd and 4th quarter cells for 2nd half member")</span></span>  
  
 <span data-ttu-id="69d34-128">假設 3rd quarter 和 4th quarter 成員的彙總就是總和，則所指定資料格的值就是 400，而這個值是上圖中所有具有陰影之分葉資料格的總和。</span><span class="sxs-lookup"><span data-stu-id="69d34-128">Assuming the aggregations for the 3rd quarter and 4th quarter members are summations, the value of the specified cell is 400, which is the total of all of the leaf cells shaded in the previous diagram.</span></span> <span data-ttu-id="69d34-129">因為資料格的值是衍生自其他資料格的匯總，所以指定的儲存格會被視為*非分葉資料格*。</span><span class="sxs-lookup"><span data-stu-id="69d34-129">Because the value of the cell is derived from the aggregation of other cells, the specified cell is considered a *nonleaf cell*.</span></span>  
  
 <span data-ttu-id="69d34-130">針對使用自訂積存的成員和成員群組所衍生的資料格值以及自訂成員，都是以類似的方式處理。</span><span class="sxs-lookup"><span data-stu-id="69d34-130">The cell values derived for members that use custom rollups and member groups, in addition to custom members, are handled similarly.</span></span> <span data-ttu-id="69d34-131">然而，針對導出成員所衍生的資料格值完全是以用來定義導出成員的多維度運算式 (MDX) 運算式為基礎；在某些情況下，可能並未包含任何實際的資料格資料。</span><span class="sxs-lookup"><span data-stu-id="69d34-131">However, cell values derived for calculated members are based completely on the Multidimensional Expressions (MDX) expression used to define the calculated member; in some cases, there may be no actual cell data involved.</span></span> <span data-ttu-id="69d34-132">如需詳細資訊，請參閱[父子式維度中的自訂匯總運算子](../multidimensional-models/parent-child-dimension-attributes-custom-rollup-operators.md)、[定義自訂成員公式](../multidimensional-models/attribute-properties-define-custom-member-formulas.md)和[計算](../multidimensional-models-olap-logical-cube-objects/calculations.md)。</span><span class="sxs-lookup"><span data-stu-id="69d34-132">For more information, see [Custom Rollup Operators in Parent-Child Dimensions](../multidimensional-models/parent-child-dimension-attributes-custom-rollup-operators.md), [Define Custom Member Formulas](../multidimensional-models/attribute-properties-define-custom-member-formulas.md), and [Calculations](../multidimensional-models-olap-logical-cube-objects/calculations.md).</span></span>  
  
## <a name="empty-cells"></a><span data-ttu-id="69d34-133">空資料格</span><span class="sxs-lookup"><span data-stu-id="69d34-133">Empty Cells</span></span>  
 <span data-ttu-id="69d34-134">並非 Cube 中的每個資料格都需要包含值；Cube 中可以有不具任何資料的交集。</span><span class="sxs-lookup"><span data-stu-id="69d34-134">It is not required that every cell in a cube contain a value; there can be intersections in a cube that have no data.</span></span> <span data-ttu-id="69d34-135">因為並非在 Cube 中具有量值之維度屬性的每一個交集在事實資料表中都包含對應的記錄，所以這些交集 (稱為空資料格) 會經常出現在 Cube 中。</span><span class="sxs-lookup"><span data-stu-id="69d34-135">These intersections, called empty cells, frequently occur in cubes because not every intersection of a dimension attribute with a measure within a cube contains a corresponding record in a fact table.</span></span> <span data-ttu-id="69d34-136">Cube 中的空白資料格與 cube 中的資料格總數的比率，通常稱為 cube 的*稀疏性*。</span><span class="sxs-lookup"><span data-stu-id="69d34-136">The ratio of empty cells in a cube to the total number of cells in a cube is frequently referred to as the *sparsity* of a cube.</span></span>  
  
 <span data-ttu-id="69d34-137">例如，下列圖表顯示之 Cube 的結構與本主題中的其他範例類似。</span><span class="sxs-lookup"><span data-stu-id="69d34-137">For example, the structure of the cube shown in the following diagram is similar to other examples in this topic.</span></span> <span data-ttu-id="69d34-138">但在本範例中，第三季沒有空運往非洲的貨物，第四季沒有空運往澳洲的貨物。</span><span class="sxs-lookup"><span data-stu-id="69d34-138">However, in this example, there were no air shipments to Africa for the third quarter or to Australia for the fourth quarter.</span></span> <span data-ttu-id="69d34-139">事實資料表中沒有資料可支援那些維度和量值的交集；因此，那些交集的資料格會是空的。</span><span class="sxs-lookup"><span data-stu-id="69d34-139">There is no data in the fact table to support the intersections of those dimensions and measures; therefore the cells at those intersections are empty.</span></span>  
  
 <span data-ttu-id="69d34-140">![識別空白資料格的 Cube 圖表](../../analysis-services/dev-guide/media/as-cubeintro7.gif "識別空白資料格的 Cube 圖表")</span><span class="sxs-lookup"><span data-stu-id="69d34-140">![Cube diagram identifying empty cells](../../analysis-services/dev-guide/media/as-cubeintro7.gif "Cube diagram identifying empty cells")</span></span>  
  
 <span data-ttu-id="69d34-141">在中 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，空的資料格是具有特殊品質的資料格。</span><span class="sxs-lookup"><span data-stu-id="69d34-141">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], an empty cell is a cell that has special qualities.</span></span> <span data-ttu-id="69d34-142">因為空資料格會扭曲交叉聯結、計數等的結果，所以許多 MDX 函數會針對計算用途提供忽略空資料格的能力。</span><span class="sxs-lookup"><span data-stu-id="69d34-142">Because empty cells can skew the results of crossjoins, counts, and so on, many MDX functions supply the ability to ignore empty cells for the purposes of calculation.</span></span> <span data-ttu-id="69d34-143">如需詳細資訊，請參閱多[維度運算式 &#40;mdx&#41; 參考](/sql/mdx/multidimensional-expressions-mdx-reference)和[mdx &#40;Analysis Services&#41;中的重要概念](../multidimensional-models/key-concepts-in-mdx-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="69d34-143">For more information, see [Multidimensional Expressions &#40;MDX&#41; Reference](/sql/mdx/multidimensional-expressions-mdx-reference), and [Key Concepts in MDX &#40;Analysis Services&#41;](../multidimensional-models/key-concepts-in-mdx-analysis-services.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="69d34-144">安全性</span><span class="sxs-lookup"><span data-stu-id="69d34-144">Security</span></span>  
 <span data-ttu-id="69d34-145">資料格資料的存取是在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的角色層級中進行管理，且可使用 MDX 運算式進行細微的控制。</span><span class="sxs-lookup"><span data-stu-id="69d34-145">Access to cell data is managed in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] at the role level, and can be finely controlled by using MDX expressions.</span></span> <span data-ttu-id="69d34-146">如需詳細資訊，請參閱[將維度資料的自訂存取權授與 &#40;Analysis Services&#41;](../multidimensional-models/grant-custom-access-to-dimension-data-analysis-services.md)，並[將自訂存取權授與 &#40;Analysis Services&#41;的資料格資料](../multidimensional-models/grant-custom-access-to-cell-data-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="69d34-146">For more information, see [Grant custom access to dimension data &#40;Analysis Services&#41;](../multidimensional-models/grant-custom-access-to-dimension-data-analysis-services.md), and [Grant custom access to cell data &#40;Analysis Services&#41;](../multidimensional-models/grant-custom-access-to-cell-data-analysis-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69d34-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69d34-147">See Also</span></span>  
 <span data-ttu-id="69d34-148">[Cube 儲存體 &#40;Analysis Services-多維度資料&#41;](../multidimensional-models-olap-logical-cube-objects/cube-storage-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="69d34-148">[Cube Storage &#40;Analysis Services - Multidimensional Data&#41;](../multidimensional-models-olap-logical-cube-objects/cube-storage-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="69d34-149">彙總和彙總設計</span><span class="sxs-lookup"><span data-stu-id="69d34-149">Aggregations and Aggregation Designs</span></span>](../multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)  
  
  
