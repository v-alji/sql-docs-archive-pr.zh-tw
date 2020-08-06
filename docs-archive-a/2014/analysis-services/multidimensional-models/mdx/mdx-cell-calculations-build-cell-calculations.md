---
title: 在 mdx 中建立資料格計算 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- calculated cells [MDX]
- queries [MDX], cell calculations
- cells [MDX]
- MDX [Analysis Services], calculations
- calculation subcubes [MDX]
- calculated values [MDX]
- Multidimensional Expressions [Analysis Services], cell calculations
ms.assetid: 068aea63-d419-4791-a960-3d74e76f808e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9ab3219850c49c2ec16a12aab3ba7db67e9a8721
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703330"
---
# <a name="building-cell-calculations-in-mdx-mdx"></a><span data-ttu-id="668c6-102">在 MDX 中建立資料格計算 (MDX)</span><span class="sxs-lookup"><span data-stu-id="668c6-102">Building Cell Calculations in MDX (MDX)</span></span>
  <span data-ttu-id="668c6-103">多維度運算式 (MDX) 為您提供許多產生導出值的工具，如導出成員、自訂積存與自訂成員。</span><span class="sxs-lookup"><span data-stu-id="668c6-103">Multidimensional Expressions (MDX) provides you with a number of tools for generating calculated values, such as calculated members, custom rollups, and custom members.</span></span> <span data-ttu-id="668c6-104">但是，就此而言光使用這些功能，很難影響一組特定的資料格或單一個資料格。</span><span class="sxs-lookup"><span data-stu-id="668c6-104">However, using these features to affect a specific set of cells, or a single cell for that matter, would be difficult.</span></span>  
  
 <span data-ttu-id="668c6-105">若要特別為資料格產生導出值，就必須在 MDX 中使用導出資料格功能。</span><span class="sxs-lookup"><span data-stu-id="668c6-105">To generated calculated values for specifically for cells, you need to use the calculated cells feature in MDX.</span></span> <span data-ttu-id="668c6-106">導出資料格功能可讓您定義特定的資料格 Slice (稱為 *「計算 Subcube」*)，並對計算 Subcube 內的每個資料格套用公式，但要視每個資料格適用的選擇性條件而定。</span><span class="sxs-lookup"><span data-stu-id="668c6-106">Calculated cells let you define a specific slice of cells, called a *calculation subcube*, and apply a formula to each and every cell within the calculation subcube, subject to an optional condition that can be applied to each cell.</span></span>  
  
 <span data-ttu-id="668c6-107">導出資料格也能提供複雜的功能，例如 KPI 中使用的目標搜尋公式或推測性分析公式。</span><span class="sxs-lookup"><span data-stu-id="668c6-107">Calculated cells also offer complex functionality, such as goal-seeking formulas, as used in KPIs, or speculative analysis formulas.</span></span> <span data-ttu-id="668c6-108">此功能層級來自中的行程順序功能，允許以匯出資料 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 格建立遞迴傳遞，並在行程順序中的特定階段套用計算公式。</span><span class="sxs-lookup"><span data-stu-id="668c6-108">This level of functionality comes from the pass order feature in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] that allows recursive passes to be made with calculated cells, with calculation formulas applied at specific passes in the pass order.</span></span> <span data-ttu-id="668c6-109">如需行程順序的詳細資訊，請參閱[了解行程順序和求解順序 &#40;MDX&#41;](mdx-data-manipulation-understanding-pass-order-and-solve-order.md)。</span><span class="sxs-lookup"><span data-stu-id="668c6-109">For more information on pass order, see [Understanding Pass Order and Solve Order &#40;MDX&#41;](mdx-data-manipulation-understanding-pass-order-and-solve-order.md).</span></span>  
  
 <span data-ttu-id="668c6-110">就建立的範圍而言，導出資料格類似於其中的命名集與導出成員，可以做為 Cube 的一部份供全域使用，也可以在工作階段或單一查詢的存留期間暫時建立。</span><span class="sxs-lookup"><span data-stu-id="668c6-110">In terms of creation scope, calculated cells are similar to both named sets and calculated members in that calculated cells can be temporarily created for the lifetime of either a session or a single query, or made globally available as part of a cube:</span></span>  
  
-   <span data-ttu-id="668c6-111">**查詢範圍** ：若要建立一個導出資料格，把它定義為 MDX 查詢的一部份，而且範圍限制在查詢內，請使用 WITH 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="668c6-111">**Query-scoped** To create a calculated cell that is defined as part of an MDX query, and therefore whose scope is limited to the query, you use the WITH keyword.</span></span> <span data-ttu-id="668c6-112">然後您就可以在 MDX SELECT 陳述式內使用導出資料格。</span><span class="sxs-lookup"><span data-stu-id="668c6-112">You can then use the calculated cell within an MDX SELECT statement.</span></span> <span data-ttu-id="668c6-113">使用這種方式，可以變更利用 `WITH` 關鍵字建立的導出資料格，而不會影響到 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="668c6-113">Using this approach, the calculated cell created by using the `WITH` keyword can be changed without disturbing the SELECT statement.</span></span>  
  
     <span data-ttu-id="668c6-114">如需如何使用 WITH 關鍵字建立導出成員的詳細資訊，請參閱 [建立查詢範圍資料格計算 &#40;MDX&#41;](../../multidimensional-models-olap-logical-cube-objects/calculations.md)。</span><span class="sxs-lookup"><span data-stu-id="668c6-114">For more information about how to use the WITH keyword to create calculated members, see [Creating Query-Scoped Cell Calculations &#40;MDX&#41;](../../multidimensional-models-olap-logical-cube-objects/calculations.md).</span></span>  
  
-   <span data-ttu-id="668c6-115">**工作階段範圍** ：若要建立一個範圍超出查詢內容的導出成員，也就是說它的範圍是 MDX 工作階段的存留期間，您可以使用 CREATE CELL CALCULATION 或 ALTER CUBE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="668c6-115">**Session-scoped** To create a calculated member whose scope is wider than the context of the query, that is, whose scope is the lifetime of the MDX session, you use either the CREATE CELL CALCULATION or ALTER CUBE statement.</span></span>  
  
     <span data-ttu-id="668c6-116">如需如何使用 CREATE CELL CALCULATION 或 ALTER CUBE 陳述式建立工作階段中的導出資料格的詳細資訊，請參閱 [建立工作階段範圍導出資料格](mdx-cell-calculations-session-scoped-calculated-cells.md)</span><span class="sxs-lookup"><span data-stu-id="668c6-116">For more information about how to use either the CREATE CELL CALCULATION or ALTER CUBE statement to create calculated cells in a session, see [Creating Session-Scoped Calculated Cells](mdx-cell-calculations-session-scoped-calculated-cells.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="668c6-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="668c6-117">See Also</span></span>  
 <span data-ttu-id="668c6-118">[ALTER CUBE 語句 &#40;MDX&#41;](/sql/mdx/mdx-data-definition-alter-cube) </span><span class="sxs-lookup"><span data-stu-id="668c6-118">[ALTER CUBE Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-alter-cube) </span></span>  
 <span data-ttu-id="668c6-119">[建立 &#40;MDX&#41;的資料格計算語句](/sql/mdx/mdx-data-definition-create-cell-calculation) </span><span class="sxs-lookup"><span data-stu-id="668c6-119">[CREATE CELL CALCULATION Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-cell-calculation) </span></span>  
 <span data-ttu-id="668c6-120">[建立查詢範圍的資料格計算 &#40;MDX&#41;](../../multidimensional-models-olap-logical-cube-objects/calculations.md) </span><span class="sxs-lookup"><span data-stu-id="668c6-120">[Creating Query-Scoped Cell Calculations &#40;MDX&#41;](../../multidimensional-models-olap-logical-cube-objects/calculations.md) </span></span>  
 [<span data-ttu-id="668c6-121">MDX 查詢基礎觀念 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="668c6-121">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-query-fundamentals-analysis-services.md)  
  
  
