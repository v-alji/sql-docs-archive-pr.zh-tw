---
title: 資料採礦解決方案和物件的管理 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], managing
- managing mining models
ms.assetid: 06fc61dd-925c-4347-8677-7046ee5d2f6f
author: minewiskan
ms.author: owend
ms.openlocfilehash: ae3e672932dd320c6b369f23f03c1f056d30d4ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584845"
---
# <a name="management-of-data-mining-solutions-and-objects"></a><span data-ttu-id="c1a1d-102">資料採礦方案與物件的管理</span><span class="sxs-lookup"><span data-stu-id="c1a1d-102">Management of Data Mining Solutions and Objects</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="c1a1d-103">提供可用於管理現有採礦結構和採礦模型的用戶端工具。</span><span class="sxs-lookup"><span data-stu-id="c1a1d-103">provides client tools that you can use to manage existing mining structures and mining models.</span></span> <span data-ttu-id="c1a1d-104">本節說明可以利用每種環境執行的管理作業。</span><span class="sxs-lookup"><span data-stu-id="c1a1d-104">This section describes the management operations that you can perform using each environment.</span></span>  
  
 <span data-ttu-id="c1a1d-105">除了這些工具以外，您也可以透過下列方式來管理資料採礦物件：程式設計方式、使用 AMO，或使用其他連接至 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫的用戶端，例如適用於 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 2007 的資料採礦增益集。</span><span class="sxs-lookup"><span data-stu-id="c1a1d-105">In addition to these tools, you can manage data mining objects programmatically, by using AMO, or use other clients that connect to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, such as the Data Mining Add-ins for [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 2007.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c1a1d-106">本章節內容</span><span class="sxs-lookup"><span data-stu-id="c1a1d-106">In this Section</span></span>  
 [<span data-ttu-id="c1a1d-107">移動資料採礦物件</span><span class="sxs-lookup"><span data-stu-id="c1a1d-107">Moving Data Mining Objects</span></span>](moving-data-mining-objects.md)  
  
 [<span data-ttu-id="c1a1d-108">處理需求和考量 (資料採礦)</span><span class="sxs-lookup"><span data-stu-id="c1a1d-108">Processing Requirements and Considerations &#40;Data Mining&#41;</span></span>](processing-requirements-and-considerations-data-mining.md)  
  
 [<span data-ttu-id="c1a1d-109">使用 SQL Server Profiler 監視資料採礦 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="c1a1d-109">Using SQL Server Profiler to Monitor Data Mining &#40;Analysis Services - Data Mining&#41;</span></span>](using-sql-server-profiler-to-monitor-data-mining-analysis-services-data-mining.md)  
  
## <a name="location-of-data-mining-objects"></a><span data-ttu-id="c1a1d-110">資料採礦物件的位置</span><span class="sxs-lookup"><span data-stu-id="c1a1d-110">Location of Data Mining Objects</span></span>  
 <span data-ttu-id="c1a1d-111">已經處理的採礦結構和模型會儲存在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]的執行個體中。</span><span class="sxs-lookup"><span data-stu-id="c1a1d-111">Mining structures and models that have been processed are stored in an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="c1a1d-112">如果您在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] `Immediate` 開發資料採礦物件時，在模式中建立資料庫的連接，則您所建立的任何物件都會在您工作時立即加入至伺服器。</span><span class="sxs-lookup"><span data-stu-id="c1a1d-112">If you create a connection to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database in `Immediate` mode when developing your data mining objects, any objects that you create are immediately added to the server as you work.</span></span> <span data-ttu-id="c1a1d-113">不過，如果在 **[離線]** 模式 (也就是在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中作業時的預設值) 中設計資料採礦物件，則您建立的採礦物件在部署到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]的執行個體之前，都只是中繼資料容器。</span><span class="sxs-lookup"><span data-stu-id="c1a1d-113">However, if you design data mining objects in **Offline** mode, which is the default when you work in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], the mining objects that you create are only metadata containers until you deploy them to an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="c1a1d-114">因此，只要您對物件進行變更，就必須將物件重新部署到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 伺服器。</span><span class="sxs-lookup"><span data-stu-id="c1a1d-114">Therefore, any time that you make a change to an object, you must redeploy the object to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server.</span></span> <span data-ttu-id="c1a1d-115">如需資料採礦架構的詳細資訊，請參閱[實體架構 &#40;Analysis Services - 資料採礦&#41;](physical-architecture-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="c1a1d-115">For more information about data mining architecture, see [Physical Architecture &#40;Analysis Services - Data Mining&#41;](physical-architecture-analysis-services-data-mining.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c1a1d-116">有些用戶端 (例如適用於 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 2007 的資料採礦增益集) 也可讓您建立工作階段採礦模型和採礦結構，這些用戶端會使用執行個體的連接，但只會將採礦結構和模型儲存在工作階段持續時間的伺服器中。</span><span class="sxs-lookup"><span data-stu-id="c1a1d-116">Some clients, such as the Data Mining Add-ins for [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 2007, also let you create session mining models and mining structures, which use a connection to an instance but store the mining structure and models on the server only for the duration of the session.</span></span> <span data-ttu-id="c1a1d-117">您仍可以透過用戶端管理這些模型，方法與您管理儲存在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫中的結構和模型相同，但是在您中斷與 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]執行個體的連接之後，並不會保存這些物件。</span><span class="sxs-lookup"><span data-stu-id="c1a1d-117">You can still manage these models through the client, the same as you would structures and models stored in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, but the objects are not persisted after you disconnect from the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="managing-data-mining-objects-in-sql-server-data-tools"></a><span data-ttu-id="c1a1d-118">使用 SQL Server 資料工具管理資料採礦物件</span><span class="sxs-lookup"><span data-stu-id="c1a1d-118">Managing Data Mining Objects in SQL Server Data Tools</span></span>  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="c1a1d-119">提供一些功能，使資料採礦物件的建立、瀏覽和編輯都更為簡易。</span><span class="sxs-lookup"><span data-stu-id="c1a1d-119">offers features that make it easy to create, browse, and edit data mining objects.</span></span>  
  
 <span data-ttu-id="c1a1d-120">以下連結提供有關如何使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]修改資料採礦物件的資訊：</span><span class="sxs-lookup"><span data-stu-id="c1a1d-120">The following links provide information on how you can modify data mining objects by using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]:</span></span>  
  
-   [<span data-ttu-id="c1a1d-121">編輯用於採礦結構的資料來源檢視</span><span class="sxs-lookup"><span data-stu-id="c1a1d-121">Edit the Data Source View used for a Mining Structure</span></span>](edit-the-data-source-view-used-for-a-mining-structure.md)  
  
-   [<span data-ttu-id="c1a1d-122">變更採礦結構的屬性</span><span class="sxs-lookup"><span data-stu-id="c1a1d-122">Change the Properties of a Mining Structure</span></span>](change-the-properties-of-a-mining-structure.md)  
  
-   [<span data-ttu-id="c1a1d-123">變更採礦模型的屬性</span><span class="sxs-lookup"><span data-stu-id="c1a1d-123">Change the Properties of a Mining Model</span></span>](change-the-properties-of-a-mining-model.md)  
  
-   [<span data-ttu-id="c1a1d-124">檢視或變更模型旗標 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="c1a1d-124">View or Change Modeling Flags &#40;Data Mining&#41;</span></span>](modeling-flags-data-mining.md)  
  
-   [<span data-ttu-id="c1a1d-125">檢視或變更演算法參數</span><span class="sxs-lookup"><span data-stu-id="c1a1d-125">View or Change Algorithm Parameters</span></span>](view-or-change-algorithm-parameters.md)  
  
 <span data-ttu-id="c1a1d-126">通常，您將使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 當做開發新專案以及加入至現有專案的工具，然後管理已使用類似 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的工具進行部署的專案和物件。</span><span class="sxs-lookup"><span data-stu-id="c1a1d-126">Typically you will use [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] as a tool for developing new projects and adding to existing projects, and then manage projects and objects that have been deployed by using tools such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="c1a1d-127">但是，您可以直接修改已使用 `Immediate` 選項部署到 ssASnoversion 執行個體並且在線上模式下連接到伺服器的物件。</span><span class="sxs-lookup"><span data-stu-id="c1a1d-127">However, you can directly modify objects that are already deployed to an instance of ssASnoversion by using the `Immediate` option and connecting to the server in Online mode.</span></span> <span data-ttu-id="c1a1d-128">如需詳細資訊，請參閱 [在連線模式下連接至 Analysis Services 資料庫](../multidimensional-models/connect-in-online-mode-to-an-analysis-services-database.md)。</span><span class="sxs-lookup"><span data-stu-id="c1a1d-128">For more information, see [Connect in Online Mode to an Analysis Services Database](../multidimensional-models/connect-in-online-mode-to-an-analysis-services-database.md).</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="c1a1d-129">採礦結構或採礦模型的所有變更 (包括類似名稱或描述等中繼資料的變更) 都需要重新處理結構或模型。</span><span class="sxs-lookup"><span data-stu-id="c1a1d-129">All changes to a mining structure or mining model, including changes to metadata such as a name or description, require that the structure or model be reprocessed.</span></span>  
  
 <span data-ttu-id="c1a1d-130">如果您沒有用於建立資料採礦專案或物件的方案檔，您可使用 Analysis Services 匯入精靈從伺服器匯入現有的專案、修改物件，然後使用 `Incremental` 選項重新部署。</span><span class="sxs-lookup"><span data-stu-id="c1a1d-130">If you do not have the solution file that was used to create the data mining project or objects, you can import the existing project from the server using the Analysis Services Import wizard, make modifications to the objects, and then redeploy using the `Incremental` option.</span></span> <span data-ttu-id="c1a1d-131">如需詳細資訊，請參閱 [使用 Analysis Services 匯入精靈匯入資料採礦專案](import-a-data-mining-project-using-the-analysis-services-import-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="c1a1d-131">For more information, see [Import a Data Mining Project using the Analysis Services Import Wizard](import-a-data-mining-project-using-the-analysis-services-import-wizard.md).</span></span>  
  
## <a name="managing-data-mining-objects-in-sql-server-management-studio"></a><span data-ttu-id="c1a1d-132">使用 SQL Server Management Studio 管理資料採礦物件</span><span class="sxs-lookup"><span data-stu-id="c1a1d-132">Managing Data Mining Objects in SQL Server Management Studio</span></span>  
 <span data-ttu-id="c1a1d-133">您可以在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中撰寫指令碼、處理或刪除採礦結構及採礦模型。</span><span class="sxs-lookup"><span data-stu-id="c1a1d-133">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you can script, process, or delete mining structures and mining models.</span></span> <span data-ttu-id="c1a1d-134">您只能使用物件總管檢視有限的屬性集；不過，您可以藉由開啟 **[DMX 查詢]** 視窗並選取採礦結構，以檢視有關採礦模型的其他中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c1a1d-134">You can view only a limited set of properties by using Object Explorer; however, you can view additional metadata about mining models by opening a **DMX Query** window and selecting a mining structure.</span></span>  
  
-   [<span data-ttu-id="c1a1d-135">在 SQL Server Management Studio 中建立 DMX 查詢</span><span class="sxs-lookup"><span data-stu-id="c1a1d-135">Create a DMX Query in SQL Server Management Studio</span></span>](create-a-dmx-query-in-sql-server-management-studio.md)  
  
## <a name="managing-data-mining-objects-programmatically"></a><span data-ttu-id="c1a1d-136">以程式設計方式管理資料採礦物件</span><span class="sxs-lookup"><span data-stu-id="c1a1d-136">Managing Data Mining Objects Programmatically</span></span>  
 <span data-ttu-id="c1a1d-137">您可以使用下列程式語言，建立、改變、處理和刪除資料採礦物件。</span><span class="sxs-lookup"><span data-stu-id="c1a1d-137">You can create, alter, process, and delete data mining objects by using the following programming languages.</span></span> <span data-ttu-id="c1a1d-138">每種語言是針對不同的工作所設計，因此，您可以執行的作業類型可能會有限制。</span><span class="sxs-lookup"><span data-stu-id="c1a1d-138">Each language is designed for different tasks and as a result, there might be restrictions on the type of operations that you can perform.</span></span> <span data-ttu-id="c1a1d-139">例如，資料採礦物件的某些屬性無法使用資料採礦延伸模組 (DMX) 變更，因此，您必須使用 XMLA 或 AMO。</span><span class="sxs-lookup"><span data-stu-id="c1a1d-139">For example, some properties of data mining objects cannot be changed by using Data Mining Extensions (DMX); you must use XMLA or AMO.</span></span>  
  
### <a name="analysis-management-objects-amo"></a><span data-ttu-id="c1a1d-140">分析管理物件 (AMO)</span><span class="sxs-lookup"><span data-stu-id="c1a1d-140">Analysis Management Objects (AMO)</span></span>  
 <span data-ttu-id="c1a1d-141">分析管理物件 (AMO) 是根據 XMLA 所建立的物件模型，可讓您完全控制資料採礦物件。</span><span class="sxs-lookup"><span data-stu-id="c1a1d-141">Analysis Management Objects (AMO) is an object model built on top of XMLA that gives you full control over data mining objects.</span></span> <span data-ttu-id="c1a1d-142">您可以藉由使用 AMO 來建立、部署和監視採礦結構和採礦模型</span><span class="sxs-lookup"><span data-stu-id="c1a1d-142">By using AMO, you can create, deploy, and monitor mining structures and mining models</span></span>  
  
-   [<span data-ttu-id="c1a1d-143">AMO 概念和物件模型</span><span class="sxs-lookup"><span data-stu-id="c1a1d-143">AMO Concepts and Object Model</span></span>](https://docs.microsoft.com/bi-reference/amo/amo-concepts-and-object-model)  
  
-   <xref:Microsoft.AnalysisServices>  
  
 <span data-ttu-id="c1a1d-144">**限制** ：無。</span><span class="sxs-lookup"><span data-stu-id="c1a1d-144">**Restrictions:** None.</span></span>  
  
### <a name="data-mining-extensions-dmx"></a><span data-ttu-id="c1a1d-145">資料採礦延伸模組 (DMX)</span><span class="sxs-lookup"><span data-stu-id="c1a1d-145">Data Mining Extensions (DMX)</span></span>  
 <span data-ttu-id="c1a1d-146">資料採礦延伸模組 (DMX) 可搭配其他的命令介面 (例如 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 或 ADOMD.Net) 來建立、刪除和查詢採礦結構和採礦模型。</span><span class="sxs-lookup"><span data-stu-id="c1a1d-146">Data Mining Extensions (DMX) can be used with other command interfaces such as [!INCLUDE[vstecado](../../includes/vstecado-md.md)] or ADOMD.Net to create, delete, and query mining structures and mining models.</span></span>  
  
-   [<span data-ttu-id="c1a1d-147">資料採礦延伸模組 &#40;DMX&#41; 資料定義陳述式</span><span class="sxs-lookup"><span data-stu-id="c1a1d-147">Data Mining Extensions &#40;DMX&#41; Data Definition Statements</span></span>](/sql/dmx/dmx-statements-data-definition)  
  
 <span data-ttu-id="c1a1d-148">**限制** ：有些屬性無法使用 DMX 變更。</span><span class="sxs-lookup"><span data-stu-id="c1a1d-148">**Restrictions:** Some properties cannot be changed by using DMX.</span></span>  
  
### <a name="xml-for-analysis-xmla"></a><span data-ttu-id="c1a1d-149">XML for Analysis (XMLA)</span><span class="sxs-lookup"><span data-stu-id="c1a1d-149">XML for Analysis (XMLA)</span></span>  
 <span data-ttu-id="c1a1d-150">XML for Analysis (XMLA) 是適用於所有 Analysis Services 的資料定義語言。</span><span class="sxs-lookup"><span data-stu-id="c1a1d-150">XML for Analysis (XMLA) is the data definition language for all of Analysis Services.</span></span> <span data-ttu-id="c1a1d-151">XMLA 讓您能夠控制大多數的資料採礦物件和伺服器作業。</span><span class="sxs-lookup"><span data-stu-id="c1a1d-151">XMLA gives you control over most data mining objects and server operations.</span></span> <span data-ttu-id="c1a1d-152">用戶端和伺服器之間的所有管理作業都可以使用 XMLA 執行。</span><span class="sxs-lookup"><span data-stu-id="c1a1d-152">All management operations between the client and the server can be performed by using XMLA.</span></span> <span data-ttu-id="c1a1d-153">為了便利起見，您可以使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 指令碼語言 (ASSL) 來包裝 XML。</span><span class="sxs-lookup"><span data-stu-id="c1a1d-153">For convenience, you can use the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Scripting Language (ASSL) to wrap the XML.</span></span>  
  
 <span data-ttu-id="c1a1d-154">**限制** [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 會產生一些僅支援內部使用而不能用於 XMLA DDL 指令碼的 XML 陳述式。</span><span class="sxs-lookup"><span data-stu-id="c1a1d-154">**Restrictions:** [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] generates some XMLA statements that are supported for internal use only, and cannot be used in XML DDL scripts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1a1d-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1a1d-155">See Also</span></span>  
 [<span data-ttu-id="c1a1d-156">開發人員指南 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="c1a1d-156">Developer's Guide &#40;Analysis Services&#41;</span></span>](../analysis-services-developer-documentation.md)  
  
  
