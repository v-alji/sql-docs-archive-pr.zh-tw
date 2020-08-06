---
title: DMX 範本 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2a577e52-821d-4bd3-ba35-075a6be285c9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 79c8615933baf4fa3d80974daae91b4d1c7fa101
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599254"
---
# <a name="dmx-templates"></a><span data-ttu-id="8796e-102">DMX 範本</span><span class="sxs-lookup"><span data-stu-id="8796e-102">DMX Templates</span></span>
  <span data-ttu-id="8796e-103">資料採礦範本可幫助您快速建立複雜的查詢。</span><span class="sxs-lookup"><span data-stu-id="8796e-103">The data mining templates help you quickly build sophisticated queries.</span></span> <span data-ttu-id="8796e-104">雖然 DMX 查詢的一般語法已完整記載，但是使用範本可直接按一下並指向引數和資料來源，讓您更容易建立查詢。</span><span class="sxs-lookup"><span data-stu-id="8796e-104">Although the general syntax for DMX queries is well documented, using the templates makes it easier to build queries by clicking and pointing to arguments and data sources.</span></span>  
  
## <a name="using-the-templates"></a><span data-ttu-id="8796e-105">使用範本</span><span class="sxs-lookup"><span data-stu-id="8796e-105">Using the Templates</span></span>  
  
1.  <span data-ttu-id="8796e-106">在 [適用于 Excel 的資料採礦用戶端] 中，按一下 [**查詢**]。</span><span class="sxs-lookup"><span data-stu-id="8796e-106">In the Data Mining Client for Excel, click **Query**.</span></span>  
  
2.  <span data-ttu-id="8796e-107">在嚮導的 [**開始**] 頁面上，按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="8796e-107">On the wizard **Start** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="8796e-108">在頁面上，**選取 [模型**]，然後按一下 [ **Advanced**]。</span><span class="sxs-lookup"><span data-stu-id="8796e-108">On the page, **Select Model**, click **Advanced**.</span></span>  
  
     <span data-ttu-id="8796e-109">**秘訣：** 如果您要在模型上建立預測查詢，您可以先選取模型，然後按一下 [ **Advanced**]，預先填入具有模型名稱的範本。</span><span class="sxs-lookup"><span data-stu-id="8796e-109">**Tip:** If you are going to create a prediction query on a model, you can select the model first, and then click **Advanced**, to prepopulate the template with the model name.</span></span>  
  
4.  <span data-ttu-id="8796e-110">在 [**資料採礦] [高級查詢編輯器**] 中，按一下 [ **DMX 範本**]，然後選取範本。</span><span class="sxs-lookup"><span data-stu-id="8796e-110">In the **Data Mining Advanced Query Editor**, click **DMX Templates**, and select a template.</span></span>  
  
5.  <span data-ttu-id="8796e-111">按 ENTER 將範本載入 [DMX 查詢] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="8796e-111">Press ENTER to load the template into the DMX Query pane.</span></span>  
  
6.  <span data-ttu-id="8796e-112">繼續按一下範本中的連結，然後在對話方塊出現時，選取適當的輸出、模型或參數。</span><span class="sxs-lookup"><span data-stu-id="8796e-112">Continue clicking the links in the template, and as the dialog box appears, select an appropriate output, model, or parameter.</span></span>  
  
     <span data-ttu-id="8796e-113">若是預測查詢，請先選擇輸入資料集，再對應資料行。</span><span class="sxs-lookup"><span data-stu-id="8796e-113">For prediction queries, choose the input dataset first, and then map the columns.</span></span>  
  
7.  <span data-ttu-id="8796e-114">按一下 [**編輯查詢**] 切換至 [文字編輯器] 視圖，然後手動變更查詢。</span><span class="sxs-lookup"><span data-stu-id="8796e-114">Click **Edit Query** to switch to text editor view and manually change the query.</span></span>  
  
     <span data-ttu-id="8796e-115">但是請注意，如果您在使用查詢編輯器時切換檢視，便會清除在上一個檢視中的所有資訊。</span><span class="sxs-lookup"><span data-stu-id="8796e-115">Be aware, however, that if you switch views when working in the query editor, any information that you had in the previous view will be cleared.</span></span> <span data-ttu-id="8796e-116">在變更檢視之前，請將 DMX 陳述式複製並貼到另一個檔案以儲存您的工作。</span><span class="sxs-lookup"><span data-stu-id="8796e-116">Before changing views, save your work by copying and pasting the DMX statements to a separate file.</span></span>  
  
8.  <span data-ttu-id="8796e-117">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="8796e-117">Click **Finish**.</span></span> <span data-ttu-id="8796e-118">在 [**選擇目的地**] 對話方塊中，指定您想要儲存結果的位置。</span><span class="sxs-lookup"><span data-stu-id="8796e-118">In the **Choose Destination** dialog  box, specify where you want the result saved.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
> [!NOTE]  
>  <span data-ttu-id="8796e-119">如果您成功執行語句，則您傳送至伺服器的 DMX 語句也會記錄在**追蹤**視窗中。</span><span class="sxs-lookup"><span data-stu-id="8796e-119">If you executed a statement successfully, the DMX statement that you sent to the server is also recorded in the **Trace** window.</span></span> <span data-ttu-id="8796e-120">如需如何使用追蹤功能的詳細資訊，請參閱[追蹤 &#40;適用于 Excel&#41;的資料採礦用戶端](trace-data-mining-client-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="8796e-120">For more information about how to use the Trace feature, see [Trace &#40;Data Mining Client for Excel&#41;](trace-data-mining-client-for-excel.md).</span></span>  
  
 <span data-ttu-id="8796e-121">如需有關如何使用 [資料採礦] [高級查詢編輯器] 的詳細資訊，請參閱[查詢 &#40;SQL Server 資料採礦增益集&#41;](query-sql-server-data-mining-add-ins.md)和[Advanced Data 挖掘查詢編輯器](advanced-data-mining-query-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="8796e-121">For more information about how to use the Data Mining Advanced Query Editor, see [Query &#40;SQL Server Data Mining Add-ins&#41;](query-sql-server-data-mining-add-ins.md) and [Advanced Data Mining Query Editor](advanced-data-mining-query-editor.md).</span></span>  
  
## <a name="list-of-dmx-templates"></a><span data-ttu-id="8796e-122">DMX 範本的清單</span><span class="sxs-lookup"><span data-stu-id="8796e-122">List of DMX Templates</span></span>  
 <span data-ttu-id="8796e-123">適用於 Excel 的資料採礦用戶端中包括下列 DMX 範本。</span><span class="sxs-lookup"><span data-stu-id="8796e-123">The following DMX templates are included in the Data Mining Client for Excel.</span></span>  
  
 <span data-ttu-id="8796e-124">**預測**</span><span class="sxs-lookup"><span data-stu-id="8796e-124">**Prediction**</span></span>  
  
 <span data-ttu-id="8796e-125">使用這些範本可建立進階預測查詢，包括增益集精靈不支援的查詢，例如，使用巢狀資料表或外部資料來源的查詢。</span><span class="sxs-lookup"><span data-stu-id="8796e-125">Use these templates to create advanced prediction queries, including queries not supported by the wizards in the add-ins, such as queries that use nested tables or external data sources.</span></span>  
  
-   <span data-ttu-id="8796e-126">篩選的預測</span><span class="sxs-lookup"><span data-stu-id="8796e-126">Filtered predictions</span></span>  
  
-   <span data-ttu-id="8796e-127">篩選的巢狀預測</span><span class="sxs-lookup"><span data-stu-id="8796e-127">Filtered nested predictions</span></span>  
  
-   <span data-ttu-id="8796e-128">巢狀預測</span><span class="sxs-lookup"><span data-stu-id="8796e-128">Nested predictions</span></span>  
  
-   <span data-ttu-id="8796e-129">單一預測</span><span class="sxs-lookup"><span data-stu-id="8796e-129">Singleton predictions</span></span>  
  
-   <span data-ttu-id="8796e-130">標準預測</span><span class="sxs-lookup"><span data-stu-id="8796e-130">Standard predictions</span></span>  
  
-   <span data-ttu-id="8796e-131">時間序列預測</span><span class="sxs-lookup"><span data-stu-id="8796e-131">Time series predictions</span></span>  
  
-   <span data-ttu-id="8796e-132">TOP 預測查詢</span><span class="sxs-lookup"><span data-stu-id="8796e-132">TOP prediction query</span></span>  
  
-   <span data-ttu-id="8796e-133">巢狀資料表上的 TOP 預測查詢</span><span class="sxs-lookup"><span data-stu-id="8796e-133">TOP prediction query on nested table</span></span>  
  
 <span data-ttu-id="8796e-134">**建立**</span><span class="sxs-lookup"><span data-stu-id="8796e-134">**Create**</span></span>  
  
 <span data-ttu-id="8796e-135">使用這些範本可建立自訂模型或資料結構。</span><span class="sxs-lookup"><span data-stu-id="8796e-135">Use these templates to build custom models or data structures.</span></span> <span data-ttu-id="8796e-136">您不受限於此程式所支援的模型-您可以使用所連接之實例所支援的任何資料採礦演算法 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，包括外掛程式演算法。</span><span class="sxs-lookup"><span data-stu-id="8796e-136">You are not limited to the models supported by the wizards - you can use any data mining algorithm supported by the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you are connected to, including plug-in algorithms.</span></span>  
  
-   <span data-ttu-id="8796e-137">採礦模型</span><span class="sxs-lookup"><span data-stu-id="8796e-137">Mining model</span></span>  
  
-   <span data-ttu-id="8796e-138">採礦結構</span><span class="sxs-lookup"><span data-stu-id="8796e-138">Mining structure</span></span>  
  
-   <span data-ttu-id="8796e-139">含鑑效組的採礦結構</span><span class="sxs-lookup"><span data-stu-id="8796e-139">Mining structure with holdout</span></span>  
  
-   <span data-ttu-id="8796e-140">暫時性模型</span><span class="sxs-lookup"><span data-stu-id="8796e-140">Temporary model</span></span>  
  
-   <span data-ttu-id="8796e-141">暫時性結構</span><span class="sxs-lookup"><span data-stu-id="8796e-141">Temporary structure</span></span>  
  
 <span data-ttu-id="8796e-142">**模型屬性**</span><span class="sxs-lookup"><span data-stu-id="8796e-142">**Model Properties**</span></span>  
  
 <span data-ttu-id="8796e-143">使用這些範本可建立查詢，取得有關模型和定型集的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="8796e-143">Use these templates to create queries that get metadata about the model and the training set.</span></span> <span data-ttu-id="8796e-144">您也可以從模型內容擷取詳細資料，或是取得定型資料的統計資料設定檔。</span><span class="sxs-lookup"><span data-stu-id="8796e-144">You can also retrieve details from the model content, or get a statistical profile of the training data.</span></span>  
  
-   <span data-ttu-id="8796e-145">採礦模型內容</span><span class="sxs-lookup"><span data-stu-id="8796e-145">Mining model content</span></span>  
  
-   <span data-ttu-id="8796e-146">最小和最大資料行的值</span><span class="sxs-lookup"><span data-stu-id="8796e-146">Minimum and maximum column values</span></span>  
  
-   <span data-ttu-id="8796e-147">採礦結構測試/定型案例</span><span class="sxs-lookup"><span data-stu-id="8796e-147">Mining structure test/training cases</span></span>  
  
-   <span data-ttu-id="8796e-148">離散資料行的值</span><span class="sxs-lookup"><span data-stu-id="8796e-148">Discrete column values</span></span>  
  
 <span data-ttu-id="8796e-149">**管理**</span><span class="sxs-lookup"><span data-stu-id="8796e-149">**Management**</span></span>  
  
 <span data-ttu-id="8796e-150">使用這些範本可執行 DMX 支援的所有管理工作，包括匯入與匯出模型、刪除模型，以及清除模型或資料結構。</span><span class="sxs-lookup"><span data-stu-id="8796e-150">Use these templates to perform any management task supported by DMX, which includes importing and exporting models, deleting models, and clearing models or data structures.</span></span>  
  
-   <span data-ttu-id="8796e-151">清除採礦模型</span><span class="sxs-lookup"><span data-stu-id="8796e-151">Clear mining model</span></span>  
  
-   <span data-ttu-id="8796e-152">清除結構和模型</span><span class="sxs-lookup"><span data-stu-id="8796e-152">Clear structure and models</span></span>  
  
-   <span data-ttu-id="8796e-153">清除採礦結構</span><span class="sxs-lookup"><span data-stu-id="8796e-153">Clear mining structure</span></span>  
  
-   <span data-ttu-id="8796e-154">刪除採礦模型</span><span class="sxs-lookup"><span data-stu-id="8796e-154">Delete mining model</span></span>  
  
-   <span data-ttu-id="8796e-155">刪除採礦結構</span><span class="sxs-lookup"><span data-stu-id="8796e-155">Delete mining structure</span></span>  
  
-   <span data-ttu-id="8796e-156">重新命名採礦模型</span><span class="sxs-lookup"><span data-stu-id="8796e-156">Rename mining model</span></span>  
  
-   <span data-ttu-id="8796e-157">重新命名採礦結構</span><span class="sxs-lookup"><span data-stu-id="8796e-157">Rename mining structure</span></span>  
  
-   <span data-ttu-id="8796e-158">定型採礦模型</span><span class="sxs-lookup"><span data-stu-id="8796e-158">Train mining model</span></span>  
  
-   <span data-ttu-id="8796e-159">定型巢狀採礦結構</span><span class="sxs-lookup"><span data-stu-id="8796e-159">Train nested mining structure</span></span>  
  
-   <span data-ttu-id="8796e-160">定型採礦結構</span><span class="sxs-lookup"><span data-stu-id="8796e-160">Train mining structure</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="8796e-161">需求</span><span class="sxs-lookup"><span data-stu-id="8796e-161">Requirements</span></span>  
 <span data-ttu-id="8796e-162">根據您使用的範本而定，您可能需要系統管理權限才能存取 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 伺服器並執行查詢。</span><span class="sxs-lookup"><span data-stu-id="8796e-162">Depending on which template you are using, you might need administrative permissions to access the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server and execute the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8796e-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8796e-163">See Also</span></span>  
 [<span data-ttu-id="8796e-164">建立資料採礦模型</span><span class="sxs-lookup"><span data-stu-id="8796e-164">Creating a Data Mining Model</span></span>](creating-a-data-mining-model.md)  
  
  
