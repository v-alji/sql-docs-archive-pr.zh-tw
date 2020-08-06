---
title: 多維度模型資料庫 (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [Analysis Services], databases
- SQL Server Analysis Services, databases
- SSAS, databases
- Analysis Services, databases
- databases [Analysis Services], designing
- Business Intelligence Development Studio, databases [Analysis Services]
- databases [Analysis Services]
ms.assetid: 78b2f22a-b7bd-4a2b-b6fc-0bff4d2b3168
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8dc4e7c872f87244e8353c80bd9acfcce584c167
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596927"
---
# <a name="multidimensional-model-databases-ssas"></a><span data-ttu-id="5e9ac-102">多維度模型資料庫 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="5e9ac-102">Multidimensional Model Databases (SSAS)</span></span>
  <span data-ttu-id="5e9ac-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫是資料來源、資料來源檢視、Cube、維度及角色的集合。</span><span class="sxs-lookup"><span data-stu-id="5e9ac-103">An [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database is a collection of data sources, data source views, cubes, dimensions, and roles.</span></span> <span data-ttu-id="5e9ac-104">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫也可以包含資料採礦結構，以及提供您方法將使用者定義函數加入至資料庫的自訂組件。</span><span class="sxs-lookup"><span data-stu-id="5e9ac-104">Optionally, an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database can include structures for data mining, and custom assemblies that provide a way for you to add user-defined functions to the database.</span></span>  
  
 <span data-ttu-id="5e9ac-105">Cube 是 Analysis Services 的基本查詢物件。</span><span class="sxs-lookup"><span data-stu-id="5e9ac-105">Cubes are the fundamental query objects in Analysis Services.</span></span> <span data-ttu-id="5e9ac-106">當您透過用戶端應用程式連接至 Analysis Services 資料庫時，您可以連接至該資料庫內的 Cube。</span><span class="sxs-lookup"><span data-stu-id="5e9ac-106">When you connect to an Analysis Services database via a client application, you connect to a cube within that database.</span></span> <span data-ttu-id="5e9ac-107">如果跨多個內容重複使用維度、組件、角色或採礦結構，資料庫可能包含多個 Cube。</span><span class="sxs-lookup"><span data-stu-id="5e9ac-107">A database might contain multiple cubes if you are reusing dimensions, assemblies, roles, or mining structures across multiple contexts.</span></span>  
  
 <span data-ttu-id="5e9ac-108">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 您可以程式設計方式或透過下列其中一個互動方法，建立及修改  資料庫：</span><span class="sxs-lookup"><span data-stu-id="5e9ac-108">You can create and modify a [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database programmatically or by using one of these interactive methods:</span></span>  
  
-   <span data-ttu-id="5e9ac-109">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 從 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 將 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]專案部署到指定的  執行個體。</span><span class="sxs-lookup"><span data-stu-id="5e9ac-109">Deploy an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project from [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to a designated instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="5e9ac-110">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 這個程序會建立  資料庫 (如果該執行個體中尚未存在這個名稱的資料庫)，並將新建之資料庫內的已設計物件具現化。</span><span class="sxs-lookup"><span data-stu-id="5e9ac-110">This process creates an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, if a database with that name does not already exist within that instance, and instantiates the designed objects within the newly created database.</span></span> <span data-ttu-id="5e9ac-111">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫時，對於 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案中物件所做的變更必須要在專案部署到  執行個體之後，才會生效。</span><span class="sxs-lookup"><span data-stu-id="5e9ac-111">When working with an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], changes made to objects in the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project take effect only when the project is deployed to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
-   <span data-ttu-id="5e9ac-112">請使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 或 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]於 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 執行個體內建立空的 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]資料庫，然後使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 直接連接到該資料庫，並在其中建立物件 (而不是在專案內建立)。</span><span class="sxs-lookup"><span data-stu-id="5e9ac-112">Create an empty [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database within an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], by using either [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], and then connect directly to that database using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and create objects within it (rather than within a project).</span></span> <span data-ttu-id="5e9ac-113">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 當以這個方式使用  資料庫時，對物件所做的變更會在儲存已變更的物件之後，於您所連接的這個資料庫中生效。</span><span class="sxs-lookup"><span data-stu-id="5e9ac-113">When working with an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database in this manner, changes made to objects take effect in the database to which you are connecting when the changed object is saved.</span></span>  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="5e9ac-114">會使用與原始檔控制軟體的整合，以支援多位開發人員同時在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案中使用不同的物件。</span><span class="sxs-lookup"><span data-stu-id="5e9ac-114">uses integration with source control software to support multiple developers working with different objects within an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project at the same time.</span></span> <span data-ttu-id="5e9ac-115">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 開發人員也可以直接與 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫互動，而不用透過 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案，但是這樣做會有一個風險，就是 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫中的物件可能不會與用於部署的  專案同步。</span><span class="sxs-lookup"><span data-stu-id="5e9ac-115">A developer can also interact with an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database directly, rather than through an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, but the risk of this is that the objects in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database can become out of sync with the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project that was used for its deployment.</span></span> <span data-ttu-id="5e9ac-116">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 在部署之後，您會使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]來管理  資料庫。</span><span class="sxs-lookup"><span data-stu-id="5e9ac-116">After deployment, you administer an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="5e9ac-117">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 您也可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]來對 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫進行某些變更 (如資料分割和角色的變更)，而這樣也會使得 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫中的物件不會與用於部署的  專案同步。</span><span class="sxs-lookup"><span data-stu-id="5e9ac-117">Certain changes can also be made to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], such as to partitions and roles, which can also cause the objects in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database to become out of sync with the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project that was used for its deployment.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="5e9ac-118">相關工作</span><span class="sxs-lookup"><span data-stu-id="5e9ac-118">Related Tasks</span></span>  
 [<span data-ttu-id="5e9ac-119">附加和卸離 Analysis Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="5e9ac-119">Attach and Detach Analysis Services Databases</span></span>](attach-and-detach-analysis-services-databases.md)  
  
 [<span data-ttu-id="5e9ac-120">備份與還原 Analysis Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="5e9ac-120">Backup and Restore of Analysis Services Databases</span></span>](backup-and-restore-of-analysis-services-databases.md)  
  
 [<span data-ttu-id="5e9ac-121">記錄和編寫 Analysis Services 資料庫的指令碼</span><span class="sxs-lookup"><span data-stu-id="5e9ac-121">Document and Script an Analysis Services Database</span></span>](document-and-script-an-analysis-services-database.md)  
  
 [<span data-ttu-id="5e9ac-122">修改或刪除 Analysis Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="5e9ac-122">Modify or Delete an Analysis Services Database</span></span>](modify-or-delete-an-analysis-services-database.md)  
  
 [<span data-ttu-id="5e9ac-123">移動 Analysis Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="5e9ac-123">Move an Analysis Services Database</span></span>](move-an-analysis-services-database.md)  
  
 [<span data-ttu-id="5e9ac-124">重新命名多維度資料庫 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="5e9ac-124">Rename a Multidimensional Database &#40;Analysis Services&#41;</span></span>](rename-a-multidimensional-database-analysis-services.md)  
  
 [<span data-ttu-id="5e9ac-125">將多維度資料庫的相容性層級設定 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="5e9ac-125">Set the Compatibility Level of a Multidimensional Database &#40;Analysis Services&#41;</span></span>](compatibility-level-of-a-multidimensional-database-analysis-services.md)  
  
 [<span data-ttu-id="5e9ac-126">設定多維度資料庫屬性 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="5e9ac-126">Set Multidimensional Database Properties &#40;Analysis Services&#41;</span></span>](set-multidimensional-database-properties-analysis-services.md)  
  
 [<span data-ttu-id="5e9ac-127">同步處理 Analysis Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="5e9ac-127">Synchronize Analysis Services Databases</span></span>](synchronize-analysis-services-databases.md)  
  
 [<span data-ttu-id="5e9ac-128">在 ReadOnly 和 ReadWrite 模式之間切換 Analysis Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="5e9ac-128">Switch an Analysis Services database between ReadOnly and ReadWrite modes</span></span>](switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
## <a name="see-also"></a><span data-ttu-id="5e9ac-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e9ac-129">See Also</span></span>  
 <span data-ttu-id="5e9ac-130">[以線上模式連接到 Analysis Services 資料庫](connect-in-online-mode-to-an-analysis-services-database.md) </span><span class="sxs-lookup"><span data-stu-id="5e9ac-130">[Connect in Online Mode to an Analysis Services Database](connect-in-online-mode-to-an-analysis-services-database.md) </span></span>  
 <span data-ttu-id="5e9ac-131">[建立 Analysis Services 專案 &#40;SSDT&#41;](create-an-analysis-services-project-ssdt.md) </span><span class="sxs-lookup"><span data-stu-id="5e9ac-131">[Create an Analysis Services Project &#40;SSDT&#41;](create-an-analysis-services-project-ssdt.md) </span></span>  
 [<span data-ttu-id="5e9ac-132">使用 MDX 查詢多維度資料</span><span class="sxs-lookup"><span data-stu-id="5e9ac-132">Querying Multidimensional Data with MDX</span></span>](mdx/querying-multidimensional-data-with-mdx.md)  
  
  
