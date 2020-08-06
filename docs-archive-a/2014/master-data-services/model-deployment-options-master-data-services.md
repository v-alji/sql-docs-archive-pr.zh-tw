---
title: 模型部署選項 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: cf1b17b4-47d5-4eba-83f9-fb0555806867
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 25af38deef2a5476f64f364116dc5e9168345fb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707657"
---
# <a name="model-deployment-options-master-data-services"></a><span data-ttu-id="63353-102">模型部署選項 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="63353-102">Model Deployment Options (Master Data Services)</span></span>
  <span data-ttu-id="63353-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，當您要部署模型封裝檔案時，必須決定要部署新的或複製的模型，還是更新之前複製的模型。</span><span class="sxs-lookup"><span data-stu-id="63353-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], when you deploy a model package file, you must decide whether to deploy a new or cloned model, or to update a model that was previously cloned.</span></span>  
  
## <a name="workflows"></a><span data-ttu-id="63353-104">工作流程</span><span class="sxs-lookup"><span data-stu-id="63353-104">Workflows</span></span>  
 <span data-ttu-id="63353-105">在使用模型封裝時，有兩個主要工作流程。</span><span class="sxs-lookup"><span data-stu-id="63353-105">When working with model packages, there are two primary workflows.</span></span>  
  
-   <span data-ttu-id="63353-106">在測試環境中建立模型封裝，並且將模型的複製部署到實際執行環境。</span><span class="sxs-lookup"><span data-stu-id="63353-106">Create a package of a model in a test environment and deploy a clone of the model to a production environment.</span></span> <span data-ttu-id="63353-107">經過一段時間後，從測試環境將更新部署到實際執行環境。</span><span class="sxs-lookup"><span data-stu-id="63353-107">Over time, deploy updates from the test environment to the production environment.</span></span>  
  
-   <span data-ttu-id="63353-108">建立模型封裝，並將它做為新模型部署到相同的環境。</span><span class="sxs-lookup"><span data-stu-id="63353-108">Create a package of a model and deploy it as a new model to the same environment.</span></span> <span data-ttu-id="63353-109">在此情況下，您必須指定模型的新名稱。</span><span class="sxs-lookup"><span data-stu-id="63353-109">In this case, you must give the model a new name.</span></span>  
  
## <a name="options"></a><span data-ttu-id="63353-110">選項</span><span class="sxs-lookup"><span data-stu-id="63353-110">Options</span></span>  
 <span data-ttu-id="63353-111">在 MDS 資料庫中，每個模型物件都有唯一識別碼 (ID)。</span><span class="sxs-lookup"><span data-stu-id="63353-111">In the MDS database, each model object has a unique identifier (ID).</span></span> <span data-ttu-id="63353-112">這些識別碼包含在模型部署封裝中。</span><span class="sxs-lookup"><span data-stu-id="63353-112">These IDs are included in model deployment packages.</span></span> <span data-ttu-id="63353-113">當您部署封裝時，必須選擇如何處理這些識別碼。</span><span class="sxs-lookup"><span data-stu-id="63353-113">When you deploy the package, you must choose what to do with these IDs.</span></span>  
  
 <span data-ttu-id="63353-114">下表有助於您在使用系統管理模型部署精靈或 MDSModelDeploy 工具部署模型時，決定選擇。</span><span class="sxs-lookup"><span data-stu-id="63353-114">The following table should help you determine which choice to make when deploying a model by using either the System Administration model deployment wizard or the MDSModelDeploy tool.</span></span>  
  
|<span data-ttu-id="63353-115">選項</span><span class="sxs-lookup"><span data-stu-id="63353-115">Option</span></span>|<span data-ttu-id="63353-116">描述</span><span class="sxs-lookup"><span data-stu-id="63353-116">Description</span></span>|<span data-ttu-id="63353-117">注意</span><span class="sxs-lookup"><span data-stu-id="63353-117">Notes</span></span>|  
|------------|-----------------|-----------|  
|<span data-ttu-id="63353-118">新增</span><span class="sxs-lookup"><span data-stu-id="63353-118">New</span></span>|<span data-ttu-id="63353-119">建立具有唯一名稱的新模型。</span><span class="sxs-lookup"><span data-stu-id="63353-119">Create a new model with a unique name.</span></span> <span data-ttu-id="63353-120">將會建立所有模型物件的新識別碼。</span><span class="sxs-lookup"><span data-stu-id="63353-120">New identifiers are created for all model objects.</span></span>|<span data-ttu-id="63353-121">如果建立具有新識別碼的新模型，稍後您無法使用模型部署工具將更新套用至此模型。</span><span class="sxs-lookup"><span data-stu-id="63353-121">If you create a new model with new identifiers, you cannot use model deployment tools to apply updates to the model later.</span></span> <span data-ttu-id="63353-122">在 Web 應用程式中使用精靈來部署模型封裝時，只在已經有相同名稱或識別碼的模型時，您才可以選擇建立新的模型。</span><span class="sxs-lookup"><span data-stu-id="63353-122">When using the wizard in the web application to deploy a model package, you have the option to create a new model only if a model with the same name or ID already exists.</span></span>|  
|<span data-ttu-id="63353-123">複製</span><span class="sxs-lookup"><span data-stu-id="63353-123">Clone</span></span>|<span data-ttu-id="63353-124">建立新的模型，它是封裝中模型的完整複製。</span><span class="sxs-lookup"><span data-stu-id="63353-124">Create a new model that is an exact clone of the model in the package.</span></span> <span data-ttu-id="63353-125">只在此模型不存在於目標環境中 (依名稱或識別碼) 時才有效。</span><span class="sxs-lookup"><span data-stu-id="63353-125">This works only if the model does not exist (by name or identifier) in the target environment.</span></span> <span data-ttu-id="63353-126">如果要在多個環境中具有相同的模型，且經過一段時間後要更新複製的模式，請使用 [複製]。</span><span class="sxs-lookup"><span data-stu-id="63353-126">Use "clone" when you want to have the same model in multiple environments and update the cloned model over time.</span></span>|<span data-ttu-id="63353-127">這是在 Web 應用程式中精靈的預設行為。</span><span class="sxs-lookup"><span data-stu-id="63353-127">This is the default behavior of the wizard in the web application.</span></span> <span data-ttu-id="63353-128">如果已經有相同名稱或識別碼的模型，系統會提示您改為建立新的模型。</span><span class="sxs-lookup"><span data-stu-id="63353-128">If a model with the same name or ID already exists, you are prompted to create a new model instead.</span></span>|  
|<span data-ttu-id="63353-129">更新</span><span class="sxs-lookup"><span data-stu-id="63353-129">Update</span></span>|<span data-ttu-id="63353-130">以封裝中的模型來更新現有模型。</span><span class="sxs-lookup"><span data-stu-id="63353-130">Update an existing model with the model in the package.</span></span> <span data-ttu-id="63353-131">這兩個模型中的識別碼必須相同。</span><span class="sxs-lookup"><span data-stu-id="63353-131">The identifiers must be the same in both models.</span></span> <span data-ttu-id="63353-132">這是用來更新之前複製的模型。</span><span class="sxs-lookup"><span data-stu-id="63353-132">This is used to update a model that you previously cloned.</span></span>|<span data-ttu-id="63353-133">您只可以更新之前複製的模型</span><span class="sxs-lookup"><span data-stu-id="63353-133">You can only update models that were previously cloned.</span></span> <span data-ttu-id="63353-134">(名稱和識別碼必須相符)。</span><span class="sxs-lookup"><span data-stu-id="63353-134">(The names and IDs must match.)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="63353-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63353-135">See Also</span></span>  
 <span data-ttu-id="63353-136">[使用 MDSModelDeploy 部署模型部署封裝](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md) </span><span class="sxs-lookup"><span data-stu-id="63353-136">[Deploy a Model Deployment Package by Using MDSModelDeploy](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md) </span></span>  
 <span data-ttu-id="63353-137">[使用 Wizard 部署模型部署封裝](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="63353-137">[Deploy a Model Deployment Package by Using the Wizard](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md) </span></span>  
 [<span data-ttu-id="63353-138">部署模型 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="63353-138">Deploying Models &#40;Master Data Services&#41;</span></span>](deploying-models-master-data-services.md)  
  
  
