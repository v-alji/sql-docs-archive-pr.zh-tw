---
title: REPLICATE (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- REPLICATE function
ms.assetid: e7a37b93-6d1d-42d5-9a65-de1790abf6a5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9502df5bc20c6ad85f1f98fb57fe6b3cf431cc20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701413"
---
# <a name="replicate-ssis-expression"></a><span data-ttu-id="08b2e-102">REPLICATE (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="08b2e-102">REPLICATE (SSIS Expression)</span></span>
  <span data-ttu-id="08b2e-103">傳回複寫許多次的字元運算式。</span><span class="sxs-lookup"><span data-stu-id="08b2e-103">Returns a character expression that is replicated a number of times.</span></span> <span data-ttu-id="08b2e-104">*times* 引數必須評估為整數。</span><span class="sxs-lookup"><span data-stu-id="08b2e-104">The *times* argument must evaluate to an integer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="08b2e-105">REPLICATE 函數經常使用長字串，因此很可能產生運算式長度為 4000 個字元的限制。</span><span class="sxs-lookup"><span data-stu-id="08b2e-105">The REPLICATE function frequently uses long strings, and therefore is more likely to incur the 4000-character limit on expression length.</span></span> <span data-ttu-id="08b2e-106">如果運算式的評估結果具有 Integration Services 資料類型 DT_WSTR 或 DT_STR，則會將運算式在 4000 個字元處截斷。</span><span class="sxs-lookup"><span data-stu-id="08b2e-106">If the evaluation result of an expression has the Integration Services data type DT_WSTR or DT_STR, the expression will be truncated at 4000 characters.</span></span> <span data-ttu-id="08b2e-107">如果子運算式的結果類型為 DT_STR 或 DT_WSTR，則同樣會將子運算式截斷到 4000 個字元，不論整體運算式的結果類型為何。</span><span class="sxs-lookup"><span data-stu-id="08b2e-107">If the result type of a sub-expression is DT_STR or DT_WSTR, that sub-expression likewise will be truncated to 4000 characters, regardless of the overall expression result type.</span></span> <span data-ttu-id="08b2e-108">截斷的結果可正常地處理，或造成警告或錯誤。</span><span class="sxs-lookup"><span data-stu-id="08b2e-108">The consequences of truncation can be handled gracefully or cause a warning or an error.</span></span> <span data-ttu-id="08b2e-109">如需詳細資訊，請參閱[語法 &#40;SSIS&#41;](syntax-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="08b2e-109">For more information, see [Syntax &#40;SSIS&#41;](syntax-ssis.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08b2e-110">語法</span><span class="sxs-lookup"><span data-stu-id="08b2e-110">Syntax</span></span>  
  
```  
  
REPLICATE(character_expression,times)  
```  
  
## <a name="arguments"></a><span data-ttu-id="08b2e-111">引數</span><span class="sxs-lookup"><span data-stu-id="08b2e-111">Arguments</span></span>  
 <span data-ttu-id="08b2e-112">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="08b2e-112">*character_expression*</span></span>  
 <span data-ttu-id="08b2e-113">是要複寫的字元運算式。</span><span class="sxs-lookup"><span data-stu-id="08b2e-113">Is a character expression to replicate.</span></span>  
  
 <span data-ttu-id="08b2e-114">*times*</span><span class="sxs-lookup"><span data-stu-id="08b2e-114">*times*</span></span>  
 <span data-ttu-id="08b2e-115">是整數運算式，指定複寫 *character_expression* 的次數。</span><span class="sxs-lookup"><span data-stu-id="08b2e-115">Is an integer expression that specifies the number of times *character_expression* is replicated.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="08b2e-116">結果類型</span><span class="sxs-lookup"><span data-stu-id="08b2e-116">Result Types</span></span>  
 <span data-ttu-id="08b2e-117">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="08b2e-117">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08b2e-118">備註</span><span class="sxs-lookup"><span data-stu-id="08b2e-118">Remarks</span></span>  
 <span data-ttu-id="08b2e-119">如果 *times* 為零，則函數會傳回長度為 0 的字串。</span><span class="sxs-lookup"><span data-stu-id="08b2e-119">If *times* is zero, the function returns a zero-length string.</span></span>  
  
 <span data-ttu-id="08b2e-120">如果 *times* 為負數，則函數會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="08b2e-120">If *times* is a negative number, the function returns an error.</span></span>  
  
 <span data-ttu-id="08b2e-121">*times* 引數亦使用變數和資料行。</span><span class="sxs-lookup"><span data-stu-id="08b2e-121">The *times* argument can also use variables and columns.</span></span>  
  
 <span data-ttu-id="08b2e-122">REPLICATE 只適用於 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="08b2e-122">REPLICATE works only with the DT_WSTR data type.</span></span> <span data-ttu-id="08b2e-123">如果 *character_expression* 引數是字串常值或具有 DT_STR 資料類型的資料行，則該引數會在 REPLICATE 執行其作業前隱含轉換成 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="08b2e-123">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before REPLICATE performs its operation.</span></span> <span data-ttu-id="08b2e-124">其他資料類型必須明確地轉換為 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="08b2e-124">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="08b2e-125">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)和[轉換 &#40;SSIS 運算式&#41;](cast-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="08b2e-125">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="08b2e-126">如果其中一個引數為 Null，則 REPLICATE 會傳回 Null 結果。</span><span class="sxs-lookup"><span data-stu-id="08b2e-126">REPLICATE returns a null result if either argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="08b2e-127">運算式範例</span><span class="sxs-lookup"><span data-stu-id="08b2e-127">Expression Examples</span></span>  
 <span data-ttu-id="08b2e-128">此範例會複寫字串常值三次。</span><span class="sxs-lookup"><span data-stu-id="08b2e-128">This example replicates a string literal three times.</span></span> <span data-ttu-id="08b2e-129">傳回結果為「Mountain BikeMountain BikeMountain Bike」。</span><span class="sxs-lookup"><span data-stu-id="08b2e-129">The return result is "Mountain BikeMountain BikeMountain Bike".</span></span>  
  
```  
REPLICATE("Mountain Bike", 3)  
```  
  
 <span data-ttu-id="08b2e-130">此範例會以 **Times** 變數中的值複寫 **Name** 資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="08b2e-130">This example replicates values in the **Name** column by the value in the **Times** variable.</span></span> <span data-ttu-id="08b2e-131">如果 **Times** 是 3，且 **Name** 是 Touring Front Wheel，則傳回結果為 Touring Front WheelTouring Front WheelTouring Front Wheel。</span><span class="sxs-lookup"><span data-stu-id="08b2e-131">If **Times** is 3 and **Name** is Touring Front Wheel, the return result is Touring Front WheelTouring Front WheelTouring Front Wheel.</span></span>  
  
```  
REPLICATE(Name, @Times)  
```  
  
 <span data-ttu-id="08b2e-132">此範例會以 **Times** 資料行中的值複寫 **Name** 變數中的值。</span><span class="sxs-lookup"><span data-stu-id="08b2e-132">This example replicates the value in the **Name** variable by the value in the **Times** column.</span></span> <span data-ttu-id="08b2e-133">**Times** 的資料類型為非整數，且運算式包括明確轉換成整數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="08b2e-133">**Times** has a non-integer data type and the expression includes an explicit cast to an integer data type.</span></span> <span data-ttu-id="08b2e-134">如果 **Name** 包含 Helmet，且 **Times** 為 2，則傳回結果為 "HelmetHelmet"。</span><span class="sxs-lookup"><span data-stu-id="08b2e-134">If **Name** contains Helmet and **Times** is 2, the return result is "HelmetHelmet".</span></span>  
  
```  
REPLICATE(@Name, (DT_I4(Times))  
```  
  
## <a name="see-also"></a><span data-ttu-id="08b2e-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08b2e-135">See Also</span></span>  
 [<span data-ttu-id="08b2e-136">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="08b2e-136">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
