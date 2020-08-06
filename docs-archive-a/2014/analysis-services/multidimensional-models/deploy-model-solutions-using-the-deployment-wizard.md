---
title: 使用部署嚮導部署模型方案 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services Deployment Wizard
- deploying [Analysis Services], Analysis Services Deployment Wizard
- Analysis Services deployments, Analysis Services Deployment Wizard
- Analysis Services Deployment Wizard, about Analysis Services Deployment Wizard
ms.assetid: ff711e8e-971c-43ba-b479-effc034af4a4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6e3dfd0b727fd917c37aa44aa8fd1d29326aaaa1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686520"
---
# <a name="deploy-model-solutions-using-the-deployment-wizard"></a><span data-ttu-id="97a07-102">使用部署精靈部署模型解決方案</span><span class="sxs-lookup"><span data-stu-id="97a07-102">Deploy Model Solutions Using the Deployment Wizard</span></span>
  <span data-ttu-id="97a07-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]部署嚮導會使用從專案產生的 XML 輸出檔 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 做為輸入檔。</span><span class="sxs-lookup"><span data-stu-id="97a07-103">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard uses the XML output files generated from a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project as input files.</span></span> <span data-ttu-id="97a07-104">這些輸入檔很容易進行修改，以自訂 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案的部署。</span><span class="sxs-lookup"><span data-stu-id="97a07-104">These input files are easily modifiable to customize the deployment of an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="97a07-105">產生的部署指令碼可以立即執行，或儲存供稍後進行部署使用。</span><span class="sxs-lookup"><span data-stu-id="97a07-105">The generated deployment script can then either be immediately run or saved for later deployment.</span></span>  
  
 <span data-ttu-id="97a07-106">您可以使用此處討論的精靈來進行部署，</span><span class="sxs-lookup"><span data-stu-id="97a07-106">You can deploy by using the wizard as discussed here.</span></span> <span data-ttu-id="97a07-107">也可以自動化部署或使用同步處理功能。</span><span class="sxs-lookup"><span data-stu-id="97a07-107">You can also automate deployment or use the Synchronize capability.</span></span> <span data-ttu-id="97a07-108">如果部署的資料庫很龐大，請考慮在目標系統上使用資料分割。</span><span class="sxs-lookup"><span data-stu-id="97a07-108">If the deployed database is large, consider using partitions on target systems.</span></span> <span data-ttu-id="97a07-109">您也可以使用分析管理物件 (AMO)，自動化資料分割的建立與擴展。</span><span class="sxs-lookup"><span data-stu-id="97a07-109">You can also automate partition creation and population by using Analysis Management Objects (AMO).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="97a07-110">如果您針對資料來源或模擬目的在連接字串中指定使用者識別碼或密碼，則 XML 輸出檔或部署指令碼都不會包含這些資訊。</span><span class="sxs-lookup"><span data-stu-id="97a07-110">Neither the XML output files nor the deployment script will contain the user id or password if these are specified in either the connection string for a data source or for impersonation purposes.</span></span> <span data-ttu-id="97a07-111">由於在這種狀況下需要使用這些資訊進行處理，所以您將手動加入這些資訊。</span><span class="sxs-lookup"><span data-stu-id="97a07-111">Since these are required for processing purposes in this scenario, you will add this information manually.</span></span> <span data-ttu-id="97a07-112">如果部署不包含處理，您就可以在部署之後視需要加入此連接和模擬資訊。</span><span class="sxs-lookup"><span data-stu-id="97a07-112">If the deployment will not include processing, you can add this connection and impersonation information as needed after deployment.</span></span> <span data-ttu-id="97a07-113">如果部署包含處理，您可以在儲存之後於精靈內部或在部署指令碼中加入這項資訊。</span><span class="sxs-lookup"><span data-stu-id="97a07-113">If the deployment will include processing, you can either add this information within the wizard or in the deployment script after it is saved.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="97a07-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="97a07-114">In This Section</span></span>  
 <span data-ttu-id="97a07-115">下列主題描述如何使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署精靈、輸入檔以及部署指令碼：</span><span class="sxs-lookup"><span data-stu-id="97a07-115">The following topics describe how to work with the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard, the input files, and the deployment script:</span></span>  
  
|<span data-ttu-id="97a07-116">主題</span><span class="sxs-lookup"><span data-stu-id="97a07-116">Topic</span></span>|<span data-ttu-id="97a07-117">描述</span><span class="sxs-lookup"><span data-stu-id="97a07-117">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="97a07-118">執行 Analysis Services 部署精靈</span><span class="sxs-lookup"><span data-stu-id="97a07-118">Running the Analysis Services Deployment Wizard</span></span>](running-the-analysis-services-deployment-wizard.md)|<span data-ttu-id="97a07-119">描述可以在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署精靈中執行的各種方式。</span><span class="sxs-lookup"><span data-stu-id="97a07-119">Describes the various ways in which you can run the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard.</span></span>|  
|[<span data-ttu-id="97a07-120">了解用來建立部署指令碼的輸入檔</span><span class="sxs-lookup"><span data-stu-id="97a07-120">Understanding the Input Files Used to Create the Deployment Script</span></span>](deployment-script-files-input-used-to-create-deployment-script.md)|<span data-ttu-id="97a07-121">描述 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署精靈使用哪些檔案做為輸入值、這些檔案中包含的內容，以及提供描述如何在這些輸入檔中修改值之主題的連結。</span><span class="sxs-lookup"><span data-stu-id="97a07-121">Describes which files the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard uses as input values, what each of those files contains, and provides links to topics that describe how to modify the values in each of the input files.</span></span>|  
|[<span data-ttu-id="97a07-122">了解 Analysis Services 部署指令碼</span><span class="sxs-lookup"><span data-stu-id="97a07-122">Understanding the Analysis Services Deployment Script</span></span>](understanding-the-analysis-services-deployment-script.md)|<span data-ttu-id="97a07-123">描述部署指令碼的內容，以及指令碼如何執行。</span><span class="sxs-lookup"><span data-stu-id="97a07-123">Describes what the deployment script contains and how the script runs.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="97a07-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97a07-124">See Also</span></span>  
 <span data-ttu-id="97a07-125">[使用 XMLA 部署模型方案](deploy-model-solutions-using-xmla.md) </span><span class="sxs-lookup"><span data-stu-id="97a07-125">[Deploy Model Solutions Using XMLA](deploy-model-solutions-using-xmla.md) </span></span>  
 <span data-ttu-id="97a07-126">[同步處理 Analysis Services 資料庫](synchronize-analysis-services-databases.md) </span><span class="sxs-lookup"><span data-stu-id="97a07-126">[Synchronize Analysis Services Databases](synchronize-analysis-services-databases.md) </span></span>  
 <span data-ttu-id="97a07-127">[瞭解用來建立部署腳本的輸入檔](deployment-script-files-input-used-to-create-deployment-script.md) </span><span class="sxs-lookup"><span data-stu-id="97a07-127">[Understanding the Input Files Used to Create the Deployment Script](deployment-script-files-input-used-to-create-deployment-script.md) </span></span>  
 [<span data-ttu-id="97a07-128">使用部署公用程式部署模型方案</span><span class="sxs-lookup"><span data-stu-id="97a07-128">Deploy Model Solutions with the Deployment Utility</span></span>](deploy-model-solutions-with-the-deployment-utility.md)  
  
  
