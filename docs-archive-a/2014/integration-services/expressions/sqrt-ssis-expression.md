---
title: SQRT (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQRT function
- square root of given expression
ms.assetid: 54a75389-c501-4e22-87b8-905f66d6a3a5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9efa3f8da2e5280692aa65a25610211aba2fa40f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701377"
---
# <a name="sqrt-ssis-expression"></a><span data-ttu-id="7e170-102">SQRT (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="7e170-102">SQRT (SSIS Expression)</span></span>
  <span data-ttu-id="7e170-103">傳回數值運算式的平方根。</span><span class="sxs-lookup"><span data-stu-id="7e170-103">Returns the square root of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e170-104">語法</span><span class="sxs-lookup"><span data-stu-id="7e170-104">Syntax</span></span>  
  
```  
  
SQRT(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="7e170-105">引數</span><span class="sxs-lookup"><span data-stu-id="7e170-105">Arguments</span></span>  
 <span data-ttu-id="7e170-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="7e170-106">*numeric_expression*</span></span>  
 <span data-ttu-id="7e170-107">任何數值資料類型的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="7e170-107">Is a numeric expression of any numeric data type.</span></span> <span data-ttu-id="7e170-108">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="7e170-108">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="7e170-109">結果類型</span><span class="sxs-lookup"><span data-stu-id="7e170-109">Result Types</span></span>  
 <span data-ttu-id="7e170-110">DT_R8</span><span class="sxs-lookup"><span data-stu-id="7e170-110">DT_R8</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e170-111">備註</span><span class="sxs-lookup"><span data-stu-id="7e170-111">Remarks</span></span>  
 <span data-ttu-id="7e170-112">如果引數為 Null，則 SQRT 會傳回 Null 結果。</span><span class="sxs-lookup"><span data-stu-id="7e170-112">SQRT returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="7e170-113">如果引數是負值，SQRT 將會失敗。</span><span class="sxs-lookup"><span data-stu-id="7e170-113">SQRT fails if the argument is a negative value.</span></span>  
  
 <span data-ttu-id="7e170-114">引數會在進行平方根運算之前，轉換成 DT_R8 資料類型。</span><span class="sxs-lookup"><span data-stu-id="7e170-114">The argument is cast to the DT_R8 data type before the square root operation.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="7e170-115">運算式範例</span><span class="sxs-lookup"><span data-stu-id="7e170-115">Expression Examples</span></span>  
 <span data-ttu-id="7e170-116">此範例會傳回數值常值的平方根。</span><span class="sxs-lookup"><span data-stu-id="7e170-116">This example returns the square root of a numeric literal.</span></span> <span data-ttu-id="7e170-117">傳回結果為 12。</span><span class="sxs-lookup"><span data-stu-id="7e170-117">The return result is 12.</span></span>  
  
```  
SQRT(144)  
```  
  
 <span data-ttu-id="7e170-118">此範例會傳回運算式的平方根，亦即 **Value1** 和 **Value2** 資料行中的值相減的結果。</span><span class="sxs-lookup"><span data-stu-id="7e170-118">This example returns the square root of an expression, the result of subtracting values in the **Value1** and **Value2** columns.</span></span>  
  
```  
SQRT(Value1 - Value2)  
```  
  
 <span data-ttu-id="7e170-119">此範例會將 SQUARE 函數套用至兩個變數，然後計算其總和的平方根，藉此傳回直角三角形第三邊的長度。</span><span class="sxs-lookup"><span data-stu-id="7e170-119">This example returns the length of the third side of a right triangle by applying the SQUARE function to two variables and then calculating the square root of their sum.</span></span> <span data-ttu-id="7e170-120">如果 **Side1** 包含 3，而 **Side2** 包含 4，SQRT 函數就會傳回 5。</span><span class="sxs-lookup"><span data-stu-id="7e170-120">If **Side1** contains 3 and **Side2** contains 4, the SQRT function returns 5.</span></span>  
  
```  
SQRT(SQUARE(@Side1) + SQUARE(@Side2))  
```  
  
> [!NOTE]  
>  <span data-ttu-id="7e170-121">在運算式中，變數名稱一律包含 \@ 前置詞。</span><span class="sxs-lookup"><span data-stu-id="7e170-121">In expressions, variable names always include the \@ prefix.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e170-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e170-122">See Also</span></span>  
 [<span data-ttu-id="7e170-123">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="7e170-123">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
