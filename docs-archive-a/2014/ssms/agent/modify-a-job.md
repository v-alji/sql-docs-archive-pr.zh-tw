---
title: 修改作業 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], modifying
- modifying jobs
- SQL Server Agent jobs, modifying
ms.assetid: dd5e5f20-20c4-4ab9-a19a-db87577dcd43
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0d25830ad119a1f5f344a4dcf318c35bee5f86ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594348"
---
# <a name="modify-a-job"></a><span data-ttu-id="ed7fa-102">Modify a Job</span><span class="sxs-lookup"><span data-stu-id="ed7fa-102">Modify a Job</span></span>
  <span data-ttu-id="ed7fa-103">本主題描述如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 、或 SQL Server 管理物件，在中變更 Agent 作業的屬性 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ed7fa-103">This topic describes how to change the properties of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="ed7fa-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="ed7fa-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ed7fa-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="ed7fa-105">**Before you begin:** ,</span></span>  
  
     [<span data-ttu-id="ed7fa-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="ed7fa-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="ed7fa-107">安全性</span><span class="sxs-lookup"><span data-stu-id="ed7fa-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ed7fa-108">**若要使用下列項目修改作業：**</span><span class="sxs-lookup"><span data-stu-id="ed7fa-108">**To modify a job, using:**</span></span>  
  
     [<span data-ttu-id="ed7fa-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ed7fa-109">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="ed7fa-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ed7fa-110">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="ed7fa-111">SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="ed7fa-111">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ed7fa-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="ed7fa-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="ed7fa-113">限制事項</span><span class="sxs-lookup"><span data-stu-id="ed7fa-113">Limitations and Restrictions</span></span>  
 <span data-ttu-id="ed7fa-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 主要作業無法同時存在於本機和遠端伺服器內。</span><span class="sxs-lookup"><span data-stu-id="ed7fa-114">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent master job cannot be targeted at both local and remote servers.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ed7fa-115">Security</span><span class="sxs-lookup"><span data-stu-id="ed7fa-115">Security</span></span>  
 <span data-ttu-id="ed7fa-116">除非您是系統管理員 ( **sysadmin** ) 固定伺服器角色的成員，否則您只能修改您所擁有的作業。</span><span class="sxs-lookup"><span data-stu-id="ed7fa-116">Unless you are a member of the **sysadmin** fixed server role, you can only modify jobs that you own.</span></span> <span data-ttu-id="ed7fa-117">如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="ed7fa-117">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="ed7fa-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ed7fa-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-job"></a><span data-ttu-id="ed7fa-119">若要修改作業</span><span class="sxs-lookup"><span data-stu-id="ed7fa-119">To modify a job</span></span>  
  
1.  <span data-ttu-id="ed7fa-120">在**物件總管中，** 連接到的實例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然後展開該實例。</span><span class="sxs-lookup"><span data-stu-id="ed7fa-120">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="ed7fa-121">展開 [SQL Server Agent]\*\*\*\*，展開 [作業]\*\*\*\*，以滑鼠右鍵按一下要修改的作業，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ed7fa-121">Expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to modify, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="ed7fa-122">在 **[作業屬性]** 對話方塊中，利用相對應的頁面更新作業的屬性、步驟、排程、警示及通知。</span><span class="sxs-lookup"><span data-stu-id="ed7fa-122">In the **Job Properties** dialog box, update the job's properties, steps, schedule, alerts, and notifications using the corresponding pages.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="ed7fa-123">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ed7fa-123">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-a-job"></a><span data-ttu-id="ed7fa-124">若要修改作業</span><span class="sxs-lookup"><span data-stu-id="ed7fa-124">To modify a job</span></span>  
  
1.  <span data-ttu-id="ed7fa-125">在 [物件總管] 中，連接到 Database Engine 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="ed7fa-125">In Object Explorer, connect to an instance of the Database Engine, and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="ed7fa-126">在工具列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="ed7fa-126">On the toolbar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ed7fa-127">在查詢視窗中，使用下列系統預存程序修改作業。</span><span class="sxs-lookup"><span data-stu-id="ed7fa-127">In the query window, use the following system stored procedures to modify a job.</span></span>  
  
    -   <span data-ttu-id="ed7fa-128">執行[sp_update_job &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql)來變更作業的屬性。</span><span class="sxs-lookup"><span data-stu-id="ed7fa-128">Execute [sp_update_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql) to change the attributes of a job.</span></span>  
  
    -   <span data-ttu-id="ed7fa-129">執行[sp_update_schedule &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-schedule-transact-sql)來變更作業定義的排程詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ed7fa-129">Execute [sp_update_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-schedule-transact-sql) to change the scheduling details for a job definition.</span></span>  
  
    -   <span data-ttu-id="ed7fa-130">執行[sp_add_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)以加入新的作業步驟。</span><span class="sxs-lookup"><span data-stu-id="ed7fa-130">Execute [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql) to add new job steps.</span></span>  
  
    -   <span data-ttu-id="ed7fa-131">執行[sp_update_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql)來變更既有的作業步驟。</span><span class="sxs-lookup"><span data-stu-id="ed7fa-131">Execute [sp_update_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql) to change pre-existing job steps.</span></span>  
  
    -   <span data-ttu-id="ed7fa-132">執行[sp_delete_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql)從作業移除作業步驟。</span><span class="sxs-lookup"><span data-stu-id="ed7fa-132">Execute [sp_delete_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql) to remove a job step from a job.</span></span>  
  
    -   <span data-ttu-id="ed7fa-133">修改任何 SQL Server Agent 主要作業的其他預存程序：</span><span class="sxs-lookup"><span data-stu-id="ed7fa-133">Additional stored procedures to modify any SQL Server Agent master job:</span></span>  
  
        -   <span data-ttu-id="ed7fa-134">執行[sp_delete_jobserver &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql)刪除目前與作業相關聯的伺服器。</span><span class="sxs-lookup"><span data-stu-id="ed7fa-134">Execute [sp_delete_jobserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql) to delete a server currently associated with a job.</span></span>  
  
        -   <span data-ttu-id="ed7fa-135">執行[sp_add_jobserver &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql) ，讓伺服器與目前的作業產生關聯。</span><span class="sxs-lookup"><span data-stu-id="ed7fa-135">Execute [sp_add_jobserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql) to associate a server with the current job.</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="ed7fa-136">使用 SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="ed7fa-136">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="ed7fa-137">**若要修改作業**</span><span class="sxs-lookup"><span data-stu-id="ed7fa-137">**To modify a job**</span></span>  
  
 <span data-ttu-id="ed7fa-138">透過所選的程式語言，例如 Visual Basic、Visual C# 或 PowerShell，使用 `Job` 類別。</span><span class="sxs-lookup"><span data-stu-id="ed7fa-138">Use the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="ed7fa-139">如需詳細資訊，請參閱 [SQL Server 管理物件 (SMO)](https://msdn.microsoft.com/library/ms162169.aspx)。</span><span class="sxs-lookup"><span data-stu-id="ed7fa-139">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
  
  
