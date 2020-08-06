---
title: '[輸入選擇] 索引標籤 () 的 [挖掘精確度圖表視圖] |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.accuracychart.columnmapping.f1
ms.assetid: f8b1193c-5c86-4c7e-8e35-158d293184fa
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3c5e99e5be275dff6e218d172316c612b5ba0c41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596406"
---
# <a name="input-selection-tab-mining-accuracy-chart-view"></a><span data-ttu-id="e9168-102">輸入選取範圍索引標籤 (採礦精確度圖表檢視)</span><span class="sxs-lookup"><span data-stu-id="e9168-102">Input Selection Tab (Mining Accuracy Chart View)</span></span>
  <span data-ttu-id="e9168-103">使用 [採礦精確度圖表]\*\*\*\* 設計師的 [輸入選擇]\*\*\*\* 索引標籤可以指定用於測試模型及建立精確度圖表的資料來源。</span><span class="sxs-lookup"><span data-stu-id="e9168-103">Use the **Input Selection** tab of the **Mining Accuracy Chart** designer to specify the source of the data that is used to test the model and build the accuracy chart.</span></span>  
  
 <span data-ttu-id="e9168-104">**如需詳細資訊，請參閱：** [測試和驗證 &#40;資料採礦&#41;](data-mining/testing-and-validation-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="e9168-104">**For more information:** [Testing and Validation &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="e9168-105">選項</span><span class="sxs-lookup"><span data-stu-id="e9168-105">Options</span></span>  
 <span data-ttu-id="e9168-106">**同步處理預測**  **資料行和值**</span><span class="sxs-lookup"><span data-stu-id="e9168-106">**Synchronize Prediction**  **Columns and Values**</span></span>  
 <span data-ttu-id="e9168-107">選取即可協調方格中的可預測屬性，使得即使它們具有不同的名稱，仍會在模型定型期間，從相同可預測採礦結構資料行中衍生而來。</span><span class="sxs-lookup"><span data-stu-id="e9168-107">Select to coordinate the predictable attributes in the grid so that, even if they have a different name, they are derived from the same predictable mining structure column during model training.</span></span>  
  
 <span data-ttu-id="e9168-108">**注意** ：預設會選取此選項。</span><span class="sxs-lookup"><span data-stu-id="e9168-108">**Note** This option is selected by default.</span></span> <span data-ttu-id="e9168-109">唯有在知道兩個採礦結構資料行都衍生自相同的基礎關聯式或多維度來源的情況下，以及這些資料行具有相同的狀態或分隔的情況下，才應清除此方塊。</span><span class="sxs-lookup"><span data-stu-id="e9168-109">You should only clear this box for cases in which you know that two mining structure columns derive from the same underlying relational or multi-dimensional source, and that the columns contain the same states or have been discretized in the same way.</span></span>  
  
 <span data-ttu-id="e9168-110">**選取可預測的採礦模型資料行，以顯示在增益圖中**</span><span class="sxs-lookup"><span data-stu-id="e9168-110">**Select predictable mining model columns to show in the lift chart**</span></span>  
 <span data-ttu-id="e9168-111">方格包含用來控制將哪些模型包含在增益圖中，以及增益圖如何使用它們的資料行。</span><span class="sxs-lookup"><span data-stu-id="e9168-111">A grid that contains columns to control which models are included in the lift chart and how they are used in the lift chart.</span></span>  
  
|<span data-ttu-id="e9168-112">值</span><span class="sxs-lookup"><span data-stu-id="e9168-112">Value</span></span>|<span data-ttu-id="e9168-113">描述</span><span class="sxs-lookup"><span data-stu-id="e9168-113">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e9168-114">**顯示**</span><span class="sxs-lookup"><span data-stu-id="e9168-114">**Show**</span></span>|<span data-ttu-id="e9168-115">在要顯示在圖表中的採礦模型中，選取每個可預測資料行名稱旁的方塊。</span><span class="sxs-lookup"><span data-stu-id="e9168-115">Select the box next to the name of each predictable column in the mining model that you want to display in the chart.</span></span><br /><br /> <span data-ttu-id="e9168-116">如果圖表過於複雜而無法輕鬆檢視，請清除一或多個資料行旁的方塊以簡化圖表。</span><span class="sxs-lookup"><span data-stu-id="e9168-116">If the chart is too complex to view easily, clear the box next to one or more columns to simplify the chart.</span></span><br /><br /> <span data-ttu-id="e9168-117">注意︰除非至少選取一個資料行，否則將無法建立精確度圖表。</span><span class="sxs-lookup"><span data-stu-id="e9168-117">Note: You cannot create an accuracy chart unless at least one column is selected.</span></span>|  
|<span data-ttu-id="e9168-118">**採礦模型**</span><span class="sxs-lookup"><span data-stu-id="e9168-118">**Mining Model**</span></span>|<span data-ttu-id="e9168-119">列出採礦結構內所包含的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="e9168-119">Lists the mining models that are contained in the mining structure.</span></span>|  
|<span data-ttu-id="e9168-120">**可預測資料行名稱**</span><span class="sxs-lookup"><span data-stu-id="e9168-120">**Predictable Column Name**</span></span>|<span data-ttu-id="e9168-121">選取採礦模型內所包含之用來建立增益圖的可預測資料行。</span><span class="sxs-lookup"><span data-stu-id="e9168-121">Select a predictable column that is contained in the mining models that are used to create the lift chart.</span></span>|  
|<span data-ttu-id="e9168-122">**預測值**</span><span class="sxs-lookup"><span data-stu-id="e9168-122">**Predict Value**</span></span>|<span data-ttu-id="e9168-123">選取可預測資料行的值。</span><span class="sxs-lookup"><span data-stu-id="e9168-123">Select a value for the predictable column.</span></span> <span data-ttu-id="e9168-124">如果您將此保留空白，增益圖就會針對可預測資料行的所有狀態，預測模型的執行效益。</span><span class="sxs-lookup"><span data-stu-id="e9168-124">If you leave this blank, the lift chart predicts how well the model performs for all states of the predictable column.</span></span>|  
  
 <span data-ttu-id="e9168-125">**選取要用於精確度圖表的資料集**</span><span class="sxs-lookup"><span data-stu-id="e9168-125">**Select data set to be used for Accuracy Chart**</span></span>  
 <span data-ttu-id="e9168-126">包含用來指定精確度測試資料之三個選項的選項群組。</span><span class="sxs-lookup"><span data-stu-id="e9168-126">An option group that contains three options for specifying accuracy test data.</span></span>  
  
|<span data-ttu-id="e9168-127">值</span><span class="sxs-lookup"><span data-stu-id="e9168-127">Value</span></span>|<span data-ttu-id="e9168-128">描述</span><span class="sxs-lookup"><span data-stu-id="e9168-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e9168-129">**使用採礦模型測試案例**</span><span class="sxs-lookup"><span data-stu-id="e9168-129">**Use mining model test cases**</span></span>|<span data-ttu-id="e9168-130">使用在對採礦結構進行資料分割時所建立的測試集，並套用定義於模型的篩選。</span><span class="sxs-lookup"><span data-stu-id="e9168-130">Use the testing set that was created when you partitioned the mining structure, and apply the filter that is defined on the model.</span></span> <span data-ttu-id="e9168-131">如需模型篩選的相關資訊，請參閱 [Filters for Mining Models &#40;Analysis Services - Data Mining&#41;](data-mining/mining-models-analysis-services-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="e9168-131">For information about model filters, see [Filters for Mining Models &#40;Analysis Services - Data Mining&#41;](data-mining/mining-models-analysis-services-data-mining.md)</span></span>|  
|<span data-ttu-id="e9168-132">**使用採礦結構測試案例**</span><span class="sxs-lookup"><span data-stu-id="e9168-132">**Use mining structure test cases**</span></span>|<span data-ttu-id="e9168-133">使用在對採礦結構進行資料分割時所建立的測試集。</span><span class="sxs-lookup"><span data-stu-id="e9168-133">Use the testing set that was created when you partitioned the mining structure.</span></span>|  
|<span data-ttu-id="e9168-134">**指定不同的資料集**</span><span class="sxs-lookup"><span data-stu-id="e9168-134">**Specify a different data set**</span></span>|<span data-ttu-id="e9168-135">從現有的資料來源檢視指定用來當做測試資料集的資料表。</span><span class="sxs-lookup"><span data-stu-id="e9168-135">Specify a table from an existing data source view to use as a test data set.</span></span>|  
  
## <a name="filtering-options"></a><span data-ttu-id="e9168-136">篩選選項</span><span class="sxs-lookup"><span data-stu-id="e9168-136">Filtering Options</span></span>  
 <span data-ttu-id="e9168-137">如果選取 [指定不同的資料集]\*\*\*\* 選項，就可以定義資料來源檢視並建立套用至該資料的篩選。</span><span class="sxs-lookup"><span data-stu-id="e9168-137">If you select the option **Specify a different data set**, you can define a data source view and create filters to apply to that data.</span></span> <span data-ttu-id="e9168-138">在建立篩選時，您是在查詢中建立會從資料來源檢視傳回測試資料的 WHERE 子句。</span><span class="sxs-lookup"><span data-stu-id="e9168-138">When you create a filter, you are creating a WHERE clause in the query that returns the test data from the data source view.</span></span>  
  
 <span data-ttu-id="e9168-139">**注意**您不能使用 [**輸入選擇**] 索引標籤，在「採礦模型」上指定篩選。若要建立模型篩選，請按一下 [**採礦模型**] 索引標籤，然後編輯模型屬性。</span><span class="sxs-lookup"><span data-stu-id="e9168-139">**Note** You cannot specify a filter on the mining model by using the **Input Selection** tab. To create a model filter, click the **Mining Models** tab and edit the model properties.</span></span>  
  
 <span data-ttu-id="e9168-140">如果沒有建立鑑效組集來測試何時建立了採礦結構，則可以選取此選項，然後將原始資料來源檢視指定為測試集。</span><span class="sxs-lookup"><span data-stu-id="e9168-140">If you did not create a holdout set for testing when you created the mining structure, you can select this option and then specify the original data source view as a test set.</span></span> <span data-ttu-id="e9168-141">您也可以使用這個解決方法在原始資料集上設定篩選。</span><span class="sxs-lookup"><span data-stu-id="e9168-141">By using  this workaround, you can also set filters on the original data set.</span></span>  
  
 <span data-ttu-id="e9168-142">**指定資料行對應**</span><span class="sxs-lookup"><span data-stu-id="e9168-142">**Specify Column Mapping**</span></span>  
 <span data-ttu-id="e9168-143">開啟 [指定資料行對應]\*\*\*\* 對話方塊，您可從中選取資料來源、指定案例及巢狀資料表，並且將外部資料行對應至採礦結構資料行。</span><span class="sxs-lookup"><span data-stu-id="e9168-143">Opens the **Specify Column Mapping** dialog box, where you select the data source, specify case and nested tables, and map external data columns to the mining structure columns.</span></span>  
  
 <span data-ttu-id="e9168-144">如需詳細資訊，請參閱[指定資料行對應對話方塊 &#40;採礦精確度圖表&#41;](specify-column-mapping-dialog-box-mining-accuracy-chart.md)。</span><span class="sxs-lookup"><span data-stu-id="e9168-144">For more information, see [Specify Column Mapping Dialog Box &#40;Mining Accuracy Chart&#41;](specify-column-mapping-dialog-box-mining-accuracy-chart.md).</span></span>  
  
 <span data-ttu-id="e9168-145">**篩選運算式**</span><span class="sxs-lookup"><span data-stu-id="e9168-145">**Filter Expression**</span></span>  
 <span data-ttu-id="e9168-146">顯示使用篩選編輯器所建立的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="e9168-146">Displays the filter condition that you built by using the filter editors.</span></span>  
  
 <span data-ttu-id="e9168-147">**開啟篩選編輯器**</span><span class="sxs-lookup"><span data-stu-id="e9168-147">**Open Filter Editor**</span></span>  
 <span data-ttu-id="e9168-148">開啟 [資料集篩選器]\*\*\*\* 對話方塊 (可用來選取外部資料表，並在案例資料表資料行上設定條件) 及 [篩選]\*\*\*\* 對話方塊 (可協助您建立條件以套用至選取的資料表中的個別資料行或巢狀資料表中的資料行)。</span><span class="sxs-lookup"><span data-stu-id="e9168-148">Opens the **Data Set Filter** dialog box, which lets you select external tables, and set conditions on case table columns, and the **Filter** dialog box, which helps you build conditions that apply to individual columns in the selected table, or to columns in nested tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9168-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9168-149">See Also</span></span>  
 <span data-ttu-id="e9168-150">[測試和驗證工作，以及如何 &#40;資料採礦&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="e9168-150">[Testing and Validation Tasks and How-tos &#40;Data Mining&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span></span>  
 <span data-ttu-id="e9168-151">[&#40;資料採礦&#41;的挖掘精確度圖表設計工具](mining-accuracy-chart-designer-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="e9168-151">[Mining Accuracy Chart Designer &#40;Data Mining&#41;](mining-accuracy-chart-designer-data-mining.md) </span></span>  
 <span data-ttu-id="e9168-152">[將篩選套用至採礦模型](data-mining/apply-a-filter-to-a-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="e9168-152">[Apply a Filter to a Mining Model](data-mining/apply-a-filter-to-a-mining-model.md) </span></span>  
 [<span data-ttu-id="e9168-153">採礦模型的篩選 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="e9168-153">Filters for Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](data-mining/mining-models-analysis-services-data-mining.md)  
  
  
