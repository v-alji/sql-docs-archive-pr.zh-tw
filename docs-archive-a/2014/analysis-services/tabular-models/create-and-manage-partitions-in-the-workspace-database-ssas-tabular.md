---
title: 在 (SSAS 表格式) 的工作空間資料庫中建立及管理資料分割 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.partitionmgr.f1
ms.assetid: 0b3027d6-652b-4eb3-a197-58b25df65218
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3824dd4763e516dc5e8e34a9ec815d3969f4eb79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594210"
---
# <a name="create-and-manage-partitions-in-the-workspace-database-ssas-tabular"></a><span data-ttu-id="a78f7-102">在工作空間資料庫中建立及管理資料分割 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="a78f7-102">Create and Manage Partitions in the Workspace Database (SSAS Tabular)</span></span>
  <span data-ttu-id="a78f7-103">分割區會將一個資料表分割成多個邏輯部分。</span><span class="sxs-lookup"><span data-stu-id="a78f7-103">Partitions divide a table into logical parts.</span></span> <span data-ttu-id="a78f7-104">每個資料分割可以不受其他資料分割的影響，單獨處理 (重新整理) 或平行處理。</span><span class="sxs-lookup"><span data-stu-id="a78f7-104">Each partition can then be processed (Refreshed) independently or in parallel with other partitions.</span></span> <span data-ttu-id="a78f7-105">資料分割可以改善大型資料庫的可調適性和管理能力。</span><span class="sxs-lookup"><span data-stu-id="a78f7-105">Partitions can improve scalability and manageability of large databases.</span></span> <span data-ttu-id="a78f7-106">依預設，每個資料表都包含一個資料分割，其中包含所有資料行。</span><span class="sxs-lookup"><span data-stu-id="a78f7-106">By default, each table has one partition that includes all columns.</span></span> <span data-ttu-id="a78f7-107">本主題中的工作描述如何使用中的 [資料**分割管理員**] 對話方塊，建立及管理模型工作空間資料庫中的資料分割[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a78f7-107">Tasks in this topic describe how to create and manage partitions in the model workspace database by using the **Partition Manager** dialog box in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]</span></span>  
  
 <span data-ttu-id="a78f7-108">將模型部署至其他 Analysis Services 執行個體之後，資料庫管理員即可使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]來建立及管理 (已部署) 模型中的資料分割。</span><span class="sxs-lookup"><span data-stu-id="a78f7-108">After a model has been deployed to another Analysis Services instance, database administrators can create and manage partitions in the (deployed) model by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="a78f7-109">如需詳細資訊，請參閱[建立及管理表格式模型資料分割 &#40;SSAS 表格式&#41;](partitions-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="a78f7-109">For more information, see [Create and Manage Tabular Model Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="a78f7-110">本主題也包括下列工作：</span><span class="sxs-lookup"><span data-stu-id="a78f7-110">This topic includes the following tasks:</span></span>  
  
-   [<span data-ttu-id="a78f7-111">建立新的資料分割</span><span class="sxs-lookup"><span data-stu-id="a78f7-111">To create a new partition</span></span>](#bkmk_create_new)  
  
-   [<span data-ttu-id="a78f7-112">複製資料分割</span><span class="sxs-lookup"><span data-stu-id="a78f7-112">To copy a partition</span></span>](#bkmk_copy)  
  
-   [<span data-ttu-id="a78f7-113">若要刪除資料分割</span><span class="sxs-lookup"><span data-stu-id="a78f7-113">To delete a partition</span></span>](#bkmk_delete)  
  
> [!NOTE]  
>  <span data-ttu-id="a78f7-114">您不能使用 [資料分割管理員] 對話方塊，來合併模型工作空間資料庫中的資料分割。</span><span class="sxs-lookup"><span data-stu-id="a78f7-114">You cannot merge partitions in the model workspace database by using the Partition Manager dialog box.</span></span> <span data-ttu-id="a78f7-115">資料分割只能透過使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]，在已部署的模型中合併。</span><span class="sxs-lookup"><span data-stu-id="a78f7-115">Partitions can be merged in a deployed model only by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="a78f7-116">工作</span><span class="sxs-lookup"><span data-stu-id="a78f7-116">Tasks</span></span>  
 <span data-ttu-id="a78f7-117">若要建立和管理資料分割，您要使用 **[資料分割管理員]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a78f7-117">To create and manage partitions, you will use the **Partitions Manager** dialog box.</span></span> <span data-ttu-id="a78f7-118">若要檢視 **[資料分割管理員]** 對話方塊，請在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中，按一下 **[資料表]** 功能表，然後按一下 **[資料分割]**。</span><span class="sxs-lookup"><span data-stu-id="a78f7-118">To view the **Partitions Manager** dialog box, in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Table** menu, and then click **Partitions**.</span></span>  
  
###  <a name="to-create-a-new-partition"></a><a name="bkmk_create_new"></a><span data-ttu-id="a78f7-119">若要建立新的磁碟分割</span><span class="sxs-lookup"><span data-stu-id="a78f7-119">To create a new partition</span></span>  
  
1.  <span data-ttu-id="a78f7-120">在模型設計師中，選取您要定義資料分割的資料表。</span><span class="sxs-lookup"><span data-stu-id="a78f7-120">In the model designer, select the table for which you want to define a partition.</span></span>  
  
2.  <span data-ttu-id="a78f7-121">按一下 **[資料表]** 功能表，然後按一下 **[資料分割]**。</span><span class="sxs-lookup"><span data-stu-id="a78f7-121">Click on the **Table** menu, and then click **Partitions**.</span></span>  
  
3.  <span data-ttu-id="a78f7-122">在 **[資料分割管理員]** 的 **[資料表]** 清單方塊中，確認或選取要資料分割的資料表，然後按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="a78f7-122">In **Partition Manager**, in the **Table** listbox, verify or select the table you want to partition, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="a78f7-123">在 **[資料分割名稱]** 中，輸入資料分割的名稱。</span><span class="sxs-lookup"><span data-stu-id="a78f7-123">In **Partition Name**, type a name for the partition.</span></span> <span data-ttu-id="a78f7-124">依預設，每個新資料分割的預設資料分割名稱是以累加的方式進行編號。</span><span class="sxs-lookup"><span data-stu-id="a78f7-124">By default, the name of the default partition will be incrementally numbered for each new partition.</span></span>  
  
5.  <span data-ttu-id="a78f7-125">您可使用資料表預覽模式或使用查詢編輯器模式所建立的 SQL 查詢，選取資料分割中要包含的資料列及資料行。</span><span class="sxs-lookup"><span data-stu-id="a78f7-125">You can select the rows and columns to be included in the partition by using Table Preview mode or by using a SQL query created using Query Editor mode.</span></span>  
  
     <span data-ttu-id="a78f7-126">若要使用資料表預覽模式 (預設值)，請按一下預覽視窗右上角附近的 [資料表預覽]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="a78f7-126">To use Table Preview mode (default), click the **Table Preview** button near the upper-right corner of the preview window.</span></span> <span data-ttu-id="a78f7-127">選取資料行名稱旁邊的核取方塊，即可選取要加入資料分割的資料行。</span><span class="sxs-lookup"><span data-stu-id="a78f7-127">Select the columns you want to include in the partition by selecting the checkbox next to the column name.</span></span> <span data-ttu-id="a78f7-128">若要篩選資料列，請以滑鼠右鍵按一下資料格值，然後按一下 **[依選取的資料格值篩選]**。</span><span class="sxs-lookup"><span data-stu-id="a78f7-128">To filter rows, right click a cell value, and click **Filter by Selected Cell Value**.</span></span>  
  
     <span data-ttu-id="a78f7-129">若要使用 SQL 陳述式，請按一下預覽視窗右上角附近的 [查詢編輯器]\*\*\*\* 按鈕，然後將 SQL 查詢陳述式輸入或貼到查詢視窗中。</span><span class="sxs-lookup"><span data-stu-id="a78f7-129">To use a SQL statement, click the **Query Editor** button near the upper-right corner of the preview window, then type or paste a SQL query statement into the query window.</span></span> <span data-ttu-id="a78f7-130">若要驗證您的陳述式，請按一下 **[驗證]**。</span><span class="sxs-lookup"><span data-stu-id="a78f7-130">To validate your statement, click **Validate**.</span></span> <span data-ttu-id="a78f7-131">若要使用查詢設計工具，請按一下 **[設計]**。</span><span class="sxs-lookup"><span data-stu-id="a78f7-131">To use the Query Designer, click **Design**.</span></span>  
  
###  <a name="to-copy-a-partition"></a><a name="bkmk_copy"></a> <span data-ttu-id="a78f7-132">複製資料分割</span><span class="sxs-lookup"><span data-stu-id="a78f7-132">To copy a partition</span></span>  
  
1.  <span data-ttu-id="a78f7-133">在 **[資料分割管理員]** 的 **[資料表]** 清單方塊中，確認或選取含有要複製之資料分割的資料表。</span><span class="sxs-lookup"><span data-stu-id="a78f7-133">In **Partition Manager**, in the **Table** listbox, verify or select the table that contains the partition you want to copy.</span></span>  
  
2.  <span data-ttu-id="a78f7-134">在 **[資料分割]** 清單中，選取要複製的資料分割，然後按一下 **[複製]**。</span><span class="sxs-lookup"><span data-stu-id="a78f7-134">In the **Partitions** list, select the partition you want to copy and then click **Copy**.</span></span>  
  
3.  <span data-ttu-id="a78f7-135">在 **[資料分割名稱]** 中，輸入資料分割的新名稱。</span><span class="sxs-lookup"><span data-stu-id="a78f7-135">In **Partition Name**, type a new name for the partition.</span></span>  
  
###  <a name="to-delete-a-partition"></a><a name="bkmk_delete"></a><span data-ttu-id="a78f7-136">若要刪除資料分割</span><span class="sxs-lookup"><span data-stu-id="a78f7-136">To delete a partition</span></span>  
  
1.  <span data-ttu-id="a78f7-137">在 **[資料分割管理員]** 的 **[資料表]** 清單方塊中，確認或選取含有要刪除之資料分割的資料表。</span><span class="sxs-lookup"><span data-stu-id="a78f7-137">In **Partition Manager**, in the **Table** listbox, verify or select the table that contains the partition you want to delete.</span></span>  
  
2.  <span data-ttu-id="a78f7-138">在 **[資料分割]** 清單中，選取要刪除的資料分割，然後按一下 **[刪除]**。</span><span class="sxs-lookup"><span data-stu-id="a78f7-138">In the **Partitions** list, select the partition you want to delete and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a78f7-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a78f7-139">See Also</span></span>  
 <span data-ttu-id="a78f7-140">[SSAS 表格式 &#40;的資料分割&#41;](partitions-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="a78f7-140">[Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="a78f7-141">在工作空間資料庫中處理資料分割 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="a78f7-141">Process Partitions in the Workspace Database &#40;SSAS Tabular&#41;</span></span>](process-partitions-in-the-workspace-database-ssas-tabular.md)  
  
  
