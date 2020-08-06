---
title: 移動資料採礦物件 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], models
- data mining editor [Analysis Services]
- mining models [Analysis Services], managing
- Data Mining Designer
- mining models [Analysis Services], modifying
ms.assetid: bc108407-2603-4387-b930-b5bb9df78069
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2b10be3a79487376b173eab87059404b7f7a618e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687369"
---
# <a name="moving-data-mining-objects"></a><span data-ttu-id="5b3b8-102">移動資料採礦物件</span><span class="sxs-lookup"><span data-stu-id="5b3b8-102">Moving Data Mining Objects</span></span>
  <span data-ttu-id="5b3b8-103">移動資料採礦物件的最常見情形是將模型從測試或分析環境部署到實際執行環境，或者與其他使用者共用模型。</span><span class="sxs-lookup"><span data-stu-id="5b3b8-103">The most common scenarios for moving data mining objects are to deploy a model from a testing or analysis environment to a production environment, or to share models with other users.</span></span>  
  
 <span data-ttu-id="5b3b8-104">本主題描述如何使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]提供的工具和指令碼語言來移動資料採礦物件。</span><span class="sxs-lookup"><span data-stu-id="5b3b8-104">This topic describes how you can use the tools and scripting languages provided by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], for moving data mining objects.</span></span>  
  
## <a name="moving-data-mining-objects-between-databases-or-servers"></a><span data-ttu-id="5b3b8-105">在資料庫或伺服器之間移動資料採礦物件</span><span class="sxs-lookup"><span data-stu-id="5b3b8-105">Moving Data Mining Objects between Databases or Servers</span></span>  
 <span data-ttu-id="5b3b8-106">您可以透過以下方法在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫之間或 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體之間移動資料採礦物件：</span><span class="sxs-lookup"><span data-stu-id="5b3b8-106">You can move data mining objects between [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases or between instances of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in the following ways:</span></span>  
  
-   <span data-ttu-id="5b3b8-107">將方案重新部署到至其他資料庫。</span><span class="sxs-lookup"><span data-stu-id="5b3b8-107">Re-deploying the solution to a different database.</span></span>  
  
-   <span data-ttu-id="5b3b8-108">撰寫個別物件的指令碼。</span><span class="sxs-lookup"><span data-stu-id="5b3b8-108">Scripting individual objects.</span></span>  
  
-   <span data-ttu-id="5b3b8-109">備份與還原資料庫副本。</span><span class="sxs-lookup"><span data-stu-id="5b3b8-109">Backing up and then restoring a copy of the database.</span></span>  
  
-   <span data-ttu-id="5b3b8-110">匯出和匯入結構與模型。</span><span class="sxs-lookup"><span data-stu-id="5b3b8-110">Exporting and importing structures and models.</span></span>  
  
 <span data-ttu-id="5b3b8-111">下節詳細說明這些選項。</span><span class="sxs-lookup"><span data-stu-id="5b3b8-111">The following section explains these options in more detail.</span></span>  
  
### <a name="deploying"></a><span data-ttu-id="5b3b8-112">正在部署</span><span class="sxs-lookup"><span data-stu-id="5b3b8-112">Deploying</span></span>  
 <span data-ttu-id="5b3b8-113">需要有使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]建立的方案檔，才能將方案部署至不同的伺服器或資料庫。</span><span class="sxs-lookup"><span data-stu-id="5b3b8-113">Deploying the solution to a different server or database requires that you have the solution file that was created by using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="5b3b8-114">如需部署 Analysis Services 方案的詳細資訊，請參閱[部署 Analysis Services 專案 &#40;SSDT&#41;](../multidimensional-models/deploy-analysis-services-projects-ssdt.md)。</span><span class="sxs-lookup"><span data-stu-id="5b3b8-114">For more information about deploying Analysis Services solutions, see [Deploy Analysis Services Projects &#40;SSDT&#41;](../multidimensional-models/deploy-analysis-services-projects-ssdt.md).</span></span>  
  
### <a name="scripting"></a><span data-ttu-id="5b3b8-115">指令碼</span><span class="sxs-lookup"><span data-stu-id="5b3b8-115">Scripting</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="5b3b8-116">提供了數種語言，可用於編寫物件的指令碼。</span><span class="sxs-lookup"><span data-stu-id="5b3b8-116">provides several languages that you can use to script objects.</span></span>  
  
-   <span data-ttu-id="5b3b8-117">**XMLA**：您可以在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中以滑鼠右鍵按一下物件，使用 XMLA 編寫物件的指令碼。</span><span class="sxs-lookup"><span data-stu-id="5b3b8-117">**XMLA**: You can script objects using XMLA by right-clicking objects in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="5b3b8-118">若要執行指令碼，請在目標伺服器上的 [XMLA 查詢]\*\*\*\* 視窗中開啟指令碼。</span><span class="sxs-lookup"><span data-stu-id="5b3b8-118">To execute the script, open it in an **XMLA Query** window on the target server.</span></span>  
  
-   <span data-ttu-id="5b3b8-119">**DMX**：您可以透過使用範本或 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 和 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中提供的其中一個查詢產生器建立指令碼。</span><span class="sxs-lookup"><span data-stu-id="5b3b8-119">**DMX**: You can create scripts by using templates or one of the query builders provided in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] and [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="5b3b8-120">但請注意，各指令碼語言可執行的工作之間有些差異：</span><span class="sxs-lookup"><span data-stu-id="5b3b8-120">Note, however, that there are differences in the tasks that you can perform with each scripting language:</span></span>  
  
-   <span data-ttu-id="5b3b8-121">諸如物件描述和資料繫結等屬性只能透過 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] DDL 語言來建立或變更，無法透過 DMX。</span><span class="sxs-lookup"><span data-stu-id="5b3b8-121">Properties such as the object description and data bindings can only by created or changed by using [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] DDL languages, not by using DMX.</span></span>  
  
-   <span data-ttu-id="5b3b8-122">只有 DMX 支援匯入和匯出採礦物件。</span><span class="sxs-lookup"><span data-stu-id="5b3b8-122">Only DMX supports the import and export of mining objects.</span></span>  
  
-   <span data-ttu-id="5b3b8-123">只有 DMX 支援產生 PMML 或從 PMML 匯入模型定義。</span><span class="sxs-lookup"><span data-stu-id="5b3b8-123">Only DMX supports generating PMML or importing model definitions from PMML.</span></span>  
  
-   <span data-ttu-id="5b3b8-124">只有 DMX 支援使用應用程式資料來定型模型。</span><span class="sxs-lookup"><span data-stu-id="5b3b8-124">Only DMX supports training a model with application data.</span></span> <span data-ttu-id="5b3b8-125">此外，DMX INSERT INTO 陳述式支援在不提供索引鍵資料行值的情況下進行模型定型。</span><span class="sxs-lookup"><span data-stu-id="5b3b8-125">Moreover, the DMX INSERT INTO statement supports training a model without providing values for a key column.</span></span>  
  
 <span data-ttu-id="5b3b8-126">如需詳細資訊，請參閱＜ [使用 Analysis Services 指令碼語言 &#40;ASSL&#41; 開發](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)＞。</span><span class="sxs-lookup"><span data-stu-id="5b3b8-126">For more information, see [Developing with Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).</span></span>  
  
### <a name="backup-and-restore"></a><span data-ttu-id="5b3b8-127">備份與還原</span><span class="sxs-lookup"><span data-stu-id="5b3b8-127">Backup and Restore</span></span>  
 <span data-ttu-id="5b3b8-128">備份和還原整個 Analysis Services 資料庫是絕佳的方法 (如果您的資料採礦方案相依於 OLAP 物件的話)。</span><span class="sxs-lookup"><span data-stu-id="5b3b8-128">Backup and restore of an entire Analysis Services database is the method of choice if your data mining solution relies on OLAP objects.</span></span> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="5b3b8-129">提供備份和還原功能，讓資料庫備份更快速而且更方便。</span><span class="sxs-lookup"><span data-stu-id="5b3b8-129">provides backup and restore functionality that makes database backups faster and easier.</span></span>  
  
 <span data-ttu-id="5b3b8-130">如需備份的詳細資訊，請參閱 [備份與還原 Analysis Services 資料庫](../multidimensional-models/backup-and-restore-of-analysis-services-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="5b3b8-130">For more information about backup, see [Backup and Restore of Analysis Services Databases](../multidimensional-models/backup-and-restore-of-analysis-services-databases.md).</span></span>  
  
### <a name="exporting-and-importing"></a><span data-ttu-id="5b3b8-131">匯出和匯入</span><span class="sxs-lookup"><span data-stu-id="5b3b8-131">Exporting and Importing</span></span>  
 <span data-ttu-id="5b3b8-132">利用 DMX 陳述式匯出採礦模型與結構，然後重新匯入，是移動或備份個別關聯式資料採礦物件最方便的方式。</span><span class="sxs-lookup"><span data-stu-id="5b3b8-132">Exporting and then re-importing mining models and structures by using DMX statements is the easiest way to move or back up individual relational data mining objects.</span></span> <span data-ttu-id="5b3b8-133">如需有關這些作業之 DMX 語法的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="5b3b8-133">For more information about the DMX syntax for these operations, see the following topics:</span></span>  
  
-   [<span data-ttu-id="5b3b8-134">EXPORT &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="5b3b8-134">EXPORT &#40;DMX&#41;</span></span>](/sql/dmx/export-dmx)  
  
-   [<span data-ttu-id="5b3b8-135">IMPORT &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="5b3b8-135">IMPORT &#40;DMX&#41;</span></span>](/sql/dmx/import-dmx)  
  
 <span data-ttu-id="5b3b8-136">如果您指定了 INCLUDE DEPENDENCIES 選項， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 也會匯出任何所需資料來源檢視的定義，而且當您匯入模型或結構時，它將在目標伺服器上重新建立資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="5b3b8-136">If you specify the INCLUDE DEPENDENCIES option, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will also export the definition of any required data source views, and when you import the model or structure, it will re-create the data source view on the target server.</span></span> <span data-ttu-id="5b3b8-137">在您已經完成匯入模型的作業之後，請務必針對此物件設定必要的採礦權限。</span><span class="sxs-lookup"><span data-stu-id="5b3b8-137">After you have finished importing the model, make sure to set the necessary mining permissions on the object.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5b3b8-138">您無法使用 DMX 來匯出和匯入 OLAP 模型。</span><span class="sxs-lookup"><span data-stu-id="5b3b8-138">You cannot export and import OLAP models by using DMX.</span></span> <span data-ttu-id="5b3b8-139">如果採礦模型是以 OLAP Cube 為基礎，您必須使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 所提供的功能來備份和還原整個資料庫，或重新部署 Cube 及其模型。</span><span class="sxs-lookup"><span data-stu-id="5b3b8-139">If your mining model is based on an OLAP cube, you must use the functionality provided by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] for backing up and restoring an entire database, or redeploy the cube and its models.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b3b8-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b3b8-140">See Also</span></span>  
 [<span data-ttu-id="5b3b8-141">資料採礦方案與物件的管理</span><span class="sxs-lookup"><span data-stu-id="5b3b8-141">Management of Data Mining Solutions and Objects</span></span>](management-of-data-mining-solutions-and-objects.md)  
  
  
