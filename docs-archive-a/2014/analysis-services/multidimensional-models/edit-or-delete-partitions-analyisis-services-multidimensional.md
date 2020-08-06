---
title: 編輯或刪除資料分割 (Analysis Services-多維度) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- modifying partitions
- partitions [Analysis Services], modifying
ms.assetid: fb7a64ca-d021-4926-b92d-83476fbc40a3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1e611ac51ce4a6495225d8e8e7ce05b0c0a83b40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599694"
---
# <a name="edit-or-delete-partitions-analyisis-services---multidimensional"></a><span data-ttu-id="ca494-102">編輯或刪除分割區 (Analysis Services - 多維度)</span><span class="sxs-lookup"><span data-stu-id="ca494-102">Edit or Delete Partitions (Analyisis Services - Multidimensional)</span></span>
  <span data-ttu-id="ca494-103">若要修改 Cube 資料分割，可以在 [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)] 中使用 Cube 設計師的 [資料分割]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ca494-103">Cube partitions are modified using the **Partitions** tab in Cube Designer in [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="ca494-104">[資料分割]\*\*\*\* 索引標籤會列出 Cube 中所有量值群組的資料分割。</span><span class="sxs-lookup"><span data-stu-id="ca494-104">The **Partitions** tab lists the partitions for all of the measure groups in a cube.</span></span> <span data-ttu-id="ca494-105">它也會列出已啟用回寫功能的回寫分割區。</span><span class="sxs-lookup"><span data-stu-id="ca494-105">It also lists the writeback partitions that have writeback enabled.</span></span>

 <span data-ttu-id="ca494-106">若要編輯任何量值群組的資料分割，請在 [資料分割] 索引卷**標上展開**量值群組。量值群組的資料分割會依照資料表格式的序數來列出，並具有下表所列的資料行。</span><span class="sxs-lookup"><span data-stu-id="ca494-106">To edit the partitions for any measure group, expand the measure group on the **Partitions** tab. Partitions for a measure group are listed by ordinal number in a table format with the columns listed in the following table.</span></span>

 <span data-ttu-id="ca494-107">連結量值群組的設定必須在來源 Cube 中編輯。</span><span class="sxs-lookup"><span data-stu-id="ca494-107">Settings for a linked measure group must be edited in the source cube.</span></span>

 <span data-ttu-id="ca494-108">當您將來源分割區合併至目的地分割區中時，會自動刪除分割區。</span><span class="sxs-lookup"><span data-stu-id="ca494-108">Deleting partitions occurs automatically when you merge a source partition into a destination partition.</span></span> <span data-ttu-id="ca494-109">完成合併之後，就會刪除指定做為來源的分割區。</span><span class="sxs-lookup"><span data-stu-id="ca494-109">The partition specified as the Source is deleted after the merge is completed.</span></span> <span data-ttu-id="ca494-110">您也可以在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 中或是 [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)]的 [分割區] 索引標籤中，手動刪除分割區。</span><span class="sxs-lookup"><span data-stu-id="ca494-110">You can also delete partitions manually in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or in the Partitions tab in [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="ca494-111">按一下滑鼠右鍵，再選擇 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ca494-111">Right-click and choose **Delete**.</span></span> <span data-ttu-id="ca494-112">請記住，刪除分割區也會刪除資料和彙總。</span><span class="sxs-lookup"><span data-stu-id="ca494-112">Remember that deleting a partition also deletes data and aggregations.</span></span> <span data-ttu-id="ca494-113">為安全起見，請確定您有資料庫的最新備份，以防您之後需要回復此步驟。</span><span class="sxs-lookup"><span data-stu-id="ca494-113">As a precaution, make sure you have a recent back up of the database in case you need to reverse this step later.</span></span>

> [!NOTE]
>  <span data-ttu-id="ca494-114">或者，您可以使用 XMLA 指令碼，將建立、合併和刪除分割區的工作自動化。</span><span class="sxs-lookup"><span data-stu-id="ca494-114">Alternatively, you can use XMLA scripts that automate tasks for building, merging, and deleting partitions.</span></span> <span data-ttu-id="ca494-115">您可以在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]，或是在以排程工作執行的自訂 SSIS 封裝中，建立和執行 XMLA 指令碼。</span><span class="sxs-lookup"><span data-stu-id="ca494-115">XMLA script can be created and executed in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], or in custom SSIS packages that runs as a scheduled task.</span></span> <span data-ttu-id="ca494-116">如需詳細資訊，請參閱 [使用 SSIS 自動化 Analysis Services 管理工作](../instances/automate-analysis-services-administrative-tasks-with-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="ca494-116">For more information, see [Automate Analysis Services Administrative Tasks with SSIS](../instances/automate-analysis-services-administrative-tasks-with-ssis.md).</span></span>

## <a name="partition-source"></a><span data-ttu-id="ca494-117">分割區來源</span><span class="sxs-lookup"><span data-stu-id="ca494-117">Partition source</span></span>
 <span data-ttu-id="ca494-118">指定分割區的來源資料表或具名查詢。</span><span class="sxs-lookup"><span data-stu-id="ca494-118">Specifies the source table or named query for the partition.</span></span> <span data-ttu-id="ca494-119">若要變更來源資料表，請按一下資料格，然後按一下瀏覽 (**...**) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ca494-119">To change the source table, click the cell and then click the browse (**...**) button.</span></span>

 <span data-ttu-id="ca494-120">![[分割區] 窗格中的來源資料行](../media/ssas-partitionsource.png "[分割區] 窗格中的來源資料行")</span><span class="sxs-lookup"><span data-stu-id="ca494-120">![Source column in Partition pane](../media/ssas-partitionsource.png "Source column in Partition pane")</span></span>

 <span data-ttu-id="ca494-121">如果分割區是以查詢為基礎，請按一下 [瀏覽] (**...**) 按鈕以編輯查詢。</span><span class="sxs-lookup"><span data-stu-id="ca494-121">If the partition is based on a query, click the browse (**...**) button to edit the query.</span></span> <span data-ttu-id="ca494-122">這樣可以編輯分割區的 **Source** 屬性。</span><span class="sxs-lookup"><span data-stu-id="ca494-122">This edits the **Source** property for the partition.</span></span> <span data-ttu-id="ca494-123">如需詳細資訊，請參閱 [變更資料分割來源以使用不同的事實資料表](change-a-partition-source-to-use-a-different-fact-table.md)。</span><span class="sxs-lookup"><span data-stu-id="ca494-123">For more information, see [Change a partition source to use a different fact table](change-a-partition-source-to-use-a-different-fact-table.md).</span></span>

 <span data-ttu-id="ca494-124">您可以在具有與原始來源資料表 (在從其擷取資料的外部資料來源中) 相同結構的資料來源檢視中，指定資料表。</span><span class="sxs-lookup"><span data-stu-id="ca494-124">You can specify a table in the data source view that has the same structure as the original source table (in the external data source from which the data is retrieved).</span></span> <span data-ttu-id="ca494-125">來源可以在 Cube 資料庫的任何資料來源或資料來源檢視中。</span><span class="sxs-lookup"><span data-stu-id="ca494-125">The source can be in any of the data sources or data source views of the cube database.</span></span>

## <a name="storage-settings"></a><span data-ttu-id="ca494-126">儲存體設定</span><span class="sxs-lookup"><span data-stu-id="ca494-126">Storage settings</span></span>
 <span data-ttu-id="ca494-127">您可以在 Cube 設計師的 [資料分割] 索引標籤上，按一下 [儲存設定]\*\*\*\*，針對 MOLAP、ROLAP 或 HOLAP 儲存挑選其中一個標準設定，或針對儲存模式和主動式快取設定自訂設定。</span><span class="sxs-lookup"><span data-stu-id="ca494-127">In Cube Designer, on the Partitions tab, you can click **Storage Settings** to pick one of the standard settings for MOLAP, ROLAP, or HOLAP storage, or to configure custom settings for the storage mode and proactive caching.</span></span> <span data-ttu-id="ca494-128">預設值為 MOLAP，因為它提供最快速的查詢效能。</span><span class="sxs-lookup"><span data-stu-id="ca494-128">The default is MOLAP because it delivers the fastest query performance.</span></span> <span data-ttu-id="ca494-129">如需每個設定的詳細資訊，請參閱[設定磁碟分割儲存體 &#40;Analysis Services - 多維度資料&#41;](set-partition-storage-analysis-services-multidimensional.md)。</span><span class="sxs-lookup"><span data-stu-id="ca494-129">For more information about each setting, see [Set Partition Storage &#40;Analysis Services - Multidimensional&#41;](set-partition-storage-analysis-services-multidimensional.md).</span></span>

 <span data-ttu-id="ca494-130">可以針對 Cube 中之每一個量值群組的每一個分割區進行個別設定儲存。</span><span class="sxs-lookup"><span data-stu-id="ca494-130">Storage can be configured separately for each partition of each measure group in a cube.</span></span> <span data-ttu-id="ca494-131">您也可以針對 Cube 或量值群組進行預設儲存設定。</span><span class="sxs-lookup"><span data-stu-id="ca494-131">You can also configure the default storage settings for a cube or measure group.</span></span> <span data-ttu-id="ca494-132">儲存是在 Cube 精靈的 [資料分割]\*\*\*\* 索引標籤上設定。</span><span class="sxs-lookup"><span data-stu-id="ca494-132">Storage is configured on the **Partitions** tab in the Cube Wizard.</span></span>

## <a name="see-also"></a><span data-ttu-id="ca494-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca494-133">See Also</span></span>
 <span data-ttu-id="ca494-134">[建立和管理本機資料分割 &#40;Analysis Services&#41;](create-and-manage-a-local-partition-analysis-services.md) [設計匯總 &#40;Analysis Services](designing-aggregations-analysis-services-multidimensional.md)&#41;[SSAS-多維度 Analysis Services 中的合併](merge-partitions-in-analysis-services-ssas-multidimensional.md)分割區</span><span class="sxs-lookup"><span data-stu-id="ca494-134">[Create and Manage a Local Partition &#40;Analysis Services&#41;](create-and-manage-a-local-partition-analysis-services.md) [Designing Aggregations &#40;Analysis Services - Multidimensional&#41;](designing-aggregations-analysis-services-multidimensional.md) [Merge Partitions in Analysis Services &#40;SSAS - Multidimensional&#41;](merge-partitions-in-analysis-services-ssas-multidimensional.md)</span></span>


