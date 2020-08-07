---
title: 將作業狀態寫入到 Windows 應用程式記錄 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- status information [SQL Server], jobs
- SQL Server Agent jobs, status
- writing job status to log
- jobs [SQL Server Agent], status
- logs [SQL Server], jobs
ms.assetid: 3b813702-8f61-40ec-bf3b-ce9deb7e68be
author: stevestein
ms.author: sstein
ms.openlocfilehash: 67bdd7948d1722e49976d5e48b571c684431cd1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703714"
---
# <a name="write-the-job-status-to-the-windows-application-log"></a><span data-ttu-id="91e73-102">Write the Job Status to the Windows Application Log</span><span class="sxs-lookup"><span data-stu-id="91e73-102">Write the Job Status to the Windows Application Log</span></span>
  <span data-ttu-id="91e73-103">本主題描述如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 、或 SQL Server 管理物件，在中設定 Agent，將作業狀態寫入 Windows 應用程式事件記錄檔 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="91e73-103">This topic describes how to configure [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] to write job status to the Windows application event log by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="91e73-104">作業回應可確保資料庫管理員知道作業已完成，以及作業的執行頻率。</span><span class="sxs-lookup"><span data-stu-id="91e73-104">Job responses ensure that database administrators know when jobs complete and how frequently they run.</span></span> <span data-ttu-id="91e73-105">典型的作業回應包括：</span><span class="sxs-lookup"><span data-stu-id="91e73-105">Typical job responses include:</span></span>  
  
-   <span data-ttu-id="91e73-106">使用電子郵件、電子呼叫或 **net send** 訊息通知操作員。</span><span class="sxs-lookup"><span data-stu-id="91e73-106">Notifying the operator by using e-mail, electronic paging, or a **net send** message.</span></span> <span data-ttu-id="91e73-107">如果操作員必須執行後續動作，請使用其中一個作業回應。</span><span class="sxs-lookup"><span data-stu-id="91e73-107">Use one of these job responses if the operator must perform a follow-up action.</span></span> <span data-ttu-id="91e73-108">例如，如果備份作業成功完成，必須告知操作員以取下備份磁帶，並將其存放在安全的地方。</span><span class="sxs-lookup"><span data-stu-id="91e73-108">For example, if a backup job completes successfully, the operator must be notified to remove the backup tape and store it in a safe location.</span></span>  
  
-   <span data-ttu-id="91e73-109">將事件訊息寫入至 Windows 應用程式記錄。</span><span class="sxs-lookup"><span data-stu-id="91e73-109">Writing an event message to the Windows application log.</span></span> <span data-ttu-id="91e73-110">這個回應只用於失敗的作業。</span><span class="sxs-lookup"><span data-stu-id="91e73-110">You can use this response only for failed jobs.</span></span>  
  
-   <span data-ttu-id="91e73-111">自動刪除作業。</span><span class="sxs-lookup"><span data-stu-id="91e73-111">Automatically deleting the job.</span></span> <span data-ttu-id="91e73-112">如果確定您將不再需要重新執行這個作業，請使用這個作業回應。</span><span class="sxs-lookup"><span data-stu-id="91e73-112">Use this job response if you are certain that you do not need to rerun this job.</span></span>  
  
 <span data-ttu-id="91e73-113">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="91e73-113">**In This Topic**</span></span>  
  
-   <span data-ttu-id="91e73-114">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="91e73-114">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="91e73-115">安全性</span><span class="sxs-lookup"><span data-stu-id="91e73-115">Security</span></span>](#Security)  
  
-   <span data-ttu-id="91e73-116">**若要使用下列項目，將作業狀態寫入 Windows 應用程式記錄檔：**</span><span class="sxs-lookup"><span data-stu-id="91e73-116">**To write the job status to the Windows application log, using:**</span></span>  
  
     [<span data-ttu-id="91e73-117">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="91e73-117">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="91e73-118">SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="91e73-118">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="91e73-119">開始之前</span><span class="sxs-lookup"><span data-stu-id="91e73-119">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="91e73-120">Security</span><span class="sxs-lookup"><span data-stu-id="91e73-120">Security</span></span>  
 <span data-ttu-id="91e73-121">如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="91e73-121">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="91e73-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="91e73-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-write-job-status-to-the-windows-application-log"></a><span data-ttu-id="91e73-123">若要將作業狀態寫入到 Windows 應用程式記錄</span><span class="sxs-lookup"><span data-stu-id="91e73-123">To write job status to the Windows application log</span></span>  
  
1.  <span data-ttu-id="91e73-124">在**物件總管中，** 連接到的實例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然後展開該實例。</span><span class="sxs-lookup"><span data-stu-id="91e73-124">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="91e73-125">展開 **[SQL Server Agent]**，展開 **[作業]**，以滑鼠右鍵按一下要編輯的作業，然後按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="91e73-125">Expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to edit, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="91e73-126">選取 **[通知]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="91e73-126">Select the **Notifications** page.</span></span>  
  
4.  <span data-ttu-id="91e73-127">勾選 **[寫入 Windows 應用程式事件記錄檔]**，並選擇下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="91e73-127">Check **Write to Windows application event log**, and choose one of the following:</span></span>  
  
    -   <span data-ttu-id="91e73-128">按一下 [當作業成功時]\*\*\*\*，在作業成功完成時記錄作業狀態。</span><span class="sxs-lookup"><span data-stu-id="91e73-128">Click**When the job succeeds**to log the job status when the job completes successfully.</span></span>  
  
    -   <span data-ttu-id="91e73-129">按一下 [當作業失敗時]\*\*\*\*，在作業失敗時記錄作業狀態。</span><span class="sxs-lookup"><span data-stu-id="91e73-129">Click**When the job fails**to log the job status when the job completes unsuccessfully.</span></span>  
  
    -   <span data-ttu-id="91e73-130">按一下 [作業完成時]\*\*\*\*，不論完成狀態為何，一律記錄作業狀態。</span><span class="sxs-lookup"><span data-stu-id="91e73-130">Click**When the job completes** to log the job status regardless of completion status.</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="91e73-131">使用 SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="91e73-131">Using SQL Server Management Objects</span></span>  

### <a name="to-write-job-status-to-the-windows-application-log"></a><span data-ttu-id="91e73-132">若要將作業狀態寫入到 Windows 應用程式記錄</span><span class="sxs-lookup"><span data-stu-id="91e73-132">To write job status to the Windows application log</span></span>
  
 <span data-ttu-id="91e73-133">使用所選的程式語言，例如 Visual Basic、Visual C# 或 PowerShell，呼叫 `EventLogLevel` 類別的 `Job` 屬性。</span><span class="sxs-lookup"><span data-stu-id="91e73-133">Call the `EventLogLevel` property of the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
  
 <span data-ttu-id="91e73-134">下列程式碼範例會設定作業在作業執行完成時，產生作業系統事件記錄項目。</span><span class="sxs-lookup"><span data-stu-id="91e73-134">The following code example sets the job to generate an operating system event log entry when the job execution finishes.</span></span>  
  
```powershell
$srv = new-object Microsoft.SqlServer.Management.Smo.Server("(local)")  
$jb = new-object Microsoft.SqlServer.Management.Smo.Agent.Job($srv.JobServer, "Test Job")  
$jb.EventLogLevel = [Microsoft.SqlServer.Management.Smo.Agent.CompletionAction]::Always  
```  
