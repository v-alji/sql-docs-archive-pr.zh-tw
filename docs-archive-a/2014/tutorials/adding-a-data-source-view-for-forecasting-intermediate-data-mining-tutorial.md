---
title: 加入資料來源視圖以進行預測 (中繼資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2665040a-1291-4064-ba01-f458637dda57
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 9424988efa6a9856f4ef0d558992fc90ac303861
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704505"
---
# <a name="adding-a-data-source-view-for-forecasting-intermediate-data-mining-tutorial"></a><span data-ttu-id="623af-102">加入預測用的資料來源檢視 (中繼資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="623af-102">Adding a Data Source View for Forecasting (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="623af-103">在這項工作中，您將新增資料來源檢視，以便用於預測狀況。</span><span class="sxs-lookup"><span data-stu-id="623af-103">In this task, you add a data source view that will be used for the forecasting scenario.</span></span> <span data-ttu-id="623af-104">預測模型的資料，必須包含可用來識別時間序列步驟的資料行。</span><span class="sxs-lookup"><span data-stu-id="623af-104">A forecasting model requires that the data contains a column that can be used to identify steps in a time series.</span></span> <span data-ttu-id="623af-105">如果您計畫分析多個資料序列，所有序列必須在同一個日期或時間步驟結束。</span><span class="sxs-lookup"><span data-stu-id="623af-105">If you plan to analyze multiple series of data, all series must end on the same date or time step.</span></span>  
  
### <a name="to-add-a-data-source-view"></a><span data-ttu-id="623af-106">若要加入資料來源檢視</span><span class="sxs-lookup"><span data-stu-id="623af-106">To add a data source view</span></span>  
  
1.  <span data-ttu-id="623af-107">在方案總管中，以滑鼠右鍵按一下 [**資料來源視圖**]，然後選取 [**新增資料來源視圖**]。</span><span class="sxs-lookup"><span data-stu-id="623af-107">In Solution Explorer, right-click **Data Source Views**, and then select **New Data Source View**.</span></span>  
  
2.  <span data-ttu-id="623af-108">在 [歡迎使用資料來源檢視精靈]  頁面上，按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="623af-108">On the **Welcome to the Data Source View Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="623af-109">在 [**選取資料來源**] 頁面的 [**關聯式資料來源**] 底下，選取 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 資料來源。</span><span class="sxs-lookup"><span data-stu-id="623af-109">On the **Select a Data Source** page, under **Relational data sources**, select the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] data source.</span></span> <span data-ttu-id="623af-110">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="623af-110">Click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="623af-111">如果您沒有此資料來源，您可以在[基本資料採礦教學](../../2014/tutorials/basic-data-mining-tutorial.md)課程中找到建立資料來源的步驟。</span><span class="sxs-lookup"><span data-stu-id="623af-111">If you do not have this data source, you can find the steps to create the data source in the [Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md).</span></span>  
  
4.  <span data-ttu-id="623af-112">在 [**選取資料表和資料檢視]** 頁面上，選取資料表 [vTimeSeries (dbo) ]，然後按一下向右箭號，將它加入至 [資料來源] 視圖。</span><span class="sxs-lookup"><span data-stu-id="623af-112">On the **Select Tables and Views** page, select the table, vTimeSeries (dbo), and then click the right arrow to add it to the data source view.</span></span>  
  
5.  <span data-ttu-id="623af-113">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="623af-113">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="623af-114">在 [**正在完成嚮導]** 頁面上，預設會將 [資料來源] 視圖命名為 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="623af-114">On the **Completing the Wizard** page, by default the data source view is named [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)].</span></span> <span data-ttu-id="623af-115">將名稱變更為**salesbyregion.dsv**，然後按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="623af-115">Change the name to **SalesByRegion**, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="623af-116">[資料來源視圖設計工具] 隨即開啟，並顯示 [ **salesbyregion.dsv** ] 資料來源視圖。</span><span class="sxs-lookup"><span data-stu-id="623af-116">Data Source View Designer opens and the **SalesByRegion** data source view appears.</span></span>  
  
## <a name="working-with-the-data-source-view"></a><span data-ttu-id="623af-117">使用資料來源檢視</span><span class="sxs-lookup"><span data-stu-id="623af-117">Working with the Data Source View</span></span>  
 <span data-ttu-id="623af-118">資料來源檢視建立完成之後，可以用下列方法探索資料：</span><span class="sxs-lookup"><span data-stu-id="623af-118">After you have created the data source view, you can explore the data in the following ways:</span></span>  
  
-   <span data-ttu-id="623af-119">以滑鼠右鍵按一下設計工具中的資料表 vTimeSeries，然後選取 [**流覽資料**]，在方格中開啟選取的資料表。</span><span class="sxs-lookup"><span data-stu-id="623af-119">Right-click the table vTimeSeries in the designer, and select **Explore Data** to open the selected table in a grid.</span></span>  
  
-   <span data-ttu-id="623af-120">按一下 [**取樣選項**]，然後使用 [**資料流覽選項**] 對話方塊來變更取樣方法。</span><span class="sxs-lookup"><span data-stu-id="623af-120">Click **Sampling options** and then use the **Data Exploration Options** dialog box to change the sampling method.</span></span> <span data-ttu-id="623af-121">按一下 **[** 重新整理]，使用新的選項設定載入資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="623af-121">Click **Refresh** to load data in the table using the new option settings.</span></span> <span data-ttu-id="623af-122">例如，您可以指定要在取樣中輸出的資料列數目，或選擇前 n 個數據列。</span><span class="sxs-lookup"><span data-stu-id="623af-122">For example, you could specify the number of rows to output in the sample, or choose the top n rows.</span></span>  
  
-   <span data-ttu-id="623af-123">以滑鼠右鍵按一下資料表 vTimeSeries，然後選取 [**屬性**]，將新名稱指派給資料表。</span><span class="sxs-lookup"><span data-stu-id="623af-123">Right-click the table vTimeSeries and select **Properties** to assign a new name to the table.</span></span> <span data-ttu-id="623af-124">您還可以從資料來源檢視中選取個別資料行，並且修改資料行的屬性。</span><span class="sxs-lookup"><span data-stu-id="623af-124">You can also select individual columns from the data source view, and the modify the column properties.</span></span>  
  
-   <span data-ttu-id="623af-125">按一下資料來源檢視設計區域中的任意位置建立新查詢並且指派該查詢的名稱、建立資料表之間的關聯性，或是變更設計區域的配置。</span><span class="sxs-lookup"><span data-stu-id="623af-125">Click anywhere in the data source view design area to create a new query and assign a name to it, to create relationships between tables, or to change the layout of the design area.</span></span>  
  
-   <span data-ttu-id="623af-126">以滑鼠右鍵按一下資料表，然後選取 [新增] [**命名計算**] 以建立衍生的資料行，包括匯總。</span><span class="sxs-lookup"><span data-stu-id="623af-126">Right-click a table and select **New Named Calculation** to create derived columns, including aggregations.</span></span> <span data-ttu-id="623af-127">您也可以從這個檢視的資料來源加入新資料表和檢視。</span><span class="sxs-lookup"><span data-stu-id="623af-127">You can also add new tables and views from the data source in this view.</span></span>  
  
 <span data-ttu-id="623af-128">在下一項工作中，您將瀏覽時間序列資料，並判斷最適合做為時間序列識別碼的資料行。</span><span class="sxs-lookup"><span data-stu-id="623af-128">In the next task, you will explore the time series data and determine the best column to use as the time series identifier.</span></span> <span data-ttu-id="623af-129">您還會學習如何處理時間序列資料中的間距。</span><span class="sxs-lookup"><span data-stu-id="623af-129">You will also learn how to handle gaps in time series data.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="623af-130">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="623af-130">Next Task in Lesson</span></span>  
 [<span data-ttu-id="623af-131">瞭解時間序列模型的需求 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="623af-131">Understanding the Requirements for a Time Series Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/time-series-model-requirements-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="623af-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="623af-132">See Also</span></span>  
 [<span data-ttu-id="623af-133">Microsoft 時間序列演算法</span><span class="sxs-lookup"><span data-stu-id="623af-133">Microsoft Time Series Algorithm</span></span>](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  
