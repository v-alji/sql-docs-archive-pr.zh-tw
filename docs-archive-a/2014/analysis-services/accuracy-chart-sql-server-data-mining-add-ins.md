---
title: 精確度圖表 (SQL Server 資料採礦增益集) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- accuracy chart
- mining models, validating
- mining models, charting
- lift chart
- mining models, testing
- lift [data mining]
ms.assetid: 303973b4-71c0-4cfc-b7bc-92218b52509d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 45ca5b4d3944948b257b5fa063ebce5583701157
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592353"
---
# <a name="accuracy-chart-sql-server-data-mining-add-ins"></a><span data-ttu-id="2b8ae-102">精確度圖表 (SQL Server 資料採礦增益集)</span><span class="sxs-lookup"><span data-stu-id="2b8ae-102">Accuracy Chart (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="2b8ae-103">![資料採礦功能區中的精確度圖表按鈕](media/dmc-accchart.gif "資料採礦功能區中的精確度圖表按鈕")</span><span class="sxs-lookup"><span data-stu-id="2b8ae-103">![Accuracy Chart button in Data Mining ribbon](media/dmc-accchart.gif "Accuracy Chart button in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="2b8ae-104">精確度圖表可讓您將模型套用到新的資料集，然後評估模型執行的妥善程度。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-104">An accuracy chart enables you to apply a model to a new set of data and then evaluate how well the model performs.</span></span> <span data-ttu-id="2b8ae-105">此 wizard 所建立的精確度圖表是增益*圖*，這是一種圖表類型，經常用來測量資料採礦模型的精確度。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-105">The accuracy chart created by this wizard is a *lift chart*, which is a type of chart that is frequently used to measure the accuracy of a data mining model.</span></span> <span data-ttu-id="2b8ae-106">這種類型的精確度圖表會顯示與隨機預測和 100% 預測均為精確的理想案例相較之下，使用指定的資料採礦模型所取得之改進的圖形表示。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-106">This type of accuracy chart displays a graphical representation of the improvement that you obtain from using the specified data mining model, as compared to random predictions, and to the ideal case where 100 percent of predictions are accurate.</span></span> <span data-ttu-id="2b8ae-107">您可以在單一圖表中比較多個模型。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-107">You can compare multiple models within a single chart.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b8ae-108">範例</span><span class="sxs-lookup"><span data-stu-id="2b8ae-108">Example</span></span>  
 <span data-ttu-id="2b8ae-109">請考量 Adventure Works Cycles 的行銷部門所要建立的鎖定郵寄活動案例。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-109">Consider the case in which the Marketing department at Adventure Works Cycles wants to create a targeted mailing campaign.</span></span> <span data-ttu-id="2b8ae-110">根據以往的活動，他們知道通常可以收到百分之 10 的回應率。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-110">From past campaigns, they know that a 10 percent response rate is typical.</span></span> <span data-ttu-id="2b8ae-111">他們在資料庫的資料表中儲存了一份 10,000 位潛在客戶的清單。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-111">They have a list of 10,000 potential customers stored in a table in the database.</span></span> <span data-ttu-id="2b8ae-112">根據一般的回應率，他們預期有 1,000 位客戶會回應。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-112">Based on the typical response rate, they can expect 1,000 customers to respond.</span></span>  
  
 <span data-ttu-id="2b8ae-113">但是因為他們只能負擔將廣告郵寄給 5,000 名客戶，因此行銷部門使用採礦模型針對 5,000 最可能回應的客戶。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-113">However, because they can afford to mail an advertisement to only 5,000 customers, the Marketing department uses a mining model to target the 5,000 customers who are most likely to respond.</span></span>  
  
 <span data-ttu-id="2b8ae-114">如果公司隨機選取 5,000 位客戶，則預期只會收到 500 個正面回應，因為鎖定的客戶中通常只有百分之 10 會回應。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-114">If the company randomly selects 5,000 customers, they can expect to receive only 500 positive responses, because only 10 percent of those who are targeted typically respond.</span></span> <span data-ttu-id="2b8ae-115">此狀況就是增益圖中的隨機線條代表的意義。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-115">This scenario is what the random line in the lift chart represents.</span></span>  
  
 <span data-ttu-id="2b8ae-116">不過，如果行銷部門使用採礦模型來鎖定郵寄，而且該模型是完美的，公司便會預期在將廣告郵寄到模型所建議的 1,000 位潛在客戶時，可收到 1,000 位的回應。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-116">However, if the Marketing department uses a mining model to target their mailing, and if the model were perfect, the company could expect to receive 1,000 responses by mailing an advertisement to the 1,000 potential customers recommended by the model.</span></span> <span data-ttu-id="2b8ae-117">在增益圖中以理想線條代表此狀況。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-117">This scenario is represented by the ideal line in the lift chart.</span></span>  
  
## <a name="using-the-accuracy-chart-wizard"></a><span data-ttu-id="2b8ae-118">使用精確度圖表精靈</span><span class="sxs-lookup"><span data-stu-id="2b8ae-118">Using the Accuracy Chart Wizard</span></span>  
 <span data-ttu-id="2b8ae-119">若要建立精確度圖表，您必須參考現有的資料採礦結構。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-119">To create an accuracy chart, you must reference an existing data mining structure.</span></span> <span data-ttu-id="2b8ae-120">只要預測的是相同的事情，您就可以根據該結構，測量多個模型的精確度。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-120">You can measure the accuracy of multiple models that are based on that structure, as long as they predict the same thing.</span></span>  
  
 <span data-ttu-id="2b8ae-121">如果不確定可以使用哪些結構，您可以瀏覽伺服器。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-121">If you are not sure which structures are available, you can browse the server.</span></span> <span data-ttu-id="2b8ae-122">如需詳細資訊，請參閱[在 Excel 中流覽模型 &#40;SQL Server 資料採礦增益集&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-122">For more information, see [Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md).</span></span>  
  
#### <a name="to-create-an-accuracy-chart"></a><span data-ttu-id="2b8ae-123">建立精確度圖表</span><span class="sxs-lookup"><span data-stu-id="2b8ae-123">To create an accuracy chart</span></span>  
  
1.  <span data-ttu-id="2b8ae-124">按一下 [**資料採礦用戶端**] 功能區。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-124">Click the **Data Mining Client** ribbon.</span></span>  
  
2.  <span data-ttu-id="2b8ae-125">在 [**精確度和驗證**] 群組中，按一下 [**精確度圖表**]。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-125">In the **Accuracy and Validation** group, click **Accuracy Chart**.</span></span>  
  
3.  <span data-ttu-id="2b8ae-126">在 [**選取結構或模型**] 對話方塊中，選擇您要評估的模型。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-126">In the **Select Structure or Model** dialog box, choose the model that you want to evaluate.</span></span> <span data-ttu-id="2b8ae-127">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-127">Click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2b8ae-128">您必須選擇緊密符合您所要測試之資料的模型。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-128">You must choose a model that closely matches the data you intend to test.</span></span>  
  
4.  <span data-ttu-id="2b8ae-129">在 [**指定要預測的資料行及要預測的值**] 對話方塊中，選擇您想要預測的資料行和目標值（如果適用的話）。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-129">In the **Specify Column to Predict and Value to Predict** dialog box, choose the column that you want to predict, and a target value, if appropriate.</span></span> <span data-ttu-id="2b8ae-130">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-130">Click **Next**.</span></span>  
  
     <span data-ttu-id="2b8ae-131">例如，在以上的範例中，您可能選擇模型化客戶回應的資料行，並將目標值指定為 "Probably Will Buy"。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-131">For example, in the example above, you might choose the column that models the customer response, and specify the target value as "Probably Will Buy".</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2b8ae-132">您無法預測連續的值；</span><span class="sxs-lookup"><span data-stu-id="2b8ae-132">You cannot predict a continuous value.</span></span> <span data-ttu-id="2b8ae-133">但是，您可以將值分在離散範圍來離散化資料行。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-133">However, you can discretize the column by separating the values into discrete ranges.</span></span> <span data-ttu-id="2b8ae-134">您必須先進行這項處理，然後才能建立資料採礦模型。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-134">You must do this before creating the data mining model.</span></span>  
  
5.  <span data-ttu-id="2b8ae-135">在 [**選取來源資料**] 對話方塊中，指定您將透過模型傳遞之資料的來源，以便建立預測。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-135">In the **Select Source Data** dialog box, specify the source of the data that you will pass through the model in order to create a prediction.</span></span>  
  
6.  <span data-ttu-id="2b8ae-136">如果您使用資料的外部來源，而不是與模型一起儲存的測試資料，請在 [**指定關聯**性] 對話方塊中，將新來源資料中的資料行對應至資料採礦模型中所使用的資料行。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-136">If you are using an external source of data, and not the test data that is stored with the model, in the **Specify Relationships** dialog box, map the columns in the new source data to the columns used in the data mining model.</span></span>  
  
     <span data-ttu-id="2b8ae-137">如果資料行名稱相似，精靈便會自動加以對應。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-137">If the column names are similar, the wizard will automatically map them.</span></span> <span data-ttu-id="2b8ae-138">雖然輸入資料中的某些資料行可能與分析無關而且可以忽略，但是還需要某些資料行，資料採礦模型才能處理輸入。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-138">Although some columns in your input data may be irrelevant to analysis and can be ignored, some columns are required for the data mining model to process the input.</span></span> <span data-ttu-id="2b8ae-139">這類資料行可能包含交易識別碼、目標值或用於預測的資料行。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-139">Such columns might include a transaction ID, the target value, or columns used for prediction.</span></span> <span data-ttu-id="2b8ae-140">如果您無法對應所需的資料行，此精靈將會提供一則警告訊息。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-140">If you fail to map a column that is required, the wizard will provide a warning message.</span></span>  
  
7.  <span data-ttu-id="2b8ae-141">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-141">Click **Finish**.</span></span>  
  
     <span data-ttu-id="2b8ae-142">精靈會建立報表，其中包含增益圖和基礎資料。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-142">The wizard creates a report that includes the lift chart and underlying data.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="2b8ae-143">需求</span><span class="sxs-lookup"><span data-stu-id="2b8ae-143">Requirements</span></span>  
 <span data-ttu-id="2b8ae-144">如果您是在預測離散值，便必須選取您所要預測的目標值。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-144">If you are predicting a discrete value, you must select the target value that you want to predict.</span></span> <span data-ttu-id="2b8ae-145">例如，如果您的資料被分類成回應 "Yes: Buy" 為 1，回應 "No: Do Not Buy" 為 2，您就必須將 1 或 2 指定為預測值。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-145">For example, if your data is categorized with a response "Yes: Buy" as 1 and the response "No: Do Not Buy" as 2, you must specify either 1 or 2 as the prediction values.</span></span> <span data-ttu-id="2b8ae-146">不過，如果您要預測值的範圍，便只能在同時比較兩個值。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-146">However, if you want to predict a range of values, you can compare only two values at a time.</span></span> <span data-ttu-id="2b8ae-147">例如，如果您要預測高於 5 的分數，便必須重新標籤您的來源資料，並建立將結果分割為兩組的新模型：高於 5 的分數和低於 5 的分數。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-147">For example, if you want to predict a score above 5, you might have to relabel your source data and create a new model that separates the results into two sets: those greater than 5 and those less than 5.</span></span> <span data-ttu-id="2b8ae-148">然後您便可以比較這兩個群組的精確度。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-148">You can then compare the accuracy of those two groups.</span></span>  
  
## <a name="understanding-accuracy"></a><span data-ttu-id="2b8ae-149">了解精確度</span><span class="sxs-lookup"><span data-stu-id="2b8ae-149">Understanding Accuracy</span></span>  
 <span data-ttu-id="2b8ae-150">您可以建立兩種類型的圖表，其中一個指定可預測資料行的狀態，另一個不指定狀態。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-150">You can create two types of charts, one in which you specify a state of the predictable column, and one in which you do not specify the state.</span></span>  
  
 <span data-ttu-id="2b8ae-151">如果您指定可預測資料行的狀態，圖表的 x 軸代表用來比較預測之測試資料集的百分比。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-151">If you specify the state of the predictable column, the x-axis of the chart represents the percentage of the test dataset that is used to compare the predictions.</span></span> <span data-ttu-id="2b8ae-152">圖表的 y 軸代表預測做為指定狀態之值的百分比。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-152">The y-axis of the chart represents the percentage of values that are predicted to be the specified state.</span></span>  
  
 <span data-ttu-id="2b8ae-153">如果您不指定可預測資料行的狀態，該圖表就會針對所有可能的預測，顯示圖表的精確度。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-153">If you do not specify the state of the predictable column, the chart shows the accuracy of the model for all possible predictions.</span></span>  
  
 <span data-ttu-id="2b8ae-154">如需有關增益圖如何運作，以及如何根據隨機和理想預測線來計算精確度的詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 線上叢書》中的＜增益圖＞主題。</span><span class="sxs-lookup"><span data-stu-id="2b8ae-154">For more information about how a lift chart works, and how accuracy is calculated based on the random and ideal prediction lines, see the topic "Lift Chart" in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b8ae-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b8ae-155">See Also</span></span>  
 [<span data-ttu-id="2b8ae-156">驗證模型及使用模型進行預測 &#40;適用于 Excel 的資料採礦增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="2b8ae-156">Validating Models and Using Models for Prediction &#40;Data Mining Add-ins for Excel&#41;</span></span>](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)  
  
  
