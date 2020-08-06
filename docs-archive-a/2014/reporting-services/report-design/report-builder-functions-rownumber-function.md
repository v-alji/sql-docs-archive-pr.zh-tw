---
title: RowNumber 函式 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9d718ba8-d323-49fb-aac8-e7013a117b75
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9f3d16188138c2f268305fddb092d56be870a3f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595699"
---
# <a name="rownumber-function-report-builder-and-ssrs"></a><span data-ttu-id="9704e-102">RowNumber 函數 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="9704e-102">RowNumber Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="9704e-103">傳回指定範圍中資料列數的執行計數。</span><span class="sxs-lookup"><span data-stu-id="9704e-103">Returns a running count of the number of rows for the specified scope.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="9704e-104">語法</span><span class="sxs-lookup"><span data-stu-id="9704e-104">Syntax</span></span>  
  
```  
  
RowNumber(scope)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9704e-105">參數</span><span class="sxs-lookup"><span data-stu-id="9704e-105">Parameters</span></span>  
 <span data-ttu-id="9704e-106">*範圍 (scope)*</span><span class="sxs-lookup"><span data-stu-id="9704e-106">*scope*</span></span>  
 <span data-ttu-id="9704e-107">(`String`) 資料集、資料區域或群組的名稱，或為 Null (在 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 中為 `Nothing`)，指定要在其中評估資料列數的內容。</span><span class="sxs-lookup"><span data-stu-id="9704e-107">(`String`) The name of a dataset, data region, or group, or null (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]), that specifies the context in which to evaluate the number of rows.</span></span> <span data-ttu-id="9704e-108">`Nothing` 指定最外層的內容，這通常為報表資料集。</span><span class="sxs-lookup"><span data-stu-id="9704e-108">`Nothing` specifies the outermost context, usually the report dataset.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9704e-109">備註</span><span class="sxs-lookup"><span data-stu-id="9704e-109">Remarks</span></span>  
 <span data-ttu-id="9704e-110">`RowNumber`傳回指定範圍內資料列計數的執行值，如同[RunningValue](report-builder-functions-runningvalue-function.md)傳回彙總函式的執行值。</span><span class="sxs-lookup"><span data-stu-id="9704e-110">`RowNumber` returns a running value of the count of rows within the specified scope, just as [RunningValue](report-builder-functions-runningvalue-function.md) returns the running value of an aggregate function.</span></span> <span data-ttu-id="9704e-111">當您指定範圍時，可以指定何時要將資料列計數重設為 1。</span><span class="sxs-lookup"><span data-stu-id="9704e-111">When you specify a scope, you specify when to reset the row count to 1.</span></span>  
  
 <span data-ttu-id="9704e-112">*scope* 不可為運算式。</span><span class="sxs-lookup"><span data-stu-id="9704e-112">*scope* cannot be an expression.</span></span> <span data-ttu-id="9704e-113">*scope* 必須是包含範圍。</span><span class="sxs-lookup"><span data-stu-id="9704e-113">*scope* must be a containing scope.</span></span> <span data-ttu-id="9704e-114">就一般範圍而言，從最外層到最內層的內含項目依序為報表資料集、資料區域、資料列群組或資料行群組。</span><span class="sxs-lookup"><span data-stu-id="9704e-114">Typical scopes, from the outermost to the innermost containment, are report dataset, data region, row groups or column groups.</span></span>  
  
 <span data-ttu-id="9704e-115">若要在全部資料行中累加值，請將範圍指定為資料行群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="9704e-115">To increment values across columns, specify a scope that is the name of a column group.</span></span> <span data-ttu-id="9704e-116">若要在資料列中向下累加數目，請將範圍指定為資料列群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="9704e-116">To increment numbers down rows, specify a scope that is the name of a row group.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9704e-117">不支援在單一運算式中包含同時指定資料列群組和資料行群組的彙總。</span><span class="sxs-lookup"><span data-stu-id="9704e-117">Including aggregates that specify both a row group and a column group in a single expression is not supported.</span></span>  
  
 <span data-ttu-id="9704e-118">如需詳細資訊，請參閱[彙總函式參考 &#40;報表產生器及 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) 和[總計、彙總與內建集合的運算式範圍 &#40;報表產生器及 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="9704e-118">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
## <a name="code-example"></a><span data-ttu-id="9704e-119">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="9704e-119">Code Example</span></span>  
 <span data-ttu-id="9704e-120">下列的運算式可用於 Tablix 資料區域詳細資料列的 `BackgroundColor` 屬性，以改變每個群組的詳細資料列色彩 (永遠從白色開始)。</span><span class="sxs-lookup"><span data-stu-id="9704e-120">The following is an expression that you can use for the `BackgroundColor` property of a Tablix data region detail row to alternate the color of detail rows for each group, always beginning with White.</span></span>  
  
```  
=IIF(RowNumber("GroupbyCategory") Mod 2, "White", "PaleGreen")  
```  
  
## <a name="see-also"></a><span data-ttu-id="9704e-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9704e-121">See Also</span></span>  
 <span data-ttu-id="9704e-122">[報表中的運算式用法 &#40;報表產生器及 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9704e-122">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="9704e-123">[運算式範例 &#40;報表產生器及 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9704e-123">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="9704e-124">[運算式中的資料類型 &#40;報表產生器及 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9704e-124">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="9704e-125">總計、彙總與內建集合的運算式範圍 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9704e-125">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
