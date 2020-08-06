---
title: CountRows 函式 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5b1c403d-6afd-44c8-b5f6-5ecff2a29a45
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6d5311dfc5dfcb89449a4039fdac4100fc5a3b47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595724"
---
# <a name="countrows-function-report-builder-and-ssrs"></a><span data-ttu-id="2b103-102">CountRows 函數 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="2b103-102">CountRows Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="2b103-103">傳回指定之範圍中的資料列數目，包括具有 Null 值的資料列。</span><span class="sxs-lookup"><span data-stu-id="2b103-103">Returns the number of rows in the specified scope, including rows with null values.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="2b103-104">語法</span><span class="sxs-lookup"><span data-stu-id="2b103-104">Syntax</span></span>  
  
```  
  
CountRows(scope, recursive)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2b103-105">參數</span><span class="sxs-lookup"><span data-stu-id="2b103-105">Parameters</span></span>  
 <span data-ttu-id="2b103-106">*範圍 (scope)*</span><span class="sxs-lookup"><span data-stu-id="2b103-106">*scope*</span></span>  
 <span data-ttu-id="2b103-107">(`String`) 包含要計數之報表項目的資料集、資料區域或群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="2b103-107">(`String`) The name of a dataset, data region, or group that contains the report items to count.</span></span>  
  
 <span data-ttu-id="2b103-108">*遞迴*</span><span class="sxs-lookup"><span data-stu-id="2b103-108">*recursive*</span></span>  
 <span data-ttu-id="2b103-109">(**列舉型別**) 選擇性。</span><span class="sxs-lookup"><span data-stu-id="2b103-109">(**Enumerated Type**) Optional.</span></span> <span data-ttu-id="2b103-110">`Simple` (預設值) 或 `RdlRecursive`。</span><span class="sxs-lookup"><span data-stu-id="2b103-110">`Simple` (default) or `RdlRecursive`.</span></span> <span data-ttu-id="2b103-111">指定是否要以遞迴方式執行彙總。</span><span class="sxs-lookup"><span data-stu-id="2b103-111">Specifies whether to perform the aggregation recursively.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="2b103-112">傳回類型</span><span class="sxs-lookup"><span data-stu-id="2b103-112">Return Type</span></span>  
 <span data-ttu-id="2b103-113">傳回 `Integer`。</span><span class="sxs-lookup"><span data-stu-id="2b103-113">Returns an `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b103-114">備註</span><span class="sxs-lookup"><span data-stu-id="2b103-114">Remarks</span></span>  
 <span data-ttu-id="2b103-115">`CountRows` 會計算指定之範圍中所有資料列的數目，包括具有 Null 值的資料列。</span><span class="sxs-lookup"><span data-stu-id="2b103-115">`CountRows` counts all rows in the specified scope, including rows that have null values.</span></span>  
  
 <span data-ttu-id="2b103-116">*scope* 的值不能為運算式，且必須參考目前的範圍或包含範圍。</span><span class="sxs-lookup"><span data-stu-id="2b103-116">The value of *scope* cannot be an expression and must refer to the current scope or a containing scope.</span></span>  
  
 <span data-ttu-id="2b103-117">如需詳細資訊，請參閱[彙總函式參考 &#40;報表產生器及 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) 和[總計、彙總與內建集合的運算式範圍 &#40;報表產生器及 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="2b103-117">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
 <span data-ttu-id="2b103-118">如需遞迴彙總的詳細資訊，請參閱[建立遞迴階層群組 &#40;報表產生器及 SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="2b103-118">For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b103-119">範例</span><span class="sxs-lookup"><span data-stu-id="2b103-119">Example</span></span>  
 <span data-ttu-id="2b103-120">下列程式碼範例顯示的運算式會計算名為 `GroupbyCategory` 的資料列群組中的資料列數目 (以 `[Category]`運算式為基礎)。</span><span class="sxs-lookup"><span data-stu-id="2b103-120">The following code example shows an expression that calculates the number of rows in a row group named `GroupbyCategory` (based on the expression `[Category]`).</span></span>  
  
```  
="Number of rows: " & CountRows("GroupbyCategory")  
```  
  
## <a name="see-also"></a><span data-ttu-id="2b103-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b103-121">See Also</span></span>  
 <span data-ttu-id="2b103-122">[報表中的運算式用法 &#40;報表產生器及 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2b103-122">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2b103-123">[運算式範例 &#40;報表產生器及 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2b103-123">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2b103-124">[運算式中的資料類型 &#40;報表產生器及 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2b103-124">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="2b103-125">總計、彙總與內建集合的運算式範圍 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="2b103-125">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
