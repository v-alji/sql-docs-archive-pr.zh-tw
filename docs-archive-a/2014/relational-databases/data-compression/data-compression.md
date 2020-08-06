---
title: 資料壓縮 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- page compression [Database Engine]
- indexes [SQL Server], compressed
- compressed indexes [SQL Server]
- storage compression [Database Engine]
- tables [SQL Server], compressed
- storage [SQL Server], compressed
- compression [SQL Server]
- row compression [Database Engine]
- compression [SQL Server], about compressed tables and indexes
- data compression [Database Engine]
- compressed tables [SQL Server]
ms.assetid: 5f33e686-e115-4687-bd39-a00c48646513
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 48c4b11963d8e05ff7787ce9200329daf2e899ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599010"
---
# <a name="data-compression"></a><span data-ttu-id="a98d4-102">資料壓縮</span><span class="sxs-lookup"><span data-stu-id="a98d4-102">Data Compression</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="a98d4-103">支援資料列存放區之資料表和索引的資料列和頁面壓縮，並且支援資料行存放區之資料表和索引的資料行存放區和資料行存放區封存壓縮。</span><span class="sxs-lookup"><span data-stu-id="a98d4-103">supports row and page compression for rowstore tables and indexes, and supports columnstore and columnstore archival compression for columnstore tables and indexes.</span></span>  
  
 <span data-ttu-id="a98d4-104">如果是資料列存放區資料表和索引，使用資料壓縮功能有助於減少資料庫的大小。</span><span class="sxs-lookup"><span data-stu-id="a98d4-104">For rowstore tables and indexes, use the data compression feature to help reduce the size of the database.</span></span> <span data-ttu-id="a98d4-105">除了節省空間之外，資料壓縮也有助於改善 I/O 密集型工作負載的效能，因為資料會儲存在更少的頁面中，而且查詢需要從磁碟讀取的頁面也變少了。</span><span class="sxs-lookup"><span data-stu-id="a98d4-105">In addition to saving space, data compression can help improve performance of I/O intensive workloads because the data is stored in fewer pages and queries need to read fewer pages from disk.</span></span> <span data-ttu-id="a98d4-106">但是在與應用程式交換資料時，資料庫伺服器上需要額外的 CPU 資源來壓縮和解壓縮資料。</span><span class="sxs-lookup"><span data-stu-id="a98d4-106">However, extra CPU resources are required on the database server to compress and decompress the data, while data is exchanged with the application.</span></span> <span data-ttu-id="a98d4-107">您可以針對下列資料庫物件來設定資料列和頁面壓縮：</span><span class="sxs-lookup"><span data-stu-id="a98d4-107">You can configure row and page compression on the following database objects:</span></span>  
  
-   <span data-ttu-id="a98d4-108">儲存為堆積的整個資料表。</span><span class="sxs-lookup"><span data-stu-id="a98d4-108">A whole table that is stored as a heap.</span></span>  
  
-   <span data-ttu-id="a98d4-109">儲存為叢集索引的整個資料表。</span><span class="sxs-lookup"><span data-stu-id="a98d4-109">A whole table that is stored as a clustered index.</span></span>  
  
-   <span data-ttu-id="a98d4-110">整個非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="a98d4-110">A whole nonclustered index.</span></span>  
  
-   <span data-ttu-id="a98d4-111">整個索引檢視。</span><span class="sxs-lookup"><span data-stu-id="a98d4-111">A whole indexed view.</span></span>  
  
-   <span data-ttu-id="a98d4-112">如果是分割資料表和索引，您可以針對每個資料分割設定壓縮選項，而物件的不同資料分割則不必擁有相同的壓縮設定。</span><span class="sxs-lookup"><span data-stu-id="a98d4-112">For partitioned tables and indexes, you can configure the compression option for each partition, and the various partitions of an object do not have to have the same compression setting.</span></span>  
  
 <span data-ttu-id="a98d4-113">如果是資料行存放區資料表和索引，所有資料行存放區資料表和索引一律都使用資料行存放區壓縮，而且使用者無法進行設定。</span><span class="sxs-lookup"><span data-stu-id="a98d4-113">For columnstore tables and indexes, all columnstore tables and indexes always use columnstore compression and this is not user configurable.</span></span> <span data-ttu-id="a98d4-114">當您可負擔額外的時間和 CPU 資源來儲存及擷取資料時，使用資料行存放區封存壓縮會進一步減少資料大小。</span><span class="sxs-lookup"><span data-stu-id="a98d4-114">Use columnstore archival compression to further reduce the data size for situations when you can afford extra time and CPU resources to store and retrieve the data.</span></span>  <span data-ttu-id="a98d4-115">您可以針對下列資料庫物件來設定資料行存放區封存壓縮：</span><span class="sxs-lookup"><span data-stu-id="a98d4-115">You can configure columnstore archival compression on the following database objects:</span></span>  
  
-   <span data-ttu-id="a98d4-116">整個資料行存放區資料表或整個叢集資料行存放區索引。</span><span class="sxs-lookup"><span data-stu-id="a98d4-116">A whole columnstore table or a whole clustered columnstore index.</span></span>  <span data-ttu-id="a98d4-117">因為資料行存放區資料表會儲存成叢集資料行存放區索引，所以兩種方法有相同的結果。</span><span class="sxs-lookup"><span data-stu-id="a98d4-117">Since a columnstore table is stored as a clustered columnstore index, both approaches have the same results.</span></span>  
  
-   <span data-ttu-id="a98d4-118">整個非叢集資料行存放區索引。</span><span class="sxs-lookup"><span data-stu-id="a98d4-118">A whole nonclustered columnstore index.</span></span>  
  
-   <span data-ttu-id="a98d4-119">如果是分割資料行存放區資料表和資料行存放區索引，您可以針對每個資料分割設定封存壓縮選項，而不同資料分割則不必擁有相同的封存壓縮設定。</span><span class="sxs-lookup"><span data-stu-id="a98d4-119">For partitioned columnstore tables and columnstore indexes, you can configure the archival compression option for each partition, and the various partitions do not have to have the same archival compression setting.</span></span>  
  
## <a name="considerations-for-when-you-use-row-and-page-compression"></a><span data-ttu-id="a98d4-120">使用資料列和頁面壓縮時的考量</span><span class="sxs-lookup"><span data-stu-id="a98d4-120">Considerations for When You Use Row and Page Compression</span></span>  
 <span data-ttu-id="a98d4-121">當您使用資料列和頁面壓縮時，請注意以下考量事項：</span><span class="sxs-lookup"><span data-stu-id="a98d4-121">When you use row and page compression, be aware the following considerations:</span></span>  
  
-   <span data-ttu-id="a98d4-122">Service Pack 或後續版本中的資料壓縮詳細資料可能會變更，恕不另行通知。</span><span class="sxs-lookup"><span data-stu-id="a98d4-122">The details of data compression are subject to change without notice in service packs or subsequent releases.</span></span>  
  
-   <span data-ttu-id="a98d4-123">每一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本中都無法使用壓縮。</span><span class="sxs-lookup"><span data-stu-id="a98d4-123">Compression is not available in every edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a98d4-124">如需詳細資訊，請參閱＜ [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)＞。</span><span class="sxs-lookup"><span data-stu-id="a98d4-124">For more information, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
-   <span data-ttu-id="a98d4-125">壓縮不適用於系統資料表。</span><span class="sxs-lookup"><span data-stu-id="a98d4-125">Compression is not available for system tables.</span></span>  
  
-   <span data-ttu-id="a98d4-126">壓縮可讓更多的資料列儲存在頁面上，但是不會變更資料表或索引的資料列大小上限。</span><span class="sxs-lookup"><span data-stu-id="a98d4-126">Compression can allow more rows to be stored on a page, but does not change the maximum row size of a table or index.</span></span>  
  
-   <span data-ttu-id="a98d4-127">當資料列大小上限加上壓縮負擔超過 8060 個位元組的資料列大小上限時，資料表將無法啟用壓縮。</span><span class="sxs-lookup"><span data-stu-id="a98d4-127">A table cannot be enabled for compression when the maximum row size plus the compression overhead exceeds the maximum row size of 8060 bytes.</span></span> <span data-ttu-id="a98d4-128">例如， `char(8000)` `char(53)` 因為有額外的壓縮負荷，所以無法壓縮具有資料行 c1 和 c2 的資料表。</span><span class="sxs-lookup"><span data-stu-id="a98d4-128">For example, a table that has the columns c1`char(8000)` and c2`char(53)` cannot be compressed because of the additional compression overhead.</span></span> <span data-ttu-id="a98d4-129">當使用 Vardecimal 儲存格式時，將會在啟用此格式時執行資料列大小檢查。</span><span class="sxs-lookup"><span data-stu-id="a98d4-129">When the vardecimal storage format is used, the row-size check is performed when the format is enabled.</span></span> <span data-ttu-id="a98d4-130">對於資料列和頁面壓縮而言，最初壓縮物件時會執行資料列大小檢查，然後在插入或修改每一個資料列時加以檢查。</span><span class="sxs-lookup"><span data-stu-id="a98d4-130">For row and page compression, the row-size check is performed when the object is initially compressed, and then checked as each row is inserted or modified.</span></span> <span data-ttu-id="a98d4-131">壓縮會強制執行下列兩個規則：</span><span class="sxs-lookup"><span data-stu-id="a98d4-131">Compression enforces the following two rules:</span></span>  
  
    -   <span data-ttu-id="a98d4-132">固定長度類型的更新一定要成功。</span><span class="sxs-lookup"><span data-stu-id="a98d4-132">An update to a fixed-length type must always succeed.</span></span>  
  
    -   <span data-ttu-id="a98d4-133">停用資料壓縮一定要成功。</span><span class="sxs-lookup"><span data-stu-id="a98d4-133">Disabling data compression must always succeed.</span></span> <span data-ttu-id="a98d4-134">即使壓縮的資料列適合頁面大小，這表示它小於 8060 個位元組；如果它未壓縮， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會防止不適合資料列大小的更新。</span><span class="sxs-lookup"><span data-stu-id="a98d4-134">Even if the compressed row fits on the page, which means that it is less than 8060 bytes; [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prevents updates that would not fit on the row when it is uncompressed.</span></span>  
  
-   <span data-ttu-id="a98d4-135">當指定了資料分割清單時，壓縮類型可以在個別資料分割上設定為 ROW、PAGE 或 NONE。</span><span class="sxs-lookup"><span data-stu-id="a98d4-135">When a list of partitions is specified, the compression type can be set to ROW, PAGE, or NONE on individual partitions.</span></span> <span data-ttu-id="a98d4-136">如果未指定資料分割的清單，將會設定所有資料分割，並包含陳述式中所指定的資料壓縮屬性。</span><span class="sxs-lookup"><span data-stu-id="a98d4-136">If the list of partitions is not specified, all partitions are set with the data compression property that is specified in the statement.</span></span> <span data-ttu-id="a98d4-137">在建立資料表或索引時，除非另外指定，否則資料壓縮會設定為 NONE。</span><span class="sxs-lookup"><span data-stu-id="a98d4-137">When a table or index is created, data compression is set to NONE unless otherwise specified.</span></span> <span data-ttu-id="a98d4-138">在修改資料表時，除非另外指定，否則會保留現有的壓縮。</span><span class="sxs-lookup"><span data-stu-id="a98d4-138">When a table is modified, the existing compression is preserved unless otherwise specified.</span></span>  
  
-   <span data-ttu-id="a98d4-139">如果您指定資料分割清單或超出範圍的資料分割，將會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="a98d4-139">If you specify a list of partitions or a partition that is out of range, an error will be generated.</span></span>  
  
-   <span data-ttu-id="a98d4-140">非叢集索引不會繼承資料表的壓縮屬性。</span><span class="sxs-lookup"><span data-stu-id="a98d4-140">Nonclustered indexes do not inherit the compression property of the table.</span></span> <span data-ttu-id="a98d4-141">若要壓縮索引，您必須明確設定索引的壓縮屬性。</span><span class="sxs-lookup"><span data-stu-id="a98d4-141">To compress indexes, you must explicitly set the compression property of the indexes.</span></span> <span data-ttu-id="a98d4-142">根據預設，當建立索引時，索引的壓縮設定將會設定為 NONE。</span><span class="sxs-lookup"><span data-stu-id="a98d4-142">By default, the compression setting for indexes will set to NONE when the index is created.</span></span>  
  
-   <span data-ttu-id="a98d4-143">在堆積上建立叢集索引時，此叢集索引會繼承堆積的壓縮狀態，除非指定了替代的壓縮狀態。</span><span class="sxs-lookup"><span data-stu-id="a98d4-143">When a clustered index is created on a heap, the clustered index inherits the compression state of the heap unless an alternative compression state is specified.</span></span>  
  
-   <span data-ttu-id="a98d4-144">當堆積設定了頁面層級壓縮時，頁面只會以下列方式接收頁面層級壓縮：</span><span class="sxs-lookup"><span data-stu-id="a98d4-144">When a heap is configured for page-level compression, pages receive page-level compression only in the following ways:</span></span>  
  
    -   <span data-ttu-id="a98d4-145">資料會在啟用大量最佳化的情況下大量匯入。</span><span class="sxs-lookup"><span data-stu-id="a98d4-145">Data is bulk imported with bulk optimizations enabled.</span></span>  
  
    -   <span data-ttu-id="a98d4-146">使用 INSERT INTO ...WITH (TABLOCK) 語法與資料表沒有非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="a98d4-146">Data is inserted using INSERT INTO ... WITH (TABLOCK) syntax and the table does not have a nonclustered index.</span></span>  
  
    -   <span data-ttu-id="a98d4-147">執行 ALTER TABLE ...REBUILD 陳述式並指定 PAGE 壓縮選項來重建資料表。</span><span class="sxs-lookup"><span data-stu-id="a98d4-147">A table is rebuilt by executing the ALTER TABLE ... REBUILD statement with the PAGE compression option.</span></span>  
  
-   <span data-ttu-id="a98d4-148">重建堆積之前，配置在堆積中成為 DML 作業一部分的新頁面將不會使用 PAGE 壓縮。</span><span class="sxs-lookup"><span data-stu-id="a98d4-148">New pages allocated in a heap as part of DML operations will not use PAGE compression until the heap is rebuilt.</span></span> <span data-ttu-id="a98d4-149">您可以透過移除並重新套用壓縮，或建立並移除叢集索引，重建堆積。</span><span class="sxs-lookup"><span data-stu-id="a98d4-149">Rebuild the heap by removing and reapplying compression, or by creating and removing a clustered index.</span></span>  
  
-   <span data-ttu-id="a98d4-150">變更堆積的壓縮設定需要重建資料表上的所有非叢集索引，好讓它們擁有指向堆積內新資料列位置的指標。</span><span class="sxs-lookup"><span data-stu-id="a98d4-150">Changing the compression setting of a heap requires all nonclustered indexes on the table to be rebuilt so that they have pointers to the new row locations in the heap.</span></span>  
  
-   <span data-ttu-id="a98d4-151">您可以在線上或離線時啟用或停用 ROW 或 PAGE 壓縮。</span><span class="sxs-lookup"><span data-stu-id="a98d4-151">You can enable or disable ROW or PAGE compression online or offline.</span></span> <span data-ttu-id="a98d4-152">在堆積上啟用壓縮對於線上作業而言是單一執行緒的作業。</span><span class="sxs-lookup"><span data-stu-id="a98d4-152">Enabling compression on a heap is single threaded for an online operation.</span></span>  
  
-   <span data-ttu-id="a98d4-153">啟用或停用資料列或頁面壓縮的磁碟空間需求與建立或重建索引的需求相同。</span><span class="sxs-lookup"><span data-stu-id="a98d4-153">The disk space requirements for enabling or disabling row or page compression are the same as for creating or rebuilding an index.</span></span> <span data-ttu-id="a98d4-154">對於分割的資料而言，您可以一次啟用或停用一個資料分割的壓縮來減少所需的空間。</span><span class="sxs-lookup"><span data-stu-id="a98d4-154">For partitioned data, you can reduce the space that is required by enabling or disabling compression for one partition at a time.</span></span>  
  
-   <span data-ttu-id="a98d4-155">若要決定資料分割資料表中資料分割的壓縮狀態，請查詢 sys.partitions 目錄檢視的 data_compression 資料行。</span><span class="sxs-lookup"><span data-stu-id="a98d4-155">To determine the compression state of partitions in a partitioned table, query the data_compression column of the sys.partitions catalog view.</span></span>  
  
-   <span data-ttu-id="a98d4-156">當您壓縮索引時，可以在壓縮資料列和頁面的情況下壓縮分葉層級頁面。</span><span class="sxs-lookup"><span data-stu-id="a98d4-156">When you are compressing indexes, leaf-level pages can be compressed with both row and page compression.</span></span> <span data-ttu-id="a98d4-157">非分葉層級頁面不會收到頁面壓縮。</span><span class="sxs-lookup"><span data-stu-id="a98d4-157">Non-leaf-level pages do not receive page compression.</span></span>  
  
-   <span data-ttu-id="a98d4-158">由於大數值資料類型的大小之緣故，這些類型有時會單獨儲存在特殊用途的頁面上，與一般資料列的資料分開。</span><span class="sxs-lookup"><span data-stu-id="a98d4-158">Because of their size, large-value data types are sometimes stored separately from the normal row data on special purpose pages.</span></span> <span data-ttu-id="a98d4-159">資料壓縮不適用於個別儲存的資料。</span><span class="sxs-lookup"><span data-stu-id="a98d4-159">Data compression is not available for the data that is stored separately.</span></span>  
  
-   <span data-ttu-id="a98d4-160">在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 中實作 Vardecimal 儲存格式的資料表將會在升級時保留此設定。</span><span class="sxs-lookup"><span data-stu-id="a98d4-160">Tables which implemented the vardecimal storage format in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] will retain that setting when upgraded.</span></span> <span data-ttu-id="a98d4-161">您可以將資料列壓縮套用到具有 Vardecimal 儲存格式的資料表。</span><span class="sxs-lookup"><span data-stu-id="a98d4-161">You can apply row compression to a table that has the vardecimal storage format.</span></span> <span data-ttu-id="a98d4-162">但是，由於資料列壓縮是 Vardecimal 儲存格式的超集，所以沒有理由保留 Vardecimal 儲存格式。</span><span class="sxs-lookup"><span data-stu-id="a98d4-162">However, because row compression is a superset of the vardecimal storage format, there is no reason to retain the vardecimal storage format.</span></span> <span data-ttu-id="a98d4-163">當您將 Vardecimal 儲存格式結合資料列壓縮時，十進位值不會取得額外的壓縮。</span><span class="sxs-lookup"><span data-stu-id="a98d4-163">Decimal values gain no additional compression when you combine the vardecimal storage format with row compression.</span></span> <span data-ttu-id="a98d4-164">您可以將頁面壓縮套用到具有 Vardecimal 儲存格式的資料表；但是，Vardecimal 儲存格式資料行可能不會封存其他壓縮。</span><span class="sxs-lookup"><span data-stu-id="a98d4-164">You can apply page compression to a table that has the vardecimal storage format; however, the vardecimal storage format columns probably will not achieve additional compression.</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="a98d4-165">支援 Vardecimal 儲存格式；但是，由於資料列層級的壓縮會達成相同的目標，所以 Vardecimal 儲存格式已被取代。</span><span class="sxs-lookup"><span data-stu-id="a98d4-165">supports the vardecimal storage format; however, because row-level compression achieves the same goals, the vardecimal storage format is deprecated.</span></span> [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="using-columnstore-and-columnstore-archive-compression"></a><span data-ttu-id="a98d4-166">使用資料行存放區和資料行存放區封存壓縮</span><span class="sxs-lookup"><span data-stu-id="a98d4-166">Using Columnstore and Columnstore Archive Compression</span></span>  
  
||  
|-|  
|<span data-ttu-id="a98d4-167">**適用於**： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 至 [目前版本](https://go.microsoft.com/fwlink/p/?LinkId=299658))。</span><span class="sxs-lookup"><span data-stu-id="a98d4-167">**Applies to**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] through [current version](https://go.microsoft.com/fwlink/p/?LinkId=299658)).</span></span>|  
  
### <a name="basics"></a><span data-ttu-id="a98d4-168">基本概念</span><span class="sxs-lookup"><span data-stu-id="a98d4-168">Basics</span></span>  
 <span data-ttu-id="a98d4-169">資料行存放區資料表和索引永遠都會以資料行存放區壓縮形式來儲存。</span><span class="sxs-lookup"><span data-stu-id="a98d4-169">Columnstore tables and indexes are always stored with columnstore compression.</span></span> <span data-ttu-id="a98d4-170">您可以進一步減少資料行存放區資料的大小，只要設定稱為封存壓縮的額外壓縮即可。</span><span class="sxs-lookup"><span data-stu-id="a98d4-170">You can further reduce the size of columnstore data by configuring an additional compression called archival compression.</span></span>  <span data-ttu-id="a98d4-171">為了執行封存壓縮， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會針對資料執行 Microsoft XPRESS 壓縮演算法。</span><span class="sxs-lookup"><span data-stu-id="a98d4-171">To perform archival compression, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] runs the Microsoft XPRESS compression algorithm on the data.</span></span> <span data-ttu-id="a98d4-172">您可以使用下列資料壓縮類型來新增或移除封存壓縮：</span><span class="sxs-lookup"><span data-stu-id="a98d4-172">Add or remove archival compression by using the following data compression types:</span></span>  
  
-   <span data-ttu-id="a98d4-173">使用 `COLUMNSTORE_ARCHIVE` 資料壓縮，以封存壓縮壓縮資料行存放區資料。</span><span class="sxs-lookup"><span data-stu-id="a98d4-173">Use `COLUMNSTORE_ARCHIVE` data compression to compress columnstore data with archival compression.</span></span>  
  
-   <span data-ttu-id="a98d4-174">使用 **COLUMNSTORE** 資料壓縮，將封存壓縮解壓縮。</span><span class="sxs-lookup"><span data-stu-id="a98d4-174">Use **COLUMNSTORE** data compression to decompress archival compression.</span></span> <span data-ttu-id="a98d4-175">這樣產生的資料將會持續以資料行存放區壓縮形式壓縮。</span><span class="sxs-lookup"><span data-stu-id="a98d4-175">This resulting data will continue to be compressed with columnstore compression.</span></span>  
  
 <span data-ttu-id="a98d4-176">若要新增封存壓縮，請使用 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) 或 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) 搭配 REBUILD 選項和 DATA COMPRESSION = COLUMNSTORE。</span><span class="sxs-lookup"><span data-stu-id="a98d4-176">To add archival compression, use [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) or [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) with the REBUILD option and DATA COMPRESSION = COLUMNSTORE.</span></span>  
  
 <span data-ttu-id="a98d4-177">範例：</span><span class="sxs-lookup"><span data-stu-id="a98d4-177">Examples:</span></span>  
  
```  
ALTER TABLE ColumnstoreTable1   
REBUILD PARTITION = 1 WITH (DATA_COMPRESSION =  COLUMNSTORE_ARCHIVE) ;  
  
ALTER TABLE ColumnstoreTable1   
REBUILD PARTITION = ALL WITH (DATA_COMPRESSION =  COLUMNSTORE_ARCHIVE) ;  
  
ALTER TABLE ColumnstoreTable1   
REBUILD PARTITION = ALL WITH (DATA_COMPRESSION =  COLUMNSTORE_ARCHIVE ON PARTITIONS (2,4)) ;  
  
```  
  
 <span data-ttu-id="a98d4-178">若要移除封存壓縮並將資料還原成資料行存放區壓縮，請使用 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) 或 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) 搭配 REBUILD 選項和 DATA COMPRESSION = COLUMNSTORE。</span><span class="sxs-lookup"><span data-stu-id="a98d4-178">To remove archival compression and restore the data to columnstore compression, use [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) or [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) with the REBUILD option and DATA COMPRESSION = COLUMNSTORE.</span></span>  
  
 <span data-ttu-id="a98d4-179">範例：</span><span class="sxs-lookup"><span data-stu-id="a98d4-179">Examples:</span></span>  
  
```  
ALTER TABLE ColumnstoreTable1   
REBUILD PARTITION = 1 WITH (DATA_COMPRESSION =  COLUMNSTORE) ;  
  
ALTER TABLE ColumnstoreTable1   
REBUILD PARTITION = ALL WITH (DATA_COMPRESSION =  COLUMNSTORE) ;  
  
ALTER TABLE ColumnstoreTable1   
REBUILD PARTITION = ALL WITH (DATA_COMPRESSION =  COLUMNSTORE ON PARTITIONS (2,4) ) ;  
  
```  
  
 <span data-ttu-id="a98d4-180">下一個範例會在某些資料分割上將資料壓縮設定為資料行存放區，以及在其他資料分割上設定為資料行存放區封存。</span><span class="sxs-lookup"><span data-stu-id="a98d4-180">This next example sets the data compression to columnstore on some partitions, and to columnstore archival on other partitions.</span></span>  
  
```  
ALTER TABLE ColumnstoreTable1   
REBUILD PARTITION = ALL WITH (  
    DATA_COMPRESSION =  COLUMNSTORE ON PARTITIONS (4,5),  
    DATA COMPRESSION = COLUMNSTORE_ARCHIVE ON PARTITIONS (1,2,3)  
) ;  
```  
  
### <a name="performance"></a><span data-ttu-id="a98d4-181">效能</span><span class="sxs-lookup"><span data-stu-id="a98d4-181">Performance</span></span>  
 <span data-ttu-id="a98d4-182">以封存壓縮壓縮資料行存放區索引將會造成該索引的效能比沒有封存壓縮的資料行存放區索引還要慢。</span><span class="sxs-lookup"><span data-stu-id="a98d4-182">Compressing columnstore indexes with archival compression will cause the index to perform slower than columnstore indexes that do not have the archival compression.</span></span>  <span data-ttu-id="a98d4-183">只有當您可以負擔使用額外時間和 CPU 資源來壓縮及擷取資料時，才使用封存壓縮。</span><span class="sxs-lookup"><span data-stu-id="a98d4-183">Use archival compression only when you can afford to use extra time and CPU resources to compress and retrieve the data.</span></span>  
  
 <span data-ttu-id="a98d4-184">效能減緩的好處就是減少儲存體，這對於不常存取的資料很實用。</span><span class="sxs-lookup"><span data-stu-id="a98d4-184">The benefit of slower performance is reduced storage which is useful for data that is not frequently accessed.</span></span> <span data-ttu-id="a98d4-185">例如，如果您每個月的資料都有一個資料分割，而您的大多數活動發生在最近的月份，您可以封存較舊的月份來減少儲存需求。</span><span class="sxs-lookup"><span data-stu-id="a98d4-185">For example, if you have a partition for each month of data, and most of your activity is for the most recent months, you could archive older months to reduce the storage requirements.</span></span>  
  
### <a name="metadata"></a><span data-ttu-id="a98d4-186">中繼資料</span><span class="sxs-lookup"><span data-stu-id="a98d4-186">Metadata</span></span>  
 <span data-ttu-id="a98d4-187">下列系統檢視表包含叢集索引之資料壓縮的相關資訊：</span><span class="sxs-lookup"><span data-stu-id="a98d4-187">The following system views contain information about data compression for clustered indexes:</span></span>  
  
-   <span data-ttu-id="a98d4-188">[&#40;transact-sql&#41;的索引](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql)-和資料行包含叢集資料行存放區 `type` 和非叢集資料行存放區 `type_desc` 。</span><span class="sxs-lookup"><span data-stu-id="a98d4-188">[sys.indexes &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql) - The `type` and `type_desc` columns include CLUSTERED COLUMNSTORE and NONCLUSTERED COLUMNSTORE.</span></span>  
  
-   <span data-ttu-id="a98d4-189">[sys.databases &#40;transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-partitions-transact-sql) - `data_compression` 和資料行包含資料行存放區 `data_compression_desc` 和 COLUMNSTORE_ARCHIVE。</span><span class="sxs-lookup"><span data-stu-id="a98d4-189">[sys.partitions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-partitions-transact-sql) - The `data_compression` and `data_compression_desc` columns include COLUMNSTORE and COLUMNSTORE_ARCHIVE.</span></span>  
  
 <span data-ttu-id="a98d4-190">[sp_estimate_data_compression_savings &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql) 程序不適用於資料行存放區索引。</span><span class="sxs-lookup"><span data-stu-id="a98d4-190">The procedure [sp_estimate_data_compression_savings &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql) does not apply to columnstore indexes.</span></span>  
  
## <a name="how-compression-affects-partitioned-tables-and-indexes"></a><span data-ttu-id="a98d4-191">壓縮對分割資料表和索引有何影響</span><span class="sxs-lookup"><span data-stu-id="a98d4-191">How Compression Affects Partitioned Tables and Indexes</span></span>  
 <span data-ttu-id="a98d4-192">當您搭配分割資料表和索引使用資料壓縮時，請注意以下考量事項：</span><span class="sxs-lookup"><span data-stu-id="a98d4-192">When you use data compression with partitioned tables and indexes, be aware of the following considerations:</span></span>  
  
-   <span data-ttu-id="a98d4-193">當使用 ALTER PARTITION 陳述式分割資料分割時，兩個資料分割都會繼承原始資料分割的資料壓縮屬性。</span><span class="sxs-lookup"><span data-stu-id="a98d4-193">When partitions are split by using the ALTER PARTITION statement, both partitions inherit the data compression attribute of the original partition.</span></span>  
  
-   <span data-ttu-id="a98d4-194">當合併兩個資料分割時，所產生的資料分割會繼承目標資料分割的資料壓縮屬性。</span><span class="sxs-lookup"><span data-stu-id="a98d4-194">When two partitions are merged, the resultant partition inherits the data compression attribute of the destination partition.</span></span>  
  
-   <span data-ttu-id="a98d4-195">若要切換資料分割，此資料分割的資料壓縮屬性必須符合資料表的壓縮屬性。</span><span class="sxs-lookup"><span data-stu-id="a98d4-195">To switch a partition, the data compression property of the partition must match the compression property of the table.</span></span>  
  
-   <span data-ttu-id="a98d4-196">您可以使用兩種語法變化來修改分割資料表或索引的壓縮：</span><span class="sxs-lookup"><span data-stu-id="a98d4-196">There are two syntax variations that you can use to modify the compression of a partitioned table or index:</span></span>  
  
    -   <span data-ttu-id="a98d4-197">下列語法只會重建參考的資料分割：</span><span class="sxs-lookup"><span data-stu-id="a98d4-197">The following syntax rebuilds only the referenced partition:</span></span>  
  
        ```  
        ALTER TABLE <table_name>   
        REBUILD PARTITION = 1 WITH (DATA_COMPRESSION =  <option>)  
        ```  
  
    -   <span data-ttu-id="a98d4-198">下列語法會將現有的壓縮設定用於任何未參考的資料分割，藉以重建整個資料表：</span><span class="sxs-lookup"><span data-stu-id="a98d4-198">The following syntax rebuilds the whole table by using the existing compression setting for any partitions that are not referenced:</span></span>  
  
        ```  
        ALTER TABLE <table_name>   
        REBUILD PARTITION = ALL   
        WITH (DATA_COMPRESSION = PAGE ON PARTITIONS(<range>),  
        ... )  
        ```  
  
     <span data-ttu-id="a98d4-199">分割索引會遵循使用 ALTER INDEX 的相同原則。</span><span class="sxs-lookup"><span data-stu-id="a98d4-199">Partitioned indexes follow the same principle using ALTER INDEX.</span></span>  
  
-   <span data-ttu-id="a98d4-200">當卸除叢集索引時，除非修改了資料分割配置，否則對應的堆積資料分割會保留其資料壓縮設定。</span><span class="sxs-lookup"><span data-stu-id="a98d4-200">When a clustered index is dropped, the corresponding heap partitions retain their data compression setting unless the partitioning scheme is modified.</span></span> <span data-ttu-id="a98d4-201">如果資料分割配置有所變更，所有資料分割都會重建為未壓縮的狀態。</span><span class="sxs-lookup"><span data-stu-id="a98d4-201">If the partitioning scheme is changed, all partitions are rebuilt to an uncompressed state.</span></span> <span data-ttu-id="a98d4-202">若要卸除叢集索引及變更資料分割配置，您需要執行以下步驟：</span><span class="sxs-lookup"><span data-stu-id="a98d4-202">To drop a clustered index and change the partitioning scheme requires the following steps:</span></span>  
  
     1. <span data-ttu-id="a98d4-203">卸除叢集索引。</span><span class="sxs-lookup"><span data-stu-id="a98d4-203">Drop the clustered index.</span></span>  
  
     2. <span data-ttu-id="a98d4-204">使用指定壓縮選項的 ALTER TABLE ...REBUILD ... 選項來修改資料表。</span><span class="sxs-lookup"><span data-stu-id="a98d4-204">Modify the table by using the ALTER TABLE ... REBUILD ... option that specifies the compression option.</span></span>  
  
     <span data-ttu-id="a98d4-205">在線上卸除叢集索引將會是非常快速的作業，因為只會移除叢集索引的上層。</span><span class="sxs-lookup"><span data-stu-id="a98d4-205">To drop a clustered index OFFLINE is a very fast operation, because only the upper levels of clustered indexes are removed.</span></span> <span data-ttu-id="a98d4-206">在線上卸除叢集索引時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 必須重建堆積兩次，一次在步驟 1，另一次在步驟 2。</span><span class="sxs-lookup"><span data-stu-id="a98d4-206">When a clustered index is dropped ONLINE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must rebuild the heap two times, once for step 1 and once for step 2.</span></span>  
  
## <a name="how-compression-affects-replication"></a><span data-ttu-id="a98d4-207">壓縮將如何影響複寫</span><span class="sxs-lookup"><span data-stu-id="a98d4-207">How Compression Affects Replication</span></span>  
 <span data-ttu-id="a98d4-208">當您搭配複寫使用資料壓縮時，請注意以下考量事項：</span><span class="sxs-lookup"><span data-stu-id="a98d4-208">When you are using data compression with replication, be aware of the following considerations:</span></span>  
  
-   <span data-ttu-id="a98d4-209">當快照集代理程式產生最初的結構描述指令碼時，新的結構描述會將相同的壓縮設定用於資料表和它的索引。</span><span class="sxs-lookup"><span data-stu-id="a98d4-209">When the Snapshot Agent generates the initial schema script, the new schema will use the same compression settings for both the table and its indexes.</span></span> <span data-ttu-id="a98d4-210">不能只在資料表上啟用壓縮，而不在索引上啟用壓縮。</span><span class="sxs-lookup"><span data-stu-id="a98d4-210">Compression cannot be enabled on just the table and not the index.</span></span>  
  
-   <span data-ttu-id="a98d4-211">如果是異動複寫，發行項結構描述選項會判斷哪些相依的物件和屬性必須編寫指令碼。</span><span class="sxs-lookup"><span data-stu-id="a98d4-211">For transactional replication the article schema option determines what dependent objects and properties have to be scripted.</span></span> <span data-ttu-id="a98d4-212">如需詳細資訊，請參閱 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a98d4-212">For more information, see [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql).</span></span>  
  
     <span data-ttu-id="a98d4-213">散發代理程式在套用指令碼時，不會檢查是否有下層的訂閱者。</span><span class="sxs-lookup"><span data-stu-id="a98d4-213">The Distribution Agent does not check for down-level Subscribers when it applies scripts.</span></span> <span data-ttu-id="a98d4-214">如果選取了壓縮的複寫，在下層訂閱者上建立資料表將會失敗。</span><span class="sxs-lookup"><span data-stu-id="a98d4-214">If the replication of compression is selected, creating the table on down-level Subscribers will fail.</span></span> <span data-ttu-id="a98d4-215">如果是混合拓撲，請勿啟用壓縮的複寫。</span><span class="sxs-lookup"><span data-stu-id="a98d4-215">In the case of a mixed topology, do not enable the replication of compression.</span></span>  
  
-   <span data-ttu-id="a98d4-216">如果是合併式複寫，發行集相容性層級會覆寫結構描述選項，並判斷將要編寫指令碼的結構描述物件。</span><span class="sxs-lookup"><span data-stu-id="a98d4-216">For merge replication, publication compatibility level overrides the schema options and determines the schema objects that will be scripted.</span></span>  
  
     <span data-ttu-id="a98d4-217">在混合拓撲的情況下，如果它不必支援新的壓縮選項，則發行集相容性層級應該設定為下層的訂閱者版本。</span><span class="sxs-lookup"><span data-stu-id="a98d4-217">In the case of a mixed topology, if it is not required to support the new compression options, the publication compatibility level should be set to the down-level Subscriber version.</span></span> <span data-ttu-id="a98d4-218">如果需要的話，請於建立資料表之後在訂閱者上壓縮資料表。</span><span class="sxs-lookup"><span data-stu-id="a98d4-218">If it is required, compress tables on the Subscriber after they have been created.</span></span>  
  
 <span data-ttu-id="a98d4-219">下表顯示在複寫期間控制壓縮的複寫設定。</span><span class="sxs-lookup"><span data-stu-id="a98d4-219">The following table shows replication settings that control compression during replication.</span></span>  
  
|<span data-ttu-id="a98d4-220">使用者意圖</span><span class="sxs-lookup"><span data-stu-id="a98d4-220">User intent</span></span>|<span data-ttu-id="a98d4-221">複寫資料表或索引的資料分割配置</span><span class="sxs-lookup"><span data-stu-id="a98d4-221">Replicate partition scheme for a table or index</span></span>|<span data-ttu-id="a98d4-222">複寫壓縮設定</span><span class="sxs-lookup"><span data-stu-id="a98d4-222">Replicate compression settings</span></span>|<span data-ttu-id="a98d4-223">指令碼行為</span><span class="sxs-lookup"><span data-stu-id="a98d4-223">Scripting behavior</span></span>|  
|-----------------|-----------------------------------------------------|------------------------------------|------------------------|  
|<span data-ttu-id="a98d4-224">複寫資料分割配置，以及在資料分割的訂閱者上啟用壓縮。</span><span class="sxs-lookup"><span data-stu-id="a98d4-224">To replicate the partition scheme and enable compression on the Subscriber on the partition.</span></span>|<span data-ttu-id="a98d4-225">True</span><span class="sxs-lookup"><span data-stu-id="a98d4-225">True</span></span>|<span data-ttu-id="a98d4-226">True</span><span class="sxs-lookup"><span data-stu-id="a98d4-226">True</span></span>|<span data-ttu-id="a98d4-227">同時針對資料分割配置和壓縮設定編寫指令碼。</span><span class="sxs-lookup"><span data-stu-id="a98d4-227">Scripts both the partition scheme and the compression settings.</span></span>|  
|<span data-ttu-id="a98d4-228">複寫資料分割配置，但是不壓縮訂閱者上的資料。</span><span class="sxs-lookup"><span data-stu-id="a98d4-228">To replicate the partition scheme but not compress the data on the Subscriber.</span></span>|<span data-ttu-id="a98d4-229">是</span><span class="sxs-lookup"><span data-stu-id="a98d4-229">True</span></span>|<span data-ttu-id="a98d4-230">否</span><span class="sxs-lookup"><span data-stu-id="a98d4-230">False</span></span>|<span data-ttu-id="a98d4-231">針對資料分割配置編寫指令碼，但是不針對資料分割的壓縮設定編寫指令碼。</span><span class="sxs-lookup"><span data-stu-id="a98d4-231">Scripts out the partition scheme but not the compression settings for the partition.</span></span>|  
|<span data-ttu-id="a98d4-232">不複寫資料分割配置，而且不壓縮訂閱者上的資料。</span><span class="sxs-lookup"><span data-stu-id="a98d4-232">To not replicate the partition scheme and not compress the data on the Subscriber.</span></span>|<span data-ttu-id="a98d4-233">False</span><span class="sxs-lookup"><span data-stu-id="a98d4-233">False</span></span>|<span data-ttu-id="a98d4-234">False</span><span class="sxs-lookup"><span data-stu-id="a98d4-234">False</span></span>|<span data-ttu-id="a98d4-235">不針對資料分割或壓縮設定編寫指令碼。</span><span class="sxs-lookup"><span data-stu-id="a98d4-235">Does not script partition or compression settings.</span></span>|  
|<span data-ttu-id="a98d4-236">如果所有資料分割都在發行者上壓縮，則壓縮訂閱者上的資料表，但是不複寫資料分割配置。</span><span class="sxs-lookup"><span data-stu-id="a98d4-236">To compress the table on the Subscriber if all the partitions are compressed on the Publisher, but not replicate the partition scheme.</span></span>|<span data-ttu-id="a98d4-237">否</span><span class="sxs-lookup"><span data-stu-id="a98d4-237">False</span></span>|<span data-ttu-id="a98d4-238">True</span><span class="sxs-lookup"><span data-stu-id="a98d4-238">True</span></span>|<span data-ttu-id="a98d4-239">檢查所有資料分割是否啟用壓縮。</span><span class="sxs-lookup"><span data-stu-id="a98d4-239">Checks if all the partitions are enabled for compression.</span></span><br /><br /> <span data-ttu-id="a98d4-240">針對資料表層級上的壓縮編寫指令碼。</span><span class="sxs-lookup"><span data-stu-id="a98d4-240">Scripts out compression at the table level.</span></span>|  
  
## <a name="how-compression-affects-other-sql-server-components"></a><span data-ttu-id="a98d4-241">壓縮對於其他 SQL Server 元件有何影響</span><span class="sxs-lookup"><span data-stu-id="a98d4-241">How Compression Affects Other SQL Server Components</span></span>  
 <span data-ttu-id="a98d4-242">壓縮會發生在儲存引擎中，而且資料會以非壓縮狀態呈現給 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的大多數其他元件。</span><span class="sxs-lookup"><span data-stu-id="a98d4-242">Compression occurs in the storage engine and the data is presented to most of the other components of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in an uncompressed state.</span></span> <span data-ttu-id="a98d4-243">這樣會將壓縮對其他元件的影響限制為以下情況：</span><span class="sxs-lookup"><span data-stu-id="a98d4-243">This limits the effects of compression on the other components to the following:</span></span>  
  
-   <span data-ttu-id="a98d4-244">大量匯入及匯出作業</span><span class="sxs-lookup"><span data-stu-id="a98d4-244">Bulk import and export operations</span></span>  
  
     <span data-ttu-id="a98d4-245">當匯出資料時 (即使是原生格式)，資料為非壓縮資料列格式的輸出。</span><span class="sxs-lookup"><span data-stu-id="a98d4-245">When data is exported, even in native format, the data is output in the uncompressed row format.</span></span> <span data-ttu-id="a98d4-246">這可能會造成匯出的資料檔大小比來源資料大出許多。</span><span class="sxs-lookup"><span data-stu-id="a98d4-246">This can cause the size of exported data file to be significantly larger than the source data.</span></span>  
  
     <span data-ttu-id="a98d4-247">當匯入資料時，如果目標資料表已啟用壓縮，則儲存引擎會將資料轉換成壓縮的資料列格式。</span><span class="sxs-lookup"><span data-stu-id="a98d4-247">When data is imported, if the target table has been enabled for compression, the data is converted by the storage engine into compressed row format.</span></span> <span data-ttu-id="a98d4-248">這樣可能會造成 CPU 使用量增加 (相較於資料匯入未壓縮的資料表時)。</span><span class="sxs-lookup"><span data-stu-id="a98d4-248">This can cause increased CPU usage compared to when data is imported into an uncompressed table.</span></span>  
  
     <span data-ttu-id="a98d4-249">將資料大量匯入具有頁面壓縮的堆積內時，大量匯入作業會在插入具有頁面壓縮的資料時，嘗試壓縮這些資料。</span><span class="sxs-lookup"><span data-stu-id="a98d4-249">When data is bulk imported into a heap with page compression, the bulk import operation will try to compress the data with page compression when the data is inserted.</span></span>  
  
-   <span data-ttu-id="a98d4-250">壓縮不會影響備份和還原。</span><span class="sxs-lookup"><span data-stu-id="a98d4-250">Compression does not affect backup and restore.</span></span>  
  
-   <span data-ttu-id="a98d4-251">壓縮不會影響記錄傳送。</span><span class="sxs-lookup"><span data-stu-id="a98d4-251">Compression does not affect log shipping.</span></span>  
  
-   <span data-ttu-id="a98d4-252">資料壓縮與疏鬆資料行不相容。</span><span class="sxs-lookup"><span data-stu-id="a98d4-252">Data compression is incompatible with sparse columns.</span></span> <span data-ttu-id="a98d4-253">因此，包含疏鬆資料行的資料表無法加以壓縮，也無法將疏鬆資料行加入至壓縮的資料表。</span><span class="sxs-lookup"><span data-stu-id="a98d4-253">Therefore, tables containing sparse columns cannot be compressed nor can sparse columns be added to a compressed table.</span></span>  
  
-   <span data-ttu-id="a98d4-254">啟用壓縮可能會造成查詢計畫變更，因為系統會使用不同的頁數以及每頁不同的資料列數來儲存資料。</span><span class="sxs-lookup"><span data-stu-id="a98d4-254">Enabling compression can cause query plans to change because the data is stored using a different number of pages and number of rows per page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a98d4-255">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a98d4-255">See Also</span></span>  
 <span data-ttu-id="a98d4-256">[資料列壓縮實作](row-compression-implementation.md) </span><span class="sxs-lookup"><span data-stu-id="a98d4-256">[Row Compression Implementation](row-compression-implementation.md) </span></span>  
 <span data-ttu-id="a98d4-257">[頁面壓縮實作](page-compression-implementation.md) </span><span class="sxs-lookup"><span data-stu-id="a98d4-257">[Page Compression Implementation](page-compression-implementation.md) </span></span>  
 <span data-ttu-id="a98d4-258">[Unicode 壓縮實作](unicode-compression-implementation.md) </span><span class="sxs-lookup"><span data-stu-id="a98d4-258">[Unicode Compression Implementation](unicode-compression-implementation.md) </span></span>  
 <span data-ttu-id="a98d4-259">[CREATE PARTITION SCHEME &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-partition-scheme-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a98d4-259">[CREATE PARTITION SCHEME &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-partition-scheme-transact-sql) </span></span>  
 <span data-ttu-id="a98d4-260">[CREATE PARTITION FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-partition-function-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a98d4-260">[CREATE PARTITION FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-partition-function-transact-sql) </span></span>  
 <span data-ttu-id="a98d4-261">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a98d4-261">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span></span>  
 <span data-ttu-id="a98d4-262">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a98d4-262">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span></span>  
 <span data-ttu-id="a98d4-263">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a98d4-263">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 [<span data-ttu-id="a98d4-264">ALTER INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a98d4-264">ALTER INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-index-transact-sql)  
  
  
