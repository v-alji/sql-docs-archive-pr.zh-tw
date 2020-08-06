---
title: LOG (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- base-10 logarithms
- LOG function
ms.assetid: f7fccace-c178-4e13-bde9-7dc4ef1d98fa
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0de84c1a92f94507bcc69c47cc4d9b6cda50a4f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597961"
---
# <a name="log-ssis-expression"></a><span data-ttu-id="5e2e5-102">LOG (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="5e2e5-102">LOG (SSIS Expression)</span></span>
  <span data-ttu-id="5e2e5-103">傳回數值運算式以 10 為底的對數。</span><span class="sxs-lookup"><span data-stu-id="5e2e5-103">Returns the base-10 logarithm of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e2e5-104">語法</span><span class="sxs-lookup"><span data-stu-id="5e2e5-104">Syntax</span></span>  
  
```  
  
LOG(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="5e2e5-105">引數</span><span class="sxs-lookup"><span data-stu-id="5e2e5-105">Arguments</span></span>  
 <span data-ttu-id="5e2e5-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="5e2e5-106">*numeric_expression*</span></span>  
 <span data-ttu-id="5e2e5-107">是有效的非零或非負數值運算式。</span><span class="sxs-lookup"><span data-stu-id="5e2e5-107">Is a valid nonzero or nonnegative numeric expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="5e2e5-108">結果類型</span><span class="sxs-lookup"><span data-stu-id="5e2e5-108">Result Types</span></span>  
 <span data-ttu-id="5e2e5-109">DT_R8</span><span class="sxs-lookup"><span data-stu-id="5e2e5-109">DT_R8</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e2e5-110">備註</span><span class="sxs-lookup"><span data-stu-id="5e2e5-110">Remarks</span></span>  
 <span data-ttu-id="5e2e5-111">*numeric expression* 會在計算對數之前轉換成 DT_R8 資料類型。</span><span class="sxs-lookup"><span data-stu-id="5e2e5-111">The *numeric expression* is cast to the DT_R8 data type before the logarithm is computed.</span></span> <span data-ttu-id="5e2e5-112">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="5e2e5-112">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="5e2e5-113">如果 *numeric_expression* 評估為零或負值，則傳回結果為 Null。</span><span class="sxs-lookup"><span data-stu-id="5e2e5-113">If *numeric_expression* evaluates to zero or a negative value, the return result is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="5e2e5-114">運算式範例</span><span class="sxs-lookup"><span data-stu-id="5e2e5-114">Expression Examples</span></span>  
 <span data-ttu-id="5e2e5-115">這個範例使用數值常值。</span><span class="sxs-lookup"><span data-stu-id="5e2e5-115">This example uses a numeric literal.</span></span> <span data-ttu-id="5e2e5-116">函數傳回值 1.988291341907488。</span><span class="sxs-lookup"><span data-stu-id="5e2e5-116">The function returns the value 1.988291341907488.</span></span>  
  
```  
LOG(97.34)  
```  
  
 <span data-ttu-id="5e2e5-117">這個範例使用資料行 **Length**。</span><span class="sxs-lookup"><span data-stu-id="5e2e5-117">This example uses the column **Length**.</span></span> <span data-ttu-id="5e2e5-118">如果資料行是 101.24，則函數會傳回 2.005352136486217。</span><span class="sxs-lookup"><span data-stu-id="5e2e5-118">If the column is 101.24, the function returns 2.005352136486217.</span></span>  
  
```  
LOG(Length)   
```  
  
 <span data-ttu-id="5e2e5-119">這個範例使用變數 **Length**。</span><span class="sxs-lookup"><span data-stu-id="5e2e5-119">This example uses the variable **Length**.</span></span> <span data-ttu-id="5e2e5-120">變數必須為數值資料類型，或運算式必須包含數值 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 資料類型的明確轉換。</span><span class="sxs-lookup"><span data-stu-id="5e2e5-120">The variable must have a numeric data type or the expression must include an explicit cast to a numeric [!INCLUDE[ssIS](../../includes/ssis-md.md)] data type.</span></span> <span data-ttu-id="5e2e5-121">如果 **Length** 為 234.567，則函數會傳回 2.370266913465859。</span><span class="sxs-lookup"><span data-stu-id="5e2e5-121">If **Length** is 234.567, the function returns 2.370266913465859.</span></span>  
  
```  
LOG(@Length)   
```  
  
## <a name="see-also"></a><span data-ttu-id="5e2e5-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e2e5-122">See Also</span></span>  
 <span data-ttu-id="5e2e5-123">[EXP &#40;SSIS 運算式&#41;](exp-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="5e2e5-123">[EXP &#40;SSIS Expression&#41;](exp-ssis-expression.md) </span></span>  
 <span data-ttu-id="5e2e5-124">[LN &#40;SSIS 運算式&#41;](ln-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="5e2e5-124">[LN &#40;SSIS Expression&#41;](ln-ssis-expression.md) </span></span>  
 [<span data-ttu-id="5e2e5-125">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="5e2e5-125">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
