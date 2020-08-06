---
title: 重建索引工作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rebuildindextask.f1
helpviewer_keywords:
- rebuilding indexes
- indexes [Integration Services]
- Rebuild Index task
ms.assetid: 021884dd-e72d-47b2-99e8-b741410509c3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 33bbe25bc8c47f4f749f95dbb7096c3a76c25297
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597261"
---
# <a name="rebuild-index-task"></a><span data-ttu-id="a87b6-102">重建索引工作</span><span class="sxs-lookup"><span data-stu-id="a87b6-102">Rebuild Index Task</span></span>
  <span data-ttu-id="a87b6-103">「重建索引」工作會重建 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫資料表與檢視中的索引。</span><span class="sxs-lookup"><span data-stu-id="a87b6-103">The Rebuild Index task rebuilds indexes in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database tables and views.</span></span> <span data-ttu-id="a87b6-104">如需管理索引的詳細資訊，請參閱 [重新組織與重建索引](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="a87b6-104">For more information about managing indexes, see [Reorganize and Rebuild Indexes](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).</span></span>  
  
 <span data-ttu-id="a87b6-105">藉由使用「重建索引」工作，封裝可重建單一資料庫或多重資料庫中的索引。</span><span class="sxs-lookup"><span data-stu-id="a87b6-105">By using the Rebuild Index task, a package can rebuild indexes in a single database or multiple databases.</span></span> <span data-ttu-id="a87b6-106">如果此工作只重建單一資料庫中的索引，您可以選擇要由此工作重建索引的檢視與資料表。</span><span class="sxs-lookup"><span data-stu-id="a87b6-106">If the task rebuilds only the indexes in a single database, you can choose the views and tables whose indexes the task rebuilds.</span></span>  
  
 <span data-ttu-id="a87b6-107">此工作使用下列索引重建選項封裝 ALTER INDEX REBUILD 陳述式：</span><span class="sxs-lookup"><span data-stu-id="a87b6-107">This task encapsulates an ALTER INDEX REBUILD statement with the following index rebuild options:</span></span>  
  
-   <span data-ttu-id="a87b6-108">指定 FILLFACTOR 百分比或使用原始 FILLFACTOR 數量。</span><span class="sxs-lookup"><span data-stu-id="a87b6-108">Specify a FILLFACTOR percentage or use the original FILLFACTOR amount.</span></span>  
  
-   <span data-ttu-id="a87b6-109">設定 PAD_INDEX = ON，將 FILLFACTOR 所指定的可用空間配置給中級索引分頁。</span><span class="sxs-lookup"><span data-stu-id="a87b6-109">Set PAD_INDEX = ON to allocate the free space specified by FILLFACTOR to the intermediate-level pages of the index.</span></span>  
  
-   <span data-ttu-id="a87b6-110">設定 SORT_IN_TEMPDB = ON，將用來重建索引的中繼排序結果儲存在 tempdb 中。</span><span class="sxs-lookup"><span data-stu-id="a87b6-110">Set SORT_IN_TEMPDB = ON to store the intermediate sort result used to rebuild the index in tempdb.</span></span> <span data-ttu-id="a87b6-111">當中繼排序結果設為 OFF 時，結果會與索引儲存在相同資料庫中。</span><span class="sxs-lookup"><span data-stu-id="a87b6-111">When the intermediate sort result is set to OFF, the result is stored in the same database as the index.</span></span>  
  
-   <span data-ttu-id="a87b6-112">設定 IGNORE_DUP_KEY = ON，允許包含違反唯一條件約束之記錄的多資料列插入作業，以插入不違反唯一條件約束的記錄。</span><span class="sxs-lookup"><span data-stu-id="a87b6-112">Set IGNORE_DUP_KEY = ON to allow a multirow insert operation that includes records that violate unique constraints to insert the records that do not violate the unique constraints.</span></span>  
  
-   <span data-ttu-id="a87b6-113">設定 ONLINE = ON，不要持有資料表鎖定，以便對基礎資料表的查詢或更新可在重建索引期間繼續進行。</span><span class="sxs-lookup"><span data-stu-id="a87b6-113">Set ONLINE = ON to not hold table locks so that queries or updates to the underlying table can proceed during re-indexing.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a87b6-114">[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的所有版本都無法使用線上索引作業。</span><span class="sxs-lookup"><span data-stu-id="a87b6-114">Online index operations are not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a87b6-115">如需版本支援的功能清單 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[SQL Server 2014 版本支援的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="a87b6-115">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="a87b6-116">如需 ALTER INDEX 陳述式和索引重建選項的詳細資訊，請參閱 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a87b6-116">For more information about the ALTER INDEX statement and index rebuild options, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a87b6-117">此工作用於建立工作執行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式之時間，與工作重建的索引數目成正比。</span><span class="sxs-lookup"><span data-stu-id="a87b6-117">The time the task takes to create the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that the task runs is proportionate to the number of indexes the task rebuilds.</span></span> <span data-ttu-id="a87b6-118">如果此工作設定成重建含有大量索引的資料庫內所有資料表與檢視中的索引，或是重建多重資料庫中的索引，則此工作可能會花費相當多的時間產生 Transact-SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="a87b6-118">If the task is configured to rebuild indexes in all the tables and views in a database with a large number of indexes, or to rebuild indexes in multiple databases, the task can take a considerable amount of time to generate the Transact-SQL statement.</span></span>  
  
## <a name="configuration-of-the-rebuild-index-task"></a><span data-ttu-id="a87b6-119">設定重建索引工作</span><span class="sxs-lookup"><span data-stu-id="a87b6-119">Configuration of the Rebuild Index Task</span></span>  
 <span data-ttu-id="a87b6-120">您可以透過 [ [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師] 設定屬性。</span><span class="sxs-lookup"><span data-stu-id="a87b6-120">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="a87b6-121">這項工作位於「 **設計師」中** [工具箱] **的** [維護計畫工作] [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 區段。</span><span class="sxs-lookup"><span data-stu-id="a87b6-121">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="a87b6-122">如需有關可在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師中設定之屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="a87b6-122">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
 [<span data-ttu-id="a87b6-123">重建索引工作 &#40;維護計畫&#41;</span><span class="sxs-lookup"><span data-stu-id="a87b6-123">Rebuild Index Task &#40;Maintenance Plan&#41;</span></span>](../../relational-databases/maintenance-plans/rebuild-index-task-maintenance-plan.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="a87b6-124">相關工作</span><span class="sxs-lookup"><span data-stu-id="a87b6-124">Related Tasks</span></span>  
 <span data-ttu-id="a87b6-125">如需如何在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計工具中設定這些屬性的詳細資訊，請參閱 [Set the Properties of a Task or Container](../set-the-properties-of-a-task-or-container.md)(設定工作或容器的屬性)。</span><span class="sxs-lookup"><span data-stu-id="a87b6-125">For more about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, see [Set the Properties of a Task or Container](../set-the-properties-of-a-task-or-container.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a87b6-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a87b6-126">See Also</span></span>  
 <span data-ttu-id="a87b6-127">[Integration Services 工作](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="a87b6-127">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="a87b6-128">控制流程</span><span class="sxs-lookup"><span data-stu-id="a87b6-128">Control Flow</span></span>](control-flow.md)  
  
  
