---
title: 設定 max worker threads 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- worker threads [SQL Server]
- max worker threads option
ms.assetid: abeadfa4-a14d-469a-bacf-75812e48fac1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4881cefee350d34d93b539c56be6f43866d3ddfe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597345"
---
# <a name="configure-the-max-worker-threads-server-configuration-option"></a><span data-ttu-id="b6131-102">設定 max worker threads 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="b6131-102">Configure the max worker threads Server Configuration Option</span></span>
  <span data-ttu-id="b6131-103">此主題描述如何使用 **或** ，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中設定 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] max worker threads [!INCLUDE[tsql](../../includes/tsql-md.md)]伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="b6131-103">This topic describes how to configure the **max worker threads** server configuration option in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="b6131-104">**max worker threads** 選項會設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 處理序可使用的工作者執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="b6131-104">The **max worker threads** option configures the number of worker threads that are available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] processes.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b6131-105">使用作業系統的原生執行緒服務，因此會有一個或多個執行緒同時支援 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所支援的每個網路、由另一個執行緒負責處理資料庫檢查點，而所有使用者則由一個執行緒集區負責處理。</span><span class="sxs-lookup"><span data-stu-id="b6131-105">uses the native thread services of the operating systems so that one or more threads support each network that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supports simultaneously, another thread handles database checkpoints, and a pool of threads handles all users.</span></span> <span data-ttu-id="b6131-106">**max worker threads** 的預設值是 0。</span><span class="sxs-lookup"><span data-stu-id="b6131-106">The default value for **max worker threads** is 0.</span></span> <span data-ttu-id="b6131-107">這會讓 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在啟動時自動設定工作者執行緒的數目。</span><span class="sxs-lookup"><span data-stu-id="b6131-107">This enables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to automatically configure the number of worker threads at startup.</span></span> <span data-ttu-id="b6131-108">此預設值對大多數系統都是最佳的。</span><span class="sxs-lookup"><span data-stu-id="b6131-108">The default setting is best for most systems.</span></span> <span data-ttu-id="b6131-109">但依系統組態而定，將 **max worker threads** 設為特定的值有時候可提高效能。</span><span class="sxs-lookup"><span data-stu-id="b6131-109">However, depending on your system configuration, setting **max worker threads** to a specific value sometimes improves performance.</span></span>  
  
 <span data-ttu-id="b6131-110">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="b6131-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b6131-111">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="b6131-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b6131-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="b6131-112">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="b6131-113">建議</span><span class="sxs-lookup"><span data-stu-id="b6131-113">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="b6131-114">安全性</span><span class="sxs-lookup"><span data-stu-id="b6131-114">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b6131-115">**使用下列方法設定 max worker threads 選項：**</span><span class="sxs-lookup"><span data-stu-id="b6131-115">**To configure the max worker threads option, using:**</span></span>  
  
     [<span data-ttu-id="b6131-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b6131-116">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b6131-117">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b6131-117">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="b6131-118">**後續操作：** [設定 max worker threads 選項之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="b6131-118">**Follow Up:**  [After you configure the max worker threads option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b6131-119">開始之前</span><span class="sxs-lookup"><span data-stu-id="b6131-119">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="b6131-120">限制事項</span><span class="sxs-lookup"><span data-stu-id="b6131-120">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="b6131-121">當實際的查詢要求數目小於 **max worker threads**的設定值時，就會由一個執行緒處理每一個查詢要求。</span><span class="sxs-lookup"><span data-stu-id="b6131-121">When the actual number of query requests is less than the amount set in **max worker threads**, one thread handles each query request.</span></span> <span data-ttu-id="b6131-122">不過，如果實際的查詢要求數目超過 [**最大工作者執行緒**] 中設定的數量，則 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會將背景工作執行緒集區，讓下一個可用的工作者執行緒可以處理要求。</span><span class="sxs-lookup"><span data-stu-id="b6131-122">However, if the actual number of query request exceeds the amount set in **max worker threads**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pools the worker threads so that the next available worker thread can handle the request.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="b6131-123">建議</span><span class="sxs-lookup"><span data-stu-id="b6131-123">Recommendations</span></span>  
  
-   <span data-ttu-id="b6131-124">這個選項是進階選項，只有有經驗的資料庫管理員或通過認證的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術人員才可變更。</span><span class="sxs-lookup"><span data-stu-id="b6131-124">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="b6131-125">當大量用戶端連接到伺服器時，執行緒集區有助於最佳化效能。</span><span class="sxs-lookup"><span data-stu-id="b6131-125">Thread pooling helps optimize performance when large numbers of clients are connected to the server.</span></span> <span data-ttu-id="b6131-126">通常，會針對每一個查詢要求建立個別的作業系統執行緒。</span><span class="sxs-lookup"><span data-stu-id="b6131-126">Usually, a separate operating system thread is created for each query request.</span></span> <span data-ttu-id="b6131-127">然而，在數以百計的伺服器連接之下，若每個查詢要求都使用一個執行緒，反而會耗用大量的系統資源。</span><span class="sxs-lookup"><span data-stu-id="b6131-127">However, with hundreds of connections to the server, using one thread per query request can consume large amounts of system resources.</span></span> <span data-ttu-id="b6131-128">**max worker threads** 選項可讓 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 建立工作者執行緒集區，以服務更多的查詢要求數量，進而改善效能。</span><span class="sxs-lookup"><span data-stu-id="b6131-128">The **max worker threads** option enables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to create a pool of worker threads to service a larger number of query requests, which improves performance.</span></span>  
  
-   <span data-ttu-id="b6131-129">下表顯示為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的不同 CPU 和版本組合自動設定的最大工作者執行緒數。</span><span class="sxs-lookup"><span data-stu-id="b6131-129">The following table shows the automatically configured number of max worker threads for various combinations of CPUs and versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
    |<span data-ttu-id="b6131-130">CPU 數</span><span class="sxs-lookup"><span data-stu-id="b6131-130">Number of CPUs</span></span>|<span data-ttu-id="b6131-131">32 位元電腦</span><span class="sxs-lookup"><span data-stu-id="b6131-131">32-bit computer</span></span>|<span data-ttu-id="b6131-132">64 位元電腦</span><span class="sxs-lookup"><span data-stu-id="b6131-132">64-bit computer</span></span>|  
    |--------------------|----------------------|----------------------|  
    |<span data-ttu-id="b6131-133">\<= 4 個處理器</span><span class="sxs-lookup"><span data-stu-id="b6131-133">\<= 4 processors</span></span>|<span data-ttu-id="b6131-134">256</span><span class="sxs-lookup"><span data-stu-id="b6131-134">256</span></span>|<span data-ttu-id="b6131-135">512</span><span class="sxs-lookup"><span data-stu-id="b6131-135">512</span></span>|  
    |<span data-ttu-id="b6131-136">8 個處理器</span><span class="sxs-lookup"><span data-stu-id="b6131-136">8 processors</span></span>|<span data-ttu-id="b6131-137">288</span><span class="sxs-lookup"><span data-stu-id="b6131-137">288</span></span>|<span data-ttu-id="b6131-138">576</span><span class="sxs-lookup"><span data-stu-id="b6131-138">576</span></span>|  
    |<span data-ttu-id="b6131-139">16 個處理器</span><span class="sxs-lookup"><span data-stu-id="b6131-139">16 processors</span></span>|<span data-ttu-id="b6131-140">352</span><span class="sxs-lookup"><span data-stu-id="b6131-140">352</span></span>|<span data-ttu-id="b6131-141">704</span><span class="sxs-lookup"><span data-stu-id="b6131-141">704</span></span>|  
    |<span data-ttu-id="b6131-142">32 個處理器</span><span class="sxs-lookup"><span data-stu-id="b6131-142">32 processors</span></span>|<span data-ttu-id="b6131-143">480</span><span class="sxs-lookup"><span data-stu-id="b6131-143">480</span></span>|<span data-ttu-id="b6131-144">960</span><span class="sxs-lookup"><span data-stu-id="b6131-144">960</span></span>|  
    |<span data-ttu-id="b6131-145">64 個處理器</span><span class="sxs-lookup"><span data-stu-id="b6131-145">64 processors</span></span>|<span data-ttu-id="b6131-146">736</span><span class="sxs-lookup"><span data-stu-id="b6131-146">736</span></span>|<span data-ttu-id="b6131-147">1472</span><span class="sxs-lookup"><span data-stu-id="b6131-147">1472</span></span>|  
    |<span data-ttu-id="b6131-148">128 個處理器</span><span class="sxs-lookup"><span data-stu-id="b6131-148">128 processors</span></span>|<span data-ttu-id="b6131-149">4224</span><span class="sxs-lookup"><span data-stu-id="b6131-149">4224</span></span>|<span data-ttu-id="b6131-150">4480</span><span class="sxs-lookup"><span data-stu-id="b6131-150">4480</span></span>|  
    |<span data-ttu-id="b6131-151">256 個處理器</span><span class="sxs-lookup"><span data-stu-id="b6131-151">256 processors</span></span>|<span data-ttu-id="b6131-152">8320</span><span class="sxs-lookup"><span data-stu-id="b6131-152">8320</span></span>|<span data-ttu-id="b6131-153">8576</span><span class="sxs-lookup"><span data-stu-id="b6131-153">8576</span></span>|  
  
    > [!NOTE]  
    >  <span data-ttu-id="b6131-154">如需有關使用超過 64 個 CPU 的建議事項，請參閱 [在超過 64 個 CPU 之電腦上執行 SQL Server 的最佳作法](https://technet.microsoft.com/library/ee210547\(SQL.105\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="b6131-154">For recommendations on using more than 64 CPUs, refer to [Best Practices for Running SQL Server on Computers That Have More Than 64 CPUs](https://technet.microsoft.com/library/ee210547\(SQL.105\).aspx).</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="b6131-155">建議在 32 位元電腦上執行的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的最大工作者執行緒設為 1024。</span><span class="sxs-lookup"><span data-stu-id="b6131-155">We recommend 1024 as the maximum number of worker threads for an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is running on a 32-bit computer.</span></span>  
  
-   <span data-ttu-id="b6131-156">當所有的工作者執行緒都在進行長時間執行的查詢時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可能會反應遲緩，直到工作者執行緒完成並恢復為可用狀態為止。</span><span class="sxs-lookup"><span data-stu-id="b6131-156">When all worker threads are active with long running queries, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] might appear unresponsive until a worker thread completes and becomes available.</span></span> <span data-ttu-id="b6131-157">雖然這不算是瑕疵，但有時卻讓人困擾。</span><span class="sxs-lookup"><span data-stu-id="b6131-157">Although this is not a defect, it can sometimes be undesirable.</span></span> <span data-ttu-id="b6131-158">若處理序反應遲緩，而且無法處理新查詢，請使用專用管理員連接 (DAC) 來連接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，然後清除處理序。</span><span class="sxs-lookup"><span data-stu-id="b6131-158">If a process appears to be unresponsive and no new queries can be processed, then connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the dedicated administrator connection (DAC), and kill the process.</span></span> <span data-ttu-id="b6131-159">若要避免這個問題，請增加 max worker threads 的最大數目。</span><span class="sxs-lookup"><span data-stu-id="b6131-159">To prevent this, increase the number of max worker threads.</span></span>  
  
 <span data-ttu-id="b6131-160">**max worker threads** 伺服器組態選項不會將所有系統工作 (例如可用性群組、Service Broker、鎖定管理員與其他工作) 需要的執行緒納入考量。</span><span class="sxs-lookup"><span data-stu-id="b6131-160">The **max worker threads** server configuration option does not take into account threads that are required for all the system tasks such as Availibility Groups, Service Broker, Lock Manager, and others.</span></span>  <span data-ttu-id="b6131-161">如果超過設定的執行緒數目，下列查詢會提供已產生其他執行緒之系統工作的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b6131-161">If the number of threads configured are being exceeded, the following query will provide information about the system tasks that have spawned the additional threads.</span></span>  
  
```  
SELECT  
s.session_id,  
r.command,  
r.status,  
r.wait_type,  
r.scheduler_id,  
w.worker_address,  
w.is_preemptive,  
w.state,  
t.task_state,  
t.session_id,  
t.exec_context_id,  
t.request_id  
FROM sys.dm_exec_sessions AS s  
INNERJOIN sys.dm_exec_requests AS r  
    ON s.session_id = r.session_id  
INNER JOIN sys.dm_os_tasks AS t  
    ON r.task_address = t.task_address  
INNER JOIN sys.dm_os_workers AS w  
    ON t.worker_address = w.worker_address  
WHERE s.is_user_process = 0;  
  
```  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b6131-162">Security</span><span class="sxs-lookup"><span data-stu-id="b6131-162">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b6131-163">權限</span><span class="sxs-lookup"><span data-stu-id="b6131-163">Permissions</span></span>  
 <span data-ttu-id="b6131-164">不含參數或只含第一個參數之 **sp_configure** 上的執行權限預設會授與所有使用者。</span><span class="sxs-lookup"><span data-stu-id="b6131-164">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="b6131-165">以同時設定兩個參數的 **sp_configure** 來變更組態選項或執行 RECONFIGURE 陳述式時，使用者必須取得 ALTER SETTINGS 伺服器層級權限。</span><span class="sxs-lookup"><span data-stu-id="b6131-165">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="b6131-166">**系統管理員 (sysadmin)** 及 **serveradmin** 固定伺服器角色會隱含 ALTER SETTINGS 權限。</span><span class="sxs-lookup"><span data-stu-id="b6131-166">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b6131-167">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b6131-167">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-max-worker-threads-option"></a><span data-ttu-id="b6131-168">設定 max worker threads 選項</span><span class="sxs-lookup"><span data-stu-id="b6131-168">To configure the max worker threads option</span></span>  
  
1.  <span data-ttu-id="b6131-169">在物件總管中，請以滑鼠右鍵按一下伺服器，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="b6131-169">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="b6131-170">按一下 **[處理器]** 節點。</span><span class="sxs-lookup"><span data-stu-id="b6131-170">Click the **Processors** node.</span></span>  
  
3.  <span data-ttu-id="b6131-171">在 [**最大工作者執行緒**] 方塊中，輸入或選取從128到32767的值。</span><span class="sxs-lookup"><span data-stu-id="b6131-171">In the **Max worker threads** box, type or select a value from 128 through 32767.</span></span>  
  
     <span data-ttu-id="b6131-172">**Max worker threads** 選項可用來設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 處理序可使用的工作者執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="b6131-172">Use the **max worker threads** option to configure the number of worker threads available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] processes.</span></span> <span data-ttu-id="b6131-173">**max worker threads** 的預設值對大部份系統而言都是最合適的。</span><span class="sxs-lookup"><span data-stu-id="b6131-173">The default setting for **max worker threads** is best for most systems.</span></span> <span data-ttu-id="b6131-174">但依系統組態而定，將 **max worker threads** 設為較小的值有時候可提高效能。</span><span class="sxs-lookup"><span data-stu-id="b6131-174">However, depending on your system configuration, setting **max worker threads** to a smaller value sometimes improves performance.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b6131-175">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b6131-175">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-max-worker-threads-option"></a><span data-ttu-id="b6131-176">設定 max worker threads 選項</span><span class="sxs-lookup"><span data-stu-id="b6131-176">To configure the max worker threads option</span></span>  
  
1.  <span data-ttu-id="b6131-177">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b6131-177">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b6131-178">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="b6131-178">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b6131-179">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="b6131-179">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="b6131-180">此範例示範如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 將 `max worker threads` 選項設定為 `900`。</span><span class="sxs-lookup"><span data-stu-id="b6131-180">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to configure the `max worker threads` option to `900`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'max worker threads', 900 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="b6131-181">如需詳細資訊，請參閱 [伺服器設定選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md)伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="b6131-181">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-max-worker-threads-option"></a><a name="FollowUp"></a> <span data-ttu-id="b6131-182">後續操作：設定最大背景工作執行緒選項之後</span><span class="sxs-lookup"><span data-stu-id="b6131-182">Follow Up: After you configure the max worker threads option</span></span>  
 <span data-ttu-id="b6131-183">變更立即生效，不需要重新啟動 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b6131-183">The change will take effect immediately without requiring the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to restart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6131-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6131-184">See Also</span></span>  
 <span data-ttu-id="b6131-185">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b6131-185">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="b6131-186">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b6131-186">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="b6131-187">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b6131-187">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="b6131-188">資料庫管理員的診斷連接</span><span class="sxs-lookup"><span data-stu-id="b6131-188">Diagnostic Connection for Database Administrators</span></span>](diagnostic-connection-for-database-administrators.md)  
  
  
