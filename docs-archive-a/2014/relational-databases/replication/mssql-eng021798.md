---
title: MSSQL_ENG021798 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021798 error
ms.assetid: 596f5092-75ab-4a19-8582-588687c7b089
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 327b4a373c28376701ea12400215ab00367df66a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697924"
---
# <a name="mssql_eng021798"></a><span data-ttu-id="7b98b-102">MSSQL_ENG021798</span><span class="sxs-lookup"><span data-stu-id="7b98b-102">MSSQL_ENG021798</span></span>
    
## <a name="message-details"></a><span data-ttu-id="7b98b-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="7b98b-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7b98b-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="7b98b-104">Product Name</span></span>|<span data-ttu-id="7b98b-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="7b98b-105">SQL Server</span></span>|  
|<span data-ttu-id="7b98b-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="7b98b-106">Event ID</span></span>|<span data-ttu-id="7b98b-107">21798</span><span class="sxs-lookup"><span data-stu-id="7b98b-107">21798</span></span>|  
|<span data-ttu-id="7b98b-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="7b98b-108">Event Source</span></span>|<span data-ttu-id="7b98b-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="7b98b-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="7b98b-110">元件</span><span class="sxs-lookup"><span data-stu-id="7b98b-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="7b98b-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="7b98b-111">Symbolic Name</span></span>||  
|<span data-ttu-id="7b98b-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="7b98b-112">Message Text</span></span>|<span data-ttu-id="7b98b-113">必須先透過 '%s' 新增 '%s' 代理程式工作，方可繼續。</span><span class="sxs-lookup"><span data-stu-id="7b98b-113">The '%s' agent job must be added through '%s' before continuing.</span></span> <span data-ttu-id="7b98b-114">請參閱 '%s' 的文件集。</span><span class="sxs-lookup"><span data-stu-id="7b98b-114">Please see the documentation for '%s'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7b98b-115">說明</span><span class="sxs-lookup"><span data-stu-id="7b98b-115">Explanation</span></span>  
 <span data-ttu-id="7b98b-116">若要建立發行集，您必須是「發行者」上 **sysadmin** 固定伺服器角色的成員，或是發行集資料庫中 **db_owner** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="7b98b-116">To create a publication, you must be a member of the **sysadmin** fixed server role on the Publisher or a member of the **db_owner** fixed database role in the publication database.</span></span> <span data-ttu-id="7b98b-117">如果您是 **db_owner** 角色的成員，則以下情況會引發此錯誤：</span><span class="sxs-lookup"><span data-stu-id="7b98b-117">If you are a member of the **db_owner** role, this error is raised if:</span></span>  
  
-   <span data-ttu-id="7b98b-118">您會從 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="7b98b-118">You run scripts from [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].</span></span> <span data-ttu-id="7b98b-119">安全性模型在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]中已變更，同時必須更新這些指令碼。</span><span class="sxs-lookup"><span data-stu-id="7b98b-119">The security model changed in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], and these scripts must be updated.</span></span>  
  
-   <span data-ttu-id="7b98b-120">執行預存程序 **sp_addpublication** 之後，再執行 [sp_addlogreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7b98b-120">The stored procedure **sp_addpublication** is executed before executing [sp_addlogreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql).</span></span> <span data-ttu-id="7b98b-121">適用於所有交易式發行集。</span><span class="sxs-lookup"><span data-stu-id="7b98b-121">This applies to all transactional publications.</span></span>  
  
-   <span data-ttu-id="7b98b-122">執行預存程序 **sp_addpublication** 之後，再執行 [sp_addqreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7b98b-122">The stored procedure **sp_addpublication** is executed before executing [sp_addqreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql).</span></span> <span data-ttu-id="7b98b-123">這適用于已針對佇列更新訂閱啟用的交易式發行集 (**@allow_queued_tran** **sp_addpublication**) 的參數值為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="7b98b-123">This applies to transactional publications that are enabled for queued updating subscriptions (a value of TRUE for the **@allow_queued_tran** parameter of **sp_addpublication**).</span></span>  
  
 <span data-ttu-id="7b98b-124">預存程序 **sp_addlogreader_agent** 和 **sp_addqreader_agent** 將分別建立一個代理程式作業，可讓您指定執行代理程式的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="7b98b-124">The stored procedures **sp_addlogreader_agent** and **sp_addqreader_agent** each create an agent job and allow you to specify the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account under which the agent runs.</span></span> <span data-ttu-id="7b98b-125">對於 **sysadmin** 角色的使用者，如果 **sp_addlogreader_agent** 和 **sp_addqreader_agent** 未執行，代理程式作業將以隱含的方式建立；代理程式會在「散發者」端的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務帳戶內容中執行。</span><span class="sxs-lookup"><span data-stu-id="7b98b-125">For users in the **sysadmin** role, agent jobs are created implicitly if **sp_addlogreader_agent** and **sp_addqreader_agent** are not executed; agents run under the context of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account at the Distributor.</span></span> <span data-ttu-id="7b98b-126">儘管 **sysadmin** 角色的使用者不需要 **sp_addlogreader_agent** 和 **sp_addqreader_agent** ，但基於安全性考量，最好是為代理程式指定單獨的帳戶。</span><span class="sxs-lookup"><span data-stu-id="7b98b-126">Although **sp_addlogreader_agent** and **sp_addqreader_agent** are not required for users in the **sysadmin** role, it is a security best practice to specify a separate account for the agents.</span></span> <span data-ttu-id="7b98b-127">如需詳細資訊，請參閱 [複寫代理程式安全性模型](security/replication-agent-security-model.md)。</span><span class="sxs-lookup"><span data-stu-id="7b98b-127">For more information, see [Replication Agent Security Model](security/replication-agent-security-model.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7b98b-128">使用者動作</span><span class="sxs-lookup"><span data-stu-id="7b98b-128">User Action</span></span>  
 <span data-ttu-id="7b98b-129">確保您以正確的順序執行程序。</span><span class="sxs-lookup"><span data-stu-id="7b98b-129">Ensure you execute procedures in the correct order.</span></span> <span data-ttu-id="7b98b-130">如需詳細資訊，請參閱[建立發行](publish/create-a-publication.md)集、更新這些腳本以包含 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新版本所需的預存程式和參數。</span><span class="sxs-lookup"><span data-stu-id="7b98b-130">For more information, see [Create a Publication](publish/create-a-publication.md), update these scripts to include the stored procedures and parameters required by [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions.</span></span> <span data-ttu-id="7b98b-131">如需詳細資訊，請參閱[升級複寫指令碼 &#40;複寫 Transact-SQL 程式設計&#41;](administration/upgrade-replication-scripts-replication-transact-sql-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="7b98b-131">For more information, see [Upgrade Replication Scripts &#40;Replication Transact-SQL Programming&#41;](administration/upgrade-replication-scripts-replication-transact-sql-programming.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b98b-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b98b-132">See Also</span></span>  
 [<span data-ttu-id="7b98b-133">錯誤和事件參考 &#40;複寫&#41;</span><span class="sxs-lookup"><span data-stu-id="7b98b-133">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
