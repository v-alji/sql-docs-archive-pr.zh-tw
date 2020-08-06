---
title: 在 MDX 中建立匯出成員 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MDX [Analysis Services], calculated members
- calculated members [MDX]
- Multidimensional Expressions [Analysis Services], calculated members
- queries [MDX], calculated members
ms.assetid: 9322e8b8-43e1-4e02-a7d1-e41a586a5bb8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 30dc6562ec394065cf2f177608d4e5679cbd7df3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594736"
---
# <a name="building-calculated-members-in-mdx-mdx"></a><span data-ttu-id="a39dd-102">在 MDX 中建立導出成員 (MDX)</span><span class="sxs-lookup"><span data-stu-id="a39dd-102">Building Calculated Members in MDX (MDX)</span></span>
  <span data-ttu-id="a39dd-103">在多維度運算式 (MDX) 中，導出成員是藉由計算 MDX 運算式以傳回一個值而解析出來的成員。</span><span class="sxs-lookup"><span data-stu-id="a39dd-103">In Multidimensional Expressions (MDX), a calculated member is a member that is resolved by calculating an MDX expression to return a value.</span></span> <span data-ttu-id="a39dd-104">此一定義涵蓋的範圍相當廣泛。</span><span class="sxs-lookup"><span data-stu-id="a39dd-104">This innocuous definition covers an incredible amount of ground.</span></span> <span data-ttu-id="a39dd-105">在 MDX 查詢中建構和使用導出成員的能力，提供了許多管理多維度資料的功能。</span><span class="sxs-lookup"><span data-stu-id="a39dd-105">The ability to construct and use calculated members in an MDX query provides a great deal of manipulation capability for multidimensional data.</span></span>  
  
 <span data-ttu-id="a39dd-106">您可以在階層內的任意點建立導出成員。</span><span class="sxs-lookup"><span data-stu-id="a39dd-106">You can create calculated members at any point within a hierarchy.</span></span> <span data-ttu-id="a39dd-107">您也可以建立一個導出成員，使它不僅要依據 Cube 中現有的成員，還要依據同一 MDX 運算式中定義的其他導出成員。</span><span class="sxs-lookup"><span data-stu-id="a39dd-107">You can also create calculated members that depend not only on existing members in a cube, but also on other calculated members defined in the same MDX expression.</span></span>  
  
 <span data-ttu-id="a39dd-108">您可以定義導出成員，以擁有以下其中一個內容：</span><span class="sxs-lookup"><span data-stu-id="a39dd-108">You can define a calculated member to have one of the following contexts:</span></span>  
  
-   <span data-ttu-id="a39dd-109">**查詢範圍** ：若要建立一個導出資料格，把它定義為 MDX 查詢的一部份，而且範圍限制在查詢內，請使用 WITH 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="a39dd-109">**Query-scoped** To create a calculated member that is defined as part of an MDX query, and therefore whose scope is limited to the query, you use the WITH keyword.</span></span> <span data-ttu-id="a39dd-110">然後您就可以在 MDX SELECT 陳述式內使用導出成員。</span><span class="sxs-lookup"><span data-stu-id="a39dd-110">You can then use the calculated member within an MDX SELECT statement.</span></span> <span data-ttu-id="a39dd-111">使用這種方式，可以變更利用 WITH 關鍵字建立的導出成員，而不會影響到 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="a39dd-111">Using this approach, the calculated member created by using the WITH keyword can be changed without disturbing the SELECT statement.</span></span>  
  
     <span data-ttu-id="a39dd-112">如需如何使用 WITH 關鍵字建立導出成員的詳細資訊，請參閱[建立查詢範圍導出成員 &#40;MDX&#41;](mdx-calculated-members-query-scoped-calculated-members.md)。</span><span class="sxs-lookup"><span data-stu-id="a39dd-112">For more information about how to use the WITH keyword to create calculated members, see [Creating Query-Scoped Calculated Members &#40;MDX&#41;](mdx-calculated-members-query-scoped-calculated-members.md).</span></span>  
  
-   <span data-ttu-id="a39dd-113">**工作階段範圍** ：若要建立一個範圍超出查詢內容的導出成員，也就是說它的範圍是 MDX 工作階段的存留時間，您可以使用 CREATE MEMBER 陳述式。</span><span class="sxs-lookup"><span data-stu-id="a39dd-113">**Session-scoped** To create a calculated member whose scope is wider than the context of the query, that is, whose scope is the lifetime of the MDX session, you use the CREATE MEMBER statement.</span></span> <span data-ttu-id="a39dd-114">使用 CREATE MEMBER 陳述式定義的導出成員，可以在那個工作階段中的所有 MDX 查詢使用。</span><span class="sxs-lookup"><span data-stu-id="a39dd-114">A calculated member defined by using the CREATE MEMBER statement is available to all MDX queries in that session.</span></span> <span data-ttu-id="a39dd-115">對於需要在不同查詢中重覆使用相同命名集的用戶端應用程式而言，CREATE MEMBER 陳述式很有用處。</span><span class="sxs-lookup"><span data-stu-id="a39dd-115">The CREATE MEMBER statement makes sense, for example, in a client application that consistently reuses the same set in a variety of queries.</span></span>  
  
     <span data-ttu-id="a39dd-116">如需如何使用 CREATE MEMBER 陳述式來建立工作階段中導出成員的詳細資訊，請參閱[建立工作階段範圍導出成員 &#40;MDX&#41;](mdx-calculated-members-session-scoped-calculated-members.md)。</span><span class="sxs-lookup"><span data-stu-id="a39dd-116">For more information about how to use the CREATE MEMBER statement to create calculated members in a session, see [Creating Session-Scoped Calculated Members &#40;MDX&#41;](mdx-calculated-members-session-scoped-calculated-members.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a39dd-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a39dd-117">See Also</span></span>  
 <span data-ttu-id="a39dd-118">[&#40;MDX&#41;的 CREATE MEMBER 語句](/sql/mdx/mdx-data-definition-create-member) </span><span class="sxs-lookup"><span data-stu-id="a39dd-118">[CREATE MEMBER Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member) </span></span>  
 <span data-ttu-id="a39dd-119">[Mdx 函數參考 &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx) </span><span class="sxs-lookup"><span data-stu-id="a39dd-119">[MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx) </span></span>  
 [<span data-ttu-id="a39dd-120">SELECT 陳述式 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="a39dd-120">SELECT Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-manipulation-select)  
  
  
