---
title: UPPER (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- UPPER function
- converting lowercase to uppercase
- uppercase characters [Integration Services]
- lowercase characters
ms.assetid: d33985f7-1048-4023-83e4-274090acda78
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 181e231d735a8e98cd2bce10c692e35668a686f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701317"
---
# <a name="upper-ssis-expression"></a><span data-ttu-id="447ac-102">UPPER (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="447ac-102">UPPER (SSIS Expression)</span></span>
  <span data-ttu-id="447ac-103">傳回小寫字元轉換為大寫字元之後的字元運算式。</span><span class="sxs-lookup"><span data-stu-id="447ac-103">Returns a character expression after converting lowercase characters to uppercase characters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="447ac-104">語法</span><span class="sxs-lookup"><span data-stu-id="447ac-104">Syntax</span></span>  
  
```  
  
UPPER(character_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="447ac-105">引數</span><span class="sxs-lookup"><span data-stu-id="447ac-105">Arguments</span></span>  
 <span data-ttu-id="447ac-106">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="447ac-106">*character_expression*</span></span>  
 <span data-ttu-id="447ac-107">是轉換成大寫字元的字元運算式。</span><span class="sxs-lookup"><span data-stu-id="447ac-107">Is a character expression to convert to uppercase characters.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="447ac-108">結果類型</span><span class="sxs-lookup"><span data-stu-id="447ac-108">Result Types</span></span>  
 <span data-ttu-id="447ac-109">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="447ac-109">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="447ac-110">備註</span><span class="sxs-lookup"><span data-stu-id="447ac-110">Remarks</span></span>  
 <span data-ttu-id="447ac-111">UPPER 只適用於 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="447ac-111">UPPER works only with the DT_WSTR data type.</span></span> <span data-ttu-id="447ac-112">如果 *character_expression* 引數是字串常值或具有 DT_STR 資料類型的資料行，則該引數會在 LOWER 執行其作業前隱含轉換成 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="447ac-112">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before UPPER performs its operation.</span></span> <span data-ttu-id="447ac-113">其他資料類型必須明確地轉換為 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="447ac-113">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="447ac-114">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)和[轉換 &#40;SSIS 運算式&#41;](cast-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="447ac-114">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="447ac-115">如果引數為 Null，則 UPPER 會傳回 Null 結果。</span><span class="sxs-lookup"><span data-stu-id="447ac-115">UPPER returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="447ac-116">運算式範例</span><span class="sxs-lookup"><span data-stu-id="447ac-116">Expression Examples</span></span>  
 <span data-ttu-id="447ac-117">此範例會將字串常值轉換成大寫字元。</span><span class="sxs-lookup"><span data-stu-id="447ac-117">This example converts a string literal to uppercase characters.</span></span> <span data-ttu-id="447ac-118">傳回結果為「HELLO」。</span><span class="sxs-lookup"><span data-stu-id="447ac-118">The return result is "HELLO".</span></span>  
  
```  
UPPER("hello")  
```  
  
 <span data-ttu-id="447ac-119">此範例會將 **FirstName** 資料行中的第一個字元轉換成大寫字元。</span><span class="sxs-lookup"><span data-stu-id="447ac-119">This example converts the first character in the **FirstName** column to an uppercase character.</span></span> <span data-ttu-id="447ac-120">如果 **FirstName** 為 anna，則傳回結果為「A」。</span><span class="sxs-lookup"><span data-stu-id="447ac-120">If **FirstName** is anna, the return result is "A".</span></span> <span data-ttu-id="447ac-121">如需詳細資訊，請參閱 [SUBSTRING &#40;SSIS 運算式&#41;](substring-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="447ac-121">For more information, see [SUBSTRING &#40;SSIS Expression&#41;](substring-ssis-expression.md).</span></span>  
  
```  
UPPER(SUBSTRING(FirstName, 1, 1))  
```  
  
 <span data-ttu-id="447ac-122">此範例會將 **PostalCode** 變數中的值轉換成大寫字元。</span><span class="sxs-lookup"><span data-stu-id="447ac-122">This example converts the value in the **PostalCode** variable to uppercase characters.</span></span> <span data-ttu-id="447ac-123">如果 **PostalCode** 為 k4b1s2，則傳回結果為「K4B1S2」。</span><span class="sxs-lookup"><span data-stu-id="447ac-123">If **PostalCode** is k4b1s2, the return result is "K4B1S2".</span></span>  
  
```  
UPPER(@PostalCode)  
```  
  
## <a name="see-also"></a><span data-ttu-id="447ac-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="447ac-124">See Also</span></span>  
 <span data-ttu-id="447ac-125">[LOWER &#40;SSIS 運算式&#41;](lower-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="447ac-125">[LOWER &#40;SSIS Expression&#41;](lower-ssis-expression.md) </span></span>  
 [<span data-ttu-id="447ac-126">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="447ac-126">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
