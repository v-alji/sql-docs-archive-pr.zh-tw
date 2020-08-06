---
title: 使用 MDSModelDeploy 部署模型部署套件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: fb2a4df4-5e0d-4b34-818f-383dbde1b15c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c23dcc592c2de34fa87703c8ba58d949dfec455c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597883"
---
# <a name="deploy-a-model-deployment-package-by-using-mdsmodeldeploy"></a><span data-ttu-id="f269c-102">使用 MDSModelDeploy 部署模型部署封裝</span><span class="sxs-lookup"><span data-stu-id="f269c-102">Deploy a Model Deployment Package by Using MDSModelDeploy</span></span>
  <span data-ttu-id="f269c-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，使用 MDSModelDeploy 工具來部署封裝，其中包含下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="f269c-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], use the MDSModelDeploy tool to deploy a package that contains either:</span></span>  
  
-   <span data-ttu-id="f269c-104">僅限模型物件。</span><span class="sxs-lookup"><span data-stu-id="f269c-104">Model objects only.</span></span>  
  
-   <span data-ttu-id="f269c-105">模型物件和資料。</span><span class="sxs-lookup"><span data-stu-id="f269c-105">Model objects and data.</span></span>  
  
 <span data-ttu-id="f269c-106">如果您想要部署只包含模型物件的封裝，您可以在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 應用程式中改用模型部署精靈。</span><span class="sxs-lookup"><span data-stu-id="f269c-106">If you want to deploy a package that contains model objects only, you can use the model deployment wizard in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application instead.</span></span> <span data-ttu-id="f269c-107">如需詳細資訊，請參閱 [使用精靈部署模型部署封裝](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="f269c-107">For more information, see [Deploy a Model Deployment Package by Using the Wizard](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f269c-108">封裝只能部署到之前建立封裝所使用的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="f269c-108">Packages can be deployed to the edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] they were created in only.</span></span> <span data-ttu-id="f269c-109">這表示，在 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 中建立的套件無法部署到 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="f269c-109">This means that packages created in [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] cannot be deployed to [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] or higher.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f269c-110">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="f269c-110">Prerequisites</span></span>  
 <span data-ttu-id="f269c-111">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="f269c-111">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="f269c-112">在目標 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 環境中，您必須擁有存取 [系統管理]\*\*\*\* 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="f269c-112">You must have permission to access the **System Administration** functional area in the target [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] environment.</span></span>  
  
-   <span data-ttu-id="f269c-113">模型部署封裝必須存在。</span><span class="sxs-lookup"><span data-stu-id="f269c-113">A model deployment package must exist.</span></span> <span data-ttu-id="f269c-114">如需詳細資訊，請參閱  [使用 MDSModelDeploy 建立模型部署套件](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md)。</span><span class="sxs-lookup"><span data-stu-id="f269c-114">For more information, see  [Create a Model Deployment Package by Using MDSModelDeploy](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md).</span></span>  
  
-   <span data-ttu-id="f269c-115">您必須是您要部署模型之環境中的管理員。</span><span class="sxs-lookup"><span data-stu-id="f269c-115">You must be an administrator in the environment where you are deploying the model.</span></span> <span data-ttu-id="f269c-116">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="f269c-116">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="f269c-117">如果您要使用資料更新模型，您所部署的版本就無法**鎖定**或**認可**。</span><span class="sxs-lookup"><span data-stu-id="f269c-117">If you are updating a model with data, the version you're deploying to cannot be **Locked** or **Committed**.</span></span>  
  
### <a name="to-deploy-a-model-deployment-package"></a><span data-ttu-id="f269c-118">若要部署模型部署封裝</span><span class="sxs-lookup"><span data-stu-id="f269c-118">To deploy a model deployment package</span></span>  
  
1.  <span data-ttu-id="f269c-119">決定您要部署新的模型、模型的複製，還是更新之前複製的模型。</span><span class="sxs-lookup"><span data-stu-id="f269c-119">Determine whether you are deploying a new model, a clone of a model, or updating a previously-cloned model.</span></span> <span data-ttu-id="f269c-120">如需詳細資訊，請參閱[模型部署選項 &#40;Master Data Services&#41;](../../2014/master-data-services/model-deployment-options-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="f269c-120">For more information, see [Model Deployment Options &#40;Master Data Services&#41;](../../2014/master-data-services/model-deployment-options-master-data-services.md).</span></span>  
  
2.  <span data-ttu-id="f269c-121">開啟命令提示字元，並導覽至 MDSModelDeploy.exe。</span><span class="sxs-lookup"><span data-stu-id="f269c-121">Open a command prompt and navigate to MDSModelDeploy.exe.</span></span>  
  
    -   <span data-ttu-id="f269c-122">如果 MDS 已安裝在預設位置，此工具可以在*磁片磁碟機*： \PROGRAM Files\Microsoft SQL Server\120\Master Data Services\Configuration\MDSModelDeploy.exe</span><span class="sxs-lookup"><span data-stu-id="f269c-122">If MDS is installed at the default location, the tool is available at *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services\Configuration\MDSModelDeploy.exe</span></span>  
  
    -   <span data-ttu-id="f269c-123">如果 MDS 未安裝在預設位置，請搜尋本機電腦中的 MDSModelDeploy.exe。</span><span class="sxs-lookup"><span data-stu-id="f269c-123">If MDS is not installed at the default location, search the local computer for MDSModelDeploy.exe.</span></span>  
  
3.  <span data-ttu-id="f269c-124">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f269c-124">Optional.</span></span> <span data-ttu-id="f269c-125">檢視選項和說明。</span><span class="sxs-lookup"><span data-stu-id="f269c-125">View options and help.</span></span>  
  
    -   <span data-ttu-id="f269c-126">若要顯示所有可用的選項，請輸入 `MDSModelDeploy` ，然後按 Enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="f269c-126">To display all available options, type `MDSModelDeploy` and press Enter.</span></span>  
  
    -   <span data-ttu-id="f269c-127">若要顯示某個選項的説明，請輸入 *，其中* OptionName `MDSModelDeploy help OptionName`是選項的名稱。</span><span class="sxs-lookup"><span data-stu-id="f269c-127">To display help for an option, type the following, where *OptionName* is the name of the option: `MDSModelDeploy help OptionName`.</span></span>  
  
4.  <span data-ttu-id="f269c-128">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f269c-128">Optional.</span></span> <span data-ttu-id="f269c-129">如果您有多個 Web 應用程式，請輸入以下命令並按 Enter 鍵，以判斷您要部署的目標服務名稱：</span><span class="sxs-lookup"><span data-stu-id="f269c-129">If you have multiple web applications, determine the name of the service you will deploy to by typing this command and pressing Enter:</span></span>  
  
    ```  
    MDSModelDeploy listservices  
    ```  
  
     <span data-ttu-id="f269c-130">隨即傳回值的清單，例如 `MDS1, Default Web Site, MDS`。</span><span class="sxs-lookup"><span data-stu-id="f269c-130">A list of values is returned, for example `MDS1, Default Web Site, MDS`.</span></span> <span data-ttu-id="f269c-131">此清單中的第一個值 (此案例中為 `MDS1`) 是部署模型所需的項目。</span><span class="sxs-lookup"><span data-stu-id="f269c-131">The first value in this list (in this case, `MDS1`) is needed to deploy the model.</span></span>  
  
5.  <span data-ttu-id="f269c-132">根據您是建立模型、複製模型還是更新模型，在命令提示字元輸入以下命令並按 Enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="f269c-132">Depending on whether you are creating a model, cloning a model, or updating a model, at the command prompt, type the following and press Enter.</span></span>  
  
    -   <span data-ttu-id="f269c-133">若要建立新模型：</span><span class="sxs-lookup"><span data-stu-id="f269c-133">To create a new model:</span></span>  
  
        ```  
        MDSModelDeploy deploynew -package PackageName -model ModelName -service ServiceName  
        ```  
  
    -   <span data-ttu-id="f269c-134">若要建立模型的複製：</span><span class="sxs-lookup"><span data-stu-id="f269c-134">To create a clone of a model:</span></span>  
  
        ```  
        MDSModelDeploy deployclone -package PackageName  
        ```  
  
    -   <span data-ttu-id="f269c-135">若要更新現有的模型及其資料：</span><span class="sxs-lookup"><span data-stu-id="f269c-135">To update an existing model and its data:</span></span>  
  
        ```  
        MDSModelDeploy deployupdate -package PackageName -version VersionName  
        ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="f269c-136">如果您使用 MDSModelDeploy 工具來更新現有模型及其資料，而且封裝不包含存在目的地模型中的實體、屬性或成員，MDSModelDeploy 就不會從模型中刪除該實體、屬性或成員。</span><span class="sxs-lookup"><span data-stu-id="f269c-136">If you use the MDSModelDeploy tool to update an existing model and its data, and the package does not contain an entity, attribute, or member that exists in the destination model, MDSModelDeploy will not delete that entity, attribute, or member from the model.</span></span>  
  
     <span data-ttu-id="f269c-137">其中 *PackageName* 是套件 (.pkg) 檔案的名稱、 *ModelName* 是新模型的名稱、 *VersionName* 是版本的名稱，而 *ServiceName* 是您在上一個步驟傳回的服務名稱。</span><span class="sxs-lookup"><span data-stu-id="f269c-137">Where *PackageName* is the name of the package (.pkg) file, *ModelName* is the name of the new model, *VersionName* is the name of the version, and *ServiceName* is the name of the service that you returned in the previous step.</span></span> <span data-ttu-id="f269c-138">確定模型和版本名稱符合區分大小寫的精確名稱。</span><span class="sxs-lookup"><span data-stu-id="f269c-138">Ensure that the model and version names match the exact case-sensitive names.</span></span>  
  
6.  <span data-ttu-id="f269c-139">當成功部署套件後，隨即顯示一則訊息，表示「MDSModelDeploy 作業已順利完成」。</span><span class="sxs-lookup"><span data-stu-id="f269c-139">When the package is successfully deployed, a message stating "MDSModelDeploy operation completed successfully" is displayed.</span></span>  
  
 <span data-ttu-id="f269c-140">**注意：**</span><span class="sxs-lookup"><span data-stu-id="f269c-140">**Notes:**</span></span>  
  
-   <span data-ttu-id="f269c-141">如果封裝中的訂閱視圖與現有模型中的訂閱視圖具有相同的名稱，則會將此視圖建立為*modelname. modelname.subscriptionviewname*。</span><span class="sxs-lookup"><span data-stu-id="f269c-141">If a subscription view in the package has the same name as a subscription view in an existing model, the view is created as *modelname.subscriptionviewname*.</span></span> <span data-ttu-id="f269c-142">如果此名稱已在使用中，則不會建立訂閱檢視。</span><span class="sxs-lookup"><span data-stu-id="f269c-142">If this name is already in use, the subscription view is not created.</span></span>  
  
-   <span data-ttu-id="f269c-143">部署程序有四個步驟：</span><span class="sxs-lookup"><span data-stu-id="f269c-143">The deployment process has four steps:</span></span>  
  
    1.  <span data-ttu-id="f269c-144">建立模型物件。</span><span class="sxs-lookup"><span data-stu-id="f269c-144">The model objects are created.</span></span>  
  
    2.  <span data-ttu-id="f269c-145">建立商務規則。</span><span class="sxs-lookup"><span data-stu-id="f269c-145">Business rules are created.</span></span>  
  
    3.  <span data-ttu-id="f269c-146">建立訂閱檢視。</span><span class="sxs-lookup"><span data-stu-id="f269c-146">Subscription views are created.</span></span>  
  
    4.  <span data-ttu-id="f269c-147">擴展主要資料。</span><span class="sxs-lookup"><span data-stu-id="f269c-147">Master data is populated.</span></span>  
  
-   <span data-ttu-id="f269c-148">當建立新的模型或複製的模型時，如果此程序在任何步驟期間失敗，就會刪除該模型。</span><span class="sxs-lookup"><span data-stu-id="f269c-148">When creating a new or cloned model, if the process fails during any step, the model is deleted.</span></span>  
  
     <span data-ttu-id="f269c-149">更新模型時，如果此程序在前三個步驟期間失敗，就不會繼續進行，但是，並不會回復已經進行的變更。</span><span class="sxs-lookup"><span data-stu-id="f269c-149">When updating a model, if the process fails during the first three steps, it does not proceed; however, changes that are already made are not rolled back.</span></span> <span data-ttu-id="f269c-150">如果此程序在步驟 4 失敗，則會更新可以更新的成員。</span><span class="sxs-lookup"><span data-stu-id="f269c-150">If the process fails in step 4, members that can be updated are updated.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f269c-151">後續步驟</span><span class="sxs-lookup"><span data-stu-id="f269c-151">Next Steps</span></span>  
 <span data-ttu-id="f269c-152">使用者定義的中繼資料、檔案屬性及使用者和群組的權限不包含在模型部署封裝中。</span><span class="sxs-lookup"><span data-stu-id="f269c-152">User-defined metadata, file attributes, and user and group permissions are not included in model deployment packages.</span></span> <span data-ttu-id="f269c-153">在部署模型之後，您必須手動更新這些項目。</span><span class="sxs-lookup"><span data-stu-id="f269c-153">After you deploy a model, you must update these manually.</span></span> <span data-ttu-id="f269c-154">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="f269c-154">For more information, see:</span></span>  
  
-   [<span data-ttu-id="f269c-155">新增中繼資料 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f269c-155">Add Metadata &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/add-metadata-master-data-services.md)  
  
-   [<span data-ttu-id="f269c-156">指派模型物件權限 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f269c-156">Assign Model Object Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="f269c-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f269c-157">See Also</span></span>  
 [<span data-ttu-id="f269c-158">部署模型 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f269c-158">Deploying Models &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/deploying-models-master-data-services.md)  
  
  
