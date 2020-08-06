---
title: FileTables (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 07/06/2016
ms.prod: sql-server-2014
ms.technology: filestream
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], overview
- FileTables [SQL Server]
- FileTable [SQL Server], see FileTables [SQL Server]
- FileTable [SQL Server]
ms.assetid: a57b629c-e9ed-48fd-9a48-ed3787d80c8f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6c0a38f0e947b0c4f68a49e13a40071f6a30cd07
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707617"
---
# <a name="filetables-sql-server"></a><span data-ttu-id="64ef9-102">FileTable (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="64ef9-102">FileTables (SQL Server)</span></span>
  <span data-ttu-id="64ef9-103">FileTable 功能可將 Windows 檔案命名空間的支援以及與 Windows 應用程式的相容性提供給儲存在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中的檔案資料。</span><span class="sxs-lookup"><span data-stu-id="64ef9-103">The FileTable feature brings support for the Windows file namespace and compatibility with Windows applications to the file data stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="64ef9-104">FileTable 可讓應用程式整合其儲存和資料管理元件，並且透過非結構化資料和中繼資料提供整合式 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務 (包含全文檢索搜尋和語意搜尋)。</span><span class="sxs-lookup"><span data-stu-id="64ef9-104">FileTable lets an application integrate its storage and data management components, and provides integrated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services - including full-text search and semantic search - over unstructured data and metadata.</span></span>  
  
 <span data-ttu-id="64ef9-105">換句話說，您可以將檔案和文件儲存在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的特殊資料表 (稱為 FileTable) 中，而從 Windows 應用程式存取它們，就像它們儲存在檔案系統中一樣，並不需要對用戶端應用程式進行任何變更。</span><span class="sxs-lookup"><span data-stu-id="64ef9-105">In other words, you can store files and documents in special tables in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] called FileTables, but access them from Windows applications as if they were stored in the file system, without making any changes to your client applications.</span></span>  
  
 <span data-ttu-id="64ef9-106">FileTable 功能是根據 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] FILESTREAM 技術所建立。</span><span class="sxs-lookup"><span data-stu-id="64ef9-106">The FileTable feature builds on top of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] FILESTREAM technology.</span></span> <span data-ttu-id="64ef9-107">若要深入了解 FILESTREAM，請參閱 [FILESTREAM &#40;SQL Server&#41;](filestream-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="64ef9-107">To learn more about FILESTREAM, see [FILESTREAM &#40;SQL Server&#41;](filestream-sql-server.md).</span></span>  
  
##  <a name="benefits-of-the-filetable-feature"></a><a name="Goals"></a> <span data-ttu-id="64ef9-108">FileTable 功能的優點</span><span class="sxs-lookup"><span data-stu-id="64ef9-108">Benefits of the FileTable Feature</span></span>  
 <span data-ttu-id="64ef9-109">FileTable 功能的目標包括：</span><span class="sxs-lookup"><span data-stu-id="64ef9-109">The goals of the FileTable feature include the following:</span></span>  
  
-   <span data-ttu-id="64ef9-110">儲存在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫內檔案資料的 Windows API 相容性。</span><span class="sxs-lookup"><span data-stu-id="64ef9-110">Windows API compatibility for file data stored within a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="64ef9-111">Windows API 相容性包括下列項目：</span><span class="sxs-lookup"><span data-stu-id="64ef9-111">Windows API compatibility includes the following:</span></span>  
  
    -   <span data-ttu-id="64ef9-112">FILESTREAM 資料的非交易式資料流存取和就地更新。</span><span class="sxs-lookup"><span data-stu-id="64ef9-112">Non-transactional streaming access and in-place updates to FILESTREAM data.</span></span>  
  
    -   <span data-ttu-id="64ef9-113">目錄和檔案的階層式命名空間。</span><span class="sxs-lookup"><span data-stu-id="64ef9-113">A hierarchical namespace of directories and files.</span></span>  
  
    -   <span data-ttu-id="64ef9-114">檔案屬性的儲存，例如建立日期和修改日期。</span><span class="sxs-lookup"><span data-stu-id="64ef9-114">Storage of file attributes, such as created date and modified date.</span></span>  
  
    -   <span data-ttu-id="64ef9-115">Windows 檔案和目錄管理 API 的支援。</span><span class="sxs-lookup"><span data-stu-id="64ef9-115">Support for Windows file and directory management APIs.</span></span>  
  
-   <span data-ttu-id="64ef9-116">與其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能的相容性，包括針對 FILESTREAM 和檔案屬性資料進行的管理工具、服務和關聯式查詢功能。</span><span class="sxs-lookup"><span data-stu-id="64ef9-116">Compatibility with other [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features including management tools, services, and relational query capabilities over FILESTREAM and file attribute data.</span></span>  
  
 <span data-ttu-id="64ef9-117">因此，FileTable 會移除一道重大障礙，可讓您使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 來儲存和管理目前位於檔案伺服器上之檔案的非結構化資料。</span><span class="sxs-lookup"><span data-stu-id="64ef9-117">Thus FileTables remove a significant barrier to the use of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for the storage and management of unstructured data that is currently residing as files on file servers.</span></span> <span data-ttu-id="64ef9-118">企業可以將這項資料從檔案伺服器移入 FileTable，以便運用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]所提供的整合式管理和服務。</span><span class="sxs-lookup"><span data-stu-id="64ef9-118">Enterprises can move this data from file servers into FileTables to take advantage of integrated administration and services provided by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="64ef9-119">同時，企業可以針對將這項資料視為檔案系統中之檔案的現有 Windows 應用程式，維持 Windows 應用程式相容性。</span><span class="sxs-lookup"><span data-stu-id="64ef9-119">At the same time, they can maintain Windows application compatibility for their existing Windows applications that see this data as files in the file system.</span></span>  
    
##  <a name="what-is-a-filetable"></a><a name="Description"></a> <span data-ttu-id="64ef9-120">何謂 FileTable</span><span class="sxs-lookup"><span data-stu-id="64ef9-120">What Is a FileTable?</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="64ef9-121">對於需要將檔案和目錄儲存在資料庫中、具備 Windows API 相容性和非交易式存取的應用程式而言，提供特殊的 **檔案資料表**(也稱為 **FileTable**)。</span><span class="sxs-lookup"><span data-stu-id="64ef9-121">provides a special **table of files**, also referred to as a **FileTable**, for applications that require file and directory storage in the database, with Windows API compatibility and non-transactional access.</span></span> <span data-ttu-id="64ef9-122">FileTable 是包含預先定義結構描述的特殊化使用者資料表，可儲存 FILESTREAM 資料、檔案和目錄階層資訊，以及檔案屬性。</span><span class="sxs-lookup"><span data-stu-id="64ef9-122">A FileTable is a specialized user table with a pre-defined schema that stores FILESTREAM data, as well as file and directory hierarchy information and file attributes.</span></span>  
  
 <span data-ttu-id="64ef9-123">FileTable 提供了下列功能：</span><span class="sxs-lookup"><span data-stu-id="64ef9-123">A FileTable provides the following functionality:</span></span>  
  
-   <span data-ttu-id="64ef9-124">FileTable 代表目錄和檔案的階層。</span><span class="sxs-lookup"><span data-stu-id="64ef9-124">A FileTable represents a hierarchy of directories and files.</span></span> <span data-ttu-id="64ef9-125">它會儲存與該階層中所有節點相關的資料 (目錄以及它們所包含的檔案)。</span><span class="sxs-lookup"><span data-stu-id="64ef9-125">It stores data related to all the nodes in that hierarchy, for both directories and the files they contain.</span></span> <span data-ttu-id="64ef9-126">這個階層是從您建立 FileTable 時指定的根目錄開始。</span><span class="sxs-lookup"><span data-stu-id="64ef9-126">This hierarchy starts from a root directory that you specify when you create the FileTable.</span></span>  
  
-   <span data-ttu-id="64ef9-127">FileTable 中的每個資料列都代表一個檔案或目錄。</span><span class="sxs-lookup"><span data-stu-id="64ef9-127">Every row in a FileTable represents a file or a directory.</span></span>  
  
-   <span data-ttu-id="64ef9-128">每個資料列都包含下列項目。</span><span class="sxs-lookup"><span data-stu-id="64ef9-128">Every row contains the following items.</span></span> <span data-ttu-id="64ef9-129">如需 FileTable 結構描述的詳細資訊，請參閱 [FileTable 結構描述](filetable-schema.md)。</span><span class="sxs-lookup"><span data-stu-id="64ef9-129">For more information about the schema of a FileTable, see [FileTable Schema](filetable-schema.md).</span></span>  
  
    -   <span data-ttu-id="64ef9-130">資料流資料的**file_stream** 資料行和 **stream_id** (GUID) 識別碼</span><span class="sxs-lookup"><span data-stu-id="64ef9-130">A**file_stream** column for stream data and a **stream_id** (GUID) identifier.</span></span> <span data-ttu-id="64ef9-131">(目錄的 **file_stream** 資料行為 NULL)。</span><span class="sxs-lookup"><span data-stu-id="64ef9-131">(The **file_stream** column is NULL for a directory.)</span></span>  
  
    -   <span data-ttu-id="64ef9-132">用於代表和維護檔案與目錄階層的 **path_locator** 和 **parent_path_locator** 資料行。</span><span class="sxs-lookup"><span data-stu-id="64ef9-132">Both **path_locator** and **parent_path_locator** columns for representing and maintaining the file and directory hierarchy.</span></span>  
  
    -   <span data-ttu-id="64ef9-133">檔案 I/O API 可用的 10 個檔案屬性，例如建立日期和修改日期。</span><span class="sxs-lookup"><span data-stu-id="64ef9-133">10 file attributes such as created date and modified date that are useful with file I/O APIs.</span></span>  
  
    -   <span data-ttu-id="64ef9-134">支援針對檔案和文件進行全文檢索搜尋和語意搜尋的類型資料行。</span><span class="sxs-lookup"><span data-stu-id="64ef9-134">A type column that supports full-text search and semantic search over files and documents.</span></span>  
  
-   <span data-ttu-id="64ef9-135">FileTable 會強制執行特定系統定義的條件約束和觸發程序來維護檔案命名空間語意。</span><span class="sxs-lookup"><span data-stu-id="64ef9-135">A FileTable enforces certain system-defined constraints and triggers to maintain file namespace semantics.</span></span>  
  
-   <span data-ttu-id="64ef9-136">當您針對非交易式存取設定資料庫時，就會透過針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體所設定的 FILESTREAM 共用來公開以 FileTable 表示的檔案和目錄階層。</span><span class="sxs-lookup"><span data-stu-id="64ef9-136">When the database is configured for non-transactional access, the file and directory hierarchy represented in the FileTable is exposed under the FILESTREAM share configured for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="64ef9-137">這會提供 Windows 應用程式的檔案系統存取。</span><span class="sxs-lookup"><span data-stu-id="64ef9-137">This provides file system access for Windows applications.</span></span>  
  
 <span data-ttu-id="64ef9-138">FileTable 的某些其他特性包括：</span><span class="sxs-lookup"><span data-stu-id="64ef9-138">Some additional characteristics of FileTables include the following:</span></span>  
  
-   <span data-ttu-id="64ef9-139">儲存在 FileTable 中的檔案和目錄資料會透過 Windows API 架構應用程式之非交易式檔案存取的 Windows 共用公開。</span><span class="sxs-lookup"><span data-stu-id="64ef9-139">The file and directory data stored in a FileTable is exposed through a Windows share for non-transactional file access for Windows API based applications.</span></span> <span data-ttu-id="64ef9-140">針對 Windows 應用程式，這看起來就像含有其檔案和目錄的一般共用。</span><span class="sxs-lookup"><span data-stu-id="64ef9-140">For a Windows application, this looks like a normal share with its files and directories.</span></span> <span data-ttu-id="64ef9-141">應用程式可以使用一組豐富的 Windows API，來管理此共用下的檔案和目錄。</span><span class="sxs-lookup"><span data-stu-id="64ef9-141">Applications can use a rich set of Windows APIs to manage the files and directories under this share.</span></span>  
  
-   <span data-ttu-id="64ef9-142">透過此共用顯示的目錄階層就是在 FileTable 內部維護的單純邏輯目錄結構。</span><span class="sxs-lookup"><span data-stu-id="64ef9-142">The directory hierarchy surfaced through the share is a purely logical directory structure that is maintained within the FileTable.</span></span>  
  
-   <span data-ttu-id="64ef9-143">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件會攔截透過 Windows 共用建立或變更檔案或目錄的呼叫，然後將它們反映在 FileTable 的對應關聯式資料中。</span><span class="sxs-lookup"><span data-stu-id="64ef9-143">Calls to create or change a file or directory through the Windows share are intercepted by a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] component and reflected in the corresponding relational data in the FileTable.</span></span>  
  
-   <span data-ttu-id="64ef9-144">Windows API 作業的本質為非交易式，而且並未與使用者交易相關聯。</span><span class="sxs-lookup"><span data-stu-id="64ef9-144">Windows API operations are non-transactional in nature, and are not associated with user transactions.</span></span> <span data-ttu-id="64ef9-145">不過，系統完全支援儲存在 FileTable 中之 FILESTREAM 資料的交易式存取，就如同一般資料表中的任何 FILESTREAM 資料行。</span><span class="sxs-lookup"><span data-stu-id="64ef9-145">However, transactional access to FILESTREAM data stored in a FileTable is fully supported, as is the case for any FILESTREAM column in a regular table.</span></span>  
  
-   <span data-ttu-id="64ef9-146">FileTable 也可以透過一般 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存取進行查詢和更新。</span><span class="sxs-lookup"><span data-stu-id="64ef9-146">FileTables can also be queried and updated through normal [!INCLUDE[tsql](../../includes/tsql-md.md)] access.</span></span> <span data-ttu-id="64ef9-147">它們也會與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理工具和備份等功能整合。</span><span class="sxs-lookup"><span data-stu-id="64ef9-147">They are also integrated with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] management tools, and features such as backup.</span></span>  
  
  
##  <a name="additional-considerations-for-using-filetables"></a><a name="additional"></a> <span data-ttu-id="64ef9-148">使用 FileTable 的額外考量</span><span class="sxs-lookup"><span data-stu-id="64ef9-148">Additional Considerations for Using FileTables</span></span>  
  
###  <a name="administrative-considerations"></a><a name="DBA"></a> <span data-ttu-id="64ef9-149">管理考量</span><span class="sxs-lookup"><span data-stu-id="64ef9-149">Administrative Considerations</span></span>  
 <span data-ttu-id="64ef9-150">**關於 FILESTREAM 和 FileTable**</span><span class="sxs-lookup"><span data-stu-id="64ef9-150">**About FILESTREAM and FileTables**</span></span>  
  
-   <span data-ttu-id="64ef9-151">您可以分別設定 FileTable 與 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="64ef9-151">You configure FileTables separately from FILESTREAM.</span></span> <span data-ttu-id="64ef9-152">因此，您可以繼續使用 FILESTREAM 功能，而不需要啟用非交易式存取或建立 FileTable。</span><span class="sxs-lookup"><span data-stu-id="64ef9-152">Therefore you can continue to use the FILESTREAM feature without enabling non-transactional access or creating FileTables.</span></span>  
  
-   <span data-ttu-id="64ef9-153">除了透過 FileTable 以外，沒有 FILESTREAM 資料的非交易式存取。</span><span class="sxs-lookup"><span data-stu-id="64ef9-153">There is no non-transactional access to FILESTREAM data except through FileTables.</span></span> <span data-ttu-id="64ef9-154">因此，當您啟用非交易式存取時，並不會影響現有 FILESTREAM 資料行和應用程式的行為。</span><span class="sxs-lookup"><span data-stu-id="64ef9-154">Therefore, when you enable non-transactional access, the behavior of existing FILESTREAM columns and applications is not affected.</span></span>  
  
 <span data-ttu-id="64ef9-155">**關於 FileTable 和非交易式存取**</span><span class="sxs-lookup"><span data-stu-id="64ef9-155">**About FileTables and non-transactional access**</span></span>  
  
-   <span data-ttu-id="64ef9-156">您可以在資料庫層級中啟用或停用非交易式存取。</span><span class="sxs-lookup"><span data-stu-id="64ef9-156">You can enable or disable non-transactional access at the database level.</span></span>  
  
-   <span data-ttu-id="64ef9-157">您可以在資料庫層級中設定或微調非交易式存取，方法是關閉它，或是啟用唯讀或完整讀取/寫入存取。</span><span class="sxs-lookup"><span data-stu-id="64ef9-157">You can configure or fine-tune non-transactional access at the database level by turning it off, or by enabling read only or full read/write access.</span></span>  
  
  
###  <a name="filetables-do-not-support-memory-mapped-files"></a><a name="memory"></a> <span data-ttu-id="64ef9-158">FileTable 不支援記憶體對應檔案</span><span class="sxs-lookup"><span data-stu-id="64ef9-158">FileTables Do Not Support Memory-Mapped Files</span></span>  
 <span data-ttu-id="64ef9-159">FileTable 不支援記憶體對應檔案。</span><span class="sxs-lookup"><span data-stu-id="64ef9-159">FileTables do not support memory-mapped files.</span></span> <span data-ttu-id="64ef9-160">記事本和小畫家是使用記憶體對應檔案的兩個常見的應用程式例子。</span><span class="sxs-lookup"><span data-stu-id="64ef9-160">Notepad and Paint are two common examples of applications that use memory-mapped files.</span></span> <span data-ttu-id="64ef9-161">不能在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所在的電腦上使用這些應用程式來開啟儲存在 FileTable 中的檔案。</span><span class="sxs-lookup"><span data-stu-id="64ef9-161">You cannot use these applications on the same computer as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to open files that are stored in a FileTable.</span></span> <span data-ttu-id="64ef9-162">但是，可以從遠端電腦使用這些應用程式來開啟儲存在 FileTable 中的檔案，因為在這些情況下不使用記憶體對應功能。</span><span class="sxs-lookup"><span data-stu-id="64ef9-162">However you can use these applications from a remote computer to open files that are stored in a FileTable, because in these circumstances the memory-mapping feature is not used.</span></span>  
  
  
##  <a name="related-tasks"></a><a name="reltasks"></a> <span data-ttu-id="64ef9-163">相關工作</span><span class="sxs-lookup"><span data-stu-id="64ef9-163">Related Tasks</span></span>  
 [<span data-ttu-id="64ef9-164">啟用 FileTable 的必要條件</span><span class="sxs-lookup"><span data-stu-id="64ef9-164">Enable the Prerequisites for FileTable</span></span>](enable-the-prerequisites-for-filetable.md)  
 <span data-ttu-id="64ef9-165">描述如何啟用建立和使用 FileTable 的必要元件。</span><span class="sxs-lookup"><span data-stu-id="64ef9-165">Describes how to enable the prerequisites for creating and using FileTables.</span></span>  
  
 [<span data-ttu-id="64ef9-166">建立、改變及卸除 FileTable</span><span class="sxs-lookup"><span data-stu-id="64ef9-166">Create, Alter, and Drop FileTables</span></span>](create-alter-and-drop-filetables.md)  
 <span data-ttu-id="64ef9-167">描述如何建立新的 FileTable，或是改變或卸除現有的 FileTable。</span><span class="sxs-lookup"><span data-stu-id="64ef9-167">Describes how to create a new FileTable, or alter or drop an existing FileTable.</span></span>  
  
 [<span data-ttu-id="64ef9-168">載入檔案至 FileTable</span><span class="sxs-lookup"><span data-stu-id="64ef9-168">Load Files into FileTables</span></span>](load-files-into-filetables.md)  
 <span data-ttu-id="64ef9-169">描述如何載入或移轉檔案至 FileTable 中。</span><span class="sxs-lookup"><span data-stu-id="64ef9-169">Describes how to load or migrate files into FileTables.</span></span>  
  
 [<span data-ttu-id="64ef9-170">使用 FileTable 中的目錄與路徑</span><span class="sxs-lookup"><span data-stu-id="64ef9-170">Work with Directories and Paths in FileTables</span></span>](work-with-directories-and-paths-in-filetables.md)  
 <span data-ttu-id="64ef9-171">描述在 FileTable 中儲存檔案的目錄結構。</span><span class="sxs-lookup"><span data-stu-id="64ef9-171">Describes the directory structure in which the files are stored in FileTables.</span></span>  
  
 [<span data-ttu-id="64ef9-172">利用 Transact-SQL 存取 FileTable</span><span class="sxs-lookup"><span data-stu-id="64ef9-172">Access FileTables with Transact-SQL</span></span>](access-filetables-with-transact-sql.md)  
 <span data-ttu-id="64ef9-173">描述 Transact-SQL 資料操作語言 (DML) 命令如何與 FileTable 搭配運作。</span><span class="sxs-lookup"><span data-stu-id="64ef9-173">Describes how Transact-SQL data manipulation language (DML) commands work with FileTables.</span></span>  
  
 [<span data-ttu-id="64ef9-174">使用檔案輸入輸出 API 存取 FileTable</span><span class="sxs-lookup"><span data-stu-id="64ef9-174">Access FileTables with File Input-Output APIs</span></span>](access-filetables-with-file-input-output-apis.md)  
 <span data-ttu-id="64ef9-175">描述檔案系統 I/O 如何在 FileTable 上運作。</span><span class="sxs-lookup"><span data-stu-id="64ef9-175">Describes how file system I/O works on a FileTable.</span></span>  
  
 [<span data-ttu-id="64ef9-176">管理 FileTable</span><span class="sxs-lookup"><span data-stu-id="64ef9-176">Manage FileTables</span></span>](manage-filetables.md)  
 <span data-ttu-id="64ef9-177">描述用於管理 FileTable 的常見管理工作。</span><span class="sxs-lookup"><span data-stu-id="64ef9-177">Describes common administrative tasks for managing FileTables.</span></span>  
  
  
##  <a name="related-content"></a><a name="relcontent"></a> <span data-ttu-id="64ef9-178">相關內容</span><span class="sxs-lookup"><span data-stu-id="64ef9-178">Related Content</span></span>  
 [<span data-ttu-id="64ef9-179">FileTable 結構描述</span><span class="sxs-lookup"><span data-stu-id="64ef9-179">FileTable Schema</span></span>](filetable-schema.md)  
 <span data-ttu-id="64ef9-180">描述 FileTable 預先定義且固定的結構描述。</span><span class="sxs-lookup"><span data-stu-id="64ef9-180">Describes the pre-defined and fixed schema of a FileTable.</span></span>  
  
 [<span data-ttu-id="64ef9-181">FileTable 與其他 SQL Server 功能的相容性</span><span class="sxs-lookup"><span data-stu-id="64ef9-181">FileTable Compatibility with Other SQL Server Features</span></span>](filetable-compatibility-with-other-sql-server-features.md)  
 <span data-ttu-id="64ef9-182">描述 FileTable 如何搭配其他的 SQL Server 功能一起運作。</span><span class="sxs-lookup"><span data-stu-id="64ef9-182">Describes how FileTables work with other features of SQL Server.</span></span>  
  
 [<span data-ttu-id="64ef9-183">FileTable DDL、函數、預存程序及檢視</span><span class="sxs-lookup"><span data-stu-id="64ef9-183">FileTable DDL, Functions, Stored Procedures, and Views</span></span>](../views/views.md)  
 <span data-ttu-id="64ef9-184">列出已加入或變更以支援 FileTable 功能的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="64ef9-184">Lists the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database objects that have been added or changed to support the FileTable feature.</span></span>  
  
 
  
