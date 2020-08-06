---
title: 設定彈性容錯移轉原則，以控制 Always On 可用性群組的自動容錯移轉 (的條件) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], flexible failover policy
- Availability Groups [SQL Server], failover
- failover [SQL Server], AlwaysOn Availability Groups
ms.assetid: 1ed564b4-9835-4245-ae35-9ba67419a4ce
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c938624a3ed39fe2d41f21a21af5231aa76a8c17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707913"
---
# <a name="configure-the-flexible-failover-policy-to-control-conditions-for-automatic-failover-always-on-availability-groups"></a><span data-ttu-id="cd597-102">設定彈性容錯移轉原則以控制自動容錯移轉的條件 (AlwaysOn 可用性群組)</span><span class="sxs-lookup"><span data-stu-id="cd597-102">Configure the Flexible Failover Policy to Control Conditions for Automatic Failover (Always On Availability Groups)</span></span>
  <span data-ttu-id="cd597-103">本主題描述如何使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 中的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]或 PowerShell 來設定 AlwaysOn 可用性群組的彈性容錯移轉原則。</span><span class="sxs-lookup"><span data-stu-id="cd597-103">This topic describes how to configure the flexible failover policy for an AlwaysOn availability group by using [!INCLUDE[tsql](../../../includes/tsql-md.md)] or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="cd597-104">彈性容錯移轉原則可讓您更精確地控制造成可用性群組之自動容錯移轉的狀況。</span><span class="sxs-lookup"><span data-stu-id="cd597-104">A flexible failover policy provides granular control over the conditions that cause automatic failover for an availability group.</span></span> <span data-ttu-id="cd597-105">透過變更觸發自動容錯移轉的失敗狀況和健全狀況檢查的頻率，您可以提高或降低自動容錯移轉的可能性，以便支援高可用性的 SLA。</span><span class="sxs-lookup"><span data-stu-id="cd597-105">By changing the failure conditions that trigger an automatic failover and the frequency of health checks, you can increase or decrease the likelihood of an automatic failover to support your SLA for high availability.</span></span>  
  
  
  
    > [!NOTE]  
    >  The flexible failover policy of an availability group cannot be configured by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="cd597-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="cd597-106">Before You Begin</span></span>  
  
###  <a name="limitations-on-automatic-failovers"></a><a name="Limitations"></a><span data-ttu-id="cd597-107">自動容錯移轉的限制</span><span class="sxs-lookup"><span data-stu-id="cd597-107">Limitations on Automatic Failovers</span></span>  
  
-   <span data-ttu-id="cd597-108">若要進行自動容錯移轉，目前的主要複本和一個次要複本必須設定為具有自動容錯移轉的同步認可可用性模式，而且次要複本必須與主要複本同步處理。</span><span class="sxs-lookup"><span data-stu-id="cd597-108">For an automatic failover to occur, the current primary replica and one secondary replica must be configured for synchronous-commit availability mode with automatic failover and the secondary replica must be synchronized with the primary replica.</span></span>  
  
-   <span data-ttu-id="cd597-109">如果可用性群組超過其 WSFC 失敗臨界值，WSFC 叢集將不會嘗試進行可用性群組的自動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="cd597-109">If an availability group exceeds its WSFC failure threshold, the WSFC cluster will not attempt an automatic failover for the availability group.</span></span> <span data-ttu-id="cd597-110">此外，可用性群組的 WSFC 資源群組會維持失敗狀態，直到叢集管理員手動讓失敗的資源群組上線，或者資料庫管理員執行可用性群組的手動容錯移轉為止。</span><span class="sxs-lookup"><span data-stu-id="cd597-110">Furthermore, the WSFC resource group of the availability group remains in a failed state until either the cluster administrator manually brings the failed resource group online or the database administrator performs a manual failover of the availability group.</span></span> <span data-ttu-id="cd597-111">*「WSFC 失敗臨界值」* (WSFC Failure Threshold) 定義為可用性群組在給定的時間週期內支援的失敗次數上限。</span><span class="sxs-lookup"><span data-stu-id="cd597-111">The *WSFC failure threshold* is defined as the maximum number of failures supported for the availability group during a given time period.</span></span> <span data-ttu-id="cd597-112">預設的時間週期為六小時，而且在這段時間內失敗次數上限的預設值為 *n*-1，其中 *n* 是 WSFC 節點的數目。</span><span class="sxs-lookup"><span data-stu-id="cd597-112">The default time period is six hours, and the default value for the maximum number of failures during this period is *n*-1, where *n* is the number of WSFC nodes.</span></span> <span data-ttu-id="cd597-113">若要變更給定可用性群組得失敗臨界值，請使用 WSFC 容錯移轉管理員主控台。</span><span class="sxs-lookup"><span data-stu-id="cd597-113">To change the failure-threshold values for a given availability group, use the WSFC Failover Manager Console.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="cd597-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="cd597-114">Prerequisites</span></span>  
  
-   <span data-ttu-id="cd597-115">您必須連接到裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="cd597-115">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="cd597-116">Security</span><span class="sxs-lookup"><span data-stu-id="cd597-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="cd597-117">權限</span><span class="sxs-lookup"><span data-stu-id="cd597-117">Permissions</span></span>  
  
|<span data-ttu-id="cd597-118">Task</span><span class="sxs-lookup"><span data-stu-id="cd597-118">Task</span></span>|<span data-ttu-id="cd597-119">權限</span><span class="sxs-lookup"><span data-stu-id="cd597-119">Permissions</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="cd597-120">若要設定新可用性群組的彈性容錯移轉原則</span><span class="sxs-lookup"><span data-stu-id="cd597-120">To configure the flexible failover policy for a new availability group</span></span>|<span data-ttu-id="cd597-121">需要 **系統管理員 (sysadmin)** 固定伺服器角色的成員資格，以及 CREATE AVAILABILITY GROUP 伺服器權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="cd597-121">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
|<span data-ttu-id="cd597-122">若要修改現有可用性群組的原則</span><span class="sxs-lookup"><span data-stu-id="cd597-122">To modify the policy of an existing availability group</span></span>|<span data-ttu-id="cd597-123">需要可用性群組的 ALTER AVAILABILITY GROUP 權限、CONTROL AVAILABILITY GROUP 權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="cd597-123">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="cd597-124">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cd597-124">Using Transact-SQL</span></span>  
 <span data-ttu-id="cd597-125">**若要設定彈性容錯移轉原則**</span><span class="sxs-lookup"><span data-stu-id="cd597-125">**To configure the flexible failover policy**</span></span>  
  
1.  <span data-ttu-id="cd597-126">連接到裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="cd597-126">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="cd597-127">若為新的可用性群組，請使用[CREATE AVAILABILITY group](/sql/t-sql/statements/create-availability-group-transact-sql) [!INCLUDE[tsql](../../../includes/tsql-md.md)] 語句。</span><span class="sxs-lookup"><span data-stu-id="cd597-127">For a new availability group, use the [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="cd597-128">如果您要修改現有的可用性群組，請使用[ALTER AVAILABILITY group](/sql/t-sql/statements/alter-availability-group-transact-sql) [!INCLUDE[tsql](../../../includes/tsql-md.md)] 語句。</span><span class="sxs-lookup"><span data-stu-id="cd597-128">If you are modifying an existing availability group, use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span>  
  
    -   <span data-ttu-id="cd597-129">若要設定容錯移轉狀況層級，請使用 FAILURE_CONDITION_LEVEL = *n* 選項，其中 *n* 是介於 1 到 5 之間的整數。</span><span class="sxs-lookup"><span data-stu-id="cd597-129">To set the failover condition level, use the FAILURE_CONDITION_LEVEL = *n* option, where, *n* is an integer from 1 to 5.</span></span>  
  
         <span data-ttu-id="cd597-130">例如，下列 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式會將現有可用性群組 `AG1`的失敗狀況層級變更為層級一：</span><span class="sxs-lookup"><span data-stu-id="cd597-130">For example, the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement changes the failure-condition level of an existing availability group, `AG1`, to level one:</span></span>  
  
        ```sql
        ALTER AVAILABILITY GROUP AG1 SET (FAILURE_CONDITION_LEVEL = 1);  
        ```  
  
         <span data-ttu-id="cd597-131">這些整數值與失敗狀況層級的關聯性如下所示：</span><span class="sxs-lookup"><span data-stu-id="cd597-131">The relationship of these integer values to the failure condition levels is as follows:</span></span>  
  
        |[!INCLUDE[tsql](../../../includes/tsql-md.md)] <span data-ttu-id="cd597-132">值</span><span class="sxs-lookup"><span data-stu-id="cd597-132">Value</span></span>|<span data-ttu-id="cd597-133">層級</span><span class="sxs-lookup"><span data-stu-id="cd597-133">Level</span></span>|<span data-ttu-id="cd597-134">起始自動容錯移轉的狀況</span><span class="sxs-lookup"><span data-stu-id="cd597-134">Automatic Is Failover Initiated When...</span></span>|  
        |------------------------------|-----------|-------------------------------------------|  
        |<span data-ttu-id="cd597-135">1</span><span class="sxs-lookup"><span data-stu-id="cd597-135">1</span></span>|<span data-ttu-id="cd597-136">一個</span><span class="sxs-lookup"><span data-stu-id="cd597-136">One</span></span>|<span data-ttu-id="cd597-137">伺服器關閉時。</span><span class="sxs-lookup"><span data-stu-id="cd597-137">On server down.</span></span> <span data-ttu-id="cd597-138">SQL Server 服務由於容錯移轉或重新啟動而停止。</span><span class="sxs-lookup"><span data-stu-id="cd597-138">The SQL Server service stops because of a failover or restart.</span></span>|  
        |<span data-ttu-id="cd597-139">2</span><span class="sxs-lookup"><span data-stu-id="cd597-139">2</span></span>|<span data-ttu-id="cd597-140">兩個</span><span class="sxs-lookup"><span data-stu-id="cd597-140">Two</span></span>|<span data-ttu-id="cd597-141">伺服器沒有回應時。</span><span class="sxs-lookup"><span data-stu-id="cd597-141">On server unresponsive.</span></span> <span data-ttu-id="cd597-142">滿足任何狀況的較低值，而且 SQL Server 服務連接到叢集且超過健全狀況檢查逾時臨界值，或者目前主要複本處於失敗狀態。</span><span class="sxs-lookup"><span data-stu-id="cd597-142">Any condition of lower value is satisfied, the SQL Server service is connected to the cluster and the health check timeout threshold is exceeded, or the current primary replica is in a failed state.</span></span>|  
        |<span data-ttu-id="cd597-143">3</span><span class="sxs-lookup"><span data-stu-id="cd597-143">3</span></span>|<span data-ttu-id="cd597-144">三</span><span class="sxs-lookup"><span data-stu-id="cd597-144">Three</span></span>|<span data-ttu-id="cd597-145">發生嚴重伺服器錯誤時。</span><span class="sxs-lookup"><span data-stu-id="cd597-145">On critical server error.</span></span> <span data-ttu-id="cd597-146">滿足任何狀況的較低值，或者發生內部嚴重伺服器錯誤。</span><span class="sxs-lookup"><span data-stu-id="cd597-146">Any condition of lower value is satisfied or an internal critical server error occurs.</span></span><br /><br /> <span data-ttu-id="cd597-147">這是預設層級。</span><span class="sxs-lookup"><span data-stu-id="cd597-147">This is the default level.</span></span>|  
        |<span data-ttu-id="cd597-148">4</span><span class="sxs-lookup"><span data-stu-id="cd597-148">4</span></span>|<span data-ttu-id="cd597-149">四</span><span class="sxs-lookup"><span data-stu-id="cd597-149">Four</span></span>|<span data-ttu-id="cd597-150">發生一般伺服器錯誤時。</span><span class="sxs-lookup"><span data-stu-id="cd597-150">On moderate server error.</span></span> <span data-ttu-id="cd597-151">滿足任何狀況的較低值，或者發生一般伺服器錯誤。</span><span class="sxs-lookup"><span data-stu-id="cd597-151">Any condition of lower value is satisfied or a moderate Server error occurs.</span></span>|  
        |<span data-ttu-id="cd597-152">5</span><span class="sxs-lookup"><span data-stu-id="cd597-152">5</span></span>|<span data-ttu-id="cd597-153">五</span><span class="sxs-lookup"><span data-stu-id="cd597-153">Five</span></span>|<span data-ttu-id="cd597-154">發生任何限定的失敗狀況時。</span><span class="sxs-lookup"><span data-stu-id="cd597-154">On any qualified failure conditions.</span></span> <span data-ttu-id="cd597-155">滿足任何狀況的較低值，或者發生限定失敗狀況。</span><span class="sxs-lookup"><span data-stu-id="cd597-155">Any condition of lower value is satisfied or a qualifying failure condition occurs.</span></span>|  
  
         <span data-ttu-id="cd597-156">如需容錯移轉條件層級的詳細資訊，請參閱[可用性群組自動容錯移轉的彈性容錯移轉原則 &#40;SQL Server&#41;](flexible-automatic-failover-policy-availability-group.md)。</span><span class="sxs-lookup"><span data-stu-id="cd597-156">For more information about the failover condition levels, see [Flexible Failover Policy for Automatic Failover of an Availability Group &#40;SQL Server&#41;](flexible-automatic-failover-policy-availability-group.md).</span></span>  
  
    -   <span data-ttu-id="cd597-157">若要設定健全狀況檢查逾時臨界值，請使用 HEALTH_CHECK_TIMEOUT = *n* 選項，其中 *n* 是介於 15000 毫秒 (15 秒) 到 4294967295 毫秒之間的整數。</span><span class="sxs-lookup"><span data-stu-id="cd597-157">To configure the health check timeout threshold, use the HEALTH_CHECK_TIMEOUT = *n* option, where, *n* is an integer from 15000 milliseconds (15 seconds) to 4294967295 milliseconds.</span></span> <span data-ttu-id="cd597-158">預設值為 30000 毫秒 (30 秒)。</span><span class="sxs-lookup"><span data-stu-id="cd597-158">The default value is 30000 milliseconds (30 seconds)</span></span>  
  
         <span data-ttu-id="cd597-159">例如，下列 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式會將現有可用性群組 `AG1`的健全狀況檢查逾時臨界值變更為 60,000 毫秒 (一分鐘)。</span><span class="sxs-lookup"><span data-stu-id="cd597-159">For example, the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement changes the health-check timeout threshold of an existing availability group, `AG1`, to 60,000 milliseconds (one minute).</span></span>  
  
        ```sql
        ALTER AVAILABILITY GROUP AG1 SET (HEALTH_CHECK_TIMEOUT = 60000);  
        ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="cd597-160">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="cd597-160">Using PowerShell</span></span>  

### <a name="to-configure-the-flexible-failover-policy"></a><span data-ttu-id="cd597-161">若要設定彈性容錯移轉原則 \* \*</span><span class="sxs-lookup"><span data-stu-id="cd597-161">To configure the flexible failover policy\*\*</span></span>  
  
1.  <span data-ttu-id="cd597-162">將預設值 (`cd`) 設定為裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="cd597-162">Set default (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="cd597-163">將可用性複本加入至可用性群組時，請使用 `New-SqlAvailabilityGroup` 指令程式。</span><span class="sxs-lookup"><span data-stu-id="cd597-163">When adding an availability replica to an availability group, use the `New-SqlAvailabilityGroup` cmdlet.</span></span> <span data-ttu-id="cd597-164">修改現有的可用性複本時，請使用 `Set-SqlAvailabilityGroup` 指令程式。</span><span class="sxs-lookup"><span data-stu-id="cd597-164">When modifying an existing availability replica, use the `Set-SqlAvailabilityGroup` cmdlet.</span></span>  
  
    -   <span data-ttu-id="cd597-165">若要設定容錯移轉狀況層級，請使用 `FailureConditionLevel` *level*參數，其中*level*是下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="cd597-165">To set the failover condition level, use the `FailureConditionLevel`*level* parameter, where, *level* is one of the following values:</span></span>  
  
        |<span data-ttu-id="cd597-166">值</span><span class="sxs-lookup"><span data-stu-id="cd597-166">Value</span></span>|<span data-ttu-id="cd597-167">層級</span><span class="sxs-lookup"><span data-stu-id="cd597-167">Level</span></span>|<span data-ttu-id="cd597-168">起始自動容錯移轉的狀況</span><span class="sxs-lookup"><span data-stu-id="cd597-168">Automatic Is Failover Initiated When...</span></span>|  
        |-----------|-----------|-------------------------------------------|  
        |`OnServerDown`|<span data-ttu-id="cd597-169">一個</span><span class="sxs-lookup"><span data-stu-id="cd597-169">One</span></span>|<span data-ttu-id="cd597-170">伺服器關閉時。</span><span class="sxs-lookup"><span data-stu-id="cd597-170">On server down.</span></span> <span data-ttu-id="cd597-171">SQL Server 服務由於容錯移轉或重新啟動而停止。</span><span class="sxs-lookup"><span data-stu-id="cd597-171">The SQL Server service stops because of a failover or restart.</span></span>|  
        |`OnServerUnresponsive`|<span data-ttu-id="cd597-172">兩個</span><span class="sxs-lookup"><span data-stu-id="cd597-172">Two</span></span>|<span data-ttu-id="cd597-173">伺服器沒有回應時。</span><span class="sxs-lookup"><span data-stu-id="cd597-173">On server unresponsive.</span></span> <span data-ttu-id="cd597-174">滿足任何狀況的較低值，而且 SQL Server 服務連接到叢集且超過健全狀況檢查逾時臨界值，或者目前主要複本處於失敗狀態。</span><span class="sxs-lookup"><span data-stu-id="cd597-174">Any condition of lower value is satisfied, the SQL Server service is connected to the cluster and the health check timeout threshold is exceeded, or the current primary replica is in a failed state.</span></span>|  
        |`OnCriticalServerError`|<span data-ttu-id="cd597-175">三</span><span class="sxs-lookup"><span data-stu-id="cd597-175">Three</span></span>|<span data-ttu-id="cd597-176">發生嚴重伺服器錯誤時。</span><span class="sxs-lookup"><span data-stu-id="cd597-176">On critical server error.</span></span> <span data-ttu-id="cd597-177">滿足任何狀況的較低值，或者發生內部嚴重伺服器錯誤。</span><span class="sxs-lookup"><span data-stu-id="cd597-177">Any condition of lower value is satisfied or an internal critical server error occurs.</span></span><br /><br /> <span data-ttu-id="cd597-178">這是預設層級。</span><span class="sxs-lookup"><span data-stu-id="cd597-178">This is the default level.</span></span>|  
        |`OnModerateServerError`|<span data-ttu-id="cd597-179">四</span><span class="sxs-lookup"><span data-stu-id="cd597-179">Four</span></span>|<span data-ttu-id="cd597-180">發生一般伺服器錯誤時。</span><span class="sxs-lookup"><span data-stu-id="cd597-180">On moderate server error.</span></span> <span data-ttu-id="cd597-181">滿足任何狀況的較低值，或者發生一般伺服器錯誤。</span><span class="sxs-lookup"><span data-stu-id="cd597-181">Any condition of lower value is satisfied or a moderate Server error occurs.</span></span>|  
        |`OnAnyQualifiedFailureConditions`|<span data-ttu-id="cd597-182">五</span><span class="sxs-lookup"><span data-stu-id="cd597-182">Five</span></span>|<span data-ttu-id="cd597-183">發生任何限定的失敗狀況時。</span><span class="sxs-lookup"><span data-stu-id="cd597-183">On any qualified failure conditions.</span></span> <span data-ttu-id="cd597-184">滿足任何狀況的較低值，或者發生限定失敗狀況。</span><span class="sxs-lookup"><span data-stu-id="cd597-184">Any condition of lower value is satisfied or a qualifying failure condition occurs.</span></span>|  
  
         <span data-ttu-id="cd597-185">如需容錯移轉條件層級的詳細資訊，請參閱[可用性群組自動容錯移轉的彈性容錯移轉原則 &#40;SQL Server&#41;](flexible-automatic-failover-policy-availability-group.md)。</span><span class="sxs-lookup"><span data-stu-id="cd597-185">For more information about the failover condition levels, see [Flexible Failover Policy for Automatic Failover of an Availability Group &#40;SQL Server&#41;](flexible-automatic-failover-policy-availability-group.md).</span></span>  
  
         <span data-ttu-id="cd597-186">例如，下列命令會將現有可用性群組 `AG1`的失敗狀況層級變更為層級一。</span><span class="sxs-lookup"><span data-stu-id="cd597-186">For example, the following command changes the failure-condition level of an existing availability group, `AG1`, to level one.</span></span>  
  
        ```powershell
        Set-SqlAvailabilityGroup `
         -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg `
         -FailureConditionLevel OnServerDown  
        ```  
  
    -   <span data-ttu-id="cd597-187">若要設定健全狀況檢查超時閾值，請使用 `HealthCheckTimeout` *n*參數，其中*n*是15000毫秒的整數， (15 秒) 到4294967295毫秒。</span><span class="sxs-lookup"><span data-stu-id="cd597-187">To set the health check timeout threshold, use the `HealthCheckTimeout`*n* parameter, where, *n* is an integer from 15000 milliseconds (15 seconds) to 4294967295 milliseconds.</span></span> <span data-ttu-id="cd597-188">預設值為 30000 毫秒 (30 秒)。</span><span class="sxs-lookup"><span data-stu-id="cd597-188">The default value is 30000 milliseconds (30 seconds).</span></span>  
  
         <span data-ttu-id="cd597-189">例如，下列命令會將現有可用性群組 `AG1`的健全狀況檢查逾時臨界值變更為 120,000 毫秒 (兩分鐘)。</span><span class="sxs-lookup"><span data-stu-id="cd597-189">For example, the following command changes the health-check timeout threshold of an existing availability group, `AG1`, to 120,000 milliseconds (two minutes).</span></span>  
  
        ```powershell
        Set-SqlAvailabilityGroup `
         -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAG `
         -HealthCheckTimeout 120000  
        ```  
  
> [!NOTE]  
>  <span data-ttu-id="cd597-190">若要檢視指令程式的語法，請在 `Get-Help` PowerShell 環境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 指令程式。</span><span class="sxs-lookup"><span data-stu-id="cd597-190">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="cd597-191">如需詳細資訊，請參閱 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="cd597-191">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="cd597-192">**若要設定和使用 SQL Server PowerShell 提供者**</span><span class="sxs-lookup"><span data-stu-id="cd597-192">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="cd597-193">SQL Server PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="cd597-193">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
-   [<span data-ttu-id="cd597-194">Get Help SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="cd597-194">Get Help SQL Server PowerShell</span></span>](../../../powershell/sql-server-powershell.md)  
  
## <a name="see-also"></a><span data-ttu-id="cd597-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd597-195">See Also</span></span>  
 <span data-ttu-id="cd597-196">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cd597-196">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="cd597-197">[可用性模式 (AlwaysOn 可用性群組) ](availability-modes-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="cd597-197">[Availability Modes (AlwaysOn Availability Groups)](availability-modes-always-on-availability-groups.md) </span></span>  
 <span data-ttu-id="cd597-198">[容錯移轉和容錯移轉模式 &#40;AlwaysOn 可用性群組&#41;](failover-and-failover-modes-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="cd597-198">[Failover and Failover Modes &#40;AlwaysOn Availability Groups&#41;](failover-and-failover-modes-always-on-availability-groups.md) </span></span>  
 <span data-ttu-id="cd597-199">[SQL Server 的 Windows Server 容錯移轉叢集 &#40;WSFC&#41;](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cd597-199">[Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md) </span></span>  
 <span data-ttu-id="cd597-200">[容錯移轉叢集執行個體的容錯移轉原則](../../../sql-server/failover-clusters/windows/failover-policy-for-failover-cluster-instances.md) </span><span class="sxs-lookup"><span data-stu-id="cd597-200">[Failover Policy for Failover Cluster Instances](../../../sql-server/failover-clusters/windows/failover-policy-for-failover-cluster-instances.md) </span></span>  
 [<span data-ttu-id="cd597-201">sp_server_diagnostics &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cd597-201">sp_server_diagnostics &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql)  
