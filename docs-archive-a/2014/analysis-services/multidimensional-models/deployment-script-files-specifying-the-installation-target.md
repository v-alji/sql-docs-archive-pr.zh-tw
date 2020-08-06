---
title: 指定安裝目標 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- input files [Analysis Services]
- installation targets [Analysis Services]
- Analysis Services deployments, installation targets
- Analysis Services Deployment Wizard, installation targets
- deploying [Analysis Services], installation targets
- modifying installation targets
ms.assetid: cb706817-6f63-4771-92c3-b70030bbce3d
author: minewiskan
ms.author: owend
ms.openlocfilehash: e830fc353898e3ec835b338e84765a0cad0de43f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596939"
---
# <a name="specifying-the-installation-target"></a><span data-ttu-id="cd1da-102">指定安裝目標</span><span class="sxs-lookup"><span data-stu-id="cd1da-102">Specifying the Installation Target</span></span>
  <span data-ttu-id="cd1da-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]部署嚮導會從 .deploymenttargets 檔案讀取安裝目標資訊 \<*project name*> 。</span><span class="sxs-lookup"><span data-stu-id="cd1da-103">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard reads the installation target information from the \<*project name*>.deploymenttargets file.</span></span> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="cd1da-104">當您建立專案時，會建立這個檔案 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cd1da-104">creates this file when you build the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="cd1da-105">使用 [屬性頁] 對話方塊之 [**部署**] 頁面上指定的資料庫和伺服器 *\<project name>* **Properties Pages**來建立 \<*project name*> .targets 檔案。</span><span class="sxs-lookup"><span data-stu-id="cd1da-105">uses the database and server specified on the **Deployment** page of the *\<project name>* **Properties Pages** dialog box to create the \<*project name*>.targets file.</span></span>  
  
## <a name="modifying-the-installation-target-for-deployment"></a><span data-ttu-id="cd1da-106">修改部署的安裝目標</span><span class="sxs-lookup"><span data-stu-id="cd1da-106">Modifying the Installation Target for Deployment</span></span>  
 <span data-ttu-id="cd1da-107">在某些情況下，您可能需要將 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案部署到與 [部署]\*\*\*\* 頁面所指定之不同的資料庫或 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體上。</span><span class="sxs-lookup"><span data-stu-id="cd1da-107">In some situations, you may need to deploy an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project to a database or [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance that is different than the one specified on the **Deployment** page.</span></span> <span data-ttu-id="cd1da-108">例如，您可能需要在部署之前先將專案部署到伺服器以進行測試，然後在測試完成後再部署到實際伺服器。</span><span class="sxs-lookup"><span data-stu-id="cd1da-108">For example, you may want to deploy the project to a server for testing before deployment, and then deploy it to a production server after testing is finished.</span></span> <span data-ttu-id="cd1da-109">您也可能需要將完整與測試的專案部署到網路負載平衡叢集中的多個實際伺服器，或部署到臨時伺服器和實際伺服器。</span><span class="sxs-lookup"><span data-stu-id="cd1da-109">You may also want to deploy a completed and tested project to multiple production servers in a Network Load Balancing cluster, or to a staging server and a production server.</span></span>  
  
 <span data-ttu-id="cd1da-110">若要將 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案部署到不同的資料庫或 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體，您可以使用下列程序描述的方法之一，來變更輸入檔中的安裝目標。</span><span class="sxs-lookup"><span data-stu-id="cd1da-110">To deploy an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project to a different database or [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, you can change the installation target in the input file by using one of the methods described in the following procedure.</span></span>  
  
#### <a name="to-change-the-installation-target-after-the-input-files-have-been-generated"></a><span data-ttu-id="cd1da-111">若要在已產生輸入檔之後，變更安裝目標</span><span class="sxs-lookup"><span data-stu-id="cd1da-111">To change the installation target after the input files have been generated</span></span>  
  
-   <span data-ttu-id="cd1da-112">以互動方式執行 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署精靈。</span><span class="sxs-lookup"><span data-stu-id="cd1da-112">Run the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard interactively.</span></span> <span data-ttu-id="cd1da-113">在 [安裝目標]\*\*\*\* 頁面上，指定 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體和資料庫的新目的地。</span><span class="sxs-lookup"><span data-stu-id="cd1da-113">On the **Installation Target** page, specify a new destination for the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance and database.</span></span>  
  
     <span data-ttu-id="cd1da-114">-或-</span><span class="sxs-lookup"><span data-stu-id="cd1da-114">-or-</span></span>  
  
-   <span data-ttu-id="cd1da-115">在命令提示字元下執行 [ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署精靈]，並將精靈設定為以回應檔案模式執行。</span><span class="sxs-lookup"><span data-stu-id="cd1da-115">Run the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard at the command prompt and set the wizard to run in answer file mode.</span></span> <span data-ttu-id="cd1da-116">如需回應檔案模式的詳細資訊，請參閱 [執行 Analysis Services 部署精靈](running-the-analysis-services-deployment-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="cd1da-116">For more information about answer file mode, see [Running the Analysis Services Deployment Wizard](running-the-analysis-services-deployment-wizard.md).</span></span>  
  
     <span data-ttu-id="cd1da-117">-或-</span><span class="sxs-lookup"><span data-stu-id="cd1da-117">-or-</span></span>  
  
-   <span data-ttu-id="cd1da-118">\<*project name*>使用任何文字編輯器來修改 .deploymenttargets 檔案。</span><span class="sxs-lookup"><span data-stu-id="cd1da-118">Modify the \<*project name*>.deploymenttargets file by using any text editor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd1da-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd1da-119">See Also</span></span>  
 <span data-ttu-id="cd1da-120">[指定資料分割和角色部署選項](deployment-script-files-partition-and-role-deployment-options.md) </span><span class="sxs-lookup"><span data-stu-id="cd1da-120">[Specifying Partition and Role Deployment Options](deployment-script-files-partition-and-role-deployment-options.md) </span></span>  
 <span data-ttu-id="cd1da-121">[指定解決方案部署的設定](deployment-script-files-solution-deployment-config-settings.md) </span><span class="sxs-lookup"><span data-stu-id="cd1da-121">[Specifying Configuration Settings for Solution Deployment](deployment-script-files-solution-deployment-config-settings.md) </span></span>  
 [<span data-ttu-id="cd1da-122">指定處理選項</span><span class="sxs-lookup"><span data-stu-id="cd1da-122">Specifying Processing Options</span></span>](deployment-script-files-specifying-processing-options.md)  
  
  
