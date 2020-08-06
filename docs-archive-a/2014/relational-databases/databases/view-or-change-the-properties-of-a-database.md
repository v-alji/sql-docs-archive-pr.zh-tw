---
title: 檢視或變更資料庫的屬性 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- displaying databases
- database viewing [SQL Server]
- databases [SQL Server], viewing
- viewing databases
ms.assetid: 9e8ac097-84b7-46c7-85e3-c1e79f94d747
author: stevestein
ms.author: sstein
ms.openlocfilehash: d6aee7503ca02d47575be4e8103641f61d9696d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708422"
---
# <a name="view-or-change-the-properties-of-a-database"></a><span data-ttu-id="a9ef4-102">檢視或變更資料庫的屬性</span><span class="sxs-lookup"><span data-stu-id="a9ef4-102">View or Change the Properties of a Database</span></span>
  <span data-ttu-id="a9ef4-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中檢視或變更資料庫的屬性。</span><span class="sxs-lookup"><span data-stu-id="a9ef4-103">This topic describes how to view or change the properties of a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="a9ef4-104">變更資料庫屬性之後，修改會立即生效。</span><span class="sxs-lookup"><span data-stu-id="a9ef4-104">After you change a database property, the modification takes effect immediately.</span></span>  
  
 <span data-ttu-id="a9ef4-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="a9ef4-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a9ef4-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="a9ef4-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a9ef4-107">建議</span><span class="sxs-lookup"><span data-stu-id="a9ef4-107">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="a9ef4-108">安全性</span><span class="sxs-lookup"><span data-stu-id="a9ef4-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a9ef4-109">**使用下列方法檢視或變更資料庫的屬性：**</span><span class="sxs-lookup"><span data-stu-id="a9ef4-109">**To view or change the properties of a database, using:**</span></span>  
  
     [<span data-ttu-id="a9ef4-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a9ef4-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a9ef4-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a9ef4-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a9ef4-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="a9ef4-112">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="a9ef4-113">建議</span><span class="sxs-lookup"><span data-stu-id="a9ef4-113">Recommendations</span></span>  
  
-   <span data-ttu-id="a9ef4-114">當 AUTO_CLOSE 是 ON 時， [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) 目錄檢視中的某些資料行及 DATABASEPROPERTYEX 函數會傳回 NULL，因為資料庫無法擷取資料。</span><span class="sxs-lookup"><span data-stu-id="a9ef4-114">When AUTO_CLOSE is ON, some columns in the [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) catalog view and DATABASEPROPERTYEX function will return NULL because the database is unavailable to retrieve the data.</span></span> <span data-ttu-id="a9ef4-115">若要解決這個問題，請執行 USE 陳述式來開啟資料庫。</span><span class="sxs-lookup"><span data-stu-id="a9ef4-115">To resolve this, execute a USE statement to open the database.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a9ef4-116">Security</span><span class="sxs-lookup"><span data-stu-id="a9ef4-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a9ef4-117">權限</span><span class="sxs-lookup"><span data-stu-id="a9ef4-117">Permissions</span></span>  
 <span data-ttu-id="a9ef4-118">需要資料庫的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="a9ef4-118">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a9ef4-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a9ef4-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-or-change-the-properties-of-a-database"></a><span data-ttu-id="a9ef4-120">檢視或變更資料庫的屬性</span><span class="sxs-lookup"><span data-stu-id="a9ef4-120">To view or change the properties of a database</span></span>  
  
1.  <span data-ttu-id="a9ef4-121">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="a9ef4-121">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="a9ef4-122">展開 [資料庫]，並以滑鼠右鍵按一下要檢視的資料庫，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="a9ef4-122">Expand **Databases**, right-click the database to view, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="a9ef4-123">在 **[資料庫屬性]** 對話方塊中，選取一個頁面以檢視對應的資訊。</span><span class="sxs-lookup"><span data-stu-id="a9ef4-123">In the **Database Properties** dialog box, select a page to view the corresponding information.</span></span> <span data-ttu-id="a9ef4-124">例如，選取 **[檔案]** 頁面以檢視資料和記錄檔資訊。</span><span class="sxs-lookup"><span data-stu-id="a9ef4-124">For example, select the **Files** page to view data and log file information.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a9ef4-125">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a9ef4-125">Using Transact-SQL</span></span>  
  
#### <a name="to-view-a-property-of-a-database-by-using-databasepropertyex"></a><span data-ttu-id="a9ef4-126">透過使用 DATABASEPROPERTYEX 檢視資料庫的屬性</span><span class="sxs-lookup"><span data-stu-id="a9ef4-126">To view a property of a database by using DATABASEPROPERTYEX</span></span>  
  
1.  <span data-ttu-id="a9ef4-127">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a9ef4-127">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a9ef4-128">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="a9ef4-128">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a9ef4-129">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="a9ef4-129">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="a9ef4-130">這個範例使用 [DATABASEPROPERTYEX](/sql/t-sql/functions/databasepropertyex-transact-sql) 系統函數傳回 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫之 AUTO_SHRINK 資料庫選項的狀態。</span><span class="sxs-lookup"><span data-stu-id="a9ef4-130">This example uses the [DATABASEPROPERTYEX](/sql/t-sql/functions/databasepropertyex-transact-sql) system function to return the status of the AUTO_SHRINK database option in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="a9ef4-131">傳回值為 1 表示選項設定為 ON，傳回值為 0 表示選項設定為 OFF。</span><span class="sxs-lookup"><span data-stu-id="a9ef4-131">A return value of 1 means that the option is set to ON, and a return value of 0 means that the option is set to OFF.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT DATABASEPROPERTYEX('AdventureWorks2012', 'IsAutoShrink');  
GO  
  
```  
  
#### <a name="to-view-the-properties-of-a-database-by-querying-sysdatabases"></a><span data-ttu-id="a9ef4-132">透過查詢 sys.databases 檢視資料庫的屬性</span><span class="sxs-lookup"><span data-stu-id="a9ef4-132">To view the properties of a database by querying sys.databases</span></span>  
  
1.  <span data-ttu-id="a9ef4-133">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a9ef4-133">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a9ef4-134">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="a9ef4-134">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a9ef4-135">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="a9ef4-135">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="a9ef4-136">這個範例會查詢 [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) 目錄檢視，以查看 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫的數個屬性。</span><span class="sxs-lookup"><span data-stu-id="a9ef4-136">This example queries the [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) catalog view to view several properties of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="a9ef4-137">這個範例會傳回資料庫識別碼 (`database_id`)、資料庫是唯讀還是讀寫 (`is_read_only`)、資料庫定序 (`collation_name`)，以及資料庫相容性層級 (`compatibility_level`)。</span><span class="sxs-lookup"><span data-stu-id="a9ef4-137">This example returns the database ID number (`database_id`), whether the database is read-only or read-write (`is_read_only`), the collation for the database (`collation_name`), and the database compatibility level (`compatibility_level`).</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT database_id, is_read_only, collation_name, compatibility_level  
FROM sys.databases WHERE name = 'AdventureWorks2012';  
GO  
  
```  
  
#### <a name="to-change-the-properties-of-a-database"></a><span data-ttu-id="a9ef4-138">變更資料庫的屬性</span><span class="sxs-lookup"><span data-stu-id="a9ef4-138">To change the properties of a database</span></span>  
  
1.  <span data-ttu-id="a9ef4-139">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a9ef4-139">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a9ef4-140">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="a9ef4-140">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a9ef4-141">將下列範例複製並貼入查詢視窗中。</span><span class="sxs-lookup"><span data-stu-id="a9ef4-141">Copy and paste the following example into the query window.</span></span> <span data-ttu-id="a9ef4-142">此範例判斷 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫上快照集隔離的狀態、變更屬性狀態，然後驗證變更。</span><span class="sxs-lookup"><span data-stu-id="a9ef4-142">The example determines the state of snapshot isolation on the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, changes the state of the property, and then verifies the change.</span></span>  
  
     <span data-ttu-id="a9ef4-143">若要判斷快照集隔離的狀態，請選取第一個 `SELECT` 陳述式並按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="a9ef4-143">To determine the state of snapshot isolation, select the first `SELECT` statement and click **Execute**.</span></span>  
  
     <span data-ttu-id="a9ef4-144">若要變更快照集隔離的狀態，請選取 `ALTER DATABASE` 陳述式並按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="a9ef4-144">To change the state of snapshot isolation, select the `ALTER DATABASE` statement and click **Execute**.</span></span>  
  
     <span data-ttu-id="a9ef4-145">若要驗證變更，請選取第二個 `SELECT` 陳述式並按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="a9ef4-145">To verify the change, select the second `SELECT` statement, and click **Execute**.</span></span>  
  
 [!code-sql[DatabaseDDL#AlterDatabase9](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase9)]  
  
## <a name="see-also"></a><span data-ttu-id="a9ef4-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9ef4-146">See Also</span></span>  
 <span data-ttu-id="a9ef4-147">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a9ef4-147">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span></span>  
 <span data-ttu-id="a9ef4-148">[ALTER DATABASE SET HADR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) </span><span class="sxs-lookup"><span data-stu-id="a9ef4-148">[ALTER DATABASE SET HADR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) </span></span>  
 <span data-ttu-id="a9ef4-149">[ALTER DATABASE SET 選項 &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options) </span><span class="sxs-lookup"><span data-stu-id="a9ef4-149">[ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options) </span></span>  
 <span data-ttu-id="a9ef4-150">[ALTER DATABASE 資料庫鏡像 &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span><span class="sxs-lookup"><span data-stu-id="a9ef4-150">[ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span></span>  
 <span data-ttu-id="a9ef4-151">[ALTER DATABASE 相容性層級 &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) </span><span class="sxs-lookup"><span data-stu-id="a9ef4-151">[ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) </span></span>  
 [<span data-ttu-id="a9ef4-152">ALTER DATABASE 檔案及檔案群組選項 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a9ef4-152">ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)  
  
  
