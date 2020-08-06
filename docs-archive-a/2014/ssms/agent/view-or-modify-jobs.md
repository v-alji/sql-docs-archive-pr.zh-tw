---
title: 檢視或修改作業 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], modifying
- jobs [SQL Server Agent], viewing
- modifying jobs
- viewing jobs
- SQL Server Agent jobs, viewing
- SQL Server Agent jobs, modifying
- displaying jobs
ms.assetid: 57f649b8-190c-4304-abd7-7ca5297deab7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5d0d731d25c20597be3ac84adfacd8973e4a51cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699139"
---
# <a name="view-or-modify-jobs"></a><span data-ttu-id="ec7d3-102">檢視或修改作業</span><span class="sxs-lookup"><span data-stu-id="ec7d3-102">View or Modify Jobs</span></span>
  <span data-ttu-id="ec7d3-103">您可檢視您所建立的任何作業。</span><span class="sxs-lookup"><span data-stu-id="ec7d3-103">You can view any job you have created.</span></span> <span data-ttu-id="ec7d3-104">在執行作業之後，您也可以檢視其記錄。</span><span class="sxs-lookup"><span data-stu-id="ec7d3-104">After you have run a job, you can also view its history.</span></span> <span data-ttu-id="ec7d3-105">檢視作業的記錄可讓您了解作業執行的時間、整體作業的狀態，以及作業中每個作業步驟的狀態。</span><span class="sxs-lookup"><span data-stu-id="ec7d3-105">Viewing a job's history allows you to see when the job ran, the status of the job as a whole, and the status of each job step in the job.</span></span> <span data-ttu-id="ec7d3-106">您可以了解作業過去是否曾經失敗、作業最後一次順利完成的時間，以及作業每次執行時所建立的輸出。</span><span class="sxs-lookup"><span data-stu-id="ec7d3-106">You can see whether the job ever failed in the past, when the job last completed successfully, and what output the job created each time the job ran.</span></span> <span data-ttu-id="ec7d3-107">無論擁有者是誰， **系統管理員** 固定伺服器角色的成員一律可以檢視或修改作業。</span><span class="sxs-lookup"><span data-stu-id="ec7d3-107">Members of the **sysadmin** fixed server role can view or modify any job, regardless of the owner.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ec7d3-108">作業至少必須已經執行過一次才會有作業記錄。</span><span class="sxs-lookup"><span data-stu-id="ec7d3-108">A job must have been executed at least one time for there to be a job history.</span></span> <span data-ttu-id="ec7d3-109">您可以限制作業記錄的總大小與其中每個作業所佔的大小。</span><span class="sxs-lookup"><span data-stu-id="ec7d3-109">You can limit the total size of the job history log and the size per job.</span></span>  
  
 <span data-ttu-id="ec7d3-110">最後，您可以修改作業以符合新的需求。</span><span class="sxs-lookup"><span data-stu-id="ec7d3-110">Finally, you can modify a job to meet new requirements.</span></span> <span data-ttu-id="ec7d3-111">您可以修改：</span><span class="sxs-lookup"><span data-stu-id="ec7d3-111">You can modify:</span></span>  
  
-   <span data-ttu-id="ec7d3-112">回應選項</span><span class="sxs-lookup"><span data-stu-id="ec7d3-112">Response options</span></span>  
  
-   <span data-ttu-id="ec7d3-113">排程</span><span class="sxs-lookup"><span data-stu-id="ec7d3-113">Schedules</span></span>  
  
-   <span data-ttu-id="ec7d3-114">作業步驟</span><span class="sxs-lookup"><span data-stu-id="ec7d3-114">Job steps</span></span>  
  
-   <span data-ttu-id="ec7d3-115">擁有權</span><span class="sxs-lookup"><span data-stu-id="ec7d3-115">Ownership</span></span>  
  
-   <span data-ttu-id="ec7d3-116">作業類別目錄</span><span class="sxs-lookup"><span data-stu-id="ec7d3-116">Job category</span></span>  
  
-   <span data-ttu-id="ec7d3-117">目標伺服器 (只適用多伺服器作業)</span><span class="sxs-lookup"><span data-stu-id="ec7d3-117">Target servers (multiserver jobs only)</span></span>  
  
 <span data-ttu-id="ec7d3-118">若要確定對多重伺服器作業所做的變更會生效，您必須將變更發佈到下載清單，目標伺服器才能下載更新的作業。</span><span class="sxs-lookup"><span data-stu-id="ec7d3-118">To make sure that changes to multiserver jobs take effect, you must post the changes to the download list so that target servers can download the updated job.</span></span> <span data-ttu-id="ec7d3-119">若要確保目標伺服器具有目前最新的作業定義，請在更新該多重伺服器作業後發佈一個 INSERT 指示，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ec7d3-119">To ensure that target servers have the most current job definitions, post an INSERT instruction after you update the multiserver job as follows:</span></span>  
  
```  
EXECUTE sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
 <span data-ttu-id="ec7d3-120">如需詳細資訊，請參閱[sp_purge_jobhistory &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-purge-jobhistory-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ec7d3-120">For more information, see [sp_purge_jobhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-purge-jobhistory-transact-sql).</span></span>  
  
 <span data-ttu-id="ec7d3-121">**系統管理員** 固定伺服器角色的成員不僅可以檢視所有作業的定義或記錄，也可修改任何作業。</span><span class="sxs-lookup"><span data-stu-id="ec7d3-121">Members of the **sysadmin** fixed server role can view the definition or history of any job, and can modify any job.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="ec7d3-122">相關工作</span><span class="sxs-lookup"><span data-stu-id="ec7d3-122">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ec7d3-123">**說明**</span><span class="sxs-lookup"><span data-stu-id="ec7d3-123">**Description**</span></span>|<span data-ttu-id="ec7d3-124">**主題**</span><span class="sxs-lookup"><span data-stu-id="ec7d3-124">**Topic**</span></span>|  
|<span data-ttu-id="ec7d3-125">說明如何檢視 [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent 作業。</span><span class="sxs-lookup"><span data-stu-id="ec7d3-125">Describes how to view [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent jobs.</span></span>|[<span data-ttu-id="ec7d3-126">檢視作業</span><span class="sxs-lookup"><span data-stu-id="ec7d3-126">View a Job</span></span>](view-a-job.md)|  
|<span data-ttu-id="ec7d3-127">說明如何檢視 [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent 作業的歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="ec7d3-127">Describes how to view the [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent job history log.</span></span>|[<span data-ttu-id="ec7d3-128">查看作業歷程記錄</span><span class="sxs-lookup"><span data-stu-id="ec7d3-128">View the Job History</span></span>](view-the-job-history.md)|  
|<span data-ttu-id="ec7d3-129">說明如何刪除 [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent 作業的歷程記錄內容。</span><span class="sxs-lookup"><span data-stu-id="ec7d3-129">Describes how to delete the contents of the [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent job history log.</span></span>|[<span data-ttu-id="ec7d3-130">清除作業歷程記錄</span><span class="sxs-lookup"><span data-stu-id="ec7d3-130">Clear the Job History Log</span></span>](clear-the-job-history-log.md)|  
|<span data-ttu-id="ec7d3-131">說明如何設定 [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent 作業的記錄大小限制。</span><span class="sxs-lookup"><span data-stu-id="ec7d3-131">Describes how to set size limits for [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent job history logs.</span></span>|[<span data-ttu-id="ec7d3-132">調整作業記錄大小</span><span class="sxs-lookup"><span data-stu-id="ec7d3-132">Resize the Job History Log</span></span>](resize-the-job-history-log.md)|  
|<span data-ttu-id="ec7d3-133">說明如何變更 [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent 作業的屬性。</span><span class="sxs-lookup"><span data-stu-id="ec7d3-133">Describes how to change the properties of [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent jobs.</span></span>|[<span data-ttu-id="ec7d3-134">Modify a Job</span><span class="sxs-lookup"><span data-stu-id="ec7d3-134">Modify a Job</span></span>](modify-a-job.md)|  
  
## <a name="see-also"></a><span data-ttu-id="ec7d3-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec7d3-135">See Also</span></span>  
 [<span data-ttu-id="ec7d3-136">dbo.sysjobhistory &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="ec7d3-136">dbo.sysjobhistory &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-tables/dbo-sysjobhistory-transact-sql)  
  
  
