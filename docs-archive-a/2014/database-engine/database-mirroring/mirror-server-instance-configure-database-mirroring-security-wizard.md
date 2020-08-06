---
title: 鏡像伺服器執行個體 (設定資料庫鏡像安全性精靈) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.mirrorsrvr.f1
ms.assetid: 53223432-615e-440f-904d-925d33ec2144
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 889e62af592d8d23f2aca0d752f1c7f535df883a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709914"
---
# <a name="mirror-server-instance-configure-database-mirroring-security-wizard"></a><span data-ttu-id="898de-102">鏡像伺服器執行個體 (設定資料庫鏡像安全性精靈)</span><span class="sxs-lookup"><span data-stu-id="898de-102">Mirror Server Instance (Configure Database Mirroring Security Wizard)</span></span>
  <span data-ttu-id="898de-103">使用此頁面來指定有關使用鏡像資料庫之伺服器執行個體的資訊。</span><span class="sxs-lookup"><span data-stu-id="898de-103">Use this page to specify information about the server instance with the mirror database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="898de-104">鏡像伺服器執行個體必須執行與主體伺服器執行個體相同的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本 (Standard 或 Enterprise)。</span><span class="sxs-lookup"><span data-stu-id="898de-104">The mirror server instance must be running the same edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], either Standard or Enterprise, as the principal server instance.</span></span> <span data-ttu-id="898de-105">此外，我們強烈建議您在可比較而且可以處理相同工作負載的系統上執行這些伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="898de-105">Also, we strongly recommend that they run on comparable systems that can handle identical workloads.</span></span>  
  
 <span data-ttu-id="898de-106">**若要使用 SQL Server Management Studio 設定資料庫鏡像**</span><span class="sxs-lookup"><span data-stu-id="898de-106">**To configure database mirroring by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="898de-107">使用 Windows 驗證建立資料庫鏡像工作階段 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="898de-107">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="898de-108">啟動設定資料庫鏡像安全性精靈 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="898de-108">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a><span data-ttu-id="898de-109">選項。</span><span class="sxs-lookup"><span data-stu-id="898de-109">Options</span></span>  
 <span data-ttu-id="898de-110">**鏡像伺服器執行個體**</span><span class="sxs-lookup"><span data-stu-id="898de-110">**Mirror server instance**</span></span>  
 <span data-ttu-id="898de-111">如果已經指定鏡像伺服器執行個體 (在 [資料庫屬性]\*\*\*\* 對話方塊的 [鏡像]\*\*\*\* 頁面上)，則會顯示該執行個體；如需詳細資訊，請參閱[資料庫屬性 &#40;鏡像頁面&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)。</span><span class="sxs-lookup"><span data-stu-id="898de-111">If a mirror server instance is already specified (on the **Mirroring** page of the **Database Properties** dialog box), that instance is displayed; for more information, see [Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md).</span></span>  
  
 <span data-ttu-id="898de-112">否則，請輸入鏡像伺服器執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="898de-112">Otherwise, enter the name of the mirror server instance.</span></span> <span data-ttu-id="898de-113">請注意，鏡像伺服器執行個體不可以與主體伺服器執行個體相同。</span><span class="sxs-lookup"><span data-stu-id="898de-113">Note that the mirror server instance cannot be the same as the principal server instance.</span></span>  
  
 <span data-ttu-id="898de-114">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="898de-114">**Connect**</span></span>  
 <span data-ttu-id="898de-115">如果未指定鏡像伺服器執行個體，請按一下 [連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="898de-115">If a mirror server instance has not been specified, click **Connect**.</span></span> <span data-ttu-id="898de-116">這會顯示 **[連接到伺服器]** 對話方塊，您可以在其中指定伺服器執行個體並建立連接。</span><span class="sxs-lookup"><span data-stu-id="898de-116">This displays the **Connect to Server** dialog box in which you can specify the server instance and establish a connection.</span></span>  
  
 <span data-ttu-id="898de-117">如果已指定執行個體，但精靈缺少具備檢查端點是否存在之權限的連接，請按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="898de-117">If the instance has been specified, but the wizard lacks a connection with sufficient permission to check for the existence of the endpoint, click **Connect**.</span></span> <span data-ttu-id="898de-118">隨即顯示已預先選取伺服器執行個體的 [連接到伺服器]\*\*\*\* 對話方塊，且無法變更。</span><span class="sxs-lookup"><span data-stu-id="898de-118">This displays the **Connect to Server** dialog box with the server instance pre-selected and unchangeable.</span></span> <span data-ttu-id="898de-119">指定具備足夠權限的網域帳戶，然後連接到伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="898de-119">Specify a domain account with sufficient permission, and connect to the server instance.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="898de-120">連接到伺服器執行個體時，「設定資料庫鏡像安全性精靈」會使用 **[連接到伺服器]** 對話方塊中提供的認證。</span><span class="sxs-lookup"><span data-stu-id="898de-120">When connecting to the server instance, the Configure Database Mirroring Security Wizard uses the credentials provided in the **Connect to Server** dialog box.</span></span> <span data-ttu-id="898de-121">這些認證與鏡像工作階段的認證不同，後者會使用以服務方式執行伺服器執行個體之啟動帳戶的認證。</span><span class="sxs-lookup"><span data-stu-id="898de-121">These are different from the credentials of a mirroring session, which uses the credentials of the startup account where the server instance is running as a service.</span></span>  
  
 <span data-ttu-id="898de-122">**接聽程式連接埠**</span><span class="sxs-lookup"><span data-stu-id="898de-122">**Listener Port**</span></span>  
 <span data-ttu-id="898de-123">此選項的行為會視此伺服器執行個體的鏡像端點是否存在，如下：</span><span class="sxs-lookup"><span data-stu-id="898de-123">The behavior of this option depends on whether the mirroring endpoint exists for this server instance, as follows:</span></span>  
  
-   <span data-ttu-id="898de-124">如果伺服器執行個體沒有接聽程式通訊埠，在 **[通訊埠]** 文字方塊中就會顯示通訊埠編號 5022。</span><span class="sxs-lookup"><span data-stu-id="898de-124">If a listener port does not exist for the server instance, port number 5022 is displayed in the **Port** text box.</span></span> <span data-ttu-id="898de-125">您可以使用任何可用的通訊埠編號，例如 7022。</span><span class="sxs-lookup"><span data-stu-id="898de-125">You can use any available port number, such as 7022.</span></span>  
  
-   <span data-ttu-id="898de-126">當鏡像端點已經存在時，會顯示來自該端點的通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="898de-126">When the mirroring endpoint already exists, the port number from that endpoint is displayed.</span></span> <span data-ttu-id="898de-127">如果您需要變更通訊埠，請使用 ALTER ENDPOINT 命令。</span><span class="sxs-lookup"><span data-stu-id="898de-127">If you need to change the port, use an ALTER ENDPOINT command.</span></span> <span data-ttu-id="898de-128">如需詳細資訊，請參閱 [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="898de-128">For more information, see [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="898de-129">需要通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="898de-129">A port number is required.</span></span>  
  
 <span data-ttu-id="898de-130">**端點名稱**</span><span class="sxs-lookup"><span data-stu-id="898de-130">**Endpoint name**</span></span>  
 <span data-ttu-id="898de-131">如果這個伺服器執行個體存在有鏡像端點，該端點名稱會顯示於此處。</span><span class="sxs-lookup"><span data-stu-id="898de-131">If the mirroring endpoint exists for this server instance, the endpoint name is displayed here.</span></span> <span data-ttu-id="898de-132">如果端點不存在，您可以指定端點名稱。</span><span class="sxs-lookup"><span data-stu-id="898de-132">If the endpoint does not exist, you can specify the name of the endpoint.</span></span>  
  
 <span data-ttu-id="898de-133">**透過此端點傳送的資料要加密**</span><span class="sxs-lookup"><span data-stu-id="898de-133">**Encrypt data sent through this endpoint**</span></span>  
 <span data-ttu-id="898de-134">依預設，加密為已啟用。</span><span class="sxs-lookup"><span data-stu-id="898de-134">By default, encryption is enabled.</span></span> <span data-ttu-id="898de-135">當已啟用時，加密為必須的 (不只是支援的)，並且所有的加密選項都使用預設值。</span><span class="sxs-lookup"><span data-stu-id="898de-135">When enabled, encryption is required (not merely supported) and uses the default values for all of the encryption options.</span></span> <span data-ttu-id="898de-136">如需詳細資訊，請參閱 [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql)的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="898de-136">For more information, see [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).</span></span>  
  
 <span data-ttu-id="898de-137">若要停用加密，請清除該核取方塊。</span><span class="sxs-lookup"><span data-stu-id="898de-137">To disable encryption, clear the check box.</span></span> <span data-ttu-id="898de-138">若要重新啟用加密，請選取該核取方塊。</span><span class="sxs-lookup"><span data-stu-id="898de-138">To re-enable encryption, select the check box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="898de-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="898de-139">See Also</span></span>  
 <span data-ttu-id="898de-140">[資料庫鏡像端點 &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="898de-140">[The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="898de-141">[資料庫屬性 &#40;鏡像頁面&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span><span class="sxs-lookup"><span data-stu-id="898de-141">[Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span></span>  
 <span data-ttu-id="898de-142">[建立 Windows 驗證的資料庫鏡像端點 &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="898de-142">[Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span></span>  
 <span data-ttu-id="898de-143">[啟動資料庫鏡像監視器 &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="898de-143">[Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="898de-144">資料庫鏡像 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="898de-144">Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)  
  
  
