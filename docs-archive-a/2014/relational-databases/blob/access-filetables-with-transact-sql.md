---
title: 利用 Transact-SQL 存取 FileTable | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], accessing files with T-SQL
ms.assetid: 3c4a5ffb-c521-4696-99cb-2b03cffc9c02
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2c47751ef34747e1b3742accf5040846ecde074f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705181"
---
# <a name="access-filetables-with-transact-sql"></a><span data-ttu-id="ac36f-102">利用 Transact-SQL 存取 FileTable</span><span class="sxs-lookup"><span data-stu-id="ac36f-102">Access FileTables with Transact-SQL</span></span>
  <span data-ttu-id="ac36f-103">描述 [!INCLUDE[tsql](../../includes/tsql-md.md)] 資料操作語言 (DML) 命令如何與 FileTable 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="ac36f-103">Describes how [!INCLUDE[tsql](../../includes/tsql-md.md)] data manipulation language (DML) commands work with FileTables.</span></span>  
  
##  <a name="insert-operations-on-filetables"></a><a name="BasicsInsert"></a> <span data-ttu-id="ac36f-104">FileTable 上的 INSERT 作業</span><span class="sxs-lookup"><span data-stu-id="ac36f-104">INSERT Operations on FileTables</span></span>  
 <span data-ttu-id="ac36f-105">下列考量適用於 FileTable 上的 **INSERT** 作業：</span><span class="sxs-lookup"><span data-stu-id="ac36f-105">The following considerations apply to **INSERT** Operations on FileTables:</span></span>  
  
-   <span data-ttu-id="ac36f-106">所有檔案屬性資料行都有 NOT NULL 條件約束。</span><span class="sxs-lookup"><span data-stu-id="ac36f-106">All the file attribute columns have NOT NULL constraints.</span></span> <span data-ttu-id="ac36f-107">若未明確設定值，則會提供適當的預設值。</span><span class="sxs-lookup"><span data-stu-id="ac36f-107">If values are not explicitly set, then appropriate default values are supplied.</span></span>  
  
-   <span data-ttu-id="ac36f-108">若 INSERT 陳述式設定 **name**、**path_locator**、**parent_path_locator** 或檔案屬性，則會強制執行系統定義的條件約束。</span><span class="sxs-lookup"><span data-stu-id="ac36f-108">System-defined constraints are enforced if the INSERT statement sets the **name**, **path_locator**, **parent_path_locator**, or file attributes.</span></span>  
  
-   <span data-ttu-id="ac36f-109">提供 [GetPathLocator &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/getpathlocator-transact-sql) 函數的檔案系統路徑，應用程式就可以取得檔案或目錄的 **path_locator**。</span><span class="sxs-lookup"><span data-stu-id="ac36f-109">The application can obtain the **path_locator** for a file or directory by providing the file system path to the [GetPathLocator &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/getpathlocator-transact-sql) function.</span></span>  
  
##  <a name="update-operations-on-filetables"></a><a name="BasicsUpdate"></a> <span data-ttu-id="ac36f-110">FileTable 上的 UPDATE 作業</span><span class="sxs-lookup"><span data-stu-id="ac36f-110">UPDATE Operations on FileTables</span></span>  
 <span data-ttu-id="ac36f-111">下列考量適用於 FileTable 上的 **UPDATE** 作業：</span><span class="sxs-lookup"><span data-stu-id="ac36f-111">The following considerations apply to **UPDATE** operations on FileTables:</span></span>  
  
-   <span data-ttu-id="ac36f-112">允許更新任何使用者定義的資料。</span><span class="sxs-lookup"><span data-stu-id="ac36f-112">Updates to any user-defined data are allowed.</span></span>  
  
-   <span data-ttu-id="ac36f-113">若 INSERT 陳述式設定 **name**、**path_locator**、**parent_path_locator** 或檔案屬性，則會強制執行系統定義的條件約束。</span><span class="sxs-lookup"><span data-stu-id="ac36f-113">System-defined constraints are enforced if the INSERT statement sets the **name**, **path_locator**, **parent_path_locator**, or file attributes.</span></span>  
  
-   <span data-ttu-id="ac36f-114">您可以更新 **file_stream** 資料行中的 FILESTREAM 資料，而不影響任何其他資料行 (包括時間戳記)。</span><span class="sxs-lookup"><span data-stu-id="ac36f-114">Updates can be made to the FILESTREAM data in the **file_stream** column without affecting any of the other columns, including the timestamps.</span></span>  
  
##  <a name="delete-operations-on-filetables"></a><a name="BasicsDelete"></a> <span data-ttu-id="ac36f-115">FileTable 上的 DELETE 作業</span><span class="sxs-lookup"><span data-stu-id="ac36f-115">DELETE Operations on FileTables</span></span>  
 <span data-ttu-id="ac36f-116">下列考量適用於 FileTable 上的 **DELETE** 作業：</span><span class="sxs-lookup"><span data-stu-id="ac36f-116">The following considerations apply to **DELETE** operations on FileTables:</span></span>  
  
-   <span data-ttu-id="ac36f-117">刪除資料列也會從檔案系統中移除對應的檔案或目錄。</span><span class="sxs-lookup"><span data-stu-id="ac36f-117">Deleting a row also removes the corresponding file or directory from the file system.</span></span>  
  
-   <span data-ttu-id="ac36f-118">若資料列對應至包含其他檔案或目錄的目錄，則無法刪除資料列。</span><span class="sxs-lookup"><span data-stu-id="ac36f-118">Deleting a row fails if the row corresponds to a directory that contains other files or directories.</span></span>  
  
##  <a name="constraints-that-are-enforced-for-dml-operations-on-filetables"></a><a name="BasicsConstraints"></a> <span data-ttu-id="ac36f-119">針對 FileTable 上 DML 作業強制執行的條件約束</span><span class="sxs-lookup"><span data-stu-id="ac36f-119">Constraints That Are Enforced for DML Operations on FileTables</span></span>  
 <span data-ttu-id="ac36f-120">系統定義的條件約束可確保 DML 動作不會危害檔案命名空間階層的完整性。</span><span class="sxs-lookup"><span data-stu-id="ac36f-120">System-defined constraints ensure that DML actions do not compromise the integrity of the file namespace hierarchy.</span></span> <span data-ttu-id="ac36f-121">強制執行的條件約束包括：</span><span class="sxs-lookup"><span data-stu-id="ac36f-121">The constraints that are enforced include the following:</span></span>  
  
-   <span data-ttu-id="ac36f-122">當您設定或變更檔案或目錄的 **名稱** 時：</span><span class="sxs-lookup"><span data-stu-id="ac36f-122">When you set or change the **name** of the file or directory:</span></span>  
  
    -   <span data-ttu-id="ac36f-123">會強制執行 Windows 檔案及目錄命名慣例。</span><span class="sxs-lookup"><span data-stu-id="ac36f-123">Windows file and directory naming conventions are enforced.</span></span>  
  
    -   <span data-ttu-id="ac36f-124">會強制執行上層目錄中名稱的唯一性。</span><span class="sxs-lookup"><span data-stu-id="ac36f-124">The uniqueness of the name in the parent directory is enforced.</span></span>  
  
-   <span data-ttu-id="ac36f-125">當您設定或變更 **path_locator** 或 **parent_path_locator**以設定或變更檔案或目錄的位置時：</span><span class="sxs-lookup"><span data-stu-id="ac36f-125">When you set or change the location of a file or directory by setting or changing the **path_locator** or **parent_path_locator**:</span></span>  
  
    -   <span data-ttu-id="ac36f-126">會強制執行唯一性。</span><span class="sxs-lookup"><span data-stu-id="ac36f-126">Uniqueness is enforced.</span></span>  
  
    -   <span data-ttu-id="ac36f-127">會強制執行目錄和檔案之階層樹狀目錄的一致性 (包括 **path_locator** 和 **parent_path_locator** 值的一致性)。</span><span class="sxs-lookup"><span data-stu-id="ac36f-127">The consistency of the hierarchical tree of directories and files is enforced, including the consistency of **path_locator** and **parent_path_locator** values.</span></span>  
  
-   <span data-ttu-id="ac36f-128">當 **file_stream** 資料行不是 Null 時，則無法將 **is_directory** 的值設定為 true。</span><span class="sxs-lookup"><span data-stu-id="ac36f-128">The value of **is_directory** cannot be set to true when the **file_stream** column is not null.</span></span> <span data-ttu-id="ac36f-129">**file_stream** 資料行中的資料指出資料列代表檔案，而非代表目錄。</span><span class="sxs-lookup"><span data-stu-id="ac36f-129">Data in the **file_stream** column indicates that the row represents a file and not a directory.</span></span>  
  
-   <span data-ttu-id="ac36f-130">檔案屬性資料行不得為 Null。</span><span class="sxs-lookup"><span data-stu-id="ac36f-130">File attribute columns cannot be null.</span></span> <span data-ttu-id="ac36f-131">會使用預設值強制執行 NOT NULL 條件約束。</span><span class="sxs-lookup"><span data-stu-id="ac36f-131">NOT NULL constraints are enforced with default values.</span></span>  
  
-   <span data-ttu-id="ac36f-132">**last_access_time** 的值不能早於 **last_write_time** 和 **creation_time**。</span><span class="sxs-lookup"><span data-stu-id="ac36f-132">The value of **last_access_time** cannot be earlier than **last_write_time** and **creation_time**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac36f-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac36f-133">See Also</span></span>  
 <span data-ttu-id="ac36f-134">[載入檔案至 FileTable](load-files-into-filetables.md) </span><span class="sxs-lookup"><span data-stu-id="ac36f-134">[Load Files into FileTables](load-files-into-filetables.md) </span></span>  
 <span data-ttu-id="ac36f-135">[Work with Directories and Paths in FileTables](work-with-directories-and-paths-in-filetables.md) </span><span class="sxs-lookup"><span data-stu-id="ac36f-135">[Work with Directories and Paths in FileTables](work-with-directories-and-paths-in-filetables.md) </span></span>  
 <span data-ttu-id="ac36f-136">[使用檔案輸入輸出 API 存取 FileTable](access-filetables-with-file-input-output-apis.md) </span><span class="sxs-lookup"><span data-stu-id="ac36f-136">[Access FileTables with File Input-Output APIs](access-filetables-with-file-input-output-apis.md) </span></span>  
 [<span data-ttu-id="ac36f-137">FileTable DDL、函數、預存程序及檢視</span><span class="sxs-lookup"><span data-stu-id="ac36f-137">FileTable DDL, Functions, Stored Procedures, and Views</span></span>](../views/views.md)  
  
  
