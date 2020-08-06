---
title: 使用錯誤號碼來建立警示 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- alerts [SQL Server], creating
- SQL Server Agent, alerts
- alerts [SQL Server], error numbers
ms.assetid: 03dd7fac-5073-4f86-babd-37e45a86023c
author: stevestein
ms.author: sstein
ms.openlocfilehash: a98f64bc5b9dffc3e2494a0c36c8fc04cdfb6fa2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597006"
---
# <a name="create-an-alert-using-an-error-number"></a><span data-ttu-id="7c90a-102">使用錯誤號碼建立警示</span><span class="sxs-lookup"><span data-stu-id="7c90a-102">Create an Alert Using an Error Number</span></span>
  <span data-ttu-id="7c90a-103">本主題描述如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在中建立 Agent 警示 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，當使用或發生特定數位的錯誤時，就會引發 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7c90a-103">This topic describes how to create a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alert occurs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] that will be raised when an error of a specific number occurs by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="7c90a-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="7c90a-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="7c90a-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="7c90a-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="7c90a-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="7c90a-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="7c90a-107">安全性</span><span class="sxs-lookup"><span data-stu-id="7c90a-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="7c90a-108">**若要使用下列項目，使用錯誤號碼建立警示：**</span><span class="sxs-lookup"><span data-stu-id="7c90a-108">**To create an alert using an error number, using:**</span></span>  
  
     [<span data-ttu-id="7c90a-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="7c90a-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="7c90a-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7c90a-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7c90a-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="7c90a-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="7c90a-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="7c90a-112">Limitations and Restrictions</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="7c90a-113">提供了一種簡單的圖形方式供您管理整個警示系統，建議您利用這個方式來設定警示基礎結構。</span><span class="sxs-lookup"><span data-stu-id="7c90a-113">provides an easy, graphical way to manage the entire alerting system and is the recommended way to configure an alert infrastructure.</span></span>  
  
-   <span data-ttu-id="7c90a-114">**xp_logevent** 產生的事件出現在 master 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="7c90a-114">Events generated with **xp_logevent** occur in the master database.</span></span> <span data-ttu-id="7c90a-115">因此，除非警示的 **xp_logevent** 是 **@database_name** 或 NULL，否則， **xp_logevent** 不會觸發警示。</span><span class="sxs-lookup"><span data-stu-id="7c90a-115">Therefore, **xp_logevent** does not trigger an alert unless the **@database_name** for the alert is **'master'** or NULL.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7c90a-116">Security</span><span class="sxs-lookup"><span data-stu-id="7c90a-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7c90a-117">權限</span><span class="sxs-lookup"><span data-stu-id="7c90a-117">Permissions</span></span>  
 <span data-ttu-id="7c90a-118">依預設，只有 **系統管理員 (sysadmin)** 固定伺服器角色的成員，才能夠執行 **sp_add_alert**。</span><span class="sxs-lookup"><span data-stu-id="7c90a-118">By default, only members of the **sysadmin** fixed server role can execute **sp_add_alert**.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="7c90a-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="7c90a-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-an-alert-using-an-error-number"></a><span data-ttu-id="7c90a-120">若要使用錯誤號碼建立警示</span><span class="sxs-lookup"><span data-stu-id="7c90a-120">To create an alert using an error number</span></span>  
  
1.  <span data-ttu-id="7c90a-121">在 **[物件總管]** 中，按一下加號，以展開您要使用錯誤號碼建立警示的伺服器。</span><span class="sxs-lookup"><span data-stu-id="7c90a-121">In **Object Explorer,** click the plus sign to expand the server where you want to create an alert using an error number.</span></span>  
  
2.  <span data-ttu-id="7c90a-122">按一下加號展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="7c90a-122">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="7c90a-123">以滑鼠右鍵按一下 **[警示]** ，然後選取 **[新增警示]**。</span><span class="sxs-lookup"><span data-stu-id="7c90a-123">Right-click **Alerts** and select **New Alert**.</span></span>  
  
4.  <span data-ttu-id="7c90a-124">在 **[新增警示]** 對話方塊中的 **[名稱]** 方塊，輸入此警示的名稱。</span><span class="sxs-lookup"><span data-stu-id="7c90a-124">In the **New Alert** dialog box, in the **Name** box, enter a name for this alert.</span></span>  
  
5.  <span data-ttu-id="7c90a-125">選取 **[啟用]** 核取方塊以讓警示得以執行。</span><span class="sxs-lookup"><span data-stu-id="7c90a-125">Check the **Enable** check box to enable the alert to run.</span></span> <span data-ttu-id="7c90a-126">根據預設，會選取 **[啟用]** 。</span><span class="sxs-lookup"><span data-stu-id="7c90a-126">By default, **Enable** is checked.</span></span>  
  
6.  <span data-ttu-id="7c90a-127">在 **[類型]** 清單中，選取 **[SQL Server 事件警示]**。</span><span class="sxs-lookup"><span data-stu-id="7c90a-127">In the **Type** list, select **SQL Server event alert**.</span></span>  
  
7.  <span data-ttu-id="7c90a-128">在 **[事件警示定義]** 下，從 **[資料庫名稱]** 清單中選取資料庫，將警示限制在特定資料庫。</span><span class="sxs-lookup"><span data-stu-id="7c90a-128">Under **Event alert definition**, in the **Database name** list, select a database to restrict the alert to a specific database.</span></span>  
  
8.  <span data-ttu-id="7c90a-129">在 **[將根據下列條件引發警示]** 下，按一下 **[錯誤號碼]**，然後為警示輸入有效的錯誤號碼。</span><span class="sxs-lookup"><span data-stu-id="7c90a-129">Under **Alerts will be raised based on**, click **Error number**, and then type a valid error number for the alert.</span></span> <span data-ttu-id="7c90a-130">或者，按一下 **[嚴重性]** ，然後選取將會引發警示的特定嚴重性。</span><span class="sxs-lookup"><span data-stu-id="7c90a-130">Alternately, click **Severity** and then select the specific severity that will raise the alert.</span></span>  
  
9. <span data-ttu-id="7c90a-131">核取對應到 **[訊息包含下列內容時引發警示]** 核取方塊，將警示限制在特定字元順序，然後在 **[訊息文字]** 中輸入關鍵字或字元字串。</span><span class="sxs-lookup"><span data-stu-id="7c90a-131">Check the box corresponding to **Raise alert when message contains** check box to restrict the alert to a particular character sequence, and then enter a keyword or character string for the **Message text**.</span></span> <span data-ttu-id="7c90a-132">最大字元數為 100。</span><span class="sxs-lookup"><span data-stu-id="7c90a-132">The maximum number of characters is 100.</span></span>  
  
10. <span data-ttu-id="7c90a-133">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="7c90a-133">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="7c90a-134">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7c90a-134">Using Transact-SQL</span></span>  
  
#### <a name="to-create-an-alert-using-an-error-number"></a><span data-ttu-id="7c90a-135">若要使用錯誤號碼建立警示</span><span class="sxs-lookup"><span data-stu-id="7c90a-135">To create an alert using an error number</span></span>  
  
1.  <span data-ttu-id="7c90a-136">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7c90a-136">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="7c90a-137">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="7c90a-137">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="7c90a-138">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="7c90a-138">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- adds an alert (Test Alert) that runs the Back up the AdventureWorks2012 Database job when fired   
    -- assumes that the message 55001 and the Back up the AdventureWorks2012 Database job already exist.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_alert  
        @name = N'Test Alert',  
        @message_id = 55001,   
       @severity = 0,   
       @notification_message = N'Error 55001 has occurred. The database will be backed up...',   
       @job_name = N'Back up the AdventureWorks2012 Database' ;  
    GO  
    ```  
  
 <span data-ttu-id="7c90a-139">如需詳細資訊，請參閱[sp_add_alert &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7c90a-139">For more information, see [sp_add_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql).</span></span>  
  
  
