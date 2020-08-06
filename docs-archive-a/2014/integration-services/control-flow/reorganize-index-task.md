---
title: 重新組織索引工作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.reorganizeindextask.f1
helpviewer_keywords:
- reorganizing indexes
- Reorganize Index task [Integration Services]
- indexes [Integration Services]
ms.assetid: 9ed87861-e5c3-4fcd-8760-d112f4c0af0c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3f910391bd3a5a35770bb677bc17c91a00ace457
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597259"
---
# <a name="reorganize-index-task"></a><span data-ttu-id="3813b-102">重新組織索引工作</span><span class="sxs-lookup"><span data-stu-id="3813b-102">Reorganize Index Task</span></span>
  <span data-ttu-id="3813b-103">「重新組織索引」工作會重新組織 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫資料表與檢視中的索引。</span><span class="sxs-lookup"><span data-stu-id="3813b-103">The Reorganize Index task reorganizes indexes in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database tables and views.</span></span> <span data-ttu-id="3813b-104">如需管理索引的詳細資訊，請參閱 [重新組織與重建索引](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="3813b-104">For more information about managing indexes, see [Reorganize and Rebuild Indexes](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).</span></span>  
  
 <span data-ttu-id="3813b-105">藉由使用「重新組織索引」工作，封裝可重新組織單一資料庫或多重資料庫中的索引。</span><span class="sxs-lookup"><span data-stu-id="3813b-105">By using the Reorganize Index task, a package can reorganize indexes in a single database or multiple databases.</span></span> <span data-ttu-id="3813b-106">如果此工作只重新組織單一資料庫中的索引，您可以選擇要由此工作重新組織索引的檢視或資料表。</span><span class="sxs-lookup"><span data-stu-id="3813b-106">If the task reorganizes only the indexes in a single database, you can choose the views or the tables whose indexes the task reorganizes.</span></span> <span data-ttu-id="3813b-107">「重新組織索引」工作亦包含壓縮大型物件資料的選項。</span><span class="sxs-lookup"><span data-stu-id="3813b-107">The Reorganize Index task also includes an option to compact large object data.</span></span> <span data-ttu-id="3813b-108">大型物件資料是指 `image`、`text`、`ntext`、`varchar(max)`、`nvarchar(max)`、`varbinary(max)` 或 `xml` 資料類型的資料。</span><span class="sxs-lookup"><span data-stu-id="3813b-108">Large object data is data with the `image`, `text`, `ntext`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)`, or `xml` data type.</span></span> <span data-ttu-id="3813b-109">如需詳細資訊，請參閱[資料類型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3813b-109">For more information, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
 <span data-ttu-id="3813b-110">「重新組織索引」工作封裝 Transact-SQL ALTER INDEX 陳述式。</span><span class="sxs-lookup"><span data-stu-id="3813b-110">The Reorganize Index task encapsulates the Transact-SQL ALTER INDEX statement.</span></span> <span data-ttu-id="3813b-111">如果您選擇壓縮大型物件資料，陳述式便會使用 REORGANIZE WITH (LOB_COMPACTION = ON) 子句，否則 LOB_COMPACTION 會設為 OFF。</span><span class="sxs-lookup"><span data-stu-id="3813b-111">If you choose to compact large object data, the statement uses the REORGANIZE WITH (LOB_COMPACTION = ON) clause, otherwise LOB_COMPACTION is set to OFF.</span></span> <span data-ttu-id="3813b-112">如需詳細資訊，請參閱 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3813b-112">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3813b-113">此工作用於建立工作執行的 Transact-SQL 陳述式之時間，與工作重新組織的索引數目成正比。</span><span class="sxs-lookup"><span data-stu-id="3813b-113">The time the task takes to create the Transact-SQL statement that the task runs is proportionate to the number of indexes the task reorganizes.</span></span> <span data-ttu-id="3813b-114">如果工作設定成重新組織擁有大量索引的資料庫內所有資料表與檢視中的索引，或是重新組織多重資料庫中的索引，則此工作可能會花費相當多的時間產生 Transact-SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="3813b-114">If the task is configured to reorganize indexes in all the tables and views in a database that holds a large number of indexes, or to reorganize indexes in multiple databases, the task can take a considerable amount of time to generate the Transact-SQL statement.</span></span>  
  
## <a name="configuration-of-the-reorganize-index-task"></a><span data-ttu-id="3813b-115">重新組織索引工作的組態</span><span class="sxs-lookup"><span data-stu-id="3813b-115">Configuration of the Reorganize Index Task</span></span>  
 <span data-ttu-id="3813b-116">您可以透過 [ [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師] 設定屬性。</span><span class="sxs-lookup"><span data-stu-id="3813b-116">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="3813b-117">這項工作位於「 **設計師」中** [工具箱] **的** [維護計畫工作] [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 區段。</span><span class="sxs-lookup"><span data-stu-id="3813b-117">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="3813b-118">如需有關可在「 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師」中設定之屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="3813b-118">For information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="3813b-119">重新組織索引工作 &#40;維護計畫&#41;</span><span class="sxs-lookup"><span data-stu-id="3813b-119">Reorganize Index Task &#40;Maintenance Plan&#41;</span></span>](../../relational-databases/maintenance-plans/reorganize-index-task-maintenance-plan.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="3813b-120">相關工作</span><span class="sxs-lookup"><span data-stu-id="3813b-120">Related Tasks</span></span>  
 <span data-ttu-id="3813b-121">如需如何在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師中設定這些屬性的詳細資訊，請參閱 [設定工作或容器的屬性](../set-the-properties-of-a-task-or-container.md)。</span><span class="sxs-lookup"><span data-stu-id="3813b-121">For more information about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, see [Set the Properties of a Task or Container](../set-the-properties-of-a-task-or-container.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3813b-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3813b-122">See Also</span></span>  
 <span data-ttu-id="3813b-123">[Integration Services 工作](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="3813b-123">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="3813b-124">控制流程</span><span class="sxs-lookup"><span data-stu-id="3813b-124">Control Flow</span></span>](control-flow.md)  
  
  
