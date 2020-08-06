---
title: 修改與 SQL Server Agent 主要作業相關聯的目標伺服器 () |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 176e73b6-08aa-48ec-b349-e84b431e65cc
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6b7b5ab114366cdafe40b7a70f523fef43eb11d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606572"
---
# <a name="modify-the-target-servers-associated-with-a-sql-server-agent-master-job"></a><span data-ttu-id="eb8b8-102">修改與 SQL Server Agent 主要作業相關聯的目標伺服器</span><span class="sxs-lookup"><span data-stu-id="eb8b8-102">Modify the Target Server(s) Associated with a SQL Server Agent Master Job</span></span>
  <span data-ttu-id="eb8b8-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中修改與 SQL Server Agent 主要作業相關聯的目標伺服器。</span><span class="sxs-lookup"><span data-stu-id="eb8b8-103">This topic describes how to modify the target server(s) associated with a SQL Server Agent master job in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="eb8b8-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="eb8b8-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="eb8b8-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="eb8b8-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="eb8b8-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="eb8b8-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="eb8b8-107">安全性</span><span class="sxs-lookup"><span data-stu-id="eb8b8-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="eb8b8-108">**若要使用下列項目來修改與 SQL Server Agent 主要作業相關聯的目標伺服器：**</span><span class="sxs-lookup"><span data-stu-id="eb8b8-108">**To modify the target server(s) associated with a SQL Server Agent master job, using:**</span></span>  
  
     [<span data-ttu-id="eb8b8-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="eb8b8-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="eb8b8-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="eb8b8-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="eb8b8-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="eb8b8-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="eb8b8-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="eb8b8-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="eb8b8-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 主要作業無法同時存在於本機和遠端伺服器內。</span><span class="sxs-lookup"><span data-stu-id="eb8b8-113">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent master job cannot be targeted at both local and remote servers.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="eb8b8-114">Security</span><span class="sxs-lookup"><span data-stu-id="eb8b8-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="eb8b8-115">權限</span><span class="sxs-lookup"><span data-stu-id="eb8b8-115">Permissions</span></span>  
 <span data-ttu-id="eb8b8-116">除非您是系統管理員 ( **sysadmin** ) 固定伺服器角色的成員，否則您只能修改您所擁有的作業。</span><span class="sxs-lookup"><span data-stu-id="eb8b8-116">Unless you are a member of the **sysadmin** fixed server role, you can only modify jobs that you own.</span></span> <span data-ttu-id="eb8b8-117">如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="eb8b8-117">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="eb8b8-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="eb8b8-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-the-target-servers-associated-with-a-sql-server-agent-master-job"></a><span data-ttu-id="eb8b8-119">若要修改與 SQL Server Agent 主要作業相關聯的目標伺服器</span><span class="sxs-lookup"><span data-stu-id="eb8b8-119">To modify the target server(s) associated with a SQL Server Agent master job</span></span>  
  
1.  <span data-ttu-id="eb8b8-120">在 **[物件總管]** 中，按一下加號，展開包含您想要修改目標伺服器之作業的伺服器。</span><span class="sxs-lookup"><span data-stu-id="eb8b8-120">In **Object Explorer,** click the plus sign to expand the server that contains the job where you want to modify the target server.</span></span>  
  
2.  <span data-ttu-id="eb8b8-121">按一下加號展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="eb8b8-121">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="eb8b8-122">按一下加號展開 **[作業]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="eb8b8-122">Click the plus sign to expand the **Jobs** folder.</span></span>  
  
4.  <span data-ttu-id="eb8b8-123">以滑鼠右鍵按一下您想要修改目標伺服器的作業，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="eb8b8-123">Right-click the job where you want to modify the target server and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="eb8b8-124">在 [**作業屬性-**_job_name_ ] 對話方塊的 [**選取頁面**] 底下，選取 [**目標**]。</span><span class="sxs-lookup"><span data-stu-id="eb8b8-124">In the **Job Properties -**_job_name_ dialog box, under **Select a page**, select **Targets**.</span></span> <span data-ttu-id="eb8b8-125">如需有關此頁面上可用選項的詳細資訊，請參閱[工作屬性：新增作業 &#40;目標頁面&#41;](job-properties-new-job-targets-page.md)。</span><span class="sxs-lookup"><span data-stu-id="eb8b8-125">For more information on the available options on this page, see [Job Properties: New Job &#40;Targets Page&#41;](job-properties-new-job-targets-page.md).</span></span>  
  
6.  <span data-ttu-id="eb8b8-126">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="eb8b8-126">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="eb8b8-127">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="eb8b8-127">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-target-server-currently-associated-with-a-sql-server-agent-master-job"></a><span data-ttu-id="eb8b8-128">若要刪除目前與 SQL Server Agent 主要作業相關聯的目標伺服器</span><span class="sxs-lookup"><span data-stu-id="eb8b8-128">To delete a target server currently associated with a SQL Server Agent master job</span></span>  
  
1.  <span data-ttu-id="eb8b8-129">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="eb8b8-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="eb8b8-130">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="eb8b8-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="eb8b8-131">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="eb8b8-131">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- removes the server SEATTLE2 from processing the Weekly Sales Backupsjob   
    -- assumes that the Weekly Sales Backups job exists  
    USE msdb ;  
    GO  
  
    EXEC sp_delete_jobserver  
        @job_name = N'Weekly Sales Backups',  
        @server_name = N'SEATTLE2' ;  
    GO  
    ```  
  
 <span data-ttu-id="eb8b8-132">如需詳細資訊，請參閱[sp_delete_jobserver &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="eb8b8-132">For more information, see [sp_delete_jobserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql).</span></span>  
  
#### <a name="to-associate-a-target-server-with-the-current-sql-server-agent-master-job"></a><span data-ttu-id="eb8b8-133">若要將目標伺服器與目前的 SQL Server Agent 主要作業產生關聯</span><span class="sxs-lookup"><span data-stu-id="eb8b8-133">To associate a target server with the current SQL Server Agent master job</span></span>  
  
1.  <span data-ttu-id="eb8b8-134">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="eb8b8-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="eb8b8-135">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="eb8b8-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="eb8b8-136">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="eb8b8-136">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- assigns the multiserver job Weekly Sales Backups to the server SEATTLE2   
    -- assumes that the Weekly Sales Backups job already exists and that   
    -- SEATTLE2 is registered as a target server for the current instance  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_jobserver  
        @job_name = N'Weekly Sales Backups',  
        @server_name = N'SEATTLE2' ;  
    GO  
    ```  
  
 <span data-ttu-id="eb8b8-137">如需詳細資訊，請參閱[sp_add_jobserver &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="eb8b8-137">For more information, see [sp_add_jobserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql).</span></span>  
  
  
