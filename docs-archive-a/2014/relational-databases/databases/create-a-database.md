---
title: 建立資料庫 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], creating
- database creation [SQL Server], SQL Server Management Studio
- creating databases
ms.assetid: 4c4beea2-6cbc-4352-9db6-49ea8130bb64
author: stevestein
ms.author: sstein
ms.openlocfilehash: fe42e394482e3abf4d87c00c6e79ee84db6ba278
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595119"
---
# <a name="create-a-database"></a><span data-ttu-id="22c3f-102">建立資料庫</span><span class="sxs-lookup"><span data-stu-id="22c3f-102">Create a Database</span></span>
  <span data-ttu-id="22c3f-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中建立資料庫。</span><span class="sxs-lookup"><span data-stu-id="22c3f-103">This topic describes how to create a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="22c3f-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="22c3f-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="22c3f-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="22c3f-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="22c3f-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="22c3f-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="22c3f-107">先決條件</span><span class="sxs-lookup"><span data-stu-id="22c3f-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="22c3f-108">建議</span><span class="sxs-lookup"><span data-stu-id="22c3f-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="22c3f-109">安全性</span><span class="sxs-lookup"><span data-stu-id="22c3f-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="22c3f-110">**使用下列方法建立資料庫：**</span><span class="sxs-lookup"><span data-stu-id="22c3f-110">**To create a database, using:**</span></span>  
  
     [<span data-ttu-id="22c3f-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="22c3f-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="22c3f-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="22c3f-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="22c3f-113">開始之前</span><span class="sxs-lookup"><span data-stu-id="22c3f-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="22c3f-114">限制事項</span><span class="sxs-lookup"><span data-stu-id="22c3f-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="22c3f-115">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的一個執行個體上，最多可以指定 32,767 個資料庫。</span><span class="sxs-lookup"><span data-stu-id="22c3f-115">A maximum of 32,767 databases can be specified on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="22c3f-116">必要條件</span><span class="sxs-lookup"><span data-stu-id="22c3f-116">Prerequisites</span></span>  
  
-   <span data-ttu-id="22c3f-117">CREATE DATABASE 陳述式必須在自動認可模式 (預設交易管理模式) 下執行，而且不能用於明確或隱含的交易。</span><span class="sxs-lookup"><span data-stu-id="22c3f-117">The CREATE DATABASE statement must run in autocommit mode (the default transaction management mode) and is not allowed in an explicit or implicit transaction.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="22c3f-118">建議</span><span class="sxs-lookup"><span data-stu-id="22c3f-118">Recommendations</span></span>  
  
-   <span data-ttu-id="22c3f-119">每當建立、修改或卸除使用者資料庫時，都應該備份 [master](master-database.md) 資料庫。</span><span class="sxs-lookup"><span data-stu-id="22c3f-119">The [master](master-database.md) database should be backed up whenever a user database is created, modified, or dropped.</span></span>  
  
-   <span data-ttu-id="22c3f-120">當您建立資料庫時，請根據您預期之資料庫中的資料量上限，盡量使資料檔案有足夠的空間。</span><span class="sxs-lookup"><span data-stu-id="22c3f-120">When you create a database, make the data files as large as possible based on the maximum amount of data you expect in the database.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="22c3f-121">Security</span><span class="sxs-lookup"><span data-stu-id="22c3f-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="22c3f-122">權限</span><span class="sxs-lookup"><span data-stu-id="22c3f-122">Permissions</span></span>  
 <span data-ttu-id="22c3f-123">需要 master 資料庫的 CREATE DATABASE 權限，或需要 CREATE ANY DATABASE 或 ALTER ANY DATABASE 權限。</span><span class="sxs-lookup"><span data-stu-id="22c3f-123">Requires CREATE DATABASE permission in the master database, or requires CREATE ANY DATABASE, or ALTER ANY DATABASE permission.</span></span>  
  
 <span data-ttu-id="22c3f-124">為了維護 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的磁碟控制，通常只有少數登入帳戶有建立資料庫的權限。</span><span class="sxs-lookup"><span data-stu-id="22c3f-124">To maintain control over disk use on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], permission to create databases is typically limited to a few login accounts.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="22c3f-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="22c3f-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-database"></a><span data-ttu-id="22c3f-126">若要建立資料庫</span><span class="sxs-lookup"><span data-stu-id="22c3f-126">To create a database</span></span>  
  
1.  <span data-ttu-id="22c3f-127">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="22c3f-127">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="22c3f-128">以滑鼠右鍵按一下 [資料庫]，然後按一下 [新增資料庫]。</span><span class="sxs-lookup"><span data-stu-id="22c3f-128">Right-click **Databases**, and then click **New Database**.</span></span>  
  
3.  <span data-ttu-id="22c3f-129">在 **[新增資料庫]** 中，輸入資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="22c3f-129">In **New Database**, enter a database name.</span></span>  
  
4.  <span data-ttu-id="22c3f-130">若要使用所有預設值來建立資料庫，請按一下 **[確定]** ，否則繼續執行下列選擇性步驟。</span><span class="sxs-lookup"><span data-stu-id="22c3f-130">To create the database by accepting all default values, click **OK**; otherwise, continue with the following optional steps.</span></span>  
  
5.  <span data-ttu-id="22c3f-131">若要變更擁有者名稱，請按一下 ( **…** ) 來選取其他擁有者。</span><span class="sxs-lookup"><span data-stu-id="22c3f-131">To change the owner name, click (**...**) to select another owner.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="22c3f-132">[使用全文檢索索引] 選項一定是核取狀態而且呈暗灰色，因為從 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 開始，所有使用者資料庫都會啟用全文檢索。</span><span class="sxs-lookup"><span data-stu-id="22c3f-132">The **Use full-text indexing** option is always checked and dimmed because, beginning in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], all user databases are full-text enabled.</span></span>  
  
6.  <span data-ttu-id="22c3f-133">若要變更主要資料與交易記錄檔的預設值，請在 **[資料庫檔案]** 方格中按一下適當的資料格，並輸入新的值。</span><span class="sxs-lookup"><span data-stu-id="22c3f-133">To change the default values of the primary data and transaction log files, in the **Database files** grid, click the appropriate cell and enter the new value.</span></span> <span data-ttu-id="22c3f-134">如需詳細資訊，請參閱 [將資料或記錄檔加入資料庫](add-data-or-log-files-to-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="22c3f-134">For more information, see [Add Data or Log Files to a Database](add-data-or-log-files-to-a-database.md).</span></span>  
  
7.  <span data-ttu-id="22c3f-135">若要變更資料庫的定序，請選取 **[選項]** 頁面，然後從清單中選取定序。</span><span class="sxs-lookup"><span data-stu-id="22c3f-135">To change the collation of the database, select the **Options** page, and then select a collation from the list.</span></span>  
  
8.  <span data-ttu-id="22c3f-136">若要變更復原模式，請選取 **[選項]** 頁面，並從清單中選取復原模式。</span><span class="sxs-lookup"><span data-stu-id="22c3f-136">To change the recovery model, select the **Options** page and select a recovery model from the list.</span></span>  
  
9. <span data-ttu-id="22c3f-137">若要變更資料庫選項，請選取 **[選項]** 頁面，然後修改資料庫選項。</span><span class="sxs-lookup"><span data-stu-id="22c3f-137">To change database options, select the **Options** page, and then modify the database options.</span></span> <span data-ttu-id="22c3f-138">如需每個選項的說明，請參閱 [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)。</span><span class="sxs-lookup"><span data-stu-id="22c3f-138">For a description of each option, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
10. <span data-ttu-id="22c3f-139">若要加入新的檔案群組，請按一下 **[檔案群組]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="22c3f-139">To add a new filegroup, click the **Filegroups** page.</span></span> <span data-ttu-id="22c3f-140">按一下 **[加入]** ，然後輸入檔案群組的值。</span><span class="sxs-lookup"><span data-stu-id="22c3f-140">Click **Add** and then enter the values for the filegroup.</span></span>  
  
11. <span data-ttu-id="22c3f-141">若要將擴充屬性加入至資料庫，請選取 **[擴充屬性]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="22c3f-141">To add an extended property to the database, select the **Extended Properties** page.</span></span>  
  
    1.  <span data-ttu-id="22c3f-142">在 **[名稱]** 資料行中，輸入擴充屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="22c3f-142">In the **Name** column, enter a name for the extended property.</span></span>  
  
    2.  <span data-ttu-id="22c3f-143">在 **[值]** 資料行中，輸入擴充屬性文字。</span><span class="sxs-lookup"><span data-stu-id="22c3f-143">In the **Value** column, enter the extended property text.</span></span> <span data-ttu-id="22c3f-144">例如，輸入一個或多個可說明資料庫的陳述。</span><span class="sxs-lookup"><span data-stu-id="22c3f-144">For example, enter one or more statements that describe the database.</span></span>  
  
12. <span data-ttu-id="22c3f-145">若要建立資料庫，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="22c3f-145">To create the database, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="22c3f-146">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="22c3f-146">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-database"></a><span data-ttu-id="22c3f-147">若要建立資料庫</span><span class="sxs-lookup"><span data-stu-id="22c3f-147">To create a database</span></span>  
  
1.  <span data-ttu-id="22c3f-148">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="22c3f-148">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="22c3f-149">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="22c3f-149">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="22c3f-150">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="22c3f-150">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="22c3f-151">這個範例會建立 `Sales`資料庫。</span><span class="sxs-lookup"><span data-stu-id="22c3f-151">This example creates the database `Sales`.</span></span> <span data-ttu-id="22c3f-152">因為沒有使用關鍵字 PRIMARY，所以第一個檔案 (`Sales`_`dat`) 會成為主要檔案。</span><span class="sxs-lookup"><span data-stu-id="22c3f-152">Because the keyword PRIMARY is not used, the first file (`Sales`_`dat`) becomes the primary file.</span></span> <span data-ttu-id="22c3f-153">因為 `Sales`\_`dat` 檔的 SIZE 參數中沒有指定 MB 或 KB，所以它會使用 MB 並 MB 來配置。</span><span class="sxs-lookup"><span data-stu-id="22c3f-153">Because neither MB nor KB is specified in the SIZE parameter for the `Sales`\_`dat` file, it uses MB and is allocated in megabytes.</span></span> <span data-ttu-id="22c3f-154">每當建立、修改或卸除使用者資料庫時，都應該備份 `Sales`\_`log` 檔會以 MB 為單位配置，因為 `MB` 參數中明確陳述 `SIZE` 後置詞。</span><span class="sxs-lookup"><span data-stu-id="22c3f-154">The `Sales`\_`log` file is allocated in megabytes because the `MB` suffix is explicitly stated in the `SIZE` parameter.</span></span>  
  
```sql  
USE master ;  
GO  
CREATE DATABASE Sales  
ON   
( NAME = Sales_dat,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\saledat.mdf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 5 )  
LOG ON  
( NAME = Sales_log,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\salelog.ldf',  
    SIZE = 5MB,  
    MAXSIZE = 25MB,  
    FILEGROWTH = 5MB ) ;  
GO  
```  
  
 <span data-ttu-id="22c3f-155">如需範例，請參閱 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="22c3f-155">For more examples, see [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22c3f-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22c3f-156">See Also</span></span>  
 <span data-ttu-id="22c3f-157">[Database Files and Filegroups](database-files-and-filegroups.md) </span><span class="sxs-lookup"><span data-stu-id="22c3f-157">[Database Files and Filegroups](database-files-and-filegroups.md) </span></span>  
 <span data-ttu-id="22c3f-158">[資料庫卸離和附加 &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="22c3f-158">[Database Detach and Attach &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md) </span></span>  
 <span data-ttu-id="22c3f-159">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="22c3f-159">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="22c3f-160">將資料或記錄檔加入資料庫</span><span class="sxs-lookup"><span data-stu-id="22c3f-160">Add Data or Log Files to a Database</span></span>](add-data-or-log-files-to-a-database.md)  
  
  
