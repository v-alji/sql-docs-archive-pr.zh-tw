---
title: 比較用於儲存 Blob 的選項 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: filestream
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 6038697b-36a9-49e8-a02a-2ad9e2e60e5a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c7f0d15950a8663852c84c4edbb8177e918a8895
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599024"
---
# <a name="compare-options-for-storing-blobs-sql-server"></a><span data-ttu-id="141dc-102">比較用於儲存 Blob 的選項 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="141dc-102">Compare Options for Storing Blobs (SQL Server)</span></span>
  <span data-ttu-id="141dc-103">討論和比較 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中儲存檔案和文件的可用選項。</span><span class="sxs-lookup"><span data-stu-id="141dc-103">Discusses and compares the options that are available for storing files and documents in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
##  <a name="storing-files-in-the-database---benefits-and-expectations"></a><a name="Expectations"></a> <span data-ttu-id="141dc-104">在資料庫中儲存檔案 - 優點和期望</span><span class="sxs-lookup"><span data-stu-id="141dc-104">Storing Files in the Database - Benefits and Expectations</span></span>  
 <span data-ttu-id="141dc-105">大部分企業資料的本質都是非結構化，而且通常會在檔案系統中儲存成檔案和文件。</span><span class="sxs-lookup"><span data-stu-id="141dc-105">A large percentage of enterprise data is unstructured in nature, and is typically stored as files and documents in file systems.</span></span> <span data-ttu-id="141dc-106">其中大多數資料是由透過 Windows API 存取檔案的應用程式所產生、管理和取用。</span><span class="sxs-lookup"><span data-stu-id="141dc-106">Most of this data is produced, managed and consumed by applications that access the files through Windows APIs.</span></span> <span data-ttu-id="141dc-107">企業通常會將這項資料保存在檔案系統中，而將檔案的相關中繼資料儲存在關聯式資料庫中。</span><span class="sxs-lookup"><span data-stu-id="141dc-107">Enterprises typically keep this data in the file system, while storing the related metadata for the files in a relational database.</span></span>  
  
 <span data-ttu-id="141dc-108">將非結構化資料整合至關聯式資料庫，提供重要的優點。</span><span class="sxs-lookup"><span data-stu-id="141dc-108">Integrating unstructured data into the relational database provides significant benefits.</span></span> <span data-ttu-id="141dc-109">這些優點包括：</span><span class="sxs-lookup"><span data-stu-id="141dc-109">These benefits include the following:</span></span>  
  
-   <span data-ttu-id="141dc-110">整合式儲存和資料管理功能，例如備份。</span><span class="sxs-lookup"><span data-stu-id="141dc-110">Integrated storage and data management capabilities such as backup.</span></span>  
  
-   <span data-ttu-id="141dc-111">整合式服務，例如針對資料和中繼資料進行全文檢索搜尋和語意搜尋。</span><span class="sxs-lookup"><span data-stu-id="141dc-111">Integrated services such as full-text search and semantic search over data and metadata.</span></span>  
  
-   <span data-ttu-id="141dc-112">輕易地針對非結構化資料進行管理和原則管理。</span><span class="sxs-lookup"><span data-stu-id="141dc-112">Ease of administration and policy management over the unstructured data.</span></span>  
  
 <span data-ttu-id="141dc-113">不過，在大部分情況下，將非結構化資料儲存在關聯式資料庫中並不是那麼方便。</span><span class="sxs-lookup"><span data-stu-id="141dc-113">For the most part, however, it has not been convenient to store unstructured data in a relational database.</span></span> <span data-ttu-id="141dc-114">先前一直無法在關聯式系統上執行以 Windows 為基礎的現有應用程式。</span><span class="sxs-lookup"><span data-stu-id="141dc-114">It has not previously been possible to run existing Windows-based applications on top of relational systems.</span></span> <span data-ttu-id="141dc-115">將已建立的應用程式 (例如 Microsoft Word 或 Adobe Reader) 重寫成可在關聯式資料庫 API 上執行並不實用。</span><span class="sxs-lookup"><span data-stu-id="141dc-115">It is not practical to rewrite established applications (such as Microsoft Word or Adobe Reader) to run on top relational database APIs.</span></span> <span data-ttu-id="141dc-116">這些應用程式只期望能夠透過 Windows API 存取資料。</span><span class="sxs-lookup"><span data-stu-id="141dc-116">These applications simply expect the data to be accessible through Windows APIs.</span></span> <span data-ttu-id="141dc-117">換言之，這些期望包括：</span><span class="sxs-lookup"><span data-stu-id="141dc-117">In other words, the expectations include the following:</span></span>  
  
-   <span data-ttu-id="141dc-118">Windows 應用程式無法識別資料庫交易而且不需要它們。</span><span class="sxs-lookup"><span data-stu-id="141dc-118">Windows applications are not aware of database transactions and do not require them.</span></span>  
  
-   <span data-ttu-id="141dc-119">Windows 應用程式需要與檔案和目錄資料的檔案系統 API 相容。</span><span class="sxs-lookup"><span data-stu-id="141dc-119">Windows applications require compatibility with file system APIs for file and directory data.</span></span>  
  
##  <a name="filestream"></a><a name="Filestream"></a> <span data-ttu-id="141dc-120">FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="141dc-120">FILESTREAM</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="141dc-121">已經具有 FILESTREAM 功能，可針對在檔案系統上儲存成檔案的非結構化資料提供有效率的儲存、管理及資料流處理。</span><span class="sxs-lookup"><span data-stu-id="141dc-121">already has the FILESTREAM feature, which provides efficient storage, management and streaming of unstructured data stored as files on the file system.</span></span> <span data-ttu-id="141dc-122">不過，FILESTREAM 解決方案需要自訂程式設計，因此無法滿足上述完整 Windows 應用程式相容性的需求。</span><span class="sxs-lookup"><span data-stu-id="141dc-122">However, a FILESTREAM solution requires custom programming, and does not satisfy the requirement for full Windows application compatibility described above.</span></span>  
  
##  <a name="filetables"></a><a name="FileTables"></a> <span data-ttu-id="141dc-123">FileTable</span><span class="sxs-lookup"><span data-stu-id="141dc-123">FileTables</span></span>  
 <span data-ttu-id="141dc-124">FileTable 功能是以現有的 FILESTREAM 功能為建置基礎，透過處理檔案架構資料之非交易式存取和 Windows 應用程式相容性的需求，讓企業客戶能夠在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫中儲存非結構化檔案資料和目錄階層。</span><span class="sxs-lookup"><span data-stu-id="141dc-124">The FileTable feature builds on top of existing FILESTREAM capabilities to enable enterprise customers to store unstructured file data and directory hierarchies in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, by addressing the requirements for non-transactional access and Windows application compatibility for file-based data.</span></span>  
  
##  <a name="comparing-filestream-and-filetable"></a><a name="CompareFileTable"></a> <span data-ttu-id="141dc-125">比較 FILESTREAM 與 FileTable</span><span class="sxs-lookup"><span data-stu-id="141dc-125">Comparing FILESTREAM and FileTable</span></span>  
  
|<span data-ttu-id="141dc-126">功能</span><span class="sxs-lookup"><span data-stu-id="141dc-126">Feature</span></span>|<span data-ttu-id="141dc-127">檔案伺服器和資料庫解決方案</span><span class="sxs-lookup"><span data-stu-id="141dc-127">File Server and Database Solution</span></span>|<span data-ttu-id="141dc-128">FILESTREAM 解決方案</span><span class="sxs-lookup"><span data-stu-id="141dc-128">FILESTREAM Solution</span></span>|<span data-ttu-id="141dc-129">FileTable 解決方案</span><span class="sxs-lookup"><span data-stu-id="141dc-129">FileTable Solution</span></span>|  
|-------------|---------------------------------------|-------------------------|------------------------|  
|<span data-ttu-id="141dc-130">**管理工作的單一本文**</span><span class="sxs-lookup"><span data-stu-id="141dc-130">**Single story for management tasks**</span></span>|<span data-ttu-id="141dc-131">否</span><span class="sxs-lookup"><span data-stu-id="141dc-131">No</span></span>|<span data-ttu-id="141dc-132">是</span><span class="sxs-lookup"><span data-stu-id="141dc-132">Yes</span></span>|<span data-ttu-id="141dc-133">**是**</span><span class="sxs-lookup"><span data-stu-id="141dc-133">**Yes**</span></span>|  
|<span data-ttu-id="141dc-134">**單一服務集合**：搜尋、報表、查詢等等</span><span class="sxs-lookup"><span data-stu-id="141dc-134">**Single set of services**: search, reporting, querying, and so forth</span></span>|<span data-ttu-id="141dc-135">否</span><span class="sxs-lookup"><span data-stu-id="141dc-135">No</span></span>|<span data-ttu-id="141dc-136">是</span><span class="sxs-lookup"><span data-stu-id="141dc-136">Yes</span></span>|<span data-ttu-id="141dc-137">**是**</span><span class="sxs-lookup"><span data-stu-id="141dc-137">**Yes**</span></span>|  
|<span data-ttu-id="141dc-138">**整合式安全性模型**</span><span class="sxs-lookup"><span data-stu-id="141dc-138">**Integrated security model**</span></span>|<span data-ttu-id="141dc-139">否</span><span class="sxs-lookup"><span data-stu-id="141dc-139">No</span></span>|<span data-ttu-id="141dc-140">是</span><span class="sxs-lookup"><span data-stu-id="141dc-140">Yes</span></span>|<span data-ttu-id="141dc-141">**是**</span><span class="sxs-lookup"><span data-stu-id="141dc-141">**Yes**</span></span>|  
|<span data-ttu-id="141dc-142">**FILESTREAM 資料的就地更新**</span><span class="sxs-lookup"><span data-stu-id="141dc-142">**In-place updates of FILESTREAM data**</span></span>|<span data-ttu-id="141dc-143">是</span><span class="sxs-lookup"><span data-stu-id="141dc-143">Yes</span></span>|<span data-ttu-id="141dc-144">否</span><span class="sxs-lookup"><span data-stu-id="141dc-144">No</span></span>|<span data-ttu-id="141dc-145">**是**</span><span class="sxs-lookup"><span data-stu-id="141dc-145">**Yes**</span></span>|  
|<span data-ttu-id="141dc-146">**在資料庫中維護的檔案和目錄階層**</span><span class="sxs-lookup"><span data-stu-id="141dc-146">**File and directory hierarchy maintained in the database**</span></span>|<span data-ttu-id="141dc-147">否</span><span class="sxs-lookup"><span data-stu-id="141dc-147">No</span></span>|<span data-ttu-id="141dc-148">否</span><span class="sxs-lookup"><span data-stu-id="141dc-148">No</span></span>|<span data-ttu-id="141dc-149">**是**</span><span class="sxs-lookup"><span data-stu-id="141dc-149">**Yes**</span></span>|  
|<span data-ttu-id="141dc-150">**Windows 應用程式相容性**</span><span class="sxs-lookup"><span data-stu-id="141dc-150">**Windows application compatibility**</span></span>|<span data-ttu-id="141dc-151">是</span><span class="sxs-lookup"><span data-stu-id="141dc-151">Yes</span></span>|<span data-ttu-id="141dc-152">否</span><span class="sxs-lookup"><span data-stu-id="141dc-152">No</span></span>|<span data-ttu-id="141dc-153">**是**</span><span class="sxs-lookup"><span data-stu-id="141dc-153">**Yes**</span></span>|  
|<span data-ttu-id="141dc-154">**檔案屬性的關聯式存取**</span><span class="sxs-lookup"><span data-stu-id="141dc-154">**Relational access to file attributes**</span></span>|<span data-ttu-id="141dc-155">否</span><span class="sxs-lookup"><span data-stu-id="141dc-155">No</span></span>|<span data-ttu-id="141dc-156">否</span><span class="sxs-lookup"><span data-stu-id="141dc-156">No</span></span>|<span data-ttu-id="141dc-157">**是**</span><span class="sxs-lookup"><span data-stu-id="141dc-157">**Yes**</span></span>|  
  
##  <a name="comparing-filestream-and-remote-blob-store-rbs"></a><a name="CompareRBS"></a> <span data-ttu-id="141dc-158">比較 FILESTREAM 與遠端 BLOB 存放區 (RBS)</span><span class="sxs-lookup"><span data-stu-id="141dc-158">Comparing FILESTREAM and Remote BLOB Store (RBS)</span></span>  
 <span data-ttu-id="141dc-159">如需此兩種功能的比較，請參閱 RBS 小組的這篇部落格文章： [SQL Server 遠端 BLOB 存放區和 FILESTREAM 功能比較](https://go.microsoft.com/fwlink/?LinkId=210317)。</span><span class="sxs-lookup"><span data-stu-id="141dc-159">For a comparison of these two features, see this blog post from the RBS team: [SQL Server Remote BLOB Store and FILESTREAM feature comparison](https://go.microsoft.com/fwlink/?LinkId=210317).</span></span>  
  
##  <a name="more-information"></a><a name="more"></a> <span data-ttu-id="141dc-160">其他資訊</span><span class="sxs-lookup"><span data-stu-id="141dc-160">More Information</span></span>  
 [<span data-ttu-id="141dc-161">FILESTREAM &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="141dc-161">FILESTREAM &#40;SQL Server&#41;</span></span>](filestream-sql-server.md)  
 [<span data-ttu-id="141dc-162">FileTables &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="141dc-162">FileTables &#40;SQL Server&#41;</span></span>](filetables-sql-server.md)  
 [<span data-ttu-id="141dc-163">遠端 Blob 存放區 &#40;RBS&#41; &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="141dc-163">Remote Blob Store &#40;RBS&#41; &#40;SQL Server&#41;</span></span>](remote-blob-store-rbs-sql-server.md)  
  
