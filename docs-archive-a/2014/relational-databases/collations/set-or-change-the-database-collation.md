---
title: 設定或變更資料庫定序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- collations [SQL Server], database
- database collations [SQL Server]
ms.assetid: 1379605c-1242-4ac8-ab1b-e2a2b5b1f895
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6d7f7c3e3ddba7ba0ea9701993dbe0fad3a8d975
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606900"
---
# <a name="set-or-change-the-database-collation"></a><span data-ttu-id="4247f-102">設定或變更資料庫定序</span><span class="sxs-lookup"><span data-stu-id="4247f-102">Set or Change the Database Collation</span></span>
  <span data-ttu-id="4247f-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中設定及變更資料庫定序。</span><span class="sxs-lookup"><span data-stu-id="4247f-103">This topic describes how set and change the database collation in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="4247f-104">如果沒有指定定序，會使用伺服器定序。</span><span class="sxs-lookup"><span data-stu-id="4247f-104">If no collation is specified, the server collation is used.</span></span>  
  
 <span data-ttu-id="4247f-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="4247f-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4247f-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="4247f-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4247f-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="4247f-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="4247f-108">建議</span><span class="sxs-lookup"><span data-stu-id="4247f-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="4247f-109">安全性</span><span class="sxs-lookup"><span data-stu-id="4247f-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4247f-110">**若要使用下列項目設定或變更資料庫定序：**</span><span class="sxs-lookup"><span data-stu-id="4247f-110">**To set or change the database collation, using:**</span></span>  
  
     [<span data-ttu-id="4247f-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4247f-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4247f-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4247f-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4247f-113">開始之前</span><span class="sxs-lookup"><span data-stu-id="4247f-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="4247f-114">限制事項</span><span class="sxs-lookup"><span data-stu-id="4247f-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="4247f-115">僅限 Windows Unicode 定序只能搭配 COLLATE 子句使用，以便將定序套用至資料行層級和運算式層級資料的 `nchar`、`nvarchar` 和 `ntext` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="4247f-115">Windows Unicode-only collations can only be used with the COLLATE clause to apply collations to the `nchar`, `nvarchar`, and `ntext` data types on column level and expression-level data.</span></span> <span data-ttu-id="4247f-116">這些定序無法搭配 COLLATE 子句使用，以變更資料庫或伺服器執行個體的定序。</span><span class="sxs-lookup"><span data-stu-id="4247f-116">They cannot be used with the COLLATE clause to change the collation of a database or server instance.</span></span>  
  
-   <span data-ttu-id="4247f-117">如果指定的定序或所參考物件所用的定序使用 Windows 不支援的字碼頁， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 就會顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="4247f-117">If the specified collation or the collation used by the referenced object uses a code page that is not supported by Windows, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] displays an error.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="4247f-118">建議</span><span class="sxs-lookup"><span data-stu-id="4247f-118">Recommendations</span></span>  
  
-   <span data-ttu-id="4247f-119">您可以在 [Windows 定序名稱 &#40;Transact-SQL&#41;](/sql/t-sql/statements/windows-collation-name-transact-sql) 和 [SQL Server 定序名稱 &#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql)中找到支援的定序名稱；您也可以使用 [sys.fn_helpcollations &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-helpcollations-transact-sql) 系統函數。</span><span class="sxs-lookup"><span data-stu-id="4247f-119">You can find the supported collation names in [Windows Collation Name &#40;Transact-SQL&#41;](/sql/t-sql/statements/windows-collation-name-transact-sql) and [SQL Server Collation Name &#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql); or you can use the [sys.fn_helpcollations &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-helpcollations-transact-sql) system function.</span></span>  
  
-   <span data-ttu-id="4247f-120">當您變更資料庫定序時，會變更下列各項：</span><span class="sxs-lookup"><span data-stu-id="4247f-120">When you change the database collation, you change the following:</span></span>  
  
    -   <span data-ttu-id="4247f-121">系統資料表中的任何 `char`、`varchar`、`text`、`nchar`、`nvarchar`，或 `ntext` 資料行都會變更為新定序。</span><span class="sxs-lookup"><span data-stu-id="4247f-121">Any `char`, `varchar`, `text`, `nchar`, `nvarchar`, or `ntext` columns in system tables are changed to the new collation.</span></span>  
  
    -   <span data-ttu-id="4247f-122">預存程序與使用者定義函數的任何現有 `char`、`varchar`、`text`、`nchar`、`nvarchar`，或 `ntext` 參數和純量傳回值，都會變更為新定序。</span><span class="sxs-lookup"><span data-stu-id="4247f-122">All existing `char`, `varchar`, `text`, `nchar`, `nvarchar`, or `ntext` parameters and scalar return values for stored procedures and user-defined functions are changed to the new collation.</span></span>  
  
    -   <span data-ttu-id="4247f-123">`char`、`varchar`、`text`、`nchar`、`nvarchar`，或 `ntext` 系統資料類型，以及以這些系統資料類型為基礎的所有使用者定義資料類型，都會變更為新的預設定序。</span><span class="sxs-lookup"><span data-stu-id="4247f-123">The `char`, `varchar`, `text`, `nchar`, `nvarchar`, or `ntext` system data types, and all user-defined data types based on these system data types, are changed to the new default collation.</span></span>  
  
-   <span data-ttu-id="4247f-124">您可以使用 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) 陳述式的 COLLATE 子句，變更在使用者資料庫中建立的任何新物件的定序。</span><span class="sxs-lookup"><span data-stu-id="4247f-124">You can change the collation of any new objects that are created in a user database by using the COLLATE clause of the [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement.</span></span> <span data-ttu-id="4247f-125">此陳述式不會變更現有使用者自訂資料表中的資料行定序。</span><span class="sxs-lookup"><span data-stu-id="4247f-125">This statement does not change the collation of the columns in any existing user-defined tables.</span></span> <span data-ttu-id="4247f-126">您可以使用 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql)的 COLLATE 子句進行變更。</span><span class="sxs-lookup"><span data-stu-id="4247f-126">These can be changed by using the COLLATE clause of [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4247f-127">Security</span><span class="sxs-lookup"><span data-stu-id="4247f-127">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4247f-128">權限</span><span class="sxs-lookup"><span data-stu-id="4247f-128">Permissions</span></span>  
 <span data-ttu-id="4247f-129">CREATE DATABASE</span><span class="sxs-lookup"><span data-stu-id="4247f-129">CREATE DATABASE</span></span>  
 <span data-ttu-id="4247f-130">需要**master**資料庫中的 create DATABASE 許可權，或需要 CREATE any DATABASE 或 ALTER any database 許可權。</span><span class="sxs-lookup"><span data-stu-id="4247f-130">Requires CREATE DATABASE permission in the **master** database, or requires CREATE ANY DATABASE, or ALTER ANY DATABASE permission.</span></span>  
  
 <span data-ttu-id="4247f-131">ALTER DATABASE</span><span class="sxs-lookup"><span data-stu-id="4247f-131">ALTER DATABASE</span></span>  
 <span data-ttu-id="4247f-132">需要資料庫的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="4247f-132">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4247f-133">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4247f-133">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-or-change-the-database-collation"></a><span data-ttu-id="4247f-134">若要設定或變更資料庫定序</span><span class="sxs-lookup"><span data-stu-id="4247f-134">To set or change the database collation</span></span>  
  
1.  <span data-ttu-id="4247f-135">在 [物件總管]  中，連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的執行個體，展開該執行個體，然後展開 [資料庫]  。</span><span class="sxs-lookup"><span data-stu-id="4247f-135">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], expand that instance, and then expand **Databases**.</span></span>  
  
2.  <span data-ttu-id="4247f-136">如果您要建立新資料庫，以滑鼠右鍵按一下 **[資料庫]** ，然後按一下 **[新增資料庫]** 。</span><span class="sxs-lookup"><span data-stu-id="4247f-136">If you are creating a new database, right-click **Databases** and then click **New Database**.</span></span> <span data-ttu-id="4247f-137">如果不要預設定序，請按一下 **[選項]** 頁面，然後從 **[定序]** 下拉式清單中選取定序。</span><span class="sxs-lookup"><span data-stu-id="4247f-137">If you do not want the default collation, click the **Options** page, and select a collation from the **Collation** drop-down list.</span></span>  
  
     <span data-ttu-id="4247f-138">或者，如果資料庫已經存在，以滑鼠右鍵按一下所要的資料庫，然後按一下 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="4247f-138">Alternatively, if the database already exists, right-click the database that you want and click **Properties**.</span></span> <span data-ttu-id="4247f-139">按一下 **[選項]** 頁面，然後從 **[定序]** 下拉式清單中選取定序。</span><span class="sxs-lookup"><span data-stu-id="4247f-139">Click the **Options** page, and select a collation from the **Collation** drop-down list.</span></span>  
  
3.  <span data-ttu-id="4247f-140">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="4247f-140">After you are finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4247f-141">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4247f-141">Using Transact-SQL</span></span>  
  
#### <a name="to-set-the-database-collation"></a><span data-ttu-id="4247f-142">若要設定資料庫定序</span><span class="sxs-lookup"><span data-stu-id="4247f-142">To set the database collation</span></span>  
  
1.  <span data-ttu-id="4247f-143">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4247f-143">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4247f-144">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="4247f-144">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4247f-145">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="4247f-145">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="4247f-146">此範例示範如何使用 [COLLATE](/sql/t-sql/statements/collations) 子句來指定定序名稱。</span><span class="sxs-lookup"><span data-stu-id="4247f-146">This example shows how to use the [COLLATE](/sql/t-sql/statements/collations) clause to specify a collation name.</span></span> <span data-ttu-id="4247f-147">範例會建立使用 `MyOptionsTest` 定序的 `Latin1_General_100_CS_AS_SC` 資料庫。</span><span class="sxs-lookup"><span data-stu-id="4247f-147">The example creates the database `MyOptionsTest` that uses the `Latin1_General_100_CS_AS_SC` collation.</span></span> <span data-ttu-id="4247f-148">在您建立資料庫之後，執行 `SELECT` 陳述式以驗證設定。</span><span class="sxs-lookup"><span data-stu-id="4247f-148">After you create the database, execute the `SELECT` statement to verify the setting.</span></span>  
  
```sql  
USE master;  
GO  
IF DB_ID (N'MyOptionsTest') IS NOT NULL  
DROP DATABASE MyOptionsTest;  
GO  
CREATE DATABASE MyOptionsTest  
COLLATE Latin1_General_100_CS_AS_SC;  
GO  
  
--Verify the collation setting.  
SELECT name, collation_name  
FROM sys.databases  
WHERE name = N'MyOptionsTest';  
GO  
  
```  
  
#### <a name="to-change-the-database-collation"></a><span data-ttu-id="4247f-149">若要變更資料庫定序</span><span class="sxs-lookup"><span data-stu-id="4247f-149">To change the database collation</span></span>  
  
1.  <span data-ttu-id="4247f-150">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4247f-150">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4247f-151">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="4247f-151">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4247f-152">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="4247f-152">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="4247f-153">此範例示範如何在 [ALTER DATABASE](/sql/t-sql/statements/collations) 陳述式中使用 [COLLATE](/sql/t-sql/statements/alter-database-transact-sql) 子句，以變更定序名稱。</span><span class="sxs-lookup"><span data-stu-id="4247f-153">This example shows how to use the [COLLATE](/sql/t-sql/statements/collations) clause in an [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement to change the collation name.</span></span> <span data-ttu-id="4247f-154">執行 `SELECT` 陳述式以驗證變更。</span><span class="sxs-lookup"><span data-stu-id="4247f-154">Execute the `SELECT` statement to verify the change.</span></span>  
  
```sql  
USE master;  
GO  
ALTER DATABASE MyOptionsTest  
COLLATE French_CI_AS ;  
GO  
  
--Verify the collation setting.  
SELECT name, collation_name  
FROM sys.databases  
WHERE name = N'MyOptionsTest';  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="4247f-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4247f-155">See Also</span></span>  
 <span data-ttu-id="4247f-156">[定序與 Unicode 支援](collation-and-unicode-support.md) </span><span class="sxs-lookup"><span data-stu-id="4247f-156">[Collation and Unicode Support](collation-and-unicode-support.md) </span></span>  
 <span data-ttu-id="4247f-157">[sys.fn_helpcollations &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-helpcollations-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4247f-157">[sys.fn_helpcollations &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-helpcollations-transact-sql) </span></span>  
 <span data-ttu-id="4247f-158">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4247f-158">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span></span>  
 <span data-ttu-id="4247f-159">[SQL Server 定序名稱 &#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4247f-159">[SQL Server Collation Name &#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql) </span></span>  
 <span data-ttu-id="4247f-160">[Windows 定序名稱 &#40;Transact-SQL&#41;](/sql/t-sql/statements/windows-collation-name-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4247f-160">[Windows Collation Name &#40;Transact-SQL&#41;](/sql/t-sql/statements/windows-collation-name-transact-sql) </span></span>  
 <span data-ttu-id="4247f-161">[COLLATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/collations) </span><span class="sxs-lookup"><span data-stu-id="4247f-161">[COLLATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/collations) </span></span>  
 <span data-ttu-id="4247f-162">[定序優先順序 &#40;Transact-SQL&#41;](/sql/t-sql/statements/collation-precedence-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4247f-162">[Collation Precedence &#40;Transact-SQL&#41;](/sql/t-sql/statements/collation-precedence-transact-sql) </span></span>  
 <span data-ttu-id="4247f-163">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4247f-163">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span></span>  
 <span data-ttu-id="4247f-164">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4247f-164">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 <span data-ttu-id="4247f-165">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4247f-165">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span></span>  
 [<span data-ttu-id="4247f-166">ALTER DATABASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4247f-166">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
