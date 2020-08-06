---
title: POWER (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- POWER function
ms.assetid: db48ae65-bfa6-4db1-8d3c-d0d4f8a399bc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e1f5742f482ae52620ec11d95b84cb3d06199fab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596782"
---
# <a name="power-ssis-expression"></a><span data-ttu-id="b5001-102">POWER (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="b5001-102">POWER (SSIS Expression)</span></span>
  <span data-ttu-id="b5001-103">傳回數值運算式的乘冪結果。</span><span class="sxs-lookup"><span data-stu-id="b5001-103">Returns the result of raising a numeric expression to a power.</span></span> <span data-ttu-id="b5001-104">power 參數必須評估為整數。</span><span class="sxs-lookup"><span data-stu-id="b5001-104">The power parameter must evaluate to an integer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5001-105">語法</span><span class="sxs-lookup"><span data-stu-id="b5001-105">Syntax</span></span>  
  
```  
  
POWER(numeric_expression,power)  
```  
  
## <a name="arguments"></a><span data-ttu-id="b5001-106">引數</span><span class="sxs-lookup"><span data-stu-id="b5001-106">Arguments</span></span>  
 <span data-ttu-id="b5001-107">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="b5001-107">*numeric_expression*</span></span>  
 <span data-ttu-id="b5001-108">有效的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="b5001-108">Is a valid numeric expression.</span></span>  
  
 <span data-ttu-id="b5001-109">*power*</span><span class="sxs-lookup"><span data-stu-id="b5001-109">*power*</span></span>  
 <span data-ttu-id="b5001-110">有效的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="b5001-110">Is a valid numeric expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="b5001-111">結果類型</span><span class="sxs-lookup"><span data-stu-id="b5001-111">Result Types</span></span>  
 <span data-ttu-id="b5001-112">DT_R8</span><span class="sxs-lookup"><span data-stu-id="b5001-112">DT_R8</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5001-113">備註</span><span class="sxs-lookup"><span data-stu-id="b5001-113">Remarks</span></span>  
 <span data-ttu-id="b5001-114">*numeric_expression* 和 *power* 引數會在計算 power 之前，轉換成 DT_R8 資料類型。</span><span class="sxs-lookup"><span data-stu-id="b5001-114">The *numeric_expression* and *power* arguments are cast to the DT_R8 data type before the power is computed.</span></span> <span data-ttu-id="b5001-115">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="b5001-115">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="b5001-116">如果 *numeric_expression* 評估為零，且 *power* 為負數，則運算式評估工具會傳回錯誤並將傳回結果設為 Null。</span><span class="sxs-lookup"><span data-stu-id="b5001-116">If *numeric_expression* evaluates to zero and *power* is negative, the expression evaluator returns an error and sets the return result to null.</span></span>  
  
 <span data-ttu-id="b5001-117">如果 *numeric_expression* 或 *power* 評估為未定的結果，則傳回結果為 Null。</span><span class="sxs-lookup"><span data-stu-id="b5001-117">If *numeric_expression* or *power* evaluate to indeterminate results, the return result is null.</span></span>  
  
 <span data-ttu-id="b5001-118">*power* 引數可以是分數。</span><span class="sxs-lookup"><span data-stu-id="b5001-118">The *power* argument can be a fraction.</span></span> <span data-ttu-id="b5001-119">例如，您可以使用數值 0.5 做為 power。</span><span class="sxs-lookup"><span data-stu-id="b5001-119">For example, you can use the value 0.5 as the power.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="b5001-120">運算式範例</span><span class="sxs-lookup"><span data-stu-id="b5001-120">Expression Examples</span></span>  
 <span data-ttu-id="b5001-121">這個範例使用數值常值。</span><span class="sxs-lookup"><span data-stu-id="b5001-121">This example uses a numeric literal.</span></span> <span data-ttu-id="b5001-122">函數會將 4 自乘至 3 的乘冪，並傳回 64。</span><span class="sxs-lookup"><span data-stu-id="b5001-122">The function raises 4 to the power of 3 and returns 64.</span></span>  
  
```  
POWER(4,3)  
```  
  
 <span data-ttu-id="b5001-123">此範例使用 **Length** 資料行和 **DimensionCount** 變數。</span><span class="sxs-lookup"><span data-stu-id="b5001-123">This example uses the **Length** column and the **DimensionCount** variable.</span></span> <span data-ttu-id="b5001-124">如果 **Length** 是 8 且 **DimensionCount** 是 2，則傳回結果為 64。</span><span class="sxs-lookup"><span data-stu-id="b5001-124">If **Length** is 8, and **DimensionCount** is 2, the return result is 64.</span></span>  
  
```  
POWER(Length, @DimensionCount)   
```  
  
## <a name="see-also"></a><span data-ttu-id="b5001-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5001-125">See Also</span></span>  
 [<span data-ttu-id="b5001-126">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="b5001-126">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
