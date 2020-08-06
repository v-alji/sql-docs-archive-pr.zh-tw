---
title: 建立和使用 (MDX) 的屬性值 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- property values [MDX]
- queries [MDX], property values
- MDX [Analysis Services], property values
- Multidimensional Expressions [Analysis Services], property values
ms.assetid: 0cafb269-03c8-4183-b6e9-220f071e4ef2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 67eadc6bc2f0bf6f318f20ad42a5cc9e7a5afa5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596947"
---
# <a name="creating-and-using-property-values-mdx"></a><span data-ttu-id="3a2d4-102">建立和使用屬性值 (MDX)</span><span class="sxs-lookup"><span data-stu-id="3a2d4-102">Creating and Using Property Values (MDX)</span></span>
  <span data-ttu-id="3a2d4-103">多維度運算式 (MDX) 支援內建和使用者自訂維度、層級、成員，和資料格的屬性。</span><span class="sxs-lookup"><span data-stu-id="3a2d4-103">Multidimensional Expressions (MDX) supports intrinsic and user-defined properties for dimensions, levels, members, and cells.</span></span> <span data-ttu-id="3a2d4-104">內建屬性可提供唯一的名稱、標題，甚至個別資料格的格式和字型大小。</span><span class="sxs-lookup"><span data-stu-id="3a2d4-104">The intrinsic properties provide unique names, captions, and even formatting and font sizes for individual cells.</span></span> <span data-ttu-id="3a2d4-105">另一方面使用者自訂屬性幾乎可以為成員提供所有的額外屬性。</span><span class="sxs-lookup"><span data-stu-id="3a2d4-105">User-defined properties, on the other hand, can provide almost any kind of additional attribute to members.</span></span>  
  
 <span data-ttu-id="3a2d4-106">以下層級可以使用內建與使用者自訂屬性：</span><span class="sxs-lookup"><span data-stu-id="3a2d4-106">Intrinsic and user-defined properties are available at the following levels:</span></span>  
  
 <span data-ttu-id="3a2d4-107">**成員屬性**</span><span class="sxs-lookup"><span data-stu-id="3a2d4-107">**Member properties**</span></span>  
 <span data-ttu-id="3a2d4-108">成員屬性包含每個 Tuple 中每個成員的基本資訊。</span><span class="sxs-lookup"><span data-stu-id="3a2d4-108">Member properties cover the basic information about each member in each tuple.</span></span> <span data-ttu-id="3a2d4-109">此基本資訊包括成員名稱、父層級、子系數目等等。</span><span class="sxs-lookup"><span data-stu-id="3a2d4-109">This basic information includes the member name, parent level, the number of children, and so on.</span></span>  
  
 <span data-ttu-id="3a2d4-110">如需成員屬性及如何使用成員屬性的資訊，請參閱[使用成員屬性 &#40;MDX&#41;](multidimensional-models/mdx/mdx-member-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="3a2d4-110">For information about member properties and how to use them, see [Using Member Properties &#40;MDX&#41;](multidimensional-models/mdx/mdx-member-properties.md).</span></span>  
  
 <span data-ttu-id="3a2d4-111">**資料格屬性**</span><span class="sxs-lookup"><span data-stu-id="3a2d4-111">**Cell properties**</span></span>  
 <span data-ttu-id="3a2d4-112">資料格屬性包含多維度資料來源 (如 Cube) 之資料格內容及格式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3a2d4-112">Cell properties contain information about the content and format of cells in a multidimensional data source, such as a cube.</span></span>  
  
 <span data-ttu-id="3a2d4-113">如需資料格屬性及如何使用資料格屬性的詳細資訊，請參閱[使用資料格屬性 &#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-using-cell-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="3a2d4-113">For more information about cell properties and how to use them, see [Using Cell Properties &#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-using-cell-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a2d4-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a2d4-114">See Also</span></span>  
 [<span data-ttu-id="3a2d4-115">MDX 查詢基礎觀念 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="3a2d4-115">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
