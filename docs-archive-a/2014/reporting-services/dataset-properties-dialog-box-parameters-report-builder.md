---
title: 資料集屬性對話方塊、參數 (報表產生器) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10023"
ms.assetid: 3a0672ad-c969-455b-b952-585164ce1dda
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ef038e7cbf113556b11af9a0e6c59aa190b2400b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606645"
---
# <a name="dataset-properties-dialog-box-parameters-report-builder"></a><span data-ttu-id="66f80-102">資料集屬性對話方塊、參數 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="66f80-102">Dataset Properties Dialog Box, Parameters (Report Builder)</span></span>
  <span data-ttu-id="66f80-103">選取 [**資料集屬性**] 對話方塊上的 [**參數**] 來加入、變更和刪除查詢參數。</span><span class="sxs-lookup"><span data-stu-id="66f80-103">Select **Parameters** on the **Dataset Properties** dialog box to add, change, and delete query parameters.</span></span>  
  
 <span data-ttu-id="66f80-104">內嵌資料集的選項適用於報表定義中的資料集。</span><span class="sxs-lookup"><span data-stu-id="66f80-104">For an embedded dataset, options apply to the dataset in the report definition.</span></span>  
  
 <span data-ttu-id="66f80-105">共用資料集的選項則適用於報表伺服器上的共用資料集定義。</span><span class="sxs-lookup"><span data-stu-id="66f80-105">For a shared dataset, options apply to the shared dataset definition on the report server.</span></span>  
  
 <span data-ttu-id="66f80-106">如需詳細資訊，請參閱[內嵌和共用資料集 &#40;報表產生器及 SSRS&#41;](report-data/embedded-and-shared-datasets-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="66f80-106">For more information, see [Embedded and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/embedded-and-shared-datasets-report-builder-and-ssrs.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="66f80-107">選項。</span><span class="sxs-lookup"><span data-stu-id="66f80-107">Options</span></span>  
 <span data-ttu-id="66f80-108">**加入**</span><span class="sxs-lookup"><span data-stu-id="66f80-108">**Add**</span></span>  
 <span data-ttu-id="66f80-109">將新的參數加入到清單中。</span><span class="sxs-lookup"><span data-stu-id="66f80-109">Add a new parameter to the list.</span></span>  
  
 <span data-ttu-id="66f80-110">**刪除**</span><span class="sxs-lookup"><span data-stu-id="66f80-110">**Delete**</span></span>  
 <span data-ttu-id="66f80-111">從清單中移除選取的參數。</span><span class="sxs-lookup"><span data-stu-id="66f80-111">Remove the selected parameter from the list.</span></span>  
  
 <span data-ttu-id="66f80-112">**向上箭頭**</span><span class="sxs-lookup"><span data-stu-id="66f80-112">**Up arrow**</span></span>  
 <span data-ttu-id="66f80-113">將清單中所選取的參數向上移動。</span><span class="sxs-lookup"><span data-stu-id="66f80-113">Move the selected parameter up in the list.</span></span>  
  
 <span data-ttu-id="66f80-114">**向下箭頭**</span><span class="sxs-lookup"><span data-stu-id="66f80-114">**Down arrow**</span></span>  
 <span data-ttu-id="66f80-115">將清單中所選取的參數向下移動。</span><span class="sxs-lookup"><span data-stu-id="66f80-115">Move the selected parameter down in the list.</span></span>  
  
 <span data-ttu-id="66f80-116">**參數名稱**</span><span class="sxs-lookup"><span data-stu-id="66f80-116">**Parameter name**</span></span>  
 <span data-ttu-id="66f80-117">在 [資料集屬性]\*\*\*\* 對話方塊的 [查詢]\*\*\*\* 索引標籤上，輸入您要加入到資料集之查詢參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="66f80-117">Type the name of a query parameter that you added to the dataset on the **Query** tab of the **Dataset Properties** dialog box.</span></span>  
  
 <span data-ttu-id="66f80-118">**參數值**</span><span class="sxs-lookup"><span data-stu-id="66f80-118">**Parameter value**</span></span>  
 <span data-ttu-id="66f80-119">僅適用於內嵌資料集。</span><span class="sxs-lookup"><span data-stu-id="66f80-119">For embedded datasets only.</span></span>  
  
 <span data-ttu-id="66f80-120">輸入查詢參數的值。</span><span class="sxs-lookup"><span data-stu-id="66f80-120">Enter a value for the query parameter.</span></span> <span data-ttu-id="66f80-121">這可為靜態值或參考報表內之物件的運算式，但是它不可以參考任何報表項目或欄位。</span><span class="sxs-lookup"><span data-stu-id="66f80-121">This can be a static value or an expression that refers to an object within the report, but it cannot refer to any report items or fields.</span></span> <span data-ttu-id="66f80-122">根據預設， **[值]** 包含指向報表參數的運算式。</span><span class="sxs-lookup"><span data-stu-id="66f80-122">By default, **Value** contains an expression that points to a report parameter.</span></span>  
  
 <span data-ttu-id="66f80-123">**預設值**</span><span class="sxs-lookup"><span data-stu-id="66f80-123">**Default value**</span></span>  
 <span data-ttu-id="66f80-124">僅適用於共用資料集。</span><span class="sxs-lookup"><span data-stu-id="66f80-124">For shared datasets only.</span></span>  
  
 <span data-ttu-id="66f80-125">選取此核取方塊以指定預設值。</span><span class="sxs-lookup"><span data-stu-id="66f80-125">Select the check box to specify a default value.</span></span>  
  
 <span data-ttu-id="66f80-126">輸入預設值。</span><span class="sxs-lookup"><span data-stu-id="66f80-126">Enter a default value.</span></span> <span data-ttu-id="66f80-127">這可以是靜態值或參考報表內之物件的運算式。</span><span class="sxs-lookup"><span data-stu-id="66f80-127">This can be a static value or an expression that refers to an object within the report.</span></span> <span data-ttu-id="66f80-128">此運算式無法參照報表項目、報表參數或欄位。</span><span class="sxs-lookup"><span data-stu-id="66f80-128">The expression cannot refer to report items, report parameters, or fields.</span></span>  
  
 <span data-ttu-id="66f80-129">若要指定空白，請將文字方塊留空。</span><span class="sxs-lookup"><span data-stu-id="66f80-129">To specify a blank, leave the text box empty.</span></span>  
  
 <span data-ttu-id="66f80-130">若要指定一個 Null，選取 [可為 Null] 選項。</span><span class="sxs-lookup"><span data-stu-id="66f80-130">To specify a null, select the Nullable option.</span></span>  
  
 <span data-ttu-id="66f80-131">**唯讀**</span><span class="sxs-lookup"><span data-stu-id="66f80-131">**Read Only**</span></span>  
 <span data-ttu-id="66f80-132">僅適用於共用資料集。</span><span class="sxs-lookup"><span data-stu-id="66f80-132">For shared datasets only.</span></span>  
  
 <span data-ttu-id="66f80-133">選取此選項，將此參數在共用資料集定義中標示為唯讀。</span><span class="sxs-lookup"><span data-stu-id="66f80-133">Select this option to mark this parameter read only in the shared dataset definition.</span></span> <span data-ttu-id="66f80-134">將共用資料集加入至報表時，參數不會出現在屬性中。</span><span class="sxs-lookup"><span data-stu-id="66f80-134">When the shared dataset is added to a report, the parameter does not appear in the properties.</span></span> <span data-ttu-id="66f80-135">在報表伺服器上快取共用資料集時，無法變更值。</span><span class="sxs-lookup"><span data-stu-id="66f80-135">When the shared dataset is cached on the report server, the value cannot be changed.</span></span>  
  
 <span data-ttu-id="66f80-136">**可為 Null**</span><span class="sxs-lookup"><span data-stu-id="66f80-136">**Nullable**</span></span>  
 <span data-ttu-id="66f80-137">僅適用於共用資料集。</span><span class="sxs-lookup"><span data-stu-id="66f80-137">For shared datasets only.</span></span>  
  
 <span data-ttu-id="66f80-138">選取此選項以允許 Null 值。</span><span class="sxs-lookup"><span data-stu-id="66f80-138">Select this option to allow a null value.</span></span>  
  
 <span data-ttu-id="66f80-139">**從查詢中忽略**</span><span class="sxs-lookup"><span data-stu-id="66f80-139">**Omit From Query**</span></span>  
 <span data-ttu-id="66f80-140">僅適用於共用資料集。</span><span class="sxs-lookup"><span data-stu-id="66f80-140">For shared datasets only.</span></span>  
  
 <span data-ttu-id="66f80-141">當報表參數的參考位於共用資料集篩選 (而非查詢) 中的運算式時，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="66f80-141">Select this option when a reference to a report parameter is in an expression in the shared dataset filter and not in the query.</span></span> <span data-ttu-id="66f80-142">當您選取這個選項時，您不需要在執行查詢時，指定這個參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="66f80-142">When you select this option, you do not need to specify a default value for this parameter when the query runs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66f80-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66f80-143">See Also</span></span>  
 <span data-ttu-id="66f80-144">[對話方塊、窗格和嚮導的報表產生器說明](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="66f80-144">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 <span data-ttu-id="66f80-145">[資料集屬性對話方塊、查詢 &#40;報表產生器&#41;](report-data/dataset-properties-dialog-box-query-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="66f80-145">[Dataset Properties Dialog Box, Query &#40;Report Builder&#41;](report-data/dataset-properties-dialog-box-query-report-builder.md) </span></span>  
 <span data-ttu-id="66f80-146">[運算式 &#40;報表產生器及 SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="66f80-146">[Expressions &#40;Report Builder and SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="66f80-147">[教學課程：將參數加入至您的報表 &#40;報表產生器&#41;](tutorial-add-a-parameter-to-your-report-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="66f80-147">[Tutorial: Add a Parameter to Your Report &#40;Report Builder&#41;](tutorial-add-a-parameter-to-your-report-report-builder.md) </span></span>  
 <span data-ttu-id="66f80-148">[報表參數 &#40;報表產生器和報表設計師&#41;](report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="66f80-148">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="66f80-149">[報表內嵌資料集和共用資料集 &#40;報表產生器和 SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="66f80-149">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="66f80-150">[查詢設計工具 &#40;報表產生器&#41;](../../2014/reporting-services/query-designers-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="66f80-150">[Query Designers &#40;Report Builder&#41;](../../2014/reporting-services/query-designers-report-builder.md) </span></span>  
 <span data-ttu-id="66f80-151">[報表內嵌資料集和共用資料集 &#40;報表產生器和 SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="66f80-151">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="66f80-152">建立共用資料集或內嵌資料集 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="66f80-152">Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;</span></span>](report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
  
