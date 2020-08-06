---
title: 介面區組態 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- reducing attackable surface area
- upgrading SQL Server, security
- surface area configuration [SQL Server]
- surface area configuration [SQL Server], about surface area configuration
- attackable surface area [SQL Server]
- installing SQL Server, security
ms.assetid: f741169c-1453-4ad2-830b-bf2be27d712f
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: ef64fbbeb2b8953ff3816db63572b499d42f012e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688702"
---
# <a name="surface-area-configuration"></a><span data-ttu-id="9a65c-102">介面區組態</span><span class="sxs-lookup"><span data-stu-id="9a65c-102">Surface Area Configuration</span></span>
  <span data-ttu-id="9a65c-103">在新安裝的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]預設組態中，許多功能都不會啟用。</span><span class="sxs-lookup"><span data-stu-id="9a65c-103">In the default configuration of new installations of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], many features are not enabled.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9a65c-104">為了將可能會遭受惡意使用者攻擊的功能數目最小化，因此會選擇性地只安裝與啟動主要的服務與功能。</span><span class="sxs-lookup"><span data-stu-id="9a65c-104">selectively installs and starts only key services and features, to minimize the number of features that can be attacked by a malicious user.</span></span> <span data-ttu-id="9a65c-105">系統管理員可在安裝期間變更這些預設值，也可以選擇性地啟用或停用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]之執行中執行個體的功能。</span><span class="sxs-lookup"><span data-stu-id="9a65c-105">A system administrator can change these defaults at installation time and also selectively enable or disable features of a running instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9a65c-106">此外，從其他電腦連接時，某些元件可能要等到設定通訊協定之後才能使用。</span><span class="sxs-lookup"><span data-stu-id="9a65c-106">Additionally, some components may not be available when connecting from other computers until protocols are configured.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9a65c-107">與新安裝不同的是，在升級處理期間不會關閉任何現有的服務或功能，但是在升級完成後可能會套用其他介面區組態選項。</span><span class="sxs-lookup"><span data-stu-id="9a65c-107">Unlike new installations, no existing services or features are turned off during an upgrade, but additional surface area configuration options can be applied after the upgrade is completed.</span></span>  
  
## <a name="protocols-connection-and-startup-options"></a><span data-ttu-id="9a65c-108">通訊協定、連接和啟動選項</span><span class="sxs-lookup"><span data-stu-id="9a65c-108">Protocols, Connection, and Startup Options</span></span>  
 <span data-ttu-id="9a65c-109">您可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員來啟動和停止服務、設定啟動選項，以及啟用通訊協定和其他連線選項。</span><span class="sxs-lookup"><span data-stu-id="9a65c-109">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager to start and stop services, configure the startup options, and enable protocols and other connection options.</span></span>  
  
#### <a name="to-start-sql-server-configuration-manager"></a><span data-ttu-id="9a65c-110">啟動 SQL Server 組態管理員</span><span class="sxs-lookup"><span data-stu-id="9a65c-110">To start SQL Server Configuration Manager</span></span>  
  
1.  <span data-ttu-id="9a65c-111">指向 **[開始]** 功能表上的 **[所有程式]** ，然後依序指向 [ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]] 和 **[組態工具]** ，再按一下 **[SQL Server 組態管理員]** 。</span><span class="sxs-lookup"><span data-stu-id="9a65c-111">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
    -   <span data-ttu-id="9a65c-112">使用 **SQL Server 服務** 區域來啟動元件並設定自動啟動選項。</span><span class="sxs-lookup"><span data-stu-id="9a65c-112">Use the **SQL Server Services** area to start components and configure the automatic starting options.</span></span>  
  
    -   <span data-ttu-id="9a65c-113">使用 **SQL Server 網路組態** 區域來啟用連線通訊協定，以及連線選項，例如固定 TCP/IP 通訊埠或強制加密。</span><span class="sxs-lookup"><span data-stu-id="9a65c-113">Use the **SQL Server Network Configuration** area to enable connection protocols, and connection options such as fixed TCP/IP ports, or forcing encryption.</span></span>  
  
 <span data-ttu-id="9a65c-114">如需詳細資訊，請參閱 [SQL Server 組態管理員](../sql-server-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="9a65c-114">For more information, see [SQL Server Configuration Manager](../sql-server-configuration-manager.md).</span></span> <span data-ttu-id="9a65c-115">遠端連接可能也會取決於防火牆的正確組態。</span><span class="sxs-lookup"><span data-stu-id="9a65c-115">Remote connectivity can also depend upon the correct configuration of a firewall.</span></span> <span data-ttu-id="9a65c-116">如需詳細資訊，請參閱 [設定 Windows 防火牆以允許 SQL Server 存取](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)。</span><span class="sxs-lookup"><span data-stu-id="9a65c-116">For more information, see [Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span>  
  
## <a name="enabling-and-disabling-features"></a><span data-ttu-id="9a65c-117">啟用和停用功能</span><span class="sxs-lookup"><span data-stu-id="9a65c-117">Enabling and Disabling Features</span></span>  
 <span data-ttu-id="9a65c-118">您可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的 Facet 來設定啟用和停用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]功能。</span><span class="sxs-lookup"><span data-stu-id="9a65c-118">Enabling and disabling [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features can be configured using facets in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-configure-surface-area-using-facets"></a><span data-ttu-id="9a65c-119">使用 Facet 來設定介面區</span><span class="sxs-lookup"><span data-stu-id="9a65c-119">To configure surface area using facets</span></span>  
  
1.  <span data-ttu-id="9a65c-120">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中，連接至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的元件。</span><span class="sxs-lookup"><span data-stu-id="9a65c-120">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] connect to a component of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="9a65c-121">在 [物件總管] 中，以滑鼠右鍵按一下伺服器，然後按一下 [Facets]。</span><span class="sxs-lookup"><span data-stu-id="9a65c-121">In Object Explorer, right-click the server, and then click **Facets**.</span></span>  
  
3.  <span data-ttu-id="9a65c-122">在 [檢視 Facets] 對話方塊中，展開 [Facet] 清單，並選取適當的 [介面區組態] Facet ([介面區組態]、[Analysis Services 的介面區組態]，或 [Reporting Services 介面區組態])。</span><span class="sxs-lookup"><span data-stu-id="9a65c-122">In the **View Facets** dialog box, expand the **Facet** list, and select the appropriate **Surface Area Configuration** facet (**Surface Area Configuration**, **Surface Area Configuration for Analysis Services**, or **Surface Area Configuration for Reporting Services**).</span></span>  
  
4.  <span data-ttu-id="9a65c-123">在 **Facet 屬性** 區域中，選取您想要用於每個屬性的值。</span><span class="sxs-lookup"><span data-stu-id="9a65c-123">In the **Facet properties** area, select the values that you want for each property.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="9a65c-124">若要定期檢查 Facet 的組態，請使用以原則為基礎的管理。</span><span class="sxs-lookup"><span data-stu-id="9a65c-124">To periodically check the configuration of a facet, use Policy-Based Management.</span></span> <span data-ttu-id="9a65c-125">如需原則式管理的詳細資訊，請參閱 [使用原則式管理來管理伺服器](../policy-based-management/administer-servers-by-using-policy-based-management.md)。</span><span class="sxs-lookup"><span data-stu-id="9a65c-125">For more information about Policy-Based Management, see [Administer Servers by Using Policy-Based Management](../policy-based-management/administer-servers-by-using-policy-based-management.md).</span></span>  
  
 <span data-ttu-id="9a65c-126">您也可以使用 `sp_configure` 預存程序來設定 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 選項。</span><span class="sxs-lookup"><span data-stu-id="9a65c-126">You can also set [!INCLUDE[ssDE](../../includes/ssde-md.md)] options using the `sp_configure` stored procedure.</span></span> <span data-ttu-id="9a65c-127">如需詳細資訊，請參閱 [伺服器設定選項 &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="9a65c-127">For more information, see [Server Configuration Options &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).</span></span>  
  
 <span data-ttu-id="9a65c-128">變更 **的** EnableIntegrated Security [!INCLUDE[ssRS](../../includes/ssrs.md)]屬性時，請使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的屬性設定。</span><span class="sxs-lookup"><span data-stu-id="9a65c-128">To change the **EnableIntegrated Security** property of [!INCLUDE[ssRS](../../includes/ssrs.md)], use the property settings in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="9a65c-129">若要變更 [排程事件和報表傳遞] 屬性以及 [Web 服務和 HTTP 存取] 屬性時，請編輯 **RSReportServer.config** 組態檔。</span><span class="sxs-lookup"><span data-stu-id="9a65c-129">To change the **Schedule events and report delivery** property and the **Web service and HTTP access** property, edit the **RSReportServer.config** configuration file.</span></span>  
  
## <a name="command-prompt-options"></a><span data-ttu-id="9a65c-130">命令提示字元選項</span><span class="sxs-lookup"><span data-stu-id="9a65c-130">Command-prompt Options</span></span>  
 <span data-ttu-id="9a65c-131">您可以使用 **Invoke-PolicyEvaluation**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell Cmdlet 以叫用介面區組態原則。</span><span class="sxs-lookup"><span data-stu-id="9a65c-131">Use the **Invoke-PolicyEvaluation**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell cmdlet to invoke Surface Area Configuration Policies.</span></span> <span data-ttu-id="9a65c-132">如需詳細資訊，請參閱 [使用 Database Engine Cmdlet](../../database-engine/use-the-database-engine-cmdlets.md)。</span><span class="sxs-lookup"><span data-stu-id="9a65c-132">For more information, see [Use the Database Engine cmdlets](../../database-engine/use-the-database-engine-cmdlets.md).</span></span>  
  
## <a name="soap-and-service-broker-endpoints"></a><span data-ttu-id="9a65c-133">SOAP 和 Service Broker 端點</span><span class="sxs-lookup"><span data-stu-id="9a65c-133">SOAP and Service Broker Endpoints</span></span>  
 <span data-ttu-id="9a65c-134">若要關閉端點，請使用以原則為基礎的管理。</span><span class="sxs-lookup"><span data-stu-id="9a65c-134">To turn endpoints off, use Policy-Based Management.</span></span> <span data-ttu-id="9a65c-135">建立和改變端點的屬性時，請使用 [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql) 和 [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="9a65c-135">To create and alter the properties of endpoints, use [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql) and [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="9a65c-136">相關內容</span><span class="sxs-lookup"><span data-stu-id="9a65c-136">Related Content</span></span>  
 [<span data-ttu-id="9a65c-137">SQL Server Database Engine 和 Azure SQL Database 的資訊安全中心</span><span class="sxs-lookup"><span data-stu-id="9a65c-137">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
 [<span data-ttu-id="9a65c-138">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9a65c-138">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
