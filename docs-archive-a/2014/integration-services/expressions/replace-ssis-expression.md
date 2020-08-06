---
title: REPLACE (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- replacing string expression
- REPLACE function
ms.assetid: a6837043-ea70-4c6a-9c7a-6868b02b2adc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e483ba6c9c72cb777f2955929a717c6c2e17a8c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701422"
---
# <a name="replace-ssis-expression"></a><span data-ttu-id="e9bd5-102">REPLACE (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="e9bd5-102">REPLACE (SSIS Expression)</span></span>
  <span data-ttu-id="e9bd5-103">以不同的字元字串或空白字串取代運算式中的字元字串後，傳回字元運算式。</span><span class="sxs-lookup"><span data-stu-id="e9bd5-103">Returns a character expression after replacing a character string within the expression with either a different character string or an empty string.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e9bd5-104">REPLACE 函數經常會使用長的字串。</span><span class="sxs-lookup"><span data-stu-id="e9bd5-104">The REPLACE function frequently uses long strings.</span></span> <span data-ttu-id="e9bd5-105">截斷的結果可正常地處理，或造成警告或錯誤。</span><span class="sxs-lookup"><span data-stu-id="e9bd5-105">The consequences of truncation can be handled gracefully or cause a warning or an error.</span></span> <span data-ttu-id="e9bd5-106">如需詳細資訊，請參閱[語法 &#40;SSIS&#41;](syntax-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="e9bd5-106">For more information, see [Syntax &#40;SSIS&#41;](syntax-ssis.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9bd5-107">語法</span><span class="sxs-lookup"><span data-stu-id="e9bd5-107">Syntax</span></span>  
  
```  
  
REPLACE(character_expression,searchstring,replacementstring)  
```  
  
## <a name="arguments"></a><span data-ttu-id="e9bd5-108">引數</span><span class="sxs-lookup"><span data-stu-id="e9bd5-108">Arguments</span></span>  
 <span data-ttu-id="e9bd5-109">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="e9bd5-109">*character_expression*</span></span>  
 <span data-ttu-id="e9bd5-110">為函數搜尋的有效字元運算式。</span><span class="sxs-lookup"><span data-stu-id="e9bd5-110">Is a valid character expression that the function searches.</span></span>  
  
 <span data-ttu-id="e9bd5-111">*searchstring*</span><span class="sxs-lookup"><span data-stu-id="e9bd5-111">*searchstring*</span></span>  
 <span data-ttu-id="e9bd5-112">為函數嘗試尋找的有效字元運算式。</span><span class="sxs-lookup"><span data-stu-id="e9bd5-112">Is a valid character expression that the function attempts to locate.</span></span>  
  
 <span data-ttu-id="e9bd5-113">*replacementstring*</span><span class="sxs-lookup"><span data-stu-id="e9bd5-113">*replacementstring*</span></span>  
 <span data-ttu-id="e9bd5-114">為取代運算式的有效字元運算式。</span><span class="sxs-lookup"><span data-stu-id="e9bd5-114">Is a valid character expression that is the replacement expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="e9bd5-115">結果類型</span><span class="sxs-lookup"><span data-stu-id="e9bd5-115">Result Types</span></span>  
 <span data-ttu-id="e9bd5-116">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="e9bd5-116">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9bd5-117">備註</span><span class="sxs-lookup"><span data-stu-id="e9bd5-117">Remarks</span></span>  
 <span data-ttu-id="e9bd5-118">*searchstring* 的長度不得為零。</span><span class="sxs-lookup"><span data-stu-id="e9bd5-118">The length of *searchstring* must not be zero.</span></span>  
  
 <span data-ttu-id="e9bd5-119">*replacementstring* 的長度可以為零。</span><span class="sxs-lookup"><span data-stu-id="e9bd5-119">The length of *replacementstring* may be zero.</span></span>  
  
 <span data-ttu-id="e9bd5-120">*searchstring* 和 *replacementstring* 引數可使用變數和資料行。</span><span class="sxs-lookup"><span data-stu-id="e9bd5-120">The *searchstring* and *replacementstring* arguments can use variables and columns.</span></span>  
  
 <span data-ttu-id="e9bd5-121">REPLACE 只適用於 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="e9bd5-121">REPLACE works only with the DT_WSTR data type.</span></span> <span data-ttu-id="e9bd5-122">為字串常值或具有 DT_STR 資料類型之資料行的*character_expression1、character_expression2* 和 *character_expression3* 引數，會在 REPLACE 執行其作業之前隱含轉換為 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="e9bd5-122">*character_expression1, character_expression2,* and *character_expression3* arguments that are string literals or data columns with the DT_STR data type are implicitly cast to the DT_WSTR data type before REPLACE performs its operation.</span></span> <span data-ttu-id="e9bd5-123">其他資料類型必須明確地轉換為 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="e9bd5-123">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="e9bd5-124">如需詳細資訊，請參閱 [Cast &#40;SSIS 運算式&#41;](cast-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="e9bd5-124">For more information, see [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="e9bd5-125">如果任何引數為 Null，則 REPLACE 會傳回 Null 結果。</span><span class="sxs-lookup"><span data-stu-id="e9bd5-125">REPLACE returns a null result if any argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="e9bd5-126">運算式範例</span><span class="sxs-lookup"><span data-stu-id="e9bd5-126">Expression Examples</span></span>  
 <span data-ttu-id="e9bd5-127">這個範例使用字串常值。</span><span class="sxs-lookup"><span data-stu-id="e9bd5-127">This example uses a string literal.</span></span> <span data-ttu-id="e9bd5-128">傳回結果為「All Terrain Bike」。</span><span class="sxs-lookup"><span data-stu-id="e9bd5-128">The return result is "All Terrain Bike".</span></span>  
  
```  
REPLACE("Mountain Bike", "Mountain","All Terrain")  
```  
  
 <span data-ttu-id="e9bd5-129">此範例會從 **Product** 資料行移除「Bike」字串。</span><span class="sxs-lookup"><span data-stu-id="e9bd5-129">This example removes the string "Bike" from the **Product** column.</span></span>  
  
```  
REPLACE(Product, "Bike","")  
```  
  
 <span data-ttu-id="e9bd5-130">此範例會取代 **DaysToManufacture** 資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="e9bd5-130">This example replaces values in the **DaysToManufacture** column.</span></span> <span data-ttu-id="e9bd5-131">資料行的資料類型為整數，且運算式包含將 **DaysToManufacture** 轉換為 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="e9bd5-131">The column has an integer data type and the expression includes casting **DaysToManufacture** to the DT_WSTR data type.</span></span>  
  
```  
REPLACE((DT_WSTR,8)DaysToManufacture,"6","5")  
```  
  
## <a name="see-also"></a><span data-ttu-id="e9bd5-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9bd5-132">See Also</span></span>  
 <span data-ttu-id="e9bd5-133">[SUBSTRING &#40;SSIS 運算式&#41;](substring-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="e9bd5-133">[SUBSTRING &#40;SSIS Expression&#41;](substring-ssis-expression.md) </span></span>  
 [<span data-ttu-id="e9bd5-134">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="e9bd5-134">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
