---
title: FINDSTRING (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- FINDSTRING function
ms.assetid: c83cb1b1-3c52-4496-b518-4c9253b9336d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 72f2ff21cb179ce565e60c6550b8ecc2618a5adb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595204"
---
# <a name="findstring-ssis-expression"></a><span data-ttu-id="2034d-102">FINDSTRING (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="2034d-102">FINDSTRING (SSIS Expression)</span></span>
  <span data-ttu-id="2034d-103">傳回字元運算式中字串的指定出現位置。</span><span class="sxs-lookup"><span data-stu-id="2034d-103">Returns the location of the specified occurrence of a string within a character expression.</span></span> <span data-ttu-id="2034d-104">傳回結果是以 1 為主的索引出現位置。</span><span class="sxs-lookup"><span data-stu-id="2034d-104">The return result is the one-based index of the occurrence.</span></span> <span data-ttu-id="2034d-105">string 參數的評估結果必須為字串運算式，且 occurrence 參數的評估結果必須為整數。</span><span class="sxs-lookup"><span data-stu-id="2034d-105">The string parameter must evaluate to a character expression, and the occurrence parameter must evaluate to an integer.</span></span> <span data-ttu-id="2034d-106">如果找不到字串，傳回值將為 0。</span><span class="sxs-lookup"><span data-stu-id="2034d-106">If the string is not found, the return value is 0.</span></span> <span data-ttu-id="2034d-107">如果字串出現的次數少於 occurrence 引數指定的次數，傳回值也是 0。</span><span class="sxs-lookup"><span data-stu-id="2034d-107">If the string occurs fewer times than the occurrence argument specifies, the return value is 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2034d-108">語法</span><span class="sxs-lookup"><span data-stu-id="2034d-108">Syntax</span></span>  
  
```  
  
FINDSTRING(character_expression, searchstring, occurrence)  
```  
  
## <a name="arguments"></a><span data-ttu-id="2034d-109">引數</span><span class="sxs-lookup"><span data-stu-id="2034d-109">Arguments</span></span>  
 <span data-ttu-id="2034d-110">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="2034d-110">*character_expression*</span></span>  
 <span data-ttu-id="2034d-111">是要在其中搜尋的字元字串。</span><span class="sxs-lookup"><span data-stu-id="2034d-111">Is the character string to search in.</span></span>  
  
 <span data-ttu-id="2034d-112">*searchstring*</span><span class="sxs-lookup"><span data-stu-id="2034d-112">*searchstring*</span></span>  
 <span data-ttu-id="2034d-113">是要搜尋的字元字串。</span><span class="sxs-lookup"><span data-stu-id="2034d-113">Is the character string to search for.</span></span>  
  
 <span data-ttu-id="2034d-114">*occurrence*</span><span class="sxs-lookup"><span data-stu-id="2034d-114">*occurrence*</span></span>  
 <span data-ttu-id="2034d-115">是帶正負號或不帶正負號的整數，指定要報告的 *searchstring* 出現位置。</span><span class="sxs-lookup"><span data-stu-id="2034d-115">Is a signed or unsigned integer specifying which occurrence of *searchstring* to report.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="2034d-116">結果類型</span><span class="sxs-lookup"><span data-stu-id="2034d-116">Result Types</span></span>  
 <span data-ttu-id="2034d-117">DT_I4</span><span class="sxs-lookup"><span data-stu-id="2034d-117">DT_I4</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2034d-118">備註</span><span class="sxs-lookup"><span data-stu-id="2034d-118">Remarks</span></span>  
 <span data-ttu-id="2034d-119">FINDSTRING 只適用於 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="2034d-119">FINDSTRING works only with the DT_WSTR data type.</span></span>  <span data-ttu-id="2034d-120">為字串常值或具有 DT_STR 資料類型之資料行的*character_expression* 和 *searchstring* 引數，會在 FINDSTRING 執行其作業之前隱含轉換為 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="2034d-120">*character_expression* and *searchstring* arguments that are string literals or data columns with the DT_STR data type are implicitly cast to the DT_WSTR data type before FINDSTRING performs its operation.</span></span> <span data-ttu-id="2034d-121">其他資料類型必須明確地轉換為 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="2034d-121">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="2034d-122">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)和[轉換 &#40;SSIS 運算式&#41;](cast-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="2034d-122">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="2034d-123">如果 *character_expression* 或 *searchstring* 都是 null，FINDSTRING 會傳回 null。</span><span class="sxs-lookup"><span data-stu-id="2034d-123">FINDSTRING returns null if either *character_expression* or *searchstring* are null.</span></span>  
  
 <span data-ttu-id="2034d-124">*occurrence* 引數使用數值 1 會取得第一次出現位置的索引，使用數值 2 則取得第二次出現位置，依此類推。</span><span class="sxs-lookup"><span data-stu-id="2034d-124">Use a value of 1 in the *occurrence* argument to get the index of the first occurrence, 2 for the second occurrence and so forth.</span></span>  
  
 <span data-ttu-id="2034d-125">*occurrence* 必須為大於 0 值的整數。</span><span class="sxs-lookup"><span data-stu-id="2034d-125">The *occurrence* must be an integer with a value greater than 0.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="2034d-126">運算式範例</span><span class="sxs-lookup"><span data-stu-id="2034d-126">Expression Examples</span></span>  
 <span data-ttu-id="2034d-127">這個範例使用字串常值。</span><span class="sxs-lookup"><span data-stu-id="2034d-127">This example uses a string literal.</span></span> <span data-ttu-id="2034d-128">它會傳回數值 11。</span><span class="sxs-lookup"><span data-stu-id="2034d-128">It returns the value 11.</span></span>  
  
```  
FINDSTRING("New York, NY, NY", "NY", 1)   
```  
  
 <span data-ttu-id="2034d-129">這個範例使用字串常值。</span><span class="sxs-lookup"><span data-stu-id="2034d-129">This example uses a string literal.</span></span> <span data-ttu-id="2034d-130">由於字串 "NY" 只出現兩次，因此傳回結果為 0。</span><span class="sxs-lookup"><span data-stu-id="2034d-130">Because the string "NY" occurs only two times, the return result is 0.</span></span>  
  
```  
FINDSTRING("New York, NY, NY", "NY", 3)   
```  
  
 <span data-ttu-id="2034d-131">此範例使用 **Name** 資料行。</span><span class="sxs-lookup"><span data-stu-id="2034d-131">This example uses the **Name** column.</span></span> <span data-ttu-id="2034d-132">它會傳回數值 n 在 **Name** 資料行中的位置。</span><span class="sxs-lookup"><span data-stu-id="2034d-132">It returns the location of the value n in the **Name** column.</span></span> <span data-ttu-id="2034d-133">傳回結果視 **Name**中的值而有所不同。</span><span class="sxs-lookup"><span data-stu-id="2034d-133">The return result varies depending on the value in **Name**.</span></span> <span data-ttu-id="2034d-134">如果 **Name** 包含 Anderson，則函數會傳回 8。</span><span class="sxs-lookup"><span data-stu-id="2034d-134">If **Name** contains Anderson, the function returns 8.</span></span>  
  
```  
FINDSTRING(Name,"n", 2)   
```  
  
 <span data-ttu-id="2034d-135">此範例使用 **Name** 和 **Size** 資料行。</span><span class="sxs-lookup"><span data-stu-id="2034d-135">This example uses the **Name** and **Size** columns.</span></span> <span data-ttu-id="2034d-136">它會傳回 **Name** 資料行中， **Size** 值最左邊字元的位置。</span><span class="sxs-lookup"><span data-stu-id="2034d-136">It returns the location of the leftmost character of the **Size** value in the **Name** column.</span></span> <span data-ttu-id="2034d-137">傳回的結果視資料行的值而有所不同。</span><span class="sxs-lookup"><span data-stu-id="2034d-137">The return result varies depending on column values.</span></span> <span data-ttu-id="2034d-138">如果 **Name** 包含 Mountain,500Red,42，而 **Size** 包含 42，則傳回結果為 17。</span><span class="sxs-lookup"><span data-stu-id="2034d-138">If **Name** contains Mountain,500Red,42 and **Size** contains 42, the return result is 17.</span></span>  
  
```  
FINDSTRING(Name,Size,1)   
```  
  
## <a name="see-also"></a><span data-ttu-id="2034d-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2034d-139">See Also</span></span>  
 <span data-ttu-id="2034d-140">[REPLACE &#40;SSIS 運算式&#41;](replace-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="2034d-140">[REPLACE &#40;SSIS Expression&#41;](replace-ssis-expression.md) </span></span>  
 [<span data-ttu-id="2034d-141">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="2034d-141">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
