---
title: 刪除作業步驟記錄檔 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- job steps [SQL Server Agent]
- deleting job step logs
- logs [SQL Server], jobs
- removing job step logs
ms.assetid: ee20c6cd-0258-4550-bdb0-71e86a0fb330
author: stevestein
ms.author: sstein
ms.openlocfilehash: de7c64c4d7cf461eef563ae6989e043d125c6f5b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596998"
---
# <a name="delete-a-job-step-log"></a><span data-ttu-id="a4795-102">Delete a Job Step Log</span><span class="sxs-lookup"><span data-stu-id="a4795-102">Delete a Job Step Log</span></span>
  <span data-ttu-id="a4795-103">本主題描述如何刪除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業步驟記錄。</span><span class="sxs-lookup"><span data-stu-id="a4795-103">This topic describes how to delete a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step log.</span></span>  
  
-   <span data-ttu-id="a4795-104">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="a4795-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a4795-105">限制事項</span><span class="sxs-lookup"><span data-stu-id="a4795-105">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="a4795-106">安全性</span><span class="sxs-lookup"><span data-stu-id="a4795-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a4795-107">**若要使用下列項目刪除 SQL Server Agent 作業步驟記錄：**</span><span class="sxs-lookup"><span data-stu-id="a4795-107">**To delete a SQL Server Agent job step log, using:**</span></span>  
  
     [<span data-ttu-id="a4795-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a4795-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="a4795-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a4795-109">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="a4795-110">SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="a4795-110">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a4795-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="a4795-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="a4795-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="a4795-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="a4795-113">刪除作業步驟時，會自動刪除其輸出記錄檔。</span><span class="sxs-lookup"><span data-stu-id="a4795-113">When job steps are deleted their output log is automatically deleted.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a4795-114">Security</span><span class="sxs-lookup"><span data-stu-id="a4795-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a4795-115">權限</span><span class="sxs-lookup"><span data-stu-id="a4795-115">Permissions</span></span>  
 <span data-ttu-id="a4795-116">除非您是系統管理員 ( **sysadmin** ) 固定伺服器角色的成員，否則您只能修改您所擁有的作業。</span><span class="sxs-lookup"><span data-stu-id="a4795-116">Unless you are a member of the **sysadmin** fixed server role, you can only modify jobs that you own.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="a4795-117">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a4795-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-sql-server-agent-job-step-log"></a><span data-ttu-id="a4795-118">若要刪除 SQL Server Agent 作業步驟記錄</span><span class="sxs-lookup"><span data-stu-id="a4795-118">To delete a SQL Server Agent job step log</span></span>  
  
1.  <span data-ttu-id="a4795-119">在**物件總管中，** 連接到的實例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然後展開該實例。</span><span class="sxs-lookup"><span data-stu-id="a4795-119">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="a4795-120">展開 [SQL Server Agent]\*\*\*\*，展開 [作業]\*\*\*\*，以滑鼠右鍵按一下要修改的作業，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a4795-120">Expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to modify, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="a4795-121">在 **[作業屬性]** 對話方塊中，刪除選取的作業步驟。</span><span class="sxs-lookup"><span data-stu-id="a4795-121">In the **Job Properties** dialog box, delete the selected job step.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="a4795-122">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a4795-122">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-sql-server-agent-job-step-log"></a><span data-ttu-id="a4795-123">若要刪除 SQL Server Agent 作業步驟記錄</span><span class="sxs-lookup"><span data-stu-id="a4795-123">To delete a SQL Server Agent job step log</span></span>  
  
1.  <span data-ttu-id="a4795-124">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a4795-124">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a4795-125">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="a4795-125">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a4795-126">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="a4795-126">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- removes the job step log for step 2 in the job Weekly Sales Data Backup  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_delete_jobsteplog  
        @job_name = N'Weekly Sales Data Backup',  
        @step_id = 2;  
    GO  
    ```  
  
 <span data-ttu-id="a4795-127">如需詳細資訊，請參閱[sp_delete_jobsteplog &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobsteplog-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a4795-127">For more information, see [sp_delete_jobsteplog &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobsteplog-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="a4795-128">使用 SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="a4795-128">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="a4795-129">透過所選的程式語言，例如 Visual Basic、Visual C# 或 PowerShell，使用 `DeleteJobStepLogs` 類別的 `Job` 方法。</span><span class="sxs-lookup"><span data-stu-id="a4795-129">Use the `DeleteJobStepLogs` methods of the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="a4795-130">如需詳細資訊，請參閱[SQL Server 管理物件 (SMO)](https://msdn.microsoft.com/library/ms162169.aspx)。</span><span class="sxs-lookup"><span data-stu-id="a4795-130">For more information, see[SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
  
```powershell
# Delete all job step log files that have ID values larger than 5.  
$srv = New-Object Microsoft.SqlServer.Management.Smo.Server("(local)")  
$jb = $srv.JobServer.Jobs["Test Job"]  
$jb.DeleteJobStepLogs(5)  
```
