---
title: 壓縮資料庫工作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.shrinkdatabasetask.f1
helpviewer_keywords:
- Shrink Database task
- database shrinking [Integration Services]
- shrinking databases
ms.assetid: e66286f8-97b1-4e5a-86b4-e56f1932b7d5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 587777928e362e87e4b691e3c46167c1239984cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599130"
---
# <a name="shrink-database-task"></a><span data-ttu-id="1ff22-102">壓縮資料庫工作</span><span class="sxs-lookup"><span data-stu-id="1ff22-102">Shrink Database Task</span></span>
  <span data-ttu-id="1ff22-103">「壓縮資料庫」工作會減少 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫資料和記錄檔的大小。</span><span class="sxs-lookup"><span data-stu-id="1ff22-103">The Shrink Database task reduces the size of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database data and log files.</span></span>  
  
 <span data-ttu-id="1ff22-104">藉由使用「壓縮資料庫」工作，封裝可壓縮單一資料庫或多重資料庫的檔案。</span><span class="sxs-lookup"><span data-stu-id="1ff22-104">By using the Shrink Database task, a package can shrink files for a single database or multiple databases.</span></span>  
  
 <span data-ttu-id="1ff22-105">將資料頁面從檔案結尾移到靠近檔案前端的未使用空間，以壓縮資料並復原儲存空間。</span><span class="sxs-lookup"><span data-stu-id="1ff22-105">Shrinking data files recovers space by moving pages of data from the end of the file to unoccupied space closer to the front of the file.</span></span> <span data-ttu-id="1ff22-106">當檔案結尾建立了足夠的可用空間後，檔案結尾的資料頁面便可取消配置並返回檔案系統。</span><span class="sxs-lookup"><span data-stu-id="1ff22-106">When enough free space is created at the end of the file, data pages at end of the file can deallocated and returned to the file system.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="1ff22-107">為壓縮檔案所移動的資料可散佈至檔案中的任何可用位置。</span><span class="sxs-lookup"><span data-stu-id="1ff22-107">Data that is moved to shrink a file can be scattered to any available location in the file.</span></span> <span data-ttu-id="1ff22-108">如此會造成索引片段，並可能導致大範圍之索引搜尋的查詢效能變慢。</span><span class="sxs-lookup"><span data-stu-id="1ff22-108">This causes index fragmentation and can slow the performance of queries that search a range of the index.</span></span> <span data-ttu-id="1ff22-109">若要消除資料片段，可考慮在壓縮之後重建該檔案的索引。</span><span class="sxs-lookup"><span data-stu-id="1ff22-109">To eliminate the fragmentation, consider rebuilding the indexes on the file after shrinking.</span></span>  
  
## <a name="commands"></a><span data-ttu-id="1ff22-110">命令</span><span class="sxs-lookup"><span data-stu-id="1ff22-110">Commands</span></span>  
 <span data-ttu-id="1ff22-111">「壓縮資料庫」工作會封裝 DBCC SHRINKDATABASE 命令，包括下列引數和選項：</span><span class="sxs-lookup"><span data-stu-id="1ff22-111">The Shrink Database task encapsulates a DBCC SHRINKDATABASE command, including the following arguments and options:</span></span>  
  
-   <span data-ttu-id="1ff22-112">*database_name*</span><span class="sxs-lookup"><span data-stu-id="1ff22-112">*database_name*</span></span>  
  
-   <span data-ttu-id="1ff22-113">*target_percent*</span><span class="sxs-lookup"><span data-stu-id="1ff22-113">*target_percent*</span></span>  
  
-   <span data-ttu-id="1ff22-114">NOTRUNCATE 或 TRUNCATEONLY。</span><span class="sxs-lookup"><span data-stu-id="1ff22-114">NOTRUNCATE or TRUNCATEONLY.</span></span>  
  
 <span data-ttu-id="1ff22-115">如果「壓縮資料庫」工作壓縮多個資料庫，則工作會執行多個 SHRINKDATABASE 命令，亦即針對每個資料庫執行一個命令。</span><span class="sxs-lookup"><span data-stu-id="1ff22-115">If the Shrink Database task shrinks multiple databases, the task runs multiple SHRINKDATABASE commands, one for each database.</span></span> <span data-ttu-id="1ff22-116">SHRINKDATABASE 命令的所有執行個體會使用相同的引數值，但 *database_name* 引數例外。</span><span class="sxs-lookup"><span data-stu-id="1ff22-116">All instances of the SHRINKDATABASE command use the same argument values, except for the *database_name* argument.</span></span> <span data-ttu-id="1ff22-117">如需詳細資訊，請參閱 [DBCC SHRINKDATABASE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1ff22-117">For more information, see [DBCC SHRINKDATABASE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql).</span></span>  
  
## <a name="configuration-of-the-shrink-database-task"></a><span data-ttu-id="1ff22-118">壓縮資料庫工作的組態</span><span class="sxs-lookup"><span data-stu-id="1ff22-118">Configuration of the Shrink Database Task</span></span>  
 <span data-ttu-id="1ff22-119">您可以透過 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師設定屬性。</span><span class="sxs-lookup"><span data-stu-id="1ff22-119">You can set properties through the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="1ff22-120">這項工作位於「 **設計師」中** [工具箱] **的** [維護計畫工作] [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 區段。</span><span class="sxs-lookup"><span data-stu-id="1ff22-120">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="1ff22-121">如需可在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師中設定之屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="1ff22-121">For more information about the properties that you can set in the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="1ff22-122">壓縮資料庫工作 &#40;維護計畫&#41;</span><span class="sxs-lookup"><span data-stu-id="1ff22-122">Shrink Database Task &#40;Maintenance Plan&#41;</span></span>](../../relational-databases/maintenance-plans/shrink-database-task-maintenance-plan.md)  
  
 <span data-ttu-id="1ff22-123">如需有關在「 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師」中設定這些屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="1ff22-123">For more information about setting these properties in the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="1ff22-124">設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="1ff22-124">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
  
