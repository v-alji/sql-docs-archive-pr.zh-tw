---
title: 遠端 Blob 存放區 (RBS) (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.technology: filestream
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Remote Blob Store (RBS) [SQL Server]
- RBS (Remote Blob Store) [SQL Server]
ms.assetid: 31c947cf-53e9-4ff4-939b-4c1d034ea5b1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8f3425474ec3b9013355536424ffcf55d9426b9c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686990"
---
# <a name="remote-blob-store-rbs-sql-server"></a><span data-ttu-id="f955f-102">遠端 Blob 存放區 (RBS) (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f955f-102">Remote Blob Store (RBS) (SQL Server)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f955f-103">遠端 BLOB 存放區 (RBS) 是選用的附加元件，可讓資料庫管理員在商品儲存方案中儲存二進位大型物件，而不是直接儲存在主要資料庫伺服器上。</span><span class="sxs-lookup"><span data-stu-id="f955f-103">Remote BLOB Store (RBS) is an optional add-on component that lets database administrators store binary large objects in commodity storage solutions instead of directly on the main database server.</span></span>  
  
 <span data-ttu-id="f955f-104">RBS 包含在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安裝媒體中，但不會由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式安裝。</span><span class="sxs-lookup"><span data-stu-id="f955f-104">RBS is included on the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installation media, but is not installed by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup program.</span></span>  
  
 <span data-ttu-id="f955f-105">如需 RBS 的詳細資訊，請參閱本主題中的 [RBS 資源](#rbsresources)。</span><span class="sxs-lookup"><span data-stu-id="f955f-105">For more information about RBS, see [RBS Resources](#rbsresources) in this topic.</span></span>  
  
## <a name="benefits-of-rbs"></a><span data-ttu-id="f955f-106">RBS 的優點</span><span class="sxs-lookup"><span data-stu-id="f955f-106">Benefits of RBS</span></span>  
 <span data-ttu-id="f955f-107">RBS 提供下列優點：</span><span class="sxs-lookup"><span data-stu-id="f955f-107">RBS provides the following benefits:</span></span>  
  
### <a name="optimized-database-storage-and-performance"></a><span data-ttu-id="f955f-108">最佳化的資料庫儲存和效能</span><span class="sxs-lookup"><span data-stu-id="f955f-108">Optimized database storage and performance</span></span>  
 <span data-ttu-id="f955f-109">將 BLOB 儲存在資料庫中可能會耗用大量的檔案空間以及昂貴的伺服器資源。</span><span class="sxs-lookup"><span data-stu-id="f955f-109">Storing BLOBs in the database can consume large amounts of file space and expensive server resources.</span></span> <span data-ttu-id="f955f-110">RBS 會將 BLOB 有效率地傳輸到您所選擇的專用儲存方案，並將其參考儲存在資料庫中。</span><span class="sxs-lookup"><span data-stu-id="f955f-110">RBS efficiently transfers the BLOBs to a dedicated storage solution of your choosing, and stores references to them in the database.</span></span> <span data-ttu-id="f955f-111">這樣會為結構化的資料釋放伺服器儲存空間，並為資料庫作業釋放伺服器資源。</span><span class="sxs-lookup"><span data-stu-id="f955f-111">This frees server storage for structured data, and frees server resources for database operations.</span></span>  
  
### <a name="efficient-management-of-blobs"></a><span data-ttu-id="f955f-112">有效率的 BLOB 管理</span><span class="sxs-lookup"><span data-stu-id="f955f-112">Efficient management of BLOBs</span></span>  
 <span data-ttu-id="f955f-113">數個 RBS 功能都支援方便管理已儲存的 BLOB：</span><span class="sxs-lookup"><span data-stu-id="f955f-113">Several RBS features support the convenient management of stored BLOBs:</span></span>  
  
-   <span data-ttu-id="f955f-114">BLOB 使用 ACID (不可部分完成、一致、隔離、持久) 交易進行管理。</span><span class="sxs-lookup"><span data-stu-id="f955f-114">BLOBS are managed with ACID (atomic consistency isolation durable) transactions.</span></span>  
  
-   <span data-ttu-id="f955f-115">BLOB 會組織成集合。</span><span class="sxs-lookup"><span data-stu-id="f955f-115">BLOBs are organized into collections.</span></span>  
  
-   <span data-ttu-id="f955f-116">記憶體回收、一致性檢查，以及其他維護功能都包含在內。</span><span class="sxs-lookup"><span data-stu-id="f955f-116">Garbage collection, consistency checking, and other maintenance functions are included.</span></span>  
  
### <a name="standardized-api"></a><span data-ttu-id="f955f-117">標準化的 API</span><span class="sxs-lookup"><span data-stu-id="f955f-117">Standardized API</span></span>  
 <span data-ttu-id="f955f-118">RBS 會定義一組 API 來為應用程式提供標準化程式撰寫模型，以存取及修改任何 BLOB 存放區。</span><span class="sxs-lookup"><span data-stu-id="f955f-118">RBS defines a set of APIs that provide a standardized programming model for applications to access and modify any BLOB store.</span></span> <span data-ttu-id="f955f-119">每一個 BLOB 存放區都可以指定它自己的提供者程式庫 (該程式庫會外掛到 RBS 用戶端程式庫)，並指定要如何儲存及存取 BLOB。</span><span class="sxs-lookup"><span data-stu-id="f955f-119">Each BLOB store can specify its own provider library, which plugs into the RBS client library and specifies how BLOBs are stored and accessed.</span></span>  
  
 <span data-ttu-id="f955f-120">有好幾個協力廠商儲存方案廠商已經開發了符合這些標準 API，並在多種儲存平台上支援 BLOB 儲存的 RBS 提供者。</span><span class="sxs-lookup"><span data-stu-id="f955f-120">A number of third-party storage solution vendors have developed RBS providers that conform to these standard APIs and support BLOB storage on various storage platforms.</span></span>  
  
## <a name="rbs-requirements"></a><span data-ttu-id="f955f-121">RBS 需求</span><span class="sxs-lookup"><span data-stu-id="f955f-121">RBS Requirements</span></span>  
 <span data-ttu-id="f955f-122">RBS 在儲存 BLOB 中繼資料所在的主要資料庫伺服器中，需要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise。</span><span class="sxs-lookup"><span data-stu-id="f955f-122">RBS requires [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise for the main database server in which the BLOB metadata is stored.</span></span> <span data-ttu-id="f955f-123">不過，如果您使用提供的 FILESTREAM 提供者，可以將 BLOB 本身儲存在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Standard 上。</span><span class="sxs-lookup"><span data-stu-id="f955f-123">However, if you use the supplied FILESTREAM provider, you can store the BLOBs themselves on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Standard.</span></span>  
  
 <span data-ttu-id="f955f-124">RBS 包含一個 FILESTREAM 提供者，可讓您使用 RBS，將 BLOB 儲存在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體上。</span><span class="sxs-lookup"><span data-stu-id="f955f-124">RBS includes a FILESTREAM provider that lets you use RBS to store BLOBs on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f955f-125">如果您要使用 RBS 將 BLOB 儲存在不同的儲存方案中，您必須使用針對該儲存方案開發的 RBS 提供者，或使用 RBS API 開發一個自訂的 RBS 提供者。</span><span class="sxs-lookup"><span data-stu-id="f955f-125">If you want use RBS to store BLOBs in a different storage solution, you have to use a third party RBS provider developed for that storage solution, or develop a custom RBS provider using the RBS API.</span></span> <span data-ttu-id="f955f-126">將 BLOB 儲存在 NTFS 檔案系統中的範例提供者，在 [Codeplex](https://go.microsoft.com/fwlink/?LinkId=210190)上作為學習資源提供。</span><span class="sxs-lookup"><span data-stu-id="f955f-126">A sample provider that stores BLOBs in the NTFS file system is available as a learning resource on [Codeplex](https://go.microsoft.com/fwlink/?LinkId=210190).</span></span>  
  
## <a name="rbs-security"></a><span data-ttu-id="f955f-127">RBS 安全性</span><span class="sxs-lookup"><span data-stu-id="f955f-127">RBS Security</span></span>  
 <span data-ttu-id="f955f-128">當您使用自訂提供者將 BLOB 儲存在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 外部時，可以提供給略過 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安全性系統的其他處理序使用。</span><span class="sxs-lookup"><span data-stu-id="f955f-128">When you use a custom provider to store BLOBs outside of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], they may be available to other processes that bypass the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security system.</span></span> <span data-ttu-id="f955f-129">請確認您會使用適合自訂提供者使用之儲存媒體的權限和加密選項，保護已儲存的 BLOB。</span><span class="sxs-lookup"><span data-stu-id="f955f-129">Make sure that you protect the stored BLOBs with permissions and encryption options that are appropriate to the storage medium used by the custom provider.</span></span>  
  
##  <a name="rbs-resources"></a><a name="rbsresources"></a><span data-ttu-id="f955f-130">RBS 資源</span><span class="sxs-lookup"><span data-stu-id="f955f-130">RBS Resources</span></span>  
 <span data-ttu-id="f955f-131">**RBS 文件集**</span><span class="sxs-lookup"><span data-stu-id="f955f-131">**RBS documentation**</span></span>  
 <span data-ttu-id="f955f-132">RBS 文件集包含在 Windows Installer 套件中。</span><span class="sxs-lookup"><span data-stu-id="f955f-132">The RBS documentation is included in the Windows installer package.</span></span> <span data-ttu-id="f955f-133">如果您要在不安裝 RBS 的情況下檢閱 RBS 文件集，則可以在 [MSDN Library 中線上](https://go.microsoft.com/fwlink/?LinkId=210192)檢視該文件集的 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="f955f-133">If you want to review the RBS documentation without installing RBS, you can view the [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] version of the documentation [online in the MSDN Library](https://go.microsoft.com/fwlink/?LinkId=210192).</span></span>  
  
 <span data-ttu-id="f955f-134">**RBS 技術白皮書**</span><span class="sxs-lookup"><span data-stu-id="f955f-134">**RBS white paper**</span></span>  
 <span data-ttu-id="f955f-135">[遠端 BLOB 儲存](https://go.microsoft.com/fwlink/?LinkId=210422)技術白皮書是可下載的 Microsoft Word 文件，這個技術白皮書提供有關安裝與設定 RBS 的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="f955f-135">The white paper "[Remote BLOB Storage](https://go.microsoft.com/fwlink/?LinkId=210422)", which is available for download as a Microsoft Word document, provides detailed information about installing and configuring RBS.</span></span>  
  
 <span data-ttu-id="f955f-136">**RBS 範例**</span><span class="sxs-lookup"><span data-stu-id="f955f-136">**RBS samples**</span></span>  
 <span data-ttu-id="f955f-137">[Codeplex](https://go.microsoft.com/fwlink/?LinkId=210190) 上提供的 RBS 範例會示範如何開發 RBS 應用程式，以及如何開發與安裝自訂的 RBS 提供者。</span><span class="sxs-lookup"><span data-stu-id="f955f-137">The RBS samples available on [Codeplex](https://go.microsoft.com/fwlink/?LinkId=210190) demonstrate how to develop an RBS application, and how to develop and install a custom RBS provider.</span></span>  
  
 <span data-ttu-id="f955f-138">**RBS 部落格**</span><span class="sxs-lookup"><span data-stu-id="f955f-138">**RBS blog**</span></span>  
 <span data-ttu-id="f955f-139">[RBS 部落格](https://go.microsoft.com/fwlink/?LinkId=210315) 會提供其他資訊來協助您了解、部署，以及維護 RBS。</span><span class="sxs-lookup"><span data-stu-id="f955f-139">The [RBS blog](https://go.microsoft.com/fwlink/?LinkId=210315) provides additional information to help you understand, deploy, and maintain RBS.</span></span>  
  
  
