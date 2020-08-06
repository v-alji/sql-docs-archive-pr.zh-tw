---
title: 建立新的 OLAP 採礦結構 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], OLAP
- mining structures [Analysis Services], creating
- OLAP [Analysis Services], mining models
ms.assetid: 368f4273-a016-4748-bcb6-505a3e745af3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2851fe6180254b129471c442297c419fd594e123
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686539"
---
# <a name="create-a-new-olap-mining-structure"></a><span data-ttu-id="fbcb0-102">建立新的 OLAP 採礦結構</span><span class="sxs-lookup"><span data-stu-id="fbcb0-102">Create a New OLAP Mining Structure</span></span>
  <span data-ttu-id="fbcb0-103">您可以使用中的資料採礦嚮導 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，建立使用多維度模型資料的採礦結構。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-103">You can use the Data Mining Wizard in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to create a mining structure that uses data from a multidimensional model.</span></span> <span data-ttu-id="fbcb0-104">以 OLAP Cube 為基礎的採礦模型可以使用事實資料表、維度和量值群組中的資料行和值做為分析屬性。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-104">Mining models that are based on OLAP cubes can use the column and values in fact tables, dimensions, and measure groups as attributes for analysis.</span></span>  
  
### <a name="to-create-a-new-olap-mining-structure"></a><span data-ttu-id="fbcb0-105">若要建立新的 OLAP 採礦結構</span><span class="sxs-lookup"><span data-stu-id="fbcb0-105">To create a new OLAP mining structure</span></span>  
  
1.  <span data-ttu-id="fbcb0-106">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 的方案總管中，以滑鼠右鍵按一下 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案中的 [採礦結構]\*\*\*\* 資料夾，然後按一下 [新增採礦結構]\*\*\*\* 開啟 [資料採礦精靈]。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-106">In Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], right-click the **Mining Structures** folder in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, and then click **New Mining Structure** to open the Data Mining Wizard.</span></span>  
  
2.  <span data-ttu-id="fbcb0-107">在 **[歡迎使用資料採礦精靈]** 頁面上，按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-107">On the **Welcome to the Data Mining Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="fbcb0-108">在 **[選取定義方法]** 頁面上，選取 **[從現有的 Cube]**，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-108">On the **Select the Definition Method** page, select **From existing cube**, and then click **Next**.</span></span>  
  
     <span data-ttu-id="fbcb0-109">如果出現錯誤訊息：「無法擷取支援的資料採礦演算法的清單」，請開啟 [專案屬性]\*\*\*\* 對話方塊，確認您已經指定支援多維度模型的 Analysis Services 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-109">If you get an error with the message, Unable to retrieve a list of supported data mining algorithms, open the **Project Properties** dialog box and verify that you have specified the name of an Analysis Services instance that supports multidimensional models.</span></span> <span data-ttu-id="fbcb0-110">不能在支援表格式模型的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體上建立採礦模型。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-110">You cannot create mining models on an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that supports tabular modeling.</span></span>  
  
4.  <span data-ttu-id="fbcb0-111">在 **[建立資料採礦結構]** 頁面上，決定只要建立採礦結構，還是建立採礦結構再加上一個相關的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-111">On the **Create the Data Mining Structure** page, decide whether you will create a mining structure only, or a mining structure plus one related mining model.</span></span> <span data-ttu-id="fbcb0-112">通常，同時建立採礦模型比較容易，因為這樣系統會提示您包含必要的資料行。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-112">Generally it is easier to create a mining model at the same time, so that you can be prompted to include necessary columns.</span></span>  
  
     <span data-ttu-id="fbcb0-113">如果您要建立採礦模型，請選取您想要使用的資料採礦演算法，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-113">If you will create a mining model, select the data mining algorithm that you want to use, and then click **Next**.</span></span> <span data-ttu-id="fbcb0-114">如需如何選擇演算法的詳細資訊，請參閱[資料採礦演算法 &#40;Analysis Services - 資料採礦&#41;](data-mining-algorithms-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-114">For more information about how to choose an algorithm, see [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md).</span></span>  
  
5.  <span data-ttu-id="fbcb0-115">在 **[選取來源 Cube 維度]** 頁面的 **[選取來源 Cube 維度]** 之下，找出包含多數案例資料的維度。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-115">On the **Select the Source Cube Dimension** page, under **Select a Source Cube Dimension**, locate the dimension that contains the majority of your case data.</span></span>  
  
     <span data-ttu-id="fbcb0-116">例如，如果您嘗試識別客戶群組，可以選擇 [Customer] 維度；如果您嘗試分析跨多筆交易的購買行為，可以選擇 [Internet Sales Order Details] 維度。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-116">For example, if you are trying to identify customer groupings, you might choose the Customer dimension; if you are trying to analyze purchases across transactions, you might choose the Internet Sales Order Details dimension.</span></span> <span data-ttu-id="fbcb0-117">不限制您只能使用此維度中的資料，但該維度應該包含要在分析中使用的重要屬性。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-117">You are not restricted to using only the data in this dimension, but it should contain important attributes to use in analysis.</span></span>  
  
     <span data-ttu-id="fbcb0-118">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-118">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="fbcb0-119">在 **[選取案例索引鍵]** 頁面的 **[屬性]** 之下，選取將成為採礦結構之索引鍵的屬性，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-119">On the **Select the Case Key** page, under **Attributes**, select the attribute that will be the key of the mining structure, and then click **Next**.</span></span>  
  
     <span data-ttu-id="fbcb0-120">通常，做為採礦結構之索引鍵的屬性也是維度的索引鍵，並且會預先選取。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-120">Typically the attribute that you use as key for the mining structure is also a key for the dimension and will be pre-selected.</span></span>  
  
7.  <span data-ttu-id="fbcb0-121">在 **[選取案例層級資料行]** 頁面的 **[相關的屬性和量值]** 之下，選取其值要加入至採礦結構中做為案例資料的屬性和量值。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-121">On the **Select Case Level Columns** page, under **Related Attributes and Measures**, select the attributes and measures that contain values you want to add to the mining structure as case data.</span></span> <span data-ttu-id="fbcb0-122">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-122">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="fbcb0-123">在 **[指定採礦模型資料行使用方式]** 頁面的 **[採礦模型結構]** 之下，先設定可預測資料行，然後選擇要做為輸入的資料行。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-123">On the **Specify Mining Model Column Usage** page, under **Mining model structure**, first set the predictable column, and then choose columns to use as inputs.</span></span>  
  
    -   <span data-ttu-id="fbcb0-124">選取最左邊資料行的核取方塊，將資料包含在採礦結構中。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-124">Select the checkbox in the leftmost column to include the data in the mining structure.</span></span> <span data-ttu-id="fbcb0-125">您可以在結構中包含僅供參考但不用於分析的資料行。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-125">You can include columns in the structure that you will use for reference, but not use them for analysis.</span></span>  
  
    -   <span data-ttu-id="fbcb0-126">選取 **[輸入]** 資料行的核取方塊，將屬性做為分析中的變數。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-126">Select the checkbox in the **Input** column to use the attribute as a variable in analysis.</span></span>  
  
    -   <span data-ttu-id="fbcb0-127">選取 **[預測]** 資料行的核取方塊，只做為可預測屬性。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-127">Select the checkbox in the **Predict** column only for predictable attributes.</span></span>  
  
     <span data-ttu-id="fbcb0-128">請注意，已指定為索引鍵的資料行不能用於輸入或預測。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-128">Note that columns you have designated as keys cannot be used for input or prediction.</span></span>  
  
     <span data-ttu-id="fbcb0-129">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-129">Click **Next**.</span></span>  
  
9. <span data-ttu-id="fbcb0-130">在 **[指定採礦模型資料行使用方式]** 頁面上，您也可以使用 **[加入巢狀資料表]** 和 **[移除巢狀資料表]**，對採礦結構新增及移除巢狀資料表。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-130">On the **Specify Mining Model Column Usage** page, you can also add and remove nested tables to the mining structure, using **Add Nested Tables** and **Nested Tables**.</span></span>  
  
     <span data-ttu-id="fbcb0-131">在 OLAP 採礦模型中，巢狀資料表是 Cube 中與表示案例屬性的維度具有一對多關聯性的另一組資料。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-131">In an OLAP mining model, a nested table is another set of data within the cube that has a one-to-many relationship with the dimension that represents the case attributes.</span></span> <span data-ttu-id="fbcb0-132">因此，在對話方塊開啟時，它會預先選取已經與您選定為案例資料表的維度相關的量值群組。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-132">Therefore, when the dialog box opens, it pre-selects measure groups that are already related to the dimension you selected as the case table.</span></span> <span data-ttu-id="fbcb0-133">此時，您可以選擇包含可用於分析之附加資訊的其他維度。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-133">At this point, you would choose a different dimension that contains additional information useful for analysis.</span></span>  
  
     <span data-ttu-id="fbcb0-134">例如，如果您要分析客戶，可以使用 [Customer] 維度作為案例資料表。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-134">For example, if you are analyzing customers, you would use the [Customer] dimension as the case table.</span></span> <span data-ttu-id="fbcb0-135">對於巢狀資料表，您可以加入客戶在購買時陳述的原因，該原因包含在 [Sales Reason] 維度中。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-135">For the nested table, you might add the reason customers cited when making a purchase, which is included in the [Sales Reason] dimension.</span></span>  
  
     <span data-ttu-id="fbcb0-136">如果您新增巢狀資料，則必須多指定兩個資料行：</span><span class="sxs-lookup"><span data-stu-id="fbcb0-136">If you add nested data, you must specify two additional columns:</span></span>  
  
    -   <span data-ttu-id="fbcb0-137">巢狀資料表的索引鍵：這應該在 [選取巢狀資料表索引鍵]\*\*\*\* 頁面上預先選取。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-137">The key of the nested table: This should be pre-selected on the page, **Select Nested Table Key**.</span></span>  
  
    -   <span data-ttu-id="fbcb0-138">用於分析的屬性： **[選取巢狀資料表資料行]** 頁面提供巢狀資料表選取範圍的量值和屬性清單。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-138">The attributes or attributes to use for analysis: The page, **Select Nested Table Columns**, provides a list of measures and attributes in the nested table selection.</span></span>  
  
        -   <span data-ttu-id="fbcb0-139">對於要包含在模型中的每個屬性，請選取左側資料行的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-139">For each attribute that you include in the model, check the box in the left column.</span></span>  
  
        -   <span data-ttu-id="fbcb0-140">如果您要屬性只做為分析之用，請核取 **[輸入]**。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-140">If you want to use the attribute for analysis only, check **Input**.</span></span>  
  
        -   <span data-ttu-id="fbcb0-141">如果您想要將資料行包含在模型中做為其中一個可預測屬性，請選取 **[預測]**。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-141">If you want to include the column as one of the predictable attributes for the model, select **Predict**.</span></span>  
  
        -   <span data-ttu-id="fbcb0-142">包含在結構中、但未指定為輸入或可預測屬性的任何項目，在新增至結構中時會標示 `Ignore`；這表示在建立模型時會處理此資料，但資料不用於分析，只供鑽研使用。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-142">Any item that you include in the structure but do not specify as an input or predictable attribute is added to the structure with the flag `Ignore`; this means that the data is processed when you build the model but is not used in analysis, and is available only for drillthrough.</span></span> <span data-ttu-id="fbcb0-143">如果您想要包含客戶名稱之類的詳細資料，但不想在分析中使用它們，這項功能就很方便。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-143">This can be handy if you want to include details such as customer names but don't want to use them in analysis.</span></span>  
  
     <span data-ttu-id="fbcb0-144">按一下 **[完成]** 關閉處理巢狀資料表的精靈部分。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-144">Click **Finish** to close the part of the wizard that works with nested tables.</span></span> <span data-ttu-id="fbcb0-145">您可以重複此程序，新增多個巢狀資料行。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-145">You can repeat the process to add multiple nested columns.</span></span>  
  
10. <span data-ttu-id="fbcb0-146">在 **[指定資料行的內容和資料類型]** 頁面的 **[採礦模型結構]** 之下，設定每一個資料行的內容類型和資料類型。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-146">On the **Specify Columns' Content and Data Type** page, under **Mining model structure**, set the content type and data type for each column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fbcb0-147"> OLAP 採礦模型不支援使用 **[偵測]** 功能，來自動偵測資料行是否包含連續資料或分隔資料。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-147">OLAP mining models do not support using the **Detect** feature to automatically detect whether a column contains continuous or discrete data.</span></span>  
  
     <span data-ttu-id="fbcb0-148">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-148">Click **Next**.</span></span>  
  
11. <span data-ttu-id="fbcb0-149">在 **[配量來源 Cube]** 頁面上，您可以篩選用來建立採礦結構的資料。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-149">On the **Slice Source Cube** page, you can filter the data that is used to create the mining structure.</span></span>  
  
     <span data-ttu-id="fbcb0-150">配量 Cube 可讓您限制用來建立模型的資料。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-150">Slicing the cube lets you restrict the data that is used to build the model.</span></span> <span data-ttu-id="fbcb0-151">例如，您可以透過對 [Geography] 階層和下列項目進行配量，為每個地區建立不同的模型。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-151">For example, you could build separate models for each region by slicing on the Geography hierarchy and</span></span>  
  
    -   <span data-ttu-id="fbcb0-152">**維度**：從下拉式清單中選擇相關維度。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-152">**Dimension**: Choose a related dimension from the dropdown list.</span></span>  
  
    -   <span data-ttu-id="fbcb0-153">**階層**：選取要套用篩選的維度階層層級。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-153">**Hierarchy**:  Select the level of the dimension hierarchy at which you want to apply the filter.</span></span> <span data-ttu-id="fbcb0-154">例如，如果您依 [Geography] 維度進行配量，則可以選擇階層層級，例如 [Region Country Name]。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-154">For example, if you are slicing by the [Geography] dimension, you would choose a hierarchy level such as [Region Country Name] .</span></span>  
  
    -   <span data-ttu-id="fbcb0-155">**運算子**：從清單選取運算子。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-155">**Operator**: Choose an operator from the list.</span></span>  
  
    -   <span data-ttu-id="fbcb0-156">**篩選運算式**：輸入要做為篩選條件的值或運算式，或者使用下拉式清單，從指定之階層層級的成員清單中選取一個值</span><span class="sxs-lookup"><span data-stu-id="fbcb0-156">**Filter Expression**: Type a value or expression to serve as the filter condition, or use the dropdown list to select a value from the list of members at the specified level of the hierarchy.</span></span>  
  
         <span data-ttu-id="fbcb0-157">例如，如果您選取 [Geography] 做為維度，並將 [Region Country Name] 做為階層層級，則下拉式清單會包含可做為篩選準則的所有有效國家/地區。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-157">For example, if you selected [Geography] as the dimension and [Region Country Name] as the hierarchy level, the dropdown list contains all the valid countries/regions that you can use as a filter condition.</span></span> <span data-ttu-id="fbcb0-158">您可以複選。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-158">You can make multiple selections.</span></span> <span data-ttu-id="fbcb0-159">因此，採礦結構中的資料會限制為來自這些地域的 Cube 資料。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-159">As a result, the data in the mining structure will be limited to cube data from these geographical areas.</span></span>  
  
    -   <span data-ttu-id="fbcb0-160">**參數**：忽略此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-160">**Parameters**: Ignore this check box.</span></span> <span data-ttu-id="fbcb0-161">此對話方塊支援多個 Cube 篩選案例，而此選項與建立採礦結構無關。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-161">This dialog box supports multiple cube filtering scenarios and this option is not relevant to building a mining structure.</span></span>  
  
     <span data-ttu-id="fbcb0-162">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-162">Click **Next**.</span></span>  
  
12. <span data-ttu-id="fbcb0-163">在 **[將資料分割成定型集和測試集]** 頁面上，指定要保留供測試的採礦結構資料百分比，或指定測試案例的最大數目。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-163">On the **Split data into training and testing sets** page, specify a percentage of the mining structure data to reserve for testing, or specify the maximum number of test cases.</span></span> <span data-ttu-id="fbcb0-164">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-164">Click **Next**.</span></span>  
  
     <span data-ttu-id="fbcb0-165">如果您指定了這兩個值，就會結合這些限制，以便使用最低的值。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-165">If you specify both values, the limits are combined to use whichever is lowest.</span></span>  
  
13. <span data-ttu-id="fbcb0-166">在 **[正在完成精靈]** 頁面上，為新的 OLAP 採礦結構和初始採礦模型提供名稱。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-166">On the **Completing the Wizard** page, provide a name for the new OLAP mining structure and the initial mining model.</span></span>  
  
14. <span data-ttu-id="fbcb0-167">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-167">Click **Finish**.</span></span>  
  
15. <span data-ttu-id="fbcb0-168">在 [正在完成精靈]\*\*\*\* 頁面上，您也可以選擇建立採礦模型維度和/或使用採礦模型維度的 Cube。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-168">On the **Completing the Wizard** page, you also have the option to create a mining model dimension and/or a cube using the mining model dimension.</span></span> <span data-ttu-id="fbcb0-169">只有使用下列演算法建立的模型才支援這些選項：</span><span class="sxs-lookup"><span data-stu-id="fbcb0-169">These options are supported only for models built using the following algorithms:</span></span>  
  
    -   <span data-ttu-id="fbcb0-170">Microsoft 叢集演算法</span><span class="sxs-lookup"><span data-stu-id="fbcb0-170">Microsoft Clustering algorithm</span></span>  
  
    -   <span data-ttu-id="fbcb0-171">Microsoft 決策樹演算法</span><span class="sxs-lookup"><span data-stu-id="fbcb0-171">Microsoft Decision Trees algorithm</span></span>  
  
    -   <span data-ttu-id="fbcb0-172">Microsoft 關聯規則演算法</span><span class="sxs-lookup"><span data-stu-id="fbcb0-172">Microsoft Association Rules algorithm</span></span>  
  
     <span data-ttu-id="fbcb0-173">**建立採礦模型維度**：選取此核取方塊，並提供採礦模型維度的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-173">**Create mining model dimension**: Select this check box and provide a type name for the mining model dimension.</span></span> <span data-ttu-id="fbcb0-174">當您使用此選項時，會在用於建立採礦結構的原始 Cube 內建立新維度。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-174">When you use this option, a new dimension is created within the original cube that was used to build the mining structure.</span></span> <span data-ttu-id="fbcb0-175">您可以使用此維度向下鑽研和執行進一步的分析。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-175">You can use this dimension to drill down and conduct further analysis.</span></span> <span data-ttu-id="fbcb0-176">因為該維度位於 Cube 內，所以該維度會自動對應至案例資料維度。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-176">Because the dimension is located within the cube, the dimension is automatically mapped to the case data dimension.</span></span>  
  
     <span data-ttu-id="fbcb0-177">**使用採礦模型維度建立 Cube**：選取此核取方塊，並提供新 Cube 的名稱。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-177">**Create cube using mining model dimension**: Select this check box, and provide a name for the new cube.</span></span> <span data-ttu-id="fbcb0-178">當您使用此選項時，所建立的新 Cube 同時會包含建立結構所使用的現有維度，以及包含模型結果的新資料採礦維度。</span><span class="sxs-lookup"><span data-stu-id="fbcb0-178">When you use this option, a new cube is created that contains both the existing dimensions that were used in building the structure, and the new data mining dimension that contains the results from the model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbcb0-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbcb0-179">See Also</span></span>  
 [<span data-ttu-id="fbcb0-180">採礦結構工作和使用說明</span><span class="sxs-lookup"><span data-stu-id="fbcb0-180">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)  
