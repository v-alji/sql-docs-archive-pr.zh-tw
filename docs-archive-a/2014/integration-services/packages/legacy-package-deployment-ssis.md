---
title: " (SSIS) 的套件部署 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, deploying
- deploying packages [Integration Services]
- SQL Server Integration Services packages, deploying
- deploying packages [Integration Services], about deploying packages
- packages [Integration Services], deploying
- SSIS packages, deploying
ms.assetid: 0f5fc7be-e37e-4ecd-ba99-697c8ae3436f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 32627eddf5e7a696decd549e9b87ebb5c3b9d031
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597199"
---
# <a name="package-deployment-ssis"></a><span data-ttu-id="67ede-102">封裝部署 (SSIS)</span><span class="sxs-lookup"><span data-stu-id="67ede-102">Package Deployment (SSIS)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="67ede-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 所包含工具和精靈可以簡化將套件從開發電腦部署到實際伺服器或部署到其他電腦的流程。</span><span class="sxs-lookup"><span data-stu-id="67ede-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes tools and wizards that make it simple to deploy packages from the development computer to the production server or to other computers.</span></span>  
  
 <span data-ttu-id="67ede-104">封裝部署處理有四個步驟：</span><span class="sxs-lookup"><span data-stu-id="67ede-104">There are four steps in the package deployment process:</span></span>  
  
1.  <span data-ttu-id="67ede-105">第一個選擇性的步驟是選擇性的，包含建立可在執行階段更新封裝元素屬性的封裝組態。</span><span class="sxs-lookup"><span data-stu-id="67ede-105">The first optional step is optional and involves creating package configurations that update properties of package elements at run time.</span></span> <span data-ttu-id="67ede-106">部署封裝時，會自動包含這些組態。</span><span class="sxs-lookup"><span data-stu-id="67ede-106">The configurations are automatically included when you deploy the packages.</span></span>  
  
2.  <span data-ttu-id="67ede-107">第二步是建立 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案，以建立封裝部署公用程式。</span><span class="sxs-lookup"><span data-stu-id="67ede-107">The second step is to build the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project to create a package deployment utility.</span></span> <span data-ttu-id="67ede-108">專案的部署公用程式包含您要部署的封裝</span><span class="sxs-lookup"><span data-stu-id="67ede-108">The deployment utility for the project contains the packages that you want to deploy</span></span>  
  
3.  <span data-ttu-id="67ede-109">第三步是將建立 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案時所建立的部署資料夾複製到目標電腦。</span><span class="sxs-lookup"><span data-stu-id="67ede-109">The third step is to copy the deployment folder that was created when you built the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project to the target computer.</span></span>  
  
4.  <span data-ttu-id="67ede-110">第四步是在目標電腦上執行 [封裝安裝精靈]，將封裝安裝到檔案系統或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="67ede-110">The fourth step is to run, on the target computer, the Package Installation Wizard to install the packages to the file system or to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="67ede-111">相關工作</span><span class="sxs-lookup"><span data-stu-id="67ede-111">Related Tasks</span></span>  
 <span data-ttu-id="67ede-112">如需如何建立部署公用程式的資訊，請參閱 [Create a Deployment Utility](../create-a-deployment-utility.md)(建立部署公用程式)。</span><span class="sxs-lookup"><span data-stu-id="67ede-112">For information about how to create a deployment utility, see [Create a Deployment Utility](../create-a-deployment-utility.md).</span></span>  
  
 <span data-ttu-id="67ede-113">如需如何使用部署公用程式來部署封裝的資訊，請參閱 [Deploy Packages by Using the Deployment Utility](../deploy-packages-by-using-the-deployment-utility.md)(使用部署公用程式來部署封裝)。</span><span class="sxs-lookup"><span data-stu-id="67ede-113">For information about how to deploy packages using the deployment utility, see [Deploy Packages by Using the Deployment Utility](../deploy-packages-by-using-the-deployment-utility.md).</span></span>  
  
 <span data-ttu-id="67ede-114">如需如何建立封裝組態的資訊，請參閱 [Create Package Configurations](../create-package-configurations.md)(建立封裝組態)。</span><span class="sxs-lookup"><span data-stu-id="67ede-114">For information about how to create package configurations, see [Create Package Configurations](../create-package-configurations.md).</span></span>  
  
  
