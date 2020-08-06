---
title: 定義命名集 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 47254fd3-525f-4c35-b93d-316607652517
author: minewiskan
ms.author: owend
ms.openlocfilehash: e02f4624dc0ec25ee0c3d8950c83550ca3d9ed57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594788"
---
# <a name="defining-named-sets"></a><span data-ttu-id="4d8db-102">定義命名集</span><span class="sxs-lookup"><span data-stu-id="4d8db-102">Defining Named Sets</span></span>
  <span data-ttu-id="4d8db-103">命名集是指傳回一組維度成員的多維度運算式 (MDX) 運算式。</span><span class="sxs-lookup"><span data-stu-id="4d8db-103">A named set is a Multidimensional Expressions (MDX) expression that returns a set of dimension members.</span></span> <span data-ttu-id="4d8db-104">您可以定義命名集，將它們儲存為 Cube 定義的一部分；也可以在用戶端應用程式建立命名集。</span><span class="sxs-lookup"><span data-stu-id="4d8db-104">You can define named sets and save them as part of the cube definition; you can also create named sets in client applications.</span></span> <span data-ttu-id="4d8db-105">您可以結合 Cube 資料、算術運算子、數字和函數，來建立命名集。</span><span class="sxs-lookup"><span data-stu-id="4d8db-105">You create named sets by combining cube data, arithmetic operators, numbers, and functions.</span></span> <span data-ttu-id="4d8db-106">使用者可以在用戶端應用程式中將命名集用於 MDX 查詢，也可以用於定義 Subcube 中的集合。</span><span class="sxs-lookup"><span data-stu-id="4d8db-106">Named sets can be used by users in MDX queries in client applications and can also be used to define sets in subcubes.</span></span> <span data-ttu-id="4d8db-107">Subcube 是指交叉聯結集的集合，它會將 Cube 空間限制為針對後續陳述式定義的子空間。</span><span class="sxs-lookup"><span data-stu-id="4d8db-107">A subcube is a collection of crossjoined sets that restricts the cube space to the defined subspace for subsequent statements.</span></span> <span data-ttu-id="4d8db-108">定義限制的 Cube 空間是 MDX 指令碼的基本概念。</span><span class="sxs-lookup"><span data-stu-id="4d8db-108">Defining a restricted cube space is a fundamental concept to MDX scripting.</span></span>

 <span data-ttu-id="4d8db-109">命名集可以簡化 MDX 查詢，為複雜常用的集合運算式，提供有用的別名。</span><span class="sxs-lookup"><span data-stu-id="4d8db-109">Named sets simplify MDX queries and provide useful aliases for complex, typically used, set expressions.</span></span> <span data-ttu-id="4d8db-110">例如，您可以定義一個稱為 [大型轉售商] 的命名集，其含有 [轉售商] 維度中，擁有最多員工的成員集合。</span><span class="sxs-lookup"><span data-stu-id="4d8db-110">For example, you can define a named set called Large Resellers that contains the set of members in the Reseller dimension that have the most employees.</span></span> <span data-ttu-id="4d8db-111">一般使用者可以在查詢使用 [大型轉售商] 命名集，也可以使用命名集在 Subcube 中定義一個集合。</span><span class="sxs-lookup"><span data-stu-id="4d8db-111">End users could then use the Large Resellers named set in queries, or you could use the named set to define a set in a subcube.</span></span> <span data-ttu-id="4d8db-112">命名集定義是儲存在 Cube 中，但其值卻只存在於記憶體。</span><span class="sxs-lookup"><span data-stu-id="4d8db-112">Named set definitions are stored in cubes, but their values exist only in memory.</span></span> <span data-ttu-id="4d8db-113">若要建立命名集，請在 Cube 設計師的 **[計算]** 索引標籤上，使用 **[新增命名集]** 命令。</span><span class="sxs-lookup"><span data-stu-id="4d8db-113">To create a named set, use the **New Named Set** command on the **Calculations** tab of Cube Designer.</span></span> <span data-ttu-id="4d8db-114">如需詳細資訊，請參閱 [計算](multidimensional-models-olap-logical-cube-objects/calculations.md)、 [建立命名集](multidimensional-models/create-named-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="4d8db-114">For more information, see [Calculations](multidimensional-models-olap-logical-cube-objects/calculations.md), [Create Named Sets](multidimensional-models/create-named-sets.md).</span></span>

 <span data-ttu-id="4d8db-115">在這個主題的工作中，您要定義兩個命名集：[核心產品] 命名集以及 [大型轉售商] 命名集。</span><span class="sxs-lookup"><span data-stu-id="4d8db-115">In the tasks in this topic, you will define two named sets: a Core Products named set and a Large Resellers named set.</span></span>

## <a name="defining-a-core-products-named-set"></a><span data-ttu-id="4d8db-116">定義核心產品命名集</span><span class="sxs-lookup"><span data-stu-id="4d8db-116">Defining a Core Products Named Set</span></span>

1.  <span data-ttu-id="4d8db-117">針對 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube，切換到 [Cube 設計師] 的 [計算]\*\*\*\* 索引標籤，然後在工具列按一下 [表單檢視]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4d8db-117">Switch to the **Calculations** tab of Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click **Form View** on the toolbar.</span></span>

2.  <span data-ttu-id="4d8db-118">按一下 [指令碼組合管理]\*\*\*\* 窗格中的 [總銷售與所有產品的比率]\*\*\*\*，然後在 [計算]\*\*\*\* 索引標籤的工具列上，按一下 [新增命名集]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4d8db-118">Click **[Total Sales Ratio to All Products]** in the **Script Organizer** pane, and then click **New Named Set** on the toolbar of the **Calculations** tab.</span></span>

     <span data-ttu-id="4d8db-119">當您在 [計算]\*\*\*\* 索引標籤上定義新的計算時，請記住，計算是根據它們出現在 [指令碼組合管理]\*\*\*\* 窗格中的順序加以解析的。</span><span class="sxs-lookup"><span data-stu-id="4d8db-119">When you define a new calculation on the **Calculations** tab, remember that calculations are resolved in the order in which they appear in the **Script Organizer** pane.</span></span> <span data-ttu-id="4d8db-120">在建立新計算時，您在窗格內的焦點，決定了執行計算的順序；新的計算會在焦點計算進行之後立即定義。</span><span class="sxs-lookup"><span data-stu-id="4d8db-120">Your focus within that pane when you create a new calculation determines the order of the execution of the calculation; a new calculation is defined immediately after the calculation on which you are focused.</span></span>

3.  <span data-ttu-id="4d8db-121">在 [**名稱**] 方塊中，將新命名集的名稱變更為 `[Core Products]` 。</span><span class="sxs-lookup"><span data-stu-id="4d8db-121">In the **Name** box, change the name of the new named set to `[Core Products]`.</span></span>

     <span data-ttu-id="4d8db-122">在 [指令碼組合管理]\*\*\*\* 窗格中，請注意分辨命名集與指令碼命令或導出成員所用的唯一圖示。</span><span class="sxs-lookup"><span data-stu-id="4d8db-122">In the **Script Organizer** pane, notice the unique icon that differentiates a named set from a script command or a calculated member.</span></span>

4.  <span data-ttu-id="4d8db-123">在 [**計算工具**] 窗格的 [**中繼資料**] 索引標籤上，依序展開 [**產品**]、[**類別**]、[] `Members` 和 [**所有產品**]。</span><span class="sxs-lookup"><span data-stu-id="4d8db-123">On the **Metadata** tab in the **Calculation Tools** pane, expand **Product**, expand **Category**, expand `Members`, and then expand **All Products**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="4d8db-124">如果您無法在 [計算工具]\*\*\*\* 窗格檢視任何中繼資料，請在工具列上按一下 [重新連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4d8db-124">If you cannot view any metadata in the **Calculation Tools** pane, click **Reconnect** on the toolbar.</span></span> <span data-ttu-id="4d8db-125">如果此舉無效，可能得處理 Cube，或者啟動 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4d8db-125">If this does not work, you may have to process the cube or start the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>

5.  <span data-ttu-id="4d8db-126">將 [自行車]\*\*\*\* 拖曳到 [運算式]\*\*\*\* 方塊。</span><span class="sxs-lookup"><span data-stu-id="4d8db-126">Drag **Bikes** into the **Expression** box.</span></span>

     <span data-ttu-id="4d8db-127">現在您已經建立了一個集合運算式，它會傳回位於 [產品] 維度 [自行車] 類別目錄中的成員集合。</span><span class="sxs-lookup"><span data-stu-id="4d8db-127">You now have created a set expression that will return the set of members that are in the Bike category in the Product dimension.</span></span>

## <a name="defining-a-large-resellers-named-set"></a><span data-ttu-id="4d8db-128">定義大型轉售商命名集</span><span class="sxs-lookup"><span data-stu-id="4d8db-128">Defining a Large Resellers Named Set</span></span>

1.  <span data-ttu-id="4d8db-129">以滑鼠右鍵按一下 `[Core Products]` [**腳本召集人**] 窗格，然後按一下 [**新增命名集**]。</span><span class="sxs-lookup"><span data-stu-id="4d8db-129">Right-click `[Core Products]` in the **Script Organizer** pane, and then click **New Named Set**.</span></span>

2.  <span data-ttu-id="4d8db-130">在 [**名稱**] 方塊中，將這個命名集的名稱變更為 `[Large Resellers]` 。</span><span class="sxs-lookup"><span data-stu-id="4d8db-130">In the **Name** box, change the name of this named set to `[Large Resellers]`.</span></span>

3.  <span data-ttu-id="4d8db-131">在 [**運算式**] 方塊中，輸入 `Exists()` 。</span><span class="sxs-lookup"><span data-stu-id="4d8db-131">In the **Expression** box, type `Exists()`.</span></span>

     <span data-ttu-id="4d8db-132">您會使用 Exists 函數，傳回 [轉售商名稱] 屬性階層中的成員集合，這個成員集合與 [員工數目] 屬性階層中，具有最多員工的成員集合交集。</span><span class="sxs-lookup"><span data-stu-id="4d8db-132">You will use the Exists function to return the set of members from the Reseller Name attribute hierarchy that intersects with the set of members in the Number of Employees attribute hierarchy that has the largest number of employees.</span></span>

4.  <span data-ttu-id="4d8db-133">在 [計算工具]\*\*\*\* 窗格中的 [中繼資料]\*\*\*\* 索引標籤上，依序展開 [轉售商]\*\*\*\* 維度和 [轉售商名稱]\*\*\*\* 屬性階層。</span><span class="sxs-lookup"><span data-stu-id="4d8db-133">On the **Metadata** tab in the **Calculation Tools** pane, expand the **Reseller** dimension, and then expand the **Reseller Name** attribute hierarchy.</span></span>

5.  <span data-ttu-id="4d8db-134">將 [轉售商名稱]\*\*\*\* 層級拖曳到 Exists 集合運算式的括弧內。</span><span class="sxs-lookup"><span data-stu-id="4d8db-134">Drag the **Reseller Name** level into the parenthesis for the Exists set expression.</span></span>

     <span data-ttu-id="4d8db-135">您要使用 Members 函數，傳回這個集合的所有成員。</span><span class="sxs-lookup"><span data-stu-id="4d8db-135">You will use the Members function to return all members of this set.</span></span> <span data-ttu-id="4d8db-136">如需詳細資訊，請參閱 [Members &#40;集合&#41; &#40;MDX&#41;](/sql/mdx/members-set-mdx)。</span><span class="sxs-lookup"><span data-stu-id="4d8db-136">For more information, see [Members &#40;Set&#41; &#40;MDX&#41;](/sql/mdx/members-set-mdx).</span></span>

6.  <span data-ttu-id="4d8db-137">在部分集合運算式之後，輸入一個英文句點，再加上 Members 函數。</span><span class="sxs-lookup"><span data-stu-id="4d8db-137">After the partial set expression, type a period, and then add the Members function.</span></span> <span data-ttu-id="4d8db-138">您的運算式應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="4d8db-138">Your expression should look like the following:</span></span>

    ```
    Exists([Reseller].[Reseller Name].[Reseller Name].Members)
    ```

     <span data-ttu-id="4d8db-139">既然您已定義 Exists 集合運算式的第一個集合，就可以加入第二個集合，也就是包含最多員工的「轉售商」維度成員集合。</span><span class="sxs-lookup"><span data-stu-id="4d8db-139">Now that you have defined the first set for the Exists set expression, you are ready to add the second set-the set of members of the Reseller dimension that contains the largest number of employees.</span></span>

7.  <span data-ttu-id="4d8db-140">在 [**計算工具**] 窗格的 [**中繼資料**] 索引標籤上，展開 [轉售商] 維度中的 [**員工數目**]，展開 `Members` ，然後展開 [**所有轉售商**]</span><span class="sxs-lookup"><span data-stu-id="4d8db-140">On the **Metadata** tab in the **Calculation Tools** pane, expand **Number of Employees** in the Reseller dimension, expand `Members`, and then expand **All Resellers**.</span></span>

     <span data-ttu-id="4d8db-141">請注意，這個屬性階層的成員並未分組。</span><span class="sxs-lookup"><span data-stu-id="4d8db-141">Notice that the members of this attribute hierarchy are not grouped.</span></span>

8.  <span data-ttu-id="4d8db-142">針對 [轉售商]\*\*\*\* 維度開啟 [維度設計師]，然後按一下 [屬性]\*\*\*\* 窗格中的 [員工數目]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4d8db-142">Open Dimension Designer for the **Reseller** dimension, and then click **Number of Employees** in the **Attributes** pane.</span></span>

9. <span data-ttu-id="4d8db-143">在屬性視窗中，將 `DiscretizationMethod` 屬性變更為 [**自動**]，然後將 `DiscretizationBucketCount` 屬性變更為 `5` 。</span><span class="sxs-lookup"><span data-stu-id="4d8db-143">In the Properties window, change the `DiscretizationMethod` property to **Automatic**, and then change the `DiscretizationBucketCount` property to `5`.</span></span> <span data-ttu-id="4d8db-144">如需詳細資訊，請參閱[群組屬性成員 &#40;離散化&#41;](multidimensional-models/attribute-properties-group-attribute-members.md)。</span><span class="sxs-lookup"><span data-stu-id="4d8db-144">For more information, see [Group Attribute Members &#40;Discretization&#41;](multidimensional-models/attribute-properties-group-attribute-members.md).</span></span>

10. <span data-ttu-id="4d8db-145">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 的 [建立]\*\*\*\* 功能表上，按一下 [部署 Analysis Services 教學課程]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4d8db-145">On the **Build** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>

11. <span data-ttu-id="4d8db-146">順利完成部署之後，針對 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube，切換到 [Cube 設計師]，然後按一下 [計算]\*\*\*\* 索引標籤之工具列上的 [重新連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4d8db-146">When deployment has successfully completed, switch to Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click **Reconnect** on the toolbar of the **Calculations** tab.</span></span>

12. <span data-ttu-id="4d8db-147">在 [**計算工具**] 窗格的 [**中繼資料**] 索引標籤上，展開 [**轉售商**] 維度中的 [**員工數目**]，展開 `Members` ，然後展開 [**所有轉售商**]</span><span class="sxs-lookup"><span data-stu-id="4d8db-147">On the **Metadata** tab in the **Calculation Tools** pane, expand **Number of Employees** in the **Reseller** dimension, expand `Members`, and then expand **All Resellers**.</span></span>

     <span data-ttu-id="4d8db-148">請注意，這個屬性階層的成員現已包含在編號 0 到 4 的五個群組中。</span><span class="sxs-lookup"><span data-stu-id="4d8db-148">Notice that the members of this attribute hierarchy are now contained in five groups, numbered 0 through 4.</span></span> <span data-ttu-id="4d8db-149">若要檢視群組的數目，請將資料指標暫停在該群組上，以檢視資訊提示。</span><span class="sxs-lookup"><span data-stu-id="4d8db-149">To view the number of a group, pause the pointer over that group to view an InfoTip.</span></span> <span data-ttu-id="4d8db-150">對於範圍 `2 -17`，資訊提示應該會包含 `[Reseller].[Number of Employees].&[0]`。</span><span class="sxs-lookup"><span data-stu-id="4d8db-150">For the range `2 -17`, the InfoTip should contain `[Reseller].[Number of Employees].&[0]`.</span></span>

     <span data-ttu-id="4d8db-151">這個屬性階層的成員會進行分組，因為 DiscretizationBucketCount 屬性設定為 `5` ，而且 DiscretizationMethod 屬性設定為**自動**。</span><span class="sxs-lookup"><span data-stu-id="4d8db-151">The members of this attribute hierarchy are grouped because the DiscretizationBucketCount property is set to `5` and the DiscretizationMethod property is set to **Automatic**.</span></span>

13. <span data-ttu-id="4d8db-152">在 [運算式]\*\*\*\* 方塊中，Exists 集合運算式的 Members 函數後面和右括弧前面加入逗號，然後將 [83 - 100]\*\*\*\* 從 [中繼資料]\*\*\*\* 窗格拖曳到逗號後面。</span><span class="sxs-lookup"><span data-stu-id="4d8db-152">In the **Expression** box, add a comma in the Exists set expression after the Members function and before the closing parenthesis, and then drag **83 - 100** from the **Metadata** pane and position it after the comma.</span></span>

     <span data-ttu-id="4d8db-153">現在您已經完成 Exists 集合運算式，當 [大型轉售商] 命名集置於軸上時，這個運算式會傳回與這兩個指定集合交集的成員集合：所有轉售商的集合以及擁有 83 到 100 名員工的轉售商集合。</span><span class="sxs-lookup"><span data-stu-id="4d8db-153">You have now completed the Exists set expression that will return the set of members that intersects with these two specified sets, the set of all resellers and the set of resellers who have 83 to 100 employees, when the Large Resellers named set is put on an axis.</span></span>

     <span data-ttu-id="4d8db-154">下圖顯示命名集的 [**計算運算式**] 窗格 `[Large Resellers]` 。</span><span class="sxs-lookup"><span data-stu-id="4d8db-154">The following image shows the **Calculation Expressions** pane for the `[Large Resellers]` named set.</span></span>

     <span data-ttu-id="4d8db-155">![[大型轉售商] 的計算運算式窗格](../../2014/tutorials/media/l6-named-set-02.gif "[大型轉售商] 的計算運算式窗格")</span><span class="sxs-lookup"><span data-stu-id="4d8db-155">![Calculation Expressions pane for [Large Resellers]](../../2014/tutorials/media/l6-named-set-02.gif "Calculation Expressions pane for [Large Resellers]")</span></span>

14. <span data-ttu-id="4d8db-156">在 [計算]\*\*\*\* 索引標籤的工具列上，按一下 [指令碼檢視]\*\*\*\*，檢視您剛剛加到計算指令碼中的兩個命名集。</span><span class="sxs-lookup"><span data-stu-id="4d8db-156">On the toolbar of the **Calculations** tab, click **Script View**, and then review the two named sets that you have just added to the calculation script.</span></span>

15. <span data-ttu-id="4d8db-157">緊接在計算指令碼的第一個 CREATE SET 命令之前加入一行，然後在指令碼那一行加入下列文字：</span><span class="sxs-lookup"><span data-stu-id="4d8db-157">Add a new line in the calculation script immediately before the first CREATE SET command, and then add the following text to the script on its own line:</span></span>

    ```
    /* named sets */
    ```

     <span data-ttu-id="4d8db-158">現在您已經定義了兩個命名集，兩個都會出現在 [指令碼組合管理]\*\*\*\* 窗格中。</span><span class="sxs-lookup"><span data-stu-id="4d8db-158">You have now defined two named sets, which are visible in the **Script Organizer** pane.</span></span> <span data-ttu-id="4d8db-159">現在就可以部署這兩個命名集，然後在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube 中瀏覽這些量值。</span><span class="sxs-lookup"><span data-stu-id="4d8db-159">You are now ready to deploy these named sets, and then to browse these measures in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span>

## <a name="browsing-the-cube-by-using-the-new-named-sets"></a><span data-ttu-id="4d8db-160">利用新的命名集來瀏覽 Cube</span><span class="sxs-lookup"><span data-stu-id="4d8db-160">Browsing the Cube by Using the New Named Sets</span></span>

1.  <span data-ttu-id="4d8db-161">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 的 [建立]\*\*\*\* 功能表上，按一下 [部署 Analysis Services 教學課程]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4d8db-161">On the **Build** menu of [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>

2.  <span data-ttu-id="4d8db-162">當部署順利完成時，請依序按一下 [瀏覽器]\*\*\*\* 索引標籤和 [重新連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4d8db-162">When deployment has successfully completed, click the **Browser** tab, and then click **Reconnect**.</span></span>

3.  <span data-ttu-id="4d8db-163">清除資料窗格中的方格。</span><span class="sxs-lookup"><span data-stu-id="4d8db-163">Clear the grid in the data pane.</span></span>

4.  <span data-ttu-id="4d8db-164">將 [轉售商銷售 - 銷售量]\*\*\*\* 量值新增至資料區域。</span><span class="sxs-lookup"><span data-stu-id="4d8db-164">Add the **Reseller Sales-Sales Amount** measure to the data area.</span></span>

5.  <span data-ttu-id="4d8db-165">展開 [產品] 維度，然後將 [類別目錄] 和 [子類別目錄] 加入至資料列區域，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="4d8db-165">Expand the Product dimension, and then add Category and Subcategory to the row area, as shown in the following image.</span></span>

     <span data-ttu-id="4d8db-166">![子類別屬性的成員](../../2014/tutorials/media/l6-named-set-03.gif "子類別屬性的成員")</span><span class="sxs-lookup"><span data-stu-id="4d8db-166">![Members of the Subcategory attribute](../../2014/tutorials/media/l6-named-set-03.gif "Members of the Subcategory attribute")</span></span>

6.  <span data-ttu-id="4d8db-167">在 [中繼資料]\*\*\*\* 窗格的 [產品]\*\*\*\* 維度中，將 [核心產品]\*\*\*\* 拖曳至篩選區域。</span><span class="sxs-lookup"><span data-stu-id="4d8db-167">In the **Metadata** pane, in the **Product** dimension, drag **Core Products** to the filter area.</span></span>

     <span data-ttu-id="4d8db-168">請注意，只有 [類別目錄]\*\*\*\* 屬性的 [自行車]\*\*\*\* 成員和 [自行車]\*\*\*\* 子類別目錄的成員會繼續留在 Cube 中。</span><span class="sxs-lookup"><span data-stu-id="4d8db-168">Notice that only the **Bike** member of the **Category** attribute and members of the **Bike** subcategories remain in the cube.</span></span> <span data-ttu-id="4d8db-169">這是因為 [核心產品]\*\*\*\* 命名集是用來定義 Subcube。</span><span class="sxs-lookup"><span data-stu-id="4d8db-169">This is because the **Core Products** named set is used to define a subcube.</span></span> <span data-ttu-id="4d8db-170">這個 Subcube 會將 Subcube 內 [產品]\*\*\*\* 維度的 [類別目錄]\*\*\*\* 屬性的成員限制為 [核心產品]\*\*\*\* 命名集的那些成員，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="4d8db-170">This subcube limits the members of the **Category** attribute in the **Product** dimension within the subcube to those members of the **Core Product** named set, as shown in the following image.</span></span>

     <span data-ttu-id="4d8db-171">![核心產品命名集的成員](../../2014/tutorials/media/l6-named-set-04.gif "核心產品命名集的成員")</span><span class="sxs-lookup"><span data-stu-id="4d8db-171">![Members of the Core Product named set](../../2014/tutorials/media/l6-named-set-04.gif "Members of the Core Product named set")</span></span>

7.  <span data-ttu-id="4d8db-172">在 [中繼資料]\*\*\*\* 窗格中，展開 [轉售商]\*\*\*\*，然後將 [大型轉售商]\*\*\*\* 加入篩選區域。</span><span class="sxs-lookup"><span data-stu-id="4d8db-172">In the **Metadata** pane, expand **Reseller**, add **Large Resellers** to the filter area.</span></span>

     <span data-ttu-id="4d8db-173">請注意，[資料] 窗格中的 [轉售商銷售量] 量值只會顯示自行車大型轉售商的銷售量。</span><span class="sxs-lookup"><span data-stu-id="4d8db-173">Notice that the Reseller Sales Amount measure in the Data pane only displays sales amounts for large resellers of bikes.</span></span> <span data-ttu-id="4d8db-174">同時也請注意，[篩選] 窗格現在會顯示用於定義這個特定 Subcube 的兩個命名集，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="4d8db-174">Notice also that the Filter pane now displays the two named sets that are used to define this particular subcube, as shown in the following image.</span></span>

     <span data-ttu-id="4d8db-175">![包含兩個命名集的篩選窗格](../../2014/tutorials/media/l6-named-set-05.gif "包含兩個命名集的篩選窗格")</span><span class="sxs-lookup"><span data-stu-id="4d8db-175">![Filter pane containing two named sets](../../2014/tutorials/media/l6-named-set-05.gif "Filter pane containing two named sets")</span></span>

## <a name="next-task-in-lesson"></a><span data-ttu-id="4d8db-176">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="4d8db-176">Next Task in Lesson</span></span>
 [<span data-ttu-id="4d8db-177">第 7 課：定義關鍵效能指標 &#40;KPI&#41;</span><span class="sxs-lookup"><span data-stu-id="4d8db-177">Lesson 7: Defining Key Performance Indicators &#40;KPIs&#41;</span></span>](lesson-7-defining-key-performance-indicators-kpis.md)

## <a name="see-also"></a><span data-ttu-id="4d8db-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d8db-178">See Also</span></span>
 <span data-ttu-id="4d8db-179">[計算](multidimensional-models-olap-logical-cube-objects/calculations.md)[建立命名集](multidimensional-models/create-named-sets.md)</span><span class="sxs-lookup"><span data-stu-id="4d8db-179">[Calculations](multidimensional-models-olap-logical-cube-objects/calculations.md) [Create Named Sets](multidimensional-models/create-named-sets.md)</span></span>


