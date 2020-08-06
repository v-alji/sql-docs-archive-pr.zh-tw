---
title: 移轉至部分自主資料庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- contained database, migrating to
ms.assetid: 90faac38-f79e-496d-b589-e8b2fe01c562
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6142d46dc0540e5998fa66d463538d1453a17d84
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709521"
---
# <a name="migrate-to-a-partially-contained-database"></a><span data-ttu-id="2fe15-102">Migrate to a Partially Contained Database</span><span class="sxs-lookup"><span data-stu-id="2fe15-102">Migrate to a Partially Contained Database</span></span>
  <span data-ttu-id="2fe15-103">此主題討論如何準備變更為部分自主資料庫模型，然後提供移轉步驟。</span><span class="sxs-lookup"><span data-stu-id="2fe15-103">This topic discusses how to prepare to change to the partially contained database model and then provides the migration steps.</span></span>  
  
 <span data-ttu-id="2fe15-104">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="2fe15-104">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="2fe15-105">準備移轉資料庫</span><span class="sxs-lookup"><span data-stu-id="2fe15-105">Preparing to Migrate a Database</span></span>](#prepare)  
  
-   [<span data-ttu-id="2fe15-106">啟用自主資料庫</span><span class="sxs-lookup"><span data-stu-id="2fe15-106">Enable Contained Databases</span></span>](#enable)  
  
-   [<span data-ttu-id="2fe15-107">將資料庫轉換成部分自主資料庫</span><span class="sxs-lookup"><span data-stu-id="2fe15-107">Converting a Database to Partially Contained</span></span>](#convert)  
  
-   [<span data-ttu-id="2fe15-108">將使用者移轉至自主資料庫使用者</span><span class="sxs-lookup"><span data-stu-id="2fe15-108">Migrating Users to Contained Database Users</span></span>](#users)  
  
##  <a name="preparing-to-migrate-a-database"></a><a name="prepare"></a> <span data-ttu-id="2fe15-109">準備移轉資料庫</span><span class="sxs-lookup"><span data-stu-id="2fe15-109">Preparing to Migrate a Database</span></span>  
 <span data-ttu-id="2fe15-110">當您考慮將資料庫移轉至部分自主資料庫模型時，請檢閱下列項目。</span><span class="sxs-lookup"><span data-stu-id="2fe15-110">Review the following items when considering migrating a database to the partially contained database model.</span></span>  
  
-   <span data-ttu-id="2fe15-111">您應該了解部分自主資料庫模型。</span><span class="sxs-lookup"><span data-stu-id="2fe15-111">You should understand the partially contained database model.</span></span> <span data-ttu-id="2fe15-112">如需相關資訊，請參閱 [自主資料庫](contained-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="2fe15-112">For more information, see [Contained Databases](contained-databases.md).</span></span>  
  
-   <span data-ttu-id="2fe15-113">您應該了解部分自主資料庫獨有的風險。</span><span class="sxs-lookup"><span data-stu-id="2fe15-113">You should understand risks that are unique to partially contained databases.</span></span> <span data-ttu-id="2fe15-114">如需詳細資訊，請參閱 [Security Best Practices with Contained Databases](security-best-practices-with-contained-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="2fe15-114">For more information, see [Security Best Practices with Contained Databases](security-best-practices-with-contained-databases.md).</span></span>  
  
-   <span data-ttu-id="2fe15-115">自主資料庫不支援複寫、異動資料擷取，或變更追蹤。</span><span class="sxs-lookup"><span data-stu-id="2fe15-115">Contained databases do not support replication, change data capture, or change tracking.</span></span> <span data-ttu-id="2fe15-116">請確認資料庫不會使用這些功能。</span><span class="sxs-lookup"><span data-stu-id="2fe15-116">Confirm the database does not use these features.</span></span>  
  
-   <span data-ttu-id="2fe15-117">請檢閱針對部分自主資料庫修改的資料庫功能清單。</span><span class="sxs-lookup"><span data-stu-id="2fe15-117">Review the list of database features that are modified for partially contained databases.</span></span> <span data-ttu-id="2fe15-118">如需詳細資訊，請參閱[修改的功能 &#40;自主資料庫&#41;](modified-features-contained-database.md)。</span><span class="sxs-lookup"><span data-stu-id="2fe15-118">For more information, see [Modified Features &#40;Contained Database&#41;](modified-features-contained-database.md).</span></span>  
  
-   <span data-ttu-id="2fe15-119">請查詢 [sys.dm_db_uncontained_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-uncontained-entities-transact-sql) 來尋找資料庫中的非內含性物件或功能。</span><span class="sxs-lookup"><span data-stu-id="2fe15-119">Query [sys.dm_db_uncontained_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-uncontained-entities-transact-sql) to find uncontained objects or features in the database.</span></span> <span data-ttu-id="2fe15-120">如需詳細資訊，請參閱。</span><span class="sxs-lookup"><span data-stu-id="2fe15-120">For more information, see.</span></span>  
  
-   <span data-ttu-id="2fe15-121">請監視 **database_uncontained_usage** XEvent 來查看使用非內含性功能的時間。</span><span class="sxs-lookup"><span data-stu-id="2fe15-121">Monitor the **database_uncontained_usage** XEvent to see when uncontained features are used.</span></span>  
  
##  <a name="enable-contained-databases"></a><a name="enable"></a> <span data-ttu-id="2fe15-122">啟用自主資料庫</span><span class="sxs-lookup"><span data-stu-id="2fe15-122">Enable Contained Databases</span></span>  
 <span data-ttu-id="2fe15-123">您必須先在 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]執行個體上啟用自主資料庫，然後才能建立自主資料庫。</span><span class="sxs-lookup"><span data-stu-id="2fe15-123">Contained databases must be enabled on the instance of [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], before contained databases can be created.</span></span>  
  
### <a name="enabling-contained-databases-using-transact-sql"></a><span data-ttu-id="2fe15-124">使用 Transact-SQL 來啟用自主資料庫</span><span class="sxs-lookup"><span data-stu-id="2fe15-124">Enabling Contained Databases Using Transact-SQL</span></span>  
 <span data-ttu-id="2fe15-125">下列範例會在 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]執行個體上啟用自主資料庫。</span><span class="sxs-lookup"><span data-stu-id="2fe15-125">The following example enables contained databases on the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
```sql  
sp_configure 'contained database authentication', 1;  
GO  
RECONFIGURE ;  
GO  
```  
  
#### <a name="enabling-contained-databases-using-management-studio"></a><span data-ttu-id="2fe15-126">使用 Management Studio 來啟用自主資料庫</span><span class="sxs-lookup"><span data-stu-id="2fe15-126">Enabling Contained Databases Using Management Studio</span></span>  
 <span data-ttu-id="2fe15-127">下列範例會在 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]執行個體上啟用自主資料庫。</span><span class="sxs-lookup"><span data-stu-id="2fe15-127">The following example enables contained databases on the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
1.  <span data-ttu-id="2fe15-128">在物件總管中，以滑鼠右鍵按一下伺服器名稱，然後按一下 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="2fe15-128">In Object Explorer, right-click the server name, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="2fe15-129">在 [進階]  頁面的 [內含項目]  區段中，將 [啟用自主資料庫]  選項設定為 [True]  。</span><span class="sxs-lookup"><span data-stu-id="2fe15-129">On the **Advanced** page, in the **Containment** section, set the **Enable Contained Databases** option to **True**.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="converting-a-database-to-partially-contained"></a><a name="convert"></a> <span data-ttu-id="2fe15-130">將資料庫轉換成部分自主資料庫</span><span class="sxs-lookup"><span data-stu-id="2fe15-130">Converting a Database to Partially Contained</span></span>  
 <span data-ttu-id="2fe15-131">您可以透過變更 [內含項目]  選項，將資料庫轉換成自主資料庫。</span><span class="sxs-lookup"><span data-stu-id="2fe15-131">A database is converted to a contained database by changing the **CONTAINMENT** option.</span></span>  
  
### <a name="converting-a-database-to-partially-contained-using-transact-sql"></a><span data-ttu-id="2fe15-132">使用 Transact-SQL，將資料庫轉換成部分自主資料庫</span><span class="sxs-lookup"><span data-stu-id="2fe15-132">Converting a Database to Partially Contained Using Transact-SQL</span></span>  
 <span data-ttu-id="2fe15-133">下列範例會將名為 `Accounting` 的資料庫轉換成部分自主資料庫。</span><span class="sxs-lookup"><span data-stu-id="2fe15-133">The following example converts a database named `Accounting` to a partially contained database.</span></span>  
  
```sql  
USE [master]  
GO  
ALTER DATABASE [Accounting] SET CONTAINMENT = PARTIAL  
GO  
```  
  
### <a name="converting-a-database-to-partially-contained-using-management-studio"></a><span data-ttu-id="2fe15-134">使用 Management Studio，將資料庫轉換成部分自主資料庫</span><span class="sxs-lookup"><span data-stu-id="2fe15-134">Converting a Database to Partially contained Using Management Studio</span></span>  
 <span data-ttu-id="2fe15-135">下列範例會將資料庫轉換成部分自主資料庫。</span><span class="sxs-lookup"><span data-stu-id="2fe15-135">The following example converts a database to a partially contained database.</span></span>  
  
1.  <span data-ttu-id="2fe15-136">在物件總管中，展開 [資料庫]  ，以滑鼠右鍵按一下要轉換的資料庫，然後按一下 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="2fe15-136">In Object Explorer, expand **Databases**, right-click the database to be converted, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="2fe15-137">在 [選項]  頁面上，將 [內含項目類型]  選項變更為 [部分]  。</span><span class="sxs-lookup"><span data-stu-id="2fe15-137">On the **Options** page, change the **Containment type** option to **Partial**.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="migrating-users-to-contained-database-users"></a><a name="users"></a> <span data-ttu-id="2fe15-138">將使用者移轉至自主資料庫使用者</span><span class="sxs-lookup"><span data-stu-id="2fe15-138">Migrating Users to Contained Database Users</span></span>  
 <span data-ttu-id="2fe15-139">下列範例會將以 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入為基礎的所有使用者移轉至具有密碼之自主資料庫使用者。</span><span class="sxs-lookup"><span data-stu-id="2fe15-139">The following example migrates all users that are based on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins to contained database users with passwords.</span></span> <span data-ttu-id="2fe15-140">此範例會排除未啟用的登入。</span><span class="sxs-lookup"><span data-stu-id="2fe15-140">The example excludes logins that are not enabled.</span></span> <span data-ttu-id="2fe15-141">您必須在自主資料庫中執行此範例。</span><span class="sxs-lookup"><span data-stu-id="2fe15-141">The example must be executed in the contained database.</span></span>  
  
```sql  
DECLARE @username sysname ;  
DECLARE user_cursor CURSOR  
    FOR   
        SELECT dp.name   
        FROM sys.database_principals AS dp  
        JOIN sys.server_principals AS sp   
        ON dp.sid = sp.sid  
        WHERE dp.authentication_type = 1 AND sp.is_disabled = 0;  
OPEN user_cursor  
FETCH NEXT FROM user_cursor INTO @username  
    WHILE @@FETCH_STATUS = 0  
    BEGIN  
        EXECUTE sp_migrate_user_to_contained   
        @username = @username,  
        @rename = N'keep_name',  
        @disablelogin = N'disable_login';  
    FETCH NEXT FROM user_cursor INTO @username  
    END  
CLOSE user_cursor ;  
DEALLOCATE user_cursor ;  
```  
  
## <a name="see-also"></a><span data-ttu-id="2fe15-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2fe15-142">See Also</span></span>  
 <span data-ttu-id="2fe15-143">[自主資料庫](contained-databases.md) </span><span class="sxs-lookup"><span data-stu-id="2fe15-143">[Contained Databases](contained-databases.md) </span></span>  
 <span data-ttu-id="2fe15-144">[sp_migrate_user_to_contained &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-migrate-user-to-contained-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2fe15-144">[sp_migrate_user_to_contained &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-migrate-user-to-contained-transact-sql) </span></span>  
 [<span data-ttu-id="2fe15-145">sys.dm_db_uncontained_entities &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2fe15-145">sys.dm_db_uncontained_entities &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-uncontained-entities-transact-sql)  
  
  
