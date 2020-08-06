---
title: " (適用于 Excel) 的資料採礦增益集的預測 Wizard |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- forecasting [data mining]
- time series [data mining]
ms.assetid: c5b33f75-42d4-4598-89e7-94815c142ce6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8c3fae97bf1c36154d8ae378840014f2fb997afd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592974"
---
# <a name="forecast-wizard-data-mining-add-ins-for-excel"></a><span data-ttu-id="e0c8e-102">預測精靈 (適用於 Excel 的資料採礦增益集)</span><span class="sxs-lookup"><span data-stu-id="e0c8e-102">Forecast Wizard (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="e0c8e-103">![資料採礦功能區中的關聯精靈](media/dmc-forecast.gif "資料採礦功能區中的關聯精靈")</span><span class="sxs-lookup"><span data-stu-id="e0c8e-103">![Associate wizard in Data Mining ribbon](media/dmc-forecast.gif "Associate wizard in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="e0c8e-104">預測精靈可協助您預測時間序列中的值。</span><span class="sxs-lookup"><span data-stu-id="e0c8e-104">The Forecast wizard helps you predict values in a time series.</span></span> <span data-ttu-id="e0c8e-105">預測精靈使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 時間序列演算法，這是用於預測連續資料行 (例如產品銷售) 的迴歸演算法。</span><span class="sxs-lookup"><span data-stu-id="e0c8e-105">The Forecast wizard uses the [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series algorithm, which is a regression algorithm for use in predicting continuous columns, such as product sales.</span></span>  
  
 <span data-ttu-id="e0c8e-106">每一個預測模型必須包含一個案例序列，它是用來區分序列中各個點的資料行。</span><span class="sxs-lookup"><span data-stu-id="e0c8e-106">Each forecasting model must contain a case series, which is the column that distinguishes between points in a sequence.</span></span> <span data-ttu-id="e0c8e-107">例如，如果您使用記錄資料來預測數個月內的銷售量，您會使用包含一連串日期的資料行做為案例序列。</span><span class="sxs-lookup"><span data-stu-id="e0c8e-107">For example, if you are using historical data to forecast sales over a period of several months, you would use a column containing a series of dates as the case series.</span></span>  
  
 <span data-ttu-id="e0c8e-108">您可以從預測模型建立預測，而不需要提供新的輸入資料。</span><span class="sxs-lookup"><span data-stu-id="e0c8e-108">You can create predictions from a forecasting model without providing new input data.</span></span>  
  
 <span data-ttu-id="e0c8e-109">[**分析**] 功能區中的 [[適用于 Excel&#41;工具的預測 &#40;資料表分析工具](forecast-table-analysis-tools-for-excel.md)] 也可讓您建立預測模型，但它的自訂性較少，而且只能使用 Excel 資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="e0c8e-109">The [Forecast &#40;Table Analysis Tools for Excel&#41;](forecast-table-analysis-tools-for-excel.md) tool, in the **Analyze** ribbon, also lets you create forecasting models, but it is less customizable and can only use data in Excel tables.</span></span>  
  
## <a name="using-the-forecast-wizard"></a><span data-ttu-id="e0c8e-110">使用預測精靈</span><span class="sxs-lookup"><span data-stu-id="e0c8e-110">Using the Forecast Wizard</span></span>  
  
1.  <span data-ttu-id="e0c8e-111">在 [**資料採礦**] 功能區中，按一下 [**預測**]。</span><span class="sxs-lookup"><span data-stu-id="e0c8e-111">In the **Data Mining** ribbon, click **Forecast**.</span></span>  
  
2.  <span data-ttu-id="e0c8e-112">在 [**選取來源資料**] 中，選擇要當做輸入使用的 Excel 資料表、範圍或外部資料源。</span><span class="sxs-lookup"><span data-stu-id="e0c8e-112">In the **Select Source Data**, choose the Excel table, range, or external data source to use as inputs.</span></span>  
  
     <span data-ttu-id="e0c8e-113">如果使用外部資料來源，您可以定義自訂檢視或查詢，然後將其儲存為 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料來源。</span><span class="sxs-lookup"><span data-stu-id="e0c8e-113">If you use an external data source, you can define custom view or queries and save it as an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data source.</span></span>  
  
3.  <span data-ttu-id="e0c8e-114">在 [**預測**] 頁面上，針對 [**時間戳記**] 選取包含唯一數值的資料行 (這包括可當做案例序列使用的日期和時間值) 。</span><span class="sxs-lookup"><span data-stu-id="e0c8e-114">On the **Forecasting** page, for **Time stamp**, select a column that contains unique numeric value (this includes date and time values) that can be used as the case series.</span></span> <span data-ttu-id="e0c8e-115">您必須依據此資料行，以遞增順序來排序資料來源。</span><span class="sxs-lookup"><span data-stu-id="e0c8e-115">The data source must be sorted in ascending order by this column.</span></span>  
  
     <span data-ttu-id="e0c8e-116">如果您的資料沒有這類資料行，您可以使用選項 \<no time stamp> 。</span><span class="sxs-lookup"><span data-stu-id="e0c8e-116">If your data does not have such a column, you can use the option \<no time stamp>.</span></span> <span data-ttu-id="e0c8e-117">精靈會為輸入資料新增唯一的排序資料行，因此，您必須確定資料是以您想要的方式排序，再執行精靈並選擇此選項。</span><span class="sxs-lookup"><span data-stu-id="e0c8e-117">The wizard will add a unique order column for the input data; therefore, you must make sure that the data is sorted the way you want before running the wizard and choosing this option.</span></span>  
  
4.  <span data-ttu-id="e0c8e-118">（選擇性）您可以按一下 [**參數**]，並自訂採礦模型的行為。</span><span class="sxs-lookup"><span data-stu-id="e0c8e-118">Optionally, you can click **Parameters** and customize the behavior of the mining model.</span></span>  
  
     <span data-ttu-id="e0c8e-119">預測模型支援數種不同的演算法：</span><span class="sxs-lookup"><span data-stu-id="e0c8e-119">Forecasting models support several different algorithms:</span></span>  
  
    -   <span data-ttu-id="e0c8e-120">ARIMA</span><span class="sxs-lookup"><span data-stu-id="e0c8e-120">ARIMA</span></span>  
  
    -   <span data-ttu-id="e0c8e-121">ARTXP (一種迴歸模型)</span><span class="sxs-lookup"><span data-stu-id="e0c8e-121">ARTXP (a type of regression model)</span></span>  
  
    -   <span data-ttu-id="e0c8e-122">結合 ARTXP 和 ARIMA</span><span class="sxs-lookup"><span data-stu-id="e0c8e-122">ARTXP and ARIMA combined</span></span>  
  
     <span data-ttu-id="e0c8e-123">如需差異的詳細資訊，請參閱[Microsoft 時間序列演算法技術參考](data-mining/microsoft-time-series-algorithm-technical-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="e0c8e-123">For information about the differences, see [Microsoft Time Series Algorithm Technical Reference](data-mining/microsoft-time-series-algorithm-technical-reference.md).</span></span>  
  
     <span data-ttu-id="e0c8e-124">您也可以新增週期性提示、指定平滑選項，以及自訂模型的迴歸選項。</span><span class="sxs-lookup"><span data-stu-id="e0c8e-124">You can also add periodicity hints, specify smoothing options, and customize regression options for the model.</span></span>  
  
5.  <span data-ttu-id="e0c8e-125">在 [**完成]** 頁面上，為您的資料集和模型提供描述性的名稱，並設定下列選項來控制如何使用完成的模型：</span><span class="sxs-lookup"><span data-stu-id="e0c8e-125">On the **Finish** page, provide a descriptive name for your data set and model, and set the following options that control how you work with the finished model:</span></span>  
  
    -   <span data-ttu-id="e0c8e-126">**流覽模型**。</span><span class="sxs-lookup"><span data-stu-id="e0c8e-126">**Browse model**.</span></span> <span data-ttu-id="e0c8e-127">選取這個選項時，一旦 wizard 完成模型的處理，就會開啟 **[流覽**] 視窗以協助您流覽結果。</span><span class="sxs-lookup"><span data-stu-id="e0c8e-127">When this option is selected, as soon as the wizard finishes processing the model, it opens a **Browse** window to help you explore the results.</span></span> <span data-ttu-id="e0c8e-128">檢視器的內容取決於建立的模型類型。</span><span class="sxs-lookup"><span data-stu-id="e0c8e-128">The contents of the viewer depend on the type of model you built.</span></span> <span data-ttu-id="e0c8e-129">如需詳細資訊，請參閱[流覽預測模型](browsing-a-forecasting-model.md)。</span><span class="sxs-lookup"><span data-stu-id="e0c8e-129">For more information, see [Browsing a Forecasting Model](browsing-a-forecasting-model.md).</span></span>  
  
    -   <span data-ttu-id="e0c8e-130">**啟用 [鑽取**]。</span><span class="sxs-lookup"><span data-stu-id="e0c8e-130">**Enable drillthrough**.</span></span> <span data-ttu-id="e0c8e-131">選取此選項可檢視完成模型中的基礎資料。</span><span class="sxs-lookup"><span data-stu-id="e0c8e-131">Select this option to view the underlying data from the finished model.</span></span> <span data-ttu-id="e0c8e-132">只有建立決策樹模型時，才能使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="e0c8e-132">This option is only available if you build a Decision Tree model.</span></span>  
  
    -   <span data-ttu-id="e0c8e-133">**使用暫時性模型**。</span><span class="sxs-lookup"><span data-stu-id="e0c8e-133">**Use temporary model**.</span></span> <span data-ttu-id="e0c8e-134">如果選取這個選項，此模型將無法儲存到伺服器。</span><span class="sxs-lookup"><span data-stu-id="e0c8e-134">If you select this option, the model will not be saved to the server.</span></span> <span data-ttu-id="e0c8e-135">當您關閉 Excel 時，即會刪除暫時性模型。</span><span class="sxs-lookup"><span data-stu-id="e0c8e-135">Temporary models are deleted when you close Excel.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="e0c8e-136">需求</span><span class="sxs-lookup"><span data-stu-id="e0c8e-136">Requirements</span></span>  
 <span data-ttu-id="e0c8e-137">您的資料應該至少包含一個可做為時間序列的資料行。</span><span class="sxs-lookup"><span data-stu-id="e0c8e-137">Your data should include at least one column that can be used as the time series.</span></span> <span data-ttu-id="e0c8e-138">此資料行中的值應該是唯一且連續的，也就是不應該有間距。</span><span class="sxs-lookup"><span data-stu-id="e0c8e-138">The values in this column should be unique and continuous - that is, there should be no gaps.</span></span> <span data-ttu-id="e0c8e-139">執行精靈之前，請依據時間序列資料行，以遞增順序來排序資料。</span><span class="sxs-lookup"><span data-stu-id="e0c8e-139">Before running the wizard, sort the data by the time series column in ascending order.</span></span>  
  
 <span data-ttu-id="e0c8e-140">如果您的資料不包含時間或日期欄，您可以指派任意數值序列，或讓精靈建立一個資料行。</span><span class="sxs-lookup"><span data-stu-id="e0c8e-140">If your data does not include a time or date column, you can assign an arbitrary numeric series, or let the wizard create one.</span></span> <span data-ttu-id="e0c8e-141">如果您讓精靈建立序列排序資料行，請確定其他資料行是以您想要的方式排序，再啟動精靈。</span><span class="sxs-lookup"><span data-stu-id="e0c8e-141">F you let the wizard create the series order column, make sure the other columns are sorted in the worder you want them before starting the wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0c8e-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0c8e-142">See Also</span></span>  
 <span data-ttu-id="e0c8e-143">[建立資料採礦模型](creating-a-data-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="e0c8e-143">[Creating a Data Mining Model](creating-a-data-mining-model.md) </span></span>  
 <span data-ttu-id="e0c8e-144">[適用于 Excel&#41;的預測 &#40;資料表分析工具](forecast-table-analysis-tools-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="e0c8e-144">[Forecast &#40;Table Analysis Tools for Excel&#41;](forecast-table-analysis-tools-for-excel.md) </span></span>  
 [<span data-ttu-id="e0c8e-145">瀏覽預測模型</span><span class="sxs-lookup"><span data-stu-id="e0c8e-145">Browsing a Forecasting Model</span></span>](browsing-a-forecasting-model.md)  
  
  
