---
title: 分類矩陣 (SQL Server 資料採礦增益集) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, validating
- classification matrix
- confusion table
- mining models, testing
ms.assetid: d6f620f4-39af-4714-9628-28ce3c361fca
author: minewiskan
ms.author: owend
ms.openlocfilehash: a930f2628ac41fc5886cf41d7ec0ad274b42bf2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593074"
---
# <a name="classification-matrix-sql-server-data-mining-add-ins"></a><span data-ttu-id="83e47-102">分類矩陣 (SQL Server 資料採礦增益集)</span><span class="sxs-lookup"><span data-stu-id="83e47-102">Classification Matrix (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="83e47-103">![資料採礦功能區中的分類矩陣按鈕](media/dmc-cmatrix.gif "資料採礦功能區中的分類矩陣按鈕")</span><span class="sxs-lookup"><span data-stu-id="83e47-103">![Classification Matrix button, Data Mining ribbon](media/dmc-cmatrix.gif "Classification Matrix button, Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="83e47-104">您可以使用分類矩陣來評估模型的預測精確度。</span><span class="sxs-lookup"><span data-stu-id="83e47-104">You can use the classification matrix to assess the accuracy of a model for prediction.</span></span> <span data-ttu-id="83e47-105">若要產生分類矩陣，您可以透過模型執行一組測試資料，然後分類矩陣工具會根據模型所做的預測，與測試集中的實際值做比較。</span><span class="sxs-lookup"><span data-stu-id="83e47-105">To generate a classification matrix, you run a set of testing data through the model, and the classification matrix tool compares the actual values from the testing set against the predictions made by the model.</span></span> <span data-ttu-id="83e47-106">您可以透過查看矩陣，快速地了解模型正確及預測錯誤的頻率。</span><span class="sxs-lookup"><span data-stu-id="83e47-106">By looking at the matrix, you can tell at a glance how often the model is correct, and how often it predicts wrongly.</span></span>  
  
 <span data-ttu-id="83e47-107">在這些增益集中，使用 [**分類矩陣**] wizard 來選取模型、指定測試資料，然後產生結果矩陣。</span><span class="sxs-lookup"><span data-stu-id="83e47-107">In these add-ins, use the **Classification Matrix** wizard to select a model, specify the testing data, and then generate a results matrix.</span></span>  
  
## <a name="how-to-read-a-classification-matrix"></a><span data-ttu-id="83e47-108">如何解讀分類矩陣</span><span class="sxs-lookup"><span data-stu-id="83e47-108">How to Read a Classification Matrix</span></span>  
 <span data-ttu-id="83e47-109">假設您的目標是要設計客戶忠誠度計畫，然後將客戶指派給適當的類別，讓您可以為他們提供適當的獎勵層級。</span><span class="sxs-lookup"><span data-stu-id="83e47-109">Let's assume your objective is to design a customer loyalty program and then assign customers to appropriate categories, so that you can provide them with the appropriate level of incentives.</span></span> <span data-ttu-id="83e47-110">您已針對報酬計畫（銅、銀級和金級）實行三個層級，並在試用階段將這些專案提供給客戶。</span><span class="sxs-lookup"><span data-stu-id="83e47-110">You have implemented three levels for the reward program -- bronze, silver, and gold - and given these out to customers in a trial phase.</span></span> <span data-ttu-id="83e47-111">您也設計了用於分析客戶及預測正確類別的模型。</span><span class="sxs-lookup"><span data-stu-id="83e47-111">You have also designed a model that analyzes customers and predicts the correct categories.</span></span> <span data-ttu-id="83e47-112">現在，您將針對測試資料使用分類矩陣，以判斷模型在預測所有客戶之適當供應項目的精確度。</span><span class="sxs-lookup"><span data-stu-id="83e47-112">Now you will use the classification matrix on the trial data to determine how good the model was at predicting the correct offer for all customers.</span></span>  
  
 <span data-ttu-id="83e47-113">分類矩陣中的資料表可顯示，根據模型的預測，分別指派到每種類別的客戶數目，並將此結果與每種獎勵等級加入的實際客戶數目進行比較。</span><span class="sxs-lookup"><span data-stu-id="83e47-113">The table from the classification matrix tells you how many customers would be assigned to each category based on the model, and compares that result to the number of customers who actually signed up for each reward level.</span></span>  
  
||<span data-ttu-id="83e47-114">銅級 (實際值)</span><span class="sxs-lookup"><span data-stu-id="83e47-114">Bronze (Actual)</span></span>|<span data-ttu-id="83e47-115">金級 (實際值)</span><span class="sxs-lookup"><span data-stu-id="83e47-115">Gold (Actual)</span></span>|<span data-ttu-id="83e47-116">銀級 (實際值)</span><span class="sxs-lookup"><span data-stu-id="83e47-116">Silver (Actual)</span></span>|  
|-|-----------------------|---------------------|-----------------------|  
|<span data-ttu-id="83e47-117">青銅卡</span><span class="sxs-lookup"><span data-stu-id="83e47-117">Bronze</span></span>|<span data-ttu-id="83e47-118">**94.45%**</span><span class="sxs-lookup"><span data-stu-id="83e47-118">**94.45%**</span></span>|<span data-ttu-id="83e47-119">15.18%</span><span class="sxs-lookup"><span data-stu-id="83e47-119">15.18%</span></span>|<span data-ttu-id="83e47-120">1.70%</span><span class="sxs-lookup"><span data-stu-id="83e47-120">1.70%</span></span>|  
|<span data-ttu-id="83e47-121">金卡</span><span class="sxs-lookup"><span data-stu-id="83e47-121">Gold</span></span>|<span data-ttu-id="83e47-122">2.72%</span><span class="sxs-lookup"><span data-stu-id="83e47-122">2.72%</span></span>|<span data-ttu-id="83e47-123">**84.82%**</span><span class="sxs-lookup"><span data-stu-id="83e47-123">**84.82%**</span></span>|<span data-ttu-id="83e47-124">0.00%</span><span class="sxs-lookup"><span data-stu-id="83e47-124">0.00%</span></span>|  
|<span data-ttu-id="83e47-125">銀卡</span><span class="sxs-lookup"><span data-stu-id="83e47-125">Silver</span></span>|<span data-ttu-id="83e47-126">1.84%</span><span class="sxs-lookup"><span data-stu-id="83e47-126">1.84%</span></span>|<span data-ttu-id="83e47-127">0.00%</span><span class="sxs-lookup"><span data-stu-id="83e47-127">0.00%</span></span>|<span data-ttu-id="83e47-128">**93.80%**</span><span class="sxs-lookup"><span data-stu-id="83e47-128">**93.80%**</span></span>|  
|<span data-ttu-id="83e47-129">*正確性*</span><span class="sxs-lookup"><span data-stu-id="83e47-129">*Correct*</span></span>|<span data-ttu-id="83e47-130">*95.45%*</span><span class="sxs-lookup"><span data-stu-id="83e47-130">*95.45%*</span></span>|<span data-ttu-id="83e47-131">*84.82%*</span><span class="sxs-lookup"><span data-stu-id="83e47-131">*84.82%*</span></span>|<span data-ttu-id="83e47-132">*98.30%*</span><span class="sxs-lookup"><span data-stu-id="83e47-132">*98.30%*</span></span>|  
|<span data-ttu-id="83e47-133">*分類錯誤*</span><span class="sxs-lookup"><span data-stu-id="83e47-133">*Misclassified*</span></span>|<span data-ttu-id="83e47-134">*4.55%*</span><span class="sxs-lookup"><span data-stu-id="83e47-134">*4.55%*</span></span>|<span data-ttu-id="83e47-135">*15.18%*</span><span class="sxs-lookup"><span data-stu-id="83e47-135">*15.18%*</span></span>|<span data-ttu-id="83e47-136">*1.70%*</span><span class="sxs-lookup"><span data-stu-id="83e47-136">*1.70%*</span></span>|  
  
-   <span data-ttu-id="83e47-137">每個資料行顯示測試資料集中的實際值。</span><span class="sxs-lookup"><span data-stu-id="83e47-137">Each column shows the actual values in the testing dataset.</span></span>  
  
-   <span data-ttu-id="83e47-138">每個資料列顯示預測值。</span><span class="sxs-lookup"><span data-stu-id="83e47-138">Each row shows the predicted values.</span></span>  
  
-   <span data-ttu-id="83e47-139">從矩陣左上角到右下角以對角線執行的粗體值，表示模型正確預測的值。</span><span class="sxs-lookup"><span data-stu-id="83e47-139">The values in boldface, which run diagonally from the upper-left corner to the lower-right corner of the matrix, give you the picture of what the model got right.</span></span>  
  
-   <span data-ttu-id="83e47-140">對角線以外的其他所有值表示錯誤。</span><span class="sxs-lookup"><span data-stu-id="83e47-140">All other values outside the diagonal represent errors.</span></span> <span data-ttu-id="83e47-141">某些錯誤是誤判，表示模型錯誤地預測客戶會加入金級方案。</span><span class="sxs-lookup"><span data-stu-id="83e47-141">Some errors are false positives, meaning the model predicted the customer would join the gold program but was wrong.</span></span>  <span data-ttu-id="83e47-142">根據您的問題範圍，誤判的成本可能會很大。</span><span class="sxs-lookup"><span data-stu-id="83e47-142">Depending on your domain, false positives can be very costly.</span></span>  
  
     <span data-ttu-id="83e47-143">其他錯誤則為誤否定，表示模型預測客戶不會感興趣，但其實客戶已加入方案。</span><span class="sxs-lookup"><span data-stu-id="83e47-143">Others are false negatives, meaning the model predicted the customer would not be interested though he or she did join the program.</span></span> <span data-ttu-id="83e47-144">同樣地，根據您的問題範圍，此錯失商機的成本可能會很大。</span><span class="sxs-lookup"><span data-stu-id="83e47-144">Again, depending on the problem domain, this lost opportunity cost might be significant.</span></span>  
  
## <a name="using-the-classification-matrix-wizard"></a><span data-ttu-id="83e47-145">使用分類矩陣精靈</span><span class="sxs-lookup"><span data-stu-id="83e47-145">Using the Classification Matrix Wizard</span></span>  
  
1.  <span data-ttu-id="83e47-146">選取要以其為預測基礎的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="83e47-146">Select the mining model on which to base predictions.</span></span>  
  
2.  <span data-ttu-id="83e47-147">選取新測試資料的來源，或使用隨結構儲存的測試資料。</span><span class="sxs-lookup"><span data-stu-id="83e47-147">Select a source of new test data, or use testing data that was saved with the structure.</span></span>  
  
3.  <span data-ttu-id="83e47-148">選取您要評估其精確度的資料行。</span><span class="sxs-lookup"><span data-stu-id="83e47-148">Select the column for which you want to assess accuracy.</span></span> <span data-ttu-id="83e47-149">建立矩陣時，可以只選擇一個資料行，但是該資料行可包含多個值。</span><span class="sxs-lookup"><span data-stu-id="83e47-149">You can choose only one column when creating a matrix, but the column can have multiple values.</span></span>  
  
     <span data-ttu-id="83e47-150">提示：如果可預測資料行包含許多要比較的資料行，解譯分類矩陣可能會很困難。</span><span class="sxs-lookup"><span data-stu-id="83e47-150">Tip: It can be difficult to interpret a classification matrix if your predictable column has many columns to compare.</span></span>  
  
     <span data-ttu-id="83e47-151">在 [**選取要預測**的資料行] 頁面中，您也可以指定是否要顯示不正確和不正確的值計數，或顯示百分比。</span><span class="sxs-lookup"><span data-stu-id="83e47-151">In the **Select Columns to Predict** page, you can also specify whether you want to display the count of incorrect and incorrect values, or display a percentage.</span></span>  
  
4.  <span data-ttu-id="83e47-152">在 [選取來源資料] 頁面上，指出您要使用外部測試資料，或使用隨模型儲存的測試資料。</span><span class="sxs-lookup"><span data-stu-id="83e47-152">On the Select Source Data page, indicate whether you are using external testing data, or the test data saved with the model.</span></span>  
  
5.  <span data-ttu-id="83e47-153">如果您使用外部測試資料，您需要在 wizard 的 [**指定關聯**性] 頁面上，將模型對應到輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="83e47-153">If you use external testing data, you need to map the model to the input columns on the **Specify Relationship** page of the wizard.</span></span>  
  
     <span data-ttu-id="83e47-154">如果使用內嵌的測試資料集，則會自動為您完成對應</span><span class="sxs-lookup"><span data-stu-id="83e47-154">If you use the embedded test data set, the mapping is done for you</span></span>  
  
6.  <span data-ttu-id="83e47-155">按一下 **[完成]** ，針對模型執行預測並產生分類矩陣。</span><span class="sxs-lookup"><span data-stu-id="83e47-155">Click **Finish** to run predictions against the model and generate the classification matrix.</span></span>  
  
     <span data-ttu-id="83e47-156">精靈會建立報表，其中包含分類矩陣和關於分析的其他詳細資料。</span><span class="sxs-lookup"><span data-stu-id="83e47-156">The wizard creates a report that contains the classification matrix and other details about the analysis.</span></span> <span data-ttu-id="83e47-157">此報表會儲存為 Excel 資料表，報表上方的摘要指出正確預測的案例數目，以及錯誤的預測數目。</span><span class="sxs-lookup"><span data-stu-id="83e47-157">This report is saved as a table in Excel, with a summary above the report that indicates how many cases were correctly predicted and how many predictions were wrong.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="83e47-158">需求</span><span class="sxs-lookup"><span data-stu-id="83e47-158">Requirements</span></span>  
  
-   <span data-ttu-id="83e47-159">若要建立分類矩陣，您必須能夠存取可評估精確度的現有採礦模型。</span><span class="sxs-lookup"><span data-stu-id="83e47-159">To create a classification matrix, you must have access to an existing mining model that supports accuracy measurement.</span></span> <span data-ttu-id="83e47-160">此工具無法用來評估預測模型和關聯模型。</span><span class="sxs-lookup"><span data-stu-id="83e47-160">Forecasting models and association models cannot be measured using this tool.</span></span>  
  
-   <span data-ttu-id="83e47-161">評估的模型需要預測一個離散值或已離散化的值。</span><span class="sxs-lookup"><span data-stu-id="83e47-161">The model that you are measuring needs to predict a value that is either discrete or that has already been discretized.</span></span>  
  
-   <span data-ttu-id="83e47-162">如果您未使用此選項來儲存測試集，以及您的結構或模型，則需要取得與模型中所使用之資料行數目相同的輸入資料集。</span><span class="sxs-lookup"><span data-stu-id="83e47-162">If you didn't use the option to save a testing set along with your structure or model, you need to obtain an input data set that has essentially the same number of columns, with matching data types, as those used in the model.</span></span>  
  
-   <span data-ttu-id="83e47-163">您用於測試的資料採礦模型和新的資料至少必須包含一個可以預測的資料行，而該資料行必須包含相同種類的資料。</span><span class="sxs-lookup"><span data-stu-id="83e47-163">Both the data mining model and the new data that you are using for testing must contain at least one column that can be predicted, and the columns must contain the same kind of data.</span></span>  
  
### <a name="known-issues"></a><span data-ttu-id="83e47-164">已知問題</span><span class="sxs-lookup"><span data-stu-id="83e47-164">Known Issues</span></span>  
 <span data-ttu-id="83e47-165">在 SQL Server 2012 和 SQL Server 2014 中，將內部測試資料集對應至模型的功能無法在**分類矩陣**工具中運作。</span><span class="sxs-lookup"><span data-stu-id="83e47-165">In SQL Server 2012 and SQL Server 2014, the ability to map the internal test data set to the model is not working in the **Classification Matrix** tool.</span></span> <span data-ttu-id="83e47-166">不過，您可以指定外部資料集，然後選取定型集做為輸入，以判斷原始資料集是否有誤。</span><span class="sxs-lookup"><span data-stu-id="83e47-166">However, you can specify an external data set, and then select the training set as the input to determine error on the original data set.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83e47-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83e47-167">See Also</span></span>  
 <span data-ttu-id="83e47-168">[驗證模型及使用模型進行預測 &#40;適用于 Excel 的資料採礦增益集&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="83e47-168">[Validating Models and Using Models for Prediction &#40;Data Mining Add-ins for Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md) </span></span>  
 <span data-ttu-id="83e47-169">[流覽資料 &#40;SQL Server 資料採礦增益集&#41;](explore-data-sql-server-data-mining-add-ins.md) </span><span class="sxs-lookup"><span data-stu-id="83e47-169">[Explore Data &#40;SQL Server Data Mining Add-ins&#41;](explore-data-sql-server-data-mining-add-ins.md) </span></span>  
 [<span data-ttu-id="83e47-170">偵測適用于 Excel&#41;&#40;資料表分析工具的分類</span><span class="sxs-lookup"><span data-stu-id="83e47-170">Detect Categories &#40;Table Analysis Tools for Excel&#41;</span></span>](detect-categories-table-analysis-tools-for-excel.md)  
  
  
