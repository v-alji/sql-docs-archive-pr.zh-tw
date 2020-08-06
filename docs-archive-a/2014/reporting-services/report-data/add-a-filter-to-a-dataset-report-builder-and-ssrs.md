---
title: 將篩選新增至資料集 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: eed37e74-6a43-4d7c-9959-2d5fa6a6aba9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f51411d31d8ee29bf0f163085077dcee8fd79bdd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585087"
---
# <a name="add-a-filter-to-a-dataset-report-builder-and-ssrs"></a><span data-ttu-id="07c2e-102">將篩選加入至資料集 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="07c2e-102">Add a Filter to a Dataset (Report Builder and SSRS)</span></span>
  <span data-ttu-id="07c2e-103">從外部資料來源擷取資料後，將篩選加入至資料集來限制報表中的資料。</span><span class="sxs-lookup"><span data-stu-id="07c2e-103">Add a filter to a dataset to limit the data in a report after the data is retrieved from an external data source.</span></span> <span data-ttu-id="07c2e-104">當您將篩選加入至資料集時，所有報表組件或資料區都只會使用符合篩選條件的資料。</span><span class="sxs-lookup"><span data-stu-id="07c2e-104">When you add a filter to a dataset, all report parts or data regions use only data that matches the filter conditions.</span></span>  
  
 <span data-ttu-id="07c2e-105">若是共用資料集，套用至所有相依項目的篩選必須是報表伺服器上共用資料集定義的一部分。</span><span class="sxs-lookup"><span data-stu-id="07c2e-105">For a shared dataset, a filter that applies to all dependent items must be part of the shared dataset definition on the report server.</span></span> <span data-ttu-id="07c2e-106">包含共用資料集執行個體的報表或報表組件可以建立只套用至執行個體的其他篩選。</span><span class="sxs-lookup"><span data-stu-id="07c2e-106">A report or report part that contains an instance of a shared dataset can create an additional filter that applies only to the instance.</span></span>  
  
 <span data-ttu-id="07c2e-107">若要加入篩選，您必須指定一個或多個屬於篩選方程式的條件。</span><span class="sxs-lookup"><span data-stu-id="07c2e-107">To add a filter, you must specify one or more conditions that are filter equations.</span></span> <span data-ttu-id="07c2e-108">篩選方程式包含一個識別您想要篩選之資料的運算式、一個運算子和一個要比較的值。</span><span class="sxs-lookup"><span data-stu-id="07c2e-108">A filter equation consists of an expression that identifies the data that you want to filter, an operator, and the value to compare to.</span></span> <span data-ttu-id="07c2e-109">篩選資料和值的資料類型必須相符。</span><span class="sxs-lookup"><span data-stu-id="07c2e-109">The data types of the filtered data and the value must match.</span></span> <span data-ttu-id="07c2e-110">不支援針對資料集的彙總值進行篩選。</span><span class="sxs-lookup"><span data-stu-id="07c2e-110">Filtering on aggregate values for a dataset is not supported.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-filter-to-a-shared-dataset"></a><span data-ttu-id="07c2e-111">若要將篩選加入至共用資料集</span><span class="sxs-lookup"><span data-stu-id="07c2e-111">To add a filter to a shared dataset</span></span>  
  
1.  <span data-ttu-id="07c2e-112">在共用資料集模式下，開啟共用資料集。</span><span class="sxs-lookup"><span data-stu-id="07c2e-112">Open a shared dataset in shared dataset mode.</span></span>  
  
2.  <span data-ttu-id="07c2e-113">在 **[主資料夾]** 索引標籤的 **[共用資料集]** 群組中，按一下 [資料集]。</span><span class="sxs-lookup"><span data-stu-id="07c2e-113">On the **Home** tab, in the **Shared Datasets** group, click Datasets.</span></span> <span data-ttu-id="07c2e-114">**[資料集屬性]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="07c2e-114">The **Dataset Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="07c2e-115">按一下 **[篩選]** 。</span><span class="sxs-lookup"><span data-stu-id="07c2e-115">Click **Filters**.</span></span> <span data-ttu-id="07c2e-116">這樣就會顯示目前的篩選方程式清單。</span><span class="sxs-lookup"><span data-stu-id="07c2e-116">This displays the current list of filter equations.</span></span> <span data-ttu-id="07c2e-117">根據預設，此清單是空的。</span><span class="sxs-lookup"><span data-stu-id="07c2e-117">By default, the list is empty.</span></span>  
  
4.  <span data-ttu-id="07c2e-118">按一下 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="07c2e-118">Click **Add**.</span></span> <span data-ttu-id="07c2e-119">新的空白篩選方程式隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="07c2e-119">A new blank filter equation appears.</span></span>  
  
5.  <span data-ttu-id="07c2e-120">在 **[運算式]** 中，針對要篩選的欄位輸入或選取運算式。</span><span class="sxs-lookup"><span data-stu-id="07c2e-120">In **Expression**, type or select the expression for the field to filter.</span></span> <span data-ttu-id="07c2e-121">若要編輯運算式，請按一下運算式 (*fx*) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="07c2e-121">To edit the expression, click the expression (*fx*) button.</span></span>  
  
6.  <span data-ttu-id="07c2e-122">在清單方塊中，選取符合您在步驟 5 中建立之運算式資料類型的資料類型。</span><span class="sxs-lookup"><span data-stu-id="07c2e-122">From the list box, select the data type that matches the type of data in the expression you created in step 5.</span></span>  
  
7.  <span data-ttu-id="07c2e-123">在 **[運算子]** 方塊中，選取您想要篩選用來比較 **[運算式]** 方塊和 **[值]** 方塊中值的運算子。</span><span class="sxs-lookup"><span data-stu-id="07c2e-123">In the **Operator** box, select the operator that you want the filter to use to compare the values in the **Expression** box and the **Value** box.</span></span> <span data-ttu-id="07c2e-124">您所選擇的運算子會決定下一個步驟所使用的值數目。</span><span class="sxs-lookup"><span data-stu-id="07c2e-124">The operator you choose determines the number of values that are used from the next step.</span></span>  
  
8.  <span data-ttu-id="07c2e-125">在 **[值]** 方塊中，輸入您想要篩選在評估 **[運算式]** 中的值時，所針對的運算式或值。</span><span class="sxs-lookup"><span data-stu-id="07c2e-125">In the **Value** box, type the expression or value against which you want the filter to evaluate the value in **Expression**.</span></span>  
  
     <span data-ttu-id="07c2e-126">如需篩選方程式的範例，請參閱[篩選方程式範例 &#40;報表產生器及 SSRS&#41;](../report-design/filter-equation-examples-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="07c2e-126">For examples of filter equations, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](../report-design/filter-equation-examples-report-builder-and-ssrs.md).</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-add-a-filter-to-an-embedded-dataset-or-a-shared-dataset-instance"></a><span data-ttu-id="07c2e-127">若要將篩選加入至內嵌資料集或共用資料集執行個體</span><span class="sxs-lookup"><span data-stu-id="07c2e-127">To add a filter to an embedded dataset or a shared dataset instance</span></span>  
  
1.  <span data-ttu-id="07c2e-128">在報表設計模式下，開啟報表。</span><span class="sxs-lookup"><span data-stu-id="07c2e-128">Open a report in report design mode.</span></span>  
  
2.  <span data-ttu-id="07c2e-129">以滑鼠右鍵按一下 [報表資料]  窗格中的資料集，然後按一下 [資料集屬性]  。</span><span class="sxs-lookup"><span data-stu-id="07c2e-129">Right-click a dataset in the **Report Data** pane and then click **Dataset Properties**.</span></span> <span data-ttu-id="07c2e-130">**[資料集屬性]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="07c2e-130">The **Dataset Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="07c2e-131">按一下 **[篩選]** 。</span><span class="sxs-lookup"><span data-stu-id="07c2e-131">Click **Filters**.</span></span> <span data-ttu-id="07c2e-132">這樣就會顯示目前的篩選方程式清單。</span><span class="sxs-lookup"><span data-stu-id="07c2e-132">This displays the current list of filter equations.</span></span> <span data-ttu-id="07c2e-133">根據預設，此清單是空的。</span><span class="sxs-lookup"><span data-stu-id="07c2e-133">By default, the list is empty.</span></span>  
  
4.  <span data-ttu-id="07c2e-134">按一下 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="07c2e-134">Click **Add**.</span></span> <span data-ttu-id="07c2e-135">新的空白篩選方程式隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="07c2e-135">A new blank filter equation appears.</span></span>  
  
5.  <span data-ttu-id="07c2e-136">在 **[運算式]** 中，針對要篩選的欄位輸入或選取運算式。</span><span class="sxs-lookup"><span data-stu-id="07c2e-136">In **Expression**, type or select the expression for the field to filter.</span></span> <span data-ttu-id="07c2e-137">若要編輯運算式，請按一下運算式 (*fx*) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="07c2e-137">To edit the expression, click the expression (*fx*) button.</span></span>  
  
6.  <span data-ttu-id="07c2e-138">在下拉式方塊中，選取符合您在步驟 5 中建立之運算式資料類型的資料類型。</span><span class="sxs-lookup"><span data-stu-id="07c2e-138">From the drop-down box, select the data type that matches the type of data in the expression you created in step 5.</span></span>  
  
7.  <span data-ttu-id="07c2e-139">在 **[運算子]** 方塊中，選取您想要篩選用來比較 **[運算式]** 方塊和 **[值]** 方塊中值的運算子。</span><span class="sxs-lookup"><span data-stu-id="07c2e-139">In the **Operator** box, select the operator that you want the filter to use to compare the values in the **Expression** box and the **Value** box.</span></span> <span data-ttu-id="07c2e-140">您所選擇的運算子會決定下一個步驟所使用的值數目。</span><span class="sxs-lookup"><span data-stu-id="07c2e-140">The operator you choose determines the number of values that are used from the next step.</span></span>  
  
8.  <span data-ttu-id="07c2e-141">在 **[值]** 方塊中，輸入您想要篩選在評估 **[運算式]** 中的值時，所針對的運算式或值。</span><span class="sxs-lookup"><span data-stu-id="07c2e-141">In the **Value** box, type the expression or value against which you want the filter to evaluate the value in **Expression**.</span></span>  
  
     <span data-ttu-id="07c2e-142">如需篩選方程式的範例，請參閱[篩選方程式範例 &#40;報表產生器及 SSRS&#41;](../report-design/filter-equation-examples-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="07c2e-142">For examples of filter equations, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](../report-design/filter-equation-examples-report-builder-and-ssrs.md).</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="07c2e-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07c2e-143">See Also</span></span>  
 <span data-ttu-id="07c2e-144">[新增資料集篩選、資料區篩選和群組篩選 &#40;報表產生器及 SSRS&#41;](../report-design/add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="07c2e-144">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](../report-design/add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="07c2e-145">[運算式範例 &#40;報表產生器及 SSRS&#41;](../report-design/expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="07c2e-145">[Expression Examples &#40;Report Builder and SSRS&#41;](../report-design/expression-examples-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="07c2e-146">新增篩選 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="07c2e-146">Add a Filter &#40;Report Builder and SSRS&#41;</span></span>](../report-design/add-a-filter-report-builder-and-ssrs.md)  
  
  
