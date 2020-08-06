---
title: 實作 SQL Server Agent 安全性 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, security
- security [SQL Server Agent], about security
- security [SQL Server Agent]
- security [SQL Server], SQL Server Agent
ms.assetid: d770d35c-c8de-4e00-9a85-7d03f45a0f0d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8b70449ace66d4e33a547eca1c0b19eafabde5a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699214"
---
# <a name="implement-sql-server-agent-security"></a><span data-ttu-id="1684c-102">實作 SQL Server Agent 安全性</span><span class="sxs-lookup"><span data-stu-id="1684c-102">Implement SQL Server Agent Security</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1684c-103">Agent 讓資料庫管理員可以在只具有執行作業步驟所需權限的安全內容中執行每個作業步驟，此權限由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Proxy 決定。</span><span class="sxs-lookup"><span data-stu-id="1684c-103">Agent lets the database administrator run each job step in a security context that has only the permissions required to perform that job step, which is determined by a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxy.</span></span> <span data-ttu-id="1684c-104">若要設定特定作業步驟的權限，請建立具有必要權限的 Proxy，然後將該 Proxy 指派給作業步驟。</span><span class="sxs-lookup"><span data-stu-id="1684c-104">To set the permissions for a particular job step, you create a proxy that has the required permissions and then assign that proxy to the job step.</span></span> <span data-ttu-id="1684c-105">您可以將 Proxy 指派給多個作業步驟。</span><span class="sxs-lookup"><span data-stu-id="1684c-105">A proxy can be specified for more than one job step.</span></span> <span data-ttu-id="1684c-106">對於要求相同權限的作業步驟，可以使用相同的 Proxy。</span><span class="sxs-lookup"><span data-stu-id="1684c-106">For job steps that require the same permissions, you use the same proxy.</span></span>  
  
 <span data-ttu-id="1684c-107">下一節將解釋您必須授與使用者哪些資料庫角色，他們才能使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 來建立或執行作業。</span><span class="sxs-lookup"><span data-stu-id="1684c-107">The following section explains what database role you must grant to users so they can create or execute jobs by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
## <a name="granting-access-to-sql-server-agent"></a><span data-ttu-id="1684c-108">授與 SQL Server Agent 的存取權</span><span class="sxs-lookup"><span data-stu-id="1684c-108">Granting Access to SQL Server Agent</span></span>  
 <span data-ttu-id="1684c-109">若要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent，使用者必須是下列一個或多個固定資料庫角色的成員：</span><span class="sxs-lookup"><span data-stu-id="1684c-109">To use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, users must be a member of one or more of the following fixed database roles:</span></span>  
  
-   <span data-ttu-id="1684c-110">**SQLAgentUserRole**</span><span class="sxs-lookup"><span data-stu-id="1684c-110">**SQLAgentUserRole**</span></span>  
  
-   <span data-ttu-id="1684c-111">**SQLAgentReaderRole**</span><span class="sxs-lookup"><span data-stu-id="1684c-111">**SQLAgentReaderRole**</span></span>  
  
-   <span data-ttu-id="1684c-112">**SQLAgentOperatorRole**</span><span class="sxs-lookup"><span data-stu-id="1684c-112">**SQLAgentOperatorRole**</span></span>  
  
 <span data-ttu-id="1684c-113">這些角色儲存在 **msdb** 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="1684c-113">These roles are stored in the **msdb** database.</span></span> <span data-ttu-id="1684c-114">根據預設，沒有任何使用者隸屬於這些資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="1684c-114">By default, no user is a member of these database roles.</span></span> <span data-ttu-id="1684c-115">您必須明確授與這些角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="1684c-115">Membership in these roles must be granted explicitly.</span></span> <span data-ttu-id="1684c-116">**系統管理員** 固定伺服器角色的成員使用者對於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 具有完整的存取權，完全不需要是這些固定資料庫角色的成員，就能使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent。</span><span class="sxs-lookup"><span data-stu-id="1684c-116">Users who are members of the **sysadmin** fixed server role have full access to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, and do not need to be a member of these fixed database roles to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="1684c-117">若使用者不是這些資料庫角色或 **系統管理員** 角色的成員，當他們使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 連線到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，將無法使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]Agent 節點。</span><span class="sxs-lookup"><span data-stu-id="1684c-117">If a user is not a member of one of these database roles or of the **sysadmin** role, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node is not available to them when they connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="1684c-118">這些資料庫角色的成員可以檢視與執行自己所擁有的物件，並建立以現有 Proxy 帳戶身分執行的作業步驟。</span><span class="sxs-lookup"><span data-stu-id="1684c-118">Members of these database roles can view and execute jobs that they own, and create job steps that run as an existing proxy account.</span></span> <span data-ttu-id="1684c-119">如需上述每個角色所關聯之特定權限的詳細資訊，請參閱＜ [SQL Server Agent 固定資料庫角色](sql-server-agent-fixed-database-roles.md)＞。</span><span class="sxs-lookup"><span data-stu-id="1684c-119">For more information about the specific permissions that are associated with each of these roles, see [SQL Server Agent Fixed Database Roles](sql-server-agent-fixed-database-roles.md).</span></span>  
  
 <span data-ttu-id="1684c-120">**系統管理員** 固定伺服器角色的成員有權建立、修改與刪除 Poxy 帳戶。</span><span class="sxs-lookup"><span data-stu-id="1684c-120">Members of the **sysadmin** fixed server role have permission to create, modify, and delete proxy accounts.</span></span> <span data-ttu-id="1684c-121">**系統管理員** 角色的成員有權建立以 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務帳戶 (此帳戶是用於啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 的帳戶)。</span><span class="sxs-lookup"><span data-stu-id="1684c-121">Members of the **sysadmin** role have permission to create job steps that do not specify a proxy, but instead run as the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, which is the account that is used to start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
## <a name="guidelines"></a><span data-ttu-id="1684c-122">指導方針</span><span class="sxs-lookup"><span data-stu-id="1684c-122">Guidelines</span></span>  
 <span data-ttu-id="1684c-123">請依照下列指導方針來改進 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 實作的安全性。</span><span class="sxs-lookup"><span data-stu-id="1684c-123">Follow these guidelines to improve the security of your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent implementation:</span></span>  
  
-   <span data-ttu-id="1684c-124">為 Proxy 建立專屬的使用者帳戶，並只使用這些 Proxy 使用者帳戶來執行作業步驟。</span><span class="sxs-lookup"><span data-stu-id="1684c-124">Create dedicated user accounts specifically for proxies, and only use these proxy user accounts for running job steps.</span></span>  
  
-   <span data-ttu-id="1684c-125">只授與必要的權限給 Proxy 使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="1684c-125">Only grant the necessary permissions to proxy user accounts.</span></span> <span data-ttu-id="1684c-126">對於指派給特定 Proxy 帳戶的作業步驟，只授與它們執行所需的必要權限。</span><span class="sxs-lookup"><span data-stu-id="1684c-126">Grant only those permissions actually required to run the job steps that are assigned to a given proxy account.</span></span>  
  
-   <span data-ttu-id="1684c-127">請勿使用隸屬於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows Administrators **群組的 Microsoft Windows 帳戶身分執行** Agent 服務。</span><span class="sxs-lookup"><span data-stu-id="1684c-127">Do not run the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service under a Microsoft Windows account that is a member of the Windows **Administrators** group.</span></span>  
  
-   <span data-ttu-id="1684c-128">只有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認證存放區安全，Proxy 才安全。</span><span class="sxs-lookup"><span data-stu-id="1684c-128">Proxies are only as secure as the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] credential store.</span></span>  
  
-   <span data-ttu-id="1684c-129">如果使用者寫入作業可以寫入 NT 事件記錄檔，它們可以透過 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 引發警示。</span><span class="sxs-lookup"><span data-stu-id="1684c-129">If user write operations can write to the NT Event log, they can raise alerts via [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
-   <span data-ttu-id="1684c-130">請勿將 NT 管理員帳戶指定為服務帳戶或 Proxy 帳戶。</span><span class="sxs-lookup"><span data-stu-id="1684c-130">Do not specify the NT Admin account as a service account or proxy account.</span></span>  
  
-   <span data-ttu-id="1684c-131">請注意，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 有存取對方資產的權限。</span><span class="sxs-lookup"><span data-stu-id="1684c-131">Note that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent have access to each other's assets.</span></span> <span data-ttu-id="1684c-132">這兩個服務共用單一處理序空間，而且 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務上的系統管理員 (sysadmin)。</span><span class="sxs-lookup"><span data-stu-id="1684c-132">The two services share a single process space and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is a sysadmin on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
-   <span data-ttu-id="1684c-133">當 TSX 在 MSX 上編列時，MSX 系統管理員 (sysadmin) 會取得 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]TSX 執行個體的完整控制權。</span><span class="sxs-lookup"><span data-stu-id="1684c-133">When a TSX enlists with an MSX, the MSX sysadmins gets total control over the TSX instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="1684c-134">ACE 是延伸模組，並不能叫用它本身。</span><span class="sxs-lookup"><span data-stu-id="1684c-134">ACE is an extension and cannot invoke itself.</span></span> <span data-ttu-id="1684c-135">ACE 是由 Chainer ScenarioEngine.exe (也稱為 Microsoft.SqlServer.Chainer.Setup.exe) 叫用，也可由另一個主機處理序叫用。</span><span class="sxs-lookup"><span data-stu-id="1684c-135">ACE is invoked by Chainer ScenarioEngine.exe - also known as Microsoft.SqlServer.Chainer.Setup.exe - or it can be invoked by another host process.</span></span>  
  
-   <span data-ttu-id="1684c-136">ACE 取決於 SSDP 所擁有的下列設定 DLL，因為 ACE 會呼叫 DLL 的這些 API：</span><span class="sxs-lookup"><span data-stu-id="1684c-136">ACE depends on the following configuration DLL's owned by SSDP, because those API's of DLL's are called by ACE:</span></span>  
  
    -   <span data-ttu-id="1684c-137">**SCO** - Microsoft.SqlServer.Configuration.Sco.dll，包括虛擬帳戶的新 SCO 驗證</span><span class="sxs-lookup"><span data-stu-id="1684c-137">**SCO** - Microsoft.SqlServer.Configuration.Sco.dll, including new SCO validations for virtual accounts</span></span>  
  
    -   <span data-ttu-id="1684c-138">**叢集** - Microsoft.SqlServer.Configuration.Cluster.dll</span><span class="sxs-lookup"><span data-stu-id="1684c-138">**Cluster** - Microsoft.SqlServer.Configuration.Cluster.dll</span></span>  
  
    -   <span data-ttu-id="1684c-139">**SFC** - Microsoft.SqlServer.Configuration.SqlConfigBase.dll</span><span class="sxs-lookup"><span data-stu-id="1684c-139">**SFC** - Microsoft.SqlServer.Configuration.SqlConfigBase.dll</span></span>  
  
    -   <span data-ttu-id="1684c-140">**延伸模組** - Microsoft.SqlServer.Configuration.ConfigExtension.dll</span><span class="sxs-lookup"><span data-stu-id="1684c-140">**Extension** - Microsoft.SqlServer.Configuration.ConfigExtension.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1684c-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1684c-141">See Also</span></span>  
 <span data-ttu-id="1684c-142">[預先定義的角色](../../reporting-services/security/role-definitions-predefined-roles.md) </span><span class="sxs-lookup"><span data-stu-id="1684c-142">[Predefined Roles](../../reporting-services/security/role-definitions-predefined-roles.md) </span></span>  
 <span data-ttu-id="1684c-143">[sp_addrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1684c-143">[sp_addrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql) </span></span>  
 <span data-ttu-id="1684c-144">[sp_droprolemember &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1684c-144">[sp_droprolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql) </span></span>  
 [<span data-ttu-id="1684c-145">SQL Server Database Engine 和 Azure SQL Database 的資訊安全中心</span><span class="sxs-lookup"><span data-stu-id="1684c-145">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
  
