---
title: 傳送 SQL Server Agent 錯誤訊息 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- messages [SQL Server], SQL Server Agent
- sending messages
- SQL Server Agent, errors
- errors [SQL Server Agent]
ms.assetid: 2597d0d7-951a-48cf-989f-abb67b9fdb36
author: stevestein
ms.author: sstein
ms.openlocfilehash: 03e38b02188eaced65a86b22ed4f22cb6984ce0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597536"
---
# <a name="send-sql-server-agent-error-messages"></a><span data-ttu-id="67962-102">傳送 SQL Server Agent 錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="67962-102">Send SQL Server Agent Error Messages</span></span>
  <span data-ttu-id="67962-103">本主題描述如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用，在中設定 Agent 以透過 net send 傳送其錯誤訊息 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="67962-103">This topic describes how to how to configure [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to send its error messages by way of net send in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="67962-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="67962-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="67962-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="67962-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="67962-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="67962-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="67962-107">安全性</span><span class="sxs-lookup"><span data-stu-id="67962-107">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="67962-108">若要使用 SQL Server Management Studio 傳送 SQL Server Agent 錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="67962-108">To send SQL Server Agent error messages using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="67962-109">開始之前</span><span class="sxs-lookup"><span data-stu-id="67962-109">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="67962-110">限制事項</span><span class="sxs-lookup"><span data-stu-id="67962-110">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="67962-111">只有當您擁有使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 節點的權限時，[物件總管] 才會顯示該節點。</span><span class="sxs-lookup"><span data-stu-id="67962-111">Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
-   <span data-ttu-id="67962-112">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Messenger 服務必須在執行中，才能接收 Net Send 事件。</span><span class="sxs-lookup"><span data-stu-id="67962-112">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Messenger service must be running to receive net send events.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="67962-113">Security</span><span class="sxs-lookup"><span data-stu-id="67962-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="67962-114">權限</span><span class="sxs-lookup"><span data-stu-id="67962-114">Permissions</span></span>  
 <span data-ttu-id="67962-115">若要執行功能，您必須將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 設定為使用帳戶認證，此帳戶必須是 **中** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)](系統管理員) 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="67962-115">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="67962-116">此帳戶必須擁有下列 Windows 權限：</span><span class="sxs-lookup"><span data-stu-id="67962-116">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="67962-117">以服務登入 (SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="67962-117">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="67962-118">取代處理序層級 Token (SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="67962-118">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="67962-119">略過跨越檢查 (SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="67962-119">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="67962-120">調整處理序的記憶體配額 (SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="67962-120">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="67962-121">如需 Agent 服務帳戶所需之 Windows 許可權的詳細資訊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[選取 SQL Server Agent 服務的帳戶](select-an-account-for-the-sql-server-agent-service.md)和[設定 Windows 服務帳戶與許可權](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="67962-121">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="67962-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="67962-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-send-sql-server-agent-error-messages"></a><span data-ttu-id="67962-123">若要傳送 SQL Server Agent 錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="67962-123">To send SQL Server Agent error messages</span></span>  
  
1.  <span data-ttu-id="67962-124">在 **[物件總管]** 中，按一下加號展開伺服器，此伺服器包含您要透過 Net Send 從中傳送錯誤訊息的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 錯誤記錄檔。</span><span class="sxs-lookup"><span data-stu-id="67962-124">In **Object Explorer**, click the plus sign to expand the server that contains the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log from which you want to send error messages via net send.</span></span>  
  
2.  <span data-ttu-id="67962-125">以滑鼠右鍵按一下**SQL Server Agent** ，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="67962-125">Right-click **SQL Server Agent** and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="67962-126">在 [ **SQL Server Agent 屬性-**_server_name_ ] 對話方塊的 [**一般**] 頁面的 [**錯誤記錄**檔] 底下，于 [ **Net send 收件**者] 方塊中輸入要傳送錯誤訊息的目標使用者名稱或電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="67962-126">In the **SQL Server Agent Properties -**_server_name_ dialog box, under **Error log** on the **General** page, , type the user name or computer name to which you want to send error messages in the **Net send recipient** box.</span></span>  
  
4.  <span data-ttu-id="67962-127">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="67962-127">Click **OK**.</span></span>  
  
  
