---
title: 運算子優先順序與關聯性 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- associativity [Integration Services]
- precedence [Integration Services]
ms.assetid: 5094164f-dabc-45b5-b611-384feb2b3fe3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 90ec23f9e961cbe4df291b9670c09e51d5d8704b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703206"
---
# <a name="operator-precedence-and-associativity"></a><span data-ttu-id="2e982-102">運算子優先順序與關聯性</span><span class="sxs-lookup"><span data-stu-id="2e982-102">Operator Precedence and Associativity</span></span>
  <span data-ttu-id="2e982-103">在運算式評估工具支援的一組運算子中，每個運算子在優先順序階層中都有指定的優先順序，且包含評估的方向。</span><span class="sxs-lookup"><span data-stu-id="2e982-103">Each operator in the set of operators that the expression evaluator supports has a designated precedence in the precedence hierarchy and includes a direction in which it is evaluated.</span></span> <span data-ttu-id="2e982-104">運算子的評估方向即為運算子關聯性。</span><span class="sxs-lookup"><span data-stu-id="2e982-104">The direction of evaluation for an operator is operator associativity.</span></span> <span data-ttu-id="2e982-105">具有較高優先順序的運算子會在低優先順序的運算子之前評估。</span><span class="sxs-lookup"><span data-stu-id="2e982-105">Operators with higher precedence are evaluated before operators with lower precedence.</span></span> <span data-ttu-id="2e982-106">如果複雜的運算式有多個運算子時，運算子優先順序即決定運算子執行的順序。</span><span class="sxs-lookup"><span data-stu-id="2e982-106">If a complex expression has multiple operators, operator precedence determines the order in which the operations are performed.</span></span> <span data-ttu-id="2e982-107">執行的順序對結果值會有很大的影響。</span><span class="sxs-lookup"><span data-stu-id="2e982-107">The order of execution can significantly affect the resulting value.</span></span> <span data-ttu-id="2e982-108">某些運算子的優先順序相同。</span><span class="sxs-lookup"><span data-stu-id="2e982-108">Some operators have equal precedence.</span></span> <span data-ttu-id="2e982-109">如果運算式含有多個優先順序相同的運算子，則會按照左到右或右到左的方向評估運算子。</span><span class="sxs-lookup"><span data-stu-id="2e982-109">If an expression contains multiple operators of equal precedence, the operators are evaluated directionally, from left to right or right to left.</span></span>  
  
 <span data-ttu-id="2e982-110">下表按高到低的順序列出運算子的優先順序。</span><span class="sxs-lookup"><span data-stu-id="2e982-110">The following table lists the precedence of operators in order of high to low.</span></span> <span data-ttu-id="2e982-111">同層級的運算子擁有相同的優先順序。</span><span class="sxs-lookup"><span data-stu-id="2e982-111">Operators at the same level have equal precedence.</span></span>  
  
|<span data-ttu-id="2e982-112">運算子符號</span><span class="sxs-lookup"><span data-stu-id="2e982-112">Operator symbol</span></span>|<span data-ttu-id="2e982-113">運算類型</span><span class="sxs-lookup"><span data-stu-id="2e982-113">Type of Operation</span></span>|<span data-ttu-id="2e982-114">關聯性</span><span class="sxs-lookup"><span data-stu-id="2e982-114">Associativity</span></span>|  
|---------------------|-----------------------|-------------------|  
|<span data-ttu-id="2e982-115">( )</span><span class="sxs-lookup"><span data-stu-id="2e982-115">( )</span></span>|<span data-ttu-id="2e982-116">運算是</span><span class="sxs-lookup"><span data-stu-id="2e982-116">Expression</span></span>|<span data-ttu-id="2e982-117">由左至右</span><span class="sxs-lookup"><span data-stu-id="2e982-117">Left to right</span></span>|  
|<span data-ttu-id="2e982-118">-、!、~</span><span class="sxs-lookup"><span data-stu-id="2e982-118">-, !, ~</span></span>|<span data-ttu-id="2e982-119">一元 (Unary)</span><span class="sxs-lookup"><span data-stu-id="2e982-119">Unary</span></span>|<span data-ttu-id="2e982-120">由右至左</span><span class="sxs-lookup"><span data-stu-id="2e982-120">Right to left</span></span>|  
|<span data-ttu-id="2e982-121">轉換</span><span class="sxs-lookup"><span data-stu-id="2e982-121">casts</span></span>|<span data-ttu-id="2e982-122">一元 (Unary)</span><span class="sxs-lookup"><span data-stu-id="2e982-122">Unary</span></span>|<span data-ttu-id="2e982-123">由右至左</span><span class="sxs-lookup"><span data-stu-id="2e982-123">Right to left</span></span>|  
|<span data-ttu-id="2e982-124">\*, / ,%</span><span class="sxs-lookup"><span data-stu-id="2e982-124">\*, / ,%</span></span>|<span data-ttu-id="2e982-125">乘法</span><span class="sxs-lookup"><span data-stu-id="2e982-125">Multiplicative</span></span>|<span data-ttu-id="2e982-126">由左至右</span><span class="sxs-lookup"><span data-stu-id="2e982-126">Left to right</span></span>|  
|<span data-ttu-id="2e982-127">+、 -</span><span class="sxs-lookup"><span data-stu-id="2e982-127">+, -</span></span>|<span data-ttu-id="2e982-128">加法</span><span class="sxs-lookup"><span data-stu-id="2e982-128">Additive</span></span>|<span data-ttu-id="2e982-129">由左至右</span><span class="sxs-lookup"><span data-stu-id="2e982-129">Left to right</span></span>|  
|<span data-ttu-id="2e982-130">\<, >, \<=, >=</span><span class="sxs-lookup"><span data-stu-id="2e982-130">\<, >, \<=, >=</span></span>|<span data-ttu-id="2e982-131">關聯式</span><span class="sxs-lookup"><span data-stu-id="2e982-131">Relational</span></span>|<span data-ttu-id="2e982-132">由左至右</span><span class="sxs-lookup"><span data-stu-id="2e982-132">Left to right</span></span>|  
|<span data-ttu-id="2e982-133">==, !=</span><span class="sxs-lookup"><span data-stu-id="2e982-133">==, !=</span></span>|<span data-ttu-id="2e982-134">等式</span><span class="sxs-lookup"><span data-stu-id="2e982-134">Equality</span></span>|<span data-ttu-id="2e982-135">由左至右</span><span class="sxs-lookup"><span data-stu-id="2e982-135">Left to right</span></span>|  
|&|<span data-ttu-id="2e982-136">位元 AND</span><span class="sxs-lookup"><span data-stu-id="2e982-136">Bitwise AND</span></span>|<span data-ttu-id="2e982-137">由左至右</span><span class="sxs-lookup"><span data-stu-id="2e982-137">Left to right</span></span>|  
|^|<span data-ttu-id="2e982-138">位元排除 OR</span><span class="sxs-lookup"><span data-stu-id="2e982-138">Bitwise exclusive OR</span></span>|<span data-ttu-id="2e982-139">由左至右</span><span class="sxs-lookup"><span data-stu-id="2e982-139">Left to right</span></span>|  
|<span data-ttu-id="2e982-140">&#124;</span><span class="sxs-lookup"><span data-stu-id="2e982-140">&#124;</span></span>|<span data-ttu-id="2e982-141">位元包含 OR</span><span class="sxs-lookup"><span data-stu-id="2e982-141">Bitwise inclusive OR</span></span>|<span data-ttu-id="2e982-142">由左至右</span><span class="sxs-lookup"><span data-stu-id="2e982-142">Left to right</span></span>|  
|&&|<span data-ttu-id="2e982-143">邏輯 AND</span><span class="sxs-lookup"><span data-stu-id="2e982-143">Logical AND</span></span>|<span data-ttu-id="2e982-144">由左至右</span><span class="sxs-lookup"><span data-stu-id="2e982-144">Left to right</span></span>|  
|<span data-ttu-id="2e982-145">&#124;&#124;</span><span class="sxs-lookup"><span data-stu-id="2e982-145">&#124;&#124;</span></span>|<span data-ttu-id="2e982-146">邏輯 OR</span><span class="sxs-lookup"><span data-stu-id="2e982-146">Logical OR</span></span>|<span data-ttu-id="2e982-147">由左至右</span><span class="sxs-lookup"><span data-stu-id="2e982-147">Left to right</span></span>|  
|<span data-ttu-id="2e982-148">?</span><span class="sxs-lookup"><span data-stu-id="2e982-148">?</span></span> <span data-ttu-id="2e982-149">所解碼的字元：</span><span class="sxs-lookup"><span data-stu-id="2e982-149">:</span></span>|<span data-ttu-id="2e982-150">條件運算式</span><span class="sxs-lookup"><span data-stu-id="2e982-150">Conditional expression</span></span>|<span data-ttu-id="2e982-151">由右至左</span><span class="sxs-lookup"><span data-stu-id="2e982-151">Right to left</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2e982-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e982-152">See Also</span></span>  
 [<span data-ttu-id="2e982-153">運算子 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="2e982-153">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
