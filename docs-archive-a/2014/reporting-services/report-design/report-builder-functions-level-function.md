---
title: Level 函式 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 41235402-bb9e-4cb7-b91e-431e77db19cf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dedbf00ce8330242c95e9592f649d95171f0987a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595715"
---
# <a name="level-function-report-builder-and-ssrs"></a><span data-ttu-id="2a875-102">Level 函數 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="2a875-102">Level Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="2a875-103">傳回遞迴階層中之目前所在的層級。</span><span class="sxs-lookup"><span data-stu-id="2a875-103">Returns the current level of depth in a recursive hierarchy.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="2a875-104">語法</span><span class="sxs-lookup"><span data-stu-id="2a875-104">Syntax</span></span>  
  
```  
  
Level(scope)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2a875-105">參數</span><span class="sxs-lookup"><span data-stu-id="2a875-105">Parameters</span></span>  
 <span data-ttu-id="2a875-106">*範圍 (scope)*</span><span class="sxs-lookup"><span data-stu-id="2a875-106">*scope*</span></span>  
 <span data-ttu-id="2a875-107">(`String`) (選擇性)。</span><span class="sxs-lookup"><span data-stu-id="2a875-107">(`String`) (Optional).</span></span> <span data-ttu-id="2a875-108">包含要套用彙總函式之報表項目的資料集、群組或資料區的名稱。</span><span class="sxs-lookup"><span data-stu-id="2a875-108">The name of a dataset, group, or data region that contains the report items to which to apply the aggregate function.</span></span> <span data-ttu-id="2a875-109">如果未指定 *scope* ，則使用目前的範圍。</span><span class="sxs-lookup"><span data-stu-id="2a875-109">If *scope* is not specified, the current scope is used.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="2a875-110">傳回類型</span><span class="sxs-lookup"><span data-stu-id="2a875-110">Return Type</span></span>  
 <span data-ttu-id="2a875-111">傳回 `Integer`。</span><span class="sxs-lookup"><span data-stu-id="2a875-111">Returns an `Integer`.</span></span> <span data-ttu-id="2a875-112">如果*scope*指定資料集或資料區域，或指定非遞迴群組 (也就是不含元素) 的群組，則會傳回 `Parent` `Level` 0。</span><span class="sxs-lookup"><span data-stu-id="2a875-112">If *scope* specifies a dataset or data region, or specifies a nonrecursive grouping (that is, a grouping with no `Parent` element), `Level` returns 0.</span></span> <span data-ttu-id="2a875-113">如果省略 *scope* ，則會傳回目前範圍的層級。</span><span class="sxs-lookup"><span data-stu-id="2a875-113">If *scope* is omitted, it returns the level of the current scope.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a875-114">備註</span><span class="sxs-lookup"><span data-stu-id="2a875-114">Remarks</span></span>  
 <span data-ttu-id="2a875-115">`Level` 函數傳回的值是以零為基礎；亦即，階層中的第一個層級是 0。</span><span class="sxs-lookup"><span data-stu-id="2a875-115">The value returned by the `Level` function is zero based; that is, the first level in a hierarchy is 0.</span></span>  
  
 <span data-ttu-id="2a875-116">`Level` 函數可以在遞迴階層 (例如員工清單) 中提供縮排。</span><span class="sxs-lookup"><span data-stu-id="2a875-116">The `Level` function can be used to provide indentation in a recursive hierarchy, such as an employee list.</span></span>  
  
 <span data-ttu-id="2a875-117">如需遞迴階層的詳細資訊，請參閱[建立遞迴階層群組 &#40;報表產生器及 SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="2a875-117">For more information about recursive hierarchies, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a875-118">範例</span><span class="sxs-lookup"><span data-stu-id="2a875-118">Example</span></span>  
 <span data-ttu-id="2a875-119">下列程式碼範例提供 Employees 群組中的資料列層級：</span><span class="sxs-lookup"><span data-stu-id="2a875-119">The following code example provides the level of row in the Employees group:</span></span>  
  
```  
=Level("Employees")  
```  
  
## <a name="see-also"></a><span data-ttu-id="2a875-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a875-120">See Also</span></span>  
 <span data-ttu-id="2a875-121">[報表中的運算式用法 &#40;報表產生器及 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2a875-121">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2a875-122">[運算式範例 &#40;報表產生器及 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2a875-122">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2a875-123">[運算式中的資料類型 &#40;報表產生器及 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2a875-123">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="2a875-124">總計、彙總與內建集合的運算式範圍 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="2a875-124">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
