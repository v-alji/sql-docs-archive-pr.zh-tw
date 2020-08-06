---
title: 建立部署公用程式 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- deploying packages [Integration Services], deployment utility
- deployment utility [Integration Services]
ms.assetid: 354322a4-ae8c-4d92-8e71-42d29dbd0614
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bdf1328d440920fed98e5fa1d16024c5fec32cbb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596836"
---
# <a name="create-a-deployment-utility"></a><span data-ttu-id="1b7d3-102">Create a Deployment Utility</span><span class="sxs-lookup"><span data-stu-id="1b7d3-102">Create a Deployment Utility</span></span>
  <span data-ttu-id="1b7d3-103">部署封裝的第一步是建立 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案的部署公用程式。</span><span class="sxs-lookup"><span data-stu-id="1b7d3-103">The first step in deploying packages is to create a deployment utility for an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span> <span data-ttu-id="1b7d3-104">部署公用程式是一個資料夾，包含在其他伺服器的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案中部署封裝所需的檔案。</span><span class="sxs-lookup"><span data-stu-id="1b7d3-104">The deployment utility is a folder that contains the files you need to deploy the packages in an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project on a different server.</span></span> <span data-ttu-id="1b7d3-105">部署公用程式在儲存 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案的電腦上建立。</span><span class="sxs-lookup"><span data-stu-id="1b7d3-105">The deployment utility is created on the computer on which the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project is stored.</span></span>  
  
 <span data-ttu-id="1b7d3-106">建立 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案之封裝部署公用程式的方法是先設定建立部署公用程式的建立程序，然後再建立專案。</span><span class="sxs-lookup"><span data-stu-id="1b7d3-106">You create a package deployment utility for an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project by first configuring the build process to create a deployment utility, and then building the project.</span></span> <span data-ttu-id="1b7d3-107">建立專案時，會自動併入專案中所有的封裝和封裝組態。</span><span class="sxs-lookup"><span data-stu-id="1b7d3-107">When you build the project, all packages and package configurations in the project are automatically included.</span></span> <span data-ttu-id="1b7d3-108">若要部署專案的其他檔案 (例如讀我檔案)，請將檔案放置在 **專案的** [Miscellaneous] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="1b7d3-108">To deploy additional files such as a Readme file with the project, place the files in the **Miscellaneous** folder of the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span> <span data-ttu-id="1b7d3-109">建立專案時，會自動併入這些檔案。</span><span class="sxs-lookup"><span data-stu-id="1b7d3-109">When the project is built, these files are also automatically included.</span></span>  
  
 <span data-ttu-id="1b7d3-110">您可以不同的方式設定每一個專案部署。</span><span class="sxs-lookup"><span data-stu-id="1b7d3-110">You can configure each project deployment differently.</span></span> <span data-ttu-id="1b7d3-111">在建立專案和建立封裝部署公用程式之前，您可以設定部署公用程式上的屬性，以自訂在專案中部署封裝的方式。</span><span class="sxs-lookup"><span data-stu-id="1b7d3-111">Before you build the project and create the package deployment utility, you can set the properties on the deployment utility to customize the way the packages in the project will be deployed.</span></span> <span data-ttu-id="1b7d3-112">例如，可以指定在部署專案時是否可以更新封裝組態。</span><span class="sxs-lookup"><span data-stu-id="1b7d3-112">For example, you can specify whether package configurations can be updated when the project is deployed.</span></span> <span data-ttu-id="1b7d3-113">若要存取 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案的屬性，請以滑鼠右鍵按一下專案，然後按一下 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="1b7d3-113">To access the properties of an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, right-click the project and click **Properties**.</span></span>  
  
 <span data-ttu-id="1b7d3-114">下表列出部署公用程式屬性。</span><span class="sxs-lookup"><span data-stu-id="1b7d3-114">The following table lists the deployment utility properties.</span></span>  
  
|<span data-ttu-id="1b7d3-115">屬性</span><span class="sxs-lookup"><span data-stu-id="1b7d3-115">Property</span></span>|<span data-ttu-id="1b7d3-116">描述</span><span class="sxs-lookup"><span data-stu-id="1b7d3-116">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="1b7d3-117">AllowConfigurationChange</span><span class="sxs-lookup"><span data-stu-id="1b7d3-117">AllowConfigurationChange</span></span>|<span data-ttu-id="1b7d3-118">指定部署期間是否可以更新組態的值。</span><span class="sxs-lookup"><span data-stu-id="1b7d3-118">A value that specifies whether configurations can be updated during deployment.</span></span>|  
|<span data-ttu-id="1b7d3-119">[CreateDeploymentUtility]</span><span class="sxs-lookup"><span data-stu-id="1b7d3-119">CreateDeploymentUtility</span></span>|<span data-ttu-id="1b7d3-120">指定建立專案時是否建立封裝部署公用程式的值。</span><span class="sxs-lookup"><span data-stu-id="1b7d3-120">A value that specifies whether a package deployment utility is created when the project is built.</span></span> <span data-ttu-id="1b7d3-121">此屬性必須為 `True`，才能建立部署公用程式。</span><span class="sxs-lookup"><span data-stu-id="1b7d3-121">This property must be `True` to create a deployment utility.</span></span>|  
|<span data-ttu-id="1b7d3-122">DeploymentOutputPath</span><span class="sxs-lookup"><span data-stu-id="1b7d3-122">DeploymentOutputPath</span></span>|<span data-ttu-id="1b7d3-123">與部署公用程式之 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案相關的位置。</span><span class="sxs-lookup"><span data-stu-id="1b7d3-123">The location, relative to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, of the deployment utility.</span></span>|  
  
 <span data-ttu-id="1b7d3-124">建立 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案時，會建立資訊清單檔 \<project name>.SSISDeploymentManifest.xml，以及專案套件和套件相依性的複本，並將資訊清單檔和這些複本新增至專案的 bin\Deployment 資料夾，或新增至 DeploymentOutputPath 屬性所指定的位置。</span><span class="sxs-lookup"><span data-stu-id="1b7d3-124">When you build an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, a manifest file, \<project name>.SSISDeploymentManifest.xml, is created and added, together with copies of the project packages and package dependencies, to the bin\Deployment folder in the project, or to the location specified in the DeploymentOutputPath property.</span></span> <span data-ttu-id="1b7d3-125">資訊清單檔會列出專案中的封裝、封裝組態和任何其他檔案。</span><span class="sxs-lookup"><span data-stu-id="1b7d3-125">The manifest file lists the packages, the package configurations, and any miscellaneous files in the project.</span></span>  
  
 <span data-ttu-id="1b7d3-126">每次建立專案時，都會重新整理部署資料夾的內容。</span><span class="sxs-lookup"><span data-stu-id="1b7d3-126">The content of the deployment folder is refreshed every time that you build the project.</span></span> <span data-ttu-id="1b7d3-127">這表示系統將會刪除儲存在這個資料夾，而建立程序並未重新複製到資料夾中的任何檔案。</span><span class="sxs-lookup"><span data-stu-id="1b7d3-127">This means that any file saved to this folder that is not copied to the folder again by the build process will be deleted.</span></span> <span data-ttu-id="1b7d3-128">例如，儲存在部署資料夾的封裝組態檔案將會被刪除。</span><span class="sxs-lookup"><span data-stu-id="1b7d3-128">For example, package configuration files saved to the deployment folders will be deleted.</span></span>  
  
### <a name="to-create-a-package-deployment-utility"></a><span data-ttu-id="1b7d3-129">建立封裝部署公用程式</span><span class="sxs-lookup"><span data-stu-id="1b7d3-129">To create a package deployment utility</span></span>  
  
1.  <span data-ttu-id="1b7d3-130">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含要為其建立封裝部署公用程式之 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案的方案。</span><span class="sxs-lookup"><span data-stu-id="1b7d3-130">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the solution that contains the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project for which you want to create a package deployment utility.</span></span>  
  
2.  <span data-ttu-id="1b7d3-131">以滑鼠右鍵按一下專案，然後按一下 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="1b7d3-131">Right-click the project and click **Properties**.</span></span>  
  
3.  <span data-ttu-id="1b7d3-132">在 [\<project name> 屬性頁面] 對話方塊中，按一下 [部署公用程式]。</span><span class="sxs-lookup"><span data-stu-id="1b7d3-132">In the **\<project name> Property Pages** dialog box, click **Deployment Utility**.</span></span>  
  
4.  <span data-ttu-id="1b7d3-133">若要在部署套件時更新封裝設定，請將**AllowConfigurationChanges**設為 `True` 。</span><span class="sxs-lookup"><span data-stu-id="1b7d3-133">To update package configurations when packages are deployed, set **AllowConfigurationChanges** to `True`.</span></span>  
  
5.  <span data-ttu-id="1b7d3-134">將 `CreateDeploymentUtility` 設定為 `True`。</span><span class="sxs-lookup"><span data-stu-id="1b7d3-134">Set `CreateDeploymentUtility` to `True`.</span></span>  
  
6.  <span data-ttu-id="1b7d3-135">選擇性地修改 `DeploymentOutputPath` 屬性，以更新部署公用程式的位置。</span><span class="sxs-lookup"><span data-stu-id="1b7d3-135">Optionally, update the location of the deployment utility by modifying the `DeploymentOutputPath` property.</span></span>  
  
7.  <span data-ttu-id="1b7d3-136">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="1b7d3-136">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="1b7d3-137">在方案總管中，以滑鼠右鍵按一下專案，然後按一下 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="1b7d3-137">In Solution Explorer, right-click the project, and then click **Build**.</span></span>  
  
9. <span data-ttu-id="1b7d3-138">檢視 **[輸出]** 視窗中的建立進度和建立錯誤。</span><span class="sxs-lookup"><span data-stu-id="1b7d3-138">View the build progress and build errors in the **Output** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b7d3-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b7d3-139">See Also</span></span>  
 <span data-ttu-id="1b7d3-140">[套件設定](../../2014/integration-services/package-configurations.md) </span><span class="sxs-lookup"><span data-stu-id="1b7d3-140">[Package Configurations](../../2014/integration-services/package-configurations.md) </span></span>  
 <span data-ttu-id="1b7d3-141">[建立套件設定](../../2014/integration-services/create-package-configurations.md) </span><span class="sxs-lookup"><span data-stu-id="1b7d3-141">[Create Package Configurations](../../2014/integration-services/create-package-configurations.md) </span></span>  
 <span data-ttu-id="1b7d3-142">[使用部署公用程式來部署封裝](../../2014/integration-services/deploy-packages-by-using-the-deployment-utility.md) </span><span class="sxs-lookup"><span data-stu-id="1b7d3-142">[Deploy Packages by Using the Deployment Utility](../../2014/integration-services/deploy-packages-by-using-the-deployment-utility.md) </span></span>  
 [<span data-ttu-id="1b7d3-143">&#40;SSIS&#41;的套件部署</span><span class="sxs-lookup"><span data-stu-id="1b7d3-143">Package Deployment &#40;SSIS&#41;</span></span>](packages/legacy-package-deployment-ssis.md)  
  
  
