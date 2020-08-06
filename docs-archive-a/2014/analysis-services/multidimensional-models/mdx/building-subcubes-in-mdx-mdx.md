---
title: 在 MDX 中建立 Subcube (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- queries [MDX], subcubes
- subcubes [MDX]
- filtered views [MDX]
- MDX [Analysis Services], subcubes
- Multidimensional Expressions [Analysis Services], subcubes
- CREATE SUBCUBE statement
ms.assetid: 5403a62b-99ac-4d83-b02a-89bf78bf0f46
author: minewiskan
ms.author: owend
ms.openlocfilehash: 653b4d30aa86f52179c7b13619ac4347aa65c339
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597417"
---
# <a name="building-subcubes-in-mdx-mdx"></a><span data-ttu-id="5f9f1-102">在 MDX 中建立 Subcube (MDX)</span><span class="sxs-lookup"><span data-stu-id="5f9f1-102">Building Subcubes in MDX (MDX)</span></span>
  <span data-ttu-id="5f9f1-103">Subcube 是 Cube 的子集，呈現篩選後的基礎資料檢視。</span><span class="sxs-lookup"><span data-stu-id="5f9f1-103">A subcube is a subset of a cube on representing a filtered view of the underlying data.</span></span> <span data-ttu-id="5f9f1-104">將 Cube 限制在 Subcube，可以改善查詢效能。</span><span class="sxs-lookup"><span data-stu-id="5f9f1-104">By limiting the cube to a subcube, you can improve query performance.</span></span>  
  
 <span data-ttu-id="5f9f1-105">若要定義 Subcube，您可以使用 [CREATE SUBCUBE](/sql/mdx/mdx-data-definition-create-subcube) 陳述式，如本主題所述。</span><span class="sxs-lookup"><span data-stu-id="5f9f1-105">To define a subcube, you use the [CREATE SUBCUBE](/sql/mdx/mdx-data-definition-create-subcube) statement, as described in this topic.</span></span>  
  
## <a name="create-subcube-syntax"></a><span data-ttu-id="5f9f1-106">CREATE SUBCUBE 語法</span><span class="sxs-lookup"><span data-stu-id="5f9f1-106">CREATE SUBCUBE Syntax</span></span>  
 <span data-ttu-id="5f9f1-107">使用下列語法來建立 Subcube：</span><span class="sxs-lookup"><span data-stu-id="5f9f1-107">Use the following syntax to create a subcube:</span></span>  
  
```  
CREATE SUBCUBE Subcube_Identifier AS Subcube_Expression  
```  
  
 <span data-ttu-id="5f9f1-108">CREATE SUBCUBE 語法相當簡單。</span><span class="sxs-lookup"><span data-stu-id="5f9f1-108">The CREATE SUBCUBE syntax is fairly simple.</span></span> <span data-ttu-id="5f9f1-109">*Subcube_Identifier* 參數可識別將作為 Subcube 基礎的 Cube。</span><span class="sxs-lookup"><span data-stu-id="5f9f1-109">The *Subcube_Identifier* parameter identifies the cube on which the subcube will be based.</span></span> <span data-ttu-id="5f9f1-110">*Subcube_Expression* 參數可選取將成為 Subcube 的 Cube 部分。</span><span class="sxs-lookup"><span data-stu-id="5f9f1-110">The *Subcube_Expression* parameter selects the part of the cube that will become the subcube</span></span>  
  
 <span data-ttu-id="5f9f1-111">建立 Subcube 之後，此 Subcube 就會成為所有 MDX 查詢的內容，直到工作階段結束或是執行 [DROP SUBCUBE](/sql/mdx/mdx-data-definition-drop-subcube) 陳述式為止。</span><span class="sxs-lookup"><span data-stu-id="5f9f1-111">After you create a subcube, that subcube becomes the context for all MDX queries until either the session closes or you run the [DROP SUBCUBE](/sql/mdx/mdx-data-definition-drop-subcube) statement.</span></span>  
  
### <a name="what-a-subcube-contains"></a><span data-ttu-id="5f9f1-112">Subcube 包含的項目</span><span class="sxs-lookup"><span data-stu-id="5f9f1-112">What a Subcube Contains</span></span>  
 <span data-ttu-id="5f9f1-113">雖然要使用 CREATE SUBCUBE 陳述式相當簡單，但陳述式本身不會明確地顯示會成為 Subcube 一部份的所有成員。</span><span class="sxs-lookup"><span data-stu-id="5f9f1-113">Although the CREATE SUBCUBE statement is fairly simple to use, the statement itself does not explicitly show all the members that become part of a subcube.</span></span> <span data-ttu-id="5f9f1-114">在定義 Subcube 期間，適用以下規則：</span><span class="sxs-lookup"><span data-stu-id="5f9f1-114">In defining a subcube, the following rules apply:</span></span>  
  
-   <span data-ttu-id="5f9f1-115">如果包含階層的 `(All)` 成員，那個階層的所有成員就會包括在內。</span><span class="sxs-lookup"><span data-stu-id="5f9f1-115">If you include the `(All)` member of a hierarchy, you include every member of that hierarchy.</span></span>  
  
-   <span data-ttu-id="5f9f1-116">如果包含任何成員，那個成員的上階及下階就會包括在內。</span><span class="sxs-lookup"><span data-stu-id="5f9f1-116">If you include any member, you include that member's ascendants and descendants.</span></span>  
  
-   <span data-ttu-id="5f9f1-117">如果包含層級的每個成員，該階層的所有成員就會包括在內。</span><span class="sxs-lookup"><span data-stu-id="5f9f1-117">If you include every member from a level, you include all members from the hierarchy.</span></span> <span data-ttu-id="5f9f1-118">如果其他階層的成員不是和該層級的成員並存，則將會予以排除 (例如，未包含客戶的城市等類的不平衡階層)。</span><span class="sxs-lookup"><span data-stu-id="5f9f1-118">Members from other hierarchies will be excluded if those members do not exist with members from the level (for example, an unbalanced hierarchy such as a city that does not contain customers).</span></span>  
  
-   <span data-ttu-id="5f9f1-119">Subcube 永遠包含 Cube 的每個 `(All)` 成員。</span><span class="sxs-lookup"><span data-stu-id="5f9f1-119">A subcube will always contain every `(All)` member from the cube.</span></span>  
  
 <span data-ttu-id="5f9f1-120">此外，Subcube 內的彙總值都是以視覺化的方式總計。</span><span class="sxs-lookup"><span data-stu-id="5f9f1-120">Additionally, aggregate values within the subcube are visually totaled.</span></span> <span data-ttu-id="5f9f1-121">例如，Subcube 包含 `USA`、 `WA`及 `OR`。</span><span class="sxs-lookup"><span data-stu-id="5f9f1-121">For example, a subcube contains `USA`, `WA`, and `OR`.</span></span> <span data-ttu-id="5f9f1-122">因為 Subcube 定義的狀態只有 `USA` 及 `{WA,OR}` ，所以 `WA` 的彙總值將會是 `OR` 的總和。</span><span class="sxs-lookup"><span data-stu-id="5f9f1-122">The aggregate value for `USA` will be the sum of `{WA,OR}` because `WA` and `OR` are the only states defined by the subcube.</span></span> <span data-ttu-id="5f9f1-123">其他狀態都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="5f9f1-123">All other states will be ignored.</span></span>  
  
 <span data-ttu-id="5f9f1-124">此外，明確參考 Subcube 外部的資料格，則會傳回在整個 Cube 內容中評估的資料格值。</span><span class="sxs-lookup"><span data-stu-id="5f9f1-124">Also, explicit references to cells outside the subcube return cell values that are evaluated in the context of the whole cube.</span></span> <span data-ttu-id="5f9f1-125">例如，您可以建立限制在目前年度的 Subcube。</span><span class="sxs-lookup"><span data-stu-id="5f9f1-125">For example, you create a subcube that is limited to the current year.</span></span> <span data-ttu-id="5f9f1-126">然後，您可以使用 [ParallelPeriod](/sql/mdx/parallelperiod-mdx) 函數比較目前年度與前一個年度。</span><span class="sxs-lookup"><span data-stu-id="5f9f1-126">You then use the [ParallelPeriod](/sql/mdx/parallelperiod-mdx) function to compare the current year to the previous year.</span></span> <span data-ttu-id="5f9f1-127">即使前一年的值位於子工作子資料集外，值的差異還是會傳回。</span><span class="sxs-lookup"><span data-stu-id="5f9f1-127">The difference in values will be returned even though the previous year's value lies outside the subcube.</span></span>  
  
 <span data-ttu-id="5f9f1-128">最後，如果原始的內容未被覆寫，就會在子選擇的內容中評估曾在子選擇中評估的集合函數。</span><span class="sxs-lookup"><span data-stu-id="5f9f1-128">Finally, if the original context is not overwritten, set functions evaluated in a subselect are evaluated in the context of the subselect.</span></span> <span data-ttu-id="5f9f1-129">如果內容會被覆寫，就會在整個 Cube 的內容中評估集合函數。</span><span class="sxs-lookup"><span data-stu-id="5f9f1-129">If the context is overwritten, set functions are evaluated in the context of the whole cube.</span></span>  
  
## <a name="create-subcube-example"></a><span data-ttu-id="5f9f1-130">CREATE SUBCUBE 範例</span><span class="sxs-lookup"><span data-stu-id="5f9f1-130">CREATE SUBCUBE Example</span></span>  
 <span data-ttu-id="5f9f1-131">下列範例會建立一個 Subcube，將 Budget Cube 限制為只有帳戶 4200 及 4300：</span><span class="sxs-lookup"><span data-stu-id="5f9f1-131">The following example creates a subcube that restricts the Budget cube to only accounts 4200 and 4300:</span></span>  
  
 `CREATE SUBCUBE Budget AS SELECT {[Account].[Account].&[4200], [Account].[Account].&[4300] } ON 0 FROM Budget`  
  
 <span data-ttu-id="5f9f1-132">在為工作階段建立 Subcube 之後，將會對該 Subcube 進行任何後續查詢，而不是對整個 Cube。</span><span class="sxs-lookup"><span data-stu-id="5f9f1-132">Having created a subcube for the session, any subsequent queries will be against the subcube, not the whole cube.</span></span> <span data-ttu-id="5f9f1-133">例如，您可以執行以下查詢。</span><span class="sxs-lookup"><span data-stu-id="5f9f1-133">For example, you run the following query.</span></span> <span data-ttu-id="5f9f1-134">此查詢將只會傳回帳戶 4200 及 4300 的成員。</span><span class="sxs-lookup"><span data-stu-id="5f9f1-134">This query will only return members from accounts 4200 and 4300.</span></span>  
  
 `SELECT [Account].[Account].Members ON 0, Measures.Members ON 1 FROM Budget`  
  
## <a name="see-also"></a><span data-ttu-id="5f9f1-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f9f1-135">See Also</span></span>  
 <span data-ttu-id="5f9f1-136">[在查詢中建立 Cube 內容 &#40;MDX&#41;](establishing-cube-context-in-a-query-mdx.md) </span><span class="sxs-lookup"><span data-stu-id="5f9f1-136">[Establishing Cube Context in a Query &#40;MDX&#41;](establishing-cube-context-in-a-query-mdx.md) </span></span>  
 [<span data-ttu-id="5f9f1-137">MDX 查詢基礎觀念 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="5f9f1-137">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-query-fundamentals-analysis-services.md)  
  
  
