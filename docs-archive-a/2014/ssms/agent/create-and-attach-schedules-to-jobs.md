---
title: 建立排程並將排程附加至作業 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server]
- scheduling jobs [SQL Server]
- jobs [SQL Server], scheduling
- CPU [SQL Server], idle conditions
- automatic job processing
- SQL Server Agent jobs, scheduling
- idle time [SQL Server]
ms.assetid: 079c2984-0052-4a37-a2b8-4ece56e6b6b5
author: stevestein
ms.author: sstein
ms.openlocfilehash: ced47013b6552725e6350b113a3722b066016a6b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699259"
---
# <a name="create-and-attach-schedules-to-jobs"></a><span data-ttu-id="5f62a-102">建立及附加排程至作業</span><span class="sxs-lookup"><span data-stu-id="5f62a-102">Create and Attach Schedules to Jobs</span></span>
  <span data-ttu-id="5f62a-103">排程 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業是表示定義在沒有使用者互動的情況下讓作業開始執行的條件。</span><span class="sxs-lookup"><span data-stu-id="5f62a-103">Scheduling [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs means defining the condition or conditions that cause the job to begin running without user interaction.</span></span> <span data-ttu-id="5f62a-104">您可以透過建立作業的新排程，或將現有的排程附加至作業，將作業排程為自動執行。</span><span class="sxs-lookup"><span data-stu-id="5f62a-104">You can schedule a job to run automatically by creating a new schedule for the job, or by attaching an existing schedule to the job.</span></span>  
  
 <span data-ttu-id="5f62a-105">建立排程的方式有兩種：</span><span class="sxs-lookup"><span data-stu-id="5f62a-105">There are two ways to create a schedule:</span></span>  
  
-   <span data-ttu-id="5f62a-106">在您建立作業時建立排程。</span><span class="sxs-lookup"><span data-stu-id="5f62a-106">Create the schedule while you are creating a job.</span></span>  
  
-   <span data-ttu-id="5f62a-107">在 [物件總管] 中建立排程。</span><span class="sxs-lookup"><span data-stu-id="5f62a-107">Create the schedule in Object Explorer.</span></span>  
  
 <span data-ttu-id="5f62a-108">建立排程之後，您就可以將該排程附加至多個作業，即使排程是針對特定作業所建立的也一樣。</span><span class="sxs-lookup"><span data-stu-id="5f62a-108">After a schedule has been created, you can attach that schedule to multiple jobs, even if the schedule was created for a specific job.</span></span> <span data-ttu-id="5f62a-109">此外，您也可以從作業中卸離排程。</span><span class="sxs-lookup"><span data-stu-id="5f62a-109">You can also detach schedules from jobs.</span></span>  
  
 <span data-ttu-id="5f62a-110">排程可以依據時間或事件。</span><span class="sxs-lookup"><span data-stu-id="5f62a-110">A schedule can be based upon time or an event.</span></span> <span data-ttu-id="5f62a-111">例如，您可以將作業排程為在下列時間執行：</span><span class="sxs-lookup"><span data-stu-id="5f62a-111">For example, you can schedule a job to run at the following times:</span></span>  
  
-   <span data-ttu-id="5f62a-112">每當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 啟動時。</span><span class="sxs-lookup"><span data-stu-id="5f62a-112">Whenever [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent starts.</span></span>  
  
-   <span data-ttu-id="5f62a-113">每當電腦的 CPU 使用率達到您定義為閒置的等級時。</span><span class="sxs-lookup"><span data-stu-id="5f62a-113">Whenever CPU utilization of the computer is at a level you have defined as idle.</span></span>  
  
-   <span data-ttu-id="5f62a-114">某個特定的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="5f62a-114">One time, at a specific date and time.</span></span>  
  
-   <span data-ttu-id="5f62a-115">依照週期性排程。</span><span class="sxs-lookup"><span data-stu-id="5f62a-115">On a recurring schedule.</span></span>  
  
 <span data-ttu-id="5f62a-116">除了作業排程之外，您也可以建立警示，讓它藉由執行作業而回應事件。</span><span class="sxs-lookup"><span data-stu-id="5f62a-116">As an alternative to job schedules, you can also create an alert that responds to an event by running a job.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5f62a-117">一次只能執行該作業的一個執行個體。</span><span class="sxs-lookup"><span data-stu-id="5f62a-117">Only one instance of the job can be run at a time.</span></span> <span data-ttu-id="5f62a-118">若您在一項作業依排程執行時又以手動操作來執行， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 會拒絕該要求。</span><span class="sxs-lookup"><span data-stu-id="5f62a-118">If you try to run a job manually while it is running as scheduled, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent refuses the request.</span></span>  
  
 <span data-ttu-id="5f62a-119">若要防止排程的作業執行，您必須進行下列其中一項動作：</span><span class="sxs-lookup"><span data-stu-id="5f62a-119">To prevent a scheduled job from running, you must do one of the following:</span></span>  
  
-   <span data-ttu-id="5f62a-120">停用排程。</span><span class="sxs-lookup"><span data-stu-id="5f62a-120">Disable the schedule.</span></span>  
  
-   <span data-ttu-id="5f62a-121">停用作業。</span><span class="sxs-lookup"><span data-stu-id="5f62a-121">Disable the job.</span></span>  
  
-   <span data-ttu-id="5f62a-122">從作業中卸離排程。</span><span class="sxs-lookup"><span data-stu-id="5f62a-122">Detach the schedule from the job.</span></span>  
  
-   <span data-ttu-id="5f62a-123">停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務。</span><span class="sxs-lookup"><span data-stu-id="5f62a-123">Stop the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service.</span></span>  
  
-   <span data-ttu-id="5f62a-124">刪除排程。</span><span class="sxs-lookup"><span data-stu-id="5f62a-124">Delete the schedule.</span></span>  
  
 <span data-ttu-id="5f62a-125">即使排程未啟動，當回應警示或使用者手動執行作業時，作業仍會回應。</span><span class="sxs-lookup"><span data-stu-id="5f62a-125">If the schedule is not enabled, the job can still run in response to an alert or when a user runs the job manually.</span></span> <span data-ttu-id="5f62a-126">若未啟用作業排程，則所有使用該排程的作業都不會啟用該排程。</span><span class="sxs-lookup"><span data-stu-id="5f62a-126">When a job schedule is not enabled, the schedule is not enabled for any job that uses the schedule.</span></span>  
  
 <span data-ttu-id="5f62a-127">您必須明確地重新啟用已停用排程。</span><span class="sxs-lookup"><span data-stu-id="5f62a-127">You must explicitly re-enable a schedule that has been disabled.</span></span> <span data-ttu-id="5f62a-128">編輯排程並不會自動重新啟用排程。</span><span class="sxs-lookup"><span data-stu-id="5f62a-128">Editing the schedule does not automatically re-enable the schedule.</span></span>  
  
## <a name="scheduling-start-dates"></a><span data-ttu-id="5f62a-129">排程開始日期</span><span class="sxs-lookup"><span data-stu-id="5f62a-129">Scheduling Start Dates</span></span>  
 <span data-ttu-id="5f62a-130">排程的開始日期必須大於或等於 19900101。</span><span class="sxs-lookup"><span data-stu-id="5f62a-130">The start date of a schedule must be greater than or equal to 19900101.</span></span>  
  
 <span data-ttu-id="5f62a-131">當您要將排程附加至作業時，應該檢閱此排程用來首次執行作業的開始日期。</span><span class="sxs-lookup"><span data-stu-id="5f62a-131">When you are attaching a schedule to a job, you should review the start date that the schedule uses to run the job for the first time.</span></span> <span data-ttu-id="5f62a-132">此開始日期會取決於您將排程附加至作業的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="5f62a-132">The start date depends upon the day and time when you attach the schedule to the job.</span></span> <span data-ttu-id="5f62a-133">例如，您可以建立在隔週星期一上午 8:00 執行的排程。</span><span class="sxs-lookup"><span data-stu-id="5f62a-133">For example, you create a schedule that runs every other Monday at 8:00 A.M.</span></span> <span data-ttu-id="5f62a-134">如果您在</span><span class="sxs-lookup"><span data-stu-id="5f62a-134">If you create a job at 10:00 A.M.</span></span> <span data-ttu-id="5f62a-135">2008 年 3 月 3 日星期一上午 10:00 建立某個作業，排程開始日期就是 2008 年 3 月 17 日星期一。</span><span class="sxs-lookup"><span data-stu-id="5f62a-135">on Monday, March 3, 2008, the schedule start date is Monday, March 17, 2008.</span></span> <span data-ttu-id="5f62a-136">如果您在 2008 年 3 月 4 日星期二建立另一個作業，排程開始日期就是 2008 年 3 月 10 日星期一。</span><span class="sxs-lookup"><span data-stu-id="5f62a-136">If you create another job on Tuesday, March 4, 2008, the schedule start date is Monday, March 10, 2008.</span></span>  
  
 <span data-ttu-id="5f62a-137">當您將排程附加至作業之後，可以變更排程開始日期。</span><span class="sxs-lookup"><span data-stu-id="5f62a-137">You can change the schedule start date after you attach the schedule to a job.</span></span>  
  
## <a name="cpu-idle-schedules"></a><span data-ttu-id="5f62a-138">CPU 閒置排程</span><span class="sxs-lookup"><span data-stu-id="5f62a-138">CPU Idle Schedules</span></span>  
 <span data-ttu-id="5f62a-139">為最大化 CPU 資源，您可以為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 定義 CPU 閒置條件。</span><span class="sxs-lookup"><span data-stu-id="5f62a-139">To maximize CPU resources, you can define a CPU idle condition for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5f62a-140">Agent 使用 CPU 閒置條件設定來判斷執行作業的最佳時間。</span><span class="sxs-lookup"><span data-stu-id="5f62a-140">Agent uses the CPU idle condition setting to determine the best time to run jobs.</span></span> <span data-ttu-id="5f62a-141">例如，您可以將重建索引作業排程在 CPU 閒置時間與慢速實際執行期間發生。</span><span class="sxs-lookup"><span data-stu-id="5f62a-141">For example, you can schedule a job to rebuild indexes during CPU idle time and slow production periods.</span></span>  
  
 <span data-ttu-id="5f62a-142">定義作業在 CPU 閒置時間執行之前，請先判斷正常處理時的 CPU 負載。</span><span class="sxs-lookup"><span data-stu-id="5f62a-142">Before you define jobs to run during CPU idle time, determine the load on the CPU during normal processing.</span></span> <span data-ttu-id="5f62a-143">如果要判斷負載，請使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 或效能監視器來監視伺服器流量並收集統計資料。</span><span class="sxs-lookup"><span data-stu-id="5f62a-143">To do this, use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] or Performance Monitor to monitor server traffic and collect statistics.</span></span> <span data-ttu-id="5f62a-144">您可以使用所收集的資訊來設定 CPU 閒置時間百分比與期間。</span><span class="sxs-lookup"><span data-stu-id="5f62a-144">You can then use the information you gather to set the CPU idle time percentage and duration.</span></span>  
  
 <span data-ttu-id="5f62a-145">定義 CPU 閒置條件時，請以低於正常 CPU 使用量 (在指定時間) 的百分比來指定。</span><span class="sxs-lookup"><span data-stu-id="5f62a-145">Define the CPU idle condition as a percentage below which CPU usage must remain for a specified time.</span></span> <span data-ttu-id="5f62a-146">接著，設定時間量。</span><span class="sxs-lookup"><span data-stu-id="5f62a-146">Next, set the amount of time.</span></span> <span data-ttu-id="5f62a-147">當 CPU 使用量在指定的時間內低於指定的百分比時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 會啟動所有具有 CPU 閒置時間排程的作業。</span><span class="sxs-lookup"><span data-stu-id="5f62a-147">When the CPU usage is below the specified percentage for the specified amount of time, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent starts all jobs that have a CPU idle time schedule.</span></span> <span data-ttu-id="5f62a-148">如需使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 或效能監視器來監視 cpu 使用量的詳細資訊，請參閱[監視 cpu 使用量](../../relational-databases/performance-monitor/monitor-cpu-usage.md)。</span><span class="sxs-lookup"><span data-stu-id="5f62a-148">For more information on using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] or Performance Monitor to monitor CPU usage, see [Monitor CPU Usage](../../relational-databases/performance-monitor/monitor-cpu-usage.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="5f62a-149">相關工作</span><span class="sxs-lookup"><span data-stu-id="5f62a-149">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5f62a-150">**說明**</span><span class="sxs-lookup"><span data-stu-id="5f62a-150">**Description**</span></span>|<span data-ttu-id="5f62a-151">**主題**</span><span class="sxs-lookup"><span data-stu-id="5f62a-151">**Topic**</span></span>|  
|<span data-ttu-id="5f62a-152">描述如何建立 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業的排程。</span><span class="sxs-lookup"><span data-stu-id="5f62a-152">Describes how to create a schedule for a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span>|[<span data-ttu-id="5f62a-153">建立排程</span><span class="sxs-lookup"><span data-stu-id="5f62a-153">Create a Schedule</span></span>](create-a-schedule.md)|  
|<span data-ttu-id="5f62a-154">描述如何排程 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業。</span><span class="sxs-lookup"><span data-stu-id="5f62a-154">Describes how to schedule a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span>|[<span data-ttu-id="5f62a-155">排程作業</span><span class="sxs-lookup"><span data-stu-id="5f62a-155">Schedule a Job</span></span>](schedule-a-job.md)|  
|<span data-ttu-id="5f62a-156">說明如何定義伺服器的 CPU 閒置條件。</span><span class="sxs-lookup"><span data-stu-id="5f62a-156">Explains how to define the CPU idle condition for your server.</span></span>|[<span data-ttu-id="5f62a-157">設定 CPU 閒置與持續時間 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="5f62a-157">Set CPU Idle Time and Duration &#40;SQL Server Management Studio&#41;</span></span>](set-cpu-idle-time-and-duration-sql-server-management-studio.md)|  
  
## <a name="see-also"></a><span data-ttu-id="5f62a-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f62a-158">See Also</span></span>  
 <span data-ttu-id="5f62a-159">[sp_help_jobschedule &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobschedule-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5f62a-159">[sp_help_jobschedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobschedule-transact-sql) </span></span>  
 [<span data-ttu-id="5f62a-160">dbo.sysjobschedules &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="5f62a-160">dbo.sysjobschedules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-tables/dbo-sysjobschedules-transact-sql)  
  
  
