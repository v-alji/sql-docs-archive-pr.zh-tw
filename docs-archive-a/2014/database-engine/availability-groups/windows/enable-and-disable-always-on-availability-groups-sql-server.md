---
title: 啟用和停用 AlwaysOn 可用性群組 (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], server instance
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], disabling
- Availability Groups [SQL Server], enabling
ms.assetid: 7c326958-5ae9-4761-9c57-905972276a8f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 585f1d86d328b7c5027241310108d102b56ca327
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592254"
---
# <a name="enable-and-disable-alwayson-availability-groups-sql-server"></a><span data-ttu-id="23e3b-102">啟用和停用 AlwaysOn 可用性群組 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="23e3b-102">Enable and Disable AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="23e3b-103">啟用 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 是伺服器執行個體使用可用性群組的必要條件。</span><span class="sxs-lookup"><span data-stu-id="23e3b-103">Enabling [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] is a prerequisite for a server instance to use availability groups.</span></span> <span data-ttu-id="23e3b-104">您必須在將要裝載一個或多個可用性群組之可用性複本的每個 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 執行個體上啟用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 功能，才能建立及設定任何可用性群組。</span><span class="sxs-lookup"><span data-stu-id="23e3b-104">Before you can create and configure any availability group, the [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] feature must have been enabled on the each instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that will host an availability replica for one or more availability groups.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="23e3b-105">如果您刪除然後重新建立 WSFC 叢集，則必須在原始 WSFC 叢集上裝載可用性複本的每個 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 執行個體，停用然後重新啟用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="23e3b-105">If you delete and re-create a WSFC cluster, you must disable and re-enable the [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] feature on each instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosted an availability replica on the original WSFC cluster.</span></span>  
  
-   <span data-ttu-id="23e3b-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="23e3b-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="23e3b-107">先決條件</span><span class="sxs-lookup"><span data-stu-id="23e3b-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="23e3b-108">安全性</span><span class="sxs-lookup"><span data-stu-id="23e3b-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="23e3b-109">**如何：**</span><span class="sxs-lookup"><span data-stu-id="23e3b-109">**How To:**</span></span>  
  
    -   [<span data-ttu-id="23e3b-110">判斷 AlwaysOn 可用性群組是否已啟用</span><span class="sxs-lookup"><span data-stu-id="23e3b-110">Determine Whether AlwaysOn Availability Groups is Enabled</span></span>](#IsEnabled)  
  
    -   [<span data-ttu-id="23e3b-111">啟用 AlwaysOn 可用性群組</span><span class="sxs-lookup"><span data-stu-id="23e3b-111">Enable AlwaysOn Availability Groups</span></span>](#EnableAOAG)  
  
    -   [<span data-ttu-id="23e3b-112">停用 AlwaysOn 可用性群組</span><span class="sxs-lookup"><span data-stu-id="23e3b-112">Disable AlwaysOn Availability Groups</span></span>](#DisableAOAG)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="23e3b-113">開始之前</span><span class="sxs-lookup"><span data-stu-id="23e3b-113">Before You Begin</span></span>  
  
###  <a name="prerequisites-for-enabling-alwayson-availability-groups"></a><a name="Prerequisites"></a><span data-ttu-id="23e3b-114">啟用 AlwaysOn 可用性群組的必要條件</span><span class="sxs-lookup"><span data-stu-id="23e3b-114">Prerequisites for Enabling AlwaysOn Availability Groups</span></span>  
  
-   <span data-ttu-id="23e3b-115">此伺服器執行個體必須位於 Windows Server 容錯移轉叢集 (WSFC) 節點上。</span><span class="sxs-lookup"><span data-stu-id="23e3b-115">The server instance must reside on a Windows Server Failover Clustering (WSFC) node.</span></span>  
  
-   <span data-ttu-id="23e3b-116">伺服器執行個體必須執行支援 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]的 SQL Server 版本。</span><span class="sxs-lookup"><span data-stu-id="23e3b-116">The server instance must be running an edition of SQL Server that supports [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].</span></span> <span data-ttu-id="23e3b-117">如需詳細資訊，請參閱＜ [Features Supported by the Editions of SQL Server 2014](../../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)＞。</span><span class="sxs-lookup"><span data-stu-id="23e3b-117">For more information, see [Features Supported by the Editions of SQL Server 2014](../../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
-   <span data-ttu-id="23e3b-118">一次只在一個伺服器執行個體啟用 AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="23e3b-118">Enable AlwaysOn Availability Groups on only one server instance at a time.</span></span> <span data-ttu-id="23e3b-119">啟用 AlwaysOn 可用性群組之後，等到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務重新啟動後才能在另一個伺服器執行個體繼續進行。</span><span class="sxs-lookup"><span data-stu-id="23e3b-119">After enabling AlwaysOn Availability Groups, wait until the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service has restarted before you proceed to another server instance.</span></span>  
  
 <span data-ttu-id="23e3b-120">如需建立和設定可用性群組之其他必要條件的詳細資訊，請參閱[AlwaysOn 可用性群組 &#40;SQL Server&#41;的必要條件、限制和建議](prereqs-restrictions-recommendations-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="23e3b-120">For information about additional prerequisites for creating and configuring availability groups, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="23e3b-121">Security</span><span class="sxs-lookup"><span data-stu-id="23e3b-121">Security</span></span>  
 <span data-ttu-id="23e3b-122">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]執行個體啟用 AlwaysOn 可用性群組之後，伺服器執行個體就會有 WSFC 叢集的完整控制。</span><span class="sxs-lookup"><span data-stu-id="23e3b-122">While AlwaysOn Availability Groups is enabled on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the server instance has full control on the WSFC cluster.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="23e3b-123">權限</span><span class="sxs-lookup"><span data-stu-id="23e3b-123">Permissions</span></span>  
 <span data-ttu-id="23e3b-124">需要本機電腦的 **Administrator** 群組成員資格和 WSFC 叢集的完整控制。</span><span class="sxs-lookup"><span data-stu-id="23e3b-124">Requires membership in the **Administrator** group on the local computer and full control on the WSFC cluster.</span></span> <span data-ttu-id="23e3b-125">透過使用 PowerShell 啟用 AlwaysOn 時，請使用 **[以系統管理員身分執行]** 選項開啟命令提示字元視窗。</span><span class="sxs-lookup"><span data-stu-id="23e3b-125">When enabling AlwaysOn by using PowerShell, open the Command Prompt window using the **Run as administrator** option.</span></span>  
  
 <span data-ttu-id="23e3b-126">需要 Active Directory 建立物件和管理物件權限。</span><span class="sxs-lookup"><span data-stu-id="23e3b-126">Requires Active Directory Create Objects and Manage Objects permissions.</span></span>  
  
##  <a name="determine-whether-alwayson-availability-groups-is-enabled"></a><a name="IsEnabled"></a><span data-ttu-id="23e3b-127">判斷是否已啟用 AlwaysOn 可用性群組</span><span class="sxs-lookup"><span data-stu-id="23e3b-127">Determine Whether AlwaysOn Availability Groups is Enabled</span></span>  
  
-   [<span data-ttu-id="23e3b-128">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="23e3b-128">SQL Server Management Studio</span></span>](#SSMS1Procedure)  
  
-   [<span data-ttu-id="23e3b-129">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="23e3b-129">Transact-SQL</span></span>](#Tsql1Procedure)  
  
-   [<span data-ttu-id="23e3b-130">PowerShell</span><span class="sxs-lookup"><span data-stu-id="23e3b-130">PowerShell</span></span>](#PowerShell1Procedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMS1Procedure"></a> <span data-ttu-id="23e3b-131">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="23e3b-131">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="23e3b-132">**判斷 AlwaysOn 可用性群組是否已啟用**</span><span class="sxs-lookup"><span data-stu-id="23e3b-132">**To determine whether AlwaysOn Availability Groups is enabled**</span></span>  
  
1.  <span data-ttu-id="23e3b-133">在物件總管中，以滑鼠右鍵按一下伺服器執行個體，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="23e3b-133">In Object Explorer, right-click the server instance, and  click **Properties**.</span></span>  
  
2.  <span data-ttu-id="23e3b-134">在 **[伺服器屬性]** 對話方塊中，按一下 **[一般]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="23e3b-134">In the **Server Properties** dialog box, click the **General** page.</span></span> <span data-ttu-id="23e3b-135">**[為已啟用 HADR]** 屬性會顯示下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="23e3b-135">The **Is HADR Enabled** property displays one of the following values:</span></span>  
  
    -   <span data-ttu-id="23e3b-136">如果 AlwaysOn 可用性群組已啟用，則為**True**</span><span class="sxs-lookup"><span data-stu-id="23e3b-136">**True**, if AlwaysOn Availability Groups is enabled</span></span>  
  
    -   <span data-ttu-id="23e3b-137">如果 AlwaysOn 可用性群組已停用，則為**False**</span><span class="sxs-lookup"><span data-stu-id="23e3b-137">**False**, if AlwaysOn Availability Groups is disabled.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="Tsql1Procedure"></a> <span data-ttu-id="23e3b-138">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="23e3b-138">Using Transact-SQL</span></span>  
 <span data-ttu-id="23e3b-139">**判斷 AlwaysOn 可用性群組是否已啟用**</span><span class="sxs-lookup"><span data-stu-id="23e3b-139">**To determine whether AlwaysOn Availability Groups is enabled**</span></span>  
  
1.  <span data-ttu-id="23e3b-140">使用下列 [SERVERPROPERTY](/sql/t-sql/functions/serverproperty-transact-sql) 陳述式：</span><span class="sxs-lookup"><span data-stu-id="23e3b-140">Use the following [SERVERPROPERTY](/sql/t-sql/functions/serverproperty-transact-sql) statement:</span></span>  
  
    ```sql
    SELECT SERVERPROPERTY ('IsHadrEnabled');  
    ```  
  
     <span data-ttu-id="23e3b-141">`IsHadrEnabled` 伺服器屬性設定會指出 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體是否已啟用 AlwaysOn 可用性群組，如下所示：</span><span class="sxs-lookup"><span data-stu-id="23e3b-141">The setting of the `IsHadrEnabled` server property indicates whether an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is enabled for AlwaysOn Availability Groups, as follows:</span></span>  
  
    -   <span data-ttu-id="23e3b-142">如果 `IsHadrEnabled` = 1，表示 AlwaysOn 可用性群組已啟用。</span><span class="sxs-lookup"><span data-stu-id="23e3b-142">If `IsHadrEnabled` = 1, AlwaysOn Availability Groups is enabled.</span></span>  
  
    -   <span data-ttu-id="23e3b-143">如果 `IsHadrEnabled` = 0，表示 AlwaysOn 可用性群組已停用。</span><span class="sxs-lookup"><span data-stu-id="23e3b-143">If `IsHadrEnabled` = 0, AlwaysOn Availability Groups is disabled.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="23e3b-144">如需伺服器屬性的詳細資訊 `IsHadrEnabled` ，請參閱[SERVERPROPERTY &#40;transact-sql&#41;](/sql/t-sql/functions/serverproperty-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="23e3b-144">For more information about the `IsHadrEnabled` server property, see [SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql).</span></span>  
  
###  <a name="using-powershell"></a><a name="PowerShell1Procedure"></a> <span data-ttu-id="23e3b-145">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="23e3b-145">Using PowerShell</span></span>  
 <span data-ttu-id="23e3b-146">**判斷 AlwaysOn 可用性群組是否已啟用**</span><span class="sxs-lookup"><span data-stu-id="23e3b-146">**To determine whether AlwaysOn Availability Groups is enabled**</span></span>  
  
1.  <span data-ttu-id="23e3b-147">將預設 (`cd`) 設定為伺服器實例 (例如 `\SQL\NODE1\DEFAULT` 您要判斷是否已啟用的) 。 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23e3b-147">Set default (`cd`) to the server instance (e.g. `\SQL\NODE1\DEFAULT`) on which you want to determine whether [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] is enabled.</span></span>  
  
2.  <span data-ttu-id="23e3b-148">輸入下列 PowerShell `Get-Item` 命令：</span><span class="sxs-lookup"><span data-stu-id="23e3b-148">Enter the following PowerShell `Get-Item` command:</span></span>  
  
    ```powershell
    Get-Item . | Select IsHadrEnabled  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="23e3b-149">若要檢視指令程式的語法，請在 `Get-Help` PowerShell 環境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 指令程式。</span><span class="sxs-lookup"><span data-stu-id="23e3b-149">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="23e3b-150">如需詳細資訊，請參閱 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="23e3b-150">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="23e3b-151">**若要設定和使用 SQL Server PowerShell 提供者**</span><span class="sxs-lookup"><span data-stu-id="23e3b-151">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="23e3b-152">SQL Server PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="23e3b-152">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="enable-alwayson-availability-groups"></a><a name="EnableAOAG"></a> <span data-ttu-id="23e3b-153">啟用 AlwaysOn 可用性群組</span><span class="sxs-lookup"><span data-stu-id="23e3b-153">Enable AlwaysOn Availability Groups</span></span>  
 <span data-ttu-id="23e3b-154">**若要啟用 AlwaysOn，請使用：**</span><span class="sxs-lookup"><span data-stu-id="23e3b-154">**To enable AlwaysOn, using:**</span></span>  
  
-   [<span data-ttu-id="23e3b-155">SQL Server 組態管理員</span><span class="sxs-lookup"><span data-stu-id="23e3b-155">SQL Server Configuration Manager</span></span>](#SQLCM2Procedure)  
  
-   [<span data-ttu-id="23e3b-156">PowerShell</span><span class="sxs-lookup"><span data-stu-id="23e3b-156">PowerShell</span></span>](#PScmd2Procedure)  
  
###  <a name="using-sql-server-configuration-manager"></a><a name="SQLCM2Procedure"></a> <span data-ttu-id="23e3b-157">使用 SQL Server 組態管理員</span><span class="sxs-lookup"><span data-stu-id="23e3b-157">Using SQL Server Configuration Manager</span></span>  
 <span data-ttu-id="23e3b-158">**若要啟用 AlwaysOn 可用性群組**</span><span class="sxs-lookup"><span data-stu-id="23e3b-158">**To enable AlwaysOn Availability Groups**</span></span>  
  
1.  <span data-ttu-id="23e3b-159">連接到 Windows Server 容錯移轉叢集 (WSFC) 節點，此節點裝載您要啟用 AlwaysOn 可用性群組的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="23e3b-159">Connect to the Windows Server Failover Clustering (WSFC) node that hosts the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance where you want to enable AlwaysOn Availability Groups.</span></span>  
  
2.  <span data-ttu-id="23e3b-160">指向 [開始]  功能表上的 [所有程式] ，然後依序指向 [ [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)]] 和 [組態工具] ，再按一下 [SQL Server 組態管理員] 。</span><span class="sxs-lookup"><span data-stu-id="23e3b-160">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and  click **SQL Server Configuration Manager**.</span></span>  
  
3.  <span data-ttu-id="23e3b-161">在**SQL Server 組態管理員**中，按一下 [ **SQL Server 服務**]，以滑鼠右鍵按一下 SQL Server (\*\* < *`instance name`*>) **]，其中 **<*`instance name`*>** 是您要啟用 AlwaysOn 可用性群組的本機伺服器實例名稱，然後按一下 [**屬性]。\*\*</span><span class="sxs-lookup"><span data-stu-id="23e3b-161">In **SQL Server Configuration Manager**, click **SQL Server Services**, right-click SQL Server (**<*`instance name`*>)**, where **<*`instance name`*>** is the name of a local server instance for which you want to enable AlwaysOn Availability Groups, and click **Properties.**</span></span>  
  
4.  <span data-ttu-id="23e3b-162">選取 **[AlwaysOn 高可用性]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="23e3b-162">Select the **AlwaysOn High Availability** tab.</span></span>  
  
5.  <span data-ttu-id="23e3b-163">確認 [Windows 容錯移轉叢集名稱] 欄位包含本機容錯移轉叢集的名稱。</span><span class="sxs-lookup"><span data-stu-id="23e3b-163">Verify that **Windows failover cluster name** field contains the name of the local failover cluster.</span></span> <span data-ttu-id="23e3b-164">如果此欄位為空白，表示此伺服器執行個體目前不支援 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="23e3b-164">If this field is blank, this server instance currently does not support [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].</span></span> <span data-ttu-id="23e3b-165">有可能本機電腦不是叢集節點，WSFC 叢集已經關閉，或者此版本 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 不支援 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="23e3b-165">Either the local computer is not a cluster node, the WSFC cluster has been shut down, or this edition of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] that does not support [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].</span></span>  
  
6.  <span data-ttu-id="23e3b-166">選取 [**啟用 AlwaysOn 可用性群組**] 核取方塊，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="23e3b-166">Select the **Enable AlwaysOn Availability Groups** check box, and click **OK**.</span></span>  
  
     [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="23e3b-167">組態管理員會儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="23e3b-167">Configuration Manager saves your change.</span></span> <span data-ttu-id="23e3b-168">然後您必須手動重新啟動 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="23e3b-168">Then, you must manually restart the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="23e3b-169">這讓您可以選擇最適合您業務需求的重新啟動時間。</span><span class="sxs-lookup"><span data-stu-id="23e3b-169">This enables you to choose a restart time that is best for your business requirements.</span></span> <span data-ttu-id="23e3b-170">當 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務重新啟動時，AlwaysOn 就會啟用，而且 `IsHadrEnabled` 伺服器屬性會設定為 1。</span><span class="sxs-lookup"><span data-stu-id="23e3b-170">When the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service restarts, AlwaysOn will be enabled, and the `IsHadrEnabled` server property will be set to 1.</span></span>  
  
###  <a name="using-sql-server-powershell"></a><a name="PScmd2Procedure"></a> <span data-ttu-id="23e3b-171">使用 SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="23e3b-171">Using SQL Server PowerShell</span></span>  
 <span data-ttu-id="23e3b-172">**啟用 AlwaysOn**</span><span class="sxs-lookup"><span data-stu-id="23e3b-172">**To enable AlwaysOn**</span></span>  
  
1.  <span data-ttu-id="23e3b-173">將目錄切換到 (`cd`) 要啟用 AlwaysOn 可用性群組的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="23e3b-173">Change directory (`cd`) to a server instance that you want to enable for AlwaysOn Availability Groups.</span></span>  
  
2.  <span data-ttu-id="23e3b-174">使用 `Enable-SqlAlwaysOn` 指令程式，啟用 AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="23e3b-174">Use the `Enable-SqlAlwaysOn` cmdlet to enable AlwaysOn Availability Groups.</span></span>  
  
     <span data-ttu-id="23e3b-175">若要檢視指令程式的語法，請在 `Get-Help` PowerShell 環境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 指令程式。</span><span class="sxs-lookup"><span data-stu-id="23e3b-175">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="23e3b-176">如需詳細資訊，請參閱 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="23e3b-176">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="23e3b-177">如需如何控制 `Enable-SqlAlwaysOn` Cmdlet 是否重新開機服務的相關資訊 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，請參閱本主題稍後的「 [Cmdlet 何時重新開機 SQL Server 服務？](#WhenCmdletRestartsSQL)」。</span><span class="sxs-lookup"><span data-stu-id="23e3b-177">For information about how to control whether the `Enable-SqlAlwaysOn` cmdlet restarts the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service, see [When Does a Cmdlet Restart the SQL Server Service?](#WhenCmdletRestartsSQL), later in this topic.</span></span>  
  
 <span data-ttu-id="23e3b-178">**若要設定和使用 SQL Server PowerShell 提供者**</span><span class="sxs-lookup"><span data-stu-id="23e3b-178">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="23e3b-179">SQL Server PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="23e3b-179">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
####  <a name="example-enable-sqlalwayson"></a><a name="ExmplEnable-SqlHadrServic"></a> <span data-ttu-id="23e3b-180">範例：Enable-SqlAlwaysOn</span><span class="sxs-lookup"><span data-stu-id="23e3b-180">Example: Enable-SqlAlwaysOn</span></span>  
 <span data-ttu-id="23e3b-181">下列 PowerShell 命令會在 SQL Server 執行個體 (電腦\\執行個體) 上啟用 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="23e3b-181">The following PowerShell command enables [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] on an instance of SQL Server (*Computer*\\*Instance*).</span></span>  
  
```powershell
Enable-SqlAlwaysOn -Path SQLSERVER:\SQL\Computer\Instance  
```  
  
##  <a name="disable-alwayson-availability-groups"></a><a name="DisableAOAG"></a><span data-ttu-id="23e3b-182">停用 AlwaysOn 可用性群組</span><span class="sxs-lookup"><span data-stu-id="23e3b-182">Disable AlwaysOn Availability Groups</span></span>  
  
-   <span data-ttu-id="23e3b-183">**在您停用 AlwaysOn 之前：**</span><span class="sxs-lookup"><span data-stu-id="23e3b-183">**Before you disable AlwaysOn:**</span></span>  
  
     [<span data-ttu-id="23e3b-184">建議</span><span class="sxs-lookup"><span data-stu-id="23e3b-184">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="23e3b-185">**若要停用 AlwaysOn，請使用：**</span><span class="sxs-lookup"><span data-stu-id="23e3b-185">**To disable AlwaysOn, using:**</span></span>  
  
    -   [<span data-ttu-id="23e3b-186">SQL Server 組態管理員</span><span class="sxs-lookup"><span data-stu-id="23e3b-186">SQL Server Configuration Manager</span></span>](#SQLCM3Procedure)  
  
    -   [<span data-ttu-id="23e3b-187">PowerShell</span><span class="sxs-lookup"><span data-stu-id="23e3b-187">PowerShell</span></span>](#PScmd3Procedure)  
  
-   <span data-ttu-id="23e3b-188">**後續操作：**  [停用 AlwaysOn 之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="23e3b-188">**Follow Up:**  [After Disabling AlwaysOn](#FollowUp)</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="23e3b-189">一次只在一個伺服器執行個體上停用 AlwaysOn。</span><span class="sxs-lookup"><span data-stu-id="23e3b-189">Disable AlwaysOn on only one server instance at a time.</span></span> <span data-ttu-id="23e3b-190">停用 AlwaysOn 可用性群組之後，等到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務重新啟動後才能在另一個伺服器執行個體繼續進行。</span><span class="sxs-lookup"><span data-stu-id="23e3b-190">After disabling AlwaysOn Availability Groups, wait until the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service has restarted before you proceed to another server instance.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="23e3b-191">建議</span><span class="sxs-lookup"><span data-stu-id="23e3b-191">Recommendations</span></span>  
 <span data-ttu-id="23e3b-192">在伺服器執行個體上停用 AlwaysOn 之前，我們建議您執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="23e3b-192">Before you disable AlwaysOn on a server instance, we recommend that you do the following:</span></span>  
  
1.  <span data-ttu-id="23e3b-193">如果伺服器執行個體目前裝載要保留之可用性群組的主要複本，建議手動將可用性群組容錯移轉至已同步處理的次要複本 (如果可能的話)。</span><span class="sxs-lookup"><span data-stu-id="23e3b-193">If the server instance is currently hosting the primary replica of an availability group that you want to keep, we recommend that you manually fail over the availability group to a synchronized secondary replica, if possible.</span></span> <span data-ttu-id="23e3b-194">如需詳細資訊，請參閱[執行可用性群組的已規劃手動容錯移轉 &#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="23e3b-194">For more information, see [Perform a Planned Manual Failover of an Availability Group &#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="23e3b-195">移除所有本機次要複本。</span><span class="sxs-lookup"><span data-stu-id="23e3b-195">Remove all local secondary replicas.</span></span> <span data-ttu-id="23e3b-196">如需詳細資訊，請參閱[將次要複本從可用性群組移除 &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="23e3b-196">For more information, see [Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md).</span></span>  
  
###  <a name="using-sql-server-configuration-manager"></a><a name="SQLCM3Procedure"></a> <span data-ttu-id="23e3b-197">使用 SQL Server 組態管理員</span><span class="sxs-lookup"><span data-stu-id="23e3b-197">Using SQL Server Configuration Manager</span></span>  
 <span data-ttu-id="23e3b-198">**停用 AlwaysOn**</span><span class="sxs-lookup"><span data-stu-id="23e3b-198">**To disable AlwaysOn**</span></span>  
  
1.  <span data-ttu-id="23e3b-199">連接到 Windows Server 容錯移轉叢集 (WSFC) 節點，此節點裝載您要停用 AlwaysOn 可用性群組的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="23e3b-199">Connect to the Windows Server Failover Clustering (WSFC) node that hosts the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance where you want to disable AlwaysOn Availability Groups.</span></span>  
  
2.  <span data-ttu-id="23e3b-200">指向 **[開始]** 功能表上的 **[所有程式]** ，然後依序指向 [ [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)]] 和 **[組態工具]** ，再按一下 **[SQL Server 組態管理員]** 。</span><span class="sxs-lookup"><span data-stu-id="23e3b-200">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and click **SQL Server Configuration Manager**.</span></span>  
  
3.  <span data-ttu-id="23e3b-201">在**SQL Server 組態管理員**中，按一下 [ **SQL Server Services**]，以滑鼠右鍵按一下 SQL Server (\*\* < *`instance name`*>) **]，其中 **<*`instance name`*>** 是您要停用 AlwaysOn 可用性群組的本機伺服器實例名稱，然後按一下 [**屬性\*\*]。</span><span class="sxs-lookup"><span data-stu-id="23e3b-201">In **SQL Server Configuration Manager**, click **SQL Server Services**, right-click SQL Server (**<*`instance name`*>)**, where **<*`instance name`*>** is the name of a local server instance for which you want to disable AlwaysOn Availability Groups, and click **Properties**.</span></span>  
  
4.  <span data-ttu-id="23e3b-202">在 [AlwaysOn 高可用性]\*\*\*\* 索引標籤上，取消選取 [啟用 AlwaysOn 可用性群組] \*\*\*\* 核取方塊，然後按一下 [確定] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="23e3b-202">On the**AlwaysOn High Availability**tab, deselect the **Enable AlwaysOn Availability Groups** check box, and click **OK**.</span></span>  
  
     [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="23e3b-203">組態管理員會儲存您的變更並重新啟動 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="23e3b-203">Configuration Manager saves your change and restarts the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="23e3b-204">當 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務重新啟動時，AlwaysOn 就會停用，而且 `IsHadrEnabled` 伺服器屬性會設定為 0，表示 AlwaysOn 可用性群組已停用。</span><span class="sxs-lookup"><span data-stu-id="23e3b-204">When the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service restarts, AlwaysOn will be disabled, and the `IsHadrEnabled` server property will be set to 0, to indicate that AlwaysOn Availability Groups is disabled.</span></span>  
  
5.  <span data-ttu-id="23e3b-205">我們建議您閱讀本主題稍後的＜ [待處理：停用 AlwaysOn 之後](#FollowUp)＞資訊。</span><span class="sxs-lookup"><span data-stu-id="23e3b-205">We recommend that you read the information in [Follow Up: After Disabling AlwaysOn](#FollowUp), later in this topic.</span></span>  
  
###  <a name="using-sql-server-powershell"></a><a name="PScmd3Procedure"></a> <span data-ttu-id="23e3b-206">使用 SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="23e3b-206">Using SQL Server PowerShell</span></span>  
 <span data-ttu-id="23e3b-207">**停用 AlwaysOn**</span><span class="sxs-lookup"><span data-stu-id="23e3b-207">**To disable AlwaysOn**</span></span>  
  
1.  <span data-ttu-id="23e3b-208">將目錄 (`cd`) 變更為您想要為 AlwaysOn 可用性群組停用的目前已啟用伺服器實例。</span><span class="sxs-lookup"><span data-stu-id="23e3b-208">Change directory (`cd`) to a currently-enabled server instance that you want to disenable for AlwaysOn Availability Groups.</span></span>  
  
2.  <span data-ttu-id="23e3b-209">使用 `Disable-SqlAlwaysOn` 指令程式，啟用 AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="23e3b-209">Use the `Disable-SqlAlwaysOn` cmdlet to enable AlwaysOn Availability Groups.</span></span>  
  
     <span data-ttu-id="23e3b-210">例如，下列命令會在 SQL Server (*電腦* \\ *實例*) 的實例上停用 AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="23e3b-210">For example, the following command disables AlwaysOn Availability Groups on an instance of SQL Server (*Computer*\\*Instance*).</span></span>  <span data-ttu-id="23e3b-211">此命令需要重新啟動執行個體，而且系統將提示您確認重新啟動。</span><span class="sxs-lookup"><span data-stu-id="23e3b-211">This command requires restarting the instance, and you will be prompted to confirm this restart.</span></span>  
  
    ```powershell
    Disable-SqlAlwaysOn -Path SQLSERVER:\SQL\Computer\Instance  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="23e3b-212">如需如何控制 `Disable-SqlAlwaysOn` Cmdlet 是否重新開機服務的相關資訊 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，請參閱本主題稍後的「 [Cmdlet 何時重新開機 SQL Server 服務？](#WhenCmdletRestartsSQL)」。</span><span class="sxs-lookup"><span data-stu-id="23e3b-212">For information about how to control whether the `Disable-SqlAlwaysOn` cmdlet restarts the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service, see [When Does a Cmdlet Restart the SQL Server Service?](#WhenCmdletRestartsSQL), later in this topic.</span></span>  
  
     <span data-ttu-id="23e3b-213">若要檢視指令程式的語法，請在 `Get-Help` PowerShell 環境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 指令程式。</span><span class="sxs-lookup"><span data-stu-id="23e3b-213">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="23e3b-214">如需詳細資訊，請參閱 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="23e3b-214">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="23e3b-215">**若要設定和使用 SQL Server PowerShell 提供者**</span><span class="sxs-lookup"><span data-stu-id="23e3b-215">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="23e3b-216">SQL Server PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="23e3b-216">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
###  <a name="follow-up-after-disabling-alwayson"></a><a name="FollowUp"></a><span data-ttu-id="23e3b-217">後續操作：停用 AlwaysOn 之後</span><span class="sxs-lookup"><span data-stu-id="23e3b-217">Follow Up: After Disabling AlwaysOn</span></span>  
 <span data-ttu-id="23e3b-218">停用 AlwaysOn 可用性群組之後，必須重新啟動 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="23e3b-218">After you disable AlwaysOn Availability Groups, the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] must be restarted.</span></span> <span data-ttu-id="23e3b-219">SQL Server 組態管理員會自動重新啟動伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="23e3b-219">SQL Configuration Manager restarts the server instance automatically.</span></span> <span data-ttu-id="23e3b-220">但是，如果您使用 `Disable-SqlAlwaysOn` 指令程式，則需要手動重新啟動伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="23e3b-220">However, if you used the `Disable-SqlAlwaysOn` cmdlet, you will need to restart the server instance manually.</span></span> <span data-ttu-id="23e3b-221">如需詳細資訊，請參閱 [sqlservr Application](../../../tools/sqlservr-application.md)。</span><span class="sxs-lookup"><span data-stu-id="23e3b-221">For more information, see [sqlservr Application](../../../tools/sqlservr-application.md).</span></span>  
  
 <span data-ttu-id="23e3b-222">在重新啟動的伺服器執行個體：</span><span class="sxs-lookup"><span data-stu-id="23e3b-222">On the restarted server instance:</span></span>  
  
-   <span data-ttu-id="23e3b-223">在 SQL Server 啟動時，可用性資料庫不會啟動，因此無法存取。</span><span class="sxs-lookup"><span data-stu-id="23e3b-223">Availability databases do not start up at SQL Server startup, making them inaccessible.</span></span>  
  
-   <span data-ttu-id="23e3b-224">唯一支援的 AlwaysOn [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式是 [DROP AVAILABILITY GROUP](/sql/t-sql/statements/drop-availability-group-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="23e3b-224">The only supported AlwaysOn [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement is [DROP AVAILABILITY GROUP](/sql/t-sql/statements/drop-availability-group-transact-sql).</span></span> <span data-ttu-id="23e3b-225">不支援 CREATE AVAILABILITY GROUP、ALTER AVAILABILITY GROUP，以及 ALTER DATABASE 的 SET HADR 選項。</span><span class="sxs-lookup"><span data-stu-id="23e3b-225">CREATE AVAILABILITY GROUP, ALTER AVAILABILITY GROUP, and the SET HADR options of ALTER DATABASE are not supported.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="23e3b-226">中繼資料和 WSFC 中的 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 組態資料不受 AlwaysOn 可用性群組停用所影響。</span><span class="sxs-lookup"><span data-stu-id="23e3b-226">metadata and [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] configuration data in WSFC are unaffected by disabling AlwaysOn Availability Groups.</span></span>  
  
 <span data-ttu-id="23e3b-227">如果您在裝載一個或多個可用性群組之可用性複本的每個伺服器執行個體上永久停用 AlwaysOn 可用性群組，建議您完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="23e3b-227">If you permanently disable AlwaysOn Availability Groups on every server instance that hosts an availability replica for one or more availability groups, we recommend that you complete the following steps:</span></span>  
  
1.  <span data-ttu-id="23e3b-228">如果您在停用 AlwaysOn 之前未移除本機可用性複本，請針對裝載可用性複本的伺服器執行個體刪除 (卸除) 每個可用性群組。</span><span class="sxs-lookup"><span data-stu-id="23e3b-228">If you did not remove the local availability replicas before disabling AlwaysOn, delete (drop) each availability group for which the server instance is hosting an availability replica.</span></span> <span data-ttu-id="23e3b-229">如需刪除可用性群組的相關資訊，請參閱[移除可用性群組 &#40;SQL Server&#41;](remove-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="23e3b-229">For information about deleting an availability group, see [Remove an Availability Group &#40;SQL Server&#41;](remove-an-availability-group-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="23e3b-230">若要移除遺留的中繼資料，在做為原始 WSFC 叢集一部分的伺服器執行個體上，刪除 (卸除) 每個受影響的可用性群組。</span><span class="sxs-lookup"><span data-stu-id="23e3b-230">To remove the metadata left behind, delete (drop) each affected availability group on a server instance that is part of the original WSFC cluster.</span></span>  
  
3.  <span data-ttu-id="23e3b-231">任何主要資料庫仍會繼續可供所有連接存取，但是主要和次要資料庫之間的資料同步處理會停止。</span><span class="sxs-lookup"><span data-stu-id="23e3b-231">Any primary databases continue to be accessible to all connections but the data synchronization between the primary and secondary databases stops.</span></span>  
  
4.  <span data-ttu-id="23e3b-232">次要資料庫會進入 RESTORING 狀態。</span><span class="sxs-lookup"><span data-stu-id="23e3b-232">The secondary databases enter the RESTORING state.</span></span> <span data-ttu-id="23e3b-233">您可以刪除它們，或透過使用 RESTORE WITH RECOVERY 還原它們。</span><span class="sxs-lookup"><span data-stu-id="23e3b-233">You can delete them, or you can restore them by using RESTORE WITH RECOVERY.</span></span> <span data-ttu-id="23e3b-234">但是，還原的資料庫不再參與可用性群組資料同步處理。</span><span class="sxs-lookup"><span data-stu-id="23e3b-234">However, restored databases are no longer participating in availability-group data synchronization.</span></span>  
  
##  <a name="when-does-a-cmdlet-restart-the-sql-server-service"></a><a name="WhenCmdletRestartsSQL"></a> <span data-ttu-id="23e3b-235">Cmdlet 在何時重新啟動 SQL Server 服務</span><span class="sxs-lookup"><span data-stu-id="23e3b-235">When Does a Cmdlet Restart the SQL Server Service?</span></span>  
 <span data-ttu-id="23e3b-236">在目前執行中的伺服器執行個體上，使用 `Enable-SqlAlwaysOn` 或 `Disable-SqlAlwaysOn` 變更目前的 AlwaysOn 設定，可能會導致 SQL Server 服務重新啟動。</span><span class="sxs-lookup"><span data-stu-id="23e3b-236">On a server instance that is currently running, using `Enable-SqlAlwaysOn` or `Disable-SqlAlwaysOn` to change the current AlwaysOn setting could cause the SQL Server service to restart.</span></span> <span data-ttu-id="23e3b-237">重新啟動行為取決於下列條件：</span><span class="sxs-lookup"><span data-stu-id="23e3b-237">The restart behavior on depends on the following conditions:</span></span>  
  
|<span data-ttu-id="23e3b-238">指定 -NoServiceRestart 參數</span><span class="sxs-lookup"><span data-stu-id="23e3b-238">-NoServiceRestart parameter specified</span></span>|<span data-ttu-id="23e3b-239">指定 -Force 參數</span><span class="sxs-lookup"><span data-stu-id="23e3b-239">-Force parameter specified</span></span>|<span data-ttu-id="23e3b-240">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務是否重新啟動？</span><span class="sxs-lookup"><span data-stu-id="23e3b-240">Is the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service restarted?</span></span>|  
|--------------------------------------------|---------------------------------|---------------------------------------------------------|  
|<span data-ttu-id="23e3b-241">否</span><span class="sxs-lookup"><span data-stu-id="23e3b-241">No</span></span>|<span data-ttu-id="23e3b-242">否</span><span class="sxs-lookup"><span data-stu-id="23e3b-242">No</span></span>|<span data-ttu-id="23e3b-243">根據預設。</span><span class="sxs-lookup"><span data-stu-id="23e3b-243">By default.</span></span> <span data-ttu-id="23e3b-244">但指令程式會出現提示，如下所示：</span><span class="sxs-lookup"><span data-stu-id="23e3b-244">But the cmdlet prompts you as follows:</span></span><br /><br /> <span data-ttu-id="23e3b-245">**若要完成這個動作，我們必須重新啟動伺服器執行個體 '<執行個體名稱>' 的 SQL Server 服務。您要繼續嗎?**</span><span class="sxs-lookup"><span data-stu-id="23e3b-245">**To complete this action, we must restart the SQL Server service for server instance '<instance_name>'. Do you want to continue?**</span></span><br /><br /> <span data-ttu-id="23e3b-246">**[Y] 是 [N] 否 [S] 暫停 [?] 說明 (預設為 "Y")：**</span><span class="sxs-lookup"><span data-stu-id="23e3b-246">**[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):**</span></span><br /><br /> <span data-ttu-id="23e3b-247">如果指定 **N** 或 **S**，就不會重新啟動服務。</span><span class="sxs-lookup"><span data-stu-id="23e3b-247">If you specify **N** or **S**, the service is not restarted.</span></span>|  
|<span data-ttu-id="23e3b-248">否</span><span class="sxs-lookup"><span data-stu-id="23e3b-248">No</span></span>|<span data-ttu-id="23e3b-249">是</span><span class="sxs-lookup"><span data-stu-id="23e3b-249">Yes</span></span>|<span data-ttu-id="23e3b-250">服務會重新啟動。</span><span class="sxs-lookup"><span data-stu-id="23e3b-250">Service is restarted.</span></span>|  
|<span data-ttu-id="23e3b-251">是</span><span class="sxs-lookup"><span data-stu-id="23e3b-251">Yes</span></span>|<span data-ttu-id="23e3b-252">否</span><span class="sxs-lookup"><span data-stu-id="23e3b-252">No</span></span>|<span data-ttu-id="23e3b-253">服務不會重新啟動。</span><span class="sxs-lookup"><span data-stu-id="23e3b-253">Service is not restarted.</span></span>|  
|<span data-ttu-id="23e3b-254">是</span><span class="sxs-lookup"><span data-stu-id="23e3b-254">Yes</span></span>|<span data-ttu-id="23e3b-255">是</span><span class="sxs-lookup"><span data-stu-id="23e3b-255">Yes</span></span>|<span data-ttu-id="23e3b-256">服務不會重新啟動。</span><span class="sxs-lookup"><span data-stu-id="23e3b-256">Service is not restarted.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="23e3b-257">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23e3b-257">See Also</span></span>  
 <span data-ttu-id="23e3b-258">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="23e3b-258">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="23e3b-259">SERVERPROPERTY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="23e3b-259">SERVERPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/serverproperty-transact-sql)  
