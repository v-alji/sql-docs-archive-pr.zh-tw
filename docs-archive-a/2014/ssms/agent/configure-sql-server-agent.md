---
title: 設定 SQL Server Agent | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, configuring
- accounts [SQL Server], SQL Server Agent
- SQL Server Agent, permissions
- security [SQL Server], SQL Server Agent
ms.assetid: 2e361a62-9e92-4fcd-80d7-d6960f127900
author: stevestein
ms.author: sstein
ms.openlocfilehash: 81c78faf733fac5ffb9a6e74dbf03f8caaff03d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595365"
---
# <a name="configure-sql-server-agent"></a><span data-ttu-id="45528-102">Configure SQL Server Agent</span><span class="sxs-lookup"><span data-stu-id="45528-102">Configure SQL Server Agent</span></span>
  <span data-ttu-id="45528-103">本主題描述如何在安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 期間指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Agent 的一些組態選項。</span><span class="sxs-lookup"><span data-stu-id="45528-103">This topic describes how to specify some configuration options for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent during installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="45528-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]管理物件 (SMO) 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 預存程序內才有完整的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 組態選項集合可用。</span><span class="sxs-lookup"><span data-stu-id="45528-104">The full set of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent configuration options is only available within [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO), or the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent stored procedures.</span></span>  
  
 <span data-ttu-id="45528-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="45528-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="45528-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="45528-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="45528-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="45528-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="45528-108">安全性</span><span class="sxs-lookup"><span data-stu-id="45528-108">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="45528-109">若要設定 SQL Server Agent</span><span class="sxs-lookup"><span data-stu-id="45528-109">To configure SQL Server Agent</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="45528-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="45528-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="45528-111">限制事項</span><span class="sxs-lookup"><span data-stu-id="45528-111">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="45528-112">在 **的 [物件總管] 中，按一下** [SQL Server Agent] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，以管理作業、運算子、警示與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務。</span><span class="sxs-lookup"><span data-stu-id="45528-112">Click **SQL Server Agent** in Object Explorer of [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to administer jobs, operators, alerts, and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service.</span></span> <span data-ttu-id="45528-113">不過，只有當您擁有使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 節點的權限時，[物件總管] 才會顯示該節點。</span><span class="sxs-lookup"><span data-stu-id="45528-113">However, Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
-   <span data-ttu-id="45528-114">容錯移轉叢集執行個體上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務不應該啟用自動重新啟動。</span><span class="sxs-lookup"><span data-stu-id="45528-114">Auto-restart should not be enabled for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service or the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service on failover cluster instances.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="45528-115">Security</span><span class="sxs-lookup"><span data-stu-id="45528-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="45528-116">權限</span><span class="sxs-lookup"><span data-stu-id="45528-116">Permissions</span></span>  
 <span data-ttu-id="45528-117">若要執行功能，您必須將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 設定為使用帳戶認證，此帳戶必須是 **中** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)](系統管理員) 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="45528-117">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="45528-118">此帳戶必須擁有下列 Windows 權限：</span><span class="sxs-lookup"><span data-stu-id="45528-118">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="45528-119">以服務登入 (SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="45528-119">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="45528-120">取代處理序層級 Token (SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="45528-120">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="45528-121">略過跨越檢查 (SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="45528-121">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="45528-122">調整處理序的記憶體配額 (SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="45528-122">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="45528-123">如需 Agent 服務帳戶所需之 Windows 許可權的詳細資訊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[選取 SQL Server Agent 服務的帳戶](select-an-account-for-the-sql-server-agent-service.md)和[設定 Windows 服務帳戶與許可權](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="45528-123">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="45528-124">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="45528-124">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-sql-server-agent"></a><span data-ttu-id="45528-125">若要設定 SQL Server Agent</span><span class="sxs-lookup"><span data-stu-id="45528-125">To configure SQL Server Agent</span></span>  
  
1.  <span data-ttu-id="45528-126">按一下 **[開始]** 按鈕，然後按一下 **[開始]**  功能表上的 **[控制台]**。</span><span class="sxs-lookup"><span data-stu-id="45528-126">Click the **Start** button, and then, on the **Start**  menu, click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="45528-127">在 [控制台] 中，依序按一下 **[系統及安全性]** 和 **[系統管理工具]**，然後選取 **[本機安全性原則]**。</span><span class="sxs-lookup"><span data-stu-id="45528-127">In Control Panel, click **System and Security**, click **Administrative Tools**, and then select **Local Security Policy**.</span></span>  
  
3.  <span data-ttu-id="45528-128">在 [本機安全性原則] 中，按一下＞形箭號展開 **[本機原則]** 資料夾，然後按一下 **[使用者權限指派]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="45528-128">In Local Security Policy, click the chevron to expand the **Local Policies** folder, and then click the **User Rights Assignment** folder.</span></span>  
  
4.  <span data-ttu-id="45528-129">以滑鼠右鍵按一下您要設定搭配 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用的權限，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="45528-129">Right-click a permission that you want to configure for use with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="45528-130">在權限的屬性對話方塊中，確認已列出用於執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 的帳戶。</span><span class="sxs-lookup"><span data-stu-id="45528-130">In the permission's properties dialog box, verify that the account under which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent runs is listed.</span></span> <span data-ttu-id="45528-131">如果未列出，請按一下 **[加入使用者或群組]**，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [選取使用者、電腦、服務帳戶或群組] **對話方塊中輸入執行** Agent 的帳戶，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="45528-131">If not, click **Add User or Group**, enter the account under which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent runs in the **Select Users, Computers, Service Accounts, or Groups** dialog box, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="45528-132">針對您要加入以搭配 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 執行的每項權限重複這項操作。</span><span class="sxs-lookup"><span data-stu-id="45528-132">Repeat for each permission that you want to add to run with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="45528-133">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="45528-133">When finished, click **OK**.</span></span>  
  
  
