---
title: 建立排程 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- scheduling jobs [SQL Server]
- SQL Server Agent jobs, scheduling
- jobs [SQL Server Agent], scheduling
- schedules [SQL Server], jobs
ms.assetid: 8c7ef3b3-c06d-4a27-802d-ed329dc86ef3
author: stevestein
ms.author: sstein
ms.openlocfilehash: ac71a61163dceb06697b61ef24fce2117d57cf2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599323"
---
# <a name="create-a-schedule"></a><span data-ttu-id="8cf66-102">Create a Schedule</span><span class="sxs-lookup"><span data-stu-id="8cf66-102">Create a Schedule</span></span>
  <span data-ttu-id="8cf66-103">您可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 SQL Server 管理物件，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中建立 [!INCLUDE[tsql](../../includes/tsql-md.md)]Agent 作業的排程。</span><span class="sxs-lookup"><span data-stu-id="8cf66-103">You can create a schedule for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
-   <span data-ttu-id="8cf66-104">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="8cf66-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="8cf66-105">安全性</span><span class="sxs-lookup"><span data-stu-id="8cf66-105">Security</span></span>](#Security)  
  
-   <span data-ttu-id="8cf66-106">**若要使用下列項目建立排程：**</span><span class="sxs-lookup"><span data-stu-id="8cf66-106">**To create a schedule, using:**</span></span>  
  
     [<span data-ttu-id="8cf66-107">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8cf66-107">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="8cf66-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8cf66-108">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="8cf66-109">SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="8cf66-109">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8cf66-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="8cf66-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8cf66-111">Security</span><span class="sxs-lookup"><span data-stu-id="8cf66-111">Security</span></span>  
 <span data-ttu-id="8cf66-112">如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="8cf66-112">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="8cf66-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8cf66-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-schedule"></a><span data-ttu-id="8cf66-114">建立排程</span><span class="sxs-lookup"><span data-stu-id="8cf66-114">To create a schedule</span></span>  
  
1.  <span data-ttu-id="8cf66-115">在**物件總管中，** 連接到的實例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然後展開該實例。</span><span class="sxs-lookup"><span data-stu-id="8cf66-115">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="8cf66-116">展開 **[SQL Server Agent]**、以滑鼠右鍵按一下 **[作業]**，然後選取 **[管理排程]**。</span><span class="sxs-lookup"><span data-stu-id="8cf66-116">Expand **SQL Server Agent**, right-click **Jobs**, and select **Manage Schedules**.</span></span>  
  
3.  <span data-ttu-id="8cf66-117">在 **[管理排程]** 對話方塊中，按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="8cf66-117">In the **Manage Schedules** dialog box, click **New**.</span></span>  
  
4.  <span data-ttu-id="8cf66-118">在 **[名稱]** 方塊中，輸入新排程的名稱。</span><span class="sxs-lookup"><span data-stu-id="8cf66-118">In the **Name** box, type a name for the new schedule.</span></span>  
  
5.  <span data-ttu-id="8cf66-119">如果您不想要讓排程在建立之後立即生效，請清除 **[已啟用]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="8cf66-119">If you do not want the schedule to take effect immediately after it has been created, clear the **Enabled** check box.</span></span>  
  
6.  <span data-ttu-id="8cf66-120">針對 **[排程類型]**，選取下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="8cf66-120">For **Schedule Type**, select one of the following:</span></span>  
  
    -   <span data-ttu-id="8cf66-121">若要在 CPU 達到閒置條件時啟動此作業，請按一下 **[只要 CPU 閒置就啟動]**。</span><span class="sxs-lookup"><span data-stu-id="8cf66-121">To start the job when the CPUs reach an idle condition, click **Start whenever the CPUs become idle**.</span></span>  
  
    -   <span data-ttu-id="8cf66-122">如果您想要重複執行排程，按一下 **[重複執行]**。</span><span class="sxs-lookup"><span data-stu-id="8cf66-122">If you want a schedule to run repeatedly, click **Recurring**.</span></span> <span data-ttu-id="8cf66-123">若要設定重複執行的排程，請完成對話方塊上的 **[頻率]**、 **[每日頻率]** 和 **[持續時間]** 群組。</span><span class="sxs-lookup"><span data-stu-id="8cf66-123">To set the recurring schedule, complete the **Frequency**, **Daily Frequency**, and **Duration** groups on the dialog.</span></span>  
  
    -   <span data-ttu-id="8cf66-124">如果您想要讓排程只執行一次，請按一下 **[執行一次]**。</span><span class="sxs-lookup"><span data-stu-id="8cf66-124">If you want the schedule to run only one time, click **One time**.</span></span> <span data-ttu-id="8cf66-125">若要設定 **[執行一次]** 排程，請完成對話方塊上的 **[僅發生一次]** 群組。</span><span class="sxs-lookup"><span data-stu-id="8cf66-125">To set the **One time** schedule, complete the **One-time occurrence** group on the dialog box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="8cf66-126">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8cf66-126">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-schedule"></a><span data-ttu-id="8cf66-127">建立排程</span><span class="sxs-lookup"><span data-stu-id="8cf66-127">To create a schedule</span></span>  
  
1.  <span data-ttu-id="8cf66-128">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="8cf66-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="8cf66-129">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="8cf66-129">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="8cf66-130">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="8cf66-130">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- creates a schedule named RunOnce.   
    -- The schedule runs one time, at 23:30 on the day that the schedule is created.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_schedule  
        @schedule_name = N'RunOnce',  
        @freq_type = 1,  
        @active_start_time = 233000 ;  
  
    GO  
    ```  
  
 <span data-ttu-id="8cf66-131">如需詳細資訊，請參閱[sp_add_schedule &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="8cf66-131">For more information, see [sp_add_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="8cf66-132">使用 SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="8cf66-132">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="8cf66-133">**建立排程**</span><span class="sxs-lookup"><span data-stu-id="8cf66-133">**To create a schedule**</span></span>  
  
 <span data-ttu-id="8cf66-134">透過所選的程式語言，例如 Visual Basic、Visual C# 或 PowerShell，使用 `JobSchedule` 類別。</span><span class="sxs-lookup"><span data-stu-id="8cf66-134">Use the `JobSchedule` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="8cf66-135">如需詳細資訊，請參閱 [SQL Server 管理物件 (SMO)](https://msdn.microsoft.com/library/ms162169.aspx)。</span><span class="sxs-lookup"><span data-stu-id="8cf66-135">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
