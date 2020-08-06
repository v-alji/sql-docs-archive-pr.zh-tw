---
title: InScope 函式 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a8cd209a-e5d3-4dce-ab2d-f271f6c54955
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 62c4ad5de7af1ac0762df29deaa17953a8a378db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595717"
---
# <a name="inscope-function-report-builder-and-ssrs"></a><span data-ttu-id="0a607-102">InScope 函數 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="0a607-102">InScope Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="0a607-103">指出某個項目目前的執行個體是否在指定的範圍內。</span><span class="sxs-lookup"><span data-stu-id="0a607-103">Indicates whether the current instance of an item is in the specified scope.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="0a607-104">語法</span><span class="sxs-lookup"><span data-stu-id="0a607-104">Syntax</span></span>  
  
```  
InScope(scope)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0a607-105">參數</span><span class="sxs-lookup"><span data-stu-id="0a607-105">Parameters</span></span>  
 <span data-ttu-id="0a607-106">*範圍 (scope)*</span><span class="sxs-lookup"><span data-stu-id="0a607-106">*scope*</span></span>  
 <span data-ttu-id="0a607-107">(`String`) 指定範圍之資料集、資料區域或群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="0a607-107">(`String`) The name of a dataset, data region, or group that specifies a scope.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="0a607-108">傳回類型</span><span class="sxs-lookup"><span data-stu-id="0a607-108">Return Type</span></span>  
 <span data-ttu-id="0a607-109">傳回 `Boolean`。</span><span class="sxs-lookup"><span data-stu-id="0a607-109">Returns a `Boolean`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a607-110">備註</span><span class="sxs-lookup"><span data-stu-id="0a607-110">Remarks</span></span>  
 <span data-ttu-id="0a607-111">函式會 `InScope` 測試報表專案目前實例的範圍，以尋找*範圍*參數所指定之範圍中的成員資格。</span><span class="sxs-lookup"><span data-stu-id="0a607-111">The `InScope` function tests the scope of the current instance of a report item for membership in the scope specified by the *scope*parameter.</span></span>  
  
 <span data-ttu-id="0a607-112">*Scope* 不能是運算式。</span><span class="sxs-lookup"><span data-stu-id="0a607-112">*Scope* cannot be an expression.</span></span>  
  
 <span data-ttu-id="0a607-113">`InScope` 函數一般會用於具有動態範圍的資料區域。</span><span class="sxs-lookup"><span data-stu-id="0a607-113">A typical use for the `InScope` function is in data regions that have dynamic scoping.</span></span> <span data-ttu-id="0a607-114">例如，資料區域資料格中的鑽研連結可以利用 `InScope`，根據按下的資料格來提供不同的報表名稱和不同組的參數。</span><span class="sxs-lookup"><span data-stu-id="0a607-114">For example, `InScope` can be used in a drillthrough link in a data region cells to provide a different report name and different sets of parameters depending on which cell is clicked.</span></span> <span data-ttu-id="0a607-115">此範例如下：</span><span class="sxs-lookup"><span data-stu-id="0a607-115">An example of this is as follows:</span></span>  
  
-   <span data-ttu-id="0a607-116">下列運算式是用做鑽研連結中的報表名稱，如果按下的資料格是在 `ProductDetail` 群組中，便會開啟 `Month` 報表，如果不是，便開啟 `ProductSummary` 報表。</span><span class="sxs-lookup"><span data-stu-id="0a607-116">The following expression, used as the report name in a drillthrough link, opens the `ProductDetail` report if the clicked cell is in the `Month` group, and the `ProductSummary` report if it is not.</span></span>  
  
    ```  
    =Iif(InScope("Month"), "ProductDetail", "ProductSummary")  
    ```  
  
-   <span data-ttu-id="0a607-117">下列運算式會用於鑽研報表參數的 `Omit` 屬性，只有按下的資料格在 `Product` 群組中時，才會將參數傳給目標報表。</span><span class="sxs-lookup"><span data-stu-id="0a607-117">The following expression, used in the `Omit` property of a drillthrough report parameter, will pass the parameter to the target report only if the clicked cell is in the `Product` group.</span></span>  
  
    ```  
    =Not(InScope("Product"))  
    ```  
  
 <span data-ttu-id="0a607-118">如需詳細資訊，請參閱[彙總函式參考 &#40;報表產生器及 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) 和[總計、彙總與內建集合的運算式範圍 &#40;報表產生器及 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="0a607-118">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a607-119">範例</span><span class="sxs-lookup"><span data-stu-id="0a607-119">Example</span></span>  
 <span data-ttu-id="0a607-120">下列程式碼範例指出項目目前的執行個體是否位在 `Product` 資料集、資料區域或群組的範圍中。</span><span class="sxs-lookup"><span data-stu-id="0a607-120">The following code example indicates whether the current instance of the item is in the `Product` dataset, data region, or group scope.</span></span>  
  
```  
=InScope("Product")  
```  
  
## <a name="see-also"></a><span data-ttu-id="0a607-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a607-121">See Also</span></span>  
 <span data-ttu-id="0a607-122">[報表中的運算式用法 &#40;報表產生器及 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0a607-122">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="0a607-123">[運算式範例 &#40;報表產生器及 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0a607-123">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="0a607-124">[運算式中的資料類型 &#40;報表產生器及 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0a607-124">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="0a607-125">總計、彙總與內建集合的運算式範圍 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="0a607-125">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
