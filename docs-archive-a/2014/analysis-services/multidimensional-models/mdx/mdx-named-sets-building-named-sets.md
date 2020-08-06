---
title: 在 mdx 中建立命名集 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Multidimensional Expressions [Analysis Services], named sets
- named sets [MDX]
- sets [MDX]
- MDX [Analysis Services], named sets
- queries [MDX], named sets
- set expressions [MDX]
ms.assetid: 213b0035-e96d-4ba0-83f2-ded206905603
author: minewiskan
ms.author: owend
ms.openlocfilehash: 91296f8c5d47afb15c67f0b60435c7f961734573
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698647"
---
# <a name="building-named-sets-in-mdx-mdx"></a><span data-ttu-id="722e0-102">在 MDX 中建立命名集 (MDX)</span><span class="sxs-lookup"><span data-stu-id="722e0-102">Building Named Sets in MDX (MDX)</span></span>
  <span data-ttu-id="722e0-103">集合運算式可能是一項冗長而複雜的宣告，因而不太容易遵照和了解。</span><span class="sxs-lookup"><span data-stu-id="722e0-103">A set expression can be a lengthy and complex declaration, and therefore be difficult to follow or understand.</span></span> <span data-ttu-id="722e0-104">或者，可能會相當頻繁地使用集合運算式，一再定義該集合就變得相當惱人。</span><span class="sxs-lookup"><span data-stu-id="722e0-104">Or, a set expression may be used so frequently that repeatedly defining the set becomes burdensome.</span></span> <span data-ttu-id="722e0-105">若要讓冗長、複雜或經常使用的運算式更為容易處理，多維度運算式 (MDX) 可讓您將這類運算式作為「命名集」\*\*。</span><span class="sxs-lookup"><span data-stu-id="722e0-105">To help make working with a lengthy, complex or commonly used expression easier, Multidimensional Expressions (MDX) lets you such an expression as a *named set*.</span></span>  
  
 <span data-ttu-id="722e0-106">基本上，命名集是一個已指派別名的集合運算式。</span><span class="sxs-lookup"><span data-stu-id="722e0-106">Basically, a named set is a set expression to which an alias has been assigned.</span></span> <span data-ttu-id="722e0-107">命名集可以包含通常被包含於集合中的任何成員或函數。</span><span class="sxs-lookup"><span data-stu-id="722e0-107">A named set can incorporate any members or functions that can ordinarily be incorporated into a set.</span></span> <span data-ttu-id="722e0-108">因為 MDX 會將命名集別名視為集合運算式，您可以在可接受集合運算式的任何地方使用那個別名。</span><span class="sxs-lookup"><span data-stu-id="722e0-108">Because MDX treats the named set alias as a set expression, you can use that alias anywhere a set expression is accepted.</span></span>  
  
 <span data-ttu-id="722e0-109">您可以定義命名集，以擁有以下其中一個內容：</span><span class="sxs-lookup"><span data-stu-id="722e0-109">You can define a named set to have one of the following contexts:</span></span>  
  
-   <span data-ttu-id="722e0-110">**查詢範圍** ：若要建立一個命名集，把它定義為 MDX 查詢的一部分，而且範圍限制在查詢內，請使用 WITH 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="722e0-110">**Query-scoped** To create a named set that is defined as part of an MDX query, and therefore whose scope is limited to the query, you use the WITH keyword.</span></span> <span data-ttu-id="722e0-111">然後您就可以在 MDX SELECT 陳述式內使用命名集。</span><span class="sxs-lookup"><span data-stu-id="722e0-111">You can then use the named set within an MDX SELECT statement.</span></span> <span data-ttu-id="722e0-112">使用這種方式，可以變更利用 WITH 關鍵字建立的命名集，而不會影響到 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="722e0-112">Using this approach, the named set created by using the WITH keyword can be changed without disturbing the SELECT statement.</span></span>  
  
     <span data-ttu-id="722e0-113">如需如何使用 WITH 關鍵字來建立命名集的詳細資訊，請參閱[建立查詢範圍命名集 &#40;MDX&#41;](mdx-named-sets-creating-query-scoped-named-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="722e0-113">For more information about how to use the WITH keyword to create named sets, see [Creating Query-Scoped Named Sets &#40;MDX&#41;](mdx-named-sets-creating-query-scoped-named-sets.md).</span></span>  
  
-   <span data-ttu-id="722e0-114">**工作階段範圍** ：若要建立一個範圍超出查詢內容的命名集，也就是說它的範圍是 MDX 工作階段的存留時間，您可以使用 CREATE SET 陳述式。</span><span class="sxs-lookup"><span data-stu-id="722e0-114">**Session-scoped** To create a named set whose scope is wider than the context of the query, that is, whose scope is the lifetime of the MDX session, you use the CREATE SET statement.</span></span> <span data-ttu-id="722e0-115">使用 CREATE SET 陳述式定義的命名集，可以在那個工作階段中的所有 MDX 查詢使用。</span><span class="sxs-lookup"><span data-stu-id="722e0-115">A named set defined by using the CREATE SET statement is available to all MDX queries in that session.</span></span> <span data-ttu-id="722e0-116">對於需要在不同查詢中重覆使用某一命名集的用戶端應用程式而言，CREATE SET 陳述式是很有用處的。</span><span class="sxs-lookup"><span data-stu-id="722e0-116">The CREATE SET statement makes sense, for example, in a client application that consistently reuses a set in a variety of queries.</span></span>  
  
     <span data-ttu-id="722e0-117">如需如何使用 CREATE SET 陳述式來建立工作階段中的命名集的詳細資訊，請參閱[建立工作階段範圍命名集 &#40;MDX&#41;](mdx-named-sets-creating-session-scoped-named-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="722e0-117">For more information about how to use the CREATE SET statement to create named sets in a session, see [Creating Session-Scoped Named Sets &#40;MDX&#41;](mdx-named-sets-creating-session-scoped-named-sets.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="722e0-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="722e0-118">See Also</span></span>  
 <span data-ttu-id="722e0-119">[SELECT 語句 &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select) </span><span class="sxs-lookup"><span data-stu-id="722e0-119">[SELECT Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select) </span></span>  
 <span data-ttu-id="722e0-120">[&#40;MDX&#41;建立 SET 語句](/sql/mdx/mdx-data-definition-create-set) </span><span class="sxs-lookup"><span data-stu-id="722e0-120">[CREATE SET Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-set) </span></span>  
 [<span data-ttu-id="722e0-121">MDX 查詢基礎觀念 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="722e0-121">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-query-fundamentals-analysis-services.md)  
  
  
