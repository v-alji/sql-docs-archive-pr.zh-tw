---
title: 二進位大型物件 (Blob) 資料 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], design and implementation
ms.assetid: 97509274-c3f8-43e5-a37c-52f1ffe0961a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a663dedf34d75a21ee8df6b97979548c04abf7ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599029"
---
# <a name="binary-large-object-blob-data-sql-server"></a><span data-ttu-id="40348-102">二進位大型物件 (Blob) 資料 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="40348-102">Binary Large Object (Blob) Data (SQL Server)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="40348-103">提供在資料庫中或遠端存放裝置上儲存檔案和文件的解決方案。</span><span class="sxs-lookup"><span data-stu-id="40348-103">provides solutions for storing files and documents in the database or on remote storage devices.</span></span>  
  
##  <a name="in-this-section"></a><a name="section"></a> <span data-ttu-id="40348-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="40348-104">In This Section</span></span>  
 [<span data-ttu-id="40348-105">比較用於儲存 Blob 的選項 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40348-105">Compare Options for Storing Blobs &#40;SQL Server&#41;</span></span>](compare-options-for-storing-blobs-sql-server.md)  
 <span data-ttu-id="40348-106">比較 FILESTREAM、FileTable 和遠端 Blob 存放區的優點。</span><span class="sxs-lookup"><span data-stu-id="40348-106">Compare the advantages of FILESTREAM, FileTables, and Remote Blob Store.</span></span>  
  
 [<span data-ttu-id="40348-107">FILESTREAM &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40348-107">FILESTREAM &#40;SQL Server&#41;</span></span>](filestream-sql-server.md)  
 <span data-ttu-id="40348-108">FILESTREAM 可讓 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]架構應用程式在檔案系統上儲存非結構化的資料，例如文件和影像。</span><span class="sxs-lookup"><span data-stu-id="40348-108">FILESTREAM enables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-based applications to store unstructured data, such as documents and images, on the file system.</span></span> <span data-ttu-id="40348-109">應用程式可以利用檔案系統的豐富資料流 API 和效能，並同時維護非結構化資料與對應結構化資料之間的交易一致性。</span><span class="sxs-lookup"><span data-stu-id="40348-109">Applications can leverage the rich streaming APIs and performance of the file system and at the same time maintain transactional consistency between the unstructured data and corresponding structured data.</span></span>  
  
 [<span data-ttu-id="40348-110">FileTables &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40348-110">FileTables &#40;SQL Server&#41;</span></span>](filetables-sql-server.md)  
 <span data-ttu-id="40348-111">FileTable 功能可將 Windows 檔案命名空間的支援以及與 Windows 應用程式的相容性提供給儲存在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中的檔案資料。</span><span class="sxs-lookup"><span data-stu-id="40348-111">The FileTable feature brings support for the Windows file namespace and compatibility with Windows applications to the file data stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="40348-112">FileTable 可讓應用程式整合其儲存和資料管理元件，並且透過非結構化資料和中繼資料提供整合式 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務 (包含全文檢索搜尋和語意搜尋)。</span><span class="sxs-lookup"><span data-stu-id="40348-112">FileTable lets an application integrate its storage and data management components, and provides integrated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services - including full-text search and semantic search - over unstructured data and metadata.</span></span>  
  
 <span data-ttu-id="40348-113">換句話說，您可以將檔案和文件儲存在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的特殊資料表 (稱為 FileTable) 中，而從 Windows 應用程式存取它們，就像它們儲存在檔案系統中一樣，並不需要對用戶端應用程式進行任何變更。</span><span class="sxs-lookup"><span data-stu-id="40348-113">In other words, you can store files and documents in special tables in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] called FileTables, but access them from Windows applications as if they were stored in the file system, without making any changes to your client applications.</span></span>  
  
 [<span data-ttu-id="40348-114">遠端 Blob 存放區 &#40;RBS&#41; &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="40348-114">Remote Blob Store &#40;RBS&#41; &#40;SQL Server&#41;</span></span>](remote-blob-store-rbs-sql-server.md)  
 <span data-ttu-id="40348-115">適用於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的遠端 BLOB 存放區 (RBS) 可讓資料庫管理員在商品儲存解決方案中儲存二進位大型物件 (BLOB)，而不是直接儲存在伺服器上。</span><span class="sxs-lookup"><span data-stu-id="40348-115">Remote BLOB store (RBS) for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lets database administrators store binary large objects (BLOBs) in commodity storage solutions instead of directly on the server.</span></span> <span data-ttu-id="40348-116">這樣會節省大量的空間，並避免浪費耗費成本的伺服器硬體資源。</span><span class="sxs-lookup"><span data-stu-id="40348-116">This saves a significant amount of space and avoids wasting expensive server hardware resources.</span></span> <span data-ttu-id="40348-117">RBS 會提供一組 API 程式庫來為應用程式定義標準化模型，以存取 BLOB 資料。</span><span class="sxs-lookup"><span data-stu-id="40348-117">RBS provides a set of API libraries that define a standardized model for applications to access BLOB data.</span></span> <span data-ttu-id="40348-118">RBS 也包含維護工具 (例如記憶體回收)，以協助管理遠端 BLOB 資料。</span><span class="sxs-lookup"><span data-stu-id="40348-118">RBS also includes maintenance tools, such as garbage collection, to help manage remote BLOB data.</span></span>  
  
 <span data-ttu-id="40348-119">RBS 包含在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝媒體中，但不會由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式安裝。</span><span class="sxs-lookup"><span data-stu-id="40348-119">RBS is included on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation media, but is not installed by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup program.</span></span>  
  
  
