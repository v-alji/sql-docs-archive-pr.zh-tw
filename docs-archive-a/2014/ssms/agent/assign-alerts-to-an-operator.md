---
title: 指派警示給操作員 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- assigning alerts to operator
- SQL Server Agent, alerts
- alerts [SQL Server], assigning to operator
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
ms.assetid: aa818155-6fa2-4565-a09f-5c7e31c89754
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3cc238b952c03595035856f377b6fdbb9eaf5e2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595371"
---
# <a name="assign-alerts-to-an-operator"></a><span data-ttu-id="edb64-102">指派警示給操作員</span><span class="sxs-lookup"><span data-stu-id="edb64-102">Assign Alerts to an Operator</span></span>
  <span data-ttu-id="edb64-103">本主題描述如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用或，將 Agent 警示指派給操作員，使其可以接收有關中作業的通知 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="edb64-103">This topic describes how to assign [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts to operators so they can receive notifications about jobs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="edb64-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="edb64-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="edb64-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="edb64-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="edb64-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="edb64-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="edb64-107">安全性</span><span class="sxs-lookup"><span data-stu-id="edb64-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="edb64-108">**若要使用下列項目指派警示給操作員：**</span><span class="sxs-lookup"><span data-stu-id="edb64-108">**To assign alerts to an operator, using:**</span></span>  
  
     [<span data-ttu-id="edb64-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="edb64-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="edb64-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="edb64-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="edb64-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="edb64-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="edb64-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="edb64-112">Limitations and Restrictions</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="edb64-113">提供了一種簡單的圖形方式供您管理整個警示系統。</span><span class="sxs-lookup"><span data-stu-id="edb64-113">provides an easy, graphical way to manage the entire alerting system.</span></span> <span data-ttu-id="edb64-114">建議您利用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 來設定您的警示基礎結構。</span><span class="sxs-lookup"><span data-stu-id="edb64-114">Using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] is the recommended way to configure your alert infrastructure.</span></span>  
  
-   <span data-ttu-id="edb64-115">若要傳送通知來回應警示，您必須先設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 來傳送郵件。</span><span class="sxs-lookup"><span data-stu-id="edb64-115">To send a notification in response to an alert, you must first configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to send mail.</span></span> <span data-ttu-id="edb64-116">如需詳細資訊，請參閱 [Configure SQL Server Agent Mail to Use Database Mail](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)。</span><span class="sxs-lookup"><span data-stu-id="edb64-116">For more information, see [Configure SQL Server Agent Mail to Use Database Mail](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).</span></span>  
  
-   <span data-ttu-id="edb64-117">如果傳送電子郵件訊息或呼叫器通知發生失敗，此失敗會在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務錯誤記錄檔中報告。</span><span class="sxs-lookup"><span data-stu-id="edb64-117">If a failure occurs when sending an e-mail message or pager notification, the failure is reported in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service error log.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="edb64-118">Security</span><span class="sxs-lookup"><span data-stu-id="edb64-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="edb64-119">權限</span><span class="sxs-lookup"><span data-stu-id="edb64-119">Permissions</span></span>  
 <span data-ttu-id="edb64-120">只有 **系統管理員 (sysadmin)** 固定伺服器角色的成員，才能夠指派警示給操作員。</span><span class="sxs-lookup"><span data-stu-id="edb64-120">Only members of the **sysadmin** fixed server role can assign alerts to operators.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="edb64-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="edb64-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-assign-alerts-to-an-operator"></a><span data-ttu-id="edb64-122">若要指派警示給操作員</span><span class="sxs-lookup"><span data-stu-id="edb64-122">To assign alerts to an operator</span></span>  
  
1.  <span data-ttu-id="edb64-123">在 **[物件總管]** 中，按一下加號展開伺服器，此伺服器包含您要指派警示的操作員。</span><span class="sxs-lookup"><span data-stu-id="edb64-123">In **Object Explorer**, click the plus sign to expand the server that contains the operator to which you want to assign an alert.</span></span>  
  
2.  <span data-ttu-id="edb64-124">按一下加號展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="edb64-124">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="edb64-125">按一下加號展開 **[操作員]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="edb64-125">Click the plus sign to expand the **Operators** folder.</span></span>  
  
4.  <span data-ttu-id="edb64-126">以滑鼠右鍵按一下要指派警示的操作員並選取 [屬性]\*\*\*\*，然後選取 [通知]\*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="edb64-126">Right-click the operator to which you want to assign an alert and select **Properties**, and select the **Notifications** page.</span></span>  
  
5.  <span data-ttu-id="edb64-127">在 [ _operator_name_**屬性**] 對話方塊的 [**選取頁面**] 底下，選取 [**通知**]。</span><span class="sxs-lookup"><span data-stu-id="edb64-127">In the _operator_name_**Properties** dialog box, under **Select a page**, select **Notifications**.</span></span>  
  
6.  <span data-ttu-id="edb64-128">在 **[檢視傳送給這名使用者的通知來源]** 下選取 **[警示]** ，以檢視傳送給這名操作員的警示清單；或選取 **[作業]** ，以檢視會傳送通知給這名操作員的作業清單。</span><span class="sxs-lookup"><span data-stu-id="edb64-128">Under **View notifications sent to this user by**, select **Alerts** to view a list of alerts sent to this operator or select **Jobs** to view a list of jobs that send notifications to this operator.</span></span> <span data-ttu-id="edb64-129">選取下列一個或多個核取方塊，視需要定義每個通知的通知方法：[電子郵件]\*\*\*\*、[呼叫器]\*\*\*\* 或 [Net send]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="edb64-129">Select one or more of the following checkboxes to define the notification method for each notification as necessary: **E-mail**, **Pager**, or **Net send**.</span></span>  
  
7.  <span data-ttu-id="edb64-130">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="edb64-130">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="edb64-131">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="edb64-131">Using Transact-SQL</span></span>  
  
#### <a name="to-assign-alerts-to-an-operator"></a><span data-ttu-id="edb64-132">若要指派警示給操作員</span><span class="sxs-lookup"><span data-stu-id="edb64-132">To assign alerts to an operator</span></span>  
  
1.  <span data-ttu-id="edb64-133">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="edb64-133">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="edb64-134">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="edb64-134">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="edb64-135">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="edb64-135">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- adds an e-mail notification for the specified alert (Test Alert)  
    -- This example assumes that Test Alert already exists and that Fran??ois Ajenstat is a valid operator name.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_notification  
     @alert_name = N'Test Alert',  
     @operator_name = N'Fran??ois Ajenstat',  
     @notification_method = 1 ;  
    GO  
    ```  
  
 <span data-ttu-id="edb64-136">如需詳細資訊，請參閱[sp_add_notification &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="edb64-136">For more information, see [sp_add_notification &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql).</span></span>  
  
  
