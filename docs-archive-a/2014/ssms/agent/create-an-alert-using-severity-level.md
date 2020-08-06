---
title: 使用嚴重性層級來建立警示 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- alerts [SQL Server], creating
- SQL Server Agent, alerts
- severity levels [SQL Server]
- alerts [SQL Server], severity levels
ms.assetid: a1fd71bf-5bf9-4ce2-9a1d-032576a4a6e9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6ee353129d60fe7fc8bed0eff279920d8d4ba640
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703741"
---
# <a name="create-an-alert-using-severity-level"></a><span data-ttu-id="9747c-102">Create an Alert Using Severity Level</span><span class="sxs-lookup"><span data-stu-id="9747c-102">Create an Alert Using Severity Level</span></span>
  <span data-ttu-id="9747c-103">本主題描述如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用或，建立在中發生特定嚴重性層級的事件時，所引發的 Agent 警示 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9747c-103">This topic describes how to create a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alert that is raised when an event of a specific severity level occurs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="9747c-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="9747c-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="9747c-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="9747c-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="9747c-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="9747c-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="9747c-107">安全性</span><span class="sxs-lookup"><span data-stu-id="9747c-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="9747c-108">**若要用嚴重性層級建立警示，您可使用下列項目：**</span><span class="sxs-lookup"><span data-stu-id="9747c-108">**To create an alert using severity level, using:**</span></span>  
  
     [<span data-ttu-id="9747c-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9747c-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="9747c-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9747c-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9747c-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="9747c-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="9747c-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="9747c-112">Limitations and Restrictions</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="9747c-113">提供了一種簡單的圖形方式供您管理整個警示系統，建議您利用這個方式來設定警示基礎結構。</span><span class="sxs-lookup"><span data-stu-id="9747c-113">provides an easy, graphical way to manage the entire alerting system and is the recommended way to configure an alert infrastructure.</span></span>  
  
-   <span data-ttu-id="9747c-114">**xp_logevent** 產生的事件出現在 master 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="9747c-114">Events generated with **xp_logevent** occur in the master database.</span></span> <span data-ttu-id="9747c-115">因此，除非警示的 **xp_logevent** 是 **@database_name** 或 NULL，否則， **xp_logevent** 不會觸發警示。</span><span class="sxs-lookup"><span data-stu-id="9747c-115">Therefore, **xp_logevent** does not trigger an alert unless the **@database_name** for the alert is **'master'** or NULL.</span></span>  
  
-   <span data-ttu-id="9747c-116">從 19 到 25 的嚴重性層級會傳送 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 訊息到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 應用程式記錄檔並觸發警示。</span><span class="sxs-lookup"><span data-stu-id="9747c-116">Severity levels from 19 through 25 send a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] message to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows application log and trigger an alert.</span></span> <span data-ttu-id="9747c-117">嚴重性層級小於 19 的事件，只有在使用 **sp_altermessage**、RAISERROR WITH LOG 或 **xp_logevent** 強制寫入 Windows 應用程式記錄檔時，才會觸發警示。</span><span class="sxs-lookup"><span data-stu-id="9747c-117">Events with severity levels less than 19 will trigger alerts only if you have used **sp_altermessage**, RAISERROR WITH LOG, or **xp_logevent** to force them to be written to the Windows application log.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9747c-118">Security</span><span class="sxs-lookup"><span data-stu-id="9747c-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9747c-119">權限</span><span class="sxs-lookup"><span data-stu-id="9747c-119">Permissions</span></span>  
 <span data-ttu-id="9747c-120">依預設，只有 **系統管理員 (sysadmin)** 固定伺服器角色的成員，才能夠執行 **sp_add_alert**。</span><span class="sxs-lookup"><span data-stu-id="9747c-120">By default, only members of the **sysadmin** fixed server role can execute **sp_add_alert**.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="9747c-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9747c-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-an-alert-using-severity-level"></a><span data-ttu-id="9747c-122">若要使用嚴重性層級建立警示</span><span class="sxs-lookup"><span data-stu-id="9747c-122">To create an alert using severity level</span></span>  
  
1.  <span data-ttu-id="9747c-123">在 **[物件總管]** 中，按一下加號，以展開您要使用嚴重性層級建立警示的伺服器。</span><span class="sxs-lookup"><span data-stu-id="9747c-123">In **Object Explorer,** click the plus sign to expand the server where you want to create an alert using severity level.</span></span>  
  
2.  <span data-ttu-id="9747c-124">按一下加號展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="9747c-124">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="9747c-125">以滑鼠右鍵按一下 **[警示]** ，然後選取 **[新增警示]**。</span><span class="sxs-lookup"><span data-stu-id="9747c-125">Right-click **Alerts** and select **New Alert**.</span></span>  
  
4.  <span data-ttu-id="9747c-126">在 **[新增警示]** 對話方塊中的 **[名稱]** 方塊，輸入此警示的名稱。</span><span class="sxs-lookup"><span data-stu-id="9747c-126">In the **New Alert** dialog box, in the **Name** box, enter a name for this alert.</span></span>  
  
5.  <span data-ttu-id="9747c-127">在 **[類型]** 清單中，選取 **[SQL Server 事件警示]**。</span><span class="sxs-lookup"><span data-stu-id="9747c-127">In the **Type** list, select **SQL Server event alert**.</span></span>  
  
6.  <span data-ttu-id="9747c-128">在 **[事件警示定義]** 下，從 **[資料庫名稱]** 清單中選取資料庫，將警示限制在特定資料庫。</span><span class="sxs-lookup"><span data-stu-id="9747c-128">Under **Event alert definition**, in the **Database name** list, select a database to restrict the alert to a specific database.</span></span>  
  
7.  <span data-ttu-id="9747c-129">在 **[將根據下列條件引發警示]** 下，按一下 **[嚴重性]** ，然後選取將會引發警示的特定嚴重性。</span><span class="sxs-lookup"><span data-stu-id="9747c-129">Under **Alerts will be raised based on**, click **Severity** and then select the specific severity that will raise the alert.</span></span>  
  
8.  <span data-ttu-id="9747c-130">核取對應到 **[訊息包含下列內容時引發警示]** 核取方塊，將警示限制在特定字元順序，然後在 **[訊息文字]** 中輸入關鍵字或字元字串。</span><span class="sxs-lookup"><span data-stu-id="9747c-130">Check the box corresponding to **Raise alert when message contains** check box to restrict the alert to a particular character sequence, and then enter a keyword or character string for the **Message text**.</span></span> <span data-ttu-id="9747c-131">最大字元數為 100。</span><span class="sxs-lookup"><span data-stu-id="9747c-131">The maximum number of characters is 100.</span></span>  
  
9. <span data-ttu-id="9747c-132">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="9747c-132">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="9747c-133">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9747c-133">Using Transact-SQL</span></span>  
  
#### <a name="to-create-an-alert-using-severity-level"></a><span data-ttu-id="9747c-134">若要使用嚴重性層級建立警示</span><span class="sxs-lookup"><span data-stu-id="9747c-134">To create an alert using severity level</span></span>  
  
1.  <span data-ttu-id="9747c-135">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9747c-135">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="9747c-136">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="9747c-136">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="9747c-137">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="9747c-137">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
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
  
 <span data-ttu-id="9747c-138">如需詳細資訊，請參閱[sp_add_alert &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="9747c-138">For more information, see [sp_add_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql).</span></span>  
  
  
