---
title: " (MDX) 建立會話範圍匯出成員 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- CREATE MEMBER statement
- session-scoped calculated members [MDX]
ms.assetid: 2875ed89-2c26-4645-8ed9-8848479d110f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8fe7a9f137d8b74eaa5bad104dbfdb471dd14588
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598618"
---
# <a name="creating-session-scoped-calculated-members-mdx"></a><span data-ttu-id="642c2-102">建立工作階段範圍導出成員 (MDX)</span><span class="sxs-lookup"><span data-stu-id="642c2-102">Creating Session-Scoped Calculated Members (MDX)</span></span>
  <span data-ttu-id="642c2-103">若要建立可在整個多維度運算式 (MDX) 工作階段取得的導出成員，您可以使用 [CREATE MEMBER](/sql/mdx/mdx-data-definition-create-member) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="642c2-103">To create a calculated member that is available throughout a Multidimensional Expressions (MDX) session, you use the [CREATE MEMBER](/sql/mdx/mdx-data-definition-create-member) statement.</span></span> <span data-ttu-id="642c2-104">使用 CREATE MEMBER 陳述式建立的導出成員，直到 MDX 工作階段結束後才會移除。</span><span class="sxs-lookup"><span data-stu-id="642c2-104">A calculated member that is created by using the CREATE MEMBER statement will not be removed until after the MDX session closes.</span></span>  
  
 <span data-ttu-id="642c2-105">如同本主題所討論，CREATE MEMBER 陳述式的語法直接且使用簡單。</span><span class="sxs-lookup"><span data-stu-id="642c2-105">As discussed in this topic, the syntax of the CREATE MEMBER statement is straightforward and easy to use.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="642c2-106">如需建立導出成員的詳細資訊，請參閱[在 MDX 中建立導出成員 &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md)。</span><span class="sxs-lookup"><span data-stu-id="642c2-106">For more information about calculated members, see [Building Calculated Members in MDX &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md).</span></span>  
  
## <a name="create-member-syntax"></a><span data-ttu-id="642c2-107">CREATE MEMBER 語法</span><span class="sxs-lookup"><span data-stu-id="642c2-107">CREATE MEMBER Syntax</span></span>  
 <span data-ttu-id="642c2-108">使用以下語法將 CREATE MEMBER 陳述式加入 MDX 陳述式：</span><span class="sxs-lookup"><span data-stu-id="642c2-108">Use the following syntax to add the CREATE MEMBER statement to the MDX statement:</span></span>  
  
```  
CREATE [SESSION] MEMBER [<cube-name>.]<fully-qualified-member-name> AS <expression> [,<property-definition-list>]  
<cube name> ::= CURRENTCUBE | <Cube Name>  
<property-definition-list> ::= <property-definition>  
  | <property-definition>, <property-definition-list>  
<property-definition> ::= <property-identifier> = <property-value>  
<property-identifier> ::= VISIBLE | SOLVEORDER | SOLVE_ORDER | FORMAT_STRING | NON_EMPTY_BEHAVIOR <ole db member properties>  
```  
  
 <span data-ttu-id="642c2-109">在 CREATE MEMBER 陳述式的語法中， `fully-qualified-member-name` 值是導出成員的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="642c2-109">In the syntax for the CREATE MEMBER statement, the `fully-qualified-member-name` value is the fully qualified name of the calculated member.</span></span> <span data-ttu-id="642c2-110">完整名稱包括與導出成員相關的維度或層級。</span><span class="sxs-lookup"><span data-stu-id="642c2-110">The fully qualified name includes the dimension or level to which the calculated member is associated.</span></span> <span data-ttu-id="642c2-111">`expression` 值會在評估過運算式後，傳回導出成員的值。</span><span class="sxs-lookup"><span data-stu-id="642c2-111">The `expression` value returns the value of the calculated member after the expression value has been evaluated,.</span></span>  
  
## <a name="create-member-example"></a><span data-ttu-id="642c2-112">CREATE MEMBER 範例</span><span class="sxs-lookup"><span data-stu-id="642c2-112">CREATE MEMBER Example</span></span>  
 <span data-ttu-id="642c2-113">以下範例使用 CREATE MEMBER 陳述式來建立 `LastFourStores` 導出成員。</span><span class="sxs-lookup"><span data-stu-id="642c2-113">The following example uses the CREATE MEMBER statement to create the `LastFourStores` calculated member.</span></span> <span data-ttu-id="642c2-114">此導出成員會傳回最後四間商店銷售的單位量總和，而且將可在 Cube 的整個工作階段中使用。</span><span class="sxs-lookup"><span data-stu-id="642c2-114">This calculated member returns the sum of units sold for the last four stores, and will be available throughout the whole session of the cube.</span></span>  
  
```  
Create Session Member [Store].[Measures].LastFourStores as   
sum(([Stores].[ByLocation].Lag(3) :  
[Stores].[ByLocation].NextMember), [Measures].[Units Sold])  
```  
  
## <a name="see-also"></a><span data-ttu-id="642c2-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="642c2-115">See Also</span></span>  
 [<span data-ttu-id="642c2-116">建立查詢範圍導出成員 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="642c2-116">Creating Query-Scoped Calculated Members &#40;MDX&#41;</span></span>](mdx-calculated-members-query-scoped-calculated-members.md)  
  
  
