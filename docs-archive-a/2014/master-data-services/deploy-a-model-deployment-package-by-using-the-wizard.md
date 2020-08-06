---
title: 使用精靈部署模型部署套件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deployment packages [Master Data Services], deploying
- models [Master Data Services], deploying a package
ms.assetid: 4f65dc60-0ff8-46e6-9988-5bc5b9603ad0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 75af9f7c12d866c6d9707f62c898aa7601f94800
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705213"
---
# <a name="deploy-a-model-deployment-package-by-using-the-wizard"></a><span data-ttu-id="02081-102">使用精靈部署模型部署封裝</span><span class="sxs-lookup"><span data-stu-id="02081-102">Deploy a Model Deployment Package by Using the Wizard</span></span>
  <span data-ttu-id="02081-103">若要部署只包含模型物件的套件，請使用 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 模型部署精靈。</span><span class="sxs-lookup"><span data-stu-id="02081-103">Use the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] model deployment wizard to deploy packages that contain model objects only.</span></span> <span data-ttu-id="02081-104">如果您需要部署包含資料的套件，請參閱 [使用 MDSModelDeploy 部署模型部署封裝](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)。</span><span class="sxs-lookup"><span data-stu-id="02081-104">If you need to deploy a package with data, see [Deploy a Model Deployment Package by Using MDSModelDeploy](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="02081-105">封裝只能部署到之前建立封裝所使用的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="02081-105">Packages can be deployed to the edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] they were created in only.</span></span> <span data-ttu-id="02081-106">這表示，在 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 中建立的封裝無法部署到 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="02081-106">This means that packages created in [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] cannot be deployed to [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="02081-107">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="02081-107">Prerequisites</span></span>  
 <span data-ttu-id="02081-108">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="02081-108">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="02081-109">在目標 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 環境中，您必須擁有存取 [系統管理]\*\*\*\* 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="02081-109">You must have permission to access the **System Administration** functional area in the target [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] environment.</span></span>  
  
-   <span data-ttu-id="02081-110">模型部署封裝必須存在。</span><span class="sxs-lookup"><span data-stu-id="02081-110">A model deployment package must exist.</span></span> <span data-ttu-id="02081-111">如需詳細資訊，請參閱 [使用精靈建立模型部署封裝](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="02081-111">For more information, see [Create a Model Deployment Package by Using the Wizard](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md).</span></span>  
  
-   <span data-ttu-id="02081-112">您必須是您要部署模型之環境中的管理員。</span><span class="sxs-lookup"><span data-stu-id="02081-112">You must be an administrator in the environment where you are deploying the model.</span></span> <span data-ttu-id="02081-113">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="02081-113">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-deploy-a-model-deployment-package-of-model-objects-only"></a><span data-ttu-id="02081-114">若僅要部署模型物件的模型部署封裝</span><span class="sxs-lookup"><span data-stu-id="02081-114">To deploy a model deployment package of model objects only</span></span>  
  
1.  <span data-ttu-id="02081-115">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。</span><span class="sxs-lookup"><span data-stu-id="02081-115">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="02081-116">在 [模型檢視]\*\*\*\* 頁面上，從功能表列指向 [系統]\*\*\*\*，然後按一下 [部署]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02081-116">On the **Model View** page, from the menu bar, point to **System** and click **Deployment**.</span></span>  
  
3.  <span data-ttu-id="02081-117">按一下 [模型部署精靈]\*\*\*\* 上的 [部署]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02081-117">On the **Model Deployment Wizard**, click **Deploy**.</span></span>  
  
4.  <span data-ttu-id="02081-118">按一下 **[瀏覽]** 。</span><span class="sxs-lookup"><span data-stu-id="02081-118">Click **Browse**.</span></span>  
  
5.  <span data-ttu-id="02081-119">尋找您的部署套件 (.pkg 檔案)，然後按一下 [開啟]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02081-119">Find your deployment package (.pkg file) and click **Open**.</span></span>  
  
6.  <span data-ttu-id="02081-120">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="02081-120">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="02081-121">載入套件之後，按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02081-121">After the package is loaded, click **Next**.</span></span>  
  
8.  <span data-ttu-id="02081-122">如果模型已存在，您可以選取 [更新現有模型]\*\*\*\* 來更新模型。</span><span class="sxs-lookup"><span data-stu-id="02081-122">If the model already exists, you can update it by selecting **Update the existing model**.</span></span> <span data-ttu-id="02081-123">若要建立新的模型，請選取 [建立新模型]\*\*\*\*，然後在按 [下一步]\*\*\*\* 之後，輸入新模型的名稱。</span><span class="sxs-lookup"><span data-stu-id="02081-123">To create a new model, select **Create a new model** and after you click **Next** you can type a name for the new model.</span></span>  
  
9. <span data-ttu-id="02081-124">按一下 [完成]\*\*\*\* 結束精靈。</span><span class="sxs-lookup"><span data-stu-id="02081-124">Click **Finish** to exit the wizard.</span></span>  
  
 <span data-ttu-id="02081-125">**注意：**</span><span class="sxs-lookup"><span data-stu-id="02081-125">**Notes:**</span></span>  
  
-   <span data-ttu-id="02081-126">如果封裝中的訂閱視圖與現有模型中的訂閱視圖具有相同的名稱，則會將此視圖建立為*modelname. modelname.subscriptionviewname*。</span><span class="sxs-lookup"><span data-stu-id="02081-126">If a subscription view in the package has the same name as a subscription view in an existing model, the view is created as *modelname.subscriptionviewname*.</span></span> <span data-ttu-id="02081-127">如果此名稱已在使用中，則不會建立訂閱檢視。</span><span class="sxs-lookup"><span data-stu-id="02081-127">If this name is already in use, the subscription view is not created.</span></span>  
  
-   <span data-ttu-id="02081-128">部署程序有四個步驟：</span><span class="sxs-lookup"><span data-stu-id="02081-128">The deployment process has four steps:</span></span>  
  
    1.  <span data-ttu-id="02081-129">建立模型物件。</span><span class="sxs-lookup"><span data-stu-id="02081-129">The model objects are created.</span></span>  
  
    2.  <span data-ttu-id="02081-130">建立訂閱檢視。</span><span class="sxs-lookup"><span data-stu-id="02081-130">Subscription views are created.</span></span>  
  
    3.  <span data-ttu-id="02081-131">建立商務規則。</span><span class="sxs-lookup"><span data-stu-id="02081-131">Business rules are created.</span></span>  
  
    4.  <span data-ttu-id="02081-132">擴展主要資料。</span><span class="sxs-lookup"><span data-stu-id="02081-132">Master data is populated.</span></span>  
  
-   <span data-ttu-id="02081-133">當建立新的模型或複製的模型時，如果此程序在任何步驟期間失敗，就會刪除該模型。</span><span class="sxs-lookup"><span data-stu-id="02081-133">When creating a new or cloned model, if the process fails during any step, the model is deleted.</span></span>  
  
     <span data-ttu-id="02081-134">更新模型時，如果此程序在前三個步驟的任何一個期間失敗，就不會繼續進行，但是，並不會回復已經進行的變更。</span><span class="sxs-lookup"><span data-stu-id="02081-134">When updating a model, if the process fails during any of the first three steps, it does not proceed beyond that step; however, changes that are already made are not rolled back.</span></span> <span data-ttu-id="02081-135">如果此程序在步驟 4 失敗，則會更新可以更新的成員。</span><span class="sxs-lookup"><span data-stu-id="02081-135">If the process fails in step 4, members that can be updated are updated.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="02081-136">後續步驟</span><span class="sxs-lookup"><span data-stu-id="02081-136">Next Steps</span></span>  
 <span data-ttu-id="02081-137">使用者定義的中繼資料、檔案屬性及使用者和群組的權限不包含在模型部署封裝中。</span><span class="sxs-lookup"><span data-stu-id="02081-137">User-defined metadata, file attributes, and user and group permissions are not included in model deployment packages.</span></span> <span data-ttu-id="02081-138">在部署模型之後，您必須手動更新這些項目。</span><span class="sxs-lookup"><span data-stu-id="02081-138">After you deploy a model, you must update these manually.</span></span> <span data-ttu-id="02081-139">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="02081-139">For more information, see:</span></span>  
  
-   [<span data-ttu-id="02081-140">新增中繼資料 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="02081-140">Add Metadata &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/add-metadata-master-data-services.md)  
  
-   [<span data-ttu-id="02081-141">指派模型物件權限 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="02081-141">Assign Model Object Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="02081-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02081-142">See Also</span></span>  
 [<span data-ttu-id="02081-143">部署模型 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="02081-143">Deploying Models &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/deploying-models-master-data-services.md)  
  
  
