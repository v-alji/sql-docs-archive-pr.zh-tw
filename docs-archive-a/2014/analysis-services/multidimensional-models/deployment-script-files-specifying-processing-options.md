---
title: 指定處理選項 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services deployments, processing options
- input files [Analysis Services]
- deploying [Analysis Services], processing options
- modifying processing options
- Analysis Services Deployment Wizard, processing options
ms.assetid: e9e50817-908e-4210-bc3d-8e2957568241
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9690aaa7e1d3b3870eb6ab01630b98027263655f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687285"
---
# <a name="specifying-processing-options"></a><span data-ttu-id="09eb6-102">指定處理選項</span><span class="sxs-lookup"><span data-stu-id="09eb6-102">Specifying Processing Options</span></span>
  <span data-ttu-id="09eb6-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]部署嚮導會從 d 檔案讀取處理選項 \<*project name*> 。</span><span class="sxs-lookup"><span data-stu-id="09eb6-103">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard reads the processing options from the \<*project name*>.deploymentoptions file.</span></span> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="09eb6-104">當您建立專案時，會建立這個檔案 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="09eb6-104">creates this file when you build the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="09eb6-105">使用 [ **Deployment** *\<project name>* **屬性頁**] 對話方塊之 [部署] 頁面上指定的處理選項來建立 \<*project name*> d 檔案。</span><span class="sxs-lookup"><span data-stu-id="09eb6-105">uses the processing options specified on the **Deployment** page of *\<project name>* **Properties Pages** dialog box to create the \<*project name*>.deploymentoptions file.</span></span>  
  
## <a name="reviewing-the-processing-options-for-deployment"></a><span data-ttu-id="09eb6-106">檢閱部署的處理選項</span><span class="sxs-lookup"><span data-stu-id="09eb6-106">Reviewing the Processing Options for Deployment</span></span>  
 <span data-ttu-id="09eb6-107">儲存在 d 檔案中的設定會如下所示 \<*project name*> ：</span><span class="sxs-lookup"><span data-stu-id="09eb6-107">The configuration settings stored within the \<*project name*>.deploymentoptions file are as follows:</span></span>  
  
-   <span data-ttu-id="09eb6-108">**處理方法** 此設定控制部署之後是否處理部署的物件，以及將要執行的處理類型。</span><span class="sxs-lookup"><span data-stu-id="09eb6-108">**Processing Method** This setting controls whether the deployed objects are processed after deployment and the type of processing that will be performed.</span></span> <span data-ttu-id="09eb6-109">有三個處理選項：</span><span class="sxs-lookup"><span data-stu-id="09eb6-109">There are three processing options:</span></span>  
  
    -   <span data-ttu-id="09eb6-110">預設的處理 (預設值)</span><span class="sxs-lookup"><span data-stu-id="09eb6-110">Default processing (default)</span></span>  
  
    -   <span data-ttu-id="09eb6-111">完整的處理</span><span class="sxs-lookup"><span data-stu-id="09eb6-111">Full processing</span></span>  
  
    -   <span data-ttu-id="09eb6-112">無</span><span class="sxs-lookup"><span data-stu-id="09eb6-112">None</span></span>  
  
-   <span data-ttu-id="09eb6-113">**回寫資料表選項** 如果 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案中已啟用回寫，則此設定會定義如何處理回寫。</span><span class="sxs-lookup"><span data-stu-id="09eb6-113">**Writeback Table Options** If writeback is enabled in the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, this setting defines how writeback is handled.</span></span> <span data-ttu-id="09eb6-114">有三個回寫資料表選項：</span><span class="sxs-lookup"><span data-stu-id="09eb6-114">There are three writeback table options:</span></span>  
  
    -   <span data-ttu-id="09eb6-115">依預設，如果有回寫資料表，就會使用回寫資料表。</span><span class="sxs-lookup"><span data-stu-id="09eb6-115">By default, if a writeback table exists, it will be used.</span></span> <span data-ttu-id="09eb6-116">如果沒有回寫資料表，則會建立新的回寫資料表。</span><span class="sxs-lookup"><span data-stu-id="09eb6-116">If a writeback table does not exist, a new writeback table will be created.</span></span>  
  
    -   <span data-ttu-id="09eb6-117">如果已經存在回寫資料表，則部署會失敗。</span><span class="sxs-lookup"><span data-stu-id="09eb6-117">If a writeback table already exists, the deployment fails.</span></span> <span data-ttu-id="09eb6-118">如果沒有回寫資料表，則會建立新的回寫資料表。</span><span class="sxs-lookup"><span data-stu-id="09eb6-118">If a writeback table does not exist, a new writeback table will be created.</span></span>  
  
    -   <span data-ttu-id="09eb6-119">無論是否已存在回寫資料表，都會建立新的回寫資料表。</span><span class="sxs-lookup"><span data-stu-id="09eb6-119">Regardless of whether a writeback table already exists, a new writeback table will be created.</span></span> <span data-ttu-id="09eb6-120">在此情況下，[ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署精靈] 將刪除任何現有的資料表，並以新的回寫資料表取代。</span><span class="sxs-lookup"><span data-stu-id="09eb6-120">In this case, the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard will delete any existing table and replace it with a new writeback table.</span></span>  
  
-   <span data-ttu-id="09eb6-121">**交易式部署** 此設定控制中繼資料變更與處理命令的部署是發生於單一交易或個別交易中。</span><span class="sxs-lookup"><span data-stu-id="09eb6-121">**Transactional Deployment** This setting controls whether the deployment of metadata changes and process commands occurs in a single transaction or in separate transactions.</span></span>  
  
    -   <span data-ttu-id="09eb6-122">如果此選項為 `True` (預設值)，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 就會在單一交易中部署所有的中繼資料變更與所有的處理命令。</span><span class="sxs-lookup"><span data-stu-id="09eb6-122">If this option is `True` (default), [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] deploys all metadata changes and all process commands within a single transaction.</span></span>  
  
    -   <span data-ttu-id="09eb6-123">如果此選項為 `False`，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 就會在單一交易中部署中繼資料變更，並在個別的交易中部署每個處理命令。</span><span class="sxs-lookup"><span data-stu-id="09eb6-123">If this option is `False`, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] deploys the metadata changes in a single transaction, and deploys each processing command in its own transaction.</span></span>  
  
## <a name="modifying-the-processing-options-for-deployment"></a><span data-ttu-id="09eb6-124">修改部署的處理選項</span><span class="sxs-lookup"><span data-stu-id="09eb6-124">Modifying the Processing Options for Deployment</span></span>  
 <span data-ttu-id="09eb6-125">不過，您可能需要 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 使用不同于 d 檔案中儲存的處理選項，來部署專案 \<*project name*> 。</span><span class="sxs-lookup"><span data-stu-id="09eb6-125">However, you may need to deploy the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project using different processing options than those stored in the \<*project name*>.deploymentoptions file.</span></span> <span data-ttu-id="09eb6-126">例如，您可能需要完整地處理所有的物件、或使用預設處理選項處理、或不進行處理。</span><span class="sxs-lookup"><span data-stu-id="09eb6-126">For example, you may want to have all objects fully processed, or processed using the default processing option, or have no processing occur.</span></span> <span data-ttu-id="09eb6-127">如果 Cube 或維度是可寫入的，您可以指定使用新的或現有的回寫資料表。</span><span class="sxs-lookup"><span data-stu-id="09eb6-127">If the cubes or dimensions are write-enabled, you can specify whether a new or existing writeback table be used.</span></span>  
  
 <span data-ttu-id="09eb6-128">若要修改部署期間使用的處理選項，您可以編輯並重建專案，或使用下列程序描述的方法之一，變更輸入檔中的處理選項。</span><span class="sxs-lookup"><span data-stu-id="09eb6-128">To modify the processing options used during deployment, you can either edit and rebuild the project, or change the processing options in the input file by using one of the methods as described in the following procedure.</span></span>  
  
#### <a name="to-change-processing-options-after-the-input-files-have-been-generated"></a><span data-ttu-id="09eb6-129">若要在已產生輸入檔之後，變更處理選項</span><span class="sxs-lookup"><span data-stu-id="09eb6-129">To change processing options after the input files have been generated</span></span>  
  
-   <span data-ttu-id="09eb6-130">以互動方式執行 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署精靈。</span><span class="sxs-lookup"><span data-stu-id="09eb6-130">Run the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard interactively.</span></span> <span data-ttu-id="09eb6-131">在 [處理選項]\*\*\*\* 頁面上，指定正在部署之專案的處理選項。</span><span class="sxs-lookup"><span data-stu-id="09eb6-131">On the **Processing Options** page, specify the processing options for the project being deployed.</span></span>  
  
     <span data-ttu-id="09eb6-132">-或-</span><span class="sxs-lookup"><span data-stu-id="09eb6-132">-or-</span></span>  
  
-   <span data-ttu-id="09eb6-133">在命令提示字元下執行 [ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署精靈]，並將精靈設定為以回應檔案模式執行。</span><span class="sxs-lookup"><span data-stu-id="09eb6-133">Run the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard at the command prompt and set the wizard to run in answer file mode.</span></span> <span data-ttu-id="09eb6-134">如需回應檔案模式的詳細資訊，請參閱 [執行 Analysis Services 部署精靈](running-the-analysis-services-deployment-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="09eb6-134">For more information about answer file mode, see [Running the Analysis Services Deployment Wizard](running-the-analysis-services-deployment-wizard.md).</span></span>  
  
     <span data-ttu-id="09eb6-135">-或-</span><span class="sxs-lookup"><span data-stu-id="09eb6-135">-or-</span></span>  
  
-   <span data-ttu-id="09eb6-136">\<*project name*>使用任何文字編輯器來修改 d 檔案。</span><span class="sxs-lookup"><span data-stu-id="09eb6-136">Modify the \<*project name*>.deploymentoptions file by using any text editor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09eb6-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09eb6-137">See Also</span></span>  
 <span data-ttu-id="09eb6-138">[指定安裝目標](deployment-script-files-specifying-the-installation-target.md) </span><span class="sxs-lookup"><span data-stu-id="09eb6-138">[Specifying the Installation Target](deployment-script-files-specifying-the-installation-target.md) </span></span>  
 <span data-ttu-id="09eb6-139">[指定資料分割和角色部署選項](deployment-script-files-partition-and-role-deployment-options.md) </span><span class="sxs-lookup"><span data-stu-id="09eb6-139">[Specifying Partition and Role Deployment Options](deployment-script-files-partition-and-role-deployment-options.md) </span></span>  
 [<span data-ttu-id="09eb6-140">指定方案部署的組態設定</span><span class="sxs-lookup"><span data-stu-id="09eb6-140">Specifying Configuration Settings for Solution Deployment</span></span>](deployment-script-files-solution-deployment-config-settings.md)  
  
  
