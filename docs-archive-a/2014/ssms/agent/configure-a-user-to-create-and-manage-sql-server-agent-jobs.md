---
title: 設定使用者可建立及管理 SQL Server Agent 作業 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, user configuration
- jobs [SQL Server Agent], user configuration
- SQLAgentUserRole database role
- proxy accounts [SQL Server Agent]
ms.assetid: 67897e3e-b7d0-43dd-a2e2-2840ec4dd1ef
author: stevestein
ms.author: sstein
ms.openlocfilehash: 83313389b3b872004fb23b0babdad19cfb5b8e7d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606576"
---
# <a name="configure-a-user-to-create-and-manage-sql-server-agent-jobs"></a><span data-ttu-id="18dd8-102">Configure a User to Create and Manage SQL Server Agent Jobs</span><span class="sxs-lookup"><span data-stu-id="18dd8-102">Configure a User to Create and Manage SQL Server Agent Jobs</span></span>
  <span data-ttu-id="18dd8-103">本主題描述如何設定使用者，以建立或執行 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業。</span><span class="sxs-lookup"><span data-stu-id="18dd8-103">This topic describes how to configure a user to create or execute [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span>  
  
-   <span data-ttu-id="18dd8-104">**開始之前：** [安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="18dd8-104">**Before you begin:**  [Security](#Security)</span></span>  
  
-   <span data-ttu-id="18dd8-105">**若要設定使用者以建立及管理 SQL Server Agent 作業，使用**  [SQL Server Management Studio](#SSMS)</span><span class="sxs-lookup"><span data-stu-id="18dd8-105">**To configure a user to create and manage SQL Server Agent jobs, using:**  [SQL Server Management Studio](#SSMS)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="18dd8-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="18dd8-106">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="18dd8-107">Security</span><span class="sxs-lookup"><span data-stu-id="18dd8-107">Security</span></span>  
 <span data-ttu-id="18dd8-108">若要設定使用者建立或執行 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業，您必須先將現有的 SQL Server 登入或 msdb 角色加入至 msdb 資料庫中的下列其中一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 固定資料庫角色： SQLAgentUserRole、SQLAgentReaderRole 或 SQLAgentOperatorRole。</span><span class="sxs-lookup"><span data-stu-id="18dd8-108">To configure a user to create or execute [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs, you must first add an existing SQL Server login or msdb role to one of the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles in the msdb database: SQLAgentUserRole, SQLAgentReaderRole, or SQLAgentOperatorRole.</span></span>  
  
 <span data-ttu-id="18dd8-109">根據預設，這些資料庫角色的成員可以在以其身分執行的自有作業步驟。</span><span class="sxs-lookup"><span data-stu-id="18dd8-109">By default, members of these database roles can create their own job steps that run as themselves.</span></span> <span data-ttu-id="18dd8-110">如果這些非管理使用者想要執行作業來執行其他作業步驟類型 (例如， [!INCLUDE[ssIS](../../includes/ssis-md.md)] 封裝)，則他們需要有 Proxy 帳戶的存取權。</span><span class="sxs-lookup"><span data-stu-id="18dd8-110">If these non-administrative users want to run jobs that execute other job step types (for example, [!INCLUDE[ssIS](../../includes/ssis-md.md)] packages), they will need to have access to a proxy account.</span></span> <span data-ttu-id="18dd8-111">系統管理員 (sysadmin) 固定伺服器角色的所有成員都擁有建立、修改和刪除 Proxy 帳戶的權限。</span><span class="sxs-lookup"><span data-stu-id="18dd8-111">All members of the sysadmin fixed server role have permission to create, modify, and delete proxy accounts.</span></span> <span data-ttu-id="18dd8-112">如需有關與這些 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 固定資料庫角色關聯之權限的詳細資訊，請參閱 [SQL Server Agent 固定資料庫角色](sql-server-agent-fixed-database-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="18dd8-112">For more information about the permissions that are associated with these [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles, see [SQL Server Agent Fixed Database Roles](sql-server-agent-fixed-database-roles.md).</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="18dd8-113">權限</span><span class="sxs-lookup"><span data-stu-id="18dd8-113">Permissions</span></span>  
 <span data-ttu-id="18dd8-114">如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="18dd8-114">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="18dd8-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="18dd8-115">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="18dd8-116">**若要將 SQL 登入或 msdb 角色加入 SQL Server Agent 固定資料庫角色中**</span><span class="sxs-lookup"><span data-stu-id="18dd8-116">**To add a SQL login or msdb role to a SQL Server Agent fixed database role**</span></span>  
  
1.  <span data-ttu-id="18dd8-117">在 **[物件總管]** 中展開伺服器。</span><span class="sxs-lookup"><span data-stu-id="18dd8-117">In **Object Explorer**, expand a server.</span></span>  
  
2.  <span data-ttu-id="18dd8-118">展開 **[安全性]**，再展開 **[登入]**。</span><span class="sxs-lookup"><span data-stu-id="18dd8-118">Expand **Security**, and then expand **Logins**.</span></span>  
  
3.  <span data-ttu-id="18dd8-119">以滑鼠右鍵按一下您要新增至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 固定資料庫角色的登入，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="18dd8-119">Right-click the login you wish to add to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database role, and select **Properties**.</span></span>  
  
4.  <span data-ttu-id="18dd8-120">在 [**登入屬性**] 對話方塊的 [**使用者對應**] 頁面上，選取包含的資料列 `msdb` 。</span><span class="sxs-lookup"><span data-stu-id="18dd8-120">On the **User Mapping** page of the **Login Properties** dialog box, select the row containing `msdb`.</span></span>  
  
5.  <span data-ttu-id="18dd8-121">在 **[資料庫角色成員資格對象: msdb]** 底下，核取適當的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 固定資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="18dd8-121">Under **Database role membership for: msdb**, check the appropriate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database role.</span></span>  
  
 <span data-ttu-id="18dd8-122">**若要設定 Proxy 帳戶來建立及管理 SQL Server Agent 作業步驟**</span><span class="sxs-lookup"><span data-stu-id="18dd8-122">**To configure a proxy account to create and manage SQL Server Agent job steps**</span></span>  
  
1.  <span data-ttu-id="18dd8-123">在 **[物件總管]** 中展開伺服器。</span><span class="sxs-lookup"><span data-stu-id="18dd8-123">In **Object Explorer**, expand a server.</span></span>  
  
2.  <span data-ttu-id="18dd8-124">展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="18dd8-124">Expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="18dd8-125">以滑鼠右鍵按一下 [Proxy]\*\*\*\*，然後選取 [新增 Proxy]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="18dd8-125">Right-click **Proxies** and select **New Proxy**.</span></span>  
  
4.  <span data-ttu-id="18dd8-126">在 **[新 Proxy 帳戶]** 對話方塊的 **[一般]** 頁面上，指定新 Proxy 的 Proxy 名稱、認證名稱及描述。</span><span class="sxs-lookup"><span data-stu-id="18dd8-126">On the **General** page of the **New Proxy Account** dialog, specify the proxy name, credential name, and description for the new proxy.</span></span> <span data-ttu-id="18dd8-127">請注意，在建立 SQL Server Agent Proxy 之前，您必須先建立認證。</span><span class="sxs-lookup"><span data-stu-id="18dd8-127">Note that you must create a credential first before creating a SQL Server Agent proxy.</span></span> <span data-ttu-id="18dd8-128">如需建立認證的詳細資訊，請參閱[建立認證](../../relational-databases/security/authentication-access/create-a-credential.md)和[建立認證 &#40;transact-sql&#41;](/sql/t-sql/statements/create-credential-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="18dd8-128">For more information about creating a credential, see [Create a Credential](../../relational-databases/security/authentication-access/create-a-credential.md) and [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql).</span></span>  
  
5.  <span data-ttu-id="18dd8-129">檢查這個 Proxy 適當的子系統。</span><span class="sxs-lookup"><span data-stu-id="18dd8-129">Check the appropriate subsystems for this proxy.</span></span>  
  
6.  <span data-ttu-id="18dd8-130">在 **[主體]** 頁面上，加入或移除登入或角色，藉此授與或移除 Proxy 帳戶的存取。</span><span class="sxs-lookup"><span data-stu-id="18dd8-130">On the **Principals** page, add or remove logins or roles to grant or remove access to the proxy account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18dd8-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18dd8-131">See Also</span></span>  
 [<span data-ttu-id="18dd8-132">實作 SQL Server Agent 安全性</span><span class="sxs-lookup"><span data-stu-id="18dd8-132">Implement SQL Server Agent Security</span></span>](implement-sql-server-agent-security.md)  
  
  
