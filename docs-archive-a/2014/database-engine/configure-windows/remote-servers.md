---
title: 遠端伺服器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- server management [SQL Server], remote servers
- remote servers [SQL Server], configuring
- remote servers [SQL Server]
- servers [SQL Server], remote
- remote access option
ms.assetid: abf0fa24-f199-4273-9a1a-e8787ac9bee1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1d42fc2ed6acd4e46e383c0a56afcc8a8b27d3aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596272"
---
# <a name="remote-servers"></a><span data-ttu-id="9a1bb-102">遠端伺服器</span><span class="sxs-lookup"><span data-stu-id="9a1bb-102">Remote Servers</span></span>
  <span data-ttu-id="9a1bb-103">基於回溯相容性，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中支援遠端伺服器。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-103">Remote servers are supported in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for backward compatibility only.</span></span> <span data-ttu-id="9a1bb-104">新應用程式應該改用連結的伺服器。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-104">New applications should use linked servers instead.</span></span> <span data-ttu-id="9a1bb-105">如需詳細資訊，請參閱 [連結的伺服器 &#40;Database Engine&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-105">For more information, see [Linked Servers &#40;Database Engine&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md).</span></span>  
  
 <span data-ttu-id="9a1bb-106">遠端伺服器設定可讓連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的用戶端不須建立另一個連接，就可以在另一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上執行預存程序。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-106">A remote server configuration allows for a client connected to one instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to execute a stored procedure on another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] without establishing a separate connection.</span></span> <span data-ttu-id="9a1bb-107">而且，與用戶端連接的伺服器會接受用戶端的要求，並以用戶端的身分將要求傳送至遠端伺服器。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-107">Instead, the server to which the client is connected accepts the client request and sends the request to the remote server on behalf of the client.</span></span> <span data-ttu-id="9a1bb-108">遠端伺服器會處理要求並將任何結果傳回到原始伺服器。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-108">The remote server processes the request and returns any results to the original server.</span></span> <span data-ttu-id="9a1bb-109">此伺服器接著就會將結果傳遞至用戶端。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-109">This server in turn passes those results to the client.</span></span> <span data-ttu-id="9a1bb-110">設定遠端伺服器組態時，您應該也要考慮如何建立安全性。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-110">When you set up a remote server configuration, you should also consider how to establish security.</span></span>  
  
 <span data-ttu-id="9a1bb-111">如果您想要設定伺服器組態來執行另一個伺服器上的預存程序，但是並沒有現有的遠端伺服器組態時，請使用連結的伺服器來代替遠端伺服器。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-111">If you want to set up a server configuration to execute stored procedures on another server and do not have existing remote server configurations, use linked servers instead of remote servers.</span></span> <span data-ttu-id="9a1bb-112">對於連結的伺服器，您可以執行預存程序與分散式查詢；但是對於遠端伺服器，您只能執行預存程序。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-112">Both stored procedures and distributed queries are allowed against linked servers; however, only stored procedures are allowed against remote servers.</span></span>  
  
## <a name="remote-server-details"></a><span data-ttu-id="9a1bb-113">遠端伺服器詳細資料</span><span class="sxs-lookup"><span data-stu-id="9a1bb-113">Remote Server Details</span></span>  
 <span data-ttu-id="9a1bb-114">遠端伺服器是以配對設定。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-114">Remote servers are set up in pairs.</span></span> <span data-ttu-id="9a1bb-115">若要設定遠端伺服器的配對，請將兩個伺服器都設定成可以相互辨識另一個為遠端伺服器。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-115">To set up a pair of remote servers, configure both servers to recognize each other as remote servers.</span></span>  
  
 <span data-ttu-id="9a1bb-116">大部份的情況下，您不需要設定遠端伺服器的組態選項。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-116">Most of the time, you should not have to set configuration options for remote servers.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9a1bb-117">會在本機和遠端電腦上設定預設值，以允許遠端伺服器的連接。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-117">Set sets the defaults on both the local and remote computers to allow for remote server connections.</span></span>  
  
 <span data-ttu-id="9a1bb-118">若要讓遠端伺服器存取可以進行，在本機與遠端電腦上的 [遠端存取] 組態選項都必須設定為 1</span><span class="sxs-lookup"><span data-stu-id="9a1bb-118">For remote server access to work, the **remote access** configuration option must be set to 1 on both the local and remote computers.</span></span> <span data-ttu-id="9a1bb-119">(這是預設值)。[遠端存取] 會控制遠端伺服器的登入。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-119">(This is the default setting.)  **remote access** controls logins from remote servers.</span></span> <span data-ttu-id="9a1bb-120">您可以使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] **sp_configure** 預存程序或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 重設此組態選項。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-120">You can reset this configuration option by using either the [!INCLUDE[tsql](../../includes/tsql-md.md)] **sp_configure** stored procedure or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="9a1bb-121">若要重設 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的選項，請使用 [伺服器屬性連接] 頁面的 [允許此伺服器的遠端連接]。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-121">To set the option in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **Server Properties Connections** page, use **Allow remote connections to this server**.</span></span> <span data-ttu-id="9a1bb-122">若要存取 [伺服器屬性連接] 頁面，請在物件總管中以滑鼠右鍵按一下伺服器名稱，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-122">To reach the **Server Properties Connections** page, in Object Explorer, right-click the server name, and then click **Properties**.</span></span> <span data-ttu-id="9a1bb-123">在 [伺服器屬性] 頁面上，按一下 [連接] 頁面。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-123">On the **Server Properties** page, click the **Connections** page.</span></span>  
  
 <span data-ttu-id="9a1bb-124">您可以從本機伺服器來停用遠端伺服器組態，以防止其配對遠端伺服器上的使用者存取本機伺服器。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-124">From the local server, you can disable a remote server configuration to prevent access to that local server by users on the remote server with which it is paired.</span></span>  
  
## <a name="security-for-remote-servers"></a><span data-ttu-id="9a1bb-125">遠端伺服器的安全性</span><span class="sxs-lookup"><span data-stu-id="9a1bb-125">Security for Remote Servers</span></span>  
 <span data-ttu-id="9a1bb-126">若要對遠端伺服器啟用遠端程序呼叫 (RPC)，您必須在遠端伺服器上，甚至在執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的本機伺服器上，設定登入對應。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-126">To enable remote procedure calls (RPC) against a remote server, you must set up login mappings on the remote server and possibly on the local server that is running an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9a1bb-127">依預設，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中會停用 RPC。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-127">RPC is disabled by default in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9a1bb-128">此組態以減少其可攻擊介面區來加強伺服器的安全性。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-128">This configuration enhances the security of your server by reducing its attackable surface area.</span></span> <span data-ttu-id="9a1bb-129">在使用 RPC 之前，您必須先啟用此功能。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-129">Before using RPC you must enable this feature.</span></span> <span data-ttu-id="9a1bb-130">如需詳細資訊，請參閱 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-130">For more information see [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql).</span></span>  
  
### <a name="setting-up-the-remote-server"></a><span data-ttu-id="9a1bb-131">設定遠端伺服器</span><span class="sxs-lookup"><span data-stu-id="9a1bb-131">Setting Up the Remote Server</span></span>  
 <span data-ttu-id="9a1bb-132">必須在遠端伺服器上設定遠端登入對應。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-132">Remote login mappings must be set up on the remote server.</span></span> <span data-ttu-id="9a1bb-133">使用這些對應，遠端伺服器便可將來自指定伺服器之 RPC 連接的內送登入對應到本機登入。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-133">Using these mappings, the remote server maps the incoming login for an RPC connection from a specified server to a local login.</span></span> <span data-ttu-id="9a1bb-134">遠端登入對應可使用 **sp_addremotelogin** 預存程序在遠端伺服器上進行設定。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-134">Remote login mappings can be set up by using the **sp_addremotelogin** stored procedure on the remote server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9a1bb-135">**不支援** sp_remoteoption  **的** trusted [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]選項。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-135">The **trusted** option of  **sp_remoteoption** is not supported in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
### <a name="setting-up-the-local-server"></a><span data-ttu-id="9a1bb-136">設定本機伺服器</span><span class="sxs-lookup"><span data-stu-id="9a1bb-136">Setting Up the Local Server</span></span>  
 <span data-ttu-id="9a1bb-137">針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證本機登入，您不需要在本機伺服器上設定登入對應。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-137">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authenticated local logins, you do not have to set up a login mapping on the local server.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9a1bb-138">使用本機登入和密碼來連接至遠端伺服器。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-138">uses the local login and password to connect to the remote server.</span></span> <span data-ttu-id="9a1bb-139">若為 Windows 驗證登入，請在本機伺服器上設定本機登入對應，以定義 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體在建立遠端伺服器之 RPC 連接時所使用的登入與密碼。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-139">For Windows authenticated logins, set up a local login mapping on a local server that defines what login and password are used by an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] when it makes an RPC connection to a remote server.</span></span>  
  
 <span data-ttu-id="9a1bb-140">若為 Windows 驗證所建立的登入，則您必須使用 **sp_addlinkedservlogin** 預存程序，來建立登入名稱與密碼的對應。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-140">For logins created by Windows Authentication, you must create a mapping to a login name and password by using the **sp_addlinkedservlogin** stored procedure.</span></span> <span data-ttu-id="9a1bb-141">這個登入名稱與密碼必須與遠端伺服器所預期的內送登入和密碼相符，如同 **sp_addremotelogin**所建立的一樣。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-141">This login name and password must match the incoming login and password expected by the remote server, as created by **sp_addremotelogin**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9a1bb-142">盡可能使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-142">When possible, use Windows Authentication.</span></span>  
  
### <a name="remote-server-security-example"></a><span data-ttu-id="9a1bb-143">遠端伺服器安全性的範例</span><span class="sxs-lookup"><span data-stu-id="9a1bb-143">Remote Server Security Example</span></span>  
 <span data-ttu-id="9a1bb-144">請考量這些 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝： **serverSend** 和 **serverReceive**。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-144">Consider these [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installations: **serverSend** and **serverReceive**.</span></span> <span data-ttu-id="9a1bb-145">**serverReceive** 的設定是將來自 **serverSend** 的內送登入 (稱為 **Sales_Mary**) 對應到 **serverReceive** 中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證登入 (稱為 **Alice**)。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-145">**serverReceive** is configured to map an incoming login from **serverSend**, called **Sales_Mary**, to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authenticated login in **serverReceive**, called **Alice**.</span></span> <span data-ttu-id="9a1bb-146">另一個來自 **serverSend** 的內送登入 (稱為 **Joe**)，則會對應到 **serverReceive** 中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證登入 (稱為 **Joe**)。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-146">Another incoming login from **serverSend**, called **Joe**, is mapped to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authenticated login in **serverReceive**_,_ called **Joe**.</span></span>  
  
 <span data-ttu-id="9a1bb-147">下列的 Transact-SQL 程式碼範例會將 `serverSend` 設定為對 `serverReceive` 執行 RPC。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-147">The following Transact-SQL code example configures `serverSend` to perform RPCs against `serverReceive`.</span></span>  
  
```  
--Create remote server entry for RPCs   
--from serverSend in serverReceive.  
EXEC sp_addserver 'serverSend';  
GO  
  
--Create remote login mapping for login 'Sales_Mary' from serverSend  
--to Alice.  
EXEC sp_addremotelogin 'serverSend', 'Alice', 'Sales_Mary';  
GO  
--Create remote login mapping for login Joe from serverReceive   
--to same login.  
--Assumes same password for Joe in both servers.  
EXEC sp_addremotelogin 'serverSend', 'Joe', 'Joe';  
GO  
```  
  
 <span data-ttu-id="9a1bb-148">在 `serverSend`上，會針對 Windows 驗證登入 `Sales\Mary` 對應於登入 `Sales_Mary`來建立本機登入對應。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-148">On `serverSend`, a local login mapping is created for a Windows authenticated login `Sales\Mary` to a login `Sales_Mary`.</span></span> <span data-ttu-id="9a1bb-149">`Joe`不需本機對應，因為預設會使用相同的登入名稱與密碼，且 `serverReceive` 會具有 `Joe`的對應。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-149">No local mapping is required for `Joe`, because the default is to use the same login name and password, and `serverReceive` has a mapping for `Joe`.</span></span>  
  
```  
--Create a remote server entry for RPCs from serverReceive.  
EXEC sp_addserver 'serverReceive';  
GO  
--Create a local login mapping for the Windows authenticated login.  
--Sales\Mary to Sales_Mary. The password should match the  
--password for the login Sales_Mary in serverReceive.  
EXEC sp_addlinkedsrvlogin 'serverReceive', false, 'Sales\Mary',  
   'Sales_Mary', '430[fj%dk';  
GO  
```  
  
## <a name="viewing-local-or-remote-server-properties"></a><span data-ttu-id="9a1bb-150">檢視本機或遠端伺服器屬性</span><span class="sxs-lookup"><span data-stu-id="9a1bb-150">Viewing Local or Remote Server Properties</span></span>  
 <span data-ttu-id="9a1bb-151">您可以使用 **xp_msver** 擴充預存程序，來檢閱本機或遠端伺服器的伺服器屬性。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-151">You can use the **xp_msver** extended stored procedure to review server attributes for local or remote servers.</span></span> <span data-ttu-id="9a1bb-152">這些屬性包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的版本號碼、電腦的處理器類型和數目以及作業系統版本。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-152">These attributes include the version number of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the type and number of processors in the computer, and the version of the operating system.</span></span> <span data-ttu-id="9a1bb-153">您可以從本機伺服器來檢視遠端伺服器的資料庫、檔案、登入與工具。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-153">From the local server, you can view databases, files, logins, and tools for a remote server.</span></span> <span data-ttu-id="9a1bb-154">如需詳細資訊，請參閱 [xp_msver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/xp-msver-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="9a1bb-154">For more information, see [xp_msver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/xp-msver-transact-sql).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="9a1bb-155">相關工作</span><span class="sxs-lookup"><span data-stu-id="9a1bb-155">Related Tasks</span></span>  
 [<span data-ttu-id="9a1bb-156">連結的伺服器 &#40;Database Engine&#41;</span><span class="sxs-lookup"><span data-stu-id="9a1bb-156">Linked Servers &#40;Database Engine&#41;</span></span>](../../relational-databases/linked-servers/linked-servers-database-engine.md)  
  
## <a name="related-content"></a><span data-ttu-id="9a1bb-157">相關內容</span><span class="sxs-lookup"><span data-stu-id="9a1bb-157">Related Content</span></span>  
 [<span data-ttu-id="9a1bb-158">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9a1bb-158">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
 [<span data-ttu-id="9a1bb-159">設定 remote access 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="9a1bb-159">Configure the remote access Server Configuration Option</span></span>](configure-the-remote-access-server-configuration-option.md)  
  
 [<span data-ttu-id="9a1bb-160">RECONFIGURE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9a1bb-160">RECONFIGURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
