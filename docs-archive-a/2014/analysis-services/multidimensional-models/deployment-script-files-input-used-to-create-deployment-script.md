---
title: 瞭解用來建立部署腳本的輸入檔 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- input files [Analysis Services]
- Analysis Services Deployment Wizard, scripts
- deploying [Analysis Services], input files
- Analysis Services Deployment Wizard, input files
- scripts [Analysis Services], deployment
- Analysis Services deployments, input files
- modifying input files
ms.assetid: 20e080cd-6a0e-4591-b022-ea4cd3638e36
author: minewiskan
ms.author: owend
ms.openlocfilehash: 34695993d4f153c6c0b97fef744d92c682517c99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596380"
---
# <a name="understanding-the-input-files-used-to-create-the-deployment-script"></a><span data-ttu-id="08e10-102">了解用來建立部署指令碼的輸入檔</span><span class="sxs-lookup"><span data-stu-id="08e10-102">Understanding the Input Files Used to Create the Deployment Script</span></span>
  <span data-ttu-id="08e10-103">當您建立 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案時，會 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 為專案產生 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="08e10-103">When you build a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] generates XML files for the project.</span></span> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="08e10-104">會將這些 XML 檔案放置在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案的輸出資料夾中。</span><span class="sxs-lookup"><span data-stu-id="08e10-104">puts these XML files in the Output folder of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="08e10-105">依預設，輸出是放在 \Bin 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="08e10-105">By default output is out in the \Bin folder.</span></span> <span data-ttu-id="08e10-106">下表列出 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 建立的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="08e10-106">The following table lists the XML files that [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] creates.</span></span>  
  
|<span data-ttu-id="08e10-107">XMLA 檔案</span><span class="sxs-lookup"><span data-stu-id="08e10-107">XMLA file</span></span>|<span data-ttu-id="08e10-108">描述</span><span class="sxs-lookup"><span data-stu-id="08e10-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="08e10-109">\<*project name*>. .asdatabase</span><span class="sxs-lookup"><span data-stu-id="08e10-109">\<*project name*>.asdatabase</span></span>|<span data-ttu-id="08e10-110">包含專案中所有 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 物件的宣告式定義。</span><span class="sxs-lookup"><span data-stu-id="08e10-110">Contains the declarative definitions for all the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects in the project.</span></span>|  
|<span data-ttu-id="08e10-111">\<*project name*>. .deploymenttargets</span><span class="sxs-lookup"><span data-stu-id="08e10-111">\<*project name*>.deploymenttargets</span></span>|<span data-ttu-id="08e10-112">包含將建立 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 物件的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體和資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="08e10-112">Contains the name of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance and database in which the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects will be created.</span></span>|  
|<span data-ttu-id="08e10-113">\<*project name*>. .configsettings</span><span class="sxs-lookup"><span data-stu-id="08e10-113">\<*project name*>.configsettings</span></span>|<span data-ttu-id="08e10-114">包含環境特定設定，例如資料來源連接資訊和物件儲存位置。</span><span class="sxs-lookup"><span data-stu-id="08e10-114">Contains environment specific settings, such as data source connection information and object storage locations.</span></span> <span data-ttu-id="08e10-115">此檔案中的設定會覆寫 .asdatabase 檔案中的設定 \<*project name*> 。</span><span class="sxs-lookup"><span data-stu-id="08e10-115">Settings in this file override settings in the \<*project name*>.asdatabase file.</span></span>|  
|<span data-ttu-id="08e10-116">\<*project name*>. d</span><span class="sxs-lookup"><span data-stu-id="08e10-116">\<*project name*>.deploymentoptions</span></span>|<span data-ttu-id="08e10-117">包含部署選項，例如部署是否為交易式，以及部署之後是否應處理部署的物件。</span><span class="sxs-lookup"><span data-stu-id="08e10-117">Contains deployment options, such as whether deployment is transactional and whether deployed objects should be processed after deployment.</span></span>|  
  
> [!NOTE]  
>  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="08e10-118">絕不會將密碼儲存在專案檔中。</span><span class="sxs-lookup"><span data-stu-id="08e10-118">never stores passwords in its project files.</span></span>  
  
## <a name="modifying-the-input-files"></a><span data-ttu-id="08e10-119">修改輸入檔</span><span class="sxs-lookup"><span data-stu-id="08e10-119">Modifying the Input Files</span></span>  
 <span data-ttu-id="08e10-120">修改輸入檔中的值，或從輸入檔中抓取的值，可讓您變更部署目的地、設定設定和部署選項，而不需要編輯整個 (.asdatabase 檔案，而是 \<*project name*> 從現有的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫) 產生腳本。</span><span class="sxs-lookup"><span data-stu-id="08e10-120">Modifying the values in the input files, or the values retrieved from the input files, makes it possible to change the deployment destination, the configuration settings, and deployment options without editing the whole \<*project name*>.asdatabase file (or a whole XMLA script file if you generate a script from an existing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database).</span></span> <span data-ttu-id="08e10-121">您可以修改個別的檔案，以輕鬆地針對各種用途建立不同的部署指令碼。</span><span class="sxs-lookup"><span data-stu-id="08e10-121">Being able to modify individual files lets you easily create different deployment scripts for different purposes.</span></span>  
  
 <span data-ttu-id="08e10-122">下列主題說明如何修改各種輸入檔中的值：</span><span class="sxs-lookup"><span data-stu-id="08e10-122">The following topics explain how to modify values in the various input files:</span></span>  
  
-   [<span data-ttu-id="08e10-123">指定安裝目標</span><span class="sxs-lookup"><span data-stu-id="08e10-123">Specifying the Installation Target</span></span>](deployment-script-files-specifying-the-installation-target.md)  
  
-   [<span data-ttu-id="08e10-124">指定資料分割和角色部署選項</span><span class="sxs-lookup"><span data-stu-id="08e10-124">Specifying Partition and Role Deployment Options</span></span>](deployment-script-files-partition-and-role-deployment-options.md)  
  
-   [<span data-ttu-id="08e10-125">指定方案部署的組態設定</span><span class="sxs-lookup"><span data-stu-id="08e10-125">Specifying Configuration Settings for Solution Deployment</span></span>](deployment-script-files-solution-deployment-config-settings.md)  
  
-   [<span data-ttu-id="08e10-126">指定處理選項</span><span class="sxs-lookup"><span data-stu-id="08e10-126">Specifying Processing Options</span></span>](deployment-script-files-specifying-processing-options.md)  
  
## <a name="see-also"></a><span data-ttu-id="08e10-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08e10-127">See Also</span></span>  
 <span data-ttu-id="08e10-128">[執行 Analysis Services 部署嚮導](running-the-analysis-services-deployment-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="08e10-128">[Running the Analysis Services Deployment Wizard](running-the-analysis-services-deployment-wizard.md) </span></span>  
 [<span data-ttu-id="08e10-129">了解 Analysis Services 部署指令碼</span><span class="sxs-lookup"><span data-stu-id="08e10-129">Understanding the Analysis Services Deployment Script</span></span>](understanding-the-analysis-services-deployment-script.md)  
  
  
