---
title: '&amp; (位元 AND) (SSIS 運算式) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- AND, bitwise AND
- '& (bitwise AND)'
- bitwise AND (&)
ms.assetid: 06d2958e-66a5-44d8-8bc4-56209ebe1ff2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fbf3c8ffcef079e25c82478947bc3b92a6b4be93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597973"
---
# <a name="amp-bitwise-and-ssis-expression"></a><span data-ttu-id="43703-102">&amp; (位元 AND) (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="43703-102">&amp; (Bitwise AND) (SSIS Expression)</span></span>
  <span data-ttu-id="43703-103">執行兩個整數值的位元 AND 運算。</span><span class="sxs-lookup"><span data-stu-id="43703-103">Performs a bitwise AND operation of two integer values.</span></span> <span data-ttu-id="43703-104">它會比較其第一個運算元的每個位元和其第二個運算元的對應位元。</span><span class="sxs-lookup"><span data-stu-id="43703-104">It compares each bit of its first operand to the corresponding bit of its second operand.</span></span> <span data-ttu-id="43703-105">如果這兩個位元都是 1，則對應的結果位元會設為 1。</span><span class="sxs-lookup"><span data-stu-id="43703-105">If both bits are 1, the corresponding result bit is set to 1.</span></span> <span data-ttu-id="43703-106">否則，對應的結果位元會設為 0。</span><span class="sxs-lookup"><span data-stu-id="43703-106">Otherwise, the corresponding result bit is set to 0.</span></span>  
  
 <span data-ttu-id="43703-107">兩種條件必須都是帶正負號的整數類型，或者兩種條件必須都是不帶正負號的整數類型。</span><span class="sxs-lookup"><span data-stu-id="43703-107">Both conditions must be a signed integer type or both conditions must be an unsigned integer type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43703-108">語法</span><span class="sxs-lookup"><span data-stu-id="43703-108">Syntax</span></span>  
  
```  
  
integer_expression1 & integer_expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="43703-109">引數</span><span class="sxs-lookup"><span data-stu-id="43703-109">Arguments</span></span>  
 <span data-ttu-id="43703-110">*integer_expression1, integer_expression2*</span><span class="sxs-lookup"><span data-stu-id="43703-110">*integer_expression1, integer_expression2*</span></span>  
 <span data-ttu-id="43703-111">已簽署或未簽署整數資料類型的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="43703-111">Is any valid expression of a signed or unsigned integer data type.</span></span> <span data-ttu-id="43703-112">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="43703-112">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="43703-113">結果類型</span><span class="sxs-lookup"><span data-stu-id="43703-113">Result Types</span></span>  
 <span data-ttu-id="43703-114">由兩個引數的資料類型決定。</span><span class="sxs-lookup"><span data-stu-id="43703-114">Determined by data types of the two arguments.</span></span> <span data-ttu-id="43703-115">如需相關資訊，請參閱 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="43703-115">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43703-116">備註</span><span class="sxs-lookup"><span data-stu-id="43703-116">Remarks</span></span>  
 <span data-ttu-id="43703-117">如果任一個條件為 Null，則運算式結果為 Null。</span><span class="sxs-lookup"><span data-stu-id="43703-117">If either condition is null, the expression result is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="43703-118">運算式範例</span><span class="sxs-lookup"><span data-stu-id="43703-118">Expression Examples</span></span>  
 <span data-ttu-id="43703-119">此範例會執行 **NumberA** 和 **NumberB**資料行之間的位元 AND 運算。</span><span class="sxs-lookup"><span data-stu-id="43703-119">This example performs a bitwise AND operation between the columns **NumberA** and **NumberB**.</span></span> <span data-ttu-id="43703-120">**NumberA** 資料行包含 3 (0000011)，且 **NumberB** 資料行包含 7 (00000111)。</span><span class="sxs-lookup"><span data-stu-id="43703-120">**NumberA** contains 3 (0000011) and column **NumberB** contains 7 (00000111).</span></span>  
  
```  
NumberA & NumberB  
```  
  
 <span data-ttu-id="43703-121">運算式評估結果為 3 (00000011)。</span><span class="sxs-lookup"><span data-stu-id="43703-121">The expression evaluates to 3 (00000011).</span></span>  
  
 <span data-ttu-id="43703-122">00000011</span><span class="sxs-lookup"><span data-stu-id="43703-122">00000011</span></span>  
  
 <span data-ttu-id="43703-123">00000111</span><span class="sxs-lookup"><span data-stu-id="43703-123">00000111</span></span>  
  
 ----------\-  
  
 <span data-ttu-id="43703-124">00000011</span><span class="sxs-lookup"><span data-stu-id="43703-124">00000011</span></span>  
  
 <span data-ttu-id="43703-125">此範例會執行 **ReorderPoint** 和 **SafetyStockLevel** 資料行之間的位元 AND 運算。</span><span class="sxs-lookup"><span data-stu-id="43703-125">This example performs a bitwise AND operation between the **ReorderPoint** and **SafetyStockLevel** columns.</span></span>  
  
```  
ReorderPoint & SafetyStockLevel  
```  
  
 <span data-ttu-id="43703-126">如果 **ReorderPoint** 為 10，且 **SafetyStockLevel** 為 8，則運算式評估結果為 8 (00001000)。</span><span class="sxs-lookup"><span data-stu-id="43703-126">If **ReorderPoint** is 10 and **SafetyStockLevel** is 8, the expression evaluates to 8 (00001000).</span></span>  
  
 <span data-ttu-id="43703-127">00001010</span><span class="sxs-lookup"><span data-stu-id="43703-127">00001010</span></span>  
  
 <span data-ttu-id="43703-128">00001000</span><span class="sxs-lookup"><span data-stu-id="43703-128">00001000</span></span>  
  
 ----------\-  
  
 <span data-ttu-id="43703-129">00001000</span><span class="sxs-lookup"><span data-stu-id="43703-129">00001000</span></span>  
  
 <span data-ttu-id="43703-130">此範例執行兩個整數之間的位元 AND 運算。</span><span class="sxs-lookup"><span data-stu-id="43703-130">This example performs a bitwise AND operation between two integers.</span></span>  
  
```  
3 & 5   
```  
  
 <span data-ttu-id="43703-131">運算式評估結果為 1 (00000001)。</span><span class="sxs-lookup"><span data-stu-id="43703-131">The expression evaluates to 1(00000001).</span></span>  
  
 <span data-ttu-id="43703-132">00000011</span><span class="sxs-lookup"><span data-stu-id="43703-132">00000011</span></span>  
  
 <span data-ttu-id="43703-133">00000101</span><span class="sxs-lookup"><span data-stu-id="43703-133">00000101</span></span>  
  
 ----------\-  
  
 <span data-ttu-id="43703-134">00000001</span><span class="sxs-lookup"><span data-stu-id="43703-134">00000001</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43703-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43703-135">See Also</span></span>  
 <span data-ttu-id="43703-136">[&& &#40;邏輯 AND&#41; &#40;SSIS 運算式&#41;](logical-and-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="43703-136">[&& &#40;Logical AND&#41; &#40;SSIS Expression&#41;](logical-and-ssis-expression.md) </span></span>  
 <span data-ttu-id="43703-137">[運算子優先順序與關聯性](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="43703-137">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="43703-138">運算子 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="43703-138">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
