---
title: ^ (位元排除 OR) (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- ^ (bitwise exclusive OR operator)
- bitwise exclusive OR (^)
ms.assetid: 6ac53cab-29c4-4835-9f87-371b058b2f38
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d86c3d810e9e5572af93c97f82c2275db2c979b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597974"
---
# <a name="-bitwise-exclusive-or-ssis-expression"></a><span data-ttu-id="bba30-102">^ (位元排除 OR) (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="bba30-102">^ (Bitwise Exclusive OR) (SSIS Expression)</span></span>
  <span data-ttu-id="bba30-103">執行兩個整數值的位元排除 OR 運算。</span><span class="sxs-lookup"><span data-stu-id="bba30-103">Performs a bitwise exclusive OR operation of two integer values.</span></span> <span data-ttu-id="bba30-104">它會比較其第一個運算元的每個位元和其第二個運算元的對應位元。</span><span class="sxs-lookup"><span data-stu-id="bba30-104">It compares each bit of its first operand to the corresponding bit of its second operand.</span></span> <span data-ttu-id="bba30-105">如果一個位元為 0 而另一個位元為 1，則對應的結果位元會設為 1。</span><span class="sxs-lookup"><span data-stu-id="bba30-105">If one bit is 0 and the other bit is 1, the corresponding result bit is set to 1.</span></span> <span data-ttu-id="bba30-106">如果這兩個位元都是 0 或都是 1，則對應的結果位元會設為 0。</span><span class="sxs-lookup"><span data-stu-id="bba30-106">If both bits are 0 or both bits are 1, the corresponding result bit is set to 0.</span></span>  
  
 <span data-ttu-id="bba30-107">兩個條件都必須是簽署的整數資料類型，或者都必須是未簽署的整數資料類型。</span><span class="sxs-lookup"><span data-stu-id="bba30-107">Both conditions must be a signed integer data type or both conditions must be an unsigned integer data type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bba30-108">語法</span><span class="sxs-lookup"><span data-stu-id="bba30-108">Syntax</span></span>  
  
```  
  
integer_expression1 ^ integer_expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="bba30-109">引數</span><span class="sxs-lookup"><span data-stu-id="bba30-109">Arguments</span></span>  
 <span data-ttu-id="bba30-110">*integer_expression1, integer_expression2*</span><span class="sxs-lookup"><span data-stu-id="bba30-110">*integer_expression1, integer_expression2*</span></span>  
 <span data-ttu-id="bba30-111">已簽署或未簽署整數資料類型的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="bba30-111">Is any valid expression of a signed or unsigned integer data type.</span></span> <span data-ttu-id="bba30-112">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="bba30-112">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="bba30-113">結果類型</span><span class="sxs-lookup"><span data-stu-id="bba30-113">Result Types</span></span>  
 <span data-ttu-id="bba30-114">由兩個引數的資料類型決定。</span><span class="sxs-lookup"><span data-stu-id="bba30-114">Determined by data types of the two arguments.</span></span> <span data-ttu-id="bba30-115">如需相關資訊，請參閱 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="bba30-115">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bba30-116">備註</span><span class="sxs-lookup"><span data-stu-id="bba30-116">Remarks</span></span>  
 <span data-ttu-id="bba30-117">如果任一個條件為 Null，則運算式結果為 Null。</span><span class="sxs-lookup"><span data-stu-id="bba30-117">If either condition is null, the expression result is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="bba30-118">運算式範例</span><span class="sxs-lookup"><span data-stu-id="bba30-118">Expression Examples</span></span>  
 <span data-ttu-id="bba30-119">此範例會在 **NumberA** 和 **NumberB**變數之間執行位元排除 OR 運算。</span><span class="sxs-lookup"><span data-stu-id="bba30-119">This example performs a bitwise exclusive OR operation between variables **NumberA** and **NumberB**.</span></span> <span data-ttu-id="bba30-120">**NumberA** 包含 3 (00000011) 且 **NumberB** 包含 7 (00000111)。</span><span class="sxs-lookup"><span data-stu-id="bba30-120">**NumberA** contains 3 (00000011) and **NumberB** contains 7 (00000111).</span></span>  
  
```  
@NumberA ^ @NumberB  
```  
  
 <span data-ttu-id="bba30-121">運算式評估為 4 (00000100)。</span><span class="sxs-lookup"><span data-stu-id="bba30-121">The expression evaluates to 4 (00000100).</span></span>  
  
 <span data-ttu-id="bba30-122">00000011</span><span class="sxs-lookup"><span data-stu-id="bba30-122">00000011</span></span>  
  
 <span data-ttu-id="bba30-123">00000111</span><span class="sxs-lookup"><span data-stu-id="bba30-123">00000111</span></span>  
  
 ----------\-  
  
 <span data-ttu-id="bba30-124">00000100</span><span class="sxs-lookup"><span data-stu-id="bba30-124">00000100</span></span>  
  
 <span data-ttu-id="bba30-125">此範例會在 **ReorderPoint** 與 **SafetyStockLevel** 資料行之間執行位元排除 OR 運算。</span><span class="sxs-lookup"><span data-stu-id="bba30-125">This example performs a bitwise exclusive OR operation between the **ReorderPoint** and **SafetyStockLevel** columns.</span></span>  
  
```  
ReorderPoint ^ SafetyStockLevel  
```  
  
 <span data-ttu-id="bba30-126">如果 **ReorderPoint** 為 10，且 **SafetyStockLevel** 為 8，則運算式評估結果為 2 (00000010)。</span><span class="sxs-lookup"><span data-stu-id="bba30-126">If **ReorderPoint** is 10 and **SafetyStockLevel** is 8, the expression evaluates to 2 (00000010).</span></span>  
  
 <span data-ttu-id="bba30-127">00001010</span><span class="sxs-lookup"><span data-stu-id="bba30-127">00001010</span></span>  
  
 <span data-ttu-id="bba30-128">00001000</span><span class="sxs-lookup"><span data-stu-id="bba30-128">00001000</span></span>  
  
 ----------\-  
  
 <span data-ttu-id="bba30-129">00000010</span><span class="sxs-lookup"><span data-stu-id="bba30-129">00000010</span></span>  
  
 <span data-ttu-id="bba30-130">此範例會在兩個整數之間執行位元排除 OR 運算。</span><span class="sxs-lookup"><span data-stu-id="bba30-130">This example performs a bitwise exclusive OR operation between two integers.</span></span>  
  
```  
3 ^ 5   
```  
  
 <span data-ttu-id="bba30-131">運算式評估為 6 (00000110)。</span><span class="sxs-lookup"><span data-stu-id="bba30-131">The expression evaluates to 6 (00000110).</span></span>  
  
 <span data-ttu-id="bba30-132">00000011</span><span class="sxs-lookup"><span data-stu-id="bba30-132">00000011</span></span>  
  
 <span data-ttu-id="bba30-133">00000101</span><span class="sxs-lookup"><span data-stu-id="bba30-133">00000101</span></span>  
  
 ----------\-  
  
 <span data-ttu-id="bba30-134">00000110</span><span class="sxs-lookup"><span data-stu-id="bba30-134">00000110</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bba30-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bba30-135">See Also</span></span>  
 <span data-ttu-id="bba30-136">[&#124;&#124; &#40;邏輯 OR&#41; &#40;SSIS 運算式&#41;](logical-or-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="bba30-136">[&#124;&#124; &#40;Logical OR&#41; &#40;SSIS Expression&#41;](logical-or-ssis-expression.md) </span></span>  
 <span data-ttu-id="bba30-137">[&#124; &#40;位元包含 OR&#41; &#40;SSIS 運算式&#41;](bitwise-inclusive-or-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="bba30-137">[&#124; &#40;Bitwise Inclusive OR&#41; &#40;SSIS Expression&#41;](bitwise-inclusive-or-ssis-expression.md) </span></span>  
 <span data-ttu-id="bba30-138">[運算子優先順序與關聯性](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="bba30-138">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="bba30-139">運算子 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="bba30-139">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
