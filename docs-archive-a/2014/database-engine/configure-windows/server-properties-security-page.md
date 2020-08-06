---
title: 伺服器屬性 (安全性頁面) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverproperties.security.f1
ms.assetid: b8a131c7-e7bd-4203-bf26-234f1ebfe622
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5f45c0a04a0d7cc627901d8de24175f1d63a99fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607085"
---
# <a name="server-properties-security-page"></a><span data-ttu-id="48433-102">伺服器屬性 (安全性頁面)</span><span class="sxs-lookup"><span data-stu-id="48433-102">Server Properties (Security Page)</span></span>
  <span data-ttu-id="48433-103">使用此頁面來檢視或修改伺服器安全性選項。</span><span class="sxs-lookup"><span data-stu-id="48433-103">Use this page to view or modify your server security options.</span></span>  
  
## <a name="server-authentication"></a><span data-ttu-id="48433-104">伺服器驗證</span><span class="sxs-lookup"><span data-stu-id="48433-104">Server Authentication</span></span>  
 <span data-ttu-id="48433-105">**Windows 驗證模式**</span><span class="sxs-lookup"><span data-stu-id="48433-105">**Windows Authentication mode**</span></span>  
 <span data-ttu-id="48433-106">使用 Windows 驗證來驗證所嘗試的連接。</span><span class="sxs-lookup"><span data-stu-id="48433-106">Uses Windows Authentication to validate attempted connections.</span></span> <span data-ttu-id="48433-107">如果在變更安全性模式時 **sa** 密碼空白，就會提示使用者輸入 **sa** 密碼。</span><span class="sxs-lookup"><span data-stu-id="48433-107">If the **sa** password is blank when the security mode is being changed, the user is prompted to enter an **sa** password.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="48433-108">Windows 驗證比 SQL Server 驗證更安全。</span><span class="sxs-lookup"><span data-stu-id="48433-108">Windows Authentication is much more secure than SQL Server Authentication.</span></span> <span data-ttu-id="48433-109">可能的話，您應該使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="48433-109">When possible, you should use Windows Authentication.</span></span>  
  
 <span data-ttu-id="48433-110">**SQL Server 及 Windows 驗證模式**</span><span class="sxs-lookup"><span data-stu-id="48433-110">**SQL Server and Windows Authentication mode**</span></span>  
 <span data-ttu-id="48433-111">使用混合模式驗證來確認所嘗試的連接，使其具有與舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="48433-111">Uses mixed mode authentication to verify attempted connections, for backward compatibility with earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="48433-112">如果在變更安全性模式時 **sa** 密碼空白，就會提示使用者輸入 **sa** 密碼。</span><span class="sxs-lookup"><span data-stu-id="48433-112">If the **sa** password is blank when the security mode is being changed, the user is prompted to enter an **sa** password.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="48433-113">變更安全性組態需要重新啟動此服務。</span><span class="sxs-lookup"><span data-stu-id="48433-113">Changing the security configuration requires a restart of the service.</span></span> <span data-ttu-id="48433-114">將伺服器驗證變更為 SQL Server 和 Windows 驗證模式時，不會自動啟用 SA 帳戶。</span><span class="sxs-lookup"><span data-stu-id="48433-114">When changing the Server Authentication to SQL Server and Windows Authentication mode the SA account is not automatically enabled.</span></span> <span data-ttu-id="48433-115">若要使用 SA 帳戶，請使用 ENABLE 選項來執行 [ALTER LOGIN](/sql/t-sql/statements/alter-login-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="48433-115">To use the SA account, execute [ALTER LOGIN](/sql/t-sql/statements/alter-login-transact-sql) with the ENABLE option.</span></span>  
  
## <a name="login-auditing"></a><span data-ttu-id="48433-116">登入稽核</span><span class="sxs-lookup"><span data-stu-id="48433-116">Login Auditing</span></span>  
 <span data-ttu-id="48433-117">**None**</span><span class="sxs-lookup"><span data-stu-id="48433-117">**None**</span></span>  
 <span data-ttu-id="48433-118">關閉登入稽核。</span><span class="sxs-lookup"><span data-stu-id="48433-118">Turns off login auditing.</span></span>  
  
 <span data-ttu-id="48433-119">**只限失敗的登入**</span><span class="sxs-lookup"><span data-stu-id="48433-119">**Failed logins only**</span></span>  
 <span data-ttu-id="48433-120">只限稽核不成功的登入。</span><span class="sxs-lookup"><span data-stu-id="48433-120">Audits unsuccessful logins only.</span></span>  
  
 <span data-ttu-id="48433-121">**只限成功的登入**</span><span class="sxs-lookup"><span data-stu-id="48433-121">**Successful logins only**</span></span>  
 <span data-ttu-id="48433-122">只限稽核成功的登入。</span><span class="sxs-lookup"><span data-stu-id="48433-122">Audits successful logins only.</span></span>  
  
 <span data-ttu-id="48433-123">**失敗和成功的登入**</span><span class="sxs-lookup"><span data-stu-id="48433-123">**Both failed and successful logins**</span></span>  
 <span data-ttu-id="48433-124">稽核所有登入嘗試。</span><span class="sxs-lookup"><span data-stu-id="48433-124">Audits all login attempts.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="48433-125">變更稽核層級需要重新啟動此服務。</span><span class="sxs-lookup"><span data-stu-id="48433-125">Changing the audit level requires restarting the service.</span></span>  
  
## <a name="server-proxy-account"></a><span data-ttu-id="48433-126">伺服器 Proxy 帳戶</span><span class="sxs-lookup"><span data-stu-id="48433-126">Server Proxy Account</span></span>  
 <span data-ttu-id="48433-127">**啟用伺服器 Proxy 帳戶**</span><span class="sxs-lookup"><span data-stu-id="48433-127">**Enable server proxy account**</span></span>  
 <span data-ttu-id="48433-128">啟用供 **xp_cmdshell**使用的帳戶。</span><span class="sxs-lookup"><span data-stu-id="48433-128">Enables an account for use by **xp_cmdshell**.</span></span> <span data-ttu-id="48433-129">Proxy 帳戶允許在執行作業系統命令時模擬登入、伺服器角色以及資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="48433-129">Proxy accounts allow for the impersonation of logins, server roles, and database roles when an operating system command is being executed.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="48433-130">伺服器 Proxy 帳戶所使用的登入至少應該具有執行工作所需的權限。</span><span class="sxs-lookup"><span data-stu-id="48433-130">The login used by the server proxy account should have the least privileges required to perform the intended work.</span></span> <span data-ttu-id="48433-131">惡意使用者可能會使用 Proxy 帳戶過多的權限來危害系統安全性。</span><span class="sxs-lookup"><span data-stu-id="48433-131">Excessive privileges for the proxy account could be used by a malicious user to compromise your system security.</span></span>  
  
 <span data-ttu-id="48433-132">**Proxy 帳戶**</span><span class="sxs-lookup"><span data-stu-id="48433-132">**Proxy account**</span></span>  
 <span data-ttu-id="48433-133">指定所使用的 Proxy 帳戶。</span><span class="sxs-lookup"><span data-stu-id="48433-133">Specify the proxy account used.</span></span>  
  
 <span data-ttu-id="48433-134">**密碼**</span><span class="sxs-lookup"><span data-stu-id="48433-134">**Password**</span></span>  
 <span data-ttu-id="48433-135">指定 Proxy 帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="48433-135">Specify the password for the proxy account.</span></span>  
  
## <a name="options"></a><span data-ttu-id="48433-136">選項。</span><span class="sxs-lookup"><span data-stu-id="48433-136">Options</span></span>  
 <span data-ttu-id="48433-137">**啟用 C2 稽核追蹤**</span><span class="sxs-lookup"><span data-stu-id="48433-137">**Enable C2 audit tracing**</span></span>  
 <span data-ttu-id="48433-138">稽核嘗試存取陳述式和物件的所有事件，並將其記錄在 \MSSQL\Data 目錄下的檔案中 (對於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的預設執行個體)，或是記錄在 \MSSQL$*instancename*\Data 目錄下的檔案中 (對於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的具名執行個體)。</span><span class="sxs-lookup"><span data-stu-id="48433-138">Audits all attempts to access statements and objects and records them to a file in the \MSSQL\Data directory for default instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or the \MSSQL$*instancename*\Data directory for named instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="48433-139">如需詳細資訊，請參閱 [C2 稽核模式伺服器組態選項](c2-audit-mode-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="48433-139">For more information, see [c2 audit mode Server Configuration Option](c2-audit-mode-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="48433-140">**跨資料庫擁有權鏈結**</span><span class="sxs-lookup"><span data-stu-id="48433-140">**Cross database ownership chaining**</span></span>  
 <span data-ttu-id="48433-141">選取以允許資料庫作為跨資料庫擁有權鏈結的來源或目標。</span><span class="sxs-lookup"><span data-stu-id="48433-141">Select to allow the database to be the source or target of a cross-database ownership chain.</span></span> <span data-ttu-id="48433-142">如需詳細資訊，請參閱 [跨資料庫擁有權鏈結伺服器組態選項](cross-db-ownership-chaining-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="48433-142">For more information, see [cross db ownership chaining Server Configuration Option](cross-db-ownership-chaining-server-configuration-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48433-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48433-143">See Also</span></span>  
 [<span data-ttu-id="48433-144">伺服器組態選項 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="48433-144">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  
