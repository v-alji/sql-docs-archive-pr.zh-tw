---
title: 針對 (SSAS 表格式) 處理資料進行疑難排解 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 678f523c-e181-4456-9a54-7b7bf044b8d2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6962f5452f9b16472a59914f557e6949ebb4ed05
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595297"
---
# <a name="troubleshoot-process-data-ssas-tabular"></a><span data-ttu-id="fa7a5-102">疑難排解處理資料 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="fa7a5-102">Troubleshoot Process Data (SSAS Tabular)</span></span>
  <span data-ttu-id="fa7a5-103">本主題提供有關使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]製作模型時，處理 (重新整理) 模型資料的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-103">This topic provides information about processing (refresh) model data when authoring a model by using [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="fa7a5-104">本主題不會提供有關處理模型中已部署至 Analysis Services 伺服器執行個體之資料的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-104">This topic does not provide information about processing data in models that has been deployed to an Analysis Services server instance.</span></span> <span data-ttu-id="fa7a5-105">如需在部署的模型中處理資料的詳細資訊，請參閱 [在 Analysis Services 中編寫管理工作的指令碼](script-administrative-tasks-in-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-105">For more information about processing data in a deployed model, see [Script Administrative Tasks in Analysis Services](script-administrative-tasks-in-analysis-services.md).</span></span>  
  
 <span data-ttu-id="fa7a5-106">本主題的章節：</span><span class="sxs-lookup"><span data-stu-id="fa7a5-106">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="fa7a5-107">資料處理如何運作</span><span class="sxs-lookup"><span data-stu-id="fa7a5-107">How Data Processing Works</span></span>](#bkmk_how_df_works)  
  
-   [<span data-ttu-id="fa7a5-108">資料處理的影響</span><span class="sxs-lookup"><span data-stu-id="fa7a5-108">Impact of Data Processing</span></span>](#bkmk_impact_of_df)  
  
-   [<span data-ttu-id="fa7a5-109">判斷資料的來源</span><span class="sxs-lookup"><span data-stu-id="fa7a5-109">Determining the Source of Data</span></span>](#bkmk_det_source)  
  
-   [<span data-ttu-id="fa7a5-110">判斷上次重新整理資料的時間</span><span class="sxs-lookup"><span data-stu-id="fa7a5-110">Determining When Data was Last Refreshed</span></span>](#bkmk_det_last_ref)  
  
-   [<span data-ttu-id="fa7a5-111">重新整理資料來源的限制</span><span class="sxs-lookup"><span data-stu-id="fa7a5-111">Restrictions on Refreshable Data Sources</span></span>](#bkmk_restrictions)  
  
-   [<span data-ttu-id="fa7a5-112">變更資料來源的限制</span><span class="sxs-lookup"><span data-stu-id="fa7a5-112">Restrictions on Changes to a Data Source</span></span>](#bkmk_rest_changes)  
  
##  <a name="how-data-processing-works"></a><a name="bkmk_how_df_works"></a><span data-ttu-id="fa7a5-113">資料處理的運作方式</span><span class="sxs-lookup"><span data-stu-id="fa7a5-113">How Data Processing Works</span></span>  
 <span data-ttu-id="fa7a5-114">當您處理資料時，便會以新的資料取代模型設計師中的資料。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-114">When you process data, the data in the model designer is replaced with new data.</span></span> <span data-ttu-id="fa7a5-115">您無法只匯入新的資料列或是只變更資料。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-115">You cannot import just new rows of data or just changed data.</span></span> <span data-ttu-id="fa7a5-116">模型設計師不會追蹤哪些資料列是在先前加入的。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-116">The model designer does not track which rows were added previously.</span></span>  
  
 <span data-ttu-id="fa7a5-117">資料的處理會以交易的方式進行。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-117">Processing of data takes place as a transaction.</span></span> <span data-ttu-id="fa7a5-118">這表示一旦開始更新資料，整個更新不是失敗就是成功，您絕不會擁有部分正確的資料。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-118">This means that once you begin updating data, the entire update must either fail or succeed; you will never have data that is partly correct.</span></span>  
  
 <span data-ttu-id="fa7a5-119">從 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]起始的手動資料處理，是由 Analysis Services 的本機記憶體中執行個體所處理。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-119">Manual data process, which you initiate from [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], is handled by the local in-memory instance of Analysis Services.</span></span> <span data-ttu-id="fa7a5-120">因此，資料處理作業會影響到電腦上其他工作的效能。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-120">Therefore, the data process operation can affect the performance of other tasks on your computer.</span></span> <span data-ttu-id="fa7a5-121">不過，如果您排程使用指令碼在已部署的模型中自動處理資料，Analysis Services 的執行個體便會管理匯入處理及其時機。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-121">However, if you schedule automatic process of data in a deployed model by using a script, the instance of Analysis Services manages the import process and its timing.</span></span>  
  
##  <a name="impact-of-data-processing"></a><a name="bkmk_impact_of_df"></a><span data-ttu-id="fa7a5-122">資料處理的影響</span><span class="sxs-lookup"><span data-stu-id="fa7a5-122">Impact of Data Processing</span></span>  
 <span data-ttu-id="fa7a5-123">資料的處理通常會觸發資料的重新計算。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-123">A process of data usually triggers recalculation of data.</span></span>  <span data-ttu-id="fa7a5-124">處理資料表示從外部來源取得最新資料；重新計算則表示更新使用已變更資料之所有公式的結果。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-124">Processing data means getting the latest data from the external sources;  recalculating means updating the result of all formulas that use data that has changed.</span></span> <span data-ttu-id="fa7a5-125">處理作業通常會觸發重新計算。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-125">A process operation usually triggers recalculation.</span></span>  
  
 <span data-ttu-id="fa7a5-126">因此，在您變更資料來源或處理取自資料來源的資料之前，永遠都該注意潛在的影響，並考慮這些潛在的結果：</span><span class="sxs-lookup"><span data-stu-id="fa7a5-126">Therefore you should always be mindful of the potential impact before you change data sources or process the data that is obtained from the data source, and consider these potential consequences:</span></span>  
  
-   <span data-ttu-id="fa7a5-127">模型資料的某些部分可能會因為資料來源中的變更而中斷。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-127">Some parts of the model data may be broken as a result of changes in the data source.</span></span> <span data-ttu-id="fa7a5-128">如果並非所有的資料行都可從資料來源擷取 (例如它們已經遭到刪除或是變更)，處理便會失敗，而您就必須更新在來源資料與模型資料之間的對應。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-128">If not all of the columns can be retrieved from the data source (for example, if they have been deleted or changed), process will fail, and you must update the mappings between the source data and the model data.</span></span> <span data-ttu-id="fa7a5-129">如需詳細資訊，請參閱 [編輯現有的資料來源連接 &#40;SSAS 表格式&#41;](edit-an-existing-data-source-connection-ssas-tabular.md)製作模型時，處理 (重新整理) 模型資料的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-129">For more information, see [Edit an Existing Data Source Connection &#40;SSAS Tabular&#41;](edit-an-existing-data-source-connection-ssas-tabular.md).</span></span>  
  
-   <span data-ttu-id="fa7a5-130">處理後，某些資料行可能會標示為包含錯誤。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-130">After processing, some columns might be flagged as containing an error.</span></span> <span data-ttu-id="fa7a5-131">這種錯誤發生的原因，可能是資料行中的 DAX 公式使用當處理時就無法使用的資料、資料行的資料類型變更，或是將無效的值加入外部資料。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-131">This can happen because the DAX formula in the column uses data that became unavailable when you processed, the data type of a column changed, or an invalid value was added to the external data.</span></span> <span data-ttu-id="fa7a5-132">若要解決這個問題，您可以編輯公式，或者，如果該公式是以無法再使用的資料為基礎，您可以刪除資料行。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-132">To resolve the issue, you can edit the formula, or you can delete the column if it is based on data that is no longer available.</span></span>  
  
-   <span data-ttu-id="fa7a5-133">使用更新之資料的公式將需要進行重新計算。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-133">Formulas that use the updated data will need to be recalculated.</span></span> <span data-ttu-id="fa7a5-134">視模型的大小而定，這可能會花費一些時間。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-134">Depending on the size of the model, this can take some time.</span></span>  
  
-   <span data-ttu-id="fa7a5-135">如果您的模型包含多個資料來源，即使只有一個外部資料來源有變更，您也可能需要處理整個模型 (處理全部)。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-135">If your model contains multiple data sources, you might need to process the entire model (Process All) even if only one external data source has changed.</span></span> <span data-ttu-id="fa7a5-136">例如，如果您建立依賴導出資料行的量值，而且這些導出資料行使用其他導出資料行中的值，模型設計師會先分析相依性，然後依序處理相關物件的整個鏈結。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-136">For example, if you create measures that rely on calculated columns, and those calculated columns use values from other calculated columns, the model designer first analyzes the dependencies and then processes the entire chain of related objects in order.</span></span> <span data-ttu-id="fa7a5-137">視相依性的複雜性而定，這可能會花費很長的時間。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-137">Depending on the complexity of the dependencies, this can take a long time.</span></span>  
  
-   <span data-ttu-id="fa7a5-138">當您變更篩選時，整個模型都必須進行重新計算。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-138">When you change a filter, the entire model must be recalculated.</span></span>  
  
##  <a name="determining-the-source-of-data"></a><a name="bkmk_det_source"></a><span data-ttu-id="fa7a5-139">判斷資料的來源</span><span class="sxs-lookup"><span data-stu-id="fa7a5-139">Determining the Source of Data</span></span>  
 <span data-ttu-id="fa7a5-140">如果您不確定模型中的資料來自何處，您可以使用 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中的工具來取得詳細資料，其中包括來源檔案名稱和路徑。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-140">If you are not sure where the data in your model came from, you can use the tools in the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] to get the details, including the source file name and path.</span></span>  
  
#### <a name="to-find-the-source-of-existing-data"></a><span data-ttu-id="fa7a5-141">尋找現有資料的來源</span><span class="sxs-lookup"><span data-stu-id="fa7a5-141">To find the source of existing data</span></span>  
  
1.  <span data-ttu-id="fa7a5-142">在模型設計師中，選取包含想要知道其來源之資料的資料表。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-142">In the model designer, select the table that contains the data for which you want to know the source.</span></span>  
  
2.  <span data-ttu-id="fa7a5-143">按一下 [資料表]\*\*\*\* 功能表，然後再按一下 [資料表屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-143">Click on the **Table** menu, and the click **Table Properties**.</span></span>  
  
3.  <span data-ttu-id="fa7a5-144">在 [編輯資料表屬性]\*\*\*\* 對話方塊中，記下針對 [連接名稱]\*\*\*\* 列出的值。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-144">In the **Edit Table Properties** dialog box, make note of the value listed for **Connection Name**.</span></span>  
  
4.  <span data-ttu-id="fa7a5-145">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中，按一下 [模型]\*\*\*\* 功能表上的 [現有連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-145">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Existing Connections**.</span></span>  
  
5.  <span data-ttu-id="fa7a5-146">在 [現有連接]\*\*\*\* 對話方塊中，選取包含您在步驟 3 找到之名稱的資料來源，然後按一下 [編輯]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-146">In the **Existing Connections** dialog box, select the data source with the name you found in step 3, and then click **Edit**.</span></span>  
  
6.  <span data-ttu-id="fa7a5-147">在 [編輯連接]\*\*\*\* 對話方塊中檢視連接資訊，例如資料庫名稱、檔案路徑或報表路徑。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-147">In the **Edit Connections** dialog box, view the connection information, such as the database name, file path, or report path.</span></span>  
  
##  <a name="determining-when-data-was-last-refreshed"></a><a name="bkmk_det_last_ref"></a><span data-ttu-id="fa7a5-148">判斷上次重新整理資料的時間</span><span class="sxs-lookup"><span data-stu-id="fa7a5-148">Determining When Data was Last Refreshed</span></span>  
 <span data-ttu-id="fa7a5-149">您可以使用 [資料表屬性] 判斷上次重新整理資料的時間。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-149">You can use the Table Properties to determine when the data was last refreshed.</span></span>  
  
#### <a name="to-find-the-date-and-time-that-a-table-was-last-processed"></a><span data-ttu-id="fa7a5-150">尋找上次處理資料表的日期和時間</span><span class="sxs-lookup"><span data-stu-id="fa7a5-150">To find the date and time that a table was last processed</span></span>  
  
1.  <span data-ttu-id="fa7a5-151">在模型設計師中，選取包含想要知道其重新整理日期之資料的資料表。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-151">In the model designer, select the table that contains the data for which you want to know the refresh date.</span></span>  
  
2.  <span data-ttu-id="fa7a5-152">按一下 **[資料表]** 功能表，然後再按一下 **[資料表屬性]**。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-152">Click on the **Table** menu, and then click **Table Properties**.</span></span>  
  
3.  <span data-ttu-id="fa7a5-153">在 [編輯資料表屬性]\*\*\*\* 對話方塊中，[上次重新整理]\*\*\*\* 會顯示上次資料表重新整理的日期。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-153">In the **Edit Table Properties** dialog box, **Last Refreshed** shows the last date that the table was refreshed.</span></span>  
  
##  <a name="restrictions-on-refreshable-data-sources"></a><a name="bkmk_restrictions"></a><span data-ttu-id="fa7a5-154">可重新整理資料來源的限制</span><span class="sxs-lookup"><span data-stu-id="fa7a5-154">Restrictions on Refreshable Data Sources</span></span>  
 <span data-ttu-id="fa7a5-155">可從 Analysis Services 執行個體之已部署模型自動處理的資料來源具有一些限制。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-155">Some restrictions apply to the data sources that can be automatically processed from a deployed model on an Analysis Services instance.</span></span> <span data-ttu-id="fa7a5-156">請務必只選取符合下列準則的資料來源：</span><span class="sxs-lookup"><span data-stu-id="fa7a5-156">Be sure to select only those data sources that meet the following criteria:</span></span>  
  
-   <span data-ttu-id="fa7a5-157">資料來源必須在執行資料處理時可使用，並且在指定的位置也可使用。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-157">The data source must be available at the time that data process occurs and available at the stated location.</span></span> <span data-ttu-id="fa7a5-158">如果原始資料來源是位於製作模型之使用者的本機磁碟機上，則必須從資料處理作業排除該資料來源，或設法將該資料來源發佈至可透過網路連接存取的位置。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-158">If the original data source is on a local disk drive of the user who authored the model, you must either exclude that data source from the data process operation, or find a way to publish that data source to a location that is accessible through a network connection.</span></span> <span data-ttu-id="fa7a5-159">如果您將資料來源移至某個網路位置，請務必在模型設計師中開啟模型，並重複資料擷取步驟。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-159">If you move a data source to a network location, be sure to open the model in the model designer and repeat the data retrieval steps.</span></span> <span data-ttu-id="fa7a5-160">這是重新建立儲存在資料來源連接屬性的連接資訊所必須執行的動作。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-160">This is necessary to re-establish the connection information that is stored in the data source connection properties.</span></span>  
  
-   <span data-ttu-id="fa7a5-161">您必須使用內嵌在資料來源連接中的認證，來存取資料來源。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-161">The data source must be accessed using the credentials that are embedded in the data source connection.</span></span> <span data-ttu-id="fa7a5-162">當您連接至外部資料來源時，會在資料來源連接中建立內嵌認證。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-162">Embedded credentials are created in the data source connection when you connect to the external data source.</span></span>  
  
-   <span data-ttu-id="fa7a5-163">您指定的所有資料來源都必須能夠順利執行資料處理。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-163">Data process must succeed for all of the data sources that you specify.</span></span> <span data-ttu-id="fa7a5-164">否則，這項作業會捨棄處理的資料，並保留模型最後儲存的版本。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-164">Otherwise, the processed data is discarded, leaving you with the last saved version of the model.</span></span> <span data-ttu-id="fa7a5-165">請排除任何您不確定的資料來源。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-165">Exclude any data sources that you are not sure about.</span></span>  
  
-   <span data-ttu-id="fa7a5-166">資料處理必須不能使模型中的其他資料失效。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-166">Data process must not invalidate other data in your model.</span></span> <span data-ttu-id="fa7a5-167">當您處理資料子集時，請務必了解一旦較新的資料與不是來自相同時間週期的靜態資料彙總後，模型是否仍然為有效。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-167">When you process a subset of your data, it is important that you understand whether the model is still valid once newer data is aggregated with static data that is not from the same time period.</span></span> <span data-ttu-id="fa7a5-168">身為模型設計師，您必須知道資料的相依性，並確定資料處理是否適用於模型本身。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-168">As a model designer, it is up to you to know your data dependencies and ensure that data process is appropriate for the model itself.</span></span>  
  
     <span data-ttu-id="fa7a5-169">外部資料來源是透過您指定的內嵌連接字串、URL 或 UNC 路徑來存取，這些是您在使用 [資料表匯入精靈]，將原始資料匯入模型時所指定。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-169">An external data source is accessed through an embedded connection string, URL, or UNC path that you specified when you imported the original data into the model using the Table Import Wizard.</span></span> <span data-ttu-id="fa7a5-170">儲存在資料來源連接中的原始連接資訊，會在後續的資料重新整理作業中重複使用。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-170">Original connection information that is stored in the data source connection is reused for subsequent data refresh operations.</span></span> <span data-ttu-id="fa7a5-171">不需要為資料處理目的建立和管理不同的連接資訊，只會使用現有的連接資訊。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-171">There is no separate connection information that is created and managed for data process purposes; only existing connection information is used.</span></span>  
  
##  <a name="restrictions-on-changes-to-a-data-source"></a><a name="bkmk_rest_changes"></a><span data-ttu-id="fa7a5-172">對資料來源所做之變更的限制</span><span class="sxs-lookup"><span data-stu-id="fa7a5-172">Restrictions on Changes to a Data Source</span></span>  
 <span data-ttu-id="fa7a5-173">針對您可以對資料來源所做的變更有一些限制：</span><span class="sxs-lookup"><span data-stu-id="fa7a5-173">There are some restrictions on the changes that you can make to a data source:</span></span>  
  
-   <span data-ttu-id="fa7a5-174">資料行的資料類型只能變更為相容的資料類型。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-174">The data types of a column can only be changed to a compatible data type.</span></span> <span data-ttu-id="fa7a5-175">例如，如果資料行中的資料包含十進位數字，您無法將資料類型變更為整數。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-175">For example, if the data in the column includes decimal numbers, you cannot change the data type to an integer.</span></span> <span data-ttu-id="fa7a5-176">不過，您可以將數值資料變更為文字。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-176">However, you can change numeric data to text.</span></span> <span data-ttu-id="fa7a5-177">如需資料類型的詳細資訊，請參閱[支援的資料類型 &#40;SSAS 表格式&#41;](tabular-models/data-types-supported-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-177">For more information about data types, see [Data Types Supported &#40;SSAS Tabular&#41;](tabular-models/data-types-supported-ssas-tabular.md).</span></span>  
  
-   <span data-ttu-id="fa7a5-178">您無法在不同的資料表中複選資料行，並變更這些資料行的內容。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-178">You cannot multi-select columns in different tables and change properties of the columns.</span></span> <span data-ttu-id="fa7a5-179">您一次只能使用一個資料表或檢視表。</span><span class="sxs-lookup"><span data-stu-id="fa7a5-179">You can work with only one table or view at a time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa7a5-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa7a5-180">See Also</span></span>  
 <span data-ttu-id="fa7a5-181">[手動處理 &#40;SSAS 表格式&#41;的資料](manually-process-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="fa7a5-181">[Manually Process Data &#40;SSAS Tabular&#41;](manually-process-data-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="fa7a5-182">編輯現有的資料來源連接 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="fa7a5-182">Edit an Existing Data Source Connection &#40;SSAS Tabular&#41;</span></span>](edit-an-existing-data-source-connection-ssas-tabular.md)  
  
  
