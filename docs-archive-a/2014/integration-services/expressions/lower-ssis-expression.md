---
title: LOWER (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- converting uppercase to lowercase
- LOWER function
- uppercase characters [Integration Services]
- lowercase characters
ms.assetid: 109328e1-5604-40ff-895e-f2e7c13fff41
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 180be8f3cfb5a15eb0fcd6ddd3d63b09fe874af5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595202"
---
# <a name="lower-ssis-expression"></a><span data-ttu-id="5d07b-102">LOWER (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="5d07b-102">LOWER (SSIS Expression)</span></span>
  <span data-ttu-id="5d07b-103">傳回將大寫字元轉換為小寫字元之後的字元運算式。</span><span class="sxs-lookup"><span data-stu-id="5d07b-103">Returns a character expression after converting uppercase characters to lowercase characters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d07b-104">語法</span><span class="sxs-lookup"><span data-stu-id="5d07b-104">Syntax</span></span>  
  
```  
  
LOWER(character_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="5d07b-105">引數</span><span class="sxs-lookup"><span data-stu-id="5d07b-105">Arguments</span></span>  
 <span data-ttu-id="5d07b-106">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="5d07b-106">*character_expression*</span></span>  
 <span data-ttu-id="5d07b-107">是轉換成小寫字元的字元運算式。</span><span class="sxs-lookup"><span data-stu-id="5d07b-107">Is a character expression to convert to lowercase characters.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="5d07b-108">結果類型</span><span class="sxs-lookup"><span data-stu-id="5d07b-108">Result Types</span></span>  
 <span data-ttu-id="5d07b-109">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="5d07b-109">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d07b-110">備註</span><span class="sxs-lookup"><span data-stu-id="5d07b-110">Remarks</span></span>  
 <span data-ttu-id="5d07b-111">LOWER 只適用於 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="5d07b-111">LOWER works only with the DT_WSTR data type.</span></span> <span data-ttu-id="5d07b-112">如果 *character_expression* 引數是字串常值或具有 DT_STR 資料類型的資料行，則該引數會在 LOWER 執行其作業前隱含轉換成 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="5d07b-112">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before LOWER performs its operation.</span></span> <span data-ttu-id="5d07b-113">其他資料類型必須明確地轉換為 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="5d07b-113">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="5d07b-114">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)和[轉換 &#40;SSIS 運算式&#41;](cast-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="5d07b-114">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="5d07b-115">如果引數為 Null，則 LOWER 會傳回 Null 結果。</span><span class="sxs-lookup"><span data-stu-id="5d07b-115">LOWER returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="5d07b-116">運算式範例</span><span class="sxs-lookup"><span data-stu-id="5d07b-116">Expression Examples</span></span>  
 <span data-ttu-id="5d07b-117">此範例會將字串常值轉換成小寫字元。</span><span class="sxs-lookup"><span data-stu-id="5d07b-117">This example converts a string literal to lowercase characters.</span></span> <span data-ttu-id="5d07b-118">傳回結果為 "new york"。</span><span class="sxs-lookup"><span data-stu-id="5d07b-118">The return result is "new york".</span></span>  
  
```  
LOWER("New York")  
```  
  
 <span data-ttu-id="5d07b-119">此範例會將 **Color** 輸入資料行中的所有字元轉換成小寫字元，除了第一個字元以外。</span><span class="sxs-lookup"><span data-stu-id="5d07b-119">This example converts all characters from the **Color** input column, except the first character, to lowercase characters.</span></span> <span data-ttu-id="5d07b-120">如果 Color 是 YELLOW，則傳回結果為 "Yellow"。</span><span class="sxs-lookup"><span data-stu-id="5d07b-120">If Color is YELLOW, the return result is "Yellow".</span></span> <span data-ttu-id="5d07b-121">如需詳細資訊，請參閱 [SUBSTRING &#40;SSIS 運算式&#41;](substring-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="5d07b-121">For more information, see [SUBSTRING &#40;SSIS Expression&#41;](substring-ssis-expression.md).</span></span>  
  
```  
LOWER(SUBSTRING(Color, 2, 15))  
```  
  
 <span data-ttu-id="5d07b-122">此範例會將 **CityName** 變數中的值轉換成小寫字元。</span><span class="sxs-lookup"><span data-stu-id="5d07b-122">This example converts the value in the **CityName** variable to lowercase characters.</span></span>  
  
```  
LOWER(@CityName)  
```  
  
## <a name="see-also"></a><span data-ttu-id="5d07b-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d07b-123">See Also</span></span>  
 <span data-ttu-id="5d07b-124">[UPPER &#40;SSIS 運算式&#41;](upper-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="5d07b-124">[UPPER &#40;SSIS Expression&#41;](upper-ssis-expression.md) </span></span>  
 [<span data-ttu-id="5d07b-125">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="5d07b-125">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
