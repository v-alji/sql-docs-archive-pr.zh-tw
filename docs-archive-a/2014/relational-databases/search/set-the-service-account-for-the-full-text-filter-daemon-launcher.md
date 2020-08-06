---
title: 設定全文檢索篩選背景程式啟動器的服務帳戶 | Microsoft 文件
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], FDHOST Launcher (MSSQLFDLauncher) service account
- FDHOST Launcher (MSSQLFDLauncher) [SQL Server]
ms.assetid: 3ab1d101-7ae0-488f-9b57-468e2517b737
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d69e68f0b00e760c4b11d1f842f22911ac8dd2c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592580"
---
# <a name="set-the-service-account-for-the-full-text-filter-daemon-launcher"></a><span data-ttu-id="df5c7-102">設定全文檢索篩選背景程式啟動器的服務帳戶</span><span class="sxs-lookup"><span data-stu-id="df5c7-102">Set the Service Account for the Full-text Filter Daemon Launcher</span></span>
  <span data-ttu-id="df5c7-103">此主題描述如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員來為 SQL 全文檢索篩選背景程式啟動器服務 (MSSQLFDLauncher) 設定服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="df5c7-103">This topic describes how to set the service account for the SQL Full-text Filter Daemon Launcher service (MSSQLFDLauncher) by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="df5c7-104">ssNoVersion 全文檢索搜尋使用 SQL 全文檢索篩選背景程式啟動器服務，來啟動篩選背景程式主機處理序，以便處理全文檢索搜尋篩選和斷詞。</span><span class="sxs-lookup"><span data-stu-id="df5c7-104">The SQL Full-text Filter Daemon Launcher service is used by full-text search ssNoVersionto start the filter daemon host process, which handles full-text search filtering and word breaking.</span></span> <span data-ttu-id="df5c7-105">若要使用全文檢索搜尋，您必須執行這個服務。</span><span class="sxs-lookup"><span data-stu-id="df5c7-105">This service must be running to use full-text search.</span></span>  
  
 <span data-ttu-id="df5c7-106">SQL 全文檢索篩選背景程式啟動器服務是與特定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體相關聯的執行個體感知服務。</span><span class="sxs-lookup"><span data-stu-id="df5c7-106">The SQL Full-text Filter Daemon Launcher service is an instance-aware service that is associated with a specific instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="df5c7-107">SQL 全文檢索篩選背景程式啟動器服務會將服務帳戶資訊傳播給每個篩選背景程式主機處理序。</span><span class="sxs-lookup"><span data-stu-id="df5c7-107">The SQL Full-text Filter Daemon Launcher service propagates the service account information to each filter daemon host process.</span></span>  
  
  
##  <a name="setting-the-service-account"></a><a name="setting"></a><span data-ttu-id="df5c7-108">設定服務帳戶</span><span class="sxs-lookup"><span data-stu-id="df5c7-108">Setting the Service Account</span></span>  
  
#### <a name="to-set-the-sql-full-text-filter-daemon-launcher-service-account-for-full-text-search"></a><span data-ttu-id="df5c7-109">設定全文檢索搜尋的 SQL 全文檢索篩選背景程式啟動器服務帳戶</span><span class="sxs-lookup"><span data-stu-id="df5c7-109">To set the SQL Full-text Filter Daemon Launcher service account for full-text search</span></span>  
  
1.  <span data-ttu-id="df5c7-110">指向 **[開始]** 功能表上的 **[所有程式]** ，然後依序指向 [ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]] 和 **[組態工具]** ，再按一下 **[SQL Server 組態管理員]** 。</span><span class="sxs-lookup"><span data-stu-id="df5c7-110">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="df5c7-111">在**SQL Server 組態管理員**中，按一下 [ **SQL Server 服務**]，以滑鼠右鍵按一下 **[SQL 全文檢索篩選背景程式啟動器] (*`instance name`*) **]，然後按一下 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="df5c7-111">In **SQL Server Configuration Manager**, click **SQL Server Services**, right-click **SQL Full-text Filter Daemon Launcher (*`instance name`*)**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="df5c7-112">按一下對話方塊的 [登入]\*\*\*\* 索引標籤，然後選取或輸入用以執行 SQL 全文檢索篩選背景程式啟動器服務所建立之每個處理序的帳戶。</span><span class="sxs-lookup"><span data-stu-id="df5c7-112">Click the **Log On** tab of the dialog box, and then select or enter the account under which to run each process created by the SQL Full-text Filter Daemon Launcher service.</span></span>  
  
4.  <span data-ttu-id="df5c7-113">在您關閉對話方塊之後，請按一下 [重新啟動] \*\*\*\* 重新啟動 SQL 全文檢索篩選背景程式啟動器服務。</span><span class="sxs-lookup"><span data-stu-id="df5c7-113">After you close the dialog box, click **Restart** to restart the SQL Full-text Filter Daemon Launcher service.</span></span>  
  
  
##  <a name="if-the-sql-full-text-filter-daemon-launcher-service-does-not-start"></a><a name="error"></a><span data-ttu-id="df5c7-114">如果 SQL 全文檢索篩選背景程式啟動器服務未啟動</span><span class="sxs-lookup"><span data-stu-id="df5c7-114">If the SQL Full-text Filter Daemon Launcher Service Does Not Start</span></span>  
 <span data-ttu-id="df5c7-115">若未啟動 SQL 全文檢索篩選背景程式啟動器服務，則可能是下列其中一個或多個原因所造成：</span><span class="sxs-lookup"><span data-stu-id="df5c7-115">If the SQL Full-text Filter Daemon Launcher service does not start, one or more of the following might be the cause:</span></span>  
  
-   <span data-ttu-id="df5c7-116">與 SQL 全文檢索篩選背景程式啟動器服務帳戶相關聯的密碼已過期。</span><span class="sxs-lookup"><span data-stu-id="df5c7-116">The password associated with the SQL Full-text Filter Daemon Launcher service account has expired.</span></span>  
  
     <span data-ttu-id="df5c7-117">若您針對 SQL 全文檢索篩選背景程式啟動器服務使用本機使用者帳戶，而且密碼已過期，您就必須：</span><span class="sxs-lookup"><span data-stu-id="df5c7-117">If you use a local user account for the SQL Full-text Filter Daemon Launcher service and your password expires, you need to:</span></span>  
  
    1.  <span data-ttu-id="df5c7-118">設定帳戶的新 Windows 密碼。</span><span class="sxs-lookup"><span data-stu-id="df5c7-118">Set a new Windows password for the account.</span></span>  
  
    2.  <span data-ttu-id="df5c7-119">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員中，更新 SQL 全文檢索篩選背景程式啟動器服務以使用新的密碼。</span><span class="sxs-lookup"><span data-stu-id="df5c7-119">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, update the SQL Full-text Filter Daemon Launcher service to use the new password.</span></span>  
  
-   <span data-ttu-id="df5c7-120">服務帳戶的使用者帳戶或密碼不正確。</span><span class="sxs-lookup"><span data-stu-id="df5c7-120">The user account or password of the service account is incorrect.</span></span>  
  
     <span data-ttu-id="df5c7-121">SQL 全文檢索篩選背景程式啟動器服務可能嘗試使用不正確的使用者帳戶和密碼登入。</span><span class="sxs-lookup"><span data-stu-id="df5c7-121">The SQL Full-text Filter Daemon Launcher service might attempt to log in with an incorrect user account and password.</span></span> <span data-ttu-id="df5c7-122">請遵循以上程序，確認此服務的使用者帳戶尚未變更。</span><span class="sxs-lookup"><span data-stu-id="df5c7-122">Follow the procedures above to verify that the user account for the service has not been changed.</span></span>  
  
-   <span data-ttu-id="df5c7-123">用於登入此服務的帳戶沒有權限。</span><span class="sxs-lookup"><span data-stu-id="df5c7-123">The account used to log in to the service does not have privileges.</span></span>  
  
     <span data-ttu-id="df5c7-124">您可能使用了在安裝伺服器執行個體的電腦上沒有登入權限的帳戶。</span><span class="sxs-lookup"><span data-stu-id="df5c7-124">You might be using an account that does not have login privileges on the computer where the server instance is installed.</span></span> <span data-ttu-id="df5c7-125">請確認您用於登入的帳戶確實具有本機電腦的使用者權限。</span><span class="sxs-lookup"><span data-stu-id="df5c7-125">Verify that you are logging in with an account that has User rights and permissions on the local computer.</span></span>  
  
-   <span data-ttu-id="df5c7-126">相同具名管道的另一個執行個體已經在執行中。</span><span class="sxs-lookup"><span data-stu-id="df5c7-126">Another instance of the same named pipe is already running.</span></span>  
  
     <span data-ttu-id="df5c7-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務會當做 SQL 全文檢索篩選背景程式啟動器服務用戶端的具名管道伺服器。</span><span class="sxs-lookup"><span data-stu-id="df5c7-127">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service acts as a named pipe server for the SQL Full-text Filter Daemon Launcher service client.</span></span> <span data-ttu-id="df5c7-128">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 啟動之前已經由另一個處理序建立此具名管道，則會有錯誤記錄到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔和 Windows 事件記錄檔中，而且將無法使用全文檢索搜尋。</span><span class="sxs-lookup"><span data-stu-id="df5c7-128">If the named pipe was already created by another process before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] starts, an error will be logged in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and the Windows Event Log, and full-text search will not be available.</span></span>  <span data-ttu-id="df5c7-129">請判斷哪一個處理序或應用程式正在嘗試使用相同的具名管道，並停止應用程式。</span><span class="sxs-lookup"><span data-stu-id="df5c7-129">Determine what process or application is attempting to use the same named pipe and stop the application.</span></span>  
  
-   <span data-ttu-id="df5c7-130">SQL 全文檢索篩選背景程式啟動器服務的設定不正確。</span><span class="sxs-lookup"><span data-stu-id="df5c7-130">The SQL Full-text Filter Daemon Launcher service is not configured correctly.</span></span>  
  
     <span data-ttu-id="df5c7-131">本機電腦上可能未正確設定此服務。</span><span class="sxs-lookup"><span data-stu-id="df5c7-131">The service may not be configured correctly on the local computer.</span></span>  
  
     <span data-ttu-id="df5c7-132">如果本機電腦上已停用具名管道功能，或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 已設定成使用非預設具名管道的具名管道，則 SQL 全文檢索篩選背景程式啟動器服務可以無法啟動。</span><span class="sxs-lookup"><span data-stu-id="df5c7-132">If named pipes functionality has been disabled on the local computer, or if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has been configured to use a named pipe other than the default named pipe, the SQL Full-text Filter Daemon Launcher service might not start.</span></span>  
  
-   <span data-ttu-id="df5c7-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務群組沒有啟動 SQL 全文檢索篩選背景程式啟動器服務的權限。</span><span class="sxs-lookup"><span data-stu-id="df5c7-133">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service group does not have permission to start SQL Full-text Filter Daemon Launcher service.</span></span>  
  
     <span data-ttu-id="df5c7-134">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]安裝期間，會將管理、查詢及啟動 SQL 全文檢索篩選背景程式啟動器服務的預設權限授與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務群組。</span><span class="sxs-lookup"><span data-stu-id="df5c7-134">During the installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service group is granted default permission to manage, query, and start the SQL Full-text Filter Daemon Launcher service.</span></span> <span data-ttu-id="df5c7-135">如果在安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之後已經移除 SQL 全文檢索篩選背景程式啟動器服務帳戶的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務群組權限，SQL 全文檢索篩選背景程式啟動器服務將不會啟動，而且全文檢索搜尋將會停用。</span><span class="sxs-lookup"><span data-stu-id="df5c7-135">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service group permissions to the SQL Full-text Filter Daemon Launcher service account have been removed after [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation, the SQL Full-text Filter Daemon Launcher service will not start, and full-text search will be disabled.</span></span> <span data-ttu-id="df5c7-136">請確認 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務群組具有 SQL 全文檢索篩選背景程式啟動器服務帳戶的權限。</span><span class="sxs-lookup"><span data-stu-id="df5c7-136">Make certain the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service group has permissions to the SQL Full-text Filter Daemon Launcher service account.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="df5c7-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df5c7-137">See Also</span></span>  
 [<span data-ttu-id="df5c7-138">管理服務的如何主題 &#40;SQL Server 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="df5c7-138">Managing Services How-to Topics &#40;SQL Server Configuration Manager&#41;</span></span>](../../database-engine/managing-services-how-to-topics-sql-server-configuration-manager.md)  
 [<span data-ttu-id="df5c7-139">升級全文檢索搜尋</span><span class="sxs-lookup"><span data-stu-id="df5c7-139">Upgrade Full-Text Search</span></span>](upgrade-full-text-search.md)  
  
  
