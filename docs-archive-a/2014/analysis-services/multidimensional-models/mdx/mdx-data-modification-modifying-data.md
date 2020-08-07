---
title: 修改 (MDX) 的資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- modifying data [MDX]
- Multidimensional Expressions [Analysis Services], data modifications
- MDX [Analysis Services], data modifications
- data modifications [MDX]
ms.assetid: 363b662c-b839-4971-bbd7-1842f73ce141
author: minewiskan
ms.author: owend
ms.openlocfilehash: 01df67471753922e3e7db39c56a9ed50aae900dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596926"
---
# <a name="modifying-data-mdx"></a><span data-ttu-id="a198d-102">修改資料 (MDX)</span><span class="sxs-lookup"><span data-stu-id="a198d-102">Modifying Data (MDX)</span></span>
  <span data-ttu-id="a198d-103">除了使用多維度運算式 (MDX) 擷取及處理維度與 Cube 的資料之外，您還可以使用 MDX來更新或「回寫」\*\* 維度與 Cube 資料。</span><span class="sxs-lookup"><span data-stu-id="a198d-103">Besides using Multidimensional Expressions (MDX) to retrieve and handle data from dimensions and cubes, you can use MDX to update or *writeback* dimension and cube data.</span></span> <span data-ttu-id="a198d-104">這些更新可能是暫時性 (如同推測性或 "what if" 分析 ) 或永久性 (例如，必須根據資料分析來變更時)。</span><span class="sxs-lookup"><span data-stu-id="a198d-104">These updates can be temporary, as with speculative, or "what if", analysis, or permanent, as when changes must occur based upon data analysis.</span></span>  
  
 <span data-ttu-id="a198d-105">資料的更新可發生在維度或 Cube 層級：</span><span class="sxs-lookup"><span data-stu-id="a198d-105">Updates to data can occur at the dimension or cube level:</span></span>  
  
 <span data-ttu-id="a198d-106">**維度回寫**</span><span class="sxs-lookup"><span data-stu-id="a198d-106">**Dimension writebacks**</span></span>  
 <span data-ttu-id="a198d-107">您可以使用 [ALTER CUBE 陳述式 (MDX)](/sql/mdx/mdx-data-definition-alter-cube) 陳述式來變更可寫入維度的資料，並且使用 [REFRESH CUBE 陳述式 (MDX)](/sql/mdx/mdx-data-definition-refresh-cube) 來反映屬性值的刪除、建立及更新。</span><span class="sxs-lookup"><span data-stu-id="a198d-107">You use the [ALTER CUBE Statement (MDX)](/sql/mdx/mdx-data-definition-alter-cube) statement to change a write-enabled dimension's data and the [REFRESH CUBE Statement (MDX)](/sql/mdx/mdx-data-definition-refresh-cube) to reflect the deletion, creation, and updating of attribute values.</span></span> <span data-ttu-id="a198d-108">您也可以使用 ALTER CUBE 陳述式來執行複雜的作業，例如刪除階層中的整個子樹，以及將已刪除成員的子系升級。</span><span class="sxs-lookup"><span data-stu-id="a198d-108">You can also use the ALTER CUBE statement to perform complex operations, such as deleting a whole sub-tree in a hierarchy and promoting the children of a deleted member.</span></span>  
  
 <span data-ttu-id="a198d-109">**Cube 回寫**</span><span class="sxs-lookup"><span data-stu-id="a198d-109">**Cube writebacks**</span></span>  
 <span data-ttu-id="a198d-110">您可以使用 [UPDATE CUBE](/sql/mdx/mdx-data-manipulation-update-cube) 陳述式，對可寫入 Cube 進行更新。</span><span class="sxs-lookup"><span data-stu-id="a198d-110">You use the [UPDATE CUBE](/sql/mdx/mdx-data-manipulation-update-cube) statement to make updates to a write-enabled cube.</span></span> <span data-ttu-id="a198d-111">您可以使用 UPDATE CUBE 陳述式，來更新具有指定值的 Tuple。</span><span class="sxs-lookup"><span data-stu-id="a198d-111">The UPDATE CUBE statement lets you update a tuple with a specific value.</span></span> <span data-ttu-id="a198d-112">您可以使用 [REFRESH CUBE 陳述式 (MDX)](/sql/mdx/mdx-data-definition-refresh-cube) ，以伺服器上的更新資料來重新整理用戶端工作階段中的資料。</span><span class="sxs-lookup"><span data-stu-id="a198d-112">You use the [REFRESH CUBE Statement (MDX)](/sql/mdx/mdx-data-definition-refresh-cube) to refresh data in a client session with updated data from the server.</span></span>  
  
 <span data-ttu-id="a198d-113">如需詳細資訊，請參閱[使用 Cube 回寫 &#40;MDX&#41;](mdx-data-modification-using-cube-writebacks.md)。</span><span class="sxs-lookup"><span data-stu-id="a198d-113">For more information, see [Using Cube Writebacks &#40;MDX&#41;](mdx-data-modification-using-cube-writebacks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a198d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a198d-114">See Also</span></span>  
 [<span data-ttu-id="a198d-115">MDX 查詢基礎觀念 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a198d-115">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-query-fundamentals-analysis-services.md)  
  
  
