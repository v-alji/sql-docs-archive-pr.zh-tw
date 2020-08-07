---
title: 檢視作業記錄 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- viewing job history
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
- displaying job history
ms.assetid: 3bbd1556-abdb-48a3-b249-546eace76343
author: stevestein
ms.author: sstein
ms.openlocfilehash: e84fafdaeddb5748a8129cd5d71d667db7e5fa37
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703725"
---
# <a name="view-the-job-history"></a><span data-ttu-id="62199-102">檢視作業記錄</span><span class="sxs-lookup"><span data-stu-id="62199-102">View the Job History</span></span>
  <span data-ttu-id="62199-103">本主題描述如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 、或 SQL Server 管理物件，在中查看代理程式作業記錄 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="62199-103">This topic describes how to view the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job history log in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
-   <span data-ttu-id="62199-104">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="62199-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="62199-105">安全性</span><span class="sxs-lookup"><span data-stu-id="62199-105">Security</span></span>](#Security)  
  
-   <span data-ttu-id="62199-106">**若要使用下列項目檢視作業記錄：**</span><span class="sxs-lookup"><span data-stu-id="62199-106">**To view the job history log, using:**</span></span>  
  
     [<span data-ttu-id="62199-107">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="62199-107">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="62199-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="62199-108">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="62199-109">SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="62199-109">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="62199-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="62199-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="62199-111">Security</span><span class="sxs-lookup"><span data-stu-id="62199-111">Security</span></span>  
 <span data-ttu-id="62199-112">如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="62199-112">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="62199-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="62199-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-job-history-log"></a><span data-ttu-id="62199-114">若要檢視作業記錄</span><span class="sxs-lookup"><span data-stu-id="62199-114">To view the job history log</span></span>  
  
1.  <span data-ttu-id="62199-115">在**物件總管中，** 連接到的實例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然後展開該實例。</span><span class="sxs-lookup"><span data-stu-id="62199-115">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="62199-116">展開 **[SQL Server Agent]**，然後展開 **[作業]**。</span><span class="sxs-lookup"><span data-stu-id="62199-116">Expand **SQL Server Agent**, and then expand **Jobs**.</span></span>  
  
3.  <span data-ttu-id="62199-117">以滑鼠右鍵按一下作業，然後按一下 **[檢視記錄]**。</span><span class="sxs-lookup"><span data-stu-id="62199-117">Right-click a job, and then click **View History**.</span></span>  
  
4.  <span data-ttu-id="62199-118">在 [記錄檔檢視器] 中檢視作業記錄。</span><span class="sxs-lookup"><span data-stu-id="62199-118">In the Log File Viewer, view the job history.</span></span>  
  
5.  <span data-ttu-id="62199-119">若要更新作業記錄，請按一下 **[重新整理]**。</span><span class="sxs-lookup"><span data-stu-id="62199-119">To update the job history, click **Refresh**.</span></span> <span data-ttu-id="62199-120">若要檢視較少的資料列，請按一下 **[篩選]** 按鈕，並輸入篩選參數。</span><span class="sxs-lookup"><span data-stu-id="62199-120">To view fewer rows, click the **Filter** button and enter filter parameters.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="62199-121">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="62199-121">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-job-history-log"></a><span data-ttu-id="62199-122">若要檢視作業記錄</span><span class="sxs-lookup"><span data-stu-id="62199-122">To view the job history log</span></span>  
  
1.  <span data-ttu-id="62199-123">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="62199-123">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="62199-124">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="62199-124">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="62199-125">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="62199-125">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- lists all job information for the NightlyBackups job.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_jobhistory   
        @job_name = N'NightlyBackups' ;  
    GO  
    ```  
  
 <span data-ttu-id="62199-126">如需詳細資訊，請參閱[sp_help_jobhistory &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobhistory-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="62199-126">For more information, see [sp_help_jobhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobhistory-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="62199-127">使用 SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="62199-127">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="62199-128">**若要檢視作業記錄**</span><span class="sxs-lookup"><span data-stu-id="62199-128">**To view the job history log**</span></span>  
  
 <span data-ttu-id="62199-129">使用所選的程式語言，例如 Visual Basic、Visual C# 或 PowerShell，呼叫 `EnumHistory` 類別的 `Job` 方法。</span><span class="sxs-lookup"><span data-stu-id="62199-129">Call the `EnumHistory` method of the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="62199-130">如需詳細資訊，請參閱 [SQL Server 管理物件 (SMO)](https://msdn.microsoft.com/library/ms162169.aspx)。</span><span class="sxs-lookup"><span data-stu-id="62199-130">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
