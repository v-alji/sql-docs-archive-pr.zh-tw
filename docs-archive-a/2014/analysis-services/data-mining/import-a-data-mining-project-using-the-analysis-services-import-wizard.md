---
title: 使用 Analysis Services 匯入嚮導匯入資料採礦專案 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 62bc9fc5-c6ff-4517-b598-d92df76743a2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5b39062cc5bc5401a1746f35e98ea643db2d16c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594272"
---
# <a name="import-a-data-mining-project-using-the-analysis-services-import-wizard"></a><span data-ttu-id="e8319-102">使用 Analysis Services 匯入精靈匯入資料採礦專案</span><span class="sxs-lookup"><span data-stu-id="e8319-102">Import a Data Mining Project using the Analysis Services Import Wizard</span></span>
  <span data-ttu-id="e8319-103">本主題描述如何在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中使用 [從伺服器匯入 (多維度和資料採礦)]\*\*\*\* 範本，從另一部伺服器上的現有資料採礦專案匯入中繼資料來建立新的資料採礦專案。</span><span class="sxs-lookup"><span data-stu-id="e8319-103">This topic describes how to create a new data mining project by importing the metadata from an existing data mining project on another server, using the template, **Import from Server (Multidimensional and Data Mining) Project**, in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="import-data-sources-mining-structures-and-mining-models-from-an-existing-data-mining-project"></a><span data-ttu-id="e8319-104">從現有的資料採礦專案匯入資料來源、採礦結構和採礦模型</span><span class="sxs-lookup"><span data-stu-id="e8319-104">Import data sources, mining structures, and mining models from an existing data mining project</span></span>  
 <span data-ttu-id="e8319-105">當您使用範本時，**從伺服器匯入 (多維度和資料採礦) 專案**，會 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 建立新的資料採礦專案，然後從指定的資料採礦專案複製中繼資料。</span><span class="sxs-lookup"><span data-stu-id="e8319-105">When you use the template, **Import from Server (Multidimensional and Data Mining) Project**, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] creates a new data mining project, and then copies the metadata from the specified data mining project.</span></span> <span data-ttu-id="e8319-106">新的專案所包含的資料來源、資料來源檢視、採礦結構和採礦模型與您匯入的來源 ssASnoversion 資料庫相同。</span><span class="sxs-lookup"><span data-stu-id="e8319-106">The new project contains the same data sources, data source views, mining structures, and mining models as the ssASnoversion database that you imported from.</span></span> <span data-ttu-id="e8319-107">但是，要等到您依照以下所述的內容更新某些屬性及處理物件之後，才能使用專案：</span><span class="sxs-lookup"><span data-stu-id="e8319-107">However, the project cannot be used until you have updated certain properties and processed the objects as described:</span></span>  
  
-   <span data-ttu-id="e8319-108">資料本身不會從來源伺服器複製到新的資料採礦專案-只會匯入資料來源和資料來源視圖的定義。</span><span class="sxs-lookup"><span data-stu-id="e8319-108">The data itself is not copied from the source server to the new data mining project-only the definitions of the data sources and data source views are imported.</span></span> <span data-ttu-id="e8319-109">因此，當您完成匯入程序及建立物件之後，您必須定型採礦結構和相依模型來以資料擴展物件。</span><span class="sxs-lookup"><span data-stu-id="e8319-109">Therefore, after the import process has completed, and the objects have been created, you must populate the objects with data by training the mining structures and dependent models.</span></span> <span data-ttu-id="e8319-110">您可以使用資料採礦設計師中的 **[全部處理]** 命令來定型模型和結構。</span><span class="sxs-lookup"><span data-stu-id="e8319-110">You can use the command **Process All** in Data Mining Designer to train the models and structures.</span></span>  
  
-   <span data-ttu-id="e8319-111">如果您正在匯入之前在舊版 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中所建立的專案，則資料來源可能會使用匯入專案之目標伺服器上所未安裝的提供者。</span><span class="sxs-lookup"><span data-stu-id="e8319-111">If you are importing a project that was created in a previous version of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the data source might use providers that are not installed on the server to which you are importing the project.</span></span> <span data-ttu-id="e8319-112">如果您在處理匯入的採礦結構時遇到錯誤，請以滑鼠右鍵按一下每一個資料來源，然後選取 [開啟設計工具]\*\*\*\* 來編輯連接字串，並檢閱提供者屬性。</span><span class="sxs-lookup"><span data-stu-id="e8319-112">If you encounter errors when processing the imported mining structures, right-click each data source and select **Open Designer** to edit the connection string and review the provider properties.</span></span>  
  
     <span data-ttu-id="e8319-113">此時您也可能需要確認，您用來處理資料採礦物件或查詢資料採礦模型的帳戶擁有資料來源的必要權限。</span><span class="sxs-lookup"><span data-stu-id="e8319-113">At this time, you might also need to verify that the account you are using to process the data mining objects or query data mining models has the necessary permissions on the data source.</span></span>  
  
-   <span data-ttu-id="e8319-114">根據預設，當您匯入專案時，工作空間資料庫會設定為 localhost，或是預設執行個體會在 **中設定為** [預設的目標伺服器] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e8319-114">By default, when you import a project, the workspace database is set to localhost, or whatever default instance is configured as the **Default Target Server** in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="e8319-115">若要設定這個屬性，請從 **[選項]** 功能表選取 **[商業智慧設計師]**，再選取 **[Analysis Services]**，然後選取 **[一般]**。</span><span class="sxs-lookup"><span data-stu-id="e8319-115">To set this property, from the **Options** menu, select **Business Intelligence Designers**, select **Analysis Services**, and then select **General**.</span></span>  
  
     <span data-ttu-id="e8319-116">請注意在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中，可設定另一個單獨的選項來設定 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 表格式模型專案的預設部署伺服器。</span><span class="sxs-lookup"><span data-stu-id="e8319-116">Note that, in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], there is another, separate option that you can set to configure the default deployment server for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tabular model projects.</span></span> <span data-ttu-id="e8319-117">**[預設部署伺服器]** 設定會決定表格式模型專案的預設工作空間資料庫。</span><span class="sxs-lookup"><span data-stu-id="e8319-117">The setting, **Default Deployment Server**, determines the default workspace database for tabular model projects.</span></span> <span data-ttu-id="e8319-118">您不能使用可支援資料採礦專案之表格式模型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e8319-118">You cannot use instances that support tabular models for data mining projects</span></span>  
  
     <span data-ttu-id="e8319-119">如果您無法變更預設部署資料庫來使用在多維度或資料採礦模式中執行的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體，您可以隨時使用 **[專案屬性]** 對話方塊來指定部署資料庫。</span><span class="sxs-lookup"><span data-stu-id="e8319-119">If you cannot change the default deployment database to use an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] running in multidimensional or data mining mode, you can always specify the deployment database by using the **Project Properties** dialog box.</span></span>  
  
#### <a name="to-create-a-new-data-mining-project-by-importing-an-existing-data-mining-project"></a><span data-ttu-id="e8319-120">若要匯入現有的資料採礦專案來建立新的資料採礦專案</span><span class="sxs-lookup"><span data-stu-id="e8319-120">To create a new data mining project by importing an existing data mining project</span></span>  
  
1.  <span data-ttu-id="e8319-121">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]的 **[檔案]** 功能表上，按一下 **[新增]**，然後再按一下 **[專案]**。</span><span class="sxs-lookup"><span data-stu-id="e8319-121">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], on the **File** menu, click **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="e8319-122">在 [新增專案]\*\*\*\* 對話方塊的 [已安裝的範本]\*\*\*\* 底下，按一下 [商業智慧]\*\*\*\*，再按一下 [Analysis Services]\*\*\*\*，然後按一下 [從伺服器匯入 (多維度和資料採礦)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e8319-122">In the **New Project** dialog box, under **Installed Templates**, click **Business Intelligence**, click **Analysis Services**, and then click **Import from Server (Multidimensional/Data Mining)**.</span></span>  
  
3.  <span data-ttu-id="e8319-123">在 **[名稱]** 中，輸入專案的名稱，並指定位置和方案名稱，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e8319-123">For **Name**, type a name for the project, then specify a location and solution name, and then click **OK**.</span></span>  
  
     <span data-ttu-id="e8319-124">**[匯入 Analysis Services 資料庫精靈]** 隨即啟動。</span><span class="sxs-lookup"><span data-stu-id="e8319-124">The **Import Analysis Services Database wizard** starts.</span></span> <span data-ttu-id="e8319-125">在歡迎頁面上按一下 [確定]，繼續進行。</span><span class="sxs-lookup"><span data-stu-id="e8319-125">Click OK on the Welcome page to proceed.</span></span>  
  
4.  <span data-ttu-id="e8319-126">在 **[選取來源資料庫]** 頁面上，針對 **[伺服器]** 指定包含您想要匯入之方案的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="e8319-126">On the page, **Select Source Database**, for **Server**, specify the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance that contains the solution you want to import.</span></span>  
  
     <span data-ttu-id="e8319-127">針對 **[資料庫]** 選擇包含您想要匯入之資料採礦物件的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="e8319-127">For **Database**, choose the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database that contains the data mining objects you want to import.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="e8319-128">您不能指定您想要匯入的物件；當您選擇現有的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫時，所有多維度和資料採礦物件都會匯入。</span><span class="sxs-lookup"><span data-stu-id="e8319-128">You cannot specify the objects you want to import; when you choose an existing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, all multidimensional and data mining objects are imported.</span></span>  
  
     <span data-ttu-id="e8319-129">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="e8319-129">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="e8319-130">**[正在完成精靈]** 頁面會顯示匯入作業的進度。</span><span class="sxs-lookup"><span data-stu-id="e8319-130">The page, **Completing the Wizard**, displays the progress of the import operation.</span></span> <span data-ttu-id="e8319-131">您不能取消此作業或是變更正在匯入的物件。</span><span class="sxs-lookup"><span data-stu-id="e8319-131">You cannot cancel the operation or change the objects that are being imported.</span></span> <span data-ttu-id="e8319-132">完成時按一下 **[完成]** 。</span><span class="sxs-lookup"><span data-stu-id="e8319-132">Click **Finish** when done.</span></span>  
  
     <span data-ttu-id="e8319-133">隨即使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]自動開啟新的專案。</span><span class="sxs-lookup"><span data-stu-id="e8319-133">The new project is automatically opened using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8319-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8319-134">See Also</span></span>  
 [<span data-ttu-id="e8319-135">專案屬性 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="e8319-135">Project Properties &#40;SSAS Tabular&#41;</span></span>](../tabular-models/properties-ssas-tabular.md)  
  
  
