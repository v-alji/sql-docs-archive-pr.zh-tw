---
title: Unicode 壓縮實作 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Unicode data compression
- compression [SQL Server], Unicode data
ms.assetid: 44e69e60-9b35-43fe-b9c7-8cf34eaea62a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4c928062169ed7feb03f1031362530474109976a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598993"
---
# <a name="unicode-compression-implementation"></a><span data-ttu-id="c5d15-102">Unicode 壓縮實作</span><span class="sxs-lookup"><span data-stu-id="c5d15-102">Unicode Compression Implementation</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c5d15-103">使用 Standard Compression Scheme for Unicode (SCSU) 演算法的實作來壓縮儲存在資料列或頁面壓縮物件中的 Unicode 值。</span><span class="sxs-lookup"><span data-stu-id="c5d15-103">uses an implementation of the Standard Compression Scheme for Unicode (SCSU) algorithm to compress Unicode values that are stored in row or page compressed objects.</span></span> <span data-ttu-id="c5d15-104">對於這些壓縮的物件而言，系統會自動針對 `nchar(n)` 和 `nvarchar(n)` 資料行進行 Unicode 壓縮。</span><span class="sxs-lookup"><span data-stu-id="c5d15-104">For these compressed objects, Unicode compression is automatic for `nchar(n)` and `nvarchar(n)` columns.</span></span> <span data-ttu-id="c5d15-105">不論地區設定為何， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 都會將 Unicode 資料儲存成 2 位元組。</span><span class="sxs-lookup"><span data-stu-id="c5d15-105">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] stores Unicode data as 2 bytes, regardless of locale.</span></span> <span data-ttu-id="c5d15-106">這稱為 UCS-2 編碼。</span><span class="sxs-lookup"><span data-stu-id="c5d15-106">This is known as UCS-2 encoding.</span></span> <span data-ttu-id="c5d15-107">對於某些地區設定而言，SQL Server 中的 SCSU 壓縮實作最多可以節省 50% 的儲存空間。</span><span class="sxs-lookup"><span data-stu-id="c5d15-107">For some locales, the implementation of SCSU compression in SQL Server can save up to 50 percent in storage space.</span></span>  
  
## <a name="supported-data-types"></a><span data-ttu-id="c5d15-108">支援的資料類型</span><span class="sxs-lookup"><span data-stu-id="c5d15-108">Supported Data Types</span></span>  
 <span data-ttu-id="c5d15-109">Unicode 壓縮支援固定長度的 `nchar(n)` 和 `nvarchar(n)` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="c5d15-109">Unicode compression supports the fixed-length `nchar(n)` and `nvarchar(n)` data types.</span></span> <span data-ttu-id="c5d15-110">不過，無法壓縮以非資料列方式儲存或儲存在 `nvarchar(max)` 資料行中的資料值。</span><span class="sxs-lookup"><span data-stu-id="c5d15-110">Data values that are stored off row or in `nvarchar(max)` columns are not compressed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c5d15-111">不支援 `nvarchar(max)` 資料使用 Unicode 壓縮，即使此資料儲存於資料列中。</span><span class="sxs-lookup"><span data-stu-id="c5d15-111">Unicode compression is not supported for `nvarchar(max)` data even if it is stored in row.</span></span> <span data-ttu-id="c5d15-112">但是，此資料類型仍可以從頁面壓縮中受益。</span><span class="sxs-lookup"><span data-stu-id="c5d15-112">However, this data type can still benefit from page compression.</span></span>  
  
## <a name="upgrading-from-earlier-versions-of-sql-server"></a><span data-ttu-id="c5d15-113">從舊版 SQL Server 升級</span><span class="sxs-lookup"><span data-stu-id="c5d15-113">Upgrading from Earlier Versions of SQL Server</span></span>  
 <span data-ttu-id="c5d15-114">當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫升級為 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]時，系統不會對任何資料庫物件 (已壓縮或未壓縮) 進行與 Unicode 壓縮相關的變更。</span><span class="sxs-lookup"><span data-stu-id="c5d15-114">When a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database is upgraded to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], Unicode compression-related changes are not made to any database object, compressed or uncompressed.</span></span> <span data-ttu-id="c5d15-115">升級資料庫之後，受影響的物件如下所示：</span><span class="sxs-lookup"><span data-stu-id="c5d15-115">After the database is upgraded, objects are affected as follows:</span></span>  
  
-   <span data-ttu-id="c5d15-116">如果某個物件未壓縮，就不會進行任何變更，而且此物件將繼續如同先前的方式運作。</span><span class="sxs-lookup"><span data-stu-id="c5d15-116">If the object is not compressed, no changes are made and the object continues to function as it did previously.</span></span>  
  
-   <span data-ttu-id="c5d15-117">資料列或頁面壓縮的物件將繼續如同先前的方式運作。</span><span class="sxs-lookup"><span data-stu-id="c5d15-117">Row- or page-compressed objects continue to function as they did previously.</span></span> <span data-ttu-id="c5d15-118">未壓縮的資料會維持未壓縮的形式，直到更新其值為止。</span><span class="sxs-lookup"><span data-stu-id="c5d15-118">Uncompressed data remains in uncompressed form until its value is updated.</span></span>  
  
-   <span data-ttu-id="c5d15-119">插入資料列或頁面壓縮資料表的新資料列將使用 Unicode 壓縮進行壓縮。</span><span class="sxs-lookup"><span data-stu-id="c5d15-119">New rows that are inserted into a row- or page-compressed table are compressed using Unicode compression.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c5d15-120">若要充分運用 Unicode 壓縮的優點，您必須使用頁面或資料列壓縮來重建物件。</span><span class="sxs-lookup"><span data-stu-id="c5d15-120">To take full advantage of the benefits of Unicode compression, the object must be rebuilt with page or row compression.</span></span>  
  
## <a name="how-unicode-compression-affects-data-storage"></a><span data-ttu-id="c5d15-121">Unicode 壓縮如何影響資料儲存</span><span class="sxs-lookup"><span data-stu-id="c5d15-121">How Unicode Compression Affects Data Storage</span></span>  
 <span data-ttu-id="c5d15-122">如果您建立或重建某個索引，或在使用資料列或頁面壓縮進行壓縮的資料表中變更某個值，只有當受影響之索引或值的壓縮大小小於目前的大小時，系統才會以壓縮方式進行儲存。</span><span class="sxs-lookup"><span data-stu-id="c5d15-122">When an index is created or rebuilt or when a value is changed in a table that was compressed with row or page compression, the affected index or value is stored compressed only if its compressed size is less than its current size.</span></span> <span data-ttu-id="c5d15-123">這樣做可避免資料表中的資料列或索引由於 Unicode 壓縮而增加大小。</span><span class="sxs-lookup"><span data-stu-id="c5d15-123">This prevents rows in a table or index from increasing in size because of Unicode compression.</span></span>  
  
 <span data-ttu-id="c5d15-124">壓縮所節省的儲存空間主要取決於所壓縮之資料的特性以及資料的地區設定。</span><span class="sxs-lookup"><span data-stu-id="c5d15-124">The storage space that compression saves depends on the characteristics of the data that is being compressed and the locale of the data.</span></span> <span data-ttu-id="c5d15-125">下表將列出許多地區設定可達成的空間節省效果。</span><span class="sxs-lookup"><span data-stu-id="c5d15-125">The following table lists the space savings that can be achieved for several locales.</span></span>  
  
|<span data-ttu-id="c5d15-126">Locale</span><span class="sxs-lookup"><span data-stu-id="c5d15-126">Locale</span></span>|<span data-ttu-id="c5d15-127">壓縮百分比</span><span class="sxs-lookup"><span data-stu-id="c5d15-127">Compression percent</span></span>|  
|------------|-------------------------|  
|<span data-ttu-id="c5d15-128">英文</span><span class="sxs-lookup"><span data-stu-id="c5d15-128">English</span></span>|<span data-ttu-id="c5d15-129">50%</span><span class="sxs-lookup"><span data-stu-id="c5d15-129">50%</span></span>|  
|<span data-ttu-id="c5d15-130">德文</span><span class="sxs-lookup"><span data-stu-id="c5d15-130">German</span></span>|<span data-ttu-id="c5d15-131">50%</span><span class="sxs-lookup"><span data-stu-id="c5d15-131">50%</span></span>|  
|<span data-ttu-id="c5d15-132">Hindi</span><span class="sxs-lookup"><span data-stu-id="c5d15-132">Hindi</span></span>|<span data-ttu-id="c5d15-133">50%</span><span class="sxs-lookup"><span data-stu-id="c5d15-133">50%</span></span>|  
|<span data-ttu-id="c5d15-134">土耳其文</span><span class="sxs-lookup"><span data-stu-id="c5d15-134">Turkish</span></span>|<span data-ttu-id="c5d15-135">48%</span><span class="sxs-lookup"><span data-stu-id="c5d15-135">48%</span></span>|  
|<span data-ttu-id="c5d15-136">越南文</span><span class="sxs-lookup"><span data-stu-id="c5d15-136">Vietnamese</span></span>|<span data-ttu-id="c5d15-137">39%</span><span class="sxs-lookup"><span data-stu-id="c5d15-137">39%</span></span>|  
|<span data-ttu-id="c5d15-138">日文</span><span class="sxs-lookup"><span data-stu-id="c5d15-138">Japanese</span></span>|<span data-ttu-id="c5d15-139">15%</span><span class="sxs-lookup"><span data-stu-id="c5d15-139">15%</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c5d15-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5d15-140">See Also</span></span>  
 <span data-ttu-id="c5d15-141">[資料壓縮](data-compression.md) </span><span class="sxs-lookup"><span data-stu-id="c5d15-141">[Data Compression](data-compression.md) </span></span>  
 <span data-ttu-id="c5d15-142">[sp_estimate_data_compression_savings &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c5d15-142">[sp_estimate_data_compression_savings &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql) </span></span>  
 <span data-ttu-id="c5d15-143">[頁面壓縮實作](page-compression-implementation.md) </span><span class="sxs-lookup"><span data-stu-id="c5d15-143">[Page Compression Implementation](page-compression-implementation.md) </span></span>  
 [<span data-ttu-id="c5d15-144">sys.dm_db_persisted_sku_features &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c5d15-144">sys.dm_db_persisted_sku_features &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-persisted-sku-features-transact-sql)  
  
  
