---
title: RTRIM (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- RTRIM function
- trailing blanks
ms.assetid: 529bd43e-3f8a-4682-a33e-569176aa7fc4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 727c30fd72bfca5676b71f4ba42e936a9b926817
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701395"
---
# <a name="rtrim-ssis-expression"></a><span data-ttu-id="15353-102">RTRIM (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="15353-102">RTRIM (SSIS Expression)</span></span>
  <span data-ttu-id="15353-103">傳回移除尾端空白之後的字元運算式。</span><span class="sxs-lookup"><span data-stu-id="15353-103">Returns a character expression after removing trailing spaces.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="15353-104">RTRIM 不會移除空白字元，例如 Tab 鍵或換行字元。</span><span class="sxs-lookup"><span data-stu-id="15353-104">RTRIM does not remove white space characters such as the tab or line feed characters.</span></span> <span data-ttu-id="15353-105">Unicode 會為許多不同類型的空格提供字碼指標，但此功能只會辨識 Unicode 字碼指標 0x0020。</span><span class="sxs-lookup"><span data-stu-id="15353-105">Unicode provides code points for many different types of spaces, but this function recognizes only the Unicode code point 0x0020.</span></span> <span data-ttu-id="15353-106">當將雙位元組字集 (DBCS) 字串轉換為 Unicode 時，它們可以包括 0x0020 以外的空格字元，但此功能無法移除這些空格。</span><span class="sxs-lookup"><span data-stu-id="15353-106">When double-byte character set (DBCS) strings are converted to Unicode they may include space characters other than 0x0020 and the function cannot remove such spaces.</span></span> <span data-ttu-id="15353-107">若要移除所有種類的空格，您可以在從「指令碼」元件執行的指令碼中使用 Microsoft Visual Basic .NET RTrim 方法。</span><span class="sxs-lookup"><span data-stu-id="15353-107">To remove all kinds of spaces, you can use the Microsoft Visual Basic .NET RTrim method in a script run from the Script component.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15353-108">語法</span><span class="sxs-lookup"><span data-stu-id="15353-108">Syntax</span></span>  
  
```  
  
RTRIM(character expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="15353-109">引數</span><span class="sxs-lookup"><span data-stu-id="15353-109">Arguments</span></span>  
 <span data-ttu-id="15353-110">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="15353-110">*character_expression*</span></span>  
 <span data-ttu-id="15353-111">要移除空白的字元運算式。</span><span class="sxs-lookup"><span data-stu-id="15353-111">Is a character expression from which to remove spaces.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="15353-112">結果類型</span><span class="sxs-lookup"><span data-stu-id="15353-112">Result Types</span></span>  
 <span data-ttu-id="15353-113">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="15353-113">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15353-114">備註</span><span class="sxs-lookup"><span data-stu-id="15353-114">Remarks</span></span>  
 <span data-ttu-id="15353-115">RTRIM 只適用於 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="15353-115">RTRIM works only with the DT_WSTR data type.</span></span> <span data-ttu-id="15353-116">如果 *character_expression* 引數是字串常值或具有 DT_STR 資料類型的資料行，則該引數會在 RTRIM 執行其作業前隱含轉換成 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="15353-116">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before RTRIM performs its operation.</span></span> <span data-ttu-id="15353-117">其他資料類型必須明確地轉換為 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="15353-117">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="15353-118">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)和[轉換 &#40;SSIS 運算式&#41;](cast-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="15353-118">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="15353-119">如果引數為 Null，則 RTRIM 會傳回 Null 結果。</span><span class="sxs-lookup"><span data-stu-id="15353-119">RTRIM returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="15353-120">運算式範例</span><span class="sxs-lookup"><span data-stu-id="15353-120">Expression Examples</span></span>  
 <span data-ttu-id="15353-121">此範例會移除字串常值尾端的空白。</span><span class="sxs-lookup"><span data-stu-id="15353-121">This example removes trailing spaces from a string literal.</span></span> <span data-ttu-id="15353-122">傳回結果為「Hello」。</span><span class="sxs-lookup"><span data-stu-id="15353-122">The return result is "Hello".</span></span>  
  
```  
RTRIM("Hello   ")  
```  
  
 <span data-ttu-id="15353-123">此範例會移除 **FirstName** 和 **LastName** 資料行串連尾端的空白。</span><span class="sxs-lookup"><span data-stu-id="15353-123">This example removes trailing spaces from a concatenation of the **FirstName** and **LastName** columns.</span></span>  
  
```  
RTRIM(FirstName + " " + LastName)  
```  
  
 <span data-ttu-id="15353-124">此範例會移除 **FirstName** 變數尾端的空白。</span><span class="sxs-lookup"><span data-stu-id="15353-124">This example removes trailing spaces from the **FirstName** variable.</span></span>  
  
```  
RTRIM(@FirstName)  
```  
  
## <a name="see-also"></a><span data-ttu-id="15353-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15353-125">See Also</span></span>  
 <span data-ttu-id="15353-126">[LTRIM &#40;SSIS 運算式&#41;](trim-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="15353-126">[LTRIM &#40;SSIS Expression&#41;](trim-ssis-expression.md) </span></span>  
 <span data-ttu-id="15353-127">[TRIM &#40;SSIS 運算式&#41;](trim-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="15353-127">[TRIM &#40;SSIS Expression&#41;](trim-ssis-expression.md) </span></span>  
 [<span data-ttu-id="15353-128">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="15353-128">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
