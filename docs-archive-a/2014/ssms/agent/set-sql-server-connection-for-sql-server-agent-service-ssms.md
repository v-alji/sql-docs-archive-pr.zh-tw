---
title: 設定 SQL Server Agent 服務 (SQL Server Management Studio) 的 SQL Server 連接 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, connections
- connections [SQL Server], SQL Server Agent service
ms.assetid: 28b6178b-0a9e-4f2c-8562-7a62d2d2a285
author: stevestein
ms.author: sstein
ms.openlocfilehash: 30f68967d6bdb8b0495cbddb1a5b0bd447cd5168
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607221"
---
# <a name="set-the-sql-server-connection-for-the-sql-server-agent-service-sql-server-management-studio"></a><span data-ttu-id="abc0a-102">設定 SQL Server Agent 服務的 SQL Server 連線 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="abc0a-102">Set the SQL Server Connection for the SQL Server Agent Service (SQL Server Management Studio)</span></span>
  <span data-ttu-id="abc0a-103">此主題描述如何在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中使用 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 設定 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Agent 和 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]之間的連接。</span><span class="sxs-lookup"><span data-stu-id="abc0a-103">This topic describes how to set the connection between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent and the [!INCLUDE[ssDE](../../includes/ssde-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="abc0a-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務可使用「Windows 驗證」連接到 SQL Server 的本機執行個體。</span><span class="sxs-lookup"><span data-stu-id="abc0a-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service can connect to a local instance of SQL Server by using Windows Authentication.</span></span>  
  
 <span data-ttu-id="abc0a-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="abc0a-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="abc0a-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="abc0a-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="abc0a-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="abc0a-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="abc0a-108">安全性</span><span class="sxs-lookup"><span data-stu-id="abc0a-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="abc0a-109">**若要為 SQL Server Agent 設定 SQL Server 連接，使用：**</span><span class="sxs-lookup"><span data-stu-id="abc0a-109">**To set the SQL Server Connection for the SQL Server Agent, using:**</span></span>  
  
     [<span data-ttu-id="abc0a-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="abc0a-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="abc0a-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="abc0a-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="abc0a-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="abc0a-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="abc0a-113">只有當您擁有使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 節點的權限時，[物件總管] 才會顯示該節點。</span><span class="sxs-lookup"><span data-stu-id="abc0a-113">Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
-   <span data-ttu-id="abc0a-114">從 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]開始， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 就不支援「 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證」。</span><span class="sxs-lookup"><span data-stu-id="abc0a-114">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent does not support [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="abc0a-115">只有當您管理舊版的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]時，才能使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="abc0a-115">This option is available only when you administer an earlier version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="abc0a-116">Security</span><span class="sxs-lookup"><span data-stu-id="abc0a-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="abc0a-117">權限</span><span class="sxs-lookup"><span data-stu-id="abc0a-117">Permissions</span></span>  
 <span data-ttu-id="abc0a-118">若要執行功能，您必須將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 設定為使用帳戶認證，此帳戶必須是 **中** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)](系統管理員) 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="abc0a-118">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="abc0a-119">此帳戶必須擁有下列 Windows 權限：</span><span class="sxs-lookup"><span data-stu-id="abc0a-119">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="abc0a-120">以服務登入 (SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="abc0a-120">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="abc0a-121">取代處理序層級 Token (SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="abc0a-121">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="abc0a-122">略過跨越檢查 (SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="abc0a-122">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="abc0a-123">調整處理序的記憶體配額 (SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="abc0a-123">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="abc0a-124">如需 Agent 服務帳戶所需之 Windows 許可權的詳細資訊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[選取 SQL Server Agent 服務的帳戶](select-an-account-for-the-sql-server-agent-service.md)和[設定 Windows 服務帳戶與許可權](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="abc0a-124">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="abc0a-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="abc0a-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-the-sql-server-connection"></a><span data-ttu-id="abc0a-126">若要設定 SQL Server 連接</span><span class="sxs-lookup"><span data-stu-id="abc0a-126">To set the SQL Server connection</span></span>  
  
1.  <span data-ttu-id="abc0a-127">在 **[物件總管]** 中，按一下加號展開要設定與其 SQL Server Agent 服務連接的伺服器。</span><span class="sxs-lookup"><span data-stu-id="abc0a-127">In **Object Explorer**, click the plus sign to expand the server that you want to set up with a connection to its SQL Server Agent Service.</span></span>  
  
2.  <span data-ttu-id="abc0a-128">以滑鼠右鍵按一下**SQL Server Agent** ，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="abc0a-128">Right-click **SQL Server Agent** and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="abc0a-129">在 [SQL Server Agent 屬性]\*\*\*\* 對話方塊的 [選取頁面]\*\*\*\* 底下，按一下 [連線]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="abc0a-129">In the **SQL Server Agent Properties** dialog box, under **Select a page**, click **Connection**.</span></span>  
  
4.  <span data-ttu-id="abc0a-130">在 [SQL Server 連線]\*\*\*\* 底下選取 [使用 Windows 驗證]\*\*\*\*，讓 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 使用  Windows 驗證來連接到 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="abc0a-130">Under **SQL Server connection**, select **Use Windows Authentication** to enable [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] with [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span> <span data-ttu-id="abc0a-131">連接到 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 及更新版本的資料庫需要 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="abc0a-131">Connections to [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later databases require Windows Authentication.</span></span>  
  
  
