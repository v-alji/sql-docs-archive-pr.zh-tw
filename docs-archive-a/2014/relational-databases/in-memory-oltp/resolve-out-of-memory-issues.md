---
title: 解決記憶體不足問題 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f855e931-7502-44bd-8a8b-b8543645c7f4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f5f57725d559b0cd62679550e2bb7c04dbd7e2bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594557"
---
# <a name="resolve-out-of-memory-issues"></a><span data-ttu-id="a38fd-102">解決記憶體不足問題</span><span class="sxs-lookup"><span data-stu-id="a38fd-102">Resolve Out Of Memory Issues</span></span>
  [!INCLUDE[hek_1](../../includes/hek-1-md.md)] <span data-ttu-id="a38fd-103">所使用的記憶體比 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]更多，而且使用方式也不同。</span><span class="sxs-lookup"><span data-stu-id="a38fd-103">uses more memory and in different ways than does [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a38fd-104">您所安裝並配置給 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 的記憶體數量可能會變得不足以支應成長的需求。</span><span class="sxs-lookup"><span data-stu-id="a38fd-104">It is possible that the amount of memory you installed and allocated for [!INCLUDE[hek_2](../../includes/hek-2-md.md)] becomes inadequate for your growing needs.</span></span> <span data-ttu-id="a38fd-105">若是如此，您可能會用完記憶體。</span><span class="sxs-lookup"><span data-stu-id="a38fd-105">If so, you could run out of memory.</span></span> <span data-ttu-id="a38fd-106">本主題將說明如何從 OOM 情況中復原。</span><span class="sxs-lookup"><span data-stu-id="a38fd-106">This topic covers how to recover from an OOM situation.</span></span> <span data-ttu-id="a38fd-107">如需可協助您避免多種 OOM 情況的指引，請參閱 [監視與疑難排解記憶體使用量](monitor-and-troubleshoot-memory-usage.md) 。</span><span class="sxs-lookup"><span data-stu-id="a38fd-107">See [Monitor and Troubleshoot Memory Usage](monitor-and-troubleshoot-memory-usage.md) for guidance that can help you avoid many OOM situations.</span></span>  
  
## <a name="covered-in-this-topic"></a><span data-ttu-id="a38fd-108">本主題所涵蓋的內容</span><span class="sxs-lookup"><span data-stu-id="a38fd-108">Covered in this topic</span></span>  
  
|<span data-ttu-id="a38fd-109">主題</span><span class="sxs-lookup"><span data-stu-id="a38fd-109">Topic</span></span>|<span data-ttu-id="a38fd-110">概觀</span><span class="sxs-lookup"><span data-stu-id="a38fd-110">Overview</span></span>|  
|-----------|--------------|  
| [<span data-ttu-id="a38fd-111">解決由於 OOM 所造成的資料庫還原失敗</span><span class="sxs-lookup"><span data-stu-id="a38fd-111">Resolve database restore failures due to OOM</span></span>](#resolve-database-restore-failures-due-to-oom) |<span data-ttu-id="a38fd-112">如果收到錯誤訊息：「資料庫 ' *\<databaseName>* ' 還原作業因為資源集區 ' *\<resourcePoolName>* ' 中的記憶體不足而失敗」，該怎麼辦。</span><span class="sxs-lookup"><span data-stu-id="a38fd-112">What to do if you get the error message, "Restore operation failed for database '*\<databaseName>*' due to insufficient memory in the resource pool '*\<resourcePoolName>*'."</span></span>|  
| [<span data-ttu-id="a38fd-113">解決低記憶體或 OOM 狀況對於工作負載的影響</span><span class="sxs-lookup"><span data-stu-id="a38fd-113">Resolve impact of low memory or OOM conditions on the workload</span></span>](#resolve-impact-of-low-memory-or-oom-conditions-on-the-workload)|<span data-ttu-id="a38fd-114">如果您發現低記憶體問題對於效能造成負面影響，該怎麼辦。</span><span class="sxs-lookup"><span data-stu-id="a38fd-114">What to do if you find low memory issues are negatively impacting performance.</span></span>|  
| [<span data-ttu-id="a38fd-115">解決有足夠的記憶體可用但卻記憶體不足所造成的頁面配置失敗</span><span class="sxs-lookup"><span data-stu-id="a38fd-115">Resolve page allocation failures due to insufficient memory when sufficient memory is available</span></span>](#resolve-page-allocation-failures-due-to-insufficient-memory-when-sufficient-memory-is-available) |<span data-ttu-id="a38fd-116">如果收到錯誤訊息：「不允許資料庫 ' *\<databaseName>* ' 的頁面配置，因為資源集區 ' *\<resourcePoolName>* ' 中的記憶體不足」，該怎麼辦。</span><span class="sxs-lookup"><span data-stu-id="a38fd-116">What to do if you get the error message, "Disallowing page allocations for database '*\<databaseName>*' due to insufficient memory in the resource pool '*\<resourcePoolName>*'.</span></span> <span data-ttu-id="a38fd-117">...」(前提是可用的記憶體足夠供執行作業)。</span><span class="sxs-lookup"><span data-stu-id="a38fd-117">..." when available memory is sufficient for the operation.</span></span>|  
  
## <a name="resolve-database-restore-failures-due-to-oom"></a><span data-ttu-id="a38fd-118">解決由於 OOM 所造成的資料庫還原失敗</span><span class="sxs-lookup"><span data-stu-id="a38fd-118">Resolve database restore failures due to OOM</span></span>  
 <span data-ttu-id="a38fd-119">當您嘗試還原資料庫時，可能會收到錯誤訊息：「資料庫 ' ' 的還原作業失敗， *\<databaseName>* 因為資源集區 ' ' 中的記憶體不足」 *\<resourcePoolName>* 。在您成功還原資料庫之前，您必須藉由提供更多記憶體來解決記憶體不足的問題。</span><span class="sxs-lookup"><span data-stu-id="a38fd-119">When you attempt to restore a database you may get the error message: "Restore operation failed for database '*\<databaseName>*' due to insufficient memory in the resource pool '*\<resourcePoolName>*'." Before you can successfully restore the database you must resolve the insufficient memory issue by making more memory available.</span></span>  
  
 <span data-ttu-id="a38fd-120">若要解決由於 OOM 所造成的復原失敗，請使用下列任何或所有方法來暫時增加復原作業可用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="a38fd-120">To resolve recovery failure due to OOM increase available memory using any or al of these means to temporarily increase memory available for the recovery operation.</span></span>  
  
-   <span data-ttu-id="a38fd-121">暫時關閉執行中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a38fd-121">Temporarily close running applications.</span></span>   
    <span data-ttu-id="a38fd-122">透過關閉一個或多個執行中的應用程式 (例如 Visual Studio、Internet Explorer、OneNote 和其他應用程式)，就可以將這些應用程式所使用的記憶體提供給還原作業。</span><span class="sxs-lookup"><span data-stu-id="a38fd-122">By closing one or more running applications, such as Visual Studio, Internet Explorer, OneNote, and others, you make the memory they were using available for the restore operation.</span></span> <span data-ttu-id="a38fd-123">您可以在成功還原之後重新啟動這些應用程式。</span><span class="sxs-lookup"><span data-stu-id="a38fd-123">You can restart them following the successful restore.</span></span>  
  
-   <span data-ttu-id="a38fd-124">提高 MAX_MEMORY_PERCENT 的值。</span><span class="sxs-lookup"><span data-stu-id="a38fd-124">Increase the value of MAX_MEMORY_PERCENT.</span></span>   
    <span data-ttu-id="a38fd-125">這個程式碼片段會將資源集區 PoolHk 的 MAX_MEMORY_PERCENT 變更為已安裝記憶體的 70%。</span><span class="sxs-lookup"><span data-stu-id="a38fd-125">This code snippet changes MAX_MEMORY_PERCENT for the resource pool PoolHk to 70% of installed memory.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="a38fd-126">如果伺服器是在 VM 上執行，而且不是專用的，請將 MIN_MEMORY_PERCENT 設成與 MAX_MEMORY_PERCENT 相同的值。</span><span class="sxs-lookup"><span data-stu-id="a38fd-126">If the server is running on a VM and is not dedicated, set the value of MIN_MEMORY_PERCENT to the same value as MAX_MEMORY_PERCENT.</span></span>   
    > <span data-ttu-id="a38fd-127">請參閱[最佳做法：在 VM 環境使用記憶體內部 OLTP](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md)主題，以了解詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="a38fd-127">See the topic [Best Practices: Using In-Memory OLTP in a VM environment](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) for more information.</span></span>  
  
    ```sql  
  
    -- disable resource governor  
    ALTER RESOURCE GOVERNOR DISABLE  
  
    -- change the value of MAX_MEMORY_PERCENT  
    ALTER RESOURCE POOL PoolHk  
    WITH  
         ( MAX_MEMORY_PERCENT = 70 )  
    GO  
  
    -- reconfigure the Resource Governor  
    --    RECONFIGURE enables resource governor  
    ALTER RESOURCE GOVERNOR RECONFIGURE  
    GO  
  
    ```  
  
     <span data-ttu-id="a38fd-128">如需 MAX_MEMORY_PERCENT 最大值的詳細資訊，請參閱[適用于記憶體優化資料表和索引的記憶體百分比](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#percent-of-memory-available-for-memory-optimized-tables-and-indexes)主題一節。</span><span class="sxs-lookup"><span data-stu-id="a38fd-128">For information on maximum values for MAX_MEMORY_PERCENT see the topic section [Percent of memory available for memory-optimized tables and indexes](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#percent-of-memory-available-for-memory-optimized-tables-and-indexes)</span></span>
  
-   <span data-ttu-id="a38fd-129">重新設定 [最大伺服器記憶體]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a38fd-129">Reconfigure **max server memory**.</span></span>  
    <span data-ttu-id="a38fd-130">如需設定 [最大伺服器記憶體]\*\*\*\* 的資訊，請參閱[使用記憶體組態選項最佳化伺服器效能](https://technet.microsoft.com/library/ms177455\(v=SQL.105\).aspx)主題。</span><span class="sxs-lookup"><span data-stu-id="a38fd-130">For information on configuring **max server memory** see the topic [Optimizing Server Performance Using Memory Configuration Options](https://technet.microsoft.com/library/ms177455\(v=SQL.105\).aspx).</span></span>  
  
## <a name="resolve-impact-of-low-memory-or-oom-conditions-on-the-workload"></a><span data-ttu-id="a38fd-131">解決低記憶體或 OOM 狀況對於工作負載的影響</span><span class="sxs-lookup"><span data-stu-id="a38fd-131">Resolve impact of low memory or OOM conditions on the workload</span></span>  
 <span data-ttu-id="a38fd-132">避免發生低記憶體或 OOM (記憶體不足) 的情況才是最上策。</span><span class="sxs-lookup"><span data-stu-id="a38fd-132">Obviously, it is best to not get into a low memory or OOM (Out of Memory) situation.</span></span> <span data-ttu-id="a38fd-133">良好的規劃和監視有助於避免 OOM 情況。</span><span class="sxs-lookup"><span data-stu-id="a38fd-133">Good planning and monitoring can help avoid OOM situations.</span></span> <span data-ttu-id="a38fd-134">不過，最佳的規劃永遠無法預測實際發生的狀況，而最後可能會導致低記憶體或 OOM。</span><span class="sxs-lookup"><span data-stu-id="a38fd-134">Still, the best planning does not always foresee what actually happens and you might end up with low memory or OOM.</span></span> <span data-ttu-id="a38fd-135">有兩個步驟可以從 OOM 中復原：</span><span class="sxs-lookup"><span data-stu-id="a38fd-135">There are two steps to recovering from OOM:</span></span>  
  
1.  [<span data-ttu-id="a38fd-136">開啟 DAC (專用管理員連接)</span><span class="sxs-lookup"><span data-stu-id="a38fd-136">Open a DAC (Dedicated Administrator Connection)</span></span>](#open-a-dac-dedicated-administrator-connection) 
  
2.  [<span data-ttu-id="a38fd-137">採取更正動作</span><span class="sxs-lookup"><span data-stu-id="a38fd-137">Take corrective action</span></span>](#take-corrective-action) 
  
### <a name="open-a-dac-dedicated-administrator-connection"></a><span data-ttu-id="a38fd-138">開啟 DAC (專用管理員連接)</span><span class="sxs-lookup"><span data-stu-id="a38fd-138">Open a DAC (Dedicated Administrator Connection)</span></span>  
 <span data-ttu-id="a38fd-139">Microsoft SQL Server 提供了專用管理員連接 (DAC)。</span><span class="sxs-lookup"><span data-stu-id="a38fd-139">Microsoft SQL Server provides a dedicated administrator connection (DAC).</span></span> <span data-ttu-id="a38fd-140">即使伺服器對其他用戶端連接沒有回應，系統管理員也可以使用 DAC 來存取 SQL Server 資料庫引擎的執行中執行個體，以針對伺服器上的問題進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="a38fd-140">The DAC allows an administrator to access a running instance of SQL Server Database Engine to troubleshoot problems on the server-even when the server is unresponsive to other client connections.</span></span> <span data-ttu-id="a38fd-141">您可以透過 `sqlcmd` 公用程式和 SQL Server Management Studio (SSMS) 使用 DAC。</span><span class="sxs-lookup"><span data-stu-id="a38fd-141">The DAC is available through the `sqlcmd` utility and SQL Server Management Studio (SSMS).</span></span>  
  
 <span data-ttu-id="a38fd-142">如需使用 `sqlcmd` 和 DAC 的指引，請參閱 [使用專用管理員連接](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)。</span><span class="sxs-lookup"><span data-stu-id="a38fd-142">For guidance on using `sqlcmd` and DAC see [Using a Dedicated Administrator Connection](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md).</span></span> <span data-ttu-id="a38fd-143">如需透過 SSMS 使用 DAC 的指引，請參閱 [如何：利用 SQL Server Management Studio 使用專用管理員連接](https://msdn.microsoft.com/library/ms178068.aspx)。</span><span class="sxs-lookup"><span data-stu-id="a38fd-143">For guidance on using DAC through SSMS see [How to: Use the Dedicated Administrator Connection with SQL Server Management Studio](https://msdn.microsoft.com/library/ms178068.aspx).</span></span>  
  
### <a name="take-corrective-action"></a><span data-ttu-id="a38fd-144">採取更正動作</span><span class="sxs-lookup"><span data-stu-id="a38fd-144">Take corrective action</span></span>  
 <span data-ttu-id="a38fd-145">若要解決 OOM 狀況，您必須透過降低使用量，釋出現有的記憶體，或是將更多記憶體提供給記憶體中的資料表。</span><span class="sxs-lookup"><span data-stu-id="a38fd-145">To resolve your OOM condition you need to either free up existing memory by reducing usage, or make more memory available to your in-memory tables.</span></span>  
  
#### <a name="free-up-existing-memory"></a><span data-ttu-id="a38fd-146">釋出現有的記憶體</span><span class="sxs-lookup"><span data-stu-id="a38fd-146">Free up existing memory</span></span>  
  
##### <a name="delete-non-essential-memory-optimized-table-rows-and-wait-for-garbage-collection"></a><span data-ttu-id="a38fd-147">刪除非必要的記憶體最佳化資料表資料列並等候記憶體回收</span><span class="sxs-lookup"><span data-stu-id="a38fd-147">Delete non-essential memory optimized table rows and wait for garbage collection</span></span>  
 <span data-ttu-id="a38fd-148">您可以從記憶體最佳化資料表中移除非必要的資料列。</span><span class="sxs-lookup"><span data-stu-id="a38fd-148">You can remove non-essential rows from a memory optimized table.</span></span> <span data-ttu-id="a38fd-149">記憶體回收行程會將這些資料列所使用的記憶體傳回給可用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="a38fd-149">The garbage collector returns the memory used by these rows to available memory.</span></span> <span data-ttu-id="a38fd-150">.</span><span class="sxs-lookup"><span data-stu-id="a38fd-150">.</span></span> <span data-ttu-id="a38fd-151">記憶體中 OLTP 引擎會積極地回收資料列佔用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="a38fd-151">In-memory OLTP engine collects garbage rows aggressively.</span></span> <span data-ttu-id="a38fd-152">不過，長時間執行的交易可能會防止記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="a38fd-152">However, a long running transaction can prevent garbage collection.</span></span> <span data-ttu-id="a38fd-153">例如，假設您的交易會執行 5 分鐘，則任何在交易作用期間由於更新/刪除作業而建立的資料列版本，都無法進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="a38fd-153">For example, if you have a transaction that runs for 5 minutes, any row versions created due to update/delete operations while the transaction was active can't be garbage collected.</span></span>  
  
##### <a name="move-one-or-more-rows-to-a-disk-based-table"></a><span data-ttu-id="a38fd-154">將一個或多個資料列移至磁碟資料表</span><span class="sxs-lookup"><span data-stu-id="a38fd-154">Move one or more rows to a disk-based table</span></span>  
 <span data-ttu-id="a38fd-155">下列 TechNet 文件提供了有關將記憶體最佳化資料表的資料列移至磁碟資料表的指引。</span><span class="sxs-lookup"><span data-stu-id="a38fd-155">The following TechNet articles provide guidance on moving rows from a memory-optimized table to a disk-based table.</span></span>  
  
-   <span data-ttu-id="a38fd-156">[應用程式層級資料分割](https://technet.microsoft.com/library/dn296452\(v=sql.120\).aspx)</span><span class="sxs-lookup"><span data-stu-id="a38fd-156">[Application-Level Partitioning](https://technet.microsoft.com/library/dn296452\(v=sql.120\).aspx)</span></span>  
  
-   <span data-ttu-id="a38fd-157">[分割記憶體最佳化資料表的應用程式模式](https://technet.microsoft.com/library/dn133171\(v=sql.120\).aspx)</span><span class="sxs-lookup"><span data-stu-id="a38fd-157">[Application Pattern for Partitioning Memory-Optimized Tables](https://technet.microsoft.com/library/dn133171\(v=sql.120\).aspx)</span></span>  
  
#### <a name="increase-available-memory"></a><span data-ttu-id="a38fd-158">增加可用的記憶體</span><span class="sxs-lookup"><span data-stu-id="a38fd-158">Increase available memory</span></span>  
  
##### <a name="increase-value-of-max_memory_percent-on-the-resource-pool"></a><span data-ttu-id="a38fd-159">提高資源集區的 MAX_MEMORY_PERCENT 值</span><span class="sxs-lookup"><span data-stu-id="a38fd-159">Increase value of MAX_MEMORY_PERCENT on the resource pool</span></span>  
 <span data-ttu-id="a38fd-160">如果您尚未針對記憶體中的資料表建立具名資源集區，就應該先建立集區，並且將 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 資料庫繫結至該集區。</span><span class="sxs-lookup"><span data-stu-id="a38fd-160">If you have not created a named resource pool for your in-memory tables you should do that and bind your [!INCLUDE[hek_2](../../includes/hek-2-md.md)] databases to it.</span></span> <span data-ttu-id="a38fd-161">如需如何建立 [資料庫並繫結至資源集區的指引，請參閱](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md) 將包含記憶體最佳化資料表的資料庫繫結至資源集區 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 主題。</span><span class="sxs-lookup"><span data-stu-id="a38fd-161">See the topic [Bind a Database with Memory-Optimized Tables to a Resource Pool](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md) for guidance on creating and binding your [!INCLUDE[hek_2](../../includes/hek-2-md.md)] databases to a resource pool.</span></span>  
  
 <span data-ttu-id="a38fd-162">如果您的 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 資料庫已繫結至資源集區，您應該能夠提高集區可存取的記憶體百分比。</span><span class="sxs-lookup"><span data-stu-id="a38fd-162">If your [!INCLUDE[hek_2](../../includes/hek-2-md.md)] database is bound to a resource pool you may be able to increase the percent of memory the pool can access.</span></span> <span data-ttu-id="a38fd-163">如需變更資源集區之 MIN_MEMORY_PERCENT 和 MAX_MEMORY_PERCENT 值的指引，請參閱 [變更現有集區上的 MIN_MEMORY_PERCENT 和 MAX_MEMORY_PERCENT](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#change-min-memory-percent-and-max-memory-percent-on-an-existing-pool) 子主題。</span><span class="sxs-lookup"><span data-stu-id="a38fd-163">See the sub-topic [Change MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT on an existing pool](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#change-min-memory-percent-and-max-memory-percent-on-an-existing-pool) for guidance on changing the value of MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT for a resource pool.</span></span>  
  
 <span data-ttu-id="a38fd-164">提高 MAX_MEMORY_PERCENT 的值。</span><span class="sxs-lookup"><span data-stu-id="a38fd-164">Increase the value of MAX_MEMORY_PERCENT.</span></span>   
<span data-ttu-id="a38fd-165">這個程式碼片段會將資源集區 PoolHk 的 MAX_MEMORY_PERCENT 變更為已安裝記憶體的 70%。</span><span class="sxs-lookup"><span data-stu-id="a38fd-165">This code snippet changes MAX_MEMORY_PERCENT for the resource pool PoolHk to 70% of installed memory.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a38fd-166">如果伺服器是在 VM 上執行，而且不是專用的，請將 MIN_MEMORY_PERCENT 與 MAX_MEMORY_PERCENT 設為相同值。</span><span class="sxs-lookup"><span data-stu-id="a38fd-166">If the server is running on a VM and is not dedicated, set the value of MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT to the same value.</span></span>   
> <span data-ttu-id="a38fd-167">請參閱[最佳做法：在 VM 環境使用記憶體內部 OLTP](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md)主題，以了解詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="a38fd-167">See the topic [Best Practices: Using In-Memory OLTP in a VM environment](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) for more information.</span></span>  
  
```sql  
  
-- disable resource governor  
ALTER RESOURCE GOVERNOR DISABLE  
  
-- change the value of MAX_MEMORY_PERCENT  
ALTER RESOURCE POOL PoolHk  
WITH  
     ( MAX_MEMORY_PERCENT = 70 )  
GO  
  
-- reconfigure the Resource Governor  
--    RECONFIGURE enables resource governor  
ALTER RESOURCE GOVERNOR RECONFIGURE  
GO  
  
```  
  
 <span data-ttu-id="a38fd-168">如需 MAX_MEMORY_PERCENT 之最大值的資訊，請參閱主題章節： [可用於記憶體最佳化資料表和索引的記憶體百分比](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#percent-of-memory-available-for-memory-optimized-tables-and-indexes)。</span><span class="sxs-lookup"><span data-stu-id="a38fd-168">For information on maximum values for MAX_MEMORY_PERCENT see the topic section [Percent of memory available for memory-optimized tables and indexes](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#percent-of-memory-available-for-memory-optimized-tables-and-indexes).</span></span>  
  
##### <a name="install-additional-memory"></a><span data-ttu-id="a38fd-169">安裝額外記憶體</span><span class="sxs-lookup"><span data-stu-id="a38fd-169">Install additional memory</span></span>  
 <span data-ttu-id="a38fd-170">最佳的終極解決方案還是安裝額外的實體記憶體 (如果可行)。</span><span class="sxs-lookup"><span data-stu-id="a38fd-170">Ultimately the best solution, if possible, is to install additional physical memory.</span></span> <span data-ttu-id="a38fd-171">如果您這樣做，請記住，因為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不太可能需要更多記憶體，所以您或許能夠一併提高 MAX_MEMORY_PERCENT 的值 (請參閱[變更現有集區上的 MIN_MEMORY_PERCENT 和 MAX_MEMORY_PERCENT](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#change-min-memory-percent-and-max-memory-percent-on-an-existing-pool) 子主題)，以便將大部分新安裝的記憶體提供給資源集區。</span><span class="sxs-lookup"><span data-stu-id="a38fd-171">If you do this, remember that you will probably be able to also increase the value of MAX_MEMORY_PERCENT (see the sub-topic [Change MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT on an existing pool](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#change-min-memory-percent-and-max-memory-percent-on-an-existing-pool)) since [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] won't likely need more memory, allowing you to make most if not all of the newly installed memory available to the resource pool.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a38fd-172">如果伺服器是在 VM 上執行，而且不是專用的，請將 MIN_MEMORY_PERCENT 與 MAX_MEMORY_PERCENT 設為相同值。</span><span class="sxs-lookup"><span data-stu-id="a38fd-172">If the server is running on a VM and is not dedicated, set the value of MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT to the same value.</span></span>   
> <span data-ttu-id="a38fd-173">請參閱[最佳做法：在 VM 環境使用記憶體內部 OLTP](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md)主題，以了解詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="a38fd-173">See the topic [Best Practices: Using In-Memory OLTP in a VM environment](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) for more information.</span></span>  
  
## <a name="resolve-page-allocation-failures-due-to-insufficient-memory-when-sufficient-memory-is-available"></a><span data-ttu-id="a38fd-174">解決有足夠的記憶體可用但卻記憶體不足所造成的頁面配置失敗</span><span class="sxs-lookup"><span data-stu-id="a38fd-174">Resolve page allocation failures due to insufficient memory when sufficient memory is available</span></span>  
 <span data-ttu-id="a38fd-175">如果您收到錯誤訊息：「不允許資料庫 ' ' 的頁面配置， *\<databaseName>* 因為資源集區 ' ' 中的記憶體不足 *\<resourcePoolName>* 。」</span><span class="sxs-lookup"><span data-stu-id="a38fd-175">If you get the error message, "Disallowing page allocations for database '*\<databaseName>*' due to insufficient memory in the resource pool '*\<resourcePoolName>*'.</span></span> <span data-ttu-id="a38fd-176">如需詳細資訊，請參閱 ' <https://go.microsoft.com/fwlink/?LinkId=330673> '。</span><span class="sxs-lookup"><span data-stu-id="a38fd-176">See '<https://go.microsoft.com/fwlink/?LinkId=330673>' for more information."</span></span> <span data-ttu-id="a38fd-177">在錯誤記錄檔中，可用的實體記憶體已足夠配置頁面時，它可能是因為已停用的資源管理員。</span><span class="sxs-lookup"><span data-stu-id="a38fd-177">in the error log when the available physical memory is sufficient to allocate the page, it may be due to a disabled Resource Governor.</span></span> <span data-ttu-id="a38fd-178">若資源管理員已停用，MEMORYBROKER_FOR_RESERVE 會誘發不實的記憶體壓力。</span><span class="sxs-lookup"><span data-stu-id="a38fd-178">When the Resource Governor is disabled MEMORYBROKER_FOR_RESERVE induces artificial memory pressure.</span></span>  
  
 <span data-ttu-id="a38fd-179">為了解決此問題，您必須啟用資源管理員。</span><span class="sxs-lookup"><span data-stu-id="a38fd-179">To resolve this you need to enable the Resource Governor.</span></span>  
  
 <span data-ttu-id="a38fd-180">如需使用物件總管、資源管理員屬性或 Transact-SQL 來啟用資源管理員之限制事項的資訊和指引，請參閱 [啟用資源管理員](https://technet.microsoft.com/library/bb895149.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="a38fd-180">See [Enable Resource Governor](https://technet.microsoft.com/library/bb895149.aspx) for information on Limits and Restrictions as well as guidance on enabling Resource Governor using Object Explorer, Resource Governor properties, or Transact-SQL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a38fd-181">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a38fd-181">See Also</span></span>  
 <span data-ttu-id="a38fd-182">[為記憶體中的 OLTP 管理記憶體](../../database-engine/managing-memory-for-in-memory-oltp.md) </span><span class="sxs-lookup"><span data-stu-id="a38fd-182">[Managing Memory for In-Memory OLTP](../../database-engine/managing-memory-for-in-memory-oltp.md) </span></span>  
 <span data-ttu-id="a38fd-183">[監視與疑難排解記憶體使用量](monitor-and-troubleshoot-memory-usage.md) </span><span class="sxs-lookup"><span data-stu-id="a38fd-183">[Monitor and Troubleshoot Memory Usage](monitor-and-troubleshoot-memory-usage.md) </span></span>  
 <span data-ttu-id="a38fd-184">[資料庫並繫結至資源集區的指引，請參閱](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="a38fd-184">[Bind a Database with Memory-Optimized Tables to a Resource Pool](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md) </span></span>  
 [<span data-ttu-id="a38fd-185">最佳做法：在 VM 環境中使用記憶體內部 OLTP</span><span class="sxs-lookup"><span data-stu-id="a38fd-185">Best Practices: Using In-Memory OLTP in a VM environment</span></span>](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md)  
  
  
