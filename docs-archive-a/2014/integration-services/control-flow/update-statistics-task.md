---
title: 更新統計資料工作 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.updatestatisticstask.f1
helpviewer_keywords:
- updating statistics
- Update Statistics task [Integration Services]
ms.assetid: 0247483b-f092-4511-8fa8-3610108bd1bc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1507ada1e4fa087901383930fce4996c191fb553
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584657"
---
# <a name="update-statistics-task"></a><span data-ttu-id="2fe95-102">更新統計資料工作</span><span class="sxs-lookup"><span data-stu-id="2fe95-102">Update Statistics Task</span></span>
  <span data-ttu-id="2fe95-103">「更新統計資料」工作會在指定的資料表或索引檢視表中，更新一個或多個統計群組 (集合) 索引鍵值散發的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="2fe95-103">The Update Statistics task updates information about the distribution of key values for one or more statistics groups (collections) in the specified table or indexed view.</span></span> <span data-ttu-id="2fe95-104">如需詳細資訊，請參閱[統計資料](../../relational-databases/statistics/statistics.md)。</span><span class="sxs-lookup"><span data-stu-id="2fe95-104">For more information, see [Statistics](../../relational-databases/statistics/statistics.md).</span></span>  
  
 <span data-ttu-id="2fe95-105">藉由使用「更新統計資料」工作，封裝可更新單一資料庫或多重資料庫的統計資料。</span><span class="sxs-lookup"><span data-stu-id="2fe95-105">By using the Update Statistics task, a package can update statistics for a single database or multiple databases.</span></span> <span data-ttu-id="2fe95-106">如果此工作只更新單一資料庫中的統計資料，您可以選擇要由此工作更新統計資料的檢視或資料表。</span><span class="sxs-lookup"><span data-stu-id="2fe95-106">If the task updates only the statistics in a single database, you can choose the views or the tables whose statistics the task updates.</span></span> <span data-ttu-id="2fe95-107">您可以將更新作業設定為更新所有統計資料、只更新資料行統計資料，或只更新索引統計資料。</span><span class="sxs-lookup"><span data-stu-id="2fe95-107">You can configure the update to update all statistics, column statistics only, or index statistics only.</span></span>  
  
 <span data-ttu-id="2fe95-108">此工作會封裝 UPDATE STATISTICS 陳述式，包括下列引數和子句在內：</span><span class="sxs-lookup"><span data-stu-id="2fe95-108">This task encapsulates an UPDATE STATISTICS statement, including the following arguments and clauses:</span></span>  
  
-   <span data-ttu-id="2fe95-109">*table_name* 或 *view_name* 引數。</span><span class="sxs-lookup"><span data-stu-id="2fe95-109">The *table_name* or *view_name* argument.</span></span>  
  
-   <span data-ttu-id="2fe95-110">如果更新套用至所有統計資料，則會隱含 WITH ALL 子句。</span><span class="sxs-lookup"><span data-stu-id="2fe95-110">If the update applies to all statistics, the WITH ALL clause is implied.</span></span>  
  
-   <span data-ttu-id="2fe95-111">如果更新只套用至資料行，則會包含 WITH COLUMN 子句。</span><span class="sxs-lookup"><span data-stu-id="2fe95-111">If the update applies only to columns, the WITH COLUMN clause is included.</span></span>  
  
-   <span data-ttu-id="2fe95-112">如果更新只套用至索引，則會包含 WITH INDEX 子句。</span><span class="sxs-lookup"><span data-stu-id="2fe95-112">If the update applies only to indexes, the WITH INDEX clause is included.</span></span>  
  
 <span data-ttu-id="2fe95-113">如果「更新統計資料」工作更新多重資料庫中的統計資料，則此工作會執行多個 UPDATE STATISTICS 陳述式，每個資料表或檢視各一個。</span><span class="sxs-lookup"><span data-stu-id="2fe95-113">If the Update Statistics task updates statistics in multiple databases, the task runs multiple UPDATE STATISTICS statements, one for each table or view.</span></span> <span data-ttu-id="2fe95-114">UPDATE STATISTICS 的所有執行個體都使用相同的子句，但使用不同的 *table_name* 或 *view_name* 值。</span><span class="sxs-lookup"><span data-stu-id="2fe95-114">All instances of UPDATE STATISTICS use the same clause, but different *table_name* or *view_name* values.</span></span> <span data-ttu-id="2fe95-115">如需詳細資訊，請參閱 [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql) 和 [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2fe95-115">For more information, see [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql) and [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2fe95-116">此工作用於建立工作執行的 Transact-SQL 陳述式之時間，與工作更新的統計資料數成正比。</span><span class="sxs-lookup"><span data-stu-id="2fe95-116">The time the task takes to create the Transact-SQL statement that the task runs is proportionate to the number of statistics the task updates.</span></span> <span data-ttu-id="2fe95-117">如果此工作設定成更新含有大量索引的資料庫內所有資料表與檢視表中的統計資料，或是更新多重資料庫中的統計資料，則此工作可能會花費相當多的時間產生 Transact-SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="2fe95-117">If the task is configured to update statistics in all the tables and views in a database with a large number of indexes, or to update statistics in multiple databases, the task can take a considerable amount of time to generate the Transact-SQL statement.</span></span>  
  
## <a name="configuration-of-the-update-statistics-task"></a><span data-ttu-id="2fe95-118">設定更新統計資料工作</span><span class="sxs-lookup"><span data-stu-id="2fe95-118">Configuration of the Update Statistics Task</span></span>  
 <span data-ttu-id="2fe95-119">您可以透過 [ [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師] 設定屬性。</span><span class="sxs-lookup"><span data-stu-id="2fe95-119">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="2fe95-120">這項工作位於「 **設計師」中** [工具箱] **的** [維護計畫工作] [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 區段。</span><span class="sxs-lookup"><span data-stu-id="2fe95-120">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="2fe95-121">如需有關可在「 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師」中設定之屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="2fe95-121">For information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="2fe95-122">更新統計資料工作 &#40;維護計畫&#41;</span><span class="sxs-lookup"><span data-stu-id="2fe95-122">Update Statistics Task &#40;Maintenance Plan&#41;</span></span>](../../relational-databases/maintenance-plans/update-statistics-task-maintenance-plan.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="2fe95-123">相關工作</span><span class="sxs-lookup"><span data-stu-id="2fe95-123">Related Tasks</span></span>  
 <span data-ttu-id="2fe95-124">如需有關如何在「 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師」中設定這些屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="2fe95-124">For more information about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="2fe95-125">設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="2fe95-125">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="2fe95-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2fe95-126">See Also</span></span>  
 <span data-ttu-id="2fe95-127">[Integration Services 工作](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="2fe95-127">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="2fe95-128">控制流程</span><span class="sxs-lookup"><span data-stu-id="2fe95-128">Control Flow</span></span>](control-flow.md)  
  
  
