---
title: 建立作業 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], creating
- SQL Server Agent jobs, creating
ms.assetid: b35af2b6-6594-40d1-9861-4d5dd906048c
author: stevestein
ms.author: sstein
ms.openlocfilehash: de74f032924fbb0b6643bd8f3d482481ffb1f983
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584966"
---
# <a name="create-a-job"></a><span data-ttu-id="fd03b-102">建立作業</span><span class="sxs-lookup"><span data-stu-id="fd03b-102">Create a Job</span></span>
  <span data-ttu-id="fd03b-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 SQL Server 管理物件 (SMO)，在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中建立 SQL Server Agent 作業。</span><span class="sxs-lookup"><span data-stu-id="fd03b-103">This topic describes how to create a SQL Server Agent job in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects (SMO).</span></span>  
  
 <span data-ttu-id="fd03b-104">若要加入作業步驟、排程、警示以及可傳送給操作員的通知，請參閱＜請參閱＞一節中的主題連結。</span><span class="sxs-lookup"><span data-stu-id="fd03b-104">To add job steps, schedules, alerts, and notifications that can be sent to operators, see the links to topics in the See Also section.</span></span>  
  
-   <span data-ttu-id="fd03b-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="fd03b-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="fd03b-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="fd03b-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="fd03b-107">安全性</span><span class="sxs-lookup"><span data-stu-id="fd03b-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="fd03b-108">**若要使用下列項目建立作業：**</span><span class="sxs-lookup"><span data-stu-id="fd03b-108">**To create a job, using:**</span></span>  
  
     <span data-ttu-id="fd03b-109">[SQL Server Management Studio](#SSMSProcedure)、</span><span class="sxs-lookup"><span data-stu-id="fd03b-109">[SQL Server Management Studio](#SSMSProcedure),</span></span>  
  
     [<span data-ttu-id="fd03b-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fd03b-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="fd03b-111">SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="fd03b-111">SQL Server Management Objects</span></span>](#SMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="fd03b-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="fd03b-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="fd03b-113">限制事項</span><span class="sxs-lookup"><span data-stu-id="fd03b-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="fd03b-114">若要建立作業，使用者必須是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 固定資料庫角色或 **系統管理員 (sysadmin)** 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="fd03b-114">To create a job, a user must be a member of one of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles or the **sysadmin** fixed server role.</span></span> <span data-ttu-id="fd03b-115">只有作業擁有者或隸屬 **sysadmin** 角色的成員可以編輯作業。</span><span class="sxs-lookup"><span data-stu-id="fd03b-115">A job can be edited only by its owner or members of the **sysadmin** role.</span></span> <span data-ttu-id="fd03b-116">如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 固定資料庫角色的詳細資訊，請參閱 [SQL Server Agent 固定資料庫角色](sql-server-agent-fixed-database-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="fd03b-116">For more information about the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles, see [SQL Server Agent Fixed Database Roles](sql-server-agent-fixed-database-roles.md).</span></span>  
  
-   <span data-ttu-id="fd03b-117">將作業指派給另一個登入並不保證新的擁有者具有充分之使用權限能夠成功執行作業。</span><span class="sxs-lookup"><span data-stu-id="fd03b-117">Assigning a job to another login does not guarantee that the new owner has sufficient permission to run the job successfully.</span></span>  
  
-   <span data-ttu-id="fd03b-118">本機作業會由本機的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 快取。</span><span class="sxs-lookup"><span data-stu-id="fd03b-118">Local jobs are cached by the local [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="fd03b-119">因此，任何修改會隱含地強制 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 重新快取作業。</span><span class="sxs-lookup"><span data-stu-id="fd03b-119">Therefore, any modifications implicitly force [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to re-cache the job.</span></span> <span data-ttu-id="fd03b-120">因為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 會等到呼叫 **sp_add_jobserver** 時才快取作業，所以最後再呼叫 **sp_add_jobserver** 會更有效率。</span><span class="sxs-lookup"><span data-stu-id="fd03b-120">Because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent does not cache the job until **sp_add_jobserver** is called, it is more efficient to call **sp_add_jobserver** last.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="fd03b-121">Security</span><span class="sxs-lookup"><span data-stu-id="fd03b-121">Security</span></span>  
  
-   <span data-ttu-id="fd03b-122">您必須是系統管理員，才能夠變更作業的擁有者。</span><span class="sxs-lookup"><span data-stu-id="fd03b-122">You must be a system administrator to change the owner of a job.</span></span>  
  
-   <span data-ttu-id="fd03b-123">基於安全考量，只有作業擁有者或隸屬 **sysadmin** 角色的成員可以變更作業的定義。</span><span class="sxs-lookup"><span data-stu-id="fd03b-123">For security reasons, only the job owner or a member of the **sysadmin** role can change the definition of the job.</span></span> <span data-ttu-id="fd03b-124">只有 **sysadmin** (系統管理員) 固定伺服器角色的成員可以將作業擁有權指定給其他使用者，而且無論作業擁有者是誰，都可以執行任何作業。</span><span class="sxs-lookup"><span data-stu-id="fd03b-124">Only members of the **sysadmin** fixed server role can assign job ownership to other users, and they can run any job, regardless of the job owner.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fd03b-125">如果將作業擁有權變更給非 **系統管理員 (sysadmin)** 固定伺服器角色成員的使用者，而且作業正在執行要求 Proxy 帳戶的作業步驟 (例如， [!INCLUDE[ssIS](../../includes/ssis-md.md)] 套件執行)，請確定使用者擁有該 Proxy 帳戶的存取權，否則作業將會失敗。</span><span class="sxs-lookup"><span data-stu-id="fd03b-125">If you change job ownership to a user who is not a member of the **sysadmin** fixed server role, and the job is executing job steps that require proxy accounts (for example, [!INCLUDE[ssIS](../../includes/ssis-md.md)] package execution), make sure that the user has access to that proxy account or else the job will fail.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="fd03b-126">權限</span><span class="sxs-lookup"><span data-stu-id="fd03b-126">Permissions</span></span>  
 <span data-ttu-id="fd03b-127">如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="fd03b-127">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="fd03b-128">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fd03b-128">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-sql-server-agent-job"></a><span data-ttu-id="fd03b-129">若要建立 SQL Server Agent 作業</span><span class="sxs-lookup"><span data-stu-id="fd03b-129">To create a SQL Server Agent job</span></span>  
  
1.  <span data-ttu-id="fd03b-130">在 **[物件總管]** 中，按一下加號展開要建立 SQL Server Agent 作業的伺服器。</span><span class="sxs-lookup"><span data-stu-id="fd03b-130">In the **Object Explorer**, click the plus sign to expand the server where you want to create a SQL Server Agent job.</span></span>  
  
2.  <span data-ttu-id="fd03b-131">按一下加號展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="fd03b-131">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="fd03b-132">以滑鼠右鍵按一下 [作業]\*\*\*\* 資料夾，然後選取 [新增作業...]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fd03b-132">Right-click the **Jobs** folder and select **New Job...**.</span></span>  
  
4.  <span data-ttu-id="fd03b-133">在 **[新增作業]** 對話方塊的 **[一般]** 頁面中，修改作業的一般屬性。</span><span class="sxs-lookup"><span data-stu-id="fd03b-133">In the **New Job** dialog box, on the **General** page, modify the general properties of the job.</span></span> <span data-ttu-id="fd03b-134">如需有關此頁面上可用選項的詳細資訊，請參閱[作業屬性和新增作業 &#40;一般頁面&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)</span><span class="sxs-lookup"><span data-stu-id="fd03b-134">For more information on the available options on this page, see [Job Properties and New Job &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)</span></span>  
  
5.  <span data-ttu-id="fd03b-135">在 **[步驟]** 頁面上，組織作業步驟。</span><span class="sxs-lookup"><span data-stu-id="fd03b-135">On the **Steps** page, organize the job steps.</span></span> <span data-ttu-id="fd03b-136">如需有關此頁面上可用選項的詳細資訊，請參閱[作業屬性：新增作業 &#40;步驟頁面&#41;](job-properties-new-job-steps-page.md)</span><span class="sxs-lookup"><span data-stu-id="fd03b-136">For more information on the available options on this page, see [Job Properties:New Job &#40;Steps Page&#41;](job-properties-new-job-steps-page.md)</span></span>  
  
6.  <span data-ttu-id="fd03b-137">在 **[排程]** 頁面上，組織作業的排程。</span><span class="sxs-lookup"><span data-stu-id="fd03b-137">On the **Schedules** page, organize schedules for the job.</span></span> <span data-ttu-id="fd03b-138">如需有關此頁面上可用選項的詳細資訊，請參閱[作業屬性：新增作業 &#40;排程頁面&#41;](job-properties-new-job-schedules-page.md)</span><span class="sxs-lookup"><span data-stu-id="fd03b-138">For more information on the available options on this page, see [Job Properties: New Job &#40;Schedules Page&#41;](job-properties-new-job-schedules-page.md)</span></span>  
  
7.  <span data-ttu-id="fd03b-139">在 **[警示]** 頁面上，組織作業的警示。</span><span class="sxs-lookup"><span data-stu-id="fd03b-139">On the **Alerts** page, organize the alerts for the job.</span></span> <span data-ttu-id="fd03b-140">如需有關此頁面上可用選項的詳細資訊，請參閱[作業屬性：新增作業 &#40;警示頁面&#41;](job-properties-new-job-alerts-page.md)</span><span class="sxs-lookup"><span data-stu-id="fd03b-140">For more information on the available options on this page, see [Job Properties: New Job &#40;Alerts Page&#41;](job-properties-new-job-alerts-page.md)</span></span>  
  
8.  <span data-ttu-id="fd03b-141">在 [通知]\*\*\*\* 頁面上設定當作業完成時，[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 要執行的動作。</span><span class="sxs-lookup"><span data-stu-id="fd03b-141">On the **Notifications** page, set actions for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to perform when the job completes.</span></span> <span data-ttu-id="fd03b-142">如需有關此頁面上可用選項的詳細資訊，請參閱[作業屬性：新增作業 &#40;通知頁面&#41;](job-properties-new-job-notifications-page.md)。</span><span class="sxs-lookup"><span data-stu-id="fd03b-142">For more information on the available options on this page, see [Job Properties: New Job &#40;Notifications Page&#41;](job-properties-new-job-notifications-page.md).</span></span>  
  
9. <span data-ttu-id="fd03b-143">在 **[目標]** 頁面上，管理作業的目標伺服器。</span><span class="sxs-lookup"><span data-stu-id="fd03b-143">On the **Targets** page, manage the target servers for the job.</span></span> <span data-ttu-id="fd03b-144">如需有關此頁面上可用選項的詳細資訊，請參閱[工作屬性：新增作業 &#40;目標頁面&#41;](job-properties-new-job-targets-page.md)。</span><span class="sxs-lookup"><span data-stu-id="fd03b-144">For more information on the available options on this page, see [Job Properties: New Job &#40;Targets Page&#41;](job-properties-new-job-targets-page.md).</span></span>  
  
10. <span data-ttu-id="fd03b-145">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="fd03b-145">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="fd03b-146">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fd03b-146">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-sql-server-agent-job"></a><span data-ttu-id="fd03b-147">若要建立 SQL Server Agent 作業</span><span class="sxs-lookup"><span data-stu-id="fd03b-147">To create a SQL Server Agent job</span></span>  
  
1.  <span data-ttu-id="fd03b-148">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="fd03b-148">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="fd03b-149">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="fd03b-149">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="fd03b-150">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="fd03b-150">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    USE msdb ;  
    GO  
    EXEC dbo.sp_add_job  
        @job_name = N'Weekly Sales Data Backup' ;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'TSQL',  
        @command = N'ALTER DATABASE SALES SET READ_ONLY',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    EXEC dbo.sp_add_schedule  
        @schedule_name = N'RunOnce',  
        @freq_type = 1,  
        @active_start_time = 233000 ;  
    USE msdb ;  
    GO  
    EXEC sp_attach_schedule  
       @job_name = N'Weekly Sales Data Backup',  
       @schedule_name = N'RunOnce';  
    GO  
    EXEC dbo.sp_add_jobserver  
        @job_name = N'Weekly Sales Data Backup';  
    GO  
    ```  
  
 <span data-ttu-id="fd03b-151">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="fd03b-151">For more information, see:</span></span>  
  
-   [<span data-ttu-id="fd03b-152">sp_add_job &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fd03b-152">sp_add_job &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql)  
  
-   [<span data-ttu-id="fd03b-153">sp_add_jobstep &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fd03b-153">sp_add_jobstep &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)  
  
-   [<span data-ttu-id="fd03b-154">sp_add_schedule &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fd03b-154">sp_add_schedule &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql)  
  
-   [<span data-ttu-id="fd03b-155">sp_attach_schedule &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fd03b-155">sp_attach_schedule &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql)  
  
-   [<span data-ttu-id="fd03b-156">sp_add_jobserver &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="fd03b-156">sp_add_jobserver &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql)  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMOProcedure"></a><span data-ttu-id="fd03b-157">使用 SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="fd03b-157">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="fd03b-158">**若要建立 SQL Server Agent 作業**</span><span class="sxs-lookup"><span data-stu-id="fd03b-158">**To create a SQL Server Agent job**</span></span>  
  
 <span data-ttu-id="fd03b-159">使用所選的程式語言，例如 Visual Basic、Visual C# 或 PowerShell，呼叫 `Create` 類別的 `Job` 方法。</span><span class="sxs-lookup"><span data-stu-id="fd03b-159">Call the `Create` method of the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="fd03b-160">如需範例程式碼，請參閱 [使用 SQL Server Agent 排程自動管理工作](sql-server-agent.md)。</span><span class="sxs-lookup"><span data-stu-id="fd03b-160">For example code, see [Scheduling Automatic Administrative Tasks in SQL Server Agent](sql-server-agent.md).</span></span>  
  
##  <a name="SSMSProc2"></a>  
