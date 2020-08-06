---
title: 建立 PowerShell 指令碼作業步驟 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- PowerShell [SQL Server], job steps
- jobs [SQL Server Agent], PowerShell
- job steps [PowerShell]
- SQL Server Agent jobs, PowerShell steps
ms.assetid: 50afcf84-fae0-4eb5-9b0f-f2cf144c1433
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4232cdfa584fdcc2e13786ecc9bd00f0c6fe7066
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595361"
---
# <a name="create-a-powershell-script-job-step"></a><span data-ttu-id="8786b-102">Create a PowerShell Script Job Step</span><span class="sxs-lookup"><span data-stu-id="8786b-102">Create a PowerShell Script Job Step</span></span>
  <span data-ttu-id="8786b-103">此主題描述如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中建立和定義執行 PowerShell 指令碼的 [!INCLUDE[tsql](../../includes/tsql-md.md)]Agent 作業步驟。</span><span class="sxs-lookup"><span data-stu-id="8786b-103">This topic describes how to create and define a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step that executes a PowerShell script in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="8786b-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="8786b-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="8786b-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="8786b-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="8786b-106">安全性</span><span class="sxs-lookup"><span data-stu-id="8786b-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="8786b-107">**若要使用下列項目建立 PowerShell 指令碼作業步驟：**</span><span class="sxs-lookup"><span data-stu-id="8786b-107">**To create a PowerShell Script job step, using:**</span></span>  
  
     [<span data-ttu-id="8786b-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8786b-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="8786b-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8786b-109">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="8786b-110">SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="8786b-110">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8786b-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="8786b-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8786b-112">Security</span><span class="sxs-lookup"><span data-stu-id="8786b-112">Security</span></span>  
 <span data-ttu-id="8786b-113">如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="8786b-113">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="8786b-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8786b-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-powershell-script-job-step"></a><span data-ttu-id="8786b-115">建立 PowerShell 指令碼作業步驟</span><span class="sxs-lookup"><span data-stu-id="8786b-115">To create a PowerShell Script job step</span></span>  
  
1.  <span data-ttu-id="8786b-116">在**物件總管中，** 連接到的實例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然後展開該實例。</span><span class="sxs-lookup"><span data-stu-id="8786b-116">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="8786b-117">展開 **SQL Server Agent**，建立新作業或以滑鼠右鍵按一下現有作業，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8786b-117">Expand **SQL Server Agent**, create a new job or right-click an existing job, and then click **Properties**.</span></span> <span data-ttu-id="8786b-118">如需建立作業的詳細資訊，請參閱＜ [建立作業](create-jobs.md)＞。</span><span class="sxs-lookup"><span data-stu-id="8786b-118">For more information on creating a job, see [Creating Jobs](create-jobs.md).</span></span>  
  
3.  <span data-ttu-id="8786b-119">在 **[作業屬性]** 方塊中，按一下 **[步驟]** 頁面，然後按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="8786b-119">In the **Job Properties** dialog, click the **Steps** page, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="8786b-120">在 **[新增作業步驟]** 對話方塊中，輸入一個作業 **步驟名稱**。</span><span class="sxs-lookup"><span data-stu-id="8786b-120">In the **New Job Step** dialog, type a job **Step name**.</span></span>  
  
5.  <span data-ttu-id="8786b-121">在 **[類型]** 清單中，按一下 **[PowerShell]**。</span><span class="sxs-lookup"><span data-stu-id="8786b-121">In the **Type** list, click **PowerShell**.</span></span>  
  
6.  <span data-ttu-id="8786b-122">在 **[執行身分]** 清單中，選取具有作業將會使用之認證的 Proxy 帳戶。</span><span class="sxs-lookup"><span data-stu-id="8786b-122">In the **Run as** list, select the proxy account with the credentials that the job will use.</span></span>  
  
7.  <span data-ttu-id="8786b-123">在 **[命令]** 方塊中，輸入將為作業步驟執行的 PowerShell 指令碼語法。</span><span class="sxs-lookup"><span data-stu-id="8786b-123">In the **Command** box, enter the PowerShell script syntax that will be executed for the job step.</span></span> <span data-ttu-id="8786b-124">或者，請按一下 **[開啟舊檔]** ，然後選取包含指令碼語法的檔案。</span><span class="sxs-lookup"><span data-stu-id="8786b-124">Alternately, click **Open** and select a file containing the script syntax.</span></span> <span data-ttu-id="8786b-125">如需 PowerShell 指令碼範例，請參閱下面的 **使用 Transact-SQL** 。</span><span class="sxs-lookup"><span data-stu-id="8786b-125">For an example of a PowerShell script, see **Using Transact-SQL** below.</span></span>  
  
8.  <span data-ttu-id="8786b-126">按一下 **[進階]** 頁面，設定下列作業步驟選項：作業步驟成功或失敗時要採取什麼動作、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 應該嘗試執行作業步驟多少次，以及應該多久重試一次。</span><span class="sxs-lookup"><span data-stu-id="8786b-126">Click the **Advanced** page to set the following job step options: what action to take if the job step succeeds or fails, how many times [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent should try to execute the job step, and how often retry attempts should be made.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="8786b-127">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8786b-127">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-powershell-script-job-step"></a><span data-ttu-id="8786b-128">建立 PowerShell 指令碼作業步驟</span><span class="sxs-lookup"><span data-stu-id="8786b-128">To create a PowerShell Script job step</span></span>  
  
1.  <span data-ttu-id="8786b-129">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="8786b-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="8786b-130">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="8786b-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="8786b-131">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="8786b-131">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- creates a PowerShell job step that finds the processes that use more than 1000 MB of memory and kills them  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Kills all processes that use more than 1000 MB of memory',  
        @subsystem = N'PowerShell',  
        @command = N'Get-Process | Where-Object { $_.WS -gt 1000MB } | Stop-Process',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
 <span data-ttu-id="8786b-132">如需詳細資訊，請參閱[sp_add_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="8786b-132">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="8786b-133">使用 SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="8786b-133">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="8786b-134">**建立 PowerShell 指令碼作業步驟**</span><span class="sxs-lookup"><span data-stu-id="8786b-134">**To create a PowerShell Script job step**</span></span>  
  
 <span data-ttu-id="8786b-135">透過所選的程式語言，例如 Visual Basic、Visual C# 或 PowerShell，使用 `JobStep` 類別。</span><span class="sxs-lookup"><span data-stu-id="8786b-135">Use the `JobStep` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
