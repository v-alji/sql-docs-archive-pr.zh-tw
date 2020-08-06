---
title: 建立維護計畫 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- maintenance plans [SQL Server], creating
ms.assetid: a945cb65-ba7a-42f4-bbd9-6ec675745523
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3df0c1cd06427deb051a9c4214d03084b44c6f9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598362"
---
# <a name="create-a-maintenance-plan"></a><span data-ttu-id="ad880-102">建立維護計畫</span><span class="sxs-lookup"><span data-stu-id="ad880-102">Create a Maintenance Plan</span></span>
  <span data-ttu-id="ad880-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中建立單一伺服器或多伺服器維護計畫。</span><span class="sxs-lookup"><span data-stu-id="ad880-103">This topic describes how to create a single server or multiserver maintenance plan in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="ad880-104">您可以使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]透過兩種方式的其中一種建立這些維護計畫：使用「維護計畫精靈」或設計介面。</span><span class="sxs-lookup"><span data-stu-id="ad880-104">Using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], you can create these maintenance plans in one of two ways: by either using the Maintenance Plan Wizard or the design surface.</span></span> <span data-ttu-id="ad880-105">本精靈最適用於建立基本的維護計畫，使用設計介面建立計畫時可讓您利用加強的工作流程。</span><span class="sxs-lookup"><span data-stu-id="ad880-105">The Wizard is best for creating basic maintenance plans, while creating a plan using the design surface allows you to utilize enhanced workflow.</span></span>  
  
 <span data-ttu-id="ad880-106">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="ad880-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ad880-107">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="ad880-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ad880-108">限制事項</span><span class="sxs-lookup"><span data-stu-id="ad880-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="ad880-109">安全性</span><span class="sxs-lookup"><span data-stu-id="ad880-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ad880-110">**使用下列方法建立維護計畫：**</span><span class="sxs-lookup"><span data-stu-id="ad880-110">**To create a maintenance plan, using:**</span></span>  
  
     [<span data-ttu-id="ad880-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ad880-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ad880-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ad880-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ad880-113">開始之前</span><span class="sxs-lookup"><span data-stu-id="ad880-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="ad880-114">限制事項</span><span class="sxs-lookup"><span data-stu-id="ad880-114">Limitations and Restrictions</span></span>  
 <span data-ttu-id="ad880-115">若要建立多伺服器維護計畫，必須設定多伺服器環境，其中包含一個主要伺服器以及一或多個目標伺服器。</span><span class="sxs-lookup"><span data-stu-id="ad880-115">To create a multiserver maintenance plan, a multiserver environment containing one master server and one or more target servers must be configured.</span></span> <span data-ttu-id="ad880-116">多伺服器維護計畫必須在主要伺服器上建立和維護。</span><span class="sxs-lookup"><span data-stu-id="ad880-116">Multiserver maintenance plans must be created and maintained on the master server.</span></span> <span data-ttu-id="ad880-117">您可以在目標伺服器上檢視這些計畫，但不能加以維護。</span><span class="sxs-lookup"><span data-stu-id="ad880-117">These plans can be viewed, but not maintained, on target servers.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ad880-118">Security</span><span class="sxs-lookup"><span data-stu-id="ad880-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ad880-119">權限</span><span class="sxs-lookup"><span data-stu-id="ad880-119">Permissions</span></span>  
 <span data-ttu-id="ad880-120">若要建立或管理維護計畫，您必須是 **系統管理員 (sysadmin)** 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="ad880-120">To create or manage Maintenance Plans, you must be a member of the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ad880-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ad880-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-maintenance-plan-using-the-maintenance-plan-wizard"></a><span data-ttu-id="ad880-122">若要使用維護計畫精靈來建立維護計畫</span><span class="sxs-lookup"><span data-stu-id="ad880-122">To create a maintenance plan using the Maintenance Plan Wizard</span></span>  
  
1.  <span data-ttu-id="ad880-123">在 [物件總管] 中，按一下加號以展開您要建立維護計畫的伺服器。</span><span class="sxs-lookup"><span data-stu-id="ad880-123">In Object Explorer, click the plus sign to expand the server where you want to create a maintenance plan.</span></span>  
  
2.  <span data-ttu-id="ad880-124">按一下加號展開 **[管理]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ad880-124">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="ad880-125">以滑鼠右鍵按一下 [維護計畫] 資料夾，然後選取 [維護計畫精靈]。</span><span class="sxs-lookup"><span data-stu-id="ad880-125">Right-click the **Maintenance Plans** folder and select **Maintenance Plan Wizard**.</span></span>  
  
4.  <span data-ttu-id="ad880-126">請遵循精靈的步驟來建立維護計畫。</span><span class="sxs-lookup"><span data-stu-id="ad880-126">Follow the steps of the wizard to create a maintenance plan.</span></span> <span data-ttu-id="ad880-127">如需詳細資訊，請參閱 [Use the Maintenance Plan Wizard](use-the-maintenance-plan-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="ad880-127">For more information, see [Use the Maintenance Plan Wizard](use-the-maintenance-plan-wizard.md).</span></span>  
  
#### <a name="to-create-a-maintenance-plan-using-the-design-surface"></a><span data-ttu-id="ad880-128">使用設計介面建立維護計畫</span><span class="sxs-lookup"><span data-stu-id="ad880-128">To create a maintenance plan using the design surface</span></span>  
  
1.  <span data-ttu-id="ad880-129">在 [物件總管] 中，按一下加號以展開您要建立維護計畫的伺服器。</span><span class="sxs-lookup"><span data-stu-id="ad880-129">In Object Explorer, click the plus sign to expand the server where you want to create a maintenance plan.</span></span>  
  
2.  <span data-ttu-id="ad880-130">按一下加號展開 **[管理]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ad880-130">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="ad880-131">以滑鼠右鍵按一下 [維護計畫] 資料夾，然後選取 [新增維護計畫]。</span><span class="sxs-lookup"><span data-stu-id="ad880-131">Right-click the **Maintenance Plans** folder and select **New Maintenance Plan**.</span></span>  
  
4.  <span data-ttu-id="ad880-132">遵循[建立維護計畫 &#40;維護計畫設計介面&#41;](create-a-maintenance-plan-maintenance-plan-design-surface.md) 中的步驟建立維護計畫。</span><span class="sxs-lookup"><span data-stu-id="ad880-132">Create a maintenance plan following the steps in [Create a Maintenance Plan &#40;Maintenance Plan Design Surface&#41;](create-a-maintenance-plan-maintenance-plan-design-surface.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ad880-133">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ad880-133">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-maintenance-plan"></a><span data-ttu-id="ad880-134">若要建立維護計畫</span><span class="sxs-lookup"><span data-stu-id="ad880-134">To create a maintenance plan</span></span>  
  
1.  <span data-ttu-id="ad880-135">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ad880-135">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ad880-136">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="ad880-136">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ad880-137">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="ad880-137">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE msdb;  
    GO  
    --  Adds a new job, executed by the SQL Server Agent service, called "HistoryCleanupTask_1".  
    EXEC dbo.sp_add_job  
       @job_name = N'HistoryCleanupTask_1',   
       @enabled = 1,   
       @description = N'Clean up old task history' ;   
    GO  
    -- Adds a job step for reorganizing all of the indexes in the HumanResources.Employee table to the HistoryCleanupTask_1 job.   
    EXEC dbo.sp_add_jobstep  
        @job_name = N'HistoryCleanupTask_1',   
        @step_name = N'Reorganize all indexes on HumanResources.Employee table',   
        @subsystem = N'TSQL',   
        @command = N'USE AdventureWorks2012  
    GO  
    ALTER INDEX AK_Employee_LoginID ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX AK_Employee_NationalIDNumber ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX AK_Employee_rowguid ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX IX_Employee_OrganizationLevel_OrganizationNode ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX IX_Employee_OrganizationNode ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX PK_Employee_BusinessEntityID ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    ',   
        @retry_attempts = 5,   
        @retry_interval = 5 ;   
    GO  
    -- Creates a schedule named RunOnce that executes every day when the time on the server is 23:00.   
    EXEC dbo.sp_add_schedule  
        @schedule_name = N'RunOnce',   
        @freq_type = 4,   
        @freq_interval = 1,   
        @active_start_time = 233000 ;   
    GO  
    -- Attaches the RunOnce schedule to the job HistoryCleanupTask_1.   
    EXEC sp_attach_schedule  
       @job_name = N'HistoryCleanupTask_1'  
       @schedule_name = N'RunOnce' ;   
    GO  
  
    ```  
  
 <span data-ttu-id="ad880-138">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="ad880-138">For more information, see:</span></span>  
  
-   [<span data-ttu-id="ad880-139">sp_add_job &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ad880-139">sp_add_job &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql)  
  
-   [<span data-ttu-id="ad880-140">sp_add_jobstep &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ad880-140">sp_add_jobstep &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)  
  
-   [<span data-ttu-id="ad880-141">sp_add_schedule &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ad880-141">sp_add_schedule &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql)  
  
-   [<span data-ttu-id="ad880-142">sp_attach_schedule &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ad880-142">sp_attach_schedule &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql)  
  
  
