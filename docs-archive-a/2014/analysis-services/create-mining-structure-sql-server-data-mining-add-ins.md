---
title: 建立 (SQL Server 資料採礦增益集的採礦結構) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures, creating
ms.assetid: b8b1eedc-4d6d-4429-a578-e629ec573934
author: minewiskan
ms.author: owend
ms.openlocfilehash: c75712a893c6271da291693f46771aa71263280e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594287"
---
# <a name="create-mining-structure-sql-server-data-mining-add-ins"></a><span data-ttu-id="26eb5-102">建立採礦結構 (SQL Server 資料採礦增益集)</span><span class="sxs-lookup"><span data-stu-id="26eb5-102">Create Mining Structure (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="26eb5-103">![資料採礦功能區中的建立採礦結構按鈕](media/dmc-createstruct.gif "資料採礦功能區中的建立採礦結構按鈕")</span><span class="sxs-lookup"><span data-stu-id="26eb5-103">![Create Mining Structure button, Data Mining ribbon](media/dmc-createstruct.gif "Create Mining Structure button, Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="26eb5-104">當您想要建立用於分析的資料集，而不一定要建立模型時，請使用 [**資料模型**化] 群組中的 [ **Advanced** ] 選項。</span><span class="sxs-lookup"><span data-stu-id="26eb5-104">Use the **Advanced** option in the **Data Modeling** group when you want to create a data set used for analysis without necessarily creating a model.</span></span> <span data-ttu-id="26eb5-105">這在您想要試驗不同的演算法時會很有用。</span><span class="sxs-lookup"><span data-stu-id="26eb5-105">This is useful when you want to experiment with different algorithms.</span></span>  
  
 <span data-ttu-id="26eb5-106">建立了採礦結構之後，請使用 [[將模型加入結構](add-model-to-structure-data-mining-add-ins-for-excel.md)] wizard 來建立以該結構為基礎的模型。</span><span class="sxs-lookup"><span data-stu-id="26eb5-106">After you have created the mining structure, use the [Add Model to Structure](add-model-to-structure-data-mining-add-ins-for-excel.md) wizard to create a model based on that structure.</span></span> <span data-ttu-id="26eb5-107">您也可以使用 [資料採礦] [**高級查詢編輯器**] 來建立新的模型。</span><span class="sxs-lookup"><span data-stu-id="26eb5-107">You can also create new models by using the **Data Mining Advanced Query Editor**.</span></span>  
  
 <span data-ttu-id="26eb5-108">當您想要建立使用進階演算法 (例如線性迴歸或時序群集，其會受到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 的支援，但是精靈不會提供) 或自訂演算法的模型時，也可以使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="26eb5-108">You can also use this option when you intend to build models using one of the advanced algorithms, which are supported by [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] but not available through a wizard, such as linear regression or sequence clustering, or if you are using a custom algorithm.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="26eb5-109">建立採礦結構時，您也可以建立隨機選取的測試資料集，以用來驗證所有模型。</span><span class="sxs-lookup"><span data-stu-id="26eb5-109">When you create the mining structure, you can also establish a randomly selected testing data set that you can use to validate all your models.</span></span> <span data-ttu-id="26eb5-110">由於您可以輕鬆地根據一般資料集比較模型精確度，因此會很有幫助。</span><span class="sxs-lookup"><span data-stu-id="26eb5-110">This is handy because you can easily compare model accuracy against a common data set.</span></span> <span data-ttu-id="26eb5-111">只要選取 [將**資料分割成定型和測試集**] 選項，並指定要保留進行測試的適當資料百分比，通常約為30%。</span><span class="sxs-lookup"><span data-stu-id="26eb5-111">Just select the option, **Split data into training and testing sets** and specify an appropriate percentage of data to reserve for testing, usually around 30 percent.</span></span>  
  
## <a name="use-the-wizard-to-create-a-mining-structure"></a><span data-ttu-id="26eb5-112">使用精靈建立採礦結構</span><span class="sxs-lookup"><span data-stu-id="26eb5-112">Use the wizard to create a mining structure</span></span>  
  
1.  <span data-ttu-id="26eb5-113">在 [**資料採礦**] 功能區中，按一下 [ **Advanced**]，然後選取 [**建立結構**]。</span><span class="sxs-lookup"><span data-stu-id="26eb5-113">In the **Data Mining** ribbon, click **Advanced**, and select **Create Structure**.</span></span>  
  
2.  <span data-ttu-id="26eb5-114">在 [**選取來源資料**] 對話方塊中，指定包含您要用於分析之資料的 excel 範圍、excel 資料表或外部資料源。</span><span class="sxs-lookup"><span data-stu-id="26eb5-114">In the **Select source data** dialog box, specify the Excel range, Excel data table, or external data source that contains the data you want to use for analysis.</span></span>  
  
     <span data-ttu-id="26eb5-115">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="26eb5-115">Click **Next**.</span></span>  
  
3.  <span data-ttu-id="26eb5-116">在 [**選取資料行**] 對話方塊中，檢查所選資料來源中可用的資料行清單。</span><span class="sxs-lookup"><span data-stu-id="26eb5-116">In the **Select Columns** dialog box, review the list of columns available in the selected data source.</span></span>  
  
4.  <span data-ttu-id="26eb5-117">按一下 [資料行名稱] 右邊的箭號，以變更資料行的**使用**方式，從下列值中進行選擇：</span><span class="sxs-lookup"><span data-stu-id="26eb5-117">Click the arrow to the right of the column name to change the **usage** of the column, choosing from these values:</span></span>  
  
    -   <span data-ttu-id="26eb5-118">**索引鍵**。</span><span class="sxs-lookup"><span data-stu-id="26eb5-118">**Key**.</span></span> <span data-ttu-id="26eb5-119">每個模型至少需要一個索引鍵。</span><span class="sxs-lookup"><span data-stu-id="26eb5-119">At least one key is required for each model.</span></span>  
  
    -   <span data-ttu-id="26eb5-120">**金鑰時間**。</span><span class="sxs-lookup"><span data-stu-id="26eb5-120">**Key time**.</span></span> <span data-ttu-id="26eb5-121">這個選項僅適用於預測模型 (為其必要項)。</span><span class="sxs-lookup"><span data-stu-id="26eb5-121">This option is available only for forecasting models, where it is required.</span></span>  
  
    -   <span data-ttu-id="26eb5-122">**包含**。</span><span class="sxs-lookup"><span data-stu-id="26eb5-122">**Include**.</span></span> <span data-ttu-id="26eb5-123">表示資料行應用於採礦結構，但不是索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="26eb5-123">Indicates that the column should be made available in the mining structure but is not a key column.</span></span>  
  
    -   <span data-ttu-id="26eb5-124">**請勿使用**。</span><span class="sxs-lookup"><span data-stu-id="26eb5-124">**Do not use**.</span></span> <span data-ttu-id="26eb5-125">表示資料行不應包含在採礦結構中。</span><span class="sxs-lookup"><span data-stu-id="26eb5-125">Indicates that the column should not be included in the mining structure.</span></span>  
  
     <span data-ttu-id="26eb5-126">請記住，在建立模型時，您一律可以忽略資料行，但稍後再加入資料行時，需要重新處理結構和模型。</span><span class="sxs-lookup"><span data-stu-id="26eb5-126">Remember that you can always ignore columns when you build the model, but to add columns later requires that you reprocess the structure and model.</span></span>  
  
5.  <span data-ttu-id="26eb5-127">按一下 [流覽\*\* ( ...] ) \*\*按鈕，設定內容類型、資料類型和模型旗標。</span><span class="sxs-lookup"><span data-stu-id="26eb5-127">Click the browse **(...)** button to set the content type, data type, and modeling flags.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="26eb5-128">如果資料行包含數值資料，您應該永遠開啟此對話方塊，以確保選擇的資料類型正確。</span><span class="sxs-lookup"><span data-stu-id="26eb5-128">If the column contains numeric data, you should always open this dialog box to ensure that the correct data type is chosen.</span></span> <span data-ttu-id="26eb5-129">在某些情況下，即使輸入資料為數字，您仍需要將它視為類別變數或離散值，而不是連續的數字。</span><span class="sxs-lookup"><span data-stu-id="26eb5-129">In some cases, even if the input data is a number, you will want to treat it as a categorical variable, or discrete value, instead of a continuous number.</span></span>  
    >   
    >  <span data-ttu-id="26eb5-130">例如，郵遞區號資料行預設可能會以連續的 LONG 資料類型列出，但是您可以指定將郵遞區號當做離散文字值處理，以便得到更好的效果。</span><span class="sxs-lookup"><span data-stu-id="26eb5-130">For example, a postal code column might be listed by default as a continuous long data type, but to get better results, you can specify that it be handled as a discrete text value.</span></span>  
    >   
    >  <span data-ttu-id="26eb5-131">如需詳細資訊，請參閱關於[選擇資料採礦資料](choosing-data-for-data-mining.md)中的內容類型一節。</span><span class="sxs-lookup"><span data-stu-id="26eb5-131">For more information, see the section on content types in [Choosing Data for Data Mining](choosing-data-for-data-mining.md).</span></span>  
  
     <span data-ttu-id="26eb5-132">按一下 **[確定]** ，關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="26eb5-132">Click **OK** to close the dialog box.</span></span>  
  
6.  <span data-ttu-id="26eb5-133">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="26eb5-133">Click **Next**.</span></span>  
  
     <span data-ttu-id="26eb5-134">根據您使用的資料類型，您可以在這個步驟之後就完成精靈。</span><span class="sxs-lookup"><span data-stu-id="26eb5-134">Depending on what type of data you are using, you might complete the wizard after this step.</span></span> <span data-ttu-id="26eb5-135">在這種情況下，請直接跳到 [**完成]** 頁面，為您的採礦結構命名。</span><span class="sxs-lookup"><span data-stu-id="26eb5-135">In that case, jump ahead to the **Finish** page to name your mining structure.</span></span>  
  
     <span data-ttu-id="26eb5-136">若為其他模型，您另外還可以建立測試資料集。</span><span class="sxs-lookup"><span data-stu-id="26eb5-136">For other models, you have the additional option to create a testing data set.</span></span>  
  
7.  <span data-ttu-id="26eb5-137">在 [將**資料分割成定型和測試資料集**] 對話方塊中，指定您想要資料分割的方式。</span><span class="sxs-lookup"><span data-stu-id="26eb5-137">In the **Split data into training and testing data sets** dialog box, specify how you want your data partitioned.</span></span> <span data-ttu-id="26eb5-138">根據預設，百分之三十的資料用於測試。</span><span class="sxs-lookup"><span data-stu-id="26eb5-138">By default, 30 percent of data is used for testing.</span></span>  
  
     <span data-ttu-id="26eb5-139">或者，輸入要用於測試之資料列的數目上限。</span><span class="sxs-lookup"><span data-stu-id="26eb5-139">Optionally, type the maximum number of rows to use for testing.</span></span>  
  
     <span data-ttu-id="26eb5-140">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="26eb5-140">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="26eb5-141">在 [**完成**] 對話方塊中，輸入新的「採礦結構」的名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="26eb5-141">In the **Finish** dialog, type a name and description for the new mining structure.</span></span>  
  
9. <span data-ttu-id="26eb5-142">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="26eb5-142">Click **Finish**.</span></span>  
  
### <a name="related-options"></a><span data-ttu-id="26eb5-143">相關的選項</span><span class="sxs-lookup"><span data-stu-id="26eb5-143">Related Options</span></span>  
  
|<span data-ttu-id="26eb5-144">選項</span><span class="sxs-lookup"><span data-stu-id="26eb5-144">Option</span></span>|<span data-ttu-id="26eb5-145">註解</span><span class="sxs-lookup"><span data-stu-id="26eb5-145">Comments</span></span>|  
|------------|--------------|  
|<span data-ttu-id="26eb5-146">[**選取來源資料**] 對話方塊</span><span class="sxs-lookup"><span data-stu-id="26eb5-146">**Select Source Data** dialog box</span></span>|<span data-ttu-id="26eb5-147">當您選取 Excel 資料表時，您應該指出資料是否已有標頭。</span><span class="sxs-lookup"><span data-stu-id="26eb5-147">When you select an Excel table, you should indicate whether the data already has headers.</span></span> <span data-ttu-id="26eb5-148">如果略過這個選項，資料的第一列會做為資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="26eb5-148">If you skip this, the first row of data will be used as the column name.</span></span><br /><br /> <span data-ttu-id="26eb5-149">如果您使用 [**外部資料源**] 選項，您可以使用任何可在資料來源中定義的資料類型 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="26eb5-149">If you use the option, **External data source**, you can use any kind of data that can be defined in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data source.</span></span> <span data-ttu-id="26eb5-150">不過，增益集中用於建立新資料來源的對話方塊不包含 Analysis Services 支援的所有資料來源，因此建議您事先在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 伺服器上建立資料來源，然後再使用增益集進行連接。</span><span class="sxs-lookup"><span data-stu-id="26eb5-150">However, the dialog box in the add-in for creating new data sources does not include the full range of data sources supported by Analysis Services, so we recommend that you create the data sources on the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server in advance and then connect using the add-ins.</span></span>|  
|<span data-ttu-id="26eb5-151">[**資料來源查詢編輯器**] 對話方塊</span><span class="sxs-lookup"><span data-stu-id="26eb5-151">**Data Source Query Editor** dialog box</span></span>|<span data-ttu-id="26eb5-152">在您連接至指定的資料來源之後，您可以加入資料行，或建立自訂查詢以產生自訂資料行。</span><span class="sxs-lookup"><span data-stu-id="26eb5-152">After you have connected to the specified data source, you can add columns, or create a custom query to generate custom columns.</span></span>|  
|<span data-ttu-id="26eb5-153">**將資料分割成定型集和測試集**</span><span class="sxs-lookup"><span data-stu-id="26eb5-153">**Split data into training and testing data sets**</span></span>|<span data-ttu-id="26eb5-154">定型與測試集的建議值為70%，用於定型，而30% 用於測試;不過，如果您有大量資料，您可以指定測試的最大資料列數目。</span><span class="sxs-lookup"><span data-stu-id="26eb5-154">A recommended value for training vs. testing sets is 70 percent for training and 30 percent for testing; however, if you have a lot of data, you can specify a maximum number of rows for testing.</span></span>|  
|<span data-ttu-id="26eb5-155">[完成] 對話方塊</span><span class="sxs-lookup"><span data-stu-id="26eb5-155">Finish dialog box</span></span>|<span data-ttu-id="26eb5-156">某些模型類型提供鑽研選項，如果您在採礦結構中包含詳細資料的資料行，這些選項會很有用。</span><span class="sxs-lookup"><span data-stu-id="26eb5-156">The options for drillthrough are available on some model types and are very useful if you included detail columns in your mining structure.</span></span> <span data-ttu-id="26eb5-157">例如，如果您建立群集模型，您可以包含用於鑽研 (而不是用於分析) 的詳細資料 (例如名稱或電子郵件地址)，以便更容易連絡特定群集中的客戶。</span><span class="sxs-lookup"><span data-stu-id="26eb5-157">For example, if you create a clustering model, you can include details such as name or email address for drillthrough but not analysis, to make it easier to contact customers in a particular cluster.</span></span>|  
  
###  <a name="setting-column-usage-in-the-create-mining-structure-wizard"></a><a name="Bkmk_strctcolumn"></a><span data-ttu-id="26eb5-158">在建立採礦結構 Wizard 中設定資料行使用方式</span><span class="sxs-lookup"><span data-stu-id="26eb5-158">Setting Column Usage in the Create Mining Structure Wizard</span></span>  
 <span data-ttu-id="26eb5-159">在建立資料採礦結構時，可以指定要在採礦結構中包含資料來源的哪些資料行，以及這些資料行的使用方式。</span><span class="sxs-lookup"><span data-stu-id="26eb5-159">When you create a new mining structure, you can specify which columns in the data source should be included in the mining structure, and how those columns should be used.</span></span> <span data-ttu-id="26eb5-160">請記住，採礦結構可以支援多個採礦模型。</span><span class="sxs-lookup"><span data-stu-id="26eb5-160">Remember that a mining structure can support multiple mining models.</span></span>  
  
|<span data-ttu-id="26eb5-161">值</span><span class="sxs-lookup"><span data-stu-id="26eb5-161">Values</span></span>|<span data-ttu-id="26eb5-162">描述</span><span class="sxs-lookup"><span data-stu-id="26eb5-162">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="26eb5-163">**包含**</span><span class="sxs-lookup"><span data-stu-id="26eb5-163">**Include**</span></span>|<span data-ttu-id="26eb5-164">指定資料行包含可用於分析或預測的資料。</span><span class="sxs-lookup"><span data-stu-id="26eb5-164">Specifies that the column contains data that can be used for analysis or prediction.</span></span>|  
|<span data-ttu-id="26eb5-165">**索引鍵**</span><span class="sxs-lookup"><span data-stu-id="26eb5-165">**Key**</span></span>|<span data-ttu-id="26eb5-166">指定資料行包含交易識別碼、序列識別碼，或處理所需的另一個索引鍵。</span><span class="sxs-lookup"><span data-stu-id="26eb5-166">Specifies that the column contains a transaction ID, a series ID, or another key required for processing.</span></span><br /><br /> <span data-ttu-id="26eb5-167">所有的演算法都需要索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="26eb5-167">All algorithms require a Key column.</span></span> <span data-ttu-id="26eb5-168">不過，有些演算法只允許單一索引鍵，有些則允許多個索引鍵。</span><span class="sxs-lookup"><span data-stu-id="26eb5-168">However, some algorithms permit only a single key, while others permit multiple keys.</span></span><br /><br /> <span data-ttu-id="26eb5-169">如果資料行包含索引鍵，但不需要進行處理，請選取 [**不使用**]。</span><span class="sxs-lookup"><span data-stu-id="26eb5-169">If the column contains a key but is not required for processing, select **Do Not Use**.</span></span>|  
|<span data-ttu-id="26eb5-170">**Key Time**</span><span class="sxs-lookup"><span data-stu-id="26eb5-170">**Key Time**</span></span>|<span data-ttu-id="26eb5-171">指定資料行包含日期或其他的數值，可用來唯一識別時間序列的項目。</span><span class="sxs-lookup"><span data-stu-id="26eb5-171">Specifies that the column contains a date or other numeric value that can be used to uniquely identify items in a time series.</span></span>|  
|<span data-ttu-id="26eb5-172">**不要使用**</span><span class="sxs-lookup"><span data-stu-id="26eb5-172">**Do Not Use**</span></span>|<span data-ttu-id="26eb5-173">指定應忽略資料行。</span><span class="sxs-lookup"><span data-stu-id="26eb5-173">Specifies that the column should be ignored.</span></span> <span data-ttu-id="26eb5-174">不會處理資料行中的資料。</span><span class="sxs-lookup"><span data-stu-id="26eb5-174">The data in the column will not be processed.</span></span>|  
  
 <span data-ttu-id="26eb5-175">若要正確地處理模型，演算法必須知道哪個資料行是唯一識別每個資料列的索引鍵資料行；如果是建立可預測模型，哪個資料行是建立預測的目標資料行；以及使用哪些資料行做為建立預測目標資料行之關聯性的輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="26eb5-175">To process a model correctly, the algorithm must know which column is the key column that uniquely identifies each row, which column is the target column for creating predictions if you are creating a predictable model, and which columns to use as input columns to create the relationships that predict the target column.</span></span>  
  
-   <span data-ttu-id="26eb5-176">指定為 [不**使用**] 的資料行不會出現在此採礦結構中。</span><span class="sxs-lookup"><span data-stu-id="26eb5-176">Columns that are specified as **Do not use** will not be present in the mining structure.</span></span>  
  
     <span data-ttu-id="26eb5-177">如果加入的資料行不必要或具有不正確的值，就會對分析結果造成不良的影響。</span><span class="sxs-lookup"><span data-stu-id="26eb5-177">If you add columns that are unnecessary or have bad values, it can adversely affect the results of analysis.</span></span> <span data-ttu-id="26eb5-178">因此，請務必只加入相關的資料行。</span><span class="sxs-lookup"><span data-stu-id="26eb5-178">Therefore, be sure to include only those columns that are relevant.</span></span> <span data-ttu-id="26eb5-179">不過，請您記住，未用於採礦結構中的資料行就無法用於查詢。</span><span class="sxs-lookup"><span data-stu-id="26eb5-179">However, remember that the columns that you do not use in the mining structure will not be available for querying.</span></span>  
  
-   <span data-ttu-id="26eb5-180">指定為**Include**類型的資料行會包含在此採礦結構中，而稍後可用於分析或預測模型。</span><span class="sxs-lookup"><span data-stu-id="26eb5-180">Columns that are specified as the **Include** type will be included in the mining structure and later can be used for either analysis or prediction in the mining models.</span></span>  
  
     <span data-ttu-id="26eb5-181">如果您不確定是否需要使用某資料行，可以將該資料行包含在採礦結構中，然後建立不使用該資料行的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="26eb5-181">If you are not sure whether you will need to use the column, you can always include the column in the mining structure and then create a mining model that does not use that column.</span></span> <span data-ttu-id="26eb5-182">例如，您可以在資料中包含電話號碼資料行以供稍後參考，但建立忽略電話號碼的群集模型。</span><span class="sxs-lookup"><span data-stu-id="26eb5-182">For example, you might include a phone number column in your data for later reference, but create a clustering model that ignores phone numbers.</span></span> <span data-ttu-id="26eb5-183">在建立該群集後，可以建立查詢以傳回屬於特定群集之人員的電話號碼。</span><span class="sxs-lookup"><span data-stu-id="26eb5-183">After the clusters have been created, you can create a query that returns the phone numbers of people who belong to a particular cluster.</span></span>  
  
-   <span data-ttu-id="26eb5-184">所有的演算法都需要索引**鍵**資料行。</span><span class="sxs-lookup"><span data-stu-id="26eb5-184">All algorithms require a **Key** column.</span></span> <span data-ttu-id="26eb5-185">索引鍵資料行中的值必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="26eb5-185">The values in the Key column must be unique.</span></span> <span data-ttu-id="26eb5-186">只有在預測或時間序列模型中，才需要**Key Time**資料行。</span><span class="sxs-lookup"><span data-stu-id="26eb5-186">A **Key Time** column is required only for forecasting or time series models.</span></span> <span data-ttu-id="26eb5-187">.</span><span class="sxs-lookup"><span data-stu-id="26eb5-187">.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="26eb5-188">需求</span><span class="sxs-lookup"><span data-stu-id="26eb5-188">Requirements</span></span>  
 <span data-ttu-id="26eb5-189">若要建立資料採礦結構，您必須具有 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體的連接。</span><span class="sxs-lookup"><span data-stu-id="26eb5-189">To create a data mining structure, you must have a connection to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="26eb5-190">即使您使用暫時性結構，還是需要連接。</span><span class="sxs-lookup"><span data-stu-id="26eb5-190">A connection is required even if you are working with temporary structures.</span></span> <span data-ttu-id="26eb5-191">如需有關如何建立或變更連接的詳細資訊，請參閱[連接到來源資料 &#40;適用于 Excel&#41;的資料採礦用戶端](connect-to-source-data-data-mining-client-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="26eb5-191">For more information about how to create or change a connection, see [Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26eb5-192">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26eb5-192">See Also</span></span>  
 [<span data-ttu-id="26eb5-193">建立資料採礦模型</span><span class="sxs-lookup"><span data-stu-id="26eb5-193">Creating a Data Mining Model</span></span>](creating-a-data-mining-model.md)  
  
  
