---
title: 應用程式角色 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- application roles [SQL Server], about application roles
- principals [SQL Server], application roles
- credentials [SQL Server], roles
- application roles [SQL Server]
- roles [SQL Server], application
- permissions [SQL Server], roles
- users [SQL Server], application roles
- authentication [SQL Server], roles
- groups [SQL Server], roles
ms.assetid: dca18b8a-ca03-4b7f-9a46-8474d5b66f76
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: f2fcc7b1e333bb42a00675da5bb9fd559d1c34f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592571"
---
# <a name="application-roles"></a><span data-ttu-id="1a20a-102">應用程式角色</span><span class="sxs-lookup"><span data-stu-id="1a20a-102">Application Roles</span></span>
  <span data-ttu-id="1a20a-103">應用程式角色是資料庫主體，可以讓應用程式以其自有、類似使用者的權限來執行。</span><span class="sxs-lookup"><span data-stu-id="1a20a-103">An application role is a database principal that enables an application to run with its own, user-like permissions.</span></span> <span data-ttu-id="1a20a-104">利用應用程式角色，您可以只允許透過特定應用程式來連接的使用者存取特定的資料。</span><span class="sxs-lookup"><span data-stu-id="1a20a-104">You can use application roles to enable access to specific data to only those users who connect through a particular application.</span></span> <span data-ttu-id="1a20a-105">不像資料庫角色，應用程式角色不包含任何成員，且依預設是非使用中狀態。</span><span class="sxs-lookup"><span data-stu-id="1a20a-105">Unlike database roles, application roles contain no members and are inactive by default.</span></span> <span data-ttu-id="1a20a-106">應用程式角色可與這兩種驗證模式搭配運作。</span><span class="sxs-lookup"><span data-stu-id="1a20a-106">Application roles work with both authentication modes.</span></span> <span data-ttu-id="1a20a-107">應用程式角色是使用 **sp_setapprole**(需要有密碼) 予以啟用。</span><span class="sxs-lookup"><span data-stu-id="1a20a-107">Application roles are enabled by using **sp_setapprole**, which requires a password.</span></span> <span data-ttu-id="1a20a-108">因為應用程式角色是資料庫層級主體，所以它們只可以透過那些資料庫中授與 **guest**的權限來存取其他資料庫。</span><span class="sxs-lookup"><span data-stu-id="1a20a-108">Because application roles are a database-level principal, they can access other databases only through permissions granted in those databases to **guest**.</span></span> <span data-ttu-id="1a20a-109">因此，其他資料庫中的應用程式角色將無法存取任何已停用 **guest** 的資料庫。</span><span class="sxs-lookup"><span data-stu-id="1a20a-109">Therefore, any database in which **guest** has been disabled will be inaccessible to application roles in other databases.</span></span>  
  
 <span data-ttu-id="1a20a-110">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中，因為應用程式角色未與伺服器層級主體產生關聯，所以應用程式角色無法存取伺服器層級中繼資料。</span><span class="sxs-lookup"><span data-stu-id="1a20a-110">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], application roles cannot access server-level metadata because they are not associated with a server-level principal.</span></span> <span data-ttu-id="1a20a-111">若要停用這項限制，並藉此允許應用程式角色存取伺服器層級中繼資料，請設定全域旗標 4616。</span><span class="sxs-lookup"><span data-stu-id="1a20a-111">To disable this restriction and thereby allow application roles to access server-level metadata, set the global flag 4616.</span></span> <span data-ttu-id="1a20a-112">如需詳細資訊，請參閱[追蹤旗標 &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql) 和 [DBCC TRACEON &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1a20a-112">For more information, see [Trace Flags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql) and [DBCC TRACEON &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-transact-sql).</span></span>  
  
## <a name="connecting-with-an-application-role"></a><span data-ttu-id="1a20a-113">與應用程式角色連接</span><span class="sxs-lookup"><span data-stu-id="1a20a-113">Connecting with an Application Role</span></span>  
 <span data-ttu-id="1a20a-114">下列步驟是應用程式角色切換安全性內容的程序：</span><span class="sxs-lookup"><span data-stu-id="1a20a-114">The following steps make up the process by which an application role switches security contexts:</span></span>  
  
1.  <span data-ttu-id="1a20a-115">使用者執行用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="1a20a-115">A user executes a client application.</span></span>  
  
2.  <span data-ttu-id="1a20a-116">用戶端應用程式以使用者身分連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="1a20a-116">The client application connects to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] as the user.</span></span>  
  
3.  <span data-ttu-id="1a20a-117">接著，應用程式利用只有該應用程式知道的密碼執行 **sp_setapprole** 預存程序。</span><span class="sxs-lookup"><span data-stu-id="1a20a-117">The application then executes the **sp_setapprole** stored procedure with a password known only to the application.</span></span>  
  
4.  <span data-ttu-id="1a20a-118">若應用程式角色的名稱與密碼是有效的，則會啟用該應用程式角色。</span><span class="sxs-lookup"><span data-stu-id="1a20a-118">If the application role name and password are valid, the application role is enabled.</span></span>  
  
5.  <span data-ttu-id="1a20a-119">此時連接會遺失使用者的權限，並假設應用程式角色的權限。</span><span class="sxs-lookup"><span data-stu-id="1a20a-119">At this point the connection loses the permissions of the user and assumes the permissions of the application role.</span></span>  
  
 <span data-ttu-id="1a20a-120">透過應用程式角色取得的權限在連接階段中仍為有效。</span><span class="sxs-lookup"><span data-stu-id="1a20a-120">The permissions acquired through the application role remain in effect for the duration of the connection.</span></span>  
  
 <span data-ttu-id="1a20a-121">在舊版 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中，使用者在啟動應用程式角色後要重新取得其原始安全性內容的唯一方式，就是中斷連接並重新連接 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1a20a-121">In earlier versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the only way for a user to reacquire its original security context after starting an application role is to disconnect and reconnect to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1a20a-122">從 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]開始， **sp_setapprole** 就有一個選項可建立 Cookie。</span><span class="sxs-lookup"><span data-stu-id="1a20a-122">Beginning with [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], **sp_setapprole** has an option that creates a cookie.</span></span> <span data-ttu-id="1a20a-123">此 Cookie 包含在啟用應用程式角色之前的內容資訊。</span><span class="sxs-lookup"><span data-stu-id="1a20a-123">The cookie contains context information before the application role is enabled.</span></span> <span data-ttu-id="1a20a-124">**sp_unsetapprole** 可使用此 Cookie 將工作階段還原為其原始內容。</span><span class="sxs-lookup"><span data-stu-id="1a20a-124">The cookie can be used by **sp_unsetapprole** to revert the session to its original context.</span></span> <span data-ttu-id="1a20a-125">如需有關這個新選項與範例的詳細資訊，請參閱 [sp_setapprole &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-setapprole-transact-sql)的權限來存取其他資料庫。</span><span class="sxs-lookup"><span data-stu-id="1a20a-125">For information about this new option and an example, see [sp_setapprole &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-setapprole-transact-sql).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1a20a-126">**SqlClient** 不支援 ODBC [加密] 選項。</span><span class="sxs-lookup"><span data-stu-id="1a20a-126">The ODBC **encrypt** option is not supported by **SqlClient**.</span></span> <span data-ttu-id="1a20a-127">當您透過網路傳輸機密資訊時，請使用安全通訊端層 (SSL) 或 IPsec 來加密該通道。</span><span class="sxs-lookup"><span data-stu-id="1a20a-127">When you are transmitting confidential information over a network, use Secure Sockets Layer (SSL) or IPsec to encrypt the channel.</span></span> <span data-ttu-id="1a20a-128">如果您必須將認證保存在用戶端應用程式中，請使用 Cypto API 函數來加密認證。</span><span class="sxs-lookup"><span data-stu-id="1a20a-128">If you must persist credentials in the client application, encrypt the credentials by using the crypto API functions.</span></span> <span data-ttu-id="1a20a-129">在 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 及更新的版本中， *password* 參數儲存為單向雜湊。</span><span class="sxs-lookup"><span data-stu-id="1a20a-129">In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] and later versions, the parameter *password* is stored as a one-way hash.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="1a20a-130">相關工作</span><span class="sxs-lookup"><span data-stu-id="1a20a-130">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1a20a-131">建立應用程式角色。</span><span class="sxs-lookup"><span data-stu-id="1a20a-131">Create an application role.</span></span>|<span data-ttu-id="1a20a-132">[建立應用程式角色](create-an-application-role.md)和 [CREATE APPLICATION ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-application-role-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="1a20a-132">[Create an Application Role](create-an-application-role.md) and [CREATE APPLICATION ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-application-role-transact-sql)</span></span>|  
|<span data-ttu-id="1a20a-133">改變應用程式角色。</span><span class="sxs-lookup"><span data-stu-id="1a20a-133">Alter an application role.</span></span>|[<span data-ttu-id="1a20a-134">ALTER APPLICATION ROLE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1a20a-134">ALTER APPLICATION ROLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-application-role-transact-sql)|  
|<span data-ttu-id="1a20a-135">刪除應用程式角色。</span><span class="sxs-lookup"><span data-stu-id="1a20a-135">Delete an application role.</span></span>|[<span data-ttu-id="1a20a-136">DROP APPLICATION ROLE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1a20a-136">DROP APPLICATION ROLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-application-role-transact-sql)|  
|<span data-ttu-id="1a20a-137">使用應用程式角色。</span><span class="sxs-lookup"><span data-stu-id="1a20a-137">Using an application role.</span></span>|[<span data-ttu-id="1a20a-138">sp_setapprole &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1a20a-138">sp_setapprole &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-setapprole-transact-sql)|  
  
## <a name="see-also"></a><span data-ttu-id="1a20a-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a20a-139">See Also</span></span>  
 [<span data-ttu-id="1a20a-140">保護 SQL Server 的安全</span><span class="sxs-lookup"><span data-stu-id="1a20a-140">Securing SQL Server</span></span>](../securing-sql-server.md)  
  
  
