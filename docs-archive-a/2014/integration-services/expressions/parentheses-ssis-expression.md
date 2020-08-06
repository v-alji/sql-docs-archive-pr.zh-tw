---
title: () (括號) (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- () (parentheses operator)
- evaluation order [Integration Services]
- parentheses operator ()
ms.assetid: 931e10eb-1707-4121-b2f1-43565561119f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e390e10e485bd9cc22480300b6a9c33098bda8f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707681"
---
# <a name="-parentheses-ssis-expression"></a><span data-ttu-id="116c8-102">() (括號) (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="116c8-102">() (Parentheses) (SSIS Expression)</span></span>
  <span data-ttu-id="116c8-103">識別運算式的評估順序。</span><span class="sxs-lookup"><span data-stu-id="116c8-103">Identifies the evaluation order of expressions.</span></span> <span data-ttu-id="116c8-104">加上括號的運算式擁有最高的評估優先順序。</span><span class="sxs-lookup"><span data-stu-id="116c8-104">Expressions enclosed in parentheses have the highest evaluation precedence.</span></span> <span data-ttu-id="116c8-105">加上括號的巢狀運算式會以由內向外的順序評估。</span><span class="sxs-lookup"><span data-stu-id="116c8-105">Nested expressions enclosed in parentheses are evaluated in inner-to-outer order.</span></span>  
  
 <span data-ttu-id="116c8-106">括號還可用來讓複雜的運算式更易於了解。</span><span class="sxs-lookup"><span data-stu-id="116c8-106">Parentheses are also used to make complex expressions easier to understand.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="116c8-107">語法</span><span class="sxs-lookup"><span data-stu-id="116c8-107">Syntax</span></span>  
  
```  
  
(expression)  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="116c8-108">引數</span><span class="sxs-lookup"><span data-stu-id="116c8-108">Arguments</span></span>  
 <span data-ttu-id="116c8-109">*expression*</span><span class="sxs-lookup"><span data-stu-id="116c8-109">*expression*</span></span>  
 <span data-ttu-id="116c8-110">為任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="116c8-110">Is any valid expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="116c8-111">結果類型</span><span class="sxs-lookup"><span data-stu-id="116c8-111">Result Types</span></span>  
 <span data-ttu-id="116c8-112">*expression*的資料類型。</span><span class="sxs-lookup"><span data-stu-id="116c8-112">The data type of *expression*.</span></span> <span data-ttu-id="116c8-113">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="116c8-113">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="116c8-114">運算式範例</span><span class="sxs-lookup"><span data-stu-id="116c8-114">Expression Examples</span></span>  
 <span data-ttu-id="116c8-115">此範例示範使用括號修改運算子之優先順序的方式。</span><span class="sxs-lookup"><span data-stu-id="116c8-115">This example shows how the use of parenthesis modifies the precedence of operators.</span></span> <span data-ttu-id="116c8-116">第一個運算式評估為 100，而第二個運算式則評估為 31。</span><span class="sxs-lookup"><span data-stu-id="116c8-116">The first expression evaluates to 100, whereas the second one evaluates to 31.</span></span>  
  
```  
(5 + 5) * (4 + 6)  
5 + 5 * 4 + 6  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="116c8-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="116c8-117">See Also</span></span>  
 <span data-ttu-id="116c8-118">[運算子優先順序與關聯性](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="116c8-118">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="116c8-119">運算子 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="116c8-119">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
