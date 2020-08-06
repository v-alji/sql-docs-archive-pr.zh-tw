---
title: 停止作業 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], stopping
- SQL Server Agent jobs, stopping
- stopping jobs
ms.assetid: 4249328a-24d8-4284-9d1d-7d04ed90e3d7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 78986e85dd8ee808f5fb621182d903a94bbc5eb7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686749"
---
# <a name="stop-a-job"></a><span data-ttu-id="0cf4c-102">停止作業</span><span class="sxs-lookup"><span data-stu-id="0cf4c-102">Stop a Job</span></span>
  <span data-ttu-id="0cf4c-103">本主題描述如何停止 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業。</span><span class="sxs-lookup"><span data-stu-id="0cf4c-103">This topic describes how to stop a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span> <span data-ttu-id="0cf4c-104">作業是 SQL Server Agent 執行的一系列指定動作。</span><span class="sxs-lookup"><span data-stu-id="0cf4c-104">A job is a specified series of actions that SQL Server Agent performs.</span></span>  
  
-   <span data-ttu-id="0cf4c-105">**開始之前：** 、</span><span class="sxs-lookup"><span data-stu-id="0cf4c-105">**Before you begin:**  ,</span></span>  
  
     [<span data-ttu-id="0cf4c-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="0cf4c-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="0cf4c-107">安全性</span><span class="sxs-lookup"><span data-stu-id="0cf4c-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0cf4c-108">**若要使用下列項目停止作業：**</span><span class="sxs-lookup"><span data-stu-id="0cf4c-108">**To stop a job, using:**</span></span>  
  
     [<span data-ttu-id="0cf4c-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0cf4c-109">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="0cf4c-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0cf4c-110">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="0cf4c-111">SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="0cf4c-111">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0cf4c-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="0cf4c-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="0cf4c-113">限制事項</span><span class="sxs-lookup"><span data-stu-id="0cf4c-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="0cf4c-114">如果作業目前正在執行 **CmdExec** 或 **PowerShell**類型的步驟，則會強制提前結束執行中的處理序 (如 MyProgram.exe)。</span><span class="sxs-lookup"><span data-stu-id="0cf4c-114">If a job is currently executing a step of type **CmdExec** or **PowerShell**, the process that is being run (for example, MyProgram.exe) is forced to end prematurely.</span></span> <span data-ttu-id="0cf4c-115">提前結束可能造成無法預期的行為，例如，由維持開啟狀態的處理序所使用的檔案。</span><span class="sxs-lookup"><span data-stu-id="0cf4c-115">This can cause unpredictable behavior, such as files that are being used by the process being held open.</span></span>  
  
-   <span data-ttu-id="0cf4c-116">對於多伺服器作業，作業的 STOP 指令會發佈到作業的所有目標伺服器。</span><span class="sxs-lookup"><span data-stu-id="0cf4c-116">For a multiserver job, a STOP instruction for the job is posted to all target servers of the job.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0cf4c-117">Security</span><span class="sxs-lookup"><span data-stu-id="0cf4c-117">Security</span></span>  
 <span data-ttu-id="0cf4c-118">如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="0cf4c-118">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="0cf4c-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0cf4c-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-stop-a-job"></a><span data-ttu-id="0cf4c-120">若要停止作業</span><span class="sxs-lookup"><span data-stu-id="0cf4c-120">To stop a job</span></span>  
  
1.  <span data-ttu-id="0cf4c-121">在**物件總管中，** 連接到的實例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然後展開該實例。</span><span class="sxs-lookup"><span data-stu-id="0cf4c-121">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="0cf4c-122">展開 **[SQL Server Agent]**，再展開 **[作業]**，以滑鼠右鍵按一下要停止的作業，然後按一下 **[停止作業]**。</span><span class="sxs-lookup"><span data-stu-id="0cf4c-122">Expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to stop, and then click **Stop Job**.</span></span>  
  
3.  <span data-ttu-id="0cf4c-123">若要停止多個作業，請以滑鼠右鍵按一下 **[作業活動監視器]**，然後按一下 **[檢視作業活動]**。</span><span class="sxs-lookup"><span data-stu-id="0cf4c-123">If you want to stop multiple jobs, right-click **Job Activity Monitor**, and then click **View Job Activity**.</span></span> <span data-ttu-id="0cf4c-124">在「作業活動監視器」中，選取要停止的作業，以滑鼠右鍵按一下選取範圍，然後按一下 **[停止作業]**。</span><span class="sxs-lookup"><span data-stu-id="0cf4c-124">In the Job Activity Monitor, select the jobs you want to stop, right-click your selection, and then click **Stop Jobs**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="0cf4c-125">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0cf4c-125">Using Transact-SQL</span></span>  
  
### <a name="to-stop-a-job"></a><span data-ttu-id="0cf4c-126">若要停止作業</span><span class="sxs-lookup"><span data-stu-id="0cf4c-126">To stop a job</span></span>  
  
1.  <span data-ttu-id="0cf4c-127">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0cf4c-127">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0cf4c-128">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="0cf4c-128">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0cf4c-129">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="0cf4c-129">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- stops a job named Weekly Sales Data Backup  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_stop_job  
        N'Weekly Sales Data Backup' ;  
    GO  
    ```  
  
 <span data-ttu-id="0cf4c-130">如需詳細資訊，請參閱[sp_stop_job &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-stop-job-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0cf4c-130">For more information, see [sp_stop_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-stop-job-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="0cf4c-131">使用 SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="0cf4c-131">Using SQL Server Management Objects</span></span>  

### <a name="to-stop-a-job"></a><span data-ttu-id="0cf4c-132">若要停止作業</span><span class="sxs-lookup"><span data-stu-id="0cf4c-132">To stop a job</span></span>
  
 <span data-ttu-id="0cf4c-133">使用所選的程式語言，例如 Visual Basic、Visual C# 或 PowerShell，呼叫 `Stop` 類別的 `Job` 方法。</span><span class="sxs-lookup"><span data-stu-id="0cf4c-133">Call the `Stop` method of the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="0cf4c-134">如需詳細資訊，請參閱 [SQL Server 管理物件 (SMO)](https://msdn.microsoft.com/library/ms162169.aspx)。</span><span class="sxs-lookup"><span data-stu-id="0cf4c-134">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
