---
title: LTRIM (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- leading blanks
- LTRIM function
ms.assetid: d082f42a-d7e7-49f5-a503-ac44ba630832
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 678d9d93eb1dcd7649d2085b651a08418bbcd6a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595200"
---
# <a name="ltrim-ssis-expression"></a><span data-ttu-id="fc3f4-102">LTRIM (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="fc3f4-102">LTRIM (SSIS Expression)</span></span>
  <span data-ttu-id="fc3f4-103">傳回移除開頭空白之後的字元運算式。</span><span class="sxs-lookup"><span data-stu-id="fc3f4-103">Returns a character expression after removing leading spaces.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fc3f4-104">LTRIM 不會移除空白字元，例如 Tab 鍵或換行字元。</span><span class="sxs-lookup"><span data-stu-id="fc3f4-104">LTRIM does not remove white-space characters such as the tab or line feed characters.</span></span> <span data-ttu-id="fc3f4-105">Unicode 會為許多不同類型的空格提供字碼指標，但此功能只會辨識 Unicode 字碼指標 0x0020。</span><span class="sxs-lookup"><span data-stu-id="fc3f4-105">Unicode provides code points for many different types of spaces, but this function recognizes only the Unicode code point 0x0020.</span></span> <span data-ttu-id="fc3f4-106">當將雙位元組字集 (DBCS) 字串轉換為 Unicode 時，它們可以包括 0x0020 以外的空格字元，但此功能無法移除這些空格。</span><span class="sxs-lookup"><span data-stu-id="fc3f4-106">When double-byte character set (DBCS) strings are converted to Unicode they may include space characters other than 0x0020 and the function cannot remove such spaces.</span></span> <span data-ttu-id="fc3f4-107">若要移除所有種類的空格，您可以在從「指令碼」元件執行的指令碼中使用 Microsoft Visual Basic .NET LTrim 方法。</span><span class="sxs-lookup"><span data-stu-id="fc3f4-107">To remove all kinds of spaces, you can use the Microsoft Visual Basic .NET LTrim method in a script run from the Script component.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc3f4-108">語法</span><span class="sxs-lookup"><span data-stu-id="fc3f4-108">Syntax</span></span>  
  
```  
  
LTRIM(character expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="fc3f4-109">引數</span><span class="sxs-lookup"><span data-stu-id="fc3f4-109">Arguments</span></span>  
 <span data-ttu-id="fc3f4-110">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="fc3f4-110">*character_expression*</span></span>  
 <span data-ttu-id="fc3f4-111">要移除空白的字元運算式。</span><span class="sxs-lookup"><span data-stu-id="fc3f4-111">Is a character expression from which to remove spaces.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="fc3f4-112">結果類型</span><span class="sxs-lookup"><span data-stu-id="fc3f4-112">Result Types</span></span>  
 <span data-ttu-id="fc3f4-113">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="fc3f4-113">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc3f4-114">備註</span><span class="sxs-lookup"><span data-stu-id="fc3f4-114">Remarks</span></span>  
 <span data-ttu-id="fc3f4-115">LTRIM 只適用於 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="fc3f4-115">LTRIM works only with the DT_WSTR data type.</span></span> <span data-ttu-id="fc3f4-116">如果 *character_expression* 引數是字串常值或具有 DT_STR 資料類型的資料行，則該引數會在 LTRIM 執行其作業前隱含轉換成 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="fc3f4-116">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before LTRIM performs its operation.</span></span> <span data-ttu-id="fc3f4-117">其他資料類型必須明確地轉換為 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="fc3f4-117">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="fc3f4-118">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)和[轉換 &#40;SSIS 運算式&#41;](cast-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="fc3f4-118">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="fc3f4-119">如果引數為 Null，則 LTRIM 會傳回 Null 結果。</span><span class="sxs-lookup"><span data-stu-id="fc3f4-119">LTRIM returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="fc3f4-120">運算式範例</span><span class="sxs-lookup"><span data-stu-id="fc3f4-120">Expression Examples</span></span>  
 <span data-ttu-id="fc3f4-121">此範例會移除字串常值的開頭空白。</span><span class="sxs-lookup"><span data-stu-id="fc3f4-121">This example removes leading spaces from a string literal.</span></span> <span data-ttu-id="fc3f4-122">傳回結果為「Hello」。</span><span class="sxs-lookup"><span data-stu-id="fc3f4-122">The return result is "Hello".</span></span>  
  
```  
LTRIM("    Hello")  
```  
  
 <span data-ttu-id="fc3f4-123">此範例會移除 **FirstName** 資料行中的開頭空白。</span><span class="sxs-lookup"><span data-stu-id="fc3f4-123">This example removes leading spaces from the **FirstName** column.</span></span>  
  
```  
LTRIM(FirstName)  
```  
  
 <span data-ttu-id="fc3f4-124">此範例會移除 **FirstName** 變數的開頭空白。</span><span class="sxs-lookup"><span data-stu-id="fc3f4-124">This example removes leading spaces from the **FirstName** variable.</span></span>  
  
```  
LTRIM(@FirstName)  
```  
  
## <a name="see-also"></a><span data-ttu-id="fc3f4-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc3f4-125">See Also</span></span>  
 <span data-ttu-id="fc3f4-126">[RTRIM &#40;SSIS 運算式&#41;](trim-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="fc3f4-126">[RTRIM &#40;SSIS Expression&#41;](trim-ssis-expression.md) </span></span>  
 <span data-ttu-id="fc3f4-127">[TRIM &#40;SSIS 運算式&#41;](trim-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="fc3f4-127">[TRIM &#40;SSIS Expression&#41;](trim-ssis-expression.md) </span></span>  
 [<span data-ttu-id="fc3f4-128">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fc3f4-128">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
