---
title: 啟動作業 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], starting
- SQL Server Agent jobs, starting
- starting jobs
ms.assetid: cec9f7f7-d0a7-4239-9dc5-a69c011ebaa0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4d5af895df518a915dacd953331b9139471933aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705853"
---
# <a name="start-a-job"></a><span data-ttu-id="fc497-102">啟動作業</span><span class="sxs-lookup"><span data-stu-id="fc497-102">Start a Job</span></span>
  <span data-ttu-id="fc497-103">本主題描述如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 SQL Server 管理物件，在中開始執行 Agent 作業 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="fc497-103">This topic describes how to start running a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="fc497-104">作業是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 執行的一系列指定動作。</span><span class="sxs-lookup"><span data-stu-id="fc497-104">A job is a specified series of actions that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent performs.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="fc497-105">Agent 作業可以在本機伺服器或多個遠端伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="fc497-105">Agent jobs can run on one local server or on multiple remote servers.</span></span>  
  
-   <span data-ttu-id="fc497-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="fc497-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="fc497-107">安全性</span><span class="sxs-lookup"><span data-stu-id="fc497-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="fc497-108">**若要使用下列項目啟動作業：**</span><span class="sxs-lookup"><span data-stu-id="fc497-108">**To start a job, using:**</span></span>  
  
     [<span data-ttu-id="fc497-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fc497-109">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="fc497-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fc497-110">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="fc497-111">SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="fc497-111">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="fc497-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="fc497-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="fc497-113">Security</span><span class="sxs-lookup"><span data-stu-id="fc497-113">Security</span></span>  
 <span data-ttu-id="fc497-114">如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="fc497-114">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="fc497-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fc497-115">Using SQL Server Management Studio</span></span>  
  
### <a name="to-start-a-job"></a><span data-ttu-id="fc497-116">若要啟動作業</span><span class="sxs-lookup"><span data-stu-id="fc497-116">To start a job</span></span>  
  
1.  <span data-ttu-id="fc497-117">在**物件總管中，** 連接到的實例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然後展開該實例。</span><span class="sxs-lookup"><span data-stu-id="fc497-117">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="fc497-118">展開 **[SQL Server Agent]** ，再展開 **[作業]**。</span><span class="sxs-lookup"><span data-stu-id="fc497-118">Expand **SQL Server Agent,** and expand **Jobs**.</span></span> <span data-ttu-id="fc497-119">請依照您所需要的作業啟動方式，執行下列其中一項作：</span><span class="sxs-lookup"><span data-stu-id="fc497-119">Depending on how you want the job to start, do one of the following:</span></span>  
  
    -   <span data-ttu-id="fc497-120">若要對單一伺服器或目標伺服器執行作業，或要在主要伺服器上執行本機伺服器作業，請在要啟動的作業上按一下滑鼠右鍵，然後按一下 [啟動作業]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fc497-120">If you are working on a single server, or working on a target server, or running a local server job on a master server, right-click the job you want to start, and then click **Start Job**.</span></span>  
  
    -   <span data-ttu-id="fc497-121">若要啟動多項作業，請在 [作業活動監視器]\*\*\*\*，然後按一下 [檢視作業活動]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fc497-121">If you want to start multiple jobs, right-click **Job Activity Monitor**, and then click **View Job Activity**.</span></span> <span data-ttu-id="fc497-122">您可以在作業活動監視器中選取多項作業，然後在選取範圍上按一下滑鼠右鍵，再按一下 [啟動作業]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fc497-122">In the Job Activity Monitor you can select multiple jobs, right-click your selection, and click **Start Jobs**.</span></span>  
  
    -   <span data-ttu-id="fc497-123">若要對主要伺服器執行作業，並希望所有目標伺服器同時執行該作業，請在要啟動的作業上按一下滑鼠右鍵，然後按一下 [啟動作業]\*\*\*\*，再按一下 [在所有目標伺服器上啟動]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fc497-123">If you are working on a master server and want all targeted servers to run the job simultaneously, right-click the job you want to start, click **Start Job**, and then click **Start on all targeted servers**.</span></span>  
  
    -   <span data-ttu-id="fc497-124">若要對主要伺服器執行作業，並要指定執行該作業的目標伺服器，請在要啟動的作業上按一下滑鼠右鍵，然後按一下 [啟動作業]\*\*\*\*，再按一下 [在特定目標伺服器上啟動]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fc497-124">If you are working on a master server and want to specify target servers for the job, right-click the job you want to start, click **Start Job**, and then click **Start on specific target servers**.</span></span> <span data-ttu-id="fc497-125">在 **[公佈下載指示]** 對話方塊中選取 **[下列目標伺服器]** 核取方塊，然後選取應該執行此作業的每個目標伺服器。</span><span class="sxs-lookup"><span data-stu-id="fc497-125">In the **Post Download Instructions** dialog box, select the **These target servers** check box, and then select each target server on which this job should run.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="fc497-126">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fc497-126">Using Transact-SQL</span></span>  
  
### <a name="to-start-a-job"></a><span data-ttu-id="fc497-127">若要啟動作業</span><span class="sxs-lookup"><span data-stu-id="fc497-127">To start a job</span></span>  
  
1.  <span data-ttu-id="fc497-128">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="fc497-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="fc497-129">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="fc497-129">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="fc497-130">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="fc497-130">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- starts a job named Weekly Sales Data Backup.    
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_start_job N'Weekly Sales Data Backup' ;  
    GO  
    ```  
  
 <span data-ttu-id="fc497-131">如需詳細資訊，請參閱 [sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="fc497-131">For more information, see [sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="fc497-132">使用 SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="fc497-132">Using SQL Server Management Objects</span></span>  

### <a name="to-start-a-job"></a><span data-ttu-id="fc497-133">若要啟動作業</span><span class="sxs-lookup"><span data-stu-id="fc497-133">To start a job</span></span>
  
 <span data-ttu-id="fc497-134">使用所選的程式語言，例如 Visual Basic、Visual C# 或 PowerShell，呼叫 `Start` 類別的 `Job` 方法。</span><span class="sxs-lookup"><span data-stu-id="fc497-134">Call the `Start` method of the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="fc497-135">如需詳細資訊，請參閱 [SQL Server 管理物件 (SMO)](https://msdn.microsoft.com/library/ms162169.aspx)。</span><span class="sxs-lookup"><span data-stu-id="fc497-135">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
