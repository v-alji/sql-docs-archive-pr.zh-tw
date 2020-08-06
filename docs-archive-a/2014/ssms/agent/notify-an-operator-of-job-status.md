---
title: 通知操作員作業狀態 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- status information [SQL Server], jobs
- jobs [SQL Server Agent], notification options
- SQL Server Agent jobs, status
- jobs [SQL Server Agent], status
- SQL Server Agent jobs, notification options
- notifications [SQL Server], job status
ms.assetid: e7399505-27ac-48d9-a637-73bf92b9df49
author: stevestein
ms.author: sstein
ms.openlocfilehash: a202327ad63cf7ef8f51d3572b257816ee6d9419
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594333"
---
# <a name="notify-an-operator-of-job-status"></a><span data-ttu-id="44e68-102">通知操作員作業狀態</span><span class="sxs-lookup"><span data-stu-id="44e68-102">Notify an Operator of Job Status</span></span>
  <span data-ttu-id="44e68-103">本主題描述如何 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 使用、或 SQL Server 管理物件，在中設定通知選項 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ，讓 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 可以將有關作業的通知傳送給操作員。</span><span class="sxs-lookup"><span data-stu-id="44e68-103">This topic describes how to set notification options in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects, so [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent can send notifications to operators about jobs.</span></span>  
  
 <span data-ttu-id="44e68-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="44e68-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="44e68-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="44e68-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="44e68-106">安全性</span><span class="sxs-lookup"><span data-stu-id="44e68-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="44e68-107">**若要使用下列項目通知操作員作業狀態：**</span><span class="sxs-lookup"><span data-stu-id="44e68-107">**To notify an operator of job status, using:**</span></span>  
  
     [<span data-ttu-id="44e68-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="44e68-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="44e68-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="44e68-109">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="44e68-110">SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="44e68-110">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="44e68-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="44e68-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="44e68-112">Security</span><span class="sxs-lookup"><span data-stu-id="44e68-112">Security</span></span>  
 <span data-ttu-id="44e68-113">如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="44e68-113">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="44e68-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="44e68-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-notify-an-operator-of-job-status"></a><span data-ttu-id="44e68-115">若要通知操作員作業狀態</span><span class="sxs-lookup"><span data-stu-id="44e68-115">To notify an operator of job status</span></span>  
  
1.  <span data-ttu-id="44e68-116">在**物件總管中，** 連接到的實例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然後展開該實例。</span><span class="sxs-lookup"><span data-stu-id="44e68-116">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="44e68-117">依序展開 [SQL Server Agent]\*\*\*\* 和 [作業]\*\*\*\*、以滑鼠右鍵按一下要編輯的作業，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="44e68-117">Expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to edit, and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="44e68-118">在 **[作業屬性]** 對話方塊中，選取 **[通知]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="44e68-118">In the **Job Properties** dialog box, select the **Notifications** page.</span></span>  
  
4.  <span data-ttu-id="44e68-119">如果您想以電子郵件通知操作員，請核取 [電子郵件]\*\*\*\*、從清單選取操作員，然後選取下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="44e68-119">If you want to notify an operator by e-mail, check **E-mail**, select an operator from the list, and then select one of the following:</span></span>  
  
    -   <span data-ttu-id="44e68-120">**[當作業成功時]** 即可在作業順利完成時，通知操作員。</span><span class="sxs-lookup"><span data-stu-id="44e68-120">**When the job succeeds** to notify the operator when the job completes successfully.</span></span>  
  
    -   <span data-ttu-id="44e68-121">**[當作業失敗時]** 會在作業未順利完成時通知操作員。</span><span class="sxs-lookup"><span data-stu-id="44e68-121">**When the job fails** to notify the operator when the job completes unsuccessfully.</span></span>  
  
    -   <span data-ttu-id="44e68-122">**[作業完成時]** 可在無論完成狀態為何，都通知操作員。</span><span class="sxs-lookup"><span data-stu-id="44e68-122">**When the job completes** to notify the operator regardless of completion status.</span></span>  
  
5.  <span data-ttu-id="44e68-123">如果您想以呼叫器來通知操作員，請核取 **[呼叫器]**、從清單選取操作員，然後選取下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="44e68-123">If you want to notify an operator by pager, check **Page**, select an operator from the list, and then select one of the following:</span></span>  
  
    -   <span data-ttu-id="44e68-124">**[當作業成功時]** 即可在作業順利完成時，通知操作員。</span><span class="sxs-lookup"><span data-stu-id="44e68-124">**When the job succeeds** to notify the operator when the job completes successfully.</span></span>  
  
    -   <span data-ttu-id="44e68-125">**[當作業失敗時]** 會在作業未順利完成時通知操作員。</span><span class="sxs-lookup"><span data-stu-id="44e68-125">**When the job fails** to notify the operator when the job completes unsuccessfully.</span></span>  
  
    -   <span data-ttu-id="44e68-126">**[作業完成時]** 可在無論完成狀態為何，都通知操作員。</span><span class="sxs-lookup"><span data-stu-id="44e68-126">**When the job completes** to notify the operator regardless of completion status.</span></span>  
  
6.  <span data-ttu-id="44e68-127">如果您想以網路傳送的方式來通知操作員，請核取 **[網路傳送]**、從清單選取操作員，然後選取下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="44e68-127">If you want to notify an operator by net send, check **Net send**, select an operator from the list, and then select one of the following:</span></span>  
  
    -   <span data-ttu-id="44e68-128">**[當作業成功時]** 即可在作業順利完成時，通知操作員。</span><span class="sxs-lookup"><span data-stu-id="44e68-128">**When the job succeeds** to notify the operator when the job completes successfully.</span></span>  
  
    -   <span data-ttu-id="44e68-129">**[當作業失敗時]** 會在作業未順利完成時通知操作員。</span><span class="sxs-lookup"><span data-stu-id="44e68-129">**When the job fails** to notify the operator when the job completes unsuccessfully.</span></span>  
  
    -   <span data-ttu-id="44e68-130">**[作業完成時]** 可在無論完成狀態為何，都通知操作員。</span><span class="sxs-lookup"><span data-stu-id="44e68-130">**When the job completes** to notify the operator regardless of completion status.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="44e68-131">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="44e68-131">Using Transact-SQL</span></span>  
  
#### <a name="to-notify-an-operator-of-job-status"></a><span data-ttu-id="44e68-132">若要通知操作員作業狀態</span><span class="sxs-lookup"><span data-stu-id="44e68-132">To notify an operator of job status</span></span>  
  
1.  <span data-ttu-id="44e68-133">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="44e68-133">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="44e68-134">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="44e68-134">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="44e68-135">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="44e68-135">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- adds an e-mail notification for the specified alert (Test Alert).  
    -- This example assumes that Test Alert already exists and that Fran??ois Ajenstat is a valid operator name.  
    USE msdb ;  
    GO  
    EXEC dbo.sp_add_notification   
    @alert_name = N'Test Alert',   
    @operator_name = N'Fran??ois Ajenstat',   
    @notification_method = 1 ;  
    GO  
    ```  
  
 <span data-ttu-id="44e68-136">如需詳細資訊，請參閱[sp_add_notification &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="44e68-136">For more information, see [sp_add_notification &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="44e68-137">使用 SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="44e68-137">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="44e68-138">**若要通知操作員作業狀態**</span><span class="sxs-lookup"><span data-stu-id="44e68-138">**To notify an operator of job status**</span></span>  
  
 <span data-ttu-id="44e68-139">透過所選的程式語言，例如 Visual Basic、Visual C# 或 PowerShell，使用 `Job` 類別。</span><span class="sxs-lookup"><span data-stu-id="44e68-139">Use the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="44e68-140">如需詳細資訊，請參閱 [SQL Server 管理物件 (SMO)](https://msdn.microsoft.com/library/ms162169.aspx)。</span><span class="sxs-lookup"><span data-stu-id="44e68-140">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
