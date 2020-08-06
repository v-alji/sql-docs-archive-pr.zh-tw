---
title: 修改作業的目標伺服器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- modifying target servers
- SQL Server Agent jobs, target servers
- target servers [SQL Server], modifying
ms.assetid: 9dbe24f2-acec-4aa2-920c-e8e96efa18e4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 246a5bb59a681a70734cc8cabef4f724cda1b52e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594338"
---
# <a name="modify-the-target-servers-for-a-job"></a><span data-ttu-id="75d9e-102">修改作業的目標伺服器</span><span class="sxs-lookup"><span data-stu-id="75d9e-102">Modify the Target Servers for a Job</span></span>
  <span data-ttu-id="75d9e-103">本主題描述如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用或，在中變更 Agent 作業的目標伺服器 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="75d9e-103">This topic describes how to change the target servers for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="75d9e-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="75d9e-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="75d9e-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="75d9e-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="75d9e-106">安全性</span><span class="sxs-lookup"><span data-stu-id="75d9e-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="75d9e-107">**若要修改作業的目標伺服器，使用：**</span><span class="sxs-lookup"><span data-stu-id="75d9e-107">**To modify the target servers for a job, using:**</span></span>  
  
     [<span data-ttu-id="75d9e-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="75d9e-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="75d9e-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="75d9e-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="75d9e-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="75d9e-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="75d9e-111">Security</span><span class="sxs-lookup"><span data-stu-id="75d9e-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="75d9e-112">權限</span><span class="sxs-lookup"><span data-stu-id="75d9e-112">Permissions</span></span>  
 <span data-ttu-id="75d9e-113">根據預設，系統管理員固定伺服器角色的成員可執行此預存程序。</span><span class="sxs-lookup"><span data-stu-id="75d9e-113">By default, members of the sysadmin fixed server role can execute this stored procedure.</span></span> <span data-ttu-id="75d9e-114">其他使用者必須獲得授與 msdb 資料庫的下列其中一個 SQL Server Agent 固定資料庫角色：</span><span class="sxs-lookup"><span data-stu-id="75d9e-114">Other users must be granted one of the following SQL Server Agent fixed database roles in the msdb database:</span></span>  
  
1.  `SQLAgentUserRole`  
  
2.  `SQLAgentReaderRole`  
  
3.  <span data-ttu-id="75d9e-115">SQLAgentOperatorRole</span><span class="sxs-lookup"><span data-stu-id="75d9e-115">SQLAgentOperatorRole</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="75d9e-116">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="75d9e-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-the-target-servers-for-a-job"></a><span data-ttu-id="75d9e-117">若要為作業修改目標伺服器</span><span class="sxs-lookup"><span data-stu-id="75d9e-117">To modify the target servers for a job</span></span>  
  
1.  <span data-ttu-id="75d9e-118">在**物件總管中，** 連接到的實例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然後展開該實例。</span><span class="sxs-lookup"><span data-stu-id="75d9e-118">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="75d9e-119">依序展開 [SQL Server Agent]\*\*\*\* 和 [作業]\*\*\*\*、以滑鼠右鍵按一下某個作業，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="75d9e-119">Expand **SQL Server Agent**, expand **Jobs**, right-click a job, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="75d9e-120">在 [作業屬性]\*\*\*\* 對話方塊中，選取 [目標]\*\*\*\* 頁面，然後按一下 [目標本機伺服器]\*\*\*\* 或 [目標多個伺服器]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="75d9e-120">In the **Job Properties** dialog, select the **Targets**page, and click **Target local server**, or **Target multiple servers**.</span></span>  
  
     <span data-ttu-id="75d9e-121">如果選擇 **[目標多個伺服器]**，請選取伺服器名稱左邊的方塊，以指定要做為作業目標的伺服器。</span><span class="sxs-lookup"><span data-stu-id="75d9e-121">If you choose **Target multiple servers**, designate the servers that will be targets for the job by checking the box to the left of the server name.</span></span> <span data-ttu-id="75d9e-122">至於不要做為作業目標的伺服器，請確認已取消選取其核取方塊。</span><span class="sxs-lookup"><span data-stu-id="75d9e-122">Verify that the check boxes for servers that will not be targets of the job are unchecked.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="75d9e-123">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="75d9e-123">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-the-target-servers-for-a-job"></a><span data-ttu-id="75d9e-124">若要為作業修改目標伺服器</span><span class="sxs-lookup"><span data-stu-id="75d9e-124">To modify the target servers for a job</span></span>  
  
1.  <span data-ttu-id="75d9e-125">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="75d9e-125">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="75d9e-126">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="75d9e-126">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="75d9e-127">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="75d9e-127">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="75d9e-128">這個範例會將多伺服器作業 Weekly Sales Backups 指派給伺服器 SEATTLE2。</span><span class="sxs-lookup"><span data-stu-id="75d9e-128">This example assigns the multiserver job Weekly Sales Backups to the server SEATTLE2.</span></span>  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_jobserver  
    @job_name = N'Weekly Sales Backups',   
    @server_name = N'SEATTLE2' ;   
GO  
  
```  
  
 <span data-ttu-id="75d9e-129">如需詳細資訊，請參閱[sp_add_jobserver &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="75d9e-129">For more information, see [sp_add_jobserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75d9e-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75d9e-130">See Also</span></span>  
 [<span data-ttu-id="75d9e-131">將整個企業的管理自動化</span><span class="sxs-lookup"><span data-stu-id="75d9e-131">Automated Administration Across an Enterprise</span></span>](automated-administration-across-an-enterprise.md)  
  
  
