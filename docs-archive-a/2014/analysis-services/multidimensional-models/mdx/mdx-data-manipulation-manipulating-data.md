---
title: 操作 (MDX) 的資料 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MDX [Analysis Services], data manipulation
- data manipulation [MDX]
- Multidimensional Expressions [Analysis Services], data manipulation
ms.assetid: 4865192e-f46b-4ce5-b51c-9e08dbad5b85
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1a1de8b9a3431d79573cd916fa7273b6d8fa7f0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596362"
---
# <a name="manipulating-data-mdx"></a><span data-ttu-id="5b7b4-102">操作資料 (MDX)</span><span class="sxs-lookup"><span data-stu-id="5b7b4-102">Manipulating Data (MDX)</span></span>

<span data-ttu-id="5b7b4-103">您可以使用多維度運算式 (MDX) 以不同的方式操作資料。</span><span class="sxs-lookup"><span data-stu-id="5b7b4-103">Multidimensional Expressions (MDX) can be used to manipulate the data in a variety of ways.</span></span> <span data-ttu-id="5b7b4-104">本文中所列的文章涵蓋一些以 MDX 語言進行資料操作的更先進概念。</span><span class="sxs-lookup"><span data-stu-id="5b7b4-104">The article listed in this article cover some of the more advanced concepts of data manipulation in the MDX language.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="5b7b4-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="5b7b4-105">In This Section</span></span>

|<span data-ttu-id="5b7b4-106">主題</span><span class="sxs-lookup"><span data-stu-id="5b7b4-106">Topic</span></span>|<span data-ttu-id="5b7b4-107">描述</span><span class="sxs-lookup"><span data-stu-id="5b7b4-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="5b7b4-108">使用 DRILLTHROUGH 擷取來源資料 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="5b7b4-108">Using DRILLTHROUGH to Retrieve Source Data &#40;MDX&#41;</span></span>](mdx-data-manipulation-retrieve-source-data-using-drillthrough.md)|<span data-ttu-id="5b7b4-109">討論使用 MDX [DRILLTHROUGH](/sql/mdx/mdx-data-manipulation-drillthrough) 陳述式，在多維度資料來源中擷取適用於資料格之來源資料的資料列集。</span><span class="sxs-lookup"><span data-stu-id="5b7b4-109">Discusses the use of the MDX [DRILLTHROUGH](/sql/mdx/mdx-data-manipulation-drillthrough) statement to retrieve the rowsets of source data applicable to a cell in a multidimensional data source</span></span>|  
|[<span data-ttu-id="5b7b4-110">使用 RollupChildren 函數 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="5b7b4-110">Working with the RollupChildren Function &#40;MDX&#41;</span></span>](mdx-data-manipulation-rollupchildren-function.md)|<span data-ttu-id="5b7b4-111">討論 MDX [RollupChildren](/sql/mdx/rollupchildren-mdx)的影響</span><span class="sxs-lookup"><span data-stu-id="5b7b4-111">Discusses the impact of the MDX [RollupChildren](/sql/mdx/rollupchildren-mdx)</span></span>
|[<span data-ttu-id="5b7b4-112">了解行程順序和求解順序 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="5b7b4-112">Understanding Pass Order and Solve Order &#40;MDX&#41;</span></span>](mdx-data-manipulation-understanding-pass-order-and-solve-order.md)|<span data-ttu-id="5b7b4-113">詳細說明解決順序的概念，以及此功能如何影響 MDX 運算式、陳述式及指令碼。</span><span class="sxs-lookup"><span data-stu-id="5b7b4-113">Details the concepts of solve order, and how this feature affects MDX expressions, statements, and scripts.</span></span>|  

<!-- ??

|[Script for Search and Replace] function on the analysis of multidimensional data.|

GeneMi is removing this commented row because it is unclear what article its link meant to link to.
Also, I had to add its leading '|' character, for consistency to aid bulk automated updated to our markdown source code.

GeneMi , 2019/01/19
-->

## <a name="see-also"></a><span data-ttu-id="5b7b4-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b7b4-114">See Also</span></span>

[<span data-ttu-id="5b7b4-115">MDX 查詢基礎觀念 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="5b7b4-115">MDX Query Fundamentals (Analysis Services)</span></span>](mdx-query-fundamentals-analysis-services.md)
