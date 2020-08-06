---
title: SQUARE (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQUARE
- square values
ms.assetid: cecf1bb2-3d55-40a6-9688-ed67bcc150b4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 09955e708aae707a88aa7821d2a72651a3a44d59
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701371"
---
# <a name="square-ssis-expression"></a><span data-ttu-id="22111-102">SQUARE (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="22111-102">SQUARE (SSIS Expression)</span></span>
  <span data-ttu-id="22111-103">傳回數值運算式的平方。</span><span class="sxs-lookup"><span data-stu-id="22111-103">Returns the square of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22111-104">語法</span><span class="sxs-lookup"><span data-stu-id="22111-104">Syntax</span></span>  
  
```  
  
SQUARE(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="22111-105">引數</span><span class="sxs-lookup"><span data-stu-id="22111-105">Arguments</span></span>  
 <span data-ttu-id="22111-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="22111-106">*numeric_expression*</span></span>  
 <span data-ttu-id="22111-107">任何數值資料類型的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="22111-107">Is a numeric expression of any numeric data type.</span></span> <span data-ttu-id="22111-108">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="22111-108">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="22111-109">結果類型</span><span class="sxs-lookup"><span data-stu-id="22111-109">Result Types</span></span>  
 <span data-ttu-id="22111-110">DT_R8</span><span class="sxs-lookup"><span data-stu-id="22111-110">DT_R8</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22111-111">備註</span><span class="sxs-lookup"><span data-stu-id="22111-111">Remarks</span></span>  
 <span data-ttu-id="22111-112">如果引數為 Null，則 SQUARE 會傳回 Null 結果。</span><span class="sxs-lookup"><span data-stu-id="22111-112">SQUARE returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="22111-113">引數會在進行平方運算之前，轉換成 DT_R8 資料類型。</span><span class="sxs-lookup"><span data-stu-id="22111-113">The argument is cast to the DT_R8 data type before the square operation.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="22111-114">運算式範例</span><span class="sxs-lookup"><span data-stu-id="22111-114">Expression Examples</span></span>  
 <span data-ttu-id="22111-115">此範例會傳回 12 的平方。</span><span class="sxs-lookup"><span data-stu-id="22111-115">This example returns the square of 12.</span></span> <span data-ttu-id="22111-116">傳回結果為 144。</span><span class="sxs-lookup"><span data-stu-id="22111-116">The return result is 144.</span></span>  
  
```  
SQUARE(12)  
```  
  
 <span data-ttu-id="22111-117">此範例會傳回在兩個資料行中減去值之結果的平方。</span><span class="sxs-lookup"><span data-stu-id="22111-117">This example returns the square of the result of subtracting values in two columns.</span></span> <span data-ttu-id="22111-118">如果 **Value1** 為 12，而 **Value2** 為 4，則 SQUARE 函數會傳回 64。</span><span class="sxs-lookup"><span data-stu-id="22111-118">If **Value1** contains 12 and **Value2** contains 4, the SQUARE function returns 64.</span></span>  
  
```  
SQUARE(Value1 - Value2)  
```  
  
 <span data-ttu-id="22111-119">此範例會將 SQUARE 函數套用至兩個變數，然後計算其總和的平方根，藉此傳回直角三角形第三邊的長度。</span><span class="sxs-lookup"><span data-stu-id="22111-119">This example returns the length of the third side of a right angle triangle by applying the SQUARE function to two variables and then calculating the square root of their sum.</span></span> <span data-ttu-id="22111-120">如果 **Side1** 包含 3，而 **Side2** 包含 4，SQRT 函數就會傳回 5。</span><span class="sxs-lookup"><span data-stu-id="22111-120">If **Side1** contains 3 and **Side2** contains 4, the SQRT function returns 5.</span></span>  
  
```  
SQRT(SQUARE(@Side1) + SQUARE(@Side2))  
```  
  
> [!NOTE]  
>  <span data-ttu-id="22111-121">在運算式中，變數名稱一律包含 \@ 前置詞。</span><span class="sxs-lookup"><span data-stu-id="22111-121">In expressions, variable names always include the \@ prefix.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22111-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22111-122">See Also</span></span>  
 [<span data-ttu-id="22111-123">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="22111-123">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
