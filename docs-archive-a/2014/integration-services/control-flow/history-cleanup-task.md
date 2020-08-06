---
title: 記錄清除工作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.historycleanuptask.f1
helpviewer_keywords:
- history tables [SQL Server]
- History Cleanup task [Integration Services]
ms.assetid: 5defc5b9-dfd3-4859-a7fe-ac8c2b5480f8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 84bc697b7fb18269fc581cea51e111aebc82c15e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584678"
---
# <a name="history-cleanup-task"></a><span data-ttu-id="dc784-102">記錄清除工作</span><span class="sxs-lookup"><span data-stu-id="dc784-102">History Cleanup Task</span></span>
  <span data-ttu-id="dc784-103">「記錄清除」工作會刪除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb 資料庫中下列記錄資料表的項目。</span><span class="sxs-lookup"><span data-stu-id="dc784-103">The History Cleanup task deletes entries in the following history tables in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb database.</span></span>  
  
-   <span data-ttu-id="dc784-104">backupfile</span><span class="sxs-lookup"><span data-stu-id="dc784-104">backupfile</span></span>  
  
-   <span data-ttu-id="dc784-105">backupfilegroup</span><span class="sxs-lookup"><span data-stu-id="dc784-105">backupfilegroup</span></span>  
  
-   <span data-ttu-id="dc784-106">backupmediafamily</span><span class="sxs-lookup"><span data-stu-id="dc784-106">backupmediafamily</span></span>  
  
-   <span data-ttu-id="dc784-107">backupmediaset</span><span class="sxs-lookup"><span data-stu-id="dc784-107">backupmediaset</span></span>  
  
-   <span data-ttu-id="dc784-108">backupset</span><span class="sxs-lookup"><span data-stu-id="dc784-108">backupset</span></span>  
  
-   <span data-ttu-id="dc784-109">restorefile</span><span class="sxs-lookup"><span data-stu-id="dc784-109">restorefile</span></span>  
  
-   <span data-ttu-id="dc784-110">restorefilegroup</span><span class="sxs-lookup"><span data-stu-id="dc784-110">restorefilegroup</span></span>  
  
-   <span data-ttu-id="dc784-111">restorehistory</span><span class="sxs-lookup"><span data-stu-id="dc784-111">restorehistory</span></span>  
  
 <span data-ttu-id="dc784-112">藉由使用「記錄清除」工作，封裝便能刪除關於備份和還原活動、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業，以及資料庫維護計畫的記錄資料。</span><span class="sxs-lookup"><span data-stu-id="dc784-112">By using the History Cleanup task, a package can delete historical data related to backup and restore activities, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs, and database maintenance plans.</span></span>  
  
 <span data-ttu-id="dc784-113">這項工作會封裝 sp_delete_backuphistory 系統預存程序，並將指定的日期傳遞至該程序做為引數。</span><span class="sxs-lookup"><span data-stu-id="dc784-113">This task encapsulates the sp_delete_backuphistory system stored procedure and passes the specified date to the procedure as an argument.</span></span> <span data-ttu-id="dc784-114">如需詳細資訊，請參閱 [sp_delete_backuphistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="dc784-114">For more information, see [sp_delete_backuphistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql).</span></span>  
  
## <a name="configuration-of-the-history-cleanup-task"></a><span data-ttu-id="dc784-115">設定記錄清除工作</span><span class="sxs-lookup"><span data-stu-id="dc784-115">Configuration of the History Cleanup Task</span></span>  
 <span data-ttu-id="dc784-116">這項工作包含指定歷程記錄資料表中最舊日期之資料的屬性。</span><span class="sxs-lookup"><span data-stu-id="dc784-116">The task includes a property for specifying the oldest date of data retained in the history tables.</span></span> <span data-ttu-id="dc784-117">您可以用目前日期起算的天數、週數、月數或年數表示該日期，而工作會自動將間隔翻譯成日期。</span><span class="sxs-lookup"><span data-stu-id="dc784-117">You can indicate the date by number of days, weeks, months, or years from the current day, and the task automatically translates the interval to a date.</span></span>  
  
 <span data-ttu-id="dc784-118">您可以透過 [ [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師] 設定屬性。</span><span class="sxs-lookup"><span data-stu-id="dc784-118">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="dc784-119">這項工作位於「 **設計師」中** [工具箱] **的** [維護計畫工作] [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 區段。</span><span class="sxs-lookup"><span data-stu-id="dc784-119">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="dc784-120">如需有關可在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師中設定之屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="dc784-120">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="dc784-121">記錄清除工作 &#40;維護計畫&#41;</span><span class="sxs-lookup"><span data-stu-id="dc784-121">History Cleanup Task &#40;Maintenance Plan&#41;</span></span>](../../relational-databases/maintenance-plans/history-cleanup-task-maintenance-plan.md)  
  
 <span data-ttu-id="dc784-122">如需有關如何在「 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師」中設定這些屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="dc784-122">For more information about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="dc784-123">設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="dc784-123">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="dc784-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc784-124">See Also</span></span>  
 <span data-ttu-id="dc784-125">[Integration Services 工作](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="dc784-125">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="dc784-126">控制流程</span><span class="sxs-lookup"><span data-stu-id="dc784-126">Control Flow</span></span>](control-flow.md)  
  
  
