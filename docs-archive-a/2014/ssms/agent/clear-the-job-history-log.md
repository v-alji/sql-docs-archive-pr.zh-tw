---
title: 清除作業記錄檔 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- clearing job history log
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: 34b9398a-c409-4040-8ea1-0deceb18f961
author: stevestein
ms.author: sstein
ms.openlocfilehash: 813c2c7c86a769eea09a093f2de999460d78ef54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606583"
---
# <a name="clear-the-job-history-log"></a><span data-ttu-id="f153b-102">清除作業歷程記錄</span><span class="sxs-lookup"><span data-stu-id="f153b-102">Clear the Job History Log</span></span>
  <span data-ttu-id="f153b-103">本主題描述如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 、或 SQL Server 管理物件，在中刪除 Agent 作業記錄的內容 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f153b-103">This topic describes how to delete the contents of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job history log in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="f153b-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="f153b-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f153b-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="f153b-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f153b-106">安全性</span><span class="sxs-lookup"><span data-stu-id="f153b-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f153b-107">**若要使用下列項目清除作業記錄：**</span><span class="sxs-lookup"><span data-stu-id="f153b-107">**To clear the job history log, using:**</span></span>  
  
     [<span data-ttu-id="f153b-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f153b-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="f153b-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f153b-109">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="f153b-110">SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="f153b-110">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f153b-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="f153b-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f153b-112">Security</span><span class="sxs-lookup"><span data-stu-id="f153b-112">Security</span></span>  
 <span data-ttu-id="f153b-113">如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="f153b-113">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="f153b-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f153b-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-clear-the-job-history-log"></a><span data-ttu-id="f153b-115">若要清除作業記錄檔</span><span class="sxs-lookup"><span data-stu-id="f153b-115">To clear the job history log</span></span>  
  
1.  <span data-ttu-id="f153b-116">在**物件總管中，** 連接到的實例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然後展開該實例。</span><span class="sxs-lookup"><span data-stu-id="f153b-116">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="f153b-117">展開 **[SQL Server Agent]**，然後展開 **[作業]**。</span><span class="sxs-lookup"><span data-stu-id="f153b-117">Expand **SQL Server Agent**, and then expand **Jobs**.</span></span>  
  
3.  <span data-ttu-id="f153b-118">以滑鼠右鍵按一下某個作業，然後按一下 **[檢視記錄]**。</span><span class="sxs-lookup"><span data-stu-id="f153b-118">Right-click a job and click **View history**.</span></span>  
  
4.  <span data-ttu-id="f153b-119">在 **[記錄檔檢視器]** 中，選取您要清除其記錄的作業，然後執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="f153b-119">In the **Log File Viewer**, select the job for which you want to clear history, and then do one of the following:</span></span>  
  
    -   <span data-ttu-id="f153b-120">按一下 **[刪除]**，然後按一下 **[刪除記錄]** 對話方塊中的 **[刪除所有的記錄]** 。</span><span class="sxs-lookup"><span data-stu-id="f153b-120">Click **Delete**, and then click **Delete all history** in the **Delete History** dialog.</span></span> <span data-ttu-id="f153b-121">您可以刪除所有的作業記錄，也可以只刪除某個特定日期之前的記錄。</span><span class="sxs-lookup"><span data-stu-id="f153b-121">You can delete all job history or only history that is older than a specified date.</span></span> <span data-ttu-id="f153b-122">如果您要移除所有的作業記錄，請按一下 **[刪除所有的記錄]**。</span><span class="sxs-lookup"><span data-stu-id="f153b-122">If you want to remove all job history, click **Delete all history**.</span></span> <span data-ttu-id="f153b-123">如果您只要移除舊的作業記錄，請按一下 **[刪除在這之前的記錄]**，然後指定日期。</span><span class="sxs-lookup"><span data-stu-id="f153b-123">If you only want to remove older job history logs, click **Delete history before**, and then specify a date.</span></span>  
  
    -   <span data-ttu-id="f153b-124">如果您要清除多重伺服器作業的記錄，請按一下 **[作業狀態]** 。</span><span class="sxs-lookup"><span data-stu-id="f153b-124">Click **Job status** if you want to clear the history log of a multiserver job.</span></span> <span data-ttu-id="f153b-125">按一下 **[作業]**，按一下作業名稱，然後按一下 **[檢視遠端作業記錄]**。</span><span class="sxs-lookup"><span data-stu-id="f153b-125">Click **Job**, click a job name, and then click **View Remote Job History**.</span></span>  
  
5.  <span data-ttu-id="f153b-126">按一下 **[刪除]** 。</span><span class="sxs-lookup"><span data-stu-id="f153b-126">Click **Delete**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="f153b-127">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f153b-127">Using Transact-SQL</span></span>  
  
#### <a name="to-clear-the-job-history-log"></a><span data-ttu-id="f153b-128">若要清除作業記錄檔</span><span class="sxs-lookup"><span data-stu-id="f153b-128">To clear the job history log</span></span>  
  
1.  <span data-ttu-id="f153b-129">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="f153b-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f153b-130">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="f153b-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f153b-131">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="f153b-131">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- example removes the history for a job named NightlyBackups.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_purge_jobhistory  
        @job_name = N'NightlyBackups' ;  
    GO  
    ```  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="f153b-132">使用 SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="f153b-132">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="f153b-133">**若要清除作業記錄檔**</span><span class="sxs-lookup"><span data-stu-id="f153b-133">**To clear the job history log**</span></span>  
  
 <span data-ttu-id="f153b-134">透過所選的程式語言，例如 Visual Basic、Visual C# 或 PowerShell，使用 `PurgeJobHistory` 類別的 `JobServer` 方法。</span><span class="sxs-lookup"><span data-stu-id="f153b-134">Use the `PurgeJobHistory` method of the `JobServer` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="f153b-135">如需詳細資訊，請參閱 [SQL Server 管理物件 (SMO)](https://msdn.microsoft.com/library/ms162169.aspx)。</span><span class="sxs-lookup"><span data-stu-id="f153b-135">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
  
  
