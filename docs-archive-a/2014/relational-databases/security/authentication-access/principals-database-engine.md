---
title: 主體 (Database Engine) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.roleproperties.selectroll.f1
- sql12.swb.databaseuser.permissions.user.f1--May use common.permissions
helpviewer_keywords:
- certificates [SQL Server], principals
- roles [SQL Server], principals
- permissions [SQL Server], principals
- '##MS_SQLAuthenticatorCertificate##'
- principals [SQL Server]
- '##MS_SQLResourceSigningCertificate##'
- groups [SQL Server], principals
- '##MS_AgentSigningCertificate##'
- authentication [SQL Server], principals
- schemas [SQL Server], principals
- principals [SQL Server], about principals
- security [SQL Server], principals
- users [SQL Server], principals
- '##MS_SQLReplicationSigningCertificate##'
ms.assetid: 3f7adbf7-6e40-4396-a8ca-71cbb843b5c2
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 808c8516b3ed9e95ea4c724736461cb00923a7fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606713"
---
# <a name="principals-database-engine"></a><span data-ttu-id="e8c9b-102">主體 (Database Engine)</span><span class="sxs-lookup"><span data-stu-id="e8c9b-102">Principals (Database Engine)</span></span>
  <span data-ttu-id="e8c9b-103">「主體」是可要求 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資源的實體。</span><span class="sxs-lookup"><span data-stu-id="e8c9b-103">*Principals* are entities that can request [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resources.</span></span> <span data-ttu-id="e8c9b-104">主體就像其他 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 授權模型的元件一樣，可以階層方式安排。</span><span class="sxs-lookup"><span data-stu-id="e8c9b-104">Like other components of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] authorization model, principals can be arranged in a hierarchy.</span></span> <span data-ttu-id="e8c9b-105">主體的影響範圍，取決於主體定義的範圍：Windows、伺服器、資料庫；以及主體是否為不可分割或集合。</span><span class="sxs-lookup"><span data-stu-id="e8c9b-105">The scope of influence of a principal depends on the scope of the definition of the principal: Windows, server, database; and whether the principal is indivisible or a collection.</span></span> <span data-ttu-id="e8c9b-106">「Windows 登入」是不可分割主體的一個範例，而「Windows 群組」則是主體為集合的範例。</span><span class="sxs-lookup"><span data-stu-id="e8c9b-106">A Windows Login is an example of an indivisible principal, and a Windows Group is an example of a principal that is a collection.</span></span> <span data-ttu-id="e8c9b-107">每個主體都有一個安全性識別碼 (SID)。</span><span class="sxs-lookup"><span data-stu-id="e8c9b-107">Every principal has a security identifier (SID).</span></span>  
  
 <span data-ttu-id="e8c9b-108">**Windows 層級主體**</span><span class="sxs-lookup"><span data-stu-id="e8c9b-108">**Windows-level principals**</span></span>  
  
-   <span data-ttu-id="e8c9b-109">Windows 網域登入</span><span class="sxs-lookup"><span data-stu-id="e8c9b-109">Windows Domain Login</span></span>  
  
-   <span data-ttu-id="e8c9b-110">Windows 本機登入</span><span class="sxs-lookup"><span data-stu-id="e8c9b-110">Windows Local Login</span></span>  
  
 <span data-ttu-id="e8c9b-111">**SQL Server** -**層級\*\*\*\*主體**</span><span class="sxs-lookup"><span data-stu-id="e8c9b-111">**SQL Server**-**level** **principals**</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="e8c9b-112">登入</span><span class="sxs-lookup"><span data-stu-id="e8c9b-112">Login</span></span>  
  
-   <span data-ttu-id="e8c9b-113">伺服器角色</span><span class="sxs-lookup"><span data-stu-id="e8c9b-113">Server Role</span></span>  
  
 <span data-ttu-id="e8c9b-114">**資料庫層級主體**</span><span class="sxs-lookup"><span data-stu-id="e8c9b-114">**Database-level principals**</span></span>  
  
-   <span data-ttu-id="e8c9b-115">資料庫使用者</span><span class="sxs-lookup"><span data-stu-id="e8c9b-115">Database User</span></span>  
  
-   <span data-ttu-id="e8c9b-116">資料庫角色</span><span class="sxs-lookup"><span data-stu-id="e8c9b-116">Database Role</span></span>  
  
-   <span data-ttu-id="e8c9b-117">應用程式角色</span><span class="sxs-lookup"><span data-stu-id="e8c9b-117">Application Role</span></span>  
  
## <a name="the-sql-server-sa-login"></a><span data-ttu-id="e8c9b-118">SQL Server sa 登入</span><span class="sxs-lookup"><span data-stu-id="e8c9b-118">The SQL Server sa Login</span></span>  
 <span data-ttu-id="e8c9b-119">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sa 登入為伺服器層級的主體。</span><span class="sxs-lookup"><span data-stu-id="e8c9b-119">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sa log in is a server-level principal.</span></span> <span data-ttu-id="e8c9b-120">根據預設，安裝執行個體時會建立它。</span><span class="sxs-lookup"><span data-stu-id="e8c9b-120">By default, it is created when an instance is installed.</span></span> <span data-ttu-id="e8c9b-121">從 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]開始，sa 的預設資料庫就是 master。</span><span class="sxs-lookup"><span data-stu-id="e8c9b-121">Beginning in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], the default database of sa is master.</span></span> <span data-ttu-id="e8c9b-122">這是和舊版 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]不同的一項行為變更。</span><span class="sxs-lookup"><span data-stu-id="e8c9b-122">This is a change of behavior from earlier versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="public-database-role"></a><span data-ttu-id="e8c9b-123">public 資料庫角色</span><span class="sxs-lookup"><span data-stu-id="e8c9b-123">public Database Role</span></span>  
 <span data-ttu-id="e8c9b-124">每個資料庫使用者都屬於 public 資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="e8c9b-124">Every database user belongs to the public database role.</span></span> <span data-ttu-id="e8c9b-125">當使用者未被授與或拒絕安全性實體的特定權限時，該使用者會繼承授與給該安全性實體之 public 的權限。</span><span class="sxs-lookup"><span data-stu-id="e8c9b-125">When a user has not been granted or denied specific permissions on a securable, the user inherits the permissions granted to public on that securable.</span></span>  
  
## <a name="information_schema-and-sys"></a><span data-ttu-id="e8c9b-126">INFORMATION_SCHEMA 與 sys</span><span class="sxs-lookup"><span data-stu-id="e8c9b-126">INFORMATION_SCHEMA and sys</span></span>  
 <span data-ttu-id="e8c9b-127">每個資料庫都包含兩個在目錄檢視中顯示為使用者的實體：INFORMATION_SCHEMA 和 sys。</span><span class="sxs-lookup"><span data-stu-id="e8c9b-127">Every database includes two entities that appear as users in catalog views: INFORMATION_SCHEMA and sys.</span></span> <span data-ttu-id="e8c9b-128">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]需要這些實體。</span><span class="sxs-lookup"><span data-stu-id="e8c9b-128">These entities are required by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e8c9b-129">它們並非主體，也不能被修改或卸除。</span><span class="sxs-lookup"><span data-stu-id="e8c9b-129">They are not principals, and they cannot be modified or dropped.</span></span>  
  
## <a name="certificate-based-sql-server-logins"></a><span data-ttu-id="e8c9b-130">以憑證為基礎的 SQL Server 登入</span><span class="sxs-lookup"><span data-stu-id="e8c9b-130">Certificate-based SQL Server Logins</span></span>  
 <span data-ttu-id="e8c9b-131">以兩個 ## 符號括住的伺服器主體名稱僅供內部系統使用。</span><span class="sxs-lookup"><span data-stu-id="e8c9b-131">Server principals with names enclosed by double hash marks (##) are for internal system use only.</span></span> <span data-ttu-id="e8c9b-132">在安裝 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 時，將會從憑證建立下列主體，而且不應該刪除它們。</span><span class="sxs-lookup"><span data-stu-id="e8c9b-132">The following principals are created from certificates when [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is installed, and should not be deleted.</span></span>  
  
-   <span data-ttu-id="e8c9b-133">\##MS_SQLResourceSigningCertificate##</span><span class="sxs-lookup"><span data-stu-id="e8c9b-133">\##MS_SQLResourceSigningCertificate##</span></span>  
  
-   <span data-ttu-id="e8c9b-134">\##MS_SQLReplicationSigningCertificate##</span><span class="sxs-lookup"><span data-stu-id="e8c9b-134">\##MS_SQLReplicationSigningCertificate##</span></span>  
  
-   <span data-ttu-id="e8c9b-135">\##MS_SQLAuthenticatorCertificate##</span><span class="sxs-lookup"><span data-stu-id="e8c9b-135">\##MS_SQLAuthenticatorCertificate##</span></span>  
  
-   <span data-ttu-id="e8c9b-136">\##MS_AgentSigningCertificate##</span><span class="sxs-lookup"><span data-stu-id="e8c9b-136">\##MS_AgentSigningCertificate##</span></span>  
  
-   <span data-ttu-id="e8c9b-137">\##MS_PolicyEventProcessingLogin##</span><span class="sxs-lookup"><span data-stu-id="e8c9b-137">\##MS_PolicyEventProcessingLogin##</span></span>  
  
-   <span data-ttu-id="e8c9b-138">\##MS_PolicySigningCertificate##</span><span class="sxs-lookup"><span data-stu-id="e8c9b-138">\##MS_PolicySigningCertificate##</span></span>  
  
-   <span data-ttu-id="e8c9b-139">\##MS_PolicyTsqlExecutionLogin##</span><span class="sxs-lookup"><span data-stu-id="e8c9b-139">\##MS_PolicyTsqlExecutionLogin##</span></span>  
  
## <a name="the-guest-user"></a><span data-ttu-id="e8c9b-140">guest 使用者</span><span class="sxs-lookup"><span data-stu-id="e8c9b-140">The guest User</span></span>  
 <span data-ttu-id="e8c9b-141">每個資料庫都包括 **guest**。</span><span class="sxs-lookup"><span data-stu-id="e8c9b-141">Each database includes a **guest**.</span></span> <span data-ttu-id="e8c9b-142">具有資料庫存取權但在資料庫中沒有使用者帳戶的使用者，將繼承授與 **guest** 使用者的權限。</span><span class="sxs-lookup"><span data-stu-id="e8c9b-142">Permissions granted to the **guest** user are inherited by users who have access to the database, but who do not have a user account in the database.</span></span> <span data-ttu-id="e8c9b-143">無法卸載**guest**使用者，但可透過撤銷其許可權予以停用 `CONNECT` 。</span><span class="sxs-lookup"><span data-stu-id="e8c9b-143">The **guest** user cannot be dropped, but it can be disabled by revoking it's `CONNECT` permission.</span></span> <span data-ttu-id="e8c9b-144">在 `CONNECT` `REVOKE CONNECT FROM GUEST` master 或 tempdb 以外的任何資料庫中執行，即可撤銷此許可權。</span><span class="sxs-lookup"><span data-stu-id="e8c9b-144">The `CONNECT` permission can be revoked by executing `REVOKE CONNECT FROM GUEST` within any database other than master or tempdb.</span></span>  
  
## <a name="client-and-database-server"></a><span data-ttu-id="e8c9b-145">用戶端和資料庫伺服器</span><span class="sxs-lookup"><span data-stu-id="e8c9b-145">Client and Database Server</span></span>  
 <span data-ttu-id="e8c9b-146">根據定義，用戶端和資料庫伺服器都是安全性主體，而且可以維護其安全。</span><span class="sxs-lookup"><span data-stu-id="e8c9b-146">By definition, a client and a database server are security principals and can be secured.</span></span> <span data-ttu-id="e8c9b-147">建立安全的網路連接之前，這些實體可以進行相互驗證。</span><span class="sxs-lookup"><span data-stu-id="e8c9b-147">These entities can be mutually authenticated before a secure network connection is established.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="e8c9b-148">支援[Kerberos](https://go.microsoft.com/fwlink/?LinkId=100758)驗證通訊協定，其定義用戶端與網路驗證服務的互動方式。</span><span class="sxs-lookup"><span data-stu-id="e8c9b-148">supports the [Kerberos](https://go.microsoft.com/fwlink/?LinkId=100758) authentication protocol, which defines how clients interact with a network authentication service.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="e8c9b-149">相關工作</span><span class="sxs-lookup"><span data-stu-id="e8c9b-149">Related Tasks</span></span>  
 <span data-ttu-id="e8c9b-150">《 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 線上叢書》的本節中包括下列主題：</span><span class="sxs-lookup"><span data-stu-id="e8c9b-150">The following topics are included in this section of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Books Online:</span></span>  
  
-   [<span data-ttu-id="e8c9b-151">管理登入、使用者與結構描述的使用說明主題</span><span class="sxs-lookup"><span data-stu-id="e8c9b-151">Managing Logins, Users, and Schemas How-to Topics</span></span>](managing-logins-users-and-schemas-how-to-topics.md)  
  
-   [<span data-ttu-id="e8c9b-152">伺服器層級角色</span><span class="sxs-lookup"><span data-stu-id="e8c9b-152">Server-Level Roles</span></span>](server-level-roles.md)  
  
-   [<span data-ttu-id="e8c9b-153">資料庫層級角色</span><span class="sxs-lookup"><span data-stu-id="e8c9b-153">Database-Level Roles</span></span>](database-level-roles.md)  
  
-   [<span data-ttu-id="e8c9b-154">應用程式角色</span><span class="sxs-lookup"><span data-stu-id="e8c9b-154">Application Roles</span></span>](application-roles.md)  
  
## <a name="see-also"></a><span data-ttu-id="e8c9b-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8c9b-155">See Also</span></span>  
 <span data-ttu-id="e8c9b-156">[保護 SQL Server 的安全](../securing-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e8c9b-156">[Securing SQL Server](../securing-sql-server.md) </span></span>  
 <span data-ttu-id="e8c9b-157">[sys.database_principals &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-principals-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e8c9b-157">[sys.database_principals &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-principals-transact-sql) </span></span>  
 <span data-ttu-id="e8c9b-158">[sys.server_principals &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-principals-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e8c9b-158">[sys.server_principals &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-principals-transact-sql) </span></span>  
 <span data-ttu-id="e8c9b-159">[sys.sql_logins &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-logins-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e8c9b-159">[sys.sql_logins &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-logins-transact-sql) </span></span>  
 <span data-ttu-id="e8c9b-160">[sys.database_role_members &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-role-members-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e8c9b-160">[sys.database_role_members &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-role-members-transact-sql) </span></span>  
 <span data-ttu-id="e8c9b-161">[伺服器層級角色](server-level-roles.md) </span><span class="sxs-lookup"><span data-stu-id="e8c9b-161">[Server-Level Roles](server-level-roles.md) </span></span>  
 [<span data-ttu-id="e8c9b-162">資料庫層級角色</span><span class="sxs-lookup"><span data-stu-id="e8c9b-162">Database-Level Roles</span></span>](database-level-roles.md)  
  
  
