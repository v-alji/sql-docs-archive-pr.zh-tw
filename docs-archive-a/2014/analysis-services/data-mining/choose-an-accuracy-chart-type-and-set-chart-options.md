---
title: 選擇精確度圖表類型及設定圖表選項 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Mining Accuracy Chart [Analysis Services]
- mining models [Analysis Services], validating
- classification accuracy [data mining]
- accuracy testing [data mining]
ms.assetid: bd24dd4a-624f-478a-9c94-b1361e857680
author: minewiskan
ms.author: owend
ms.openlocfilehash: 33c2b5e8a1e228a86328ef6df1b636742d3614ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594854"
---
# <a name="choose-an-accuracy-chart-type-and-set-chart-options"></a><span data-ttu-id="880f1-102">選擇精確度圖表類型及設定圖表選項</span><span class="sxs-lookup"><span data-stu-id="880f1-102">Choose an Accuracy Chart Type and Set Chart Options</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="880f1-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]提供多種方法來判斷您的採礦模型是否有效。</span><span class="sxs-lookup"><span data-stu-id="880f1-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] provides multiple methods for determining the validity of your mining models.</span></span> <span data-ttu-id="880f1-104">您可以為每一個模型或結構建立之精確度圖表的類型取決於以下因素：</span><span class="sxs-lookup"><span data-stu-id="880f1-104">The type of accuracy chart that you can create for each model or structure depends on these factors:</span></span>  
  
-   <span data-ttu-id="880f1-105">建立模型時所使用的演算法類型</span><span class="sxs-lookup"><span data-stu-id="880f1-105">The type of algorithm that was used to create the model</span></span>  
  
-   <span data-ttu-id="880f1-106">可預測屬性的資料類型</span><span class="sxs-lookup"><span data-stu-id="880f1-106">The data type of the predictable attribute</span></span>  
  
-   <span data-ttu-id="880f1-107">要測量之可預測屬性的數目</span><span class="sxs-lookup"><span data-stu-id="880f1-107">The number of predictable attributes to measure</span></span>  
  
 <span data-ttu-id="880f1-108">本主題提供不同精確度圖表的概觀。</span><span class="sxs-lookup"><span data-stu-id="880f1-108">This topic provides an overview of the different accuracy charts.</span></span>  
  
 <span data-ttu-id="880f1-109">**注意** ：圖表及其定義並不會儲存。</span><span class="sxs-lookup"><span data-stu-id="880f1-109">**Note** Charts and their definitions are not saved.</span></span> <span data-ttu-id="880f1-110">如果將包含圖表的視窗關閉，則必須再次建立該圖表。</span><span class="sxs-lookup"><span data-stu-id="880f1-110">If you close the window that contains a chart, you must create the chart again.</span></span>  
  
## <a name="accuracy-chart-types"></a><span data-ttu-id="880f1-111">精確度圖表類型</span><span class="sxs-lookup"><span data-stu-id="880f1-111">Accuracy Chart Types</span></span>  
 <span data-ttu-id="880f1-112">根據您選擇的圖表類型而定，您將能夠進一步設定選項、瀏覽圖表，或是將圖表複製到剪貼簿，然後在 Excel 中處理資料。</span><span class="sxs-lookup"><span data-stu-id="880f1-112">Depending on the chart type that you choose, you have the ability to further configure options, to browse the chart, or copy the chart to the Clipboard and work with the data in Excel.</span></span>  
  
#### <a name="lift-chart"></a><span data-ttu-id="880f1-113">增益圖</span><span class="sxs-lookup"><span data-stu-id="880f1-113">Lift chart</span></span>  
 <span data-ttu-id="880f1-114">在設定模型及測試資料的選項後，請按一下 [增益圖]\*\*\*\* 索引標籤來檢視結果。</span><span class="sxs-lookup"><span data-stu-id="880f1-114">After you have configured the options for the models and the testing data, click the **Lift Chart** tab to view the results.</span></span> <span data-ttu-id="880f1-115">您也可以將圖表複製到剪貼簿，或是在 [採礦圖例] 中檢視個別趨勢線或資料點的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="880f1-115">You can also copy the chart to the Clipboard, or view details of individual trend lines or data points in the Mining Legend.</span></span>  
  
#### <a name="profit-chart"></a><span data-ttu-id="880f1-116">收益圖</span><span class="sxs-lookup"><span data-stu-id="880f1-116">Profit Chart</span></span>  
 <span data-ttu-id="880f1-117">在設定模型及測試資料的選項後，請按一下 [增益圖]\*\*\*\* 索引標籤，然後從 [圖表類型]\*\*\*\* 清單中選取 [收益圖]\*\*\*\* 來設定收益圖選項，再按一下 [確定]\*\*\*\* 檢視結果。</span><span class="sxs-lookup"><span data-stu-id="880f1-117">After you have configured the options for the models and the testing data, click the **Lift Chart** tab, select **Profit Chart** from the **Chart Type** list to set profit chart options, and then click **OK** to view the results.</span></span>  
  
 <span data-ttu-id="880f1-118">您可以視需要多次使用 [收益圖設定]\*\*\*\* 對話方塊，嘗試不同的成本選項及重新顯示圖表。</span><span class="sxs-lookup"><span data-stu-id="880f1-118">You can use the **Profit Chart Settings** dialog box as many times as you want to try different cost options and redisplay the chart.</span></span> <span data-ttu-id="880f1-119">採礦圖例會包含有關每一個模型之預估收益的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="880f1-119">The Mining Legend contains detailed information about the estimated profit for each model.</span></span> <span data-ttu-id="880f1-120">您也可以將圖表和 [採礦圖例] 的內容複製到剪貼簿，在 Excel 中進行處理。</span><span class="sxs-lookup"><span data-stu-id="880f1-120">You can also copy the chart and the contents of the Mining Legend to the Clipboard to work with it in Excel.</span></span>  
  
#### <a name="scatter-plot"></a><span data-ttu-id="880f1-121">散佈圖</span><span class="sxs-lookup"><span data-stu-id="880f1-121">Scatter Plot</span></span>  
 <span data-ttu-id="880f1-122">如果您選取了適當的模型類型，則當您按一下 [增益圖]\*\*\*\* 索引標籤時，圖表類型會自動設定為 [散佈圖]\*\*\*\*，然後顯示散佈圖。</span><span class="sxs-lookup"><span data-stu-id="880f1-122">If you have selected the appropriate type of model, when you click the **Lift Chart** tab, the chart type is automatically set to **Scatter Plot** and a scatter plot is displayed.</span></span> <span data-ttu-id="880f1-123">將無法進行進一步的組態設定。</span><span class="sxs-lookup"><span data-stu-id="880f1-123">No further configuration is possible.</span></span> <span data-ttu-id="880f1-124">您也可以將圖表複製到剪貼簿，然後以圖形的形式將圖表貼到 Excel 或另一個應用程式中。</span><span class="sxs-lookup"><span data-stu-id="880f1-124">You can also copy the chart to the Clipboard and paste the chart as a graphic into Excel or another application.</span></span>  
  
#### <a name="classification-matrix"></a><span data-ttu-id="880f1-125">分類矩陣</span><span class="sxs-lookup"><span data-stu-id="880f1-125">Classification Matrix</span></span>  
 <span data-ttu-id="880f1-126">如果是分類矩陣，請使用 [輸入選擇]\*\*\*\* 索引標籤來選擇模型及測試資料，然後按一下 [分類矩陣]\*\*\*\* 索引標籤來檢視結果。</span><span class="sxs-lookup"><span data-stu-id="880f1-126">For a classification matrix, use the **Input Selection** tab to choose the models and the testing data, and then click the **Classification Matrix** tab to view the results.</span></span>  
  
 <span data-ttu-id="880f1-127">所有模型類型的分類矩陣內容都相同且無法設定。</span><span class="sxs-lookup"><span data-stu-id="880f1-127">The contents of a classification matrix are the same for all model types, and cannot be configured.</span></span> <span data-ttu-id="880f1-128">您可以將圖表中的資料複製到剪貼簿，然後在 Excel 中進行處理。</span><span class="sxs-lookup"><span data-stu-id="880f1-128">You can copy the data in the chart to the Clipboard and then work with it in Excel.</span></span>  
  
#### <a name="cross-validation-report"></a><span data-ttu-id="880f1-129">交叉驗證報表</span><span class="sxs-lookup"><span data-stu-id="880f1-129">Cross-Validation Report</span></span>  
 <span data-ttu-id="880f1-130">如果是交叉驗證報表，當您在方案總管中選取採礦結構或採礦模型之後，請按一下 [交叉驗證]\*\*\*\* 索引標籤、設定所有相關的選項，然後按一下 [取得結果]\*\*\*\* 來產生報表。</span><span class="sxs-lookup"><span data-stu-id="880f1-130">For a cross-validation report, after you have selected a mining structure or mining model in Solution Explorer, click the **Cross Validation** tab, configure all relevant options, and then click **Get Results** to generate the report.</span></span> <span data-ttu-id="880f1-131">將無法進行進一步的組態設定。</span><span class="sxs-lookup"><span data-stu-id="880f1-131">No further configuration is possible.</span></span>  
  
 <span data-ttu-id="880f1-132">所有模型類型的交叉驗證報表格式都相同，且無法設定。</span><span class="sxs-lookup"><span data-stu-id="880f1-132">The format of the cross-validation report is the same for all model types, and cannot be configured.</span></span> <span data-ttu-id="880f1-133">但是，報表的內容會因您分析的模型類型以及可預測屬性的資料類型而異。</span><span class="sxs-lookup"><span data-stu-id="880f1-133">However, the content of the report differs depending on the type of model that you are analyzing, and the data type of the predictable attribute.</span></span> <span data-ttu-id="880f1-134">您也可以將報表的結果複製到剪貼簿，然後在 Excel 中處理資料。</span><span class="sxs-lookup"><span data-stu-id="880f1-134">You can also copy the results of the report to the Clipboard and work with the data in Excel.</span></span>  
  
  
