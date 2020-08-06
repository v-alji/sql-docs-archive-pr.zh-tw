---
title: 建立交叉驗證報表 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- validating data mining models
- mining structures [Analysis Services], how-to topics
- cross-validation [data mining]
- statistical standard deviation
ms.assetid: 7b1fec4c-7053-41eb-b030-5179257967a4
author: minewiskan
ms.author: owend
ms.openlocfilehash: ccbafe63b0026cd45a15ea71fd84e223c1b32a9c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686545"
---
# <a name="create-a-cross-validation-report"></a><span data-ttu-id="b87ac-102">建立交叉驗證報表</span><span class="sxs-lookup"><span data-stu-id="b87ac-102">Create a Cross-Validation Report</span></span>
  <span data-ttu-id="b87ac-103">此主題逐步解說如何在資料採礦設計師中使用 [精確度圖表] 索引標籤來建立交叉驗證報表。</span><span class="sxs-lookup"><span data-stu-id="b87ac-103">This topic walks you through creation of a cross-validation report using the Accuracy Chart tab in Data Mining Designer.</span></span> <span data-ttu-id="b87ac-104">如需交叉驗證報表外觀及其所含統計量值的一般資訊，請參閱[交叉驗證 &#40;Analysis Services - 資料採礦&#41;](cross-validation-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="b87ac-104">For general information about what a cross-validation report looks like, and the statistical measures it includes, see [Cross-Validation &#40;Analysis Services - Data Mining&#41;](cross-validation-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="b87ac-105">交叉驗證報表在本質上不同於增益圖或分類矩陣之類的精確度圖表。</span><span class="sxs-lookup"><span data-stu-id="b87ac-105">A cross-validation report is fundamentally different from an accuracy chart, such as a lift chart or classification matrix.</span></span>  
  
-   <span data-ttu-id="b87ac-106">交叉驗證評估模型或結構中所用資料的整體分佈情況；因此，您不指定測試資料集。</span><span class="sxs-lookup"><span data-stu-id="b87ac-106">Cross-validation assesses the overall distribution of data that is used in a model or structure; therefore, you do not specify a testing data set.</span></span> <span data-ttu-id="b87ac-107">交叉驗證永遠僅使用定型模型或採礦結構所用的原始資料。</span><span class="sxs-lookup"><span data-stu-id="b87ac-107">Cross-validation always uses only the original data that was used to train the model or the mining structure.</span></span>  
  
-   <span data-ttu-id="b87ac-108">只能針對單一可預測結果執行交叉驗證。</span><span class="sxs-lookup"><span data-stu-id="b87ac-108">Cross-validation can only be performed with respect to a single predictable outcome.</span></span> <span data-ttu-id="b87ac-109">如果結構支援具有不同可預測屬性的模型，您必須為每個可預測輸出建立不同的報表。</span><span class="sxs-lookup"><span data-stu-id="b87ac-109">If the structure supports models that have different predictable attributes, you must create separate reports for each predictable output.</span></span>  
  
-   <span data-ttu-id="b87ac-110">只有與目前選定結構有關的模型才可供交叉驗證使用。</span><span class="sxs-lookup"><span data-stu-id="b87ac-110">Only models that are related to the currently selected structure are available for cross-validation.</span></span>  
  
-   <span data-ttu-id="b87ac-111">如果目前所選的結構支援叢集和非叢集模型的組合，則在您按一下 [取得結果]\*\*\*\* 時，交叉驗證預存程序會自動載入具有相同預測資料行的模型，並且忽略不共用相同可預測屬性的叢集模型。</span><span class="sxs-lookup"><span data-stu-id="b87ac-111">If the structure that is currently selected supports a combination of clustering and non-clustering models, when you click **Get Results**, the cross-validation stored procedure will automatically load models that have the same predicted column, and ignore clustering models that do not share the same predictable attribute.</span></span>  
  
-   <span data-ttu-id="b87ac-112">只有在採礦模型不支援任何其他可預測屬性的情況下，您才可以對沒有可預測屬性的叢集模型建立交叉驗證報表。</span><span class="sxs-lookup"><span data-stu-id="b87ac-112">You can create a cross-validation report on a clustering model that does not have a predictable attribute only if the mining structure does not support any other predictable attributes.</span></span>  
  
### <a name="select-a-mining-structure"></a><span data-ttu-id="b87ac-113">選取採礦結構</span><span class="sxs-lookup"><span data-stu-id="b87ac-113">Select a mining structure</span></span>  
  
1.  <span data-ttu-id="b87ac-114">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中開啟資料採礦設計師。</span><span class="sxs-lookup"><span data-stu-id="b87ac-114">Open the Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="b87ac-115">在 [方案總管] 中，開啟包含您想要建立報表之結構或模型的資料庫。</span><span class="sxs-lookup"><span data-stu-id="b87ac-115">In Solution Explorer, open the database that contains the structure or model for which you want to create a report.</span></span>  
  
3.  <span data-ttu-id="b87ac-116">按兩下此採礦結構，在資料採礦設計師中開啟此結構以及其相關的模型。</span><span class="sxs-lookup"><span data-stu-id="b87ac-116">Double-click the mining structure to open the structure and its related models in Data Mining Designer.</span></span>  
  
4.  <span data-ttu-id="b87ac-117">按一下 **[採礦精確度圖表]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b87ac-117">Click the **Mining Accuracy Chart** tab.</span></span>  
  
5.  <span data-ttu-id="b87ac-118">按一下 **[交叉驗證]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b87ac-118">Click the **Cross Validation** tab.</span></span>  
  
### <a name="set-cross-validation-options"></a><span data-ttu-id="b87ac-119">設定交叉驗證選項</span><span class="sxs-lookup"><span data-stu-id="b87ac-119">Set cross-validation options</span></span>  
  
1.  <span data-ttu-id="b87ac-120">在 **[交叉驗證]** 索引標籤上，針對 **[摺疊計數]** 按一下向下箭頭，選取 1 到 10 之間的數字。</span><span class="sxs-lookup"><span data-stu-id="b87ac-120">On the **Cross Validation** tab, for **Fold Count**, click the down arrow to select a number between 1 and 10.</span></span> <span data-ttu-id="b87ac-121">預設值是 10。</span><span class="sxs-lookup"><span data-stu-id="b87ac-121">The default value is 10.</span></span>  
  
     <span data-ttu-id="b87ac-122">**[摺疊計數]** 表示將會在原始資料集內建立的資料分割數目。</span><span class="sxs-lookup"><span data-stu-id="b87ac-122">The **Fold Count** represents the number of partitions that will be created within the original data set.</span></span> <span data-ttu-id="b87ac-123">如果您將 [摺疊計數] 設定為 1，將會使用定型集而不加以分割。</span><span class="sxs-lookup"><span data-stu-id="b87ac-123">If you set Fold Count to 1, the training set will be used without partitioning.</span></span>  
  
2.  <span data-ttu-id="b87ac-124">針對 **[目標屬性]** 按一下向下箭頭，然後從清單中選取資料行。</span><span class="sxs-lookup"><span data-stu-id="b87ac-124">For **Target Attribute**, click the down arrow, and select a column from the list.</span></span> <span data-ttu-id="b87ac-125">如果此模型為叢集模型，請選取 [#Cluster]\*\*\*\* 來指示此模型沒有可預測屬性。</span><span class="sxs-lookup"><span data-stu-id="b87ac-125">If the model is a clustering model, select **#Cluster** to indicate that the model does not have a predictable attribute.</span></span> <span data-ttu-id="b87ac-126">請注意，只有在採礦結構不支援其他類型的可預測屬性時，值 **#Cluster**才可供使用。</span><span class="sxs-lookup"><span data-stu-id="b87ac-126">Note that the value, **#Cluster**, is available only when the mining structure does not support other types of predictable attributes.</span></span>  
  
     <span data-ttu-id="b87ac-127">每一個報表只能選取一個可預測屬性。</span><span class="sxs-lookup"><span data-stu-id="b87ac-127">You can select only one predictable attribute per report.</span></span> <span data-ttu-id="b87ac-128">根據預設，具有相同可預測屬性的所有相關模型都會包含在報表中。</span><span class="sxs-lookup"><span data-stu-id="b87ac-128">By default, all related models that have the same predictable attribute are included in the report.</span></span>  
  
3.  <span data-ttu-id="b87ac-129">在 **[最大案例數]** 中，輸入一個夠大的數字來提供當資料分割成指定的摺疊數時的代表性資料樣本。</span><span class="sxs-lookup"><span data-stu-id="b87ac-129">For **Max Cases**, type a number that is large enough to provide a representative sample of data when the data is split among the specified number of folds.</span></span> <span data-ttu-id="b87ac-130">如果此數字大於模型定型集內的案例計數，將會使用所有的案例。</span><span class="sxs-lookup"><span data-stu-id="b87ac-130">If the number is greater than the count of cases in the model training set, all cases will be used.</span></span>  
  
     <span data-ttu-id="b87ac-131">如果訓練資料集非常大，則設定 **[最大案例數]** 的值會限制處理的總案例數，並讓報表更快完成。</span><span class="sxs-lookup"><span data-stu-id="b87ac-131">If the training data set is very large, setting the value for **Max Cases** limits the total number of cases processed, and lets the report finish faster.</span></span> <span data-ttu-id="b87ac-132">但是，您不應該將 [最大案例數]\*\*\*\* 設定為太低的值，否則將不會有足夠的資料來進行交叉驗證。</span><span class="sxs-lookup"><span data-stu-id="b87ac-132">However, you should not set **Max Cases** too low or there may be insufficient data for cross-validation.</span></span>  
  
4.  <span data-ttu-id="b87ac-133">選擇性地針對 **[目標狀態]** 輸入您想要模型化之可預測屬性的值。</span><span class="sxs-lookup"><span data-stu-id="b87ac-133">Optionally, for **Target State**, type the value of the predictable attribute that you want to model.</span></span> <span data-ttu-id="b87ac-134">例如，如果 [Bike Buyer] 資料行有兩個可能的值：1 (是) 和 2 (否)，您可以輸入 1 的值，只針對所需結果評估此模型的精確度。</span><span class="sxs-lookup"><span data-stu-id="b87ac-134">For example, if the column [Bike Buyer] has two possible values, 1 (Yes) and 2 (No), you can enter the value 1 to assess the accuracy of the model for just the desired outcome.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b87ac-135"> 如果您不輸入值， **[目標臨界值]** 選項將無法使用，而且將會針對可預測屬性的所有可能值來評估此模型。</span><span class="sxs-lookup"><span data-stu-id="b87ac-135">If you do not enter a value, the **Target Threshold** option is not available, and the model is assessed for all possible values of the predictable attribute.</span></span>  
  
5.  <span data-ttu-id="b87ac-136">選擇性地針對 **[目標臨界值]** 輸入一個介於 0 和 1 之間的小數值，以指定要將預測算為精確時，所必須擁有的最小機率。</span><span class="sxs-lookup"><span data-stu-id="b87ac-136">Optionally, for **Target Threshold**, type a decimal number between 0 and 1 to specify the minimum probability that a prediction must have to be counted as accurate.</span></span>  
  
     <span data-ttu-id="b87ac-137">如需如何設定機率臨界值的更多提示，請參閱 [交叉驗證報表中的量值](measures-in-the-cross-validation-report.md)。</span><span class="sxs-lookup"><span data-stu-id="b87ac-137">For additional tips about how to set probability thresholds, see [Measures in the Cross-Validation Report](measures-in-the-cross-validation-report.md).</span></span>  
  
6.  <span data-ttu-id="b87ac-138">按一下 **[取得結果]**。</span><span class="sxs-lookup"><span data-stu-id="b87ac-138">Click **Get Results**.</span></span>  
  
### <a name="print-the-cross-validation-report"></a><span data-ttu-id="b87ac-139">列印交叉驗證報表</span><span class="sxs-lookup"><span data-stu-id="b87ac-139">Print the cross-validation report</span></span>  
  
1.  <span data-ttu-id="b87ac-140">在 [交叉驗證]\*\*\*\* 索引標籤上，以滑鼠右鍵按一下完成的報表。</span><span class="sxs-lookup"><span data-stu-id="b87ac-140">Right-click the completed report on the **Cross Validation** tab.</span></span>  
  
2.  <span data-ttu-id="b87ac-141">在快速鍵功能表中，選取 **[列印]** ，或選取 **[預覽列印]** 先檢閱報表。</span><span class="sxs-lookup"><span data-stu-id="b87ac-141">In the shortcut menu, select **Print** or **Print Preview** to review the report first.</span></span>  
  
### <a name="create-a-copy-of-the-report-in-microsoft-excel"></a><span data-ttu-id="b87ac-142">在 Microsoft Excel 中建立報表的複本</span><span class="sxs-lookup"><span data-stu-id="b87ac-142">Create a copy of the report in Microsoft Excel</span></span>  
  
1.  <span data-ttu-id="b87ac-143">在 [交叉驗證]\*\*\*\* 索引標籤上，以滑鼠右鍵按一下完成的報表。</span><span class="sxs-lookup"><span data-stu-id="b87ac-143">Right-click the completed report on the **Cross Validation** tab.</span></span>  
  
2.  <span data-ttu-id="b87ac-144">在快速鍵功能表中，選取 **[全選]**。</span><span class="sxs-lookup"><span data-stu-id="b87ac-144">In the shortcut menu, select **Select All**.</span></span>  
  
3.  <span data-ttu-id="b87ac-145">以滑鼠右鍵按一下選取的文字，然後選取 [複製]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b87ac-145">Right-click the selected text, and select **Copy**.</span></span>  
  
4.  <span data-ttu-id="b87ac-146">將選取範圍貼到開啟的 Excel 活頁簿中。</span><span class="sxs-lookup"><span data-stu-id="b87ac-146">Paste the selection into an open Excel workbook.</span></span> <span data-ttu-id="b87ac-147">如果您使用 **[貼上]** 選項，報表將會以 HTML 格式貼到 Excel 中，這樣會保留資料列和資料行的格式設定。</span><span class="sxs-lookup"><span data-stu-id="b87ac-147">If you use the **Paste** option, the report is pasted into Excel as HTML, which preserves row and column formatting.</span></span> <span data-ttu-id="b87ac-148">如果您針對文字或 Unicode 文字使用 [選擇性貼上]\*\*\*\* 選項來貼上報表，報表將會使用資料列分隔的格式貼上。</span><span class="sxs-lookup"><span data-stu-id="b87ac-148">If you paste the report by using the **Paste Special** options for text or Unicode text, the report is pasted in row-delimited format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b87ac-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b87ac-149">See Also</span></span>  
 [<span data-ttu-id="b87ac-150">交叉驗證報表中的量值</span><span class="sxs-lookup"><span data-stu-id="b87ac-150">Measures in the Cross-Validation Report</span></span>](measures-in-the-cross-validation-report.md)  
  
  
