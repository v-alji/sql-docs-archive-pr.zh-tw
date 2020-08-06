---
title: 設定 SQL Server Agent 服務的 SQL Server 別名 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- aliases [SQL Server], creating
- SQL Server Agent, aliases
ms.assetid: 02d6295d-ab52-44f0-8f1b-f3910a507d8f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b178d91a47d907b182ef7962b98c7f22d4454094
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585564"
---
# <a name="set-a-sql-server-alias-for-the-sql-server-agent-service-sql-server-management-studio"></a><span data-ttu-id="38c58-102">Set a SQL Server Alias for the SQL Server Agent Service (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="38c58-102">Set a SQL Server Alias for the SQL Server Agent Service (SQL Server Management Studio)</span></span>
  <span data-ttu-id="38c58-103">本主題描述如何 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 使用設定別名，以供 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 用來連接到 [!INCLUDE[ssDE](../includes/ssde-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="38c58-103">This topic describes how to set a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] alias for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent to use to connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)] by using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="38c58-104">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 服務預設會使用不需要額外的用戶端組態之動態伺服器名稱，透過具名管道連接至 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="38c58-104">By default, the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent service connects to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] over named pipes by using dynamic server names that require no additional client configuration.</span></span> <span data-ttu-id="38c58-105">只有未使用預設網路傳輸，或當您連接到正在接聽替代具名管道之 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的執行個體時，才需要設定伺服器連接別名。</span><span class="sxs-lookup"><span data-stu-id="38c58-105">You need to configure a server connection alias only if you are not using the default network transport or if you are connecting to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that listens on an alternate named pipe.</span></span>  
  
 <span data-ttu-id="38c58-106">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="38c58-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="38c58-107">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="38c58-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="38c58-108">限制事項</span><span class="sxs-lookup"><span data-stu-id="38c58-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="38c58-109">安全性</span><span class="sxs-lookup"><span data-stu-id="38c58-109">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="38c58-110">若要使用 SQL Server Management Studio，為 SQL Server Agent 服務設定 SQL Server 別名</span><span class="sxs-lookup"><span data-stu-id="38c58-110">To set a SQL Server Alias for the SQL Server Agent Service using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="38c58-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="38c58-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="38c58-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="38c58-112">Limitations and Restrictions</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="38c58-113">之本機執行個體的別名，否則 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="38c58-113">Agent will not work correctly unless you select an alias that refers to the local instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="38c58-114">只有當您擁有使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 節點的權限時，[物件總管] 才會顯示該節點。</span><span class="sxs-lookup"><span data-stu-id="38c58-114">Object Explorer only displays the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="38c58-115">Security</span><span class="sxs-lookup"><span data-stu-id="38c58-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="38c58-116">權限</span><span class="sxs-lookup"><span data-stu-id="38c58-116">Permissions</span></span>  
 <span data-ttu-id="38c58-117">若要執行功能，您必須將 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 設定為使用帳戶認證，此帳戶必須是 **中** sysadmin [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)](系統管理員) 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="38c58-117">To perform its functions, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="38c58-118">此帳戶必須擁有下列 Windows 權限：</span><span class="sxs-lookup"><span data-stu-id="38c58-118">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="38c58-119">以服務登入 (SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="38c58-119">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="38c58-120">取代處理序層級 Token (SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="38c58-120">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="38c58-121">略過跨越檢查 (SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="38c58-121">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="38c58-122">調整處理序的記憶體配額 (SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="38c58-122">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="38c58-123">如需 Agent 服務帳戶所需之 Windows 許可權的詳細資訊 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，請參閱[選取 SQL Server Agent 服務的帳戶](../ssms/agent/select-an-account-for-the-sql-server-agent-service.md)和[設定 Windows 服務帳戶與許可權](configure-windows/configure-windows-service-accounts-and-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="38c58-123">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="38c58-124">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="38c58-124">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-a-sql-server-alias-for-the-sql-server-agent-service"></a><span data-ttu-id="38c58-125">若要為 SQL Server Agent 服務設定 SQL Server 別名</span><span class="sxs-lookup"><span data-stu-id="38c58-125">To set a SQL Server Alias for the SQL Server Agent Service</span></span>  
  
1.  <span data-ttu-id="38c58-126">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="38c58-126">In the **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="38c58-127">以滑鼠右鍵按一下 [SQL Server Agent]\*\*\*\*，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="38c58-127">Right-click **SQL Server Agent**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="38c58-128">在 [ **SQL Server Agent 屬性**_server_name_ ] 對話方塊的 [**選取頁面**] 底下，選取 [**連接**]，然後</span><span class="sxs-lookup"><span data-stu-id="38c58-128">In the **SQL Server Agent Properties**_server_name_ dialog box, under **Select a page**, select **Connection**, and</span></span>  
  
4.  <span data-ttu-id="38c58-129">在 **[別名本機主機伺服器]** 方塊中，輸入 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 要連接之伺服器的別名。</span><span class="sxs-lookup"><span data-stu-id="38c58-129">In the **Alias local host server** box, type the alias of the server to which [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent should connect.</span></span>  
  
5.  <span data-ttu-id="38c58-130">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="38c58-130">Click **OK**.</span></span>  
  
  
