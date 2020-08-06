---
title: 啟用 FileTable 的必要條件 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], prerequisites
ms.assetid: 6286468c-9dc9-4eda-9961-071d2a36ebd6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5d5d2c5dab7909ec5403911d482823f488cdd809
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584591"
---
# <a name="enable-the-prerequisites-for-filetable"></a><span data-ttu-id="bbcfc-102">啟用 FileTable 的必要條件</span><span class="sxs-lookup"><span data-stu-id="bbcfc-102">Enable the Prerequisites for FileTable</span></span>
  <span data-ttu-id="bbcfc-103">描述如何啟用建立和使用 FileTable 的必要元件。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-103">Describes how to enable the prerequisites for creating and using FileTables.</span></span>  
  
##  <a name="enabling-the-prerequisites-for-filetable"></a><a name="EnablePrereq"></a> <span data-ttu-id="bbcfc-104">啟用 FileTable 的必要條件</span><span class="sxs-lookup"><span data-stu-id="bbcfc-104">Enabling the Prerequisites for FileTable</span></span>  
 <span data-ttu-id="bbcfc-105">若要啟用建立和使用 FileTable 的必要條件，請啟用下列項目：</span><span class="sxs-lookup"><span data-stu-id="bbcfc-105">To enable the prerequisites for creating and using FileTables, enable the following items:</span></span>  
  
-   <span data-ttu-id="bbcfc-106">**於執行個體層級：**</span><span class="sxs-lookup"><span data-stu-id="bbcfc-106">**At the instance level:**</span></span>  
  
    -   [<span data-ttu-id="bbcfc-107">在執行個體層級啟用 FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="bbcfc-107">Enabling FILESTREAM at the Instance Level</span></span>](#BasicsFilestream)  
  
-   <span data-ttu-id="bbcfc-108">**於資料庫層級：**</span><span class="sxs-lookup"><span data-stu-id="bbcfc-108">**At the database level:**</span></span>  
  
    -   [<span data-ttu-id="bbcfc-109">在資料庫層級提供 FILESTREAM 檔案群組</span><span class="sxs-lookup"><span data-stu-id="bbcfc-109">Providing a FILESTREAM Filegroup at the Database Level</span></span>](#filegroup)  
  
    -   [<span data-ttu-id="bbcfc-110">在資料庫層級啟用非交易式存取</span><span class="sxs-lookup"><span data-stu-id="bbcfc-110">Enabling Non-Transactional Access at the Database Level</span></span>](#BasicsNTAccess)  
  
    -   [<span data-ttu-id="bbcfc-111">在資料庫層級指定 FileTable 的目錄</span><span class="sxs-lookup"><span data-stu-id="bbcfc-111">Specifying a Directory for FileTables at the Database Level</span></span>](#BasicsDirectory)  
  
##  <a name="enabling-filestream-at-the-instance-level"></a><a name="BasicsFilestream"></a> <span data-ttu-id="bbcfc-112">在執行個體層級啟用 FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="bbcfc-112">Enabling FILESTREAM at the Instance Level</span></span>  
 <span data-ttu-id="bbcfc-113">FileTable 會擴充 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]之 FILESTREAM 功能的能力。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-113">FileTables extend the capabilities of the FILESTREAM feature of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bbcfc-114">因此，您必須先在 Windows 層級和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上啟用 FILESTREAM 的檔案 I/O 存取，然後才能建立和使用 FileTable。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-114">Therefore you have to enable FILESTREAM for file I/O access at the Windows level and on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before you can create and use FileTables.</span></span>  
  
###  <a name="how-to-enable-filestream-at-the-instance-level"></a><a name="HowToFilestream"></a> <span data-ttu-id="bbcfc-115">如何：在執行個體層級啟用 FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="bbcfc-115">How To: Enable FILESTREAM at the Instance Level</span></span>  
 <span data-ttu-id="bbcfc-116">如需如何啟用 FILESTREAM 的相關資訊，請參閱 [啟用及設定 FILESTREAM](enable-and-configure-filestream.md)。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-116">For information about how to enable FILESTREAM, see [Enable and Configure FILESTREAM](enable-and-configure-filestream.md).</span></span>  
  
 <span data-ttu-id="bbcfc-117">當您呼叫 `sp_configure` 在執行個體層級啟用 FILESTREAM 時，必須將 filestream_access_level 選項設定為 2。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-117">When you call `sp_configure` to enable FILESTREAM at the instance level, you have to set the filestream_access_level option to 2.</span></span> <span data-ttu-id="bbcfc-118">如需詳細資訊，請參閱 [Filestream 存取層級伺服器組態選項](../../database-engine/configure-windows/filestream-access-level-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-118">For more information, see [filestream access level Server Configuration Option](../../database-engine/configure-windows/filestream-access-level-server-configuration-option.md).</span></span>  
  
###  <a name="how-to-allow-filestream-through-the-firewall"></a><a name="firewall"></a> <span data-ttu-id="bbcfc-119">如何：允許 FILESTREAM 通過防火牆</span><span class="sxs-lookup"><span data-stu-id="bbcfc-119">How To: Allow FILESTREAM through the Firewall</span></span>  
 <span data-ttu-id="bbcfc-120">如需有關如何允許 FILESTREAM 通過防火牆的詳細資訊，請參閱＜ [Configure a Firewall for FILESTREAM Access](configure-a-firewall-for-filestream-access.md)＞。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-120">For information about how to allow FILESTREAM through the firewall, see [Configure a Firewall for FILESTREAM Access](configure-a-firewall-for-filestream-access.md).</span></span>  
  
##  <a name="providing-a-filestream-filegroup-at-the-database-level"></a><a name="filegroup"></a> <span data-ttu-id="bbcfc-121">在資料庫層級提供 FILESTREAM 檔案群組</span><span class="sxs-lookup"><span data-stu-id="bbcfc-121">Providing a FILESTREAM Filegroup at the Database Level</span></span>  
 <span data-ttu-id="bbcfc-122">資料庫必須具有 FILESTREAM 檔案群組，然後您才能在該資料庫中建立 FileTable。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-122">Before you can create FileTables in a database, the database must have a FILESTREAM filegroup.</span></span> <span data-ttu-id="bbcfc-123">如需此必要條件的詳細資訊，請參閱 [建立啟用 FILESTREAM 的資料庫](create-a-filestream-enabled-database.md)。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-123">For more information about this prerequisite, see [Create a FILESTREAM-Enabled Database](create-a-filestream-enabled-database.md).</span></span>  
  
##  <a name="enabling-non-transactional-access-at-the-database-level"></a><a name="BasicsNTAccess"></a> <span data-ttu-id="bbcfc-124">在資料庫層級啟用非交易式存取</span><span class="sxs-lookup"><span data-stu-id="bbcfc-124">Enabling Non-Transactional Access at the Database Level</span></span>  
 <span data-ttu-id="bbcfc-125">FileTable 可讓 Windows 應用程式取得 FILESTREAM 資料的 Windows 檔案控制代碼，而不需要使用交易。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-125">FileTables let Windows applications obtain a Windows file handle to FILESTREAM data without requiring a transaction.</span></span> <span data-ttu-id="bbcfc-126">若要允許對儲存在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中的檔案進行這種非交易式存取，您必須針對將包含 FileTable 的每個資料庫，指定在資料庫層級啟用非交易式存取的所需層級。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-126">To allow this non-transactional access to files stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you have to specify the desired level of non-transactional access at the database level for each database that will contain FileTables.</span></span>  
  
###  <a name="how-to-check-whether-non-transactional-access-is-enabled-on-databases"></a><a name="HowToCheckAccess"></a> <span data-ttu-id="bbcfc-127">如何：檢查是否已在資料庫上啟用非交易式存取</span><span class="sxs-lookup"><span data-stu-id="bbcfc-127">How To: Check Whether Non-Transactional Access Is Enabled on Databases</span></span>  
 <span data-ttu-id="bbcfc-128">查詢 [sys.database_filestream_options &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql) 目錄檢視，並檢查 **non_transacted_access** 和 **non_transacted_access_desc** 資料行。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-128">Query the catalog view [sys.database_filestream_options &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql) and check the **non_transacted_access** and **non_transacted_access_desc** columns.</span></span>  
  
```sql  
SELECT DB_NAME(database_id), non_transacted_access, non_transacted_access_desc  
    FROM sys.database_filestream_options;  
GO  
```  
  
###  <a name="how-to-enable-non-transactional-access-at-the-database-level"></a><a name="HowToNTAccess"></a> <span data-ttu-id="bbcfc-129">如何：在資料庫層級啟用非交易式存取</span><span class="sxs-lookup"><span data-stu-id="bbcfc-129">How To: Enable Non-Transactional Access at the Database Level</span></span>  
 <span data-ttu-id="bbcfc-130">非交易式存取的可用層級是 FULL、READ_ONLY 和 OFF。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-130">The available levels of non-transactional access are FULL, READ_ONLY, and OFF.</span></span>  
  
 <span data-ttu-id="bbcfc-131">**使用 Transact-SQL 指定非交易式存取的層級**</span><span class="sxs-lookup"><span data-stu-id="bbcfc-131">**Specify the level of non-transactional access by using Transact-SQL**</span></span>  
 -   <span data-ttu-id="bbcfc-132">**建立新資料庫**時，請使用 **NON_TRANSACTED_ACCESS** FILESTREAM 選項，呼叫 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-132">When you **create a new database**, call the [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) statement with the **NON_TRANSACTED_ACCESS** FILESTREAM option.</span></span>  
  
    ```sql  
    CREATE DATABASE database_name  
        WITH FILESTREAM ( NON_TRANSACTED_ACCESS = FULL, DIRECTORY_NAME = N'directory_name' )  
    ```  
  
-   <span data-ttu-id="bbcfc-133">**改變現有資料庫**時，請使用 **NON_TRANSACTED_ACCESS** FILESTREAM 選項，呼叫 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-133">When you **alter an existing database**, call the [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) statement with the **NON_TRANSACTED_ACCESS** FILESTREAM option.</span></span>  
  
    ```sql  
    ALTER DATABASE database_name  
        SET FILESTREAM ( NON_TRANSACTED_ACCESS = FULL, DIRECTORY_NAME = N'directory_name' )  
    ```  
  
 <span data-ttu-id="bbcfc-134">**使用 SQL Server Management Studio 指定非交易式存取的層級**</span><span class="sxs-lookup"><span data-stu-id="bbcfc-134">**Specify the level of non-transactional access by using SQL Server Management Studio**</span></span>  
 <span data-ttu-id="bbcfc-135">在 [資料庫屬性]  對話方塊中，您可以透過 [選項]  頁面的 [FILESTREAM 非交易式存取]  欄位，來指定非交易式存取的層級。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-135">You can specify the level of non-transactional access in the **FILESTREAM Non-transacted Access** field of the **Options** page of the **Database Properties** dialog box.</span></span> <span data-ttu-id="bbcfc-136">如需此對話方塊的詳細資訊，請參閱[資料庫屬性 &#40;選項頁面&#41;](../databases/database-properties-options-page.md)。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-136">For more information about this dialog box, see [Database Properties &#40;Options Page&#41;](../databases/database-properties-options-page.md).</span></span>  
  
##  <a name="specifying-a-directory-for-filetables-at-the-database-level"></a><a name="BasicsDirectory"></a> <span data-ttu-id="bbcfc-137">在資料庫層級指定 FileTable 的目錄</span><span class="sxs-lookup"><span data-stu-id="bbcfc-137">Specifying a Directory for FileTables at the Database Level</span></span>  
 <span data-ttu-id="bbcfc-138">當您在資料庫層級啟用檔案的非交易式存取時，可以選擇性地使用 **DIRECTORY_NAME** 選項，一併提供目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-138">When you enable non-transactional access to files at the database level, you can optionally provide a directory name at the same time by using the **DIRECTORY_NAME** option.</span></span> <span data-ttu-id="bbcfc-139">如果您在啟用非交易式存取時沒有提供目錄名稱，則之後必須先提供此名稱，然後才能在資料庫中建立 FileTable。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-139">If you do not provide a directory name when you enable non-transactional access, then you have to provide it later before you can create FileTables in the database.</span></span>  
  
 <span data-ttu-id="bbcfc-140">在 FileTable 資料夾階層中，這個資料庫層級目錄會成為在執行個體層級中針對 FILESTREAM 指定之共用名稱的子系，以及在資料庫中建立之 FileTable 的父系。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-140">In the FileTable folder hierarchy, this database-level directory becomes the child of the share name specified for FILESTREAM at the instance level, and the parent of the FileTables created in the database.</span></span> <span data-ttu-id="bbcfc-141">如需詳細資訊，請參閱 [Work with Directories and Paths in FileTables](work-with-directories-and-paths-in-filetables.md)。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-141">For more information, see [Work with Directories and Paths in FileTables](work-with-directories-and-paths-in-filetables.md).</span></span>  
  
###  <a name="how-to-specify-a-directory-for-filetables-at-the-database-level"></a><a name="HowToDirectory"></a> <span data-ttu-id="bbcfc-142">如何：在資料庫層級指定 FileTable 的目錄</span><span class="sxs-lookup"><span data-stu-id="bbcfc-142">How To: Specify a Directory for FileTables at the Database Level</span></span>  
 <span data-ttu-id="bbcfc-143">跨資料庫層級目錄的執行個體中，指定的名稱必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-143">The name that you specify must be unique across the instance for database-level directories.</span></span>  
  
 <span data-ttu-id="bbcfc-144">**使用 Transact-SQL 指定 FileTable 的目錄**</span><span class="sxs-lookup"><span data-stu-id="bbcfc-144">**Specify a directory for FileTables by using Transact-SQL**</span></span>  
 -   <span data-ttu-id="bbcfc-145">**建立新資料庫**時，請使用 **DIRECTORY_NAME** FILESTREAM 選項，呼叫 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-145">When you **create a new database**, call the [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) statement with the **DIRECTORY_NAME** FILESTREAM option.</span></span>  
  
    ```sql  
    CREATE DATABASE database_name  
        WITH FILESTREAM ( NON_TRANSACTED_ACCESS = FULL, DIRECTORY_NAME = N'directory_name' );  
    GO  
    ```  
  
-   <span data-ttu-id="bbcfc-146">**改變現有資料庫**時，請使用 **DIRECTORY_NAME** FILESTREAM 選項，呼叫 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-146">When you **alter an existing database**, call the [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) statement with the **DIRECTORY_NAME** FILESTREAM option.</span></span> <span data-ttu-id="bbcfc-147">當您使用這些選項來變更目錄名稱時，資料庫必須獨佔鎖定，而且沒有任何開啟的檔案控制代碼。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-147">When you use these options to change the directory name, the database must be exclusively locked, with no open file handles.</span></span>  
  
    ```sql  
    ALTER DATABASE database_name  
        SET FILESTREAM ( NON_TRANSACTED_ACCESS = FULL, DIRECTORY_NAME = N'directory_name' );  
    GO  
    ```  
  
-   <span data-ttu-id="bbcfc-148">**附加資料庫**時，請使用 **FOR ATTACH** 選項和 **DIRECTORY_NAME** FILESTREAM 選項，呼叫 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-148">When you **attach a database**, call the [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) statement with the **FOR ATTACH** option and with the **DIRECTORY_NAME** FILESTREAM option.</span></span>  
  
    ```sql  
    CREATE DATABASE database_name  
        FOR ATTACH WITH FILESTREAM ( DIRECTORY_NAME = N'directory_name' );  
    GO  
    ```  
  
-   <span data-ttu-id="bbcfc-149">**還原資料庫**時，請使用 **DIRECTORY_NAME** FILESTREAM 選項，呼叫 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-149">When you **restore a database**, call the [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) statement with the **DIRECTORY_NAME** FILESTREAM option.</span></span>  
  
    ```sql  
    RESTORE DATABASE database_name  
        WITH FILESTREAM ( DIRECTORY_NAME = N'directory_name' );  
    GO  
    ```  
  
 <span data-ttu-id="bbcfc-150">**使用 SQL Server Management Studio 指定 FileTable 的目錄**</span><span class="sxs-lookup"><span data-stu-id="bbcfc-150">**Specify a directory for FileTables by using SQL Server Management Studio**</span></span>  
 <span data-ttu-id="bbcfc-151">在 [資料庫屬性]  對話方塊中，您可以透過 [選項]  頁面的 [FILESTREAM 目錄名稱]  欄位，來指定目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-151">You can specify a directory name in the **FILESTREAM Directory Name** field of the **Options** page of the **Database Properties** dialog box.</span></span> <span data-ttu-id="bbcfc-152">如需此對話方塊的詳細資訊，請參閱[資料庫屬性 &#40;選項頁面&#41;](../databases/database-properties-options-page.md)。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-152">For more information about this dialog box, see [Database Properties &#40;Options Page&#41;](../databases/database-properties-options-page.md).</span></span>  
  
###  <a name="how-to-view-existing-directory-names-for-the-instance"></a><a name="viewnames"></a> <span data-ttu-id="bbcfc-153">如何：檢視執行個體的現有目錄名稱</span><span class="sxs-lookup"><span data-stu-id="bbcfc-153">How to: View Existing Directory Names for the Instance</span></span>  
 <span data-ttu-id="bbcfc-154">若要檢視執行個體的現有目錄名稱清單，請查詢 [sys.database_filestream_options &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql) 目錄檢視，並檢查 **filestream_database_directory_name** 資料行。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-154">To view the list of existing directory names for the instance, query the catalog view [sys.database_filestream_options &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql) and check the **filestream_database_directory_name** column.</span></span>  
  
```sql  
SELECT DB_NAME ( database_id ), directory_name  
    FROM sys.database_filestream_options;  
GO  
```  
  
###  <a name="requirements-and-restrictions-for-the-database-level-directory"></a><a name="ReqDirectory"></a> <span data-ttu-id="bbcfc-155">資料庫層級目錄的需求和限制</span><span class="sxs-lookup"><span data-stu-id="bbcfc-155">Requirements and Restrictions for the Database-Level Directory</span></span>  
  
-   <span data-ttu-id="bbcfc-156">當您呼叫 **CREATE DATABASE** 或 **ALTER DATABASE** 時， **DIRECTORY_NAME**是選擇性設定。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-156">Setting the **DIRECTORY_NAME** is optional when you call **CREATE DATABASE** or **ALTER DATABASE**.</span></span> <span data-ttu-id="bbcfc-157">如果您沒有指定 **DIRECTORY_NAME**的值，則目錄名稱會維持 Null。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-157">If you do not specify a value for **DIRECTORY_NAME**, then the directory name remains null.</span></span> <span data-ttu-id="bbcfc-158">不過，如果您未在資料庫層級中指定 **DIRECTORY_NAME** 的值，就無法在資料庫中建立 FileTable。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-158">However you cannot create FileTables in the database until you specify a value for **DIRECTORY_NAME** at the database level.</span></span>  
  
-   <span data-ttu-id="bbcfc-159">您所提供的目錄名稱必須符合有效目錄名稱的檔案系統需求。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-159">The directory name that you provide must comply with the requirements of the file system for a valid directory name.</span></span>  
  
-   <span data-ttu-id="bbcfc-160">當資料庫包含 FileTable 時，您無法將 **DIRECTORY_NAME** 設定回 Null 值。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-160">When the database contains FileTables, you cannot set the **DIRECTORY_NAME** back to a null value.</span></span>  
  
-   <span data-ttu-id="bbcfc-161">當您附加或還原資料庫時，如果新的資料庫具有已經存在目標執行個體中的 **DIRECTORY_NAME** 值，此作業就會失敗。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-161">When you attach or restore a database, the operation fails if the new database has a value for **DIRECTORY_NAME** that already exists in the target instance.</span></span> <span data-ttu-id="bbcfc-162">因此，當您呼叫 **CREATE DATABASE FOR ATTACH** 或 **RESTORE DATABASE** 時，請針對 **DIRECTORY_NAME**指定唯一的值。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-162">Specify a unique value for **DIRECTORY_NAME** when you call **CREATE DATABASE FOR ATTACH** or **RESTORE DATABASE**.</span></span>  
  
-   <span data-ttu-id="bbcfc-163">當您將現有的資料庫升級為 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]時， **DIRECTORY_NAME** 的值為 Null。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-163">When you upgrade an existing database to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the value of **DIRECTORY_NAME** is null.</span></span>  
  
-   <span data-ttu-id="bbcfc-164">當您在資料庫層級中啟用或停用非交易式存取時，此作業不會檢查是否已經指定目錄名稱，或者目錄名稱是否唯一。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-164">When you enable or disable non-transactional access at the database level, the operation does not check whether the directory name has been specified or whether it is unique.</span></span>  
  
-   <span data-ttu-id="bbcfc-165">當您卸除已針對 FileTable 啟用的資料庫時，會一併移除資料庫層級目錄和其下所有 FileTable 的所有目錄結構。</span><span class="sxs-lookup"><span data-stu-id="bbcfc-165">When you drop a database that was enabled for FileTables, the database-level directory and all the directory stuctures of all the FileTables under it are removed.</span></span>  
  
  
