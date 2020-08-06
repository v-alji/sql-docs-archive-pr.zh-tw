---
title: 從 SQL Server Data Tools (SSAS 表格式) 部署 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.deploystatus.f1
ms.assetid: 67dde3fe-ba43-41f3-b56c-c656029ee93f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8bc8008e7c79e1652b54b21e6afb116301d1700b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596921"
---
# <a name="deploy-from-sql-server-data-tools-ssas-tabular"></a><span data-ttu-id="030d2-102">從 SQL Server Data Tools 部署 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="030d2-102">Deploy From SQL Server Data Tools (SSAS Tabular)</span></span>
  <span data-ttu-id="030d2-103">使用本主題的工作，透過 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中的 [部署] 命令來部署表格式模型方案。</span><span class="sxs-lookup"><span data-stu-id="030d2-103">Use the tasks in this topic to deploy a tabular model solution by using the Deploy command in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="030d2-104">本主題的章節：</span><span class="sxs-lookup"><span data-stu-id="030d2-104">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="030d2-105">設定部署選項與部署伺服器屬性</span><span class="sxs-lookup"><span data-stu-id="030d2-105">Configure Deployment Options and Deployment Server Properties</span></span>](#bkmk_deploy)  
  
-   [<span data-ttu-id="030d2-106">部署表格式模型方案</span><span class="sxs-lookup"><span data-stu-id="030d2-106">Deploy a Tabular Model Solution</span></span>](#bkmk_deploy_proc)  
  
-   [<span data-ttu-id="030d2-107">部署狀態</span><span class="sxs-lookup"><span data-stu-id="030d2-107">Deploy Status</span></span>](#bkmk_deploy_status)  
  
##  <a name="configure-deployment-options-and-deployment-server-properties"></a><a name="bkmk_deploy"></a><span data-ttu-id="030d2-108">設定部署選項與部署伺服器屬性</span><span class="sxs-lookup"><span data-stu-id="030d2-108">Configure Deployment Options and Deployment Server Properties</span></span>  
 <span data-ttu-id="030d2-109">在您部署表格式模型方案之前，必須先指定 [部署選項] 與 [部署伺服器] 屬性。</span><span class="sxs-lookup"><span data-stu-id="030d2-109">Before you deploy your tabular model solution, you must first specify the Deployment Options and Deployment Server properties.</span></span> <span data-ttu-id="030d2-110">如需部署屬性和設定的詳細資訊，請參閱 [表格式模型方案部署 &#40;SSAS 表格式&#41;](tabular-model-solution-deployment-ssas-tabular.md)中的 [部署] 命令來部署表格式模型方案。</span><span class="sxs-lookup"><span data-stu-id="030d2-110">For more information about deployment properties and settings, see [Tabular Model Solution Deployment &#40;SSAS Tabular&#41;](tabular-model-solution-deployment-ssas-tabular.md).</span></span>  
  
#### <a name="to-configure-deployment-options-and-deployment-server-properties"></a><span data-ttu-id="030d2-111">若要設定部署選項與部署伺服器屬性</span><span class="sxs-lookup"><span data-stu-id="030d2-111">To configure Deployment Options and Deployment Server properties</span></span>  
  
1.  <span data-ttu-id="030d2-112">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 的方案總管\*\*\*\* 中，以滑鼠右鍵按一下專案名稱，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="030d2-112">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], in **Solution Explorer**, right-click the project name, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="030d2-113">在 [ \*\* \<project name> 屬性**] 對話方塊的 [**部署選項\*\*] 中，指定屬性設定（如果不同于預設設定）。</span><span class="sxs-lookup"><span data-stu-id="030d2-113">In the **\<project name> Properties** dialog, in **Deployment Options**, specify property settings if different from the default settings.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="030d2-114">快取模式之模型的 [查詢模式]\*\*\*\* 一律是 [記憶體內部]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="030d2-114">For models in cached mode, **Query Mode** is always **In-Memory**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="030d2-115">您無法在 DirectQuery 模式下指定模型的 [模擬設定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="030d2-115">You cannot specify **Impersonation Settings** for models in DirectQuery mode.</span></span>  
  
3.  <span data-ttu-id="030d2-116">在 [部署伺服器]\*\*\*\* 中，指定 [伺服器]\*\*\*\* (名稱)、[版本]\*\*\*\*、[資料庫]\*\*\*\* (名稱) 及 [Cube 名稱]\*\*\*\* 屬性設定 (如果與預設設定不同)，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="030d2-116">In **Deployment Server**, specify the **Server** (name), **Edition**, **Database** (name), and **Cube Name** property settings, if different from the default settings, and then click **OK**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="030d2-117">您也可以指定 [預設部署伺服器] 屬性設定，自動將您建立的任何新專案部署至指定的伺服器。</span><span class="sxs-lookup"><span data-stu-id="030d2-117">You can also specify the Default Deployment Server property setting so any new projects you create will automatically be deployed to the specified server.</span></span> <span data-ttu-id="030d2-118">如需詳細資訊，請參閱 [設定預設的資料模型和部署屬性 &#40;SSAS 表格式&#41;](properties-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="030d2-118">For more information, see [Configure Default Data Modeling and Deployment Properties &#40;SSAS Tabular&#41;](properties-ssas-tabular.md).</span></span>  
  
##  <a name="deploy-a-tabular-model-solution"></a><a name="bkmk_deploy_proc"></a><span data-ttu-id="030d2-119">部署表格式模型方案</span><span class="sxs-lookup"><span data-stu-id="030d2-119">Deploy a Tabular Model Solution</span></span>  
  
#### <a name="to-deploy-a-tabular-model-solution"></a><span data-ttu-id="030d2-120">若要部署表格式模型方案</span><span class="sxs-lookup"><span data-stu-id="030d2-120">To deploy a tabular model solution</span></span>  
  
-   <span data-ttu-id="030d2-121">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 的 [**建立**] 功能表上，按一下 [\*\*部署 \<project name> \*\*]。</span><span class="sxs-lookup"><span data-stu-id="030d2-121">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], on the **Build** menu, click **Deploy \<project name>**.</span></span>  
  
     <span data-ttu-id="030d2-122">[部署]\*\*\*\* 對話方塊將會出現，並指出模型中包含之每個資料表的中繼資料部署與處理狀態 (除非 [處理選項] 屬性設為 [不處理])。</span><span class="sxs-lookup"><span data-stu-id="030d2-122">The **Deploy** dialog box will appear and indicate the status of the metadata deployment and the processing (unless Processing Option property is set to Do Not Process) of each table included in the model.</span></span> <span data-ttu-id="030d2-123">部署程序完成後，請使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 連接至 Analysis Services 執行個體，並確認已建立新的模型資料庫物件，或使用用戶端報表應用程式連接至已部署的模型。</span><span class="sxs-lookup"><span data-stu-id="030d2-123">After the deployment process is complete, use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to connect to the Analysis Services instance and verify the new model database object has been created or use a client reporting application to connect to the deployed model.</span></span>  
  
##  <a name="deploy-status"></a><a name="bkmk_deploy_status"></a><span data-ttu-id="030d2-124">部署狀態</span><span class="sxs-lookup"><span data-stu-id="030d2-124">Deploy Status</span></span>  
 <span data-ttu-id="030d2-125">[部署]\*\*\*\* 對話方塊可讓您監視部署作業的進度。</span><span class="sxs-lookup"><span data-stu-id="030d2-125">The **Deploy** dialog box enables you to monitor the progress of a Deploy operation.</span></span> <span data-ttu-id="030d2-126">您也可以停止部署作業。</span><span class="sxs-lookup"><span data-stu-id="030d2-126">A deploy operation can also be stopped.</span></span>  
  
 <span data-ttu-id="030d2-127">**狀態**</span><span class="sxs-lookup"><span data-stu-id="030d2-127">**Status**</span></span>  
 <span data-ttu-id="030d2-128">指出部署作業是否成功。</span><span class="sxs-lookup"><span data-stu-id="030d2-128">Indicates whether the Deploy operation was successful or not.</span></span>  
  
 <span data-ttu-id="030d2-129">**詳細資料**</span><span class="sxs-lookup"><span data-stu-id="030d2-129">**Details**</span></span>  
 <span data-ttu-id="030d2-130">列出已部署的中繼資料項目、每個中繼資料項目的狀態，並提供每個問題的訊息。</span><span class="sxs-lookup"><span data-stu-id="030d2-130">Lists the metadata items that were deployed, the status for each metadata item, and provides a message of any issues.</span></span>  
  
 <span data-ttu-id="030d2-131">**停止部署**</span><span class="sxs-lookup"><span data-stu-id="030d2-131">**Stop Deploy**</span></span>  
 <span data-ttu-id="030d2-132">按一下可停止部署作業。</span><span class="sxs-lookup"><span data-stu-id="030d2-132">Click to halt the Deploy operation.</span></span> <span data-ttu-id="030d2-133">如果部署作業耗費時間過長，或者如果有太多錯誤，這個選項會很有用。</span><span class="sxs-lookup"><span data-stu-id="030d2-133">This option is useful if the Deploy operation is taking too long, or if there are too many errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="030d2-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="030d2-134">See Also</span></span>  
 <span data-ttu-id="030d2-135">[表格式模型方案部署 &#40;SSAS 表格式&#41;](tabular-model-solution-deployment-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="030d2-135">[Tabular Model Solution Deployment &#40;SSAS Tabular&#41;](tabular-model-solution-deployment-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="030d2-136">設定預設的資料模型和部署屬性 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="030d2-136">Configure Default Data Modeling and Deployment Properties &#40;SSAS Tabular&#41;</span></span>](properties-ssas-tabular.md)  
  
  
