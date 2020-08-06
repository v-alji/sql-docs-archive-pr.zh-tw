---
title: SQL Server 2014 中已停止的資料庫引擎功能 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: release-landing
ms.topic: conceptual
helpviewer_keywords:
- VIA protocol
- unsupported features [SQL Server]
- SQL Mail
- discontinued functionality [SQL Server]
- RESTORE WITH DBO_ONLY
- BACKUP WITH PASSWORD
- user instances enabled
- BACKUP WITH MEDIAPASSWORD
- AWE
- SQL-DMO
- '*= and =*'
- 80 compatibility levels
- COMPUTE BY
- user instance timeout
- sp_dropalias
- COMPUTE
- WITH APPEND
- sys.database_principal_aliases
- sp_dboption
- DATABASEPROPERTY
- FASTFIRSTROW hint
- SET DISABLE_DEF_CNST_CHK
ms.assetid: d686cdf0-d11d-4dba-9ec8-de1a5f189f25
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e7fbc371526c4623cf289019b506aa01eb683ad0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701644"
---
# <a name="discontinued-database-engine-functionality-in-sql-server-2014"></a><span data-ttu-id="31d5c-102">SQL Server 2014 中已停止的 Database Engine 功能</span><span class="sxs-lookup"><span data-stu-id="31d5c-102">Discontinued Database Engine Functionality in SQL Server 2014</span></span>
  <span data-ttu-id="31d5c-103">本主題描述 [!INCLUDE[ssDE](../includes/ssde-md.md)] 中不再可用的 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]功能。</span><span class="sxs-lookup"><span data-stu-id="31d5c-103">This topic describes the [!INCLUDE[ssDE](../includes/ssde-md.md)] features that are no longer available in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span>  
  
## <a name="discontinued-features-in-sssql14"></a><a name="SQL14"></a><span data-ttu-id="31d5c-104">中已停止的功能[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31d5c-104">Discontinued Features in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]</span></span>  
 <span data-ttu-id="31d5c-105">下表列出已在 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]中移除的功能。</span><span class="sxs-lookup"><span data-stu-id="31d5c-105">The following table lists features that were removed in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span>  
  
|<span data-ttu-id="31d5c-106">類別</span><span class="sxs-lookup"><span data-stu-id="31d5c-106">Category</span></span>|<span data-ttu-id="31d5c-107">已停止的功能</span><span class="sxs-lookup"><span data-stu-id="31d5c-107">Discontinued feature</span></span>|<span data-ttu-id="31d5c-108">取代</span><span class="sxs-lookup"><span data-stu-id="31d5c-108">Replacement</span></span>|  
|--------------|--------------------------|-----------------|  
|<span data-ttu-id="31d5c-109">相容性層級</span><span class="sxs-lookup"><span data-stu-id="31d5c-109">Compatibility level</span></span>|<span data-ttu-id="31d5c-110">90 相容性層級</span><span class="sxs-lookup"><span data-stu-id="31d5c-110">90 compatibility level</span></span>|<span data-ttu-id="31d5c-111">資料庫至少必須設定為相容性層級 100。</span><span class="sxs-lookup"><span data-stu-id="31d5c-111">Databases must be set to at least compatibility level 100.</span></span> <span data-ttu-id="31d5c-112">當相容性層級低於 100 的資料庫升級為 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]時，資料庫的相容性層級會在升級作業期間設定為 100。</span><span class="sxs-lookup"><span data-stu-id="31d5c-112">When a database with a compatibility level of less than 100 is upgraded to [!INCLUDE[ssSQL14](../includes/sssql14-md.md)], the compatibility level of the database is set to 100 during the upgrade operation.</span></span>|  
  
## <a name="discontinued-features-in-sssql11"></a><a name="Denali"></a><span data-ttu-id="31d5c-113">中已停止的功能[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31d5c-113">Discontinued Features in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]</span></span>  
 <span data-ttu-id="31d5c-114">下表列出已在 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]中移除的功能。</span><span class="sxs-lookup"><span data-stu-id="31d5c-114">The following table lists features that were removed in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span></span>  
  
|<span data-ttu-id="31d5c-115">類別</span><span class="sxs-lookup"><span data-stu-id="31d5c-115">Category</span></span>|<span data-ttu-id="31d5c-116">已停止的功能</span><span class="sxs-lookup"><span data-stu-id="31d5c-116">Discontinued feature</span></span>|<span data-ttu-id="31d5c-117">取代</span><span class="sxs-lookup"><span data-stu-id="31d5c-117">Replacement</span></span>|  
|--------------|--------------------------|-----------------|  
|<span data-ttu-id="31d5c-118">備份與還原</span><span class="sxs-lookup"><span data-stu-id="31d5c-118">Backup and Restore</span></span>|<span data-ttu-id="31d5c-119">**備份 {資料庫 &#124; LOG} （含密碼**）和**備份 {資料庫 &#124; log} 已停用 MEDIAPASSWORD** 。</span><span class="sxs-lookup"><span data-stu-id="31d5c-119">**BACKUP { DATABASE &#124; LOG } WITH PASSWORD** and **BACKUP { DATABASE &#124; LOG } WITH MEDIAPASSWORD** are discontinued.</span></span> <span data-ttu-id="31d5c-120">**RESTORE {DATABASE &#124; LOG} WITH [MEDIA] 密碼**會繼續被取代。</span><span class="sxs-lookup"><span data-stu-id="31d5c-120">**RESTORE { DATABASE &#124; LOG } WITH [MEDIA]PASSWORD**continues to be deprecated.</span></span>|<span data-ttu-id="31d5c-121">無</span><span class="sxs-lookup"><span data-stu-id="31d5c-121">None</span></span>|  
|<span data-ttu-id="31d5c-122">備份與還原</span><span class="sxs-lookup"><span data-stu-id="31d5c-122">Backup and Restore</span></span>|<span data-ttu-id="31d5c-123">**還原 {資料庫 &#124; 記錄檔} .。。使用 DBO_ONLY**</span><span class="sxs-lookup"><span data-stu-id="31d5c-123">**RESTORE { DATABASE &#124; LOG } ... WITH DBO_ONLY**</span></span>|<span data-ttu-id="31d5c-124">**還原 {資料庫 &#124; 記錄檔} ... .。。使用 RESTRICTED_USER**</span><span class="sxs-lookup"><span data-stu-id="31d5c-124">**RESTORE { DATABASE &#124; LOG } ... ... WITH RESTRICTED_USER**</span></span>|  
|<span data-ttu-id="31d5c-125">相容性層級</span><span class="sxs-lookup"><span data-stu-id="31d5c-125">Compatibility level</span></span>|<span data-ttu-id="31d5c-126">80 相容性層級</span><span class="sxs-lookup"><span data-stu-id="31d5c-126">80 compatibility level</span></span>|<span data-ttu-id="31d5c-127">資料庫至少必須設定為相容性層級 90。</span><span class="sxs-lookup"><span data-stu-id="31d5c-127">Databases must be set to at least compatibility level 90.</span></span>|  
|<span data-ttu-id="31d5c-128">設定選項</span><span class="sxs-lookup"><span data-stu-id="31d5c-128">Configuration Options</span></span>|<span data-ttu-id="31d5c-129">`sp_configure 'user instance timeout'` 和 `'user instances enabled'`</span><span class="sxs-lookup"><span data-stu-id="31d5c-129">`sp_configure 'user instance timeout'` and `'user instances enabled'`</span></span>|<span data-ttu-id="31d5c-130">使用本機資料庫功能。</span><span class="sxs-lookup"><span data-stu-id="31d5c-130">Use the Local Database feature.</span></span> <span data-ttu-id="31d5c-131">如需詳細資訊，請參閱[SqlLocalDB 公用程式](../tools/sqllocaldb-utility.md)</span><span class="sxs-lookup"><span data-stu-id="31d5c-131">For more information, see [SqlLocalDB Utility](../tools/sqllocaldb-utility.md)</span></span>|  
|<span data-ttu-id="31d5c-132">連接通訊協定</span><span class="sxs-lookup"><span data-stu-id="31d5c-132">Connection protocols</span></span>|<span data-ttu-id="31d5c-133">VIA 通訊協定支援已停用。</span><span class="sxs-lookup"><span data-stu-id="31d5c-133">Support for the VIA protocol is discontinued.</span></span>|<span data-ttu-id="31d5c-134">請改用 TCP。</span><span class="sxs-lookup"><span data-stu-id="31d5c-134">Use TCP instead.</span></span>|  
|<span data-ttu-id="31d5c-135">資料庫物件</span><span class="sxs-lookup"><span data-stu-id="31d5c-135">Database objects</span></span>|<span data-ttu-id="31d5c-136">觸發程序上的 `WITH APPEND` 子句</span><span class="sxs-lookup"><span data-stu-id="31d5c-136">`WITH APPEND` clause on triggers</span></span>|<span data-ttu-id="31d5c-137">請重新建立整個觸發程序。</span><span class="sxs-lookup"><span data-stu-id="31d5c-137">Re-create the whole trigger.</span></span>|  
|<span data-ttu-id="31d5c-138">資料庫選項</span><span class="sxs-lookup"><span data-stu-id="31d5c-138">Database options</span></span>|`sp_dboption`|`ALTER DATABASE`|  
|<span data-ttu-id="31d5c-139">郵件</span><span class="sxs-lookup"><span data-stu-id="31d5c-139">Mail</span></span>|<span data-ttu-id="31d5c-140">SQL Mail</span><span class="sxs-lookup"><span data-stu-id="31d5c-140">SQL Mail</span></span>|<span data-ttu-id="31d5c-141">使用 Database Mail。</span><span class="sxs-lookup"><span data-stu-id="31d5c-141">Use Database Mail.</span></span> <span data-ttu-id="31d5c-142">如需詳細資訊，請參閱＜ [Database Mail](../relational-databases/database-mail/database-mail.md) ＞和＜  [Use Database Mail Instead of SQL Mail](../relational-databases/policy-based-management/use-database-mail-instead-of-sql-mail.md)＞。</span><span class="sxs-lookup"><span data-stu-id="31d5c-142">For more information, see [Database Mail](../relational-databases/database-mail/database-mail.md) and  [Use Database Mail Instead of SQL Mail](../relational-databases/policy-based-management/use-database-mail-instead-of-sql-mail.md).</span></span>|  
|<span data-ttu-id="31d5c-143">記憶體管理</span><span class="sxs-lookup"><span data-stu-id="31d5c-143">Memory Management</span></span>|<span data-ttu-id="31d5c-144">32 位元 Address Windowing Extensions (AWE) 和 32 位元 Hot Add Memory 支援。</span><span class="sxs-lookup"><span data-stu-id="31d5c-144">32-bit Address Windowing Extensions (AWE) and 32-bit Hot Add memory support.</span></span>|<span data-ttu-id="31d5c-145">使用 64 位元作業系統。</span><span class="sxs-lookup"><span data-stu-id="31d5c-145">Use a 64-bit operating system.</span></span>|  
|<span data-ttu-id="31d5c-146">中繼資料</span><span class="sxs-lookup"><span data-stu-id="31d5c-146">Metadata</span></span>|`DATABASEPROPERTY`|`DATABASEPROPERTYEX`|  
|<span data-ttu-id="31d5c-147">可程式性</span><span class="sxs-lookup"><span data-stu-id="31d5c-147">Programmability</span></span>|<span data-ttu-id="31d5c-148">SQL Server Distributed Management Objects (SQL-DMO)</span><span class="sxs-lookup"><span data-stu-id="31d5c-148">SQL Server Distributed Management Objects (SQL-DMO)</span></span>|<span data-ttu-id="31d5c-149">SQL Server 管理物件 (SMO)</span><span class="sxs-lookup"><span data-stu-id="31d5c-149">SQL Server Management Objects (SMO)</span></span>|  
|<span data-ttu-id="31d5c-150">查詢提示</span><span class="sxs-lookup"><span data-stu-id="31d5c-150">Query hints</span></span>|<span data-ttu-id="31d5c-151">`FASTFIRSTROW` 提示</span><span class="sxs-lookup"><span data-stu-id="31d5c-151">`FASTFIRSTROW` hint</span></span>|<span data-ttu-id="31d5c-152">`OPTION (FAST`*n* `)` 。</span><span class="sxs-lookup"><span data-stu-id="31d5c-152">`OPTION (FAST` *n* `)`.</span></span>|  
|<span data-ttu-id="31d5c-153">遠端伺服器</span><span class="sxs-lookup"><span data-stu-id="31d5c-153">Remote servers</span></span>|<span data-ttu-id="31d5c-154">使用者已無法使用 `sp_addserver` 建立新的遠端伺服器。</span><span class="sxs-lookup"><span data-stu-id="31d5c-154">The ability for users to create new remote servers by using `sp_addserver` is discontinued.</span></span> <span data-ttu-id="31d5c-155">`sp_addserver` 與 'local' 選項仍可使用。</span><span class="sxs-lookup"><span data-stu-id="31d5c-155">`sp_addserver` with the 'local' option remains available.</span></span> <span data-ttu-id="31d5c-156">升級期間所保留或複寫所建立的遠端伺服器仍然可以使用。</span><span class="sxs-lookup"><span data-stu-id="31d5c-156">Remote servers preserved during upgrade or created by replication can be used.</span></span>|<span data-ttu-id="31d5c-157">使用連結的伺服器取代遠端伺服器。</span><span class="sxs-lookup"><span data-stu-id="31d5c-157">Replace remote servers by using linked servers.</span></span>|  
|<span data-ttu-id="31d5c-158">安全性</span><span class="sxs-lookup"><span data-stu-id="31d5c-158">Security</span></span>|`sp_dropalias`|<span data-ttu-id="31d5c-159">以使用者帳戶和資料庫角色的組合來取代別名。</span><span class="sxs-lookup"><span data-stu-id="31d5c-159">Replace aliases with a combination of user accounts and database roles.</span></span> <span data-ttu-id="31d5c-160">請使用 `sp_dropalias`，在升級的資料庫中移除別名。</span><span class="sxs-lookup"><span data-stu-id="31d5c-160">Use `sp_dropalias` to remove aliases in upgraded databases.</span></span>|  
|<span data-ttu-id="31d5c-161">安全性</span><span class="sxs-lookup"><span data-stu-id="31d5c-161">Security</span></span>|<span data-ttu-id="31d5c-162">代表早於 **2000 之登入值的版本參數** PWDCOMPARE [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 已停止。</span><span class="sxs-lookup"><span data-stu-id="31d5c-162">The version parameter of **PWDCOMPARE** representing a value from a login earlier than [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2000 is discontinued.</span></span>|<span data-ttu-id="31d5c-163">無</span><span class="sxs-lookup"><span data-stu-id="31d5c-163">None</span></span>|  
|<span data-ttu-id="31d5c-164">SMO 中的 Service Broker 可程式性</span><span class="sxs-lookup"><span data-stu-id="31d5c-164">Service Broker programmability in SMO</span></span>|<span data-ttu-id="31d5c-165">**Microsoft.SqlServer.Management.Smo.Broker.BrokerPriority** 類別不再實作 **Microsoft.SqlServer.Management.Smo.IObjectPermission** 介面。</span><span class="sxs-lookup"><span data-stu-id="31d5c-165">The **Microsoft.SqlServer.Management.Smo.Broker.BrokerPriority** class no longer implements the **Microsoft.SqlServer.Management.Smo.IObjectPermission** interface.</span></span>||  
|<span data-ttu-id="31d5c-166">Set 選項</span><span class="sxs-lookup"><span data-stu-id="31d5c-166">SET options</span></span>|`SET DISABLE_DEF_CNST_CHK`|<span data-ttu-id="31d5c-167">無。</span><span class="sxs-lookup"><span data-stu-id="31d5c-167">None.</span></span>|  
|<span data-ttu-id="31d5c-168">系統資料表</span><span class="sxs-lookup"><span data-stu-id="31d5c-168">System tables</span></span>|<span data-ttu-id="31d5c-169">sys.database_principal_aliases</span><span class="sxs-lookup"><span data-stu-id="31d5c-169">sys.database_principal_aliases</span></span>|<span data-ttu-id="31d5c-170">請使用角色，而非別名。</span><span class="sxs-lookup"><span data-stu-id="31d5c-170">Use roles instead of aliases.</span></span>|  
|<span data-ttu-id="31d5c-171">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="31d5c-171">Transact-SQL</span></span>|<span data-ttu-id="31d5c-172">`RAISERROR` 格式的 `RAISERROR integer 'string'` 已停止。</span><span class="sxs-lookup"><span data-stu-id="31d5c-172">`RAISERROR` in the format `RAISERROR integer 'string'` is discontinued.</span></span>|<span data-ttu-id="31d5c-173">請使用目前的\*\*RAISERROR ( ... ) \*\*語法來重寫語句。</span><span class="sxs-lookup"><span data-stu-id="31d5c-173">Rewrite the statement using the current **RAISERROR(...)** syntax.</span></span>|  
|<span data-ttu-id="31d5c-174">Transact-SQL 語法</span><span class="sxs-lookup"><span data-stu-id="31d5c-174">Transact-SQL syntax</span></span>|`COMPUTE / COMPUTE BY`|<span data-ttu-id="31d5c-175">使用`ROLLUP`</span><span class="sxs-lookup"><span data-stu-id="31d5c-175">Use `ROLLUP`</span></span>|  
|<span data-ttu-id="31d5c-176">Transact-SQL 語法</span><span class="sxs-lookup"><span data-stu-id="31d5c-176">Transact-SQL syntax</span></span>|<span data-ttu-id="31d5c-177">使用 **\*=** 和 **=&#42;**</span><span class="sxs-lookup"><span data-stu-id="31d5c-177">Use of **\*=** and **=&#42;**</span></span>|<span data-ttu-id="31d5c-178">使用 ANSI 聯結語法。</span><span class="sxs-lookup"><span data-stu-id="31d5c-178">Use ANSI join syntax.</span></span> <span data-ttu-id="31d5c-179">如需詳細資訊，請參閱 [FROM (Transact-SQL)。](https://msdn.microsoft.com/library/ms177634\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="31d5c-179">For more information, see [FROM (Transact-SQL).](https://msdn.microsoft.com/library/ms177634\(SQL.105\).aspx)</span></span>|  
|<span data-ttu-id="31d5c-180">XEvents</span><span class="sxs-lookup"><span data-stu-id="31d5c-180">XEvents</span></span>|<span data-ttu-id="31d5c-181">databases_data_file_size_changed、databases_log_file_size_changed</span><span class="sxs-lookup"><span data-stu-id="31d5c-181">databases_data_file_size_changed, databases_log_file_size_changed</span></span><br /><br /> <span data-ttu-id="31d5c-182">eventdatabases_log_file_used_size_changed</span><span class="sxs-lookup"><span data-stu-id="31d5c-182">eventdatabases_log_file_used_size_changed</span></span><br /><br /> <span data-ttu-id="31d5c-183">locks_lock_timeouts_greater_than_0</span><span class="sxs-lookup"><span data-stu-id="31d5c-183">locks_lock_timeouts_greater_than_0</span></span><br /><br /> <span data-ttu-id="31d5c-184">locks_lock_timeouts</span><span class="sxs-lookup"><span data-stu-id="31d5c-184">locks_lock_timeouts</span></span>|<span data-ttu-id="31d5c-185">已取代為 database_file_size_change event、database_file_size_change</span><span class="sxs-lookup"><span data-stu-id="31d5c-185">Replaced by database_file_size_change event, database_file_size_change</span></span><br /><br /> <span data-ttu-id="31d5c-186">database_file_size_change event</span><span class="sxs-lookup"><span data-stu-id="31d5c-186">database_file_size_change event</span></span><br /><br /> <span data-ttu-id="31d5c-187">lock_timeout_greater_than_0</span><span class="sxs-lookup"><span data-stu-id="31d5c-187">lock_timeout_greater_than_0</span></span><br /><br /> <span data-ttu-id="31d5c-188">lock_timeout</span><span class="sxs-lookup"><span data-stu-id="31d5c-188">lock_timeout</span></span>|  
  
 <span data-ttu-id="31d5c-189">**其他 XEvent 變更**</span><span class="sxs-lookup"><span data-stu-id="31d5c-189">**Additional XEvent changes**</span></span>  
  
 <span data-ttu-id="31d5c-190">**resource_monitor_ring_buffer_record**：</span><span class="sxs-lookup"><span data-stu-id="31d5c-190">**resource_monitor_ring_buffer_record**:</span></span>  
  
-   <span data-ttu-id="31d5c-191">移除的欄位：single_pages_kb、multiple_pages_kb</span><span class="sxs-lookup"><span data-stu-id="31d5c-191">Fields removed: single_pages_kb, multiple_pages_kb</span></span>  
  
-   <span data-ttu-id="31d5c-192">加入的欄位：target_kb、pages_kb</span><span class="sxs-lookup"><span data-stu-id="31d5c-192">Fields added: target_kb, pages_kb</span></span>  
  
 <span data-ttu-id="31d5c-193">**memory_node_oom_ring_buffer_recorded**：</span><span class="sxs-lookup"><span data-stu-id="31d5c-193">**memory_node_oom_ring_buffer_recorded**:</span></span>  
  
-   <span data-ttu-id="31d5c-194">移除的欄位：single_pages_kb、multiple_pages_kb</span><span class="sxs-lookup"><span data-stu-id="31d5c-194">Fields removed: single_pages_kb, multiple_pages_kb</span></span>  
  
-   <span data-ttu-id="31d5c-195">加入的欄位：target_kb、pages_kb</span><span class="sxs-lookup"><span data-stu-id="31d5c-195">Fields added: target_kb, pages_kb</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31d5c-196">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31d5c-196">See Also</span></span>  
 [<span data-ttu-id="31d5c-197">SQL Server 2014 中已被取代的 Database Engine 功能</span><span class="sxs-lookup"><span data-stu-id="31d5c-197">Deprecated Database Engine Features in SQL Server 2014</span></span>](deprecated-database-engine-features-in-sql-server-2016.md?view=sql-server-2014)  
  
  
