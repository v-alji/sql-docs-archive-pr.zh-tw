---
title: 建立 Analysis Services 專案 (基本資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 784c0401-0358-4117-9c85-4e8220ce71d9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 83eb808bc7d18ebe715d309d9f911c010ee172d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585719"
---
# <a name="creating-an-analysis-services-project-basic-data-mining-tutorial"></a><span data-ttu-id="eaf26-102">建立 Analysis Services 專案 (基本資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="eaf26-102">Creating an Analysis Services Project (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="eaf26-103">每個 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 專案都會在單一資料庫中定義物件 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="eaf26-103">Each [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project defines the objects in a single [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="eaf26-104">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫可包含許多不同類型的物件</span><span class="sxs-lookup"><span data-stu-id="eaf26-104">An [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database can contains many different types of objects</span></span>  
  
-   <span data-ttu-id="eaf26-105">多維度模型 (Cube)</span><span class="sxs-lookup"><span data-stu-id="eaf26-105">Multidimensional models (cubes)</span></span>  
  
-   <span data-ttu-id="eaf26-106">採礦結構和採礦模型</span><span class="sxs-lookup"><span data-stu-id="eaf26-106">Mining structures and mining models</span></span>  
  
-   <span data-ttu-id="eaf26-107">提供支援的物件，例如資料來源、資料來源檢視和自訂組件</span><span class="sxs-lookup"><span data-stu-id="eaf26-107">Supporting objects such as data sources, data source views, and custom assemblies</span></span>  
  
 <span data-ttu-id="eaf26-108">請注意，您 **不需要** Cube 便能進行資料採礦。</span><span class="sxs-lookup"><span data-stu-id="eaf26-108">Note that you **do not** require a cube to do data mining.</span></span> <span data-ttu-id="eaf26-109">如果您必須對現有的 Cube 進行資料採礦，就應該將資料採礦模型加入至您用來建立 Cube 的相同專案。</span><span class="sxs-lookup"><span data-stu-id="eaf26-109">If you need to perform data mining on an existing cube, you should add the data mining models to the same project you used to build the cube.</span></span> <span data-ttu-id="eaf26-110">不過，大多數的用途情況下您都能根據關聯式資料來源 (例如資料倉儲) 建立模型，只要不涉及 Cube 即可有更好的效能。</span><span class="sxs-lookup"><span data-stu-id="eaf26-110">However, for most purposes you can build your models on relational data sources, such as a data warehouse, and get better performance if a cube is not involved.</span></span>  
  
 <span data-ttu-id="eaf26-111">在本教學課程中，您將使用關聯式資料倉儲 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]做為資料來源。</span><span class="sxs-lookup"><span data-stu-id="eaf26-111">In this tutorial you will use a relational data warehouse, [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)], as the data source.</span></span> <span data-ttu-id="eaf26-112">您會將所有的資料採礦物件部署到名稱為 `BasicDataMining` 的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫，僅供用於資料採礦。</span><span class="sxs-lookup"><span data-stu-id="eaf26-112">You will deploy all your data mining objects to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database named `BasicDataMining`, used just for data mining.</span></span>  
  
 <span data-ttu-id="eaf26-113">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 預設會針對新專案使用 **localhost** 執行個體。</span><span class="sxs-lookup"><span data-stu-id="eaf26-113">By default, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] uses the **localhost** instance for new projects.</span></span> <span data-ttu-id="eaf26-114">如果您要使用具名執行個體或不同的伺服器，您必須先建立並開啟專案，然後變更執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="eaf26-114">If you are using a named instance or a different server, you must first create and open the project and then change the instance name.</span></span>  
  
 <span data-ttu-id="eaf26-115">如需專案的詳細資訊 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，請參閱[建立 Analysis Services 專案](../analysis-services/lesson-1-1-creating-an-analysis-services-project.md)。</span><span class="sxs-lookup"><span data-stu-id="eaf26-115">For more information about [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] projects, see [Creating an Analysis Services Project](../analysis-services/lesson-1-1-creating-an-analysis-services-project.md).</span></span>  
  
### <a name="to-create-an-analysis-services-project"></a><span data-ttu-id="eaf26-116">若要建立 Analysis Services 專案</span><span class="sxs-lookup"><span data-stu-id="eaf26-116">To create an Analysis Services project</span></span>  
  
1.  <span data-ttu-id="eaf26-117">開啟 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="eaf26-117">Open [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="eaf26-118">在 **[檔案]** 功能表上，指向 **[開新檔案]**，再選取 **[專案]**。</span><span class="sxs-lookup"><span data-stu-id="eaf26-118">On the **File** menu, point to **New**, and then select **Project**.</span></span>  
  
3.  <span data-ttu-id="eaf26-119">確認 **[專案類型]** 窗格中已選取 **[商業智慧專案]** 。</span><span class="sxs-lookup"><span data-stu-id="eaf26-119">Verify that **Business Intelligence Projects** is selected in the **Project types** pane.</span></span>  
  
4.  <span data-ttu-id="eaf26-120">在 **[範本]** 窗格中，選取 **[Analysis Services 多維度和資料採礦專案]**。</span><span class="sxs-lookup"><span data-stu-id="eaf26-120">In the **Templates** pane, select **Analysis Services Multidimensional and Data Mining Project**.</span></span>  
  
5.  <span data-ttu-id="eaf26-121">在 [**名稱**] 方塊中，將新專案命名為 `BasicDataMining` 。</span><span class="sxs-lookup"><span data-stu-id="eaf26-121">In the **Name** box, name the new project `BasicDataMining`.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-change-the-instance-where-data-mining-objects-are-stored"></a><span data-ttu-id="eaf26-122">變更儲存資料採礦物件所在的執行個體</span><span class="sxs-lookup"><span data-stu-id="eaf26-122">To change the instance where data mining objects are stored</span></span>  
  
1.  <span data-ttu-id="eaf26-123">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中的 **[專案]** 功能表上，選取 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="eaf26-123">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], on the **Project** menu, select **Properties**.</span></span>  
  
2.  <span data-ttu-id="eaf26-124">在 **[屬性頁]** 窗格左邊的 **[組態屬性]** 底下，按一下 **[部署]**。</span><span class="sxs-lookup"><span data-stu-id="eaf26-124">On the left side of the **Property Pages** pane, under **Configuration Properties**, click **Deployment**.</span></span>  
  
3.  <span data-ttu-id="eaf26-125">在 **[屬性頁]** 窗格右邊的 **[目標]** 底下，確認 **[伺服器]** 名稱是 **localhost**。</span><span class="sxs-lookup"><span data-stu-id="eaf26-125">On the right side of the **Property Pages** pane, under **Target**, verify that the **Server** name is **localhost**.</span></span> <span data-ttu-id="eaf26-126">如果您要使用不同的執行個體，請輸入執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="eaf26-126">If you are using a different instance, type the name of the instance.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="eaf26-127">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="eaf26-127">Next Task in Lesson</span></span>  
 [<span data-ttu-id="eaf26-128">建立資料來源 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="eaf26-128">Creating a Data Source &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-data-source-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="eaf26-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eaf26-129">See Also</span></span>  
 <span data-ttu-id="eaf26-130">[組建 Analysis Services 專案 &#40;SSDT&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/build-analysis-services-projects-ssdt) </span><span class="sxs-lookup"><span data-stu-id="eaf26-130">[Build Analysis Services Projects &#40;SSDT&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/build-analysis-services-projects-ssdt) </span></span>  
 [<span data-ttu-id="eaf26-131">建立 Analysis Services 專案 &#40;SSDT&#41;</span><span class="sxs-lookup"><span data-stu-id="eaf26-131">Create an Analysis Services Project &#40;SSDT&#41;</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt)  
  
  
