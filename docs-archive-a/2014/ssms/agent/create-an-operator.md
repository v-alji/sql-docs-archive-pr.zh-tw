---
title: 建立操作員 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- jobs [SQL Server Agent], notification options
- operators (users) [Database Engine], creating with Management Studio
- SQL Server Agent jobs, notification options
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
ms.assetid: 1359d790-5905-4927-a208-e7155e7768a2
author: stevestein
ms.author: sstein
ms.openlocfilehash: dfe07042f9a4b8ac595ada8b86e7bad131032700
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699256"
---
# <a name="create-an-operator"></a><span data-ttu-id="358f8-102">建立操作員</span><span class="sxs-lookup"><span data-stu-id="358f8-102">Create an Operator</span></span>
  <span data-ttu-id="358f8-103">本主題描述如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 使用或，在中設定使用者，以接收 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業的通知 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="358f8-103">This topic describes how to configure a user to receive notifications about [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="358f8-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="358f8-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="358f8-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="358f8-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="358f8-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="358f8-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="358f8-107">安全性</span><span class="sxs-lookup"><span data-stu-id="358f8-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="358f8-108">**若要使用下列項目建立操作員：**</span><span class="sxs-lookup"><span data-stu-id="358f8-108">**To create an operator, using:**</span></span>  
  
     [<span data-ttu-id="358f8-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="358f8-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="358f8-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="358f8-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="358f8-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="358f8-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="358f8-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="358f8-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="358f8-113">呼叫器和 **net send** 選項會從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 未來版本的 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="358f8-113">The Pager and **net send** options will be removed from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in a future version of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="358f8-114">請避免在新的開發工作中使用這些功能，並規劃修改目前使用這些功能的應用程式。</span><span class="sxs-lookup"><span data-stu-id="358f8-114">Avoid using these features in new development work, and plan to modify applications that currently use these features.</span></span>  
  
-   <span data-ttu-id="358f8-115">請注意，必須設定 SQL Server Agent 使用 Database Mail，才能將電子郵件及呼叫器通知傳送給操作員。</span><span class="sxs-lookup"><span data-stu-id="358f8-115">Note that SQL Server Agent must be configured to use Database Mail to send e-mail and pager notifications to operators.</span></span> <span data-ttu-id="358f8-116">如需詳細資訊，請參閱＜ [指派警示給操作員](assign-alerts-to-an-operator.md)＞。</span><span class="sxs-lookup"><span data-stu-id="358f8-116">For more information, see [Assign Alerts to an Operator](assign-alerts-to-an-operator.md).</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="358f8-117">提供了一種簡單的圖形方式供您管理各項作業，建議您利用這個方式來建立和管理作業基礎結構。</span><span class="sxs-lookup"><span data-stu-id="358f8-117">provides an easy, graphical way to manage jobs, and is the recommended way to create and manage the job infrastructure.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="358f8-118">Security</span><span class="sxs-lookup"><span data-stu-id="358f8-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="358f8-119">權限</span><span class="sxs-lookup"><span data-stu-id="358f8-119">Permissions</span></span>  
 <span data-ttu-id="358f8-120">只有 **系統管理員 (sysadmin)** 固定伺服器角色的成員，才可以建立操作員。</span><span class="sxs-lookup"><span data-stu-id="358f8-120">Only members of the **sysadmin** fixed server role can create operators.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="358f8-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="358f8-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-an-operator"></a><span data-ttu-id="358f8-122">若要建立操作員</span><span class="sxs-lookup"><span data-stu-id="358f8-122">To create an operator</span></span>  
  
1.  <span data-ttu-id="358f8-123">在 **[物件總管]** 中，按一下加號展開要建立 SQL Server Agent 操作員的伺服器。</span><span class="sxs-lookup"><span data-stu-id="358f8-123">In **Object Explorer**, click the plus sign to expand the server where you want to create a SQL Server Agent operator.</span></span>  
  
2.  <span data-ttu-id="358f8-124">按一下加號展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="358f8-124">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="358f8-125">以滑鼠右鍵按一下 [操作員]\*\*\*\* 資料夾，然後選取 [新增操作員]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="358f8-125">Right-click the **Operators** folder and select **New Operator**.</span></span>  
  
     <span data-ttu-id="358f8-126">下列選項可從 **[新增操作員]** 對話方塊的 **[一般]** 頁面取得：</span><span class="sxs-lookup"><span data-stu-id="358f8-126">The following options are available on the **General** page of the **New Operator** dialog box:</span></span>  
  
     <span data-ttu-id="358f8-127">**名稱**</span><span class="sxs-lookup"><span data-stu-id="358f8-127">**Name**</span></span>  
     <span data-ttu-id="358f8-128">變更操作員的名稱。</span><span class="sxs-lookup"><span data-stu-id="358f8-128">Change the name of the operator.</span></span>  
  
     <span data-ttu-id="358f8-129">**已啟用**</span><span class="sxs-lookup"><span data-stu-id="358f8-129">**Enabled**</span></span>  
     <span data-ttu-id="358f8-130">啟用操作員。</span><span class="sxs-lookup"><span data-stu-id="358f8-130">Enable the operator.</span></span> <span data-ttu-id="358f8-131">未啟用時，不會傳送通知給操作員。</span><span class="sxs-lookup"><span data-stu-id="358f8-131">When not enabled, no notifications are sent to the operator.</span></span>  
  
     <span data-ttu-id="358f8-132">**電子郵件名稱**</span><span class="sxs-lookup"><span data-stu-id="358f8-132">**E-mail name**</span></span>  
     <span data-ttu-id="358f8-133">指定操作員的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="358f8-133">Specifies the e-mail address for the operator.</span></span>  
  
     <span data-ttu-id="358f8-134">**Net Send 位址**</span><span class="sxs-lookup"><span data-stu-id="358f8-134">**Net send address**</span></span>  
     <span data-ttu-id="358f8-135">指定用於 **net send**的位址。</span><span class="sxs-lookup"><span data-stu-id="358f8-135">Specify the address to use for **net send**.</span></span>  
  
     <span data-ttu-id="358f8-136">**呼叫器電子郵件名稱**</span><span class="sxs-lookup"><span data-stu-id="358f8-136">**Pager e-mail name**</span></span>  
     <span data-ttu-id="358f8-137">指定操作員呼叫器所用的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="358f8-137">Specifies the e-mail address to use for the operator's pager.</span></span>  
  
     <span data-ttu-id="358f8-138">**傳呼待命排程**</span><span class="sxs-lookup"><span data-stu-id="358f8-138">**Pager on duty schedule**</span></span>  
     <span data-ttu-id="358f8-139">設定呼叫器使用中的時間。</span><span class="sxs-lookup"><span data-stu-id="358f8-139">Sets the times at which the pager is active.</span></span>  
  
     <span data-ttu-id="358f8-140">**星期一至星期日**</span><span class="sxs-lookup"><span data-stu-id="358f8-140">**Monday - Sunday**</span></span>  
     <span data-ttu-id="358f8-141">選取呼叫器使用中的日子。</span><span class="sxs-lookup"><span data-stu-id="358f8-141">Select the days that the pager is active.</span></span>  
  
     <span data-ttu-id="358f8-142">**工作日開始**</span><span class="sxs-lookup"><span data-stu-id="358f8-142">**Workday begin**</span></span>  
     <span data-ttu-id="358f8-143">選取時間，在該時間之後 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 就會傳送訊息給呼叫器。</span><span class="sxs-lookup"><span data-stu-id="358f8-143">Select the time of day after which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sends messages to the pager.</span></span>  
  
     <span data-ttu-id="358f8-144">**工作日結束**</span><span class="sxs-lookup"><span data-stu-id="358f8-144">**Workday end**</span></span>  
     <span data-ttu-id="358f8-145">選取時間，在該時間之後 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 就不再傳送訊息給呼叫器。</span><span class="sxs-lookup"><span data-stu-id="358f8-145">Select the time of day after which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent no longer sends messages to the pager.</span></span>  
  
     <span data-ttu-id="358f8-146">下列選項可從 **[新增操作員]** 對話方塊的 **[通知]** 頁面取得：</span><span class="sxs-lookup"><span data-stu-id="358f8-146">The following options are available on the **Notifications** page of the **New Operator** dialog box:</span></span>  
  
     <span data-ttu-id="358f8-147">**警示**</span><span class="sxs-lookup"><span data-stu-id="358f8-147">**Alerts**</span></span>  
     <span data-ttu-id="358f8-148">檢視執行個體中的警示。</span><span class="sxs-lookup"><span data-stu-id="358f8-148">View the alerts in the instance.</span></span>  
  
     <span data-ttu-id="358f8-149">**作業**</span><span class="sxs-lookup"><span data-stu-id="358f8-149">**Jobs**</span></span>  
     <span data-ttu-id="358f8-150">檢視執行個體中的作業。</span><span class="sxs-lookup"><span data-stu-id="358f8-150">View the jobs in the instance.</span></span>  
  
     <span data-ttu-id="358f8-151">**警示清單**</span><span class="sxs-lookup"><span data-stu-id="358f8-151">**Alert list**</span></span>  
     <span data-ttu-id="358f8-152">列出執行個體中的警示。</span><span class="sxs-lookup"><span data-stu-id="358f8-152">Lists the alerts in the instance.</span></span>  
  
     <span data-ttu-id="358f8-153">**作業清單**</span><span class="sxs-lookup"><span data-stu-id="358f8-153">**Job list**</span></span>  
     <span data-ttu-id="358f8-154">列出執行個體中的作業。</span><span class="sxs-lookup"><span data-stu-id="358f8-154">Lists the jobs in the instance.</span></span>  
  
     <span data-ttu-id="358f8-155">**位址**</span><span class="sxs-lookup"><span data-stu-id="358f8-155">**E-mail**</span></span>  
     <span data-ttu-id="358f8-156">使用電子郵件通知此操作員。</span><span class="sxs-lookup"><span data-stu-id="358f8-156">Notify this operator using e-mail.</span></span>  
  
     <span data-ttu-id="358f8-157">**呼叫器**</span><span class="sxs-lookup"><span data-stu-id="358f8-157">**Pager**</span></span>  
     <span data-ttu-id="358f8-158">將電子郵件傳送至呼叫器位址，來通知此操作員。</span><span class="sxs-lookup"><span data-stu-id="358f8-158">Notify this operator by sending e-mail to the pager address.</span></span>  
  
     <span data-ttu-id="358f8-159">**Net send**</span><span class="sxs-lookup"><span data-stu-id="358f8-159">**Net send**</span></span>  
     <span data-ttu-id="358f8-160">使用 **net send**通知此操作員。</span><span class="sxs-lookup"><span data-stu-id="358f8-160">Notify this operator using **net send**.</span></span>  
  
4.  <span data-ttu-id="358f8-161">完成建立新的操作員後，請按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="358f8-161">When finished creating the new operator, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="358f8-162">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="358f8-162">Using Transact-SQL</span></span>  
  
#### <a name="to-create-an-operator"></a><span data-ttu-id="358f8-163">若要建立操作員</span><span class="sxs-lookup"><span data-stu-id="358f8-163">To create an operator</span></span>  
  
1.  <span data-ttu-id="358f8-164">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="358f8-164">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="358f8-165">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="358f8-165">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="358f8-166">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="358f8-166">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- sets up the operator information for user 'danwi.' The operator is enabled.   
    -- SQL Server Agent sends notifications by pager from Monday through Friday from 8 A.M. to 5 P.M.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_operator  
        @name = N'Dan Wilson',  
        @enabled = 1,  
        @email_address = N'danwi',  
        @pager_address = N'5551290AW@pager.Adventure-Works.com',  
        @weekday_pager_start_time = 080000,  
        @weekday_pager_end_time = 170000,  
        @pager_days = 62 ;  
    GO  
    ```  
  
 <span data-ttu-id="358f8-167">如需詳細資訊，請參閱[sp_add_operator &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-operator-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="358f8-167">For more information, see [sp_add_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-operator-transact-sql).</span></span>  
  
  
