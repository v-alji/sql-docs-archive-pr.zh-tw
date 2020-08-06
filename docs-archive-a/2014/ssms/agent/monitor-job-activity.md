---
title: 監視作業活動 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, monitoring
- jobs [SQL Server Agent], monitoring
- monitoring [SQL Server], jobs
- activity monitoring [SQL Server Agent]
- monitoring [SQL Server], SQL Server Agent
- monitoring [SQL Server Agent]
- SQL Server Agent Job Activity Monitor
- SQL Server Agent jobs, monitoring
- performance [SQL Server], jobs
- current activity
ms.assetid: 71cb432b-631d-4b8b-9965-e731b3d8266d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5088e029e90b4556c1559f8c948e8a8734762749
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594336"
---
# <a name="monitor-job-activity"></a><span data-ttu-id="111e5-102">監視作業活動</span><span class="sxs-lookup"><span data-stu-id="111e5-102">Monitor Job Activity</span></span>
  <span data-ttu-id="111e5-103">您可以使用「[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業活動監視器」，監視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上所有已定義作業的目前活動。</span><span class="sxs-lookup"><span data-stu-id="111e5-103">You can monitor the current activity of all defined jobs on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Job Activity Monitor.</span></span>  
  
## <a name="sql-server-agent-sessions"></a><span data-ttu-id="111e5-104">SQL Server Agent 工作階段</span><span class="sxs-lookup"><span data-stu-id="111e5-104">SQL Server Agent Sessions</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="111e5-105">每次服務啟動時，Agent 都會建立新的工作階段。</span><span class="sxs-lookup"><span data-stu-id="111e5-105">Agent creates a new session each time the service starts.</span></span> <span data-ttu-id="111e5-106">建立新的工作階段時， **msdb** 資料庫中的 **sysjobactivity** 資料表就會填入所有現有的已定義作業。</span><span class="sxs-lookup"><span data-stu-id="111e5-106">When a new session is created, the **sysjobactivity** table in the **msdb** database is populated with all the existing defined jobs.</span></span> <span data-ttu-id="111e5-107">當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 重新啟動時，這個資料表會保留作業的上一個活動。</span><span class="sxs-lookup"><span data-stu-id="111e5-107">This table preserves the last activity for jobs when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is restarted.</span></span> <span data-ttu-id="111e5-108">每一個工作階段會記錄從作業開始到完成的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 一般作業活動。</span><span class="sxs-lookup"><span data-stu-id="111e5-108">Each session records [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent normal job activity from the start of the job to its finish.</span></span> <span data-ttu-id="111e5-109">這些工作階段的相關資訊儲存在 **msdb** 資料庫的 **syssessions** 資料表中。</span><span class="sxs-lookup"><span data-stu-id="111e5-109">Information about these sessions is stored in the **syssessions** table of the **msdb** database.</span></span>  
  
## <a name="job-activity-monitor"></a><span data-ttu-id="111e5-110">作業活動監視器</span><span class="sxs-lookup"><span data-stu-id="111e5-110">Job Activity Monitor</span></span>  
 <span data-ttu-id="111e5-111">「作業活動監視器」可讓您使用 **檢視** sysjobactivity [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]資料表。</span><span class="sxs-lookup"><span data-stu-id="111e5-111">The Job Activity Monitor allows you to view the **sysjobactivity** table by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="111e5-112">您可以檢視伺服器上的所有作業，或者您也可以定義篩選，來限制所顯示的作業數目。</span><span class="sxs-lookup"><span data-stu-id="111e5-112">You can view all jobs on the server, or you can define filters to limit the number of jobs displayed.</span></span> <span data-ttu-id="111e5-113">您也可以按一下 [代理程式作業活動]\*\*\*\* 方格中的資料行標題，排序作業資訊。</span><span class="sxs-lookup"><span data-stu-id="111e5-113">You can also sort the job information by clicking on a column heading in the **Agent Job Activity** grid.</span></span> <span data-ttu-id="111e5-114">例如，選取 [上次執行]\*\*\*\* 資料行標題時，可以按作業上次執行的順序來檢視作業；</span><span class="sxs-lookup"><span data-stu-id="111e5-114">For example, when you select the **Last Run** column heading, you can view the jobs in the order that they were last run.</span></span> <span data-ttu-id="111e5-115">再按一下資料行標題，可切換作業依上次執行日期的遞增或遞減順序來顯示。</span><span class="sxs-lookup"><span data-stu-id="111e5-115">Clicking the column heading again toggles the jobs in ascending and descending order based on their last run date.</span></span>  
  
 <span data-ttu-id="111e5-116">使用「作業活動監視器」，您可以執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="111e5-116">Using the Job Activity Monitor you can perform the following tasks:</span></span>  
  
-   <span data-ttu-id="111e5-117">啟動和停止作業。</span><span class="sxs-lookup"><span data-stu-id="111e5-117">Start and stop jobs.</span></span>  
  
-   <span data-ttu-id="111e5-118">檢視作業屬性。</span><span class="sxs-lookup"><span data-stu-id="111e5-118">View job properties.</span></span>  
  
-   <span data-ttu-id="111e5-119">檢視特定作業的記錄。</span><span class="sxs-lookup"><span data-stu-id="111e5-119">View the history for a specific job.</span></span>  
  
-   <span data-ttu-id="111e5-120">以手動方式重新整理 [代理程式作業活動]\*\*\*\* 方格中的資訊，或按一下 [檢視重新整理設定]\*\*\*\* 設定自動重新整理間隔。</span><span class="sxs-lookup"><span data-stu-id="111e5-120">Refresh the information in the **Agent Job Activity** grid manually or set an automatic refresh interval by clicking **View refresh settings**.</span></span>  
  
 <span data-ttu-id="111e5-121">當您想要了解有哪些作業已排程執行、目前工作階段期間已執行作業的最後結果，以及找出哪些作業目前執行中或閒置時，便可使用「作業活動監視器」。</span><span class="sxs-lookup"><span data-stu-id="111e5-121">Use the Job Activity Monitor when you want to find out what jobs are scheduled to run, the last outcome of jobs that have run during the current session, and to find out which jobs are currently running or idle.</span></span> <span data-ttu-id="111e5-122">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務異常失敗，您可以查看「作業活動監視器」中的先前工作階段，判斷哪些作業原本正在執行中。</span><span class="sxs-lookup"><span data-stu-id="111e5-122">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service fails unexpectedly, you can determine which jobs were in the middle of being executed by looking at the previous session in the Job Activity Monitor.</span></span>  
  
 <span data-ttu-id="111e5-123">若要開啟「作業活動監視器」，請展開「[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 物件總管」中的 [SQL Server Agent]\*\*\*\*、以滑鼠右鍵按一下 [作業活動監視器]\*\*\*\*，然後按一下 [檢視作業活動]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="111e5-123">To open the Job Activity Monitor, expand **SQL Server Agent** in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] Object Explorer, right-click **Job Activity Monitor**, and click **View Job Activity**.</span></span>  
  
 <span data-ttu-id="111e5-124">您也可以使用預存程序 **sp_help_jobactivity**來檢視目前工作階段的作業活動。</span><span class="sxs-lookup"><span data-stu-id="111e5-124">You can also view job activity for the current session by using the stored procedure **sp_help_jobactivity**.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="111e5-125">相關工作</span><span class="sxs-lookup"><span data-stu-id="111e5-125">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="111e5-126">**說明**</span><span class="sxs-lookup"><span data-stu-id="111e5-126">**Description**</span></span>|<span data-ttu-id="111e5-127">**主題**</span><span class="sxs-lookup"><span data-stu-id="111e5-127">**Topic**</span></span>|  
|<span data-ttu-id="111e5-128">描述如何檢視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業的執行階段狀態。</span><span class="sxs-lookup"><span data-stu-id="111e5-128">Describes how to view the runtime state of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span>|[<span data-ttu-id="111e5-129">View Job Activity</span><span class="sxs-lookup"><span data-stu-id="111e5-129">View Job Activity</span></span>](view-job-activity.md)|  
  
## <a name="see-also"></a><span data-ttu-id="111e5-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="111e5-130">See Also</span></span>  
 <span data-ttu-id="111e5-131">[查看作業活動](view-job-activity.md) </span><span class="sxs-lookup"><span data-stu-id="111e5-131">[View Job Activity](view-job-activity.md) </span></span>  
 <span data-ttu-id="111e5-132">[dbo.sysjobactivity &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/dbo-sysjobactivity-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="111e5-132">[dbo.sysjobactivity &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobactivity-transact-sql) </span></span>  
 <span data-ttu-id="111e5-133">[&#40;Transact-sql 的dbo.sys會話&#41;](/sql/relational-databases/system-tables/dbo-syssessions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="111e5-133">[dbo.syssessions &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-syssessions-transact-sql) </span></span>  
 [<span data-ttu-id="111e5-134">sp_help_jobactivity &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="111e5-134">sp_help_jobactivity &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-help-jobactivity-transact-sql)  
  
  
