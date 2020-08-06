---
title: 探索和清除資料 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7c888c95-8986-461e-9f11-2395044b9d97
author: minewiskan
ms.author: owend
ms.openlocfilehash: 154c711f735bcbb472e49654139fd16a036a0dd5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584809"
---
# <a name="exploring-and-cleaning-data"></a><span data-ttu-id="6fc29-102">瀏覽和清除資料</span><span class="sxs-lookup"><span data-stu-id="6fc29-102">Exploring and Cleaning Data</span></span>
  <span data-ttu-id="6fc29-103">資料準備不只是進行資料清理而已。</span><span class="sxs-lookup"><span data-stu-id="6fc29-103">Data preparation is much more than data cleansing.</span></span> <span data-ttu-id="6fc29-104">務必記得，準備資料的方式也會影響最後解譯結果的方式。</span><span class="sxs-lookup"><span data-stu-id="6fc29-104">Remember that how data is prepared also affects how results are interpreted in the end.</span></span> <span data-ttu-id="6fc29-105">資料準備包含下列工作：</span><span class="sxs-lookup"><span data-stu-id="6fc29-105">Data preparation involves these tasks:</span></span>  
  
-   <span data-ttu-id="6fc29-106">瀏覽及檢查資料分佈情形。</span><span class="sxs-lookup"><span data-stu-id="6fc29-106">Exploring and checking the distribution of data.</span></span>  
  
-   <span data-ttu-id="6fc29-107">清除不正確的記錄，以及選擇要進行資料採礦的資料行。</span><span class="sxs-lookup"><span data-stu-id="6fc29-107">Cleaning bad records, and choosing columns for data mining.</span></span>  
  
-   <span data-ttu-id="6fc29-108">適當處理 Null。</span><span class="sxs-lookup"><span data-stu-id="6fc29-108">Handling nulls appropriately.</span></span>  
  
-   <span data-ttu-id="6fc29-109">分類收納值，或依不同的時段彙總值。</span><span class="sxs-lookup"><span data-stu-id="6fc29-109">Binning values, or aggregating values by different chunks of time.</span></span>  
  
-   <span data-ttu-id="6fc29-110">加入標籤來改善結果的可用性。</span><span class="sxs-lookup"><span data-stu-id="6fc29-110">Adding labels to improve the usability of the results.</span></span>  
  
-   <span data-ttu-id="6fc29-111">視需要轉換資料類型或將值分類以進行分析。</span><span class="sxs-lookup"><span data-stu-id="6fc29-111">Converting data types or categorizing values where necessary for analysis.</span></span>  
  
 <span data-ttu-id="6fc29-112">如果您是資料模型化的新手，我們建議您閱讀相關主題：[資料採礦準備的檢查清單](checklist-of-preparation-for-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="6fc29-112">If you are new to data modeling, we recommend that you read the related topic, [Checklist of Preparation for Data Mining](checklist-of-preparation-for-data-mining.md).</span></span>  
  
## <a name="data-preparation-tools"></a><span data-ttu-id="6fc29-113">資料準備工具</span><span class="sxs-lookup"><span data-stu-id="6fc29-113">Data Preparation Tools</span></span>  
 <span data-ttu-id="6fc29-114">適用於 Office 的資料採礦增益集包括了可用於資料清理和準備的以下工具：</span><span class="sxs-lookup"><span data-stu-id="6fc29-114">The Data Mining Add-ins for Office includes the following tools for data cleansing and preparation:</span></span>  
  
### <a name="explore-data"></a><span data-ttu-id="6fc29-115">瀏覽資料</span><span class="sxs-lookup"><span data-stu-id="6fc29-115">Explore Data</span></span>  
 <span data-ttu-id="6fc29-116">使用 [**流覽資料**] 嚮導來進行這些資料準備工作：</span><span class="sxs-lookup"><span data-stu-id="6fc29-116">Use the **Explore Data** wizard for these data preparation tasks:</span></span>  
  
-   <span data-ttu-id="6fc29-117">預覽資料並識別出必須在分析之前修正的錯誤。</span><span class="sxs-lookup"><span data-stu-id="6fc29-117">Preview your data and identify errors that must be fixed prior to analysis.</span></span>  
  
-   <span data-ttu-id="6fc29-118">收集統計資訊，有助於了解資料的平衡與必要的清除工作。</span><span class="sxs-lookup"><span data-stu-id="6fc29-118">Gather statistical information that is useful for understanding the balance of data and the required clean-up tasks.</span></span>  
  
-   <span data-ttu-id="6fc29-119">識別對分析有用的資料行，並規劃資料模型化階段。</span><span class="sxs-lookup"><span data-stu-id="6fc29-119">Identify columns that are useful for analysis, and plan the data modeling phase.</span></span>  
  
 <span data-ttu-id="6fc29-120">[流覽資料 &#40;SQL Server 資料採礦增益集&#41;](explore-data-sql-server-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="6fc29-120">[Explore Data &#40;SQL Server Data Mining Add-ins&#41;](explore-data-sql-server-data-mining-add-ins.md).</span></span>  
  
### <a name="detect-and-handle-outliers"></a><span data-ttu-id="6fc29-121">偵測及處理極端值</span><span class="sxs-lookup"><span data-stu-id="6fc29-121">Detect and Handle Outliers</span></span>  
 <span data-ttu-id="6fc29-122">[極端**值] 嚮導會將資料**中的值分佈繪製成圖形，並協助您移除極端值。</span><span class="sxs-lookup"><span data-stu-id="6fc29-122">The **Outliers** wizard graphs the distribution of values in your data and helps you remove extreme values.</span></span> <span data-ttu-id="6fc29-123">使用 [極端值 **] 工具進行**下列資料準備工作：</span><span class="sxs-lookup"><span data-stu-id="6fc29-123">Use the **Outliers** tool for the following data preparation tasks:</span></span>  
  
-   <span data-ttu-id="6fc29-124">根據在資料中找到的模式來判斷個別值是否可靠。</span><span class="sxs-lookup"><span data-stu-id="6fc29-124">Determine whether individual values are reliable, based on patterns found in the data.</span></span>  
  
-   <span data-ttu-id="6fc29-125">檢閱不尋常的值並採取行動來刪除或取代它們。</span><span class="sxs-lookup"><span data-stu-id="6fc29-125">Review unusual values and take action by deleting or replacing them.</span></span>  
  
-   <span data-ttu-id="6fc29-126">將模型限定在某指定範圍的值。</span><span class="sxs-lookup"><span data-stu-id="6fc29-126">Scope a model to a specific range of values.</span></span> <span data-ttu-id="6fc29-127">例如，如果您知道某特定商店有極端值，您可以刪除該值並取得更能準確預測其他商店的模型。</span><span class="sxs-lookup"><span data-stu-id="6fc29-127">For example, if you know that you have outliers at a particular store, you can eliminate that value and get a model that better predicts other stores.</span></span>  
  
 <span data-ttu-id="6fc29-128">[SQL Server 資料採礦增益集&#41;](outliers-sql-server-data-mining-add-ins.md)的極端值 &#40;。</span><span class="sxs-lookup"><span data-stu-id="6fc29-128">[Outliers &#40;SQL Server Data Mining Add-ins&#41;](outliers-sql-server-data-mining-add-ins.md).</span></span>  
  
### <a name="relabel-and-bin-data"></a><span data-ttu-id="6fc29-129">重定標籤和分類收納資料</span><span class="sxs-lookup"><span data-stu-id="6fc29-129">Relabel and Bin Data</span></span>  
 <span data-ttu-id="6fc29-130">重新**標記**的 wizard 會依值將資料分組，讓您可以變更資料上的標籤。</span><span class="sxs-lookup"><span data-stu-id="6fc29-130">The **Relabel** wizard groups data by values so that you can change the labels on the data.</span></span> <span data-ttu-id="6fc29-131">使用重定標籤工具來進行以下這些資料準備工作：</span><span class="sxs-lookup"><span data-stu-id="6fc29-131">Use the Relabel tool for these data preparation tasks:</span></span>  
  
-   <span data-ttu-id="6fc29-132">將調查結果中使用的數字代碼變更為此數字代碼所代表的文字描述。</span><span class="sxs-lookup"><span data-stu-id="6fc29-132">Change numeric codes used in survey results to a text description of what the numeric code means.</span></span>  
  
     <span data-ttu-id="6fc29-133">例如，您可以取代資料項目 (例如以 Gender = Female 取代 Gender = 1)。</span><span class="sxs-lookup"><span data-stu-id="6fc29-133">For example, you might replace data entries such as Gender = 1 with Gender = Female.</span></span>  
  
-   <span data-ttu-id="6fc29-134">您可以建立代表數量範圍的群組，來分類收納資料。</span><span class="sxs-lookup"><span data-stu-id="6fc29-134">Bin data, by creating groups to represents number ranges.</span></span>  
  
     <span data-ttu-id="6fc29-135">例如，您可能會想要將數位的收入資料行取代為標籤，例如**收入-中度**和**收入-高**。</span><span class="sxs-lookup"><span data-stu-id="6fc29-135">For example, you might want to replace an Income column of numbers with labels such as **Income - Moderate** and **Income - High**.</span></span>  
  
-   <span data-ttu-id="6fc29-136">將離散值摺疊成類別目錄。</span><span class="sxs-lookup"><span data-stu-id="6fc29-136">Collapse discrete values into categories.</span></span>  
  
     <span data-ttu-id="6fc29-137">例如，如果您有太多個別產品偵測到購買模式，您可以嘗試將這些產品指派到更廣泛的類別目錄。</span><span class="sxs-lookup"><span data-stu-id="6fc29-137">For example, if you have too many individual products to detect a pattern among purchases, you could try assigning products into broader categories.</span></span>  
  
 [<span data-ttu-id="6fc29-138">重新標記 &#40;SQL Server 資料採礦增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="6fc29-138">Relabel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](relabel-sql-server-data-mining-add-ins.md)  
  
### <a name="cleanse-data"></a><span data-ttu-id="6fc29-139">清理資料</span><span class="sxs-lookup"><span data-stu-id="6fc29-139">Cleanse Data</span></span>  
 <span data-ttu-id="6fc29-140">資料清理包含各種活動，大部分活動由增益集支援。</span><span class="sxs-lookup"><span data-stu-id="6fc29-140">Data cleansing encompasses a wide range of activities, most of which are supported by the add-ins</span></span>  
  
-   <span data-ttu-id="6fc29-141">識別 Null 值，並判斷是否應該將這些值變更為實數值，或視為 `Missing` 值來處理。</span><span class="sxs-lookup"><span data-stu-id="6fc29-141">Identify nulls and determine whether they should be changed to a real value or handled as `Missing` values.</span></span>  
  
-   <span data-ttu-id="6fc29-142">偵測遺漏的值，然後移除它們或推算一個適當的值，例如平均值、Null 或其他值。</span><span class="sxs-lookup"><span data-stu-id="6fc29-142">Detect missing values, and then remove them, or impute an appropriate value, such as a mean, null, or other value.</span></span>  
  
 [<span data-ttu-id="6fc29-143">流覽資料 &#40;SQL Server 資料採礦增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="6fc29-143">Explore Data &#40;SQL Server Data Mining Add-ins&#41;</span></span>](explore-data-sql-server-data-mining-add-ins.md)  
  
 [<span data-ttu-id="6fc29-144">重新標記 &#40;SQL Server 資料採礦增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="6fc29-144">Relabel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](relabel-sql-server-data-mining-add-ins.md)  
  
 [<span data-ttu-id="6fc29-145">根據範例填滿</span><span class="sxs-lookup"><span data-stu-id="6fc29-145">Fill From Example</span></span>](fill-from-example-table-analysis-tools-for-excel.md)  
  
### <a name="sample-data"></a><span data-ttu-id="6fc29-146">取樣資料</span><span class="sxs-lookup"><span data-stu-id="6fc29-146">Sample Data</span></span>  
 <span data-ttu-id="6fc29-147">取樣資料精靈提供兩種方法，可用來建立定型模型和測試模型的對稱資料集。</span><span class="sxs-lookup"><span data-stu-id="6fc29-147">The Sample Data wizard provides two methods for creating balanced data sets for training and testing models.</span></span>  
  
-   <span data-ttu-id="6fc29-148">**隨機取樣。**</span><span class="sxs-lookup"><span data-stu-id="6fc29-148">**Random sampling.**</span></span> <span data-ttu-id="6fc29-149">使用這個選項即可從較大資料集擷取代表性資料集，以用於定型或測試。</span><span class="sxs-lookup"><span data-stu-id="6fc29-149">Use this option to extract a representative set of data from a larger data set, for use in either training or testing.</span></span> <span data-ttu-id="6fc29-150">資料採礦增益集會使用*分層取樣*，以確保為每個取樣的變數取得一組平衡的值。</span><span class="sxs-lookup"><span data-stu-id="6fc29-150">The Data Mining Add-ins use *stratified sampling* to ensure that a balanced set of values is obtained for each variable sampled.</span></span>  
  
-   <span data-ttu-id="6fc29-151">**超取樣.**</span><span class="sxs-lookup"><span data-stu-id="6fc29-151">**Oversampling.**</span></span> <span data-ttu-id="6fc29-152">當您的資料比目標結果所需的資料少，而必須提高資料的加權時，請使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="6fc29-152">Use this option when you have less data than you would like for a target outcome, and need to weight that data more heavily.</span></span> <span data-ttu-id="6fc29-153">例如，詐欺可能相當罕見，不過您可以超取樣與詐欺相關的案例，為模型取得足夠的資料。</span><span class="sxs-lookup"><span data-stu-id="6fc29-153">For example, fraud might be relatively rare, but you can oversample cases involving fraud to get adequate data for modeling.</span></span>  
  
 <span data-ttu-id="6fc29-154">[SQL Server 資料採礦增益集&#41;的範例資料 &#40;](sample-data-sql-server-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="6fc29-154">[Sample Data &#40;SQL Server Data Mining Add-ins&#41;](sample-data-sql-server-data-mining-add-ins.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fc29-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6fc29-155">See Also</span></span>  
 <span data-ttu-id="6fc29-156">[建立資料採礦模型](creating-a-data-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="6fc29-156">[Creating a Data Mining Model](creating-a-data-mining-model.md) </span></span>  
 <span data-ttu-id="6fc29-157">[驗證模型及使用模型進行預測 &#40;適用于 Excel 的資料採礦增益集&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="6fc29-157">[Validating Models and Using Models for Prediction &#40;Data Mining Add-ins for Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md) </span></span>  
 [<span data-ttu-id="6fc29-158">&#40;適用于 Excel 的資料採礦增益集部署和調整採礦模型&#41;</span><span class="sxs-lookup"><span data-stu-id="6fc29-158">Deploying and Scaling Mining Models &#40;Data Mining Add-ins for Excel&#41;</span></span>](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  
