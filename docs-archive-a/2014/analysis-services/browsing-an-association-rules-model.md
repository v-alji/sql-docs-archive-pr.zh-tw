---
title: 流覽關聯規則模型 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- mining model, association
- mining models, viewing
- association [data mining]
ms.assetid: faffe208-7a64-4ec6-825f-ecbaa79caff7
author: minewiskan
ms.author: owend
ms.openlocfilehash: de5adbca264fff81b44424d865a2c8201a6fdfc3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593099"
---
# <a name="browsing-an-association-rules-model"></a><span data-ttu-id="7440a-102">瀏覽關聯規則模型</span><span class="sxs-lookup"><span data-stu-id="7440a-102">Browsing an Association Rules Model</span></span>
  <span data-ttu-id="7440a-103">當您使用 **[流覽]** 開啟關聯模型時，該模型會顯示在互動式檢視器中，類似于中的關聯規則檢視器 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7440a-103">When you open an association model using **Browse**, the model is displayed in an interactive viewer, similar to the Association Rules Viewer in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  <span data-ttu-id="7440a-104">此檢視器可讓您快速查看相互關聯的項目，並顯示可用於預測或提出建議的規則。</span><span class="sxs-lookup"><span data-stu-id="7440a-104">The viewer lets you see at a glance which items were correlated with each other, and displays rules that you can use for prediction or making recommendations.</span></span>  
  
##  <a name="explore-the-model"></a><a name="BKMK_ViewerTabs"></a><span data-ttu-id="7440a-105">探索模型</span><span class="sxs-lookup"><span data-stu-id="7440a-105">Explore the Model</span></span>  
 <span data-ttu-id="7440a-106">當您開啟使用關聯規則演算法建立的採礦模型時 [!INCLUDE[msCoName](../includes/msconame-md.md)] ，[**流覽**] 視窗會包含下列視圖，每個都設計成讓您探索模型的不同層面：</span><span class="sxs-lookup"><span data-stu-id="7440a-106">When you open a mining model that was created using the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association Rules algorithm, the **Browse** window includes the following views, each designed to let you explore a different aspect of the model:</span></span>  
  
-   [<span data-ttu-id="7440a-107">項目集</span><span class="sxs-lookup"><span data-stu-id="7440a-107">Itemsets</span></span>](#BKMK_Itemsets)  
  
-   [<span data-ttu-id="7440a-108">規則</span><span class="sxs-lookup"><span data-stu-id="7440a-108">Rules</span></span>](#BKMK_Rules)  
  
-   [<span data-ttu-id="7440a-109">相依性網路</span><span class="sxs-lookup"><span data-stu-id="7440a-109">Dependency Net</span></span>](#BKMK_Dependency)  
  
 <span data-ttu-id="7440a-110">請記下每個索引標籤上的選項 [**顯示完整名稱**]。</span><span class="sxs-lookup"><span data-stu-id="7440a-110">Take note of the option on each tab, **Show long name** .</span></span> <span data-ttu-id="7440a-111">透過選取這個選項，您可以顯示或隱藏項目集的來源資料表，以及縮短或增長規則或項目集的名稱。</span><span class="sxs-lookup"><span data-stu-id="7440a-111">By selecting this option, you can show or hide the table from which the itemset originates, and shorten or lengthen the name of the rule or itemset.</span></span> <span data-ttu-id="7440a-112">當您的案例資料和屬性資料來自不同資料來源時，這個選項特別有用。</span><span class="sxs-lookup"><span data-stu-id="7440a-112">This option is particularly useful when your case data and attribute data are from different data sources.</span></span>  
  
 <span data-ttu-id="7440a-113">若要試驗關聯模型，您可以使用範例資料活頁簿之 [關聯] 索引標籤上的範例資料，然後使用所有預設值建立關聯模型。</span><span class="sxs-lookup"><span data-stu-id="7440a-113">To experiment with an association model, you can use the sample data on the Associate tab of the sample data workbook, and build an association model using all the defaults.</span></span> <span data-ttu-id="7440a-114">您也可以建立購物籃分析模型，並使用 **[流覽]** 來開啟它。</span><span class="sxs-lookup"><span data-stu-id="7440a-114">You can also build a Shopping Basket Analysis model and open that using **Browse**.</span></span>  
  
###  <a name="itemsets"></a><a name="BKMK_Itemsets"></a><span data-ttu-id="7440a-115">專案集</span><span class="sxs-lookup"><span data-stu-id="7440a-115">Itemsets</span></span>  
 <span data-ttu-id="7440a-116">[**專案集**] 索引標籤是開始探索關聯模型的絕佳位置。</span><span class="sxs-lookup"><span data-stu-id="7440a-116">The **Itemsets** tab is a good place to begin exploring an association model.</span></span> <span data-ttu-id="7440a-117">此索引標籤會顯示常被模型湊在一起的項目清單。</span><span class="sxs-lookup"><span data-stu-id="7440a-117">This tab shows a list of the items that the model frequently found together.</span></span>  
  
 <span data-ttu-id="7440a-118">![關聯模型中的項目清單](media/dm13-association-itemsets.gif "關聯模型中的項目清單")</span><span class="sxs-lookup"><span data-stu-id="7440a-118">![List of items in an association model](media/dm13-association-itemsets.gif "List of items in an association model")</span></span>  
  
 <span data-ttu-id="7440a-119">您可以在購物籃模型中找到項目集的最常見範例，在此模型中，項目集表示許多客戶會同時購買的產品配對或組合。</span><span class="sxs-lookup"><span data-stu-id="7440a-119">The most common example of itemsets is in a shopping basket model, where an itemset represents pairs or sets of products that lots of customers purchase at the same time.</span></span> <span data-ttu-id="7440a-120">不過，根據您分組及排序項目的方式，項目集可能包含客戶在一段時間內訂購的影片序列，或傾向在特定位置發生的事件。</span><span class="sxs-lookup"><span data-stu-id="7440a-120">However, depending on how you group and order your items, the itemset might contain a sequence of movies that customers order over a period of time, or events that tend to occur in  a particular location.</span></span>  
  
 <span data-ttu-id="7440a-121">專案*集可以包含*最少一個專案到兩個、三個，或多個設定為模型的專案集大小上限。</span><span class="sxs-lookup"><span data-stu-id="7440a-121">An *itemset* can contain as few as one item to two, three, or however, many is set as the maximum itemset size for the model.</span></span> <span data-ttu-id="7440a-122">針對每個專案集，檢視器會顯示專案集的*支援* *、機率和\*\*大小*。</span><span class="sxs-lookup"><span data-stu-id="7440a-122">For each itemset, the viewer displays the itemset  *support*,  *probability*, and *size*.</span></span> <span data-ttu-id="7440a-123">支援和機率是用來排名項目集的主體統計資料，並且是關聯模型所產生的規則。</span><span class="sxs-lookup"><span data-stu-id="7440a-123">Support and probability are the principal statistics used to rank the itemsets and rules generated by an association model.</span></span> <span data-ttu-id="7440a-124">這些值也可用來計算及描述其重要性。</span><span class="sxs-lookup"><span data-stu-id="7440a-124">These values are also used to calculate and describe their importance.</span></span>  
  
 <span data-ttu-id="7440a-125">**支援**。</span><span class="sxs-lookup"><span data-stu-id="7440a-125">**Support**.</span></span> <span data-ttu-id="7440a-126">支援表示包含此項目的案例數目或輸入資料的資料列數。</span><span class="sxs-lookup"><span data-stu-id="7440a-126">Support means the number of cases or rows of input data that have this item.</span></span> <span data-ttu-id="7440a-127">例如，如果專案集包含在「購物車」中找到的兩個專案，[**支援**] 資料行中的數位會指出在來源資料中出現該專案組合的次數。</span><span class="sxs-lookup"><span data-stu-id="7440a-127">For example, if an itemset contains two items that are found in a shopping cart, the number in the **Support** column indicates how many times that combination of items occurred in the source data.</span></span>  
  
 <span data-ttu-id="7440a-128">**大小**。</span><span class="sxs-lookup"><span data-stu-id="7440a-128">**Size**.</span></span> <span data-ttu-id="7440a-129">藉由變更項目集大小，您可以控制項目集清單的長度。</span><span class="sxs-lookup"><span data-stu-id="7440a-129">By changing itemset size, you can control the length of the lists of itemsets.</span></span> <span data-ttu-id="7440a-130">如果您不想要在清單中看到單一產品，請將 [專案集**大小下限**] 選項變更為2個以上。</span><span class="sxs-lookup"><span data-stu-id="7440a-130">If you don't want to see single products in the list, change the option, **Minimum itemset size**, to 2 or more.</span></span>  <span data-ttu-id="7440a-131">增加項目集大小下限來限制清單，讓您能夠尋找非常特定的模式，</span><span class="sxs-lookup"><span data-stu-id="7440a-131">Restricting the list by increasing the minimum size of itemsets lets you look for very specific patterns.</span></span> <span data-ttu-id="7440a-132">而且可能會在處理非常龐大的資料集時相當有用。</span><span class="sxs-lookup"><span data-stu-id="7440a-132">This might be useful if you are working with a very large set of data.</span></span>  
  
 <span data-ttu-id="7440a-133">您可以變更 [**最小支援**] 和 [**最大資料列**數] 值，以篩選顯示在索引標籤中的專案集數目。</span><span class="sxs-lookup"><span data-stu-id="7440a-133">You can filter the number of itemsets that are displayed in the tab by changing the **Minimum support** and **Maximum rows** values.</span></span> <span data-ttu-id="7440a-134">如果您增加 [**最小支援**] 值，此清單會顯示較少的專案集，但專案集會是輸入資料中較常見的一個。</span><span class="sxs-lookup"><span data-stu-id="7440a-134">If you increase the **Minimum Support** value, the list will show fewer itemsets, but the itemsets will be the more common ones in the input data.</span></span> <span data-ttu-id="7440a-135">一般是否與重要相同是另一個問題，您可以使用 [**規則**] 索引標籤來探索。</span><span class="sxs-lookup"><span data-stu-id="7440a-135">Whether common is the same as important is another question, which you can explore using the **Rules** tab.</span></span>  
  
 <span data-ttu-id="7440a-136">請注意，變更 [**專案集**] 索引標籤上的 [支援] 值或其他控制項，只會變更顯示的專案，而不會影響基礎模型。</span><span class="sxs-lookup"><span data-stu-id="7440a-136">Note that changing the support value or other controls on the **Itemsets** tab only changes the items that are displayed, and does not affect the underlying model.</span></span> <span data-ttu-id="7440a-137">如果您想要產生較少或更多的專案集，或限制其大小，您應該使用 `MINIMUM_SUPPORT` `MAXIMUM_SUPPORT` [**演算法參數**] 對話方塊中提供的參數和。</span><span class="sxs-lookup"><span data-stu-id="7440a-137">If you want to generate fewer or more itemsets, or limit their size, you should use the parameters, `MINIMUM_SUPPORT` and `MAXIMUM_SUPPORT`, available in the **Algorithm Parameters** dialog box.</span></span>  
  
##### <a name="explore-the-itemsets-list"></a><span data-ttu-id="7440a-138">探索項目集清單</span><span class="sxs-lookup"><span data-stu-id="7440a-138">Explore the itemsets list</span></span>  
  
1.  <span data-ttu-id="7440a-139">按一下 [**支援**] 資料行，依最高至最低支援排序。</span><span class="sxs-lookup"><span data-stu-id="7440a-139">Click the **Support** column to sort by highest to lowest support.</span></span> <span data-ttu-id="7440a-140">如此可讓您了解客戶最常購買的項目。</span><span class="sxs-lookup"><span data-stu-id="7440a-140">This will give you an idea of what customers are buying most often.</span></span>  
  
2.  <span data-ttu-id="7440a-141">若要將焦點放在感興趣的特定專案集，請在 [**篩選**專案集] 方塊中輸入一些文字。</span><span class="sxs-lookup"><span data-stu-id="7440a-141">To focus on a particular itemset of interest, out of the many thousand combinations possible, type some text in the **Filter Itemset** box.</span></span>  
  
     <span data-ttu-id="7440a-142">我們在此輸入 `Gloves` 。</span><span class="sxs-lookup"><span data-stu-id="7440a-142">Here we typed `Gloves`.</span></span> <span data-ttu-id="7440a-143">當您套用篩選時，系統會重新整理清單，並只顯示包含手套的項目集。</span><span class="sxs-lookup"><span data-stu-id="7440a-143">When you apply the filter, the list is refreshed to show only itemsets containing gloves.</span></span> <span data-ttu-id="7440a-144">如此可讓您專注於客戶購買手套及其他一些項目的交易。</span><span class="sxs-lookup"><span data-stu-id="7440a-144">This lets you focus on the transactions where customers purchased gloves and some other item.</span></span>  
  
     <span data-ttu-id="7440a-145">**[篩選項目集]** 選項也會顯示您先前已用過的篩選清單。</span><span class="sxs-lookup"><span data-stu-id="7440a-145">The **Filter Itemset** option also displays a list of the filters that you have used previously.</span></span>  
  
3.  <span data-ttu-id="7440a-146">變更 [專案集**大小下限**] 的值，以篩選出僅購買手套但沒有其他專案的客戶。</span><span class="sxs-lookup"><span data-stu-id="7440a-146">Change the value of **Minimum itemset size** to filter out the customers who bought only gloves and no other items.</span></span>  
  
4.  <span data-ttu-id="7440a-147">按一下 [**顯示**] 選項的下拉式清單，以控制屬性的顯示方式：</span><span class="sxs-lookup"><span data-stu-id="7440a-147">Click the dropdown list for the option **Show**, to control how the attributes are displayed:</span></span>  
  
    -   <span data-ttu-id="7440a-148">**顯示屬性名稱和值**</span><span class="sxs-lookup"><span data-stu-id="7440a-148">**Show attribute name and value**</span></span>  
  
    -   <span data-ttu-id="7440a-149">**只顯示屬性值**</span><span class="sxs-lookup"><span data-stu-id="7440a-149">**Show attribute value only**</span></span>  
  
    -   <span data-ttu-id="7440a-150">**只顯示屬性名稱**</span><span class="sxs-lookup"><span data-stu-id="7440a-150">**Show attribute name only**</span></span>  
  
     <span data-ttu-id="7440a-151">注意名稱有何改變。</span><span class="sxs-lookup"><span data-stu-id="7440a-151">Notice how the name changes.</span></span> <span data-ttu-id="7440a-152">在購物籃模型案例中，此模型是建立在多位客戶購買之產品的巢狀資料表上，因此屬性名稱通常是產品名稱，而清單中顯示的產品會標示為 `Existing`，表示客戶確實購買此項目。</span><span class="sxs-lookup"><span data-stu-id="7440a-152">In the case of a market basket model, which is built on nested tables of products that were purchased by multiple customers, the attribute name is typically the product name, and the presence of the product in the list is marked as `Existing`, meaning that the customer did buy the item.</span></span>  
  
     <span data-ttu-id="7440a-153">`Existing` 的相反是 `Missing`，在資料採礦中調查時是相當有用的屬性。</span><span class="sxs-lookup"><span data-stu-id="7440a-153">The opposite of `Existing` is `Missing`, which can be a very useful attribute to investigate in data mining.</span></span> <span data-ttu-id="7440a-154">例如，假設專案集 A + B 非常熱門，您想要尋找購買專案 A 但不是專案 B 的客戶。您可以使用預測查詢來執行這項操作，並使用其中一個來抓取交易，而不是另一個來進行進一步的分析。</span><span class="sxs-lookup"><span data-stu-id="7440a-154">For example, suppose the itemset A +B is so very popular that you wanted to find customers who purchased Item A but not item B. You could do this by using a prediction query and retrieving the transactions with one but not the other, and do some further analysis on those.</span></span> <span data-ttu-id="7440a-155">如需有關如何在關聯模型上建立預測查詢的詳細資訊，請參閱 SQL Server 線上叢書中的[關聯模型查詢範例](data-mining/association-model-query-examples.md)</span><span class="sxs-lookup"><span data-stu-id="7440a-155">For information about how to create prediction queries on association models, see [Association Model Query Examples](data-mining/association-model-query-examples.md) in SQL Server Books Online</span></span>  
  
5.  <span data-ttu-id="7440a-156">若要強制專案集清單使用新的篩選準則重新顯示，您可以選取或清除 [**顯示完整名稱**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="7440a-156">To force the list of itemsets to redisplay using your new filter criteria, you can select or clear the **Show long name** check box.</span></span>  
  
 [<span data-ttu-id="7440a-157">回到頁首</span><span class="sxs-lookup"><span data-stu-id="7440a-157">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="rules"></a><a name="BKMK_Rules"></a><span data-ttu-id="7440a-158">條</span><span class="sxs-lookup"><span data-stu-id="7440a-158">Rules</span></span>  
 <span data-ttu-id="7440a-159">[**規則**] 索引標籤會合併專案集的相關資訊及其相對值。</span><span class="sxs-lookup"><span data-stu-id="7440a-159">The **Rules** tab combines information about the itemsets and their relative value.</span></span>  
  
 <span data-ttu-id="7440a-160">![關聯模型建立的規則清單](media/dm13-association-rules.gif "關聯模型建立的規則清單")</span><span class="sxs-lookup"><span data-stu-id="7440a-160">![List of rules created by an association model](media/dm13-association-rules.gif "List of rules created by an association model")</span></span>  
  
 <span data-ttu-id="7440a-161">機率*代表資料*集中包含目標專案組合的案例分數。</span><span class="sxs-lookup"><span data-stu-id="7440a-161">*Probability* represents the fraction of cases in the dataset that contain the targeted combination of items.</span></span> <span data-ttu-id="7440a-162">機率類似于*信賴*的統計概念，並可讓您指出規則的結果可能發生的原因。</span><span class="sxs-lookup"><span data-stu-id="7440a-162">Probability is similar to the statistical concept of *confidence*, and gives you an indication of how likely the result of a rule is to occur.</span></span> <span data-ttu-id="7440a-163">您可以在此窗格中變更 [**最小**機率] 的值，以篩選顯示的規則。</span><span class="sxs-lookup"><span data-stu-id="7440a-163">You can change the value of **Minimum probability** in this pane to filter the rules that are displayed.</span></span>  
  
 <span data-ttu-id="7440a-164">您一開始看到的**最小**機率值是建立模型時，演算法所使用的臨界值。</span><span class="sxs-lookup"><span data-stu-id="7440a-164">The value for **Minimum probability** that you initially see is the threshold value that was used by the algorithm when building the model.</span></span> <span data-ttu-id="7440a-165">模型完成後，您無法減少此值，但您可以將它增加，只顯示較高的機率專案。</span><span class="sxs-lookup"><span data-stu-id="7440a-165">After the model is complete, you can't decrease this value, but you can increase it to show only the higher probability items.</span></span>  
  
 <span data-ttu-id="7440a-166">*重要性*的設計是要測量規則的實用性。</span><span class="sxs-lookup"><span data-stu-id="7440a-166">*Importance* is designed to measure the usefulness of a rule.</span></span> <span data-ttu-id="7440a-167">很常見的規則可能非常普遍，而擁有較少的資訊價值。</span><span class="sxs-lookup"><span data-stu-id="7440a-167">A rule that is very common might be so ubiquitous that is has little information value.</span></span> <span data-ttu-id="7440a-168">重要性越高，規則對於預測結果便越有價值。</span><span class="sxs-lookup"><span data-stu-id="7440a-168">The greater the importance, the more valuable the rule is for predicting the outcome.</span></span> <span data-ttu-id="7440a-169">在 [[購物籃分析] &#40;[適用于 Excel&#41;工具的資料表 AnalysisTools](shopping-basket-analysis-table-analysistools-for-excel.md) ] 中，[重要性] 可以與專案的價格結合，以判斷在銷售方面可能最具價值的組合。</span><span class="sxs-lookup"><span data-stu-id="7440a-169">In the [Shopping Basket Analysis &#40;Table AnalysisTools for Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md) tool, importance can be combined with the price of items to determine the bundles that are potentially most valuable in terms of sales.</span></span>  
  
##### <a name="explore-the-rules-list"></a><span data-ttu-id="7440a-170">探索規則清單</span><span class="sxs-lookup"><span data-stu-id="7440a-170">Explore the rules list</span></span>  
  
1.  <span data-ttu-id="7440a-171">嘗試按一下欄位標題-[機率]、[**重要性**] 和 [**規則** **]，以**查看資料變更的方式。</span><span class="sxs-lookup"><span data-stu-id="7440a-171">Try clicking the column headings - **Probability**, **Importance**, and **Rule** - to see how the data changes.</span></span>  
  
2.  <span data-ttu-id="7440a-172">使用 [**篩選規則**] 選項來輸入值，並將焦點放在目標規則上。</span><span class="sxs-lookup"><span data-stu-id="7440a-172">Use the **Filter Rule** option to type in values and focus on targeted rules.</span></span>  
  
     <span data-ttu-id="7440a-173">例如，如果您想要查看預測客戶可能隨手套購買的所有規則，請在文字方塊中輸入 "手套"，然後重新整理窗格。</span><span class="sxs-lookup"><span data-stu-id="7440a-173">For example, if you want to see all the rules that predict what customers are likely to purchase along with gloves, type "gloves" in the text box and refresh the pane.</span></span>  
  
     <span data-ttu-id="7440a-174">**[篩選項目集]** 選項也會顯示您先前已用過的篩選清單。</span><span class="sxs-lookup"><span data-stu-id="7440a-174">The **Filter Itemset** option also displays a list of the filters that you have used previously.</span></span>  
  
3.  <span data-ttu-id="7440a-175">若要強制使用篩選準則重新顯示規則清單，您可以選取或清除 [**顯示完整名稱**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="7440a-175">To force the list of rules to redisplay using filter criteria, you can select or clear the **Show long name** check box.</span></span>  
  
4.  <span data-ttu-id="7440a-176">使用 [**顯示**] 選項來控制規則名稱的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="7440a-176">Use the option, **Show** to control the way that rule names are displayed.</span></span>  
  
5.  <span data-ttu-id="7440a-177">將 [**最大資料列數**] 選項的值設定為100，然後按一下 [**複製到 Excel**]。</span><span class="sxs-lookup"><span data-stu-id="7440a-177">Set the value for the **Maximum rows** option to 100, and then click **Copy to Excel**.</span></span>  
  
     <span data-ttu-id="7440a-178">請注意，變更此值不會對模型中的資料量產生任何影響;它只會控制顯示清單中的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="7440a-178">Note that changing this value doesn't have any effect on the amount of data in the model; it simply controls the number of rows in the display list.</span></span> <span data-ttu-id="7440a-179">此選項適合搭配超大型模型使用。</span><span class="sxs-lookup"><span data-stu-id="7440a-179">This option can be useful when working with very large models.</span></span>  
  
 [<span data-ttu-id="7440a-180">回到頁首</span><span class="sxs-lookup"><span data-stu-id="7440a-180">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="dependency-network"></a><a name="BKMK_Dependency"></a><span data-ttu-id="7440a-181">相依性網路</span><span class="sxs-lookup"><span data-stu-id="7440a-181">Dependency Network</span></span>  
 <span data-ttu-id="7440a-182">[相依性**網路**] 索引標籤是專案之間相互關聯的視覺化地圖。</span><span class="sxs-lookup"><span data-stu-id="7440a-182">The **Dependency Network** tab is a visual map of the correlations among items.</span></span> <span data-ttu-id="7440a-183">圖形中的每個橢圓形 (稱為*節點*) 代表屬性/值組，例如 "背心 = Existing" 或 "Age = 1-30"。</span><span class="sxs-lookup"><span data-stu-id="7440a-183">Each oval in the graph (referred to as a *node*) represents an attribute-value pair, such as "Vest = Existing" or "Age = 1-30".</span></span>  <span data-ttu-id="7440a-184">每一行連接橢圓形 (稱為「*邊緣*」) 代表相互關聯的類型。</span><span class="sxs-lookup"><span data-stu-id="7440a-184">Each line connecting the ovals (referred to as an *edge*) represents a type of correlation.</span></span>  
  
 <span data-ttu-id="7440a-185">![關聯模型的相依性網路圖表](media/dm13-association-dependencynetwork.gif "關聯模型的相依性網路圖表")</span><span class="sxs-lookup"><span data-stu-id="7440a-185">![Dependency network graph for an association model](media/dm13-association-dependencynetwork.gif "Dependency network graph for an association model")</span></span>  
  
##### <a name="explore-the-dependency-network"></a><span data-ttu-id="7440a-186">探索相依性網路</span><span class="sxs-lookup"><span data-stu-id="7440a-186">Explore the dependency network</span></span>  
  
1.  <span data-ttu-id="7440a-187">按一下 [**尋找**] 按鈕，然後使用 [**尋找節點**] 對話方塊來輸入感利率的專案。</span><span class="sxs-lookup"><span data-stu-id="7440a-187">Click the **Find** button and use the **Find Node** dialog box to type an item of interest.</span></span>  
  
     <span data-ttu-id="7440a-188">例如，輸入 "手套"，然後將視窗中的圖形最大化，讓您可以輕鬆地查看結果。</span><span class="sxs-lookup"><span data-stu-id="7440a-188">For example, type "gloves" and then maximize the graph in the window so that you can easily see the results.</span></span>  
  
     <span data-ttu-id="7440a-189">包含項目的節點會醒目提示，而指向節點的箭頭表示連接項目的規則。</span><span class="sxs-lookup"><span data-stu-id="7440a-189">The node that contains the item is highlighted, while the arrows pointing to the node represent a rule that connects the items.</span></span>  
  
     <span data-ttu-id="7440a-190">箭頭方向表示規則方向。</span><span class="sxs-lookup"><span data-stu-id="7440a-190">The direction of the arrow tells you the direction of the rule.</span></span> <span data-ttu-id="7440a-191">例如，如果購買手套的人也可能購買背心，箭號就會從 "手套" 節點開始，並在 "背心" 節點上終止。</span><span class="sxs-lookup"><span data-stu-id="7440a-191">For example, if someone who buys gloves is also likely to buy a vest, the arrow will start from the "glove" node and terminate on the "vest" node.</span></span>  
  
     <span data-ttu-id="7440a-192">若要取得此規則的其他相關統計資料，您可以按一下 [**規則**] 索引標籤，然後尋找包含「手套-現有」-> 「背心-現有」描述的規則。) </span><span class="sxs-lookup"><span data-stu-id="7440a-192">To get additional statistics about this rule, you can click the **Rules** tab and look for a rule with the description, "Glove - Existing" -> "Vest - Existing.")</span></span>  
  
2.  <span data-ttu-id="7440a-193">按一下並拖曳檢視器左側的滑桿。</span><span class="sxs-lookup"><span data-stu-id="7440a-193">Click and drag the slider at the left of the viewer.</span></span>  
  
     <span data-ttu-id="7440a-194">此滑桿具有篩選規則機率的作用。</span><span class="sxs-lookup"><span data-stu-id="7440a-194">The slider acts as a filter on the probability of the rules.</span></span> <span data-ttu-id="7440a-195">降低滑桿只顯示最強的規則。</span><span class="sxs-lookup"><span data-stu-id="7440a-195">Lowering the slider shows only the strongest rules.</span></span>  
  
3.  <span data-ttu-id="7440a-196">按一下 [**複製到 excel** ]，將目前視窗的快照集複製到 excel。</span><span class="sxs-lookup"><span data-stu-id="7440a-196">Click **Copy to Excel** to copy a snapshot of the current window to Excel.</span></span>  
  
     <span data-ttu-id="7440a-197">您將無法使用複製到 Excel 的圖形;如果您需要互動式網狀圖形，請使用在[Visio 中觀看資料採礦模型 &#40;資料採礦增益集&#41;](viewing-data-mining-models-in-visio-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="7440a-197">You won't be able to work with the graph that you copy into Excel; if you need an interactive network graph, use the [Viewing Data Mining Models in Visio &#40;Data Mining Add-ins&#41;](viewing-data-mining-models-in-visio-data-mining-add-ins.md).</span></span>  
  
 [<span data-ttu-id="7440a-198">回到頁首</span><span class="sxs-lookup"><span data-stu-id="7440a-198">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
## <a name="more-about-association-models"></a><span data-ttu-id="7440a-199">進一步了解關聯模型</span><span class="sxs-lookup"><span data-stu-id="7440a-199">More about Association Models</span></span>  
 <span data-ttu-id="7440a-200">您可以使用 [**流覽]** 功能來開啟和探索使用 Microsoft 關聯規則演算法建立的任何模型。</span><span class="sxs-lookup"><span data-stu-id="7440a-200">You can use the **Browse** feature to open and explore any model that was created using the Microsoft Association Rules algorithm.</span></span> <span data-ttu-id="7440a-201">這包括使用購物籃分析所建立的模型[&#40;適用于 Excel&#41;工具的資料表 AnalysisTools](shopping-basket-analysis-table-analysistools-for-excel.md) 、**資料表的分析工具**功能區，或中的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7440a-201">This includes models built using the [Shopping Basket Analysis &#40;Table AnalysisTools for Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md) tool, in the **Table Analysis Tools** ribbon, or in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="7440a-202">如果您使用購物籃分析工具建立關聯規則模型，許多進階選項將會自動為您設定。</span><span class="sxs-lookup"><span data-stu-id="7440a-202">If you create an association rules model using the Shopping Basket Analysis tool, many of the advanced options are configured automatically for you.</span></span>  
  
 <span data-ttu-id="7440a-203">如果您想要設定 [高級參數] 或 [變更最小機率和支援]，請使用 [[關聯] Wizard &#40;適用于 excel&#41;Wizard 的資料採礦用戶端](associate-wizard-data-mining-client-for-excel.md)，或使用 [[將模型加入至 excel 的結構 &#40;資料採礦增益集&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md)模型化] 選項來建立您自己的模型。</span><span class="sxs-lookup"><span data-stu-id="7440a-203">If you want to set advanced parameters or alter minimum probability and support, use the [Associate Wizard &#40;Data Mining Client for Excel&#41;](associate-wizard-data-mining-client-for-excel.md) wizard, or build your own model using the [Add Model to Structure &#40;Data Mining Add-ins for Excel&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md) modeling option.</span></span>  
  
-   <span data-ttu-id="7440a-204">**專案集：** 當您建立模型時，您也可以將值指派給 MINIMUM_PROBABILITY 參數，以控制所產生的專案集數目。</span><span class="sxs-lookup"><span data-stu-id="7440a-204">**Itemsets:** When you create the model, you can also control the number of itemsets that are generated by assigning a value to the MINIMUM_PROBABILITY parameter.</span></span> <span data-ttu-id="7440a-205">您可以在 [演算法參數] 對話方塊使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="7440a-205">This parameter is available in the Algorithm Parameters dialog box.</span></span>  
  
-   <span data-ttu-id="7440a-206">**規則：**[!INCLUDE[msCoName](../includes/msconame-md.md)]關聯規則演算法會使用機率值來限制所產生的規則數目。</span><span class="sxs-lookup"><span data-stu-id="7440a-206">**Rules:** The [!INCLUDE[msCoName](../includes/msconame-md.md)] Association Rules algorithm uses probability values to restrict the number of rules that are generated.</span></span> <span data-ttu-id="7440a-207">您可以設定 `MINIMUM_PROBABILITY` 或 `MINIMUM _IMPORTANCE` 參數來控制規則數目。</span><span class="sxs-lookup"><span data-stu-id="7440a-207">You can control the number of rules by setting the parameters, `MINIMUM_PROBABILITY` or `MINIMUM _IMPORTANCE`.</span></span>  
  
 <span data-ttu-id="7440a-208">如需設定 advanced 參數的詳細資訊，請參閱[資料採礦演算法 &#40;SQL Server 資料採礦增益集&#41;](data-mining-algorithms-sql-server-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="7440a-208">For more information about configuring advanced parameters, see [Data Mining Algorithms &#40;SQL Server Data Mining Add-ins&#41;](data-mining-algorithms-sql-server-data-mining-add-ins.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7440a-209">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7440a-209">See Also</span></span>  
 [<span data-ttu-id="7440a-210">在 Excel 中流覽模型 &#40;SQL Server 資料採礦增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="7440a-210">Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
