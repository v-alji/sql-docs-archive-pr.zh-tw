---
title: 封裝的重新部署 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- redeploying packages [Integration Services]
- deploying packages [Integration Services], redeploying
ms.assetid: 86806efb-8cf4-4f9d-9824-1152cb4c495c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4c5286d406d96f62fc74eb619f7e7a6064fde2a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687993"
---
# <a name="redeployment-of-packages"></a><span data-ttu-id="401c4-102">封裝的重新部署</span><span class="sxs-lookup"><span data-stu-id="401c4-102">Redeployment of Packages</span></span>
  <span data-ttu-id="401c4-103">在部署專案後，您可能需要更新或擴充封裝功能，然後部署包含已更新封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="401c4-103">After a project is deployed, you may need to update or extend package functionality and then redeploy the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the updated packages.</span></span> <span data-ttu-id="401c4-104">做為重新部署封裝處理的一部分，您應該檢視包含在部署公用程式中的組態屬性。</span><span class="sxs-lookup"><span data-stu-id="401c4-104">As part of the process of redeploying packages, you should review the configuration properties that are included in the deployment utility.</span></span> <span data-ttu-id="401c4-105">例如，您可能不允許組態在重新部署封裝之後變更。</span><span class="sxs-lookup"><span data-stu-id="401c4-105">For example, you may not want to allow configuration changes after the package is redeployed.</span></span>  
  
## <a name="process-for-redeployment"></a><span data-ttu-id="401c4-106">重新部署程序</span><span class="sxs-lookup"><span data-stu-id="401c4-106">Process for Redeployment</span></span>  
 <span data-ttu-id="401c4-107">在封裝更新完成後，您會重新建置專案、將部署資料夾複製到目標電腦，然後傳回 [封裝安裝精靈]。</span><span class="sxs-lookup"><span data-stu-id="401c4-107">After you finish updating the packages, you rebuild the project, copy the deployment folder to the target computer, and then rerun the Package Installation Wizard.</span></span>  
  
 <span data-ttu-id="401c4-108">如果您只更新專案中的幾個封裝，則可能不想重新部署整個專案。</span><span class="sxs-lookup"><span data-stu-id="401c4-108">If you update only a few packages in the project, you may not want to redeploy the entire project.</span></span> <span data-ttu-id="401c4-109">若要只部署幾個封裝，您可以建立新的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案、將已更新的封裝加入新的專案，然後建立和部署該專案。</span><span class="sxs-lookup"><span data-stu-id="401c4-109">To deploy only a few packages, you can create a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, add the updated packages to the new project, and then build and deploy the project.</span></span> <span data-ttu-id="401c4-110">當您將封裝加入其他專案時，封裝組態會自動隨封裝一同複製。</span><span class="sxs-lookup"><span data-stu-id="401c4-110">Package configurations are automatically copied with the package when you add the package to a different project.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="401c4-111">相關工作</span><span class="sxs-lookup"><span data-stu-id="401c4-111">Related Tasks</span></span>  
 [<span data-ttu-id="401c4-112">Deploy Packages by Using the Deployment Utility</span><span class="sxs-lookup"><span data-stu-id="401c4-112">Deploy Packages by Using the Deployment Utility</span></span>](../../2014/integration-services/deploy-packages-by-using-the-deployment-utility.md)  
  
  
