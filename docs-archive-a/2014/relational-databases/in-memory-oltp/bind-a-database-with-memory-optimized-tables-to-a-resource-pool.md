---
title: 將包含記憶體最佳化資料表的資料庫繫結至資源集區 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f222b1d5-d2fa-4269-8294-4575a0e78636
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: cd163c5d3bc7a2cd9051b8d37b8127a1cc88c30b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607390"
---
# <a name="bind-a-database-with-memory-optimized-tables-to-a-resource-pool"></a><span data-ttu-id="59d8d-102">將包含記憶體最佳化資料表的資料庫繫結至資源集區</span><span class="sxs-lookup"><span data-stu-id="59d8d-102">Bind a Database with Memory-Optimized Tables to a Resource Pool</span></span>
  <span data-ttu-id="59d8d-103">資源集區代表可受管制的實體資源子集。</span><span class="sxs-lookup"><span data-stu-id="59d8d-103">A resource pool represents a subset of physical resources that can be governed.</span></span> <span data-ttu-id="59d8d-104">根據預設， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫會繫結至預設資源集區並取用其資源。</span><span class="sxs-lookup"><span data-stu-id="59d8d-104">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases are bound to and consume the resources of the default resource pool.</span></span> <span data-ttu-id="59d8d-105">為了防止一個或多個記憶體最佳化資料表取用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的所有資源，以及避免其他記憶體使用者耗用記憶體最佳化資料表所需的記憶體，您應該針對具有記憶體最佳化資料表的資料庫建立另一個資源集區來管理記憶體耗用量。</span><span class="sxs-lookup"><span data-stu-id="59d8d-105">To protect [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from having its resources consumed by one or more memory-optimized tables, and to prevent other memory users from consuming memory needed by memory-optimized tables, you should create a separate resource pool to manage memory consumption for the database with memory-optimized tables.</span></span>  
  
 <span data-ttu-id="59d8d-106">一個資料庫只能繫結至一個資源集區。</span><span class="sxs-lookup"><span data-stu-id="59d8d-106">A database can be bound on only one resource pool.</span></span> <span data-ttu-id="59d8d-107">不過，您可以將多個資料庫繫結至相同的集區。</span><span class="sxs-lookup"><span data-stu-id="59d8d-107">However, you can bind multiple databases to the same pool.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="59d8d-108">允許將不含記憶體最佳化資料表的資料庫繫結至資源集區，但是這樣沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="59d8d-108">allows binding a database without memory-optimized tables to a resource pool but it has no effect.</span></span> <span data-ttu-id="59d8d-109">如果您日後想要在資料庫中建立記憶體最佳化資料表，就可以將該資料庫繫結至具名資源集區。</span><span class="sxs-lookup"><span data-stu-id="59d8d-109">You may want to bind a database to a named resource pool if, in future, you may want to create memory-optimized tables in the database.</span></span>  
  
 <span data-ttu-id="59d8d-110">資料庫與資源集區都必須事先存在，然後您才能將資料庫繫結至資源集區。</span><span class="sxs-lookup"><span data-stu-id="59d8d-110">Before you can bind a database to a resource pool both the database and the resource pool must exist.</span></span> <span data-ttu-id="59d8d-111">繫結會在下一次資料庫重新上線時生效。</span><span class="sxs-lookup"><span data-stu-id="59d8d-111">The binding takes effect the next time the database is brought online.</span></span> <span data-ttu-id="59d8d-112">如需詳細資訊，請參閱 [資料庫狀態](../databases/database-states.md) 。</span><span class="sxs-lookup"><span data-stu-id="59d8d-112">See [Database States](../databases/database-states.md) for more information.</span></span>  
  
 <span data-ttu-id="59d8d-113">如需有關資源集區的詳細資訊，請參閱 [Resource Governor 資源集區](../resource-governor/resource-governor-resource-pool.md)。</span><span class="sxs-lookup"><span data-stu-id="59d8d-113">For information about resource pools, see [Resource Governor Resource Pool](../resource-governor/resource-governor-resource-pool.md).</span></span>  
  
  
## <a name="create-the-database-and-resource-pool"></a><span data-ttu-id="59d8d-114">建立資料庫和資源集區</span><span class="sxs-lookup"><span data-stu-id="59d8d-114">Create the database and resource pool</span></span>  
 <span data-ttu-id="59d8d-115">您可以按照任何順序建立資料庫和資源集區。</span><span class="sxs-lookup"><span data-stu-id="59d8d-115">You can create the database and resource pool in any order.</span></span> <span data-ttu-id="59d8d-116">重點在於這兩者必須事先存在，才能將資料庫繫結至資源集區。</span><span class="sxs-lookup"><span data-stu-id="59d8d-116">What matters is that they both exist prior to binding the database to the resource pool.</span></span>  
  
### <a name="create-the-database"></a><span data-ttu-id="59d8d-117">建立資料庫</span><span class="sxs-lookup"><span data-stu-id="59d8d-117">Create the database</span></span>  
 <span data-ttu-id="59d8d-118">下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 會建立名為 IMOLTP_DB 的資料庫，其中將包含一個或多個記憶體最佳化資料表。</span><span class="sxs-lookup"><span data-stu-id="59d8d-118">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] creates a database named IMOLTP_DB which will contain one or more memory-optimized tables.</span></span> <span data-ttu-id="59d8d-119">執行此命令之前，路徑 \<driveAndPath> 必須存在。</span><span class="sxs-lookup"><span data-stu-id="59d8d-119">The path \<driveAndPath> must exist prior to running this command.</span></span>  
  
```sql  
CREATE DATABASE IMOLTP_DB  
GO  
ALTER DATABASE IMOLTP_DB ADD FILEGROUP IMOLTP_DB_fg CONTAINS MEMORY_OPTIMIZED_DATA  
ALTER DATABASE IMOLTP_DB ADD FILE( NAME = 'IMOLTP_DB_fg' , FILENAME = 'c:\data\IMOLTP_DB_fg') TO FILEGROUP IMOLTP_DB_fg;  
GO  
```  
  
### <a name="determine-the-minimum-value-for-min_memory_percent-and-max_memory_percent"></a><span data-ttu-id="59d8d-120">決定 MIN_MEMORY_PERCENT 和 MAX_MEMORY_PERCENT 的最小值</span><span class="sxs-lookup"><span data-stu-id="59d8d-120">Determine the minimum value for MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT</span></span>  
 <span data-ttu-id="59d8d-121">判斷出記憶體最佳化資料表的記憶體需求之後，您必須決定所需數量佔可用記憶體的百分比，並將記憶體百分比設定為該值或更高。</span><span class="sxs-lookup"><span data-stu-id="59d8d-121">Once you determine the memory needs for your memory-optimized tables, you need to determine what percentage of available memory you need, and set the memory percentages to that value or higher.</span></span>  
  
 <span data-ttu-id="59d8d-122">**範例：**  </span><span class="sxs-lookup"><span data-stu-id="59d8d-122">**Example:** </span></span>  
<span data-ttu-id="59d8d-123">此範例假設您經過計算後，判斷出記憶體最佳化資料表和索引需要 16 GB 的記憶體。</span><span class="sxs-lookup"><span data-stu-id="59d8d-123">For this example we will assume that from your calculations you determined that your memory-optimized tables and indexes need 16 GB of memory.</span></span> <span data-ttu-id="59d8d-124">假設您已獲認可使用 32 GB 的記憶體。</span><span class="sxs-lookup"><span data-stu-id="59d8d-124">Assume that you have 32 GB of memory committed for your use.</span></span>  
  
 <span data-ttu-id="59d8d-125">乍看之下，您似乎必須將 MIN_MEMORY_PERCENT 和 MAX_MEMORY_PERCENT 設定為 50 (16 等於 32 乘以 50%)。</span><span class="sxs-lookup"><span data-stu-id="59d8d-125">At first glance it could seem that you need to set MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT to 50 (16 is 50% of 32).</span></span>  <span data-ttu-id="59d8d-126">不過，這樣並不會使您的記憶體最佳化資料表擁有足夠的記憶體。</span><span class="sxs-lookup"><span data-stu-id="59d8d-126">However, that would not give your memory-optimized tables sufficient memory.</span></span> <span data-ttu-id="59d8d-127">看看下面表格 ([記憶體最佳化資料表和索引可用的記憶體百分比](#percent-of-memory-available-for-memory-optimized-tables-and-indexes)) 我們得知假設有 32 GB 的認可記憶體時，只有 80% 可用於記憶體最佳化資料表和索引。</span><span class="sxs-lookup"><span data-stu-id="59d8d-127">Looking at the table below ([Percent of memory available for memory-optimized tables and indexes](#percent-of-memory-available-for-memory-optimized-tables-and-indexes)) we see that if there is 32 GB of committed memory, only 80% of that is available for memory-optimized tables and indexes.</span></span>  <span data-ttu-id="59d8d-128">因此，最小和最大百分比要依據可用的記憶體來計算，而不是依據認可的記憶體。</span><span class="sxs-lookup"><span data-stu-id="59d8d-128">Therefore, we calculate the min and max percentages based upon the available memory, not the committed memory.</span></span>  
  
 `memoryNeedeed = 16`   
 `memoryCommitted = 32`   
 `availablePercent = 0.8`   
 `memoryAvailable = memoryCommitted * availablePercent`   
 `percentNeeded = memoryNeeded / memoryAvailable`  
  
 <span data-ttu-id="59d8d-129">代入實際數字：</span><span class="sxs-lookup"><span data-stu-id="59d8d-129">Plugging in real numbes:</span></span>   
`percentNeeded = 16 / (32 * 0.8) = 16 / 25.6 = 0.625`  
  
 <span data-ttu-id="59d8d-130">換言之，您至少需要 62.5% 的可用記憶體，才會符合記憶體最佳化資料表和索引的 16 GB 需求。</span><span class="sxs-lookup"><span data-stu-id="59d8d-130">Thus you need at least 62.5% of the available memory to meet the 16 GB requirement of your memory-optimized tables and indexes.</span></span>  <span data-ttu-id="59d8d-131">由於 MIN_MEMORY_PERCENT 和 MAX_MEMORY_PERCENT 的值必須是整數，您就要將兩者設定為至少佔 63%。</span><span class="sxs-lookup"><span data-stu-id="59d8d-131">Since the values for MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT must be integers, we set them to at least 63%.</span></span>  
  
### <a name="create-a-resource-pool-and-configure-memory"></a><span data-ttu-id="59d8d-132">建立資源集區和設定記憶體</span><span class="sxs-lookup"><span data-stu-id="59d8d-132">Create a resource pool and configure memory</span></span>  
 <span data-ttu-id="59d8d-133">設定記憶體最佳化資料表的記憶體時，應該依據 MIN_MEMORY_PERCENT 規劃容量，而不是依據 MAX_MEMORY_PERCENT。</span><span class="sxs-lookup"><span data-stu-id="59d8d-133">When configuring memory for memory-optimized tables, the capacity planning should be done based on MIN_MEMORY_PERCENT, not on MAX_MEMORY_PERCENT.</span></span>  <span data-ttu-id="59d8d-134">如需有關 MIN_MEMORY_PERCENT 和 MAX_MEMORY_PERCENT 的詳細資訊，請參閱 [ALTER RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-pool-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="59d8d-134">See [ALTER RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-pool-transact-sql) for information on MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT.</span></span> <span data-ttu-id="59d8d-135">這樣可以為記憶體最佳化資料提供更可預測的記憶體可用性，因為 MIN_MEMORY_PERCENT 會對其他資源集區造成記憶體壓力，以確保記憶體可被接受。</span><span class="sxs-lookup"><span data-stu-id="59d8d-135">This provides more predictable memory availability for memory-optimized tables as MIN_MEMORY_PERCENT causes memory pressure to other resource pools to make sure it is honored.</span></span> <span data-ttu-id="59d8d-136">若要確保記憶體可用，並幫助避免記憶體不足狀況，MIN_MEMORY_PERCENT 和 MAX_MEMORY_PERCENT 的值應相同。</span><span class="sxs-lookup"><span data-stu-id="59d8d-136">To ensure that memory is available and help avoid out-of-memory conditions, the values for MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT should be the same.</span></span> <span data-ttu-id="59d8d-137">如需以認可記憶體數量為基礎，可用於記憶體最佳化資料表的記憶體百分比，請參閱以下的 [可用記憶體最佳化資料表和索引的記憶體百分比](#percent-of-memory-available-for-memory-optimized-tables-and-indexes) 。</span><span class="sxs-lookup"><span data-stu-id="59d8d-137">See [Percent of memory available for memory-optimized tables and indexes](#percent-of-memory-available-for-memory-optimized-tables-and-indexes) below for the percent of memory available for memory-optimized tables based on the amount of committed memory.</span></span>  
  
 <span data-ttu-id="59d8d-138">請參閱[最佳做法：在 VM 環境使用記憶體內部 OLTP](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md)，以了解有關在 VM 環境下作業的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="59d8d-138">See [Best Practices: Using In-Memory OLTP in a VM environment](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) for more information when working in a VM environment.</span></span>  
  
 <span data-ttu-id="59d8d-139">下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼會建立名為 Pool_IMOLTP 的資源集區，而且一半的記憶體可供它使用。</span><span class="sxs-lookup"><span data-stu-id="59d8d-139">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] code creates a resource pool named Pool_IMOLTP with half of the memory available for its use.</span></span>  <span data-ttu-id="59d8d-140">建立集區之後，資源管理員會重新設定為包含 Pool_IMOLTP。</span><span class="sxs-lookup"><span data-stu-id="59d8d-140">After the pool is created Resource Governor is reconfigured to include Pool_IMOLTP.</span></span>  
  
```sql  
-- set MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT to the same value  
CREATE RESOURCE POOL Pool_IMOLTP   
  WITH   
    ( MIN_MEMORY_PERCENT = 63,   
    MAX_MEMORY_PERCENT = 63 );  
GO  
  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="bind-the-database-to-the-pool"></a><span data-ttu-id="59d8d-141">將資料庫繫結至集區</span><span class="sxs-lookup"><span data-stu-id="59d8d-141">Bind the database to the pool</span></span>  
 <span data-ttu-id="59d8d-142">您可以使用系統函數 `sp_xtp_bind_db_resource_pool` ，將資料庫繫結至資源集區。</span><span class="sxs-lookup"><span data-stu-id="59d8d-142">Use the system function `sp_xtp_bind_db_resource_pool` to bind the database to the resource pool.</span></span> <span data-ttu-id="59d8d-143">此函數會採用兩個參數：資料庫名稱和資源集區名稱。</span><span class="sxs-lookup"><span data-stu-id="59d8d-143">The function takes two parameters: the database name and the resource pool name.</span></span>  
  
 <span data-ttu-id="59d8d-144">下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 會定義 IMOLTP_DB 資料庫與 Pool_IMOLTP 資源集區的繫結。</span><span class="sxs-lookup"><span data-stu-id="59d8d-144">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] defines a binding of the database IMOLTP_DB to the resource pool Pool_IMOLTP.</span></span> <span data-ttu-id="59d8d-145">在您讓資料庫重新上線之前，此繫結不會生效。</span><span class="sxs-lookup"><span data-stu-id="59d8d-145">The binding does not become effective until you bring the database online.</span></span>  
  
```sql  
EXEC sp_xtp_bind_db_resource_pool 'IMOLTP_DB', 'Pool_IMOLTP'  
GO  
```  
  
 <span data-ttu-id="59d8d-146">系統函數 sp_xtp_bind_db_resourece_pool 會採用兩個字串參數：database_name 和 pool_name。</span><span class="sxs-lookup"><span data-stu-id="59d8d-146">The system function sp_xtp_bind_db_resourece_pool takes two string parameters: database_name and pool_name.</span></span>  
  
## <a name="confirm-the-binding"></a><span data-ttu-id="59d8d-147">確認繫結</span><span class="sxs-lookup"><span data-stu-id="59d8d-147">Confirm the binding</span></span>  
 <span data-ttu-id="59d8d-148">確認繫結，並記下 IMOLTP_DB 的資源集區識別碼。</span><span class="sxs-lookup"><span data-stu-id="59d8d-148">Confirm the binding, noting the resource pool id for IMOLTP_DB.</span></span> <span data-ttu-id="59d8d-149">它不應該是 NULL。</span><span class="sxs-lookup"><span data-stu-id="59d8d-149">It should not be NULL.</span></span>  
  
```sql  
SELECT d.database_id, d.name, d.resource_pool_id  
FROM sys.databases d  
GO  
```  
  
## <a name="make-the-binding-effective"></a><span data-ttu-id="59d8d-150">使繫結生效</span><span class="sxs-lookup"><span data-stu-id="59d8d-150">Make the binding effective</span></span>  
 <span data-ttu-id="59d8d-151">將資料庫繫結至資源集區之後，您必須讓資料庫離線再恢復上線，以使繫結生效。</span><span class="sxs-lookup"><span data-stu-id="59d8d-151">You must take the database offline and back online after binding it to the resource pool for binding to take effect.</span></span> <span data-ttu-id="59d8d-152">如果您的資料庫先前已繫結至不同的集區，這樣做便會從先前的資源集區移除已配置的記憶體，而且記憶體最佳化資料表和索引的記憶體配置現在將由最近剛與資料庫繫結的新資源集區提供。</span><span class="sxs-lookup"><span data-stu-id="59d8d-152">If your database was bound to an a different pool earlier, this removes the allocated memory from the previous resource pool and memory allocations for your memory-optimized table and indexes will now come from the resource pool newly bound with the database.</span></span>  
  
```sql  
USE master  
GO  
  
ALTER DATABASE IMOLTP_DB SET OFFLINE  
GO  
ALTER DATABASE IMOLTP_DB SET ONLINE  
GO  
  
USE IMOLTP_DB  
GO  
```  
  
 <span data-ttu-id="59d8d-153">此時，資料庫已繫結至資源集區。</span><span class="sxs-lookup"><span data-stu-id="59d8d-153">And now, the database is bound to the resource pool.</span></span>  
  
## <a name="change-min-memory-percent-and-max-memory-percent-on-an-existing-pool"></a><span data-ttu-id="59d8d-154">變更現有集區上的最小記憶體百分比和最大記憶體百分比</span><span class="sxs-lookup"><span data-stu-id="59d8d-154">Change MIN MEMORY PERCENT and MAX MEMORY PERCENT on an existing pool</span></span>  
 <span data-ttu-id="59d8d-155">如果您為伺服器另外再加入記憶體，或是您的記憶體最佳化資料表所需的記憶體數量已變更，可能就必須更改 MIN_MEMORY_PERCENT 和 MAX_MEMORY_PERCENT 的值。</span><span class="sxs-lookup"><span data-stu-id="59d8d-155">If you add additional memory to the server or the amount of memory needed for your memory-optimized tables changes, you may need to alter the value of MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT.</span></span> <span data-ttu-id="59d8d-156">下列步驟將為您示範如何更改資源集區的 MIN_MEMORY_PERCENT 和 MAX_MEMORY_PERCENT 值。</span><span class="sxs-lookup"><span data-stu-id="59d8d-156">The following steps show you how to alter the value of MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT on a resource pool.</span></span> <span data-ttu-id="59d8d-157">請參閱下一節提供的指引，以得知 MIN_MEMORY_PERCENT 和 MAX_MEMORY_PERCENT 應該使用哪些值。</span><span class="sxs-lookup"><span data-stu-id="59d8d-157">See the section below, for guidance on what values to use for MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT.</span></span>  <span data-ttu-id="59d8d-158">請參閱[最佳做法：在 VM 環境使用記憶體內部 OLTP](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md)主題，以了解詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="59d8d-158">See the topic [Best Practices: Using In-Memory OLTP in a VM environment](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) for more information.</span></span>  
  
1.  <span data-ttu-id="59d8d-159">使用 `ALTER RESOURCE POOL` 變更 MIN_MEMORY_PERCENT 和 MAX_MEMORY_PERCENT 的值。</span><span class="sxs-lookup"><span data-stu-id="59d8d-159">Use `ALTER RESOURCE POOL` to change the value of both MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT.</span></span>  
  
2.  <span data-ttu-id="59d8d-160">使用 `ALTER RESURCE GOVERNOR` ，以新的值重新設定資源管理員。</span><span class="sxs-lookup"><span data-stu-id="59d8d-160">Use `ALTER RESURCE GOVERNOR` to reconfigure the Resource Governor with the new values.</span></span>  
  
 <span data-ttu-id="59d8d-161">**範例程式碼**</span><span class="sxs-lookup"><span data-stu-id="59d8d-161">**Sample Code**</span></span>  
  
```sql  
ALTER RESOURCE POOL Pool_IMOLTP  
WITH  
     ( MIN_MEMORY_PERCENT = 70,  
       MAX_MEMORY_PERCENT = 70 )   
GO  
  
-- reconfigure the Resource Governor  
ALTER RESOURCE GOVERNOR RECONFIGURE  
GO  
```  
  
## <a name="percent-of-memory-available-for-memory-optimized-tables-and-indexes"></a><span data-ttu-id="59d8d-162">可用於記憶體最佳化資料表和索引的記憶體百分比</span><span class="sxs-lookup"><span data-stu-id="59d8d-162">Percent of memory available for memory-optimized tables and indexes</span></span>  
 <span data-ttu-id="59d8d-163">如果您將具有記憶體最佳化資料表的資料庫和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 工作負載對應至相同的資源集區，資源管理員就會設定 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] 使用的內部臨界值，避免集區的使用者在集區使用量上發生衝突。</span><span class="sxs-lookup"><span data-stu-id="59d8d-163">If you map a database with memory-optimized tables and a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] workload to the same resource pool, the Resource Governor sets an internal threshold for [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] use so that the users of the pool do not have conflicts over pool usage.</span></span> <span data-ttu-id="59d8d-164">一般而言， [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] 使用的臨界值大約是 80% 的集區。</span><span class="sxs-lookup"><span data-stu-id="59d8d-164">Generally speaking, the threshold for [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] use is about 80% of the pool.</span></span> <span data-ttu-id="59d8d-165">下表顯示各種記憶體大小的實際臨界值。</span><span class="sxs-lookup"><span data-stu-id="59d8d-165">The following table shows actual thresholds for various memory sizes.</span></span>  
  
 <span data-ttu-id="59d8d-166">您為 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] 資料庫建立專用資源集區時，在考量資料列版本和資料成長之後，需要估計記憶體中資料表所需的實體記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="59d8d-166">When you create a dedicated resource pool for the [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] database, you need to estimate how much physical memory you need for the in-memory tables after accounting for row versions and data growth.</span></span> <span data-ttu-id="59d8d-167">估計需要的記憶體之後，請建立資源集區，且其中有一定比例的認可目標記憶體可用於 SQL 執行個體，如 DMV `sys.dm_os_sys_info` 中的 'committed_target_kb' 資料行所反映 (請參閱 [sys.dm_os_sys_info](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql))。</span><span class="sxs-lookup"><span data-stu-id="59d8d-167">Once estimate the memory needed, you create a resource pool with a percent of the commit target memory for SQL Instance as reflected by column 'committed_target_kb' in the DMV `sys.dm_os_sys_info` (see [sys.dm_os_sys_info](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql)).</span></span> <span data-ttu-id="59d8d-168">例如，您可以建立資源集區 P1，其中有 40% 的總記憶體可供執行個體使用。</span><span class="sxs-lookup"><span data-stu-id="59d8d-168">For example, you can create a resource pool P1 with 40% of the total memory available to the instance.</span></span> <span data-ttu-id="59d8d-169">在此 40% 之中， [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] 引擎會取用較小的百分比來儲存 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] 資料。</span><span class="sxs-lookup"><span data-stu-id="59d8d-169">Out of this 40%, the [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] engine gets a smaller percent to store [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] data.</span></span>  <span data-ttu-id="59d8d-170">這樣做可確保 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] 不會耗用此集區中的所有記憶體。</span><span class="sxs-lookup"><span data-stu-id="59d8d-170">This is done to make sure [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] does not consume all the memory from this pool.</span></span>  <span data-ttu-id="59d8d-171">這個較小的百分比值取決於目標認可的記憶體。</span><span class="sxs-lookup"><span data-stu-id="59d8d-171">This value of the smaller percent depends upon the Target committed Memory.</span></span> <span data-ttu-id="59d8d-172">下表描述在 OOM 錯誤引發之前，資源集區 (具名或預設) 中可供 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] 資料庫使用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="59d8d-172">The following table describes memory available to [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] database in a resource pool (named or default) before an OOM error is raised.</span></span>  
  
|<span data-ttu-id="59d8d-173">目標認可的記憶體</span><span class="sxs-lookup"><span data-stu-id="59d8d-173">Target Committed Memory</span></span>|<span data-ttu-id="59d8d-174">記憶體中資料表可用的百分比</span><span class="sxs-lookup"><span data-stu-id="59d8d-174">Percent available for in-memory tables</span></span>|  
|-----------------------------|---------------------------------------------|  
|<span data-ttu-id="59d8d-175"><= 8 GB</span><span class="sxs-lookup"><span data-stu-id="59d8d-175"><= 8 GB</span></span>|<span data-ttu-id="59d8d-176">70%</span><span class="sxs-lookup"><span data-stu-id="59d8d-176">70%</span></span>|  
|<span data-ttu-id="59d8d-177"><= 16 GB</span><span class="sxs-lookup"><span data-stu-id="59d8d-177"><= 16 GB</span></span>|<span data-ttu-id="59d8d-178">75%</span><span class="sxs-lookup"><span data-stu-id="59d8d-178">75%</span></span>|  
|<span data-ttu-id="59d8d-179"><= 32 GB</span><span class="sxs-lookup"><span data-stu-id="59d8d-179"><= 32 GB</span></span>|<span data-ttu-id="59d8d-180">80%</span><span class="sxs-lookup"><span data-stu-id="59d8d-180">80%</span></span>|  
|<span data-ttu-id="59d8d-181">\<= 96 GB</span><span class="sxs-lookup"><span data-stu-id="59d8d-181">\<= 96 GB</span></span>|<span data-ttu-id="59d8d-182">85%</span><span class="sxs-lookup"><span data-stu-id="59d8d-182">85%</span></span>|  
|<span data-ttu-id="59d8d-183">>96 GB</span><span class="sxs-lookup"><span data-stu-id="59d8d-183">>96 GB</span></span>|<span data-ttu-id="59d8d-184">90%</span><span class="sxs-lookup"><span data-stu-id="59d8d-184">90%</span></span>|  
  
 <span data-ttu-id="59d8d-185">例如，如果您的「目標認可的記憶體」為 100 GB，而您估計經記憶體最佳化的資料表和索引需要 60GB 的記憶體，則您可以建立一個 MAX_MEMORY_PERCENT = 67 的資源集區 (需要 60GB / 0.90 = 66.667GB - 四捨五入為 67GB；已安裝 67GB / 100GB = 67%)，確保您的 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] 物件擁有所需的 60GB。</span><span class="sxs-lookup"><span data-stu-id="59d8d-185">For example, if your 'target committed memory' is 100 GB, and you estimate your memory-optimized tables and indexes need 60GBof memory, then you can create a resource pool with MAX_MEMORY_PERCENT = 67 (60GB needed / 0.90 = 66.667GB - round up to 67GB; 67GB / 100GB installed = 67%) to ensure that your [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] objects have the 60GB they need.</span></span>  
  
 <span data-ttu-id="59d8d-186">資料庫繫結至具名的資源集區後，請使用下列查詢查看跨不同資源集區的記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="59d8d-186">Once a database has been bound to a named resource pool, use the following query to see memory allocations across different resource pools.</span></span>  
  
```sql  
SELECT pool_id  
     , Name  
     , min_memory_percent  
     , max_memory_percent  
     , max_memory_kb/1024 AS max_memory_mb  
     , used_memory_kb/1024 AS used_memory_mb   
     , target_memory_kb/1024 AS target_memory_mb  
   FROM sys.dm_resource_governor_resource_pools  
```  
  
 <span data-ttu-id="59d8d-187">此範例輸出表示，記憶體最佳化物件在資源集區 PoolIMOLTP 中取用的記憶體為 1356 MB，上限為 2307 MB。</span><span class="sxs-lookup"><span data-stu-id="59d8d-187">This sample output shows that the memory taken by memory-optimized objects is 1356 MB in resource pool, PoolIMOLTP, with an upper bound of 2307 MB.</span></span> <span data-ttu-id="59d8d-188">此上限可控制對應至此集區的使用者和系統記憶體最佳化物件能夠取用的記憶體總數。</span><span class="sxs-lookup"><span data-stu-id="59d8d-188">This upper bound controls the total memory that can be taken by user and system memory-optimized objects mapped to this pool.</span></span>  
  
 <span data-ttu-id="59d8d-189">**範例輸出** </span><span class="sxs-lookup"><span data-stu-id="59d8d-189">**Sample Output** </span></span>  
<span data-ttu-id="59d8d-190">這個輸出來自前面所建立的資料庫和資料表。</span><span class="sxs-lookup"><span data-stu-id="59d8d-190">This output is from the database and tables we created above.</span></span>  
  
```  
pool_id     Name        min_memory_percent max_memory_percent max_memory_mb used_memory_mb target_memory_mb  
----------- ----------- ------------------ ------------------ ------------- -------------- ----------------   
1           internal    0                  100                3845          125            3845  
2           default     0                  100                3845          32             3845  
259         PoolIMOLTP 0                  100                3845          1356           2307  
```  
  
 <span data-ttu-id="59d8d-191">如需詳細資訊，請參閱 [sys.dm_resource_governor_resource_pools (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="59d8d-191">For more information see [sys.dm_resource_governor_resource_pools (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql).</span></span>  
  
 <span data-ttu-id="59d8d-192">如果您無法將資料庫繫結至具名資源集區，則資料庫會繫結至「預設」集區。</span><span class="sxs-lookup"><span data-stu-id="59d8d-192">If you do not bind your database to a named resource pool, it is bound to the 'default' pool.</span></span> <span data-ttu-id="59d8d-193">由於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在大多數其他配置中會使用預設資源集區，因此您將無法針對所需資料庫精確使用 DMV sys.dm_resource_governor_resource_pools 監視記憶體最佳化資料表所耗用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="59d8d-193">Since default resource pool is used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for most other allocations, you will not be able to monitor memory consumed by memory-optimized tables using the DMV sys.dm_resource_governor_resource_pools accurately for the database of interest.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59d8d-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59d8d-194">See Also</span></span>  
 <span data-ttu-id="59d8d-195">[sys.sp_xtp_bind_db_resource_pool &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-bind-db-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="59d8d-195">[sys.sp_xtp_bind_db_resource_pool &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-bind-db-resource-pool-transact-sql) </span></span>  
 <span data-ttu-id="59d8d-196">[sys.sp_xtp_bind_db_resource_pool &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-unbind-db-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="59d8d-196">[sys.sp_xtp_unbind_db_resource_pool &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-unbind-db-resource-pool-transact-sql) </span></span>  
 <span data-ttu-id="59d8d-197">[資源管理員](../resource-governor/resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="59d8d-197">[Resource Governor](../resource-governor/resource-governor.md) </span></span>  
 <span data-ttu-id="59d8d-198">[資源管理員資源集區](../resource-governor/resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="59d8d-198">[Resource Governor Resource Pool](../resource-governor/resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="59d8d-199">[建立資源集區](../resource-governor/create-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="59d8d-199">[Create a Resource Pool](../resource-governor/create-a-resource-pool.md) </span></span>  
 <span data-ttu-id="59d8d-200">[變更資源集區設定](../resource-governor/change-resource-pool-settings.md) </span><span class="sxs-lookup"><span data-stu-id="59d8d-200">[Change Resource Pool Settings](../resource-governor/change-resource-pool-settings.md) </span></span>  
 [<span data-ttu-id="59d8d-201">刪除資源集區</span><span class="sxs-lookup"><span data-stu-id="59d8d-201">Delete a Resource Pool</span></span>](../resource-governor/delete-a-resource-pool.md)  
  
  
