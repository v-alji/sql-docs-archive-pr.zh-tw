---
title: 載入檔案至 FileTable | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], migrating files
- FileTables [SQL Server], bulk loading
- FileTables [SQL Server], loading files
ms.assetid: dc842a10-0586-4b0f-9775-5ca0ecc761d9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 43ea31523da2dfa8b387f68ce4f7c7f07868dd6f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707614"
---
# <a name="load-files-into-filetables"></a><span data-ttu-id="03177-102">載入檔案至 FileTable</span><span class="sxs-lookup"><span data-stu-id="03177-102">Load Files into FileTables</span></span>
  <span data-ttu-id="03177-103">描述如何載入或移轉檔案至 FileTable 中。</span><span class="sxs-lookup"><span data-stu-id="03177-103">Describes how to load or migrate files into FileTables.</span></span>  
  
##  <a name="loading-or-migrating-files-into-a-filetable"></a><a name="BasicsLoadNew"></a> <span data-ttu-id="03177-104">將檔案載入或移轉至 FileTable</span><span class="sxs-lookup"><span data-stu-id="03177-104">Loading or Migrating Files into a FileTable</span></span>  
 <span data-ttu-id="03177-105">您選擇用於將檔案載入或移轉至 FileTable 中的方法，取決於目前儲存檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="03177-105">The method that you choose for loading or migrating files into a FileTable depends on where the files are currently stored.</span></span>  
  
|<span data-ttu-id="03177-106">檔案的目前位置</span><span class="sxs-lookup"><span data-stu-id="03177-106">Current location of files</span></span>|<span data-ttu-id="03177-107">移轉選項</span><span class="sxs-lookup"><span data-stu-id="03177-107">Options for migration</span></span>|  
|-------------------------------|---------------------------|  
|<span data-ttu-id="03177-108">檔案目前儲存在檔案系統中。</span><span class="sxs-lookup"><span data-stu-id="03177-108">Files are currently stored in the file system.</span></span><br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="03177-109">沒有檔案的知識。</span><span class="sxs-lookup"><span data-stu-id="03177-109">has no knowledge of the files.</span></span>|<span data-ttu-id="03177-110">因為 FileTable 會顯示成 Windows 檔案系統中的資料夾，所以您可以使用任何移動或複製檔案的可用方法，輕鬆地將檔案載入新的 FileTable。</span><span class="sxs-lookup"><span data-stu-id="03177-110">Since a FileTable appears as a folder in the Windows file system, you can easily load files into a new FileTable by using any of the available methods for moving or copying files.</span></span> <span data-ttu-id="03177-111">這些方法包括 Windows 檔案總管、命令列選項 (包括 xcopy 與 robocopy)，以及自訂指令碼或應用程式。</span><span class="sxs-lookup"><span data-stu-id="03177-111">These methods include Windows Explorer, command line options including xcopy and robocopy, and custom scripts or applications.</span></span><br /><br /> <span data-ttu-id="03177-112">您無法將現有的資料夾轉換為 FileTable。</span><span class="sxs-lookup"><span data-stu-id="03177-112">You cannot convert an existing folder to a FileTable.</span></span>|  
|<span data-ttu-id="03177-113">檔案目前儲存在檔案系統中。</span><span class="sxs-lookup"><span data-stu-id="03177-113">Files are currently stored in the file system.</span></span><br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="03177-114">包含內有指向檔案之指標的中繼資料資料表。</span><span class="sxs-lookup"><span data-stu-id="03177-114">contains a table of metadata that contains pointers to the files.</span></span>|<span data-ttu-id="03177-115">第一個步驟是使用上述方法之一，移動或複製檔案。</span><span class="sxs-lookup"><span data-stu-id="03177-115">The first step is to move or copy the files by using one of the methods mentioned above.</span></span><br /><br /> <span data-ttu-id="03177-116">第二個步驟是將中繼資料的現有資料表，更新為指向該檔案的新位置。</span><span class="sxs-lookup"><span data-stu-id="03177-116">The second step is to update the existing table of metadata to point to the new location of the files.</span></span><br /><br /> <span data-ttu-id="03177-117">如需詳細資訊，請參閱本主題的＜ [範例：從檔案系統移轉檔案至 FileTable](#HowToMigrateFiles) ＞。</span><span class="sxs-lookup"><span data-stu-id="03177-117">For more information, see [Example: Migrating Files from the File System into a FileTable](#HowToMigrateFiles) in this topic.</span></span>|  
  
###  <a name="how-to-load-files-into-a-filetable"></a><a name="HowToLoadNew"></a> <span data-ttu-id="03177-118">如何：將檔案載入 FileTable</span><span class="sxs-lookup"><span data-stu-id="03177-118">How To: Load Files into a FileTable</span></span>  
 <span data-ttu-id="03177-119">您可用以將檔案載入 FileTable 的方法包括：</span><span class="sxs-lookup"><span data-stu-id="03177-119">The methods that you can use to load files into a FileTable include the following:</span></span>  
  
-   <span data-ttu-id="03177-120">在 [Windows 檔案總管] 中，將檔案從來源資料夾拖放至新的 FileTable 資料夾。</span><span class="sxs-lookup"><span data-stu-id="03177-120">Drag and drop files from the source folders to the new FileTable folder in Windows Explorer.</span></span>  
  
-   <span data-ttu-id="03177-121">透過命令提示字元或在批次檔或指令碼中，使用命令列選項，例如 MOVE、COPY、XCOPY 或 ROBOCOPY。</span><span class="sxs-lookup"><span data-stu-id="03177-121">Use command line options such as MOVE, COPY, XCOPY, or ROBOCOPY from the command prompt or in a batch file or script.</span></span>  
  
-   <span data-ttu-id="03177-122">以 C# 或 Visual Basic.NET 撰寫使用來自 **System.IO** 命名空間之方法的自訂應用程式，移動或複製檔案。</span><span class="sxs-lookup"><span data-stu-id="03177-122">Write a custom application in C# or Visual Basic.NET that uses methods from the **System.IO** namespace to move or copy the files.</span></span>  
  
###  <a name="example-migrating-files-from-the-file-system-into-a-filetable"></a><a name="HowToMigrateFiles"></a> <span data-ttu-id="03177-123">範例：將檔案從檔案系移轉至 FileTable</span><span class="sxs-lookup"><span data-stu-id="03177-123">Example: Migrating Files from the File System into a FileTable</span></span>  
 <span data-ttu-id="03177-124">在此案例中，您的檔案儲存在檔案系統中，而且您在擁有內含指向該檔案之指標的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，具有中繼資料表。</span><span class="sxs-lookup"><span data-stu-id="03177-124">In this scenario, your files are stored in the file system, and you have a table of metadata in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that contains pointers to the files.</span></span> <span data-ttu-id="03177-125">您想要將檔案移入 FileTable，然後使用 FileTable UNC 路徑來取代中繼資料內每個檔案的原始 UNC 路徑。</span><span class="sxs-lookup"><span data-stu-id="03177-125">You want to move the files into a FileTable, and then replace the original UNC path for each file in the metadata with the FileTable UNC path.</span></span> <span data-ttu-id="03177-126">[GetPathLocator &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/getpathlocator-transact-sql) 函式可協助您達成此目標。</span><span class="sxs-lookup"><span data-stu-id="03177-126">The [GetPathLocator &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/getpathlocator-transact-sql) function helps you to achieve this goal.</span></span>  
  
 <span data-ttu-id="03177-127">在此範例中，假設有一個現有的資料庫資料表， `PhotoMetadata` 其中包含相片的相關資料。</span><span class="sxs-lookup"><span data-stu-id="03177-127">For this example, assume that there is an existing database table, `PhotoMetadata`, which contains data about photographs.</span></span> <span data-ttu-id="03177-128">此資料表中有一個 `varchar`(512) 類型的 `UNCPath` 資料行，其中包含對應至 .jpg 檔案的實際 UNC 路徑。</span><span class="sxs-lookup"><span data-stu-id="03177-128">This table has a column `UNCPath` of type `varchar`(512) which contains the actual UNC path to a .jpg file.</span></span>  
  
 <span data-ttu-id="03177-129">若要將影像檔從檔案系統移轉至 FileTable，您必須進行下列動作：</span><span class="sxs-lookup"><span data-stu-id="03177-129">To migrate the image files from the file system into a FileTable, you have to do the following:</span></span>  
  
1.  <span data-ttu-id="03177-130">建立新的 FileTable 以保存該檔案。</span><span class="sxs-lookup"><span data-stu-id="03177-130">Create a new FileTable to hold the files.</span></span> <span data-ttu-id="03177-131">這個範例使用資料表名稱 `dbo.PhotoTable`，但並未顯示建立資料表的程式碼。</span><span class="sxs-lookup"><span data-stu-id="03177-131">This example uses the table name, `dbo.PhotoTable`, but does not show the code to create the table.</span></span>  
  
2.  <span data-ttu-id="03177-132">使用 xcopy 或類似的工具，將 .jpg 檔案及其目錄結構複製到 FileTable 的根目錄中。</span><span class="sxs-lookup"><span data-stu-id="03177-132">Use xcopy or a similar tool to copy the .jpg files, with their directory structure, into the root directory of the FileTable.</span></span>  
  
3.  <span data-ttu-id="03177-133">使用類似下面的程式碼，修正 `PhotoMetadata` 資料表中的中繼資料：</span><span class="sxs-lookup"><span data-stu-id="03177-133">Fix the metadata in the `PhotoMetadata` table, by using code similar to the following:</span></span>  
  
```sql  
--  Add a path locator column to the PhotoMetadata table.  
ALTER TABLE PhotoMetadata ADD pathlocator hierarchyid;  
  
-- Get the root path of the Photo directory on the File Server.  
DECLARE @UNCPathRoot varchar(100) = '\\RemoteShare\Photographs';  
  
-- Get the root path of the FileTable.  
DECLARE @FileTableRoot varchar(1000);  
SELECT @FileTableRoot = FileTableRootPath('dbo.PhotoTable');  
  
-- Update the PhotoMetadata table.  
  
-- Replace the File Server UNC path with the FileTable path.  
UPDATE PhotoMetadata  
    SET UNCPath = REPLACE(UNCPath, @UNCPathRoot, @FileTableRoot);  
  
-- Update the pathlocator column to contain the pathlocator IDs from the FileTable.  
UPDATE PhotoMetadata  
    SET pathlocator = GetPathLocator(UNCPath);  
```  
  
##  <a name="bulk-loading-files-into-a-filetable"></a><a name="BasicsBulkLoad"></a> <span data-ttu-id="03177-134">將檔案大量載入 FileTable</span><span class="sxs-lookup"><span data-stu-id="03177-134">Bulk Loading Files into a FileTable</span></span>  
 <span data-ttu-id="03177-135">FileTable 大量作業的行為和一般資料表相同，包含以下條件。</span><span class="sxs-lookup"><span data-stu-id="03177-135">A FileTable behaves like a normal table for bulk operations, with the following qualifications.</span></span>  
  
 <span data-ttu-id="03177-136">FileTable 具有系統定義的條件約束，可確保能維持檔案與目錄命名空間的完整性。</span><span class="sxs-lookup"><span data-stu-id="03177-136">A FileTable has system-defined constraints which ensure that the integrity of the file and directory namespace is maintained.</span></span> <span data-ttu-id="03177-137">大量載入至 FileTable 中的資料，必須通過這些條件約束的驗證。</span><span class="sxs-lookup"><span data-stu-id="03177-137">These constraints have to be verified on the data bulk loaded into the FileTable.</span></span> <span data-ttu-id="03177-138">因為某些大量插入作業允許忽略資料表條件約束，所以系統會強制執行下列要求。</span><span class="sxs-lookup"><span data-stu-id="03177-138">Since some bulk insert operations allow table constraints to be ignored, the following requirements are enforced.</span></span>  
  
-   <span data-ttu-id="03177-139">針對 FileTable 進行的強制執行條件約束之大量載入，與針對任何其他資料表所進行的大量載入作業執行方式相同。</span><span class="sxs-lookup"><span data-stu-id="03177-139">Bulk loading operations that enforce constraints can be run against a FileTable as against any other table.</span></span> <span data-ttu-id="03177-140">此類別目錄包括以下作業：</span><span class="sxs-lookup"><span data-stu-id="03177-140">This category includes the following operations:</span></span>  
  
    -   <span data-ttu-id="03177-141">含有 CHECK_CONSTRAINTS 子句的 bcp。</span><span class="sxs-lookup"><span data-stu-id="03177-141">bcp with CHECK_CONSTRAINTS clause.</span></span>  
  
    -   <span data-ttu-id="03177-142">含有 CHECK_CONSTRAINTS 子句的 BULK INSERT。</span><span class="sxs-lookup"><span data-stu-id="03177-142">BULK INSERT with CHECK_CONSTRAINTS clause.</span></span>  
  
    -   <span data-ttu-id="03177-143">INSERT INTO ...不含 IGNORE_CONSTRAINTS 子句的 SELECT \* FROM OPENROWSET(BULK …)。</span><span class="sxs-lookup"><span data-stu-id="03177-143">INSERT INTO ... SELECT \* FROM OPENROWSET(BULK ...) without IGNORE_CONSTRAINTS clause.</span></span>  
  
-   <span data-ttu-id="03177-144">除非已停用 FileTable 系統定義的條件約束，否則不強制執行條件約束的 FileTable 大量載入作業將會失敗。</span><span class="sxs-lookup"><span data-stu-id="03177-144">Bulk loading operations that do not enforce constraints fail unless the FileTable system-defined constraints have been disabled.</span></span> <span data-ttu-id="03177-145">此類別目錄包括以下作業：</span><span class="sxs-lookup"><span data-stu-id="03177-145">This category includes the following operations:</span></span>  
  
    -   <span data-ttu-id="03177-146">不含 CHECK_CONSTRAINTS 子句的 bcp。</span><span class="sxs-lookup"><span data-stu-id="03177-146">bcp without CHECK_CONSTRAINTS clause.</span></span>  
  
    -   <span data-ttu-id="03177-147">不含 CHECK_CONSTRAINTS 子句的 BULK INSERT。</span><span class="sxs-lookup"><span data-stu-id="03177-147">BULK INSERT without CHECK_CONSTRAINTS clause.</span></span>  
  
    -   <span data-ttu-id="03177-148">INSERT INTO ...含 IGNORE_CONSTRAINTS 子句的 SELECT \* FROM OPENROWSET(BULK …)。</span><span class="sxs-lookup"><span data-stu-id="03177-148">INSERT INTO ... SELECT \* FROM OPENROWSET(BULK ...) with IGNORE_CONSTRAINTS clause.</span></span>  
  
###  <a name="how-to-bulk-load-files-into-a-filetable"></a><a name="HowToBulkLoad"></a> <span data-ttu-id="03177-149">如何：將檔案大量載入 FileTable</span><span class="sxs-lookup"><span data-stu-id="03177-149">How To: Bulk Load Files into a FileTable</span></span>  
 <span data-ttu-id="03177-150">您可以使用各種方法將檔案大量載入 FileTable：</span><span class="sxs-lookup"><span data-stu-id="03177-150">You can use various methods to bulk load files into a FileTable:</span></span>  
  
-   <span data-ttu-id="03177-151">**bcp**</span><span class="sxs-lookup"><span data-stu-id="03177-151">**bcp**</span></span>  
  
    -   <span data-ttu-id="03177-152">使用 **CHECK_CONSTRAINTS** 子句呼叫。</span><span class="sxs-lookup"><span data-stu-id="03177-152">Call with the **CHECK_CONSTRAINTS** clause.</span></span>  
  
    -   <span data-ttu-id="03177-153">停用 FileTable 命名空間，但不使用 **CHECK_CONSTRAINTS** 子句呼叫。</span><span class="sxs-lookup"><span data-stu-id="03177-153">Disable the FileTable namespace and call without the **CHECK_CONSTRAINTS** clause.</span></span> <span data-ttu-id="03177-154">然後重新啟用 FileTable 命名空間。</span><span class="sxs-lookup"><span data-stu-id="03177-154">Then re-enable the FileTable namespace.</span></span>  
  
-   <span data-ttu-id="03177-155">**BULK INSERT**</span><span class="sxs-lookup"><span data-stu-id="03177-155">**BULK INSERT**</span></span>  
  
    -   <span data-ttu-id="03177-156">使用 **CHECK_CONSTRAINTS** 子句呼叫。</span><span class="sxs-lookup"><span data-stu-id="03177-156">Call with the **CHECK_CONSTRAINTS** clause.</span></span>  
  
    -   <span data-ttu-id="03177-157">停用 FileTable 命名空間，但不使用 **CHECK_CONSTRAINTS** 子句呼叫。</span><span class="sxs-lookup"><span data-stu-id="03177-157">Disable the FileTable namespace and call without the **CHECK_CONSTRAINTS** clause.</span></span> <span data-ttu-id="03177-158">然後重新啟用 FileTable 命名空間。</span><span class="sxs-lookup"><span data-stu-id="03177-158">Then re-enable the FileTable namespace.</span></span>  
  
-   <span data-ttu-id="03177-159">**INSERT INTO ...SELECT \* FROM OPENROWSET(BULK ...)**</span><span class="sxs-lookup"><span data-stu-id="03177-159">**INSERT INTO ... SELECT \* FROM OPENROWSET(BULK ...)**</span></span>  
  
    -   <span data-ttu-id="03177-160">使用 **IGNORE_CONSTRAINTS** 子句呼叫。</span><span class="sxs-lookup"><span data-stu-id="03177-160">Call with the **IGNORE_CONSTRAINTS** clause.</span></span>  
  
    -   <span data-ttu-id="03177-161">停用 FileTable 命名空間，且不使用 **IGNORE_CONSTRAINTS** 子句進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="03177-161">Disable the FileTable namespace and call without the **IGNORE_CONSTRAINTS** clause.</span></span> <span data-ttu-id="03177-162">然後重新啟用 FileTable 命名空間。</span><span class="sxs-lookup"><span data-stu-id="03177-162">Then re-enable the FileTable namespace.</span></span>  
  
 <span data-ttu-id="03177-163">如需停用 FileTable 條件約束的詳細資訊，請參閱 [管理 FileTables](manage-filetables.md)。</span><span class="sxs-lookup"><span data-stu-id="03177-163">For information about disabling the FileTable constraints, see [Manage FileTables](manage-filetables.md).</span></span>  
  
###  <a name="how-to-disable-filetable-constraints-for-bulk-loading"></a><a name="disabling"></a> <span data-ttu-id="03177-164">如何：為大量載入停用 FileTable 條件約束</span><span class="sxs-lookup"><span data-stu-id="03177-164">How To: Disable FileTable Constraints for Bulk Loading</span></span>  
 <span data-ttu-id="03177-165">若不希望大量載入檔案至 FileTable 時發生強制啟動系統定義之條件約束負擔，您可暫時停用該條件約束。</span><span class="sxs-lookup"><span data-stu-id="03177-165">To bulk load files into a FileTable without the overhead of enforcing the system-defined constraints, you can temporarily disable the constraints.</span></span> <span data-ttu-id="03177-166">如需詳細資訊，請參閱 [管理作業步驟](manage-filetables.md)。</span><span class="sxs-lookup"><span data-stu-id="03177-166">For more information, see [Manage FileTables](manage-filetables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03177-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03177-167">See Also</span></span>  
 <span data-ttu-id="03177-168">[利用 Transact-SQL 存取 FileTable](access-filetables-with-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="03177-168">[Access FileTables with Transact-SQL](access-filetables-with-transact-sql.md) </span></span>  
 [<span data-ttu-id="03177-169">使用檔案輸入輸出 API 存取 FileTable</span><span class="sxs-lookup"><span data-stu-id="03177-169">Access FileTables with File Input-Output APIs</span></span>](access-filetables-with-file-input-output-apis.md)  
  
  
