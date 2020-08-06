---
title: MSSQLSERVER_21879 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21879 (Database Engine error)
ms.assetid: fcfab735-05ca-423a-89f1-fdee7e2ed8c0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 08c5d4f45faf94d555ed7acedd90cc55ec4791ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702937"
---
# <a name="mssqlserver_21879"></a><span data-ttu-id="f998f-102">MSSQLSERVER_21879</span><span class="sxs-lookup"><span data-stu-id="f998f-102">MSSQLSERVER_21879</span></span>
    
## <a name="details"></a><span data-ttu-id="f998f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f998f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f998f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f998f-104">Product Name</span></span>|<span data-ttu-id="f998f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f998f-105">SQL Server</span></span>|  
|<span data-ttu-id="f998f-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f998f-106">Event ID</span></span>|<span data-ttu-id="f998f-107">21879</span><span class="sxs-lookup"><span data-stu-id="f998f-107">21879</span></span>|  
|<span data-ttu-id="f998f-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="f998f-108">Event Source</span></span>|<span data-ttu-id="f998f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f998f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f998f-110">元件</span><span class="sxs-lookup"><span data-stu-id="f998f-110">Component</span></span>|<span data-ttu-id="f998f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f998f-111">SQLEngine</span></span>|  
|<span data-ttu-id="f998f-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f998f-112">Symbolic Name</span></span>|<span data-ttu-id="f998f-113">SQLErrorNum21879</span><span class="sxs-lookup"><span data-stu-id="f998f-113">SQLErrorNum21879</span></span>|  
|<span data-ttu-id="f998f-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f998f-114">Message Text</span></span>|<span data-ttu-id="f998f-115">無法查詢原始發行者 '%s' 和發行者資料庫 '%s' 的重新導向伺服器 '%s' 以判斷遠端伺服器之名稱; 錯誤 %d，錯誤訊息 '%s'。</span><span class="sxs-lookup"><span data-stu-id="f998f-115">Unable to query the redirected server '%s' for original publisher '%s' and publisher database '%s' to determine the name of the remote server; Error %d, Error message '%s'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f998f-116">說明</span><span class="sxs-lookup"><span data-stu-id="f998f-116">Explanation</span></span>  
 <span data-ttu-id="f998f-117">`sp_validate_redirected_publisher` 會使用暫時連結的伺服器，而建立此伺服器的目的是要連接到重新導向的發行者，以便探索遠端伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="f998f-117">`sp_validate_redirected_publisher` uses a temporary linked server that it creates to connect to the redirected publisher in order to discover the name of the remote server.</span></span> <span data-ttu-id="f998f-118">當連結的伺服器查詢失敗時，就會傳回錯誤 21879。</span><span class="sxs-lookup"><span data-stu-id="f998f-118">Error 21879 is returned when the linked server query fails.</span></span> <span data-ttu-id="f998f-119">要求遠端伺服器名稱的呼叫通常是在第一次使用暫時連結的伺服器時進行，因此如果發生連接問題，這些問題可能會先與此呼叫一起顯示。</span><span class="sxs-lookup"><span data-stu-id="f998f-119">The call to request the remote server name is typically the first use of the temporary linked server, so if there are connectivity problems they are likely to appear first with this call.</span></span> <span data-ttu-id="f998f-120">這個遠端呼叫只會在遠端伺服器上執行選取的 `@@servername`。</span><span class="sxs-lookup"><span data-stu-id="f998f-120">This remote call simply executes select `@@servername` at the remote server.</span></span>  
  
 <span data-ttu-id="f998f-121">用來查詢重新導向發行者的連結伺服器會使用針對原始發行者呼叫 `sp_adddistpublisher` 時所提供的安全性模式、登入和密碼。</span><span class="sxs-lookup"><span data-stu-id="f998f-121">The linked server used to query the redirected publisher uses the security mode, login, and password supplied when `sp_adddistpublisher` was called for the original publisher.</span></span>  
  
-   <span data-ttu-id="f998f-122">如果使用了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證 (安全性模式 0)，則指定的登入和密碼就會用來連接到遠端伺服器。</span><span class="sxs-lookup"><span data-stu-id="f998f-122">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authentication was used (security mode 0) then the login and password specified are used to connect to the remote server.</span></span>  
  
-   <span data-ttu-id="f998f-123">如果使用了 Windows 驗證 (安全性模式 1)，就會使用信任的連接進行連接。</span><span class="sxs-lookup"><span data-stu-id="f998f-123">If Windows authentication was used (security mode 1) a trusted connection is used for the connection.</span></span>  
  
    -   <span data-ttu-id="f998f-124">如果使用者明確呼叫了 `sp_validate_redirected_publisher`，就會使用使用者用以執行的 Windows 登入進行連接。</span><span class="sxs-lookup"><span data-stu-id="f998f-124">If `sp_validate_redirected_publisher` is called explicitly by a user, the Windows login that the user is running under is used for the connection.</span></span>  
  
    -   <span data-ttu-id="f998f-125">如果複寫代理程式從 `sp_validate_redirected_` 呼叫 `sp_get_redirected_publisher`publisher，就會使用與代理程式相關聯的 Windows 登入。</span><span class="sxs-lookup"><span data-stu-id="f998f-125">If `sp_validate_redirected_`publisher is called by a replication agent from `sp_get_redirected_publisher`, the Windows login associated with the agent is used.</span></span>  
  
 <span data-ttu-id="f998f-126">錯誤 21879 可能表示呼叫 `sp_validate_redirected_publisher` 時使用了重新導向目標發行者未知的登入。</span><span class="sxs-lookup"><span data-stu-id="f998f-126">Error 21879 can indicate that `sp_validate_redirected_publisher` was called using a login that is not known at the redirected target publisher.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f998f-127">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f998f-127">User Action</span></span>  
 <span data-ttu-id="f998f-128">請確定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證登入或 Windows 驗證登入在所有可用性群組複本上有效，而且具有足夠的授權，可存取發行者資料庫中的訂閱中繼資料資料表 (syssubscriptions 和 sysmergesubscriptions)。</span><span class="sxs-lookup"><span data-stu-id="f998f-128">Make certain that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authentication login or the Windows authentication login is valid at all of the availability group replicas and has sufficient authorization to access the subscription metadata tables (syssubscriptions and sysmergesubscriptions) in the publisher database.</span></span>  
  
 <span data-ttu-id="f998f-129">在散發者以外之節點上執行的複寫代理程式 (例如在訂閱者端執行的合併代理程式) 所起始的 `sp_get_redirected_publisher` 呼叫傳回錯誤 21879 時，就會存在一些特殊考量。</span><span class="sxs-lookup"><span data-stu-id="f998f-129">There are special considerations when error 21879 is returned from a call to `sp_get_redirected_publisher` that is initiated by a replication agent running on a node other that the distributor; such as a merge agent running at a subscriber.</span></span> <span data-ttu-id="f998f-130">如果 Windows 驗證用於重新導向發行者的連接，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 就必須設定為 Kerberos 驗證，才能成功建立連接。</span><span class="sxs-lookup"><span data-stu-id="f998f-130">If Windows authentication is used for the connection to the redirected publisher, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be configured for Kerberos authentication for the connection to be successfully established.</span></span> <span data-ttu-id="f998f-131">當您使用 Windows 驗證而且 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 並未設定為 Kerberos 驗證時，在訂閱者端執行的合併代理程式就會收到表示 'NT AUTHORITY\ANONYMOUS LOGON' 登入失敗的錯誤 18456。</span><span class="sxs-lookup"><span data-stu-id="f998f-131">When Windows authentication is used and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not configured for Kerberos authentication, error 18456 indicating that the 'NT AUTHORITY\ANONYMOUS LOGON' login failed, is received by a merge agent running at a subscriber.</span></span> <span data-ttu-id="f998f-132">可解決此問題的方式有三種：</span><span class="sxs-lookup"><span data-stu-id="f998f-132">There are three possible ways to address this issue:</span></span>  
  
-   <span data-ttu-id="f998f-133">將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 設定為 Kerberos 驗證。</span><span class="sxs-lookup"><span data-stu-id="f998f-133">Configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for Kerberos authentication.</span></span> <span data-ttu-id="f998f-134">請參閱 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書中的 **Kerberos 驗證和 SQL Server**。</span><span class="sxs-lookup"><span data-stu-id="f998f-134">See **Kerberos Authentication and SQL Server** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
-   <span data-ttu-id="f998f-135">使用 `sp_changedistpublisher` 來變更與 msdb.dbo.msdistpublishers 中原始發行者相關聯的安全性模式，以及指定用於連接的登入和密碼。</span><span class="sxs-lookup"><span data-stu-id="f998f-135">Use `sp_changedistpublisher` to change the security mode associated with the original publisher in MSdistpublishers, as well as to specify a login and password to use for the connection.</span></span>  
  
-   <span data-ttu-id="f998f-136">在「合併代理程式」命令列上指定命令列參數*BypassPublisherValidation* ，以在「散發者」端呼叫時略過驗證 `sp_get_redirected_publisher` 。</span><span class="sxs-lookup"><span data-stu-id="f998f-136">Specify the command line parameter *BypassPublisherValidation* on the merge agent command line to bypass validation when `sp_get_redirected_publisher` is called at the distributor.</span></span>  
  
  
