---
title: 定義對警示的回應 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, alerts
- alerts [SQL Server], responding to
- responding to alerts
ms.assetid: c86ca6eb-c59f-46e9-bc32-d474e7c3b170
author: stevestein
ms.author: sstein
ms.openlocfilehash: c14e5adf43602b57697483b9ce4c2cdf20ff8e10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699217"
---
# <a name="define-the-response-to-an-alert-sql-server-management-studio"></a><span data-ttu-id="662ab-102">定義對警示的回應 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="662ab-102">Define the Response to an Alert (SQL Server Management Studio)</span></span>
  <span data-ttu-id="662ab-103">本主題描述如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用或，在中定義回應 Agent 警示 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 方式 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="662ab-103">This topic describes how to define how [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] responds to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="662ab-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="662ab-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="662ab-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="662ab-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="662ab-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="662ab-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="662ab-107">安全性</span><span class="sxs-lookup"><span data-stu-id="662ab-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="662ab-108">**若要使用下列項目定義對警示的回應：**</span><span class="sxs-lookup"><span data-stu-id="662ab-108">**To define the response to an alert, using:**</span></span>  
  
     [<span data-ttu-id="662ab-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="662ab-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="662ab-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="662ab-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="662ab-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="662ab-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="662ab-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="662ab-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="662ab-113">呼叫器和 **net send** 選項會從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 未來版本的 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="662ab-113">The Pager and **net send** options will be removed from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in a future version of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="662ab-114">請避免在新的開發工作中使用這些功能，並規劃修改目前使用這些功能的應用程式。</span><span class="sxs-lookup"><span data-stu-id="662ab-114">Avoid using these features in new development work, and plan to modify applications that currently use these features.</span></span>  
  
-   <span data-ttu-id="662ab-115">請注意，必須設定 SQL Server Agent 使用 Database Mail，才能將電子郵件及呼叫器通知傳送給操作員。</span><span class="sxs-lookup"><span data-stu-id="662ab-115">Note that SQL Server Agent must be configured to use Database Mail to send e-mail and pager notifications to operators.</span></span> <span data-ttu-id="662ab-116">如需詳細資訊，請參閱＜ [指派警示給操作員](assign-alerts-to-an-operator.md)＞。</span><span class="sxs-lookup"><span data-stu-id="662ab-116">For more information, see [Assign Alerts to an Operator](assign-alerts-to-an-operator.md).</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="662ab-117">提供了一種簡單的圖形方式供您管理各項作業，建議您利用這個方式來建立和管理作業基礎結構。</span><span class="sxs-lookup"><span data-stu-id="662ab-117">provides an easy, graphical way to manage jobs, and is the recommended way to create and manage the job infrastructure.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="662ab-118">Security</span><span class="sxs-lookup"><span data-stu-id="662ab-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="662ab-119">權限</span><span class="sxs-lookup"><span data-stu-id="662ab-119">Permissions</span></span>  
 <span data-ttu-id="662ab-120">只有 **系統管理員 (sysadmin)** 固定伺服器角色的成員，才能夠定義對警示的回應。</span><span class="sxs-lookup"><span data-stu-id="662ab-120">Only members of the **sysadmin** fixed server role can define the response to an alert.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="662ab-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="662ab-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-define-the-response-to-an-alert"></a><span data-ttu-id="662ab-122">若要定義對警示的回應</span><span class="sxs-lookup"><span data-stu-id="662ab-122">To define the response to an alert</span></span>  
  
1.  <span data-ttu-id="662ab-123">在 **[物件總管]** 中，按一下加號展開伺服器，此伺服器包含您要定義回應的警示。</span><span class="sxs-lookup"><span data-stu-id="662ab-123">In **Object Explorer**, click the plus sign to expand the server that contains the alert on which you want to define a response.</span></span>  
  
2.  <span data-ttu-id="662ab-124">按一下加號展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="662ab-124">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="662ab-125">按一下加號展開 **[警示]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="662ab-125">Click the plus sign to expand the **Alerts** folder.</span></span>  
  
4.  <span data-ttu-id="662ab-126">在要定義回應的警示上按一下滑鼠右鍵，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="662ab-126">Right-click the alert on which you want to define a response and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="662ab-127">在 [ _alert_name_**警示屬性**] 對話方塊的 [**選取頁面**] 底下，選取 [**回應**]。</span><span class="sxs-lookup"><span data-stu-id="662ab-127">In the _alert_name_**alert properties** dialog box, under **Select a page**, select **Response**.</span></span>  
  
6.  <span data-ttu-id="662ab-128">選取 **[執行作業]** 核取方塊，然後從 **[執行作業]** 核取方塊底下的清單中選取發生警示時要執行的作業。</span><span class="sxs-lookup"><span data-stu-id="662ab-128">Select the **Execute job** check box and, from the list below the **Execute job** check box, select a job to execute when the alert occurs.</span></span> <span data-ttu-id="662ab-129">您可以按一下 **[新增作業]** 來建立新作業。</span><span class="sxs-lookup"><span data-stu-id="662ab-129">You can create a new job by clicking **New Job**.</span></span> <span data-ttu-id="662ab-130">您可以按一下 **[檢視作業]** 檢視作業的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="662ab-130">You can view more information about the job by clicking **View Job**.</span></span> <span data-ttu-id="662ab-131">如需 [**新增作業**] 和 [**作業屬性**]_job_name_ ] 對話方塊中可用選項的詳細資訊，請參閱[建立作業](create-a-job.md)和[查看作業](view-a-job.md)。</span><span class="sxs-lookup"><span data-stu-id="662ab-131">For more information about the available options in the **New Job** and **Job Properties**_job_name_ dialog boxes, see [Create a Job](create-a-job.md) and [View a Job](view-a-job.md).</span></span>  
  
7.  <span data-ttu-id="662ab-132">如果您要在啟動警示時通知操作員，請選取 **[通知操作員]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="662ab-132">Select the **Notify Operators** check box if you want to notify operators when the alert is activated.</span></span> <span data-ttu-id="662ab-133">在**運算子清單**中，選取下列一或多種方法通知操作員：[電子郵件]\*\*\*\*、[呼叫器]\*\*\*\* 或 [Net Send]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="662ab-133">In the **Operator list**, select one or more of the following methods for notifying the operator or operators: **E-mail**, **Pager**, or **Net Send**.</span></span> <span data-ttu-id="662ab-134">您可以按一下 **[新增操作員]** 來建立新操作員。</span><span class="sxs-lookup"><span data-stu-id="662ab-134">You can create a new operator by clicking **New Operator**.</span></span> <span data-ttu-id="662ab-135">您可以按一下 **[檢視操作員]** 檢視操作員的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="662ab-135">You can view more information about an operator by clicking **View Operator**.</span></span> <span data-ttu-id="662ab-136">如需有關 **[新增操作員]** 和 **[檢視操作員屬性]** 對話方塊中之可用選項的詳細資訊，請參閱＜ [Create an Operator](create-an-operator.md) ＞和＜ [View Information About an Operator](view-information-about-an-operator.md)＞。</span><span class="sxs-lookup"><span data-stu-id="662ab-136">For more information about the available options in the **New Operator** and **View Operator Properties** dialog boxes, see [Create an Operator](create-an-operator.md) and [View Information About an Operator](view-information-about-an-operator.md).</span></span>  
  
8.  <span data-ttu-id="662ab-137">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="662ab-137">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="662ab-138">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="662ab-138">Using Transact-SQL</span></span>  
  
#### <a name="to-define-the-response-to-an-alert"></a><span data-ttu-id="662ab-139">若要定義對警示的回應</span><span class="sxs-lookup"><span data-stu-id="662ab-139">To define the response to an alert</span></span>  
  
1.  <span data-ttu-id="662ab-140">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="662ab-140">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="662ab-141">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="662ab-141">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="662ab-142">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="662ab-142">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- adds an e-mail notification for Test Alert.  
    -- assumes that Test Alert already exists and that Fran??ois Ajenstat is a valid operator name   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_notification  
     @alert_name = N'Test Alert',  
     @operator_name = N'Fran??ois Ajenstat',  
     @notification_method = 1 ;  
    GO  
    ```  
  
 <span data-ttu-id="662ab-143">如需詳細資訊，請參閱[sp_add_notification &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="662ab-143">For more information, see [sp_add_notification &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql).</span></span>  
  
  
