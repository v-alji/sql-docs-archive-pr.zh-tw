---
title: 在簡單的範例中使用查詢和交叉分析篩選器軸 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- slicer axis
- query axis [MDX]
ms.assetid: 85bcb26f-5971-4153-b334-61f8d8b475b5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 324f082fd6659592e56af65680bd4aa623c625d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598029"
---
# <a name="using-query-and-slicer-axes-in-a-simple-example-mdx"></a><span data-ttu-id="5c057-102">在簡單的範例中使用查詢及 Slicer 軸 (MDX)</span><span class="sxs-lookup"><span data-stu-id="5c057-102">Using Query and Slicer Axes in a Simple Example (MDX)</span></span>
  <span data-ttu-id="5c057-103">本主題中的簡單範例說明指定和使用查詢及 Slicer 軸的基本知識。</span><span class="sxs-lookup"><span data-stu-id="5c057-103">The simple example presented in this topic illustrates the basics of specifying and using query and slicer axes.</span></span>  
  
## <a name="the-cube"></a><span data-ttu-id="5c057-104">Cube</span><span class="sxs-lookup"><span data-stu-id="5c057-104">The Cube</span></span>  
 <span data-ttu-id="5c057-105">一個稱為 TestCube 的 Cube，有稱為 Route 與 Time 的兩個簡單維度。</span><span class="sxs-lookup"><span data-stu-id="5c057-105">A cube, named TestCube, has two simple dimensions named Route and Time.</span></span> <span data-ttu-id="5c057-106">每個維度都只有一個使用者階層，分別稱為 Route 與 Time。</span><span class="sxs-lookup"><span data-stu-id="5c057-106">Each dimension has only one user hierarchy, named Route and Time respectively.</span></span> <span data-ttu-id="5c057-107">因為 Cube 的量值是 Measures 維度的一部份，這個 Cube 總共有 3 個維度。</span><span class="sxs-lookup"><span data-stu-id="5c057-107">Because the measures of the cube are part of the Measures dimension, this cube has three dimensions in all.</span></span>  
  
## <a name="the-query"></a><span data-ttu-id="5c057-108">查詢</span><span class="sxs-lookup"><span data-stu-id="5c057-108">The Query</span></span>  
 <span data-ttu-id="5c057-109">查詢是要提供一個矩陣，在此矩陣中，Packages 量值可以在路徑與時間之間交叉比較。</span><span class="sxs-lookup"><span data-stu-id="5c057-109">The query is to provide a matrix in which the Packages measure can be compared across routes and times.</span></span>  
  
 <span data-ttu-id="5c057-110">在下列的 MDX 查詢範例中，Route 與 Time 階層是查詢座標軸，而 Measures 維度則是 Slicer 軸。</span><span class="sxs-lookup"><span data-stu-id="5c057-110">In the following MDX query example, the Route and Time hierarchies are the query axes, and the Measures dimension is the slicer axis.</span></span> <span data-ttu-id="5c057-111">[Members](/sql/mdx/members-set-mdx) 函數指出 MDX 將會使用階層或層級的成員建構集合。</span><span class="sxs-lookup"><span data-stu-id="5c057-111">The [Members](/sql/mdx/members-set-mdx) function indicates that MDX will use the members of the hierarchy or level to construct a set.</span></span> <span data-ttu-id="5c057-112">使用 `Members` 函數代表您不需要在 MDX 查詢中，明確地陳述特定階層或層級的每個成員。</span><span class="sxs-lookup"><span data-stu-id="5c057-112">The use of the `Members` function means that you do not have to explicitly state each member of a specific hierarchy or level in an MDX query.</span></span>  
  
```  
SELECT  
   { Route.nonground.Members } ON COLUMNS,  
   { Time.[1st half].Members } ON ROWS  
FROM TestCube  
WHERE ( [Measures].[Packages] )  
```  
  
## <a name="the-results"></a><span data-ttu-id="5c057-113">結果</span><span class="sxs-lookup"><span data-stu-id="5c057-113">The Results</span></span>  
 <span data-ttu-id="5c057-114">所得結果會是可識別 Packages 量值一值的方格，此量值位於 COLUMNS 與 ROWS 座標軸維度的每個交集處。</span><span class="sxs-lookup"><span data-stu-id="5c057-114">The result is a grid that identifies the value of the Packages measure at each intersection of the COLUMNS and ROWS axis dimensions.</span></span> <span data-ttu-id="5c057-115">下表顯示此方格內容：</span><span class="sxs-lookup"><span data-stu-id="5c057-115">The following table shows how this grid would look.</span></span>  
  
||<span data-ttu-id="5c057-116">air</span><span class="sxs-lookup"><span data-stu-id="5c057-116">air</span></span>|<span data-ttu-id="5c057-117">sea</span><span class="sxs-lookup"><span data-stu-id="5c057-117">sea</span></span>|  
|-|---------|---------|  
|<span data-ttu-id="5c057-118">1st quarter</span><span class="sxs-lookup"><span data-stu-id="5c057-118">1st quarter</span></span>|<span data-ttu-id="5c057-119">60</span><span class="sxs-lookup"><span data-stu-id="5c057-119">60</span></span>|<span data-ttu-id="5c057-120">50</span><span class="sxs-lookup"><span data-stu-id="5c057-120">50</span></span>|  
|<span data-ttu-id="5c057-121">2nd quarter</span><span class="sxs-lookup"><span data-stu-id="5c057-121">2nd quarter</span></span>|<span data-ttu-id="5c057-122">45</span><span class="sxs-lookup"><span data-stu-id="5c057-122">45</span></span>|<span data-ttu-id="5c057-123">45</span><span class="sxs-lookup"><span data-stu-id="5c057-123">45</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5c057-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c057-124">See Also</span></span>  
 <span data-ttu-id="5c057-125">[指定查詢座標軸的內容 &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md) </span><span class="sxs-lookup"><span data-stu-id="5c057-125">[Specifying the Contents of a Query Axis &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md) </span></span>  
 [<span data-ttu-id="5c057-126">指定 Slicer 軸的內容 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="5c057-126">Specifying the Contents of a Slicer Axis &#40;MDX&#41;</span></span>](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)  
  
  
