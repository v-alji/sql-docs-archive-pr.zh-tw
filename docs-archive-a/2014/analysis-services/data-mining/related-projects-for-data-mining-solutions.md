---
title: 資料採礦解決方案的相關專案 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: dc26489a-4c27-4b89-8215-6d245427c350
author: minewiskan
ms.author: owend
ms.openlocfilehash: fc0f235871607363b436867d44affd561876bf1e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606497"
---
# <a name="related-projects-for-data-mining-solutions"></a><span data-ttu-id="303d7-102">資料採礦方案的相關專案</span><span class="sxs-lookup"><span data-stu-id="303d7-102">Related Projects for Data Mining Solutions</span></span>
  <span data-ttu-id="303d7-103">資料採礦方案至少需要資料採礦專案，專案中會定義資料來源、資料來源檢視、採礦結構和採礦模型。</span><span class="sxs-lookup"><span data-stu-id="303d7-103">The minimum that is required for a data mining solution is the data mining project, which defines data sources, data source views, mining structures and mining models.</span></span> <span data-ttu-id="303d7-104">但是，當使用資料採礦模型進行每日決策時，資料採礦一定要與預測性分析方案的其他部分整合，該方案可包含這些程序和元件：</span><span class="sxs-lookup"><span data-stu-id="303d7-104">However, when data mining models are used in daily decision making, it is important that data mining be integrated with other part of a predictive analytics solution, which can include these processes and components:</span></span>  
  
-   <span data-ttu-id="303d7-105">準備及選取資料和變數。</span><span class="sxs-lookup"><span data-stu-id="303d7-105">Preparation and selection of data and of variables.</span></span> <span data-ttu-id="303d7-106">包括資料清理、中繼資料管理及整合多個資料來源，以及將資料轉換、合併和上傳到資料倉儲中。</span><span class="sxs-lookup"><span data-stu-id="303d7-106">Includes data cleansing, metadata management and integration of multiple data sources, and the conversion, merging, and uploading of data into a data warehouse.</span></span>  
  
-   <span data-ttu-id="303d7-107">報告分析、呈現預測及稽核/追蹤資料採礦活動。</span><span class="sxs-lookup"><span data-stu-id="303d7-107">Reporting of analysis, presentation of predictions, and auditing/tracking of data mining activities.</span></span>  
  
-   <span data-ttu-id="303d7-108">使用多維度模型或表格式模型來探索各種發現。</span><span class="sxs-lookup"><span data-stu-id="303d7-108">Using multidimensional models or tabular models to explore findings.</span></span>  
  
-   <span data-ttu-id="303d7-109">調整資料採礦方案來支援新的資料，或是目前分析所驅使之支援基礎結構的變更。</span><span class="sxs-lookup"><span data-stu-id="303d7-109">Refinement of the data mining solution to support new data, or changes in the support infrastructure driven by current analysis.</span></span>  
  
 <span data-ttu-id="303d7-110">本主題描述 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的其他功能 (這些通常是預測性分析方案的一部分)，以便支援資料準備和資料採礦的處理，或是藉由提供分析和動作工具來支援使用者。</span><span class="sxs-lookup"><span data-stu-id="303d7-110">This topic describes the other features of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] that are often part of a predictive analytics solution, either to support the processes of data preparation and data mining, or to support users by providing tools for analysis and action.</span></span>  
  
 [<span data-ttu-id="303d7-111">Integration Services</span><span class="sxs-lookup"><span data-stu-id="303d7-111">Integration Services</span></span>](#bkmk_SSIS)  
  
 [<span data-ttu-id="303d7-112">Reporting Services</span><span class="sxs-lookup"><span data-stu-id="303d7-112">Reporting Services</span></span>](#bkmk_SSRS)  
  
 [<span data-ttu-id="303d7-113">Data Quality Service</span><span class="sxs-lookup"><span data-stu-id="303d7-113">Data Quality Service</span></span>](#bkmk_DQSetc)  
  
 [<span data-ttu-id="303d7-114">全文檢索搜尋</span><span class="sxs-lookup"><span data-stu-id="303d7-114">Full-Text Search</span></span>](#bkmk_FTSetc)  
  
 [<span data-ttu-id="303d7-115">語意索引</span><span class="sxs-lookup"><span data-stu-id="303d7-115">Semantic Indexing</span></span>](#bkmk_SemSearch)  
  
##  <a name="sql-server-integration-services"></a><a name="bkmk_SSIS"></a> <span data-ttu-id="303d7-116">SQL Server Integration Services</span><span class="sxs-lookup"><span data-stu-id="303d7-116">SQL Server Integration Services</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="303d7-117">提供了資料準備和資料採礦專案定型階段所需的元件與功能。</span><span class="sxs-lookup"><span data-stu-id="303d7-117">provides components and features that are required for the data preparation and training phases of a data mining project.</span></span> <span data-ttu-id="303d7-118">雖然您可以使用類似指令碼的其他工具來執行許多資料清理或準備工作，但是 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 擁有許多資料採礦的優點：</span><span class="sxs-lookup"><span data-stu-id="303d7-118">Although you can perform many data cleansing or preparation tasks by using other tools, such as scripts, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] has numerous advantages for data mining:</span></span>  
  
-   <span data-ttu-id="303d7-119">將工作表示為工作流程的一部分，工作流程可以重複、自動化、建立分支及擴充。</span><span class="sxs-lookup"><span data-stu-id="303d7-119">Represents tasks as part of a workflow, which can be repeated, automated, branched, and extended.</span></span>  
  
-   <span data-ttu-id="303d7-120">提供稽核的擴充支援以及擷取錯誤和記錄事件的多個方式。</span><span class="sxs-lookup"><span data-stu-id="303d7-120">Provides extensive support for auditing and multiple ways of capturing errors and logging events.</span></span>  
  
     <span data-ttu-id="303d7-121">除了擷取資料歷程之外，您也可以監視整個資料轉換管線中的資料變更。</span><span class="sxs-lookup"><span data-stu-id="303d7-121">In addition to capturing data lineage, you can monitor changes to the data throughout the data transformation pipeline.</span></span>  
  
     <span data-ttu-id="303d7-122">您也可以將 SSIS 工作流程與支援 SQL Server 異動資料擷取功能的功能整合。</span><span class="sxs-lookup"><span data-stu-id="303d7-122">You can also integrate your SSIS workflows with the features that support Change Data Capture functionality in SQL Server.</span></span>  
  
-   <span data-ttu-id="303d7-123">資料採礦可以併入 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 工作流程，以智慧的方式將內送資料分成多個資料表。</span><span class="sxs-lookup"><span data-stu-id="303d7-123">Data mining can be incorporated in the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] workflow, to intelligently separate incoming data into multiple tables.</span></span> <span data-ttu-id="303d7-124">例如，您可能會使用預測查詢將新的客戶分成不同的群組，以便在郵寄促銷活動中鎖定目標客戶。</span><span class="sxs-lookup"><span data-stu-id="303d7-124">For example, you could use a prediction query to split new customers into different groups for targeting in a mailing campaign.</span></span>  
  
 <span data-ttu-id="303d7-125">下列清單提供為了支援資料採礦所最常使用之 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 元件的連結。</span><span class="sxs-lookup"><span data-stu-id="303d7-125">The following lists provide links to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] components that are most widely used in support of data mining.</span></span>  
  
 <span data-ttu-id="303d7-126">**控制流程元件**</span><span class="sxs-lookup"><span data-stu-id="303d7-126">**Control Flow Components**</span></span>  
  
-   [<span data-ttu-id="303d7-127">Analysis Services 執行 DDL 工作</span><span class="sxs-lookup"><span data-stu-id="303d7-127">Analysis Services Execute DDL Task</span></span>](../../integration-services/control-flow/analysis-services-execute-ddl-task.md)  
  
-   [<span data-ttu-id="303d7-128">Analysis Services 處理工作</span><span class="sxs-lookup"><span data-stu-id="303d7-128">Analysis Services Processing Task</span></span>](../../integration-services/control-flow/analysis-services-processing-task.md)  
  
-   [<span data-ttu-id="303d7-129">CDC 控制工作</span><span class="sxs-lookup"><span data-stu-id="303d7-129">CDC Control Task</span></span>](../../integration-services/control-flow/cdc-control-task.md)  
  
-   [<span data-ttu-id="303d7-130">資料清理</span><span class="sxs-lookup"><span data-stu-id="303d7-130">Data Cleansing</span></span>](../../data-quality-services/data-cleansing.md)  
  
-   [<span data-ttu-id="303d7-131">資料採礦查詢工作</span><span class="sxs-lookup"><span data-stu-id="303d7-131">Data Mining Query Task</span></span>](../../integration-services/control-flow/data-mining-query-task.md)  
  
-   [<span data-ttu-id="303d7-132">資料分析工作</span><span class="sxs-lookup"><span data-stu-id="303d7-132">Data Profiling Task</span></span>](../../integration-services/control-flow/data-profiling-task.md)  
  
 <span data-ttu-id="303d7-133">**資料流程元件**</span><span class="sxs-lookup"><span data-stu-id="303d7-133">**Data Flow Components**</span></span>  
  
-   [<span data-ttu-id="303d7-134">CDC 流程元件</span><span class="sxs-lookup"><span data-stu-id="303d7-134">CDC Flow Components</span></span>](../../integration-services/data-flow/cdc-flow-components.md)  
  
-   [<span data-ttu-id="303d7-135">條件式分割轉換</span><span class="sxs-lookup"><span data-stu-id="303d7-135">Conditional Split Transformation</span></span>](../../integration-services/data-flow/transformations/conditional-split-transformation.md)  
  
-   [<span data-ttu-id="303d7-136">資料轉換</span><span class="sxs-lookup"><span data-stu-id="303d7-136">Data Conversion Transformation</span></span>](../../integration-services/data-flow/transformations/data-conversion-transformation.md)  
  
-   [<span data-ttu-id="303d7-137">資料採礦模型訓練目的地</span><span class="sxs-lookup"><span data-stu-id="303d7-137">Data Mining Model Training Destination</span></span>](../../integration-services/data-flow/data-mining-model-training-destination.md)  
  
-   [<span data-ttu-id="303d7-138">資料採礦查詢轉換</span><span class="sxs-lookup"><span data-stu-id="303d7-138">Data Mining Query Transformation</span></span>](../../integration-services/data-flow/transformations/data-mining-query-transformation.md)  
  
-   [<span data-ttu-id="303d7-139">衍生的資料行轉換</span><span class="sxs-lookup"><span data-stu-id="303d7-139">Derived Column Transformation</span></span>](../../integration-services/data-flow/transformations/derived-column-transformation.md)  
  
-   [<span data-ttu-id="303d7-140">百分比取樣轉換</span><span class="sxs-lookup"><span data-stu-id="303d7-140">Percentage Sampling Transformation</span></span>](../../integration-services/data-flow/transformations/percentage-sampling-transformation.md)  
  
-   [<span data-ttu-id="303d7-141">詞彙擷取轉換</span><span class="sxs-lookup"><span data-stu-id="303d7-141">Term Extraction Transformation</span></span>](../../integration-services/data-flow/transformations/term-extraction-transformation.md)  
  
-   [<span data-ttu-id="303d7-142">詞彙查閱轉換</span><span class="sxs-lookup"><span data-stu-id="303d7-142">Term Lookup Transformation</span></span>](../../integration-services/data-flow/transformations/lookup-transformation.md)  
  
##  <a name="sql-server-reporting-services"></a><a name="bkmk_SSRS"></a> <span data-ttu-id="303d7-143">SQL Server Reporting Services</span><span class="sxs-lookup"><span data-stu-id="303d7-143">SQL Server Reporting Services</span></span>  
 <span data-ttu-id="303d7-144">雖然 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 通常不會被視為資料採礦方案的重要元件，但是它會提供對於呈現資料採礦方案非常實用的以下功能。</span><span class="sxs-lookup"><span data-stu-id="303d7-144">Although [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is typically not seen as a critical component of data mining solutions, it provides the following features that are useful for presentation of data mining solutions.</span></span>  
  
-   <span data-ttu-id="303d7-145">在複雜的報表中整合多個來源的資料。</span><span class="sxs-lookup"><span data-stu-id="303d7-145">Integration of data from multiple sources in complex reports.</span></span> <span data-ttu-id="303d7-146">針對模型內容來為分析師建立查詢，並為使用者建立報表，報表中會顯示預測和趨勢。</span><span class="sxs-lookup"><span data-stu-id="303d7-146">Create queries against the model content for analysts, and reports that show predictions and trends for end users.</span></span>  
  
-   <span data-ttu-id="303d7-147">建立報表的功能，該報表可讓使用者直接針對現有採礦模型進行查詢。</span><span class="sxs-lookup"><span data-stu-id="303d7-147">The ability to create a report that lets users directly query against an existing mining model.</span></span>  
  
-   <span data-ttu-id="303d7-148">與 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]整合，以便支援鑽研和瀏覽資料採礦維度及從 OLAP 模型建立而來的資料採礦 Cube。</span><span class="sxs-lookup"><span data-stu-id="303d7-148">Integration with [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], to support drillthrough and exploration of data mining dimensions and data mining cubes created from OLAP models.</span></span>  
  
-   <span data-ttu-id="303d7-149">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]中所提供的參數化和格式化功能。</span><span class="sxs-lookup"><span data-stu-id="303d7-149">parameterization and formatting features that are available in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="303d7-150">如需有關如何搭配資料來源形式的 DMX 查詢使用 Reporting Services 的詳細資訊，請參閱以下連結：</span><span class="sxs-lookup"><span data-stu-id="303d7-150">For more information about how to use Reporting Services with DMX queries as a data source, see these links:</span></span>  
  
 [<span data-ttu-id="303d7-151">從資料採礦模型擷取資料 &#40;DMX&#41; &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="303d7-151">Retrieve Data from a Data Mining Model &#40;DMX&#41; &#40;SSRS&#41;</span></span>](../../reporting-services/report-data/retrieve-data-from-a-data-mining-model-dmx-ssrs.md)  
  
 [<span data-ttu-id="303d7-152">Analysis Services DMX 查詢設計工具使用者介面</span><span class="sxs-lookup"><span data-stu-id="303d7-152">Analysis Services DMX Query Designer User Interface</span></span>](../../reporting-services/report-data/analysis-services-dmx-query-designer-user-interface.md)  
  
 [<span data-ttu-id="303d7-153">Analysis Services Connection Type for DMX &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="303d7-153">Analysis Services Connection Type for DMX &#40;SSRS&#41;</span></span>](../../reporting-services/report-data/analysis-services-connection-type-for-dmx-ssrs.md)  
  
 <span data-ttu-id="303d7-154">但是，使用 DMX 當做資料來源並不是必要的。</span><span class="sxs-lookup"><span data-stu-id="303d7-154">However, it is not necessary to use DMX as the data source.</span></span> <span data-ttu-id="303d7-155">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 的資料採礦元件也支援將預測查詢結果儲存到關聯式資料庫。</span><span class="sxs-lookup"><span data-stu-id="303d7-155">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] components for data mining also support saving the results of a prediction query to a relational database.</span></span> <span data-ttu-id="303d7-156">如果您已經使用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]建立更新模型的工作流程，則將預測和其他資料採礦查詢結果保存到 SQL Server 可讓您啟用報告用的 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 以及不與 DMX 接觸的其他工具。</span><span class="sxs-lookup"><span data-stu-id="303d7-156">If you have an established workflow for updating models using [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], persisting predictions and other data mining query results to SQL Server enable you to use [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] for reporting, as well as other tools that do not interface with DMX.</span></span>  
  
 <span data-ttu-id="303d7-157">如需有關使用 Reporting Services 當做資料來源展示層的詳細資訊，請參閱＜ [Integrating Reporting Services into Applications](../../reporting-services/application-integration/integrating-reporting-services-into-applications.md)＞。</span><span class="sxs-lookup"><span data-stu-id="303d7-157">For more information about using Reporting Services as the presentation layer for data sources, see [Integrating Reporting Services into Applications](../../reporting-services/application-integration/integrating-reporting-services-into-applications.md).</span></span>  
  
##  <a name="data-quality-services"></a><a name="bkmk_DQSetc"></a><span data-ttu-id="303d7-158">Data Quality Services</span><span class="sxs-lookup"><span data-stu-id="303d7-158">Data Quality Services</span></span>  
 <span data-ttu-id="303d7-159">Data Quality Services (DQS) 是 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中的新功能。</span><span class="sxs-lookup"><span data-stu-id="303d7-159">Data Quality Services (DQS) is new in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="303d7-160">因為資料問題可能會讓資料採礦無法進行，所以執行重複分析或是在大型組織處理複雜資料來源的資料採礦人員應該會發現，使用 DQS 的規劃完善資料專案比起使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 或其他指令碼隨選清理資料，為支援資料採礦的一個更可靠的方案。</span><span class="sxs-lookup"><span data-stu-id="303d7-160">Because data problems can make data mining impossible, data miners who perform repeated analysis or who work in large organizations with complex data sources are expected to find that a well-planned data project using DQS is a more reliable solution for support of data mining than ad hoc cleansing of data using [!INCLUDE[tsql](../../includes/tsql-md.md)] or other scripts.</span></span>  
  
 <span data-ttu-id="303d7-161">資料採礦方案中的資料準備與資料完整性中，應該考量下列 DQS 功能。</span><span class="sxs-lookup"><span data-stu-id="303d7-161">The following features of DQS should be considered for data preparation and data integrity in a data mining solution.</span></span>  
  
 <span data-ttu-id="303d7-162">**電腦輔助的資料清理程序，可分析來源資料及建議變更。**</span><span class="sxs-lookup"><span data-stu-id="303d7-162">**A computer-assisted data cleansing process that analyzes source data and proposes changes.**</span></span>  
 <span data-ttu-id="303d7-163">DQS 可以將來源資料與資料品質提供者所維護和保證的雲端架構參考資料做比較。</span><span class="sxs-lookup"><span data-stu-id="303d7-163">DQS can compare source data with cloud-based reference data maintained and guaranteed by data quality providers.</span></span>  
  
 <span data-ttu-id="303d7-164">DQS 可以分析原始來源資料，並從使用者資料建立知識庫。</span><span class="sxs-lookup"><span data-stu-id="303d7-164">DQS can also analyze raw source data and create a knowledge base from user data.</span></span> <span data-ttu-id="303d7-165">處理過的資料會加以分類，然後顯示給使用者以供進一步處理。</span><span class="sxs-lookup"><span data-stu-id="303d7-165">The processed data is categorized and then displayed to the user for further processing.</span></span> <span data-ttu-id="303d7-166">清理程序為互動式，這表示資料監管可以核准、拒絕或修改電腦輔助的資料清理程序所提議的資料。</span><span class="sxs-lookup"><span data-stu-id="303d7-166">The cleansing process is interactive, meaning the data steward can approve, reject, or modify the data proposed by the computer-assisted data cleansing process.</span></span>  
  
 <span data-ttu-id="303d7-167">此程序的結果為知識庫，您可以在多個資料增強階段持續改良或重複使用此知識庫。</span><span class="sxs-lookup"><span data-stu-id="303d7-167">The outcome of the process is a knowledge base that you can continuously improve, or reuse in multiple data-enhancement phases.</span></span>  
  
 <span data-ttu-id="303d7-168">如需詳細資訊，請參閱 [Data Cleansing](../../data-quality-services/data-cleansing.md)。</span><span class="sxs-lookup"><span data-stu-id="303d7-168">For more information, see [Data Cleansing](../../data-quality-services/data-cleansing.md).</span></span>  
  
 <span data-ttu-id="303d7-169">**電腦輔助的比對程序，可分析來源資料及建議變更。**</span><span class="sxs-lookup"><span data-stu-id="303d7-169">**A computer-assisted matching process that analyzes source data and proposes changes.**</span></span>  
 <span data-ttu-id="303d7-170">為了避免資料重複，您可以執行資料來源的額外清理，以識別完全相符和大致相符的項目。</span><span class="sxs-lookup"><span data-stu-id="303d7-170">To prevent data duplication, you can perform addition cleansing of the data source, to identify exact and approximate matches.</span></span> <span data-ttu-id="303d7-171">這些元件可讓您指定比對規則以及套用規則的臨界值。</span><span class="sxs-lookup"><span data-stu-id="303d7-171">These components let you specify the matching rules, and the thresholds at which to apply them.</span></span>  
  
 <span data-ttu-id="303d7-172">您可以藉由尋找資料相符項目來移除重複項目，因為重複項目可能會讓資料採礦發生問題。</span><span class="sxs-lookup"><span data-stu-id="303d7-172">By finding data matches, you can remove duplicates, which can be a problem for data mining.</span></span> <span data-ttu-id="303d7-173">刪除重複資料作業不會自動進行；資料監管或 IT 專業人員必須驗證知識庫中的知識以及要進行的資料變更。</span><span class="sxs-lookup"><span data-stu-id="303d7-173">Data de-duplication is not automatic; the data steward or IT professional must verify both the knowledge in the knowledge base and the changes to be made to the data.</span></span>  
  
 <span data-ttu-id="303d7-174">在您建立初始 DQS 專案之後，您可以使用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 元件將許多工作自動化。</span><span class="sxs-lookup"><span data-stu-id="303d7-174">After you have created the initial DQS project, you can automate many of the tasks by using [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] components.</span></span>  
  
 <span data-ttu-id="303d7-175">如需詳細資訊，請參閱 [Data Matching](../../data-quality-services/data-matching.md)。</span><span class="sxs-lookup"><span data-stu-id="303d7-175">For more information, see [Data Matching](../../data-quality-services/data-matching.md).</span></span>  
  
 <span data-ttu-id="303d7-176">在資料品質專案中執行清理和比對活動之後，您可以得到有關 DQS 正在處理之資料的即時統計資料和資訊。</span><span class="sxs-lookup"><span data-stu-id="303d7-176">While performing cleansing and matching activities in a data quality project, you can get real-time statistics and information about the data that is being processed by DQS.</span></span> <span data-ttu-id="303d7-177">資料分析會幫助您評估資料清理或比對提升資料品質的程度，並幫助您了解所做的變更。</span><span class="sxs-lookup"><span data-stu-id="303d7-177">Data profiling helps you assess the extent to which data cleansing or matching helped improve the data quality, and understand the changes that were made.</span></span> <span data-ttu-id="303d7-178">如需有關資料分析和通知的詳細資訊，請參閱＜ [Data Profiling and Notifications in DQS](../../data-quality-services/data-profiling-and-notifications-in-dqs.md)＞。</span><span class="sxs-lookup"><span data-stu-id="303d7-178">For information about data profiling and notifications, see [Data Profiling and Notifications in DQS](../../data-quality-services/data-profiling-and-notifications-in-dqs.md).</span></span>  
  
 <span data-ttu-id="303d7-179">**代表三種知識類型的知識庫：現成的知識、DQS 伺服器產生的知識，以及使用者產生的知識。**</span><span class="sxs-lookup"><span data-stu-id="303d7-179">**A knowledge base that represents three types of knowledge: out-of-the-box knowledge, knowledge generated by the DQS server, and knowledge generated by the user.**</span></span>  
 <span data-ttu-id="303d7-180">一旦您建立知識庫之後，就可以反覆使用它來清理和驗證其他資料。</span><span class="sxs-lookup"><span data-stu-id="303d7-180">Once you have created a knowledge base, you can use it iteratively to cleanse and verify other data.</span></span>  
  
 <span data-ttu-id="303d7-181">您可以從多個來源將新的資料匯入知識庫資料中，資料可以是參考提供者的乾淨資料，或是與知識庫中現有資料符合的原始資料。</span><span class="sxs-lookup"><span data-stu-id="303d7-181">You can import new data into the knowledge base data from multiple sources, either known clean data from reference providers, or raw data that is matched to existing data in the knowledge base.</span></span>  
  
 <span data-ttu-id="303d7-182">如需有關資料品質專案中清理活動的詳細資訊，請參閱＜資料清理 (DQS)＞。</span><span class="sxs-lookup"><span data-stu-id="303d7-182">For detailed information about the cleansing activity in a data quality project, see Data Cleansing (DQS).</span></span>  
  
 <span data-ttu-id="303d7-183">您也可以將知識庫中的知識套用到其他來源，在其他程序中執行資料清理。</span><span class="sxs-lookup"><span data-stu-id="303d7-183">You can also apply the knowledge in the knowledge base to other sources, to perform data cleansing within other processes.</span></span> <span data-ttu-id="303d7-184">這類資料清理有助於識別使用者輸入錯誤、傳輸或儲存中的損毀，或是不符的資料字典定義。</span><span class="sxs-lookup"><span data-stu-id="303d7-184">Such data cleansing can help identify user entry errors, corruption in transmission or storage, or mismatched data dictionary definitions.</span></span>  
  
 <span data-ttu-id="303d7-185">如需詳細資訊，請參閱 [DQS Knowledge Bases and Domains](../../data-quality-services/dqs-knowledge-bases-and-domains.md)。</span><span class="sxs-lookup"><span data-stu-id="303d7-185">For more information, see [DQS Knowledge Bases and Domains](../../data-quality-services/dqs-knowledge-bases-and-domains.md).</span></span>  
  
##  <a name="full-text-search"></a><a name="bkmk_FTSetc"></a><span data-ttu-id="303d7-186">全文檢索搜尋</span><span class="sxs-lookup"><span data-stu-id="303d7-186">Full-Text Search</span></span>  
 <span data-ttu-id="303d7-187">SQL Server 中的全文檢索搜尋可讓應用程式和使用者針對 SQL Server 資料表中以字元為主的資料，執行全文檢索查詢。</span><span class="sxs-lookup"><span data-stu-id="303d7-187">Full-Text Search in SQL Server lets applications and users run full-text queries against character-based data in SQL Server tables.</span></span> <span data-ttu-id="303d7-188">當啟用全文檢索搜尋時，您可以針對文字資料執行搜尋，該搜尋是以有關多形式單字或片語的語言特有規則來增強功能。</span><span class="sxs-lookup"><span data-stu-id="303d7-188">When full-text search is enabled, you can perform searches against text data that are enhanced by language-specific rules about the multiple forms of a word or phrase.</span></span> <span data-ttu-id="303d7-189">您也可以設定搜尋條件 (例如多個詞彙之間的距離)，並使用函數來限制依可能性順序傳回的結果。</span><span class="sxs-lookup"><span data-stu-id="303d7-189">You can also configure search conditions, such as the distance between multiple terms, and use functions to constrain the results that are returned in order of likelihood.</span></span>  
  
 <span data-ttu-id="303d7-190">因為全文檢索查詢是 SQL Server 引擎提供的功能，所以您可以建立參數化查詢、使用文字資料來源上的全文檢索搜尋功能來產生自訂資料集或詞彙向量，並在資料採礦中使用這些來源。</span><span class="sxs-lookup"><span data-stu-id="303d7-190">Because full-text queries are a feature provided by the SQL Server engine, you can create parameterized queries, generate custom data sets or term vectors by using full-text search features on a text data source, and use these sources in data mining.</span></span>  
  
 <span data-ttu-id="303d7-191">如需全文檢索查詢如何與全文檢索索引互動的詳細資訊，請參閱 [使用全文檢索搜尋進行查詢](../../relational-databases/search/query-with-full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="303d7-191">For more information about how full-text queries interact with the full-text index, see [Query with Full-Text Search](../../relational-databases/search/query-with-full-text-search.md).</span></span>  
  
 <span data-ttu-id="303d7-192">使用 SQL Server 全文檢索搜尋功能的優點就是可以利用所有 SQL Server 語言隨附之斷詞工具和字幹分析器中所包含的語言智慧。</span><span class="sxs-lookup"><span data-stu-id="303d7-192">An advantage of using the full-text search features of SQL Server is that you can leverage the linguistic intelligence that is contained in the word breakers and stemmers shipped for all SQL Server languages.</span></span> <span data-ttu-id="303d7-193">藉由使用隨附的斷詞工具和字幹分析器，可確保使用適合每種語言的字元來分隔字詞，而且不會忽略以讀音符號或拼字變化為根據的同義字 (例如日文中的多種數字格式)。</span><span class="sxs-lookup"><span data-stu-id="303d7-193">By using the supplied word breakers and stemmers, you can ensure that words are separated using the characters appropriate for each language, and that synonyms based on diacritics or orthographic variations (such as the multiple number formats in Japanese) are not overlooked.</span></span>  
  
 <span data-ttu-id="303d7-194">除了控制字詞界限的語言智慧以外，每一個語言的字幹分析器都會根據該語言中的詞形變化和拼字變化規則知識，將字詞的變化減少成單一詞彙。</span><span class="sxs-lookup"><span data-stu-id="303d7-194">In addition to linguistic intelligence that governs word boundaries, the stemmers for each language can reduce variants of a word to a single term, based on knowledge of the rules for conjugation and orthographic variation in that language.</span></span> <span data-ttu-id="303d7-195">每一種語言的語言分析規則都不一樣，而且會根據實際生活語料庫的大規模研究而發展。</span><span class="sxs-lookup"><span data-stu-id="303d7-195">The rules for linguistic analysis differ for each language and are developed based on extensive research on real-life corpora.</span></span>  
  
 <span data-ttu-id="303d7-196">如需詳細資訊，請參閱 [設定及管理搜尋的斷詞工具與字幹分析器](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)。</span><span class="sxs-lookup"><span data-stu-id="303d7-196">For more information, see [Configure and Manage Word Breakers and Stemmers for Search](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md).</span></span>  
  
 <span data-ttu-id="303d7-197">儲存在全文檢索索引之後的字詞版本為壓縮形式的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="303d7-197">The version of a word that is stored after full-text indexing is a token in compressed form.</span></span> <span data-ttu-id="303d7-198">全文檢索索引後續的查詢會根據該語言的規則產生特定字詞的多個變化形式，以確保能產生所有可能的相符項目。</span><span class="sxs-lookup"><span data-stu-id="303d7-198">Subsequent queries to the full-text index generate multiple inflectional forms of a particular word based on the rules of that language, to ensure that all probable matches are made.</span></span> <span data-ttu-id="303d7-199">例如，雖然儲存的 token 可能是 "run"，但查詢引擎也會尋找「執行中」、「已執行」和「執行器」這兩個詞彙，因為這些會定期衍生根字「回合」的形態變化。</span><span class="sxs-lookup"><span data-stu-id="303d7-199">For example, although the token that is stored might be "run", the query engine also looks for the terms "running", "ran", and "runner," because these are regularly derived morphological variations of the root word "run".</span></span>  
  
 <span data-ttu-id="303d7-200">您也可以建立及產生使用者同義字，以便儲存同義字並啟用更好的搜尋結果或分類詞彙。</span><span class="sxs-lookup"><span data-stu-id="303d7-200">You can also create and build a user thesaurus to store synonyms and enable better search results, or categorization of terms.</span></span> <span data-ttu-id="303d7-201">透過開發符合全文檢索資料的同義字，您可以有效地擴大針對該資料進行全文檢索查詢的範圍。</span><span class="sxs-lookup"><span data-stu-id="303d7-201">By developing a thesaurus tailored to your full-text data, you can effectively broaden the scope of full-text queries on that data.</span></span> <span data-ttu-id="303d7-202">如需詳細資訊，請參閱 [設定及管理全文檢索搜尋的同義字檔案](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="303d7-202">For more information, see [Configure and Manage Thesaurus Files for Full-Text Search](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md).</span></span>  
  
 <span data-ttu-id="303d7-203">使用全文檢索搜尋的需求如下：</span><span class="sxs-lookup"><span data-stu-id="303d7-203">Requirements for using full-text search include the following:</span></span>  
  
-   <span data-ttu-id="303d7-204">資料庫管理員必須在資料表上建立全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="303d7-204">The database administrator must create a full-text index on the table.</span></span>  
  
-   <span data-ttu-id="303d7-205">每個資料表只允許有一個全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="303d7-205">Only one full-text index is allowed per table.</span></span>  
  
-   <span data-ttu-id="303d7-206">您編制索引的每一個資料行必須有唯一的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="303d7-206">Each column that you index must have a unique key.</span></span>  
  
-   <span data-ttu-id="303d7-207">只有以下資料類型的資料行才支援全文檢索索引：char、varchar、nchar、nvarchar、text、ntext、image、xml、varbinary 和 varbinary(max)。</span><span class="sxs-lookup"><span data-stu-id="303d7-207">Full-text indexing is supported only for columns with these data types: char, varchar, nchar, nvarchar, text, ntext, image, xml, varbinary, and varbinary(max).</span></span> <span data-ttu-id="303d7-208">如果資料行為 varbinary、varbinary(max)、image 或 xml，您必須在個別類型資料行中指定可建立索引之文件的副檔名 (.doc、.pdf、.xls 等)。</span><span class="sxs-lookup"><span data-stu-id="303d7-208">If the column is varbinary, varbinary(max), image, or xml, you must specify the file extension of the indexable document (.doc, .pdf, .xls, and so forth), in a separate type column.</span></span>  
  
##  <a name="semantic-indexing"></a><a name="bkmk_SemSearch"></a><span data-ttu-id="303d7-209">語義索引</span><span class="sxs-lookup"><span data-stu-id="303d7-209">Semantic Indexing</span></span>  
 <span data-ttu-id="303d7-210">語意搜尋會根據 SQL Server 中的現有全文檢索搜尋功能而建立，但是會使用其他功能和統計資料來啟用類似自動關鍵字擷取及探索相關文件等案例。</span><span class="sxs-lookup"><span data-stu-id="303d7-210">Semantic search builds upon the existing full-text search features in SQL Server, but uses additional capabilities and statistics to enable scenarios such as automatic keyword extraction and discovery of related documents.</span></span> <span data-ttu-id="303d7-211">例如，您可能會使用語意搜尋來為組織建立基本分類，或是分類某個語料的文件。</span><span class="sxs-lookup"><span data-stu-id="303d7-211">For example, you might use semantic search to build a base taxonomy for an organization, or classify a corpus of documents.</span></span> <span data-ttu-id="303d7-212">或者，您可能會使用群集或決策樹模型中擷取之詞彙和文件相似度分數的組合。</span><span class="sxs-lookup"><span data-stu-id="303d7-212">Or, you could use the combination of extracted terms and document similarity scores in clustering or decision tree models.</span></span>  
  
 <span data-ttu-id="303d7-213">在您成功啟用語意搜尋並將資料行編制索引之後，您可以使用語意索引原本所提供的功能執行以下作業：</span><span class="sxs-lookup"><span data-stu-id="303d7-213">After you have enabled semantic search successfully, and indexed your data columns, you can use the functions that are provided natively with semantic indexing to do the following:</span></span>  
  
-   <span data-ttu-id="303d7-214">傳回單一字詞關鍵片語以及其分數。</span><span class="sxs-lookup"><span data-stu-id="303d7-214">Return single-word key phrases with their score.</span></span>  
  
-   <span data-ttu-id="303d7-215">傳回包含指定之關鍵片語的文件。</span><span class="sxs-lookup"><span data-stu-id="303d7-215">Return documents that contain a specified key phrase.</span></span>  
  
-   <span data-ttu-id="303d7-216">傳回相似度分數以及對分數有貢獻的詞彙。</span><span class="sxs-lookup"><span data-stu-id="303d7-216">Return similarity scores, and the terms that contribute to the score.</span></span>  
  
 <span data-ttu-id="303d7-217">如需詳細資訊，請參閱 [使用語意搜尋找到文件中的主要片語](../../relational-databases/search/find-key-phrases-in-documents-with-semantic-search.md) 和 [使用語意搜尋尋找相似及相關的文件](../../relational-databases/search/find-similar-and-related-documents-with-semantic-search.md)。</span><span class="sxs-lookup"><span data-stu-id="303d7-217">For more information, see [Find Key Phrases in Documents with Semantic Search](../../relational-databases/search/find-key-phrases-in-documents-with-semantic-search.md) and [Find Similar and Related Documents with Semantic Search](../../relational-databases/search/find-similar-and-related-documents-with-semantic-search.md).</span></span>  
  
 <span data-ttu-id="303d7-218">如需支援語意索引之資料庫物件的詳細資訊，請參閱 [在資料表和資料行上啟用語意搜尋](../../relational-databases/search/enable-semantic-search-on-tables-and-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="303d7-218">For more information about the database objects that support semantic indexing, see [Enable Semantic Search on Tables and Columns](../../relational-databases/search/enable-semantic-search-on-tables-and-columns.md).</span></span>  
  
 <span data-ttu-id="303d7-219">使用語意搜尋的需求如下：</span><span class="sxs-lookup"><span data-stu-id="303d7-219">Requirements for using semantic search include the following:</span></span>  
  
-   <span data-ttu-id="303d7-220">也必須啟用全文檢索搜尋。</span><span class="sxs-lookup"><span data-stu-id="303d7-220">Full-text search also be enabled.</span></span>  
  
-   <span data-ttu-id="303d7-221">安裝語意搜尋元件也會建立特殊系統資料庫，該資料庫無法重新命名、更改或取代。</span><span class="sxs-lookup"><span data-stu-id="303d7-221">Installation of the semantic search components also creates a special system database, which cannot be renamed, altered, or replaced.</span></span>  
  
-   <span data-ttu-id="303d7-222">您使用此服務編制索引的文件必須在 SQL Server 中，儲存為全文檢索索引所支援的任何資料庫物件，包括資料表和索引檢視表。</span><span class="sxs-lookup"><span data-stu-id="303d7-222">Documents that you index using the service must be stored in SQL Server, in any of the database objects that are supported for full-text indexing, including tables and indexed views.</span></span>  
  
-   <span data-ttu-id="303d7-223">並非所有全文檢索語言都支援語意索引。</span><span class="sxs-lookup"><span data-stu-id="303d7-223">Not all of the full-text languages support semantic indexing.</span></span> <span data-ttu-id="303d7-224">如需受支援語言的清單，請參閱 [sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="303d7-224">For a list of supported languages, see [sys.fulltext_semantic_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="303d7-225">另請參閱</span><span class="sxs-lookup"><span data-stu-id="303d7-225">See Also</span></span>  
 <span data-ttu-id="303d7-226">[&#40;SSAS&#41;的多維度模型方案](../multidimensional-models/multidimensional-model-solutions-ssas.md) </span><span class="sxs-lookup"><span data-stu-id="303d7-226">[Multidimensional Model Solutions &#40;SSAS&#41;](../multidimensional-models/multidimensional-model-solutions-ssas.md) </span></span>  
 [<span data-ttu-id="303d7-227">表格式模型方案 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="303d7-227">Tabular Model Solutions &#40;SSAS Tabular&#41;</span></span>](../tabular-model-solutions-ssas-tabular.md)  
  
  
