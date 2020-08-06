---
title: 建立、改變及卸除 FileTable | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], altering
- FileTables [SQL Server], dropping
- FileTables [SQL Server], creating
ms.assetid: 47d69e37-8778-4630-809b-2261b5c41c2c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3a10e6333f6dd38a850a832b82a7cb7a0e0bf698
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592070"
---
# <a name="create-alter-and-drop-filetables"></a><span data-ttu-id="341f9-102">建立、改變及卸除 FileTable</span><span class="sxs-lookup"><span data-stu-id="341f9-102">Create, Alter, and Drop FileTables</span></span>
  <span data-ttu-id="341f9-103">描述如何建立新的 FileTable，或是改變或卸除現有的 FileTable。</span><span class="sxs-lookup"><span data-stu-id="341f9-103">Describes how to create a new FileTable, or alter or drop an existing FileTable.</span></span>  
  
##  <a name="creating-a-filetable"></a><a name="BasicsCreate"></a> <span data-ttu-id="341f9-104">建立 FileTable</span><span class="sxs-lookup"><span data-stu-id="341f9-104">Creating a FileTable</span></span>  
 <span data-ttu-id="341f9-105">FileTable 是一種特殊化使用者資料表，它具有預先定義且固定的結構描述。</span><span class="sxs-lookup"><span data-stu-id="341f9-105">A FileTable is a specialized user table that has a pre-defined and fixed schema.</span></span> <span data-ttu-id="341f9-106">這個結構描述會儲存 FILESTREAM 資料、檔案和目錄資訊，以及檔案屬性。</span><span class="sxs-lookup"><span data-stu-id="341f9-106">This schema stores FILESTREAM data, file and directory information, and file attributes.</span></span> <span data-ttu-id="341f9-107">如需有關 FileTable 結構描述的詳細資訊，請參閱＜ [FileTable Schema](filetable-schema.md)＞。</span><span class="sxs-lookup"><span data-stu-id="341f9-107">For information about the FileTable schema, see [FileTable Schema](filetable-schema.md).</span></span>  
  
 <span data-ttu-id="341f9-108">您可以使用 Transact-SQL 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]來建立新的 FileTable。</span><span class="sxs-lookup"><span data-stu-id="341f9-108">You can create a new FileTable by using Transact-SQL or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="341f9-109">因為 FileTable 具有固定的結構描述，所以您不需要指定資料行的清單。</span><span class="sxs-lookup"><span data-stu-id="341f9-109">Since a FileTable has a fixed schema, you do not have to specify a list of columns.</span></span> <span data-ttu-id="341f9-110">用於建立 FileTable 的簡單語法可讓您指定：</span><span class="sxs-lookup"><span data-stu-id="341f9-110">The simple syntax for creating a FileTable lets you specify:</span></span>  
  
-   <span data-ttu-id="341f9-111">目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="341f9-111">A directory name.</span></span> <span data-ttu-id="341f9-112">在 FileTable 資料夾階層中，這個資料表層級目錄會成為在資料庫層級中指定之資料庫目錄的子系，以及儲存在資料表中之檔案或目錄的父系。</span><span class="sxs-lookup"><span data-stu-id="341f9-112">In the FileTable folder hierarchy, this table-level directory becomes the child of the database directory specified at the database level, and the parent of the files or directories stored in the table.</span></span>  
  
-   <span data-ttu-id="341f9-113">要用於 FileTable **Name** 資料行中之檔案名稱的定序名稱。</span><span class="sxs-lookup"><span data-stu-id="341f9-113">The name of the collation to be used for file names in the **Name** column of the FileTable.</span></span>  
  
-   <span data-ttu-id="341f9-114">要用於 3 個自動建立的主索引鍵條件約束和唯一條件約束的名稱。</span><span class="sxs-lookup"><span data-stu-id="341f9-114">The names to be used for the 3 primary key and unique constraints that are automatically created.</span></span>  
  
###  <a name="how-to-create-a-filetable"></a><a name="HowToCreate"></a> <span data-ttu-id="341f9-115">如何：建立 FileTable</span><span class="sxs-lookup"><span data-stu-id="341f9-115">How To: Create a FileTable</span></span>  
 <span data-ttu-id="341f9-116">**使用 Transact-SQL 建立 FileTable**</span><span class="sxs-lookup"><span data-stu-id="341f9-116">**Create a FileTable by Using Transact-SQL**</span></span>  
 <span data-ttu-id="341f9-117">您可以使用 **AS FileTable** 選項來呼叫 [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) 陳述式，藉以建立 FileTable。</span><span class="sxs-lookup"><span data-stu-id="341f9-117">Create a FileTable by calling the [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) statement with the **AS FileTable** option.</span></span> <span data-ttu-id="341f9-118">因為 FileTable 具有固定的結構描述，所以您不需要指定資料行的清單。</span><span class="sxs-lookup"><span data-stu-id="341f9-118">Since a FileTable has a fixed schema, you do not have to specify a list of columns.</span></span> <span data-ttu-id="341f9-119">您可以針對新的 FileTable 指定下列設定：</span><span class="sxs-lookup"><span data-stu-id="341f9-119">You can specify the following settings for the new FileTable:</span></span>  
  
1.  <span data-ttu-id="341f9-120">**FILETABLE_DIRECTORY**。</span><span class="sxs-lookup"><span data-stu-id="341f9-120">**FILETABLE_DIRECTORY**.</span></span> <span data-ttu-id="341f9-121">指定目錄，以做為 FileTable 中儲存之所有檔案和目錄的根目錄。</span><span class="sxs-lookup"><span data-stu-id="341f9-121">Specifies the directory that serves as the root directory for all the files and directories stored in the FileTable.</span></span> <span data-ttu-id="341f9-122">在資料庫的所有 FileTable 目錄名稱之間，此名稱必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="341f9-122">This name should be unique among all the FileTable directory names in the database.</span></span> <span data-ttu-id="341f9-123">不論目前的定序設定為何，唯一性的比較都不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="341f9-123">Comparison for uniqueness is case-insensitive, regardless of the current collation settings.</span></span>  
  
    -   <span data-ttu-id="341f9-124">此值的資料類型為 **nvarchar(255)** ，並使用 **Latin1_General_CI_AS_KS_WS**的固定定序。</span><span class="sxs-lookup"><span data-stu-id="341f9-124">This value has a data type of **nvarchar(255)** and uses a fixed collation of **Latin1_General_CI_AS_KS_WS**.</span></span>  
  
    -   <span data-ttu-id="341f9-125">您所提供的目錄名稱必須符合有效目錄名稱的檔案系統需求。</span><span class="sxs-lookup"><span data-stu-id="341f9-125">The directory name that you provide must comply with the requirements of the file system for a valid directory name.</span></span>  
  
    -   <span data-ttu-id="341f9-126">在資料庫的所有 FileTable 目錄名稱之間，此名稱必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="341f9-126">This name should be unique among all the FileTable directory names in the database.</span></span> <span data-ttu-id="341f9-127">不論目前的定序設定為何，唯一性的比較都不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="341f9-127">Comparison for uniqueness is case-insensitive, regardless of the current collation settings.</span></span>  
  
    -   <span data-ttu-id="341f9-128">如果您在建立 FileTable 時未提供目錄名稱，則會使用 FileTable 本身的名稱做為目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="341f9-128">If you do not provide a directory name when you create the FileTable, then the name of the FileTable itself is used as the directory name.</span></span>  
  
2.  <span data-ttu-id="341f9-129">**FILETABLE_COLLATE_FILENAME**。</span><span class="sxs-lookup"><span data-stu-id="341f9-129">**FILETABLE_COLLATE_FILENAME**.</span></span> <span data-ttu-id="341f9-130">指定定序名稱，用於套用至 FileTable 中的 **Name** 資料行。</span><span class="sxs-lookup"><span data-stu-id="341f9-130">Specifies the name of the collation to be applied to the **Name** column in the FileTable.</span></span>  
  
    1.  <span data-ttu-id="341f9-131">指定的定序必須 **不區分大小寫** ，以符合 Windows 檔案命名語意。</span><span class="sxs-lookup"><span data-stu-id="341f9-131">The specified collation must be **case-insensitive** to comply with Windows file naming semantics.</span></span>  
  
    2.  <span data-ttu-id="341f9-132">如果您未提供 **FILETABLE_COLLATE_FILENAME**的值，或指定 **database_default**，則資料行會繼承目前資料庫的定序。</span><span class="sxs-lookup"><span data-stu-id="341f9-132">If you do not provide a value for **FILETABLE_COLLATE_FILENAME**, or you specify **database_default**, the column inherits the collation of the current database.</span></span> <span data-ttu-id="341f9-133">如果目前的資料庫定序區分大小寫，則會引發錯誤，而且 **CREATE TABLE** 作業會失敗。</span><span class="sxs-lookup"><span data-stu-id="341f9-133">If the current database collation is case-sensitive, an error is raised and the **CREATE TABLE** operation fails.</span></span>  
  
3.  <span data-ttu-id="341f9-134">您也可以指定要用於 3 個自動建立的主索引鍵條件約束和唯一條件約束的名稱。</span><span class="sxs-lookup"><span data-stu-id="341f9-134">You can also specify the names to be used for the 3 primary key and unique constraints that are automatically created.</span></span> <span data-ttu-id="341f9-135">如果您未提供名稱，則系統會產生名稱，如本主題稍後所述。</span><span class="sxs-lookup"><span data-stu-id="341f9-135">If you do not provide names, then the system generates names as described later in this topic.</span></span>  
  
    -   <span data-ttu-id="341f9-136">**FILETABLE_PRIMARY_KEY_CONSTRAINT_NAME**</span><span class="sxs-lookup"><span data-stu-id="341f9-136">**FILETABLE_PRIMARY_KEY_CONSTRAINT_NAME**</span></span>  
  
    -   <span data-ttu-id="341f9-137">**FILETABLE_STREAMID_UNIQUE_CONSTRAINT_NAME**</span><span class="sxs-lookup"><span data-stu-id="341f9-137">**FILETABLE_STREAMID_UNIQUE_CONSTRAINT_NAME**</span></span>  
  
    -   <span data-ttu-id="341f9-138">**FILETABLE_FULLPATH_UNIQUE_CONSTRAINT_NAME**</span><span class="sxs-lookup"><span data-stu-id="341f9-138">**FILETABLE_FULLPATH_UNIQUE_CONSTRAINT_NAME**</span></span>  
  
 <span data-ttu-id="341f9-139">**範例**</span><span class="sxs-lookup"><span data-stu-id="341f9-139">**Examples**</span></span>  
  
 <span data-ttu-id="341f9-140">下列範例會建立新的 FileTable，並指定 **FILETABLE_DIRECTORY** 和 **FILETABLE_COLLATE_FILENAME**的使用者定義值。</span><span class="sxs-lookup"><span data-stu-id="341f9-140">The following example creates a new FileTable and specifies user-defined values for both **FILETABLE_DIRECTORY** and **FILETABLE_COLLATE_FILENAME**.</span></span>  
  
```sql  
CREATE TABLE DocumentStore AS FileTable  
    WITH (   
          FileTable_Directory = 'DocumentTable',  
          FileTable_Collate_Filename = database_default  
         );  
GO  
```  
  
 <span data-ttu-id="341f9-141">下列範例也會建立新的 FileTable。</span><span class="sxs-lookup"><span data-stu-id="341f9-141">The following example also creates a new FileTable.</span></span> <span data-ttu-id="341f9-142">因為未指定使用者定義值，所以 **FILETABLE_DIRECTORY** 的值會成為 FileTable 的名稱， **FILETABLE_COLLATE_FILENAME** 的值會成為 database_default，而主索引鍵和唯一條件約束則會接受系統產生的名稱。</span><span class="sxs-lookup"><span data-stu-id="341f9-142">Since user-defined values are not specified, the value of **FILETABLE_DIRECTORY** becomes the name of the FileTable, the value of **FILETABLE_COLLATE_FILENAME** becomes database_default, and the primary key and unique contraints receive system-generated names.</span></span>  
  
```sql  
CREATE TABLE DocumentStore AS FileTable;  
GO  
```  
  
 <span data-ttu-id="341f9-143">**使用 SQL Server Management Studio 建立 FileTable**</span><span class="sxs-lookup"><span data-stu-id="341f9-143">**Create a FileTable by Using SQL Server Management Studio**</span></span>  
 <span data-ttu-id="341f9-144">在物件總管中，展開選取之資料庫底下的物件、以滑鼠右鍵按一下 [資料表] 資料夾，然後選取 [New FileTable (新增 FileTable)]。</span><span class="sxs-lookup"><span data-stu-id="341f9-144">In Object Explorer, expand the objects under the selected database, then right-click on the **Tables** folder, and then select **New FileTable**.</span></span>  
  
 <span data-ttu-id="341f9-145">此選項會開啟新的指令碼視窗，其中包含您可以自訂及執行以建立 FileTable 的 Transact-SQL 指令碼範本。</span><span class="sxs-lookup"><span data-stu-id="341f9-145">This option opens a new script window which contains a Transact-SQL script template that you can customize and run to create a FileTable.</span></span> <span data-ttu-id="341f9-146">使用 **[查詢]** 功能表上的 **[指定範本參數的值]** 選項，輕鬆地自訂指令碼。</span><span class="sxs-lookup"><span data-stu-id="341f9-146">Use the **Specify Values for Template Parameters** option on the **Query** menu to customize the script easily.</span></span>  
  
###  <a name="requirements-and-restrictions-for-creating-a-filetable"></a><a name="ReqCreate"></a> <span data-ttu-id="341f9-147">建立 FileTable 的需求和限制</span><span class="sxs-lookup"><span data-stu-id="341f9-147">Requirements and Restrictions for Creating a FileTable</span></span>  
  
-   <span data-ttu-id="341f9-148">您無法改變現有的資料表，以便將它轉換成 FileTable。</span><span class="sxs-lookup"><span data-stu-id="341f9-148">You cannot alter an existing table to convert it into a FileTable.</span></span>  
  
-   <span data-ttu-id="341f9-149">先前在資料庫層級中指定的上層目錄必須具有非 Null 值。</span><span class="sxs-lookup"><span data-stu-id="341f9-149">The parent directory previously specified at the database level must have a non-null value.</span></span> <span data-ttu-id="341f9-150">如需指定資料庫層級目錄的相關資訊，請參閱 [啟用 FileTable 的必要條件](enable-the-prerequisites-for-filetable.md)。</span><span class="sxs-lookup"><span data-stu-id="341f9-150">For information about specifying the database-level directory, see [Enable the Prerequisites for FileTable](enable-the-prerequisites-for-filetable.md).</span></span>  
  
-   <span data-ttu-id="341f9-151">因為 FileTable 包含 FILESTREAM 資料行，所以 FileTable 需要使用有效的 FILESTREAM 檔案群組。</span><span class="sxs-lookup"><span data-stu-id="341f9-151">A FileTable requires a valid FILESTREAM filegroup, since a FileTable contains a FILESTREAM column.</span></span> <span data-ttu-id="341f9-152">您可以選擇性地指定有效的 FILESTREAM 檔案群組，當做建立 FileTable 之 **CREATE TABLE** 命令的一部分。</span><span class="sxs-lookup"><span data-stu-id="341f9-152">You can optionally specify a valid FILESTREAM filegroup as part of the **CREATE TABLE** command for creating a FileTable.</span></span> <span data-ttu-id="341f9-153">如果您沒有指定檔案群組，則 FileTable 就會使用資料庫的預設 FILESTREAM 檔案群組。</span><span class="sxs-lookup"><span data-stu-id="341f9-153">If you do not specify a filegroup, then the FileTable uses the default FILESTREAM filegroup for the database.</span></span> <span data-ttu-id="341f9-154">如果資料庫沒有 FILESTREAM 檔案群組，則系統會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="341f9-154">If the database does not have a FILESTREAM filegroup, then an error is raised.</span></span>  
  
-   <span data-ttu-id="341f9-155">您無法將資料表條件約束建立成 **CREATE TABLE…AS FILETABLE** 陳述式的一部分。</span><span class="sxs-lookup"><span data-stu-id="341f9-155">You cannot create a table constraint as part of a **CREATE TABLE...AS FILETABLE** statement.</span></span> <span data-ttu-id="341f9-156">不過，您之後可以使用 **ALTER TABLE** 陳述式來加入條件約束。</span><span class="sxs-lookup"><span data-stu-id="341f9-156">However you can add the constraint later by using an **ALTER TABLE** statement.</span></span>  
  
-   <span data-ttu-id="341f9-157">您無法在 **tempdb** 資料庫或任何其他系統資料庫中建立 FileTable。</span><span class="sxs-lookup"><span data-stu-id="341f9-157">You cannot create a FileTable in the **tempdb** database or in any of the other system databases.</span></span>  
  
-   <span data-ttu-id="341f9-158">您無法將 FileTable 建立成暫存資料表。</span><span class="sxs-lookup"><span data-stu-id="341f9-158">You cannot create a FileTable as a temporary table.</span></span>  
  
##  <a name="altering-a-filetable"></a><a name="BasicsAlter"></a> <span data-ttu-id="341f9-159">改變 FileTable</span><span class="sxs-lookup"><span data-stu-id="341f9-159">Altering a FileTable</span></span>  
 <span data-ttu-id="341f9-160">因為 FileTable 具有預先定義且固定的結構描述，所以您無法加入或變更其資料行。</span><span class="sxs-lookup"><span data-stu-id="341f9-160">Since a FileTable has a pre-defined and fixed schema, you cannot add or change its columns.</span></span> <span data-ttu-id="341f9-161">不過，您可以在 FileTable 中加入自訂索引、觸發程序、條件約束及其他選項。</span><span class="sxs-lookup"><span data-stu-id="341f9-161">However, you can add custom indexes, triggers, constraints, and other options to a FileTable.</span></span>  
  
 <span data-ttu-id="341f9-162">如需使用 ALTER TABLE 陳述式啟用或停用 FileTable 命名空間 (包括系統定義的條件約束) 的相關資訊，請參閱 [管理 FileTable](manage-filetables.md)。</span><span class="sxs-lookup"><span data-stu-id="341f9-162">For information about using the ALTER TABLE statement to enable or disable the FileTable namespace, including the system-defined constraints, see [Manage FileTables](manage-filetables.md).</span></span>  
  
###  <a name="how-to-change-the-directory-for-a-filetable"></a><a name="HowToChange"></a> <span data-ttu-id="341f9-163">如何：變更 FileTable 的目錄</span><span class="sxs-lookup"><span data-stu-id="341f9-163">How To: Change the Directory for a FileTable</span></span>  
 <span data-ttu-id="341f9-164">**使用 Transact-SQL 變更 FileTable 的目錄**</span><span class="sxs-lookup"><span data-stu-id="341f9-164">**Change the Directory for a FileTable by Using Transact-SQL**</span></span>  
 <span data-ttu-id="341f9-165">呼叫 ALTER TABLE 陳述式，並提供有效的新 **FILETABLE_DIRECTORY** SET 選項值。</span><span class="sxs-lookup"><span data-stu-id="341f9-165">Call the ALTER TABLE statement and provide a valid new value for the **FILETABLE_DIRECTORY** SET option.</span></span>  
  
 <span data-ttu-id="341f9-166">**範例**</span><span class="sxs-lookup"><span data-stu-id="341f9-166">**Example**</span></span>  
  
```sql  
ALTER TABLE filetable_name  
    SET ( FILETABLE_DIRECTORY = N'directory_name' );  
GO  
```  
  
 <span data-ttu-id="341f9-167">**使用 SQL Server Management Studio 變更 FileTable 的目錄**</span><span class="sxs-lookup"><span data-stu-id="341f9-167">**Change the Directory for a FileTable by Using SQL Server Management Studio**</span></span>  
 <span data-ttu-id="341f9-168">在物件總管中，以滑鼠右鍵按一下 [FileTable]，並選取 [屬性] 開啟 [資料表屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="341f9-168">In Object Explorer, right-click on the FileTable and select **Properties** to open the **Table Properties** dialog box.</span></span> <span data-ttu-id="341f9-169">在 **[FileTable]** 頁面上，輸入 **[FileTable 目錄名稱]** 的新值。</span><span class="sxs-lookup"><span data-stu-id="341f9-169">On the **FileTable** page, enter a new value for **FileTable directory name**.</span></span>  
  
###  <a name="requirements-and-restrictions-for-altering-a-filetable"></a><a name="ReqAlter"></a> <span data-ttu-id="341f9-170">改變 FileTable 的需求和限制</span><span class="sxs-lookup"><span data-stu-id="341f9-170">Requirements and Restrictions for Altering a FileTable</span></span>  
  
-   <span data-ttu-id="341f9-171">您無法改變 **FILETABLE_COLLATE_FILENAME**的值。</span><span class="sxs-lookup"><span data-stu-id="341f9-171">You cannot alter the value of **FILETABLE_COLLATE_FILENAME**.</span></span>  
  
-   <span data-ttu-id="341f9-172">您無法變更、卸除或停用 FileTable 的系統定義資料行。</span><span class="sxs-lookup"><span data-stu-id="341f9-172">You cannot change, drop, or disable the system-defined columns of a FileTable.</span></span>  
  
-   <span data-ttu-id="341f9-173">您無法將新的使用者資料行、計算資料行或已保存的計算資料行加入至 FileTable。</span><span class="sxs-lookup"><span data-stu-id="341f9-173">You cannot add new user columns, computed columns, or persisted computed columns to a FileTable.</span></span>  
  
##  <a name="dropping-a-filetable"></a><a name="BasicsDrop"></a> <span data-ttu-id="341f9-174">卸除 FileTable</span><span class="sxs-lookup"><span data-stu-id="341f9-174">Dropping a FileTable</span></span>  
 <span data-ttu-id="341f9-175">您可以使用 [DROP TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql) 陳述式的一般語法來卸除 FileTable。</span><span class="sxs-lookup"><span data-stu-id="341f9-175">You can drop a FileTable by using the ordinary syntax for the [DROP TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql) statement.</span></span>  
  
 <span data-ttu-id="341f9-176">當您卸除 FileTable 時，也會一併卸除下列物件：</span><span class="sxs-lookup"><span data-stu-id="341f9-176">When you drop a FileTable, the following objects are also dropped:</span></span>  
  
-   <span data-ttu-id="341f9-177">也會一併卸除 FileTable 的所有資料行以及與資料表相關聯的所有物件，例如索引、條件約束及觸發程序。</span><span class="sxs-lookup"><span data-stu-id="341f9-177">All the columns of the FileTable and all the objects associated with the table, such as indexes, constraints, and triggers, are also dropped.</span></span>  
  
-   <span data-ttu-id="341f9-178">FileTable 目錄和其所含的子目錄會從資料庫的 FILESTREAM 檔案及目錄階層中消失。</span><span class="sxs-lookup"><span data-stu-id="341f9-178">The FileTable directory and the sub-directories that it contained disappear from the FILESTREAM file and directory hierarchy of the database.</span></span>  
  
 <span data-ttu-id="341f9-179">如果 FileTable 的檔案命名空間中存在開啟的檔案控制代碼，DROP TABLE 命令就會失敗。</span><span class="sxs-lookup"><span data-stu-id="341f9-179">The DROP TABLE command fails if there are open file handles in the FileTable's file namespace.</span></span> <span data-ttu-id="341f9-180">如需關閉開啟之控制代碼的相關資訊，請參閱 [管理 FileTable](manage-filetables.md)。</span><span class="sxs-lookup"><span data-stu-id="341f9-180">For information about closing open handles, see [Manage FileTables](manage-filetables.md).</span></span>  
  
##  <a name="other-database-objects-are-created-when-you-create-a-filetable"></a><a name="BasicsOtherObjects"></a> <span data-ttu-id="341f9-181">當您建立 FileTable 時也會建立其他資料庫物件</span><span class="sxs-lookup"><span data-stu-id="341f9-181">Other Database Objects Are Created When You Create a FileTable</span></span>  
 <span data-ttu-id="341f9-182">當您建立新的 FileTable 時，也會建立一些系統定義的索引和條件約束。</span><span class="sxs-lookup"><span data-stu-id="341f9-182">When you create a new FileTable, some system-defined indexes and constraints are also created.</span></span> <span data-ttu-id="341f9-183">您不能改變或卸除這些物件，只有當 FileTable 本身卸除時它們才會消失。</span><span class="sxs-lookup"><span data-stu-id="341f9-183">You cannot alter or drop these objects; they disappear only when the FileTable itself is dropped.</span></span> <span data-ttu-id="341f9-184">若要查看這些物件的清單，請查詢目錄檢視 [sys.filetable_system_defined_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-filetable-system-defined-objects-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="341f9-184">To see the list of these objects, query the catalog view [sys.filetable_system_defined_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-filetable-system-defined-objects-transact-sql).</span></span>  
  
```sql  
--View all objects for all filetables, unsorted  
SELECT * FROM sys.filetable_system_defined_objects;  
GO  
  
--View sorted list with friendly names  
SELECT OBJECT_NAME(parent_object_id) AS 'FileTable', OBJECT_NAME(object_id) AS 'System-defined Object'  
    FROM sys.filetable_system_defined_objects  
    ORDER BY FileTable, 'System-defined Object';  
GO  
```  
  
 <span data-ttu-id="341f9-185">**建立新 FileTable 時所建立的索引**</span><span class="sxs-lookup"><span data-stu-id="341f9-185">**Indexes that are created when you create a new FileTable**</span></span>  
 <span data-ttu-id="341f9-186">當您建立新的 FileTable 時，也會建立下列系統定義的索引：</span><span class="sxs-lookup"><span data-stu-id="341f9-186">When you create a new FileTable, the following system-defined indexes are also created:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="341f9-187">**資料行**</span><span class="sxs-lookup"><span data-stu-id="341f9-187">**Columns**</span></span>|<span data-ttu-id="341f9-188">**索引類型**</span><span class="sxs-lookup"><span data-stu-id="341f9-188">**Index type**</span></span>|  
|<span data-ttu-id="341f9-189">[path_locator] ASC</span><span class="sxs-lookup"><span data-stu-id="341f9-189">[path_locator] ASC</span></span>|<span data-ttu-id="341f9-190">主索引鍵，非叢集</span><span class="sxs-lookup"><span data-stu-id="341f9-190">Primary Key, nonclustered</span></span>|  
|<span data-ttu-id="341f9-191">[parent_path_locator] ASC、</span><span class="sxs-lookup"><span data-stu-id="341f9-191">[parent_path_locator] ASC,</span></span><br /><br /> <span data-ttu-id="341f9-192">[name] ASC</span><span class="sxs-lookup"><span data-stu-id="341f9-192">[name] ASC</span></span>|<span data-ttu-id="341f9-193">唯一，非叢集</span><span class="sxs-lookup"><span data-stu-id="341f9-193">Unique, nonclustered</span></span>|  
|<span data-ttu-id="341f9-194">[stream_id] ASC</span><span class="sxs-lookup"><span data-stu-id="341f9-194">[stream_id] ASC</span></span>|<span data-ttu-id="341f9-195">唯一，非叢集</span><span class="sxs-lookup"><span data-stu-id="341f9-195">Unique, nonclustered</span></span>|  
  
 <span data-ttu-id="341f9-196">**建立新 FileTable 時所建立的條件約束**</span><span class="sxs-lookup"><span data-stu-id="341f9-196">**Constraints that are created when you create a new FileTable**</span></span>  
 <span data-ttu-id="341f9-197">當您建立新的 FileTable 時，也會建立下列系統定義的條件約束：</span><span class="sxs-lookup"><span data-stu-id="341f9-197">When you create a new FileTable, the following system-defined constraints are also created:</span></span>  
  
|<span data-ttu-id="341f9-198">條件約束</span><span class="sxs-lookup"><span data-stu-id="341f9-198">Constraints</span></span>|<span data-ttu-id="341f9-199">強制執行</span><span class="sxs-lookup"><span data-stu-id="341f9-199">Enforces</span></span>|  
|-----------------|--------------|  
|<span data-ttu-id="341f9-200">下列資料行的預設條件約束：</span><span class="sxs-lookup"><span data-stu-id="341f9-200">Default constraints on the following columns:</span></span><br /><br /> <span data-ttu-id="341f9-201">**creation_time**</span><span class="sxs-lookup"><span data-stu-id="341f9-201">**creation_time**</span></span> <br /> <span data-ttu-id="341f9-202">**is_archive**</span><span class="sxs-lookup"><span data-stu-id="341f9-202">**is_archive**</span></span> <br /> <span data-ttu-id="341f9-203">**is_directory**</span><span class="sxs-lookup"><span data-stu-id="341f9-203">**is_directory**</span></span> <br /> <span data-ttu-id="341f9-204">**is_hidden**</span><span class="sxs-lookup"><span data-stu-id="341f9-204">**is_hidden**</span></span> <br /> <span data-ttu-id="341f9-205">**is_offline**</span><span class="sxs-lookup"><span data-stu-id="341f9-205">**is_offline**</span></span> <br /> <span data-ttu-id="341f9-206">**is_readonly**</span><span class="sxs-lookup"><span data-stu-id="341f9-206">**is_readonly**</span></span> <br /> <span data-ttu-id="341f9-207">**is_system**</span><span class="sxs-lookup"><span data-stu-id="341f9-207">**is_system**</span></span> <br /> <span data-ttu-id="341f9-208">**is_temporary**</span><span class="sxs-lookup"><span data-stu-id="341f9-208">**is_temporary**</span></span> <br /> <span data-ttu-id="341f9-209">**last_access_time**</span><span class="sxs-lookup"><span data-stu-id="341f9-209">**last_access_time**</span></span> <br /> <span data-ttu-id="341f9-210">**last_write_time**</span><span class="sxs-lookup"><span data-stu-id="341f9-210">**last_write_time**</span></span> <br /> <span data-ttu-id="341f9-211">**path_locator**</span><span class="sxs-lookup"><span data-stu-id="341f9-211">**path_locator**</span></span> <br /> <span data-ttu-id="341f9-212">**stream_id**</span><span class="sxs-lookup"><span data-stu-id="341f9-212">**stream_id**</span></span>|<span data-ttu-id="341f9-213">系統定義的預設條件約束會針對指定的資料行強制執行預設值。</span><span class="sxs-lookup"><span data-stu-id="341f9-213">The system-defined default constraints enforce default values for the specified columns.</span></span>|  
|<span data-ttu-id="341f9-214">檢查條件約束</span><span class="sxs-lookup"><span data-stu-id="341f9-214">Check constraints</span></span>|<span data-ttu-id="341f9-215">系統定義的檢查條件約束會強制執行下列需求：</span><span class="sxs-lookup"><span data-stu-id="341f9-215">The system-defined check constraints enforce the following requirements:</span></span><br /><br /> <span data-ttu-id="341f9-216">有效的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="341f9-216">Valid filenames.</span></span><br /><br /> <span data-ttu-id="341f9-217">有效的檔案屬性。</span><span class="sxs-lookup"><span data-stu-id="341f9-217">Valid file attributes.</span></span><br /><br /> <span data-ttu-id="341f9-218">父物件必須是目錄。</span><span class="sxs-lookup"><span data-stu-id="341f9-218">Parent object must be a directory.</span></span><br /><br /> <span data-ttu-id="341f9-219">在檔案操作期間，會鎖定命名空間階層。</span><span class="sxs-lookup"><span data-stu-id="341f9-219">Namespace hierarchy is locked during file manipulation.</span></span>|  
  
 <span data-ttu-id="341f9-220">**系統定義之條件約束的命名慣例**</span><span class="sxs-lookup"><span data-stu-id="341f9-220">**Naming convention for the system-defined constraints**</span></span>  
 <span data-ttu-id="341f9-221">上述系統定義的條件約束會使用 **\<constraintType>_\<tablename>[\_\<columnname>]\_\<uniquifier>** 格式來命名，其中：</span><span class="sxs-lookup"><span data-stu-id="341f9-221">The system-defined constraints described above are named in the format **\<constraintType>_\<tablename>[\_\<columnname>]\_\<uniquifier>** where:</span></span>  
  
-   <span data-ttu-id="341f9-222">其中的 <條件約束類型> 是 CK (檢查條件約束)、DF (預設條件約束)、FK (外部索引鍵)、PK (主索引鍵) 或 UQ (唯一條件約束)。</span><span class="sxs-lookup"><span data-stu-id="341f9-222">*<constraint_type>* is CK (check constraint), DF (default constraint), FK (foreign key), PK (primary key), or UQ (unique constraint).</span></span>  
  
-   <span data-ttu-id="341f9-223">*\<uniquifier>* 是讓名稱成為唯一名稱的系統產生字串。</span><span class="sxs-lookup"><span data-stu-id="341f9-223">*\<uniquifier>* is a system-generated string to make the name unique.</span></span> <span data-ttu-id="341f9-224">這個字串可能會包含 FileTable 名稱和唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="341f9-224">This string may contain the FileTable name and a unique identifier.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="341f9-225">另請參閱</span><span class="sxs-lookup"><span data-stu-id="341f9-225">See Also</span></span>  
 [<span data-ttu-id="341f9-226">管理 FileTable</span><span class="sxs-lookup"><span data-stu-id="341f9-226">Manage FileTables</span></span>](manage-filetables.md)  
  
  
