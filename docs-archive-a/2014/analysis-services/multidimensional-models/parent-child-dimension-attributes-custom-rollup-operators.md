---
title: 父子式維度中的自訂 Rollup 運算子 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- child rollup operations
- UnaryOperatorColumn property
- custom rollup operators [Analysis Services]
- unary operators
- parent-child dimensions [Analysis Services]
ms.assetid: a3ddd9fc-5fa3-4227-9322-8c45a5b5c2c3
author: minewiskan
ms.author: owend
ms.openlocfilehash: db12ccc6703ee4863dd3b6bd598d2317b54fce6a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597409"
---
# <a name="custom-rollup-operators-in-parent-child-dimensions"></a><span data-ttu-id="3d519-102">父子式維度中的自訂 ROLLUP 運算子</span><span class="sxs-lookup"><span data-stu-id="3d519-102">Custom Rollup Operators in Parent-Child Dimensions</span></span>
  <span data-ttu-id="3d519-103">自訂積存運算子提供簡易的方法，控制在父子式階層中成員值如何積存到父系值中。</span><span class="sxs-lookup"><span data-stu-id="3d519-103">Custom rollup operators provide a simple way to control how member values are rolled up into parent values in a parent-child hierarchy.</span></span> <span data-ttu-id="3d519-104">在包含父子式關聯性的維度中，您可指定包含一元運算子的資料行，為父屬性的所有非導出成員指定積存。</span><span class="sxs-lookup"><span data-stu-id="3d519-104">In a dimension containing a parent-child relationship, you specify a column that contains unary operators that specify rollup for all noncalculated members of the parent attribute.</span></span> <span data-ttu-id="3d519-105">只要評估父成員的值時，就會將一元運算子套用至成員。</span><span class="sxs-lookup"><span data-stu-id="3d519-105">The unary operator is applied to members whenever the values of the parent members are evaluated.</span></span>  
  
 <span data-ttu-id="3d519-106">儲存一元運算子的資料行是由父屬性之 `UnaryOperatorColumn` 屬性定義的，並會套用到屬性的每個成員。</span><span class="sxs-lookup"><span data-stu-id="3d519-106">The unary operators are stored in column defined by the `UnaryOperatorColumn` property of the parent attribute, and they are applied to each member of the attribute.</span></span> <span data-ttu-id="3d519-107">此屬性指定的資料行可位於維度資料表中，或依維度資料表中的外部索引鍵，位於與維度資料表有關的資料表中。</span><span class="sxs-lookup"><span data-stu-id="3d519-107">The column specified by this property can reside either in the dimension table or in a table related to the dimension table by a foreign key in the dimension table.</span></span>  
  
 <span data-ttu-id="3d519-108">自訂積存運算子提供的功能與自訂成員公式類似，但較為簡化。</span><span class="sxs-lookup"><span data-stu-id="3d519-108">Custom rollup operators provide functionality similar to, but more simplified than, custom member formulas.</span></span> <span data-ttu-id="3d519-109">自訂成員公式使用多維度運算式 (MDX) 運算式來決定如何積存成員。</span><span class="sxs-lookup"><span data-stu-id="3d519-109">A custom member formula uses Multidimensional Expressions (MDX) expressions to determine how the members are rolled up.</span></span> <span data-ttu-id="3d519-110">相反地，自訂積存運算子使用簡單的一元運算子來決定成員的值如何影響父系。</span><span class="sxs-lookup"><span data-stu-id="3d519-110">In contrast, a custom rollup operator uses a simple unary operator to determine how the value of a member affects the parent.</span></span> <span data-ttu-id="3d519-111">在維度中，前一個層級的自訂成員公式會覆寫層級的自訂積存運算子。</span><span class="sxs-lookup"><span data-stu-id="3d519-111">Custom member formulas of the preceding level in a dimension override a level's custom rollup operator.</span></span>  
  
## <a name="custom-rollup-precedence"></a><span data-ttu-id="3d519-112">自訂積存優先順序</span><span class="sxs-lookup"><span data-stu-id="3d519-112">Custom Rollup Precedence</span></span>  
 <span data-ttu-id="3d519-113">在優先順序方面，階層中某個層級之來源屬性的自訂積存運算子，會覆寫前一個層級的自訂成員公式。</span><span class="sxs-lookup"><span data-stu-id="3d519-113">In terms of precedence, the custom rollup operators of the source attribute for a level in a hierarchy override the custom member formulas of the previous level.</span></span> <span data-ttu-id="3d519-114">然而，先前層級的自訂成員公式會覆寫一層級的自訂積存運算子。</span><span class="sxs-lookup"><span data-stu-id="3d519-114">However, the custom member formulas of the preceding level override the custom rollup operators of a level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d519-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d519-115">See Also</span></span>  
 <span data-ttu-id="3d519-116">[定義自訂成員公式](attribute-properties-define-custom-member-formulas.md) </span><span class="sxs-lookup"><span data-stu-id="3d519-116">[Define Custom Member Formulas](attribute-properties-define-custom-member-formulas.md) </span></span>  
 [<span data-ttu-id="3d519-117">父子式維度中的一元運算子</span><span class="sxs-lookup"><span data-stu-id="3d519-117">Unary Operators in Parent-Child Dimensions</span></span>](parent-child-dimension-attributes-unary-operators.md)  
  
  
