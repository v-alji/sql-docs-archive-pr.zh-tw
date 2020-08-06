---
title: 設定 FailureConditionLevel 屬性設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 513dd179-9a46-46da-9fdd-7632cf6d0816
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8924b864d7cc8be078b370e3182713114f54ff6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595574"
---
# <a name="configure-failureconditionlevel-property-settings"></a><span data-ttu-id="1ba67-102">設定 FailureConditionLeve 屬性設定</span><span class="sxs-lookup"><span data-stu-id="1ba67-102">Configure FailureConditionLevel Property Settings</span></span>
  <span data-ttu-id="1ba67-103">使用 FailureConditionLevel 屬性，即可將 AlwaysOn 容錯移轉叢集執行個體 (FCI) 的條件設定為容錯移轉或重新啟動。</span><span class="sxs-lookup"><span data-stu-id="1ba67-103">Use the FailureConditionLevel property to set the conditions for the AlwaysOn Failover Cluster Instance (FCI) to fail over or restart.</span></span> <span data-ttu-id="1ba67-104">對這個屬性的變更會立即套用，而不需要重新啟動 Windows Server 容錯移轉叢集 (WSFC) 服務或 FCI 資源。</span><span class="sxs-lookup"><span data-stu-id="1ba67-104">Changes to this property are applied immediately without requiring a restart of the Windows Server Failover Cluster (WSFC) service or the FCI resource.</span></span>  
  
-   <span data-ttu-id="1ba67-105">**開始之前：** [FailureConditionLevel 屬性設定](#Restrictions)[安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="1ba67-105">**Before you begin:**  [FailureConditionLevel Property Settings](#Restrictions), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="1ba67-106">**若要進行 FailureConditionLevel 屬性設定，請使用**  [PowerShell](#PowerShellProcedure)、[容錯移轉叢集管理員](#WSFC)、[Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="1ba67-106">**To configure the FailureConditionLevel property settings using,** [PowerShell](#PowerShellProcedure), [Failover Cluster Manager](#WSFC), [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1ba67-107">開始之前</span><span class="sxs-lookup"><span data-stu-id="1ba67-107">Before You Begin</span></span>  
  
###  <a name="failureconditionlevel-property-settings"></a><a name="Restrictions"></a> <span data-ttu-id="1ba67-108">FailureConditionLevel 屬性設定</span><span class="sxs-lookup"><span data-stu-id="1ba67-108">FailureConditionLevel Property Settings</span></span>  
 <span data-ttu-id="1ba67-109">失敗狀況會設定為遞增等級。</span><span class="sxs-lookup"><span data-stu-id="1ba67-109">The failure conditions are set on an increasing scale.</span></span> <span data-ttu-id="1ba67-110">對於等級 1-5，每個等級都包含來自上一個等級的所有狀況，並加上自身的狀況。</span><span class="sxs-lookup"><span data-stu-id="1ba67-110">For levels 1-5, each level includes all the conditions from the previous levels in addition to its own conditions.</span></span> <span data-ttu-id="1ba67-111">這表示，每個等級都具有更高的容錯移轉或重新啟動可能性。</span><span class="sxs-lookup"><span data-stu-id="1ba67-111">This means that with each level, there is an increased probability of a failover or restart.</span></span>  <span data-ttu-id="1ba67-112">如需詳細資訊，請參閱＜ [Failover Policy for Failover Cluster Instances](failover-policy-for-failover-cluster-instances.md) ＞主題中的＜判斷失敗＞一節。</span><span class="sxs-lookup"><span data-stu-id="1ba67-112">For more information, see the "Determining Failures" section of the [Failover Policy for Failover Cluster Instances](failover-policy-for-failover-cluster-instances.md) topic.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1ba67-113">Security</span><span class="sxs-lookup"><span data-stu-id="1ba67-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1ba67-114">權限</span><span class="sxs-lookup"><span data-stu-id="1ba67-114">Permissions</span></span>  
 <span data-ttu-id="1ba67-115">需要 ALTER SETTINGS 及 VIEW SERVER STATE 權限。</span><span class="sxs-lookup"><span data-stu-id="1ba67-115">Requires ALTER SETTINGS and VIEW SERVER STATE permissions.</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="1ba67-116">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1ba67-116">Using PowerShell</span></span>  
  
### <a name="to-configure-failureconditionlevel-settings"></a><span data-ttu-id="1ba67-117">設定 FailureConditionLevel 設定</span><span class="sxs-lookup"><span data-stu-id="1ba67-117">To configure FailureConditionLevel settings</span></span>  
  
1.  <span data-ttu-id="1ba67-118">透過 **[以系統管理員身分執行]** 來啟動更高權限的 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="1ba67-118">Start an elevated Windows PowerShell via **Run as Administrator**.</span></span>  
  
2.  <span data-ttu-id="1ba67-119">匯入 `FailoverClusters` 模組來啟用叢集指令程式。</span><span class="sxs-lookup"><span data-stu-id="1ba67-119">Import the `FailoverClusters` module to enable cluster cmdlets.</span></span>  
  
3.  <span data-ttu-id="1ba67-120">使用 `Get-ClusterResource` Cmdlet 來尋找 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資源，然後使用 `Set-ClusterParameter` Cmdlet 設定容錯移轉叢集實例的**FailureConditionLevel**屬性。</span><span class="sxs-lookup"><span data-stu-id="1ba67-120">Use the `Get-ClusterResource` cmdlet to find the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resource, then use `Set-ClusterParameter` cmdlet to set the **FailureConditionLevel** property for a Failover Cluster Instance.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="1ba67-121">每次開啟新的 PowerShell 視窗時，都需要匯入 `FailoverClusters` 模組。</span><span class="sxs-lookup"><span data-stu-id="1ba67-121">Every time you open a new PowerShell window, you need to import the `FailoverClusters` module.</span></span>  

 <span data-ttu-id="1ba67-122">下列範例會將 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資源 "`SQL Server (INST1)`" 上的 FailureConditionLevel 設定變更為在發生嚴重伺服器錯誤時容錯移轉或重新啟動。</span><span class="sxs-lookup"><span data-stu-id="1ba67-122">The following example changes the FailureConditionLevel setting on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resource "`SQL Server (INST1)`" to fail over or restart on critical server errors.</span></span>  
  
```powershell  
Import-Module FailoverClusters  
  
$fci = "SQL Server (INST1)"  
Get-ClusterResource $fci | Set-ClusterParameter FailureConditionLevel 3
```  
  
### <a name="related-content-powershell"></a><span data-ttu-id="1ba67-123">相關內容 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="1ba67-123">Related Content (PowerShell)</span></span>  
  
-   <span data-ttu-id="1ba67-124">[Clustering and High-Availability](https://techcommunity.microsoft.com/t5/failover-clustering/bg-p/FailoverClustering) (叢集和高可用性 - 容錯移轉叢集和網路負載平衡團隊部落格)</span><span class="sxs-lookup"><span data-stu-id="1ba67-124">[Clustering and High-Availability](https://techcommunity.microsoft.com/t5/failover-clustering/bg-p/FailoverClustering) (Failover Clustering and Network Load Balancing Team Blog)</span></span>  
  
-   <span data-ttu-id="1ba67-125">[在容錯移轉叢集上開始使用 Windows PowerShell](https://technet.microsoft.com/library/ee619762\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="1ba67-125">[Getting Started with Windows PowerShell on a Failover Cluster](https://technet.microsoft.com/library/ee619762\(WS.10\).aspx)</span></span>  
  
-   [<span data-ttu-id="1ba67-126">叢集資源命令和對等的 Windows PowerShell 指令程式</span><span class="sxs-lookup"><span data-stu-id="1ba67-126">Cluster resource commands and equivalent Windows PowerShell cmdlets</span></span>](https://msdn.microsoft.com/library/ee619744.aspx#BKMK_resource)  
  
##  <a name="using-the-failover-cluster-manager-snap-in"></a><a name="WSFC"></a> <span data-ttu-id="1ba67-127">使用容錯移轉叢集管理員嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="1ba67-127">Using the Failover Cluster Manager Snap-in</span></span>  

### <a name="to-configure-failureconditionlevel-property-settings"></a><span data-ttu-id="1ba67-128">若要設定 FailureConditionLevel 屬性設定</span><span class="sxs-lookup"><span data-stu-id="1ba67-128">To configure FailureConditionLevel property settings</span></span>
  
1.  <span data-ttu-id="1ba67-129">開啟 [容錯移轉叢集管理員] 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="1ba67-129">Open the Failover Cluster Manager snap-in.</span></span>  
  
2.  <span data-ttu-id="1ba67-130">展開 **[服務及應用程式]** 並選取 FCI。</span><span class="sxs-lookup"><span data-stu-id="1ba67-130">Expand the **Services and Applications** and select the FCI.</span></span>  
  
3.  <span data-ttu-id="1ba67-131">以滑鼠右鍵按一下 [其他資源] 下方的 [SQL Server 資源]，然後從功能表中選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="1ba67-131">Right-click the **SQL Server resource** under **Other Resources**, and then select **Properties** from the menu.</span></span> <span data-ttu-id="1ba67-132">SQL Server 資源的 **[屬性]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="1ba67-132">The SQL Server resource **Properties** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="1ba67-133">選取 **[屬性]** 索引標籤，為 **[FaliureConditionLevel]** 屬性輸入所要的值，然後再按一下 **[確定]** 以套用變更。</span><span class="sxs-lookup"><span data-stu-id="1ba67-133">Select the **Properties** tab, enter the desired value for the **FaliureConditionLevel** property, and then click **OK** to apply the change.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1ba67-134">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1ba67-134">Using Transact-SQL</span></span>  

### <a name="to-configure-failureconditionlevel-property-settings"></a><span data-ttu-id="1ba67-135">若要設定 FailureConditionLevel 屬性設定</span><span class="sxs-lookup"><span data-stu-id="1ba67-135">To configure FailureConditionLevel property settings</span></span>
  
 <span data-ttu-id="1ba67-136">使用 [ALTER SERVER CONFIGURATION](/sql/t-sql/statements/alter-server-configuration-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式，可以指定 FailureConditionLevel 屬性值。</span><span class="sxs-lookup"><span data-stu-id="1ba67-136">Using the [ALTER SERVER CONFIGURATION](/sql/t-sql/statements/alter-server-configuration-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement, you can specify the FailureConditionLevel property value.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="1ba67-137">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1ba67-137">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="1ba67-138">下列範例會將 FailureConditionLevel 屬性設定為 0，指出任何失敗狀況都不會自動觸發容錯移轉或重新啟動。</span><span class="sxs-lookup"><span data-stu-id="1ba67-138">The following example sets the FailureConditionLevel property to 0, indicating that failover or restart will not be triggered automatically on any failure conditions.</span></span>  
  
```sql
ALTER SERVER CONFIGURATION SET FAILOVER CLUSTER PROPERTY FailureConditionLevel = 0;  
```  
  
## <a name="see-also"></a><span data-ttu-id="1ba67-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ba67-139">See Also</span></span>  
 <span data-ttu-id="1ba67-140">[sp_server_diagnostics &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1ba67-140">[sp_server_diagnostics &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) </span></span>  
 [<span data-ttu-id="1ba67-141">Failover Policy for Failover Cluster Instances</span><span class="sxs-lookup"><span data-stu-id="1ba67-141">Failover Policy for Failover Cluster Instances</span></span>](failover-policy-for-failover-cluster-instances.md)  
