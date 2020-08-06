---
title: 建立目標郵寄採礦模型結構 (基本資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a9c67f29-0c47-4a5a-862b-db0f5213c2c9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 6a27f818b29120e40248044091c78205dad945bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703558"
---
# <a name="creating-a-targeted-mailing-mining-model-structure-basic-data-mining-tutorial"></a><span data-ttu-id="67d95-102">建立目標郵寄採礦模型結構 (基本資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="67d95-102">Creating a Targeted Mailing Mining Model Structure (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="67d95-103">建立目標郵寄狀況的第一個步驟是，利用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中的資料採礦精靈來建立新的採礦結構和決策樹採礦模型。</span><span class="sxs-lookup"><span data-stu-id="67d95-103">The first step in creating a targeted mailing scenario is to use the Data Mining Wizard in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to create a new mining structure and decision tree mining model.</span></span>  
  
 <span data-ttu-id="67d95-104">在這項工作中，您將設定新的「採礦結構」，並根據決策樹演算法新增初始的「採礦模型」 [!INCLUDE[msCoName](../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="67d95-104">In this task you will set up a new mining structure, and add an initial mining model based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees algorithm.</span></span> <span data-ttu-id="67d95-105">若要建立此結構，您會先選取資料表和檢視表，然後識別哪些資料行將用於定型，哪些資料行將用於測試。</span><span class="sxs-lookup"><span data-stu-id="67d95-105">To create the structure, you will first select tables and views and then identify which columns will be used for training and which for testing.</span></span>  
  
### <a name="to-create-a-mining-structure-for-the-targeted-mailing-scenario"></a><span data-ttu-id="67d95-106">若要建立目標郵寄案例的採礦結構</span><span class="sxs-lookup"><span data-stu-id="67d95-106">To create a mining structure for the targeted mailing scenario</span></span>  
  
1.  <span data-ttu-id="67d95-107">在方案總管中，以滑鼠右鍵按一下 [**採礦結構**]，然後選取 [新增] [**採礦結構**] 來啟動資料採礦嚮導。</span><span class="sxs-lookup"><span data-stu-id="67d95-107">In Solution Explorer, right-click **Mining Structures** and select **New Mining Structure** to start the Data Mining Wizard.</span></span>  
  
2.  <span data-ttu-id="67d95-108">在 **[歡迎使用資料採礦精靈]** 頁面上，按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="67d95-108">On the **Welcome to the Data Mining Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="67d95-109">在 [**選取定義方法**] 頁面上，確認已選取 [**從現有的關係資料庫或資料倉儲**]，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="67d95-109">On the **Select the Definition Method** page, verify that **From existing relational database or data warehouse** is selected, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="67d95-110">在 [**建立資料採礦結構**] 頁面上，于 [**您要使用哪一項資料採礦技術？**] 底下，選取 [ **Microsoft 決策樹**]。</span><span class="sxs-lookup"><span data-stu-id="67d95-110">On the **Create the Data Mining Structure** page, under **Which data mining technique do you want to use?**, select **Microsoft Decision Trees**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="67d95-111">如果出現找不到資料採礦演算法的警告，可能無法正確設定專案屬性。</span><span class="sxs-lookup"><span data-stu-id="67d95-111">If you get a warning that no data mining algorithms can be found, the project properties might not be configured correctly.</span></span> <span data-ttu-id="67d95-112">當專案嘗試從 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 伺服器擷取資料採礦演算法的清單，而且找不到伺服器時，就會出現這個警告。</span><span class="sxs-lookup"><span data-stu-id="67d95-112">This warning occurs when the project attempts to retrieve a list of data mining algorithms from the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server and cannot find the server.</span></span> <span data-ttu-id="67d95-113">根據預設， [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 會使用**localhost**做為伺服器。</span><span class="sxs-lookup"><span data-stu-id="67d95-113">By default, [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] will use **localhost** as the server.</span></span> <span data-ttu-id="67d95-114">如果您要使用不同的執行個體或具名執行個體，您必須變更專案屬性。</span><span class="sxs-lookup"><span data-stu-id="67d95-114">If you are using a different instance, or a named instance, you must change the project properties.</span></span> <span data-ttu-id="67d95-115">如需詳細資訊，請參閱[建立 Analysis Services 專案 &#40;基本資料採礦教學課程&#41;](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="67d95-115">For more information, see [Creating an Analysis Services Project &#40;Basic Data Mining Tutorial&#41;](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md).</span></span>  
  
5.  <span data-ttu-id="67d95-116">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="67d95-116">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="67d95-117">在 [**選取資料來源視圖**] 頁面的 [**可用的資料來源視圖**] 窗格中，選取 [**目標郵寄**]。</span><span class="sxs-lookup"><span data-stu-id="67d95-117">On the **Select Data Source View** page, in the **Available data source views** pane, select **Targeted Mailing**.</span></span> <span data-ttu-id="67d95-118">您可以按一下 **[流覽]** 以在 [資料來源] 視圖中查看資料表，然後按一下 [**關閉**] 返回嚮導。</span><span class="sxs-lookup"><span data-stu-id="67d95-118">You can click **Browse** to view the tables in the data source view and then click **Close** to return to the wizard.</span></span>  
  
7.  <span data-ttu-id="67d95-119">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="67d95-119">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="67d95-120">在 [**指定資料表類型**] 頁面上，選取 [vTargetMail] 的 [**案例**] 資料行中的核取方塊，以將它當做案例資料表，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="67d95-120">On the **Specify Table Types** page, select the check box in the **Case** column for vTargetMail to use it as the case table, and then click **Next**.</span></span> <span data-ttu-id="67d95-121">您之後將會使用 ProspectiveBuyer 資料表進行測試，現在請先忽略。</span><span class="sxs-lookup"><span data-stu-id="67d95-121">You will use the ProspectiveBuyer table later for testing; ignore it for now.</span></span>  
  
9. <span data-ttu-id="67d95-122">在 [**指定定型資料**] 頁面上，您將會識別至少一個可預測資料行、一個索引鍵資料行，以及一個用於模型的輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="67d95-122">On the **Specify the Training Data** page, you will identify at least one predictable column, one key column, and one input column for your model.</span></span> <span data-ttu-id="67d95-123">在 [ **BikeBuyer** ] 資料列的 [**可預測**] 資料行中選取此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="67d95-123">Select the check box in the **Predictable** column in the **BikeBuyer** row.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="67d95-124">請注意視窗底部的警告。</span><span class="sxs-lookup"><span data-stu-id="67d95-124">Notice the warning at the bottom of the window.</span></span> <span data-ttu-id="67d95-125">您必須至少選取一個**輸入**和一個**可預測**的資料行，才能流覽至下一個頁面。</span><span class="sxs-lookup"><span data-stu-id="67d95-125">You will not be able to navigate to the next page until you select at least one **Input** and one **Predictable** column.</span></span>  
  
10. <span data-ttu-id="67d95-126">按一下 [**建議**] 以開啟 [**建議相關資料行**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="67d95-126">Click **Suggest** to open the **Suggest Related Columns** dialog box.</span></span>  
  
     <span data-ttu-id="67d95-127">每當至少選取一個可預測的屬性時，就會啟用 [**建議**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="67d95-127">The **Suggest** button is enabled whenever at least one predictable attribute has been selected.</span></span> <span data-ttu-id="67d95-128">[**建議相關資料行**] 對話方塊會列出與可預測資料行最密切相關的資料行，並依其與可預測屬性的相互關聯排序屬性。</span><span class="sxs-lookup"><span data-stu-id="67d95-128">The **Suggest Related Columns** dialog box lists the columns that are most closely related to the predictable column, and orders the attributes by their correlation with the predictable attribute.</span></span> <span data-ttu-id="67d95-129">系統會自動選取具有重大相互關聯性的資料行 (信心大於 95%)，使其包含在模型中。</span><span class="sxs-lookup"><span data-stu-id="67d95-129">Columns with a significant correlation (confidence greater than 95%) are automatically selected to be included in the model.</span></span>  
  
     <span data-ttu-id="67d95-130">檢查建議，然後按一下 [**取消**] 以 toignore 建議。</span><span class="sxs-lookup"><span data-stu-id="67d95-130">Review the suggestions, and then click **Cancel** toignore the suggestions.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="67d95-131">如果您按一下 **[確定**]，則會在嚮導中將所有列出的建議標示為輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="67d95-131">If you click **OK**, all listed suggestions will be marked as input columns in the wizard.</span></span> <span data-ttu-id="67d95-132">如果您僅同意其中某些建議，就必須手動變更其值。</span><span class="sxs-lookup"><span data-stu-id="67d95-132">If you agree with only some of the suggestions, you must change the values manually.</span></span>  
  
11. <span data-ttu-id="67d95-133">確認已在**CustomerKey**資料列中選取 [索引**鍵**] 資料行中的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="67d95-133">Verify that the check box in the **Key** column is selected in the **CustomerKey** row.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="67d95-134">如果資料來源檢視中的來源資料表指出索引鍵，資料採礦精靈會自動選擇這個資料行來做為模型的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="67d95-134">If the source table from the data source view indicates a key, the Data Mining Wizard automatically chooses that column as a key for the model.</span></span>  
  
12. <span data-ttu-id="67d95-135">在下列資料列中，選取 [**輸入**] 資料行中的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="67d95-135">Select the check boxes in the **Input** column in the following rows.</span></span> <span data-ttu-id="67d95-136">您可以核取多個資料行，其方式是反白顯示某個資料格範圍並按下 CTRL 鍵，然後同時選取核取方塊。</span><span class="sxs-lookup"><span data-stu-id="67d95-136">You can check multiple columns by highlighting a range of cells and pressing CTRL while selecting a check box.</span></span>  
  
    -   <span data-ttu-id="67d95-137">**年齡**</span><span class="sxs-lookup"><span data-stu-id="67d95-137">**Age**</span></span>  
  
    -   <span data-ttu-id="67d95-138">**CommuteDistance**</span><span class="sxs-lookup"><span data-stu-id="67d95-138">**CommuteDistance**</span></span>  
  
    -   <span data-ttu-id="67d95-139">**EnglishEducation**</span><span class="sxs-lookup"><span data-stu-id="67d95-139">**EnglishEducation**</span></span>  
  
    -   <span data-ttu-id="67d95-140">**EnglishOccupation**</span><span class="sxs-lookup"><span data-stu-id="67d95-140">**EnglishOccupation**</span></span>  
  
    -   <span data-ttu-id="67d95-141">**性別**</span><span class="sxs-lookup"><span data-stu-id="67d95-141">**Gender**</span></span>  
  
    -   <span data-ttu-id="67d95-142">**GeographyKey**</span><span class="sxs-lookup"><span data-stu-id="67d95-142">**GeographyKey**</span></span>  
  
    -   <span data-ttu-id="67d95-143">**HouseOwnerFlag**</span><span class="sxs-lookup"><span data-stu-id="67d95-143">**HouseOwnerFlag**</span></span>  
  
    -   <span data-ttu-id="67d95-144">**MaritalStatus**</span><span class="sxs-lookup"><span data-stu-id="67d95-144">**MaritalStatus**</span></span>  
  
    -   <span data-ttu-id="67d95-145">**NumberCarsOwned**</span><span class="sxs-lookup"><span data-stu-id="67d95-145">**NumberCarsOwned**</span></span>  
  
    -   <span data-ttu-id="67d95-146">**NumberChildrenAtHome**</span><span class="sxs-lookup"><span data-stu-id="67d95-146">**NumberChildrenAtHome**</span></span>  
  
    -   <span data-ttu-id="67d95-147">**區域**</span><span class="sxs-lookup"><span data-stu-id="67d95-147">**Region**</span></span>  
  
    -   <span data-ttu-id="67d95-148">**TotalChildren**</span><span class="sxs-lookup"><span data-stu-id="67d95-148">**TotalChildren**</span></span>  
  
    -   <span data-ttu-id="67d95-149">**YearlyIncome**</span><span class="sxs-lookup"><span data-stu-id="67d95-149">**YearlyIncome**</span></span>  
  
13. <span data-ttu-id="67d95-150">在頁面上最左邊的資料行上，選取以下資料列中的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="67d95-150">On the far left column of the page, select the check boxes in the following rows.</span></span>  
  
    -   <span data-ttu-id="67d95-151">**AddressLine1**</span><span class="sxs-lookup"><span data-stu-id="67d95-151">**AddressLine1**</span></span>  
  
    -   <span data-ttu-id="67d95-152">**AddressLine2**</span><span class="sxs-lookup"><span data-stu-id="67d95-152">**AddressLine2**</span></span>  
  
    -   <span data-ttu-id="67d95-153">**DateFirstPurchase**</span><span class="sxs-lookup"><span data-stu-id="67d95-153">**DateFirstPurchase**</span></span>  
  
    -   <span data-ttu-id="67d95-154">**EmailAddress**</span><span class="sxs-lookup"><span data-stu-id="67d95-154">**EmailAddress**</span></span>  
  
    -   <span data-ttu-id="67d95-155">**名字**</span><span class="sxs-lookup"><span data-stu-id="67d95-155">**FirstName**</span></span>  
  
    -   <span data-ttu-id="67d95-156">**姓氏**</span><span class="sxs-lookup"><span data-stu-id="67d95-156">**LastName**</span></span>  
  
     <span data-ttu-id="67d95-157">請確定這些資料列只有在左邊的資料行中才有核取記號。</span><span class="sxs-lookup"><span data-stu-id="67d95-157">Ensure that these rows have checks only in the left column.</span></span> <span data-ttu-id="67d95-158">這些資料行將會加入到您的結構中，但是不會併入模型中。</span><span class="sxs-lookup"><span data-stu-id="67d95-158">These columns will be added to your structure but will not be included in the model.</span></span> <span data-ttu-id="67d95-159">但是在建立此模型之後，這些資料行將可用於鑽研和測試。</span><span class="sxs-lookup"><span data-stu-id="67d95-159">However, after the model is built, they will be available for drillthrough and testing.</span></span> <span data-ttu-id="67d95-160">如需有關「鑽取」的詳細資訊，請參閱[&#40;資料採礦的鑽看查詢&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="67d95-160">For more information about drillthrough, see [Drillthrough Queries &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)</span></span>  
  
14. <span data-ttu-id="67d95-161">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="67d95-161">Click **Next**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="67d95-162">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="67d95-162">Next Task in Lesson</span></span>  
 [<span data-ttu-id="67d95-163">&#40;基本資料採礦教學課程中指定資料類型和內容類型&#41;</span><span class="sxs-lookup"><span data-stu-id="67d95-163">Specifying the Data Type and Content Type &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/specifying-the-data-type-and-content-type-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="67d95-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67d95-164">See Also</span></span>  
 <span data-ttu-id="67d95-165">[指定資料表類型 &#40;資料採礦嚮導&#41;](../../2014/analysis-services/specify-table-types-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="67d95-165">[Specify Table Types &#40;Data Mining Wizard&#41;](../../2014/analysis-services/specify-table-types-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="67d95-166">[資料採礦設計工具](../../2014/analysis-services/data-mining/data-mining-designer.md) </span><span class="sxs-lookup"><span data-stu-id="67d95-166">[Data Mining Designer](../../2014/analysis-services/data-mining/data-mining-designer.md) </span></span>  
 [<span data-ttu-id="67d95-167">Microsoft 決策樹演算法</span><span class="sxs-lookup"><span data-stu-id="67d95-167">Microsoft Decision Trees Algorithm</span></span>](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)  
  
  
