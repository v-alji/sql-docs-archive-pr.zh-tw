---
title: 編輯操作員 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- modifying operators
- jobs [SQL Server Agent], operators
- operators (users) [Database Engine], modifying with Management Studio
ms.assetid: b2ba2168-ca0b-4b59-9007-4e1e4c30679e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 45ffb520e240dfd97002060370ff6dcf7c60d083
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584965"
---
# <a name="edit-an-operator"></a><span data-ttu-id="8e3aa-102">編輯操作員</span><span class="sxs-lookup"><span data-stu-id="8e3aa-102">Edit an Operator</span></span>
  <span data-ttu-id="8e3aa-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中編輯操作員的可用性，以供接收通知及其電子郵件、呼叫器和 Net Send 位址。</span><span class="sxs-lookup"><span data-stu-id="8e3aa-103">This topic describes how to edit an operators' availability for receiving notifications and their e-mail, pager, and net send addresses in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="8e3aa-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="8e3aa-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="8e3aa-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="8e3aa-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="8e3aa-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="8e3aa-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="8e3aa-107">安全性</span><span class="sxs-lookup"><span data-stu-id="8e3aa-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="8e3aa-108">**若要使用下列項目編輯操作員：**</span><span class="sxs-lookup"><span data-stu-id="8e3aa-108">**To edit an operator, using:**</span></span>  
  
     [<span data-ttu-id="8e3aa-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8e3aa-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="8e3aa-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8e3aa-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8e3aa-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="8e3aa-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="8e3aa-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="8e3aa-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="8e3aa-113">呼叫器和 **net send** 選項會從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 未來版本的 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8e3aa-113">The Pager and **net send** options will be removed from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in a future version of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8e3aa-114">請避免在新的開發工作中使用這些功能，並規劃修改目前使用這些功能的應用程式。</span><span class="sxs-lookup"><span data-stu-id="8e3aa-114">Avoid using these features in new development work, and plan to modify applications that currently use these features.</span></span>  
  
-   <span data-ttu-id="8e3aa-115">請注意，必須設定 SQL Server Agent 使用 Database Mail，才能將電子郵件及呼叫器通知傳送給操作員。</span><span class="sxs-lookup"><span data-stu-id="8e3aa-115">Note that SQL Server Agent must be configured to use Database Mail to send e-mail and pager notifications to operators.</span></span> <span data-ttu-id="8e3aa-116">如需詳細資訊，請參閱＜ [指派警示給操作員](assign-alerts-to-an-operator.md)＞。</span><span class="sxs-lookup"><span data-stu-id="8e3aa-116">For more information, see [Assign Alerts to an Operator](assign-alerts-to-an-operator.md).</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="8e3aa-117">提供了一種簡單的圖形方式供您管理各項作業，建議您利用這個方式來建立和管理作業基礎結構。</span><span class="sxs-lookup"><span data-stu-id="8e3aa-117">provides an easy, graphical way to manage jobs, and is the recommended way to create and manage the job infrastructure.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8e3aa-118">Security</span><span class="sxs-lookup"><span data-stu-id="8e3aa-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8e3aa-119">權限</span><span class="sxs-lookup"><span data-stu-id="8e3aa-119">Permissions</span></span>  
 <span data-ttu-id="8e3aa-120">只有 **系統管理員 (sysadmin)** 固定伺服器角色的成員，才可以編輯操作員。</span><span class="sxs-lookup"><span data-stu-id="8e3aa-120">Only members of the **sysadmin** fixed server role can edit operators.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="8e3aa-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8e3aa-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-edit-an-operator"></a><span data-ttu-id="8e3aa-122">若要編輯操作員</span><span class="sxs-lookup"><span data-stu-id="8e3aa-122">To edit an operator</span></span>  
  
1.  <span data-ttu-id="8e3aa-123">在 **[物件總管]** 中，按一下加號，展開包含要編輯之操作員的伺服器。</span><span class="sxs-lookup"><span data-stu-id="8e3aa-123">In **Object Explorer**, click the plus sign to expand the server that contains the operator you want to edit.</span></span>  
  
2.  <span data-ttu-id="8e3aa-124">按一下加號展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="8e3aa-124">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="8e3aa-125">按一下加號展開 **[操作員]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="8e3aa-125">Click the plus sign to expand the **Operators** folder.</span></span>  
  
4.  <span data-ttu-id="8e3aa-126">以滑鼠右鍵按一下您要編輯的操作員，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8e3aa-126">Right-click the operator that you want to edit and select **Properties**.</span></span>  
  
     <span data-ttu-id="8e3aa-127">如需 [<操作員名稱> 屬性]__\*\*\*\* 對話方塊中之可用選項的詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="8e3aa-127">For more information on the available options contained in the _operator_name_**Properties** dialog box, see:</span></span>  
  
    -   [<span data-ttu-id="8e3aa-128">操作員屬性和 New 運算子 &#40;一般頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="8e3aa-128">Operator Properties and New Operator &#40;General Page&#41;</span></span>](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
    -   [<span data-ttu-id="8e3aa-129">操作員屬性：新的操作員 &#40;通知頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="8e3aa-129">Operator Properties: New Operator &#40;Notifications Page&#41;</span></span>](operator-properties-new-operator-notifications-page.md)  
  
    -   [<span data-ttu-id="8e3aa-130">操作員屬性 &#40;記錄頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="8e3aa-130">Operator Properties &#40;History Page&#41;</span></span>](operator-properties-history-page.md)  
  
5.  <span data-ttu-id="8e3aa-131">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="8e3aa-131">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="8e3aa-132">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8e3aa-132">Using Transact-SQL</span></span>  
  
#### <a name="to-edit-an-operator"></a><span data-ttu-id="8e3aa-133">若要編輯操作員</span><span class="sxs-lookup"><span data-stu-id="8e3aa-133">To edit an operator</span></span>  
  
1.  <span data-ttu-id="8e3aa-134">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="8e3aa-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="8e3aa-135">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="8e3aa-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="8e3aa-136">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="8e3aa-136">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- updates the operator status to enabled, and sets the days   
    -- (from Monday through Friday, from 8 A.M. through 5 P.M.) when the operator can be paged.   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_operator   
        @name = N'Fran??ois Ajenstat',  
        @enabled = 1,  
        @email_address = N'fran??oisa',  
        @pager_address = N'5551290AW@pager.Adventure-Works.com',  
        @weekday_pager_start_time = 080000,  
        @weekday_pager_end_time = 170000,  
        @pager_days = 64 ;  
    GO  
    ```  
  
 <span data-ttu-id="8e3aa-137">如需詳細資訊，請參閱[sp_update_operator &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-operator-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="8e3aa-137">For more information, see [sp_update_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-operator-transact-sql).</span></span>  
  
  
