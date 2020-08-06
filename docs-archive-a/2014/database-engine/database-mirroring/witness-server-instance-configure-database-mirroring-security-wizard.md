---
title: 見證伺服器執行個體 (設定資料庫鏡像安全性精靈) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.witnsrvr.f1
ms.assetid: b5763663-984a-473b-93a3-6cd3322ad41c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fcea7d39e1bc2c6161b5c6e1edd4852d9fdeb073
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593568"
---
# <a name="witness-server-instance-configure-database-mirroring-security-wizard"></a><span data-ttu-id="41e8d-102">見證伺服器執行個體 (設定資料庫鏡像安全性精靈)</span><span class="sxs-lookup"><span data-stu-id="41e8d-102">Witness Server Instance (Configure Database Mirroring Security Wizard)</span></span>
  <span data-ttu-id="41e8d-103">使用此頁面來指定有關做為工作階段見證之伺服器執行個體的資訊。</span><span class="sxs-lookup"><span data-stu-id="41e8d-103">Use this page to specify information about the server instance that is to serve as the witness for the session.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="41e8d-104">並非所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本都可使用見證伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="41e8d-104">A witness server instance is not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="41e8d-105">如需版本支援的功能清單 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[SQL Server 2014 版本支援的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="41e8d-105">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="41e8d-106">**若要使用 SQL Server Management Studio 設定資料庫鏡像**</span><span class="sxs-lookup"><span data-stu-id="41e8d-106">**To configure database mirroring by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="41e8d-107">使用 Windows 驗證建立資料庫鏡像工作階段 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="41e8d-107">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="41e8d-108">啟動設定資料庫鏡像安全性精靈 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="41e8d-108">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a><span data-ttu-id="41e8d-109">選項。</span><span class="sxs-lookup"><span data-stu-id="41e8d-109">Options</span></span>  
 <span data-ttu-id="41e8d-110">**見證伺服器執行個體**</span><span class="sxs-lookup"><span data-stu-id="41e8d-110">**Witness server instance**</span></span>  
 <span data-ttu-id="41e8d-111">如果已經指定見證伺服器執行個體 (在 [資料庫屬性]\*\*\*\* 對話方塊的 [鏡像]\*\*\*\* 頁面上)，就會顯示該執行個體 (如需詳細資訊，請參閱[資料庫屬性 &#40;鏡像頁面&#41;](../../relational-databases/databases/database-properties-mirroring-page.md))。</span><span class="sxs-lookup"><span data-stu-id="41e8d-111">If a witness server instance is already specified (on the **Mirroring** page of the **Database Properties** dialog box), that instance is displayed (for more information, see [Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)).</span></span>  
  
 <span data-ttu-id="41e8d-112">否則，此清單方塊會顯示目前伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="41e8d-112">Otherwise, this list box displays the name of the current server.</span></span> <span data-ttu-id="41e8d-113">請注意，見證伺服器執行個體不可以與主體或鏡像伺服器執行個體相同。</span><span class="sxs-lookup"><span data-stu-id="41e8d-113">Be aware that the witness server instance cannot be the same as the principal or mirror server instances.</span></span>  
  
 <span data-ttu-id="41e8d-114">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="41e8d-114">**Connect**</span></span>  
 <span data-ttu-id="41e8d-115">如果未指定見證伺服器執行個體，請按一下 [連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="41e8d-115">If a witness server instance has not been specified, click **Connect**.</span></span> <span data-ttu-id="41e8d-116">這會顯示 **[連接到伺服器]** 對話方塊，您可以在其中指定伺服器執行個體並建立連接。</span><span class="sxs-lookup"><span data-stu-id="41e8d-116">This displays the **Connect to Server** dialog box in which you can specify the server instance and establish a connection.</span></span>  
  
 <span data-ttu-id="41e8d-117">如果已指定執行個體，但精靈缺少具備檢查端點是否存在之權限的連接，請按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="41e8d-117">If the instance has been specified, but the wizard lacks a connection with sufficient permission to check for the existence of the endpoint, click **Connect**.</span></span> <span data-ttu-id="41e8d-118">隨即顯示已預先選取伺服器執行個體的 [連接到伺服器]\*\*\*\* 對話方塊，且無法變更。</span><span class="sxs-lookup"><span data-stu-id="41e8d-118">This displays the **Connect to Server** dialog box with the server instance pre-selected and unchangeable.</span></span> <span data-ttu-id="41e8d-119">指定具備足夠權限的網域帳戶，然後連接到伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="41e8d-119">Specify a domain account with sufficient permission, and connect to the server instance.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="41e8d-120">連接到伺服器執行個體時，「設定資料庫鏡像安全性精靈」會使用 **[連接到伺服器]** 對話方塊中提供的認證。</span><span class="sxs-lookup"><span data-stu-id="41e8d-120">When connecting to the server instance, the Configure Database Mirroring Security Wizard uses the credentials provided in the **Connect to Server** dialog box.</span></span> <span data-ttu-id="41e8d-121">這些認證與鏡像工作階段的認證不同，後者會使用以服務方式執行伺服器執行個體之啟動帳戶的認證。</span><span class="sxs-lookup"><span data-stu-id="41e8d-121">These are different from the credentials of a mirroring session, which uses the credentials of the startup account where the server instance is running as a service.</span></span>  
  
 <span data-ttu-id="41e8d-122">**接聽程式連接埠**</span><span class="sxs-lookup"><span data-stu-id="41e8d-122">**Listener Port**</span></span>  
 <span data-ttu-id="41e8d-123">此選項的行為會視此伺服器執行個體的鏡像端點是否存在，如下：</span><span class="sxs-lookup"><span data-stu-id="41e8d-123">The behavior of this option depends on whether the mirroring endpoint exists for this server instance, as follows:</span></span>  
  
-   <span data-ttu-id="41e8d-124">如果伺服器執行個體沒有接聽程式通訊埠，在 [通訊埠]\*\*\*\* 文字方塊中就會顯示通訊埠編號 5022。</span><span class="sxs-lookup"><span data-stu-id="41e8d-124">If the listener port does not exist for the server instance, port number 5022 is displayed in the **Port** text box.</span></span> <span data-ttu-id="41e8d-125">您可以輸入任何可用的通訊埠編號，例如 7022。</span><span class="sxs-lookup"><span data-stu-id="41e8d-125">You can enter any available port number, such as, 7022.</span></span>  
  
-   <span data-ttu-id="41e8d-126">當鏡像端點已經存在時，會顯示來自端點的通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="41e8d-126">When the mirroring endpoint already exists, the port number from the endpoint is displayed.</span></span> <span data-ttu-id="41e8d-127">如果您需要變更該通訊埠，請使用 ALTER ENDPOINT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="41e8d-127">If you need to change that port, use an ALTER ENDPOINT statement.</span></span> <span data-ttu-id="41e8d-128">如需詳細資訊，請參閱 [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="41e8d-128">For more information, see [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="41e8d-129">需要通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="41e8d-129">A port number is required.</span></span>  
  
 <span data-ttu-id="41e8d-130">**端點名稱**</span><span class="sxs-lookup"><span data-stu-id="41e8d-130">**Endpoint name**</span></span>  
 <span data-ttu-id="41e8d-131">如果這個伺服器執行個體存在有鏡像端點，該端點名稱會顯示於此處。</span><span class="sxs-lookup"><span data-stu-id="41e8d-131">If the mirroring endpoint exists for this server instance, the endpoint name is displayed here.</span></span> <span data-ttu-id="41e8d-132">如果端點不存在，您可以指定端點名稱。</span><span class="sxs-lookup"><span data-stu-id="41e8d-132">If the endpoint does not exist, you can specify the name of the endpoint.</span></span>  
  
 <span data-ttu-id="41e8d-133">**透過此端點傳送的資料要加密**</span><span class="sxs-lookup"><span data-stu-id="41e8d-133">**Encrypt data sent through this endpoint**</span></span>  
 <span data-ttu-id="41e8d-134">依預設，加密為已啟用。</span><span class="sxs-lookup"><span data-stu-id="41e8d-134">By default, encryption is enabled.</span></span> <span data-ttu-id="41e8d-135">當已啟用時，加密為必須的 (不只是支援的)，並且所有的加密選項都使用預設值。</span><span class="sxs-lookup"><span data-stu-id="41e8d-135">When enabled, encryption is required (not merely supported) and uses the default values for all of the encryption options.</span></span> <span data-ttu-id="41e8d-136">如需詳細資訊，請參閱 [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql)的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="41e8d-136">For more information, see [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).</span></span>  
  
 <span data-ttu-id="41e8d-137">若要停用加密，請清除該核取方塊。</span><span class="sxs-lookup"><span data-stu-id="41e8d-137">To disable encryption, clear the check box.</span></span> <span data-ttu-id="41e8d-138">若要重新啟用加密，請選取該核取方塊。</span><span class="sxs-lookup"><span data-stu-id="41e8d-138">To re-enable encryption, select the check box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41e8d-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41e8d-139">See Also</span></span>  
 <span data-ttu-id="41e8d-140">[資料庫鏡像端點 &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="41e8d-140">[The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="41e8d-141">[資料庫屬性 &#40;鏡像頁面&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span><span class="sxs-lookup"><span data-stu-id="41e8d-141">[Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span></span>  
 <span data-ttu-id="41e8d-142">[建立 Windows 驗證的資料庫鏡像端點 &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="41e8d-142">[Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span></span>  
 <span data-ttu-id="41e8d-143">[啟動資料庫鏡像監視器 &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="41e8d-143">[Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="41e8d-144">[資料庫鏡像 &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="41e8d-144">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="41e8d-145">資料庫鏡像見證</span><span class="sxs-lookup"><span data-stu-id="41e8d-145">Database Mirroring Witness</span></span>](database-mirroring-witness.md)  
  
  
