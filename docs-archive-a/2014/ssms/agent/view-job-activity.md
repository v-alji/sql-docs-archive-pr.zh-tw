---
title: 檢視作業活動 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- viewing job activity
- jobs [SQL Server Agent], viewing
- SQL Server Agent jobs, viewing
- displaying job activity
ms.assetid: 5c284e5e-7775-435d-ac49-f3f12a27ddc7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 56b159952c83ed243c4c5d8012c76e5a2a248519
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708905"
---
# <a name="view-job-activity"></a><span data-ttu-id="e0d18-102">檢視作業活動</span><span class="sxs-lookup"><span data-stu-id="e0d18-102">View Job Activity</span></span>
  <span data-ttu-id="e0d18-103">此主題描述如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中檢視 [!INCLUDE[tsql](../../includes/tsql-md.md)]Agent 作業的執行階段狀態。</span><span class="sxs-lookup"><span data-stu-id="e0d18-103">This topic describes how to view the runtime state of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="e0d18-104">當 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務啟動時，會建立新的工作階段，並在 **msdb** 資料庫的 **sysjobactivity** 資料表中填入所有已定義現存作業。</span><span class="sxs-lookup"><span data-stu-id="e0d18-104">When the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service starts, a new session is created and the **sysjobactivity** table in the **msdb** database is populated with all the existing defined jobs.</span></span> <span data-ttu-id="e0d18-105">此資料表會記錄目前的作業活動及狀態。</span><span class="sxs-lookup"><span data-stu-id="e0d18-105">This table records current job activity and status.</span></span> <span data-ttu-id="e0d18-106">您可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 中的「作業活動監視器」來檢視作業目前的狀態。</span><span class="sxs-lookup"><span data-stu-id="e0d18-106">You can use the Job Activity Monitor in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to view the current state of jobs.</span></span> <span data-ttu-id="e0d18-107">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務突然終止，您可以參考 **sysjobactivity** 資料表，查看服務終止時正在執行的作業。</span><span class="sxs-lookup"><span data-stu-id="e0d18-107">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service unexpectedly terminates, you can refer to the **sysjobactivity** table to see which jobs were being executed when the service terminated.</span></span>  
  
 <span data-ttu-id="e0d18-108">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="e0d18-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e0d18-109">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="e0d18-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e0d18-110">安全性</span><span class="sxs-lookup"><span data-stu-id="e0d18-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e0d18-111">**若要使用下列項目檢視作業活動：**</span><span class="sxs-lookup"><span data-stu-id="e0d18-111">**To view job activity, using:**</span></span>  
  
     [<span data-ttu-id="e0d18-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e0d18-112">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="e0d18-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e0d18-113">Transact-SQL</span></span>](#TSQL)  
  
## <a name="before-you-begin"></a><span data-ttu-id="e0d18-114">開始之前</span><span class="sxs-lookup"><span data-stu-id="e0d18-114">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e0d18-115">Security</span><span class="sxs-lookup"><span data-stu-id="e0d18-115">Security</span></span>  
 <span data-ttu-id="e0d18-116">如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="e0d18-116">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="e0d18-117">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e0d18-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-job-activity"></a><span data-ttu-id="e0d18-118">若要檢視作業活動</span><span class="sxs-lookup"><span data-stu-id="e0d18-118">To view job activity</span></span>  
  
1.  <span data-ttu-id="e0d18-119">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="e0d18-119">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="e0d18-120">展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="e0d18-120">Expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="e0d18-121">以滑鼠右鍵按一下 [**作業活動監視器**]，然後按一下 [**查看作業活動**]。</span><span class="sxs-lookup"><span data-stu-id="e0d18-121">Right-click **Job Activity Monitor** and click **View Job Activity**.</span></span>  
  
4.  <span data-ttu-id="e0d18-122">您可以在 **[作業活動監視器]** 中檢視為此伺服器定義之每項作業的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e0d18-122">In the **Job Activity Monitor**, you can view details about each job that is defined for this server.</span></span>  
  
5.  <span data-ttu-id="e0d18-123">以滑鼠右鍵按一下作業以啟動、停止、啟用或停用作業，重新整理其顯示在「作業活動監視器」中的狀態，將其刪除，或是檢視其記錄或屬性。</span><span class="sxs-lookup"><span data-stu-id="e0d18-123">Right-click a job to start it, stop it, enable or disable it, refresh its status as displayed in the Job Activity Monitor, delete it, or view its history or properties.</span></span>  <span data-ttu-id="e0d18-124">若要啟動、停止、啟用或停用，或是重新整理多個作業，請在「作業活動監視器」中選取數個資料列，並以滑鼠右鍵按一下選取範圍。</span><span class="sxs-lookup"><span data-stu-id="e0d18-124">To start, stop, enable or disable, or refresh multiple jobs, select multiple rows in the Job Activity Monitor, and right-click your selection.</span></span>  
  
6.  <span data-ttu-id="e0d18-125">若要更新「作業活動監視器」，請按一下 **[重新整理]**。</span><span class="sxs-lookup"><span data-stu-id="e0d18-125">To update the Job Activity Monitor, click **Refresh**.</span></span> <span data-ttu-id="e0d18-126">若不要檢視那麼多資料列，請按一下 **[篩選]** ，並輸入篩選參數。</span><span class="sxs-lookup"><span data-stu-id="e0d18-126">To view fewer rows, click **Filter** and enter filter parameters.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="e0d18-127">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e0d18-127">Using Transact-SQL</span></span>  
  
#### <a name="to-view-job-activity"></a><span data-ttu-id="e0d18-128">若要檢視作業活動</span><span class="sxs-lookup"><span data-stu-id="e0d18-128">To view job activity</span></span>  
  
1.  <span data-ttu-id="e0d18-129">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e0d18-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e0d18-130">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="e0d18-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e0d18-131">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="e0d18-131">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- lists activity for all jobs that the current user has permission to view.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_jobactivity ;  
    GO  
    ```  
  
 <span data-ttu-id="e0d18-132">如需詳細資訊，請參閱[sp_help_jobactivity &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobactivity-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e0d18-132">For more information, see [sp_help_jobactivity &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobactivity-transact-sql).</span></span>  
  
  
