---
title: 作業活動監視器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.ACTIVITYMON.F1
- sql12.ag.jobactivitymonitor.alljobs.f1
ms.assetid: 11f2182c-5f71-46f8-8d2b-74f0fc48f2d6
author: stevestein
ms.author: sstein
ms.openlocfilehash: f6f89d5448f0885c85229c2808ee6f85bf6fa071
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699220"
---
# <a name="job-activity-monitor"></a><span data-ttu-id="b7da5-102">作業活動監視器</span><span class="sxs-lookup"><span data-stu-id="b7da5-102">Job Activity Monitor</span></span>
  <span data-ttu-id="b7da5-103">使用此頁面即可檢視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業的目前活動。</span><span class="sxs-lookup"><span data-stu-id="b7da5-103">Use this page to view the current activity of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span> <span data-ttu-id="b7da5-104">按一下 [篩選]\*\*\*\* 即可限制顯示的作業。</span><span class="sxs-lookup"><span data-stu-id="b7da5-104">Click **Filter** to limit the jobs displayed.</span></span> <span data-ttu-id="b7da5-105">[代理程式作業活動]\*\*\*\* 方格是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="b7da5-105">The **Agent Job Activity** grid is read-only.</span></span> <span data-ttu-id="b7da5-106">按一下資料行標頭即可排序方格。</span><span class="sxs-lookup"><span data-stu-id="b7da5-106">Click on the column headers to sort the grid.</span></span> <span data-ttu-id="b7da5-107">若要修改作業，請按兩下作業以開啟 [作業屬性]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b7da5-107">To modify a job, double-click the job to open the **Job Properties** dialog box.</span></span> <span data-ttu-id="b7da5-108">以滑鼠右鍵按一下方格中的作業，即可開始執行所有作業步驟、於特定作業步驟開始、停用或啟用作業、重新整理作業、刪除作業、檢視作業的記錄或檢視作業的屬性。</span><span class="sxs-lookup"><span data-stu-id="b7da5-108">Right-click a job in the grid to start it running all job steps, start at a particular job step, disable or enable the job, refresh the job, delete the job, view the history of the job, or view the properties of the job.</span></span> <span data-ttu-id="b7da5-109">按一下 [重新整理]\*\*\*\*，以最新資訊更新方格。</span><span class="sxs-lookup"><span data-stu-id="b7da5-109">Click **Refresh** to update the grid with current information.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b7da5-110">選項。</span><span class="sxs-lookup"><span data-stu-id="b7da5-110">Options</span></span>  
 <span data-ttu-id="b7da5-111">**名稱**</span><span class="sxs-lookup"><span data-stu-id="b7da5-111">**Name**</span></span>  
 <span data-ttu-id="b7da5-112">作業的名稱。</span><span class="sxs-lookup"><span data-stu-id="b7da5-112">Name of the job.</span></span>  
  
 <span data-ttu-id="b7da5-113">**已啟用**</span><span class="sxs-lookup"><span data-stu-id="b7da5-113">**Enabled**</span></span>  
 <span data-ttu-id="b7da5-114">不論作業為已啟用 ([是]\*\*\*\*) 或未啟用 ([否]\*\*\*\*)。</span><span class="sxs-lookup"><span data-stu-id="b7da5-114">Whether the job is enabled (**yes**) or not enabled (**no**).</span></span>  
  
 <span data-ttu-id="b7da5-115">**狀態** <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b7da5-115">**Status** <sup>1</sup></span></span>  
 <span data-ttu-id="b7da5-116">作業的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="b7da5-116">Current status of the job.</span></span>  
  
 <span data-ttu-id="b7da5-117">**上次執行結果**</span><span class="sxs-lookup"><span data-stu-id="b7da5-117">**Last Run Outcome**</span></span>  
 <span data-ttu-id="b7da5-118">作業上次執行的狀態。</span><span class="sxs-lookup"><span data-stu-id="b7da5-118">Job status when last run.</span></span>  
  
 <span data-ttu-id="b7da5-119">**最後執行**</span><span class="sxs-lookup"><span data-stu-id="b7da5-119">**Last Run**</span></span>  
 <span data-ttu-id="b7da5-120">上次使用伺服器的當地日期和時間執行作業的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="b7da5-120">Date and time job was last run using the local date and time of the server.</span></span>  
  
 <span data-ttu-id="b7da5-121">**下次執行** <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b7da5-121">**Next Run** <sup>1</sup></span></span>  
 <span data-ttu-id="b7da5-122">下次排程為使用伺服器的當地日期和時間執行作業的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="b7da5-122">Date and time the job is next scheduled to run using the local date and time of the server.</span></span>  
  
 <span data-ttu-id="b7da5-123">**類別**</span><span class="sxs-lookup"><span data-stu-id="b7da5-123">**Category**</span></span>  
 <span data-ttu-id="b7da5-124">指派給作業的作業類別目錄。</span><span class="sxs-lookup"><span data-stu-id="b7da5-124">The job category assigned to the job.</span></span>  
  
 <span data-ttu-id="b7da5-125">**可**</span><span class="sxs-lookup"><span data-stu-id="b7da5-125">**Runnable**</span></span>  
 <span data-ttu-id="b7da5-126">[是]\*\*\*\* 如果作業可執行；[否]\*\*\*\* 如果作業無法執行。</span><span class="sxs-lookup"><span data-stu-id="b7da5-126">**Yes** if the job can be run; **No** if the job cannot be run.</span></span> <span data-ttu-id="b7da5-127">如果作業沒有任何步驟，或者沒有目標伺服器，就無法執行此作業。</span><span class="sxs-lookup"><span data-stu-id="b7da5-127">A job is not runnable if it has no steps or if it has no target server.</span></span>  
  
 <span data-ttu-id="b7da5-128">**排程**</span><span class="sxs-lookup"><span data-stu-id="b7da5-128">**Scheduled**</span></span>  
 <span data-ttu-id="b7da5-129">[是]\*\*\*\* 表示作業已指派給作業排程；[否]\*\*\*\* 表示作業沒有排程。</span><span class="sxs-lookup"><span data-stu-id="b7da5-129">**Yes** if the job is assigned to a job schedule; **No** if the job has no schedule.</span></span>  
  
 <span data-ttu-id="b7da5-130"><sup>1</sup>只有系統管理員（ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sysadmin）固定伺服器角色和伺服器管理員群組的成員，才能夠看到此資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="b7da5-130"><sup>1</sup>Only members of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sysadmin fixed server role and the server administrators group can see values in this column.</span></span> <span data-ttu-id="b7da5-131">SQLAgentOperatorRole 角色的成員無法看到此資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="b7da5-131">Members of the SQLAgentOperatorRole role cannot see values in this column.</span></span>  
  
#### <a name="to-open-the-job-activity-monitor"></a><span data-ttu-id="b7da5-132">若要開啟作業活動監視器</span><span class="sxs-lookup"><span data-stu-id="b7da5-132">To open the Job Activity Monitor</span></span>  
  
-   <span data-ttu-id="b7da5-133">在物件總管\*\*\*\* 中，依序展開伺服器和 [SQL Server Agent]\*\*\*\*、以滑鼠右鍵按一下 [作業活動監視器]\*\*\*\*，然後按一下 [檢視作業活動]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b7da5-133">In **Object Explorer**, expand your server, expand **SQL Server Agent**, right-click **Job Activity Monitor**, and then click **View Job Activity**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7da5-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7da5-134">See Also</span></span>  
 [<span data-ttu-id="b7da5-135">監視作業活動</span><span class="sxs-lookup"><span data-stu-id="b7da5-135">Monitor Job Activity</span></span>](monitor-job-activity.md)  
  
  
