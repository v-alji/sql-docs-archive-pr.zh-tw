---
title: 將模型加入結構 (適用于 Excel) 的資料採礦增益集 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, creating
ms.assetid: 8efd5bf4-4e6a-4ee8-971a-6efaed5f3b76
author: minewiskan
ms.author: owend
ms.openlocfilehash: b42cecafc2e3d676465e372e00fe472132f06a3e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593244"
---
# <a name="add-model-to-structure-data-mining-add-ins-for-excel"></a><span data-ttu-id="95beb-102">將模型加入結構 (適用於 Excel 的資料採礦增益集)</span><span class="sxs-lookup"><span data-stu-id="95beb-102">Add Model to Structure (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="95beb-103">![將模型加入到結構按鈕中](media/dmc-addmodel.gif "將模型加入到結構按鈕中")</span><span class="sxs-lookup"><span data-stu-id="95beb-103">![Add Model to Structure button](media/dmc-addmodel.gif "Add Model to Structure button")</span></span>  
  
 <span data-ttu-id="95beb-104">當您按一下 [**將模型加入結構**] 時，就會啟動 wizard，協助您建立新的採礦模型以搭配現有的採礦結構使用。</span><span class="sxs-lookup"><span data-stu-id="95beb-104">When you click **Add Model to Structure**, a wizard starts that helps you create a new mining model to use with an existing mining structure.</span></span> <span data-ttu-id="95beb-105">這個選項可讓您比較以相同資料為基礎的模型，或是建立自訂的模型，因此會很有用。</span><span class="sxs-lookup"><span data-stu-id="95beb-105">This option is useful because it lets you compare models that are based on the same data, or create customized models.</span></span>  
  
 <span data-ttu-id="95beb-106">如果 Analysis Services 的實例尚未包含您所需的資料，請使用 [[建立採礦結構 &#40;SQL Server 資料採礦增益集&#41;](create-mining-structure-sql-server-data-mining-add-ins.md) wizard] 來設定採礦結構。</span><span class="sxs-lookup"><span data-stu-id="95beb-106">If the instance of Analysis Services does not already contain the data you need, use the [Create Mining Structure &#40;SQL Server Data Mining Add-ins&#41;](create-mining-structure-sql-server-data-mining-add-ins.md) wizard to set up a mining structure.</span></span> <span data-ttu-id="95beb-107">或者，您可以啟動其中一個模型精靈，然後將新模型加入由精靈所建立的結構中。</span><span class="sxs-lookup"><span data-stu-id="95beb-107">Or, you can launch one of the modeling wizards, and then add a new model to the structure created by the wizard.</span></span>  
  
 <span data-ttu-id="95beb-108">若要使用不受嚮導支援的演算法來建立 advanced model，請建立一個 [採礦結構]，然後使用 [**資料採礦] [高級查詢編輯器**] 來加入模型。</span><span class="sxs-lookup"><span data-stu-id="95beb-108">To create advanced models using algorithms not supported by the wizards, create a mining structure and then add a model using the **Data Mining Advanced Query Editor**.</span></span>  
  
## <a name="add-a-new-model-to-an-existing-structure"></a><span data-ttu-id="95beb-109">將新模型加入現有的結構</span><span class="sxs-lookup"><span data-stu-id="95beb-109">Add a new model to an existing structure</span></span>  
  
1.  <span data-ttu-id="95beb-110">在 [**資料採礦**] 功能區上，按一下 [ **Advanced**] 底下的箭號，然後選取 [**將模型加入結構**]。</span><span class="sxs-lookup"><span data-stu-id="95beb-110">On the **Data Mining** ribbon, click the arrow under **Advanced**, and then select **Add Model to Structure**.</span></span>  
  
2.  <span data-ttu-id="95beb-111">在 [**選取結構**] 對話方塊中，選擇包含您要使用之資料的結構，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="95beb-111">In the **Select Structure** dialog box, choose the structure that contains the data you want to use, and then click **Next**.</span></span>  
  
     <span data-ttu-id="95beb-112">**提示**：如果您不確定哪一個採礦結構包含所需的資料，請使用 [**檔模型**wizard] 來查看資料的資料行和基本統計資料。</span><span class="sxs-lookup"><span data-stu-id="95beb-112">**Tip**: If you are not sure which mining structure contains the data you need, use the **Document Model** wizard to view the columns and basic statistics about the data.</span></span>  
  
     <span data-ttu-id="95beb-113">如果找不到任何「採礦結構」，請檢查您目前使用的連接。</span><span class="sxs-lookup"><span data-stu-id="95beb-113">If you can't find a mining structure, check the connection that you are currently using.</span></span> <span data-ttu-id="95beb-114">您可能需要開啟與另一部伺服器的連接。</span><span class="sxs-lookup"><span data-stu-id="95beb-114">You might need to open a connection to a different server.</span></span>  
  
3.  <span data-ttu-id="95beb-115">在 [**選取挖掘演算法**] 對話方塊中，選擇要在新的「採礦模型」中使用的「挖掘演算法」。</span><span class="sxs-lookup"><span data-stu-id="95beb-115">In the **Select Mining Algorithm** dialog box, choose a mining algorithm to use in the new mining model.</span></span>  
  
     <span data-ttu-id="95beb-116">請注意，對話方塊所提供的選項比您在 [嚮導] 中看到的還要多。</span><span class="sxs-lookup"><span data-stu-id="95beb-116">Notice that the dialog box provides a lot more options than you'll see in the wizards.</span></span> <span data-ttu-id="95beb-117">如果您的資料相容，則可以建立使用 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 伺服器所支援之任何演算法的模型。</span><span class="sxs-lookup"><span data-stu-id="95beb-117">You can create a model using any algorithm supported on your [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server, provided your data is compatible.</span></span>  
  
4.  <span data-ttu-id="95beb-118">我們建議您也要按一下 [**參數**] 按鈕，以開啟 [**演算法參數**] 對話方塊，並自訂演算法上的參數。</span><span class="sxs-lookup"><span data-stu-id="95beb-118">We recommend that you also click the **Parameters** button to open the **Algorithm Parameters** dialog box and customize parameters on the algorithm.</span></span> <span data-ttu-id="95beb-119">這個選項是建立自訂採礦模型的最簡單的方式。</span><span class="sxs-lookup"><span data-stu-id="95beb-119">This option is the easiest way to create custom mining models.</span></span>  
  
5.  <span data-ttu-id="95beb-120">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="95beb-120">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="95beb-121">在 [**選取資料行**] 對話方塊中，檢查資料行的清單，並在必要時，將資料行的使用方式變更為下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="95beb-121">In the **Select Columns** dialog box, review the list of columns, and if necessary, change the usage of the columns to one of these values:</span></span>  
  
    -   <span data-ttu-id="95beb-122">**輸入**。</span><span class="sxs-lookup"><span data-stu-id="95beb-122">**Input**.</span></span> <span data-ttu-id="95beb-123">表示資料行所包含的變數可能會影響結果，因此應該當做模型的輸入來使用。</span><span class="sxs-lookup"><span data-stu-id="95beb-123">Indicates that the column contains variables that may affect the outcome and should be used as inputs to the model.</span></span>  
  
    -   <span data-ttu-id="95beb-124">**輸入和預測**。</span><span class="sxs-lookup"><span data-stu-id="95beb-124">**Input and Predict**.</span></span> <span data-ttu-id="95beb-125">表示應該做為輸入的資料，您也想要預測這些值。</span><span class="sxs-lookup"><span data-stu-id="95beb-125">Indicates that the data should be used as an input, and that you also want to predict these values.</span></span>  
  
    -   <span data-ttu-id="95beb-126">**僅限預測**。</span><span class="sxs-lookup"><span data-stu-id="95beb-126">**Predict only**.</span></span> <span data-ttu-id="95beb-127">表示不應做為模型輸入的資料。</span><span class="sxs-lookup"><span data-stu-id="95beb-127">Indicates that the data should not be used as an input for the model.</span></span>  
  
    -   <span data-ttu-id="95beb-128">**索引鍵**。</span><span class="sxs-lookup"><span data-stu-id="95beb-128">**Key**.</span></span> <span data-ttu-id="95beb-129">每個模型至少需要一個索引鍵。</span><span class="sxs-lookup"><span data-stu-id="95beb-129">Each model requires at least one key.</span></span> <span data-ttu-id="95beb-130">視模型類型而定，您可能也會有其他特殊金鑰的選項，例如**SequenceKey**或**TimeKey**。</span><span class="sxs-lookup"><span data-stu-id="95beb-130">Depending on the model type, you might also have the option to additional special keys, such as the **SequenceKey** or **TimeKey**.</span></span>  
  
    -   <span data-ttu-id="95beb-131">**請勿使用**。</span><span class="sxs-lookup"><span data-stu-id="95beb-131">**Do not use**.</span></span> <span data-ttu-id="95beb-132">表示即使在結構中也不應在模型內使用的資料。</span><span class="sxs-lookup"><span data-stu-id="95beb-132">Indicates that the data should not be used in the model, even if present in the structure.</span></span>  
  
7.  <span data-ttu-id="95beb-133">按一下 [流覽\*\* ( ...] ) \*\* ] 按鈕，開啟 [**設定資料行模型旗標**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="95beb-133">Click the browse **(...)** button to open the **Set Column Model Flags** dialog box.</span></span>  
  
     <span data-ttu-id="95beb-134">花點時間驗證每個資料行的使用方式是否適合模型。</span><span class="sxs-lookup"><span data-stu-id="95beb-134">Take a minute to verify that the usage of each data column is appropriate for the model.</span></span> <span data-ttu-id="95beb-135">當您嘗試處理模型時，這是防止錯誤發生的重要步驟。</span><span class="sxs-lookup"><span data-stu-id="95beb-135">This is an important step for preventing errors when you try to process the model.</span></span>  
  
     <span data-ttu-id="95beb-136">例如，如果您重複使用為決策樹模型而建立的結構，並對此結構套用貝氏機率分類演算法，則需要分類收納具有資料類型 `Numeric` 和內容類型 `Continuous` 的資料行，或將其變更為離散變數。</span><span class="sxs-lookup"><span data-stu-id="95beb-136">For example, if you re-use a structure that was created for a decision trees model and apply the Naïve Bayes algorithm to it, columns that have the data type `Numeric` and the content type `Continuous` will need to be binned or changed to discrete variables.</span></span>  
  
     <span data-ttu-id="95beb-137">如果結構中的資料行不適用於新的演算法，您可以選取 [**不要使用**] 來略過它們。</span><span class="sxs-lookup"><span data-stu-id="95beb-137">If columns in the structure are not applicable to the new algorithm, you can bypass them by selecting **Do not use**.</span></span>  
  
8.  <span data-ttu-id="95beb-138">在 [**設定資料行模型旗標**] 對話方塊中，檢查或設定模型旗標（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="95beb-138">In the **Set Column Model Flags** dialog box, review or set the modeling flags, if any.</span></span>  
  
     <span data-ttu-id="95beb-139">模型旗標可讓您控制處理 Null 的方式及執行其他作業。</span><span class="sxs-lookup"><span data-stu-id="95beb-139">Modeling flags let you control the way that nulls are handled, among other things.</span></span> <span data-ttu-id="95beb-140">如需詳細資訊，請參閱[模型旗標 &#40;資料採礦&#41;](data-mining/modeling-flags-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="95beb-140">For more information, see [Modeling Flags &#40;Data Mining&#41;](data-mining/modeling-flags-data-mining.md).</span></span>  
  
     <span data-ttu-id="95beb-141">完成時，按一下 **[確定**] 以關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="95beb-141">Click **OK** when done to close the dialog box.</span></span>  
  
9. <span data-ttu-id="95beb-142">在 [**完成**] 對話方塊中，輸入新的「採礦模型」的名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="95beb-142">In the **Finish** dialog box, type a name and description for the new mining model.</span></span>  
  
     <span data-ttu-id="95beb-143">根據您建立的模型類型而定，您可能也會擁有以下選項：</span><span class="sxs-lookup"><span data-stu-id="95beb-143">Depending on the type of model you built, you might also have these options:</span></span>  
  
    -   <span data-ttu-id="95beb-144">建立採礦模型之後，瀏覽已完成的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="95beb-144">Browse the completed mining model after it is built.</span></span>  
  
    -   <span data-ttu-id="95beb-145">使用從模型到來源資料的鑽研。</span><span class="sxs-lookup"><span data-stu-id="95beb-145">Use drillthrough from the model to the source data.</span></span>  
  
         <span data-ttu-id="95beb-146">如需詳細資訊，請參閱[對採礦模型的鑽](data-mining/drillthrough-on-mining-models.md)看。</span><span class="sxs-lookup"><span data-stu-id="95beb-146">For more information, see [Drillthrough on Mining Models](data-mining/drillthrough-on-mining-models.md).</span></span>  
  
10. <span data-ttu-id="95beb-147">按一下 [完成] 以儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="95beb-147">Click **Finish** to save your changes.</span></span> <span data-ttu-id="95beb-148">當您這樣做時，會將新模型部署到伺服器並進行處理。</span><span class="sxs-lookup"><span data-stu-id="95beb-148">As you do so the new model is deployed to the server and processed.</span></span>  
  
### <a name="related-options"></a><span data-ttu-id="95beb-149">相關的選項</span><span class="sxs-lookup"><span data-stu-id="95beb-149">Related Options</span></span>  
  
|<span data-ttu-id="95beb-150">選項</span><span class="sxs-lookup"><span data-stu-id="95beb-150">Option</span></span>|<span data-ttu-id="95beb-151">註解</span><span class="sxs-lookup"><span data-stu-id="95beb-151">Comments</span></span>|  
|------------|--------------|  
|<span data-ttu-id="95beb-152">[**選取結構或模型**] 對話方塊</span><span class="sxs-lookup"><span data-stu-id="95beb-152">**Select Structure or Model** dialog box</span></span>|<span data-ttu-id="95beb-153">選擇現有的採礦結構，以做為建立新模型的基礎。</span><span class="sxs-lookup"><span data-stu-id="95beb-153">Choose en existing mining structure to use as the basis for building a new model.</span></span>  <span data-ttu-id="95beb-154">您挑選的結構必須位於目前的連接中。</span><span class="sxs-lookup"><span data-stu-id="95beb-154">The structure you pick must be located on the current connection.</span></span> <span data-ttu-id="95beb-155">如果沒有，請使用 [[連接到來源資料] &#40;[適用于 Excel&#41;工具的資料採礦用戶端] 來](connect-to-source-data-data-mining-client-for-excel.md)變更連接。</span><span class="sxs-lookup"><span data-stu-id="95beb-155">If not, change connections using the [Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md) tool.</span></span>|  
|<span data-ttu-id="95beb-156">[**選取挖掘演算法**] 對話方塊</span><span class="sxs-lookup"><span data-stu-id="95beb-156">**Select Mining Algorithm** dialog Box</span></span>|<span data-ttu-id="95beb-157">此資料採礦演算法清單會視您連接的伺服器而不同。</span><span class="sxs-lookup"><span data-stu-id="95beb-157">The list of data mining algorithms depends on which server you are connected to.</span></span> [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="95beb-158">Standard Edition 和 Enterprise Edition 提供不同的演算法。</span><span class="sxs-lookup"><span data-stu-id="95beb-158">provides different algorithms in the Standard and Enterprise editions.</span></span> <span data-ttu-id="95beb-159">您的管理員可能還加入了自訂演算法。</span><span class="sxs-lookup"><span data-stu-id="95beb-159">Your administrator also might have added custom algorithms.</span></span><br /><br /> <span data-ttu-id="95beb-160">如果您看不到任何演算法，請確認您已連接到的實例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="95beb-160">If you can't see any algorithms, verify that you are connected to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>|  
|<span data-ttu-id="95beb-161">**演算法參數**對話方塊</span><span class="sxs-lookup"><span data-stu-id="95beb-161">**Algorithm Parameters** Dialog Box</span></span>|<span data-ttu-id="95beb-162">在這些設定中，您可以使用分析方法特定的參數來自訂每個演算法。</span><span class="sxs-lookup"><span data-stu-id="95beb-162">In these settings, you can customize each algorithm using parameters specific to the analytical method.</span></span> <span data-ttu-id="95beb-163">您也可以設定種子，以確保可跨多個定型傳遞重現模型的結果。</span><span class="sxs-lookup"><span data-stu-id="95beb-163">You can also set a seed to ensure that the results of the model can be reproduced across multiple training passes.</span></span><br /><br /> <span data-ttu-id="95beb-164">如需詳細資訊，請參閱[演算法參數 &#40;SQL Server 資料採礦增益集&#41;](algorithm-parameters-sql-server-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="95beb-164">For more information, see [Algorithm Parameters &#40;SQL Server Data Mining Add-ins&#41;](algorithm-parameters-sql-server-data-mining-add-ins.md).</span></span>|  
|<span data-ttu-id="95beb-165">**設定資料行模型旗標**對話方塊</span><span class="sxs-lookup"><span data-stu-id="95beb-165">**Set Column Model Flags** Dialog Box</span></span>|<span data-ttu-id="95beb-166">模型旗標可透過指定遺漏資料的處理方式來改善您的模型。</span><span class="sxs-lookup"><span data-stu-id="95beb-166">Modeling flags can improve your model by specifying how missing data is to be handled.</span></span> <span data-ttu-id="95beb-167">如需詳細資訊，請參閱[模型旗標 &#40;資料採礦&#41;](data-mining/modeling-flags-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="95beb-167">For more information, see [Modeling Flags &#40;Data Mining&#41;](data-mining/modeling-flags-data-mining.md).</span></span>|  
  
###  <a name="setting-column-usage"></a><a name="Bkmk_mdlcolumn"></a><span data-ttu-id="95beb-168">設定資料行使用方式</span><span class="sxs-lookup"><span data-stu-id="95beb-168">Setting Column Usage</span></span>  
 <span data-ttu-id="95beb-169">當您將新模型加入現有的採礦結構時，必須指定模型將如何在採礦結構中使用每個資料行。</span><span class="sxs-lookup"><span data-stu-id="95beb-169">When you add a new model to an existing mining structure, you must specify how the model will use each of the columns of data in the mining structure.</span></span> <span data-ttu-id="95beb-170">您可能會發現，此 wizard 中的選項遠比在「採礦結構」上的選項更詳細。</span><span class="sxs-lookup"><span data-stu-id="95beb-170">You'll probably observe that the options in this wizard are far more detailed than the options on the mining structure.</span></span> <span data-ttu-id="95beb-171">原因為何？</span><span class="sxs-lookup"><span data-stu-id="95beb-171">Why?</span></span>  
  
 <span data-ttu-id="95beb-172">這是因為當您使用精靈同時建立模型和結構時，會自動設定控制演算法如何使用資料的許多選項。</span><span class="sxs-lookup"><span data-stu-id="95beb-172">The reason is that when you create a model and a structure together using a wizard, many of the options that control how data is used by the algorithm are set automatically.</span></span> <span data-ttu-id="95beb-173">不過，當您將新模型加入現有的結構時，您需要手動檢視這些選項，並指定資料是否應用於分析、資料類型是否正確等等。</span><span class="sxs-lookup"><span data-stu-id="95beb-173">However, when you add a new model to an existing, you need to see these options manually, and specify whether data should be used for analysis, whether the data type is correct, and so forth.</span></span>  
  
 <span data-ttu-id="95beb-174">將新演算法套用至現有的資料時，可能會收到錯誤訊息，但這些訊息通常會提供您進行更正以處理模型所需的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="95beb-174">You might get error messages when applying new algorithms to existing data, but these messages generally provide detailed information about the corrections you need to make to allow the model to be processed.</span></span> <span data-ttu-id="95beb-175">常見的問題包括：</span><span class="sxs-lookup"><span data-stu-id="95beb-175">Typical problems include the following:</span></span>  
  
-   <span data-ttu-id="95beb-176">模型預期的資料類型與結構所包含的資料類型不同。</span><span class="sxs-lookup"><span data-stu-id="95beb-176">The model expects a different data type than the structure contains.</span></span>  
  
     <span data-ttu-id="95beb-177">有些演算法只能處理數字，有些演算法只能處理文字。</span><span class="sxs-lookup"><span data-stu-id="95beb-177">Some algorithms can only work with numbers; some can only work with text.</span></span> <span data-ttu-id="95beb-178">如果您的資料類型對於新模型而言不正確，您可能需要修改結構才能處理模型。</span><span class="sxs-lookup"><span data-stu-id="95beb-178">If your data is the wrong type for the new model, you might need to modify the structure to enable the model to process.</span></span>  
  
-   <span data-ttu-id="95beb-179">採礦結構沒有包含可預測的屬性。</span><span class="sxs-lookup"><span data-stu-id="95beb-179">The mining structure contains no predictable attribute.</span></span>  
  
     <span data-ttu-id="95beb-180">您可以建立不含可預測值的群集模型，但其他模型通常會要求您指定單一資料行以進行預測。</span><span class="sxs-lookup"><span data-stu-id="95beb-180">Clustering models can be built with no predictable value, but other models generally require that you specify a single column for prediction.</span></span>  
  
-   <span data-ttu-id="95beb-181">資料的撰寫與您選擇的演算法不相容。</span><span class="sxs-lookup"><span data-stu-id="95beb-181">The composition of the data is incompatible with the algorithm you've chosen.</span></span>  
  
     <span data-ttu-id="95beb-182">某些分析類型需要資料根據獨特的規則而小心地結構化。</span><span class="sxs-lookup"><span data-stu-id="95beb-182">Some types of analysis require data that is carefully structured according to unique rules.</span></span> <span data-ttu-id="95beb-183">例如，預測模型和關聯模型。</span><span class="sxs-lookup"><span data-stu-id="95beb-183">Examples are forecasting models and association models.</span></span> <span data-ttu-id="95beb-184">您可以輕鬆地加入相同類型的新模型，可能包含自訂內容，但這些資料可能不適用於其他演算法。</span><span class="sxs-lookup"><span data-stu-id="95beb-184">You can easily add new models of the same type, perhaps with customizations, but the data might not work with other algorithms.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="95beb-185">需求</span><span class="sxs-lookup"><span data-stu-id="95beb-185">Requirements</span></span>  
 <span data-ttu-id="95beb-186">若要建立資料採礦模型，您必須具有 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體的連接。</span><span class="sxs-lookup"><span data-stu-id="95beb-186">To create data mining models, you must have a connection to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="95beb-187">如需有關如何建立或變更連接的詳細資訊，請參閱[連接到來源資料 &#40;適用于 Excel&#41;的資料採礦用戶端](connect-to-source-data-data-mining-client-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="95beb-187">For more information about how to create or change a connection, see [Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).</span></span>  
  
 <span data-ttu-id="95beb-188">如果您看不到所需的資料採礦結構，可能是該結構儲存在不同的執行個體或不同的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="95beb-188">If you cannot see the data mining structure that you want, it could be that the structure was saved to a different instance or different [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="95beb-189">如需如何變更為不同資料採礦連接的相關資訊，請參閱[連接到資料採礦伺服器](connect-to-a-data-mining-server.md)。</span><span class="sxs-lookup"><span data-stu-id="95beb-189">For information about how to change to a different data mining connection, see [Connect to a Data Mining Server](connect-to-a-data-mining-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95beb-190">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95beb-190">See Also</span></span>  
 [<span data-ttu-id="95beb-191">建立資料採礦模型</span><span class="sxs-lookup"><span data-stu-id="95beb-191">Creating a Data Mining Model</span></span>](creating-a-data-mining-model.md)   
