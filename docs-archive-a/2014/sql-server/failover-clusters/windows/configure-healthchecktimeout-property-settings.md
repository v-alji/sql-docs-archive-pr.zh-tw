---
title: 設定 HealthCheckTimeout 屬性設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 3bbeb979-e6fc-4184-ad6e-cca62108de74
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a38cd6e9e4718a2f1c136e5412cde340e92f14c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595572"
---
# <a name="configure-healthchecktimeout-property-settings"></a><span data-ttu-id="9d061-102">設定 HealthCheckTimeout 屬性設定</span><span class="sxs-lookup"><span data-stu-id="9d061-102">Configure HealthCheckTimeout Property Settings</span></span>
  <span data-ttu-id="9d061-103">HealthCheckTimeout 設定是用來指定 SQL Server 資源 DLL 應該等候[sp_server_diagnostics](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql)預存程式傳回信息的時間長度（以毫秒為單位），然後再將 AlwaysOn 容錯移轉叢集實例回報 (FCI) 為沒有回應。</span><span class="sxs-lookup"><span data-stu-id="9d061-103">The HealthCheckTimeout setting is used to specify the length of time, in milliseconds, that the SQL Server resource DLL should wait for information returned by the [sp_server_diagnostics](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) stored procedure before reporting the AlwaysOn Failover Cluster Instance (FCI) as unresponsive.</span></span> <span data-ttu-id="9d061-104">針對逾時設定值所做的變更會立即生效，且不需要重新啟動 SQL Server 資源。</span><span class="sxs-lookup"><span data-stu-id="9d061-104">Changes that are made to the timeout settings are effective immediately and do not require a restart of the SQL Server resource.</span></span>  
  
-   <span data-ttu-id="9d061-105">**開始之前：** [限制事項](#Limits)、[安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="9d061-105">**Before you begin:**  [Limitations and Restrictions](#Limits), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="9d061-106">**使用下列項目設定 HeathCheckTimeout 設定：**  [PowerShell](#PowerShellProcedure)、[容錯移轉叢集管理員](#WSFC)、[Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="9d061-106">**To Configure the HeathCheckTimeout setting, using:**  [PowerShell](#PowerShellProcedure), [Failover Cluster Manager](#WSFC), [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9d061-107">開始之前</span><span class="sxs-lookup"><span data-stu-id="9d061-107">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Limits"></a> <span data-ttu-id="9d061-108">限制事項</span><span class="sxs-lookup"><span data-stu-id="9d061-108">Limitations and Restrictions</span></span>  
 <span data-ttu-id="9d061-109">此屬性的預設值為 60,000 毫秒 (60 秒)。</span><span class="sxs-lookup"><span data-stu-id="9d061-109">The default value for this property is 60,000 milliseconds (60 seconds).</span></span> <span data-ttu-id="9d061-110">最小值為 15,000 毫秒 (15 秒)。</span><span class="sxs-lookup"><span data-stu-id="9d061-110">The minimum value is 15,000 milliseconds (15 seconds).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9d061-111">Security</span><span class="sxs-lookup"><span data-stu-id="9d061-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9d061-112">權限</span><span class="sxs-lookup"><span data-stu-id="9d061-112">Permissions</span></span>  
 <span data-ttu-id="9d061-113">需要 ALTER SETTINGS 及 VIEW SERVER STATE 權限。</span><span class="sxs-lookup"><span data-stu-id="9d061-113">Requires ALTER SETTINGS and VIEW SERVER STATE permissions.</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="9d061-114">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="9d061-114">Using PowerShell</span></span>  
  
### <a name="to-configure-healthchecktimeout-settings"></a><span data-ttu-id="9d061-115">設定 HealthCheckTimeout 設定</span><span class="sxs-lookup"><span data-stu-id="9d061-115">To configure HealthCheckTimeout settings</span></span>  
  
1.  <span data-ttu-id="9d061-116">透過 **[以系統管理員身分執行]** 來啟動更高權限的 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="9d061-116">Start an elevated Windows PowerShell via **Run as Administrator**.</span></span>  
  
2.  <span data-ttu-id="9d061-117">匯入 `FailoverClusters` 模組來啟用叢集指令程式。</span><span class="sxs-lookup"><span data-stu-id="9d061-117">Import the `FailoverClusters` module to enable cluster cmdlets.</span></span>  
  
3.  <span data-ttu-id="9d061-118">使用 `Get-ClusterResource` Cmdlet 來尋找 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資源，然後使用 `Set-ClusterParameter` Cmdlet 設定容錯移轉叢集實例的**HealthCheckTimeout**屬性。</span><span class="sxs-lookup"><span data-stu-id="9d061-118">Use the `Get-ClusterResource` cmdlet to find the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resource, then use `Set-ClusterParameter` cmdlet to set the **HealthCheckTimeout** property for the failover cluster instance.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="9d061-119">每次開啟新的 PowerShell 視窗時，都需要匯入 `FailoverClusters` 模組。</span><span class="sxs-lookup"><span data-stu-id="9d061-119">Every time you open a new PowerShell window, you need to import the `FailoverClusters` module.</span></span>  

 <span data-ttu-id="9d061-120">下列範例會將 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資源 "`SQL Server (INST1)`" 上的 HealthCheckTimeout 設定變更為 60000 毫秒。</span><span class="sxs-lookup"><span data-stu-id="9d061-120">The following example changes the HealthCheckTimeout setting on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resource "`SQL Server (INST1)`" to 60000 milliseconds.</span></span>  
  
```powershell  
Import-Module FailoverClusters  
  
$fci = "SQL Server (INST1)"  
Get-ClusterResource $fci | Set-ClusterParameter HealthCheckTimeout 60000  
```  
  
### <a name="related-content-powershell"></a><span data-ttu-id="9d061-121">相關內容 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="9d061-121">Related Content (PowerShell)</span></span>  
  
-   <span data-ttu-id="9d061-122">[Clustering and High-Availability](https://techcommunity.microsoft.com/t5/failover-clustering/bg-p/FailoverClustering) (叢集和高可用性 - 容錯移轉叢集和網路負載平衡團隊部落格)</span><span class="sxs-lookup"><span data-stu-id="9d061-122">[Clustering and High-Availability](https://techcommunity.microsoft.com/t5/failover-clustering/bg-p/FailoverClustering) (Failover Clustering and Network Load Balancing Team Blog)</span></span>  
  
-   <span data-ttu-id="9d061-123">[在容錯移轉叢集上開始使用 Windows PowerShell](https://technet.microsoft.com/library/ee619762\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="9d061-123">[Getting Started with Windows PowerShell on a Failover Cluster](https://technet.microsoft.com/library/ee619762\(WS.10\).aspx)</span></span>  
  
-   [<span data-ttu-id="9d061-124">叢集資源命令和對等的 Windows PowerShell 指令程式</span><span class="sxs-lookup"><span data-stu-id="9d061-124">Cluster resource commands and equivalent Windows PowerShell cmdlets</span></span>](https://msdn.microsoft.com/library/ee619744.aspx#BKMK_resource)  
  
##  <a name="using-the-failover-cluster-manager-snap-in"></a><a name="WSFC"></a> <span data-ttu-id="9d061-125">使用容錯移轉叢集管理員嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="9d061-125">Using the Failover Cluster Manager Snap-in</span></span>  
 <span data-ttu-id="9d061-126">**設定 HealthCheckTimeout 設定**</span><span class="sxs-lookup"><span data-stu-id="9d061-126">**To configure HealthCheckTimeout setting**</span></span>  
  
1.  <span data-ttu-id="9d061-127">開啟 [容錯移轉叢集管理員] 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="9d061-127">Open the Failover Cluster Manager snap-in.</span></span>  
  
2.  <span data-ttu-id="9d061-128">展開 **[服務及應用程式]** 並選取 FCI。</span><span class="sxs-lookup"><span data-stu-id="9d061-128">Expand **Services and Applications** and select the FCI.</span></span>  
  
3.  <span data-ttu-id="9d061-129">以滑鼠右鍵按一下 [其他資源]\*\*\*\* 下方的 [SQL Server 資源]\*\*\*\*，並從滑鼠右鍵功能表中選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9d061-129">Right-click the **SQL Server resource** under **Other Resources** and select **Properties** from the right-click menu.</span></span> <span data-ttu-id="9d061-130">SQL Server 資源的 **[屬性]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="9d061-130">The SQL Server resource **Properties** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="9d061-131">選取 **[屬性]** 索引標籤，輸入需要的 **[HealthCheckTimeout]** 屬性值，然後按一下 **[確定]** 套用變更。</span><span class="sxs-lookup"><span data-stu-id="9d061-131">Select the **Properties** tab, enter the desired value for the **HealthCheckTimeout** property, and then click **OK** to apply the change.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="9d061-132">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9d061-132">Using Transact-SQL</span></span>  
 <span data-ttu-id="9d061-133">您可以使用[ALTER SERVER CONFIGURATION](/sql/t-sql/statements/alter-server-configuration-transact-sql) [!INCLUDE[tsql](../../../includes/tsql-md.md)] 語句來指定 HealthCheckTimeOut 屬性值。</span><span class="sxs-lookup"><span data-stu-id="9d061-133">Using the [ALTER SERVER CONFIGURATION](/sql/t-sql/statements/alter-server-configuration-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement, you can specify the HealthCheckTimeOut property value.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="9d061-134">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9d061-134">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="9d061-135">下列範例會將 HealthCheckTimeout 選項設定為 15,000 毫秒 (15 秒)。</span><span class="sxs-lookup"><span data-stu-id="9d061-135">The following example sets the HealthCheckTimeout option to 15,000 milliseconds (15 seconds).</span></span>  
  
```sql
ALTER SERVER CONFIGURATION   
SET FAILOVER CLUSTER PROPERTY HealthCheckTimeout = 15000;  
```  
  
## <a name="see-also"></a><span data-ttu-id="9d061-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d061-136">See Also</span></span>  
 [<span data-ttu-id="9d061-137">Failover Policy for Failover Cluster Instances</span><span class="sxs-lookup"><span data-stu-id="9d061-137">Failover Policy for Failover Cluster Instances</span></span>](failover-policy-for-failover-cluster-instances.md)  
