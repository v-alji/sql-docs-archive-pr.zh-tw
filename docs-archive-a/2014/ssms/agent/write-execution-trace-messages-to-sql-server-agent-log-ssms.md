---
title: 將執行追蹤訊息寫入 SQL Server Agent 錯誤記錄檔 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], SQL Server Agent
- writing trace messages
- traces [SQL Server], SQL Server Agent logs
- SQL Server Agent, errors
- errors [SQL Server Agent]
ms.assetid: 90e3731e-6fae-43db-833e-9accecdd1c03
author: stevestein
ms.author: sstein
ms.openlocfilehash: 38b08452ef2680b654dd735b901488cb5f5f5f97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703718"
---
# <a name="write-execution-trace-messages-to-the-sql-server-agent-error-log-sql-server-management-studio"></a><span data-ttu-id="f49f3-102">Write Execution Trace Messages to the SQL Server Agent Error Log (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="f49f3-102">Write Execution Trace Messages to the SQL Server Agent Error Log (SQL Server Management Studio)</span></span>
  <span data-ttu-id="f49f3-103">本主題描述如何使用， [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在中設定 Agent 將執行追蹤訊息納入其錯誤記錄檔中 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f49f3-103">This topic describes how to configure [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to include execution trace messages in its error log in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="f49f3-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="f49f3-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f49f3-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="f49f3-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f49f3-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="f49f3-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="f49f3-107">安全性</span><span class="sxs-lookup"><span data-stu-id="f49f3-107">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="f49f3-108">若要使用 SQL Server Management Studio，將執行追蹤訊息寫入 SQL Server Agent 錯誤記錄檔</span><span class="sxs-lookup"><span data-stu-id="f49f3-108">To write execution trace messages to the SQL Server Agent Error Log using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f49f3-109">開始之前</span><span class="sxs-lookup"><span data-stu-id="f49f3-109">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="f49f3-110">限制事項</span><span class="sxs-lookup"><span data-stu-id="f49f3-110">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="f49f3-111">只有當您擁有使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 節點的權限時，[物件總管] 才會顯示該節點。</span><span class="sxs-lookup"><span data-stu-id="f49f3-111">Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
-   <span data-ttu-id="f49f3-112">因為這個選項會使錯誤記錄檔變得很大，請只在調查特定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 問題時，才將執行追蹤訊息包含在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 錯誤記錄檔。</span><span class="sxs-lookup"><span data-stu-id="f49f3-112">Because this option can cause the error log to become large, only include execution trace messages in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error logs when investigating a specific [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent problem.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f49f3-113">Security</span><span class="sxs-lookup"><span data-stu-id="f49f3-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f49f3-114">權限</span><span class="sxs-lookup"><span data-stu-id="f49f3-114">Permissions</span></span>  
 <span data-ttu-id="f49f3-115">若要執行功能，您必須將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 設定為使用帳戶認證，此帳戶必須是 **中** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)](系統管理員) 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="f49f3-115">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f49f3-116">此帳戶必須擁有下列 Windows 權限：</span><span class="sxs-lookup"><span data-stu-id="f49f3-116">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="f49f3-117">以服務登入 (SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="f49f3-117">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="f49f3-118">取代處理序層級 Token (SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="f49f3-118">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="f49f3-119">略過跨越檢查 (SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="f49f3-119">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="f49f3-120">調整處理序的記憶體配額 (SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="f49f3-120">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="f49f3-121">如需 Agent 服務帳戶所需之 Windows 許可權的詳細資訊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[選取 SQL Server Agent 服務的帳戶](select-an-account-for-the-sql-server-agent-service.md)和[設定 Windows 服務帳戶與許可權](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="f49f3-121">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="SSMSProcedure"></a>   
#### <a name="to-write-execution-trace-messages-to-the-sql-server-agent-error-log"></a><span data-ttu-id="f49f3-122">若要將執行追蹤訊息寫入 SQL Server Agent 錯誤記錄檔</span><span class="sxs-lookup"><span data-stu-id="f49f3-122">To write execution trace messages to the SQL Server Agent error log</span></span>  
  
1.  <span data-ttu-id="f49f3-123">在 **[物件總管]** 中，按一下加號展開伺服器，此伺服器包含您要寫入執行追蹤訊息的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 錯誤記錄檔。</span><span class="sxs-lookup"><span data-stu-id="f49f3-123">In **Object Explorer**, click the plus sign to expand the server that contains the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log to which you want to write execution trace messages.</span></span>  
  
2.  <span data-ttu-id="f49f3-124">以滑鼠右鍵按一下**SQL Server Agent** ，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="f49f3-124">Right-click **SQL Server Agent** and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="f49f3-125">在 [ **SQL Server Agent 屬性-**_server_name_ ] 對話方塊的 [**一般**] 頁面的 [**錯誤記錄**檔] 底下，選取 [**包含執行追蹤訊息**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="f49f3-125">In the **SQL Server Agent Properties -**_server_name_ dialog box, under **Error log** on the **General** page, select the **Include execution trace messages** check box.</span></span>  
  
4.  <span data-ttu-id="f49f3-126">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="f49f3-126">Click **OK**.</span></span>  
  
  
