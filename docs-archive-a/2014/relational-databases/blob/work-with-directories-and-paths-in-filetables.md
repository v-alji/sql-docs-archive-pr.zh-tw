---
title: 使用 FileTables 中的目錄與路徑 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], directories
ms.assetid: f1e45900-bea0-4f6f-924e-c11e1f98ab62
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4641159e894b764cbee4d7f02085f3ceb8e6d87d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686981"
---
# <a name="work-with-directories-and-paths-in-filetables"></a><span data-ttu-id="5f5ac-102">使用 FileTables 中的目錄與路徑</span><span class="sxs-lookup"><span data-stu-id="5f5ac-102">Work with Directories and Paths in FileTables</span></span>
  <span data-ttu-id="5f5ac-103">描述在 FileTable 中儲存檔案的目錄結構。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-103">Describes the directory structure in which the files are stored in FileTables.</span></span>  
  
##  <a name="how-to-work-with-directories-and-paths-in-filetables"></a><a name="HowToDirectories"></a> <span data-ttu-id="5f5ac-104">如何：使用 FileTables 中的目錄與路徑</span><span class="sxs-lookup"><span data-stu-id="5f5ac-104">How To: Work with Directories and Paths in FileTables</span></span>  
 <span data-ttu-id="5f5ac-105">您可使用下列三項函數在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中使用 FileTable 目錄：</span><span class="sxs-lookup"><span data-stu-id="5f5ac-105">You can use the following 3 functions to work with FileTable directories in [!INCLUDE[tsql](../../includes/tsql-md.md)]:</span></span>  
  
|<span data-ttu-id="5f5ac-106">為得到此結果</span><span class="sxs-lookup"><span data-stu-id="5f5ac-106">To get this result</span></span>|<span data-ttu-id="5f5ac-107">使用此函數</span><span class="sxs-lookup"><span data-stu-id="5f5ac-107">Use this function</span></span>|  
|------------------------|-----------------------|  
|<span data-ttu-id="5f5ac-108">取得特定 FileTable 或目前資料庫的根層級 UNC 路徑。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-108">Get the root-level UNC path for a specific FileTable or for the current database.</span></span>|[<span data-ttu-id="5f5ac-109">FileTableRootPath &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5f5ac-109">FileTableRootPath &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/filetablerootpath-transact-sql)|  
|<span data-ttu-id="5f5ac-110">取得 FileTable 中檔案或目錄的絕對路徑或相對 UNC 路徑。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-110">Get an absolute or relative UNC path for a file or directory in a FileTable.</span></span>|[<span data-ttu-id="5f5ac-111">GetFileNamespacePath &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5f5ac-111">GetFileNamespacePath &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/getfilenamespacepath-transact-sql)|  
|<span data-ttu-id="5f5ac-112">經由提供路徑的方法，取得 FileTable 中指定之檔案或目錄的路徑定位器識別碼值。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-112">Get the path locator ID value for the specified file or directory in a FileTable, by providing the path.</span></span>|[<span data-ttu-id="5f5ac-113">GetPathLocator &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5f5ac-113">GetPathLocator &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/getpathlocator-transact-sql)|  
  
##  <a name="how-to-use-relative-paths-for-portable-code"></a><a name="BestPracticeRelativePaths"></a> <span data-ttu-id="5f5ac-114">如何：使用可攜式程式碼的相對路徑</span><span class="sxs-lookup"><span data-stu-id="5f5ac-114">How to: Use Relative Paths for Portable Code</span></span>  
 <span data-ttu-id="5f5ac-115">若要讓程式碼和應用程式獨立於目前的電腦和資料庫之外，請避免撰寫依賴絕對檔案路徑的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-115">To keep code and applications independent of the current computer and database, avoid writing code that relies on absolute file paths.</span></span> <span data-ttu-id="5f5ac-116">相反地，同時使用 [FileTableRootPath &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/filetablerootpath-transact-sql) 和 [GetFileNamespacePath &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/getfilenamespacepath-transact-sql)函數，以取得檔案在執行階段的完整路徑，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-116">Instead, get the complete path for a file at run time by using the [FileTableRootPath &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/filetablerootpath-transact-sql) and [GetFileNamespacePath &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/getfilenamespacepath-transact-sql)) functions together, as shown in the following example.</span></span> <span data-ttu-id="5f5ac-117">根據預設，`GetFileNamespacePath` 函數會傳回資料庫根路徑之下的檔案相對路徑。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-117">By default, the `GetFileNamespacePath` function returns the relative path of the file under the root path for the database.</span></span>  
  
```sql  
USE database_name;  
DECLARE @root nvarchar(100);  
DECLARE @fullpath nvarchar(1000);  
  
SELECT @root = FileTableRootPath();  
SELECT @fullpath = @root + file_stream.GetFileNamespacePath()  
    FROM filetable_name  
    WHERE name = N'document_name';  
  
PRINT @fullpath;  
GO  
```  
  
##  <a name="important-restrictions"></a><a name="restrictions"></a> <span data-ttu-id="5f5ac-118">重要限制</span><span class="sxs-lookup"><span data-stu-id="5f5ac-118">Important restrictions</span></span>  
  
###  <a name="nesting-level"></a><a name="nesting"></a> <span data-ttu-id="5f5ac-119">巢狀層級</span><span class="sxs-lookup"><span data-stu-id="5f5ac-119">Nesting level</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5f5ac-120">您不能在 FileTable 目錄中儲存超過 15 層的子目錄。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-120">You cannot store more than 15 levels of subdirectories in the FileTable directory.</span></span> <span data-ttu-id="5f5ac-121">當您儲存了 15 層的子目錄時，最低的一層將無法包含任何檔案，因為這些檔案代表另外的一層。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-121">When you store 15 levels of subdirectories, then the lowest level cannot contain files, since these files would represent an additional level.</span></span>  
  
###  <a name="length-of-full-path-name"></a><a name="fqnlength"></a> <span data-ttu-id="5f5ac-122">完整路徑名稱長度</span><span class="sxs-lookup"><span data-stu-id="5f5ac-122">Length of full path name</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5f5ac-123">NTFS 檔案系統支援遠超過 Windows Shell 和大多數 Windows API 的 260 字元限制的路徑名稱。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-123">The NTFS file system supports path names that are much longer than the 260-character limit of the Windows shell and most Windows APIs.</span></span> <span data-ttu-id="5f5ac-124">因此，可以使用 Transact-SQL 建立 FileTable 檔案階層中完整路徑名稱超過 260 字元的檔案，但卻無法以 Windows 檔案總管或許多其他 Windows 應用程式檢視或開啟這些檔案。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-124">Therefore it is possible to create files in the file hierarchy of a FileTable by using Transact-SQL that you cannot view or open with Windows Explorer or many other Windows applications, because the full path name exceeds 260 characters.</span></span> <span data-ttu-id="5f5ac-125">不過，您可以繼續使用 Transact-SQL 存取這些檔案。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-125">However you can continue to access these files by using Transact-SQL.</span></span>  
  
##  <a name="the-full-path-to-an-item-stored-in-a-filetable"></a><a name="fullpath"></a> <span data-ttu-id="5f5ac-126">FileTable 中儲存之項目的完整路徑</span><span class="sxs-lookup"><span data-stu-id="5f5ac-126">The full path to an item stored in a FileTable</span></span>  
 <span data-ttu-id="5f5ac-127">FileTable 中儲存之檔案或目錄的完整路徑，由下列元素做為開頭：</span><span class="sxs-lookup"><span data-stu-id="5f5ac-127">The full path to a file or directory stored in a FileTable begins with the following elements:</span></span>  
  
1.  <span data-ttu-id="5f5ac-128">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體層級為 FILESTREAM 檔 I/O 存取啟用共用。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-128">The share enabled for FILESTREAM file I/O access at the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance level.</span></span>  
  
2.  <span data-ttu-id="5f5ac-129">**DIRECTORY_NAME** 於資料庫層級指定。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-129">The **DIRECTORY_NAME** specified at the database level.</span></span>  
  
3.  <span data-ttu-id="5f5ac-130">**FILETABLE_DIRECTORY** 於 FileTable 層級指定。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-130">The **FILETABLE_DIRECTORY** specified at the FileTable level.</span></span>  
  
 <span data-ttu-id="5f5ac-131">所產生的階層如下：</span><span class="sxs-lookup"><span data-stu-id="5f5ac-131">The resulting hierarchy looks like this:</span></span>  
  
 `\\<machine>\<instance-level FILESTREAM share>\<database-level directory>\<FileTable directory>\`  
  
 <span data-ttu-id="5f5ac-132">此目錄階層會形成 FileTable 檔案命名空間的根目錄。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-132">This directory hierarchy forms the root of the FileTable's file namespace.</span></span> <span data-ttu-id="5f5ac-133">在此目錄階層之下，FileTable 的 FILESTREAM 資料將會儲存為檔案，以及其下也可以再包含檔案與子目錄的子目錄。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-133">Under this directory hierarchy, the FILESTREAM data for the FileTable is stored as files, and as subdirectories which can also contain files and subdirectories.</span></span>  
  
 <span data-ttu-id="5f5ac-134">請務必牢記，於此執行個體層級的 FILESTREAM 共用之下所建立的目錄階層，是一個虛擬的目錄階層。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-134">It is important to keep in mind that the directory hierarchy created under the instance-level FILESTREAM share is a virtual directory hierarchy.</span></span> <span data-ttu-id="5f5ac-135">此階層儲存於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫，且不會實際於 NTFS 檔案系統中呈現出來。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-135">This hierarchy is stored in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database and is not represented physically in the NTFS file system.</span></span> <span data-ttu-id="5f5ac-136">所有存取 FILESTREAM 共用之下以及其所包含之 FileTables 中檔案與目錄的作業，都會由檔案系統中內嵌的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件所攔截與處理。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-136">All operations that access files and directories under the FILESTREAM share and in the FileTables that it contains are intercepted and handled by a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] component embedded in the file system.</span></span>  
  
##  <a name="the-semantics-of-the-root-directories-at-the-instance-database-and-filetable-levels"></a><a name="roots"></a> <span data-ttu-id="5f5ac-137">執行個體、資料庫與 FileTable 層級上根目錄的語意</span><span class="sxs-lookup"><span data-stu-id="5f5ac-137">The semantics of the root directories at the instance, database, and FileTable levels</span></span>  
 <span data-ttu-id="5f5ac-138">此目錄階層結構遵循下列語義：</span><span class="sxs-lookup"><span data-stu-id="5f5ac-138">This directory hierarchy observes the following semantics:</span></span>  
  
-   <span data-ttu-id="5f5ac-139">執行個體層級的 FILESTREAM 共用由管理員所設定，而且會儲存為伺服器屬性。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-139">The instance-level FILESTREAM share is configured by an administrator and stored as a property of the server.</span></span> <span data-ttu-id="5f5ac-140">您可使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員，重新命名此共用。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-140">You can rename this share by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="5f5ac-141">伺服器重新啟動之前重新命名作業不會生效。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-141">A renaming operation does not take effect until the server is restarted.</span></span>  
  
-   <span data-ttu-id="5f5ac-142">當您建立新的資料庫時，資料庫層級的 **DIRECTORY_NAME** 預設為 null。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-142">The database-level **DIRECTORY_NAME** is null by default when you create a new database.</span></span> <span data-ttu-id="5f5ac-143">管理員可使用 **ALTER DATABASE** 陳述式設定或變更此名稱。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-143">An administrator can set or change this name by using the **ALTER DATABASE** statement.</span></span> <span data-ttu-id="5f5ac-144">該執行個體中的名稱不行重複 (不分大小寫)。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-144">The name must be unique (in a case-insensitive comparison) in that instance.</span></span>  
  
-   <span data-ttu-id="5f5ac-145">一般來說，當您建立 FileTable 時，會提供 **FILETABLE_DIRECTORY** 名稱作為 **CREATE TABLE** 陳述式的一部分。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-145">You typically provide the **FILETABLE_DIRECTORY** name as part of the **CREATE TABLE** statement when you create a FileTable.</span></span> <span data-ttu-id="5f5ac-146">您也可以使用 **ALTER TABLE** 命令變更此名稱。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-146">You can change this name by using the **ALTER TABLE** command.</span></span>  
  
-   <span data-ttu-id="5f5ac-147">您無法透過檔案 I/O 作業變更這些根目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-147">You cannot rename these root directories through file I/O operations.</span></span>  
  
-   <span data-ttu-id="5f5ac-148">您無法以獨佔的檔案控制開啟這些根目錄。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-148">You cannot open these root directories with exclusive file handles.</span></span>  
  
##  <a name="the-is_directory-column-in-the-filetable-schema"></a><a name="is_directory"></a> <span data-ttu-id="5f5ac-149">FileTable 結構描述中的 is_directory 資料行</span><span class="sxs-lookup"><span data-stu-id="5f5ac-149">The is_directory column in the FileTable schema</span></span>  
 <span data-ttu-id="5f5ac-150">下表描述 **is_directory** 資料行以及與將 FILESTREAM 資料包含於 FileTable 中的 **file_stream** 資料行之間的互動。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-150">The following table describes the interaction between the **is_directory** column and the **file_stream** column that contains the FILESTREAM data in a FileTable.</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="5f5ac-151">*is_directory* **value**</span><span class="sxs-lookup"><span data-stu-id="5f5ac-151">*is_directory* **value**</span></span>|<span data-ttu-id="5f5ac-152">*file_stream* **value**</span><span class="sxs-lookup"><span data-stu-id="5f5ac-152">*file_stream* **value**</span></span>|<span data-ttu-id="5f5ac-153">**行為**</span><span class="sxs-lookup"><span data-stu-id="5f5ac-153">**Behavior**</span></span>|  
|<span data-ttu-id="5f5ac-154">FALSE</span><span class="sxs-lookup"><span data-stu-id="5f5ac-154">FALSE</span></span>|<span data-ttu-id="5f5ac-155">NULL</span><span class="sxs-lookup"><span data-stu-id="5f5ac-155">NULL</span></span>|<span data-ttu-id="5f5ac-156">此為無效的組合，將由系統定義的條件約束所攔截。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-156">This is an invalid combination that will be caught by a system-defined constraint.</span></span>|  
|<span data-ttu-id="5f5ac-157">FALSE</span><span class="sxs-lookup"><span data-stu-id="5f5ac-157">FALSE</span></span>|\<value>|<span data-ttu-id="5f5ac-158">該項目代表檔案。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-158">The item represents a file.</span></span>|  
|<span data-ttu-id="5f5ac-159">TRUE</span><span class="sxs-lookup"><span data-stu-id="5f5ac-159">TRUE</span></span>|<span data-ttu-id="5f5ac-160">NULL</span><span class="sxs-lookup"><span data-stu-id="5f5ac-160">NULL</span></span>|<span data-ttu-id="5f5ac-161">該項目代表目錄。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-161">The item represents a directory.</span></span>|  
|<span data-ttu-id="5f5ac-162">TRUE</span><span class="sxs-lookup"><span data-stu-id="5f5ac-162">TRUE</span></span>|\<value>|<span data-ttu-id="5f5ac-163">此為無效的組合，將由系統定義的條件約束所攔截。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-163">This is an invalid combination that will be caught by a system-defined constraint.</span></span>|  
  
##  <a name="using-virtual-network-names-vnns-with-alwayson-availability-groups"></a><a name="alwayson"></a> <span data-ttu-id="5f5ac-164">使用虛擬網路名稱 (VNN) 搭配 AlwaysOn 可用性群組</span><span class="sxs-lookup"><span data-stu-id="5f5ac-164">Using Virtual Network Names (VNNs) with AlwaysOn Availability Groups</span></span>  
 <span data-ttu-id="5f5ac-165">當包含 FILESTREAM 或 FileTable 資料的資料庫屬於 AlwaysOn 可用性群組時：</span><span class="sxs-lookup"><span data-stu-id="5f5ac-165">When the database that contains FILESTREAM or FileTable data belongs to an AlwaysOn availability group:</span></span>  
  
-   <span data-ttu-id="5f5ac-166">FILESTREAM 和 FileTable 函數會接受或傳回虛擬網路名稱 (VNN) 而非電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-166">The FILESTREAM and FileTable functions accept or return virtual network names (VNNs) instead of computer names.</span></span> <span data-ttu-id="5f5ac-167">如需有關這些函數的詳細資訊，請參閱 [Filestream and FileTable Functions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/filestream-and-filetable-functions-transact-sql) (Filestream 和 FileTable 函數 (Transact-SQL))。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-167">For more information about these functions, see [Filestream and FileTable Functions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/filestream-and-filetable-functions-transact-sql).</span></span>  
  
-   <span data-ttu-id="5f5ac-168">透過檔案系統 API 對 FILESTREAM 或 FileTable 資料進行的所有存取都應該使用 VNN 而非電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-168">All access to FILESTREAM or FileTable data through the file system APIs should use VNNs instead of computer names.</span></span> <span data-ttu-id="5f5ac-169">如需詳細資訊，請參閱 [FILESTREAM 和 FileTable 與 AlwaysOn 可用性群組 &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/filestream-and-filetable-with-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="5f5ac-169">For more information, see [FILESTREAM and FileTable with AlwaysOn Availability Groups &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/filestream-and-filetable-with-always-on-availability-groups-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f5ac-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f5ac-170">See Also</span></span>  
 <span data-ttu-id="5f5ac-171">[啟用 FileTable 的必要條件](enable-the-prerequisites-for-filetable.md) </span><span class="sxs-lookup"><span data-stu-id="5f5ac-171">[Enable the Prerequisites for FileTable](enable-the-prerequisites-for-filetable.md) </span></span>  
 <span data-ttu-id="5f5ac-172">[建立、改變及卸除 FileTable](create-alter-and-drop-filetables.md) </span><span class="sxs-lookup"><span data-stu-id="5f5ac-172">[Create, Alter, and Drop FileTables](create-alter-and-drop-filetables.md) </span></span>  
 <span data-ttu-id="5f5ac-173">[利用 Transact-SQL 存取 FileTable](access-filetables-with-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="5f5ac-173">[Access FileTables with Transact-SQL](access-filetables-with-transact-sql.md) </span></span>  
 [<span data-ttu-id="5f5ac-174">使用檔案輸入輸出 API 存取 FileTable</span><span class="sxs-lookup"><span data-stu-id="5f5ac-174">Access FileTables with File Input-Output APIs</span></span>](access-filetables-with-file-input-output-apis.md)  
  
  
