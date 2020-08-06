---
title: 建立 WMI 事件警示 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- WMI event alerts [SQL Server Management Studio]
ms.assetid: b8c46db6-408b-484e-98f0-a8af3e7ec763
author: stevestein
ms.author: sstein
ms.openlocfilehash: 737e7ccac9c92e663040e71339aa120f8db8b80b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597543"
---
# <a name="create-a-wmi-event-alert"></a><span data-ttu-id="48f5b-102">建立 WMI 事件警示</span><span class="sxs-lookup"><span data-stu-id="48f5b-102">Create a WMI Event Alert</span></span>
  <span data-ttu-id="48f5b-103">此主題描述如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中建立在伺服器事件的 WMI 提供者所監視的特定 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 事件發生時，所引發的 [!INCLUDE[tsql](../../includes/tsql-md.md)]Agent 警示。</span><span class="sxs-lookup"><span data-stu-id="48f5b-103">This topic describes how to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alert that is raised when a specific [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] event occurs that is monitored by the WMI Provider for Server Events in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="48f5b-104">如需使用 WMI 提供者監視事件的詳細資訊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[伺服器事件的 WMI 提供者概念](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="48f5b-104">For information about the using the WMI Provider to monitor [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] events, see [WMI Provider for Server Events Concepts](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md).</span></span> <span data-ttu-id="48f5b-105">如需接收 WMI 事件警示通知所需權限的詳細資訊，請參閱 [選取 SQL Server Agent 服務的帳戶](select-an-account-for-the-sql-server-agent-service.md)。</span><span class="sxs-lookup"><span data-stu-id="48f5b-105">For information about the permissions necessary to receive WMI event alert notifications, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md).</span></span> <span data-ttu-id="48f5b-106">如需 WQL 的詳細資訊，請參閱 [搭配伺服器事件的 WMI 提供者使用 WQL](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md)。</span><span class="sxs-lookup"><span data-stu-id="48f5b-106">For more information about WQL, see [Using WQL with the WMI Provider for Server Events](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md).</span></span>  
  
 <span data-ttu-id="48f5b-107">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="48f5b-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="48f5b-108">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="48f5b-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="48f5b-109">限制事項</span><span class="sxs-lookup"><span data-stu-id="48f5b-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="48f5b-110">安全性</span><span class="sxs-lookup"><span data-stu-id="48f5b-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="48f5b-111">**若要使用下列項目建立 WMI 事件警示：**</span><span class="sxs-lookup"><span data-stu-id="48f5b-111">**To create a WMI event alert, using:**</span></span>  
  
     [<span data-ttu-id="48f5b-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="48f5b-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="48f5b-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="48f5b-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="48f5b-114">開始之前</span><span class="sxs-lookup"><span data-stu-id="48f5b-114">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="48f5b-115">限制事項</span><span class="sxs-lookup"><span data-stu-id="48f5b-115">Limitations and Restrictions</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="48f5b-116">提供了一種簡單的圖形方式供您管理整個警示系統，建議您利用這個方式來設定警示基礎結構。</span><span class="sxs-lookup"><span data-stu-id="48f5b-116">provides an easy, graphical way to manage the entire alerting system and is the recommended way to configure an alert infrastructure.</span></span>  
  
-   <span data-ttu-id="48f5b-117">**xp_logevent** 產生的事件出現在 master 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="48f5b-117">Events generated with **xp_logevent** occur in the master database.</span></span> <span data-ttu-id="48f5b-118">因此，除非警示的 **xp_logevent** 是 **@database_name** 或 NULL，否則， **xp_logevent** 不會觸發警示。</span><span class="sxs-lookup"><span data-stu-id="48f5b-118">Therefore, **xp_logevent** does not trigger an alert unless the **@database_name** for the alert is **'master'** or NULL.</span></span>  
  
-   <span data-ttu-id="48f5b-119">僅支援執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 之電腦上的 WMI 命名空間。</span><span class="sxs-lookup"><span data-stu-id="48f5b-119">Only WMI namespaces on the computer that runs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent are supported.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="48f5b-120">Security</span><span class="sxs-lookup"><span data-stu-id="48f5b-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="48f5b-121">權限</span><span class="sxs-lookup"><span data-stu-id="48f5b-121">Permissions</span></span>  
 <span data-ttu-id="48f5b-122">依預設，只有 **系統管理員 (sysadmin)** 固定伺服器角色的成員，才能夠執行 **sp_add_alert**。</span><span class="sxs-lookup"><span data-stu-id="48f5b-122">By default, only members of the **sysadmin** fixed server role can execute **sp_add_alert**.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="48f5b-123">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="48f5b-123">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-wmi-event-alert"></a><span data-ttu-id="48f5b-124">若要建立 WMI 事件警示</span><span class="sxs-lookup"><span data-stu-id="48f5b-124">To create a WMI event alert</span></span>  
  
1.  <span data-ttu-id="48f5b-125">在 **[物件總管]** 中，按一下加號以展開您要建立 WMI 事件警示的伺服器。</span><span class="sxs-lookup"><span data-stu-id="48f5b-125">In **Object Explorer,** click the plus sign to expand the server where you want to create a WMI event alert.</span></span>  
  
2.  <span data-ttu-id="48f5b-126">按一下加號展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="48f5b-126">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="48f5b-127">以滑鼠右鍵按一下 **[警示]** ，然後選取 **[新增警示]**。</span><span class="sxs-lookup"><span data-stu-id="48f5b-127">Right-click **Alerts** and select **New Alert**.</span></span>  
  
4.  <span data-ttu-id="48f5b-128">在 **[新增警示]** 對話方塊中的 **[名稱]** 方塊，輸入此警示的名稱。</span><span class="sxs-lookup"><span data-stu-id="48f5b-128">In the **New Alert** dialog box, in the **Name** box, enter a name for this alert.</span></span>  
  
5.  <span data-ttu-id="48f5b-129">選取 **[啟用]** 核取方塊以讓警示得以執行。</span><span class="sxs-lookup"><span data-stu-id="48f5b-129">Check the **Enable** check box to enable the alert to run.</span></span> <span data-ttu-id="48f5b-130">根據預設，會選取 **[啟用]** 。</span><span class="sxs-lookup"><span data-stu-id="48f5b-130">By default, **Enable** is checked.</span></span>  
  
6.  <span data-ttu-id="48f5b-131">在 **[類型]** 清單中，選取 **[WMI 事件警示]**。</span><span class="sxs-lookup"><span data-stu-id="48f5b-131">In the **Type** list, select **WMI event alert**.</span></span>  
  
7.  <span data-ttu-id="48f5b-132">在 [WMI 事件警示定義]\*\*\*\* 底下的 [命名空間]\*\*\*\* 方塊中，指定 WMI 查詢語言 (WQL) 陳述式的 WMI 命名空間，以識別哪個 WMI 事件將會觸發此警示。</span><span class="sxs-lookup"><span data-stu-id="48f5b-132">Under **WMI event alert definition**, in the **Namespace** box, specify the WMI namespace for the WMI Query Language (WQL) statement that identifies which WMI event will trigger this alert.</span></span>  
  
8.  <span data-ttu-id="48f5b-133">在 **[查詢]** 方塊中，指定會識別警示所回應之事件的 WQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="48f5b-133">In the **Query** box, specify the WQL statement that identifies the event that this alert responds to.</span></span>  
  
9. <span data-ttu-id="48f5b-134">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="48f5b-134">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="48f5b-135">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="48f5b-135">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-wmi-event-alert"></a><span data-ttu-id="48f5b-136">若要建立 WMI 事件警示</span><span class="sxs-lookup"><span data-stu-id="48f5b-136">To create a WMI event alert</span></span>  
  
1.  <span data-ttu-id="48f5b-137">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="48f5b-137">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="48f5b-138">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="48f5b-138">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="48f5b-139">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="48f5b-139">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- creates a WMI event alert that retrieves all event properties for any ALTER_TABLE event that occurs on table AdventureWorks2012.Sales.SalesOrderDetail  
    -- This example assumes that the message 54001 already exists.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_alert  
        @name = N'Test Alert 2',  
        @message_id = 54001  
        @notification_message = N'Error 54001 has occurred on the Sales.SalesOrderDetail table on the AdventureWorks2012 database. Please see the following information...',  
        @wmi_namespace = '\\.\root\Microsoft\SqlServer\ServerEvents\,  
        @wmi_query = N'SELECT * FROM ALTER_TABLE   
    WHERE DatabaseName = 'AdventureWorks2012' AND SchemaName = 'Sales'   
        AND ObjectType='Table' AND ObjectName = 'SalesOrderDetail'';  
    GO  
    ```  
  
 <span data-ttu-id="48f5b-140">如需詳細資訊，請參閱[sp_add_alert &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="48f5b-140">For more information, see [sp_add_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql).</span></span>  
  
  
