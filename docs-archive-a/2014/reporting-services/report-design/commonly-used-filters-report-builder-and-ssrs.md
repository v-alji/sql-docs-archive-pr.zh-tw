---
title: 常用的篩選 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- multivalued parameters [Reporting Services]
- single-valued parameters [Reporting Services]
- parameters [Reporting Services], multivalued
- valid values [Reporting Services]
ms.assetid: cb70d0cd-707b-4de5-b39f-e4eb57d316aa
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 201cf83d431d1b61e0f20e9d039b2016ad4f13e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596499"
---
# <a name="commonly-used-filters-report-builder-and-ssrs"></a><span data-ttu-id="be1fe-102">常用的篩選 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="be1fe-102">Commonly Used Filters (Report Builder and SSRS)</span></span>
  <span data-ttu-id="be1fe-103">若要建立篩選，您必須指定一個或多個篩選方程式。</span><span class="sxs-lookup"><span data-stu-id="be1fe-103">To create a filter, you must specify one or more filter equations.</span></span> <span data-ttu-id="be1fe-104">篩選方程式包含運算式、資料類型、運算子和值。</span><span class="sxs-lookup"><span data-stu-id="be1fe-104">A filter equation includes an expression, a data type, an operator, and a value.</span></span> <span data-ttu-id="be1fe-105">本主題提供常用的篩選範例。</span><span class="sxs-lookup"><span data-stu-id="be1fe-105">This topic provides examples of commonly used filters.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="filter-examples"></a><span data-ttu-id="be1fe-106">篩選範例</span><span class="sxs-lookup"><span data-stu-id="be1fe-106">Filter Examples</span></span>  
 <span data-ttu-id="be1fe-107">下表說明使用不同資料類型和不同運算子的篩選方程式範例。</span><span class="sxs-lookup"><span data-stu-id="be1fe-107">The following table shows examples of filter equations that use different data types and different operators.</span></span> <span data-ttu-id="be1fe-108">比較的範圍是由定義篩選的報表項目所決定。</span><span class="sxs-lookup"><span data-stu-id="be1fe-108">The scope for the comparison is determined by report item for which a filter is defined.</span></span> <span data-ttu-id="be1fe-109">例如，如果是資料集上所定義的篩選， **TOP % 10** 就是資料集中前百分之 10 的值；如果是群組上所定義的篩選， **TOP % 10** 就是群組中前百分之 10 的值。</span><span class="sxs-lookup"><span data-stu-id="be1fe-109">For example, for a filter defined on a dataset, **TOP % 10** is the top 10 percent of values in the dataset; for a filter defined on a group, **TOP % 10** is the top 10 percent of values in the group.</span></span>  
  
|<span data-ttu-id="be1fe-110">簡單運算式</span><span class="sxs-lookup"><span data-stu-id="be1fe-110">Simple Expression</span></span>|<span data-ttu-id="be1fe-111">資料類型</span><span class="sxs-lookup"><span data-stu-id="be1fe-111">Data Type</span></span>|<span data-ttu-id="be1fe-112">運算子</span><span class="sxs-lookup"><span data-stu-id="be1fe-112">Operator</span></span>|<span data-ttu-id="be1fe-113">值</span><span class="sxs-lookup"><span data-stu-id="be1fe-113">Value</span></span>|<span data-ttu-id="be1fe-114">描述</span><span class="sxs-lookup"><span data-stu-id="be1fe-114">Description</span></span>|  
|-----------------------|---------------|--------------|-----------|-----------------|  
|`[SUM(Quantity)]`|`Integer`|`>`|`7`|<span data-ttu-id="be1fe-115">包含大於 7 的資料值。</span><span class="sxs-lookup"><span data-stu-id="be1fe-115">Includes data values that are greater than 7.</span></span>|  
|`[SUM(Quantity)]`|`Integer`|`TOP N`|`10`|<span data-ttu-id="be1fe-116">包含前 10 大資料值。</span><span class="sxs-lookup"><span data-stu-id="be1fe-116">Includes the top 10 data values.</span></span>|  
|`[SUM(Quantity)]`|`Integer`|`TOP %`|`20`|<span data-ttu-id="be1fe-117">包含前百分之 20 的資料值。</span><span class="sxs-lookup"><span data-stu-id="be1fe-117">Includes the top 20% of data values.</span></span>|  
|`[Sales]`|`Text`|`>`|`=CDec(100)`|<span data-ttu-id="be1fe-118">包含所有大於 $100 之 System.Decimal 類型 (SQL "money" 資料類型) 的值。</span><span class="sxs-lookup"><span data-stu-id="be1fe-118">Includes all values of type System.Decimal (SQL "money" data types) greater than $100.</span></span>|  
|`[OrderDate]`|`DateTime`|`>`|`2088-01-01`|<span data-ttu-id="be1fe-119">包含從 2008 年 1 月 1 日到目前的所有日期。</span><span class="sxs-lookup"><span data-stu-id="be1fe-119">Includes all dates from January 1, 2008 to the present date.</span></span>|  
|`[OrderDate]`|`DateTime`|`BETWEEN`|`2008-01-01`<br /><br /> `2008-02-01`|<span data-ttu-id="be1fe-120">包含從 2008 年 1 月 1 日 (含) 算起的日期。</span><span class="sxs-lookup"><span data-stu-id="be1fe-120">Includes dates from January 1, 2008 up to and including February 1, 2008.</span></span>|  
|`[Territory]`|`Text`|`LIKE`|`*east`|<span data-ttu-id="be1fe-121">所有以 "east" 結尾的領域名稱。</span><span class="sxs-lookup"><span data-stu-id="be1fe-121">All territory names that end in "east".</span></span>|  
|`[Territory]`|`Text`|`LIKE`|`%o%th*`|<span data-ttu-id="be1fe-122">所有在名稱開頭包含 North 和 South 的領域名稱。</span><span class="sxs-lookup"><span data-stu-id="be1fe-122">All territory names that include North and South at the beginning of the name.</span></span>|  
|`=LEFT(Fields!Subcat.Value,1)`|`Text`|`IN`|`B, C, T`|<span data-ttu-id="be1fe-123">所有以字母 B、C 或 T 為開頭的子類別目錄值。</span><span class="sxs-lookup"><span data-stu-id="be1fe-123">All subcategory values that begin with the letters B, C, or T.</span></span>|  
  
## <a name="examples-with-report-parameters"></a><span data-ttu-id="be1fe-124">報表參數的範例</span><span class="sxs-lookup"><span data-stu-id="be1fe-124">Examples with Report Parameters</span></span>  
 <span data-ttu-id="be1fe-125">下表提供篩選運算式的範例，其中包含了單一值或多重值的參數參考。</span><span class="sxs-lookup"><span data-stu-id="be1fe-125">The following table provides examples of filter expression that includes a single-value or multivalue parameter reference.</span></span>  
  
|<span data-ttu-id="be1fe-126">參數類型</span><span class="sxs-lookup"><span data-stu-id="be1fe-126">Parameter type</span></span>|<span data-ttu-id="be1fe-127">(篩選) 運算式</span><span class="sxs-lookup"><span data-stu-id="be1fe-127">(Filter) Expression</span></span>|<span data-ttu-id="be1fe-128">運算子</span><span class="sxs-lookup"><span data-stu-id="be1fe-128">Operator</span></span>|<span data-ttu-id="be1fe-129">值</span><span class="sxs-lookup"><span data-stu-id="be1fe-129">Value</span></span>|<span data-ttu-id="be1fe-130">資料類型</span><span class="sxs-lookup"><span data-stu-id="be1fe-130">Data Type</span></span>|  
|--------------------|---------------------------|--------------|-----------|---------------|  
|<span data-ttu-id="be1fe-131">單一值</span><span class="sxs-lookup"><span data-stu-id="be1fe-131">Single value</span></span>|`[EmployeeID]`|=|`[@EmployeeID]`|<span data-ttu-id="be1fe-132">整數</span><span class="sxs-lookup"><span data-stu-id="be1fe-132">Integer</span></span>|  
|<span data-ttu-id="be1fe-133">多重值</span><span class="sxs-lookup"><span data-stu-id="be1fe-133">Multivalue</span></span>|`[EmployeeID]`|<span data-ttu-id="be1fe-134">IN</span><span class="sxs-lookup"><span data-stu-id="be1fe-134">IN</span></span>|`[@EmployeeID]`|<span data-ttu-id="be1fe-135">整數</span><span class="sxs-lookup"><span data-stu-id="be1fe-135">Integer</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="be1fe-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be1fe-136">See Also</span></span>  
 <span data-ttu-id="be1fe-137">[報表參數 &#40;報表產生器和報表設計師&#41;](report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="be1fe-137">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="be1fe-138">[新增資料集篩選、資料區域篩選和群組篩選 &#40;報表產生器和 SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="be1fe-138">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="be1fe-139">[運算式用於報表 &#40;報表產生器和 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="be1fe-139">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="be1fe-140">[運算式範例 &#40;報表產生器及 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="be1fe-140">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="be1fe-141">運算式中的資料類型 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="be1fe-141">Data Types in Expressions &#40;Report Builder and SSRS&#41;</span></span>](expressions-report-builder-and-ssrs.md)  
  
  
