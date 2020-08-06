---
title: 建立會話範圍命名集 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- CREATE SET statement
- session-scoped named sets [MDX]
ms.assetid: b751e1e4-6d4c-4d36-a28d-ffdaaee0f1c7
author: minewiskan
ms.author: owend
ms.openlocfilehash: d35bd61dcc59eca8bcb920ed99f2e791631047c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703333"
---
# <a name="creating-session-scoped-named-sets-mdx"></a><span data-ttu-id="ac0da-102">建立工作階段範圍命名集 (MDX)</span><span class="sxs-lookup"><span data-stu-id="ac0da-102">Creating Session-Scoped Named Sets (MDX)</span></span>
  <span data-ttu-id="ac0da-103">若要建立可在整個多維度運算式 (MDX) 工作階段取得的命名集，您可以使用 [CREATE SET](/sql/mdx/mdx-data-definition-create-set) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ac0da-103">To create a named set that is available throughout a Multidimensional Expressions (MDX) session, you use the [CREATE SET](/sql/mdx/mdx-data-definition-create-set) statement.</span></span> <span data-ttu-id="ac0da-104">使用 CREATE SET 陳述式建立的命名集，直到 MDX 工作階段結束後才會移除。</span><span class="sxs-lookup"><span data-stu-id="ac0da-104">A named set that is created by using the CREATE SET statement will not be removed until after the MDX session closes.</span></span>  
  
 <span data-ttu-id="ac0da-105">如同本主題所討論，WITH 關鍵字的語法直接且使用簡單。</span><span class="sxs-lookup"><span data-stu-id="ac0da-105">As discussed in this topic, the syntax of the WITH keyword is straightforward and easy to use.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ac0da-106">如需命名集的詳細資訊，請參閱[在 MDX 中建立命名集 &#40;MDX&#41;](mdx-named-sets-building-named-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="ac0da-106">For more information about named sets, see [Building Named Sets in MDX &#40;MDX&#41;](mdx-named-sets-building-named-sets.md).</span></span>  
  
## <a name="create-set-syntax"></a><span data-ttu-id="ac0da-107">CREATE SET 語法</span><span class="sxs-lookup"><span data-stu-id="ac0da-107">CREATE SET Syntax</span></span>  
 <span data-ttu-id="ac0da-108">使用下列 CREATE SET 陳述式的語法：</span><span class="sxs-lookup"><span data-stu-id="ac0da-108">Use the following syntax for the CREATE SET statement:</span></span>  
  
```  
CREATE SESSION SET [CURRENTCUBE. | <cube name>.]<Set Identifier> AS <Set Expression>  
```  
  
 <span data-ttu-id="ac0da-109">在 CREATE SET 語法中， `cube name` 參數包含命名集成員的 Cube 名稱。</span><span class="sxs-lookup"><span data-stu-id="ac0da-109">In the CREATE SET syntax, the `cube name` parameter contains the name of the cube that contains the members for the named set.</span></span> <span data-ttu-id="ac0da-110">如果未指定 `cube name` 參數，目前的 Cube 就會做為包含命名集成員的 Cube 使用。</span><span class="sxs-lookup"><span data-stu-id="ac0da-110">If the `cube name` parameter is not specified, the current cube will be used as the cube that contains the member for the named set.</span></span> <span data-ttu-id="ac0da-111">此外， `Set_Identifier` 參數包含命名集的別名，以及包含命名集別名將會參考之集合運算式的 `Set_Expression` 參數。</span><span class="sxs-lookup"><span data-stu-id="ac0da-111">Also, the `Set_Identifier` parameter contains the alias for the named set, and the `Set_Expression` parameter contains the set expression to which the named set alias will refer.</span></span>  
  
## <a name="create-set-example"></a><span data-ttu-id="ac0da-112">CREATE SET 範例</span><span class="sxs-lookup"><span data-stu-id="ac0da-112">CREATE SET Example</span></span>  
 <span data-ttu-id="ac0da-113">以下範例使用 CREATE SET 陳述式，根據 Store Cube 建立 `SetCities_2_3` 命名集。</span><span class="sxs-lookup"><span data-stu-id="ac0da-113">The following example uses the CREATE SET statement to create the `SetCities_2_3` named set based on the Store cube.</span></span> <span data-ttu-id="ac0da-114">`SetCities_2_3` 命名集的成員是在 City 2 及 City 3 內的商店。</span><span class="sxs-lookup"><span data-stu-id="ac0da-114">The members of the `SetCities_2_3` named set are the stores within City 2 and City 3.</span></span>  
  
```  
create Session set [Store].[SetCities_2_3] as  
{[Data Stores].[ByLocation].[State].&[CA].&[City 02],  
[Data Stores].[ByLocation].[State].&[NH].&[City 03]}  
```  
  
 <span data-ttu-id="ac0da-115">使用 CREATE SET 陳述式以定義 `SetCities_2_3` 命名集，此命名集就可以在目前的 MDX 工作階段期間內持續使用。</span><span class="sxs-lookup"><span data-stu-id="ac0da-115">By using the CREATE SET statement to define the `SetCities_2_3` named set, this named set remains available for the length of the current MDX session.</span></span> <span data-ttu-id="ac0da-116">以下範例是一個有效查詢，可傳回 City 2 及 City 3 成員，而且可以在建立 `SetCities_2_3` 命名集之後和工作階段關閉之前隨時執行。</span><span class="sxs-lookup"><span data-stu-id="ac0da-116">The following example is a valid query that would return City 2 and City 3 members, and that could be run anytime after you create the `SetCities_2_3` named set and before the session closes.</span></span>  
  
```  
select SetCities_2_3 on 0 from [Store]  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac0da-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac0da-117">See Also</span></span>  
 [<span data-ttu-id="ac0da-118">建立查詢範圍命名集 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="ac0da-118">Creating Query-Scoped Named Sets &#40;MDX&#41;</span></span>](mdx-named-sets-creating-query-scoped-named-sets.md)  
  
  
