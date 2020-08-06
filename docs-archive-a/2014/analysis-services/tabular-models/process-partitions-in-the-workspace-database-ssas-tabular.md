---
title: 在工作空間資料庫中處理資料分割 (SSAS 表格式) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 3a369705-43fa-4961-9045-32e06fbdde33
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4a996e90b30794882535327ea3192d7e72818422
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687186"
---
# <a name="process-partitions-in-the-workspace-database-ssas-tabular"></a><span data-ttu-id="8fcb5-102">在工作空間資料庫中處理資料分割 (SSAS 表格式) </span><span class="sxs-lookup"><span data-stu-id="8fcb5-102">Process Partitions in the Workspace Database (SSAS Tabular)</span></span>
  <span data-ttu-id="8fcb5-103">分割區會將一個資料表分割成多個邏輯部分。</span><span class="sxs-lookup"><span data-stu-id="8fcb5-103">Partitions divide a table into logical parts.</span></span> <span data-ttu-id="8fcb5-104">接著，每個分割區可以不受其他分割區的影響，單獨處理 (重新整理)。</span><span class="sxs-lookup"><span data-stu-id="8fcb5-104">Each partition can then be processed (Refreshed) independent of other partitions.</span></span> <span data-ttu-id="8fcb5-105">本主題中的工作說明如何使用 **中的** [處理資料分割] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]對話方塊，處理模型工作空間資料庫中的資料分割。</span><span class="sxs-lookup"><span data-stu-id="8fcb5-105">The tasks in this topic describe how to process partitions in the model workspace database by using the **Process Partitions** dialog box in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="8fcb5-106">將模型部署至其他 Analysis Services 執行個體之後，資料庫管理員即可使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、指令碼或 IS 封裝，建立及管理 (已部署) 模型中的資料分割。</span><span class="sxs-lookup"><span data-stu-id="8fcb5-106">After a model has been deployed to another Analysis Services instance, database administrators can create and manage partitions in the (deployed) model by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], by script, or by using an IS package.</span></span> <span data-ttu-id="8fcb5-107">如需詳細資訊，請參閱[建立及管理表格式模型資料分割 &#40;SSAS 表格式&#41;](partitions-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="8fcb5-107">For more information, see [Create and Manage Tabular Model Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md).</span></span>  
  
###  <a name="to-process-a-partition"></a><a name="bkmk_create_new"></a> <span data-ttu-id="8fcb5-108">處理資料分割</span><span class="sxs-lookup"><span data-stu-id="8fcb5-108">To process a partition</span></span>  
  
1.  <span data-ttu-id="8fcb5-109">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 中，依序按一下 [模型]\*\*\*\* 功能表、[處理]\*\*\*\* (重新整理) 及 [處理資料分割]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8fcb5-109">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Model** menu, and then click **Process** (Refresh), and then click **Process Partitions**.</span></span>  
  
2.  <span data-ttu-id="8fcb5-110">在 **[模式]** 清單方塊，選取下列其中一個處理模式：</span><span class="sxs-lookup"><span data-stu-id="8fcb5-110">In the **Mode** listbox, select one of the following process modes:</span></span>  
  
    |<span data-ttu-id="8fcb5-111">[模式]</span><span class="sxs-lookup"><span data-stu-id="8fcb5-111">Mode</span></span>|<span data-ttu-id="8fcb5-112">描述</span><span class="sxs-lookup"><span data-stu-id="8fcb5-112">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="8fcb5-113">**處理預設**</span><span class="sxs-lookup"><span data-stu-id="8fcb5-113">**Process Default**</span></span>|<span data-ttu-id="8fcb5-114">偵測資料分割物件的處理狀態，並且執行必要的處理，以便將尚未處理或部分處理的資料分割物件傳遞為完整處理的狀態。</span><span class="sxs-lookup"><span data-stu-id="8fcb5-114">Detects the process state of a partition object, and performs processing necessary to deliver unprocessed or partially processed partition objects to a fully processed state.</span></span> <span data-ttu-id="8fcb5-115">載入空白資料表和資料分割的資料；建立或重新建立階層、導出資料行及關聯性。</span><span class="sxs-lookup"><span data-stu-id="8fcb5-115">Data for empty tables and partitions is loaded; hierarchies, calculated columns, and relationships are built or rebuilt.</span></span>|  
    |<span data-ttu-id="8fcb5-116">**完整處理**</span><span class="sxs-lookup"><span data-stu-id="8fcb5-116">**Process Full**</span></span>|<span data-ttu-id="8fcb5-117">處理資料分割物件及其包含的所有物件。</span><span class="sxs-lookup"><span data-stu-id="8fcb5-117">Processes a partition object and all the objects that it contains.</span></span> <span data-ttu-id="8fcb5-118">對已處理過的物件執行完整處理時， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會先卸除該物件中的所有資料，然後再處理該物件。</span><span class="sxs-lookup"><span data-stu-id="8fcb5-118">When Process Full is run for an object that has already been processed, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] drops all data in the object, and then processes the object.</span></span> <span data-ttu-id="8fcb5-119">當物件已進行過任何結構性變更時，就需要這種處理。</span><span class="sxs-lookup"><span data-stu-id="8fcb5-119">This kind of processing is required when a structural change has been made to an object.</span></span>|  
    |<span data-ttu-id="8fcb5-120">**處理資料**</span><span class="sxs-lookup"><span data-stu-id="8fcb5-120">**Process Data**</span></span>|<span data-ttu-id="8fcb5-121">將資料載入資料分割或資料表，而不重新建立階層或關聯性，或重新計算導出資料行和量值。</span><span class="sxs-lookup"><span data-stu-id="8fcb5-121">Load data into a partition or a table without rebuilding hierarchies or relationships or recalculating calculated columns and measures.</span></span>|  
    |<span data-ttu-id="8fcb5-122">**處理清除**</span><span class="sxs-lookup"><span data-stu-id="8fcb5-122">**Process Clear**</span></span>|<span data-ttu-id="8fcb5-123">移除資料分割中的所有資料。</span><span class="sxs-lookup"><span data-stu-id="8fcb5-123">Removes all data from a partition.</span></span>|  
    |<span data-ttu-id="8fcb5-124">**處理加入**</span><span class="sxs-lookup"><span data-stu-id="8fcb5-124">**Process Add**</span></span>|<span data-ttu-id="8fcb5-125">以新資料累加地更新資料分割。</span><span class="sxs-lookup"><span data-stu-id="8fcb5-125">Incrementally update partition with new data.</span></span>|  
  
3.  <span data-ttu-id="8fcb5-126">在 **[處理]** 核取方塊資料行中，選取您想透過選取的模式處理的資料分割，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="8fcb5-126">In the **Process** checkbox column, select the partitions you want to process with the selected mode, and then click **Ok**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fcb5-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8fcb5-127">See Also</span></span>  
 <span data-ttu-id="8fcb5-128">[SSAS 表格式 &#40;的資料分割&#41;](partitions-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="8fcb5-128">[Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="8fcb5-129">在工作空間資料庫中建立及管理資料分割 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="8fcb5-129">Create and Manage Partitions in the Workspace Database &#40;SSAS Tabular&#41;</span></span>](workspace-database-ssas-tabular.md)  
  
  
