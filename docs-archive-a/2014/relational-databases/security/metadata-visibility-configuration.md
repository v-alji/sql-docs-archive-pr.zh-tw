---
title: 中繼資料可見性組態 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- subcomponents visibility [SQL Server]
- metadata [SQL Server], visibility
- permissions [SQL Server], metadata access
- viewing metadata
- objects [SQL Server], metadata
- displaying metadata
- database metadata [SQL Server]
- metadata [SQL Server], permissions
ms.assetid: 50d2e015-05ae-4014-a1cd-4de7866ad651
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 5198dc4ba4e81bc1d7a8dd2411da59da81596102
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596609"
---
# <a name="metadata-visibility-configuration"></a><span data-ttu-id="e3c36-102">中繼資料可見性組態</span><span class="sxs-lookup"><span data-stu-id="e3c36-102">Metadata Visibility Configuration</span></span>
  <span data-ttu-id="e3c36-103">中繼資料的可見性會限制在使用者所擁有的安全性實體，或已授與使用者某些權限的安全性實體。</span><span class="sxs-lookup"><span data-stu-id="e3c36-103">The visibility of metadata is limited to securables that a user either owns or on which the user has been granted some permission.</span></span> <span data-ttu-id="e3c36-104">例如，如果授與使用者資料表 `myTable`的 SELECT 或 INSERT 權限，則下列查詢會傳回一個資料列。</span><span class="sxs-lookup"><span data-stu-id="e3c36-104">For example, the following query returns a row if the user has been granted a permission such as SELECT or INSERT on the table `myTable`.</span></span>  
  
```  
SELECT name, object_id  
FROM sys.tables  
WHERE name = 'myTable';  
GO  
```  
  
 <span data-ttu-id="e3c36-105">但是，如果使用者對 `myTable`沒有任何權限，則查詢會傳回空的結果集。</span><span class="sxs-lookup"><span data-stu-id="e3c36-105">However, if the user does not have any permission on `myTable`, the query returns an empty result set.</span></span>  
  
## <a name="scope-and-impact-of-metadata-visibility-configuration"></a><span data-ttu-id="e3c36-106">中繼資料可見性組態的範圍和影響</span><span class="sxs-lookup"><span data-stu-id="e3c36-106">Scope and Impact of Metadata Visibility Configuration</span></span>  
 <span data-ttu-id="e3c36-107">中繼資料可見性組態僅適用於下列安全性實體。</span><span class="sxs-lookup"><span data-stu-id="e3c36-107">Metadata visibility configuration only applies to the following securables.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e3c36-108">目錄檢視</span><span class="sxs-lookup"><span data-stu-id="e3c36-108">Catalog views</span></span>|[!INCLUDE[ssDE](../../includes/ssde-md.md)] <span data-ttu-id="e3c36-109">**sp_help** 預存程序</span><span class="sxs-lookup"><span data-stu-id="e3c36-109">**sp_help** stored procedures</span></span>|  
|<span data-ttu-id="e3c36-110">公開內建函數的中繼資料</span><span class="sxs-lookup"><span data-stu-id="e3c36-110">Metadata exposing built-in functions</span></span>|<span data-ttu-id="e3c36-111">資訊結構描述檢視</span><span class="sxs-lookup"><span data-stu-id="e3c36-111">Information schema views</span></span>|  
|<span data-ttu-id="e3c36-112">相容性檢視</span><span class="sxs-lookup"><span data-stu-id="e3c36-112">Compatibility views</span></span>|<span data-ttu-id="e3c36-113">擴充屬性</span><span class="sxs-lookup"><span data-stu-id="e3c36-113">Extended properties</span></span>|  
  
 <span data-ttu-id="e3c36-114">中繼資料可見性組態不適用於下列安全性實體。</span><span class="sxs-lookup"><span data-stu-id="e3c36-114">Metadata visibility configuration does not apply to the following securables.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e3c36-115">「記錄傳送」系統資料表</span><span class="sxs-lookup"><span data-stu-id="e3c36-115">Log shipping system tables</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e3c36-116">Agent 系統資料表</span><span class="sxs-lookup"><span data-stu-id="e3c36-116">Agent system tables</span></span>|  
|<span data-ttu-id="e3c36-117">資料庫維護計畫系統資料表</span><span class="sxs-lookup"><span data-stu-id="e3c36-117">Database maintenance plan system tables</span></span>|<span data-ttu-id="e3c36-118">「備份」系統資料表</span><span class="sxs-lookup"><span data-stu-id="e3c36-118">Backup system tables</span></span>|  
|<span data-ttu-id="e3c36-119">「複寫」系統資料表</span><span class="sxs-lookup"><span data-stu-id="e3c36-119">Replication system tables</span></span>|<span data-ttu-id="e3c36-120">複寫和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent **sp_help** 預存程序</span><span class="sxs-lookup"><span data-stu-id="e3c36-120">Replication and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent **sp_help** stored procedures</span></span>|  
  
 <span data-ttu-id="e3c36-121">中繼資料存取範圍有限制的意義如下：</span><span class="sxs-lookup"><span data-stu-id="e3c36-121">Limited metadata accessibility means the following:</span></span>  
  
-   <span data-ttu-id="e3c36-122">假設以 **public** 來存取中繼資料的應用程式會中斷。</span><span class="sxs-lookup"><span data-stu-id="e3c36-122">Applications that assume **public** metadata access will break.</span></span>  
  
-   <span data-ttu-id="e3c36-123">對系統檢視查詢可能只會傳回資料列的子集，或有時候傳回空的結果集。</span><span class="sxs-lookup"><span data-stu-id="e3c36-123">Queries on system views might only return a subset of rows, or sometimes an empty result set.</span></span>  
  
-   <span data-ttu-id="e3c36-124">發出中繼資料的內建函數 (例如 OBJECTPROPERTYEX) 可能傳回 NULL。</span><span class="sxs-lookup"><span data-stu-id="e3c36-124">Metadata-emitting, built-in functions such as OBJECTPROPERTYEX may return NULL.</span></span>  
  
-   <span data-ttu-id="e3c36-125">[!INCLUDE[ssDE](../../includes/ssde-md.md)] **sp_help** 預存程序可能只會傳回資料列的子集，或傳回 NULL。</span><span class="sxs-lookup"><span data-stu-id="e3c36-125">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] **sp_help** stored procedures might return only a subset of rows, or NULL.</span></span>  
  
 <span data-ttu-id="e3c36-126">SQL 模組 (例如預存程序和觸發程序) 會在呼叫者的安全性內容下執行，因此在中繼資料的存取上受到限制。</span><span class="sxs-lookup"><span data-stu-id="e3c36-126">SQL modules, such as stored procedures and triggers, run under the security context of the caller and, therefore, have limited metadata accessibility.</span></span> <span data-ttu-id="e3c36-127">例如，在下列的程式碼中，當預存程序嘗試存取資料表 `myTable` 的中繼資料而呼叫者對此資料表沒有任何權限時，將會傳回空的結果集。</span><span class="sxs-lookup"><span data-stu-id="e3c36-127">For example, in the following code, when the stored procedure tries to access metadata for the table `myTable` on which the caller has no rights, an empty result set is returned.</span></span> <span data-ttu-id="e3c36-128">若在舊版的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，則會傳回一個資料列。</span><span class="sxs-lookup"><span data-stu-id="e3c36-128">In earlier releases of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a row is returned.</span></span>  
  
```  
CREATE PROCEDURE assumes_caller_can_access_metadata  
BEGIN  
SELECT name, id   
FROM sysobjects   
WHERE name = 'myTable';  
END;  
GO  
```  
  
 <span data-ttu-id="e3c36-129">若要讓呼叫者能夠檢視中繼資料，您可以在適當範圍 (例如，物件層級、資料庫層級或伺服器層級) 授與呼叫者 VIEW DEFINITION 權限。</span><span class="sxs-lookup"><span data-stu-id="e3c36-129">To allow callers to view metadata, you can grant the callers VIEW DEFINITION permission at an appropriate scope: object level, database level or server level.</span></span> <span data-ttu-id="e3c36-130">因此，在上個範例中，如果呼叫者具有 `myTable`的 VIEW DEFINITION 權限，預存程序就會傳回一個資料列。</span><span class="sxs-lookup"><span data-stu-id="e3c36-130">Therefore, in the previous example, if the caller has VIEW DEFINITION permission on `myTable`, the stored procedure returns a row.</span></span> <span data-ttu-id="e3c36-131">如需詳細資訊，請參閱 [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) 和[授與資料庫權限 &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e3c36-131">For more information, see [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) and [GRANT Database Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql).</span></span>  
  
 <span data-ttu-id="e3c36-132">您也可以修改預存程序，使其在擁有者的認證下執行。</span><span class="sxs-lookup"><span data-stu-id="e3c36-132">You can also modify the stored procedure so that it executes under the credentials of the owner.</span></span> <span data-ttu-id="e3c36-133">若程序擁有者和資料表擁有者是相同的擁有者，就會套用擁有權鏈結，且程序擁有者的安全性內容就可以存取 `myTable`的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="e3c36-133">When the procedure owner and the table owner are the same owner, ownership chaining applies, and the security context of the procedure owner enables access to the metadata for `myTable`.</span></span> <span data-ttu-id="e3c36-134">在這種狀況下，下列程式碼會將中繼資料的資料列傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="e3c36-134">Under this scenario, the following code returns a row of metadata to the caller.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e3c36-135">下列範例使用 [sys.objects](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql) 目錄檢視，而非 [sys.sysobjects](/sql/relational-databases/system-compatibility-views/sys-sysobjects-transact-sql) 相容性檢視。</span><span class="sxs-lookup"><span data-stu-id="e3c36-135">The following example uses the [sys.objects](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql) catalog view instead of the [sys.sysobjects](/sql/relational-databases/system-compatibility-views/sys-sysobjects-transact-sql) compatibility view.</span></span>  
  
```  
CREATE PROCEDURE does_not_assume_caller_can_access_metadata  
WITH EXECUTE AS OWNER  
AS  
BEGIN  
SELECT name, id  
FROM sys.objects   
WHERE name = 'myTable'   
END;  
GO  
```  
  
> [!NOTE]  
>  <span data-ttu-id="e3c36-136">您可以使用 EXECUTE AS，暫時切換到呼叫者的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="e3c36-136">You can use EXECUTE AS to temporarily switch to the security context of the caller.</span></span> <span data-ttu-id="e3c36-137">如需詳細資訊，請參閱 [EXECUTE AS &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e3c36-137">For more information, see [EXECUTE AS &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-transact-sql).</span></span>  
  
## <a name="benefits-and-limits-of-metadata-visibility-configuration"></a><span data-ttu-id="e3c36-138">中繼資料可見性組態的優點和限制</span><span class="sxs-lookup"><span data-stu-id="e3c36-138">Benefits and Limits of Metadata Visibility Configuration</span></span>  
 <span data-ttu-id="e3c36-139">中繼資料可見性組態在整體安全性計畫中扮演著重要的角色。</span><span class="sxs-lookup"><span data-stu-id="e3c36-139">Metadata visibility configuration can play an important role in your overall security plan.</span></span> <span data-ttu-id="e3c36-140">但在某些情況中，技術純熟又執意操作的使用者還是能夠強制洩漏某些中繼資料。</span><span class="sxs-lookup"><span data-stu-id="e3c36-140">However, there are cases in which a skilled and determined user can force the disclosure of some metadata.</span></span> <span data-ttu-id="e3c36-141">我們建議您將中繼資料權限部署為全面防禦中的一環。</span><span class="sxs-lookup"><span data-stu-id="e3c36-141">We recommend that you deploy metadata permissions as one of many defenses-in-depth.</span></span>  
  
 <span data-ttu-id="e3c36-142">強制發出錯誤訊息中的中繼資料，理論上是可行的，做法是在查詢中操縱述詞評估的順序。</span><span class="sxs-lookup"><span data-stu-id="e3c36-142">It is theoretically possible to force the emission of metadata in error messages by manipulating the order of predicate evaluation in queries.</span></span> <span data-ttu-id="e3c36-143">這種「嘗試與錯誤攻擊」的可能性不是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所特有。</span><span class="sxs-lookup"><span data-stu-id="e3c36-143">The possibility of such *trial-and-error attacks* is not specific to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e3c36-144">它由關聯式代數所允許的關聯式和交換式轉換所暗示。</span><span class="sxs-lookup"><span data-stu-id="e3c36-144">It is implied by the associative and commutative transformations permitted in relational algebra.</span></span> <span data-ttu-id="e3c36-145">您可以限制錯誤訊息所傳回的資訊來減輕此風險。</span><span class="sxs-lookup"><span data-stu-id="e3c36-145">You can mitigate this risk by limiting the information returned in error messages.</span></span> <span data-ttu-id="e3c36-146">若要以此方式進一步限制中繼資料的可見性，您可以用追蹤旗標 3625 來啟動伺服器。</span><span class="sxs-lookup"><span data-stu-id="e3c36-146">To further restrict the visibility of metadata in this way, you can start the server with trace flag 3625.</span></span> <span data-ttu-id="e3c36-147">此追蹤旗標限制錯誤訊息所顯示的資訊量。</span><span class="sxs-lookup"><span data-stu-id="e3c36-147">This trace flag limits the amount of information shown in error messages.</span></span> <span data-ttu-id="e3c36-148">而這有助於防止強制洩漏。</span><span class="sxs-lookup"><span data-stu-id="e3c36-148">In turn, this helps to prevent forced disclosures.</span></span> <span data-ttu-id="e3c36-149">代價是錯誤訊息會簡單一些，用於偵錯時可能會比較困難。</span><span class="sxs-lookup"><span data-stu-id="e3c36-149">The tradeoff is that error messages will be terse and might be difficult to use for debugging purposes.</span></span> <span data-ttu-id="e3c36-150">如需詳細資訊，請參閱 [Database Engine 服務啟動選項](../../database-engine/configure-windows/database-engine-service-startup-options.md)和[追蹤旗標 &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e3c36-150">For more information, see [Database Engine Service Startup Options](../../database-engine/configure-windows/database-engine-service-startup-options.md) and [Trace Flags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).</span></span>  
  
 <span data-ttu-id="e3c36-151">下列的中繼資料不會被強制洩漏：</span><span class="sxs-lookup"><span data-stu-id="e3c36-151">The following metadata is not subject to forced disclosure:</span></span>  
  
-   <span data-ttu-id="e3c36-152">**sys.servers** 的 **provider_string**資料行中儲存的值。</span><span class="sxs-lookup"><span data-stu-id="e3c36-152">The value stored in the **provider_string** column of **sys.servers**.</span></span> <span data-ttu-id="e3c36-153">沒有 ALTER ANY LINKED SERVER 權限的使用者在資料行中只會看見 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="e3c36-153">A user that does not have ALTER ANY LINKED SERVER permission will see a NULL value in this column.</span></span>  
  
-   <span data-ttu-id="e3c36-154">使用者自訂物件 (例如預存程序或觸發程序) 的來源定義。</span><span class="sxs-lookup"><span data-stu-id="e3c36-154">Source definition of a user-defined object such as a stored procedure or trigger.</span></span> <span data-ttu-id="e3c36-155">只有下列任一狀況屬實時，才能看見原始程式碼：</span><span class="sxs-lookup"><span data-stu-id="e3c36-155">The source code is visible only when one of the following is true:</span></span>  
  
    -   <span data-ttu-id="e3c36-156">使用者具有物件的 VIEW DEFINITION 權限。</span><span class="sxs-lookup"><span data-stu-id="e3c36-156">The user has VIEW DEFINITION permission on the object.</span></span>  
  
    -   <span data-ttu-id="e3c36-157">使用者對該物件的 VIEW DEFINITION 權限尚未被拒絕，且使用者具有該物件的 CONTROL、ALTER 或 TAKE OWNERSHIP 權限。</span><span class="sxs-lookup"><span data-stu-id="e3c36-157">The user has not been denied VIEW DEFINITION permission on the object and has CONTROL, ALTER, or TAKE OWNERSHIP permission on the object.</span></span> <span data-ttu-id="e3c36-158">其他所有使用者都只會看到 NULL。</span><span class="sxs-lookup"><span data-stu-id="e3c36-158">All other users will see NULL.</span></span>  
  
-   <span data-ttu-id="e3c36-159">下列目錄檢視中的定義資料行：</span><span class="sxs-lookup"><span data-stu-id="e3c36-159">The definition columns found in the following catalog views:</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="e3c36-160">**sys.all_sql_modules**</span><span class="sxs-lookup"><span data-stu-id="e3c36-160">**sys.all_sql_modules**</span></span>|<span data-ttu-id="e3c36-161">**sys.sql_modules**</span><span class="sxs-lookup"><span data-stu-id="e3c36-161">**sys.sql_modules**</span></span>|  
    |<span data-ttu-id="e3c36-162">**sys.server_sql_modules**</span><span class="sxs-lookup"><span data-stu-id="e3c36-162">**sys.server_sql_modules**</span></span>|<span data-ttu-id="e3c36-163">**sys.check_constraints**</span><span class="sxs-lookup"><span data-stu-id="e3c36-163">**sys.check_constraints**</span></span>|  
    |<span data-ttu-id="e3c36-164">**sys.default_constraints**</span><span class="sxs-lookup"><span data-stu-id="e3c36-164">**sys.default_constraints**</span></span>|<span data-ttu-id="e3c36-165">**sys.computed_columns**</span><span class="sxs-lookup"><span data-stu-id="e3c36-165">**sys.computed_columns**</span></span>|  
    |<span data-ttu-id="e3c36-166">**sys.numbered_procedures**</span><span class="sxs-lookup"><span data-stu-id="e3c36-166">**sys.numbered_procedures**</span></span>||  
  
-   <span data-ttu-id="e3c36-167">**syscomments** 相容性檢視中的 **ctext** 資料行。</span><span class="sxs-lookup"><span data-stu-id="e3c36-167">The **ctext** column in the **syscomments** compatibility view.</span></span>  
  
-   <span data-ttu-id="e3c36-168">**sp_helptext** 程序的輸出。</span><span class="sxs-lookup"><span data-stu-id="e3c36-168">The output of the **sp_helptext** procedure.</span></span>  
  
-   <span data-ttu-id="e3c36-169">資訊結構描述檢視中的下列資料行：</span><span class="sxs-lookup"><span data-stu-id="e3c36-169">The following columns in the information schema views:</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="e3c36-170">INFORMATION_SCHEMA.CHECK_CONSTRAINTS.CHECK_CLAUSE</span><span class="sxs-lookup"><span data-stu-id="e3c36-170">INFORMATION_SCHEMA.CHECK_CONSTRAINTS.CHECK_CLAUSE</span></span>|<span data-ttu-id="e3c36-171">INFORMATION_SCHEMA.COLUMNS.COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="e3c36-171">INFORMATION_SCHEMA.COLUMNS.COLUMN_DEFAULT</span></span>|  
    |<span data-ttu-id="e3c36-172">INFORMATION_SCHEMA.DOMAINS.DOMAIN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="e3c36-172">INFORMATION_SCHEMA.DOMAINS.DOMAIN_DEFAULT</span></span>|<span data-ttu-id="e3c36-173">INFORMATION_SCHEMA.ROUTINE_COLUMNS.COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="e3c36-173">INFORMATION_SCHEMA.ROUTINE_COLUMNS.COLUMN_DEFAULT</span></span>|  
    |<span data-ttu-id="e3c36-174">INFORMATION_SCHEMA.ROUTINES.ROUTINE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="e3c36-174">INFORMATION_SCHEMA.ROUTINES.ROUTINE_DEFINITION</span></span>|<span data-ttu-id="e3c36-175">INFORMATION_SCHEMA.VIEWS.VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="e3c36-175">INFORMATION_SCHEMA.VIEWS.VIEW_DEFINITION</span></span>|  
  
-   <span data-ttu-id="e3c36-176">OBJECT_DEFINITION() 函數</span><span class="sxs-lookup"><span data-stu-id="e3c36-176">OBJECT_DEFINITION() function</span></span>  
  
-   <span data-ttu-id="e3c36-177">**sys.sql_logins**的 password_hash 資料行中儲存的值。</span><span class="sxs-lookup"><span data-stu-id="e3c36-177">The value stored in the password_hash column of **sys.sql_logins**.</span></span>  <span data-ttu-id="e3c36-178">沒有 CONTROL SERVER 權限的使用者將在此資料行中看到 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="e3c36-178">A user that does not have CONTROL SERVER permission will see a NULL value in this column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e3c36-179">內建系統程序和函數的 SQL 定義，可經由 **sys.system_sql_modules** 目錄檢視、 **sp_helptext** 預存程序和 OBJECT_DEFINITION() 函數公開檢視。</span><span class="sxs-lookup"><span data-stu-id="e3c36-179">The SQL definitions of built-in system procedures and functions are publicly visible through the **sys.system_sql_modules** catalog view, the **sp_helptext** stored procedure, and the OBJECT_DEFINITION() function.</span></span>  
  
## <a name="general-principles-of-metadata-visibility"></a><span data-ttu-id="e3c36-180">中繼資料可見性的一般原則</span><span class="sxs-lookup"><span data-stu-id="e3c36-180">General Principles of Metadata Visibility</span></span>  
 <span data-ttu-id="e3c36-181">下列是幾個關於中繼資料可見性的一般考量原則：</span><span class="sxs-lookup"><span data-stu-id="e3c36-181">The following are some general principles to consider regarding metadata visibility:</span></span>  
  
-   <span data-ttu-id="e3c36-182">固定角色的隱含權限</span><span class="sxs-lookup"><span data-stu-id="e3c36-182">Fixed roles implicit permissions</span></span>  
  
-   <span data-ttu-id="e3c36-183">權限範圍</span><span class="sxs-lookup"><span data-stu-id="e3c36-183">Scope of permissions</span></span>  
  
-   <span data-ttu-id="e3c36-184">DENY 的優先順序</span><span class="sxs-lookup"><span data-stu-id="e3c36-184">Precedence of DENY</span></span>  
  
-   <span data-ttu-id="e3c36-185">子元件中繼資料的可見性</span><span class="sxs-lookup"><span data-stu-id="e3c36-185">Visibility of subcomponent metadata</span></span>  
  
### <a name="fixed-roles-and-implicit-permissions"></a><span data-ttu-id="e3c36-186">固定角色和隱含權限</span><span class="sxs-lookup"><span data-stu-id="e3c36-186">Fixed Roles and Implicit Permissions</span></span>  
 <span data-ttu-id="e3c36-187">固定角色可以存取的中繼資料取決於其對應的隱含權限。</span><span class="sxs-lookup"><span data-stu-id="e3c36-187">Metadata that can be accessed by fixed roles depends upon their corresponding implicit permissions.</span></span>  
  
### <a name="scope-of-permissions"></a><span data-ttu-id="e3c36-188">權限範圍</span><span class="sxs-lookup"><span data-stu-id="e3c36-188">Scope of Permissions</span></span>  
 <span data-ttu-id="e3c36-189">在某個範圍的權限意味著，查看該範圍及所有包含範圍之中繼資料的能力。</span><span class="sxs-lookup"><span data-stu-id="e3c36-189">Permissions at one scope imply the ability to see metadata at that scope and at all enclosed scopes.</span></span> <span data-ttu-id="e3c36-190">例如，結構描述的 SELECT 權限表示被授與者對該結構描述包含的所有安全性實體具有 SELECT 權限。</span><span class="sxs-lookup"><span data-stu-id="e3c36-190">For example, SELECT permission on a schema implies that the grantee has SELECT permission on all securables that are contained by that schema.</span></span> <span data-ttu-id="e3c36-191">因此，授與結構描述的 SELECT 權限，可讓使用者查看結構描述的中繼資料，以及其中所有資料表、檢視、函數、程序、佇列、同義字、類型和 XML 結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="e3c36-191">The granting of SELECT permission on a schema therefore enables a user to see the metadata of the schema and also all tables, views, functions, procedures, queues, synonyms, types, and XML schema collections within it.</span></span> <span data-ttu-id="e3c36-192">如需範圍的詳細資訊，請參閱[權限階層 &#40;Database Engine&#41;](permissions-hierarchy-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="e3c36-192">For more information about scopes, see [Permissions Hierarchy &#40;Database Engine&#41;](permissions-hierarchy-database-engine.md).</span></span>  
  
### <a name="precedence-of-deny"></a><span data-ttu-id="e3c36-193">DENY 的優先順序</span><span class="sxs-lookup"><span data-stu-id="e3c36-193">Precedence of DENY</span></span>  
 <span data-ttu-id="e3c36-194">DENY 的優先順序通常高於其他權限。</span><span class="sxs-lookup"><span data-stu-id="e3c36-194">DENY typically takes precedence over other permissions.</span></span> <span data-ttu-id="e3c36-195">例如，如果授與資料庫使用者結構描述的 EXECUTE 權限，但是對該結構描述中某個預存程序的 EXECUTE 權限遭到拒絕，則使用者就不能檢視該預存程序的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="e3c36-195">For example, if a database user is granted EXECUTE permission on a schema but has been denied EXECUTE permission on a stored procedure in that schema, the user cannot view the metadata for that stored procedure.</span></span>  
  
 <span data-ttu-id="e3c36-196">此外，如果某個使用者對結構描述的 EXECUTE 權限被拒，但是曾被授與該結構描述中某個預存程序的 EXECUTE 權限，則使用者還是不能檢視該預存程序的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="e3c36-196">Additionally, if a user is denied EXECUTE permission on a schema but has been granted EXECUTE permission on a stored procedure in that schema, the user cannot view the metadata for that stored procedure.</span></span>  
  
 <span data-ttu-id="e3c36-197">以其他例子來說，如果授與使用者預存程序的 EXECUTE 權限而又被拒絕 (使用不同角色成員資格可能會造成這種情形)，則會優先執行 DENY，而使用者將不能檢視該預存程序的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="e3c36-197">For another example, if a user has been granted and denied EXECUTE permission on a stored procedure, which is possible through your various role memberships, DENY takes precedence and the user cannot view the metadata of the stored procedure.</span></span>  
  
### <a name="visibility-of-subcomponent-metadata"></a><span data-ttu-id="e3c36-198">子元件中繼資料的可見性</span><span class="sxs-lookup"><span data-stu-id="e3c36-198">Visibility of Subcomponent Metadata</span></span>  
 <span data-ttu-id="e3c36-199">子元件 (例如索引、檢查條件約束和觸發程序) 的可見性是由其父元件上的權限來決定。</span><span class="sxs-lookup"><span data-stu-id="e3c36-199">The visibility of subcomponents, such as indexes, check constraints, and triggers is determined by permissions on the parent.</span></span> <span data-ttu-id="e3c36-200">這些子元件不具有可授與的權限。</span><span class="sxs-lookup"><span data-stu-id="e3c36-200">These subcomponents do not have grantable permissions.</span></span> <span data-ttu-id="e3c36-201">例如，如果某個使用者被授與了某個資料表的部分權限，該使用者就能檢視資料表、資料行、索引、檢查條件約束、觸發程序和其他子元件的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="e3c36-201">For example, if a user has been granted some permission on a table, the user can view the metadata for the tables, columns, indexes, check constraints, triggers, and other such subcomponents.</span></span>  
  
#### <a name="metadata-that-is-accessible-to-all-database-users"></a><span data-ttu-id="e3c36-202">所有資料庫使用者都可以存取的中繼資料</span><span class="sxs-lookup"><span data-stu-id="e3c36-202">Metadata That Is Accessible to All Database Users</span></span>  
 <span data-ttu-id="e3c36-203">在特定資料庫中，某些中繼資料必須可由所有使用者存取。</span><span class="sxs-lookup"><span data-stu-id="e3c36-203">Some metadata must be accessible to all users in a specific database.</span></span> <span data-ttu-id="e3c36-204">例如，檔案群組不具可授與的權限，所以使用者無法被授與權限來檢視檔案群組的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="e3c36-204">For example, filegroups do not have conferrable permissions; therefore, a user cannot be granted permission to view the metadata of a filegroup.</span></span> <span data-ttu-id="e3c36-205">但是，任何可以建立資料表的使用者，必定能夠存取檔案群組中繼資料，以使用 CREATE TABLE 陳述式中的 ON *filegroup* 或 TEXTIMAGE_ON *filegroup* 子句。</span><span class="sxs-lookup"><span data-stu-id="e3c36-205">However, any user that can create a table must be able to access filegroup metadata to use the ON *filegroup* or TEXTIMAGE_ON *filegroup* clauses of the CREATE TABLE statement.</span></span>  
  
 <span data-ttu-id="e3c36-206">DB_ID() 和 DB_NAME() 函數傳回的中繼資料，所有使用者都可以看到。</span><span class="sxs-lookup"><span data-stu-id="e3c36-206">The metadata that is returned by the DB_ID() and DB_NAME() functions is visible to all users.</span></span>  
  
 <span data-ttu-id="e3c36-207">下表列出 **public** 角色可以看見的目錄檢視。</span><span class="sxs-lookup"><span data-stu-id="e3c36-207">The following table lists the catalog views that are visible to the **public** role.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e3c36-208">**sys.partition_functions**</span><span class="sxs-lookup"><span data-stu-id="e3c36-208">**sys.partition_functions**</span></span>|<span data-ttu-id="e3c36-209">**sys.partition_range_values**</span><span class="sxs-lookup"><span data-stu-id="e3c36-209">**sys.partition_range_values**</span></span>|  
|<span data-ttu-id="e3c36-210">**sys.partition_schemes**</span><span class="sxs-lookup"><span data-stu-id="e3c36-210">**sys.partition_schemes**</span></span>|<span data-ttu-id="e3c36-211">**sys.data_spaces**</span><span class="sxs-lookup"><span data-stu-id="e3c36-211">**sys.data_spaces**</span></span>|  
|<span data-ttu-id="e3c36-212">**sys.filegroups**</span><span class="sxs-lookup"><span data-stu-id="e3c36-212">**sys.filegroups**</span></span>|<span data-ttu-id="e3c36-213">**sys.destination_data_spaces**</span><span class="sxs-lookup"><span data-stu-id="e3c36-213">**sys.destination_data_spaces**</span></span>|  
|<span data-ttu-id="e3c36-214">**sys.database_files**</span><span class="sxs-lookup"><span data-stu-id="e3c36-214">**sys.database_files**</span></span>|<span data-ttu-id="e3c36-215">**sys.allocation_units**</span><span class="sxs-lookup"><span data-stu-id="e3c36-215">**sys.allocation_units**</span></span>|  
|<span data-ttu-id="e3c36-216">**sys.partitions**</span><span class="sxs-lookup"><span data-stu-id="e3c36-216">**sys.partitions**</span></span>|<span data-ttu-id="e3c36-217">**sys.messages**</span><span class="sxs-lookup"><span data-stu-id="e3c36-217">**sys.messages**</span></span>|  
|<span data-ttu-id="e3c36-218">**sys.schemas**</span><span class="sxs-lookup"><span data-stu-id="e3c36-218">**sys.schemas**</span></span>|<span data-ttu-id="e3c36-219">**sys.configurations**</span><span class="sxs-lookup"><span data-stu-id="e3c36-219">**sys.configurations**</span></span>|  
|<span data-ttu-id="e3c36-220">**sys.sql_dependencies**</span><span class="sxs-lookup"><span data-stu-id="e3c36-220">**sys.sql_dependencies**</span></span>|<span data-ttu-id="e3c36-221">**sys.type_assembly_usages**</span><span class="sxs-lookup"><span data-stu-id="e3c36-221">**sys.type_assembly_usages**</span></span>|  
|<span data-ttu-id="e3c36-222">**sys.parameter_type_usages**</span><span class="sxs-lookup"><span data-stu-id="e3c36-222">**sys.parameter_type_usages**</span></span>|<span data-ttu-id="e3c36-223">**sys.column_type_usages**</span><span class="sxs-lookup"><span data-stu-id="e3c36-223">**sys.column_type_usages**</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e3c36-224">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3c36-224">See Also</span></span>  
 <span data-ttu-id="e3c36-225">[GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e3c36-225">[GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) </span></span>  
 <span data-ttu-id="e3c36-226">[DENY &#40;Transact-SQL&#41;](/sql/t-sql/statements/deny-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e3c36-226">[DENY &#40;Transact-SQL&#41;](/sql/t-sql/statements/deny-transact-sql) </span></span>  
 <span data-ttu-id="e3c36-227">[REVOKE &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e3c36-227">[REVOKE &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql) </span></span>  
 <span data-ttu-id="e3c36-228">[EXECUTE AS 子句 &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-clause-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e3c36-228">[EXECUTE AS Clause &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-clause-transact-sql) </span></span>  
 <span data-ttu-id="e3c36-229">[目錄檢視 &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/catalog-views-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e3c36-229">[Catalog Views &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/catalog-views-transact-sql) </span></span>  
 [<span data-ttu-id="e3c36-230">相容性檢視 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e3c36-230">Compatibility Views &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql)  
  
  
