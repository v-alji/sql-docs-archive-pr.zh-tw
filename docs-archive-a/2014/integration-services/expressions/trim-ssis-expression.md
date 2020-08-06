---
title: TRIM (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- leading blanks
- TRIM function
- trailing blanks
ms.assetid: 7dd9081d-a3d4-483a-bf7e-bf2bd7692d39
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 42cef8a816f399e39ac99061f34c394156bde45f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701329"
---
# <a name="trim-ssis-expression"></a><span data-ttu-id="c95a5-102">TRIM (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="c95a5-102">TRIM (SSIS Expression)</span></span>
  <span data-ttu-id="c95a5-103">傳回移除開頭和尾端空白之後的字元運算式。</span><span class="sxs-lookup"><span data-stu-id="c95a5-103">Returns a character expression after removing leading and trailing spaces.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c95a5-104">TRIM 不會移除空白字元，例如 Tab 鍵或換行字元。</span><span class="sxs-lookup"><span data-stu-id="c95a5-104">TRIM does not remove white-space characters such as the tab or line feed characters.</span></span> <span data-ttu-id="c95a5-105">Unicode 會為許多不同類型的空格提供字碼指標，但此功能只會辨識 Unicode 字碼指標 0x0020。</span><span class="sxs-lookup"><span data-stu-id="c95a5-105">Unicode provides code points for many different types of spaces, but this function recognizes only the Unicode code point 0x0020.</span></span> <span data-ttu-id="c95a5-106">當將雙位元組字集 (DBCS) 字串轉換為 Unicode 時，它們可以包括 0x0020 以外的空格字元，但此功能無法移除這些空格。</span><span class="sxs-lookup"><span data-stu-id="c95a5-106">When double-byte character set (DBCS) strings are converted to Unicode they may include space characters other than 0x0020 and the function cannot remove such spaces.</span></span> <span data-ttu-id="c95a5-107">若要移除所有種類的空格，您可以在從「指令碼」元件執行的指令碼中使用 Microsoft Visual Basic .NET Trim 方法。</span><span class="sxs-lookup"><span data-stu-id="c95a5-107">To remove all kinds of spaces, you can use the Microsoft Visual Basic .NET Trim method in a script run from the Script component.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c95a5-108">語法</span><span class="sxs-lookup"><span data-stu-id="c95a5-108">Syntax</span></span>  
  
```  
  
TRIM(character_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="c95a5-109">引數</span><span class="sxs-lookup"><span data-stu-id="c95a5-109">Arguments</span></span>  
 <span data-ttu-id="c95a5-110">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="c95a5-110">*character_expression*</span></span>  
 <span data-ttu-id="c95a5-111">要移除空白的字元運算式。</span><span class="sxs-lookup"><span data-stu-id="c95a5-111">Is a character expression from which to remove spaces.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="c95a5-112">結果類型</span><span class="sxs-lookup"><span data-stu-id="c95a5-112">Result Types</span></span>  
 <span data-ttu-id="c95a5-113">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="c95a5-113">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c95a5-114">備註</span><span class="sxs-lookup"><span data-stu-id="c95a5-114">Remarks</span></span>  
 <span data-ttu-id="c95a5-115">如果引數為 Null，則 TRIM 會傳回 Null 結果。</span><span class="sxs-lookup"><span data-stu-id="c95a5-115">TRIM returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="c95a5-116">TRIM 只適用於 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="c95a5-116">TRIM works only with the DT_WSTR data type.</span></span> <span data-ttu-id="c95a5-117">如果 *character_expression* 引數是字串常值或具有 DT_STR 資料類型的資料行，則該引數會在 TRIM 執行其作業前隱含轉換成 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="c95a5-117">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before TRIM performs its operation.</span></span> <span data-ttu-id="c95a5-118">其他資料類型必須明確地轉換為 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="c95a5-118">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="c95a5-119">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)和[轉換 &#40;SSIS 運算式&#41;](cast-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="c95a5-119">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="c95a5-120">運算式範例</span><span class="sxs-lookup"><span data-stu-id="c95a5-120">Expression Examples</span></span>  
 <span data-ttu-id="c95a5-121">此範例會移除字串常值開頭和尾端的空白。</span><span class="sxs-lookup"><span data-stu-id="c95a5-121">This example removes leading and trailing spaces from a string literal.</span></span> <span data-ttu-id="c95a5-122">傳回結果為「New York」。</span><span class="sxs-lookup"><span data-stu-id="c95a5-122">The return result is "New York".</span></span>  
  
```  
TRIM("   New York   ")  
```  
  
 <span data-ttu-id="c95a5-123">此範例會從串連 **FirstName** 和 **LastName** 資料行的結果中移除開頭和尾端的空白。</span><span class="sxs-lookup"><span data-stu-id="c95a5-123">This example removes leading and trailing spaces from the result of concatenating the **FirstName** and **LastName** columns.</span></span> <span data-ttu-id="c95a5-124">**FirstName** 和 **LastName** 之間的空白字串則不會移除。</span><span class="sxs-lookup"><span data-stu-id="c95a5-124">The empty string between **FirstName** and **LastName** is not removed.</span></span>  
  
```  
TRIM(FirstName + " "+ LastName)  
```  
  
## <a name="see-also"></a><span data-ttu-id="c95a5-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c95a5-125">See Also</span></span>  
 <span data-ttu-id="c95a5-126">[LTRIM &#40;SSIS 運算式&#41;](trim-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="c95a5-126">[LTRIM &#40;SSIS Expression&#41;](trim-ssis-expression.md) </span></span>  
 <span data-ttu-id="c95a5-127">[RTRIM &#40;SSIS 運算式&#41;](rtrim-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="c95a5-127">[RTRIM &#40;SSIS Expression&#41;](rtrim-ssis-expression.md) </span></span>  
 [<span data-ttu-id="c95a5-128">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="c95a5-128">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
