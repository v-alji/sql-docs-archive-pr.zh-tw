---
title: RIGHT (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- RIGHT function
ms.assetid: 83e70e75-4be5-4783-a8cf-032f82afe16e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2584ee33ecbf0436c4e3dc6e92b957e60ae396ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701407"
---
# <a name="right-ssis-expression"></a><span data-ttu-id="766cb-102">RIGHT (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="766cb-102">RIGHT (SSIS Expression)</span></span>
  <span data-ttu-id="766cb-103">傳回來自給定字元運算式最右邊部分的指定字元數。</span><span class="sxs-lookup"><span data-stu-id="766cb-103">Returns the specified number of characters from the rightmost portion of the given character expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="766cb-104">語法</span><span class="sxs-lookup"><span data-stu-id="766cb-104">Syntax</span></span>  
  
```  
  
RIGHT(character_expression,integer_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="766cb-105">引數</span><span class="sxs-lookup"><span data-stu-id="766cb-105">Arguments</span></span>  
 <span data-ttu-id="766cb-106">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="766cb-106">*character_expression*</span></span>  
 <span data-ttu-id="766cb-107">要擷取字元的字元運算式。</span><span class="sxs-lookup"><span data-stu-id="766cb-107">Is a character expression from which to extract characters.</span></span>  
  
 <span data-ttu-id="766cb-108">*integer_expression*</span><span class="sxs-lookup"><span data-stu-id="766cb-108">*integer_expression*</span></span>  
 <span data-ttu-id="766cb-109">為表示要傳回字元數的整數運算式。</span><span class="sxs-lookup"><span data-stu-id="766cb-109">Is an integer expression that indicates the number of characters to be returned.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="766cb-110">結果類型</span><span class="sxs-lookup"><span data-stu-id="766cb-110">Result Types</span></span>  
 <span data-ttu-id="766cb-111">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="766cb-111">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="766cb-112">備註</span><span class="sxs-lookup"><span data-stu-id="766cb-112">Remarks</span></span>  
 <span data-ttu-id="766cb-113">如果 *integer_expression* 大於 *character_expression*的長度，函數會傳回 *character_expression*。</span><span class="sxs-lookup"><span data-stu-id="766cb-113">If *integer_expression* is greater than the length of *character_expression*, the function returns *character_expression*.</span></span>  
  
 <span data-ttu-id="766cb-114">如果 *integer_expression* 為零，則函數會傳回長度為 0 的字串。</span><span class="sxs-lookup"><span data-stu-id="766cb-114">If *integer_expression* is zero, the function returns a zero-length string.</span></span>  
  
 <span data-ttu-id="766cb-115">如果 *integer_expression* 為負數，則函數會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="766cb-115">If *integer_expression* is a negative number, the function returns an error.</span></span>  
  
 <span data-ttu-id="766cb-116">*integer_expression* 引數可採用變數和資料行。</span><span class="sxs-lookup"><span data-stu-id="766cb-116">The *integer_expression* argument can take variables and columns.</span></span>  
  
 <span data-ttu-id="766cb-117">RIGHT 只適用於 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="766cb-117">RIGHT works only with the DT_WSTR data type.</span></span> <span data-ttu-id="766cb-118">如果 *character_expression* 引數是字串常值或具有 DT_STR 資料類型的資料行，則該引數會在 RIGHT 執行其作業前隱含轉換成 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="766cb-118">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before RIGHT performs its operation.</span></span> <span data-ttu-id="766cb-119">其他資料類型必須明確地轉換為 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="766cb-119">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="766cb-120">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)和[轉換 &#40;SSIS 運算式&#41;](cast-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="766cb-120">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="766cb-121">如果其中一個引數為 Null，則 RIGHT 會傳回 Null 結果。</span><span class="sxs-lookup"><span data-stu-id="766cb-121">RIGHT returns a null result if either argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="766cb-122">運算式範例</span><span class="sxs-lookup"><span data-stu-id="766cb-122">Expression Examples</span></span>  
 <span data-ttu-id="766cb-123">下列範例會使用字串常值。</span><span class="sxs-lookup"><span data-stu-id="766cb-123">The following example uses a string literal.</span></span> <span data-ttu-id="766cb-124">傳回結果為 `"Bike"`。</span><span class="sxs-lookup"><span data-stu-id="766cb-124">The return result is `"Bike"`.</span></span>  
  
```  
RIGHT("Mountain Bike", 4)  
```  
  
 <span data-ttu-id="766cb-125">下列範例會從 `Times` 資料行傳回 `Name` 變數中指定的最右邊字元數。</span><span class="sxs-lookup"><span data-stu-id="766cb-125">The following example returns the number of rightmost characters that is specified in the `Times` variable, from the `Name` column.</span></span> <span data-ttu-id="766cb-126">如果 `Name` 為 `Touring Front Wheel` 且 `Times` 為 5，傳回的結果為 `"Wheel"`。</span><span class="sxs-lookup"><span data-stu-id="766cb-126">If `Name` is `Touring Front Wheel` and `Times` is 5, the return result is `"Wheel"`.</span></span>  
  
```  
RIGHT(Name, @Times)  
```  
  
 <span data-ttu-id="766cb-127">下列範例亦會從 `Times` 資料行傳回 `Name` 變數中指定的最右邊字元數。</span><span class="sxs-lookup"><span data-stu-id="766cb-127">The following example also returns the number of rightmost characters that is specified in the `Times` variable, from the `Name` column.</span></span> <span data-ttu-id="766cb-128">`Times` 的資料類型為非整數，且運算式包括明確轉換成 DT_I2 的資料類型。</span><span class="sxs-lookup"><span data-stu-id="766cb-128">`Times` has a noninteger data type and the expression includes an explicit cast to the DT_I2 data type.</span></span> <span data-ttu-id="766cb-129">如果 `Name` 是 `Touring Front Wheel` ，而 `Times` 是 `4.32`，傳回的結果會是 `"heel"` ，因為 RIGHT 函數會將值 4.32 轉換成 4，然後傳回最右邊的四個字元。</span><span class="sxs-lookup"><span data-stu-id="766cb-129">If `Name` is `Touring Front Wheel` and `Times` is `4.32`, the return result is `"heel"` because the RIGHT function converts the value of 4.32 to 4, and then returns the rightmost four characters.</span></span>  
  
```  
RIGHT(Name, (DT_I2)@Times))  
```  
  
## <a name="see-also"></a><span data-ttu-id="766cb-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="766cb-130">See Also</span></span>  
 <span data-ttu-id="766cb-131">[LEFT &#40;SSIS 運算式&#41;](left-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="766cb-131">[LEFT &#40;SSIS Expression&#41;](left-ssis-expression.md) </span></span>  
 [<span data-ttu-id="766cb-132">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="766cb-132">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
