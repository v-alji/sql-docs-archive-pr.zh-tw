---
title: LN (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- LN function
- natural logarithm of expression [Integration Services]
ms.assetid: 55d7b657-b5fd-4753-9c81-54ed7575e720
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4c06d6e246cfa51f8e84eb93ab7eb73eab40c392
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597965"
---
# <a name="ln-ssis-expression"></a><span data-ttu-id="b2d91-102">LN (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="b2d91-102">LN (SSIS Expression)</span></span>
  <span data-ttu-id="b2d91-103">傳回數值運算式的自然對數。</span><span class="sxs-lookup"><span data-stu-id="b2d91-103">Returns the natural logarithm of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2d91-104">語法</span><span class="sxs-lookup"><span data-stu-id="b2d91-104">Syntax</span></span>  
  
```  
  
LN(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="b2d91-105">引數</span><span class="sxs-lookup"><span data-stu-id="b2d91-105">Arguments</span></span>  
 <span data-ttu-id="b2d91-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="b2d91-106">*numeric_expression*</span></span>  
 <span data-ttu-id="b2d91-107">是有效的非零或非負數值運算式。</span><span class="sxs-lookup"><span data-stu-id="b2d91-107">Is a valid non-zero and non-negative numeric expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="b2d91-108">結果類型</span><span class="sxs-lookup"><span data-stu-id="b2d91-108">Result Types</span></span>  
 <span data-ttu-id="b2d91-109">DT_R8</span><span class="sxs-lookup"><span data-stu-id="b2d91-109">DT_R8</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2d91-110">備註</span><span class="sxs-lookup"><span data-stu-id="b2d91-110">Remarks</span></span>  
 <span data-ttu-id="b2d91-111">numeric expression 會在計算對數之前轉換成 DT_R8 資料類型。</span><span class="sxs-lookup"><span data-stu-id="b2d91-111">The numeric expression is cast to the DT_R8 data type before the logarithm is computed.</span></span> <span data-ttu-id="b2d91-112">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="b2d91-112">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="b2d91-113">如果 *numeric_expression* 評估為零或負值，則傳回結果為 Null。</span><span class="sxs-lookup"><span data-stu-id="b2d91-113">If *numeric_expression* evaluates to zero or a negative value, the return result is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="b2d91-114">運算式範例</span><span class="sxs-lookup"><span data-stu-id="b2d91-114">Expression Examples</span></span>  
 <span data-ttu-id="b2d91-115">這個範例使用數值常值。</span><span class="sxs-lookup"><span data-stu-id="b2d91-115">This example uses a numeric literal.</span></span> <span data-ttu-id="b2d91-116">此函數傳回值 3.737766961828337。</span><span class="sxs-lookup"><span data-stu-id="b2d91-116">The function returns the value 3.737766961828337.</span></span>  
  
```  
LN(42)  
```  
  
 <span data-ttu-id="b2d91-117">這個範例使用資料行 **Length**。</span><span class="sxs-lookup"><span data-stu-id="b2d91-117">This example uses the column **Length**.</span></span> <span data-ttu-id="b2d91-118">如果資料行的值是 53.99，則函數會傳回 3.9887988442302。</span><span class="sxs-lookup"><span data-stu-id="b2d91-118">If the column value is 53.99, the function returns 3.9887988442302.</span></span>  
  
```  
LN(Length)   
```  
  
 <span data-ttu-id="b2d91-119">這個範例使用變數 **Length**。</span><span class="sxs-lookup"><span data-stu-id="b2d91-119">This example uses the variable **Length**.</span></span> <span data-ttu-id="b2d91-120">變數必須為數值資料類型，或運算式必須包含數值資料類型的明確轉換。</span><span class="sxs-lookup"><span data-stu-id="b2d91-120">The variable must have a numeric data type or the expression must include an explicit cast to a numeric data type.</span></span> <span data-ttu-id="b2d91-121">如果 **Length** 為 234.567，則函數會傳回 5.45774126708797。</span><span class="sxs-lookup"><span data-stu-id="b2d91-121">If **Length** is 234.567, the function returns 5.45774126708797.</span></span>  
  
```  
LN(@Length)   
```  
  
## <a name="see-also"></a><span data-ttu-id="b2d91-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2d91-122">See Also</span></span>  
 <span data-ttu-id="b2d91-123">[LOG &#40;SSIS 運算式&#41;](log-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="b2d91-123">[LOG &#40;SSIS Expression&#41;](log-ssis-expression.md) </span></span>  
 [<span data-ttu-id="b2d91-124">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="b2d91-124">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
