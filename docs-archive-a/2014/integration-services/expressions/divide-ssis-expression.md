---
title: 除 (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- / (divide)
- divide operator (/)
ms.assetid: 5bde9223-872d-443e-8a27-57735e1d8f3d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4541cd4601047770d1bf361077b1c474219e8833
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592763"
---
# <a name="divide-ssis-expression"></a><span data-ttu-id="2e424-102">Divide (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="2e424-102">Divide (SSIS Expression)</span></span>
  <span data-ttu-id="2e424-103">將第一個數值運算式除以第二個數值運算式。</span><span class="sxs-lookup"><span data-stu-id="2e424-103">Divides the first numeric expression by the second one.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e424-104">語法</span><span class="sxs-lookup"><span data-stu-id="2e424-104">Syntax</span></span>  
  
```  
  
dividend / divisor  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="2e424-105">引數</span><span class="sxs-lookup"><span data-stu-id="2e424-105">Arguments</span></span>  
 <span data-ttu-id="2e424-106">*dividend*</span><span class="sxs-lookup"><span data-stu-id="2e424-106">*dividend*</span></span>  
 <span data-ttu-id="2e424-107">要執行除法的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="2e424-107">Is the numeric expression to divide.</span></span> <span data-ttu-id="2e424-108">*dividend* 可以是任何有效的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="2e424-108">*dividend* can be any valid numeric expression.</span></span> <span data-ttu-id="2e424-109">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="2e424-109">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="2e424-110">*divisor*</span><span class="sxs-lookup"><span data-stu-id="2e424-110">*divisor*</span></span>  
 <span data-ttu-id="2e424-111">要除以被除數的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="2e424-111">Is the numeric expression to divide the dividend by.</span></span> <span data-ttu-id="2e424-112">*divisor* 可以是任何有效的數值運算式 (零除外)。</span><span class="sxs-lookup"><span data-stu-id="2e424-112">*divisor* can be any valid numeric expression except zero.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="2e424-113">結果類型</span><span class="sxs-lookup"><span data-stu-id="2e424-113">Result Types</span></span>  
 <span data-ttu-id="2e424-114">由兩個引數的資料類型決定。</span><span class="sxs-lookup"><span data-stu-id="2e424-114">Determined by data types of the two arguments.</span></span> <span data-ttu-id="2e424-115">如需相關資訊，請參閱 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="2e424-115">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e424-116">備註</span><span class="sxs-lookup"><span data-stu-id="2e424-116">Remarks</span></span>  
 <span data-ttu-id="2e424-117">如果任一個運算元為 Null，則結果為 Null。</span><span class="sxs-lookup"><span data-stu-id="2e424-117">If either operand is null, the result is null.</span></span>  
  
 <span data-ttu-id="2e424-118">除以零並不合法。</span><span class="sxs-lookup"><span data-stu-id="2e424-118">Dividing by zero is not legal.</span></span> <span data-ttu-id="2e424-119">根據如何評估 *divisor* 子運算式而定，會發生下列其中一項錯誤：</span><span class="sxs-lookup"><span data-stu-id="2e424-119">Depending on how the *divisor* subexpression is evaluated, one of following errors occurs:</span></span>  
  
-   <span data-ttu-id="2e424-120">如果評估為零的 *divisor* 子運算式是常數，則會在設計階段出現錯誤，導致運算式驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="2e424-120">If the *divisor* subexpression that evaluates to zero is a constant, the error appears at design time, causing the expression to fail validation.</span></span>  
  
-   <span data-ttu-id="2e424-121">如果評估為零的 *divisor* 子運算式含有變數，但沒有輸入資料行，則在封裝執行之前發生的運算式所屬元件的前置執行驗證便會失敗。</span><span class="sxs-lookup"><span data-stu-id="2e424-121">If the *divisor* subexpression that evaluates to zero contains variables, but no input columns, the component to which the expression belongs fails the pre-execution validation that occurs before the package runs.</span></span>  
  
-   <span data-ttu-id="2e424-122">如果評估為零的 *divisor* 子運算式含有輸入資料行，則會在執行階段出現錯誤，並根據資料流程元件的錯誤流程規則處理該錯誤。</span><span class="sxs-lookup"><span data-stu-id="2e424-122">If the *divisor* subexpression that evaluates to zero contains input columns, the error appears at run time and is handled according to the error flow rules of the data flow component.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="2e424-123">運算式範例</span><span class="sxs-lookup"><span data-stu-id="2e424-123">Expression Examples</span></span>  
 <span data-ttu-id="2e424-124">此範例會執行兩個數值常值的除法。</span><span class="sxs-lookup"><span data-stu-id="2e424-124">This example divides two numeric literals.</span></span>  
  
```  
25 / 5  
```  
  
 <span data-ttu-id="2e424-125">此範例會將 **ListPrice** 資料行中的值除以 **StandardCost** 資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="2e424-125">This example divides values in the **ListPrice** column by values in the **StandardCost** column.</span></span>  
  
```  
ListPrice / StandardCost  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e424-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e424-126">See Also</span></span>  
 <span data-ttu-id="2e424-127">[運算子優先順序與關聯性](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="2e424-127">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="2e424-128">運算子 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="2e424-128">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
