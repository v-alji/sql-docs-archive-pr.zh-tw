---
title: SUBSTRING (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SUBSTRING function
- part of expression returned [Integration Services]
ms.assetid: 3a46748a-f5f8-4a6c-9108-673666754068
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ba53676bc6d13ed34892f48fca3b70372cb30604
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701356"
---
# <a name="substring-ssis-expression"></a><span data-ttu-id="8f812-102">SUBSTRING (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="8f812-102">SUBSTRING (SSIS Expression)</span></span>
  <span data-ttu-id="8f812-103">傳回從指定位置開始算起指定長度的字元運算式部分。</span><span class="sxs-lookup"><span data-stu-id="8f812-103">Returns the part of a character expression that starts at the specified position and has the specified length.</span></span> <span data-ttu-id="8f812-104">*position* 參數和 *length* 參數必須評估為整數。</span><span class="sxs-lookup"><span data-stu-id="8f812-104">The *position* parameter and the *length* parameter must evaluate to integers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f812-105">語法</span><span class="sxs-lookup"><span data-stu-id="8f812-105">Syntax</span></span>  
  
```  
  
SUBSTRING(character_expression, position, length)  
```  
  
## <a name="arguments"></a><span data-ttu-id="8f812-106">引數</span><span class="sxs-lookup"><span data-stu-id="8f812-106">Arguments</span></span>  
 <span data-ttu-id="8f812-107">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="8f812-107">*character_expression*</span></span>  
 <span data-ttu-id="8f812-108">要擷取字元的字元運算式。</span><span class="sxs-lookup"><span data-stu-id="8f812-108">Is a character expression from which to extract characters.</span></span>  
  
 <span data-ttu-id="8f812-109">*position*</span><span class="sxs-lookup"><span data-stu-id="8f812-109">*position*</span></span>  
 <span data-ttu-id="8f812-110">是指定子字串開始處的整數。</span><span class="sxs-lookup"><span data-stu-id="8f812-110">Is an integer that specifies where the substring begins.</span></span>  
  
 <span data-ttu-id="8f812-111">*length*</span><span class="sxs-lookup"><span data-stu-id="8f812-111">*length*</span></span>  
 <span data-ttu-id="8f812-112">是指定做為字元數之子字串長度的整數。</span><span class="sxs-lookup"><span data-stu-id="8f812-112">Is an integer that specifies the length of the substring as number of characters.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="8f812-113">結果類型</span><span class="sxs-lookup"><span data-stu-id="8f812-113">Result Types</span></span>  
 <span data-ttu-id="8f812-114">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="8f812-114">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f812-115">備註</span><span class="sxs-lookup"><span data-stu-id="8f812-115">Remarks</span></span>  
 <span data-ttu-id="8f812-116">SUBSTRING 使用以 1 為基底的索引。</span><span class="sxs-lookup"><span data-stu-id="8f812-116">SUBSTRING uses a one-based index.</span></span> <span data-ttu-id="8f812-117">如果 *position* 是 1，則子字串會以 *character_expression*中的第一個字元開頭。</span><span class="sxs-lookup"><span data-stu-id="8f812-117">If *position* is 1, the substring begins with the first character in *character_expression*.</span></span>  
  
 <span data-ttu-id="8f812-118">SUBSTRING 只適用於 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="8f812-118">SUBSTRING works only with the DT_WSTR data type.</span></span> <span data-ttu-id="8f812-119">如果 *character_expression* 引數是字串常值或具有 DT_STR 資料類型的資料行，則該引數會在 SUBSTRING 執行其作業前隱含轉換成 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="8f812-119">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before SUBSTRING performs its operation.</span></span> <span data-ttu-id="8f812-120">其他資料類型必須明確地轉換為 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="8f812-120">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="8f812-121">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)和[轉換 &#40;SSIS 運算式&#41;](cast-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="8f812-121">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="8f812-122">如果引數為 Null，則 SUBSTRING 會傳回 Null 結果。</span><span class="sxs-lookup"><span data-stu-id="8f812-122">SUBSTRING returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="8f812-123">運算式中的所有引數都可使用變數和資料行。</span><span class="sxs-lookup"><span data-stu-id="8f812-123">All arguments in the expression can use variables and columns.</span></span>  
  
 <span data-ttu-id="8f812-124">*length* 引數可以超過字串長度。</span><span class="sxs-lookup"><span data-stu-id="8f812-124">The *length* argument can exceed the length of the string.</span></span> <span data-ttu-id="8f812-125">在此情況下，函數會傳回字串的其餘部份。</span><span class="sxs-lookup"><span data-stu-id="8f812-125">In that case, the function returns the remainder of the string.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="8f812-126">運算式範例</span><span class="sxs-lookup"><span data-stu-id="8f812-126">Expression Examples</span></span>  
 <span data-ttu-id="8f812-127">此範例會從字串常值傳回以第 4 個字元開頭的兩個字元。</span><span class="sxs-lookup"><span data-stu-id="8f812-127">This example returns two characters, beginning with character 4, from a string literal.</span></span> <span data-ttu-id="8f812-128">傳回結果為 "ph"。</span><span class="sxs-lookup"><span data-stu-id="8f812-128">The return result is "ph".</span></span>  
  
```  
SUBSTRING("elephant",4,2)  
```  
  
 <span data-ttu-id="8f812-129">此範例會傳回從字串常值中第 4 個字元起算的其餘部份。</span><span class="sxs-lookup"><span data-stu-id="8f812-129">This example returns the remainder of a string literal, beginning at the fourth character.</span></span> <span data-ttu-id="8f812-130">傳回結果為 "phant"。</span><span class="sxs-lookup"><span data-stu-id="8f812-130">The return result is "phant".</span></span> <span data-ttu-id="8f812-131">*length* 引數超過字串長度並非錯誤。</span><span class="sxs-lookup"><span data-stu-id="8f812-131">It is not an error for the *length* argument to exceed the length of the string.</span></span>  
  
```  
SUBSTRING ("elephant",4,50)  
```  
  
 <span data-ttu-id="8f812-132">此範例會傳回 **MiddleName** 資料行中的第一個字母。</span><span class="sxs-lookup"><span data-stu-id="8f812-132">This example returns the first letter from the **MiddleName** column.</span></span>  
  
```  
SUBSTRING(MiddleName,1,1)  
```  
  
 <span data-ttu-id="8f812-133">此範例會使用 *position* 和 *length* 引數中的變數。</span><span class="sxs-lookup"><span data-stu-id="8f812-133">This example uses variables in the *position* and *length* arguments.</span></span> <span data-ttu-id="8f812-134">如果 **Start** 是 1 且 **Length** 是 5，則函數會傳回 **Name** 資料行中的前五個字元。</span><span class="sxs-lookup"><span data-stu-id="8f812-134">If **Start** is 1 and **Length** is 5, the function returns the first five characters in the **Name** column.</span></span>  
  
```  
SUBSTRING(Name,@Start,@Length)  
```  
  
 <span data-ttu-id="8f812-135">此範例會傳回 **PostalCode** 變數中，從第六個字元起算的後四個字元。</span><span class="sxs-lookup"><span data-stu-id="8f812-135">This example returns the last four characters from the **PostalCode** variable beginning at the sixth character.</span></span>  
  
```  
SUBSTRING (@PostalCode,6,4)  
```  
  
 <span data-ttu-id="8f812-136">此範例會從字串常值中傳回零長度的字串。</span><span class="sxs-lookup"><span data-stu-id="8f812-136">This example returns a zero-length string from a string literal.</span></span>  
  
```  
SUBSTRING ("Redmond",4,0)  
```  
  
## <a name="see-also"></a><span data-ttu-id="8f812-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f812-137">See Also</span></span>  
 [<span data-ttu-id="8f812-138">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="8f812-138">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
