---
title: 主體伺服器執行個體 (設定資料庫鏡像安全性精靈) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.principalsrvr.f1
ms.assetid: 58af27d7-c5dd-4669-be6b-b472bc2c8ef4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2632b5ffd5355065b4b5c1f905b3b6e5c5b6204d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701839"
---
# <a name="principal-server-instance-configure-database-mirroring-security-wizard"></a><span data-ttu-id="1716b-102">主體伺服器執行個體 (設定資料庫鏡像安全性精靈)</span><span class="sxs-lookup"><span data-stu-id="1716b-102">Principal Server Instance (Configure Database Mirroring Security Wizard)</span></span>
  <span data-ttu-id="1716b-103">使用此頁面來指定有關主體資料庫之伺服器執行個體的資訊。</span><span class="sxs-lookup"><span data-stu-id="1716b-103">Use this page to specify information about the server instance of the principal database.</span></span> <span data-ttu-id="1716b-104">主體資料庫是開始鏡像工作階段的資料庫副本。</span><span class="sxs-lookup"><span data-stu-id="1716b-104">The principal database is the copy of the database that begins the mirroring session.</span></span> <span data-ttu-id="1716b-105">工作階段開始之後，主體資料庫是接受使用者變更的資料庫副本。</span><span class="sxs-lookup"><span data-stu-id="1716b-105">After the session has begun, the principal database is the copy of the database that accepts user changes.</span></span> <span data-ttu-id="1716b-106">(發生容錯移轉時，主體與鏡像角色會交換，所以初始的主體資料庫可能不再是主體資料庫)。</span><span class="sxs-lookup"><span data-stu-id="1716b-106">(When a failover occurs, the principal and mirroring roles are swapped; therefore, the initial principal database might not remain the principal database.)</span></span>  
  
 <span data-ttu-id="1716b-107">**若要使用 SQL Server Management Studio 設定資料庫鏡像**</span><span class="sxs-lookup"><span data-stu-id="1716b-107">**To configure database mirroring by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="1716b-108">使用 Windows 驗證建立資料庫鏡像工作階段 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="1716b-108">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="1716b-109">啟動設定資料庫鏡像安全性精靈 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="1716b-109">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a><span data-ttu-id="1716b-110">選項。</span><span class="sxs-lookup"><span data-stu-id="1716b-110">Options</span></span>  
 <span data-ttu-id="1716b-111">**主體伺服器執行個體**</span><span class="sxs-lookup"><span data-stu-id="1716b-111">**Principal server instance**</span></span>  
 <span data-ttu-id="1716b-112">因為 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的資料庫鏡像一律從主體伺服器設定，所以目前的伺服器執行個體一律為主體伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="1716b-112">Because database mirroring in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is always configured from the principal server, the current server instance is always the principal server instance.</span></span>  
  
 <span data-ttu-id="1716b-113">**接聽程式連接埠**</span><span class="sxs-lookup"><span data-stu-id="1716b-113">**Listener Port**</span></span>  
 <span data-ttu-id="1716b-114">此選項的行為會視此伺服器執行個體的鏡像端點是否存在，如下：</span><span class="sxs-lookup"><span data-stu-id="1716b-114">The behavior of this option depends on whether the mirroring endpoint exists for this server instance, as follows:</span></span>  
  
-   <span data-ttu-id="1716b-115">如果這個伺服器執行個體沒有接聽程式通訊埠，在 **[通訊埠]** 文字方塊中就會顯示通訊埠編號 5022。</span><span class="sxs-lookup"><span data-stu-id="1716b-115">If the listener port does not exist for this server instance, port number 5022 is displayed in the **Port** text box.</span></span> <span data-ttu-id="1716b-116">您可以使用任何可用的通訊埠編號，例如 7022。</span><span class="sxs-lookup"><span data-stu-id="1716b-116">You can use any available port number, such as, 7022.</span></span>  
  
-   <span data-ttu-id="1716b-117">當鏡像端點已經存在時，會顯示來自端點的通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="1716b-117">When the mirroring endpoint already exists, the port number from the endpoint is displayed.</span></span> <span data-ttu-id="1716b-118">如果您需要變更通訊埠，請使用 ALTER ENDPOINT 命令。</span><span class="sxs-lookup"><span data-stu-id="1716b-118">If you need to change the port, use an ALTER ENDPOINT command.</span></span> <span data-ttu-id="1716b-119">如需詳細資訊，請參閱 [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1716b-119">For more information, see [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1716b-120">需要通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="1716b-120">A port number is required.</span></span>  
  
 <span data-ttu-id="1716b-121">**端點名稱**</span><span class="sxs-lookup"><span data-stu-id="1716b-121">**Endpoint name**</span></span>  
 <span data-ttu-id="1716b-122">如果這個伺服器執行個體存在有鏡像端點，該端點名稱會顯示於此處。</span><span class="sxs-lookup"><span data-stu-id="1716b-122">If the mirroring endpoint exists for this server instance, the endpoint name is displayed here.</span></span> <span data-ttu-id="1716b-123">如果端點不存在，您可以指定端點名稱。</span><span class="sxs-lookup"><span data-stu-id="1716b-123">If the endpoint does not exist, you can specify the name of the endpoint.</span></span>  
  
 <span data-ttu-id="1716b-124">**透過此端點傳送的資料要加密**</span><span class="sxs-lookup"><span data-stu-id="1716b-124">**Encrypt data sent through this endpoint**</span></span>  
 <span data-ttu-id="1716b-125">依預設，加密為已啟用。</span><span class="sxs-lookup"><span data-stu-id="1716b-125">By default, encryption is enabled.</span></span> <span data-ttu-id="1716b-126">當已啟用時，加密為必須的 (不只是支援的)，並且所有的加密選項都使用預設值。</span><span class="sxs-lookup"><span data-stu-id="1716b-126">When enabled, encryption is required (not merely supported) and uses the default values for all of the encryption options.</span></span> <span data-ttu-id="1716b-127">如需詳細資訊，請參閱 [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql)的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="1716b-127">For more information, see [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).</span></span>  
  
 <span data-ttu-id="1716b-128">若要停用加密，請清除該核取方塊。</span><span class="sxs-lookup"><span data-stu-id="1716b-128">To disable encryption, clear the check box.</span></span> <span data-ttu-id="1716b-129">若要重新啟用加密，請選取該核取方塊。</span><span class="sxs-lookup"><span data-stu-id="1716b-129">To re-enable encryption, select the check box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1716b-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1716b-130">See Also</span></span>  
 <span data-ttu-id="1716b-131">[資料庫鏡像端點 &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1716b-131">[The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="1716b-132">[資料庫屬性 &#40;鏡像頁面&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span><span class="sxs-lookup"><span data-stu-id="1716b-132">[Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span></span>  
 <span data-ttu-id="1716b-133">[建立 Windows 驗證的資料庫鏡像端點 &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="1716b-133">[Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span></span>  
 <span data-ttu-id="1716b-134">[啟動資料庫鏡像監視器 &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="1716b-134">[Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="1716b-135">資料庫鏡像 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1716b-135">Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)  
  
  
