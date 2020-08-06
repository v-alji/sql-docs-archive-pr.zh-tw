---
title: 使用 AlwaysOn 原則來查看可用性群組的健全狀況 (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 6f1bcbc3-1220-4071-8e53-4b957f5d3089
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5c4444afc2348b2407dc19c1c12761ef0251631e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708622"
---
# <a name="use-alwayson-policies-to-view-the-health-of-an-availability-group-sql-server"></a><span data-ttu-id="b6dd9-102">使用 AlwaysOn 原則檢視可用性群組的健全狀況 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b6dd9-102">Use AlwaysOn Policies to View the Health of an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="b6dd9-103">此主題描述如何使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 中的 AlwaysOn 原則或 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]中的 PowerShell，判斷 AlwaysOn 可用性群組的作業健全狀況。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-103">This topic describes how to determine the operational health of an AlwaysOn availability group by using an AlwaysOn policy in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="b6dd9-104">如需 AlwaysOn 原則式管理的詳細資訊，請參閱[AlwaysOn 可用性群組 (SQL Server) 操作問題的 AlwaysOn 原則](always-on-policies-for-operational-issues-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-104">For information about AlwaysOn Policy Based Management, see [AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b6dd9-105">對於 AlwaysOn 原則，類別目錄名稱會做為識別碼。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-105">For AlwaysOn policies, the category names are used as IDs.</span></span> <span data-ttu-id="b6dd9-106">變更 AlwaysOn 類別目錄的名稱會破壞其健全狀況評估功能。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-106">Changing the name of an AlwaysOn category would break its health-evaluation functionality.</span></span> <span data-ttu-id="b6dd9-107">因此，永遠不應修改 AlwaysOn 類別目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-107">Therefore, the names of AlwaysOn category should never be modified.</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b6dd9-108">開始之前</span><span class="sxs-lookup"><span data-stu-id="b6dd9-108">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b6dd9-109">Security</span><span class="sxs-lookup"><span data-stu-id="b6dd9-109">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b6dd9-110">權限</span><span class="sxs-lookup"><span data-stu-id="b6dd9-110">Permissions</span></span>  
 <span data-ttu-id="b6dd9-111">需要 CONNECT、VIEW SERVER STATE 和 VIEW ANY DEFINITION 權限。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-111">Requires CONNECT, VIEW SERVER STATE, and VIEW ANY DEFINITION permissions.</span></span>  
  
##  <a name="using-the-alwayson-dashboard"></a><a name="SSMSProcedure"></a><span data-ttu-id="b6dd9-112">使用 AlwaysOn 儀表板</span><span class="sxs-lookup"><span data-stu-id="b6dd9-112">Using the AlwaysOn Dashboard</span></span>  
 <span data-ttu-id="b6dd9-113">**若要開啟 AlwaysOn 儀表板**</span><span class="sxs-lookup"><span data-stu-id="b6dd9-113">**To open the AlwaysOn Dashboard**</span></span>  
  
1.  <span data-ttu-id="b6dd9-114">在 [物件總管] 中，連接到裝載其中一個可用性複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-114">In Object Explorer, connect to the server instance that hosts one of the availability replicas.</span></span> <span data-ttu-id="b6dd9-115">若要檢視可用性群組中所有可用性複本的相關資訊，請用於裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-115">To view information about all of the availability replicas in an availability group, use to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="b6dd9-116">按一下伺服器名稱展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-116">Click the server name to expand the server tree.</span></span>  
  
3.  <span data-ttu-id="b6dd9-117">展開 **[AlwaysOn 高可用性]** 節點。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-117">Expand the **AlwaysOn High Availability** node.</span></span>  
  
     <span data-ttu-id="b6dd9-118">以滑鼠右鍵按一下 [可用性群組]\*\*\*\* 節點，或展開此節點，然後以滑鼠右鍵按一下特定的可用性群組。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-118">Either right-click the **Availability Groups** node or expand this node and right-click a specific availability group.</span></span>  
  
4.  <span data-ttu-id="b6dd9-119">選取 **[顯示儀表板]** 命令。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-119">Select the **Show Dashboard** command.</span></span>  
  
 <span data-ttu-id="b6dd9-120">如需如何使用 AlwaysOn 儀表板的相關資訊，請參閱[使用 AlwaysOn 儀表板 &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-120">For information about how to use the AlwaysOn Dashboard, see [Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md).</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="b6dd9-121">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b6dd9-121">Using PowerShell</span></span>  
 <span data-ttu-id="b6dd9-122">**使用 AlwaysOn 原則來查看可用性群組的健全狀況**</span><span class="sxs-lookup"><span data-stu-id="b6dd9-122">**Use AlwaysOn policies to view the health of an availability group**</span></span>  
  
1.  <span data-ttu-id="b6dd9-123">將目錄切換到 (`cd`) 裝載其中一個可用性複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-123">Set default (`cd`) to a server instance that hosts one of the availability replicas.</span></span> <span data-ttu-id="b6dd9-124">若要檢視可用性群組中所有可用性複本的相關資訊，請用於裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-124">To view information about all of the availability replicas in an availability group, use to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="b6dd9-125">使用下列 Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="b6dd9-125">Use the following cmdlets:</span></span>  
  
     `Test-SqlAvailabilityGroup`  
     <span data-ttu-id="b6dd9-126">透過評估 SQL Server 原則式管理 (PBM) 原則，評估可用性群組的健全狀況。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-126">Assesses the health of an availability group by evaluating SQL Server policy based management (PBM) policies.</span></span> <span data-ttu-id="b6dd9-127">您必須擁有 CONNECT、VIEW SERVER STATE 和 VIEW ANY DEFINITION 權限，才能執行這個 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-127">You must have CONNECT, VIEW SERVER STATE, and VIEW ANY DEFINITION permissions to execute this cmdlet.</span></span>  
  
     <span data-ttu-id="b6dd9-128">例如，下列命令會顯示伺服器執行個體 `Computer\Instance`上健全狀態為 "Error" 的所有可用性群組。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-128">For example, the following command shows all availability groups with a health state of "Error" on the server instance `Computer\Instance`.</span></span>  
  
    ```powershell
    Get-ChildItem SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups |
        Test-SqlAvailabilityGroup |
        Where-Object { $_.HealthState -eq "Error" }  
    ```  
  
     `Test-SqlAvailabilityReplica`  
     <span data-ttu-id="b6dd9-129">透過評估 SQL Server 原則式管理 (PBM) 原則，評估可用性複本的健全狀況。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-129">Assesses the health of availability replicas by evaluating SQL Server policy based management (PBM) policies.</span></span> <span data-ttu-id="b6dd9-130">您必須擁有 CONNECT、VIEW SERVER STATE 和 VIEW ANY DEFINITION 權限，才能執行這個 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-130">You must have CONNECT, VIEW SERVER STATE, and VIEW ANY DEFINITION permissions to execute this cmdlet.</span></span>  
  
     <span data-ttu-id="b6dd9-131">例如，下列命令會評估可用性群組 `MyReplica` 中名為 `MyAg` 之可用性複本的健全狀況並且輸出簡短摘要。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-131">For example, the following command evaluates the health of the availability replica named `MyReplica` in the availability group `MyAg` and outputs a brief summary.</span></span>  
  
    ```powershell
    Test-SqlAvailabilityReplica -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
     `Test-SqlDatabaseReplicaState`  
     <span data-ttu-id="b6dd9-132">透過評估 SQL Server 原則式管理 (PBM) 原則，評估所有聯結可用性複本之可用性資料庫的健全狀況。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-132">Assesses the health of an availability database on all joined availability replicas by evaluating SQL Server policy based management (PBM) policies.</span></span>  
  
     <span data-ttu-id="b6dd9-133">例如，下列命令會評估可用性群組 `MyAg` 中所有可用性資料庫的健全狀況並且輸出每個資料庫的簡短摘要。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-133">For example, the following command evaluates the health of all availability databases in the availability group `MyAg` and outputs a brief summary for each database.</span></span>  
  
    ```powershell
    Get-ChildItem SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\DatabaseReplicaStates |
        Test-SqlDatabaseReplicaState  
    ```  
  
     <span data-ttu-id="b6dd9-134">這些指令程式接受下列選項：</span><span class="sxs-lookup"><span data-stu-id="b6dd9-134">These cmdlets accept the following options:</span></span>  
  
    |<span data-ttu-id="b6dd9-135">選項</span><span class="sxs-lookup"><span data-stu-id="b6dd9-135">Option</span></span>|<span data-ttu-id="b6dd9-136">描述</span><span class="sxs-lookup"><span data-stu-id="b6dd9-136">Description</span></span>|  
    |------------|-----------------|  
    |`AllowUserPolicies`|<span data-ttu-id="b6dd9-137">執行 AlwaysOn 原則類別目錄中的使用者原則。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-137">Runs user policies found in the AlwaysOn policy categories.</span></span>|  
    |`InputObject`|<span data-ttu-id="b6dd9-138">表示可用性群組、可用性複本或可用性資料庫狀態的物件集合 (依據使用的指令程式而定)。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-138">A collection of objects that, represent availability groups, availability replicas, or availability database states (depending on which cmdlet you are using).</span></span> <span data-ttu-id="b6dd9-139">指令程式會計算指定之物件的健全狀況。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-139">The cmdlet will compute the health of the specified objects.</span></span>|  
    |`NoRefresh`|<span data-ttu-id="b6dd9-140">設定此參數時，指令程式不會手動重新整理 `-Path` 或 `-InputObject` 參數所指定的物件。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-140">When this parameter is set, the cmdlet will not manually refresh the objects specified by the `-Path` or `-InputObject` parameter.</span></span>|  
    |`Path`|<span data-ttu-id="b6dd9-141">可用性群組、一個或多個可用性複本，或可用性資料庫之資料庫複本叢集狀態的路徑 (依據使用的指令程式而定)。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-141">The path to the availability group, one or more availability replicas, or database replica cluster state of the availability database (depending on which cmdlet you are using).</span></span> <span data-ttu-id="b6dd9-142">這是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-142">This is an optional parameter.</span></span> <span data-ttu-id="b6dd9-143">如果未指定，此參數的值預設為目前的工作位置。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-143">If not specified, the value of this parameter defaults to the current working location.</span></span>|  
    |`ShowPolicyDetails`|<span data-ttu-id="b6dd9-144">顯示此 Cmdlet 執行之各項原則評估的結果。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-144">Shows the result of each policy evaluation performed by this cmdlet.</span></span> <span data-ttu-id="b6dd9-145">Cmdlet 針對每項原則評估輸出一個物件，此物件的欄位描述評估結果 (原則通過或失敗、原則名稱和類別目錄等等)。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-145">The cmdlet outputs one object per policy evaluation, and this object has fields describing the results of evaluation (whether the policy passed or not, the policy name and category, and so forth).</span></span>|  
  
     <span data-ttu-id="b6dd9-146">例如，下列 `Test-SqlAvailabilityGroup` 命令會指定 `-ShowPolicyDetails` 參數，針對在可用性群組 `MyAg` 上執行的每個原則式管理 (PBM) 原則，顯示此指令程式執行的每個原則評估結果。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-146">For example, the following `Test-SqlAvailabilityGroup` command specifies the `-ShowPolicyDetails` parameter to show the result of each policy evaluation performed by this cmdlet for each policy-based management (PBM) policy that was executed on the availability group named `MyAg`.</span></span>  
  
    ```powershell
    Test-SqlAvailabilityGroup -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\AgName -ShowPolicyDetails  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="b6dd9-147">若要檢視指令程式的語法，請在 `Get-Help` PowerShell 環境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 指令程式。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-147">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="b6dd9-148">如需詳細資訊，請參閱 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="b6dd9-148">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="b6dd9-149">**若要設定和使用 SQL Server PowerShell 提供者**</span><span class="sxs-lookup"><span data-stu-id="b6dd9-149">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="b6dd9-150">SQL Server PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="b6dd9-150">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
-   [<span data-ttu-id="b6dd9-151">Get Help SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="b6dd9-151">Get Help SQL Server PowerShell</span></span>](../../../powershell/sql-server-powershell.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="b6dd9-152">相關內容</span><span class="sxs-lookup"><span data-stu-id="b6dd9-152">Related Content</span></span>  
 <span data-ttu-id="b6dd9-153">**SQL Server AlwaysOn Team Blog-使用 PowerShell 監視 AlwaysOn 健全狀況：**</span><span class="sxs-lookup"><span data-stu-id="b6dd9-153">**SQL Server AlwaysOn Team Blogs-Monitoring AlwaysOn Health with PowerShell:**</span></span>  
  
-   [<span data-ttu-id="b6dd9-154">第 1 部：基本指令程式概觀</span><span class="sxs-lookup"><span data-stu-id="b6dd9-154">Part 1: Basic Cmdlet Overview</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/monitoring-alwayson-health-with-powershell-part-1-basic-cmdlet-overview)  
  
-   [<span data-ttu-id="b6dd9-155">第 2 部：進階指令程式使用</span><span class="sxs-lookup"><span data-stu-id="b6dd9-155">Part 2: Advanced Cmdlet Usage</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/the-alwayson-health-model-part-2-extending-the-health-model)  
  
-   [<span data-ttu-id="b6dd9-156">第 3 部：簡單監控應用程式</span><span class="sxs-lookup"><span data-stu-id="b6dd9-156">Part 3: A Simple Monitoring Application</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/monitoring-alwayson-health-with-powershell-part-3-a-simple-monitoring-application)  
  
-   [<span data-ttu-id="b6dd9-157">第 4 部：與 SQL Server Agent 整合</span><span class="sxs-lookup"><span data-stu-id="b6dd9-157">Part 4: Integration with SQL Server Agent</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/monitoring-alwayson-health-with-powershell-part-4-integration-with-sql-server-agent)  
  
## <a name="see-also"></a><span data-ttu-id="b6dd9-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6dd9-158">See Also</span></span>  
 <span data-ttu-id="b6dd9-159">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b6dd9-159">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="b6dd9-160">[管理可用性群組 &#40;SQL Server&#41;](administration-of-an-availability-group-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b6dd9-160">[Administration of an Availability Group &#40;SQL Server&#41;](administration-of-an-availability-group-sql-server.md) </span></span>  
 <span data-ttu-id="b6dd9-161">[監視可用性群組 &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b6dd9-161">[Monitoring of Availability Groups &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="b6dd9-162">AlwaysOn 可用性群組操作問題適用的 AlwaysOn 原則 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b6dd9-162">AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups (SQL Server)</span></span>](always-on-policies-for-operational-issues-always-on-availability.md) 
