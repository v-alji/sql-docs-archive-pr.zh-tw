---
title: MDX 查詢基本概念 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- statements [MDX]
- Multidimensional Expressions [Analysis Services], statements
- Multidimensional Expressions [Analysis Services], queries
- MDX [Analysis Services], statements
- MDX queries [Analysis Services]
- MDX [Analysis Services], queries
- queries [MDX]
ms.assetid: a560383b-bb58-472e-95f5-65d03d8ea08b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1a2a9a4f564bc33cc7a1b41a1a4c766c7a76a2cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598616"
---
# <a name="mdx-query-fundamentals-analysis-services"></a><span data-ttu-id="7fad7-102">MDX 查詢基礎觀念 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="7fad7-102">MDX Query Fundamentals (Analysis Services)</span></span>
  <span data-ttu-id="7fad7-103">您可以使用多維度運算式 (MDX) 查詢多維度物件 (例如 Cube)，然後傳回包含 Cube 資料的多維度資料格集。</span><span class="sxs-lookup"><span data-stu-id="7fad7-103">Multidimensional Expressions (MDX) lets you query multidimensional objects, such as cubes, and return multidimensional cellsets that contain the cube's data.</span></span> <span data-ttu-id="7fad7-104">這個主題以及子主題將提供對 MDX 查詢的概觀。</span><span class="sxs-lookup"><span data-stu-id="7fad7-104">This topic and its subtopics provide an overview of MDX queries.</span></span>  
  
 <span data-ttu-id="7fad7-105">以下主題描述 MDX 查詢與其產生的資料格集，並提供有關基本 MDX 語法更詳細的資訊。</span><span class="sxs-lookup"><span data-stu-id="7fad7-105">The following topics describe MDX queries and the cellsets they produce, and provide more detailed information about basic MDX syntax.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7fad7-106">如需 MDX 查詢和計算相關效能問題的詳細資訊，請參閱《 [SQL Server 2005 Analysis Services 效能指南》](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide)中的「撰寫有效率的 MDX」一節。</span><span class="sxs-lookup"><span data-stu-id="7fad7-106">For more information about performance issues related to MDX queries and calculations, see the section "Writing Efficient MDX" in the [SQL Server 2005 Analysis Services Performance Guide](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7fad7-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="7fad7-107">In This Section</span></span>  
  
|<span data-ttu-id="7fad7-108">主題</span><span class="sxs-lookup"><span data-stu-id="7fad7-108">Topic</span></span>|<span data-ttu-id="7fad7-109">描述</span><span class="sxs-lookup"><span data-stu-id="7fad7-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="7fad7-110">基本 MDX 查詢 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="7fad7-110">The Basic MDX Query &#40;MDX&#41;</span></span>](mdx-query-the-basic-query.md)|<span data-ttu-id="7fad7-111">提供 MDX SELECT 陳述式的基本語法資訊。</span><span class="sxs-lookup"><span data-stu-id="7fad7-111">Provides basic syntax information for the MDX SELECT statement.</span></span>|  
|[<span data-ttu-id="7fad7-112">利用查詢與 Slicer 軸限制查詢 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="7fad7-112">Restricting the Query with Query and Slicer Axes &#40;MDX&#41;</span></span>](mdx-query-and-slicer-axes-restricting-the-query.md)|<span data-ttu-id="7fad7-113">描述什麼是查詢及 Slicer 軸，以及如何指定它們。</span><span class="sxs-lookup"><span data-stu-id="7fad7-113">Describes what query and slicer axes are and how to specify them.</span></span>|  
|[<span data-ttu-id="7fad7-114">建立查詢中的 Cube 內容 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="7fad7-114">Establishing Cube Context in a Query &#40;MDX&#41;</span></span>](establishing-cube-context-in-a-query-mdx.md)|<span data-ttu-id="7fad7-115">描述 MDX SELECT 陳述式中 FROM 子句的目的。</span><span class="sxs-lookup"><span data-stu-id="7fad7-115">Provides a description of the purpose of the FROM clause in an MDX SELECT statement.</span></span>|  
|[<span data-ttu-id="7fad7-116">在 MDX 中建立命名集 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="7fad7-116">Building Named Sets in MDX &#40;MDX&#41;</span></span>](mdx-named-sets-building-named-sets.md)|<span data-ttu-id="7fad7-117">描述 MDX 中命名集的用途，以及在 MDX 查詢中建立和使用它們所需的技巧。</span><span class="sxs-lookup"><span data-stu-id="7fad7-117">Describes the purpose of named sets in MDX, and the techniques needed to create and use them in MDX queries.</span></span>|  
|[<span data-ttu-id="7fad7-118">在 MDX 中建立導出成員 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="7fad7-118">Building Calculated Members in MDX &#40;MDX&#41;</span></span>](mdx-calculated-members-building-calculated-members.md)|<span data-ttu-id="7fad7-119">提供有關 MDX 中導出成員的資訊，包括在 MDX 運算式中建立和使用它們所需的技巧。</span><span class="sxs-lookup"><span data-stu-id="7fad7-119">Provides information about calculated members in MDX, including the techniques needed to create and use them in MDX expressions.</span></span>|  
|[<span data-ttu-id="7fad7-120">在 MDX 中建立資料格計算 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="7fad7-120">Building Cell Calculations in MDX &#40;MDX&#41;</span></span>](../../multidimensional-models-olap-logical-cube-objects/calculations.md)|<span data-ttu-id="7fad7-121">詳述建立與使用導出資料格的程序。</span><span class="sxs-lookup"><span data-stu-id="7fad7-121">Details the process of creating and using calculated cells.</span></span>|  
|[<span data-ttu-id="7fad7-122">建立和使用屬性值 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="7fad7-122">Creating and Using Property Values &#40;MDX&#41;</span></span>](../../creating-and-using-property-values-mdx.md)|<span data-ttu-id="7fad7-123">詳述建立和使用維度、層級、成員及資料格屬性的程序。</span><span class="sxs-lookup"><span data-stu-id="7fad7-123">Details the process of creating and using dimension, level, member, and cell properties.</span></span>|  
|[<span data-ttu-id="7fad7-124">操作資料 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="7fad7-124">Manipulating Data &#40;MDX&#41;</span></span>](mdx-data-manipulation-manipulating-data.md)|<span data-ttu-id="7fad7-125">描述使用鑽研及積存功能操作資料背後的基本知識，還會描述 MDX 中的行程順序及解決順序。</span><span class="sxs-lookup"><span data-stu-id="7fad7-125">Describes the basics behind manipulating data using drillthrough and rollup, and also describes pass order and solve order in MDX.</span></span>|  
|[<span data-ttu-id="7fad7-126">修改資料 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="7fad7-126">Modifying Data &#40;MDX&#41;</span></span>](mdx-data-modification-modifying-data.md)|<span data-ttu-id="7fad7-127">描述如何使用回寫，暫時或永久地變更多維度資料。</span><span class="sxs-lookup"><span data-stu-id="7fad7-127">Describes how to use writebacks to temporarily or permanently change multidimensional data.</span></span>|  
|[<span data-ttu-id="7fad7-128">使用變數與參數 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="7fad7-128">Using Variables and Parameters &#40;MDX&#41;</span></span>](using-variables-and-parameters-mdx.md)|<span data-ttu-id="7fad7-129">描述如何在 MDX 查詢中使用變數和參數。</span><span class="sxs-lookup"><span data-stu-id="7fad7-129">Describes how to use variables and parameters within MDX queries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7fad7-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7fad7-130">See Also</span></span>  
 [<span data-ttu-id="7fad7-131">多維度運算式 &#40;MDX&#41 參考</span><span class="sxs-lookup"><span data-stu-id="7fad7-131">Multidimensional Expressions &#40;MDX&#41; Reference</span></span>](/sql/mdx/multidimensional-expressions-mdx-reference)  
  
  
