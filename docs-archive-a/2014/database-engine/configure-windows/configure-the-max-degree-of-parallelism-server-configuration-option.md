---
title: 設定 max degree of parallelism 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- parallel queries [SQL Server]
- processors [SQL Server], parallel queries
- number of processors for parallel queries
- max degree of parallelism option
ms.assetid: 86b65bf1-a6a1-4670-afc0-cdfad1558032
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 824dc837142acc4a0898cb04b4a8687bc5be4043
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597347"
---
# <a name="configure-the-max-degree-of-parallelism-server-configuration-option"></a><span data-ttu-id="e364a-102">設定 max degree of parallelism 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="e364a-102">Configure the max degree of parallelism Server Configuration Option</span></span>
  <span data-ttu-id="e364a-103">本主題描述如何 `max degree of parallelism` 使用或，在中設定 server configuration 選項 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e364a-103">This topic describes how to configure the `max degree of parallelism` server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="e364a-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體在具有多個微處理器或 CPU 的電腦上執行時，會偵測平行處理原則的最佳程度，也就是說，針對每一個平行計畫的執行，執行單一陳述式所要採用的處理器個數。</span><span class="sxs-lookup"><span data-stu-id="e364a-104">When an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] runs on a computer that has more than one microprocessor or CPU, it detects the best degree of parallelism, that is, the number of processors employed to run a single statement, for each parallel plan execution.</span></span> <span data-ttu-id="e364a-105">您可以使用 `max degree of parallelism` 選項來限制執行平行計畫所用的處理器數目。</span><span class="sxs-lookup"><span data-stu-id="e364a-105">You can use the `max degree of parallelism` option to limit the number of processors to use in parallel plan execution.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e364a-106">會針對查詢、索引資料定義語言 (DDL) 作業，以及靜態和索引鍵集驅動資料指標擴展，考慮進行平行執行計畫。</span><span class="sxs-lookup"><span data-stu-id="e364a-106">considers parallel execution plans for queries, index data definition language (DDL) operations, and static and keyset-driven cursor population.</span></span>  
  
 <span data-ttu-id="e364a-107">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="e364a-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e364a-108">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="e364a-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e364a-109">限制事項</span><span class="sxs-lookup"><span data-stu-id="e364a-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="e364a-110">建議</span><span class="sxs-lookup"><span data-stu-id="e364a-110">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="e364a-111">安全性</span><span class="sxs-lookup"><span data-stu-id="e364a-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e364a-112">**使用下列方法設定 max degree of parallelism 選項：**</span><span class="sxs-lookup"><span data-stu-id="e364a-112">**To configure the max degree of parallelism option, using:**</span></span>  
  
     [<span data-ttu-id="e364a-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e364a-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e364a-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e364a-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="e364a-115">**待處理**  [設定 max degree of parallelism 選項之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="e364a-115">**Follow Up:**  [After you configure the max degree of parallelism option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e364a-116">開始之前</span><span class="sxs-lookup"><span data-stu-id="e364a-116">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="e364a-117">限制事項</span><span class="sxs-lookup"><span data-stu-id="e364a-117">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="e364a-118">如果 affinity mask 選項不是設成預設值，它可能會限制對稱式多處理 (SMP) 系統上 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可用的處理器個數。</span><span class="sxs-lookup"><span data-stu-id="e364a-118">If the affinity mask option is not set to the default, it may restrict the number of processors available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on symmetric multiprocessing (SMP) systems.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="e364a-119">建議</span><span class="sxs-lookup"><span data-stu-id="e364a-119">Recommendations</span></span>  
  
-   <span data-ttu-id="e364a-120">這個選項是進階選項，只有有經驗的資料庫管理員或通過認證的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術人員才可變更。</span><span class="sxs-lookup"><span data-stu-id="e364a-120">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="e364a-121">若要讓伺服器判斷平行處理原則的最大程度，請將此選項設定為 0 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="e364a-121">To enable the server to determine the maximum degree of parallelism, set this option to 0, the default value.</span></span> <span data-ttu-id="e364a-122">將平行處理原則的最大程度設定為 0 就會允許 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用所有可用的處理器 (最多 64 個處理器)。</span><span class="sxs-lookup"><span data-stu-id="e364a-122">Setting maximum degree of parallelism to 0 allows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to use all the available processors up to 64 processors.</span></span> <span data-ttu-id="e364a-123">若要抑制平行計畫的產生，請將 `max degree of parallelism` 設定為 1。</span><span class="sxs-lookup"><span data-stu-id="e364a-123">To suppress parallel plan generation, set `max degree of parallelism` to 1.</span></span> <span data-ttu-id="e364a-124">將此值設成 1 到 32,767 的數字會指定單一查詢執行可用的最大處理器核心數目。</span><span class="sxs-lookup"><span data-stu-id="e364a-124">Set the value to a number from 1 to 32,767 to specify the maximum number of processor cores that can be used by a single query execution.</span></span> <span data-ttu-id="e364a-125">如果指定的數值大於可用的處理器數目，就會使用可用處理器的實際數目。</span><span class="sxs-lookup"><span data-stu-id="e364a-125">If a value greater than the number of available processors is specified, the actual number of available processors is used.</span></span> <span data-ttu-id="e364a-126">如果電腦只有一個處理器，則會忽略 `max degree of parallelism` 值。</span><span class="sxs-lookup"><span data-stu-id="e364a-126">If the computer has only one processor, the `max degree of parallelism` value is ignored.</span></span>  
  
-   <span data-ttu-id="e364a-127">您可以在查詢陳述適中指定 MAXDOP 查詢提示，來覆寫查詢中的 max degree of parallelism 值。</span><span class="sxs-lookup"><span data-stu-id="e364a-127">You can override the max degree of parallelism value in queries by specifying the MAXDOP query hint in the query statement.</span></span> <span data-ttu-id="e364a-128">如需詳細資訊，請參閱[查詢提示 &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query)。</span><span class="sxs-lookup"><span data-stu-id="e364a-128">For more information, see [Query Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query).</span></span>  
  
-   <span data-ttu-id="e364a-129">建立或重建索引的索引作業，或者卸除叢集索引的索引作業，都需要大量資源。</span><span class="sxs-lookup"><span data-stu-id="e364a-129">Index operations that create or rebuild an index, or that drop a clustered index, can be resource intensive.</span></span> <span data-ttu-id="e364a-130">您可以在索引陳述式中指定 MAXDOP 索引選項，覆寫索引作業中的 max degree of parallelism 值。</span><span class="sxs-lookup"><span data-stu-id="e364a-130">You can override the max degree of parallelism value for index operations by specifying the MAXDOP index option in the index statement.</span></span> <span data-ttu-id="e364a-131">MAXDOP 值會在執行時套用至陳述式，且不會儲存在索引中繼資料內。</span><span class="sxs-lookup"><span data-stu-id="e364a-131">The MAXDOP value is applied to the statement at execution time and is not stored in the index metadata.</span></span> <span data-ttu-id="e364a-132">如需詳細資訊，請參閱 [設定平行索引作業](../../relational-databases/indexes/configure-parallel-index-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="e364a-132">For more information, see [Configure Parallel Index Operations](../../relational-databases/indexes/configure-parallel-index-operations.md).</span></span>  
  
-   <span data-ttu-id="e364a-133">除了查詢作業和索引作業外，此選項也會控制 DBCC CHECKTABLE、DBCC CHECKDB 和 DBCC CHECKFILEGROUP 的平行處理原則。</span><span class="sxs-lookup"><span data-stu-id="e364a-133">In addition to queries and index operations, this option also controls the parallelism of DBCC CHECKTABLE, DBCC CHECKDB, and DBCC CHECKFILEGROUP.</span></span> <span data-ttu-id="e364a-134">您可以使用追蹤旗標 2528 來停用這些陳述式的平行執行計畫。</span><span class="sxs-lookup"><span data-stu-id="e364a-134">You can disable parallel execution plans for these statements by using trace flag 2528.</span></span> <span data-ttu-id="e364a-135">如需詳細資訊，請參閱[追蹤旗標 &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e364a-135">For more information, see [Trace Flags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e364a-136">Security</span><span class="sxs-lookup"><span data-stu-id="e364a-136">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e364a-137">權限</span><span class="sxs-lookup"><span data-stu-id="e364a-137">Permissions</span></span>  
 <span data-ttu-id="e364a-138">不含參數或只含第一個參數之 **sp_configure** 上的執行權限預設會授與所有使用者。</span><span class="sxs-lookup"><span data-stu-id="e364a-138">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="e364a-139">以同時設定兩個參數的 **sp_configure** 來變更組態選項或執行 RECONFIGURE 陳述式時，使用者必須取得 ALTER SETTINGS 伺服器層級權限。</span><span class="sxs-lookup"><span data-stu-id="e364a-139">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="e364a-140">**系統管理員 (sysadmin)** 及 **serveradmin** 固定伺服器角色會隱含 ALTER SETTINGS 權限。</span><span class="sxs-lookup"><span data-stu-id="e364a-140">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e364a-141">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e364a-141">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-max-degree-of-parallelism-option"></a><span data-ttu-id="e364a-142">設定 max degree of parallelism 選項</span><span class="sxs-lookup"><span data-stu-id="e364a-142">To configure the max degree of parallelism option</span></span>  
  
1.  <span data-ttu-id="e364a-143">在 **[物件總管]** 中，以滑鼠右鍵按一下伺服器，然後選取 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="e364a-143">In **Object Explorer**, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="e364a-144">按一下 **[進階]** 節點。</span><span class="sxs-lookup"><span data-stu-id="e364a-144">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="e364a-145">在 **[平行處理原則的最大程度]** 方塊中，選取用於執行平行計畫的最大處理器數目。</span><span class="sxs-lookup"><span data-stu-id="e364a-145">In the **Max Degree of Parallelism** box, select the maximum number of processors to use in parallel plan execution.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e364a-146">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e364a-146">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-max-degree-of-parallelism-option"></a><span data-ttu-id="e364a-147">設定 max degree of parallelism 選項</span><span class="sxs-lookup"><span data-stu-id="e364a-147">To configure the max degree of parallelism option</span></span>  
  
1.  <span data-ttu-id="e364a-148">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e364a-148">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e364a-149">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="e364a-149">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e364a-150">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="e364a-150">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="e364a-151">此範例示範如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 將 `max degree of parallelism` 選項設定為 `8`。</span><span class="sxs-lookup"><span data-stu-id="e364a-151">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to configure the `max degree of parallelism` option to `8`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO   
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE WITH OVERRIDE;  
GO  
EXEC sp_configure 'max degree of parallelism', 8;  
GO  
RECONFIGURE WITH OVERRIDE;  
GO  
```  
  
 <span data-ttu-id="e364a-152">如需詳細資訊，請參閱 [伺服器設定選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md)伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="e364a-152">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-max-degree-of-parallelism-option"></a><a name="FollowUp"></a> <span data-ttu-id="e364a-153">後續操作：在您設定完最大平行處理程度的選項後</span><span class="sxs-lookup"><span data-stu-id="e364a-153">Follow Up: After you configure the max degree of parallelism option</span></span>  
 <span data-ttu-id="e364a-154">設定會立即生效，不需要重新啟動伺服器。</span><span class="sxs-lookup"><span data-stu-id="e364a-154">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e364a-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e364a-155">See Also</span></span>  
 <span data-ttu-id="e364a-156">[affinity mask 伺服器組態選項](affinity-mask-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="e364a-156">[affinity mask Server Configuration Option](affinity-mask-server-configuration-option.md) </span></span>  
 <span data-ttu-id="e364a-157">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e364a-157">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="e364a-158">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e364a-158">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="e364a-159">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e364a-159">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="e364a-160">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e364a-160">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 <span data-ttu-id="e364a-161">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e364a-161">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span></span>  
 <span data-ttu-id="e364a-162">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e364a-162">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span></span>  
 <span data-ttu-id="e364a-163">[DBCC CHECKTABLE &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-checktable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e364a-163">[DBCC CHECKTABLE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checktable-transact-sql) </span></span>  
 <span data-ttu-id="e364a-164">[DBCC CHECKDB &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e364a-164">[DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span></span>  
 <span data-ttu-id="e364a-165">[DBCC CHECKFILEGROUP &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-checkfilegroup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e364a-165">[DBCC CHECKFILEGROUP &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkfilegroup-transact-sql) </span></span>  
 <span data-ttu-id="e364a-166">[設定平行索引作業](../../relational-databases/indexes/configure-parallel-index-operations.md) </span><span class="sxs-lookup"><span data-stu-id="e364a-166">[Configure Parallel Index Operations](../../relational-databases/indexes/configure-parallel-index-operations.md) </span></span>  
 <span data-ttu-id="e364a-167">[查詢提示 &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query) </span><span class="sxs-lookup"><span data-stu-id="e364a-167">[Query Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query) </span></span>  
 [<span data-ttu-id="e364a-168">設定索引選項</span><span class="sxs-lookup"><span data-stu-id="e364a-168">Set Index Options</span></span>](../../relational-databases/indexes/set-index-options.md)  
  
  
