---
title: 定義匯出成員 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 07f13e1c-0b20-4f9e-ad62-c438983f2785
author: minewiskan
ms.author: owend
ms.openlocfilehash: f2a054356613ebf3d4cf825c1fa4c238a5362ec3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594787"
---
# <a name="defining-calculated-members"></a><span data-ttu-id="94d70-102">定義導出成員</span><span class="sxs-lookup"><span data-stu-id="94d70-102">Defining Calculated Members</span></span>
  <span data-ttu-id="94d70-103">導出成員是根據 Cube 資料、算術運算子、數字和函數組合所定義的維度成員或量值群組成員。</span><span class="sxs-lookup"><span data-stu-id="94d70-103">Calculated members are members of a dimension or a measure group that are defined based on a combination of cube data, arithmetic operators, numbers, and functions.</span></span> <span data-ttu-id="94d70-104">例如，您可以建立一個導出成員，計算 Cube 中兩個實體量值的總和。</span><span class="sxs-lookup"><span data-stu-id="94d70-104">For example, you can create a calculated member that calculates the sum of two physical measures in the cube.</span></span> <span data-ttu-id="94d70-105">導出成員定義是儲存在 Cube 中，但其值是在查詢時計算。</span><span class="sxs-lookup"><span data-stu-id="94d70-105">Calculated member definitions are stored in cubes, but their values are calculated at query time.</span></span>  
  
 <span data-ttu-id="94d70-106">若要建立導出成員，請在 Cube 設計師的 [計算]\*\*\*\* 索引標籤上使用 [新增導出成員]\*\*\*\* 命令。</span><span class="sxs-lookup"><span data-stu-id="94d70-106">To create a calculated member, use the **New Calculated Member** command on the **Calculations** tab of Cube Designer.</span></span> <span data-ttu-id="94d70-107">您可以在任何維度 (包括量值維度) 內建立導出成員，</span><span class="sxs-lookup"><span data-stu-id="94d70-107">You can create a calculated member within any dimension, including the measures dimension.</span></span> <span data-ttu-id="94d70-108">也可以在 [計算屬性]\*\*\*\* 對話方塊中的顯示資料夾內放置導出成員。</span><span class="sxs-lookup"><span data-stu-id="94d70-108">You can also place a calculated member within a display folder in the **Calculation Properties** dialog box.</span></span> <span data-ttu-id="94d70-109">如需詳細資訊，請參閱 [計算](multidimensional-models-olap-logical-cube-objects/calculations.md)、 [多維度模型中的計算](multidimensional-models/calculations-in-multidimensional-models.md)和 [建立導出成員](multidimensional-models/create-calculated-members.md)。</span><span class="sxs-lookup"><span data-stu-id="94d70-109">For more information, see [Calculations](multidimensional-models-olap-logical-cube-objects/calculations.md), [Calculations in Multidimensional Models](multidimensional-models/calculations-in-multidimensional-models.md), and [Create Calculated Members](multidimensional-models/create-calculated-members.md).</span></span>  
  
 <span data-ttu-id="94d70-110">在本主題的工作中，您要定義導出成員，讓使用者檢視網際網路銷售、轉售商銷售和所有銷售的毛利率百分比和銷售比率。</span><span class="sxs-lookup"><span data-stu-id="94d70-110">In the tasks in this topic, you define calculated measures to let users view the gross profit margin percentage and sales ratios for Internet sales, reseller sales, and for all sales.</span></span>  
  
## <a name="defining-calculations-to-aggregate-physical-measures"></a><span data-ttu-id="94d70-111">將計算定義為彙總實體量值</span><span class="sxs-lookup"><span data-stu-id="94d70-111">Defining Calculations to Aggregate Physical Measures</span></span>  
  
1.  <span data-ttu-id="94d70-112">開啟適用於 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube 的 Cube 設計師，然後按一下 [計算]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="94d70-112">Open Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Calculations** tab.</span></span>  
  
     <span data-ttu-id="94d70-113">請注意 [計算運算式]\*\*\*\* 窗格和 [指令碼組合管理]\*\*\*\* 窗格中的預設 CALCULATE 命令。</span><span class="sxs-lookup"><span data-stu-id="94d70-113">Notice the default CALCULATE command in the **Calculation Expressions** pane and in the **Script Organizer** pane.</span></span> <span data-ttu-id="94d70-114">這個命令會指定 Cube 中的量值，根據其 AggregateFunction 屬性所指定的值加以彙總。</span><span class="sxs-lookup"><span data-stu-id="94d70-114">This command specifies that the measures in the cube should be aggregated according to the value that is specified by their AggregateFunction properties.</span></span> <span data-ttu-id="94d70-115">量值是以一般方式加總，不過也可以用其他方式計算或彙總。</span><span class="sxs-lookup"><span data-stu-id="94d70-115">Measure values are generally summed, but may also be counted or aggregated in some other manner.</span></span>  
  
     <span data-ttu-id="94d70-116">下圖顯示 Cube 設計師的 [計算]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="94d70-116">The following image shows the **Calculations** tab of Cube Designer.</span></span>  
  
     <span data-ttu-id="94d70-117">![Cube 設計師的計算索引標籤](../../2014/tutorials/media/l6-calculatedmembers-1.gif "Cube 設計師的計算索引標籤")</span><span class="sxs-lookup"><span data-stu-id="94d70-117">![Calculations tab of Cube Designer](../../2014/tutorials/media/l6-calculatedmembers-1.gif "Calculations tab of Cube Designer")</span></span>  
  
2.  <span data-ttu-id="94d70-118">在 [計算]\*\*\*\* 索引標籤的工具列上，按一下 [新增導出成員]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94d70-118">On the toolbar of the **Calculations** tab, click **New Calculated Member**.</span></span>  
  
     <span data-ttu-id="94d70-119">[計算運算式]\*\*\*\* 窗格即會出現新的表單，您可在該窗格中定義這個新導出成員的屬性。</span><span class="sxs-lookup"><span data-stu-id="94d70-119">A new form appears in the **Calculation Expressions** pane within which you define the properties of this new calculated member.</span></span> <span data-ttu-id="94d70-120">新成員也會出現在 [指令碼組合管理]\*\*\*\* 窗格中。</span><span class="sxs-lookup"><span data-stu-id="94d70-120">The new member also appears in the **Script Organizer** pane.</span></span>  
  
     <span data-ttu-id="94d70-121">下圖顯示當您按一下 [新增導出成員]\*\*\*\* 時，出現在 [計算運算式]\*\*\*\* 窗格的表單。</span><span class="sxs-lookup"><span data-stu-id="94d70-121">The following image shows the form that appears in the **Calculation Expressions** pane when you click **New Calculated Member**.</span></span>  
  
     <span data-ttu-id="94d70-122">![計算運算式窗格表單](../../2014/tutorials/media/l6-calculatedmembers-02.gif "計算運算式窗格表單")</span><span class="sxs-lookup"><span data-stu-id="94d70-122">![Calculation Expressions pane form](../../2014/tutorials/media/l6-calculatedmembers-02.gif "Calculation Expressions pane form")</span></span>  
  
3.  <span data-ttu-id="94d70-123">在 [**名稱**] 方塊中，將匯出量值的名稱變更為 `[Total Sales Amount]` 。</span><span class="sxs-lookup"><span data-stu-id="94d70-123">In the **Name** box, change the name of the calculated measure to `[Total Sales Amount]`.</span></span>  
  
     <span data-ttu-id="94d70-124">如果導出成員的名稱包含空格，則必須以方括號括住導出成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="94d70-124">If the name of a calculated member contains a space, the calculated member name must be enclosed in square brackets.</span></span>  
  
     <span data-ttu-id="94d70-125">請注意，在 [父階層]\*\*\*\* 清單中，新的導出成員預設是以 [量值]\*\*\*\* 維度建立的。</span><span class="sxs-lookup"><span data-stu-id="94d70-125">Notice in the **Parent hierarchy** list that, by default, a new calculated member is created in the **Measures** dimension.</span></span> <span data-ttu-id="94d70-126">量值維度中的導出成員，也常被稱為導出量值。</span><span class="sxs-lookup"><span data-stu-id="94d70-126">A calculated member in the Measures dimension is also frequently called a calculated measure.</span></span>  
  
4.  <span data-ttu-id="94d70-127">在 [計算]\*\*\*\* 索引標籤 [計算工具]\*\*\*\* 窗格中，展開 [中繼資料]\*\*\*\* 索引標籤上的 [量值]\*\*\*\*，再展開 [網際網路銷售]\*\*\*\* 以檢視 [網際網路銷售]\*\*\*\* 量值群組的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="94d70-127">On the **Metadata** tab in the **Calculation Tools** pane of the **Calculations** tab, expand **Measures** and then expand **Internet Sales** to view the metadata for the **Internet Sales** measure group.</span></span>  
  
     <span data-ttu-id="94d70-128">您可以將中繼資料元素，從 [計算工具]\*\*\*\* 窗格拖曳到 [運算式]\*\*\*\* 方塊中，再加上運算子和其他元素，來建立多維度運算式 (MDX) 運算式。</span><span class="sxs-lookup"><span data-stu-id="94d70-128">You can drag metadata elements from the **Calculation Tools** pane into the **Expression** box and then add operators and other elements to create Multidimensional Expressions (MDX) expressions.</span></span> <span data-ttu-id="94d70-129">或者，您也可以在 [運算式]\*\*\*\* 方塊中，直接輸入 MDX 運算式。</span><span class="sxs-lookup"><span data-stu-id="94d70-129">Alternatively, you can type the MDX expression directly into the **Expression** box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="94d70-130">如果您無法在 [計算工具]\*\*\*\* 窗格檢視任何中繼資料，請在工具列上按一下 [重新連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94d70-130">If you cannot view any metadata in the **Calculation Tools** pane, click **Reconnect** on the toolbar.</span></span> <span data-ttu-id="94d70-131">如果此舉無效，可能得處理 Cube，或者啟動 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="94d70-131">If this does not work, you may have to process the cube or start the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
5.  <span data-ttu-id="94d70-132">從 [計算工具]\*\*\*\* 窗格的 [中繼資料]\*\*\*\* 索引標籤，將 [網際網路銷售 - 銷售量]\*\*\*\* 拖曳到 [計算運算式]\*\*\*\* 窗格中的 [運算式]\*\*\*\* 方塊。</span><span class="sxs-lookup"><span data-stu-id="94d70-132">Drag **Internet Sales-Sales Amount** from the **Metadata** tab in the **Calculation Tools** pane into the **Expression** box in the **Calculation Expressions** pane.</span></span>  
  
6.  <span data-ttu-id="94d70-133">在 [運算式]\*\*\*\* 方塊的 [量值].[網際網路銷售 - 銷售量]\*\*\*\* 後面，輸入一個加號 (`+`)。</span><span class="sxs-lookup"><span data-stu-id="94d70-133">In the **Expression** box, type a plus sign (`+`) after **[Measures].[Internet Sales-Sales Amount]**.</span></span>  
  
7.  <span data-ttu-id="94d70-134">在 [計算工具]\*\*\*\* 窗格的 [中繼資料]\*\*\*\* 索引標籤中，展開 [轉售商銷售]\*\*\*\*，再將 [轉售商銷售 - 銷售量]\*\*\*\* 拖曳到 [計算運算式]\*\*\*\* 窗格中 [運算式]\*\*\*\* 方塊的加號 (+) 後面。</span><span class="sxs-lookup"><span data-stu-id="94d70-134">On the **Metadata** tab in the **Calculation Tools** pane, expand **Reseller Sales**, and then drag **Reseller Sales-Sales Amount** into the **Expression** box in the **Calculation Expressions** pane after the plus sign (+).</span></span>  
  
8.  <span data-ttu-id="94d70-135">在 [**格式字串**] 清單中，選取 **[貨幣]。**</span><span class="sxs-lookup"><span data-stu-id="94d70-135">In the **Format string** list, select **"Currency".**</span></span>  
  
9. <span data-ttu-id="94d70-136">在 [非空白行為]\*\*\*\* 清單中，勾選 [網際網路銷售 - 銷售量]\*\*\*\* 和 [轉售商銷售 - 銷售量]\*\*\*\* 的核取方塊，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94d70-136">In the **Non-empty behavior** list, select the check boxes for **Internet Sales-Sales Amount** and **Reseller Sales-Sales Amount**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="94d70-137">您在 [非空白行為]\*\*\*\* 清單所指定的量值，是用於解析 MDX 的 NON EMPTY 查詢。</span><span class="sxs-lookup"><span data-stu-id="94d70-137">The measures you specify in the **Non-empty behavior** list are used to resolve NON EMPTY queries in MDX.</span></span> <span data-ttu-id="94d70-138">如果所有指定的量值都是空的，那麼當您在 [非空白行為]\*\*\*\* 清單中指定一或多個量值時，[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 會把導出成員視為空白。</span><span class="sxs-lookup"><span data-stu-id="94d70-138">When you specify one or more measures in the **Non-empty behavior** list, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] treats the calculated member as empty if all the specified measures are empty.</span></span> <span data-ttu-id="94d70-139">如果 [非空白行為]\*\*\*\* 屬性空白，[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 必須評估導出成員本身，來判定該成員是否為空白。</span><span class="sxs-lookup"><span data-stu-id="94d70-139">If the **Non-empty behavior** property is blank, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] must evaluate the calculated member itself to determine whether the member is empty.</span></span>  
  
     <span data-ttu-id="94d70-140">下圖顯示 [計算運算式]\*\*\*\* 窗格，其中含有您在前面步驟所指定的設定。</span><span class="sxs-lookup"><span data-stu-id="94d70-140">The following image shows the **Calculation Expressions** pane populated with the settings that you specified in the previous steps.</span></span>  
  
     <span data-ttu-id="94d70-141">![擴展的計算運算式窗格](../../2014/tutorials/media/l6-calculatedmembers-03.gif "擴展的計算運算式窗格")</span><span class="sxs-lookup"><span data-stu-id="94d70-141">![Populated Calculation Expressions pane](../../2014/tutorials/media/l6-calculatedmembers-03.gif "Populated Calculation Expressions pane")</span></span>  
  
10. <span data-ttu-id="94d70-142">在 [計算]\*\*\*\* 索引標籤的工具列上，按一下 [指令碼檢視]\*\*\*\*，然後再檢閱 [計算運算式]\*\*\*\* 窗格中的計算指令碼。</span><span class="sxs-lookup"><span data-stu-id="94d70-142">On the toolbar of the **Calculations** tab, click **Script View**, and then review the calculation script in the **Calculation Expressions** pane.</span></span>  
  
     <span data-ttu-id="94d70-143">請注意，新的計算值會加入初始的 CALCULATE 運算式中；每個個別計算值都以分號區隔。</span><span class="sxs-lookup"><span data-stu-id="94d70-143">Notice that the new calculation is added to the initial CALCULATE expression; each individual calculation is separated by a semicolon.</span></span> <span data-ttu-id="94d70-144">同時也請注意，註解會出現在計算指令碼的開頭。</span><span class="sxs-lookup"><span data-stu-id="94d70-144">Notice also that a comment appears at the beginning of the calculation script.</span></span> <span data-ttu-id="94d70-145">在計算群組的計算指令碼中加入註解，有助於您自己和其他開發人員了解複雜的計算指令碼。</span><span class="sxs-lookup"><span data-stu-id="94d70-145">Adding comments within the calculation script for groups of calculations is a good practice, to help you and other developers understand complex calculation scripts.</span></span>  
  
11. <span data-ttu-id="94d70-146">在計算指令碼的 **Calculate;** 命令之後、剛新增的計算指令碼之前，新增一行，然後把下列文字新增到指令碼的那一行：</span><span class="sxs-lookup"><span data-stu-id="94d70-146">Add a new line in the calculation script after the **Calculate;** command and before the newly added calculation script, and then add the following text to the script on its own line:</span></span>  
  
    ```  
    /* Calculations to aggregate Internet Sales and Reseller Sales measures */  
    ```  
  
     <span data-ttu-id="94d70-147">下圖顯示此時在教學課程中應該顯示在 [計算運算式]\*\*\*\* 窗格的計算指令碼。</span><span class="sxs-lookup"><span data-stu-id="94d70-147">The following image shows the calculation scripts as they should appear in the **Calculation Expressions** pane at this point in the tutorial.</span></span>  
  
     <span data-ttu-id="94d70-148">![計算運算式窗格中的指令碼](../../2014/tutorials/media/l6-calculatedmembers-04.gif "計算運算式窗格中的指令碼")</span><span class="sxs-lookup"><span data-stu-id="94d70-148">![Scripts in Calculation Expressions pane](../../2014/tutorials/media/l6-calculatedmembers-04.gif "Scripts in Calculation Expressions pane")</span></span>  
  
12. <span data-ttu-id="94d70-149">在 [**計算**] 索引標籤的工具列上，按一下 [**表單檢視**]，確認 `[Total Sales Amount]` 已在 [**腳本召集人**] 窗格中選取，然後按一下 [**新增匯出成員**]。</span><span class="sxs-lookup"><span data-stu-id="94d70-149">On the toolbar of the **Calculations** tab, click **Form View**, verify that `[Total Sales Amount]` is selected in the **Script Organizer** pane, and then click **New Calculated Member**.</span></span>  
  
13. <span data-ttu-id="94d70-150">將這個新匯出成員的名稱變更為 `[Total Product Cost]` ，然後在 [**運算式**] 方塊中建立下列運算式：</span><span class="sxs-lookup"><span data-stu-id="94d70-150">Change the name of this new calculated member to `[Total Product Cost]`, and then create the following expression in the **Expression** box:</span></span>  
  
    ```  
    [Measures].[Internet Sales-Total Product Cost] + [Measures].[Reseller Sales-Total Product Cost]  
    ```  
  
14. <span data-ttu-id="94d70-151">在 [格式字串]\*\*\*\* 清單中，選取 [貨幣]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94d70-151">In the **Format string** list, select **"Currency"**.</span></span>  
  
15. <span data-ttu-id="94d70-152">在 [非空白行為]\*\*\*\* 清單中，勾選 [網際網路銷售 - 總產品成本]\*\*\*\* 和 [轉售商銷售 - 總產品成本]\*\*\*\* 的核取方塊，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94d70-152">In the **Non-empty behavior** list, select the check boxes for **Internet Sales-Total Product Cost** and **Reseller Sales-Total Product Cost**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="94d70-153">現在您已經定義了兩個導出成員，兩個都會出現在 [指令碼組合管理]\*\*\*\* 窗格中。</span><span class="sxs-lookup"><span data-stu-id="94d70-153">You have now defined two calculated members, both of which are visible in the **Script Organizer** pane.</span></span> <span data-ttu-id="94d70-154">這些導出成員可被您在計算指令碼後半段所定義的其他計算使用。</span><span class="sxs-lookup"><span data-stu-id="94d70-154">These calculated members can be used by other calculations that you define later in the calculation script.</span></span> <span data-ttu-id="94d70-155">您可以在 [指令碼組合管理]\*\*\*\* 窗格中，選取任何導出成員，以檢視該導出成員的定義；該導出成員的定義會顯示在表單檢視的 [計算運算式]\*\*\*\* 窗格中。</span><span class="sxs-lookup"><span data-stu-id="94d70-155">You can view the definition of any calculated member by selecting the calculated member in the **Script Organizer** pane; the definition of the calculated member will appear in the **Calculation Expressions** pane in the Form view.</span></span> <span data-ttu-id="94d70-156">但是新定義的導出成員在部署之前，不會顯示在 [計算工具]\*\*\*\* 窗格中。</span><span class="sxs-lookup"><span data-stu-id="94d70-156">Newly defined calculated members will not appear in the **Calculation Tools** pane until these objects have been deployed.</span></span> <span data-ttu-id="94d70-157">計算並不需要處理。</span><span class="sxs-lookup"><span data-stu-id="94d70-157">Calculations do not require processing.</span></span>  
  
## <a name="defining-gross-profit-margin-calculations"></a><span data-ttu-id="94d70-158">定義毛利率計算</span><span class="sxs-lookup"><span data-stu-id="94d70-158">Defining Gross Profit Margin Calculations</span></span>  
  
1.  <span data-ttu-id="94d70-159">確認 `[Total Product Cost]` 已在 [**腳本召集人**] 窗格中選取，然後在 [**計算**] 索引標籤的工具列上，按一下 [**新增匯出成員**]。</span><span class="sxs-lookup"><span data-stu-id="94d70-159">Verify that `[Total Product Cost]` is selected in the **Script Organizer** pane, and then click **New Calculated Member** on the toolbar of the **Calculations** tab.</span></span>  
  
2.  <span data-ttu-id="94d70-160">在 [**名稱**] 方塊中，將這個新計算量值的名稱變更為 `[Internet GPM]` 。</span><span class="sxs-lookup"><span data-stu-id="94d70-160">In the **Name** box, change the name of this new calculated measure to `[Internet GPM]`.</span></span>  
  
3.  <span data-ttu-id="94d70-161">在 [運算式]\*\*\*\* 方塊中，建立下列 MDX 運算式：</span><span class="sxs-lookup"><span data-stu-id="94d70-161">In the **Expression** box, create the following MDX expression:</span></span>  
  
    ```  
    ([Measures].[Internet Sales-Sales Amount] -   
    [Measures].[Internet Sales-Total Product Cost]) /  
    [Measures].[Internet Sales-Sales Amount]  
    ```  
  
4.  <span data-ttu-id="94d70-162">在 [格式字串]\*\*\*\* 清單中，選取 [百分比]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94d70-162">In the **Format string** list, select **"Percent"**.</span></span>  
  
5.  <span data-ttu-id="94d70-163">在 [非空白行為]\*\*\*\* 清單中，勾選 [網際網路銷售 - 銷售量]\*\*\*\* 的核取方塊，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94d70-163">In the **Non-empty behavior** list, select the check box for **Internet Sales-Sales Amount**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="94d70-164">在 [計算]\*\*\*\* 索引標籤的工具列上，按一下 [新增導出成員]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94d70-164">On the toolbar of the **Calculations** tab, click **New Calculated Member**.</span></span>  
  
7.  <span data-ttu-id="94d70-165">在 [**名稱**] 方塊中，將這個新計算量值的名稱變更為 `[Reseller GPM]` 。</span><span class="sxs-lookup"><span data-stu-id="94d70-165">In the **Name** box, change the name of this new calculated measure to `[Reseller GPM]`.</span></span>  
  
8.  <span data-ttu-id="94d70-166">在 [運算式]\*\*\*\* 方塊中，建立下列 MDX 運算式：</span><span class="sxs-lookup"><span data-stu-id="94d70-166">In the **Expression** box, create the following MDX expression:</span></span>  
  
    ```  
    ([Measures].[Reseller Sales-Sales Amount] -   
    [Measures].[Reseller Sales-Total Product Cost]) /  
    [Measures].[Reseller Sales-Sales Amount]  
    ```  
  
9. <span data-ttu-id="94d70-167">在 [格式字串]\*\*\*\* 清單中，選取 [百分比]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94d70-167">In the **Format string** list, select **"Percent"**.</span></span>  
  
10. <span data-ttu-id="94d70-168">在 [非空白行為]\*\*\*\* 清單中，勾選 [轉售商銷售 - 銷售量]\*\*\*\* 的核取方塊，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94d70-168">In the **Non-empty behavior** list, select the check box for **Reseller Sales-Sales Amount**, and then click **OK**.</span></span>  
  
11. <span data-ttu-id="94d70-169">在 [計算]\*\*\*\* 索引標籤的工具列上，按一下 [新增導出成員]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94d70-169">On the toolbar of the **Calculations** tab, click **New Calculated Member**.</span></span>  
  
12. <span data-ttu-id="94d70-170">在 [**名稱**] 方塊中，將這個匯出量值的名稱變更為 `[Total GPM]` 。</span><span class="sxs-lookup"><span data-stu-id="94d70-170">In the **Name** box, change the name of this calculated measure to `[Total GPM]`.</span></span>  
  
13. <span data-ttu-id="94d70-171">在 [運算式]\*\*\*\* 方塊中，建立下列 MDX 運算式：</span><span class="sxs-lookup"><span data-stu-id="94d70-171">In the **Expression** box, create the following MDX expression:</span></span>  
  
    ```  
    ([Measures].[Total Sales Amount] -   
    [Measures].[Total Product Cost]) /  
    [Measures].[Total Sales Amount]  
    ```  
  
     <span data-ttu-id="94d70-172">請注意，這個導出成員參考其他導出成員。</span><span class="sxs-lookup"><span data-stu-id="94d70-172">Notice that this calculated member is referencing other calculated members.</span></span> <span data-ttu-id="94d70-173">由於這個導出成員會在它所參考的導出成員之後導出，因此它是有效的導出成員。</span><span class="sxs-lookup"><span data-stu-id="94d70-173">Because this calculated member will be calculated after the calculated members that it references, this is a valid calculated member.</span></span>  
  
14. <span data-ttu-id="94d70-174">在 [格式字串]\*\*\*\* 清單中，選取 [百分比]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94d70-174">In the **Format string** list, select **"Percent"**.</span></span>  
  
15. <span data-ttu-id="94d70-175">在 [非空白行為]\*\*\*\* 清單中，勾選 [網際網路銷售 - 銷售量]\*\*\*\* 和 [轉售商銷售 - 銷售量]\*\*\*\* 的核取方塊，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94d70-175">In the **Non-empty behavior** list, select the check boxes for **Internet Sales-Sales Amount** and **Reseller Sales-Sales Amount**, and then click **OK**.</span></span>  
  
16. <span data-ttu-id="94d70-176">在 [計算]\*\*\*\* 索引標籤的工具列上，按一下 [指令碼檢視]\*\*\*\*，然後檢閱您剛新增至計算指令碼中的三個計算值。</span><span class="sxs-lookup"><span data-stu-id="94d70-176">On the toolbar of the **Calculations** tab, click **Script View** and review the three calculations you just added to the calculation script.</span></span>  
  
17. <span data-ttu-id="94d70-177">在計算腳本中，緊接在計算之前加入新行 `[Internet GPM]` ，然後將下列文字新增至腳本本身的行：</span><span class="sxs-lookup"><span data-stu-id="94d70-177">Add a new line in the calculation script immediately before the `[Internet GPM]` calculation, and then add the following text to the script on its own line:</span></span>  
  
    ```  
    /* Calculations to calculate gross profit margin */  
    ```  
  
     <span data-ttu-id="94d70-178">下圖顯示含有三個新計算值的 [運算式]\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="94d70-178">The following image shows the **Expressions** pane with the three new calculations.</span></span>  
  
     <span data-ttu-id="94d70-179">![計算運算式窗格中的新計算](../../2014/tutorials/media/l6-calculatedmembers-05.gif "計算運算式窗格中的新計算")</span><span class="sxs-lookup"><span data-stu-id="94d70-179">![New calculations in Calculation Expressions pane](../../2014/tutorials/media/l6-calculatedmembers-05.gif "New calculations in Calculation Expressions pane")</span></span>  
  
## <a name="defining-the-percent-of-total-calculations"></a><span data-ttu-id="94d70-180">定義總計算值的百分比</span><span class="sxs-lookup"><span data-stu-id="94d70-180">Defining the Percent of Total Calculations</span></span>  
  
1.  <span data-ttu-id="94d70-181">在 [計算]\*\*\*\* 索引標籤的工具列上，按一下 [表單檢視]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94d70-181">On the toolbar of the **Calculations** tab, click **Form View**.</span></span>  
  
2.  <span data-ttu-id="94d70-182">在 [**腳本召集人**] 窗格中，選取 `[Total GPM]` ，然後在 [**計算**] 索引標籤的工具列上，按一下 [**新增匯出成員**]。</span><span class="sxs-lookup"><span data-stu-id="94d70-182">In the **Script Organizer** pane, select `[Total GPM]`, and then click **New Calculated Member** on the toolbar of the **Calculations** tab.</span></span>  
  
     <span data-ttu-id="94d70-183">在按一下 [新增導出成員]\*\*\*\* 之前，先按一下 [指令碼組合管理]\*\*\*\* 窗格中的最後一個導出成員，可確保這個新的導出成員加在指令碼結尾。</span><span class="sxs-lookup"><span data-stu-id="94d70-183">Clicking the final calculated member in the **Script Organizer** pane before you click **New Calculated Member** guarantees that the new calculated member will be entered at the end of the script.</span></span> <span data-ttu-id="94d70-184">指令碼是以它們出現在 [指令碼組合管理]\*\*\*\* 窗格中的順序執行的。</span><span class="sxs-lookup"><span data-stu-id="94d70-184">Scripts execute in the order that they appear in the **Script Organizer** pane.</span></span>  
  
3.  <span data-ttu-id="94d70-185">將這個新匯出成員的名稱變更為 `[Internet Sales Ratio to All Products]` 。</span><span class="sxs-lookup"><span data-stu-id="94d70-185">Change the name of this new calculated member to `[Internet Sales Ratio to All Products]`.</span></span>  
  
4.  <span data-ttu-id="94d70-186">在 [運算式]\*\*\*\* 方塊中，輸入下列運算式：</span><span class="sxs-lookup"><span data-stu-id="94d70-186">Type the following expression in the **Expression** box:</span></span>  
  
    ```  
    Case  
        When IsEmpty( [Measures].[Internet Sales-Sales Amount] )   
        Then 0  
        Else ( [Product].[Product Categories].CurrentMember,  
               [Measures].[Internet Sales-Sales Amount]) /  
             ( [Product].[Product Categories].[(All)].[All],   
               [Measures].[Internet Sales-Sales Amount] )  
        End  
    ```  
  
     <span data-ttu-id="94d70-187">這個 MDX 運算式會將比重計算為每項產品的總網際網路銷售值。</span><span class="sxs-lookup"><span data-stu-id="94d70-187">This MDX expression calculates the contribution to total Internet sales of each product.</span></span> <span data-ttu-id="94d70-188">Case 陳述式與 IS EMPTY 函數，可以共同確保產品沒有銷售量時，並不會發生除以零的錯誤。</span><span class="sxs-lookup"><span data-stu-id="94d70-188">The Case statement together with the IS EMPTY function ensures that a divide by zero error does not occur when a product has no sales.</span></span>  
  
5.  <span data-ttu-id="94d70-189">在 [格式字串]\*\*\*\* 清單中，選取 [百分比]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94d70-189">In the **Format string** list, select **"Percent"**.</span></span>  
  
6.  <span data-ttu-id="94d70-190">在 [非空白行為]\*\*\*\* 清單中，勾選 [網際網路銷售 - 銷售量]\*\*\*\* 的核取方塊，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94d70-190">In the **Non-empty behavior** list, select the check box for **Internet Sales-Sales Amount**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="94d70-191">在 [計算]\*\*\*\* 索引標籤的工具列上，按一下 [新增導出成員]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94d70-191">On the toolbar of the **Calculations** tab, click **New Calculated Member**.</span></span>  
  
8.  <span data-ttu-id="94d70-192">將這個匯出成員的名稱變更為 `[Reseller Sales Ratio to All Products]` 。</span><span class="sxs-lookup"><span data-stu-id="94d70-192">Change the name of this calculated member to `[Reseller Sales Ratio to All Products]`.</span></span>  
  
9. <span data-ttu-id="94d70-193">在 [運算式]\*\*\*\* 方塊中，輸入下列運算式：</span><span class="sxs-lookup"><span data-stu-id="94d70-193">Type the following expression in the **Expression** box:</span></span>  
  
    ```  
    Case  
        When IsEmpty( [Measures].[Reseller Sales-Sales Amount] )   
        Then 0  
        Else ( [Product].[Product Categories].CurrentMember,  
               [Measures].[Reseller Sales-Sales Amount]) /  
             ( [Product].[Product Categories].[(All)].[All],   
               [Measures].[Reseller Sales-Sales Amount] )  
        End  
    ```  
  
10. <span data-ttu-id="94d70-194">在 [格式字串]\*\*\*\* 清單中，選取 [百分比]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94d70-194">In the **Format string** list, select **"Percent"**.</span></span>  
  
11. <span data-ttu-id="94d70-195">在 [非空白行為]\*\*\*\* 清單中，勾選 [轉售商銷售 - 銷售量]\*\*\*\* 的核取方塊，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94d70-195">In the **Non-empty behavior** list, select the check box for **Reseller Sales-Sales Amount**, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="94d70-196">在 [計算]\*\*\*\* 索引標籤的工具列上，按一下 [新增導出成員]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94d70-196">On the toolbar of the **Calculations** tab, click **New Calculated Member**.</span></span>  
  
13. <span data-ttu-id="94d70-197">將這個匯出成員的名稱變更為 `[Total Sales Ratio to All Products]` 。</span><span class="sxs-lookup"><span data-stu-id="94d70-197">Change the name of this calculated member to `[Total Sales Ratio to All Products]`.</span></span>  
  
14. <span data-ttu-id="94d70-198">在 [運算式]\*\*\*\* 方塊中，輸入下列運算式：</span><span class="sxs-lookup"><span data-stu-id="94d70-198">Type the following expression in the **Expression** box:</span></span>  
  
    ```  
    Case  
        When IsEmpty( [Measures].[Total Sales Amount] )   
        Then 0  
        Else ( [Product].[Product Categories].CurrentMember,  
               [Measures].[Total Sales Amount]) /  
             ( [Product].[Product Categories].[(All)].[All],   
               [Measures].[Total Sales Amount] )  
        End  
    ```  
  
15. <span data-ttu-id="94d70-199">在 [格式字串]\*\*\*\* 清單中，選取 [百分比]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94d70-199">In the **Format string** list, select **"Percent"**.</span></span>  
  
16. <span data-ttu-id="94d70-200">在 [非空白行為]\*\*\*\* 清單中，勾選 [網際網路銷售 - 銷售量]\*\*\*\* 和 [轉售商銷售 - 銷售量]\*\*\*\* 的核取方塊，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94d70-200">In the **Non-empty behavior** list, select the check boxes for **Internet Sales-Sales Amount** and **Reseller Sales-Sales Amount**, and then click **OK**.</span></span>  
  
17. <span data-ttu-id="94d70-201">在 [計算]\*\*\*\* 索引標籤的工具列上，按一下 [指令碼檢視]\*\*\*\*，然後檢閱您剛新增至計算指令碼中的三個計算值。</span><span class="sxs-lookup"><span data-stu-id="94d70-201">On the toolbar of the **Calculations** tab, click **Script View**, and then review the three calculations that you just added to the calculation script.</span></span>  
  
18. <span data-ttu-id="94d70-202">在計算腳本中，緊接在計算之前加入新行 `[Internet Sales Ratio to All Products]` ，然後將下列文字新增至腳本本身的行：</span><span class="sxs-lookup"><span data-stu-id="94d70-202">Add a new line in the calculation script immediately before the `[Internet Sales Ratio to All Products]` calculation, and then add the following text to the script on its own line:</span></span>  
  
    ```  
    /* Calculations to calculate percentage of product to total product sales */  
    ```  
  
     <span data-ttu-id="94d70-203">您總共定義了八個導出成員，當您在表單檢視時，它們都會出現在 [指令碼組合管理]\*\*\*\* 窗格中。</span><span class="sxs-lookup"><span data-stu-id="94d70-203">You have now defined a total of eight calculated members, which are visible in the **Script Organizer** pane when you are in Form view.</span></span>  
  
## <a name="browsing-the-new-calculated-members"></a><span data-ttu-id="94d70-204">瀏覽新的導出成員</span><span class="sxs-lookup"><span data-stu-id="94d70-204">Browsing the New Calculated Members</span></span>  
  
1.  <span data-ttu-id="94d70-205">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 的 [建立]\*\*\*\* 功能表上，按一下 [部署 Analysis Services 教學課程]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94d70-205">On the **Build** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="94d70-206">順利完成部署之後，切換到 [瀏覽器]\*\*\*\* 索引標籤，然後按一下 [重新連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94d70-206">When deployment has successfully completed, switch to the **Browser** tab, click **Reconnect**.</span></span>  
  
3.  <span data-ttu-id="94d70-207">按一下 Excel 圖示，然後按一下 [啟用]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="94d70-207">Click the Excel icon, and then click **Enable**.</span></span>  
  
4.  <span data-ttu-id="94d70-208">在 [樞紐分析表欄位清單]\*\*\*\* 窗格中，展開 [值]\*\*\*\* 資料夾來檢視量值維度中的新導出成員。</span><span class="sxs-lookup"><span data-stu-id="94d70-208">In the **PivotTable Field List** pane, expand **Values** folder to view the new calculated members in the Measures dimension.</span></span>  
  
5.  <span data-ttu-id="94d70-209">將 [總銷售量]\*\*\*\* 拖曳至 [值] 區域中，然後檢閱結果。</span><span class="sxs-lookup"><span data-stu-id="94d70-209">Drag the **Total Sales Amount** to the Values area, and then review the results.</span></span>  
  
     <span data-ttu-id="94d70-210">從 [網際網路銷售]\*\*\*\* 和 [轉售商銷售]\*\*\*\* 量值群組，將 [網際網路銷售 - 銷售量]\*\*\*\* 和 [轉售商銷售 - 銷售量]\*\*\*\* 量值拖曳至 [值] 區域中。</span><span class="sxs-lookup"><span data-stu-id="94d70-210">Drag **Internet Sales-Sales Amount** and **Reseller Sales-Sales Amount** measures from the **Internet Sales** and **Reseller Sales** measure groups to the Values area.</span></span>  
  
     <span data-ttu-id="94d70-211">請注意，[總銷售量]\*\*\*\* 量值是 [網際網路銷售 - 銷售量]\*\*\*\* 量值和 [轉售商銷售 - 銷售量]\*\*\*\* 量值的總和。</span><span class="sxs-lookup"><span data-stu-id="94d70-211">Notice that the **Total Sales Amount** measure is the sum of the **Internet Sales-Sales Amount** measure and the **Reseller Sales-Sales Amount** measure.</span></span>  
  
6.  <span data-ttu-id="94d70-212">將 [產品類別目錄]\*\*\*\* 使用者定義階層新增至 [報表篩選]\*\*\*\* 區域的篩選區域，然後再依 [越野車]\*\*\*\* 篩選資料。</span><span class="sxs-lookup"><span data-stu-id="94d70-212">Add the **Product Categories** user-defined hierarchy to the filter area of the **Report Filter** area, and then filter the data by **Mountain Bikes**.</span></span>  
  
     <span data-ttu-id="94d70-213">請注意，[總銷售量]\*\*\*\* 量值是根據 [越野車]\*\*\*\* 的 [網際網路銷售 - 銷售量]\*\*\*\* 和 [轉售商銷售 - 銷售量]\*\*\*\* 量值，針對產品銷售的 [越野車]\*\*\*\* 類別目錄而計算的。</span><span class="sxs-lookup"><span data-stu-id="94d70-213">Notice that the **Total Sales Amount** measure is calculated for the **Mountain Bikes** category of product sales based on the **Internet Sales-Sales Amount** and the **Reseller Sales-Sales Amount** measures for **Mountain Bikes**.</span></span>  
  
7.  <span data-ttu-id="94d70-214">將 **Date.Calendar Date** 使用者定義階層新增至 [資料列標籤] 區域，然後檢閱結果。</span><span class="sxs-lookup"><span data-stu-id="94d70-214">Add the **Date.Calendar Date** user-defined hierarchy to the Row labels area, and then review the results.</span></span>  
  
     <span data-ttu-id="94d70-215">請注意，每個日曆年度的 [總銷售量]\*\*\*\* 量值，是以 [越野車]\*\*\*\* 的 [網際網路銷售 - 銷售量]\*\*\*\* 和 [轉售商銷售 - 銷售量]\*\*\*\* 量值為依據，並針對產品銷售的 [越野車]\*\*\*\* 類別目錄而計算的。</span><span class="sxs-lookup"><span data-stu-id="94d70-215">Notice that the **Total Sales Amount** measure for each calendar year is calculated for the **Mountain Bikes** category of product sales based on the **Internet Sales-Sales Amount** and the **Reseller Sales-Sales Amount** measures for **Mountain Bikes**.</span></span>  
  
8.  <span data-ttu-id="94d70-216">將 [總毛利率]\*\*\*\*、[網際網路毛利率]\*\*\*\* 和 [轉售商毛利率]\*\*\*\* 量值新增至 [值] 區域中，然後檢閱結果。</span><span class="sxs-lookup"><span data-stu-id="94d70-216">Add the **Total GPM**, **Internet GPM**, and **Reseller GPM** measures to the Values area, and then review the results.</span></span>  
  
     <span data-ttu-id="94d70-217">請注意，轉售商銷售的毛利率遠低於透過網際網路的銷售，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="94d70-217">Notice that the gross profit margin for reseller sales is significantly lower than for sales over the Internet, as shown in the following image.</span></span>  
  
     <span data-ttu-id="94d70-218">![顯示轉售商銷售額的資料窗格](../../2014/tutorials/media/l6-calculatedmembers-7b.gif "顯示轉售商銷售額的資料窗格")</span><span class="sxs-lookup"><span data-stu-id="94d70-218">![Data pane showing reseller sales](../../2014/tutorials/media/l6-calculatedmembers-7b.gif "Data pane showing reseller sales")</span></span>  
  
9. <span data-ttu-id="94d70-219">將 [總銷售與所有產品的比率]\*\*\*\*、[網際網路銷售與所有產品的比率]\*\*\*\* 以及 [轉售商銷售與所有產品的比率]\*\*\*\* 量值新增至 [值] 區域中。</span><span class="sxs-lookup"><span data-stu-id="94d70-219">Add the **Total Sales Ratio to All Products**, **Internet Sales Ratio to All Products**, and **Reseller Sales Ratio to All Products** measures to the Values area.</span></span>  
  
     <span data-ttu-id="94d70-220">請注意，越野車銷售與所有產品的比率，在網際網路銷售方面正逐漸提升，不過在轉售商銷售方面卻有下滑趨勢。</span><span class="sxs-lookup"><span data-stu-id="94d70-220">Notice that the ratio of the sales of mountain bikes to all products has increased over time for Internet sales, but is decreasing over time for reseller sales.</span></span> <span data-ttu-id="94d70-221">另外也請注意，越野車銷售與所有產品的比率，透過轉售商的銷售，低於透過網際網路的銷售。</span><span class="sxs-lookup"><span data-stu-id="94d70-221">Notice also that the ratio of the sale of mountain bikes to all products is lower from sales through resellers than it is for sales over the Internet.</span></span>  
  
10. <span data-ttu-id="94d70-222">將篩選器從 [越野車]\*\*\*\* 改為 [自行車]\*\*\*\*，然後檢閱結果。</span><span class="sxs-lookup"><span data-stu-id="94d70-222">Change the filter from **Mountain Bikes** to **Bikes**, and review the results.</span></span>  
  
     <span data-ttu-id="94d70-223">請注意，透過轉售商銷售的所有自行車毛利率是負值，因為休旅車和公路自行車是虧本出售。</span><span class="sxs-lookup"><span data-stu-id="94d70-223">Notice that the gross profit margin for all bikes sold through resellers is negative, because touring bikes and road bikes are being sold at a loss.</span></span>  
  
11. <span data-ttu-id="94d70-224">將篩選器改為 [配件]\*\*\*\*，然後檢閱結果。</span><span class="sxs-lookup"><span data-stu-id="94d70-224">Change the filter to **Accessories**, and then review the results.</span></span>  
  
     <span data-ttu-id="94d70-225">請注意，配件的銷售量逐漸上升中，但這些銷售在總銷售量中只佔一小部分。</span><span class="sxs-lookup"><span data-stu-id="94d70-225">Notice that the sale of accessories is increasing over time, but that these sales make up only a small fraction of total sales.</span></span> <span data-ttu-id="94d70-226">另外也請注意，配件銷售的毛利率高於自行車的毛利率。</span><span class="sxs-lookup"><span data-stu-id="94d70-226">Notice also that the gross profit margin for sales of accessories is higher than for bikes.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="94d70-227">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="94d70-227">Next Task in Lesson</span></span>  
 [<span data-ttu-id="94d70-228">定義命名集</span><span class="sxs-lookup"><span data-stu-id="94d70-228">Defining Named Sets</span></span>](lesson-6-2-defining-named-sets.md)  
  
## <a name="see-also"></a><span data-ttu-id="94d70-229">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94d70-229">See Also</span></span>  
 <span data-ttu-id="94d70-230">[Acwp](multidimensional-models-olap-logical-cube-objects/calculations.md) </span><span class="sxs-lookup"><span data-stu-id="94d70-230">[Calculations](multidimensional-models-olap-logical-cube-objects/calculations.md) </span></span>  
 <span data-ttu-id="94d70-231">[多維度模型中的計算](multidimensional-models/calculations-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="94d70-231">[Calculations in Multidimensional Models](multidimensional-models/calculations-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="94d70-232">建立導出成員</span><span class="sxs-lookup"><span data-stu-id="94d70-232">Create Calculated Members</span></span>](multidimensional-models/create-calculated-members.md)  
  
  
