---
title: 資料集屬性對話方塊、篩選 (報表產生器) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10025"
ms.assetid: 933a6f44-4eb7-4e73-9c40-ac0fd17b23d3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7bc13b0eeff1eaf27fb0ec0c4279ff00d0809e4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592536"
---
# <a name="dataset-properties-dialog-box-filters-report-builder"></a><span data-ttu-id="acd5e-102">資料集屬性對話方塊、篩選 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="acd5e-102">Dataset Properties Dialog Box, Filters (Report Builder)</span></span>
  <span data-ttu-id="acd5e-103">選取 **[資料集屬性]** 對話方塊上的 **[篩選]** ，即可建立資料集的篩選。</span><span class="sxs-lookup"><span data-stu-id="acd5e-103">Select **Filters** on the **Dataset Properties** dialog box to create filters for the dataset.</span></span>  
  
 <span data-ttu-id="acd5e-104">屬於報表伺服器上共用資料集定義之一部分的篩選會影響所有使用共用資料集的報表。</span><span class="sxs-lookup"><span data-stu-id="acd5e-104">Filters that are part of a shared dataset definition on the report server affect all reports that use the shared dataset.</span></span> <span data-ttu-id="acd5e-105">當共用資料集加入至報表之後，可以為共用資料集指定其他篩選。</span><span class="sxs-lookup"><span data-stu-id="acd5e-105">Additional filters for the shared dataset can be specified after it is added to a report.</span></span> <span data-ttu-id="acd5e-106">這些篩選只會影響其定義所在的報表。</span><span class="sxs-lookup"><span data-stu-id="acd5e-106">These filters affect only the report in which they are defined.</span></span>  
  
 <span data-ttu-id="acd5e-107">內嵌資料集的篩選只會影響其定義所在的報表。</span><span class="sxs-lookup"><span data-stu-id="acd5e-107">Filters for an embedded dataset affect only the report in which they are defined.</span></span>  
  
 <span data-ttu-id="acd5e-108">如需詳細資訊，請參閱 [篩選、分組和排序資料 &#40;報表產生器及 SSRS&#41;](report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)(將互動式排序加入資料表或矩陣 (報表產生器及 SSRS))。</span><span class="sxs-lookup"><span data-stu-id="acd5e-108">For more information, see [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](report-design/filter-group-and-sort-data-report-builder-and-ssrs.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="acd5e-109">選項。</span><span class="sxs-lookup"><span data-stu-id="acd5e-109">Options</span></span>  
 <span data-ttu-id="acd5e-110">**加入**</span><span class="sxs-lookup"><span data-stu-id="acd5e-110">**Add**</span></span>  
 <span data-ttu-id="acd5e-111">將新的篩選子句加入到清單中。</span><span class="sxs-lookup"><span data-stu-id="acd5e-111">Add a new filter clause to the list.</span></span>  
  
 <span data-ttu-id="acd5e-112">**刪除**</span><span class="sxs-lookup"><span data-stu-id="acd5e-112">**Delete**</span></span>  
 <span data-ttu-id="acd5e-113">從清單中刪除選取的篩選子句。</span><span class="sxs-lookup"><span data-stu-id="acd5e-113">Delete the selected filter clause from the list.</span></span>  
  
 <span data-ttu-id="acd5e-114">**向上箭頭**</span><span class="sxs-lookup"><span data-stu-id="acd5e-114">**Up arrow**</span></span>  
 <span data-ttu-id="acd5e-115">將清單中所選取的篩選向上移動。</span><span class="sxs-lookup"><span data-stu-id="acd5e-115">Move the selected filter up in the list.</span></span>  
  
 <span data-ttu-id="acd5e-116">**向下箭頭**</span><span class="sxs-lookup"><span data-stu-id="acd5e-116">**Down arrow**</span></span>  
 <span data-ttu-id="acd5e-117">將清單中所選取的篩選向下移動</span><span class="sxs-lookup"><span data-stu-id="acd5e-117">Move the selected filter down in the list</span></span>  
  
 <span data-ttu-id="acd5e-118">**運算式**</span><span class="sxs-lookup"><span data-stu-id="acd5e-118">**Expression**</span></span>  
 <span data-ttu-id="acd5e-119">輸入或選擇您要套用篩選的目標運算式。</span><span class="sxs-lookup"><span data-stu-id="acd5e-119">Type or choose the expression to which you want to apply a filter.</span></span> <span data-ttu-id="acd5e-120">按一下運算式 (**fx**) ] 按鈕，即可編輯運算式。</span><span class="sxs-lookup"><span data-stu-id="acd5e-120">Click the Expression (**fx**) button to edit the expression.</span></span>  
  
 <span data-ttu-id="acd5e-121">**Data type**</span><span class="sxs-lookup"><span data-stu-id="acd5e-121">**Data type**</span></span>  
 <span data-ttu-id="acd5e-122">選擇 [值]\*\*\*\* 的資料類型。</span><span class="sxs-lookup"><span data-stu-id="acd5e-122">Choose the data type for **Value**.</span></span> <span data-ttu-id="acd5e-123">可能的話，請選擇符合 **[運算式]** 資料類型的資料類型。</span><span class="sxs-lookup"><span data-stu-id="acd5e-123">When possible, choose a data type that matches the data type for **Expression**.</span></span>  
  
 <span data-ttu-id="acd5e-124">**[運算式]** 與 **[值]** 中的值必須評估為相同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="acd5e-124">The values in **Expression** and **Value** must evaluate to the same data type.</span></span> <span data-ttu-id="acd5e-125">例如，如果 [運算式]\*\*\*\* 設定為具有 System.Int32 資料類型的欄位，而 [值]\*\*\*\* 設定為 7，請從下拉式清單中，選擇 [整數]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="acd5e-125">For example, if **Expression** is set to a field that has the data type System.Int32 and **Value** is set to 7, from the drop-down list, choose **Integer**.</span></span>  
  
 <span data-ttu-id="acd5e-126">如果您所需要的資料類型選項不在此下拉式清單中，請撰寫運算式，以便將此值轉換為正確的資料類型。</span><span class="sxs-lookup"><span data-stu-id="acd5e-126">If the data type option you need is not in the drop-down list, write an expression to convert the value to the correct data type.</span></span> <span data-ttu-id="acd5e-127">如需詳細資訊，請參閱[篩選、分組和排序資料 &#40;報表產生器及&#41;](report-design/filter-equation-examples-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="acd5e-127">For more information, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](report-design/filter-equation-examples-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="acd5e-128">**運算子**</span><span class="sxs-lookup"><span data-stu-id="acd5e-128">**Operator**</span></span>  
 <span data-ttu-id="acd5e-129">選擇要用來比較運算式和值的運算子。</span><span class="sxs-lookup"><span data-stu-id="acd5e-129">Choose the operator to use to compare the expression and the value.</span></span>  
  
 <span data-ttu-id="acd5e-130">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="acd5e-130">**Value**</span></span>  
 <span data-ttu-id="acd5e-131">評估在 [運算式]\*\*\*\* 方塊中指定的運算式時，輸入要使用的運算式或值。</span><span class="sxs-lookup"><span data-stu-id="acd5e-131">Type the expression or value to use when evaluating the expression specified in the **Expression** box.</span></span> <span data-ttu-id="acd5e-132">按一下運算式 (**fx**) ] 按鈕，即可編輯運算式。</span><span class="sxs-lookup"><span data-stu-id="acd5e-132">Click the Expression (**fx**) button to edit the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acd5e-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="acd5e-133">See Also</span></span>  
 <span data-ttu-id="acd5e-134">[報表內嵌資料集和共用資料集 &#40;報表產生器和 SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="acd5e-134">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="acd5e-135">[報表參數 &#40;報表產生器和報表設計師&#41;](report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="acd5e-135">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="acd5e-136">[將篩選加入至資料集 &#40;報表產生器和 SSRS&#41;](report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="acd5e-136">[Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;](report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="acd5e-137">報表中的運算式用法 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="acd5e-137">Expression Uses in Reports &#40;Report Builder and SSRS&#41;</span></span>](report-design/expression-uses-in-reports-report-builder-and-ssrs.md)  
  
  
