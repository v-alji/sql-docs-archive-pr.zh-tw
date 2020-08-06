---
title: 資料採礦準備的檢查清單 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0e056c95-ba06-413e-8dc1-4d411a447c3b
author: minewiskan
ms.author: owend
ms.openlocfilehash: e37b1adb6aebe5d5f8fd23f5289f52425f752a6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593707"
---
# <a name="checklist-of-preparation-for-data-mining"></a><span data-ttu-id="c4019-102">資料採礦準備清單</span><span class="sxs-lookup"><span data-stu-id="c4019-102">Checklist of Preparation for Data Mining</span></span>
  <span data-ttu-id="c4019-103">雖然資料採礦增益集讓模型的建立和試驗工作變得相當簡單有趣，不過當您需要取得可重複、可付諸行動的結果時，就必須預留足夠的時間來擬定基本業務需求，以及取得和準備資料。</span><span class="sxs-lookup"><span data-stu-id="c4019-103">Although the Data Mining Add-ins make it fairly easy and fun to create and experiment with models, when you need to get repeatable, actionable results, you must allow adequate time for formulating basic business requirements, and for obtaining and preparing data.</span></span> <span data-ttu-id="c4019-104">本節提供一份檢查清單以協助您規劃調查，並描述常見的問題。</span><span class="sxs-lookup"><span data-stu-id="c4019-104">This section provides a checklist to help you plan your investigation, and describes common problems.</span></span>  
  
## <a name="checklist-of-data-preparation"></a><span data-ttu-id="c4019-105">資料準備清單</span><span class="sxs-lookup"><span data-stu-id="c4019-105">Checklist of Data Preparation</span></span>  
 <span data-ttu-id="c4019-106">**我已經識別清楚定義的輸出。**</span><span class="sxs-lookup"><span data-stu-id="c4019-106">**I have identified a clearly defined output.**</span></span>  
 <span data-ttu-id="c4019-107">要有如何使用結果的計畫。</span><span class="sxs-lookup"><span data-stu-id="c4019-107">Have a plan for how you will use the results.</span></span> <span data-ttu-id="c4019-108">不同類型的模型會有不同的輸出。</span><span class="sxs-lookup"><span data-stu-id="c4019-108">Different types of models have different outputs.</span></span> <span data-ttu-id="c4019-109">時間序列模型會產生未來序列的值，這些值容易了解及加以採取動作。</span><span class="sxs-lookup"><span data-stu-id="c4019-109">A time series model generates values for a series in the future, which are easily understood and acted on.</span></span> <span data-ttu-id="c4019-110">其他模型會產生複雜的資料集，必須由主題專家分析以獲得大部分的值。</span><span class="sxs-lookup"><span data-stu-id="c4019-110">Other models generate complex sets that must be analyzed by subject matter experts to yield the most value.</span></span>  
  
-   <span data-ttu-id="c4019-111">您想要什麼樣的輸出？</span><span class="sxs-lookup"><span data-stu-id="c4019-111">What output do you want?</span></span>  
  
-   <span data-ttu-id="c4019-112">您可以將輸出定義為單一資料行或值，或其他可付諸行動的結果嗎？</span><span class="sxs-lookup"><span data-stu-id="c4019-112">Can you define the output as a single column or value, or other actionable result?</span></span>  
  
-   <span data-ttu-id="c4019-113">知道模型是否為有用的準則是什麼？</span><span class="sxs-lookup"><span data-stu-id="c4019-113">What are your criteria for knowing that the model was useful?</span></span>  
  
-   <span data-ttu-id="c4019-114">您將如何使用及解譯這些結果？</span><span class="sxs-lookup"><span data-stu-id="c4019-114">How will you use and interpret those results?</span></span>  
  
-   <span data-ttu-id="c4019-115">您能否將新的輸入資料對應至預期的結果？</span><span class="sxs-lookup"><span data-stu-id="c4019-115">Can you map new input data to the expected results?</span></span>  
  
 <span data-ttu-id="c4019-116">**我了解輸入資料的意義、資料類型和分佈。**</span><span class="sxs-lookup"><span data-stu-id="c4019-116">**I know the meaning, data types, and distribution of the input data.**</span></span>  
 <span data-ttu-id="c4019-117">花一些時間來探索及了解來源資料。</span><span class="sxs-lookup"><span data-stu-id="c4019-117">Take some time to explore and understand your source data.</span></span> <span data-ttu-id="c4019-118">檢閱模型的人員必須了解使用的輸入資料種類，而且知道如何解譯資料類型和變化性，以及平衡和品質。</span><span class="sxs-lookup"><span data-stu-id="c4019-118">It is important that people who review the model understand what kind of input data was used and know how to interpret the data types and the variability, as well as the balance and the quality.</span></span>  
  
-   <span data-ttu-id="c4019-119">您有多少資料？</span><span class="sxs-lookup"><span data-stu-id="c4019-119">How much data do you have?</span></span> <span data-ttu-id="c4019-120">是否有足夠的資料可用於模型？</span><span class="sxs-lookup"><span data-stu-id="c4019-120">Is there sufficient data for modeling?</span></span>  
  
     <span data-ttu-id="c4019-121">它不需要太大的容量，而且也比較好。</span><span class="sxs-lookup"><span data-stu-id="c4019-121">It need not be a huge amount - smaller and balanced can be better.</span></span>  
  
-   <span data-ttu-id="c4019-122">資料是來自多個來源或單一來源？</span><span class="sxs-lookup"><span data-stu-id="c4019-122">Is the data from multiple sources, or a single source?</span></span>  
  
-   <span data-ttu-id="c4019-123">資料是否已處理及清除？</span><span class="sxs-lookup"><span data-stu-id="c4019-123">Is the data already processed and clean?</span></span> <span data-ttu-id="c4019-124">是否有其他輸入資料可用？</span><span class="sxs-lookup"><span data-stu-id="c4019-124">Is more input data available?</span></span>  
  
-   <span data-ttu-id="c4019-125">在收到資料之前，您是否知道其操作方式-資料可能被截斷、摘要或轉換？</span><span class="sxs-lookup"><span data-stu-id="c4019-125">Do you know how it was manipulated before you received it - how data might have been truncated, summarized, or converted?</span></span>  
  
-   <span data-ttu-id="c4019-126">輸入資料是否有可用於定型的一些範例結果？</span><span class="sxs-lookup"><span data-stu-id="c4019-126">Does the input data have some example results that can be used for training?</span></span>  
  
 <span data-ttu-id="c4019-127">**我了解目前擁有的資料完整性層級，以及所需要的層級。**</span><span class="sxs-lookup"><span data-stu-id="c4019-127">**I understand the level of data integrity we have and the level we need.**</span></span>  
 <span data-ttu-id="c4019-128">不正確的資料可能會影響模型的品質，或是根本就無法建立模型。</span><span class="sxs-lookup"><span data-stu-id="c4019-128">Bad data can affect the quality of the model, or prevent the model from being built at all.</span></span> <span data-ttu-id="c4019-129">您應該充分了解資料的分佈和意義，以及變成這種狀態的原因。</span><span class="sxs-lookup"><span data-stu-id="c4019-129">You should have a good understanding of both the distribution and meaning of the data, and how it came to this state.</span></span> <span data-ttu-id="c4019-130">您必須瞭解是否可能或適當地透過標記、截斷數值資料類型或匯總來簡化資料。</span><span class="sxs-lookup"><span data-stu-id="c4019-130">You'll need to understand if it is possible or appropriate to simplify the data by labeling, truncating numeric data types, or by summarizing.</span></span>  
  
-   <span data-ttu-id="c4019-131">資料標籤：是否清楚且正確？</span><span class="sxs-lookup"><span data-stu-id="c4019-131">Data labels: are they clear and correct?</span></span>  
  
-   <span data-ttu-id="c4019-132">資料類型：是否適當，以及是否已經變更？</span><span class="sxs-lookup"><span data-stu-id="c4019-132">Data types: are they appropriate, and have they been changed?</span></span>  
  
-   <span data-ttu-id="c4019-133">您是否已排序、清除或捨棄錯誤資料？</span><span class="sxs-lookup"><span data-stu-id="c4019-133">Have you sorted, cleaned up, or discarded wrong data?</span></span>  
  
     <span data-ttu-id="c4019-134">您是否已確認沒有重複項目？</span><span class="sxs-lookup"><span data-stu-id="c4019-134">Have you verified there are no duplicates?</span></span>  
  
-   <span data-ttu-id="c4019-135">您要如何處理遺漏值？</span><span class="sxs-lookup"><span data-stu-id="c4019-135">How will you handle missing values?</span></span> <span data-ttu-id="c4019-136">遺漏值是否具有意義？</span><span class="sxs-lookup"><span data-stu-id="c4019-136">Do missing values have a meaning?</span></span>  
  
-   <span data-ttu-id="c4019-137">您是否有檢查來源，看看是否在匯入過程中就已經導入了任何錯誤？</span><span class="sxs-lookup"><span data-stu-id="c4019-137">Have you verified the sources to see if any errors might have been introduced in the import process?</span></span>  
  
     <span data-ttu-id="c4019-138">輸入資料儲存在哪裡？</span><span class="sxs-lookup"><span data-stu-id="c4019-138">Where is the input stored?</span></span> <span data-ttu-id="c4019-139">它會保持可用狀態多久？</span><span class="sxs-lookup"><span data-stu-id="c4019-139">How long does it stay available?</span></span>  
  
     <span data-ttu-id="c4019-140">是否有資料字典？</span><span class="sxs-lookup"><span data-stu-id="c4019-140">Is there a data dictionary?</span></span> <span data-ttu-id="c4019-141">您可以建立資料字典嗎？</span><span class="sxs-lookup"><span data-stu-id="c4019-141">Can you create one?</span></span>  
  
-   <span data-ttu-id="c4019-142">如果您結合了資料集，是否有檢查其中有沒有代表相同資料的多個資料行？</span><span class="sxs-lookup"><span data-stu-id="c4019-142">If you combined data sets, did you check for multiple columns representing the same data?</span></span>  
  
 <span data-ttu-id="c4019-143">**我知道來源資料的儲存位置、來自何處，以及它的處理方式。如有需要，可以輕鬆地重複處理常式。**</span><span class="sxs-lookup"><span data-stu-id="c4019-143">**I know where source data is stored, where it came from, and how it is processed. The process can be easily repeated if needed.**</span></span>  
 <span data-ttu-id="c4019-144">一次性資料集適用于實驗，但如果您想要將模型移至生產環境，您會想要事先考慮清理程式如何套用至運算元據。</span><span class="sxs-lookup"><span data-stu-id="c4019-144">One-off data sets are fine for experiments, but if you ever want to move the model into production, you'll want to think in advance about how the cleaning process can be applied to operational data.</span></span> <span data-ttu-id="c4019-145">此外，如果您有運算元據，您需要知道它在您得到它之前的改變方式-您必須知道它是如何舍入或摘要的。</span><span class="sxs-lookup"><span data-stu-id="c4019-145">Also, if you have operational data, you need to know how it might have been altered before you got it-you'll need to know how it was rounded, or summarized, certainly.</span></span>  
  
-   <span data-ttu-id="c4019-146">您是否需要能夠重複進行實驗？</span><span class="sxs-lookup"><span data-stu-id="c4019-146">Do you want to be able to repeat the experiment?</span></span>  
  
-   <span data-ttu-id="c4019-147">您會使用哪些工具來準備支援資料分析的資料格式？</span><span class="sxs-lookup"><span data-stu-id="c4019-147">What tools will you use to prepare data in a format that supports data analysis?</span></span> <span data-ttu-id="c4019-148">此程序能否自動化，或者您是否需要其他人在 Excel 中檢閱並清理？</span><span class="sxs-lookup"><span data-stu-id="c4019-148">Can it be automated or do you need someone to review and clean up in Excel?</span></span>  
  
-   <span data-ttu-id="c4019-149">如果您是從另一個系統取得資料，是否能夠擷取及追蹤所套用的篩選？</span><span class="sxs-lookup"><span data-stu-id="c4019-149">If you are sourcing data from another system, will you be able to capture and track filters that were applied?</span></span>  
  
-   <span data-ttu-id="c4019-150">您的資料處理架構是否也能套用機器學習演算法、執行測試，以及將結果視覺效果？</span><span class="sxs-lookup"><span data-stu-id="c4019-150">Can your data processing framework also apply machine learning algorithms, perform tests, and visualize results?</span></span>  
  
 <span data-ttu-id="c4019-151">**我們已經一致同意所需的預測資料粒度，而且我們的資料已經修改成輸出這些單位。**</span><span class="sxs-lookup"><span data-stu-id="c4019-151">**We have agreed on the desired granularity of predictions and our data has been modified to output those units.**</span></span>  
 <span data-ttu-id="c4019-152">在準備資料之前決定您要的結果資料粒度。例如，您是要每日的銷售預測，或是要每一季的銷售預測？</span><span class="sxs-lookup"><span data-stu-id="c4019-152">Decide on the granularity of the results you want before preparing data, For example, do you want sales predictions by the day, or for each quarter?</span></span> <span data-ttu-id="c4019-153">您可能會考慮針對相同資料設定不同的資料結構，以應付不同的摘要層級。</span><span class="sxs-lookup"><span data-stu-id="c4019-153">You might consider setting up different data structures for the same data, to handle different levels of summary.</span></span>  
  
-   <span data-ttu-id="c4019-154">目前的度量單位或時間單位是什麼？</span><span class="sxs-lookup"><span data-stu-id="c4019-154">What is the current unit of measure or unit of time?</span></span>  
  
     <span data-ttu-id="c4019-155">您要在結果中使用什麼單位？</span><span class="sxs-lookup"><span data-stu-id="c4019-155">What unit do you want to use in the results?</span></span>  
  
-   <span data-ttu-id="c4019-156">是否可以為所有輸入資料定義基本單位 (例如日/小時/分鐘/指令呼叫) ？</span><span class="sxs-lookup"><span data-stu-id="c4019-156">Is it possible to define a basic unit (e.g. day/ hour / min / instruction call) for all input data?</span></span>  
  
     <span data-ttu-id="c4019-157">您是否要縮合到較高的單位？</span><span class="sxs-lookup"><span data-stu-id="c4019-157">Do you want to rollup to higher units?</span></span>  
  
-   <span data-ttu-id="c4019-158">類別目錄的標籤是否一致？</span><span class="sxs-lookup"><span data-stu-id="c4019-158">Are categories labeled consistently?</span></span> <span data-ttu-id="c4019-159">加入或移除類別目錄是否很簡單？</span><span class="sxs-lookup"><span data-stu-id="c4019-159">Is it easy to add or remove categories?</span></span>  
  
 <span data-ttu-id="c4019-160">**我們的試驗設計不但可重複，而且可重現。**</span><span class="sxs-lookup"><span data-stu-id="c4019-160">**Our experimental design is repeatable and reproducible.**</span></span>  
 <span data-ttu-id="c4019-161">考量用於分析及驗證結果的策略，並擬定擷取資料快照集的計畫，以確保您可以回溯對資料所做的效果。</span><span class="sxs-lookup"><span data-stu-id="c4019-161">Consider strategies for analyzing and validating your results and plan to capture a data snapshot, to make sure you can trace back effects to data.</span></span> <span data-ttu-id="c4019-162">如果使用了隨機種子，結果可能會稍有不同。</span><span class="sxs-lookup"><span data-stu-id="c4019-162">If a random seed is used, the results can differ subtly.</span></span> <span data-ttu-id="c4019-163">這樣可能會變得難以比較和驗證模型。</span><span class="sxs-lookup"><span data-stu-id="c4019-163">This can make it difficult to compare and validate models.</span></span>  
  
-   <span data-ttu-id="c4019-164">如果您對資料做了很多自訂變更，那麼下次您要建立模型時會發生什麼事呢？</span><span class="sxs-lookup"><span data-stu-id="c4019-164">If you make a lot of custom changes to the data, what happens the next time you want to build the model?</span></span>  
  
-   <span data-ttu-id="c4019-165">是否已經定義了您應該用來處理輸入資料並獲得所要輸出的手動程序或已核准的處理程序？</span><span class="sxs-lookup"><span data-stu-id="c4019-165">Has a manual procedure or approved process already been defined that you should use to process input and get the desired outputs?</span></span>  
  
-   <span data-ttu-id="c4019-166">您決定要為模型使用種子嗎？</span><span class="sxs-lookup"><span data-stu-id="c4019-166">Have you decided to use a seed for the model?</span></span>  
  
 <span data-ttu-id="c4019-167">**我們擁有定義域知識來驗證結果，或者能夠諮詢可提供建議的主題專家。**</span><span class="sxs-lookup"><span data-stu-id="c4019-167">**We have the domain knowledge to validate the results, or have access to subject matter experts who can advise.**</span></span>  
 <span data-ttu-id="c4019-168">花一些時間來驗證變數、模型和結果。</span><span class="sxs-lookup"><span data-stu-id="c4019-168">Take time to validate the variables, the model, and the results.</span></span> <span data-ttu-id="c4019-169">取得專家的協助來評估互動和結果。</span><span class="sxs-lookup"><span data-stu-id="c4019-169">Get the help of experts to assess interactions and results.</span></span> <span data-ttu-id="c4019-170">不過，請不要讓假設 overrule 辨識項。</span><span class="sxs-lookup"><span data-stu-id="c4019-170">However, don't let assumptions overrule evidence.</span></span> <span data-ttu-id="c4019-171">對新的和非預期的發現保持開放的態度。</span><span class="sxs-lookup"><span data-stu-id="c4019-171">Be open to new and unexpected findings.</span></span>  
  
-   <span data-ttu-id="c4019-172">是否有可用的定義域知識可協助篩選資料和減少輸入干擾？</span><span class="sxs-lookup"><span data-stu-id="c4019-172">Is domain knowledge available to help in filtering data and reducing input noise?</span></span>  
  
-   <span data-ttu-id="c4019-173">定義域專家是否能夠協助了解及解譯結果，並提供改善建議？</span><span class="sxs-lookup"><span data-stu-id="c4019-173">Can domain experts help understand interpret the results and suggest improvements?</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4019-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4019-174">See Also</span></span>  
 [<span data-ttu-id="c4019-175">選擇要進行資料採礦的資料</span><span class="sxs-lookup"><span data-stu-id="c4019-175">Choosing Data for Data Mining</span></span>](choosing-data-for-data-mining.md)  
  
  
