---
title: 處理 (SSAS 表格式) 的表格式模型資料分割 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6c498d2b-22d6-4661-bc21-2ee708336c8b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 496874707bd4030a98b1794fe7513d1d857390ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687183"
---
# <a name="process-tabular-model-partitions-ssas-tabular"></a><span data-ttu-id="afe81-102">處理表格式模型資料分割 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="afe81-102">Process Tabular Model Partitions (SSAS Tabular)</span></span>
  <span data-ttu-id="afe81-103">分割區會將一個資料表分割成多個邏輯部分。</span><span class="sxs-lookup"><span data-stu-id="afe81-103">Partitions divide a table into logical parts.</span></span> <span data-ttu-id="afe81-104">接著，每個分割區可以不受其他分割區的影響，單獨處理 (重新整理)。</span><span class="sxs-lookup"><span data-stu-id="afe81-104">Each partition can then be processed (Refreshed) independent of other partitions.</span></span> <span data-ttu-id="afe81-105">此主題中的工作描述如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的 [處理資料分割]\*\*\*\* 對話方塊，處理模型資料庫中的資料分割。</span><span class="sxs-lookup"><span data-stu-id="afe81-105">The tasks in this topic describe how to process partitions in a model database by using the **Process Partitions** dialog box in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
###  <a name="to-process-a-partition"></a><a name="bkmk_create_new"></a> <span data-ttu-id="afe81-106">處理資料分割</span><span class="sxs-lookup"><span data-stu-id="afe81-106">To process a partition</span></span>  
  
1.  <span data-ttu-id="afe81-107">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，以滑鼠右鍵按一下含有您要處理之資料分割的資料表，然後按一下 [資料分割]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="afe81-107">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click on the table that has the partitions you want to process, and then click **Partitions**.</span></span>  
  
2.  <span data-ttu-id="afe81-108">在 [資料分割]\*\*\*\* 對話方塊的 [資料分割]\*\*\*\* 中，按一下 [處理] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="afe81-108">In the **Partitions** dialog box, in **Partitions**, click on the Process button.</span></span>  
  
3.  <span data-ttu-id="afe81-109">在 [**處理資料分割 (s) \*\* ] 對話方塊的 [**模式\*\*] 清單方塊中，選取下列其中一個處理模式：</span><span class="sxs-lookup"><span data-stu-id="afe81-109">In the **Process Partition(s)** dialog box, in the **Mode** listbox, select one of the following process modes:</span></span>  
  
    |<span data-ttu-id="afe81-110">[模式]</span><span class="sxs-lookup"><span data-stu-id="afe81-110">Mode</span></span>|<span data-ttu-id="afe81-111">描述</span><span class="sxs-lookup"><span data-stu-id="afe81-111">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="afe81-112">**處理預設**</span><span class="sxs-lookup"><span data-stu-id="afe81-112">**Process Default**</span></span>|<span data-ttu-id="afe81-113">偵測資料分割物件的處理狀態，並且執行必要的處理，以便將尚未處理或部分處理的資料分割物件傳遞為完整處理的狀態。</span><span class="sxs-lookup"><span data-stu-id="afe81-113">Detects the process state of a partition object, and performs processing necessary to deliver unprocessed or partially processed partition objects to a fully processed state.</span></span> <span data-ttu-id="afe81-114">載入空白資料表和資料分割的資料；建立或重新建立階層、導出資料行及關聯性。</span><span class="sxs-lookup"><span data-stu-id="afe81-114">Data for empty tables and partitions is loaded; hierarchies, calculated columns, and relationships are built or rebuilt.</span></span>|  
    |<span data-ttu-id="afe81-115">**完整處理**</span><span class="sxs-lookup"><span data-stu-id="afe81-115">**Process Full**</span></span>|<span data-ttu-id="afe81-116">處理資料分割物件及其包含的所有物件。</span><span class="sxs-lookup"><span data-stu-id="afe81-116">Processes a partition object and all the objects that it contains.</span></span> <span data-ttu-id="afe81-117">對已處理過的物件執行完整處理時， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會先卸除該物件中的所有資料，然後再處理該物件。</span><span class="sxs-lookup"><span data-stu-id="afe81-117">When Process Full is run for an object that has already been processed, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] drops all data in the object, and then processes the object.</span></span> <span data-ttu-id="afe81-118">當物件已進行過任何結構性變更時，就需要這種處理。</span><span class="sxs-lookup"><span data-stu-id="afe81-118">This kind of processing is required when a structural change has been made to an object.</span></span>|  
    |<span data-ttu-id="afe81-119">**處理資料**</span><span class="sxs-lookup"><span data-stu-id="afe81-119">**Process Data**</span></span>|<span data-ttu-id="afe81-120">將資料載入資料分割或資料表，而不重新建立階層或關聯性，或重新計算導出資料行和量值。</span><span class="sxs-lookup"><span data-stu-id="afe81-120">Load data into a partition or a table without rebuilding hierarchies or relationships or recalculating calculated columns and measures.</span></span>|  
    |<span data-ttu-id="afe81-121">**處理清除**</span><span class="sxs-lookup"><span data-stu-id="afe81-121">**Process Clear**</span></span>|<span data-ttu-id="afe81-122">移除資料分割中的所有資料。</span><span class="sxs-lookup"><span data-stu-id="afe81-122">Removes all data from a partition.</span></span>|  
    |<span data-ttu-id="afe81-123">**處理加入**</span><span class="sxs-lookup"><span data-stu-id="afe81-123">**Process Add**</span></span>|<span data-ttu-id="afe81-124">以新資料累加地更新資料分割。</span><span class="sxs-lookup"><span data-stu-id="afe81-124">Incrementally update partition with new data.</span></span>|  
  
4.  <span data-ttu-id="afe81-125">在 **[處理]** 核取方塊資料行中，選取您想透過選取的模式處理的資料分割，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="afe81-125">In the **Process** checkbox column, select the partitions you want to process with the selected mode, and then click **Ok**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afe81-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="afe81-126">See Also</span></span>  
 <span data-ttu-id="afe81-127">[表格式模型資料分割 &#40;SSAS 表格式&#41;](partitions-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="afe81-127">[Tabular Model Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="afe81-128">建立及管理表格式模型資料分割 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="afe81-128">Create and Manage Tabular Model Partitions &#40;SSAS Tabular&#41;</span></span>](create-and-manage-tabular-model-partitions-ssas-tabular.md)  
  
  
