---
title: 被遺棄使用者疑難排解 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- orphaned users [SQL Server]
- logins [SQL Server], orphaned users
- troubleshooting [SQL Server], user accounts
- user accounts [SQL Server], orphaned users
- failover [SQL Server], managing metadata
- database mirroring [SQL Server], metadata
- users [SQL Server], orphaned
ms.assetid: 11eefa97-a31f-4359-ba5b-e92328224133
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5df714d818949b921ff2236e50d58913eab0e0db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595580"
---
# <a name="troubleshoot-orphaned-users-sql-server"></a><span data-ttu-id="2f392-102">被遺棄使用者疑難排解 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2f392-102">Troubleshoot Orphaned Users (SQL Server)</span></span>
  <span data-ttu-id="2f392-103">若要登入 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，則主體必須提供有效的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。</span><span class="sxs-lookup"><span data-stu-id="2f392-103">To log into an instance of Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a principal must have a valid [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span> <span data-ttu-id="2f392-104">此登入是用於驗證處理序，可確認是否允許該主體連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2f392-104">This login is used in the authentication process that verifies whether the principal is allowed to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2f392-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]伺服器實例上的登入可以在**server_principals**目錄檢視和**sys.sys**登入相容性檢視中看見。</span><span class="sxs-lookup"><span data-stu-id="2f392-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins on a server instance are visible in the **sys.server_principals** catalog view and the **sys.syslogins** compatibility view.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="2f392-106">登入會使用對應到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入的資料庫使用者來存取個別資料庫。</span><span class="sxs-lookup"><span data-stu-id="2f392-106">logins access individual databases using a database user that is mapped to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span> <span data-ttu-id="2f392-107">這項規則有兩個例外狀況：</span><span class="sxs-lookup"><span data-stu-id="2f392-107">There are two exceptions to this rule:</span></span>  
  
-   <span data-ttu-id="2f392-108">guest 帳戶</span><span class="sxs-lookup"><span data-stu-id="2f392-108">The guest account.</span></span>  
  
     <span data-ttu-id="2f392-109">在資料庫中啟用此帳戶時，會使未對應到資料庫使用者的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入都能以 guest 使用者的身分進入資料庫。</span><span class="sxs-lookup"><span data-stu-id="2f392-109">This is an account that, when enabled in the database, enables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins that are not mapped to a database user to enter the database as the guest user.</span></span>  
  
-   <span data-ttu-id="2f392-110">Microsoft Windows 群組成員資格。</span><span class="sxs-lookup"><span data-stu-id="2f392-110">Microsoft Windows group memberships.</span></span>  
  
     <span data-ttu-id="2f392-111">如果 Windows 使用者是 Windows 群組的成員，而且也是資料庫中的使用者，則從 Windows 使用者建立的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入可進入該資料庫。</span><span class="sxs-lookup"><span data-stu-id="2f392-111">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login created from a Windows user can enter a database if the Windows user is a member of a Windows group that is also a user in the database.</span></span>  
  
 <span data-ttu-id="2f392-112">有關 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入對應到資料庫使用者的資訊會儲存在資料庫內。</span><span class="sxs-lookup"><span data-stu-id="2f392-112">Information about the mapping of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to a database user is stored within the database.</span></span> <span data-ttu-id="2f392-113">它包括資料庫使用者的名稱和對應之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入的 SID。</span><span class="sxs-lookup"><span data-stu-id="2f392-113">It includes the name of the database user and the SID of the corresponding [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span> <span data-ttu-id="2f392-114">此資料庫使用者的權限使用於資料庫中的授權。</span><span class="sxs-lookup"><span data-stu-id="2f392-114">The permissions of this database user are used for authorization in the database.</span></span>  
  
 <span data-ttu-id="2f392-115">在伺服器執行個體上未定義或定義不正確之對應 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入的資料庫使用者無法登入此執行個體。</span><span class="sxs-lookup"><span data-stu-id="2f392-115">A database user for which the corresponding [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login is undefined or is incorrectly defined on a server instance cannot log in to the instance.</span></span> <span data-ttu-id="2f392-116">這類使用者就是伺服器執行個體上的資料庫 *「被遺棄使用者」* (Orphaned User)。</span><span class="sxs-lookup"><span data-stu-id="2f392-116">Such a user is said to be an *orphaned user* of the database on that server instance.</span></span> <span data-ttu-id="2f392-117">如果卸除了對應的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入，則資料庫使用者可能遭到遺棄。</span><span class="sxs-lookup"><span data-stu-id="2f392-117">A database user can become orphaned if the corresponding [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login is dropped.</span></span> <span data-ttu-id="2f392-118">此外，資料庫還原或附加到其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，也會讓資料庫使用者遭到遺棄。</span><span class="sxs-lookup"><span data-stu-id="2f392-118">Also, a database user can become orphaned after a database is restored or attached to a different instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2f392-119">如果資料庫使用者對應到的 SID 未出現在新的伺服器執行個體中，則會遭到遺棄。</span><span class="sxs-lookup"><span data-stu-id="2f392-119">Orphaning can happen if the database user is mapped to a SID that is not present in the new server instance.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2f392-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]登入無法存取缺少對應資料庫使用者的資料庫，除非該資料庫中已啟用**guest** 。</span><span class="sxs-lookup"><span data-stu-id="2f392-120">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login cannot access a database in which it lacks a corresponding database user unless **guest** is enabled in that database.</span></span> <span data-ttu-id="2f392-121">如需建立資料庫使用者帳戶的相關資訊，請參閱[CREATE user &#40;transact-sql&#41;](/sql/t-sql/statements/create-user-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2f392-121">For information about creating a database user account, see [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql).</span></span>  
  
## <a name="to-detect-orphaned-users"></a><span data-ttu-id="2f392-122">若要偵測被遺棄使用者</span><span class="sxs-lookup"><span data-stu-id="2f392-122">To Detect Orphaned Users</span></span>  
 <span data-ttu-id="2f392-123">若要偵測被遺棄使用者，請執行以下 Transact-SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="2f392-123">To detect orphaned users, execute the following Transact-SQL statements:</span></span>  
  
```  
USE <database_name>;  
GO;   
sp_change_users_login @Action='Report';  
GO;  
```  
  
 <span data-ttu-id="2f392-124">輸出會列出使用者及對應的安全性識別碼 (SID)，這些使用者皆為目前資料庫中的使用者，且並未與任何 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入有連結。</span><span class="sxs-lookup"><span data-stu-id="2f392-124">The output lists the users and corresponding security identifiers (SID) in the current database that are not linked to any [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span> <span data-ttu-id="2f392-125">如需詳細資訊，請參閱[sp_change_users_login &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2f392-125">For more information, see [sp_change_users_login &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2f392-126">**sp_change_users_login**不能與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 從 Windows 建立的登入一起使用。</span><span class="sxs-lookup"><span data-stu-id="2f392-126">**sp_change_users_login** cannot be used with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins that are created from Windows.</span></span>  
  
## <a name="to-resolve-an-orphaned-user"></a><span data-ttu-id="2f392-127">若要解析被遺棄使用者</span><span class="sxs-lookup"><span data-stu-id="2f392-127">To Resolve an Orphaned User</span></span>  
 <span data-ttu-id="2f392-128">若要解析被遺棄使用者，請使用以下程序：</span><span class="sxs-lookup"><span data-stu-id="2f392-128">To resolve an orphaned user, use the following procedure:</span></span>  
  
1.  <span data-ttu-id="2f392-129">下列命令會重新連結由 *<login_name>* 指定的伺服器登入帳戶與 *<database_user>* 所指定的資料庫使用者。</span><span class="sxs-lookup"><span data-stu-id="2f392-129">The following command relinks the server login account specified by *<login_name>* with the database user specified by *<database_user>*.</span></span>  
  
    ```  
    USE <database_name>;  
    GO  
    sp_change_users_login @Action='update_one', @UserNamePattern='<database_user>', @LoginName='<login_name>';  
    GO  
  
    ```  
  
     <span data-ttu-id="2f392-130">如需詳細資訊，請參閱[sp_change_users_login &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2f392-130">For more information, see [sp_change_users_login &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql).</span></span>  
  
2.  <span data-ttu-id="2f392-131">執行先前步驟中的程式碼後，使用者就能夠存取伺服器。</span><span class="sxs-lookup"><span data-stu-id="2f392-131">After you run the code in the preceding step, the user can access the database.</span></span> <span data-ttu-id="2f392-132">然後，使用者可以使用**sp_password**預存程式來改變 *<login_name>* 登入帳戶的密碼，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2f392-132">The user then can alter the password of the *<login_name>* login account by using the **sp_password** stored procedure, as follows:</span></span>  
  
    ```  
    USE master   
    GO  
    sp_password @old=NULL, @new='password', @loginame='<login_name>';  
    GO  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="2f392-133">只有具有 ALTER ANY LOGIN 權限的登入，才能夠變更其他使用者登入的密碼。</span><span class="sxs-lookup"><span data-stu-id="2f392-133">Only logins with the ALTER ANY LOGIN permission can change the password of another user's login.</span></span> <span data-ttu-id="2f392-134">不過，只有 **sysadmin** 角色成員才能修改 **sysadmin** 角色成員的密碼。</span><span class="sxs-lookup"><span data-stu-id="2f392-134">However, only members of the **sysadmin** role can modify passwords of **sysadmin** role members.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2f392-135">**sp_password**無法用於 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="2f392-135">**sp_password** cannot be used for [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows accounts.</span></span> <span data-ttu-id="2f392-136">透過 Windows 網路帳戶連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的使用者是由 Windows 驗證，因此他們的密碼只能在 Windows 中變更。</span><span class="sxs-lookup"><span data-stu-id="2f392-136">Users connecting to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] through their Windows network account are authenticated by Windows; therefore, their passwords can only be changed in Windows.</span></span>  
  
     <span data-ttu-id="2f392-137">如需詳細資訊，請參閱[sp_password &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-password-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2f392-137">For more information, see [sp_password &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-password-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f392-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f392-138">See Also</span></span>  
 <span data-ttu-id="2f392-139">[CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2f392-139">[CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql) </span></span>  
 <span data-ttu-id="2f392-140">[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2f392-140">[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql) </span></span>  
 <span data-ttu-id="2f392-141">[sp_change_users_login &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2f392-141">[sp_change_users_login &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql) </span></span>  
 <span data-ttu-id="2f392-142">[sp_addlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogin-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2f392-142">[sp_addlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogin-transact-sql) </span></span>  
 <span data-ttu-id="2f392-143">[sp_grantlogin &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-grantlogin-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2f392-143">[sp_grantlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-grantlogin-transact-sql) </span></span>  
 <span data-ttu-id="2f392-144">[sp_password &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-password-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2f392-144">[sp_password &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-password-transact-sql) </span></span>  
 <span data-ttu-id="2f392-145">[sys.sys使用者 &#40;Transact-sql&#41;](/sql/relational-databases/system-compatibility-views/sys-sysusers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2f392-145">[sys.sysusers &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-sysusers-transact-sql) </span></span>  
 [<span data-ttu-id="2f392-146">sys.sys登入 &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="2f392-146">sys.syslogins &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-compatibility-views/sys-syslogins-transact-sql)  
  
  
