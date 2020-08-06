---
title: 將作業擁有權授與其他人 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], owners
- owners [SQL Server], jobs
- SQL Server Agent jobs, owners
ms.assetid: 2ded5e9c-4251-4fb1-a047-99f13d150b61
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2cf03fdc9031ce9761125d95619438837f2959bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584954"
---
# <a name="give-others-ownership-of-a-job"></a><span data-ttu-id="22e49-102">將作業擁有權授與其他人</span><span class="sxs-lookup"><span data-stu-id="22e49-102">Give Others Ownership of a Job</span></span>
  <span data-ttu-id="22e49-103">本主題描述如何將 Agent 作業的擁有權重新指派 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 給另一位使用者。</span><span class="sxs-lookup"><span data-stu-id="22e49-103">This topic describes how to reassign ownership of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs to another user.</span></span>  
  
-   <span data-ttu-id="22e49-104">**開始之前：** [限制事項](#Restrictions)、[安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="22e49-104">**Before you begin:**  [Limitations and Restrictions](#Restrictions), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="22e49-105">**若要使用下列項目賦予作業擁有權給其他人：**</span><span class="sxs-lookup"><span data-stu-id="22e49-105">**To give others ownership of a job, using:**</span></span>  
  
     [<span data-ttu-id="22e49-106">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="22e49-106">SQL Server Management Studio</span></span>](#SSMSProc2)  
  
     [<span data-ttu-id="22e49-107">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="22e49-107">Transact-SQL</span></span>](#TsqlProc2)  
  
     [<span data-ttu-id="22e49-108">SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="22e49-108">SQL Server Management Objects</span></span>](#SMOProc2)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="22e49-109">開始之前</span><span class="sxs-lookup"><span data-stu-id="22e49-109">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="22e49-110">限制事項</span><span class="sxs-lookup"><span data-stu-id="22e49-110">Limitations and Restrictions</span></span>  
 <span data-ttu-id="22e49-111">若要建立作業，使用者必須是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 固定資料庫角色或 **系統管理員 (sysadmin)** 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="22e49-111">To create a job, a user must be a member of one of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles or the **sysadmin** fixed server role.</span></span> <span data-ttu-id="22e49-112">只有作業擁有者或隸屬 **sysadmin** 角色的成員可以編輯作業。</span><span class="sxs-lookup"><span data-stu-id="22e49-112">A job can be edited only by its owner or members of the **sysadmin** role.</span></span> <span data-ttu-id="22e49-113">如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 固定資料庫角色的詳細資訊，請參閱 [SQL Server Agent 固定資料庫角色](sql-server-agent-fixed-database-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="22e49-113">For more information about the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles, see [SQL Server Agent Fixed Database Roles](sql-server-agent-fixed-database-roles.md).</span></span>  
  
 <span data-ttu-id="22e49-114">您必須是系統管理員，才能夠變更作業的擁有者。</span><span class="sxs-lookup"><span data-stu-id="22e49-114">You must be a system administrator to change the owner of a job.</span></span>  
  
 <span data-ttu-id="22e49-115">將作業指派給另一個登入並不保證新的擁有者具有充分之使用權限能夠成功執行作業。</span><span class="sxs-lookup"><span data-stu-id="22e49-115">Assigning a job to another login does not guarantee that the new owner has sufficient permission to run the job successfully.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="22e49-116">Security</span><span class="sxs-lookup"><span data-stu-id="22e49-116">Security</span></span>  
 <span data-ttu-id="22e49-117">基於安全考量，只有作業擁有者或隸屬 **sysadmin** 角色的成員可以變更作業的定義。</span><span class="sxs-lookup"><span data-stu-id="22e49-117">For security reasons, only the job owner or a member of the **sysadmin** role can change the definition of the job.</span></span> <span data-ttu-id="22e49-118">只有 **sysadmin** (系統管理員) 固定伺服器角色的成員可以將作業擁有權指定給其他使用者，而且無論作業擁有者是誰，都可以執行任何作業。</span><span class="sxs-lookup"><span data-stu-id="22e49-118">Only members of the **sysadmin** fixed server role can assign job ownership to other users, and they can run any job, regardless of the job owner.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="22e49-119">如果將作業擁有權變更給非 **系統管理員 (sysadmin)** 固定伺服器角色成員的使用者，而且作業正在執行要求 Proxy 帳戶的作業步驟 (例如， [!INCLUDE[ssIS](../../includes/ssis-md.md)] 套件執行)，請確定使用者擁有該 Proxy 帳戶的存取權，否則作業將會失敗。</span><span class="sxs-lookup"><span data-stu-id="22e49-119">If you change job ownership to a user who is not a member of the **sysadmin** fixed server role, and the job is executing job steps that require proxy accounts (for example, [!INCLUDE[ssIS](../../includes/ssis-md.md)] package execution), make sure that the user has access to that proxy account or else the job will fail.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="22e49-120">權限</span><span class="sxs-lookup"><span data-stu-id="22e49-120">Permissions</span></span>  
 <span data-ttu-id="22e49-121">如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="22e49-121">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProc2"></a> <span data-ttu-id="22e49-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="22e49-122">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="22e49-123">**若要賦予作業擁有權給其他人**</span><span class="sxs-lookup"><span data-stu-id="22e49-123">**To give others ownership of a job**</span></span>  
  
1.  <span data-ttu-id="22e49-124">在**物件總管中，** 連接到的實例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然後展開該實例。</span><span class="sxs-lookup"><span data-stu-id="22e49-124">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="22e49-125">依序展開 [SQL Server Agent]\*\*\*\* 和 [作業]\*\*\*\*、以滑鼠右鍵按一下作業，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="22e49-125">Expand **SQL Server Agent**, expand **Jobs**, right-click the job, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="22e49-126">在 **[擁有者]** 清單選取登入。</span><span class="sxs-lookup"><span data-stu-id="22e49-126">In the **Owner** list, select a login.</span></span> <span data-ttu-id="22e49-127">您必須是系統管理員，才能夠變更作業的擁有者。</span><span class="sxs-lookup"><span data-stu-id="22e49-127">You must be a system administrator to change the owner of a job.</span></span>  
  
     <span data-ttu-id="22e49-128">將作業指派給另一個登入並不保證新的擁有者具有充分之使用權限能夠成功執行作業。</span><span class="sxs-lookup"><span data-stu-id="22e49-128">Assigning a job to another login does not guarantee that the new owner has sufficient permission to run the job successfully.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProc2"></a> <span data-ttu-id="22e49-129">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="22e49-129">Using Transact-SQL</span></span>  
 <span data-ttu-id="22e49-130">**若要賦予作業擁有權給其他人**</span><span class="sxs-lookup"><span data-stu-id="22e49-130">**To give others ownership of a job**</span></span>  
  
1.  <span data-ttu-id="22e49-131">在 [物件總管] 中，連接到 Database Engine 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="22e49-131">In Object Explorer, connect to an instance of the Database Engine, and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="22e49-132">在工具列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="22e49-132">On the toolbar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="22e49-133">在查詢視窗中，輸入下列語句，以使用[sp_manage_jobs_by_login &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-manage-jobs-by-login-transact-sql)系統預存程式。</span><span class="sxs-lookup"><span data-stu-id="22e49-133">In the query window, enter the following statements that use the [sp_manage_jobs_by_login &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-manage-jobs-by-login-transact-sql) system stored procedure.</span></span> <span data-ttu-id="22e49-134">下列範例會將 `danw` 的所有作業重新指派給 `fran??oisa`。</span><span class="sxs-lookup"><span data-stu-id="22e49-134">The following example reassigns all jobs from `danw` to `fran??oisa`.</span></span>  
  
    ```sql
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_manage_jobs_by_login  
        @action = N'REASSIGN',  
        @current_owner_login_name = N'danw',  
        @new_owner_login_name = N'fran??oisa' ;  
    GO  
    ```  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMOProc2"></a><span data-ttu-id="22e49-135">使用 SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="22e49-135">Using SQL Server Management Objects</span></span>  

### <a name="to-give-others-ownership-of-a-job"></a><span data-ttu-id="22e49-136">若要賦予作業擁有權給其他人</span><span class="sxs-lookup"><span data-stu-id="22e49-136">To give others ownership of a job</span></span>
  
1.  <span data-ttu-id="22e49-137">使用所選的程式語言，例如 Visual Basic、Visual C# 或 PowerShell 呼叫 `Job` 類別。</span><span class="sxs-lookup"><span data-stu-id="22e49-137">Call the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="22e49-138">如需範例程式碼，請參閱 [使用 SQL Server Agent 排程自動管理工作](sql-server-agent.md)。</span><span class="sxs-lookup"><span data-stu-id="22e49-138">For example code, see [Scheduling Automatic Administrative Tasks in SQL Server Agent](sql-server-agent.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22e49-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22e49-139">See Also</span></span>  
 <span data-ttu-id="22e49-140">[實作作業](implement-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="22e49-140">[Implement Jobs](implement-jobs.md) </span></span>  
 [<span data-ttu-id="22e49-141">建立作業</span><span class="sxs-lookup"><span data-stu-id="22e49-141">Create Jobs</span></span>](create-jobs.md)  
