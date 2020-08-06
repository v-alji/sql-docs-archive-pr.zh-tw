---
title: 使用 MDSModelDeploy 建立模型部署套件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: c2687e39-dc20-494f-a707-2aa29f4c329e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c546d6398234dd43103d0e6c75822377e11de61a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606954"
---
# <a name="create-a-model-deployment-package-by-using-mdsmodeldeploy"></a><span data-ttu-id="dddbe-102">使用 MDSModelDeploy 建立模型部署封裝</span><span class="sxs-lookup"><span data-stu-id="dddbe-102">Create a Model Deployment Package by Using MDSModelDeploy</span></span>
  <span data-ttu-id="dddbe-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，使用 MDSModelDeploy 工具來建立封裝。</span><span class="sxs-lookup"><span data-stu-id="dddbe-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], use the MDSModelDeploy tool to create a package.</span></span> <span data-ttu-id="dddbe-104">根據您指定的命令，此封裝可以包含：</span><span class="sxs-lookup"><span data-stu-id="dddbe-104">Depending on the commands you specify, the package can contain either:</span></span>  
  
-   <span data-ttu-id="dddbe-105">僅限模型物件。</span><span class="sxs-lookup"><span data-stu-id="dddbe-105">Model objects only.</span></span>  
  
-   <span data-ttu-id="dddbe-106">模型物件和資料。</span><span class="sxs-lookup"><span data-stu-id="dddbe-106">Model objects and data.</span></span>  
  
 <span data-ttu-id="dddbe-107">如果您想要部署只包含模型物件的封裝，您可以在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 應用程式中改用模型部署精靈。</span><span class="sxs-lookup"><span data-stu-id="dddbe-107">If you want to deploy a package that contains model objects only, you can use the model deployment wizard in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application instead.</span></span> <span data-ttu-id="dddbe-108">如需詳細資訊，請參閱 [使用精靈建立模型部署封裝](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="dddbe-108">For more information, see [Create a Model Deployment Package by Using the Wizard](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md).</span></span>  
> [!NOTE]  
> <span data-ttu-id="dddbe-109">這個版本的 MDSModelDeploy 工具無法使用超過 gb (GB 的記憶體) 。</span><span class="sxs-lookup"><span data-stu-id="dddbe-109">This version of the MDSModelDeploy tool cannot use more than gigabytes (GB) of memory.</span></span> <span data-ttu-id="dddbe-110">當您使用**模型物件和資料**選項建立或部署大型模型時，可能會遇到「記憶體不足」或「資料流程太長」錯誤。</span><span class="sxs-lookup"><span data-stu-id="dddbe-110">When you create or deploy large models by using **Model objects and data** option, you may experience "Out of Memory" or "Stream was too long" errors.</span></span> <span data-ttu-id="dddbe-111">若要解決此問題，請使用 MDS 預備環境來部署資料;或升級至 MDS 2016 或更新版本，其中包含 MDSModelDeploy 工具的更新版本。</span><span class="sxs-lookup"><span data-stu-id="dddbe-111">To resolve this issue, use MDS staging to deploy the data; or upgrade to MDS 2016 or a later version, which includes the updated version of the MDSModelDeploy tool.</span></span>
## <a name="prerequisites"></a><span data-ttu-id="dddbe-112">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="dddbe-112">Prerequisites</span></span>  
 <span data-ttu-id="dddbe-113">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="dddbe-113">To perform this procedure:</span></span>  
  
1.  <span data-ttu-id="dddbe-114">執行 MDSModelDeploy 工作所需的基本權限如下：</span><span class="sxs-lookup"><span data-stu-id="dddbe-114">The basic permissions required to run the MDSModelDeploy tool are the following:</span></span>  
  
    -   <span data-ttu-id="dddbe-115">與 MDS 組態管理員相同的 Windows 權限 (Windows 管理員)</span><span class="sxs-lookup"><span data-stu-id="dddbe-115">The same Windows permission as the MDS Configuration Manager (administrator of Windows)</span></span>  
  
    -   <span data-ttu-id="dddbe-116">MDS 資料庫的 DBA 權限。</span><span class="sxs-lookup"><span data-stu-id="dddbe-116">DBA permission on the MDS database.</span></span>  
  
2.  <span data-ttu-id="dddbe-117">使用 MDSModelDeploy 工作建立封裝所需的權限如下：</span><span class="sxs-lookup"><span data-stu-id="dddbe-117">The permissions required to create the package using the MDSModelDeploy tool are the following:</span></span>  
  
    -   <span data-ttu-id="dddbe-118">資料模型的 MDS 模型管理員權限。</span><span class="sxs-lookup"><span data-stu-id="dddbe-118">MDS model administrator permission on the data model.</span></span>  
  
    -   <span data-ttu-id="dddbe-119">MDS 整合管理功能權限。</span><span class="sxs-lookup"><span data-stu-id="dddbe-119">MDS Integration Management function permission.</span></span>  
  
3.  <span data-ttu-id="dddbe-120">使用 MDSModelDeploy 工作部署模型所需的權限如下：</span><span class="sxs-lookup"><span data-stu-id="dddbe-120">The permissions required to deploy a model using the MDSModelDeploy tool are the following:</span></span>  
  
    -   <span data-ttu-id="dddbe-121">MDS Explorer 功能權限</span><span class="sxs-lookup"><span data-stu-id="dddbe-121">MDS Explorer function permission</span></span>  
  
    -   <span data-ttu-id="dddbe-122">MDS 整合管理功能權限</span><span class="sxs-lookup"><span data-stu-id="dddbe-122">MDS Integration Management function permission</span></span>  
  
    -   <span data-ttu-id="dddbe-123">MDS 系統管理功能權限。</span><span class="sxs-lookup"><span data-stu-id="dddbe-123">MDS System Administration function permission.</span></span>  
  
4.  <span data-ttu-id="dddbe-124">使用 MDSModelDeploy 工作列出模型所需的權限如下：</span><span class="sxs-lookup"><span data-stu-id="dddbe-124">The permissions required to list models using the MDSModelDeploy tool are the following:</span></span>  
  
    -   <span data-ttu-id="dddbe-125">MDS Explorer 功能權限</span><span class="sxs-lookup"><span data-stu-id="dddbe-125">MDS Explorer function permission</span></span>  
  
    -   <span data-ttu-id="dddbe-126">在訂單的資料模型上查看清單中模型的 MDS 模型管理員權限。</span><span class="sxs-lookup"><span data-stu-id="dddbe-126">MDS model administrator permission on the data model on order to see the model in the list.</span></span>  
  
 <span data-ttu-id="dddbe-127">模型必須存在，才能建立其封裝。</span><span class="sxs-lookup"><span data-stu-id="dddbe-127">A model must exist for you to create a package of.</span></span> <span data-ttu-id="dddbe-128">如需詳細資訊，請參閱[建立模型 &#40;Master Data Services&#41;](create-a-model-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="dddbe-128">For more information, see [Create a Model &#40;Master Data Services&#41;](create-a-model-master-data-services.md).</span></span>  
  
 <span data-ttu-id="dddbe-129">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="dddbe-129">For more information, see [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).</span></span>  
  
### <a name="to-create-a-model-deployment-package-by-using-mdsmodeldeploy"></a><span data-ttu-id="dddbe-130">若要使用 MDSModelDeploy 建立模型部署封裝</span><span class="sxs-lookup"><span data-stu-id="dddbe-130">To create a model deployment package by using MDSModelDeploy</span></span>  
  
1.  <span data-ttu-id="dddbe-131">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="dddbe-131">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="dddbe-132">導覽至 MDSModelDeploy.exe 的位置。</span><span class="sxs-lookup"><span data-stu-id="dddbe-132">Navigate to the location of MDSModelDeploy.exe.</span></span>  
  
    -   <span data-ttu-id="dddbe-133">如果 MDS 已安裝在預設位置，檔案就會在*磁片磁碟機*： \PROGRAM Files\Microsoft SQL Server\120\Master Data services\configuration。中。</span><span class="sxs-lookup"><span data-stu-id="dddbe-133">If MDS was installed in the default location, the file is in *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services\Configuration.</span></span>  
  
    -   <span data-ttu-id="dddbe-134">如果 MDS 未安裝在預設位置，請搜尋本機電腦中的 MDSModelDeploy.exe。</span><span class="sxs-lookup"><span data-stu-id="dddbe-134">If MDS was not installed in the default location, search the local computer for MDSModelDeploy.exe.</span></span>  
  
3.  <span data-ttu-id="dddbe-135">選擇性。</span><span class="sxs-lookup"><span data-stu-id="dddbe-135">Optional.</span></span> <span data-ttu-id="dddbe-136">檢視選項和說明。</span><span class="sxs-lookup"><span data-stu-id="dddbe-136">View options and help.</span></span>  
  
    -   <span data-ttu-id="dddbe-137">若要顯示所有可用的選項，請輸入 `MDSModelDeploy` ，然後按 Enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="dddbe-137">To display all available options, type `MDSModelDeploy` and press Enter.</span></span>  
  
    -   <span data-ttu-id="dddbe-138">若要顯示某個選項的説明，請輸入 *，其中* OptionName `MDSModelDeploy help OptionName`是選項的名稱。</span><span class="sxs-lookup"><span data-stu-id="dddbe-138">To display help for an option, type the following, where *OptionName* is the name of the option: `MDSModelDeploy help OptionName`.</span></span>  
  
4.  <span data-ttu-id="dddbe-139">選擇性。</span><span class="sxs-lookup"><span data-stu-id="dddbe-139">Optional.</span></span> <span data-ttu-id="dddbe-140">如果您有多個 Web 應用程式，請輸入以下命令並按 Enter 鍵，以判斷您要部署的目標服務名稱：</span><span class="sxs-lookup"><span data-stu-id="dddbe-140">If you have multiple web applications, determine the name of the service you will deploy to by typing this command and pressing Enter:</span></span>  
  
    ```  
    MDSModelDeploy listservices  
    ```  
  
     <span data-ttu-id="dddbe-141">隨即傳回值的清單，例如 `MDS1, Default Web Site, MDS`。</span><span class="sxs-lookup"><span data-stu-id="dddbe-141">A list of values is returned, for example `MDS1, Default Web Site, MDS`.</span></span> <span data-ttu-id="dddbe-142">此清單中的第一個值 (此案例中為 `MDS1`) 是部署模型所需的項目。</span><span class="sxs-lookup"><span data-stu-id="dddbe-142">The first value in this list (in this case, `MDS1`) is needed to deploy the model.</span></span>  
  
5.  <span data-ttu-id="dddbe-143">若要建立包含模型物件和資料的封裝，請輸入下列命令，其中 *ModelName*、 *VersionName*、 *ServiceName*和 *PackageName* 分別是模型、版本、服務和 .pkg 輸出檔的名稱：</span><span class="sxs-lookup"><span data-stu-id="dddbe-143">To create a package that contains model objects and data, type the following, where *ModelName*, *VersionName*, *ServiceName*,  and *PackageName* are the names of the model, version, service, and of the .pkg output file respectively:</span></span>  
  
    ```  
    MDSModelDeploy createpackage -model ModelName -version VersionName -service ServiceName -package PackageName -includedata  
    ```  
  
     <span data-ttu-id="dddbe-144">如果您不想要包含資料，請勿使用 `-version` 和 `-includedata` 參數。</span><span class="sxs-lookup"><span data-stu-id="dddbe-144">If you do not want to include data, do not use the `-version` and `-includedata` switches.</span></span>  
  
6.  <span data-ttu-id="dddbe-145">按 Enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="dddbe-145">Press Enter.</span></span> <span data-ttu-id="dddbe-146">當成功建立套件之後，隨即顯示一則訊息，表示「MDSModelDeploy 作業已順利完成」。</span><span class="sxs-lookup"><span data-stu-id="dddbe-146">When the package is successfully created, a message stating "MDSModelDeploy operation completed successfully" is displayed.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="dddbe-147">後續步驟</span><span class="sxs-lookup"><span data-stu-id="dddbe-147">Next Steps</span></span>  
  
-   [<span data-ttu-id="dddbe-148">使用 MDSModelDeploy 部署模型部署封裝</span><span class="sxs-lookup"><span data-stu-id="dddbe-148">Deploy a Model Deployment Package by Using MDSModelDeploy</span></span>](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)  
  
## <a name="see-also"></a><span data-ttu-id="dddbe-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dddbe-149">See Also</span></span>  
 <span data-ttu-id="dddbe-150">[模型部署選項 &#40;Master Data Services&#41;](../../2014/master-data-services/model-deployment-options-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="dddbe-150">[Model Deployment Options &#40;Master Data Services&#41;](../../2014/master-data-services/model-deployment-options-master-data-services.md) </span></span>  
 [<span data-ttu-id="dddbe-151">部署模型 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="dddbe-151">Deploying Models &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/deploying-models-master-data-services.md)  
  
  
