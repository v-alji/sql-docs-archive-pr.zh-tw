---
title: '|| (邏輯 OR) (SSIS 運算式) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- OR operator
- logical OR (||)
- '|| (logical OR)'
ms.assetid: a3c07c09-f121-4187-9617-b01adcf843c4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 72d4a1c7b54856675f0faa7f5f58452cb8bca450
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688073"
---
# <a name="-logical-or-ssis-expression"></a><span data-ttu-id="74e0e-102">|| (邏輯 OR) (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="74e0e-102">|| (Logical OR) (SSIS Expression)</span></span>
  <span data-ttu-id="74e0e-103">執行邏輯 OR 運算。</span><span class="sxs-lookup"><span data-stu-id="74e0e-103">Performs a logical OR operation.</span></span> <span data-ttu-id="74e0e-104">如果其中一項或兩項條件均為 TRUE，則運算式的評估結果為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="74e0e-104">The expression evaluates to TRUE if one or both conditions are TRUE.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74e0e-105">語法</span><span class="sxs-lookup"><span data-stu-id="74e0e-105">Syntax</span></span>  
  
```  
  
boolean_expression1 || boolean_expression2  
```  
  
## <a name="arguments"></a><span data-ttu-id="74e0e-106">引數</span><span class="sxs-lookup"><span data-stu-id="74e0e-106">Arguments</span></span>  
 <span data-ttu-id="74e0e-107">*boolean_expression1、boolean_expression2*</span><span class="sxs-lookup"><span data-stu-id="74e0e-107">*boolean_expression1, boolean_expression2*</span></span>  
 <span data-ttu-id="74e0e-108">評估為 TRUE、FALSE 或 NULL 的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="74e0e-108">Is any valid expression that evaluates to TRUE, FALSE, or NULL.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="74e0e-109">結果類型</span><span class="sxs-lookup"><span data-stu-id="74e0e-109">Result Types</span></span>  
 <span data-ttu-id="74e0e-110">DT_BOOL</span><span class="sxs-lookup"><span data-stu-id="74e0e-110">DT_BOOL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74e0e-111">備註</span><span class="sxs-lookup"><span data-stu-id="74e0e-111">Remarks</span></span>  
 <span data-ttu-id="74e0e-112">下表顯示 || 運算子的結果。</span><span class="sxs-lookup"><span data-stu-id="74e0e-112">The following table shows the result of the || operator.</span></span>  
  
|<span data-ttu-id="74e0e-113">結果</span><span class="sxs-lookup"><span data-stu-id="74e0e-113">Result</span></span>|<span data-ttu-id="74e0e-114">運算是</span><span class="sxs-lookup"><span data-stu-id="74e0e-114">Expression</span></span>|<span data-ttu-id="74e0e-115">運算是</span><span class="sxs-lookup"><span data-stu-id="74e0e-115">Expression</span></span>|  
|------------|----------------|----------------|  
|<span data-ttu-id="74e0e-116">TRUE</span><span class="sxs-lookup"><span data-stu-id="74e0e-116">TRUE</span></span>|<span data-ttu-id="74e0e-117">TRUE</span><span class="sxs-lookup"><span data-stu-id="74e0e-117">TRUE</span></span>|<span data-ttu-id="74e0e-118">TRUE</span><span class="sxs-lookup"><span data-stu-id="74e0e-118">TRUE</span></span>|  
|<span data-ttu-id="74e0e-119">TRUE</span><span class="sxs-lookup"><span data-stu-id="74e0e-119">TRUE</span></span>|<span data-ttu-id="74e0e-120">TRUE</span><span class="sxs-lookup"><span data-stu-id="74e0e-120">TRUE</span></span>|<span data-ttu-id="74e0e-121">FALSE</span><span class="sxs-lookup"><span data-stu-id="74e0e-121">FALSE</span></span>|  
|<span data-ttu-id="74e0e-122">FALSE</span><span class="sxs-lookup"><span data-stu-id="74e0e-122">FALSE</span></span>|<span data-ttu-id="74e0e-123">FALSE</span><span class="sxs-lookup"><span data-stu-id="74e0e-123">FALSE</span></span>|<span data-ttu-id="74e0e-124">FALSE</span><span class="sxs-lookup"><span data-stu-id="74e0e-124">FALSE</span></span>|  
|<span data-ttu-id="74e0e-125">NULL</span><span class="sxs-lookup"><span data-stu-id="74e0e-125">NULL</span></span>|<span data-ttu-id="74e0e-126">NULL</span><span class="sxs-lookup"><span data-stu-id="74e0e-126">NULL</span></span>|<span data-ttu-id="74e0e-127">NULL</span><span class="sxs-lookup"><span data-stu-id="74e0e-127">NULL</span></span>|  
|<span data-ttu-id="74e0e-128">TRUE</span><span class="sxs-lookup"><span data-stu-id="74e0e-128">TRUE</span></span>|<span data-ttu-id="74e0e-129">NULL</span><span class="sxs-lookup"><span data-stu-id="74e0e-129">NULL</span></span>|<span data-ttu-id="74e0e-130">TRUE</span><span class="sxs-lookup"><span data-stu-id="74e0e-130">TRUE</span></span>|  
|<span data-ttu-id="74e0e-131">NULL</span><span class="sxs-lookup"><span data-stu-id="74e0e-131">NULL</span></span>|<span data-ttu-id="74e0e-132">NULL</span><span class="sxs-lookup"><span data-stu-id="74e0e-132">NULL</span></span>|<span data-ttu-id="74e0e-133">FALSE</span><span class="sxs-lookup"><span data-stu-id="74e0e-133">FALSE</span></span>|  
  
## <a name="ssis-expression-examples"></a><span data-ttu-id="74e0e-134">SSIS 運算式範例</span><span class="sxs-lookup"><span data-stu-id="74e0e-134">SSIS Expression Examples</span></span>  
 <span data-ttu-id="74e0e-135">此範例使用 **StandardCost** 和 **ListPrice** 資料行。</span><span class="sxs-lookup"><span data-stu-id="74e0e-135">This example uses the **StandardCost** and **ListPrice** columns.</span></span> <span data-ttu-id="74e0e-136">如果 **StandardCost** 資料行的值小於 300，或 **ListPrice** 資料行的值大於 500，則範例的評估結果為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="74e0e-136">The example evaluates to TRUE if the value of the **StandardCost** column is less than 300 or the **ListPrice** column is greater than 500.</span></span>  
  
```  
StandardCost < 300 || ListPrice > 500  
```  
  
 <span data-ttu-id="74e0e-137">此範例使用 **SPrice** 和 **LPrice** 變數，而非數值常值。</span><span class="sxs-lookup"><span data-stu-id="74e0e-137">This example uses the variables **SPrice** and **LPrice** instead of numeric literals.</span></span>  
  
```  
StandardCost < @SPrice || ListPrice > @LPrice  
```  
  
## <a name="see-also"></a><span data-ttu-id="74e0e-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74e0e-138">See Also</span></span>  
 <span data-ttu-id="74e0e-139">[&#124; &#40;位元包含 OR&#41; &#40;SSIS 運算式&#41;](bitwise-inclusive-or-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="74e0e-139">[&#124; &#40;Bitwise Inclusive OR&#41; &#40;SSIS Expression&#41;](bitwise-inclusive-or-ssis-expression.md) </span></span>  
 <span data-ttu-id="74e0e-140">[^ &#40;位元排除 OR&#41; &#40;SSIS 運算式&#41;](bitwise-exclusive-or-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="74e0e-140">[^ &#40;Bitwise Exclusive OR&#41; &#40;SSIS Expression&#41;](bitwise-exclusive-or-ssis-expression.md) </span></span>  
 <span data-ttu-id="74e0e-141">[運算子優先順序與關聯性](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="74e0e-141">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="74e0e-142">運算子 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="74e0e-142">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
