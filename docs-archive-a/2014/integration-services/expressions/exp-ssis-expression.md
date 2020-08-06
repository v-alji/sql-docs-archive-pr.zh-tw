---
title: EXP (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- exponential functions
- EXP function
ms.assetid: 4cd96d3c-58c9-4a67-a6f6-b72758232912
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 150c92355ab3e0d3a028c98defe2e2fa9a1bf8ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596785"
---
# <a name="exp-ssis-expression"></a><span data-ttu-id="1b754-102">EXP (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="1b754-102">EXP (SSIS Expression)</span></span>
  <span data-ttu-id="1b754-103">傳回做為數值運算式中 e 之基底的指數。</span><span class="sxs-lookup"><span data-stu-id="1b754-103">Returns the exponent to base e of a numeric expression.</span></span> <span data-ttu-id="1b754-104">EXP 函數會補充 LN 函數的動作，有時亦稱為反對數 (Antilogarithm)。</span><span class="sxs-lookup"><span data-stu-id="1b754-104">The EXP function complements the action of the LN function and is sometimes referred to as the antilogarithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b754-105">語法</span><span class="sxs-lookup"><span data-stu-id="1b754-105">Syntax</span></span>  
  
```  
  
EXP(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="1b754-106">引數</span><span class="sxs-lookup"><span data-stu-id="1b754-106">Arguments</span></span>  
 <span data-ttu-id="1b754-107">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="1b754-107">*numeric_expression*</span></span>  
 <span data-ttu-id="1b754-108">有效的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="1b754-108">Is a valid numeric expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="1b754-109">結果類型</span><span class="sxs-lookup"><span data-stu-id="1b754-109">Result Types</span></span>  
 <span data-ttu-id="1b754-110">DT_R8</span><span class="sxs-lookup"><span data-stu-id="1b754-110">DT_R8</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b754-111">備註</span><span class="sxs-lookup"><span data-stu-id="1b754-111">Remarks</span></span>  
 <span data-ttu-id="1b754-112">numeric expression 會在計算指數之前轉換成 DT_R8 資料類型。</span><span class="sxs-lookup"><span data-stu-id="1b754-112">The numeric expression is cast to the DT_R8 data type before the exponent is computed.</span></span> <span data-ttu-id="1b754-113">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="1b754-113">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="1b754-114">傳回結果永遠為正數。</span><span class="sxs-lookup"><span data-stu-id="1b754-114">The return result is always a positive number.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="1b754-115">運算式範例</span><span class="sxs-lookup"><span data-stu-id="1b754-115">Expression Examples</span></span>  
 <span data-ttu-id="1b754-116">這些範例會將 EXP 函數套用至正值、負值和零值。</span><span class="sxs-lookup"><span data-stu-id="1b754-116">These examples apply the EXP function to positive and negative values and to zero.</span></span>  
  
```  
EXP(74)  
```  
  
 <span data-ttu-id="1b754-117">傳回 1.373382979540176E+32。</span><span class="sxs-lookup"><span data-stu-id="1b754-117">Returns 1.373382979540176E+32.</span></span>  
  
```  
EXP(-27)  
```  
  
 <span data-ttu-id="1b754-118">傳回 1.879528816539083E-12。</span><span class="sxs-lookup"><span data-stu-id="1b754-118">Returns 1.879528816539083E-12.</span></span>  
  
```  
EXP(0)  
```  
  
 <span data-ttu-id="1b754-119">傳回 1。</span><span class="sxs-lookup"><span data-stu-id="1b754-119">Returns 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b754-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b754-120">See Also</span></span>  
 <span data-ttu-id="1b754-121">[LOG &#40;SSIS 運算式&#41;](log-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="1b754-121">[LOG &#40;SSIS Expression&#41;](log-ssis-expression.md) </span></span>  
 [<span data-ttu-id="1b754-122">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="1b754-122">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
