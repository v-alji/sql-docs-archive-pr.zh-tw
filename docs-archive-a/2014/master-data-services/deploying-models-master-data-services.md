---
title: 部署模型 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deployment packages [Master Data Services], about deployment packages
- deployment packages [Master Data Services]
ms.assetid: 30085c08-034f-4efe-80fe-408f9091ff5c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: a9cc99112ec874e89ae07faa575235d9a041a972
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607434"
---
# <a name="deploying-models-master-data-services"></a><span data-ttu-id="cfa6e-102">部署模型 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="cfa6e-102">Deploying Models (Master Data Services)</span></span>
  <span data-ttu-id="cfa6e-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，套件是一個 XML 檔案，其中包含可部署的模型結構，以及模型中的資料 (選擇性)。</span><span class="sxs-lookup"><span data-stu-id="cfa6e-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], a package is an XML file that contains a deployable model structure, and optionally, data from the model.</span></span> <span data-ttu-id="cfa6e-104">使用模型封裝將模型的副本從一個 MDS 環境移到另一個 MDS 環境，或在現有的 MDS 環境中建立新的模型。</span><span class="sxs-lookup"><span data-stu-id="cfa6e-104">Use model packages to move copies of models from one MDS environment to another, or to create new models in your existing MDS environment.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="cfa6e-105">封裝只能部署到之前建立封裝所使用的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="cfa6e-105">Packages can be deployed to the edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] they were created in only.</span></span> <span data-ttu-id="cfa6e-106">這表示，在 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 中建立的套件無法部署到 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="cfa6e-106">This means that packages created in [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] cannot be deployed to [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] or higher.</span></span>  
  
## <a name="tools-for-deploying-models"></a><span data-ttu-id="cfa6e-107">部署模型的工具</span><span class="sxs-lookup"><span data-stu-id="cfa6e-107">Tools for Deploying Models</span></span>  
 <span data-ttu-id="cfa6e-108">若要使用模型封裝，您可以使用以下三個工具之一，端視您的需要而定。</span><span class="sxs-lookup"><span data-stu-id="cfa6e-108">To work with model packages, you can use one of three tools, depending on your needs.</span></span>  
  
-   <span data-ttu-id="cfa6e-109">**MDSModelDeploy 工具**：若要建立與部署模型物件和資料，請使用 MDSModelDeploy.exe 工具。</span><span class="sxs-lookup"><span data-stu-id="cfa6e-109">**MDSModelDeploy tool**: To create and deploy model objects and data, use the MDSModelDeploy.exe tool.</span></span> <span data-ttu-id="cfa6e-110">如果您在安裝 MDS 時選取了預設路徑，此工具會位於*drive*： \PROGRAM Files\Microsoft SQL Server\120\Master Data services\configuration。</span><span class="sxs-lookup"><span data-stu-id="cfa6e-110">If you selected the default path when installing MDS, this tool is located on *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services\Configuration.</span></span>  
  
-   <span data-ttu-id="cfa6e-111">**模型部署精靈：** 若只要建立與部署模型結構的套件，請使用 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 應用程式中的精靈。</span><span class="sxs-lookup"><span data-stu-id="cfa6e-111">**Model Deployment wizard**: To create and deploy packages of the model structure only, use the wizard in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application.</span></span> <span data-ttu-id="cfa6e-112">您無法使用此精靈來部署資料。</span><span class="sxs-lookup"><span data-stu-id="cfa6e-112">You cannot use this wizard to deploy data.</span></span>  
  
-   <span data-ttu-id="cfa6e-113">**模型套件編輯器**：若要編輯模型套件，請使用 ModelPackageEditor.exe 以啟動模型套件編輯器精靈。</span><span class="sxs-lookup"><span data-stu-id="cfa6e-113">**Model Package Editor**: To edit a model package, use the ModelPackageEditor.exe that launches the Model Package Editor wizard.</span></span> <span data-ttu-id="cfa6e-114">您可以使用此精靈編輯 MDSModelDeploy 工具或「模型部署」精靈所建立的封裝。</span><span class="sxs-lookup"><span data-stu-id="cfa6e-114">You use this wizard to edit a package that was created by the MDSModelDeploy tool or the Model Deployment wizard.</span></span> <span data-ttu-id="cfa6e-115">如果您在安裝 MDS 時選取了預設路徑，此工具會位於*drive*： \PROGRAM Files\Microsoft SQL Server\120\Master Data services\configuration。</span><span class="sxs-lookup"><span data-stu-id="cfa6e-115">If you selected the default path when installing MDS, this tool is located on *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services\Configuration.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="cfa6e-116">您可以使用 MDSDeployModel 來建立新模型、建立模型的複製或更新現有模型及其資料。</span><span class="sxs-lookup"><span data-stu-id="cfa6e-116">You can use the MDSDeployModel to create a new model, create a clone of a model, or update an existing model and its data.</span></span> <span data-ttu-id="cfa6e-117">如果您使用 MDSModelDeploy 工具來更新現有模型及其資料，而且封裝不包含存在目的地模型中的實體、屬性或成員，MDSModelDeploy 就不會從模型中刪除該實體、屬性或成員。</span><span class="sxs-lookup"><span data-stu-id="cfa6e-117">If you use the MDSModelDeploy tool to update an existing model and its data, and the package does not contain an entity, attribute, or member that exists in the destination model, MDSModelDeploy will not delete that entity, attribute, or member from the model.</span></span>  
  
## <a name="what-packages-contain"></a><span data-ttu-id="cfa6e-118">封裝內容</span><span class="sxs-lookup"><span data-stu-id="cfa6e-118">What Packages Contain</span></span>  
 <span data-ttu-id="cfa6e-119">模型封裝是以副檔名 .pkg 儲存的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="cfa6e-119">A model package is an XML file that is saved with the .pkg extension.</span></span> <span data-ttu-id="cfa6e-120">當您建立部署封裝時，可以決定是否要包含資料。</span><span class="sxs-lookup"><span data-stu-id="cfa6e-120">When you create a deployment package, you can decide whether or not to include data.</span></span> <span data-ttu-id="cfa6e-121">如果決定要包含資料，必須選取要包含的資料版本。</span><span class="sxs-lookup"><span data-stu-id="cfa6e-121">If you decide to include data, you must select a version of the data to include.</span></span>  
  
 <span data-ttu-id="cfa6e-122">所有模型物件都會包含在封裝中。</span><span class="sxs-lookup"><span data-stu-id="cfa6e-122">All model objects are included in a package.</span></span> <span data-ttu-id="cfa6e-123">包括下列物件：</span><span class="sxs-lookup"><span data-stu-id="cfa6e-123">These objects are:</span></span>  
  
-   <span data-ttu-id="cfa6e-124">實體</span><span class="sxs-lookup"><span data-stu-id="cfa6e-124">Entities</span></span>  
  
-   <span data-ttu-id="cfa6e-125">屬性</span><span class="sxs-lookup"><span data-stu-id="cfa6e-125">Attributes</span></span>  
  
-   <span data-ttu-id="cfa6e-126">屬性群組</span><span class="sxs-lookup"><span data-stu-id="cfa6e-126">Attribute groups</span></span>  
  
-   <span data-ttu-id="cfa6e-127">階層</span><span class="sxs-lookup"><span data-stu-id="cfa6e-127">Hierarchies</span></span>  
  
-   <span data-ttu-id="cfa6e-128">集合</span><span class="sxs-lookup"><span data-stu-id="cfa6e-128">Collections</span></span>  
  
-   <span data-ttu-id="cfa6e-129">商務規則</span><span class="sxs-lookup"><span data-stu-id="cfa6e-129">Business rules</span></span>  
  
-   <span data-ttu-id="cfa6e-130">版本旗標</span><span class="sxs-lookup"><span data-stu-id="cfa6e-130">Version flags</span></span>  
  
-   <span data-ttu-id="cfa6e-131">訂閱檢視</span><span class="sxs-lookup"><span data-stu-id="cfa6e-131">Subscription views</span></span>  
  
 <span data-ttu-id="cfa6e-132">使用者定義的中繼資料、檔案屬性及使用者和群組的權限不包含在內。</span><span class="sxs-lookup"><span data-stu-id="cfa6e-132">User-defined metadata, file attributes, and user and group permissions are not included.</span></span> <span data-ttu-id="cfa6e-133">在部署模型之後，您必須手動更新這些項目。</span><span class="sxs-lookup"><span data-stu-id="cfa6e-133">After you deploy a model, you must update these manually.</span></span>  
  
## <a name="sample-packages"></a><span data-ttu-id="cfa6e-134">範例封裝</span><span class="sxs-lookup"><span data-stu-id="cfa6e-134">Sample Packages</span></span>  
 <span data-ttu-id="cfa6e-135">當您安裝 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]時，會包含範例封裝檔案。</span><span class="sxs-lookup"><span data-stu-id="cfa6e-135">Sample package files are included when you install [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].</span></span> <span data-ttu-id="cfa6e-136">這些封裝檔案位於 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]安裝位置的 Master Data Services\Samples\Packages 目錄中。</span><span class="sxs-lookup"><span data-stu-id="cfa6e-136">These package files are in the Master Data Services\Samples\Packages directory where you installed [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].</span></span> <span data-ttu-id="cfa6e-137">當您使用 MDSModelDeploy 工具部署這些範例封裝時，則會建立範例模型並以資料擴展。</span><span class="sxs-lookup"><span data-stu-id="cfa6e-137">When you deploy these sample packages by using the MDSModelDeploy tool, sample models are created and populated with data.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="cfa6e-138">相關工作</span><span class="sxs-lookup"><span data-stu-id="cfa6e-138">Related Tasks</span></span>  
  
|<span data-ttu-id="cfa6e-139">工作描述</span><span class="sxs-lookup"><span data-stu-id="cfa6e-139">Task Description</span></span>|<span data-ttu-id="cfa6e-140">主題</span><span class="sxs-lookup"><span data-stu-id="cfa6e-140">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="cfa6e-141">使用 MDSModelDeploy 工具建立模型物件與/或資料的新部署封裝。</span><span class="sxs-lookup"><span data-stu-id="cfa6e-141">Create a new deployment package of model objects and/or data by using the MDSModelDeploy tool.</span></span>|[<span data-ttu-id="cfa6e-142">使用 MDSModelDeploy 建立模型部署封裝</span><span class="sxs-lookup"><span data-stu-id="cfa6e-142">Create a Model Deployment Package by Using MDSModelDeploy</span></span>](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md)|  
|<span data-ttu-id="cfa6e-143">使用精靈僅建立模型物件的新部署封裝。</span><span class="sxs-lookup"><span data-stu-id="cfa6e-143">Create a new deployment package of model objects only by using the wizard.</span></span>|[<span data-ttu-id="cfa6e-144">使用精靈建立模型部署封裝</span><span class="sxs-lookup"><span data-stu-id="cfa6e-144">Create a Model Deployment Package by Using the Wizard</span></span>](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md)|  
|<span data-ttu-id="cfa6e-145">使用 MDSModelDeploy 工具部署模型物件與資料的封裝。</span><span class="sxs-lookup"><span data-stu-id="cfa6e-145">Deploy a package of model objects and data by using the MDSModelDeploy tool.</span></span>|[<span data-ttu-id="cfa6e-146">使用 MDSModelDeploy 部署模型部署封裝</span><span class="sxs-lookup"><span data-stu-id="cfa6e-146">Deploy a Model Deployment Package by Using MDSModelDeploy</span></span>](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)|  
|<span data-ttu-id="cfa6e-147">使用精靈僅部署模型物件的封裝。</span><span class="sxs-lookup"><span data-stu-id="cfa6e-147">Deploy a package of model objects only by using the wizard.</span></span>|[<span data-ttu-id="cfa6e-148">使用精靈部署模型部署封裝</span><span class="sxs-lookup"><span data-stu-id="cfa6e-148">Deploy a Model Deployment Package by Using the Wizard</span></span>](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md)|  
|<span data-ttu-id="cfa6e-149">編輯模型部署封裝以部署選取的模型部分，而非整個模型。</span><span class="sxs-lookup"><span data-stu-id="cfa6e-149">Edit a model deployment package to deploy selected parts of a model, rather than the entire model.</span></span>|[<span data-ttu-id="cfa6e-150">編輯模型部署封裝</span><span class="sxs-lookup"><span data-stu-id="cfa6e-150">Edit a Model Deployment Package</span></span>](../../2014/master-data-services/edit-a-model-deployment-package.md)|  
  
## <a name="related-content"></a><span data-ttu-id="cfa6e-151">相關內容</span><span class="sxs-lookup"><span data-stu-id="cfa6e-151">Related Content</span></span>  
  
-   [<span data-ttu-id="cfa6e-152">模型部署選項 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="cfa6e-152">Model Deployment Options &#40;Master Data Services&#41;</span></span>](model-deployment-options-master-data-services.md)  
  
  
