---
title: Analysis Services 與 AlwaysOn 可用性群組 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 14d16bfd-228c-4870-b463-a283facda965
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9ea0c7f30fd8f431f70284122df7e2a036658f4e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585622"
---
# <a name="analysis-services-with-always-on-availability-groups"></a><span data-ttu-id="f093c-102">Analysis Services 與 AlwaysOn 可用性群組</span><span class="sxs-lookup"><span data-stu-id="f093c-102">Analysis Services with Always On Availability Groups</span></span>
  <span data-ttu-id="f093c-103">AlwaysOn 可用性群組是預先定義的 SQL Server 關聯式資料庫集合，會在條件觸發任何一個資料庫的容錯移轉時一起容錯移轉，將要求重新導向至相同可用性群組中其他執行個體上的鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="f093c-103">An AlwaysOn availability group is a predefined collection of SQL Server relational databases that failover together when conditions trigger a failover in any one database, redirecting requests to a mirrored database on another instance in the same availability group.</span></span> <span data-ttu-id="f093c-104">如果使用可用性群組做為高可用性解決方案，則可以使用該群組中的資料庫做為 Analysis Services 表格式或多維度解決方案的資料來源。</span><span class="sxs-lookup"><span data-stu-id="f093c-104">If you are using availability groups as your high availability solution, you can use a database in that group as a data source in an Analysis Services tabular or multidimensional solution.</span></span> <span data-ttu-id="f093c-105">使用可用性資料庫時，下列所有 Analysis Services 作業都會如預期般運作：處理或匯入資料、直接查詢關聯式資料 (使用 ROLAP 儲存或 DirectQuery 模式)，以及回寫。</span><span class="sxs-lookup"><span data-stu-id="f093c-105">All of the following Analysis Services operations work as expected when using an availability database: processing or importing data, querying relational data directly (using ROLAP storage or DirectQuery mode), and writeback.</span></span>  
  
 <span data-ttu-id="f093c-106">處理及查詢是唯讀工作負載。</span><span class="sxs-lookup"><span data-stu-id="f093c-106">Processing and querying are read-only workloads.</span></span> <span data-ttu-id="f093c-107">您可以將這些工作負載卸載至可讀取的次要複本，以提升效能。</span><span class="sxs-lookup"><span data-stu-id="f093c-107">You can improve performance by offloading these workloads to a readable secondary replica.</span></span> <span data-ttu-id="f093c-108">這個案例不需要進行其他組態設定。</span><span class="sxs-lookup"><span data-stu-id="f093c-108">Additional configuration is required for this scenario.</span></span> <span data-ttu-id="f093c-109">使用本主題中的檢查清單，以確保您遵循所有步驟。</span><span class="sxs-lookup"><span data-stu-id="f093c-109">Use the checklist in this topic to ensure you follow all the steps.</span></span>  
  
  
##  <a name="prerequisites"></a><a name="bkmk_prereq"></a> <span data-ttu-id="f093c-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="f093c-110">Prerequisites</span></span>  
 <span data-ttu-id="f093c-111">您必須擁有所有複本的 SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="f093c-111">You must have a SQL Server login on all replicas.</span></span> <span data-ttu-id="f093c-112">您必須是 **系統管理員** ，才能設定可用性群組、接聽程式及資料庫，但是使用者只需要 **db_datareader** 權限，即可從 Analysis Services 用戶端存取資料庫。</span><span class="sxs-lookup"><span data-stu-id="f093c-112">You must be a **sysadmin** to configure availability groups, listeners, and databases, but users only need **db_datareader** permissions to access the database from an Analysis Services client.</span></span>  
  
 <span data-ttu-id="f093c-113">使用支援表格式資料流 (TDS) 通訊協定 7.4 版或更新版本的資料提供者，例如 SQL Server Native Client 11.0 或 .NET Framework 4.02 的 Data Provider for SQL Server。</span><span class="sxs-lookup"><span data-stu-id="f093c-113">Use a data provider that supports the tabular data stream (TDS) protocol version 7.4 or newer, such as the SQL Server Native Client 11.0 or the Data Provider for SQL Server in .NET Framework 4.02.</span></span>  
  
 <span data-ttu-id="f093c-114">**(適用於唯讀工作負載)**。</span><span class="sxs-lookup"><span data-stu-id="f093c-114">**(For read-only workloads)**.</span></span> <span data-ttu-id="f093c-115">您必須設定唯讀連接的次要複本角色，可用性群組必須具有路由清單，且 Analysis Services 資料來源中的連接必須指定可用性群組接聽程式。</span><span class="sxs-lookup"><span data-stu-id="f093c-115">The secondary replica role must be configured for read-only connections, the availability group must have a routing list, and the connection in the Analysis Services data source must specify the availability group listener.</span></span> <span data-ttu-id="f093c-116">本主題將提供指示。</span><span class="sxs-lookup"><span data-stu-id="f093c-116">Instructions are provided in this topic.</span></span>  
  
##  <a name="checklist-use-a-secondary-replica-for-read-only-operations"></a><a name="bkmk_UseSecondary"></a> <span data-ttu-id="f093c-117">檢查清單：僅針對唯讀作業使用次要複本</span><span class="sxs-lookup"><span data-stu-id="f093c-117">Checklist: Use a secondary replica for read-only operations</span></span>  
 <span data-ttu-id="f093c-118">除非 Analysis Services 解決方案包含回寫，否則您可以設定資料來源連接使用可讀取的次要複本。</span><span class="sxs-lookup"><span data-stu-id="f093c-118">Unless your Analysis Services solution includes writeback, you can configure a data source connection to use a readable secondary replica.</span></span> <span data-ttu-id="f093c-119">如果具有快速網路連接，次要複本的資料延遲會很低，因此提供與主要複本幾乎相同的資料。</span><span class="sxs-lookup"><span data-stu-id="f093c-119">If you have a fast network connection, the secondary replica has very low data latency, providing nearly identical data as the primary replica.</span></span> <span data-ttu-id="f093c-120">透過使用次要複本進行 Analysis Services 作業，您可以降低主要複本的讀寫競爭，並更善用可用性群組中的次要複本。</span><span class="sxs-lookup"><span data-stu-id="f093c-120">By using the secondary replica for Analysis Services operations, you can reduce read-write contention on the primary replica and get better utilization of secondary replicas in your availability group.</span></span>  
  
 <span data-ttu-id="f093c-121">預設允許與主要複本之間的讀寫和讀取意圖的存取，但是不允許連接次要複本。</span><span class="sxs-lookup"><span data-stu-id="f093c-121">By default, both read-write and read-intent access are allowed to the primary replica and no connections are allowed to secondary replicas.</span></span> <span data-ttu-id="f093c-122">次要複本的唯讀用戶端連接需要進行其他組態設定。</span><span class="sxs-lookup"><span data-stu-id="f093c-122">Additional configuration is required to set up a read-only client connection to a secondary replica.</span></span> <span data-ttu-id="f093c-123">這些組態設定需要設定次要複本的屬性，以及執行定義唯讀路由清單的 T-SQL 指令碼。</span><span class="sxs-lookup"><span data-stu-id="f093c-123">Configuration requires setting properties on the secondary replica and running a T-SQL script that defines a read-only routing list.</span></span> <span data-ttu-id="f093c-124">使用下列程序，以確保您已經執行這兩個步驟。</span><span class="sxs-lookup"><span data-stu-id="f093c-124">Use the following procedures to ensure you have performed both steps.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f093c-125">下列步驟假設存在 AlwaysOn 可用性群組和資料庫。</span><span class="sxs-lookup"><span data-stu-id="f093c-125">The following steps assume an existing AlwaysOn availability group and databases.</span></span> <span data-ttu-id="f093c-126">如果您想設定新群組，請使用 [新增可用性群組精靈] 建立群組並加入資料庫。</span><span class="sxs-lookup"><span data-stu-id="f093c-126">If you are configuring a new group, use the New Availability Group Wizard to create the group and join the databases.</span></span> <span data-ttu-id="f093c-127">這個精靈會檢查先決條件、提供每個步驟的指引，並執行初始同步處理。</span><span class="sxs-lookup"><span data-stu-id="f093c-127">The wizard checks for prerequisites, provides guidance for each step, and performs the initial synchronization.</span></span> <span data-ttu-id="f093c-128">如需詳細資訊，請參閱[使用可用性群組精靈 &#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="f093c-128">For more information, see [Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md).</span></span>  
  
#### <a name="step-1-configure-access-on-an-availability-replica"></a><span data-ttu-id="f093c-129">步驟 1：設定可用性複本的存取</span><span class="sxs-lookup"><span data-stu-id="f093c-129">Step 1: Configure access on an availability replica</span></span>  
  
1.  <span data-ttu-id="f093c-130">在 [物件總管] 中，連接到裝載主要複本的伺服器執行個體，然後展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="f093c-130">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f093c-131">這些步驟摘錄自[設定可用性複本上的唯讀存取 &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md)，文中提供執行這項工作的其他資訊和替代指示。</span><span class="sxs-lookup"><span data-stu-id="f093c-131">These steps are taken from [Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md), which provides additional information and alternative instructions for performing this task.</span></span>  
  
2.  <span data-ttu-id="f093c-132">依序展開 **[AlwaysOn 高可用性]** 節點和 **[可用性群組]** 節點。</span><span class="sxs-lookup"><span data-stu-id="f093c-132">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="f093c-133">按一下要變更複本的可用性群組。</span><span class="sxs-lookup"><span data-stu-id="f093c-133">Click the availability group whose replica you want to change.</span></span> <span data-ttu-id="f093c-134">展開 **[可用性複本]**。</span><span class="sxs-lookup"><span data-stu-id="f093c-134">Expand **Availability Replicas**.</span></span>  
  
4.  <span data-ttu-id="f093c-135">以滑鼠右鍵按一下次要複本，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f093c-135">Right-click the secondary replica, and click **Properties**.</span></span>  
  
5.  <span data-ttu-id="f093c-136">在 **[可用性複本屬性]** 對話方塊中，變更次要角色的連接存取，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f093c-136">In the **Availability Replica Properties** dialog box, change the connection access for the secondary role, as follows:</span></span>  
  
    -   <span data-ttu-id="f093c-137">在 [可讀取次要]\*\*\*\* 下拉式清單中，選取 [僅限讀取意圖]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f093c-137">In the **Readable secondary** drop list, select **Read-intent only**.</span></span>  
  
    -   <span data-ttu-id="f093c-138">在 **[主要角色的連接]** 下拉式清單中，選取 **[允許所有連接]**。</span><span class="sxs-lookup"><span data-stu-id="f093c-138">In the **Connections in primary role** drop list, select **Allow all connections**.</span></span> <span data-ttu-id="f093c-139">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="f093c-139">This is the default.</span></span>  
  
    -   <span data-ttu-id="f093c-140">或者，在 **[可用性模式]** 下拉式清單中，選取 **[同步認可]**。</span><span class="sxs-lookup"><span data-stu-id="f093c-140">Optionally, in **Availability mode** drop list, select **Synchronous commit**.</span></span> <span data-ttu-id="f093c-141">不需要這個步驟，但是進行設定可確保主要與次要複本之間的資料同位。</span><span class="sxs-lookup"><span data-stu-id="f093c-141">This step is not required, but setting it ensures that there is data parity between the primary and secondary replica.</span></span>  
  
         <span data-ttu-id="f093c-142">規劃的容錯移轉也需要這個屬性。</span><span class="sxs-lookup"><span data-stu-id="f093c-142">This property is also a requirement for planned failover.</span></span> <span data-ttu-id="f093c-143">如果您要執行規劃的手動容錯移轉以進行測試，請將主要與次要複本的 **[可用性模式]** 同時設為 **[同步認可]** 。</span><span class="sxs-lookup"><span data-stu-id="f093c-143">If you want to perform a planned manual failover for testing purposes, set **Availability mode** to **Synchronous commit** for both the primary and secondary replica.</span></span>  
  
#### <a name="step-2-configure-read-only-routing"></a><span data-ttu-id="f093c-144">步驟 2：設定唯讀路由</span><span class="sxs-lookup"><span data-stu-id="f093c-144">Step 2: Configure read-only routing</span></span>  
  
1.  <span data-ttu-id="f093c-145">連接到主要複本。</span><span class="sxs-lookup"><span data-stu-id="f093c-145">Connect to the primary replica.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f093c-146">這些步驟摘錄自[設定可用性群組的唯讀路由 &#40;SQL Server&#41;](configure-read-only-routing-for-an-availability-group-sql-server.md)，文中提供執行這項工作的其他資訊和替代指示。</span><span class="sxs-lookup"><span data-stu-id="f093c-146">These steps are taken from [Configure Read-Only Routing for an Availability Group &#40;SQL Server&#41;](configure-read-only-routing-for-an-availability-group-sql-server.md), which provides additional information and alternative instructions for performing this task.</span></span>  
  
2.  <span data-ttu-id="f093c-147">開啟查詢視窗並貼上下列指令碼。</span><span class="sxs-lookup"><span data-stu-id="f093c-147">Open a query window and paste in the following script.</span></span> <span data-ttu-id="f093c-148">這個指令碼會執行三個動作：啟用次要複本的可讀取連接 (預設為關閉)、設定唯讀路由 URL，以及建立路由清單以排定導向連接要求的優先順序。</span><span class="sxs-lookup"><span data-stu-id="f093c-148">This script does three things: enables readable connections to a secondary replica (which is off by default), sets the read-only routing URL, and creates the routing list that prioritizes how connection requests are directed.</span></span>  <span data-ttu-id="f093c-149">如果您已經在 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]中設定屬性，但是為求完整性已併入屬性，則第一個陳述式 (允許可讀取連接) 為多餘的陳述式。</span><span class="sxs-lookup"><span data-stu-id="f093c-149">The first statement, allowing readable connections, is redundant if you already set the properties in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], but are included for completeness.</span></span>  
  
    ```  
    ALTER AVAILABILITY GROUP [AG1]  
     MODIFY REPLICA ON  
    N'COMPUTER01' WITH   
    (SECONDARY_ROLE (ALLOW_CONNECTIONS = READ_ONLY));  
  
    ALTER AVAILABILITY GROUP [AG1]  
     MODIFY REPLICA ON  
    N'COMPUTER01' WITH   
    (SECONDARY_ROLE (READ_ONLY_ROUTING_URL = N'TCP://COMPUTER01.contoso.com:1433'));  
  
    ALTER AVAILABILITY GROUP [AG1]  
     MODIFY REPLICA ON  
    N'COMPUTER02' WITH   
    (SECONDARY_ROLE (ALLOW_CONNECTIONS = READ_ONLY));  
  
    ALTER AVAILABILITY GROUP [AG1]  
     MODIFY REPLICA ON  
    N'COMPUTER02' WITH   
    (SECONDARY_ROLE (READ_ONLY_ROUTING_URL = N'TCP://COMPUTER02.contoso.com:1433'));  
  
    ALTER AVAILABILITY GROUP [AG1]   
    MODIFY REPLICA ON  
    N'COMPUTER01' WITH   
    (PRIMARY_ROLE (READ_ONLY_ROUTING_LIST=('COMPUTER02','COMPUTER01')));  
  
    ALTER AVAILABILITY GROUP [AG1]   
    MODIFY REPLICA ON  
    N'COMPUTER02' WITH   
    (PRIMARY_ROLE (READ_ONLY_ROUTING_LIST=('COMPUTER01','COMPUTER02')));  
    GO  
    ```  
  
3.  <span data-ttu-id="f093c-150">修改指令碼，以對您的部署有效的值來取代預留位置：</span><span class="sxs-lookup"><span data-stu-id="f093c-150">Modify the script, replacing placeholders with values that are valid for your deployment:</span></span>  
  
    -   <span data-ttu-id="f093c-151">以裝載主要複本之伺服器執行個體的名稱取代 'Computer01'。</span><span class="sxs-lookup"><span data-stu-id="f093c-151">Replace 'Computer01' with the name of the server instance that hosts the primary replica.</span></span>  
  
    -   <span data-ttu-id="f093c-152">以裝載次要複本之伺服器執行個體的名稱取代 'Computer02'。</span><span class="sxs-lookup"><span data-stu-id="f093c-152">Replace 'Computer02' with the name of the server instance that hosts the secondary replica.</span></span>  
  
    -   <span data-ttu-id="f093c-153">以您的網域名稱取代 'contoso.com'，如果所有電腦都在相同的網域，則可以從指令碼加以省略。</span><span class="sxs-lookup"><span data-stu-id="f093c-153">Replace 'contoso.com' with the name of your domain, or omit it from the script if all computers are in the same domain.</span></span> <span data-ttu-id="f093c-154">如果接聽程式使用預設通訊埠，請保留通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="f093c-154">Keep the port number if the listener is using the default port.</span></span> <span data-ttu-id="f093c-155">接聽程式實際使用的通訊埠會列於 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]的屬性頁面中。</span><span class="sxs-lookup"><span data-stu-id="f093c-155">The port that is actually used by the listener is listed in the properties page in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)].</span></span>  
  
4.  <span data-ttu-id="f093c-156">執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="f093c-156">Execute the script.</span></span>  
  
     <span data-ttu-id="f093c-157">下一步，建立 Analysis Services 模型中的資料來源，這個資料來源會使用您剛才設定之群組中的資料庫。</span><span class="sxs-lookup"><span data-stu-id="f093c-157">Next, create a data source in an Analysis Services model that uses a database from the group you just configured.</span></span>  
  
##  <a name="create-an-analysis-services-data-source-using-an-alwayson-availability-database"></a><a name="bkmk_ssasAODB"></a><span data-ttu-id="f093c-158">使用 AlwaysOn 可用性資料庫建立 Analysis Services 資料來源</span><span class="sxs-lookup"><span data-stu-id="f093c-158">Create an Analysis Services data source using an AlwaysOn availability database</span></span>  
 <span data-ttu-id="f093c-159">本節說明如何建立連接至可用性群組中某個資料庫的 Analysis Services 資料來源。</span><span class="sxs-lookup"><span data-stu-id="f093c-159">This section explains how to create an Analysis Services data source that connects to a database in an availability group.</span></span> <span data-ttu-id="f093c-160">您可以使用這些說明，設定主要複本 (預設) 或您根據上一節步驟所設定之可讀取次要複本的連接。</span><span class="sxs-lookup"><span data-stu-id="f093c-160">You can use these instructions to configure a connection to either a primary replica (default) or a readable secondary replica that you configured based on steps in a previous section.</span></span> <span data-ttu-id="f093c-161">AlwaysOn 組態設定及在用戶端設定的連接屬性，決定使用主要或次要複本。</span><span class="sxs-lookup"><span data-stu-id="f093c-161">AlwaysOn configuration settings, plus the connection properties set in the client, will determine whether a primary or secondary replica is used.</span></span>  
  
1.  <span data-ttu-id="f093c-162">在 [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)] 的 Analysis Services 多維度和資料採礦模型專案中，以滑鼠右鍵按一下 [資料來源]\*\*\*\*，然後選取 [新增資料來源]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f093c-162">In [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)], in an Analysis Services Multidimensional and Data Mining Model project, right-click **Data Sources** and select **New Data Source**.</span></span> <span data-ttu-id="f093c-163">按一下 **[新增]** 建立新的資料來源。</span><span class="sxs-lookup"><span data-stu-id="f093c-163">Click **New** to create a new data source.</span></span>  
  
     <span data-ttu-id="f093c-164">或者，針對表格式模型專案，按一下 [模型] 功能表，然後按一下 **[從資料來源匯入]**。</span><span class="sxs-lookup"><span data-stu-id="f093c-164">Alternatively, for a tabular model project, click the Model menu, and then click **Import from Data Source**.</span></span>  
  
2.  <span data-ttu-id="f093c-165">在 [連接管理員] 的 [提供者] 中，選擇支援表格式資料流 (TDS) 通訊協定的提供者。</span><span class="sxs-lookup"><span data-stu-id="f093c-165">In Connection Manager, in Provider, choose a provider that supports the Tabular Data Stream (TDS) protocol.</span></span> <span data-ttu-id="f093c-166">SQL Server Native Client 11.0 支援這個通訊協定。</span><span class="sxs-lookup"><span data-stu-id="f093c-166">The SQL Server Native Client 11.0 supports this protocol.</span></span>  
  
3.  <span data-ttu-id="f093c-167">在 [連接管理員] 的 [伺服器名稱] 中，輸入 *「可用性群組接聽程式」*(Availability Group Listener) 的名稱，然後選擇群組中可用的資料庫。</span><span class="sxs-lookup"><span data-stu-id="f093c-167">In Connection Manager, in Server Name, enter the name of the *availability group listener*, and then choose a database that is available in the group.</span></span>  
  
     <span data-ttu-id="f093c-168">若是讀寫要求，可用性群組接聽程式會將用戶端連接重新導向至主要複本，如果在連接字串中指定讀取意圖，則會重新導向至次要複本。</span><span class="sxs-lookup"><span data-stu-id="f093c-168">The availability group listener redirects a client connection to a primary replica for read-write requests or to a secondary replica if you specify read-intent in the connection string.</span></span> <span data-ttu-id="f093c-169">由於複本角色在容錯移轉期間會變更 (主要變成次要，而次要變成主要)，因此請務必指定接聽程式據以重新導向用戶端連接。</span><span class="sxs-lookup"><span data-stu-id="f093c-169">Because replica roles will change during a failover (where the primary becomes the secondary and a secondary becomes a primary), you should always specify the listener so that the client connection is redirected accordingly.</span></span>  
  
     <span data-ttu-id="f093c-170">若要確定可用性群組接聽程式的名稱，您可以詢問資料庫管理員，或連接至可用性群組中的執行個體並檢視其 AlwaysOn 可用性組態。</span><span class="sxs-lookup"><span data-stu-id="f093c-170">To determine the name of the availability group listener, you can either ask a database administrator or connect to an instance in the availability group and view its AlwaysOn availability configuration.</span></span> <span data-ttu-id="f093c-171">在下面的螢幕擷取畫面中，可用性群組接聽程式為 **AdventureWorks2**。</span><span class="sxs-lookup"><span data-stu-id="f093c-171">In the screenshot below, the availability group listener is **AdventureWorks2**.</span></span>  
  
     <span data-ttu-id="f093c-172">![Management Studio 中的 AlwaysOn 可用性群組資料夾](../../media/ssas-alwaysoninfoinssms.png "Management Studio 中的 AlwaysOn 可用性群組資料夾")</span><span class="sxs-lookup"><span data-stu-id="f093c-172">![AlwaysOn Availability folder in Management Studio](../../media/ssas-alwaysoninfoinssms.png "AlwaysOn Availability folder in Management Studio")</span></span>  
  
4.  <span data-ttu-id="f093c-173">同樣在 [連接管理員] 中，按一下左邊功能窗格中的 **[全部]** ，以檢視資料提供者的屬性方格。</span><span class="sxs-lookup"><span data-stu-id="f093c-173">Still in Connection Manager, click **All** in the left navigation pane to view the property grid of data provider.</span></span>  
  
     <span data-ttu-id="f093c-174">如果將唯讀用戶端連線設定為次要複本，請將 [應用程式的意圖]\*\*\*\* 設為 [READONLY]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f093c-174">Set **Application Intent** to **READONLY** if you are configuring a read-only client connection to a secondary replica.</span></span> <span data-ttu-id="f093c-175">否則，請保留 **[READWRITE]** 預設值，將連接重新導向至主要複本。</span><span class="sxs-lookup"><span data-stu-id="f093c-175">Otherwise, keep the **READWRITE** default to redirect the connection to the primary replica.</span></span>  
  
5.  <span data-ttu-id="f093c-176">在 [模擬資訊] 中，選取 [使用特定的 Windows 使用者名稱和密碼]\*\*\*\*，然後輸入至少具有資料庫之 **db_datareader** 權限的 Windows 網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="f093c-176">In Impersonation Information, select **Use a specific Windows user name and password**, and then enter a Windows domain user account that has a minimum of **db_datareader** permissions on the database.</span></span>  
  
     <span data-ttu-id="f093c-177">請勿選擇 **[使用目前使用者的認證]** 或 **[繼承]**。</span><span class="sxs-lookup"><span data-stu-id="f093c-177">Do not choose **Use the credentials of the current user** or **Inherit**.</span></span> <span data-ttu-id="f093c-178">您可以選擇 **[使用服務帳戶]**，但是該帳戶必須具有資料庫的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="f093c-178">You can choose **Use the service account**, but only if that account has read permissions on the database.</span></span>  
  
     <span data-ttu-id="f093c-179">完成資料來源並關閉 [資料來源精靈]。</span><span class="sxs-lookup"><span data-stu-id="f093c-179">Finish the data source and close the Data Source Wizard.</span></span>  
  
6.  <span data-ttu-id="f093c-180">將 **MultiSubnetFailover=Yes** 加入連接字串，以提供更快的使用中伺服器偵測及連線。</span><span class="sxs-lookup"><span data-stu-id="f093c-180">Add **MultiSubnetFailover=Yes** to the connection string to provide faster detection and connection to the active server.</span></span> <span data-ttu-id="f093c-181">如需有關這個屬性的詳細資訊，請參閱＜ [高可用性/災害復原的 SQL Server Native Client 支援](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)＞。</span><span class="sxs-lookup"><span data-stu-id="f093c-181">For more information about this property, see [SQL Server Native Client Support for High Availability, Disaster Recovery](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).</span></span>  
  
     <span data-ttu-id="f093c-182">這個屬性不會在屬性方格中顯示。</span><span class="sxs-lookup"><span data-stu-id="f093c-182">This property is not visible in the property grid.</span></span> <span data-ttu-id="f093c-183">若要新增屬性，請以滑鼠右鍵按一下資料來源，然後選擇 [檢視程式碼]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f093c-183">To add the property, right-click the data source and choose **View Code**.</span></span> <span data-ttu-id="f093c-184">將 `MultiSubnetFailover=Yes` 新增至連接字串。</span><span class="sxs-lookup"><span data-stu-id="f093c-184">Add `MultiSubnetFailover=Yes` to the connection string.</span></span>  
  
 <span data-ttu-id="f093c-185">現在您已經定義資料來源。</span><span class="sxs-lookup"><span data-stu-id="f093c-185">The data source is now defined.</span></span> <span data-ttu-id="f093c-186">您可以接著繼續建立模型，請從資料來源檢視開始，或在表格式模型中建立關聯性。</span><span class="sxs-lookup"><span data-stu-id="f093c-186">You can now proceed to build a model, starting with the data source view, or in the case of tabular models, creating relationships.</span></span> <span data-ttu-id="f093c-187">如果您必須從可用性資料庫擷取資料 (例如在您準備處理或部署解決方案時)，您可以測試組態，確認可從次要複本存取資料。</span><span class="sxs-lookup"><span data-stu-id="f093c-187">When you are at a point where data must be retrieved from the availability database (for example when you are ready to process or deploy the solution), you can test the configuration to verify data is accessed from the secondary replica.</span></span>  
  
##  <a name="test-the-configuration"></a><a name="bkmk_test"></a><span data-ttu-id="f093c-188">測試設定</span><span class="sxs-lookup"><span data-stu-id="f093c-188">Test the configuration</span></span>  
 <span data-ttu-id="f093c-189">在您設定次要複本並在 Analysis Services 中建立資料來源連接之後，即可確認處理及查詢命令是否已重新導向至次要複本。</span><span class="sxs-lookup"><span data-stu-id="f093c-189">After you configure the secondary replica and create a data source connection in Analysis Services, you can confirm that processing and query commands are redirected to the secondary replica.</span></span> <span data-ttu-id="f093c-190">您也可以執行規劃的手動容錯移轉，以確認這個案例的復原計劃。</span><span class="sxs-lookup"><span data-stu-id="f093c-190">You can also perform a planned manual failover to verify your recovery plan for this scenario.</span></span>  
  
#### <a name="step-1-confirm-the-data-source-connection-is-redirected-to-the-secondary-replica"></a><span data-ttu-id="f093c-191">步驟 1：確認資料來源連接已重新導向至次要複本</span><span class="sxs-lookup"><span data-stu-id="f093c-191">Step 1: Confirm the data source connection is redirected to the secondary replica</span></span>  
  
1.  <span data-ttu-id="f093c-192">啟動 SQL Server Profiler 並連接至裝載次要複本的 SQL Server 執行個體。</span><span class="sxs-lookup"><span data-stu-id="f093c-192">Start SQL Server Profiler and connect to the SQL Server instance hosting the secondary replica.</span></span>  
  
     <span data-ttu-id="f093c-193">執行追蹤時，`SQL:BatchStarting` 和 `SQL:BatchCompleting` 事件會顯示 Analysis Services 所發出、在資料庫引擎執行個體上執行的查詢。</span><span class="sxs-lookup"><span data-stu-id="f093c-193">As the trace runs, the `SQL:BatchStarting` and `SQL:BatchCompleting` events will show the queries issued from Analysis Services that are executing on the database engine instance.</span></span> <span data-ttu-id="f093c-194">預設會選取這些事件，因此您只需要啟動追蹤。</span><span class="sxs-lookup"><span data-stu-id="f093c-194">These events are selected by default so all you need to do is start the trace.</span></span>  
  
2.  <span data-ttu-id="f093c-195">在 [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)]中，開啟包含您要測試之資料來源連接的 Analysis Services 專案或解決方案。</span><span class="sxs-lookup"><span data-stu-id="f093c-195">In [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)], open the Analysis Services project or solution containing a data source connection you want to test.</span></span> <span data-ttu-id="f093c-196">確定資料來源指定可用性群組接聽程式，而不是群組中的執行個體。</span><span class="sxs-lookup"><span data-stu-id="f093c-196">Be sure that the data source specifies the availability group listener and not an instance in the group.</span></span>  
  
     <span data-ttu-id="f093c-197">此步驟很重要。</span><span class="sxs-lookup"><span data-stu-id="f093c-197">This step is important.</span></span> <span data-ttu-id="f093c-198">如果指定伺服器執行個體名稱，則不會路由至次要複本。</span><span class="sxs-lookup"><span data-stu-id="f093c-198">Routing to the secondary replica will not occur if you specify a server instance name.</span></span>  
  
3.  <span data-ttu-id="f093c-199">排列應用程式視窗，以並排檢視 SQL Server Profiler 和 [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f093c-199">Arrange the application windows so that you can view SQL Server Profiler and [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)] side by side.</span></span>  
  
4.  <span data-ttu-id="f093c-200">部署解決方案，並在完成時停止追蹤。</span><span class="sxs-lookup"><span data-stu-id="f093c-200">Deploy the solution, and when it completes, stop the trace.</span></span>  
  
     <span data-ttu-id="f093c-201">在追蹤視窗中，您應該會看到 **Microsoft SQL Server Analysis Services**應用程式中的事件。</span><span class="sxs-lookup"><span data-stu-id="f093c-201">In the trace window, you should see events from the application **Microsoft SQL Server Analysis Services**.</span></span> <span data-ttu-id="f093c-202">您應該會看到 `SELECT` 陳述式從裝載次要複本之伺服器執行個體上的資料庫擷取資料，證明透過接聽程式建立與次要複本的連接。</span><span class="sxs-lookup"><span data-stu-id="f093c-202">You should see `SELECT` statements that retrieve data from a database on the server instance that hosts the secondary replica, proving that the connection was made via the listener to the secondary replica.</span></span>  
  
#### <a name="step-2-perform-a-planned-failover-to-test-the-configuration"></a><span data-ttu-id="f093c-203">步驟 2：執行規劃的容錯移轉以測試組態</span><span class="sxs-lookup"><span data-stu-id="f093c-203">Step 2: Perform a planned failover to test the configuration</span></span>  
  
1.  <span data-ttu-id="f093c-204">在 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] 中檢查主要與次要複本，確定已將這兩個複本設定為同步認可模式，且這兩個複本最近已經過同步處理。</span><span class="sxs-lookup"><span data-stu-id="f093c-204">In [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] check the primary and secondary replicas to ensure that both are configured for synchronous-commit mode and are currently synchronized.</span></span>  
  
     <span data-ttu-id="f093c-205">下列步驟假設已將次要複本設定為同步認可。</span><span class="sxs-lookup"><span data-stu-id="f093c-205">The following steps assume a secondary replica is configured for synchronous commit.</span></span>  
  
     <span data-ttu-id="f093c-206">若要確認同步處理，請開啟裝載主要與次要複本之每個執行個體的連線，請展開 [資料庫] 資料夾，並確定每個複本的資料庫名稱已附加 **(Synchronized)** 和 **(Synchronizing)**。</span><span class="sxs-lookup"><span data-stu-id="f093c-206">To verify synchronization, open a connection to each instance that hosts the primary and secondary replicas, expand the Databases folder, and ensure that the database has **(Synchronized)** and **(Synchronizing)** appended to its name in each replica.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f093c-207">這些步驟摘錄自[執行可用性群組的已規劃手動容錯移轉 &#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md)，文中提供執行這項工作的其他資訊和替代指示。</span><span class="sxs-lookup"><span data-stu-id="f093c-207">These steps are taken from [Perform a Planned Manual Failover of an Availability Group &#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md), which provides additional information and alternative instructions for performing this task.</span></span>  
  
2.  <span data-ttu-id="f093c-208">在 SQL Server Profiler 中，啟動每個複本的追蹤，以並排檢視追蹤。</span><span class="sxs-lookup"><span data-stu-id="f093c-208">In SQL Server Profiler, start traces for each replica and view the traces side-by-side.</span></span> <span data-ttu-id="f093c-209">在下列步驟中，您將比較追蹤，以確認從 Analysis Services 處理或查詢所使用的 SQL 查詢從其中一個複本切換至另一個複本。</span><span class="sxs-lookup"><span data-stu-id="f093c-209">In the following steps, you will compare traces, confirming that the SQL queries used for processing or querying from Analysis Services switch from one replica to the other.</span></span>  
  
3.  <span data-ttu-id="f093c-210">從 Analysis Services 執行處理或查詢命令。</span><span class="sxs-lookup"><span data-stu-id="f093c-210">Execute a processing or query command from within Analysis Services.</span></span> <span data-ttu-id="f093c-211">由於您已經設定唯讀連接的資料來源，因此您應該會看到這個命令在次要複本上執行。</span><span class="sxs-lookup"><span data-stu-id="f093c-211">Because you configured the data source for a read-only connection, you should see the command execute on the secondary replica.</span></span>  
  
4.  <span data-ttu-id="f093c-212">在 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] 中，連接至次要複本。</span><span class="sxs-lookup"><span data-stu-id="f093c-212">In [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], connect to the secondary replica.</span></span>  
  
5.  <span data-ttu-id="f093c-213">依序展開 **[AlwaysOn 高可用性]** 節點和 **[可用性群組]** 節點。</span><span class="sxs-lookup"><span data-stu-id="f093c-213">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
6.  <span data-ttu-id="f093c-214">以滑鼠右鍵按一下要容錯移轉的可用性群組，然後選取 [容錯移轉]  命令。</span><span class="sxs-lookup"><span data-stu-id="f093c-214">Right-click the availability group to be failed over, and select the **Failover** command.</span></span> <span data-ttu-id="f093c-215">這會啟動 [容錯移轉可用性群組精靈]。</span><span class="sxs-lookup"><span data-stu-id="f093c-215">This starts the Fail Over Availability Group Wizard.</span></span> <span data-ttu-id="f093c-216">使用精靈選擇複本，以做為新的主要複本。</span><span class="sxs-lookup"><span data-stu-id="f093c-216">Use the wizard to choose which replica to make the new primary replica.</span></span>  
  
7.  <span data-ttu-id="f093c-217">確認容錯移轉成功：</span><span class="sxs-lookup"><span data-stu-id="f093c-217">Confirm that failover succeeded:</span></span>  
  
    -   <span data-ttu-id="f093c-218">在 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]中，展開可用性群組以檢視 (主要) 與 (次要) 指定。</span><span class="sxs-lookup"><span data-stu-id="f093c-218">In [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], expand the availability groups to view the (primary) and (secondary) designations.</span></span> <span data-ttu-id="f093c-219">之前為主要複本的執行個體現在會變成次要複本。</span><span class="sxs-lookup"><span data-stu-id="f093c-219">The instance that was previously a primary replica should now be a secondary replica.</span></span>  
  
    -   <span data-ttu-id="f093c-220">檢視儀表板以判斷是否偵測到任何健全狀況問題。</span><span class="sxs-lookup"><span data-stu-id="f093c-220">View the dashboard to determine if any health issues were detected.</span></span> <span data-ttu-id="f093c-221">以滑鼠右鍵按一下可用性群組，然後選取 [顯示儀表板]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f093c-221">Right-click the availability group and select **Show Dashboard**.</span></span>  
  
8.  <span data-ttu-id="f093c-222">等候一到兩分鐘，在後端完成容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="f093c-222">Wait one or two minutes for the failover to complete on the backend.</span></span>  
  
9. <span data-ttu-id="f093c-223">重複 Analysis Services 解決方案中的處理或查詢命令，然後在 SQL Server Profiler 中並排檢視追蹤。</span><span class="sxs-lookup"><span data-stu-id="f093c-223">Repeat the processing or query command in the Analysis Services solution, and then watch the traces side by side in SQL Server Profiler.</span></span> <span data-ttu-id="f093c-224">您應該會看到執行處理的其他執行個體現在成為新的次要複本。</span><span class="sxs-lookup"><span data-stu-id="f093c-224">You should see evidence of processing on the other instance, which is now the new secondary replica.</span></span>  
  
##  <a name="what-happens-after-a-failover-occurs"></a><a name="bkmk_whathappens"></a><span data-ttu-id="f093c-225">容錯移轉之後會發生什麼事</span><span class="sxs-lookup"><span data-stu-id="f093c-225">What happens after a failover occurs</span></span>  
 <span data-ttu-id="f093c-226">在容錯移轉期間，次要複本會轉換到主要角色，而先前的主要複本會轉換到次要角色。</span><span class="sxs-lookup"><span data-stu-id="f093c-226">During a failover, a secondary replica transitions to the primary role and the former primary replica transitions to the secondary role.</span></span> <span data-ttu-id="f093c-227">所有用戶端連線會終止，可用性群組接聽程式的擁有權會隨主要複本角色移至新的 SQL Server 執行個體，且接聽程式端點會繫結到新執行個體的虛擬 IP 位址和 TCP 連接埠。</span><span class="sxs-lookup"><span data-stu-id="f093c-227">All client connections are terminated, ownership of the availability group listener moves with the primary replica role to a new SQL Server instance, and the listener endpoint is bound to the new instance's virtual IP addresses and TCP ports.</span></span> <span data-ttu-id="f093c-228">如需詳細資訊，請參閱本主題稍後的 [關於可用性複本的用戶端連接存取 &#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md))。</span><span class="sxs-lookup"><span data-stu-id="f093c-228">For more information, see [About Client Connection Access to Availability Replicas &#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md).</span></span>  
  
 <span data-ttu-id="f093c-229">如果在處理期間發生容錯移轉，Analysis Services 的記錄檔或輸出視窗中會發生下列錯誤：「OLE DB 錯誤: OLE DB 或 ODBC 錯誤: 通訊連結失敗; 08S01; TPC 提供者: 遠端主機已強制關閉一個現有連線。</span><span class="sxs-lookup"><span data-stu-id="f093c-229">If failover occurs during processing, the following error occurs in Analysis Services in the log file or output window: "OLE DB error: OLE DB or ODBC error: Communication link failure; 08S01; TPC Provider: An existing connection was forcibly closed by the remote host.</span></span> <span data-ttu-id="f093c-230">; 08S01。」</span><span class="sxs-lookup"><span data-stu-id="f093c-230">; 08S01."</span></span>  
  
 <span data-ttu-id="f093c-231">如果您稍候幾分鐘再試一次，應該可以解決這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="f093c-231">This error should resolve if you wait a minute and try again.</span></span> <span data-ttu-id="f093c-232">如果將可用性群組正確設定為可讀取的次要複本，當您重試處理時，會繼續在新的次要複本上處理。</span><span class="sxs-lookup"><span data-stu-id="f093c-232">If the availability group is configured correctly for readable secondary replica, processing will resume on the new secondary replica when you retry processing.</span></span>  
  
 <span data-ttu-id="f093c-233">持續性錯誤的主要原因可能是組態問題。</span><span class="sxs-lookup"><span data-stu-id="f093c-233">Persistent errors are most likely due to a configuration problem.</span></span> <span data-ttu-id="f093c-234">您可以嘗試重新執行 T-SQL 指令碼，解決次要複本上的路由清單、唯讀路由 URL 及讀取意圖的問題。</span><span class="sxs-lookup"><span data-stu-id="f093c-234">You can try re-running the T-SQL script to resolve problems with the routing list, read-only routing URLs, and read-intent on the secondary replica.</span></span> <span data-ttu-id="f093c-235">您也應該確認主要複本允許所有連接。</span><span class="sxs-lookup"><span data-stu-id="f093c-235">You should also verify that the primary replica allows all connections.</span></span>  
  
##  <a name="writeback-when-using-an-alwayson-availability-database"></a><a name="bkmk_writeback"></a><span data-ttu-id="f093c-236">使用 AlwaysOn 可用性資料庫時回寫</span><span class="sxs-lookup"><span data-stu-id="f093c-236">Writeback when using an AlwaysOn availability database</span></span>  
 <span data-ttu-id="f093c-237">回寫是 Analysis Services 功能，支援 Excel 的假設分析。</span><span class="sxs-lookup"><span data-stu-id="f093c-237">Writeback is an Analysis Services feature that supports What If analysis in Excel.</span></span> <span data-ttu-id="f093c-238">這項功能也常用於自訂應用程式中的預算和預測工作。</span><span class="sxs-lookup"><span data-stu-id="f093c-238">It is also commonly used for budgeting and forecasting tasks in custom applications.</span></span>  
  
 <span data-ttu-id="f093c-239">回寫支援需要 READWRITE 用戶端連接。</span><span class="sxs-lookup"><span data-stu-id="f093c-239">Support for writeback requires a READWRITE client connection.</span></span> <span data-ttu-id="f093c-240">在 Excel 中，如果您嘗試在唯讀連線上回寫，會發生下列錯誤：「無法從外部資料來源擷取資料。」</span><span class="sxs-lookup"><span data-stu-id="f093c-240">In Excel, if you attempt to write back on a read-only connection, the following error will occur: "Data could not be retrieved from the external data source."</span></span> <span data-ttu-id="f093c-241">「無法從外部資料來源擷取資料。」</span><span class="sxs-lookup"><span data-stu-id="f093c-241">"Data could not be retrieved from the external data source."</span></span>  
  
 <span data-ttu-id="f093c-242">如果設定連接一律存取可讀取的次要複本，現在就必須設定使用主要複本之 READWRITE 連接的新連接。</span><span class="sxs-lookup"><span data-stu-id="f093c-242">If you configured a connection to always access a readable secondary replica, you must now configure a new connection that uses a READWRITE connection to the primary replica.</span></span>  
  
 <span data-ttu-id="f093c-243">若要執行這項操作，請在 Analysis Services 模型中建立其他資料來源，以支援讀寫連接。</span><span class="sxs-lookup"><span data-stu-id="f093c-243">To do this, create an additional data source in an Analysis Services model to support the read-write connection.</span></span> <span data-ttu-id="f093c-244">建立其他資料來源時，請使用您在唯讀連線中指定的相同接聽程式名稱和資料庫，但不要修改 [應用程式的意圖]\*\*\*\*，保留支援 READWRITE 連線的預設值。</span><span class="sxs-lookup"><span data-stu-id="f093c-244">When creating the additional data source, use the same listener name and database that you specified in the read-only connection, but instead of modifying **Application Intent**, keep the default that supports READWRITE connections.</span></span> <span data-ttu-id="f093c-245">您現在可以將以讀寫資料來源為基礎的新事實或維度資料表新增至資料來源檢視，然後啟用新資料表的回寫功能。</span><span class="sxs-lookup"><span data-stu-id="f093c-245">You can now add new fact or dimension tables to your data source view that are based on the read-write data source, and then enable writeback on the new tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f093c-246">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f093c-246">See Also</span></span>  
 <span data-ttu-id="f093c-247">[可用性群組接聽程式、用戶端連接性及應用程式容錯移轉 &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span><span class="sxs-lookup"><span data-stu-id="f093c-247">[Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span></span>  
 <span data-ttu-id="f093c-248">[使用中次要：可讀取的次要複本 &#40;AlwaysOn 可用性群組&#41;](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="f093c-248">[Active Secondaries: Readable Secondary Replicas &#40;AlwaysOn Availability Groups&#41;](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) </span></span>  
 <span data-ttu-id="f093c-249">[AlwaysOn 可用性群組 &#40;SQL Server 的操作問題 AlwaysOn 原則&#41;](always-on-policies-for-operational-issues-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="f093c-249">[AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups &#40;SQL Server&#41;](always-on-policies-for-operational-issues-always-on-availability.md) </span></span>  
 <span data-ttu-id="f093c-250">[建立 &#40;SSAS 多維度&#41;的資料來源](https://docs.microsoft.com/analysis-services/multidimensional-models/create-a-data-source-ssas-multidimensional) </span><span class="sxs-lookup"><span data-stu-id="f093c-250">[Create a Data Source &#40;SSAS Multidimensional&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/create-a-data-source-ssas-multidimensional) </span></span>  
 <span data-ttu-id="f093c-251">[[啟用維度回寫]](https://docs.microsoft.com/analysis-services/multidimensional-models/bi-wizard-enable-dimension-writeback)</span><span class="sxs-lookup"><span data-stu-id="f093c-251">[Enable Dimension Writeback](https://docs.microsoft.com/analysis-services/multidimensional-models/bi-wizard-enable-dimension-writeback)</span></span>  
  
  
