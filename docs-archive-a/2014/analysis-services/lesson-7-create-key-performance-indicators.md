---
title: 第8課：建立關鍵效能指標 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a6c8ac2b-64ba-456f-b418-7bf0afe145d1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3beaab8a34844ecbd633eb5fabbacf37edfede2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698731"
---
# <a name="lesson-8-create-key-performance-indicators"></a><span data-ttu-id="50bf7-102">第 8 課：建立關鍵效能指標</span><span class="sxs-lookup"><span data-stu-id="50bf7-102">Lesson 8: Create Key Performance Indicators</span></span>
  <span data-ttu-id="50bf7-103">在這一課，您將建立關鍵效能指標 (KPI)。</span><span class="sxs-lookup"><span data-stu-id="50bf7-103">In this lesson, you will create Key Performance Indicators (KPIs).</span></span> <span data-ttu-id="50bf7-104">Kpi 是用來針對*目標*值（也是由量值或絕對值所定義），測量由*基底*量值定義之值的效能。</span><span class="sxs-lookup"><span data-stu-id="50bf7-104">KPIs are used to gauge performance of a value, defined by a *Base* measure, against a *Target* value, also defined by a measure or by an absolute value.</span></span> <span data-ttu-id="50bf7-105">在報告用戶端應用程式中，KPI 可讓商務專業人士輕鬆、快速地概括了解商務成果或找出趨勢。</span><span class="sxs-lookup"><span data-stu-id="50bf7-105">In reporting client applications, KPIs can provide business professionals a quick and easy way to understand a summary of business success or to identify trends.</span></span> <span data-ttu-id="50bf7-106">如需詳細資訊，請參閱 [KPI &#40;SSAS 表格式&#41;](tabular-models/kpis-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="50bf7-106">To learn more, see [KPIs &#40;SSAS Tabular&#41;](tabular-models/kpis-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="50bf7-107">完成本課程的估計時間： **15 分鐘**</span><span class="sxs-lookup"><span data-stu-id="50bf7-107">Estimated time to complete this lesson: **15 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="50bf7-108">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="50bf7-108">Prerequisites</span></span>  
 <span data-ttu-id="50bf7-109">本主題是表格式模型教學課程的一部分，請依序完成。</span><span class="sxs-lookup"><span data-stu-id="50bf7-109">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="50bf7-110">在執行本課中的工作之前，您應已完成上一課： [第 7 課：建立量值](lesson-6-create-measures.md)。</span><span class="sxs-lookup"><span data-stu-id="50bf7-110">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 7: Create Measures](lesson-6-create-measures.md).</span></span>  
  
## <a name="create-key-performance-indicators"></a><span data-ttu-id="50bf7-111">建立關鍵效能指標</span><span class="sxs-lookup"><span data-stu-id="50bf7-111">Create Key Performance Indicators</span></span>  
  
#### <a name="to-create-an-internet-current-quarter-sales-performance-kpi"></a><span data-ttu-id="50bf7-112">若要建立網際網路當季銷售績效 (Internet Current Quarter Sales Performance) KPI</span><span class="sxs-lookup"><span data-stu-id="50bf7-112">To create an Internet Current Quarter Sales Performance KPI</span></span>  
  
1.  <span data-ttu-id="50bf7-113">在模型設計師中，按一下 [網際網路銷售]\*\*\*\* 資料表 (索引標籤)。</span><span class="sxs-lookup"><span data-stu-id="50bf7-113">In the model designer, click the **Internet Sales** table (tab).</span></span>  
  
2.  <span data-ttu-id="50bf7-114">在量值方格中，按一下空的儲存格。</span><span class="sxs-lookup"><span data-stu-id="50bf7-114">In the measure grid, click an empty cell.</span></span>  
  
3.  <span data-ttu-id="50bf7-115">在資料表上方的公式列中，輸入下列公式︰</span><span class="sxs-lookup"><span data-stu-id="50bf7-115">In the formula bar, above the table, type the following formula:</span></span>  
  
     `Internet Current Quarter Sales Performance :=IFERROR([Internet Current Quarter Sales]/[Internet Previous Quarter Sales Proportion to QTD],BLANK())`  
  
     <span data-ttu-id="50bf7-116">完成建立公式時，按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="50bf7-116">When you have finished building the formula, press ENTER.</span></span>  
  
     <span data-ttu-id="50bf7-117">此量值將做為 KPI 的基底量值。</span><span class="sxs-lookup"><span data-stu-id="50bf7-117">This measure will serve as the Base measure for the KPI.</span></span>  
  
4.  <span data-ttu-id="50bf7-118">在量值方格中，以滑鼠右鍵按一下 [網際網路當季銷售績效]\*\*\*\* 量值，然後按一下 [建立 KPI]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="50bf7-118">In the measure grid, right-click the **Internet Current Quarter Sales Performance** measure, and then click **Create KPI**.</span></span>  
  
     <span data-ttu-id="50bf7-119">[關鍵效能指標]\*\*\*\* 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="50bf7-119">The **Key Performance Indicator** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="50bf7-120">在 [關鍵效能指標]\*\*\*\* 對話方塊的 [定義目標值]\*\*\*\* 中，選取 [絕對值]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="50bf7-120">In the **Key Performance Indicator** dialog box, in **Define Target Value**, select the **Absolute Value** option.</span></span>  
  
6.  <span data-ttu-id="50bf7-121">在 [**絕對值**] 欄位中，輸入 `1.1` ，然後按 enter。</span><span class="sxs-lookup"><span data-stu-id="50bf7-121">In the **Absolute Value** field, type `1.1`, and then press ENTER.</span></span>  
  
7.  <span data-ttu-id="50bf7-122">在 [**定義狀態臨界**值] 的左邊 ([低) 滑杆] 欄位中，輸入 `1` ，然後在右邊 ([高) 滑杆] 欄位中輸入 `1.07` 。</span><span class="sxs-lookup"><span data-stu-id="50bf7-122">In **Define Status Thresholds**, in the left (low) slider field, type `1`, and then in the right (high) slider field, type `1.07`.</span></span>  
  
8.  <span data-ttu-id="50bf7-123">在 [選取圖示樣式]\*\*\*\* 中，選取菱形 (紅色)、三角形 (黃色)、圓形 (綠色) 圖示類型。</span><span class="sxs-lookup"><span data-stu-id="50bf7-123">In **Select Icon Style**, select the diamond (red), triangle (yellow), circle (green) icon type.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="50bf7-124">請注意可用圖示樣式下方的 [描述]\*\*\*\* 可擴充欄位。</span><span class="sxs-lookup"><span data-stu-id="50bf7-124">Notice the **Descriptions** expandable field below the available icon styles.</span></span> <span data-ttu-id="50bf7-125">您可以為各個不同的 KPI 元素輸入描述，使其在用戶端應用程式中更容易識別。</span><span class="sxs-lookup"><span data-stu-id="50bf7-125">You can type descriptions for the various KPI elements to make them more identifiable in client applications.</span></span>  
  
9. <span data-ttu-id="50bf7-126">按一下 [確定] \*\*\*\* 來完成 KPI。</span><span class="sxs-lookup"><span data-stu-id="50bf7-126">Click **OK** to complete the KPI.</span></span>  
  
     <span data-ttu-id="50bf7-127">請注意量值方格中 [網際網路當季銷售績效]\*\*\*\* 量值旁的圖示。</span><span class="sxs-lookup"><span data-stu-id="50bf7-127">In the measure grid, notice the icon next to the **Internet Current Quarter Sales Performance** measure.</span></span> <span data-ttu-id="50bf7-128">這個圖示表示此量值做為 KPI 的基準值。</span><span class="sxs-lookup"><span data-stu-id="50bf7-128">This icon indicates that this measure serves as a Base value for a KPI.</span></span>  
  
#### <a name="to-create-an-internet-current-quarter-margin-performance-kpi"></a><span data-ttu-id="50bf7-129">若要建立網際網路當季毛利率績效 (Internet Current Quarter Margin Performance) KPI</span><span class="sxs-lookup"><span data-stu-id="50bf7-129">To create an Internet Current Quarter Margin Performance KPI</span></span>  
  
1.  <span data-ttu-id="50bf7-130">在 [網際網路銷售]\*\*\*\* 資料表的量值方格中，按一下空的資料格。</span><span class="sxs-lookup"><span data-stu-id="50bf7-130">In the measure grid for the **Internet Sales** table, click an empty cell.</span></span>  
  
2.  <span data-ttu-id="50bf7-131">在資料表上方的公式列中，輸入下列公式︰</span><span class="sxs-lookup"><span data-stu-id="50bf7-131">In the formula bar, above the table, type the following formula:</span></span>  
  
     `Internet Current Quarter Margin Performance :=IF([Internet Previous Quarter Margin Proportion to QTD]<>0,([Internet Current Quarter Margin]-[Internet Previous Quarter Margin Proportion to QTD])/[Internet Previous Quarter Margin Proportion to QTD],BLANK())`  
  
     <span data-ttu-id="50bf7-132">完成建立公式時，按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="50bf7-132">When you have finished building the formula, press ENTER.</span></span>  
  
3.  <span data-ttu-id="50bf7-133">在量值方格中，以滑鼠右鍵按一下 [網際網路當季毛利率績效]\*\*\*\* 量值，然後按一下 [建立 KPI]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="50bf7-133">In the measure grid, right-click the **Internet Current Quarter Margin Performance** measure, and then click **Create KPI**.</span></span>  
  
4.  <span data-ttu-id="50bf7-134">在 [關鍵效能指標]\*\*\*\* 對話方塊的 [定義目標值]\*\*\*\* 中，選取 [絕對值]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="50bf7-134">In the **Key Performance Indicator** dialog box, in **Define Target Value**, select the **Absolute Value** option.</span></span>  
  
5.  <span data-ttu-id="50bf7-135">在 [**絕對值**] 欄位中，輸入 `1.25` 。</span><span class="sxs-lookup"><span data-stu-id="50bf7-135">In the **Absolute Value** field, type `1.25`.</span></span>  
  
6.  <span data-ttu-id="50bf7-136">在 [定義狀態臨界值]\*\*\*\* 中，滑動左側 (下) 滑動軸欄位，直到欄位顯示 **0.8**，然後滑動右側 (上) 滑動軸欄位，直到欄位顯示 **1.03**。</span><span class="sxs-lookup"><span data-stu-id="50bf7-136">In **Define Status Thresholds**, slide the left (low) slider field until the field displays **0.8**, and then slide the right (high) slider field, until the field displays **1.03**.</span></span>  
  
7.  <span data-ttu-id="50bf7-137">在 [選取圖示樣式]\*\*\*\* 中，選取菱形 (紅色)、三角形 (黃色)、圓形 (綠色) 圖示類型，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="50bf7-137">In **Select Icon Style**, select the diamond (red), triangle (yellow), circle (green) icon type, and then click **OK**.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="50bf7-138">後續步驟</span><span class="sxs-lookup"><span data-stu-id="50bf7-138">Next Step</span></span>  
 <span data-ttu-id="50bf7-139">若要繼續進行本教學課程，請前往下一課： [第 9 課：建立檢視方塊](lesson-8-create-perspectives.md)。</span><span class="sxs-lookup"><span data-stu-id="50bf7-139">To continue this tutorial, go to the next lesson: [Lesson 9: Create Perspectives](lesson-8-create-perspectives.md).</span></span>  
  
  
