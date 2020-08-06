---
title: 指定查詢準則 (基於使用方式的優化 Wizard) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.usagebasedoptimizationwizard.specifyquerycriteria.f1
ms.assetid: 3193adc2-af9f-4234-a4cc-dea0c280a724
author: minewiskan
ms.author: owend
ms.openlocfilehash: f3b93034a089ff3121155e35de4cec96846824a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593620"
---
# <a name="specify-query-criteria-usage-based-optimization-wizard"></a><span data-ttu-id="b9c13-102">指定查詢準則 (基於使用方式的最佳化精靈)</span><span class="sxs-lookup"><span data-stu-id="b9c13-102">Specify Query Criteria (Usage-Based Optimization Wizard)</span></span>
  <span data-ttu-id="b9c13-103">使用 **[指定查詢準則]** 頁面選擇一個或多個篩選選項來識別要最佳化的查詢。</span><span class="sxs-lookup"><span data-stu-id="b9c13-103">Use the **Specify Query Criteria** page to choose one or more filter options in order to identify queries to optimize.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b9c13-104">如果 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 無法連接到查詢記錄，此頁面就會停用。</span><span class="sxs-lookup"><span data-stu-id="b9c13-104">This page is disabled if [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cannot connect to the query log.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b9c13-105">選項</span><span class="sxs-lookup"><span data-stu-id="b9c13-105">Options</span></span>  
 <span data-ttu-id="b9c13-106">**查詢記錄統計資料**</span><span class="sxs-lookup"><span data-stu-id="b9c13-106">**Query log statistics**</span></span>  
 <span data-ttu-id="b9c13-107">顯示所選取資料分割的查詢記錄中，所儲存之查詢的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b9c13-107">Displays information about the queries stored in the query log for the selected partitions.</span></span> <span data-ttu-id="b9c13-108">其中會顯示下列項目：</span><span class="sxs-lookup"><span data-stu-id="b9c13-108">The following items are displayed:</span></span>  
  
|<span data-ttu-id="b9c13-109">詞彙</span><span class="sxs-lookup"><span data-stu-id="b9c13-109">Term</span></span>|<span data-ttu-id="b9c13-110">定義</span><span class="sxs-lookup"><span data-stu-id="b9c13-110">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="b9c13-111">**查詢總計**</span><span class="sxs-lookup"><span data-stu-id="b9c13-111">**Total queries**</span></span>|<span data-ttu-id="b9c13-112">顯示所選取資料分割的查詢記錄中，所儲存的查詢總數。</span><span class="sxs-lookup"><span data-stu-id="b9c13-112">Displays the total number of queries stored in the query log for the selected partitions.</span></span>|  
|<span data-ttu-id="b9c13-113">**相異查詢**</span><span class="sxs-lookup"><span data-stu-id="b9c13-113">**Distinct queries**</span></span>|<span data-ttu-id="b9c13-114">顯示所選取資料分割的查詢記錄中，所儲存的相異查詢數目。</span><span class="sxs-lookup"><span data-stu-id="b9c13-114">Displays the number of distinct queries stored in the query log for the selected partitions.</span></span>|  
|<span data-ttu-id="b9c13-115">**相異使用者**</span><span class="sxs-lookup"><span data-stu-id="b9c13-115">**Distinct users**</span></span>|<span data-ttu-id="b9c13-116">顯示所選取資料分割的查詢記錄中，與所儲存之查詢相關聯的相異使用者總數。</span><span class="sxs-lookup"><span data-stu-id="b9c13-116">Displays the total number of distinct users associated with queries stored in the query log for the selected partitions.</span></span>|  
|<span data-ttu-id="b9c13-117">**平均回應時間**</span><span class="sxs-lookup"><span data-stu-id="b9c13-117">**Average response time**</span></span>|<span data-ttu-id="b9c13-118">顯示所選取資料分割的查詢記錄中，所儲存之查詢的平均回應時間。</span><span class="sxs-lookup"><span data-stu-id="b9c13-118">Displays the average response time for queries stored in the query log for the selected partitions.</span></span>|  
  
 <span data-ttu-id="b9c13-119">**開始日期**</span><span class="sxs-lookup"><span data-stu-id="b9c13-119">**Beginning date**</span></span>  
 <span data-ttu-id="b9c13-120">依據開始日期和時間篩選查詢記錄中的查詢。</span><span class="sxs-lookup"><span data-stu-id="b9c13-120">Filters queries in the query log based on a starting date and time.</span></span> <span data-ttu-id="b9c13-121">在下拉式清單中選擇或輸入日期。</span><span class="sxs-lookup"><span data-stu-id="b9c13-121">Choose or type a date in the dropdown list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b9c13-122"> 如果未選取 **[結束日期]** ，則會考量查詢記錄中，符合此選項指定的日期和時間或之後的所有查詢。</span><span class="sxs-lookup"><span data-stu-id="b9c13-122">If **Ending date** is not selected, all queries in the query log on or after the date and time specified for this option are considered.</span></span>  
  
 <span data-ttu-id="b9c13-123">**結束日期**</span><span class="sxs-lookup"><span data-stu-id="b9c13-123">**Ending date**</span></span>  
 <span data-ttu-id="b9c13-124">依據結束日期和時間篩選查詢記錄中的查詢。</span><span class="sxs-lookup"><span data-stu-id="b9c13-124">Filters queries in the query log based on an ending date and time.</span></span> <span data-ttu-id="b9c13-125">在下拉式清單中選擇或輸入日期。</span><span class="sxs-lookup"><span data-stu-id="b9c13-125">Choose or type a date in the dropdown list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b9c13-126"> 如果未選取 **[開始日期]** ，則會考量查詢記錄中，符合在此選項指定的日期和時間或之前的所有查詢。</span><span class="sxs-lookup"><span data-stu-id="b9c13-126">If **Beginning date** is not selected, all queries in the query log on or before the date and time specified for this option are considered.</span></span>  
  
 <span data-ttu-id="b9c13-127">**使用者**</span><span class="sxs-lookup"><span data-stu-id="b9c13-127">**Users**</span></span>  
 <span data-ttu-id="b9c13-128">依據指定的使用者集合篩選查詢記錄中的查詢。</span><span class="sxs-lookup"><span data-stu-id="b9c13-128">Filters queries in the query log based on a specified set of users.</span></span> <span data-ttu-id="b9c13-129">按一下省略符號 (**...**) 按鈕，即可顯示 [使用者選取]\*\*\*\* 對話方塊，並選擇用來篩選查詢的使用者。</span><span class="sxs-lookup"><span data-stu-id="b9c13-129">Click the ellipsis (**...**) button to display the **User Selection** dialog box and choose users on which to filter queries.</span></span> <span data-ttu-id="b9c13-130">如需 [使用者選取]\*\*\*\* 對話方塊的詳細資訊，請參閱[使用者選取對話方塊 &#40;Analysis Services - 多維度資料&#41;](user-selection-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="b9c13-130">For more information about the **User Selection** dialog box, see [User Selection Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](user-selection-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="b9c13-131">**最常使用查詢**</span><span class="sxs-lookup"><span data-stu-id="b9c13-131">**Most frequent queries**</span></span>  
 <span data-ttu-id="b9c13-132">依據所選取資料分割最常執行之相異查詢的最高百分比，篩選查詢記錄中的查詢。</span><span class="sxs-lookup"><span data-stu-id="b9c13-132">Filters queries in the query log based on the topmost percentage of the distinct queries most often run for the selected partitions.</span></span> <span data-ttu-id="b9c13-133">選擇或在文字方塊輸入百分比值。</span><span class="sxs-lookup"><span data-stu-id="b9c13-133">Choose or type a percent value in the text box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9c13-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9c13-134">See Also</span></span>  
 <span data-ttu-id="b9c13-135">[基於使用方式的優化嚮導 F1 說明](usage-based-optimization-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="b9c13-135">[Usage-Based Optimization Wizard F1 Help](usage-based-optimization-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="b9c13-136">Analysis Services 的 &#40;多維度資料的嚮導&#41;</span><span class="sxs-lookup"><span data-stu-id="b9c13-136">Analysis Services Wizards &#40;Multidimensional Data&#41;</span></span>](analysis-services-wizards-multidimensional-data.md)  
  
  
