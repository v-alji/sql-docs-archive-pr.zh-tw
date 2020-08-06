---
title: '&amp;&amp; (邏輯 AND) (SSIS 運算式) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '&& (logical AND)'
- AND, logical AND
- logical AND (&&)
ms.assetid: a8cb3517-d5d1-4861-9f04-905c719185ff
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8d973d7d4e86f88f7ae88c820ed4e4a5c1ce526f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688070"
---
# <a name="ampamp-logical-and-ssis-expression"></a><span data-ttu-id="7ed6a-102">&amp;&amp; (邏輯 AND) (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="7ed6a-102">&amp;&amp; (Logical AND) (SSIS Expression)</span></span>
  <span data-ttu-id="7ed6a-103">執行邏輯 AND 運算。</span><span class="sxs-lookup"><span data-stu-id="7ed6a-103">Performs a logical AND operation.</span></span> <span data-ttu-id="7ed6a-104">如果所有條件均為 TRUE，則運算式的評估結果為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="7ed6a-104">The expression evaluates to TRUE if all conditions are TRUE.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ed6a-105">語法</span><span class="sxs-lookup"><span data-stu-id="7ed6a-105">Syntax</span></span>  
  
```  
  
boolean_expression1 && boolean_expression2  
```  
  
## <a name="arguments"></a><span data-ttu-id="7ed6a-106">引數</span><span class="sxs-lookup"><span data-stu-id="7ed6a-106">Arguments</span></span>  
 <span data-ttu-id="7ed6a-107">*boolean _expression1、boolean_expression2*</span><span class="sxs-lookup"><span data-stu-id="7ed6a-107">*boolean _expression1, boolean_expression2*</span></span>  
 <span data-ttu-id="7ed6a-108">評估為 TRUE、FALSE 或 NULL 的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="7ed6a-108">Is any valid expression that evaluates to TRUE, FALSE, or NULL.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="7ed6a-109">結果類型</span><span class="sxs-lookup"><span data-stu-id="7ed6a-109">Result Types</span></span>  
 <span data-ttu-id="7ed6a-110">DT_BOOL</span><span class="sxs-lookup"><span data-stu-id="7ed6a-110">DT_BOOL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ed6a-111">備註</span><span class="sxs-lookup"><span data-stu-id="7ed6a-111">Remarks</span></span>  
 <span data-ttu-id="7ed6a-112">下表顯示 && 運算子的結果。</span><span class="sxs-lookup"><span data-stu-id="7ed6a-112">The following table shows the result of the && operator.</span></span>  
  
|<span data-ttu-id="7ed6a-113">結果</span><span class="sxs-lookup"><span data-stu-id="7ed6a-113">Result</span></span>|<span data-ttu-id="7ed6a-114">運算是</span><span class="sxs-lookup"><span data-stu-id="7ed6a-114">Expression</span></span>|<span data-ttu-id="7ed6a-115">運算是</span><span class="sxs-lookup"><span data-stu-id="7ed6a-115">Expression</span></span>|  
|------------|----------------|----------------|  
|<span data-ttu-id="7ed6a-116">TRUE</span><span class="sxs-lookup"><span data-stu-id="7ed6a-116">TRUE</span></span>|<span data-ttu-id="7ed6a-117">TRUE</span><span class="sxs-lookup"><span data-stu-id="7ed6a-117">TRUE</span></span>|<span data-ttu-id="7ed6a-118">TRUE</span><span class="sxs-lookup"><span data-stu-id="7ed6a-118">TRUE</span></span>|  
|<span data-ttu-id="7ed6a-119">FALSE</span><span class="sxs-lookup"><span data-stu-id="7ed6a-119">FALSE</span></span>|<span data-ttu-id="7ed6a-120">TRUE</span><span class="sxs-lookup"><span data-stu-id="7ed6a-120">TRUE</span></span>|<span data-ttu-id="7ed6a-121">FALSE</span><span class="sxs-lookup"><span data-stu-id="7ed6a-121">FALSE</span></span>|  
|<span data-ttu-id="7ed6a-122">FALSE</span><span class="sxs-lookup"><span data-stu-id="7ed6a-122">FALSE</span></span>|<span data-ttu-id="7ed6a-123">FALSE</span><span class="sxs-lookup"><span data-stu-id="7ed6a-123">FALSE</span></span>|<span data-ttu-id="7ed6a-124">FALSE</span><span class="sxs-lookup"><span data-stu-id="7ed6a-124">FALSE</span></span>|  
|<span data-ttu-id="7ed6a-125">NULL</span><span class="sxs-lookup"><span data-stu-id="7ed6a-125">NULL</span></span>|<span data-ttu-id="7ed6a-126">NULL</span><span class="sxs-lookup"><span data-stu-id="7ed6a-126">NULL</span></span>|<span data-ttu-id="7ed6a-127">NULL</span><span class="sxs-lookup"><span data-stu-id="7ed6a-127">NULL</span></span>|  
|<span data-ttu-id="7ed6a-128">NULL</span><span class="sxs-lookup"><span data-stu-id="7ed6a-128">NULL</span></span>|<span data-ttu-id="7ed6a-129">NULL</span><span class="sxs-lookup"><span data-stu-id="7ed6a-129">NULL</span></span>|<span data-ttu-id="7ed6a-130">TRUE</span><span class="sxs-lookup"><span data-stu-id="7ed6a-130">TRUE</span></span>|  
|<span data-ttu-id="7ed6a-131">FALSE</span><span class="sxs-lookup"><span data-stu-id="7ed6a-131">FALSE</span></span>|<span data-ttu-id="7ed6a-132">NULL</span><span class="sxs-lookup"><span data-stu-id="7ed6a-132">NULL</span></span>|<span data-ttu-id="7ed6a-133">FALSE</span><span class="sxs-lookup"><span data-stu-id="7ed6a-133">FALSE</span></span>|  
  
## <a name="expression-examples"></a><span data-ttu-id="7ed6a-134">運算式範例</span><span class="sxs-lookup"><span data-stu-id="7ed6a-134">Expression Examples</span></span>  
 <span data-ttu-id="7ed6a-135">此範例使用 **StandardCost** 和 **ListPrice** 資料行。</span><span class="sxs-lookup"><span data-stu-id="7ed6a-135">This example uses the **StandardCost** and the **ListPrice** columns.</span></span> <span data-ttu-id="7ed6a-136">如果 **StandardCost** 資料行的值小於 300，且 **ListPrice** 資料行的值大於 500，則範例的評估結果為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="7ed6a-136">The example evaluates to TRUE if the value of the **StandardCost** column is less than 300 and the **ListPrice** column is greater than 500.</span></span>  
  
```  
StandardCost < 300 && ListPrice > 500  
```  
  
 <span data-ttu-id="7ed6a-137">此範例使用 **SPrice** 和 **LPrice** 變數，而非常值。</span><span class="sxs-lookup"><span data-stu-id="7ed6a-137">This example uses the variables **SPrice** and **LPrice** instead of literals.</span></span>  
  
```  
StandardCost < @SPrice && ListPrice > @LPrice  
```  
  
## <a name="see-also"></a><span data-ttu-id="7ed6a-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ed6a-138">See Also</span></span>  
 <span data-ttu-id="7ed6a-139">[& &#40;位元 AND&#41; &#40;SSIS 運算式&#41;](bitwise-and-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="7ed6a-139">[& &#40;Bitwise AND&#41; &#40;SSIS Expression&#41;](bitwise-and-ssis-expression.md) </span></span>  
 <span data-ttu-id="7ed6a-140">[運算子優先順序與關聯性](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="7ed6a-140">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="7ed6a-141">運算子 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="7ed6a-141">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
