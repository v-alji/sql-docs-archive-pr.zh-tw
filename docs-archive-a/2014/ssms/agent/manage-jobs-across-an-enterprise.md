---
title: 管理整個企業的作業 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- multiserver job management [SQL Server]
- jobs [SQL Server Agent], modifying
- modifying jobs
- SQL Server Agent jobs, modifying
- target servers [SQL Server], job changes
ms.assetid: 4fe7f6c6-f89b-4430-979c-4994a5dcf7a6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 385435302b2e987c86afb17eaebf90e91bc93e56
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594351"
---
# <a name="manage-jobs-across-an-enterprise"></a><span data-ttu-id="a2235-102">管理整個企業的作業</span><span class="sxs-lookup"><span data-stu-id="a2235-102">Manage Jobs Across an Enterprise</span></span>
  <span data-ttu-id="a2235-103">如果您對外部的多伺服器作業定義進行變更 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，您必須將變更公佈到下載清單，以便目標伺服器可以再次下載已更新的作業。</span><span class="sxs-lookup"><span data-stu-id="a2235-103">If you make changes to multiserver job definitions outside [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you must post the changes to the download list so that target servers can download the updated job again.</span></span> <span data-ttu-id="a2235-104">若要確保目標伺服器具有目前的作業定義，請在更新多伺服器作業後公佈 INSERT 指示，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a2235-104">To ensure that target servers have current job definitions, post an INSERT instruction after you update the multiserver job, as follows:</span></span>  
  
```  
EXECUTE sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
 <span data-ttu-id="a2235-105">若要通知目標伺服器多伺服器作業已有修改，您必須在使用下列任一程序後，叫用先前的命令：</span><span class="sxs-lookup"><span data-stu-id="a2235-105">To notify target servers that a multiserver job has been modified, you must invoke the preceding command after using any of the following procedures:</span></span>  
  
-   [<span data-ttu-id="a2235-106">sp_add_jobstep (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a2235-106">sp_add_jobstep (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)  
  
-   [<span data-ttu-id="a2235-107">sp_update_jobstep (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a2235-107">sp_update_jobstep (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql)  
  
-   [<span data-ttu-id="a2235-108">sp_delete_jobstep (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a2235-108">sp_delete_jobstep (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql)  
  
-   [<span data-ttu-id="a2235-109">sp_attach_schedule &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a2235-109">sp_attach_schedule &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql)  
  
-   [<span data-ttu-id="a2235-110">sp_detach_schedule &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="a2235-110">sp_detach_schedule &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-detach-schedule-transact-sql)  
  
    > [!NOTE]  
    >  <span data-ttu-id="a2235-111">在您呼叫 **sp_update_job** 或 **sp_delete_job** 之後，不需要呼叫 **sp_post_msx_operation**，因為這些預存程序會自動將所需的變更傳送到下載清單。</span><span class="sxs-lookup"><span data-stu-id="a2235-111">It is not necessary to call **sp_post_msx_operation** after you call **sp_update_job** or **sp_delete_job**, because these stored procedures post the required changes to the download list automatically.</span></span>  
  
 <span data-ttu-id="a2235-112">下列是管理整個企業作業的一般工作。</span><span class="sxs-lookup"><span data-stu-id="a2235-112">The following are common tasks for managing jobs across an enterprise:</span></span>  
  
 <span data-ttu-id="a2235-113">**若要檢查目標伺服器的狀態**</span><span class="sxs-lookup"><span data-stu-id="a2235-113">**To check the status of a target server**</span></span>  
  
-   [<span data-ttu-id="a2235-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a2235-114">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-help-targetserver-transact-sql)  
  
-   [<span data-ttu-id="a2235-115">SQL Server 管理物件 (SMO)</span><span class="sxs-lookup"><span data-stu-id="a2235-115">SQL Server Management Objects (SMO)</span></span>](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
 <span data-ttu-id="a2235-116">**若要變更作業的目標伺服器**</span><span class="sxs-lookup"><span data-stu-id="a2235-116">**To change the target servers for a job**</span></span>  
  
-   [<span data-ttu-id="a2235-117">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a2235-117">SQL Server Management Studio</span></span>](modify-the-target-servers-for-a-job.md)  
  
-   [<span data-ttu-id="a2235-118">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a2235-118">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql)  
  
-   [<span data-ttu-id="a2235-119">SQL Server 管理物件 (SMO)</span><span class="sxs-lookup"><span data-stu-id="a2235-119">SQL Server Management Objects (SMO)</span></span>](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
 <span data-ttu-id="a2235-120">**若要變更目標伺服器的位置**</span><span class="sxs-lookup"><span data-stu-id="a2235-120">**To change the location of a target server**</span></span>  
  
-   [<span data-ttu-id="a2235-121">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a2235-121">SQL Server Management Studio</span></span>](../sql-server-management-studio-ssms.md)  
  
-   [<span data-ttu-id="a2235-122">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a2235-122">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql)  
  
-   [<span data-ttu-id="a2235-123">SQL Server 管理物件 (SMO)</span><span class="sxs-lookup"><span data-stu-id="a2235-123">SQL Server Management Objects (SMO)</span></span>](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
 <span data-ttu-id="a2235-124">**若要將目標伺服器的時鐘同步化**</span><span class="sxs-lookup"><span data-stu-id="a2235-124">**To synchronize target server clocks**</span></span>  
  
-   [<span data-ttu-id="a2235-125">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a2235-125">SQL Server Management Studio</span></span>](synchronize-target-server-clocks-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="a2235-126">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a2235-126">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql)  
  
 <span data-ttu-id="a2235-127">**若要強制目標伺服器輪詢主要伺服器**</span><span class="sxs-lookup"><span data-stu-id="a2235-127">**To force a target server to poll the master server**</span></span>  
  
-   [<span data-ttu-id="a2235-128">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a2235-128">SQL Server Management Studio</span></span>](force-a-target-server-to-poll-the-master-server.md)  
  
-   [<span data-ttu-id="a2235-129">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a2235-129">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="a2235-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2235-130">See Also</span></span>  
 [<span data-ttu-id="a2235-131">管理事件</span><span class="sxs-lookup"><span data-stu-id="a2235-131">Manage Events</span></span>](manage-events.md)  
  
  
