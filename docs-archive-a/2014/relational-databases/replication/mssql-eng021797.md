---
title: MSSQL_ENG021797 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021797 error
ms.assetid: 54d83a1e-43fd-449c-a2b2-fdda2609a534
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d33ade7e7eea9fa9e95453a5b232447f7b222b18
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697930"
---
# <a name="mssql_eng021797"></a><span data-ttu-id="cebab-102">MSSQL_ENG021797</span><span class="sxs-lookup"><span data-stu-id="cebab-102">MSSQL_ENG021797</span></span>
    
## <a name="message-details"></a><span data-ttu-id="cebab-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="cebab-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cebab-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="cebab-104">Product Name</span></span>|<span data-ttu-id="cebab-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="cebab-105">SQL Server</span></span>|  
|<span data-ttu-id="cebab-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="cebab-106">Event ID</span></span>|<span data-ttu-id="cebab-107">21797</span><span class="sxs-lookup"><span data-stu-id="cebab-107">21797</span></span>|  
|<span data-ttu-id="cebab-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="cebab-108">Event Source</span></span>|<span data-ttu-id="cebab-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="cebab-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="cebab-110">元件</span><span class="sxs-lookup"><span data-stu-id="cebab-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="cebab-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="cebab-111">Symbolic Name</span></span>||  
|<span data-ttu-id="cebab-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="cebab-112">Message Text</span></span>|<span data-ttu-id="cebab-113">'%s' 必須是有效的 Windows 登入，格式為：'MACHINE\Login' 或 'DOMAIN\Login'。</span><span class="sxs-lookup"><span data-stu-id="cebab-113">'%s' must be a valid Windows Login in the form: 'MACHINE\Login' or 'DOMAIN\Login'.</span></span> <span data-ttu-id="cebab-114">請參閱 '%s' 的文件集。</span><span class="sxs-lookup"><span data-stu-id="cebab-114">Please see the documentation for '%s'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cebab-115">說明</span><span class="sxs-lookup"><span data-stu-id="cebab-115">Explanation</span></span>  
 <span data-ttu-id="cebab-116">如果為參數指定的值 **@job_login** 為 null 或無效，下列複寫預存程式就會引發此錯誤。</span><span class="sxs-lookup"><span data-stu-id="cebab-116">This error is raised by the following replication stored procedures if the value specified for the **@job_login** parameter is null or not valid.</span></span> <span data-ttu-id="cebab-117">如果 **db_owner** 固定資料庫角色成員從舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行指令碼，則可能發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="cebab-117">This error can occur if a member of the **db_owner** fixed database role runs scripts from previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="cebab-118">安全性模型在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]中已變更，同時必須更新這些指令碼。</span><span class="sxs-lookup"><span data-stu-id="cebab-118">The security model changed in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], and these scripts must be updated.</span></span>  
  
-   [<span data-ttu-id="cebab-119">sp_addlogreader_agent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cebab-119">sp_addlogreader_agent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql)  
  
-   [<span data-ttu-id="cebab-120">sp_addqreader_agent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cebab-120">sp_addqreader_agent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql)  
  
-   [<span data-ttu-id="cebab-121">sp_addpublication_snapshot &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cebab-121">sp_addpublication_snapshot &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql)  
  
-   [<span data-ttu-id="cebab-122">sp_addpushsubscription_agent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cebab-122">sp_addpushsubscription_agent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql)  
  
-   [<span data-ttu-id="cebab-123">sp_addpullsubscription_agent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cebab-123">sp_addpullsubscription_agent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)  
  
-   [<span data-ttu-id="cebab-124">sp_addmergepushsubscription_agent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cebab-124">sp_addmergepushsubscription_agent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql)  
  
-   [<span data-ttu-id="cebab-125">sp_addmergepullsubscription_agent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cebab-125">sp_addmergepullsubscription_agent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql)  
  
 <span data-ttu-id="cebab-126">這些預存程序可由適當伺服器上的 **sysadmin** 固定伺服器角色之成員執行，或可由適當資料庫中的 **db_owner** 固定資料庫角色之成員來執行。</span><span class="sxs-lookup"><span data-stu-id="cebab-126">These stored procedures can be executed by a member of the **sysadmin** fixed server role on the appropriate server or a member of the **db_owner** fixed database role in the appropriate database.</span></span> <span data-ttu-id="cebab-127">每個預存程序均會建立一個代理程式作業，並允許您指定代理程式執行所使用的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="cebab-127">The stored procedures each create an agent job and allow you to specify the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account under which the agent runs.</span></span> <span data-ttu-id="cebab-128">對於 **sysadmin** 角色中的使用者，即使未指定 Windows 帳戶(如果帳戶已指定，則其必須是有效帳戶)，也會隱含建立代理程式作業；代理程式會在適當伺服器端的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理程式服務帳戶內容下執行。</span><span class="sxs-lookup"><span data-stu-id="cebab-128">For users in the **sysadmin** role, agent jobs are created implicitly even if a Windows account is not specified (if an account is specified, it must be valid); agents run under the context of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account at the appropriate server.</span></span> <span data-ttu-id="cebab-129">雖然不需要此帳戶，但安全性最佳做法是為代理程式指定不同的帳戶。</span><span class="sxs-lookup"><span data-stu-id="cebab-129">Although the account is not required, it is a security best practice to specify a separate account for the agents.</span></span> <span data-ttu-id="cebab-130">如需詳細資訊，請參閱 [複寫代理程式安全性模型](security/replication-agent-security-model.md)。</span><span class="sxs-lookup"><span data-stu-id="cebab-130">For more information, see [Replication Agent Security Model](security/replication-agent-security-model.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cebab-131">使用者動作</span><span class="sxs-lookup"><span data-stu-id="cebab-131">User Action</span></span>  
 <span data-ttu-id="cebab-132">請確定您為每個程式的參數指定有效的 Windows 帳戶 **@job_login** 。</span><span class="sxs-lookup"><span data-stu-id="cebab-132">Ensure you specify a valid Windows account for the **@job_login** parameter of each procedure.</span></span> <span data-ttu-id="cebab-133">若您有上一版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]複寫指令碼，請更新這些指令碼以納入 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]所需的預存程序和參數。</span><span class="sxs-lookup"><span data-stu-id="cebab-133">If you have replication scripts from previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], update these scripts to include the stored procedures and parameters required by [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="cebab-134">如需詳細資訊，請參閱[升級複寫指令碼 &#40;複寫 Transact-SQL 程式設計&#41;](administration/upgrade-replication-scripts-replication-transact-sql-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="cebab-134">For more information, see [Upgrade Replication Scripts &#40;Replication Transact-SQL Programming&#41;](administration/upgrade-replication-scripts-replication-transact-sql-programming.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cebab-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cebab-135">See Also</span></span>  
 [<span data-ttu-id="cebab-136">錯誤和事件參考 &#40;複寫&#41;</span><span class="sxs-lookup"><span data-stu-id="cebab-136">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
