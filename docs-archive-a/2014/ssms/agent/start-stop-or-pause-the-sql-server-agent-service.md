---
title: 啟動、停止或暫停 SQL Server Agent 服務 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, starting
- SQL Server Agent, pausing
- SQL Server Agent, stopping
ms.assetid: c95a9759-dd30-4ab6-9ab0-087bb3bfb97c
author: stevestein
ms.author: sstein
ms.openlocfilehash: f2feb6a18c602271b1bec871fbfc9793979b100e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686750"
---
# <a name="start-stop-or-pause-the-sql-server-agent-service"></a><span data-ttu-id="46d7a-102">啟動、停止或暫停 SQL Server Agent 服務</span><span class="sxs-lookup"><span data-stu-id="46d7a-102">Start, Stop, or Pause the SQL Server Agent Service</span></span>
  <span data-ttu-id="46d7a-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中啟動、停止或重新啟動 SQL Server Agent 服務。</span><span class="sxs-lookup"><span data-stu-id="46d7a-103">This topic describes how to start, stop, or restart the SQL Server Agent Service in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="46d7a-104">您可以將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務設定為在啟動作業系統時自動啟動，或者您可以在需要完成作業時再以手動方式啟動服務。</span><span class="sxs-lookup"><span data-stu-id="46d7a-104">You can configure the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service to start automatically when the operating system starts, or you can start it manually when you need to complete jobs.</span></span> <span data-ttu-id="46d7a-105">您可以停止或暫停 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務，以暫止作業、操作員通知及警示。</span><span class="sxs-lookup"><span data-stu-id="46d7a-105">You can stop or pause the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service to suspend jobs, operator notifications, and alerts.</span></span>  
  
 <span data-ttu-id="46d7a-106">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="46d7a-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="46d7a-107">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="46d7a-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="46d7a-108">限制事項</span><span class="sxs-lookup"><span data-stu-id="46d7a-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="46d7a-109">安全性</span><span class="sxs-lookup"><span data-stu-id="46d7a-109">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="46d7a-110">若要使用 SQL Server Management Studio 啟動、停止或重新啟動 SQL Server Agent 服務</span><span class="sxs-lookup"><span data-stu-id="46d7a-110">To start, stop, or restart the SQL Server Agent Service using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="46d7a-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="46d7a-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="46d7a-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="46d7a-112">Limitations and Restrictions</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="46d7a-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]代理程式必須以服務的形式執行，才能將系統管理工作自動化。</span><span class="sxs-lookup"><span data-stu-id="46d7a-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be running as a service in order to automate administrative tasks.</span></span> <span data-ttu-id="46d7a-114">如需詳細資訊，請參閱 [Configure SQL Server Agent](configure-sql-server-agent.md)。</span><span class="sxs-lookup"><span data-stu-id="46d7a-114">For more information, see [Configure SQL Server Agent](configure-sql-server-agent.md).</span></span>  
  
-   <span data-ttu-id="46d7a-115">只有當您擁有使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 節點的權限時，[物件總管] 才會顯示該節點。</span><span class="sxs-lookup"><span data-stu-id="46d7a-115">Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="46d7a-116">Security</span><span class="sxs-lookup"><span data-stu-id="46d7a-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="46d7a-117">權限</span><span class="sxs-lookup"><span data-stu-id="46d7a-117">Permissions</span></span>  
 <span data-ttu-id="46d7a-118">若要執行功能，您必須將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 設定為使用帳戶認證，此帳戶必須是 **中** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)](系統管理員) 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="46d7a-118">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="46d7a-119">此帳戶必須擁有下列 Windows 權限：</span><span class="sxs-lookup"><span data-stu-id="46d7a-119">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="46d7a-120">以服務登入 (SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="46d7a-120">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="46d7a-121">取代處理序層級 Token (SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="46d7a-121">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="46d7a-122">略過跨越檢查 (SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="46d7a-122">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="46d7a-123">調整處理序的記憶體配額 (SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="46d7a-123">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="46d7a-124">如需 Agent 服務帳戶所需之 Windows 許可權的詳細資訊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[選取 SQL Server Agent 服務的帳戶](select-an-account-for-the-sql-server-agent-service.md)和[設定 Windows 服務帳戶與許可權](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="46d7a-124">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="46d7a-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="46d7a-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-start-stop-or-restart-the-sql-server-agent-service"></a><span data-ttu-id="46d7a-126">若要啟動、停止或重新啟動 SQL Server Agent 服務</span><span class="sxs-lookup"><span data-stu-id="46d7a-126">To start, stop, or restart the SQL Server Agent Service</span></span>  
  
1.  <span data-ttu-id="46d7a-127">在 **[物件總管]** 中，按一下加號展開要管理 SQL Server Agent 服務所在的伺服器。</span><span class="sxs-lookup"><span data-stu-id="46d7a-127">In **Object Explorer**, click the plus sign to expand the server where you want to manage SQL Server Agent Service.</span></span>  
  
2.  <span data-ttu-id="46d7a-128">在 [SQL Server Agent]\*\*\*\*，然後選取 [啟動]\*\*\*\*、[停止]\*\*\*\* 或 [重新啟動]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="46d7a-128">Right-click **SQL Server Agent**, and then select either **Start**, **Stop**, or **Restart**.</span></span>  
  
3.  <span data-ttu-id="46d7a-129">在 [使用者帳戶控制] 對話方塊中，按一下 [是]。</span><span class="sxs-lookup"><span data-stu-id="46d7a-129">In the **User Account Control** dialog box, click **Yes**.</span></span>  
  
4.  <span data-ttu-id="46d7a-130">當系統提示您是否要執行動作時，請按一下 **[是]**。</span><span class="sxs-lookup"><span data-stu-id="46d7a-130">When prompted if you want to perform the action, click **Yes**.</span></span>  
  
 <span data-ttu-id="46d7a-131">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="46d7a-131">For more information, see:</span></span>  
  
-   [<span data-ttu-id="46d7a-132">啟動、停止、暫停、繼續、重新啟動 Database Engine、SQL Server Agent 或 SQL Server Browser 服務</span><span class="sxs-lookup"><span data-stu-id="46d7a-132">Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service</span></span>](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
-   [<span data-ttu-id="46d7a-133">自動啟動t SQL Server Agent &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="46d7a-133">Autostart SQL Server Agent &#40;SQL Server Management Studio&#41;</span></span>](autostart-sql-server-agent-sql-server-management-studio.md)  
  
  
