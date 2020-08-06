---
title: 選擇和對應模型測試資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- columns [data mining], mining accuracy charts
- Mining Accuracy Chart [Analysis Services], column mappings
- input column mapping [Analysis Services]
- mapping input columns [Analysis Services]
ms.assetid: be0d9f20-40c3-4dac-81da-281cfe724126
author: minewiskan
ms.author: owend
ms.openlocfilehash: 84f1d01c40070069d610bb028ab003223c5afbcd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594847"
---
# <a name="choose-and-map-model-testing-data"></a><span data-ttu-id="fc5be-102">選擇和對應模型測試資料</span><span class="sxs-lookup"><span data-stu-id="fc5be-102">Choose and Map Model Testing Data</span></span>
  <span data-ttu-id="fc5be-103">若要在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中建立精確度圖表，您必須選擇將用來測試模型的資料，並將資料對應至模型。</span><span class="sxs-lookup"><span data-stu-id="fc5be-103">To create an accuracy chart in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you must choose the data that will be used to test the model, and map the data to the model.</span></span>  
  
 <span data-ttu-id="fc5be-104">根據預設，只要您在建立採礦結構時建立了鑑效組資料集， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 就會使用採礦模型測試資料。</span><span class="sxs-lookup"><span data-stu-id="fc5be-104">By default, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will use the mining model testing data, provided that you created a holdout data set when you built the mining structure.</span></span> <span data-ttu-id="fc5be-105">建立鑑效組測試集是測試根據相同採礦結構之模型的最簡單方式，因為資料行名稱和資料類型永遠符合模型，並且您可以合理地確定資料分佈是相似的。</span><span class="sxs-lookup"><span data-stu-id="fc5be-105">Creating a holdout test set is the easiest way to test models that are based on the same mining structure, because the column names and data types will always match the model, and you can be reasonably assured that the distribution of the data is similar.</span></span> <span data-ttu-id="fc5be-106">此外，設計工具將自動建立輸入和模型資料行之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="fc5be-106">Also, the designer will automatically create the relationships between the input and model columns.</span></span>  
  
 <span data-ttu-id="fc5be-107">您也可以指定外部資料來源。</span><span class="sxs-lookup"><span data-stu-id="fc5be-107">Alternatively, you can specify an external source of data.</span></span> <span data-ttu-id="fc5be-108">對於外部資料，有一些其他需求：</span><span class="sxs-lookup"><span data-stu-id="fc5be-108">For external data, there are some additional requirements:</span></span>  
  
-   <span data-ttu-id="fc5be-109">外部資料集必須在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]的執行個體中定義為資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="fc5be-109">The external data set must be defined as a data source view in an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="fc5be-110">外部資料集至少必須包含一個資料行，而且該資料行可以對應至採礦模型中的可預測資料行。</span><span class="sxs-lookup"><span data-stu-id="fc5be-110">The external data set must at least contain one column that can be mapped to the predictable column in the mining model.</span></span> <span data-ttu-id="fc5be-111">您可以選擇忽略某些資料行。</span><span class="sxs-lookup"><span data-stu-id="fc5be-111">You can choose to ignore some columns.</span></span>  
  
-   <span data-ttu-id="fc5be-112">您無法加入新的資料行或是對應不同資料來源檢視中的資料行。</span><span class="sxs-lookup"><span data-stu-id="fc5be-112">You cannot add new columns or map columns in a different data source view.</span></span> <span data-ttu-id="fc5be-113">您所選的資料來源檢視必須包含預測查詢所需的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="fc5be-113">The data source view that you select must contain all the columns that you need for the prediction query.</span></span>  
  
-   <span data-ttu-id="fc5be-114">如果外部資料行名稱與模型中的資料行名稱完全符合，則設計工具會自動對應這些資料行。</span><span class="sxs-lookup"><span data-stu-id="fc5be-114">If the external column names exactly match those in the model, the designer will map them for you.</span></span> <span data-ttu-id="fc5be-115">如果對應錯誤，您可以變更這些對應、刪除對應，或是為現有的資料行建立新的對應。</span><span class="sxs-lookup"><span data-stu-id="fc5be-115">If the mappings are wrong, you can change them, or delete and create new mappings for existing columns.</span></span>  
  
-   <span data-ttu-id="fc5be-116">如果您使用外部資料來源，可以套用篩選，將測試資料限制為相關的案例子集。</span><span class="sxs-lookup"><span data-stu-id="fc5be-116">If you use an external data source, you can apply filters to restrict the testing data to a relevant subset of cases.</span></span>  
  
-   <span data-ttu-id="fc5be-117">即使在使用鑑效組測試集時，您也應該意識到篩選器可能在與採礦結構關聯的測試資料和採礦模型測試案例之間造成差異。</span><span class="sxs-lookup"><span data-stu-id="fc5be-117">Even when you use the holdout test set, you should be aware that filters can cause differences between the testing data associated with a mining structure and the mining model test cases.</span></span>  
  
 <span data-ttu-id="fc5be-118">本主題描述如何選擇和對應測試資料：</span><span class="sxs-lookup"><span data-stu-id="fc5be-118">This topic describes how to choose and map the testing data:</span></span>  
  
 [<span data-ttu-id="fc5be-119">選取輸入資料表來測試採礦模型的精確度</span><span class="sxs-lookup"><span data-stu-id="fc5be-119">Select input tables to test the accuracy of a mining model</span></span>](#bkmk_SelectInputs)  
  
 [<span data-ttu-id="fc5be-120">將模型資料行對應到測試資料的資料行</span><span class="sxs-lookup"><span data-stu-id="fc5be-120">Map model columns to the columns in the testing data</span></span>](#bkmk_MapColumns)  
  
 [<span data-ttu-id="fc5be-121">變更測試資料中的資料行對應至模型的方式</span><span class="sxs-lookup"><span data-stu-id="fc5be-121">Change the way that columns in the testing data are mapped to the model</span></span>](#bkmk_ChangeMappings)  
  
##  <a name="to-select-input-tables-to-test-the-accuracy-of-a-mining-model"></a><a name="bkmk_SelectInputs"></a> <span data-ttu-id="fc5be-122">若要選取輸入資料表來測試採礦模型的精確度</span><span class="sxs-lookup"><span data-stu-id="fc5be-122">To select input tables to test the accuracy of a mining model</span></span>  
  
1.  <span data-ttu-id="fc5be-123">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]的資料採礦設計師中，按兩下包含您想要建立圖表之模型的採礦結構。</span><span class="sxs-lookup"><span data-stu-id="fc5be-123">In Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], double-click the mining structure that contains the models you want to chart.</span></span>  
  
2.  <span data-ttu-id="fc5be-124">選取 **[採礦精確度圖表]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="fc5be-124">Select the **Mining Accuracy Chart** tab.</span></span>  
  
3.  <span data-ttu-id="fc5be-125">在 [採礦精確度圖表]\*\*\*\* 檢視的 [輸入選擇]\*\*\*\* 索引標籤中，選取下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="fc5be-125">On the **Input Selection Tab** of the **Mining Accuracy Chart** view, select one of the following options:</span></span>  
  
     <span data-ttu-id="fc5be-126">**使用採礦模型測試案例**</span><span class="sxs-lookup"><span data-stu-id="fc5be-126">**Use mining model test cases**</span></span>  
  
     <span data-ttu-id="fc5be-127">**使用採礦結構測試案例**</span><span class="sxs-lookup"><span data-stu-id="fc5be-127">**Use mining structure test cases**</span></span>  
  
     <span data-ttu-id="fc5be-128">**指定不同的資料集**</span><span class="sxs-lookup"><span data-stu-id="fc5be-128">**Specify a different data set**</span></span>  
  
4.  <span data-ttu-id="fc5be-129">如果您選取了 [指定不同的資料集]\*\*\*\*，請選擇性地按一下 [開啟篩選編輯器]\*\*\*\*，以便建立輸入資料集的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="fc5be-129">If you selected **Specify a different data set**, optionally click **Open Filter Editor** to create filter conditions on the input data set.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="fc5be-130">按一下 [增益圖]\*\*\*\* 索引標籤或 [分類矩陣]\*\*\*\* 索引標籤，以便使用指定的測試資料來自動建立圖表。</span><span class="sxs-lookup"><span data-stu-id="fc5be-130">Click the **Lift Chart** tab or the **Classification Matrix** tab to automatically build the chart by using the testing data you specified.</span></span>  
  
##  <a name="to-map-model-columns-to-the-columns-in-the-testing-data"></a><a name="bkmk_MapColumns"></a> <span data-ttu-id="fc5be-131">若要將模型資料行對應到測試資料的資料行</span><span class="sxs-lookup"><span data-stu-id="fc5be-131">To map model columns to the columns in the testing data</span></span>  
  
1.  <span data-ttu-id="fc5be-132">在資料採礦設計師中，按兩下包含您想要建立圖表之模型的採礦結構，以開啟結構與模型。</span><span class="sxs-lookup"><span data-stu-id="fc5be-132">Double-click the mining structure that contains the models you want to chart, to open the structure and models in Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="fc5be-133">選取 **[採礦精確度圖表]** 索引標籤，然後選取 **[輸入選擇]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="fc5be-133">Select the **Mining Accuracy Chart** tab, and then select the **Input Selection** tab.</span></span>  
  
3.  <span data-ttu-id="fc5be-134">在 [輸入選擇]\*\*\*\* 索引標籤的 [選取要用於精確度圖表的資料集]\*\*\*\* 下，選取 [指定不同的資料集]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fc5be-134">In the **Input Selection** tab, under **Select data set to be used for Accuracy Chart**, select **Specify a different data set**.</span></span>  
  
4.  <span data-ttu-id="fc5be-135">按一下 [流覽] 按鈕\*\* ( ...] ) \*\*開啟對話方塊，並建立外部資料集的定義。</span><span class="sxs-lookup"><span data-stu-id="fc5be-135">Click the browse button **(...)** to open a dialog box and build the definition of the external data set.</span></span>  
  
5.  <span data-ttu-id="fc5be-136">在 [選取採礦結構]\*\*\*\* 對話方塊中，選取包含您要使用之模型的採礦結構，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fc5be-136">In the **Select Mining Structure** dialog box, select the mining structure that contains the models you want to work with, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="fc5be-137">在 [採礦精確度圖表]\*\*\*\* 索引標籤的 [選取輸入資料表]\*\*\*\* 資料表上，按一下 [選取案例資料表]\*\*\*\*，即可開啟 [選取資料表]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="fc5be-137">On the **Select Input Table(s)** table of the **Mining Accuracy Chart** tab, click **Select Case Table** to open the **Select Table** dialog box.</span></span>  
  
7.  <span data-ttu-id="fc5be-138">在 **[選取資料表]** 對話方塊中，從 **[資料來源]** 清單裡選取一個資料來源。</span><span class="sxs-lookup"><span data-stu-id="fc5be-138">In the **Select Table** dialog box, select a data source from the **Data Source** list.</span></span> <span data-ttu-id="fc5be-139">選擇含有資料的資料表，而這項資料就是您想要在預測查詢中判斷模型精確度時使用的資料。</span><span class="sxs-lookup"><span data-stu-id="fc5be-139">Choose a table that contains the data that you want to use in the prediction queries to determine the accuracy of the models.</span></span>  
  
8.  <span data-ttu-id="fc5be-140">在 [資料表/檢視表名稱]\*\*\*\* 方塊中，選取包含您要用來測試模型之資料的資料表。</span><span class="sxs-lookup"><span data-stu-id="fc5be-140">In the **Table/View Name** box, select the table that contains the data that you want to use to test the models.</span></span>  
  
9. <span data-ttu-id="fc5be-141">必要時，請編輯對應。</span><span class="sxs-lookup"><span data-stu-id="fc5be-141">Edit the mappings, if necessary.</span></span> <span data-ttu-id="fc5be-142">採礦結構中的資料行會自動對應至輸入資料表中名稱相同的資料行。</span><span class="sxs-lookup"><span data-stu-id="fc5be-142">Columns in the mining structure are automatically mapped to the columns with the same name in the input table.</span></span> <span data-ttu-id="fc5be-143">若要手動建立對應，請按一下 [選取輸入資料表]\*\*\*\* 資料表中的資料行，然後將它拖曳到 [採礦結構]\*\*\*\* 資料表中的對應資料行上。</span><span class="sxs-lookup"><span data-stu-id="fc5be-143">To manually create mappings, click a column in the **Select Input Table(s)** table and drag it onto the corresponding column in the **Mining Structure** table.</span></span> <span data-ttu-id="fc5be-144">若要刪除對應，請按一下將 [採礦結構]\*\*\*\* 資料表中的資料行連結到 [選取輸入資料表]\*\*\*\* 資料表中之對應資料行的線條，然後按下 DELETE 鍵。</span><span class="sxs-lookup"><span data-stu-id="fc5be-144">To delete a mapping, click the line that links the column in the **Mining Structure** table to the mapped column in the **Select Input Table(s)** table, and then press DELETE.</span></span>  
  
10. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="to-modify-the-way-input-data-is-mapped-to-the-model"></a><a name="bkmk_ChangeMappings"></a><span data-ttu-id="fc5be-145">若要修改輸入資料對應至模型的方式</span><span class="sxs-lookup"><span data-stu-id="fc5be-145">To modify the way input data is mapped to the model</span></span>  
  
1.  <span data-ttu-id="fc5be-146">在資料採礦設計師中，按兩下包含您想要繪製之模型的結構。</span><span class="sxs-lookup"><span data-stu-id="fc5be-146">In Data Mining Designer, double-click the structure that contains the models you want to chart.</span></span>  
  
2.  <span data-ttu-id="fc5be-147">選取 **[採礦精確度圖表]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="fc5be-147">Select the **Mining Accuracy Chart** tab.</span></span>  
  
3.  <span data-ttu-id="fc5be-148">按一下 [輸入選擇]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="fc5be-148">Click the **Input Selection** tab.</span></span>  
  
4.  <span data-ttu-id="fc5be-149">在 [**選取要用於精確度圖表的資料集**] 中，選取 [**指定不同的資料集**] 選項。</span><span class="sxs-lookup"><span data-stu-id="fc5be-149">In **Select data set to be used for Accuracy Chart**, select the option **Specify a different data set**.</span></span>  
  
5.  <span data-ttu-id="fc5be-150">按一下 [流覽] 按鈕\*\* ( ...] ) \*\*開啟對話方塊，並建立外部資料源的定義。</span><span class="sxs-lookup"><span data-stu-id="fc5be-150">Click the browse button **(...)** to open a dialog box and build the definition of the external data source.</span></span>  
  
6.  <span data-ttu-id="fc5be-151">在 [指定資料行對應]\*\*\*\* 對話方塊中，按一下 [選取案例資料表]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fc5be-151">In the **Specify Column Mapping** dialog box, click **Select Case Table**.</span></span>  
  
7.  <span data-ttu-id="fc5be-152">在 [選取資料表] 對話方塊中，從清單中選取資料來源檢視，然後選取包含案例資料的資料表。</span><span class="sxs-lookup"><span data-stu-id="fc5be-152">In the Select Table dialog box, Select a data source view from the list, and select the table that contains the case data.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="fc5be-153">如果您需要的資料表無法使用，請關閉此對話方塊，然後建立包含此資料表的新資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="fc5be-153">If the tables you need are not available, close the dialog box and create a new data source view that contains the table.</span></span> <span data-ttu-id="fc5be-154">如需如何建立資料來源檢視的資訊，請參閱[定義資料來源檢視 &#40;Analysis Services&#41;](../multidimensional-models/defining-a-data-source-view-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="fc5be-154">For information about how to create a data source view, see [Defining a Data Source View &#40;Analysis Services&#41;](../multidimensional-models/defining-a-data-source-view-analysis-services.md).</span></span>  
  
9. <span data-ttu-id="fc5be-155">如果採礦模型包含巢狀資料表，請按一下 [選取巢狀資料表]\*\*\*\*，然後從資料來源檢視的資料表清單中選取巢狀資料表。</span><span class="sxs-lookup"><span data-stu-id="fc5be-155">If the mining model contains a nested table, click **Select Nested Table**, and select the nested table from the list of tables in the data source view.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
10. <span data-ttu-id="fc5be-156">選取您要修改之對應的連接線，然後選取 [修改連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fc5be-156">Select the join line of the mapping you want to modify, and select **Modify Connections**.</span></span>  
  
     <span data-ttu-id="fc5be-157">**[修改對應]** 對話方塊會開啟。</span><span class="sxs-lookup"><span data-stu-id="fc5be-157">The **Modify Mapping** dialog box opens.</span></span> <span data-ttu-id="fc5be-158">在此對話方塊的資料表中，[採礦結構資料行]\*\*\*\* 會列出所選取採礦結構包含的每一個資料行，而 [資料表資料行]\*\*\*\* 則會列出輸入資料表中，對應到採礦結構之資料行的資料行。</span><span class="sxs-lookup"><span data-stu-id="fc5be-158">In the table in this dialog box, **Mining Structure Column** lists each column that the selected mining structure contains, and **Table Column** lists the columns from input tables that are mapped to columns in the mining structure.</span></span>  
  
11. <span data-ttu-id="fc5be-159">在 [資料表資料行]\*\*\*\* 之下，選取對應到在 [採礦結構資料行]\*\*\*\* 之下，您要修改關聯性之資料列的資料列。</span><span class="sxs-lookup"><span data-stu-id="fc5be-159">Under **Table Column**, select the row that corresponds to the row under **Mining Structure Column** for which you want to modify a relationship.</span></span> <span data-ttu-id="fc5be-160">從清單中選取新的資料行，或選取清單中的空白項目來刪除資料行。</span><span class="sxs-lookup"><span data-stu-id="fc5be-160">Select a new column from the list, or select the blank entry from the list to delete the column.</span></span>  
  
12. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="fc5be-161">新的資料行對應會顯示在 [指定資料行對應]\*\*\*\* 對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="fc5be-161">The new column mappings are displayed in the **Specify Column Mapping** dialog box.</span></span> <span data-ttu-id="fc5be-162">您可以選取資料行之間的線，然後按 DELETE 鍵來移除對應。</span><span class="sxs-lookup"><span data-stu-id="fc5be-162">You can remove a mapping by selecting the line between the columns and pressing the DELETE key.</span></span> <span data-ttu-id="fc5be-163">您可以在 [採礦結構]\*\*\*\* 資料表中選取資料行，並將它拖曳到 [選取輸入資料表]\*\*\*\* 資料表中的對應資料行，以建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="fc5be-163">You can create a new connection by selecting a column in the **Mining Structure** table and dragging it to the corresponding column in the **SelectInput Table(s)** table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc5be-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc5be-164">See Also</span></span>  
 [<span data-ttu-id="fc5be-165">測試及驗證工作與操作方法 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="fc5be-165">Testing and Validation Tasks and How-tos &#40;Data Mining&#41;</span></span>](testing-and-validation-tasks-and-how-tos-data-mining.md)  
  
  
