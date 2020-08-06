---
title: (模數) (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '% (modulo operator)'
- remainder of division operation
- modulo operator (%)
ms.assetid: e2920821-2f5b-4c76-8db8-8b9eddf4606f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2e23152fca9c9f2c7c3ac11490a56b03d1a1f9dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595201"
---
# <a name="modulo-ssis-expression"></a><span data-ttu-id="6c9a9-102">(模數) (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="6c9a9-102">(Modulo) (SSIS Expression)</span></span>
  <span data-ttu-id="6c9a9-103">提供第一個數值運算式除以第二個數值運算式之後的整數餘數。</span><span class="sxs-lookup"><span data-stu-id="6c9a9-103">Provides the integer remainder after dividing the first numeric expression by the second one.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c9a9-104">語法</span><span class="sxs-lookup"><span data-stu-id="6c9a9-104">Syntax</span></span>  
  
```  
  
dividend % divisor  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="6c9a9-105">引數</span><span class="sxs-lookup"><span data-stu-id="6c9a9-105">Arguments</span></span>  
 <span data-ttu-id="6c9a9-106">*dividend*</span><span class="sxs-lookup"><span data-stu-id="6c9a9-106">*dividend*</span></span>  
 <span data-ttu-id="6c9a9-107">要執行除法的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="6c9a9-107">Is the numeric expression to divide.</span></span> <span data-ttu-id="6c9a9-108">*dividend* 可以是任何有效的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="6c9a9-108">*dividend* can be any valid numeric expression.</span></span> <span data-ttu-id="6c9a9-109">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)</span><span class="sxs-lookup"><span data-stu-id="6c9a9-109">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md)</span></span>  
  
 <span data-ttu-id="6c9a9-110">*divisor*</span><span class="sxs-lookup"><span data-stu-id="6c9a9-110">*divisor*</span></span>  
 <span data-ttu-id="6c9a9-111">要除以被除數的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="6c9a9-111">Is the numeric expression to divide the dividend by.</span></span> <span data-ttu-id="6c9a9-112">*divisor* 可以是任何有效的數值運算式 (零除外)。</span><span class="sxs-lookup"><span data-stu-id="6c9a9-112">*divisor* can be any valid numeric expression except zero.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="6c9a9-113">結果類型</span><span class="sxs-lookup"><span data-stu-id="6c9a9-113">Result Types</span></span>  
 <span data-ttu-id="6c9a9-114">由兩個引數的資料類型決定。</span><span class="sxs-lookup"><span data-stu-id="6c9a9-114">Determined by data types of the two arguments.</span></span> <span data-ttu-id="6c9a9-115">如需相關資訊，請參閱 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="6c9a9-115">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c9a9-116">備註</span><span class="sxs-lookup"><span data-stu-id="6c9a9-116">Remarks</span></span>  
 <span data-ttu-id="6c9a9-117">這兩個運算式都須評估為帶正負號或不帶正負號的整數資料類型。</span><span class="sxs-lookup"><span data-stu-id="6c9a9-117">Both expressions must evaluate to signed or unsigned integer data types.</span></span>  
  
 <span data-ttu-id="6c9a9-118">如果任一個運算元為 Null，則結果為 Null。</span><span class="sxs-lookup"><span data-stu-id="6c9a9-118">If either operand is null, the result is null.</span></span>  
  
 <span data-ttu-id="6c9a9-119">模數零不合法。</span><span class="sxs-lookup"><span data-stu-id="6c9a9-119">Modulo zero is not legal.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="6c9a9-120">運算式範例</span><span class="sxs-lookup"><span data-stu-id="6c9a9-120">Expression Examples</span></span>  
 <span data-ttu-id="6c9a9-121">此範例會計算來自兩個數值常值的模數。</span><span class="sxs-lookup"><span data-stu-id="6c9a9-121">This example computes the modulus from two numeric literals.</span></span> <span data-ttu-id="6c9a9-122">結果為 3。</span><span class="sxs-lookup"><span data-stu-id="6c9a9-122">The result is 3.</span></span>  
  
```  
42 % 13  
```  
  
 <span data-ttu-id="6c9a9-123">此範例會計算來自 **SalesQuota** 資料行和數值常數的模數。</span><span class="sxs-lookup"><span data-stu-id="6c9a9-123">This example computes the modulus from the **SalesQuota** column and a numeric literal.</span></span>  
  
```  
SalesQuota % 12  
```  
  
 <span data-ttu-id="6c9a9-124">此範例會計算來自 **Sales$** 和 **Month**這兩個數值變數的模數。</span><span class="sxs-lookup"><span data-stu-id="6c9a9-124">This example computes the modulus from two numeric variables **Sales$** and **Month**.</span></span> <span data-ttu-id="6c9a9-125">**Sales$** 變數必須加上方括號，因為名稱包含 $ 字元。</span><span class="sxs-lookup"><span data-stu-id="6c9a9-125">The variable **Sales$** must be enclosed in brackets because the name includes the $ character.</span></span> <span data-ttu-id="6c9a9-126">如需詳細資訊，請參閱[識別碼 &#40;SSIS&#41;](identifiers-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="6c9a9-126">For more information, see [Identifiers &#40;SSIS&#41;](identifiers-ssis.md).</span></span>  
  
```  
@[Sales$] % @Month  
```  
  
 <span data-ttu-id="6c9a9-127">此範例使用模數運算子判斷 **Value** 變數的值為偶數或奇數，並使用條件運算子傳回描述結果的字串。</span><span class="sxs-lookup"><span data-stu-id="6c9a9-127">This example uses the modulo operator to determine if the value of the **Value** variable is even or odd, and uses the conditional operator to return a string that describes the result.</span></span> <span data-ttu-id="6c9a9-128">如需詳細資訊，請參閱 [? : &#40;條件式&#41; &#40;SSIS 運算式&#41;](conditional-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="6c9a9-128">For more information, see [? : &#40;Conditional&#41; &#40;SSIS Expression&#41;](conditional-ssis-expression.md).</span></span>  
  
```  
@Value % 2 == 0? "even":"odd"  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c9a9-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c9a9-129">See Also</span></span>  
 <span data-ttu-id="6c9a9-130">[運算子優先順序與關聯性](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="6c9a9-130">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="6c9a9-131">運算子 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="6c9a9-131">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
