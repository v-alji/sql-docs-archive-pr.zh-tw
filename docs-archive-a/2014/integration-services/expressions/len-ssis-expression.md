---
title: LEN (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- LEN function
- number of characters
ms.assetid: d961398b-e4d0-4936-be17-8f4c5882a640
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8863864168295a3a9a924df588312ee65b6f7fa7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594599"
---
# <a name="len-ssis-expression"></a><span data-ttu-id="7df3d-102">LEN (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="7df3d-102">LEN (SSIS Expression)</span></span>
  <span data-ttu-id="7df3d-103">傳回字元運算式中的字元數。</span><span class="sxs-lookup"><span data-stu-id="7df3d-103">Returns the number of characters in a character expression.</span></span> <span data-ttu-id="7df3d-104">如果字串包含開頭和尾端空白，則函數會將它們加入計數中。</span><span class="sxs-lookup"><span data-stu-id="7df3d-104">If the string includes leading and trailing blanks, the function includes them in the count.</span></span> <span data-ttu-id="7df3d-105">LEN 會針對單位元組和雙位元組字元的相同字串傳回完全相同的值。</span><span class="sxs-lookup"><span data-stu-id="7df3d-105">LEN returns identical values for the same string of single and double byte characters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7df3d-106">語法</span><span class="sxs-lookup"><span data-stu-id="7df3d-106">Syntax</span></span>  
  
```  
  
LEN(character_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="7df3d-107">引數</span><span class="sxs-lookup"><span data-stu-id="7df3d-107">Arguments</span></span>  
 <span data-ttu-id="7df3d-108">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="7df3d-108">*character_expression*</span></span>  
 <span data-ttu-id="7df3d-109">是要評估的運算式。</span><span class="sxs-lookup"><span data-stu-id="7df3d-109">Is the expression to evaluate.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="7df3d-110">結果類型</span><span class="sxs-lookup"><span data-stu-id="7df3d-110">Result Types</span></span>  
 <span data-ttu-id="7df3d-111">DT_I4</span><span class="sxs-lookup"><span data-stu-id="7df3d-111">DT_I4</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7df3d-112">備註</span><span class="sxs-lookup"><span data-stu-id="7df3d-112">Remarks</span></span>  
 <span data-ttu-id="7df3d-113">*character_expression* 引數可以是 DT_WSTR、DT_TEXT、DT_NTEXT 或 DT_IMAGE 資料類型。</span><span class="sxs-lookup"><span data-stu-id="7df3d-113">The *character_expression* argument can be a DT_WSTR, DT_TEXT, DT_NTEXT, or DT_IMAGE data type.</span></span> <span data-ttu-id="7df3d-114">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="7df3d-114">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="7df3d-115">如果 *character_expression* 是字串常值或具有 DT_STR 資料類型的資料行，則它會在 LEN 執行其作業前隱含轉換成 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="7df3d-115">If *character_expression* is a string literal or a data column with the DT_STR data type, it is implicitly cast to the DT_WSTR data type before LEN performs its operation.</span></span> <span data-ttu-id="7df3d-116">其他資料類型必須明確地轉換為 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="7df3d-116">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="7df3d-117">如需詳細資訊，請參閱 [Cast &#40;SSIS 運算式&#41;](cast-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="7df3d-117">For more information, see [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="7df3d-118">如果傳遞至 LEN 函數的引數資料類型為「二進位大型物件區塊」(Binary Large Object Block，BLOB)，例如 DT_TEXT、DT_NTEXT 或 DT_IMAGE，則函數會傳回位元組計數。</span><span class="sxs-lookup"><span data-stu-id="7df3d-118">If the argument passed to the LEN function has a Binary Large Object Block (BLOB) data type, such as DT_TEXT, DT_NTEXT, or DT_IMAGE, the function returns a byte count.</span></span>  
  
 <span data-ttu-id="7df3d-119">如果引數為 Null，則 LEN 會傳回 Null 結果。</span><span class="sxs-lookup"><span data-stu-id="7df3d-119">LEN returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="7df3d-120">運算式範例</span><span class="sxs-lookup"><span data-stu-id="7df3d-120">Expression Examples</span></span>  
 <span data-ttu-id="7df3d-121">此範例會傳回字串常值的長度。</span><span class="sxs-lookup"><span data-stu-id="7df3d-121">This example returns the length of a string literal.</span></span> <span data-ttu-id="7df3d-122">傳回結果為 12。</span><span class="sxs-lookup"><span data-stu-id="7df3d-122">The return result is 12.</span></span>  
  
```  
LEN("Ball Bearing")  
```  
  
 <span data-ttu-id="7df3d-123">此範例會傳回 **FirstName** 和 **LastName** 資料行中各值長度之間的差異。</span><span class="sxs-lookup"><span data-stu-id="7df3d-123">This example returns the difference between the length of values in the **FirstName** and **LastName** columns.</span></span>  
  
```  
LEN(FirstName) - LEN(LastName)  
```  
  
 <span data-ttu-id="7df3d-124">使用「系統」變數 **MachineName**傳回電腦名稱的長度。</span><span class="sxs-lookup"><span data-stu-id="7df3d-124">Returns the length of a computer name using the System variable **MachineName**.</span></span>  
  
```  
LEN(@MachineName)  
```  
  
## <a name="see-also"></a><span data-ttu-id="7df3d-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7df3d-125">See Also</span></span>  
 [<span data-ttu-id="7df3d-126">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="7df3d-126">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
