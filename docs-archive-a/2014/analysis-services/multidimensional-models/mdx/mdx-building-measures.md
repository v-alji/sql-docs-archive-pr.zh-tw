---
title: 在 MDX 中建立量值 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f0347835-4983-4d26-acbb-6c8fae7992bd
author: minewiskan
ms.author: owend
ms.openlocfilehash: ac49d37f11584bfbc5d372241056da39e7dd8c93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594742"
---
# <a name="building-measures-in-mdx"></a><span data-ttu-id="04f77-102">在 MDX 中建立量值</span><span class="sxs-lookup"><span data-stu-id="04f77-102">Building Measures in MDX</span></span>
  <span data-ttu-id="04f77-103">在多維度運算式 (MDX) 中，量值是具名 DAX 運算式，藉由計算運算式以傳回表格式模型中的值而解析出來。</span><span class="sxs-lookup"><span data-stu-id="04f77-103">In Multidimensional Expressions (MDX), a measure is a named DAX expression that is resolved by calculating the expression to return a value in a Tabular Model.</span></span> <span data-ttu-id="04f77-104">此一定義涵蓋的範圍相當廣泛。</span><span class="sxs-lookup"><span data-stu-id="04f77-104">This innocuous definition covers an incredible amount of ground.</span></span> <span data-ttu-id="04f77-105">在 MDX 查詢中建構和使用量值的能力，提供了許多管理表格式資料的功能。</span><span class="sxs-lookup"><span data-stu-id="04f77-105">The ability to construct and use measures in an MDX query provides a great deal of manipulation capability for tabular data.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="04f77-106">量值只能在表格式模型中定義；如果您的資料庫設定為多維度模式，建立量值將會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="04f77-106">Measures can only be defined in tabular models; if your database is set in multidimensional mode, creating a measure will generate an error</span></span>  
  
 <span data-ttu-id="04f77-107">若要建立定義為 MDX 查詢一部分的量值 (因此其範圍限制在查詢內)，請使用 WITH 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="04f77-107">To create a measure that is defined as part of an MDX query, and therefore whose scope is limited to the query, you use the WITH keyword.</span></span> <span data-ttu-id="04f77-108">然後您就可以在 MDX SELECT 陳述式內使用量值。</span><span class="sxs-lookup"><span data-stu-id="04f77-108">You can then use the measure within an MDX SELECT statement.</span></span> <span data-ttu-id="04f77-109">使用這種方式，可以變更利用 WITH 關鍵字建立的導出成員，而不會影響到 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="04f77-109">Using this approach, the calculated member created by using the WITH keyword can be changed without disturbing the SELECT statement.</span></span> <span data-ttu-id="04f77-110">然而，在 MDX 中參考量值的方式不同於 DAX 運算式；若要參考量值，您要將它命名為 [Measures] 維度的成員，請參閱下列 MDX 範例：</span><span class="sxs-lookup"><span data-stu-id="04f77-110">However, in MDX you reference the measure in a different way than when in DAX expressions; to reference the measure you name it as a member of the [Measures] dimension, see the following MDX example:</span></span>  
  
```  
with measure  'Sales Territory'[Total Sales Amount] = SUM('Internet Sales'[Sales Amount]) + SUM('Reseller Sales'[Sales Amount])  
select measures.[Total Sales Amount] on columns  
     ,NON EMPTY [Date].[Calendar Year].children on rows  
from [Model]  
  
```  
  
 <span data-ttu-id="04f77-111">執行時，它會傳回下列資料：</span><span class="sxs-lookup"><span data-stu-id="04f77-111">It will return the following data when executed:</span></span>  
  
||<span data-ttu-id="04f77-112">Total Sales Amount</span><span class="sxs-lookup"><span data-stu-id="04f77-112">Total Sales Amount</span></span>||  
|-|------------------------|-|  
|<span data-ttu-id="04f77-113">2001</span><span class="sxs-lookup"><span data-stu-id="04f77-113">2001</span></span>|<span data-ttu-id="04f77-114">11331808.96</span><span class="sxs-lookup"><span data-stu-id="04f77-114">11331808.96</span></span>||  
|<span data-ttu-id="04f77-115">2002</span><span class="sxs-lookup"><span data-stu-id="04f77-115">2002</span></span>|<span data-ttu-id="04f77-116">30674773.18</span><span class="sxs-lookup"><span data-stu-id="04f77-116">30674773.18</span></span>||  
|<span data-ttu-id="04f77-117">2003</span><span class="sxs-lookup"><span data-stu-id="04f77-117">2003</span></span>|<span data-ttu-id="04f77-118">41993729.72</span><span class="sxs-lookup"><span data-stu-id="04f77-118">41993729.72</span></span>||  
|<span data-ttu-id="04f77-119">2004</span><span class="sxs-lookup"><span data-stu-id="04f77-119">2004</span></span>|<span data-ttu-id="04f77-120">25808962.34</span><span class="sxs-lookup"><span data-stu-id="04f77-120">25808962.34</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="04f77-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04f77-121">See Also</span></span>  
 <span data-ttu-id="04f77-122">[&#40;MDX&#41;的 CREATE MEMBER 語句](/sql/mdx/mdx-data-definition-create-member) </span><span class="sxs-lookup"><span data-stu-id="04f77-122">[CREATE MEMBER Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member) </span></span>  
 <span data-ttu-id="04f77-123">[Mdx 函數參考 &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx) </span><span class="sxs-lookup"><span data-stu-id="04f77-123">[MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx) </span></span>  
 [<span data-ttu-id="04f77-124">SELECT 陳述式 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="04f77-124">SELECT Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-manipulation-select)  
  
  
