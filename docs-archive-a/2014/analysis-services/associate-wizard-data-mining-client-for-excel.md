---
title: " (適用于 Excel) 的資料採礦用戶端相關聯的 Wizard |Microsoft Docs"
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- nested tables, in association models
- association [data mining]
ms.assetid: 4db6462f-93c7-443f-8ff7-39474dc7029e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 73ce4bbedb710de1ded149a12f6f9b83f0b92a11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593179"
---
# <a name="associate-wizard-data-mining-client-for-excel"></a><span data-ttu-id="b14cb-102">關聯精靈 (適用於 Excel 的資料採礦用戶端)</span><span class="sxs-lookup"><span data-stu-id="b14cb-102">Associate Wizard (Data Mining Client for Excel)</span></span>
  <span data-ttu-id="b14cb-103">![資料採礦功能區中的關聯精靈](media/dmc-associate.gif "資料採礦功能區中的關聯精靈")</span><span class="sxs-lookup"><span data-stu-id="b14cb-103">![Associate wizard in Data Mining ribbon](media/dmc-associate.gif "Associate wizard in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="b14cb-104">關聯精靈可協助您使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 關聯規則演算法建立資料採礦模型。</span><span class="sxs-lookup"><span data-stu-id="b14cb-104">The Associate wizard helps you create a data mining model using the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association Rules algorithm.</span></span> <span data-ttu-id="b14cb-105">這類的採礦模型特別適合用來建立*建議系統*。</span><span class="sxs-lookup"><span data-stu-id="b14cb-105">Such mining models are particularly useful for creating *recommendation systems*.</span></span>  
  
 <span data-ttu-id="b14cb-106">其運作方式為：[!INCLUDE[msCoName](../includes/msconame-md.md)] 關聯規則演算法會掃描由交易或事件組成的資料集，並尋找經常一起出現的組合。</span><span class="sxs-lookup"><span data-stu-id="b14cb-106">How it works is that the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association Rules algorithm scans a dataset comprised of transactions or events, and finds the combinations that frequently appear together.</span></span> <span data-ttu-id="b14cb-107">可能有數千種組合，不過您可以自訂演算法來尋找較多或較少結果，並且僅保留最可能的組合。</span><span class="sxs-lookup"><span data-stu-id="b14cb-107">There can be many thousand combinations, but the algorithm can be customized to find more or fewer, and to retain only the most probable combinations.</span></span>  
  
 <span data-ttu-id="b14cb-108">您可以對許多問題套用關聯分析。</span><span class="sxs-lookup"><span data-stu-id="b14cb-108">You can apply association analysis to many problems.</span></span> <span data-ttu-id="b14cb-109">這個方法最常應用在購物籃分析，用於找出經常一起購買的個別產品。</span><span class="sxs-lookup"><span data-stu-id="b14cb-109">The most popular application of this method is market basket analysis, which finds individual products that are often purchased together.</span></span> <span data-ttu-id="b14cb-110">您接著可以使用這項資訊，根據客戶已經購買的項目向客戶建議其他產品。</span><span class="sxs-lookup"><span data-stu-id="b14cb-110">You can then use that information to recommend products to customers based on items they have already bought.</span></span>  
  
## <a name="using-the-associate-wizard"></a><span data-ttu-id="b14cb-111">使用關聯精靈</span><span class="sxs-lookup"><span data-stu-id="b14cb-111">Using the Associate Wizard</span></span>  
  
1.  <span data-ttu-id="b14cb-112">在 [**資料採礦**] 功能區中，按一下 [**關聯**]。</span><span class="sxs-lookup"><span data-stu-id="b14cb-112">In the **Data Mining** ribbon, click **Associate**.</span></span>  
  
2.  <span data-ttu-id="b14cb-113">在 [**選取來源資料**] 頁面上，選擇 Excel 資料表或資料範圍，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="b14cb-113">On the **Select Source Data** page, choose an Excel table or data range, and click **Next**.</span></span>  
  
     <span data-ttu-id="b14cb-114">[關聯] 索引標籤中的範例資料活頁簿包含交易資料通常如何排列的範例；例如，每筆交易有多項產品或每個客戶有多筆購買記錄需要分析。</span><span class="sxs-lookup"><span data-stu-id="b14cb-114">The sample data workbook contains an example, in the Associate tab, of how transaction data is typically arranged if, for example, you have multiple products in each transaction or multiple purchasing records per customer that you want to analyze.</span></span>  
  
     <span data-ttu-id="b14cb-115">如果您想要使用 [關聯] wizard 來建立關聯模型，您必須先將資料新增至 Excel，然後將資料壓*平*合併。</span><span class="sxs-lookup"><span data-stu-id="b14cb-115">If you want to use external data to build an association model using the Associate wizard, you must add the data to Excel first, and *flatten* the data.</span></span> <span data-ttu-id="b14cb-116">如需準備關聯模型化資料的詳細資訊，請參閱 SQL Server 線上叢書中的[&#40;Analysis Services 資料採礦&#41;的嵌套資料表](data-mining/nested-tables-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="b14cb-116">For more information about preparing data for association modeling, see [Nested Tables &#40;Analysis Services - Data Mining&#41;](data-mining/nested-tables-analysis-services-data-mining.md), in SQL Server Books Online.</span></span>  
  
3.  <span data-ttu-id="b14cb-117">在 [**關聯**] 頁面上，選擇用來識別交易的資料行。</span><span class="sxs-lookup"><span data-stu-id="b14cb-117">On the **Association** page, choose the column that identifies the transaction.</span></span>  
  
     <span data-ttu-id="b14cb-118">若為購物籃模型，此識別碼表示您要建立模型的單位。</span><span class="sxs-lookup"><span data-stu-id="b14cb-118">For market basket models, this identifier represents the unit you want to model.</span></span> <span data-ttu-id="b14cb-119">您是否要分析個別客戶在一段時間內購買的項目，或者您要分析涉及多個客戶的許多交易？</span><span class="sxs-lookup"><span data-stu-id="b14cb-119">Do you want to analyze items that individual customers have purchased over time, or do you want to analyze many transactions involving multiple customers?</span></span> <span data-ttu-id="b14cb-120">在第一個案例中，您會選擇客戶識別碼；在第二個案例中，您會選擇採購單或其他交易識別碼。</span><span class="sxs-lookup"><span data-stu-id="b14cb-120">In the first case, you would choose the customer ID; in the latter you would choose the purchase order or other transaction ID.</span></span>  
  
4.  <span data-ttu-id="b14cb-121">針對 [**專案**]，選取包含您需要尋找關聯之專案的資料行。</span><span class="sxs-lookup"><span data-stu-id="b14cb-121">For **Item**, select the column that contains the things among which you need to find associations.</span></span>  
  
     <span data-ttu-id="b14cb-122">例如，在購物籃模型中，您可以選擇產品欄位，以分析哪些產品經常一起購買。</span><span class="sxs-lookup"><span data-stu-id="b14cb-122">For example, in a market basket model, you would choose a products field, to analyze which products are often purchased together.</span></span> <span data-ttu-id="b14cb-123">如果有太多個別產品，而無法有效地相互關聯，您可以選擇產品類別目錄或子類別目錄欄位。</span><span class="sxs-lookup"><span data-stu-id="b14cb-123">If there are too many individual products to correlate them effectively, you might choose a product category or subcategory field.</span></span>  
  
5.  <span data-ttu-id="b14cb-124">在 [**閾值**] 中，您可以設定控制或影響模型輸出的值：</span><span class="sxs-lookup"><span data-stu-id="b14cb-124">In **Thresholds**, you can set values that control or affect the output of the model:</span></span>  
  
    -   <span data-ttu-id="b14cb-125">**最低支援。**</span><span class="sxs-lookup"><span data-stu-id="b14cb-125">**Minimum support.**</span></span> <span data-ttu-id="b14cb-126">指定項目群組必須被視為重要的次數。</span><span class="sxs-lookup"><span data-stu-id="b14cb-126">Specifies how many times a group of items must appear to be considered important.</span></span> <span data-ttu-id="b14cb-127">演算法會忽略不符合此準則的任何項目組合。</span><span class="sxs-lookup"><span data-stu-id="b14cb-127">The algorithm will ignore any item combinations that do not meet this criterion.</span></span> <span data-ttu-id="b14cb-128">例如，您可能只想查看項目一起出現至少 10 次的項目集。</span><span class="sxs-lookup"><span data-stu-id="b14cb-128">For example, you might want to see only itemsets where the items appeared together at least 10 times overall.</span></span>  
  
    -   <span data-ttu-id="b14cb-129">**最小規則**機率。</span><span class="sxs-lookup"><span data-stu-id="b14cb-129">**Minimum rule probability**.</span></span> <span data-ttu-id="b14cb-130">指定儲存規則所需的最小機率值。</span><span class="sxs-lookup"><span data-stu-id="b14cb-130">Specifies the minimum probability value required for a rule to be saved.</span></span> <span data-ttu-id="b14cb-131">系統會分析整個資料集以尋找所有組合，然後計算機率。</span><span class="sxs-lookup"><span data-stu-id="b14cb-131">The entire data set is analyzed to find all combinations, and then probability is calculated.</span></span> <span data-ttu-id="b14cb-132">如果臨界值太低，則精靈可能會讓相互關聯性鬆散的項目產生關聯。</span><span class="sxs-lookup"><span data-stu-id="b14cb-132">If the threshold is low, the wizard may associate items that are only loosely correlated.</span></span> <span data-ttu-id="b14cb-133">如果臨界值太高，則某些關聯可能會省略，因為這些關聯沒有足夠的支援資料。</span><span class="sxs-lookup"><span data-stu-id="b14cb-133">If the threshold is too high, some associations may be omitted because they do not have enough supporting data.</span></span>  
  
     <span data-ttu-id="b14cb-134">一般而言，變更這些值會產生下列結果：</span><span class="sxs-lookup"><span data-stu-id="b14cb-134">In general, changing these values has the following effects:</span></span>  
  
    -   <span data-ttu-id="b14cb-135">當您降低支援的值時，您會增加找到的組合數目。</span><span class="sxs-lookup"><span data-stu-id="b14cb-135">As you lower the value for support, you increase the number of combinations that are found.</span></span>  
  
    -   <span data-ttu-id="b14cb-136">當您減少最大支援時，您會篩選出太常發生，但是沒有什麼意義的項目。</span><span class="sxs-lookup"><span data-stu-id="b14cb-136">As you decrease the maximum support, you filter out items that occur so often that they have little meaning.</span></span>  
  
    -   <span data-ttu-id="b14cb-137">當您降低規則的機率時，您會降低組合必須達到的門檻需求，才能在總資料集的內容中視為是重要的。</span><span class="sxs-lookup"><span data-stu-id="b14cb-137">As you lower the probability of a rule, you lower the requirements that a combination must meet to be considered important in the context of the total data set.</span></span>  
  
     <span data-ttu-id="b14cb-138">**秘訣：** 使用不同的支援和機率組合來建立多個採礦模型是個不錯的主意。</span><span class="sxs-lookup"><span data-stu-id="b14cb-138">**Tip:** It is a good idea to create multiple mining models using different combinations of support and probability.</span></span> <span data-ttu-id="b14cb-139">若要追蹤您用於每個模型的設定，您可以使用 [**檔模型**] wizard （可在適用于 Excel 的資料採礦用戶端中取得），並使用 [**詳細**報告] 選項。</span><span class="sxs-lookup"><span data-stu-id="b14cb-139">To track which settings you used for each model, you can use the **Document Model** wizard, available in the Data Mining Client for Excel, and use the **Detailed** report option.</span></span> <span data-ttu-id="b14cb-140">如需詳細資訊，請參閱[記載 &#40;適用于 Excel 的資料採礦增益集&#41;的採礦模型](documenting-mining-models-data-mining-add-ins-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="b14cb-140">For more information, see [Documenting Mining Models &#40;Data Mining Add-ins for Excel&#41;](documenting-mining-models-data-mining-add-ins-for-excel.md).</span></span>  
  
6.  <span data-ttu-id="b14cb-141">（選擇性）按一下 [**參數**] 以變更演算法參數，並自訂採礦模型的行為。</span><span class="sxs-lookup"><span data-stu-id="b14cb-141">Optionally, click **Parameters** to change the algorithm parameters and customize the behavior of the mining model.</span></span>  
  
     <span data-ttu-id="b14cb-142">演算法參數對話方塊包含您在精靈中設定的所有參數，以及幾個較少使用的參數，例如 MAXIMUM_SUPPORT。</span><span class="sxs-lookup"><span data-stu-id="b14cb-142">The Algorithm Parameters dialog box includes all of the parameters you set in the wizard, plus a few that are less commonly used, such as MAXIMUM_SUPPORT.</span></span> <span data-ttu-id="b14cb-143">如需如何使用這些參數的相關資訊，請參閱[Microsoft 關聯分析演算法技術參考](data-mining/microsoft-association-algorithm-technical-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="b14cb-143">For information about how to use these parameters, see [Microsoft Association Algorithm Technical Reference](data-mining/microsoft-association-algorithm-technical-reference.md).</span></span>  
  
7.  <span data-ttu-id="b14cb-144">在 [**完成]** 頁面上，輸入資料集和模型的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="b14cb-144">On the **Finish** page, type a unique name for the data set and the model.</span></span>  
  
8.  <span data-ttu-id="b14cb-145">在 [**選項**] 中，您可以定義在模型完成後要如何使用它：</span><span class="sxs-lookup"><span data-stu-id="b14cb-145">In **Options**, you define how you want to work with the model after it is completed:</span></span>  
  
    -   <span data-ttu-id="b14cb-146">**流覽**。</span><span class="sxs-lookup"><span data-stu-id="b14cb-146">**Browse**.</span></span>  <span data-ttu-id="b14cb-147">當模型就緒時，精靈會開啟視窗，以顯示規則、項目集及描述關聯的相依性網路圖表。</span><span class="sxs-lookup"><span data-stu-id="b14cb-147">When the model is ready, the wizard opens a window that displays the rules, the itemsets, and a dependency network graph that depicts associations.</span></span>  
  
         <span data-ttu-id="b14cb-148">如需如何在關聯模型檢視器中解讀資料的詳細資訊，請參閱[流覽關聯規則模型](browsing-an-association-rules-model.md)。</span><span class="sxs-lookup"><span data-stu-id="b14cb-148">For more information about how to interpret the data in the association model viewer, see [Browsing an Association Rules Model](browsing-an-association-rules-model.md).</span></span>  
  
    -   <span data-ttu-id="b14cb-149">**啟用 [鑽取**]。</span><span class="sxs-lookup"><span data-stu-id="b14cb-149">**Enable drillthrough**.</span></span> <span data-ttu-id="b14cb-150">選取此選項可透過模型取得基礎資料的存取權。</span><span class="sxs-lookup"><span data-stu-id="b14cb-150">Select this option to gain access to the underlying data, via the model.</span></span>  
  
         <span data-ttu-id="b14cb-151">例如，如果您想按一下特定項目集以查看來源資料，鑽研是很有用的方式。</span><span class="sxs-lookup"><span data-stu-id="b14cb-151">Drillthrough is useful, for example, if you want to click on a particular itemset and see the source data.</span></span>  
  
    -   <span data-ttu-id="b14cb-152">**使用暫時性模型**。</span><span class="sxs-lookup"><span data-stu-id="b14cb-152">**Use temporary model**.</span></span> <span data-ttu-id="b14cb-153">如果您不想要在伺服器上儲存模型，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="b14cb-153">Select this option if you don't want the model saved on the server.</span></span> <span data-ttu-id="b14cb-154">當您關閉 Excel 時，即會刪除暫時性模型。</span><span class="sxs-lookup"><span data-stu-id="b14cb-154">Temporary models are deleted when you close Excel.</span></span>  
  
9. <span data-ttu-id="b14cb-155">精靈會分析所有可能的組合，並且建立包含項目集和規則的報表。</span><span class="sxs-lookup"><span data-stu-id="b14cb-155">The wizard analyzes all possible combinations and creates a report that contains the itemsets and rules.</span></span>  
  
## <a name="more-about-association-models"></a><span data-ttu-id="b14cb-156">進一步了解關聯模型</span><span class="sxs-lookup"><span data-stu-id="b14cb-156">More About Association Models</span></span>  
 <span data-ttu-id="b14cb-157">[!INCLUDE[msCoName](../includes/msconame-md.md)] 關聯規則演算法會檢查定型資料來尋找一起出現在交易中的項目。</span><span class="sxs-lookup"><span data-stu-id="b14cb-157">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Association Rules algorithm examines the training data to find items that appear together in a transaction.</span></span> <span data-ttu-id="b14cb-158">每個專案群組都會構成*一個專案*集。</span><span class="sxs-lookup"><span data-stu-id="b14cb-158">Each group of items constitutes an *itemset*.</span></span> <span data-ttu-id="b14cb-159">接著，演算法會計算每個項目集出現的次數，以及每個項目集在所有交易中的相對重要性。</span><span class="sxs-lookup"><span data-stu-id="b14cb-159">The algorithm then counts the number of times each itemset appears and calculates the relative importance of each itemset across all transactions.</span></span>  
  
 <span data-ttu-id="b14cb-160">演算法會使用關於項目集的這個資訊產生可用於預測關聯或進行建議的規則。</span><span class="sxs-lookup"><span data-stu-id="b14cb-160">The algorithm uses this information about itemsets to generate rules that can be used to predict associations or make recommendations.</span></span> <span data-ttu-id="b14cb-161">例如，規則可以如下：「如果使用者購買作者 1 和作者 2 的書，則這位使用者也可能會購買作者 3 的書」。</span><span class="sxs-lookup"><span data-stu-id="b14cb-161">For example, a rule could be "if the user purchased a book by Author 1 and a book by Author 2, then it is likely that the user will also purchase a book by Author 3".</span></span> <span data-ttu-id="b14cb-162">系統會根據關聯的強度來為每個建議指派機率。</span><span class="sxs-lookup"><span data-stu-id="b14cb-162">Each recommendation is assigned a probability, based on the strength of the associations.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="b14cb-163">需求</span><span class="sxs-lookup"><span data-stu-id="b14cb-163">Requirements</span></span>  
 <span data-ttu-id="b14cb-164">若要使用關聯精靈，您必須連接到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="b14cb-164">To use the Associate wizard, you must be connected to a [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="b14cb-165">您的來源資料必須組織成交易資料表，</span><span class="sxs-lookup"><span data-stu-id="b14cb-165">Your source data must be organized as a transaction table.</span></span> <span data-ttu-id="b14cb-166">來源資料必須包含一個含有交易識別碼的資料行，</span><span class="sxs-lookup"><span data-stu-id="b14cb-166">The source data must contain one column that contains the transaction identifier.</span></span> <span data-ttu-id="b14cb-167">此資料行會識別每一組項目。</span><span class="sxs-lookup"><span data-stu-id="b14cb-167">This column identifies each group of items.</span></span> <span data-ttu-id="b14cb-168">該交易資料行必須與第二個資料行 (也就是項目識別碼) 具有一對多的關聯性，第二個資料行會儲存群組中個別項目的名稱或識別碼。</span><span class="sxs-lookup"><span data-stu-id="b14cb-168">That transaction column must be in a one-to-many relationship with a second column, the item ID, which stores names or ID numbers for the individual items in the group.</span></span>  
  
 <span data-ttu-id="b14cb-169">概念上而言，如果回想起購物車的範例，這可能是最容易了解的部分。</span><span class="sxs-lookup"><span data-stu-id="b14cb-169">Conceptually, this might be easiest to understand by recalling the shopping cart example.</span></span> <span data-ttu-id="b14cb-170">如果為購物車指派識別碼，此購物車識別碼會當做交易的識別碼。</span><span class="sxs-lookup"><span data-stu-id="b14cb-170">If the shopping cart is assigned an ID, the shopping cart ID serves as the identifier for the transaction.</span></span> <span data-ttu-id="b14cb-171">購物車中的每一個項目 (如馬鈴薯或牛奶) 都是該筆交易的成員。</span><span class="sxs-lookup"><span data-stu-id="b14cb-171">Each item in the shopping cart, such as potatoes or milk, is a member of that transaction.</span></span> <span data-ttu-id="b14cb-172">關聯分析演算法可跨交易追蹤項目，例如，用來判斷馬鈴薯和牛奶出現在任何單筆交易中的次數。</span><span class="sxs-lookup"><span data-stu-id="b14cb-172">The Associate algorithm can track items across transactions: for example, to determine how many times potatoes and milk appear within any single transaction.</span></span>  
  
 <span data-ttu-id="b14cb-173">您的來源資料必須依據交易識別碼資料行排序。</span><span class="sxs-lookup"><span data-stu-id="b14cb-173">Your source data must be sorted by the transaction identifier column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b14cb-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b14cb-174">See Also</span></span>  
 <span data-ttu-id="b14cb-175">[建立資料採礦模型](creating-a-data-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="b14cb-175">[Creating a Data Mining Model](creating-a-data-mining-model.md) </span></span>  
 <span data-ttu-id="b14cb-176">[流覽關聯規則模型](browsing-an-association-rules-model.md) </span><span class="sxs-lookup"><span data-stu-id="b14cb-176">[Browsing an Association Rules Model](browsing-an-association-rules-model.md) </span></span>  
 <span data-ttu-id="b14cb-177">[適用于 Excel&#41;的購物籃分析 &#40;資料表 AnalysisTools](shopping-basket-analysis-table-analysistools-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="b14cb-177">[Shopping Basket Analysis &#40;Table AnalysisTools for Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md) </span></span>  
 [<span data-ttu-id="b14cb-178">相依性網狀圖表逐步解說 &#40;資料採礦增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="b14cb-178">Dependency Network Diagram Walkthrough &#40;Data Mining Add-ins&#41;</span></span>](dependency-network-diagram-walkthrough-data-mining-add-ins.md)  
  
  
