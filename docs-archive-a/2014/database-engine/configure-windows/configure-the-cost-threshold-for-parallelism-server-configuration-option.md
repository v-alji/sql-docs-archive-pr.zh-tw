---
title: 設定 cost threshold for parallelism 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 10/26/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- cost threshold for parallelism option
ms.assetid: dad21bee-fe28-41f6-9d2f-e6ababfaf9db
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 675055a753e84ace3a4fcb44b41b8c914326c5c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592245"
---
# <a name="configure-the-cost-threshold-for-parallelism-server-configuration-option"></a><span data-ttu-id="71d4e-102">設定 cost threshold for parallelism 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="71d4e-102">Configure the cost threshold for parallelism Server Configuration Option</span></span>
  <span data-ttu-id="71d4e-103">此主題描述如何使用 **或** ，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中設定 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] cost threshold for parallelism [!INCLUDE[tsql](../../includes/tsql-md.md)]伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="71d4e-103">This topic describes how to configure the **cost threshold for parallelism** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="71d4e-104">**平行處理原則的成本臨界值** 選項指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 為查詢建立及執行平行計劃的臨界值。</span><span class="sxs-lookup"><span data-stu-id="71d4e-104">The **cost threshold for parallelism** option specifies the threshold at which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] creates and runs parallel plans for queries.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="71d4e-105">或 **或**。</span><span class="sxs-lookup"><span data-stu-id="71d4e-105">creates and runs a parallel plan for a query only when the estimated cost to run a serial plan for the same query is higher than the value set in **cost threshold for parallelism**.</span></span> <span data-ttu-id="71d4e-106">成本是指在特定硬體組態下，估計執行序列計畫所需的已耗用時間 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="71d4e-106">The cost refers to an estimated elapsed time in seconds required to run the serial plan on a specific hardware configuration.</span></span> <span data-ttu-id="71d4e-107">**cost threshold for parallelism** 選項可設成從 0 到 32767 的任何值。</span><span class="sxs-lookup"><span data-stu-id="71d4e-107">The **cost threshold for parallelism** option can be set to any value from 0 through 32767.</span></span> <span data-ttu-id="71d4e-108">預設值為 5。</span><span class="sxs-lookup"><span data-stu-id="71d4e-108">The default value is 5.</span></span>  
  
 <span data-ttu-id="71d4e-109">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="71d4e-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="71d4e-110">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="71d4e-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="71d4e-111">限制事項</span><span class="sxs-lookup"><span data-stu-id="71d4e-111">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="71d4e-112">建議</span><span class="sxs-lookup"><span data-stu-id="71d4e-112">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="71d4e-113">安全性</span><span class="sxs-lookup"><span data-stu-id="71d4e-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="71d4e-114">**使用下列方法設定 cost threshold for parallelism 選項：**</span><span class="sxs-lookup"><span data-stu-id="71d4e-114">**To configure the cost threshold for parallelism option, using:**</span></span>  
  
     [<span data-ttu-id="71d4e-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="71d4e-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="71d4e-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="71d4e-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="71d4e-117">**後續操作：** [設定平行處理原則的成本閾值選項之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="71d4e-117">**Follow Up:**  [After you configure the cost threshold for parallelism option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="71d4e-118">開始之前</span><span class="sxs-lookup"><span data-stu-id="71d4e-118">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="71d4e-119">限制事項</span><span class="sxs-lookup"><span data-stu-id="71d4e-119">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="71d4e-120">成本是指在特定硬體組態下，估計執行序列計畫所需的已耗用時間 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="71d4e-120">The cost refers to an estimated elapsed time in seconds required to run the serial plan on a specific hardware configuration.</span></span> <span data-ttu-id="71d4e-121">只有在對稱式多重處理器上才應該設定 **cost threshold for parallelism** 。</span><span class="sxs-lookup"><span data-stu-id="71d4e-121">Only set **cost threshold for parallelism** on symmetric multiprocessors.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="71d4e-122">會忽略 **或** 值：</span><span class="sxs-lookup"><span data-stu-id="71d4e-122">ignores the **cost threshold for parallelism** value under the following conditions:</span></span>  
  
    -   <span data-ttu-id="71d4e-123">您的電腦只有一個邏輯處理器。</span><span class="sxs-lookup"><span data-stu-id="71d4e-123">Your computer has only one logical processor.</span></span>  
  
    -   <span data-ttu-id="71d4e-124">因為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affinity mask **組態選項的關係，只有一個邏輯處理器可供** 使用。</span><span class="sxs-lookup"><span data-stu-id="71d4e-124">Only a single logical processor is available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] because of the **affinity mask** configuration option.</span></span>  
  
    -   <span data-ttu-id="71d4e-125">**max degree of parallelism** 選項設為 1。</span><span class="sxs-lookup"><span data-stu-id="71d4e-125">The **max degree of parallelism** option is set to 1.</span></span>  
  
 <span data-ttu-id="71d4e-126">邏輯處理器是處理器硬體的基本單位，允許作業系統分派工作或執行執行緒內容。</span><span class="sxs-lookup"><span data-stu-id="71d4e-126">A logical processor is the basic unit of processor hardware that allows the operating system to dispatch a task or execute a thread context.</span></span> <span data-ttu-id="71d4e-127">每個邏輯處理器一次只能執行一個執行緒內容。</span><span class="sxs-lookup"><span data-stu-id="71d4e-127">Each logical processor can execute only one thread context at a time.</span></span> <span data-ttu-id="71d4e-128">處理器核心是提供解碼及執行指令能力的電路。</span><span class="sxs-lookup"><span data-stu-id="71d4e-128">The processor core is the circuitry that provides ability to decode and execute instructions.</span></span> <span data-ttu-id="71d4e-129">處理器核心可能包含一個或多個邏輯處理器。</span><span class="sxs-lookup"><span data-stu-id="71d4e-129">A processor core may contain one or more logical processors.</span></span> <span data-ttu-id="71d4e-130">下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢可用於取得系統的 CPU 資訊。</span><span class="sxs-lookup"><span data-stu-id="71d4e-130">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] query can be used for obtaining CPU information for the system.</span></span>  
  
```  
SELECT (cpu_count / hyperthread_ratio) AS PhysicalCPUs,   
cpu_count AS logicalCPUs   
FROM sys.dm_os_sys_info  
```  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="71d4e-131">建議</span><span class="sxs-lookup"><span data-stu-id="71d4e-131">Recommendations</span></span>  
  
-   <span data-ttu-id="71d4e-132">這個選項是進階選項，只有有經驗的資料庫管理員或通過認證的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術人員才可變更。</span><span class="sxs-lookup"><span data-stu-id="71d4e-132">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="71d4e-133">在某些狀況下，即使查詢的成本計畫小於目前的 **cost threshold for parallelism** 值，還是會選擇平行計畫。</span><span class="sxs-lookup"><span data-stu-id="71d4e-133">In certain cases, a parallel plan may be chosen even though the query's cost plan is less than the current **cost threshold for parallelism** value.</span></span> <span data-ttu-id="71d4e-134">之所以會發生這種情形，是因為在決定要使用平行或序列計畫時，所依據的成本預估值是在完成整體最佳化之前提供的。</span><span class="sxs-lookup"><span data-stu-id="71d4e-134">This can happen because the decision to use a parallel or serial plan is based on a cost estimate provided before the full optimization is complete.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="71d4e-135">Security</span><span class="sxs-lookup"><span data-stu-id="71d4e-135">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="71d4e-136">權限</span><span class="sxs-lookup"><span data-stu-id="71d4e-136">Permissions</span></span>  
 <span data-ttu-id="71d4e-137">不含參數或只含第一個參數之 **sp_configure** 上的執行權限預設會授與所有使用者。</span><span class="sxs-lookup"><span data-stu-id="71d4e-137">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="71d4e-138">以同時設定兩個參數的 **sp_configure** 來變更組態選項或執行 RECONFIGURE 陳述式時，使用者必須取得 ALTER SETTINGS 伺服器層級權限。</span><span class="sxs-lookup"><span data-stu-id="71d4e-138">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="71d4e-139">**系統管理員 (sysadmin)** 及 **serveradmin** 固定伺服器角色會隱含 ALTER SETTINGS 權限。</span><span class="sxs-lookup"><span data-stu-id="71d4e-139">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="71d4e-140">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="71d4e-140">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-cost-threshold-for-parallelism-option"></a><span data-ttu-id="71d4e-141">設定 cost threshold for parallelism 選項</span><span class="sxs-lookup"><span data-stu-id="71d4e-141">To configure the cost threshold for parallelism option</span></span>  
  
1.  <span data-ttu-id="71d4e-142">在物件總管中，請以滑鼠右鍵按一下伺服器，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="71d4e-142">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="71d4e-143">按一下 **[進階]** 節點。</span><span class="sxs-lookup"><span data-stu-id="71d4e-143">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="71d4e-144">在 **[平行處理原則]** 下，將 **[CostThresholdForParallelism]** 選項變更為所需的值。</span><span class="sxs-lookup"><span data-stu-id="71d4e-144">Under **Parallelism**, change the **CostThresholdForParallelism** option to the value you want.</span></span> <span data-ttu-id="71d4e-145">輸入或選取 0 到 32767 之間的值。</span><span class="sxs-lookup"><span data-stu-id="71d4e-145">Type or select a value from 0 to 32767.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="71d4e-146">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="71d4e-146">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-cost-threshold-for-parallelism-option"></a><span data-ttu-id="71d4e-147">設定 cost threshold for parallelism 選項</span><span class="sxs-lookup"><span data-stu-id="71d4e-147">To configure the cost threshold for parallelism option</span></span>  
  
1.  <span data-ttu-id="71d4e-148">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="71d4e-148">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="71d4e-149">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="71d4e-149">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="71d4e-150">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="71d4e-150">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="71d4e-151">此範例示範如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 將 `cost threshold for parallelism` 選項的值設定為 `10`。</span><span class="sxs-lookup"><span data-stu-id="71d4e-151">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `cost threshold for parallelism` option to `10`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'cost threshold for parallelism', 10 ;  
GO  
RECONFIGURE  
GO  
```  
  
 <span data-ttu-id="71d4e-152">如需詳細資訊，請參閱 [伺服器設定選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md)伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="71d4e-152">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-cost-threshold-for-parallelism-option"></a><a name="FollowUp"></a> <span data-ttu-id="71d4e-153">後續操作：設定平行處理原則的成本閾值選項之後</span><span class="sxs-lookup"><span data-stu-id="71d4e-153">Follow Up: After you configure the cost threshold for parallelism option</span></span>  
 <span data-ttu-id="71d4e-154">設定會立即生效，不需要重新啟動伺服器。</span><span class="sxs-lookup"><span data-stu-id="71d4e-154">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71d4e-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71d4e-155">See Also</span></span>  
 <span data-ttu-id="71d4e-156">[設定平行索引作業](../../relational-databases/indexes/configure-parallel-index-operations.md) </span><span class="sxs-lookup"><span data-stu-id="71d4e-156">[Configure Parallel Index Operations](../../relational-databases/indexes/configure-parallel-index-operations.md) </span></span>  
 <span data-ttu-id="71d4e-157">[查詢提示 &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query) </span><span class="sxs-lookup"><span data-stu-id="71d4e-157">[Query Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query) </span></span>  
 <span data-ttu-id="71d4e-158">[ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-workload-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="71d4e-158">[ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-workload-group-transact-sql) </span></span>  
 <span data-ttu-id="71d4e-159">[affinity mask 伺服器組態選項](affinity-mask-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="71d4e-159">[affinity mask Server Configuration Option](affinity-mask-server-configuration-option.md) </span></span>  
 <span data-ttu-id="71d4e-160">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="71d4e-160">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="71d4e-161">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="71d4e-161">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="71d4e-162">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="71d4e-162">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
