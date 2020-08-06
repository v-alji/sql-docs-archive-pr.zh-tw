---
title: 資料採礦解決方案的部署 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], deploying
- deploying [Analysis Services], production environments
- deploying [Analysis Services - data mining]
- solutions [Analysis Services], deploying
- models [Analysis Services], data mining
ms.assetid: d83effc7-437d-42e9-8ac3-b65f79e27043
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5764be2f7530add2fa4cb028b288be69598bb95c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599266"
---
# <a name="deployment-of-data-mining-solutions"></a><span data-ttu-id="00d31-102">部署資料採礦方案</span><span class="sxs-lookup"><span data-stu-id="00d31-102">Deployment of Data Mining Solutions</span></span>
  <span data-ttu-id="00d31-103">資料採礦程序的最後一個步驟就是將模型部署到實際執行環境。</span><span class="sxs-lookup"><span data-stu-id="00d31-103">The last step in the data mining process is to deploy the models to a production environment.</span></span> <span data-ttu-id="00d31-104">部署作業非常重要，因為可將模型提供給使用者，好讓您可以執行以下任何工作：</span><span class="sxs-lookup"><span data-stu-id="00d31-104">Deployment is important because it makes the models available to users so that you can perform any of the following tasks:</span></span>  
  
-   <span data-ttu-id="00d31-105">使用模型來建立預測，並做出商業決策。</span><span class="sxs-lookup"><span data-stu-id="00d31-105">Use the models to create predictions and make business decisions.</span></span> <span data-ttu-id="00d31-106">如需您可以用來建立查詢之工具的詳細資訊，請參閱[資料採礦查詢介面](data-mining-query-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="00d31-106">For information about the tools you can use to create queries, see [Data Mining Query Interfaces](data-mining-query-tools.md).</span></span>  
  
-   <span data-ttu-id="00d31-107">直接將資料採礦功能內嵌於應用程式中。</span><span class="sxs-lookup"><span data-stu-id="00d31-107">Embed data mining functionality directly into an application.</span></span> <span data-ttu-id="00d31-108">您可以包括分析管理物件 (AMO) 或含有一組物件的組件，讓應用程式用來建立、改變、處理以及刪除採礦結構和採礦模型。</span><span class="sxs-lookup"><span data-stu-id="00d31-108">You can include Analysis Management Objects (AMO) or an assembly that contains a set of objects that your application can use to create, alter, process, and delete mining structures and mining models.</span></span>  
  
-   <span data-ttu-id="00d31-109">建立報表，好讓使用者要求預測、檢視趨勢或比較模型。</span><span class="sxs-lookup"><span data-stu-id="00d31-109">Create reports that let users request predictions, view trends, or compare models.</span></span>  
  
 <span data-ttu-id="00d31-110">本節提供有關部署選項的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="00d31-110">This section provides detailed information about deployment options.</span></span>  
  
 [<span data-ttu-id="00d31-111">部署資料採礦方案的需求</span><span class="sxs-lookup"><span data-stu-id="00d31-111">Requirements for Deployment of Data Mining Solutions</span></span>](#bkmk_Reqs)  
  
 [<span data-ttu-id="00d31-112">部署關聯式方案</span><span class="sxs-lookup"><span data-stu-id="00d31-112">Deploying a Relational Solution</span></span>](#bkmk_RelationalSltn)  
  
 [<span data-ttu-id="00d31-113">部署多維度方案</span><span class="sxs-lookup"><span data-stu-id="00d31-113">Deploying a Multidimensional Solution</span></span>](#bkmk_MDSltn)  
  
 [<span data-ttu-id="00d31-114">相關資源</span><span class="sxs-lookup"><span data-stu-id="00d31-114">Related Resources</span></span>](#bkmk_Resources)  
  
## <a name="in-this-section"></a><span data-ttu-id="00d31-115">本節內容</span><span class="sxs-lookup"><span data-stu-id="00d31-115">In This Section</span></span>  
 [<span data-ttu-id="00d31-116">將資料採礦方案部署到舊版的 SQL Server</span><span class="sxs-lookup"><span data-stu-id="00d31-116">Deploy a Data Mining Solution to Previous Versions of SQL Server</span></span>](deploy-a-data-mining-solution-to-previous-versions-of-sql-server.md)  
  
 [<span data-ttu-id="00d31-117">匯出及匯入資料採礦物件</span><span class="sxs-lookup"><span data-stu-id="00d31-117">Export and Import Data Mining Objects</span></span>](export-and-import-data-mining-objects.md)  
  
##  <a name="requirements-for-deployment-of-data-mining-solutions"></a><a name="bkmk_Reqs"></a><span data-ttu-id="00d31-118">資料採礦解決方案部署的需求</span><span class="sxs-lookup"><span data-stu-id="00d31-118">Requirements for Deployment of Data Mining Solutions</span></span>  
 <span data-ttu-id="00d31-119">部署方案的目標 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體必須在支援多維度物件和資料採礦物件的模式下執行；也就是說，您不能將資料採礦物件部署到裝載表格式模型或 PowerPivot 資料的執行個體。</span><span class="sxs-lookup"><span data-stu-id="00d31-119">The instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to which you deploy the solution must be running in a mode that supports multidimensional objects and data mining objects; that is, you cannot deploy data mining objects to an instance that hosts tabular models or PowerPivot data.</span></span>  
  
 <span data-ttu-id="00d31-120">因此，當您在 Visual Studio 中建立資料採礦方案時，請務必使用 [Analysis Services 多維度和資料採礦專案]\*\*\*\* 範本。</span><span class="sxs-lookup"><span data-stu-id="00d31-120">Therefore, when you create a data mining solution in Visual Studio, be sure to use the template, **Analysis Services Multidimensional and Data Mining Project**.</span></span>  
  
 <span data-ttu-id="00d31-121">當您部署方案時，用於資料採礦的物件會在指定的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體中建立 (位於與方案檔同名的資料庫中)。</span><span class="sxs-lookup"><span data-stu-id="00d31-121">When you deploy the solution, the objects used for data mining are created in the specified [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, in a database with the same name as the solution file.</span></span>  
  
###  <a name="deploying-a-relational-solution"></a><a name="bkmk_RelationalSltn"></a><span data-ttu-id="00d31-122">部署關聯式解決方案</span><span class="sxs-lookup"><span data-stu-id="00d31-122">Deploying a Relational Solution</span></span>  
 <span data-ttu-id="00d31-123">當您部署關聯式資料採礦方案時，將會在新的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫中建立必要的資料採礦物件，而且預設會處理這些物件。</span><span class="sxs-lookup"><span data-stu-id="00d31-123">When you deploy a relational data mining solution, the required data mining objects are created within a new [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, and the objects are processed by default.</span></span> <span data-ttu-id="00d31-124">您可以使用 [處理選項]\*\*\*\* 組態屬性來變更處理選項。</span><span class="sxs-lookup"><span data-stu-id="00d31-124">You can change processing options by using the configuration property, **Processing Option**.</span></span> <span data-ttu-id="00d31-125">如需詳細資訊，請參閱 [設定 Analysis Services 專案屬性 &#40;SSDT&#41;](../multidimensional-models/configure-analysis-services-project-properties-ssdt.md)。</span><span class="sxs-lookup"><span data-stu-id="00d31-125">For more information, see [Configure Analysis Services Project Properties &#40;SSDT&#41;](../multidimensional-models/configure-analysis-services-project-properties-ssdt.md).</span></span>  
  
 <span data-ttu-id="00d31-126">根據預設，每次只會部署累加變更。</span><span class="sxs-lookup"><span data-stu-id="00d31-126">By default, only incremental changes are deployed each time.</span></span> <span data-ttu-id="00d31-127">換句話說，您可以修改採礦模型，而且當您重新部署專案時，只會更新該採礦模型。</span><span class="sxs-lookup"><span data-stu-id="00d31-127">In other words, you can modify a mining model, and when you re-deploy the project, only that mining model would be updated.</span></span> <span data-ttu-id="00d31-128">但是，如果您有多個用戶端正在編輯 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫，這可能會導致錯誤發生。</span><span class="sxs-lookup"><span data-stu-id="00d31-128">However, if you have multiple clients editing the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, this can lead to errors.</span></span> <span data-ttu-id="00d31-129">若要變更預設部署模式，好讓您部署方案時重新整理整個資料庫，請變更 [部署模式]\*\*\*\* 屬性</span><span class="sxs-lookup"><span data-stu-id="00d31-129">To change the default deployment mode so that the entire database is refreshed when you deploy the solution, change the **Deployment Mode** property</span></span>  
  
 <span data-ttu-id="00d31-130">在關聯式資料採礦方案中，必須部署的物件只有資料來源定義、任何已使用的資料來源檢視、採礦結構，以及所有相依的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="00d31-130">In a relational data mining solution, the only objects that must be deployed are the data source definition, any data source views that were used, the mining structures, and all dependent mining models.</span></span>  
  
###  <a name="deploying-a-multidimensional-solution"></a><a name="bkmk_MDSltn"></a><span data-ttu-id="00d31-131">部署多維度方案</span><span class="sxs-lookup"><span data-stu-id="00d31-131">Deploying a Multidimensional Solution</span></span>  
 <span data-ttu-id="00d31-132">當您部署多維度資料採礦方案時，這個方案會在與來源 Cube 相同的資料庫中建立您的資料採礦物件。</span><span class="sxs-lookup"><span data-stu-id="00d31-132">When you deploy a multidimensional data mining solution, this solution creates your data mining objects within the same database as the source cube.</span></span>  
  
 <span data-ttu-id="00d31-133">當您處理採礦結構或採礦模型時，您也必須處理來源 Cube。</span><span class="sxs-lookup"><span data-stu-id="00d31-133">When you process the mining structure or mining model, you must process the source cube as well.</span></span> <span data-ttu-id="00d31-134">因此，部署使用 OLAP 採礦模型的方案比起關聯式資料採礦方案需要更長的時間。</span><span class="sxs-lookup"><span data-stu-id="00d31-134">For this reason, deploying a solution that uses OLAP mining models can take longer than relational data mining solutions.</span></span>  
  
 <span data-ttu-id="00d31-135">通常資料採礦物件也會使用 Cube 所使用的相同資料來源和資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="00d31-135">Typically data mining objects also use the same data sources and data source views that are used for the cube.</span></span> <span data-ttu-id="00d31-136">但是，您可以加入專門以資料採礦為目標的資料來源和資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="00d31-136">However, you can add data sources and data source views that are targeted specifically to data mining.</span></span> <span data-ttu-id="00d31-137">例如，通常 Cube 不會包含有關潛在客戶的資料或是多維度物件中未使用的外部資料。</span><span class="sxs-lookup"><span data-stu-id="00d31-137">For example, typically a cube would not contain data about prospective clients, or external data not used in the multidimensional objects.</span></span>  
  
##  <a name="related-resources"></a><a name="bkmk_Resources"></a><span data-ttu-id="00d31-138">相關資源</span><span class="sxs-lookup"><span data-stu-id="00d31-138">Related Resources</span></span>  
 [<span data-ttu-id="00d31-139">移動資料採礦物件</span><span class="sxs-lookup"><span data-stu-id="00d31-139">Moving Data Mining Objects</span></span>](moving-data-mining-objects.md)  
  
 <span data-ttu-id="00d31-140">如果您的模型只以關聯式資料為根據，則使用 DMX 匯出和匯入物件是最方便的移動模型方式。</span><span class="sxs-lookup"><span data-stu-id="00d31-140">If your model is based on relational data only, exporting and importing objects using DMX is the easiest way to move models.</span></span>  
  
 [<span data-ttu-id="00d31-141">移動 Analysis Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="00d31-141">Move an Analysis Services Database</span></span>](../multidimensional-models/move-an-analysis-services-database.md)  
  
 <span data-ttu-id="00d31-142">當模型使用 Cube 當做資料來源時，請參考本主題，以取得有關如何移動模型及其支援 Cube 資料的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="00d31-142">When models use a cube as a data source, refer to this topic for more information about how to move models and their supporting cube data.</span></span>  
  
 [<span data-ttu-id="00d31-143">部署 Analysis Services 專案 &#40;SSDT&#41;</span><span class="sxs-lookup"><span data-stu-id="00d31-143">Deploy Analysis Services Projects &#40;SSDT&#41;</span></span>](../multidimensional-models/deploy-analysis-services-projects-ssdt.md)  
  
 <span data-ttu-id="00d31-144">提供有關 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案部署的一般資訊，並描述可當作專案組態之一部分設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="00d31-144">Provides general information about deployment of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projects, and describes the properties that you can set as part of the project configuration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00d31-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00d31-145">See Also</span></span>  
 <span data-ttu-id="00d31-146">[多維度模型物件處理](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="00d31-146">[Multidimensional Model Object Processing](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md) </span></span>  
 <span data-ttu-id="00d31-147">[資料採礦查詢介面](data-mining-query-tools.md) </span><span class="sxs-lookup"><span data-stu-id="00d31-147">[Data Mining Query Interfaces](data-mining-query-tools.md) </span></span>  
 [<span data-ttu-id="00d31-148">處理需求和考量 (資料採礦)</span><span class="sxs-lookup"><span data-stu-id="00d31-148">Processing Requirements and Considerations &#40;Data Mining&#41;</span></span>](processing-requirements-and-considerations-data-mining.md)  
  
  
