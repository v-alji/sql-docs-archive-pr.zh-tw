---
title: 註冊伺服器
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqlserverregisteredserver.dhelp
helpviewer_keywords:
- connections [SQL Server], registered servers
- registering servers
- servers [SQL Server], registering
- server management [SQL Server], registering servers
- server registration [SQL Server]
ms.assetid: c2a2513e-fa09-419c-99e7-a12d57c5a0db
author: markingmyname
ms.author: maghan
ms.openlocfilehash: f4b23ba127c6b000b0abbe832c4c072ada78c5e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594314"
---
# <a name="register-servers"></a><span data-ttu-id="b1071-102">註冊伺服器</span><span class="sxs-lookup"><span data-stu-id="b1071-102">Register Servers</span></span>
  <span data-ttu-id="b1071-103">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中註冊伺服器可讓您儲存伺服器連接資訊，以供未來連接使用。在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中註冊伺服器的方法有三種。</span><span class="sxs-lookup"><span data-stu-id="b1071-103">Registering a server in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] allows you to store the server connection information for future connections.There are three ways to register a server in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
1.  <span data-ttu-id="b1071-104">在安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之後，第一次啟動時就會自動註冊 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 的本機執行個體。</span><span class="sxs-lookup"><span data-stu-id="b1071-104">Local instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are automatically registered during the first launch of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] after its installation.</span></span>  
  
2.  <span data-ttu-id="b1071-105">您也可以隨時初始化自動註冊處理序，以還原本機伺服器執行個體的註冊。</span><span class="sxs-lookup"><span data-stu-id="b1071-105">You can also initiate the automatic registration process at any time, to restore the registration of local server instances.</span></span>  
  
3.  <span data-ttu-id="b1071-106">最後，您還可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的 [已註冊的伺服器] 工具來註冊伺服器。</span><span class="sxs-lookup"><span data-stu-id="b1071-106">Lastly, you can register a server using the Registered Servers tool in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="benefits-of-registered-servers"></a><span data-ttu-id="b1071-107">已註冊伺服器的優點</span><span class="sxs-lookup"><span data-stu-id="b1071-107">Benefits of Registered Servers</span></span>  
 <span data-ttu-id="b1071-108">您可以利用已註冊的伺服器來執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="b1071-108">With Registered Servers you can:</span></span>  
  
-   <span data-ttu-id="b1071-109">註冊伺服器來保留連接資訊。</span><span class="sxs-lookup"><span data-stu-id="b1071-109">Register servers to preserve the connection information.</span></span>  
  
-   <span data-ttu-id="b1071-110">判斷已註冊的伺服器是否在執行中。</span><span class="sxs-lookup"><span data-stu-id="b1071-110">Determine if a registered server is running.</span></span>  
  
-   <span data-ttu-id="b1071-111">輕易將物件總管和查詢編輯器連接到已註冊的伺服器。</span><span class="sxs-lookup"><span data-stu-id="b1071-111">Easily connect Object Explorer and Query Editor to a registered server.</span></span>  
  
-   <span data-ttu-id="b1071-112">編輯或刪除已註冊的伺服器之登錄資訊。</span><span class="sxs-lookup"><span data-stu-id="b1071-112">Edit or delete the registration information for a registered server.</span></span>  
  
-   <span data-ttu-id="b1071-113">建立伺服器群組。</span><span class="sxs-lookup"><span data-stu-id="b1071-113">Create groups of servers.</span></span>  
  
-   <span data-ttu-id="b1071-114">在有別於 [伺服器名稱] 清單的 [已註冊的伺服器名稱] 方塊中提供一個值，以提供已註冊的伺服器之使用者易讀的名稱。</span><span class="sxs-lookup"><span data-stu-id="b1071-114">Provide user-friendly names for registered servers by providing a value in the **Registered server name** box that is different from the **Server name** list.</span></span>  
  
-   <span data-ttu-id="b1071-115">提供已註冊的伺服器的詳細說明。</span><span class="sxs-lookup"><span data-stu-id="b1071-115">Provide detailed descriptions for registered servers.</span></span>  
  
-   <span data-ttu-id="b1071-116">提供已註冊的伺服器群組的詳細說明。</span><span class="sxs-lookup"><span data-stu-id="b1071-116">Provide detailed descriptions of registered server groups.</span></span>  
  
-   <span data-ttu-id="b1071-117">匯出已註冊的伺服器群組。</span><span class="sxs-lookup"><span data-stu-id="b1071-117">Export registered server groups.</span></span>  
  
-   <span data-ttu-id="b1071-118">匯入已註冊的伺服器群組。</span><span class="sxs-lookup"><span data-stu-id="b1071-118">Import registered server groups.</span></span>  
  
-   <span data-ttu-id="b1071-119">檢視線上或離線 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b1071-119">View the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log files for online or offline instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="b1071-120">相關工作</span><span class="sxs-lookup"><span data-stu-id="b1071-120">Related Tasks</span></span>  
 <span data-ttu-id="b1071-121">若要開始使用已註冊的伺服器，請使用下列主題：</span><span class="sxs-lookup"><span data-stu-id="b1071-121">Use the following topics to get started with registered servers:</span></span>  
  
|<span data-ttu-id="b1071-122">**說明**</span><span class="sxs-lookup"><span data-stu-id="b1071-122">**Description**</span></span>|<span data-ttu-id="b1071-123">**主題**</span><span class="sxs-lookup"><span data-stu-id="b1071-123">**Topic**</span></span>|  
|---------------------|---------------|  
|<span data-ttu-id="b1071-124">註冊本機伺服器執行個體</span><span class="sxs-lookup"><span data-stu-id="b1071-124">Register local server instances</span></span>|[<span data-ttu-id="b1071-125">註冊連接的伺服器 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b1071-125">Register a Connected Server &#40;SQL Server Management Studio&#41;</span></span>](register-a-connected-server-sql-server-management-studio.md)|  
|<span data-ttu-id="b1071-126">註冊伺服器</span><span class="sxs-lookup"><span data-stu-id="b1071-126">Register a server</span></span>|[<span data-ttu-id="b1071-127">建立新的已註冊伺服器 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b1071-127">Create a New Registered Server &#40;SQL Server Management Studio&#41;</span></span>](create-a-new-registered-server-sql-server-management-studio.md)|  
|<span data-ttu-id="b1071-128">檢視已註冊的伺服器</span><span class="sxs-lookup"><span data-stu-id="b1071-128">View registered servers</span></span>|[<span data-ttu-id="b1071-129">在 SQL Server Management Studio 中檢視已註冊的伺服器</span><span class="sxs-lookup"><span data-stu-id="b1071-129">View Registered Servers in SQL Server Management Studio</span></span>](view-registered-servers-in-sql-server-management-studio.md)|  
|<span data-ttu-id="b1071-130">移除已註冊的伺服器</span><span class="sxs-lookup"><span data-stu-id="b1071-130">Remove a registered server</span></span>|[<span data-ttu-id="b1071-131">移除已註冊的伺服器 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b1071-131">Remove a Registered Server &#40;SQL Server Management Studio&#41;</span></span>](remove-a-registered-server-sql-server-management-studio.md)|  
|<span data-ttu-id="b1071-132">變更伺服器的註冊</span><span class="sxs-lookup"><span data-stu-id="b1071-132">Change a server's registration</span></span>|[<span data-ttu-id="b1071-133">變更伺服器的註冊 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b1071-133">Change a Server's Registration &#40;SQL Server Management Studio&#41;</span></span>](change-a-server-s-registration-sql-server-management-studio.md)|  
|<span data-ttu-id="b1071-134">連接到已註冊的伺服器</span><span class="sxs-lookup"><span data-stu-id="b1071-134">Connect to a registered server</span></span>|[<span data-ttu-id="b1071-135">連接至已註冊的伺服器 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b1071-135">Connect to a Registered Server &#40;SQL Server Management Studio&#41;</span></span>](connect-to-a-registered-server-sql-server-management-studio.md)|  
|<span data-ttu-id="b1071-136">中斷與已註冊伺服器的連接</span><span class="sxs-lookup"><span data-stu-id="b1071-136">Disconnect from a registered server</span></span>|[<span data-ttu-id="b1071-137">中斷與註冊伺服器的連接 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b1071-137">Disconnect from a Registered Server &#40;SQL Server Management Studio&#41;</span></span>](disconnect-from-a-registered-server-sql-server-management-studio.md)|  
|<span data-ttu-id="b1071-138">移動已註冊的伺服器或伺服器群組</span><span class="sxs-lookup"><span data-stu-id="b1071-138">Move a registered server or server group</span></span>|[<span data-ttu-id="b1071-139">移動已註冊的伺服器或已註冊的伺服器群組 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b1071-139">Move a Registered Server or Registered Server Group &#40;SQL Server Management Studio&#41;</span></span>](move-a-registered-server-or-registered-server-group.md)|  
|<span data-ttu-id="b1071-140">變更已註冊伺服器或伺服器群組的名稱</span><span class="sxs-lookup"><span data-stu-id="b1071-140">Change the name of a registered server or server group</span></span>|[<span data-ttu-id="b1071-141">變更已註冊的伺服器或已註冊的伺服器群組名稱 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b1071-141">Change the Name of a Registered Server or Registered Server Group &#40;SQL Server Management Studio&#41;</span></span>](change-the-name-of-registered-server-or-registered-server-group.md)|  
|<span data-ttu-id="b1071-142">建立或編輯伺服器群組</span><span class="sxs-lookup"><span data-stu-id="b1071-142">Create or edit a server group</span></span>|[<span data-ttu-id="b1071-143">建立或編輯伺服器群組 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b1071-143">Create or Edit a Server Group &#40;SQL Server Management Studio&#41;</span></span>](create-or-edit-a-server-group-sql-server-management-studio.md)|  
|<span data-ttu-id="b1071-144">移除伺服器群組</span><span class="sxs-lookup"><span data-stu-id="b1071-144">Remove a server group</span></span>|[<span data-ttu-id="b1071-145">移除伺服器群組 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b1071-145">Remove a Server Group &#40;SQL Server Management Studio&#41;</span></span>](remove-a-server-group-sql-server-management-studio.md)|  
|<span data-ttu-id="b1071-146">匯出已註冊的伺服器資訊</span><span class="sxs-lookup"><span data-stu-id="b1071-146">Export registered server information</span></span>|[<span data-ttu-id="b1071-147">匯出已註冊的伺服器資訊 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b1071-147">Export Registered Server Information &#40;SQL Server Management Studio&#41;</span></span>](export-registered-server-information-sql-server-management-studio.md)|  
|<span data-ttu-id="b1071-148">匯入已註冊的伺服器資訊</span><span class="sxs-lookup"><span data-stu-id="b1071-148">Import registered server information</span></span>|[<span data-ttu-id="b1071-149">匯入已註冊的伺服器資訊 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b1071-149">Import Registered Server Information &#40;SQL Server Management Studio&#41;</span></span>](import-registered-server-information-sql-server-management-studio.md)|  
|<span data-ttu-id="b1071-150">建立中央管理伺服器和伺服器群組</span><span class="sxs-lookup"><span data-stu-id="b1071-150">Create a Central Management Server and Server Group</span></span>|[<span data-ttu-id="b1071-151">建立中央管理伺服器與伺服器群組 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b1071-151">Create a Central Management Server and Server Group &#40;SQL Server Management Studio&#41;</span></span>](create-a-central-management-server-and-server-group.md)|  
|<span data-ttu-id="b1071-152">同時對多部伺服器執行陳述式</span><span class="sxs-lookup"><span data-stu-id="b1071-152">Execute statements against multiple servers simultaneously</span></span>|[<span data-ttu-id="b1071-153">同時針對多部伺服器執行陳述式 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b1071-153">Execute Statements Against Multiple Servers Simultaneously &#40;SQL Server Management Studio&#41;</span></span>](execute-statements-against-multiple-servers-simultaneously.md)|  
  
## <a name="see-also"></a><span data-ttu-id="b1071-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1071-154">See Also</span></span>  
 [<span data-ttu-id="b1071-155">遠端伺服器</span><span class="sxs-lookup"><span data-stu-id="b1071-155">Remote Servers</span></span>](../../database-engine/configure-windows/remote-servers.md)  
  
  
