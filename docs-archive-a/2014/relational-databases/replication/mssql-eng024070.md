---
title: MSSQL_ENG024070 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG024070 error
ms.assetid: 23ac7e00-fab6-429b-9f85-2736a322aa65
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 07fcfcb96b284d46d46f63af4a650f925ef2de73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697918"
---
# <a name="mssql_eng024070"></a><span data-ttu-id="e57ff-102">MSSQL_ENG024070</span><span class="sxs-lookup"><span data-stu-id="e57ff-102">MSSQL_ENG024070</span></span>
    
## <a name="message-details"></a><span data-ttu-id="e57ff-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="e57ff-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e57ff-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e57ff-104">Product Name</span></span>|<span data-ttu-id="e57ff-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="e57ff-105">SQL Server</span></span>|  
|<span data-ttu-id="e57ff-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e57ff-106">Event ID</span></span>|<span data-ttu-id="e57ff-107">24070</span><span class="sxs-lookup"><span data-stu-id="e57ff-107">24070</span></span>|  
|<span data-ttu-id="e57ff-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="e57ff-108">Event Source</span></span>|<span data-ttu-id="e57ff-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e57ff-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e57ff-110">元件</span><span class="sxs-lookup"><span data-stu-id="e57ff-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="e57ff-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e57ff-111">Symbolic Name</span></span>||  
|<span data-ttu-id="e57ff-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e57ff-112">Message Text</span></span>|<span data-ttu-id="e57ff-113">用戶端沒有必要的權限。</span><span class="sxs-lookup"><span data-stu-id="e57ff-113">A required privilege is not held by the client.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e57ff-114">說明</span><span class="sxs-lookup"><span data-stu-id="e57ff-114">Explanation</span></span>  
 <span data-ttu-id="e57ff-115">這是不論是否使用複寫，都有可能引發的一般性錯誤。</span><span class="sxs-lookup"><span data-stu-id="e57ff-115">This is a general error that can be raised regardless of whether replication is being used.</span></span> <span data-ttu-id="e57ff-116">如果是複寫拓撲中的伺服器，通常是因為使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows 服務控制管理員 (而不是正確使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 組態管理員) 變更 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務帳戶，而引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="e57ff-116">For a server in a replication topology, the error is typically raised because the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account is changed by using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Service Control Manager instead of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="e57ff-117">當您在變更服務帳戶之後嘗試執行代理程式作業時，作業可能失敗，並會顯示訊息如下：</span><span class="sxs-lookup"><span data-stu-id="e57ff-117">When you try to run an agent job after changing the service account, the job might fail with an error message that is similar to the following:</span></span>  
  
 <span data-ttu-id="e57ff-118">「以使用者身分執行： \<UserAccount> 。</span><span class="sxs-lookup"><span data-stu-id="e57ff-118">"Executed as user: \<UserAccount>.</span></span> <span data-ttu-id="e57ff-119">複寫-複寫快照集子系統：代理程式 \<AgentName> 失敗。</span><span class="sxs-lookup"><span data-stu-id="e57ff-119">Replication-Replication Snapshot Subsystem: agent \<AgentName> failed.</span></span> <span data-ttu-id="e57ff-120">以使用者身分執行： \<UserAccount> 。</span><span class="sxs-lookup"><span data-stu-id="e57ff-120">Executed as user: \<UserAccount>.</span></span> <span data-ttu-id="e57ff-121">用戶端沒有必要的權限。</span><span class="sxs-lookup"><span data-stu-id="e57ff-121">A required privilege is not held by the client.</span></span> <span data-ttu-id="e57ff-122">步驟失敗。</span><span class="sxs-lookup"><span data-stu-id="e57ff-122">The step failed.</span></span> <span data-ttu-id="e57ff-123">`[SQLSTATE 42000] (Error 14151)`.</span><span class="sxs-lookup"><span data-stu-id="e57ff-123">`[SQLSTATE 42000] (Error 14151)`.</span></span> <span data-ttu-id="e57ff-124">步驟失敗。」</span><span class="sxs-lookup"><span data-stu-id="e57ff-124">The step failed."</span></span>  
  
 <span data-ttu-id="e57ff-125">發生這個問題是因為 Windows 服務控制管理員無法授與權限給 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 的新服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="e57ff-125">This problem occurs because the Windows Service Control Manager cannot grant the required permissions to the new service account for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e57ff-126">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e57ff-126">User Action</span></span>  
 <span data-ttu-id="e57ff-127">若要避免未來發生這個問題，一律要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員 (而非 Windows 服務控制管理員) 來變更服務帳戶及密碼。</span><span class="sxs-lookup"><span data-stu-id="e57ff-127">To avoid this problem in the future, always use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager instead of the Windows Service Control Manager to change service accounts and passwords.</span></span>  
  
 <span data-ttu-id="e57ff-128">若要解決這個問題，請使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員，將服務帳戶變更回原始帳戶。</span><span class="sxs-lookup"><span data-stu-id="e57ff-128">To resolve this problem, use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager to change the service account back to the original account.</span></span> <span data-ttu-id="e57ff-129">然後，使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員變更為新帳戶。</span><span class="sxs-lookup"><span data-stu-id="e57ff-129">Then, use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager to change to the new account.</span></span> <span data-ttu-id="e57ff-130">當您執行此動作時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員會將新帳戶加入至下列安全性群組：</span><span class="sxs-lookup"><span data-stu-id="e57ff-130">When you do this, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager adds the new account to the following security group:</span></span>  
  
 <span data-ttu-id="e57ff-131">SQLServer2008SQLAgentUser$ComputerName$InstanceName</span><span class="sxs-lookup"><span data-stu-id="e57ff-131">SQLServer2008SQLAgentUser$ComputerName$InstanceName</span></span>  
  
 <span data-ttu-id="e57ff-132">做為這個安全性群組的成員，便會授與新帳戶執行複寫代理程式作業所需的權限。</span><span class="sxs-lookup"><span data-stu-id="e57ff-132">Being a member of this security group grants to the new account the required permissions to run the replication agent job.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e57ff-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e57ff-133">See Also</span></span>  
 <span data-ttu-id="e57ff-134">[錯誤和事件參考 &#40;複寫&#41;](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="e57ff-134">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 <span data-ttu-id="e57ff-135">[管理複寫的登入與密碼](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span><span class="sxs-lookup"><span data-stu-id="e57ff-135">[Manage Logins and Passwords in Replication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span></span>  
 [<span data-ttu-id="e57ff-136">SQL Server 組態管理員</span><span class="sxs-lookup"><span data-stu-id="e57ff-136">SQL Server Configuration Manager</span></span>](../sql-server-configuration-manager.md)  
  
  
