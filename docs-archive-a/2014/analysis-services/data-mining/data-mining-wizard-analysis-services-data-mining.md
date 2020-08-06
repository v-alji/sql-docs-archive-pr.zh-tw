---
title: 資料採礦嚮導 (Analysis Services 資料採礦) |Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], data mining
- OLAP [Analysis Services], mining models
- Data Mining Wizard
- relational mining models [Analysis Services]
ms.assetid: d5fea90f-5f38-4639-8851-7707f6606a12
author: minewiskan
ms.author: owend
ms.openlocfilehash: 30c1800e24a1d655dc87aff10dcfb214bcd69bf2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607164"
---
# <a name="data-mining-wizard-analysis-services---data-mining"></a><span data-ttu-id="fdecf-102">資料採礦精靈 (Analysis Services - 資料採礦)</span><span class="sxs-lookup"><span data-stu-id="fdecf-102">Data Mining Wizard (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="fdecf-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 每次在資料採礦專案中加入新的採礦結構時，中的資料採礦嚮導都會啟動。</span><span class="sxs-lookup"><span data-stu-id="fdecf-103">The Data Mining Wizard in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] starts every time that you add a new mining structure to a data mining project.</span></span> <span data-ttu-id="fdecf-104">此精靈可幫助您選擇資料來源及設定資料來源檢視來定義用於分析的資料，然後幫助您建立初始模型。</span><span class="sxs-lookup"><span data-stu-id="fdecf-104">The wizard helps you choose a data source and set up a data source view that defines the data to be used for analysis, and then helps you create an initial model.</span></span>  
  
 <span data-ttu-id="fdecf-105">在精靈的最後一個階段，您可以選擇將資料分成定型集和測試集，並啟用類似鑽研的功能。</span><span class="sxs-lookup"><span data-stu-id="fdecf-105">In the final phase of the wizard, you can optionally divide your data into training and testing sets, and enable features such as drillthrough.</span></span>  
  
## <a name="what-to-know-before-you-start"></a><span data-ttu-id="fdecf-106">開始之前應該知道的事項</span><span class="sxs-lookup"><span data-stu-id="fdecf-106">What to Know Before You Start</span></span>  
 <span data-ttu-id="fdecf-107">以下是啟動精靈之前所需要知道的事項。</span><span class="sxs-lookup"><span data-stu-id="fdecf-107">Here are the things you need to know before you start the wizard.</span></span>  
  
-   <span data-ttu-id="fdecf-108">是否要從關聯式資料庫或從 OLAP 資料庫之現有的 Cube 中，建立資料採礦結構和模型？</span><span class="sxs-lookup"><span data-stu-id="fdecf-108">Will you build the data mining structure and models from a relational database or from an existing cube in an OLAP database?</span></span>  
  
-   <span data-ttu-id="fdecf-109">哪些資料行包含了可唯一識別案例記錄的索引鍵？</span><span class="sxs-lookup"><span data-stu-id="fdecf-109">Which columns contain the keys that uniquely identify a case record?</span></span>  
  
-   <span data-ttu-id="fdecf-110">您想要使用哪些資料行或屬性來預測？</span><span class="sxs-lookup"><span data-stu-id="fdecf-110">Which columns or attributes do you want to use for prediction?</span></span> <span data-ttu-id="fdecf-111">哪些資料行或屬性非常適合當做分析的輸入使用？</span><span class="sxs-lookup"><span data-stu-id="fdecf-111">Which columns or attributes are good to use as input for analysis?</span></span>  
  
-   <span data-ttu-id="fdecf-112">您應該使用哪一個演算法？</span><span class="sxs-lookup"><span data-stu-id="fdecf-112">Which algorithm should you use?</span></span> <span data-ttu-id="fdecf-113">中提供的演算法 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 具有不同的特性，且會產生不同的結果。</span><span class="sxs-lookup"><span data-stu-id="fdecf-113">The algorithms provided in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] all have different characteristics and produce different results.</span></span> <span data-ttu-id="fdecf-114">很幸運的是，每一組資料不限於一個模型，所以您可以自由地加入不同的模型進行試驗。</span><span class="sxs-lookup"><span data-stu-id="fdecf-114">Fortunately you are not limited to one model for each set of data, so feel free to experiment by adding different models.</span></span>  
  
-   <span data-ttu-id="fdecf-115">您是否需要能夠針對統一的資料集測試模型？</span><span class="sxs-lookup"><span data-stu-id="fdecf-115">Do you need to be able to test your models on a unified data set?</span></span> <span data-ttu-id="fdecf-116">如果是的話，請考慮使用此選項，以保留某些資料進行測試。</span><span class="sxs-lookup"><span data-stu-id="fdecf-116">If so, consider using the option to set some data aside for testing.</span></span> <span data-ttu-id="fdecf-117">您可以選擇某個百分比，然後視需要加以覆蓋指定的資料列數。</span><span class="sxs-lookup"><span data-stu-id="fdecf-117">You can choose a percentage, and cap that by a specified number of rows if desired.</span></span>  
  
##  <a name="starting-the-data-mining-wizard"></a><a name="BKMK_Using_DM_Wizard"></a> <span data-ttu-id="fdecf-118">啟動資料採礦精靈</span><span class="sxs-lookup"><span data-stu-id="fdecf-118">Starting the Data Mining Wizard</span></span>  
 <span data-ttu-id="fdecf-119">若要使用資料採礦精靈，您必須已在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中開啟方案，此方案至少包含一個資料採礦或 OLAP 專案。</span><span class="sxs-lookup"><span data-stu-id="fdecf-119">To use the Data Mining Wizard, you must have opened a solution in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] that contains at least one data mining or OLAP project.</span></span>  
  
-   <span data-ttu-id="fdecf-120">如果您的方案已經準備好進行資料採礦，您只需要以滑鼠右鍵按一下方案總管中的 [採礦結構]\*\*\*\* 節點，然後選取 [新增採礦結構]\*\*\*\*，即可啟動此精靈。</span><span class="sxs-lookup"><span data-stu-id="fdecf-120">If your solution is ready for data mining, you can simply right-click the **Mining Structures** node in Solution Explorer and select **New Mining Structure** to start the wizard.</span></span>  
  
-   <span data-ttu-id="fdecf-121">如果您的方案不包含任何現有專案，您可以加入新的資料採礦專案。</span><span class="sxs-lookup"><span data-stu-id="fdecf-121">If your solution does not contain any existing projects, you can add a new data mining project.</span></span> <span data-ttu-id="fdecf-122">在 [檔案]\*\*\*\* 功能表上選取 [新增]\*\*\*\*，然後選取 [專案]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fdecf-122">From the **File** menu, select **New**, and then select **Project**.</span></span> <span data-ttu-id="fdecf-123">請務必選擇 [Analysis Services 多維度和資料採礦專案]\*\*\*\* 範本。</span><span class="sxs-lookup"><span data-stu-id="fdecf-123">Be sure to choose the template, **Analysis Services Multidimensional and Data Mining Project**.</span></span>  
  
-   <span data-ttu-id="fdecf-124">您也可以使用 Analysis Services 匯入精靈，從現有的資料採礦方案取得中繼資料。</span><span class="sxs-lookup"><span data-stu-id="fdecf-124">You can also use the Analysis Services Import Wizard to obtain metadata from an existing data mining solution.</span></span> <span data-ttu-id="fdecf-125">但是，您不能選取個別物件來匯入，整個資料庫都要匯入，包括任何 Cube、資料來源檢視等。也請注意，透過匯入建立的新方案會自動設定為使用本機預設資料庫。</span><span class="sxs-lookup"><span data-stu-id="fdecf-125">However, you cannot select the individual objects to import; the entire database is imported, including any cubes, data source views, etc. Also note that the new solution that is created via import is automatically configured to use the local default database.</span></span> <span data-ttu-id="fdecf-126">您可能需要將此設定變更為另一個執行個體，然後才可以處理或瀏覽物件，而且如果您從舊版 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]匯入，您可能需要更新提供者的參考。</span><span class="sxs-lookup"><span data-stu-id="fdecf-126">You might need to change this to another instance before you can process or browse the objects, and if you are importing from a previous version of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you might need to update references to providers.</span></span>  
  
 <span data-ttu-id="fdecf-127">接下來，您將會建立採礦結構以及一個相關聯的資料採礦模型。</span><span class="sxs-lookup"><span data-stu-id="fdecf-127">Next, you will create the mining structure and one associated data mining model.</span></span> <span data-ttu-id="fdecf-128">您也可以只建立採礦結構，並在之後加入模型，但是先建立測試模型通常是最容易的方式。</span><span class="sxs-lookup"><span data-stu-id="fdecf-128">You can also create just the mining structure and add models later, but it is generally easiest to create a test model first.</span></span>  
  
###  <a name="relational-vs-olap-mining-models"></a><a name="BKMK_Relational"></a> <span data-ttu-id="fdecf-129">關聯式與OLAP 採礦模型的比較</span><span class="sxs-lookup"><span data-stu-id="fdecf-129">Relational vs. OLAP Mining Models</span></span>  
 <span data-ttu-id="fdecf-130">下一個重要的選項是選擇是否使用關聯式資料來源，或是讓您的模型根據多維度 (OLAP) 資料。</span><span class="sxs-lookup"><span data-stu-id="fdecf-130">The next important option that you have is whether to use a relational data source, or to base your model on multidimensional (OLAP) data.</span></span>  
  
 <span data-ttu-id="fdecf-131">資料採礦精靈會在這個點分成兩個路徑，這取決於您的資料來源為關聯式或是在 Cube 中。</span><span class="sxs-lookup"><span data-stu-id="fdecf-131">The Data Mining Wizard branches into two paths at this point, depending on whether your data source is relational or in a cube.</span></span> <span data-ttu-id="fdecf-132">除了資料選取程式以外的其他所有專案，都是相同的演算法選擇、加入維持資料集的能力等，但是選取 cube 資料比使用關聯式資料更為複雜。</span><span class="sxs-lookup"><span data-stu-id="fdecf-132">Everything else except the data selection process is the same-the choice of algorithm, the ability to add a holdout data set, etc.-but selecting cube data is a bit more complex than using relational data.</span></span> <span data-ttu-id="fdecf-133">(如果您建立的模型是以 Cube 為根據，最後您也可以取得一些其他選項)。</span><span class="sxs-lookup"><span data-stu-id="fdecf-133">(You also get some additional options at the end if you create a model based on a cube.)</span></span>  
  
 <span data-ttu-id="fdecf-134">如需每一個選項的詳細逐步解說，請參閱以下主題：</span><span class="sxs-lookup"><span data-stu-id="fdecf-134">See the following topics for a walkthrough of each option in more detail:</span></span>  
  
 [<span data-ttu-id="fdecf-135">建立關聯式採礦結構</span><span class="sxs-lookup"><span data-stu-id="fdecf-135">Create a Relational Mining Structure</span></span>](create-a-relational-mining-structure.md)  
 <span data-ttu-id="fdecf-136">在您建立關聯式資料採礦模型時，引導您進行決策。</span><span class="sxs-lookup"><span data-stu-id="fdecf-136">Walks you through the decisions you make when building a relational data mining model.</span></span>  
  
 [<span data-ttu-id="fdecf-137">建立 OLAP 採礦結構</span><span class="sxs-lookup"><span data-stu-id="fdecf-137">Create an OLAP Mining Structure</span></span>](create-an-olap-mining-structure.md)  
 <span data-ttu-id="fdecf-138">描述當您從 OLAP Cube 中選擇資料時所做的其他選項和選擇。</span><span class="sxs-lookup"><span data-stu-id="fdecf-138">Describes the additional options and selections to make when choosing data from an OLAP cube.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fdecf-139">您不需要 Cube 或 OLAP 資料庫，也可以進行資料採礦。</span><span class="sxs-lookup"><span data-stu-id="fdecf-139">You do not need to have a cube or an OLAP database to do data mining.</span></span> <span data-ttu-id="fdecf-140">除非您的資料已儲存在 Cube 中，或是您想要採礦 OLAP 維度或是 OLAP 彙總或計算的結果，否則我們建議您針對資料採礦使用關聯式資料表或資料來源。</span><span class="sxs-lookup"><span data-stu-id="fdecf-140">Unless your data is already stored in a cube, or you want to mine OLAP dimensions or the results of OLAP aggregations or calculations, we recommend that you use a relational table or data source for data mining.</span></span>  
  
### <a name="choosing-an-algorithm"></a><span data-ttu-id="fdecf-141">選擇演算法</span><span class="sxs-lookup"><span data-stu-id="fdecf-141">Choosing an Algorithm</span></span>  
 <span data-ttu-id="fdecf-142">接下來，您必須決定要使用哪一個演算法來處理資料。</span><span class="sxs-lookup"><span data-stu-id="fdecf-142">Next, you must decide on which algorithm to use in processing your data.</span></span> <span data-ttu-id="fdecf-143">這個決定可能很困難。</span><span class="sxs-lookup"><span data-stu-id="fdecf-143">This decision can be difficult to make.</span></span> <span data-ttu-id="fdecf-144">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中提供的每一個演算法都有不同的功能而且會產生不同的結果，所以您可以試驗並嘗試幾個不同模型，然後再決定哪一個模型最適合您的資料和商業問題。</span><span class="sxs-lookup"><span data-stu-id="fdecf-144">Each algorithm provided in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] has different features and produces different results, so you can experiment and try several different models before determining which is most appropriate for your data and your business problem.</span></span> <span data-ttu-id="fdecf-145">如需每一個演算法最適合之工作的說明，請參閱以下主題：</span><span class="sxs-lookup"><span data-stu-id="fdecf-145">See the following topic for an explanation of the tasks to which each algorithm is best suited:</span></span>  
  
 [<span data-ttu-id="fdecf-146">資料採礦演算法 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="fdecf-146">Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;</span></span>](data-mining-algorithms-analysis-services-data-mining.md)  
  
 <span data-ttu-id="fdecf-147">同樣地，您可以使用不同的演算法建立多個模型，或變更演算法的參數以建立不同的模型。</span><span class="sxs-lookup"><span data-stu-id="fdecf-147">Again, you can create multiple models using different algorithms, or change parameters for the algorithms to create different models.</span></span> <span data-ttu-id="fdecf-148">系統不會限制您的演算法選擇，針對相同資料建立幾個不同模型也是很好的作法。</span><span class="sxs-lookup"><span data-stu-id="fdecf-148">You are not locked into your choice of algorithm, and it is good practice to create several different models on the same data.</span></span>  
  
### <a name="define-the-data-used-for-modeling"></a><span data-ttu-id="fdecf-149">定義用於模型化的資料</span><span class="sxs-lookup"><span data-stu-id="fdecf-149">Define the Data Used for Modeling</span></span>  
 <span data-ttu-id="fdecf-150">除了從來源中選擇資料以外，您也必須指定資料來源檢視中的哪一個資料表包含「案例資料」\*\*。</span><span class="sxs-lookup"><span data-stu-id="fdecf-150">In addition to choosing the data from a source, you must specify which of the table in the data source view contains the *case data*.</span></span> <span data-ttu-id="fdecf-151">案例資料表將會用來定型資料採礦模型，因此您應該包含您想要分析的實體：例如，客戶和客戶的人口統計資訊。</span><span class="sxs-lookup"><span data-stu-id="fdecf-151">The case table will be used to train the data mining model, and as such should contain the entities that you want to analyze: for example, customers and their demographic information.</span></span> <span data-ttu-id="fdecf-152">每一個案例都必須是獨一無二的，而且必須可由「案例索引鍵」\*\* 識別。</span><span class="sxs-lookup"><span data-stu-id="fdecf-152">Each case must be unique, and must be identifiable by a *case key*.</span></span>  
  
 <span data-ttu-id="fdecf-153">除了指定案例資料表以外，您也可以在資料中包含「巢狀資料表」\*\*。</span><span class="sxs-lookup"><span data-stu-id="fdecf-153">In addition to specifying the case table, you can include *nested tables* in your data.</span></span> <span data-ttu-id="fdecf-154">巢狀資料表通常會包含有關案例資料表內實體 (例如客戶所進行之交易) 的詳細資訊，或是與實體具有多對一關聯性的屬性。</span><span class="sxs-lookup"><span data-stu-id="fdecf-154">A nested table usually contains additional information about the entities in the case table, such as transactions conducted by the customer, or attributes that have a many-to-one relationship with the entity.</span></span> <span data-ttu-id="fdecf-155">例如，聯結到 **Customers** 案例資料表的巢狀資料表可能包含每個客戶所購買的產品清單。</span><span class="sxs-lookup"><span data-stu-id="fdecf-155">For example, a nested table joined to the **Customers** case table might include a list of products purchased by each customer.</span></span> <span data-ttu-id="fdecf-156">在分析網站流量的模型中，巢狀資料表可能會包含使用者造訪之頁面的順序。</span><span class="sxs-lookup"><span data-stu-id="fdecf-156">In a model that analyzes traffic to a Web site, the nested table might include the sequences of pages that the user visited.</span></span> <span data-ttu-id="fdecf-157">如需詳細資訊，請參閱[巢狀資料表 &#40;Analysis Services - 資料採礦&#41;](nested-tables-analysis-services-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="fdecf-157">For more information, see [Nested Tables &#40;Analysis Services - Data Mining&#41;](nested-tables-analysis-services-data-mining.md)</span></span>  
  
### <a name="additional-features"></a><span data-ttu-id="fdecf-158">其他功能</span><span class="sxs-lookup"><span data-stu-id="fdecf-158">Additional Features</span></span>  
 <span data-ttu-id="fdecf-159">為了協助您選擇正確的資料，並正確設定資料來源，資料採礦精靈會提供以下其他功能：</span><span class="sxs-lookup"><span data-stu-id="fdecf-159">To assist you in choosing the right data, and configuring the data sources correctly, the Data Mining Wizard provides these additional features:</span></span>  
  
-   <span data-ttu-id="fdecf-160">**自動偵測資料類型**：此精靈將會檢查資料行值的唯一性與分佈，然後建議最佳資料類型和資料的使用類型。</span><span class="sxs-lookup"><span data-stu-id="fdecf-160">**Auto -detection of data types**: The wizard will examine the uniqueness and distribution of column values and then recommend the best data type, and suggest a usage type for the data.</span></span> <span data-ttu-id="fdecf-161">您可以從清單中選取值來覆寫這些建議。</span><span class="sxs-lookup"><span data-stu-id="fdecf-161">You can override these suggestions by selecting values from a list.</span></span>  
  
-   <span data-ttu-id="fdecf-162">**變數的建議**：您可以在對話方塊上按一下，並啟動分析器來計算模型包含的資料行之間的相互關聯性，並判斷是否有任何資料行可能是結果屬性的預測指標 (在給定目前的模型組態之下)。</span><span class="sxs-lookup"><span data-stu-id="fdecf-162">**Suggestions for variables**: You can click on a dialog box and start an analyzer that calculates correlations across the columns included in the model, and determines whether any columns are likely predictors of the outcome attribute, given the configuration of the model so far.</span></span> <span data-ttu-id="fdecf-163">您可以輸入不同的值來覆寫這些建議。</span><span class="sxs-lookup"><span data-stu-id="fdecf-163">You can override these suggestions by typing different values.</span></span>  
  
-   <span data-ttu-id="fdecf-164">**特徵選取**：大多數的演算法都會自動偵測屬於良好預測指標的資料行，並優先使用這些資料行。</span><span class="sxs-lookup"><span data-stu-id="fdecf-164">**Feature selection**: Most algorithms will automatically detect columns that are good predictors and use those preferentially.</span></span> <span data-ttu-id="fdecf-165">如果資料行中包含太多的值，則會套用「特徵選取」\*\*，以減少資料的基數，並提升找到有意義模式的機率。</span><span class="sxs-lookup"><span data-stu-id="fdecf-165">In columns that contain too many values, *feature selection* will be applied, to reduce the cardinality of the data and improve the chances for finding a meaningful pattern.</span></span> <span data-ttu-id="fdecf-166">您可以使用模型參數來影響特徵選取行為。</span><span class="sxs-lookup"><span data-stu-id="fdecf-166">You can affect feature selection behavior by using model parameters.</span></span>  
  
-   <span data-ttu-id="fdecf-167">**自動配量 Cube**：如果採礦模型是以 OLAP 資料來源為基礎，則會自動提供使用 Cube 屬性配量模型的功能。</span><span class="sxs-lookup"><span data-stu-id="fdecf-167">**Automatic cube slicing**: If your mining model is based on an OLAP data source, the ability to slice the model by using cube attributes is automatically provided.</span></span> <span data-ttu-id="fdecf-168">這對於根據 Cube 資料的子集來建立模型非常實用。</span><span class="sxs-lookup"><span data-stu-id="fdecf-168">This is handy for crating models based on subsets of cube data.</span></span>  
  
### <a name="completing-the-wizard"></a><span data-ttu-id="fdecf-169">正在完成精靈</span><span class="sxs-lookup"><span data-stu-id="fdecf-169">Completing the Wizard</span></span>  
 <span data-ttu-id="fdecf-170">此精靈中的最後一個步驟為命名採礦結構和相關聯的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="fdecf-170">The last step in the wizard is to name the mining structure and the associated mining model.</span></span> <span data-ttu-id="fdecf-171">根據您建立的模型類型而定，您可能也會擁有以下的重要選項：</span><span class="sxs-lookup"><span data-stu-id="fdecf-171">Depending on the type of model you created, you might also have the following important options:</span></span>  
  
-   <span data-ttu-id="fdecf-172">如果您選取 [允許使用鑽研]\*\*\*\*，就會在模型中啟用「鑽研」\*\*(drill through) 功能。</span><span class="sxs-lookup"><span data-stu-id="fdecf-172">If you select **Allow drill through**, the ability to *drill through* is enabled in the model.</span></span> <span data-ttu-id="fdecf-173">有了鑽研功能，具有適當權限的使用者便可以瀏覽用來建立此模型的來源資料。</span><span class="sxs-lookup"><span data-stu-id="fdecf-173">With drillthrough, users who have the appropriate permissions can explore the source data that is used to build the model.</span></span>  
  
-   <span data-ttu-id="fdecf-174">如果您正在建立 OLAP 模型，您可以選取 [Create a data mining dimension (建立新的資料採礦 Cube)]\*\*\*\* 或 [建立資料採礦維度]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="fdecf-174">If you are building an OLAP model, you can select the options, **Create a new data mining cube**, **or Create a data mining dimension**.</span></span> <span data-ttu-id="fdecf-175">這兩個選項都可讓您輕鬆瀏覽完成的模型，並鑽研至基礎資料。</span><span class="sxs-lookup"><span data-stu-id="fdecf-175">Both these options make it easier to browse the completed model and drill through to the underlying data.</span></span>  
  
 <span data-ttu-id="fdecf-176">完成資料採礦精靈之後，您可以使用資料採礦設計師來修改採礦結構和模型、檢視模型的精確度、檢視結構和模型的特性，或使用模型進行預測。</span><span class="sxs-lookup"><span data-stu-id="fdecf-176">After you complete the Data Mining Wizard, you use Data Mining Designer to modify the mining structure and models, to view the accuracy of the model, view characteristics of the structure and models, or make predictions by using the models.</span></span>  
  
 [<span data-ttu-id="fdecf-177">回到頁首</span><span class="sxs-lookup"><span data-stu-id="fdecf-177">Back to Top</span></span>](#BKMK_Using_DM_Wizard)  
  
## <a name="related-content"></a><span data-ttu-id="fdecf-178">相關內容</span><span class="sxs-lookup"><span data-stu-id="fdecf-178">Related Content</span></span>  
 <span data-ttu-id="fdecf-179">若要深入了解當您建立資料採礦模型時所需要做的決策，請參閱以下連結：</span><span class="sxs-lookup"><span data-stu-id="fdecf-179">To learn more about the decisions you need to make when creating a data mining model, see the following links:</span></span>  
  
 [<span data-ttu-id="fdecf-180">資料採礦演算法 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="fdecf-180">Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;</span></span>](data-mining-algorithms-analysis-services-data-mining.md)  
  
 [<span data-ttu-id="fdecf-181">內容類型 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="fdecf-181">Content Types &#40;Data Mining&#41;</span></span>](content-types-data-mining.md)  
  
 [<span data-ttu-id="fdecf-182">資料類型 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="fdecf-182">Data Types &#40;Data Mining&#41;</span></span>](data-types-data-mining.md)  
  
 [<span data-ttu-id="fdecf-183">&#40;資料採礦&#41;的特徵選取</span><span class="sxs-lookup"><span data-stu-id="fdecf-183">Feature Selection &#40;Data Mining&#41;</span></span>](feature-selection-data-mining.md)  
  
 [<span data-ttu-id="fdecf-184">遺漏值 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="fdecf-184">Missing Values &#40;Analysis Services - Data Mining&#41;</span></span>](missing-values-analysis-services-data-mining.md)  
  
 [<span data-ttu-id="fdecf-185">採礦模型的鑽研</span><span class="sxs-lookup"><span data-stu-id="fdecf-185">Drillthrough on Mining Models</span></span>](drillthrough-on-mining-models.md)  
  
## <a name="see-also"></a><span data-ttu-id="fdecf-186">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fdecf-186">See Also</span></span>  
 <span data-ttu-id="fdecf-187">[資料採礦工具](data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="fdecf-187">[Data Mining Tools](data-mining-tools.md) </span></span>  
 [<span data-ttu-id="fdecf-188">資料採礦方案</span><span class="sxs-lookup"><span data-stu-id="fdecf-188">Data Mining Solutions</span></span>](data-mining-solutions.md)  
  
  
