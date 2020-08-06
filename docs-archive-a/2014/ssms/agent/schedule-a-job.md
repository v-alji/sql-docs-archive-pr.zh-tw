---
title: 排程作業 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- scheduling jobs [SQL Server]
- SQL Server Agent jobs, scheduling
- jobs [SQL Server Agent], scheduling
ms.assetid: f626390a-a3df-4970-b7a7-a0529e4a109c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1077766d6853ed7c029b8eefa76515c89ad861fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699175"
---
# <a name="schedule-a-job"></a><span data-ttu-id="377ce-102">排定作業執行時間</span><span class="sxs-lookup"><span data-stu-id="377ce-102">Schedule a Job</span></span>
  <span data-ttu-id="377ce-103">本主題描述如何排程 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業。</span><span class="sxs-lookup"><span data-stu-id="377ce-103">This topic describes how to schedule a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span>  
  
-   <span data-ttu-id="377ce-104">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="377ce-104">**Before you begin:** ,</span></span>  
  
     [<span data-ttu-id="377ce-105">安全性</span><span class="sxs-lookup"><span data-stu-id="377ce-105">Security</span></span>](#Security)  
  
-   <span data-ttu-id="377ce-106">**若要使用下列項目排程作業：**</span><span class="sxs-lookup"><span data-stu-id="377ce-106">**To schedule a job, using:**</span></span>  
  
     [<span data-ttu-id="377ce-107">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="377ce-107">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="377ce-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="377ce-108">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="377ce-109">SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="377ce-109">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="377ce-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="377ce-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="377ce-111">Security</span><span class="sxs-lookup"><span data-stu-id="377ce-111">Security</span></span>  
 <span data-ttu-id="377ce-112">如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="377ce-112">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="377ce-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="377ce-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-and-attach-a-schedule-to-a-job"></a><span data-ttu-id="377ce-114">若要建立並附加排程至作業</span><span class="sxs-lookup"><span data-stu-id="377ce-114">To create and attach a schedule to a job</span></span>  
  
1.  <span data-ttu-id="377ce-115">在**物件總管中，** 連接到的實例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然後展開該實例。</span><span class="sxs-lookup"><span data-stu-id="377ce-115">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="377ce-116">依序展開 [SQL Server Agent]\*\*\*\* 和 [作業]\*\*\*\*、以滑鼠右鍵按一下要排程的作業，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="377ce-116">Expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to schedule, and click **Properties**.</span></span>  
  
3.  <span data-ttu-id="377ce-117">按一下 **[排程]** 頁面，然後按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="377ce-117">Select the **Schedules** page, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="377ce-118">在 **[名稱]** 方塊中，輸入新排程的名稱。</span><span class="sxs-lookup"><span data-stu-id="377ce-118">In the **Name** box, type a name for the new schedule.</span></span>  
  
5.  <span data-ttu-id="377ce-119">如果您不要排程在建立後立即生效，請清除 **[啟用]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="377ce-119">Clear the **Enabled** check box if you do not want the schedule to take effect immediately following its creation.</span></span>  
  
6.  <span data-ttu-id="377ce-120">針對 **[排程類型]**，選取下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="377ce-120">For **Schedule Type**, select one of the following:</span></span>  
  
    -   <span data-ttu-id="377ce-121">按一下 **[當 SQL Server Agent 啟動時自動啟動]** ，以在啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務時啟動作業。</span><span class="sxs-lookup"><span data-stu-id="377ce-121">Click **Start automatically when SQL Server Agent starts** to start the job when the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service is started.</span></span>  
  
    -   <span data-ttu-id="377ce-122">按一下 **[只要 CPU 閒置就啟動]** ，以便在 CPU 到達閒置條件時啟動作業。</span><span class="sxs-lookup"><span data-stu-id="377ce-122">Click **Start whenever the CPUs become idle** to start the job when the CPUs reach an idle condition.</span></span>  
  
    -   <span data-ttu-id="377ce-123">如果您想要重複執行排程，請按一下 **[重複執行]** 。</span><span class="sxs-lookup"><span data-stu-id="377ce-123">Click **Recurring** if you want a schedule to run repeatedly.</span></span> <span data-ttu-id="377ce-124">若要設定重複執行的排程，請完成對話方塊上的 **[頻率]**、 **[每日頻率]** 和 **[持續時間]** 群組。</span><span class="sxs-lookup"><span data-stu-id="377ce-124">To set the recurring schedule, complete the **Frequency**, **Daily Frequency**, and **Duration** groups on the dialog.</span></span>  
  
    -   <span data-ttu-id="377ce-125">如果您只要排程執行一次，請按一下 **[執行一次]** 。</span><span class="sxs-lookup"><span data-stu-id="377ce-125">Click **One time** if you want the schedule to run only once.</span></span> <span data-ttu-id="377ce-126">若要設定 [執行一次]\*\*\*\* 排程，請完成對話方塊上的 [僅執行一次]\*\*\*\* 群組。</span><span class="sxs-lookup"><span data-stu-id="377ce-126">To set the **One time** schedule, complete the **One-time occurrence** group on the dialog.</span></span>  
  
#### <a name="to-attach-a-schedule-to-a-job"></a><span data-ttu-id="377ce-127">附加排程至作業</span><span class="sxs-lookup"><span data-stu-id="377ce-127">To attach a schedule to a job</span></span>  
  
1.  <span data-ttu-id="377ce-128">在**物件總管中，** 連接到的實例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然後展開該實例。</span><span class="sxs-lookup"><span data-stu-id="377ce-128">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="377ce-129">依序展開 [SQL Server Agent]\*\*\*\* 和 [作業]\*\*\*\*、以滑鼠右鍵按一下要排程的作業，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="377ce-129">Expand **SQL Server Agent**, expand **Jobs**, right-click the job that you want to schedule, and click **Properties**.</span></span>  
  
3.  <span data-ttu-id="377ce-130">選取 **[排程]** 頁面，然後按一下 **[挑選]**。</span><span class="sxs-lookup"><span data-stu-id="377ce-130">Select the **Schedules** page, and then click **Pick**.</span></span>  
  
4.  <span data-ttu-id="377ce-131">選取您想要附加的排程，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="377ce-131">Select the schedule that you want to attach, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="377ce-132">在 [作業屬性]\*\*\*\* 對話方塊中，按兩下附加的排程。</span><span class="sxs-lookup"><span data-stu-id="377ce-132">In the **Job Properties** dialog box, double-click the attached schedule.</span></span>  
  
6.  <span data-ttu-id="377ce-133">確認 **[開始日期]** 的設定是否正確。</span><span class="sxs-lookup"><span data-stu-id="377ce-133">Verify that **Start date** is set correctly.</span></span> <span data-ttu-id="377ce-134">如果不正確，請設定您想要讓排程啟動的日期，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="377ce-134">If it is not, set the date when you want for the schedule to start, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="377ce-135">在 **[作業屬性]** 對話方塊中，按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="377ce-135">In the **Job Properties** dialog box, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="377ce-136">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="377ce-136">Using Transact-SQL</span></span>  
  
#### <a name="to-schedule-a-job"></a><span data-ttu-id="377ce-137">排程作業</span><span class="sxs-lookup"><span data-stu-id="377ce-137">To schedule a job</span></span>  
  
1.  <span data-ttu-id="377ce-138">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="377ce-138">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="377ce-139">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="377ce-139">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="377ce-140">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="377ce-140">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    USE msdb ;  
    GO  
    -- creates a schedule named NightlyJobs.   
    -- Jobs that use this schedule execute every day when the time on the server is 01:00.   
    EXEC sp_add_schedule  
        @schedule_name = N'NightlyJobs' ,  
        @freq_type = 4,  
        @freq_interval = 1,  
        @active_start_time = 010000 ;  
    GO  
    -- attaches the schedule to the job BackupDatabase  
    EXEC sp_attach_schedule  
       @job_name = N'BackupDatabase',  
       @schedule_name = N'NightlyJobs' ;  
    GO  
    ```  
  
 <span data-ttu-id="377ce-141">如需詳細資訊，請參閱[sp_add_schedule &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql)和[sp_attach_schedule &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="377ce-141">For more information, see [sp_add_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql) and [sp_attach_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="377ce-142">使用 SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="377ce-142">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="377ce-143">透過所選的程式語言，例如 Visual Basic、Visual C# 或 PowerShell，使用 `JobSchedule` 類別。</span><span class="sxs-lookup"><span data-stu-id="377ce-143">Use the `JobSchedule` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="377ce-144">如需詳細資訊，請參閱[SQL Server 管理物件 (SMO)](https://msdn.microsoft.com/library/ms162169.aspx)。</span><span class="sxs-lookup"><span data-stu-id="377ce-144">For more information, see[SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
