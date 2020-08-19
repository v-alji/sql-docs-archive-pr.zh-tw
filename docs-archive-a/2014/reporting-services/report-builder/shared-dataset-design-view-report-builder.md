---
title: 共用資料集設計檢視 (報表產生器) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 47c502da-d163-45d9-bf04-0849e5ba7929
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4a3c34b984ab3aca5bbd6313d088695f22ef2255
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593316"
---
# <a name="shared-dataset-design-view-report-builder"></a><span data-ttu-id="d0427-102">共用資料集設計檢視 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="d0427-102">Shared Dataset Design View (Report Builder)</span></span>
  <span data-ttu-id="d0427-103">[共用資料集設計] 視窗可協助您建立資料集查詢來與其他人共用。</span><span class="sxs-lookup"><span data-stu-id="d0427-103">The Shared Dataset Design window helps you create a dataset query that you can share with others.</span></span> <span data-ttu-id="d0427-104">此視窗可讓您選取共用資料來源、指定共用資料集的屬性，以及在查詢設計工具中建立查詢。</span><span class="sxs-lookup"><span data-stu-id="d0427-104">The window lets you select a shared data source, specify properties for the shared dataset, and create a query in the query designer.</span></span>  
  
 <span data-ttu-id="d0427-105">![rs_SharedDatasetDesignMode](../media/rs-shareddatasetdesignmode.gif "rs_SharedDatasetDesignMode")</span><span class="sxs-lookup"><span data-stu-id="d0427-105">![rs_SharedDatasetDesignMode](../media/rs-shareddatasetdesignmode.gif "rs_SharedDatasetDesignMode")</span></span>  
  
 <span data-ttu-id="d0427-106">如需有關在報表中使用資料的詳細資訊，請參閱 [將資料加入至報表 &#40;Report Builder 和 SSRS&#41;](../report-data/report-datasets-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="d0427-106">For more information about working with data in a report, see [Add Data to a Report &#40;Report Builder and SSRS&#41;](../report-data/report-datasets-ssrs.md).</span></span>  
  
##  <a name="the-ribbon"></a><a name="Ribbon"></a> <span data-ttu-id="d0427-107">功能區</span><span class="sxs-lookup"><span data-stu-id="d0427-107">The Ribbon</span></span>  
 <span data-ttu-id="d0427-108">[功能區] 可協助您快速找到完成工作所需的命令。</span><span class="sxs-lookup"><span data-stu-id="d0427-108">The Ribbon helps you quickly find the commands that you need to complete a task.</span></span> <span data-ttu-id="d0427-109">命令會分成下列邏輯群組：連接、資料集和查詢設計工具。</span><span class="sxs-lookup"><span data-stu-id="d0427-109">Commands are organized into the following logical groups: Connection, Dataset, and Query Designer.</span></span>  
  
### <a name="connection"></a><span data-ttu-id="d0427-110">Connection</span><span class="sxs-lookup"><span data-stu-id="d0427-110">Connection</span></span>  
 <span data-ttu-id="d0427-111">使用 [連接] 群組中的 **[選取]** 按鈕，可選取報表中的共用資料來源，或瀏覽到報表伺服器上的共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="d0427-111">Use the **Select** button in the Connection group to select a shared data source in your report, or browse to a shared data source on the report server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d0427-112">共用資料集必須以共用資料來源為基礎。</span><span class="sxs-lookup"><span data-stu-id="d0427-112">A shared dataset must be based on a shared data source.</span></span> <span data-ttu-id="d0427-113">如果您需要的資料來源無法使用，就必須在報表伺服器上建立一個資料來源。</span><span class="sxs-lookup"><span data-stu-id="d0427-113">If the data source that you need is not available, you must create one on the report server.</span></span> <span data-ttu-id="d0427-114">如需詳細資訊，請參閱《線上叢書》中 Reporting Services 檔集的[建立、刪除或修改共用資料來源 &#40;報表管理員&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md) [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [ ](https://go.microsoft.com/fwlink/?linkid=121312)。</span><span class="sxs-lookup"><span data-stu-id="d0427-114">For more information, see [Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md) in the Reporting Services documentation in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  
 <span data-ttu-id="d0427-115">如需詳細資訊，請參閱＜ [資料連接、資料來源及連接字串](../data-connections-data-sources-and-connection-strings-in-report-builder.md)＞。</span><span class="sxs-lookup"><span data-stu-id="d0427-115">For more information, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
### <a name="dataset"></a><span data-ttu-id="d0427-116">資料集</span><span class="sxs-lookup"><span data-stu-id="d0427-116">Dataset</span></span>  
 <span data-ttu-id="d0427-117">使用 **[設定選項]** 按鈕可設定共用資料集屬性。</span><span class="sxs-lookup"><span data-stu-id="d0427-117">Use the **Set Options** button to set shared dataset properties.</span></span> <span data-ttu-id="d0427-118">這些選項包括：</span><span class="sxs-lookup"><span data-stu-id="d0427-118">These include the following:</span></span>  
  
-   <span data-ttu-id="d0427-119">欄位。</span><span class="sxs-lookup"><span data-stu-id="d0427-119">Fields.</span></span> <span data-ttu-id="d0427-120">您可以在欄位集合中加入欄位或編輯欄位。</span><span class="sxs-lookup"><span data-stu-id="d0427-120">You can add a field or edit a field in the field collection.</span></span>  
  
-   <span data-ttu-id="d0427-121">資料選項。</span><span class="sxs-lookup"><span data-stu-id="d0427-121">Data options.</span></span> <span data-ttu-id="d0427-122">您可以設定選項來影響比對準則和排序順序，例如區分大小寫和定序。</span><span class="sxs-lookup"><span data-stu-id="d0427-122">You can set options that affect match criteria and sort order, such as case sensitivity and collation.</span></span>  
  
-   <span data-ttu-id="d0427-123">篩選器。</span><span class="sxs-lookup"><span data-stu-id="d0427-123">Filters.</span></span> <span data-ttu-id="d0427-124">您可以定義篩選器，在從資料連接擷取資料後，限制出現在報表中的資料。</span><span class="sxs-lookup"><span data-stu-id="d0427-124">You can define filters that limit the data in a report after it is retrieved from the data connection.</span></span>  
  
-   <span data-ttu-id="d0427-125">參數。</span><span class="sxs-lookup"><span data-stu-id="d0427-125">Parameters.</span></span> <span data-ttu-id="d0427-126">您可以加入參數或編輯參數選項。</span><span class="sxs-lookup"><span data-stu-id="d0427-126">You can add a parameter or edit parameter options.</span></span> <span data-ttu-id="d0427-127">例如，您可以為每個參數指定預設值，以便為報表伺服器上的這個共用資料集建立快取重新整理計劃。</span><span class="sxs-lookup"><span data-stu-id="d0427-127">For example, you can specify a default value for each parameter so that you can create a cache refresh plan for this shared dataset on the report server.</span></span>  
  
 <span data-ttu-id="d0427-128">您設定的值會變成報表伺服器上共用資料集定義的一部分。</span><span class="sxs-lookup"><span data-stu-id="d0427-128">The values that you set become part of the shared dataset definition on the report server.</span></span> <span data-ttu-id="d0427-129">當報表作者在報表中包含這個共用資料集時，您指定的選項會套用到該資料集執行個體。</span><span class="sxs-lookup"><span data-stu-id="d0427-129">When a report author includes this shared dataset in a report, the options that you specify apply to that dataset instance.</span></span>  
  
 <span data-ttu-id="d0427-130">將共用資料集加入報表後，報表作者可以覆寫下列選項：定序、區分大小寫、區分腔調字、區分假名、區分全半形、小計。</span><span class="sxs-lookup"><span data-stu-id="d0427-130">After a shared dataset is added to a report, a report author can override the following options: collation, case sensitivity, accent sensitivity, kanatype sensitivity, width sensitivity, subtotals.</span></span> <span data-ttu-id="d0427-131">還可以建立其他資料集篩選器來限制報表中的資料。</span><span class="sxs-lookup"><span data-stu-id="d0427-131">They can also create additional dataset filters to limit the data in the report.</span></span>  
  
 <span data-ttu-id="d0427-132">如需詳細資訊，請參閱 [報表內嵌資料集和共用資料集 &#40;報表產生器及 SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="d0427-132">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="d0427-133">如需快取重新整理計畫的詳細資訊，請參閱《線上叢書》 Reporting Services 檔中的 [&#40;SSRS&#41;快取共用資料集 ](../report-server/cache-shared-datasets-ssrs.md) [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [ ](https://go.microsoft.com/fwlink/?linkid=121312)。</span><span class="sxs-lookup"><span data-stu-id="d0427-133">For more information about cache refresh plans, see [Cache Shared Datasets &#40;SSRS&#41;](../report-server/cache-shared-datasets-ssrs.md) in the Reporting Services documentation in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  
### <a name="query-designer"></a><span data-ttu-id="d0427-134">查詢設計工具</span><span class="sxs-lookup"><span data-stu-id="d0427-134">Query Designer</span></span>  
 <span data-ttu-id="d0427-135">使用查詢設計工具工具列可協助建立查詢，以指定從資料連接擷取的資料。</span><span class="sxs-lookup"><span data-stu-id="d0427-135">Use the query designer toolbar to help build a query that specifies which data to retrieve from the data connection.</span></span> <span data-ttu-id="d0427-136">您所看到的工具列，會視與資料連接的資料來源類型關聯的查詢設計工具而定。</span><span class="sxs-lookup"><span data-stu-id="d0427-136">The toolbar that you see depends on the query designer that is associated with the data source type from the data connection.</span></span>  
  
 <span data-ttu-id="d0427-137">如需詳細資訊，請參閱從 [外部資料源加入資料 &#40;SSRS&#41;](../report-data/add-data-from-external-data-sources-ssrs.md) 和 [查詢設計工具 &#40;Report Builder&#41;](../query-designers-report-builder.md)中對應至資料來源類型的主題。</span><span class="sxs-lookup"><span data-stu-id="d0427-137">For more information, see the topic that corresponds to the data source type in [Add Data from External Data Sources &#40;SSRS&#41;](../report-data/add-data-from-external-data-sources-ssrs.md) and [Query Designers &#40;Report Builder&#41;](../query-designers-report-builder.md).</span></span>  
  

  
##  <a name="the-query-designer-surface"></a><a name="DesignSurface"></a> <span data-ttu-id="d0427-138">查詢設計工具介面</span><span class="sxs-lookup"><span data-stu-id="d0427-138">The Query Designer Surface</span></span>  
 <span data-ttu-id="d0427-139">查詢設計工具可協助您以外部資料來源所需的語法建立查詢。</span><span class="sxs-lookup"><span data-stu-id="d0427-139">A query designer helps you to build a query in the syntax that is required by the external data source.</span></span>  
  
 <span data-ttu-id="d0427-140">某些資料來源類型提供圖形化查詢設計工具，可用來瀏覽外部資料來源上的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="d0427-140">Some data source types provide a graphical query designer that you can use to explore the metadata on an external data source.</span></span> <span data-ttu-id="d0427-141">您可以用互動方式將名稱從中繼資料窗格拖曳到查詢設計介面，或用互動方式選取要使用的名稱。</span><span class="sxs-lookup"><span data-stu-id="d0427-141">You can interactively drag names from the metadata pane to the query design surface, or interactively select the names to use.</span></span>  
  
 <span data-ttu-id="d0427-142">某些資料來源類型則支援以文字為基礎的查詢設計工具，可用來貼上您已在其他工具 (如 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]) 中建立的查詢。</span><span class="sxs-lookup"><span data-stu-id="d0427-142">Some data source types support a text-based query designer that you can use to paste in queries that you have created in other tools, such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="d0427-143">每種資料來源類型對於在外部資料來源執行的查詢都有特定需求。</span><span class="sxs-lookup"><span data-stu-id="d0427-143">Each data source type has specific requirements for the query that will work against the external data source.</span></span> <span data-ttu-id="d0427-144">如需詳細資訊，請參閱《線上叢書》中&#41;檔集的 [從外部資料源加入資料 &#40;ssrs&#41;](../report-data/add-data-from-external-data-sources-ssrs.md) 和 [Reporting Services &#40;Ssrs Reporting Services 所支援之資料 ](../create-deploy-and-manage-mobile-and-paginated-reports.md) 源的主題 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [ ](https://go.microsoft.com/fwlink/?linkid=121312)。</span><span class="sxs-lookup"><span data-stu-id="d0427-144">For more information, see the topic that corresponds to the data source type in [Add Data from External Data Sources &#40;SSRS&#41;](../report-data/add-data-from-external-data-sources-ssrs.md) and [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the Reporting Services documentation in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  

  
##  <a name="viewing-query-results"></a><a name="Results"></a> <span data-ttu-id="d0427-145">查看查詢結果</span><span class="sxs-lookup"><span data-stu-id="d0427-145">Viewing Query Results</span></span>  
 <span data-ttu-id="d0427-146">在共用資料集設計檢視中，您所建立的查詢會在處理報表時，從資料連接擷取資料。</span><span class="sxs-lookup"><span data-stu-id="d0427-146">In shared dataset design view, you are building a query that will retrieve data from the data connection when the report is processed.</span></span>  
  
 <span data-ttu-id="d0427-147">請執行查詢以查看資料連接傳回的範例資料，以確認查詢傳回您所要的資料類型。</span><span class="sxs-lookup"><span data-stu-id="d0427-147">Run the query to see example data from the data connection to verify that the query returns the type of data that you expect.</span></span> <span data-ttu-id="d0427-148">結果集中的資料行來自於資料連接傳回之資料結構描述的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="d0427-148">The columns in the result set come from the metadata for data schemas from the data connection.</span></span> <span data-ttu-id="d0427-149">資料行名稱會變成資料集欄位集合。</span><span class="sxs-lookup"><span data-stu-id="d0427-149">The column names become the dataset field collection.</span></span> <span data-ttu-id="d0427-150">您在查詢結果集中看到的資料值是設計階段資料。</span><span class="sxs-lookup"><span data-stu-id="d0427-150">The values of the data that you see in the query result set is design time data.</span></span> <span data-ttu-id="d0427-151">將共用資料集儲存成報表伺服器上的共用資料集定義之後，只會儲存查詢文字。</span><span class="sxs-lookup"><span data-stu-id="d0427-151">After you save the shared dataset as a shared dataset definition on the report server, only the query text is saved.</span></span> <span data-ttu-id="d0427-152">查詢結果集中的資料不會儲存。</span><span class="sxs-lookup"><span data-stu-id="d0427-152">The data in the query result set is not saved.</span></span>  
  
 <span data-ttu-id="d0427-153">當報表作者將這個共用資料集加入到報表時，會加入指向報表伺服器上資料集定義的指標。</span><span class="sxs-lookup"><span data-stu-id="d0427-153">When a report author adds this shared dataset to a report, a pointer to the dataset definition on the report server is added.</span></span> <span data-ttu-id="d0427-154">在報表中，資料集欄位集合會出現在 [報表資料] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="d0427-154">In the report, the dataset field collection appears in the Report Data pane.</span></span> <span data-ttu-id="d0427-155">查詢文字不會出現。</span><span class="sxs-lookup"><span data-stu-id="d0427-155">The query text is not available.</span></span>  
  
 <span data-ttu-id="d0427-156">您用來執行查詢的認證，與用來預覽報表或從報表伺服器執行報表的認證不同。</span><span class="sxs-lookup"><span data-stu-id="d0427-156">The credentials that you use to run a query are separate from the credentials that are used to preview a report or to run a report from the report server.</span></span> <span data-ttu-id="d0427-157">如需詳細資訊，請參閱 [在報表產生器中指定認證](../specify-credentials-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="d0427-157">For more information, see [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
### <a name="running-a-report-with-parameters"></a><span data-ttu-id="d0427-158">使用參數執行報表</span><span class="sxs-lookup"><span data-stu-id="d0427-158">Running a Report with Parameters</span></span>  
 <span data-ttu-id="d0427-159">當您的查詢包含查詢變數時，系統會自動建立資料集參數。</span><span class="sxs-lookup"><span data-stu-id="d0427-159">When your query includes query variables, dataset parameters are created automatically for you.</span></span> <span data-ttu-id="d0427-160">接著，當您完成建立資料集查詢時，系統會自動建立設為資料集參數的報表參數。</span><span class="sxs-lookup"><span data-stu-id="d0427-160">In turn, when you finish building the dataset query, report parameters that are set to dataset parameters are created automatically.</span></span>  
  
 <span data-ttu-id="d0427-161">如果報表包含參數，所有參數都必須具有預設值，然後報表才能自動執行。</span><span class="sxs-lookup"><span data-stu-id="d0427-161">If a report contains parameters, all the parameters must have default values before the report can run automatically.</span></span> <span data-ttu-id="d0427-162">如果某個參數沒有預設值，當您執行報表時，就必須選擇該參數的值，然後按一下 **[執行]** 索引標籤上的 **[檢視報表]** 。</span><span class="sxs-lookup"><span data-stu-id="d0427-162">If a parameter does not have a default value, when you run the report you must choose a value for the parameter, and then click **View Report** on the **Run** tab.</span></span>  
  
 <span data-ttu-id="d0427-163">如需詳細資訊，請參閱 MSDN 上的 [報表參數 &#40;報表產生器和報表設計師&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)類型之報表資料來源為基礎的資料集。</span><span class="sxs-lookup"><span data-stu-id="d0427-163">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).</span></span>  
  

  
##  <a name="saving-the-shared-dataset"></a><a name="Save"></a> <span data-ttu-id="d0427-164">儲存共用資料集</span><span class="sxs-lookup"><span data-stu-id="d0427-164">Saving the Shared Dataset</span></span>  
 <span data-ttu-id="d0427-165">若要儲存建立的查詢，請按一下 **[報表產生器]** 按鈕上的 **[儲存]** 或 **[另存新檔]**。</span><span class="sxs-lookup"><span data-stu-id="d0427-165">To save the query that you built, on the **Report Builder** button, click **Save** or **Save As**.</span></span> <span data-ttu-id="d0427-166">瀏覽至報表伺服器上適當的資料夾，然後儲存共用資料集定義。</span><span class="sxs-lookup"><span data-stu-id="d0427-166">Navigate to the appropriate folder on the report server and save the shared dataset definition.</span></span> <span data-ttu-id="d0427-167">除非將共用資料集儲存在報表伺服器上，否則其他人將無法使用它。</span><span class="sxs-lookup"><span data-stu-id="d0427-167">The shared dataset is not available to others until you save it to the report server.</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="d0427-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0427-168">See Also</span></span>  
 <span data-ttu-id="d0427-169">[將資料加入至報表 &#40;Report Builder 和 SSRS&#41;](../report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d0427-169">[Add Data to a Report &#40;Report Builder and SSRS&#41;](../report-data/report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="d0427-170">[篩選、分組和排序資料 &#40;報表產生器及 SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d0427-170">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="d0427-171">報表參數 &#40;報表產生器和報表設計師&#41;</span><span class="sxs-lookup"><span data-stu-id="d0427-171">Report Parameters &#40;Report Builder and Report Designer&#41;</span></span>](../report-design/report-parameters-report-builder-and-report-designer.md)  
  
  
