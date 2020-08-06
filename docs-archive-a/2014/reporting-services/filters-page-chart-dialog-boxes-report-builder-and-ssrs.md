---
title: 篩選頁面、圖表對話方塊 (報表產生器和 SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.categorygroupproperties.filters.f1
- "10409"
- sql12.rtp.rptdesigner.seriesgroupproperties.filters.f1
- "10401"
- sql12.rtp.rptdesigner.chartproperties.filters.f1
- "10165"
ms.assetid: fab97b2f-d53f-42f2-900c-c159653d89ed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 01d5054ce7d0c3e02d960885f149bd0ef209dc34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700855"
---
# <a name="filters-page-chart-dialog-boxes-report-builder-and-ssrs"></a><span data-ttu-id="777d8-102">篩選頁面、圖表對話方塊 ((報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="777d8-102">Filters page, Chart Dialog Boxes (Report Builder and SSRS)</span></span>
  <span data-ttu-id="777d8-103">按一下以下對話方塊中的 **[篩選]** ：</span><span class="sxs-lookup"><span data-stu-id="777d8-103">Click **Filters** in the:</span></span>  
  
-   <span data-ttu-id="777d8-104">**[類別目錄群組屬性]** 對話方塊，在依類別目錄分組的數列中篩選資料點。</span><span class="sxs-lookup"><span data-stu-id="777d8-104">**Category Group Properties** dialog box to filter data points in a series that has been grouped by category.</span></span>  
  
-   <span data-ttu-id="777d8-105">**[圖表屬性]** 對話方塊，定義圖表的篩選選項。</span><span class="sxs-lookup"><span data-stu-id="777d8-105">**Chart Properties** dialog box to define filtering options for the chart.</span></span>  
  
-   <span data-ttu-id="777d8-106">**[數列群組屬性]** 對話方塊，以限制選定群組中的數列數。</span><span class="sxs-lookup"><span data-stu-id="777d8-106">**Series Group Properties** dialog box to limit the number of series in the selected group.</span></span>  
  
## <a name="options"></a><span data-ttu-id="777d8-107">選項。</span><span class="sxs-lookup"><span data-stu-id="777d8-107">Options</span></span>  
 <span data-ttu-id="777d8-108">**加入**</span><span class="sxs-lookup"><span data-stu-id="777d8-108">**Add**</span></span>  
 <span data-ttu-id="777d8-109">按一下即可將新的篩選子句加入到清單。</span><span class="sxs-lookup"><span data-stu-id="777d8-109">Click to add a new filter clause to the list.</span></span>  
  
 <span data-ttu-id="777d8-110">**刪除**</span><span class="sxs-lookup"><span data-stu-id="777d8-110">**Delete**</span></span>  
 <span data-ttu-id="777d8-111">按一下即可從清單中刪除選取的篩選子句。</span><span class="sxs-lookup"><span data-stu-id="777d8-111">Click to delete the selected filter clause from the list.</span></span>  
  
 <span data-ttu-id="777d8-112">**向上箭頭**</span><span class="sxs-lookup"><span data-stu-id="777d8-112">**Up arrow**</span></span>  
 <span data-ttu-id="777d8-113">按一下即可將選取的篩選在清單中向上移動。</span><span class="sxs-lookup"><span data-stu-id="777d8-113">Click to move the selected filter up in the list.</span></span>  
  
 <span data-ttu-id="777d8-114">**向下箭頭**</span><span class="sxs-lookup"><span data-stu-id="777d8-114">**Down arrow**</span></span>  
 <span data-ttu-id="777d8-115">按一下即可將選取的篩選在清單中向下移動。</span><span class="sxs-lookup"><span data-stu-id="777d8-115">Click to move the selected filter down in the list.</span></span>  
  
 <span data-ttu-id="777d8-116">**運算式**</span><span class="sxs-lookup"><span data-stu-id="777d8-116">**Expression**</span></span>  
 <span data-ttu-id="777d8-117">輸入或選擇您要套用篩選的目標運算式。</span><span class="sxs-lookup"><span data-stu-id="777d8-117">Type or choose the expression to which you want to apply a filter.</span></span> <span data-ttu-id="777d8-118">按一下運算式 (**fx**) ] 按鈕，即可編輯運算式。</span><span class="sxs-lookup"><span data-stu-id="777d8-118">Click the Expression (**fx**) button to edit the expression.</span></span>  
  
 <span data-ttu-id="777d8-119">**Data type**</span><span class="sxs-lookup"><span data-stu-id="777d8-119">**Data type**</span></span>  
 <span data-ttu-id="777d8-120">選擇 [值]\*\*\*\* 的資料類型。</span><span class="sxs-lookup"><span data-stu-id="777d8-120">Choose the data type for **Value**.</span></span> <span data-ttu-id="777d8-121">可能的話，請選擇符合 **[運算式]** 資料類型的資料類型。</span><span class="sxs-lookup"><span data-stu-id="777d8-121">When possible, choose a data type that matches the data type for **Expression**.</span></span>  
  
 <span data-ttu-id="777d8-122">**[運算式]** 與 **[值]** 中的值必須評估為相同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="777d8-122">The values in **Expression** and **Value** must evaluate to the same data type.</span></span> <span data-ttu-id="777d8-123">例如，如果 [運算式]\*\*\*\* 設定為具有 System.Int32 資料類型的欄位，而 [值]\*\*\*\* 設定為 7，請從下拉式清單中，選擇 [整數]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="777d8-123">For example, if **Expression** is set to a field that has the data type System.Int32 and **Value** is set to 7, from the drop-down list, choose **Integer**.</span></span>  
  
 <span data-ttu-id="777d8-124">如果您所需要的資料類型選項不在此下拉式清單中，請撰寫運算式，以便將此值轉換為正確的資料類型。</span><span class="sxs-lookup"><span data-stu-id="777d8-124">If the data type option you need is not in the drop-down list, write an expression to convert the value to the correct data type.</span></span> <span data-ttu-id="777d8-125">如需詳細資訊，請參閱[篩選、分組和排序資料 &#40;報表產生器及&#41;](report-design/filter-equation-examples-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="777d8-125">For more information, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](report-design/filter-equation-examples-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="777d8-126">**運算子**</span><span class="sxs-lookup"><span data-stu-id="777d8-126">**Operator**</span></span>  
 <span data-ttu-id="777d8-127">選擇要用來比較運算式和值的運算子。</span><span class="sxs-lookup"><span data-stu-id="777d8-127">Choose the operator to use to compare the expression and the value.</span></span>  
  
 <span data-ttu-id="777d8-128">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="777d8-128">**Value**</span></span>  
 <span data-ttu-id="777d8-129">在 [運算式]\*\*\*\* 中，輸入運算式或是要用來評估運算式的值。</span><span class="sxs-lookup"><span data-stu-id="777d8-129">Type the expression or value against which to evaluate the expression in **Expression**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="777d8-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="777d8-130">See Also</span></span>  
 <span data-ttu-id="777d8-131">[新增資料集篩選、資料區域篩選和群組篩選 &#40;報表產生器和 SSRS&#41;](report-design/add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="777d8-131">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](report-design/add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="777d8-132">[運算式範例 &#40;報表產生器及 SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="777d8-132">[Expression Examples &#40;Report Builder and SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="777d8-133">[運算式 &#40;報表產生器及 SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="777d8-133">[Expressions &#40;Report Builder and SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="777d8-134">篩選、分組和排序資料 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="777d8-134">Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;</span></span>](report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  
