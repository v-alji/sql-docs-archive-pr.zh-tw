---
title: 啟用和停用異動資料擷取 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- change data capture [SQL Server], enabling tables
- change data capture [SQL Server], enabling databases
- change data capture [SQL Server], disabling databases
- change data capture [SQL Server], disabling tables
ms.assetid: b741894f-d267-4b10-adfe-cbc14aa6caeb
author: rothja
ms.author: jroth
ms.openlocfilehash: df0a2fd4a2c6ffb2de58d6b52360d1730d0fa7df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595864"
---
# <a name="enable-and-disable-change-data-capture-sql-server"></a><span data-ttu-id="2e572-102">啟用和停用異動資料擷取 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2e572-102">Enable and Disable Change Data Capture (SQL Server)</span></span>
  <span data-ttu-id="2e572-103">此主題描述如何針對資料庫和資料表啟用及停用異動資料擷取。</span><span class="sxs-lookup"><span data-stu-id="2e572-103">This topic describes how to enable and disable change data capture for a database and a table.</span></span>  
  
## <a name="enable-change-data-capture-for-a-database"></a><span data-ttu-id="2e572-104">針對資料庫啟用異動資料擷取</span><span class="sxs-lookup"><span data-stu-id="2e572-104">Enable Change Data Capture for a Database</span></span>  
 <span data-ttu-id="2e572-105">針對個別資料表建立擷取執行個體之前，`sysadmin` 固定伺服器角色的成員必須先啟用異動資料擷取的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2e572-105">Before a capture instance can be created for individual tables, a member of the `sysadmin` fixed server role must first enable the database for change data capture.</span></span> <span data-ttu-id="2e572-106">這項步驟可透過在資料庫內容中執行 [sys.sp_cdc_enable_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-enable-db-transact-sql) 預存程序完成。</span><span class="sxs-lookup"><span data-stu-id="2e572-106">This is done by running the stored procedure [sys.sp_cdc_enable_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-enable-db-transact-sql) in the database context.</span></span> <span data-ttu-id="2e572-107">若要判斷資料庫是否已經啟用，請查詢 `is_cdc_enabled` 目錄檢視中的 `sys.databases` 資料行。</span><span class="sxs-lookup"><span data-stu-id="2e572-107">To determine if a database is already enabled, query the `is_cdc_enabled` column in the `sys.databases` catalog view.</span></span>  
  
 <span data-ttu-id="2e572-108">啟用異動資料擷取的資料庫時，也會針對資料庫建立 `cdc` 結構描述、`cdc` 使用者、中繼資料表，以及其他系統物件。</span><span class="sxs-lookup"><span data-stu-id="2e572-108">When a database is enabled for change data capture, the `cdc` schema, `cdc` user, metadata tables, and other system objects are created for the database.</span></span> <span data-ttu-id="2e572-109">`cdc` 結構描述包含異動資料擷取中繼資料表，以及啟用異動資料擷取的來源資料表後，當做變更資料儲存機制使用的個別變更資料表。</span><span class="sxs-lookup"><span data-stu-id="2e572-109">The `cdc` schema contains the change data capture metadata tables and, after source tables are enabled for change data capture, the individual change tables serve as a repository for change data.</span></span> <span data-ttu-id="2e572-110">`cdc` 結構描述也包含用來查詢變更資料的相關聯系統函數。</span><span class="sxs-lookup"><span data-stu-id="2e572-110">The `cdc` schema also contains associated system functions used to query for change data.</span></span>  
  
 <span data-ttu-id="2e572-111">異動資料擷取需要獨佔使用 `cdc` 結構描述與 `cdc` 使用者。</span><span class="sxs-lookup"><span data-stu-id="2e572-111">Change data capture requires exclusive use of the `cdc` schema and `cdc` user.</span></span> <span data-ttu-id="2e572-112">如果名稱為 *cdc* 的結構描述或資料庫使用者目前存在於資料庫中，就無法啟用異動資料擷取的資料庫，直到卸除或重新命名結構描述和 (或) 使用者為止。</span><span class="sxs-lookup"><span data-stu-id="2e572-112">If either a schema or a database user named *cdc* currently exists in a database, the database cannot be enabled for change data capture until the schema and or user are dropped or renamed.</span></span>  
  
 <span data-ttu-id="2e572-113">如需啟用資料庫的範例，請參閱「啟用異動資料擷取的資料庫」範本。</span><span class="sxs-lookup"><span data-stu-id="2e572-113">See the Enable Database for Change Data Capture template for an example of enabling a database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2e572-114">若要在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中找出範本，請移至 **[檢視]** 、按一下 **[範本總管]** ，然後選取 **[SQL Server 範本]** 。</span><span class="sxs-lookup"><span data-stu-id="2e572-114">To locate the templates in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], go to **View**, click **Template Explorer**, and then select **SQL Server Templates**.</span></span> <span data-ttu-id="2e572-115">**[異動資料擷取]** 是子資料夾。</span><span class="sxs-lookup"><span data-stu-id="2e572-115">**Change Data Capture** is a sub-folder.</span></span> <span data-ttu-id="2e572-116">在這個資料夾底下，您將會找到這個主題所參考的所有範本。</span><span class="sxs-lookup"><span data-stu-id="2e572-116">Under this folder, you will find all the templates referenced in this topic.</span></span> <span data-ttu-id="2e572-117">**工具列上也有一個** [範本總管] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 圖示。</span><span class="sxs-lookup"><span data-stu-id="2e572-117">There is also a **Template Explorer** icon on the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] toolbar.</span></span>  
  
```sql  
-- ====  
-- Enable Database for CDC template   
-- ====  
USE MyDB  
GO  
EXEC sys.sp_cdc_enable_db  
GO  
```  
  
## <a name="disable-change-data-capture-for-a-database"></a><span data-ttu-id="2e572-118">針對資料庫停用異動資料擷取</span><span class="sxs-lookup"><span data-stu-id="2e572-118">Disable Change Data Capture for a Database</span></span>  
 <span data-ttu-id="2e572-119">`sysadmin`系統固定伺服器角色的成員可以在資料庫內容中執行預存[程式 Sp_cdc_disable_db &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-disable-db-transact-sql) ，以停用資料庫的變更資料捕獲。</span><span class="sxs-lookup"><span data-stu-id="2e572-119">A member of the `sysadmin` fixed server role can run the stored procedure [sys.sp_cdc_disable_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-disable-db-transact-sql) in the database context to disable change data capture for a database.</span></span> <span data-ttu-id="2e572-120">在您停用資料庫之前，不需要停用個別資料表。</span><span class="sxs-lookup"><span data-stu-id="2e572-120">It is not necessary to disable individual tables before you disable the database.</span></span> <span data-ttu-id="2e572-121">停用資料庫就會移除所有相關聯的異動資料擷取中繼資料，包括 `cdc` 使用者和結構描述以及異動資料擷取作業。</span><span class="sxs-lookup"><span data-stu-id="2e572-121">Disabling the database removes all associated change data capture metadata, including the `cdc` user and schema and the change data capture jobs.</span></span> <span data-ttu-id="2e572-122">不過，系統不會自動移除異動資料擷取所建立的任何控制角色，而且您必須明確刪除這些角色。</span><span class="sxs-lookup"><span data-stu-id="2e572-122">However, any gating roles created by change data capture will not be removed automatically and must be explicitly deleted.</span></span> <span data-ttu-id="2e572-123">若要判斷資料庫是否已啟用，請查詢 sys.databases 目錄檢視中的 `is_cdc_enabled` 資料行。</span><span class="sxs-lookup"><span data-stu-id="2e572-123">To determine if a database is enabled, query the `is_cdc_enabled` column in the sys.databases catalog view.</span></span>  
  
 <span data-ttu-id="2e572-124">如果啟用異動資料擷取的資料庫已卸除，系統就會自動移除異動資料擷取作業。</span><span class="sxs-lookup"><span data-stu-id="2e572-124">If a change data capture enabled database is dropped, change data capture jobs are automatically removed.</span></span>  
  
 <span data-ttu-id="2e572-125">如需停用資料庫的範例，請參閱「停用異動資料擷取的資料庫」範本。</span><span class="sxs-lookup"><span data-stu-id="2e572-125">See the Disable Database for Change Data Capture template for an example of disabling a database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2e572-126">若要在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中找出範本，請移至 **[檢視]** 、按一下 **[範本總管]** ，然後按一下 **[SQL Server 範本]** 。</span><span class="sxs-lookup"><span data-stu-id="2e572-126">To locate the templates in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], go to **View**, click **Template Explorer**, and then click **SQL Server Templates**.</span></span> <span data-ttu-id="2e572-127">**[異動資料擷取]** 是子資料夾，而且您將會在其中找到這個主題所參考的所有範本。</span><span class="sxs-lookup"><span data-stu-id="2e572-127">**Change Data Capture** is a sub-folder where you will find all the templates that are referenced in this topic.</span></span> <span data-ttu-id="2e572-128">**工具列上也有一個** [範本總管] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 圖示。</span><span class="sxs-lookup"><span data-stu-id="2e572-128">There is also a **Template Explorer** icon on the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] toolbar.</span></span>  
  
```sql  
-- =======  
-- Disable Database for Change Data Capture template   
-- =======  
USE MyDB  
GO  
EXEC sys.sp_cdc_disable_db  
GO  
```  
  
## <a name="enable-change-data-capture-for-a-table"></a><span data-ttu-id="2e572-129">針對資料表啟用異動資料擷取</span><span class="sxs-lookup"><span data-stu-id="2e572-129">Enable Change Data Capture for a Table</span></span>  
 <span data-ttu-id="2e572-130">啟用異動資料擷取的資料庫之後，`db_owner` 固定資料庫角色的成員就可以使用 `sys.sp_cdc_enable_table` 預存程序，針對個別的來源資料表建立擷取執行個體。</span><span class="sxs-lookup"><span data-stu-id="2e572-130">After a database has been enabled for change data capture, members of the `db_owner` fixed database role can create a capture instance for individual source tables by using the stored procedure `sys.sp_cdc_enable_table`.</span></span> <span data-ttu-id="2e572-131">若要判斷是否已經啟用異動資料擷取的來源資料表，請檢查 `sys.tables` 目錄檢視中的 is_tracked_by_cdc 資料行。</span><span class="sxs-lookup"><span data-stu-id="2e572-131">To determine whether a source table has already been enabled for change data capture, examine the is_tracked_by_cdc column in the `sys.tables` catalog view.</span></span>  
  
 <span data-ttu-id="2e572-132">您可以在建立擷取執行個體時指定下列選項：</span><span class="sxs-lookup"><span data-stu-id="2e572-132">The following options can be specified when creating a capture instance:</span></span>  
  
 <span data-ttu-id="2e572-133">`Columns in the source table to be captured`.</span><span class="sxs-lookup"><span data-stu-id="2e572-133">`Columns in the source table to be captured`.</span></span>  
  
 <span data-ttu-id="2e572-134">根據預設，系統會將來源資料表中的所有資料行識別為擷取資料行。</span><span class="sxs-lookup"><span data-stu-id="2e572-134">By default, all of the columns in the source table are identified as captured columns.</span></span> <span data-ttu-id="2e572-135">如果只需要追蹤資料行的子集（例如基於隱私權或效能的原因），請使用 *@captured_column_list* 參數來指定資料行的子集。</span><span class="sxs-lookup"><span data-stu-id="2e572-135">If only a subset of columns need to be tracked, such as for privacy or performance reasons, use the *@captured_column_list* parameter to specify the subset of columns.</span></span>  
  
 `A filegroup to contain the change table.`  
  
 <span data-ttu-id="2e572-136">根據預設，變更資料表位於資料庫的預設檔案群組中。</span><span class="sxs-lookup"><span data-stu-id="2e572-136">By default, the change table is located in the default filegroup of the database.</span></span> <span data-ttu-id="2e572-137">想要控制個別變更資料表位置的資料庫擁有者可以使用 *@filegroup_name* 參數來指定與 capture 實例相關聯之變更資料表的特定檔案群組。</span><span class="sxs-lookup"><span data-stu-id="2e572-137">Database owners who want to control the placement of individual change tables can use the *@filegroup_name* parameter to specify a particular filegroup for the change table associated with the capture instance.</span></span> <span data-ttu-id="2e572-138">此指定的檔案群組必須已存在。</span><span class="sxs-lookup"><span data-stu-id="2e572-138">The named filegroup must already exist.</span></span> <span data-ttu-id="2e572-139">一般而言，我們建議您將變更資料表放在與來源資料表不同的檔案群組中。</span><span class="sxs-lookup"><span data-stu-id="2e572-139">Generally, it is recommended that change tables be placed in a filegroup separate from source tables.</span></span> <span data-ttu-id="2e572-140">如需示範如何使用參數的範例，請參閱 `Enable a Table Specifying Filegroup Option` 範本 *@filegroup_name* 。</span><span class="sxs-lookup"><span data-stu-id="2e572-140">See the `Enable a Table Specifying Filegroup Option` template for an example showing use of the *@filegroup_name* parameter.</span></span>  
  
```sql  
-- =========  
-- Enable a Table Specifying Filegroup Option Template  
-- =========  
USE MyDB  
GO  
  
EXEC sys.sp_cdc_enable_table  
@source_schema = N'dbo',  
@source_name   = N'MyTable',  
@role_name     = N'MyRole',  
@filegroup_name = N'MyDB_CT',  
@supports_net_changes = 1  
GO  
```  
  
 `A role for controlling access to a change table.`  
  
 <span data-ttu-id="2e572-141">指定角色的目的是要控制變更資料的存取權。</span><span class="sxs-lookup"><span data-stu-id="2e572-141">The purpose of the named role is to control access to the change data.</span></span> <span data-ttu-id="2e572-142">指定的角色可以是現有的固定伺服器角色或資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="2e572-142">The specified role can be an existing fixed server role or a database role.</span></span> <span data-ttu-id="2e572-143">如果指定的角色不存在，則會自動建立該名稱的資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="2e572-143">If the specified role does not already exist, a database role of that name is created automatically.</span></span> <span data-ttu-id="2e572-144">`sysadmin` 或 `db_owner` 角色的成員對於變更資料表中的資料擁有完整存取權。</span><span class="sxs-lookup"><span data-stu-id="2e572-144">Members of either the `sysadmin` or `db_owner` role have full access to the data in the change tables.</span></span> <span data-ttu-id="2e572-145">其他所有使用者對於來源資料表的所有擷取資料行必須具備 SELECT 權限。</span><span class="sxs-lookup"><span data-stu-id="2e572-145">All other users must have SELECT permission on all the captured columns of the source table.</span></span> <span data-ttu-id="2e572-146">此外，指定角色時，不是 `sysadmin` 或 `db_owner` 角色之成員的使用者也必須是指定之角色的成員。</span><span class="sxs-lookup"><span data-stu-id="2e572-146">In addition, when a role is specified, users who are not members of either the `sysadmin` or `db_owner` role must also be members of the specified role.</span></span>  
  
 <span data-ttu-id="2e572-147">如果您不想要使用控制角色，請將參數明確設定 *@role_name* 為 Null。</span><span class="sxs-lookup"><span data-stu-id="2e572-147">If you do not want to use a gating role, explicitly set the *@role_name* parameter to NULL.</span></span> <span data-ttu-id="2e572-148">如需在不使用控制角色的情況下啟用資料表的範例，請參閱「`Enable a Table Without Using a Gating Role`」範本。</span><span class="sxs-lookup"><span data-stu-id="2e572-148">See the `Enable a Table Without Using a Gating Role` template for an example of enabling a table without a gating role.</span></span>  
  
```sql  
-- =========  
-- Enable a Table Without Using a Gating Role template   
-- =========  
USE MyDB  
GO  
EXEC sys.sp_cdc_enable_table  
@source_schema = N'dbo',  
@source_name   = N'MyTable',  
@role_name     = NULL,  
@supports_net_changes = 1  
GO  
  
```  
  
 `A function to query for net changes.`  
  
 <span data-ttu-id="2e572-149">擷取執行個體一定會包含資料表值函式，以便傳回在定義間隔內發生的所有變更資料表項目。</span><span class="sxs-lookup"><span data-stu-id="2e572-149">A capture instance will always include a table valued function for returning all change table entries that occurred within a defined interval.</span></span> <span data-ttu-id="2e572-150">這個函數的命名方式是將擷取執行個體名稱附加至 "cdc.fn_cdc_get_all_changes_"。</span><span class="sxs-lookup"><span data-stu-id="2e572-150">This function is named by appending the capture instance name to "cdc.fn_cdc_get_all_changes_".</span></span> <span data-ttu-id="2e572-151">如需詳細資訊，請參閱 [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2e572-151">For more information, see [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql).</span></span>  
  
 <span data-ttu-id="2e572-152">如果參數 *@supports_net_changes* 設為1，則也會針對 capture 實例產生淨變更函數。</span><span class="sxs-lookup"><span data-stu-id="2e572-152">If the parameter *@supports_net_changes* is set to 1, a net changes function is also generated for the capture instance.</span></span> <span data-ttu-id="2e572-153">此函數僅會針對在呼叫中指定之間隔內變更的每個不同資料列，傳回一個變更。</span><span class="sxs-lookup"><span data-stu-id="2e572-153">This function returns only one change for each distinct row changed in the interval specified in the call.</span></span> <span data-ttu-id="2e572-154">如需詳細資訊，請參閱 [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2e572-154">For more information, see [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql).</span></span>  
  
 <span data-ttu-id="2e572-155">若要支援淨變更查詢，來源資料表必須具有主索引鍵或唯一的索引才能唯一識別資料列。</span><span class="sxs-lookup"><span data-stu-id="2e572-155">To support net changes queries, the source table must have a primary key or unique index to uniquely identify rows.</span></span> <span data-ttu-id="2e572-156">如果使用唯一索引，則必須使用參數來指定索引的名稱 *@index_name* 。</span><span class="sxs-lookup"><span data-stu-id="2e572-156">If a unique index is used, the name of the index must be specified using the *@index_name* parameter.</span></span> <span data-ttu-id="2e572-157">在主索引鍵或唯一索引中定義的資料行必須包含在要擷取之來源資料行的清單中。</span><span class="sxs-lookup"><span data-stu-id="2e572-157">The columns defined in the primary key or unique index must be included in the list of source columns to be captured.</span></span>  
  
 <span data-ttu-id="2e572-158">如需示範建立含有兩個查詢函數之擷取執行個體的範例，請參閱「`Enable a Table for All and Net Changes Queries`」範本。</span><span class="sxs-lookup"><span data-stu-id="2e572-158">See the `Enable a Table for All and Net Changes Queries` template for an example demonstrating the creation of a capture instance with both query functions.</span></span>  
  
```sql  
-- =============  
-- Enable a Table for All and Net Changes Queries template   
-- =============  
USE MyDB  
GO  
EXEC sys.sp_cdc_enable_table  
@source_schema = N'dbo',  
@source_name   = N'MyTable',  
@role_name     = N'MyRole',  
@supports_net_changes = 1  
GO  
```  
  
> [!NOTE]
>  <span data-ttu-id="2e572-159">如果已在具有現有主鍵的資料表上啟用變更資料捕獲，而參數未 *@index_name* 用來識別替代的唯一索引，則變更資料捕獲功能將會使用主鍵。</span><span class="sxs-lookup"><span data-stu-id="2e572-159">If change data capture is enabled on a table with an existing primary key, and the *@index_name* parameter is not used to identify an alternative unique index, the change data capture feature will use the primary key.</span></span> <span data-ttu-id="2e572-160">如果沒有先針對資料表停用異動資料擷取，系統就不允許對主索引鍵進行後續變更。</span><span class="sxs-lookup"><span data-stu-id="2e572-160">Subsequent changes to the primary key will not be allowed without first disabling change data capture for the table.</span></span> <span data-ttu-id="2e572-161">不論設定異動資料擷取時是否要求淨變更查詢的支援，都是如此。</span><span class="sxs-lookup"><span data-stu-id="2e572-161">This is true regardless of whether support for net changes queries was requested when change data capture was configured.</span></span> <span data-ttu-id="2e572-162">如果啟用異動資料擷取時，資料表沒有任何主索引鍵，則異動資料擷取就會忽略後續加入主索引鍵的作業。</span><span class="sxs-lookup"><span data-stu-id="2e572-162">If there is no primary key on a table at the time it is enabled for change data capture, the subsequent addition of a primary key is ignored by change data capture.</span></span> <span data-ttu-id="2e572-163">由於異動資料擷取不會使用啟用資料表之後所建立的主索引鍵，因此您可以移除此索引鍵和索引鍵資料行，而且沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="2e572-163">Because change data capture will not use a primary key that is created after the table was enabled, the key and key columns can be removed without restrictions.</span></span>  
  
## <a name="disable-change-data-capture-for-a-table"></a><span data-ttu-id="2e572-164">針對資料表停用異動資料擷取</span><span class="sxs-lookup"><span data-stu-id="2e572-164">Disable Change Data Capture for a Table</span></span>  
 <span data-ttu-id="2e572-165">`db_owner` 固定資料庫角色的成員可以使用 `sys.sp_cdc_disable_table` 預存程序，針對個別的來源資料表移除擷取執行個體。</span><span class="sxs-lookup"><span data-stu-id="2e572-165">Members of the `db_owner` fixed database role can remove a capture instance for individual source tables by using the stored procedure `sys.sp_cdc_disable_table`.</span></span> <span data-ttu-id="2e572-166">若要判斷目前是否已啟用異動資料擷取的來源資料表，請檢查 `is_tracked_by_cdc` 目錄檢視中的 `sys.tables` 資料行。</span><span class="sxs-lookup"><span data-stu-id="2e572-166">To determine whether a source table is currently enabled for change data capture, examine the `is_tracked_by_cdc` column in the `sys.tables` catalog view.</span></span> <span data-ttu-id="2e572-167">如果進行停用之後，資料庫中沒有任何資料表啟用，系統也會移除異動資料擷取作業。</span><span class="sxs-lookup"><span data-stu-id="2e572-167">If there are no tables enabled for the database after the disabling takes place, the change data capture jobs are also removed.</span></span>  
  
 <span data-ttu-id="2e572-168">如果啟用異動資料擷取的資料表已卸除，系統就會自動移除與此資料表相關聯的異動資料擷取中繼資料。</span><span class="sxs-lookup"><span data-stu-id="2e572-168">If a change data capture-enabled table is dropped, change data capture metadata that is associated with the table is automatically removed.</span></span>  
  
 <span data-ttu-id="2e572-169">如需停用資料表的範例，請參閱「停用資料表的擷取執行個體」範本。</span><span class="sxs-lookup"><span data-stu-id="2e572-169">See the Disable a Capture Instance for a Table template for an example of disabling a table.</span></span>  
  
```sql  
-- =====  
-- Disable a Capture Instance for a Table template   
-- =====  
USE MyDB  
GO  
EXEC sys.sp_cdc_disable_table  
@source_schema = N'dbo',  
@source_name   = N'MyTable',  
@capture_instance = N'dbo_MyTable'  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e572-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e572-170">See Also</span></span>  
 <span data-ttu-id="2e572-171">[追蹤資料變更 &#40;SQL Server&#41;](track-data-changes-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2e572-171">[Track Data Changes &#40;SQL Server&#41;](track-data-changes-sql-server.md) </span></span>  
 <span data-ttu-id="2e572-172">[關於異動資料擷取 &#40;SQL Server&#41;](../track-changes/about-change-data-capture-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2e572-172">[About Change Data Capture &#40;SQL Server&#41;](../track-changes/about-change-data-capture-sql-server.md) </span></span>  
 <span data-ttu-id="2e572-173">[使用變更資料 &#40;SQL Server&#41;](work-with-change-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2e572-173">[Work with Change Data &#40;SQL Server&#41;](work-with-change-data-sql-server.md) </span></span>  
 [<span data-ttu-id="2e572-174">管理和監視異動資料擷取 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="2e572-174">Administer and Monitor Change Data Capture &#40;SQL Server&#41;</span></span>](../track-changes/administer-and-monitor-change-data-capture-sql-server.md)  
  
  
