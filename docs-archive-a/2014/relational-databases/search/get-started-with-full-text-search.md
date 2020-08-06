---
title: 全文檢索搜尋使用者入門 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text catalogs [SQL Server], creating
- full-text indexes [SQL Server], creating
- full-text search [SQL Server], about
- full-text search [SQL Server], setting up
ms.assetid: 1fa628ba-0ee4-4d8f-b086-c4e52962ca4a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: eec806bffba330ac3ab995c1b3bfd3504589ecfd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697822"
---
# <a name="get-started-with-full-text-search"></a><span data-ttu-id="dc559-102">全文檢索搜尋使用者入門</span><span class="sxs-lookup"><span data-stu-id="dc559-102">Get Started with Full-Text Search</span></span>
  <span data-ttu-id="dc559-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的資料庫預設會啟用全文檢索。</span><span class="sxs-lookup"><span data-stu-id="dc559-103">Databases in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are full-text enabled by default.</span></span> <span data-ttu-id="dc559-104">不過，若要針對資料表使用全文檢索索引，您必須在要以全文檢索引擎存取的資料表資料行中設定全文檢索索引功能。</span><span class="sxs-lookup"><span data-stu-id="dc559-104">However, to use a full-text index on a table, you must set up full-text indexing capability on the columns of the tables that you want to access using the Full-Text Engine.</span></span>  
  
##  <a name="configuring-a-database-for-full-text-search"></a><a name="configure"></a><span data-ttu-id="dc559-105">設定全文檢索搜尋的資料庫</span><span class="sxs-lookup"><span data-stu-id="dc559-105">Configuring a Database for Full-Text Search</span></span>  
 <span data-ttu-id="dc559-106">在任何案例中，資料庫管理員都會執行下列基本步驟，針對全文檢索搜尋設定資料庫中的資料表資料行：</span><span class="sxs-lookup"><span data-stu-id="dc559-106">For any scenario, a database administrator performs the following basic steps to configure table columns in a database for full-text search:</span></span>  
  
1.  <span data-ttu-id="dc559-107">建立全文檢索目錄。</span><span class="sxs-lookup"><span data-stu-id="dc559-107">Create a full-text catalog.</span></span>  
  
2.  <span data-ttu-id="dc559-108">在您想要搜尋的每個資料表上，建立全文檢索索引：</span><span class="sxs-lookup"><span data-stu-id="dc559-108">On each table that you want to search, create a full-text index by:</span></span>  
  
    1.  <span data-ttu-id="dc559-109">識別您想要包含在全文檢索索引中的每個文字資料行。</span><span class="sxs-lookup"><span data-stu-id="dc559-109">Identify each text columns that you want to include in the full-text index.</span></span>  
  
    2.  <span data-ttu-id="dc559-110">如果給定的資料行包含儲存為二進位資料 (`varbinary(max)` 或 `image` 資料) 的檔，您就必須指定資料表資料行 ([類型] 資料*行*) 識別要編制索引之資料行中每份檔的類型。</span><span class="sxs-lookup"><span data-stu-id="dc559-110">If a given column contains documents stored as binary data (`varbinary(max)`, or `image` data), you must specify a table column (the *type column*) that identifies the type of each document in the column being indexed.</span></span>  
  
    3.  <span data-ttu-id="dc559-111">指定您想讓全文檢索搜尋用於資料行中文件的語言。</span><span class="sxs-lookup"><span data-stu-id="dc559-111">Specify the language that you want full-text search to use on the documents in the column.</span></span>  
  
    4.  <span data-ttu-id="dc559-112">選擇您想要針對全文檢索索引使用的變更追蹤機制，以便追蹤基底資料表及其資料行中的變更。</span><span class="sxs-lookup"><span data-stu-id="dc559-112">Choose the change-tracking mechanism that you want to use on the full-text index to track changes in the base table and its columns.</span></span>  
  
 <span data-ttu-id="dc559-113">全文檢索搜尋會透過使用下列「語言元件」\*\*(Linguistic Component) 支援多國語言：斷詞工具和字幹分析器、包含停用字詞 (也稱為非搜尋字) 的停用字詞表，以及同義字檔案。</span><span class="sxs-lookup"><span data-stu-id="dc559-113">Full-text search supports multiple languages through the use of the following *linguistic components*: word breakers and stemmers, stoplists that contain stopwords (also known as noise words), and thesaurus files.</span></span> <span data-ttu-id="dc559-114">同義字檔案和停用字詞表 (在某些情況下) 會要求資料庫管理員進行組態設定。</span><span class="sxs-lookup"><span data-stu-id="dc559-114">Thesaurus files and, in some cases, stoplists require configuration by a database administrator.</span></span> <span data-ttu-id="dc559-115">給定的同義字檔案支援所有使用對應語言的全文檢索索引，而且給定的停用字詞表可以與任意數目的全文檢索索引相關聯。</span><span class="sxs-lookup"><span data-stu-id="dc559-115">A given thesaurus file supports all full-text indexes that use the corresponding language, and a given stoplist can be associated with as many full-text indexes as you want.</span></span>  
  
##  <a name="setting-up-a-full-text-catalog-and-index"></a><a name="setup"></a><span data-ttu-id="dc559-116">設定全文檢索目錄和索引</span><span class="sxs-lookup"><span data-stu-id="dc559-116">Setting Up a Full-Text Catalog and Index</span></span>  
 <span data-ttu-id="dc559-117">這項作業包含下列基本步驟：</span><span class="sxs-lookup"><span data-stu-id="dc559-117">This involves the following basic steps:</span></span>  
  
1.  <span data-ttu-id="dc559-118">建立全文檢索目錄以儲存全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="dc559-118">Create a full-text catalog to store full-text indexes.</span></span>  
  
     <span data-ttu-id="dc559-119">每個全文檢索索引都必須屬於一個全文檢索目錄。</span><span class="sxs-lookup"><span data-stu-id="dc559-119">Each full-text index must belong to a full-text catalog.</span></span> <span data-ttu-id="dc559-120">您可以針對每個全文檢索索引建立個別的文字目錄，也可以讓多個全文檢索索引與給定的目錄產生關聯。</span><span class="sxs-lookup"><span data-stu-id="dc559-120">You can create a separate text catalog for each full-text index, or you can associate multiple full-text indexes with a given catalog.</span></span> <span data-ttu-id="dc559-121">全文檢索目錄是虛擬物件，而且不屬於任何檔案群組。</span><span class="sxs-lookup"><span data-stu-id="dc559-121">A full-text catalog is a virtual object and does not belong to any filegroup.</span></span> <span data-ttu-id="dc559-122">目錄是參考一組全文檢索索引的邏輯概念。</span><span class="sxs-lookup"><span data-stu-id="dc559-122">The catalog is a logical concept that refers to a group of full-text indexes.</span></span>  
  
2.  <span data-ttu-id="dc559-123">針對資料表或索引檢視表建立全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="dc559-123">Create a full-text index on the table or indexed view.</span></span>  
  
     <span data-ttu-id="dc559-124">全文檢索索引是一種特殊類型的 Token 式功能索引，由全文檢索引擎所建立與維護。</span><span class="sxs-lookup"><span data-stu-id="dc559-124">A full-text index is a special type of token-based functional index that is built and maintained by the Full-Text Engine.</span></span> <span data-ttu-id="dc559-125">若要針對資料表或檢視表建立全文檢索搜尋，它必須具有唯一、單一資料行且不可為 Null 的索引。</span><span class="sxs-lookup"><span data-stu-id="dc559-125">To create full-text search on a table or view, it must have a unique, single-column, non-nullable index.</span></span> <span data-ttu-id="dc559-126">全文檢索引擎需要使用此唯一索引，將資料表中的各資料列對應至唯一且可壓縮的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="dc559-126">The Full-Text Engine requires this unique index to map each row in the table to a unique, compressible key.</span></span> <span data-ttu-id="dc559-127">全文檢索索引可以包括 `char`、`varchar`、`nchar``nvarchar`、`text`、`ntext`、`image`、`xml`、`varbinary` 和 `varbinary(max)` 資料行。</span><span class="sxs-lookup"><span data-stu-id="dc559-127">A full-text index can include `char`, `varchar`, `nchar`, `nvarchar`, `text`, `ntext`, `image`, `xml`, `varbinary`, and `varbinary(max)` columns.</span></span> <span data-ttu-id="dc559-128">如需詳細資訊，請參閱 [建立及管理全文檢索索引](create-and-manage-full-text-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="dc559-128">For more information, see [Create and Manage Full-Text Indexes](create-and-manage-full-text-indexes.md).</span></span>  
  
 <span data-ttu-id="dc559-129">學習建立全文檢索索引之前，請務必了解全文檢索索引與一般 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 索引的差異。</span><span class="sxs-lookup"><span data-stu-id="dc559-129">Before learning about creating full-text indexes, it is important to consider how they differ from regular [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] indexes.</span></span> <span data-ttu-id="dc559-130">下表列出差異。</span><span class="sxs-lookup"><span data-stu-id="dc559-130">The following table lists the differences.</span></span>  
  
|<span data-ttu-id="dc559-131">全文檢索索引</span><span class="sxs-lookup"><span data-stu-id="dc559-131">Full-text indexes</span></span>|<span data-ttu-id="dc559-132">一般 SQL Server 索引</span><span class="sxs-lookup"><span data-stu-id="dc559-132">Regular SQL Server indexes</span></span>|  
|------------------------|--------------------------------|  
|<span data-ttu-id="dc559-133">每個資料表只允許有一個全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="dc559-133">Only one full-text index allowed per table.</span></span>|<span data-ttu-id="dc559-134">每個資料表允許有多個一般索引。</span><span class="sxs-lookup"><span data-stu-id="dc559-134">Several regular indexes allowed per table.</span></span>|  
|<span data-ttu-id="dc559-135">將資料加入至全文檢索索引的作業稱為「母體擴展」(Population)，可透過排程或特定的要求來要求執行，也可在加入新的資料時自動執行。</span><span class="sxs-lookup"><span data-stu-id="dc559-135">The addition of data to full-text indexes, called a *population*, can be requested through either a schedule or a specific request, or can occur automatically with the addition of new data.</span></span>|<span data-ttu-id="dc559-136">當依據的資料有插入、更新或刪除時，會自動更新索引內容。</span><span class="sxs-lookup"><span data-stu-id="dc559-136">Updated automatically when the data upon which they are based is inserted, updated, or deleted.</span></span>|  
|<span data-ttu-id="dc559-137">在相同的資料庫中分組為一個或多個全文檢索目錄。</span><span class="sxs-lookup"><span data-stu-id="dc559-137">Grouped within the same database into one or more full-text catalogs.</span></span>|<span data-ttu-id="dc559-138">沒有分組。</span><span class="sxs-lookup"><span data-stu-id="dc559-138">Not grouped.</span></span>|  
  
  
##  <a name="choosing-options-for-a-full-text-index"></a><a name="options"></a><span data-ttu-id="dc559-139">選擇全文檢索索引的選項</span><span class="sxs-lookup"><span data-stu-id="dc559-139">Choosing Options for a Full-Text Index</span></span>  
 <span data-ttu-id="dc559-140">本節內容包括下列主題：</span><span class="sxs-lookup"><span data-stu-id="dc559-140">This section covers the following:</span></span>  
  
-   <span data-ttu-id="dc559-141">選擇資料行語言</span><span class="sxs-lookup"><span data-stu-id="dc559-141">Choosing the column language</span></span>  
  
-   <span data-ttu-id="dc559-142">選擇全文檢索索引的檔案群組</span><span class="sxs-lookup"><span data-stu-id="dc559-142">Choosing a filegroup for a full-text index</span></span>  
  
-   <span data-ttu-id="dc559-143">將全文檢索索引指派給全文檢索目錄</span><span class="sxs-lookup"><span data-stu-id="dc559-143">Assigning the full-text index to a full-text catalog</span></span>  
  
-   <span data-ttu-id="dc559-144">將停用字詞表與全文檢索索引產生關聯</span><span class="sxs-lookup"><span data-stu-id="dc559-144">Associating a stoplist with the full-text index</span></span>  
  
-   <span data-ttu-id="dc559-145">更新全文檢索索引</span><span class="sxs-lookup"><span data-stu-id="dc559-145">Updating a full-text index</span></span>  
  
### <a name="choosing-the-column-language"></a><span data-ttu-id="dc559-146">選擇資料行語言</span><span class="sxs-lookup"><span data-stu-id="dc559-146">Choosing the Column Language</span></span>  
 <span data-ttu-id="dc559-147">如需有關選擇資料行語言時應考慮哪些事項的詳細資訊，請參閱[選擇建立全文檢索索引時的語言](choose-a-language-when-creating-a-full-text-index.md)。</span><span class="sxs-lookup"><span data-stu-id="dc559-147">For information about things to consider when you are choosing the column language, see [Choose a Language When Creating a Full-Text Index](choose-a-language-when-creating-a-full-text-index.md).</span></span>  
  
### <a name="choosing-a-filegroup-for-a-full-text-index"></a><span data-ttu-id="dc559-148">選擇全文檢索索引的檔案群組</span><span class="sxs-lookup"><span data-stu-id="dc559-148">Choosing a Filegroup for a Full-Text Index</span></span>  
 <span data-ttu-id="dc559-149">建立全文檢索索引的程序需要大量 I/O (在較高層次中，此程序包括從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中讀取資料，然後將篩選的資料傳播至全文檢索索引)。</span><span class="sxs-lookup"><span data-stu-id="dc559-149">The process of building a full-text index is fairly I/O intensive (on a high level, it consists of reading data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and then propagating the filtered data to the full-text index).</span></span> <span data-ttu-id="dc559-150">最佳作法是將全文檢索索引放置於最適合將 I/O 效能發揮到極致的資料庫檔案群組中，或是將全文檢索索引放置於另一個磁碟區的不同檔案群組中。</span><span class="sxs-lookup"><span data-stu-id="dc559-150">As a best practice, locate a full-text index in the database filegroup that is best for maximizing I/O performance or locate the full-text indexes in a different filegroup on another volume.</span></span>  
  
 <span data-ttu-id="dc559-151">如果管理方便對您很重要，我們建議您將資料表資料及任何附屬的全文檢索目錄儲存在相同檔案群組中。</span><span class="sxs-lookup"><span data-stu-id="dc559-151">When ease of management is important to you, we recommend that you store table data and any affiliated full-text catalogs in the same filegroup.</span></span> <span data-ttu-id="dc559-152">有時候，基於效能的考量，您可能會想要將資料表資料和全文檢索索引存放在儲存於不同磁碟區上的不同檔案群組中，以便有效發揮 I/O 平行處理原則。</span><span class="sxs-lookup"><span data-stu-id="dc559-152">Sometimes, for performance reasons, you might want to have the table data and the full-text index in different filegroups that are stored on different volumes to maximize I/O parallelism.</span></span>  
  
  
### <a name="assigning-the-full-text-index-to-a-full-text-catalog"></a><span data-ttu-id="dc559-153">將全文檢索索引指派給全文檢索目錄</span><span class="sxs-lookup"><span data-stu-id="dc559-153">Assigning the Full-Text Index to a Full-Text Catalog</span></span>  
 <span data-ttu-id="dc559-154">在全文檢索目錄中，規劃資料表之全文檢索索引的位置是相當重要的步驟。</span><span class="sxs-lookup"><span data-stu-id="dc559-154">It is important to plan the placement of full-text indexes for tables in full-text catalogs.</span></span>  
  
 <span data-ttu-id="dc559-155">我們建議您在相同的全文檢索目錄底下，將具有相同更新特性的資料表 (例如少量變更與大量變更，或在每日特定時段頻繁變更的資料表) 產生關聯。</span><span class="sxs-lookup"><span data-stu-id="dc559-155">We recommend associating tables with the same update characteristics (such as small number of changes versus large number of changes, or tables that change frequently during a particular time of day) together under the same full-text catalog.</span></span> <span data-ttu-id="dc559-156">透過設定全文檢索目錄的母體擴展排程，在高度資料庫活動期間，全文檢索索引仍然能夠保持與資料表同步，而不會對資料庫伺服器的資源使用量造成負面影響。</span><span class="sxs-lookup"><span data-stu-id="dc559-156">By setting up full-text catalog population schedules, full-text indexes stay synchronous with the tables without adversely affecting the resource usage of the database server during periods of high database activity.</span></span>  
  
 <span data-ttu-id="dc559-157">當您將資料表指派給全文檢索目錄時，請考量下列指導方針：</span><span class="sxs-lookup"><span data-stu-id="dc559-157">When you assign a table to a full-text catalog, consider the following guidelines:</span></span>  
  
-   <span data-ttu-id="dc559-158">永遠選取最小的唯一索引，做為全文檢索唯一索引鍵。</span><span class="sxs-lookup"><span data-stu-id="dc559-158">Always select the smallest unique index available for your full-text unique key.</span></span> <span data-ttu-id="dc559-159"> (4 位元組的整數型索引是最佳的。 ) 這會 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 大幅減少搜尋服務在檔案系統中所需的資源。</span><span class="sxs-lookup"><span data-stu-id="dc559-159">(A 4-byte, integer-based index is optimal.) This reduces the resources required by [!INCLUDE[msCoName](../../includes/msconame-md.md)] Search service in the file system significantly.</span></span> <span data-ttu-id="dc559-160">如果主索引鍵較大 (超過 101 個位元組) 時，可考慮選擇資料表中其他的唯一索引，做為全文檢索唯一的索引鍵 (或建立另一個唯一索引)。</span><span class="sxs-lookup"><span data-stu-id="dc559-160">If the primary key is large (over 100 bytes), consider choosing another unique index in the table (or creating another unique index) as the full-text unique key.</span></span> <span data-ttu-id="dc559-161">若全文檢索唯一索引鍵的大小超過允許的最大值 (900 個位元組) 時，將無法執行全文檢索的母體擴展作業。</span><span class="sxs-lookup"><span data-stu-id="dc559-161">Otherwise, if the full-text unique key size exceeds the maximum size allowed (900 bytes), full-text population will not be able to proceed.</span></span>  
  
-   <span data-ttu-id="dc559-162">如果您正在針對包含數百萬資料列的資料表建立索引，請將此資料表指派給它本身的全文檢索目錄。</span><span class="sxs-lookup"><span data-stu-id="dc559-162">If you are indexing a table that has millions of rows, assign the table to its own full-text catalog.</span></span>  
  
-   <span data-ttu-id="dc559-163">考慮正在建立全文檢索索引之資料表中發生的變更數量，以及資料列總數。</span><span class="sxs-lookup"><span data-stu-id="dc559-163">Consider the amount of changes occurring in the tables being full-text indexed, as well as the total number of rows.</span></span> <span data-ttu-id="dc559-164">如果變更的資料列總數，與上次執行全文檢索母體擴展的資料列總和超過百萬，請將此資料表指派給它本身的全文檢索目錄。</span><span class="sxs-lookup"><span data-stu-id="dc559-164">If the total number of rows being changed, together with the numbers of rows in the table present during the last full-text population, represents millions of rows, assign the table to its own full-text catalog.</span></span>  
  
  
### <a name="associating-a-stoplist-with-the-full-text-index"></a><span data-ttu-id="dc559-165">將停用字詞表與全文檢索索引產生關聯</span><span class="sxs-lookup"><span data-stu-id="dc559-165">Associating a Stoplist with the Full-Text Index</span></span>  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] <span data-ttu-id="dc559-166">導入了停用字詞表。</span><span class="sxs-lookup"><span data-stu-id="dc559-166">introduces stoplists.</span></span> <span data-ttu-id="dc559-167">*「停用字詞表」* (Stoplist) 是停用字詞 (也稱為非搜尋字) 的清單。</span><span class="sxs-lookup"><span data-stu-id="dc559-167">A *stoplist* is a list of stopwords, also known as noise words.</span></span> <span data-ttu-id="dc559-168">停用字詞表會與每個全文檢索索引相關聯，而且該停用字詞表中的字詞會套用至該索引的全文檢索查詢。</span><span class="sxs-lookup"><span data-stu-id="dc559-168">A stoplist is associated with each full-text index, and the words in that stoplist are applied to full-text queries on that index.</span></span> <span data-ttu-id="dc559-169">根據預設，系統停用字詞表會與新的全文檢索索引相關聯。</span><span class="sxs-lookup"><span data-stu-id="dc559-169">By default, the system stoplist is associated with a new full-text index.</span></span> <span data-ttu-id="dc559-170">不過，您可以改為建立並使用自己的停用字詞表。</span><span class="sxs-lookup"><span data-stu-id="dc559-170">However, you can create and use your own stoplist instead.</span></span> <span data-ttu-id="dc559-171">如需詳細資訊，請參閱 [設定及管理全文檢索搜尋的停用字詞與停用字詞表](configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="dc559-171">For more information, see [Configure and Manage Stopwords and Stoplists for Full-Text Search](configure-and-manage-stopwords-and-stoplists-for-full-text-search.md).</span></span>  
  
 <span data-ttu-id="dc559-172">例如，下列[建立全文](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql)檢索停用字詞表 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 語句會從系統停用字詞表中複製，以建立名為 myStoplist3 的新全文檢索停用字詞表：</span><span class="sxs-lookup"><span data-stu-id="dc559-172">For example, the following [CREATE FULLTEXT STOPLIST](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement creates a new full-text stoplist named myStoplist3 by copying from the system stoplist:</span></span>  
  
```  
CREATE FULLTEXT STOPLIST myStoplist FROM SYSTEM STOPLIST;  
GO  
```  
  
 <span data-ttu-id="dc559-173">下列[ALTER 全文](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql)檢索停 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 用字詞表語句會改變名為 myStoplist 的停用字詞表，並加入 ' en ' 這個字，第一個是針對西班牙文，再針對法文</span><span class="sxs-lookup"><span data-stu-id="dc559-173">The following [ALTER FULLTEXT STOPLIST](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement alters a stoplist named myStoplist, adding the word 'en', first for Spanish and then for French:</span></span>  
  
```  
ALTER FULLTEXT STOPLIST MyStoplist ADD 'en' LANGUAGE 'Spanish';  
ALTER FULLTEXT STOPLIST MyStoplist ADD 'en' LANGUAGE 'French';  
GO  
```  
  
  
### <a name="updating-a-full-text-index"></a><span data-ttu-id="dc559-174">更新全文檢索索引</span><span class="sxs-lookup"><span data-stu-id="dc559-174">Updating a Full-Text Index</span></span>  
 <span data-ttu-id="dc559-175">如同一般 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 索引，當相關聯資料表中的資料變更時，就可以自動更新全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="dc559-175">Like regular [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] indexes, full-text indexes can be automatically updated as data is modified in the associated tables.</span></span> <span data-ttu-id="dc559-176">此為預設行為。</span><span class="sxs-lookup"><span data-stu-id="dc559-176">This is the default behavior.</span></span> <span data-ttu-id="dc559-177">或者，您也可以手動或以指定的排程間隔將全文檢索索引保持在最新狀態。</span><span class="sxs-lookup"><span data-stu-id="dc559-177">Alternatively, you can keep your full-text indexes up-to-date manually or at specified scheduled intervals.</span></span> <span data-ttu-id="dc559-178">擴展全文檢索索引可能會相當耗時而且需要大量資源，因此，索引更新通常會當做在背景中執行的非同步處理序執行並且在修改基底資料表之後，將全文檢索索引保持在最新狀態。</span><span class="sxs-lookup"><span data-stu-id="dc559-178">Populating a full-text index can be time-consuming and resource-intensive, therefore, index updating is usually performed as an asynchronous process that runs in the background and keeps the full-text index up to date after modifications in the base table.</span></span> <span data-ttu-id="dc559-179">在基底資料表每次變更之後立即更新全文檢索索引可能需要大量資源。</span><span class="sxs-lookup"><span data-stu-id="dc559-179">Updating a full-text index immediately after each change in the base table can be resource-intensive.</span></span> <span data-ttu-id="dc559-180">因此，如果您設定了非常高的更新/插入/刪除速率，可能會遇到查詢效能降低的情況。</span><span class="sxs-lookup"><span data-stu-id="dc559-180">Therefore, if you have a very high update/insert/delete rate, you might experience some degradation in query performance.</span></span> <span data-ttu-id="dc559-181">如果發生這種情況，請考慮排程手動變更追蹤更新，以便偶爾與許多變更保持同步，而非與查詢競爭資源。</span><span class="sxs-lookup"><span data-stu-id="dc559-181">If this occurs, consider scheduling manual change tracking updates to keep up with the numerous changes from time to time, rather than competing with queries for resources.</span></span>  
  
 <span data-ttu-id="dc559-182">若要監視母體擴展狀態，請使用 FULLTEXTCATALOGPROPERTY 函數或 OBJECTPROPERTYEX 函數。</span><span class="sxs-lookup"><span data-stu-id="dc559-182">To monitor the population status, use either the FULLTEXTCATALOGPROPERTY or OBJECTPROPERTYEX functions.</span></span> <span data-ttu-id="dc559-183">若要取得目錄母體擴展狀態，請執行下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="dc559-183">To get the catalog population status, run the following statement:</span></span>  
  
```  
SELECT FULLTEXTCATALOGPROPERTY('AdvWksDocFTCat', 'Populatestatus');  
```  
  
 <span data-ttu-id="dc559-184">一般而言，如果完整母體擴展進行中，傳回的結果會是 1。</span><span class="sxs-lookup"><span data-stu-id="dc559-184">Typically, if a full population is in progress, the result returned is 1.</span></span>  
  
  
##  <a name="example-setting-up-full-text-search"></a><a name="example"></a><span data-ttu-id="dc559-185">範例：設定全文檢索搜尋</span><span class="sxs-lookup"><span data-stu-id="dc559-185">Example: Setting Up Full-Text Search</span></span>  
 <span data-ttu-id="dc559-186">下列兩部分的範例會針對 AdventureWorks 資料庫建立名為 `AdvWksDocFTCat` 的全文檢索目錄，然後針對 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 中的 `Document` 資料表建立全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="dc559-186">The following two-part example creates a full-text catalog named `AdvWksDocFTCat` on the AdventureWorks database and then creates a full-text index on the `Document` table in [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span> <span data-ttu-id="dc559-187">這個陳述式會在安裝期間所指定的預設目錄中建立全文檢索目錄。</span><span class="sxs-lookup"><span data-stu-id="dc559-187">This statement creates the full-text catalog in the default directory specified during setup.</span></span> <span data-ttu-id="dc559-188">名為 `AdvWksDocFTCat` 的資料夾位於預設的目錄中。</span><span class="sxs-lookup"><span data-stu-id="dc559-188">The folder named `AdvWksDocFTCat` is in the default directory.</span></span>  
  
1.  <span data-ttu-id="dc559-189">為了建立名為 `AdvWksDocFTCat`的全文檢索目錄，此範例會使用 [CREATE FULLTEXT CATALOG](/sql/t-sql/statements/create-fulltext-catalog-transact-sql) 陳述式：</span><span class="sxs-lookup"><span data-stu-id="dc559-189">To create a full-text catalog named `AdvWksDocFTCat`, the example uses a [CREATE FULLTEXT CATALOG](/sql/t-sql/statements/create-fulltext-catalog-transact-sql) statement:</span></span>  
  
    ```  
    USE AdventureWorks;  
    GO  
    CREATE FULLTEXT CATALOG AdvWksDocFTCat;  
    ```  
  
2.  <span data-ttu-id="dc559-190">針對 Document 資料表建立全文檢索索引之前，請確定此資料表具有唯一、單一資料行且不可為 Null 的索引。</span><span class="sxs-lookup"><span data-stu-id="dc559-190">Before you can create a full-text index on the Document table, ensure that the table has a unique, single-column, non-nullable index.</span></span> <span data-ttu-id="dc559-191">下列 [CREATE INDEX](/sql/t-sql/statements/create-index-transact-sql) 陳述式會針對 Document 資料表的 DocumentID 資料行建立唯一索引 `ui_ukDoc`：</span><span class="sxs-lookup"><span data-stu-id="dc559-191">The following [CREATE INDEX](/sql/t-sql/statements/create-index-transact-sql) statement creates a unique index, `ui_ukDoc`, on the DocumentID column of the Document table:</span></span>  
  
    ```  
    CREATE UNIQUE INDEX ui_ukDoc ON Production.Document(DocumentID);  
    ```  
  
3.  <span data-ttu-id="dc559-192">在您擁有唯一索引鍵之後，就可以使用下列 `Document` CREATE FULLTEXT INDEX [陳述式，針對](/sql/t-sql/statements/create-fulltext-index-transact-sql) 資料表建立全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="dc559-192">After you have a unique key, you can create a full-text index on the `Document` table by using the following [CREATE FULLTEXT INDEX](/sql/t-sql/statements/create-fulltext-index-transact-sql) statement.</span></span>  
  
    ```  
    CREATE FULLTEXT INDEX ON Production.Document  
    (  
        Document                         --Full-text index column name   
            TYPE COLUMN FileExtension    --Name of column that contains file type information  
            Language 2057                 --2057 is the LCID for British English  
    )  
    KEY INDEX ui_ukDoc ON AdvWksDocFTCat --Unique index  
    WITH CHANGE_TRACKING AUTO            --Population type;  
    GO  
  
    ```  
  
     <span data-ttu-id="dc559-193">在這個範例中定義的 TYPE COLUMN 會在資料表中指定類型資料行，其中在 'Document' 資料行的每個資料列中包含文件類型 (二進位類型)。</span><span class="sxs-lookup"><span data-stu-id="dc559-193">The TYPE COLUMN defined in this example specifies the type column in the table that contains the type of the document in each row of the column 'Document' (which is of binary type).</span></span> <span data-ttu-id="dc559-194">類型資料行會在給定的資料列中儲存使用者提供的副檔名-".doc"、".xls" 等等檔。</span><span class="sxs-lookup"><span data-stu-id="dc559-194">The type column stores the user-supplied file extension-".doc", ".xls", and so on-of the document in a given row.</span></span> <span data-ttu-id="dc559-195">全文檢索引擎會使用給定資料列中的副檔名來叫用正確的篩選，以便用於剖析該資料列中的資料。</span><span class="sxs-lookup"><span data-stu-id="dc559-195">The Full-Text Engine uses the file extension in a given row to invoke the correct filter to use for parsing the data in that row.</span></span> <span data-ttu-id="dc559-196">在此篩選已經剖析資料列的二進位資料之後，指定的斷詞工具將會剖析內容 (在此範例中，將會使用英式英文的斷詞工具)。</span><span class="sxs-lookup"><span data-stu-id="dc559-196">After the filter has parsed the binary data of the row, the specified word breaker will parse the content (in this example, the word breaker for British English is used).</span></span> <span data-ttu-id="dc559-197">請注意，當全文檢索索引已啟用自動變更追蹤時，篩選程序只會在建立索引時進行，或在使用者於基底資料表中插入或更新資料行時進行。</span><span class="sxs-lookup"><span data-stu-id="dc559-197">Note that the filtering process happens only at indexing time or if a user inserts or updates a column in the base table while automatic change tracking is enabled for the full-text index.</span></span> <span data-ttu-id="dc559-198">如需詳細資訊，請參閱 [設定及管理搜尋的篩選](configure-and-manage-filters-for-search.md)。</span><span class="sxs-lookup"><span data-stu-id="dc559-198">For more information, see [Configure and Manage Filters for Search](configure-and-manage-filters-for-search.md).</span></span>  
  
  
##  <a name="common-tasks"></a><a name="tasks"></a><span data-ttu-id="dc559-199">一般工作</span><span class="sxs-lookup"><span data-stu-id="dc559-199">Common Tasks</span></span>  
  
### <a name="to-create-a-full-text-catalog"></a><span data-ttu-id="dc559-200">建立全文檢索目錄</span><span class="sxs-lookup"><span data-stu-id="dc559-200">To Create a Full-Text Catalog</span></span>  
  
-   [<span data-ttu-id="dc559-201">CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dc559-201">CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-catalog-transact-sql)  
  
-   [<span data-ttu-id="dc559-202">建立及管理全文檢索目錄</span><span class="sxs-lookup"><span data-stu-id="dc559-202">Create and Manage Full-Text Catalogs</span></span>](create-and-manage-full-text-catalogs.md)  
  
### <a name="to-view-the-indexes-of-a-table-or-view"></a><span data-ttu-id="dc559-203">檢視資料表 (或檢視表) 的索引</span><span class="sxs-lookup"><span data-stu-id="dc559-203">To View the Indexes of a Table (or View)</span></span>  
  
-   [<span data-ttu-id="dc559-204">sys.indexes &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dc559-204">sys.indexes &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql)  
  
### <a name="to-create-a-unique-index"></a><span data-ttu-id="dc559-205">建立唯一的索引</span><span class="sxs-lookup"><span data-stu-id="dc559-205">To Create a Unique Index</span></span>  
  
-   [<span data-ttu-id="dc559-206">CREATE INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dc559-206">CREATE INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-index-transact-sql)  
  
-   [<span data-ttu-id="dc559-207">開啟資料表設計工具 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="dc559-207">Open Table Designer &#40;Visual Database Tools&#41;</span></span>](../../ssms/visual-db-tools/visual-database-tools.md)  
  
### <a name="to-create-a-full-text-index"></a><span data-ttu-id="dc559-208">建立全文檢索索引</span><span class="sxs-lookup"><span data-stu-id="dc559-208">To Create a Full-Text Index</span></span>  
  
-   [<span data-ttu-id="dc559-209">CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dc559-209">CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-index-transact-sql)  
  
-   [<span data-ttu-id="dc559-210">建立及管理全文檢索索引</span><span class="sxs-lookup"><span data-stu-id="dc559-210">Create and Manage Full-Text Indexes</span></span>](create-and-manage-full-text-indexes.md)  
  
### <a name="to-view-information-about-a-full-text-index"></a><span data-ttu-id="dc559-211">檢視全文檢索索引的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="dc559-211">To View Information about a Full-Text Index</span></span>  
  
|<span data-ttu-id="dc559-212">目錄或動態管理檢視</span><span class="sxs-lookup"><span data-stu-id="dc559-212">Catalog or Dynamic Management View</span></span>|<span data-ttu-id="dc559-213">描述</span><span class="sxs-lookup"><span data-stu-id="dc559-213">Description</span></span>|  
|----------------------------------------|-----------------|  
|[<span data-ttu-id="dc559-214">sys.fulltext_index_catalog_usages &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dc559-214">sys.fulltext_index_catalog_usages &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-index-catalog-usages-transact-sql)|<span data-ttu-id="dc559-215">針對通往全文檢索索引參考的每個全文檢索目錄，各傳回一個資料列。</span><span class="sxs-lookup"><span data-stu-id="dc559-215">Returns a row for each full-text catalog to full-text index reference.</span></span>|  
|[<span data-ttu-id="dc559-216">sys.fulltext_index_columns &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dc559-216">sys.fulltext_index_columns &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)|<span data-ttu-id="dc559-217">屬於全文檢索索引一部分的每個資料行各有一個資料列。</span><span class="sxs-lookup"><span data-stu-id="dc559-217">Contains a row for each column that is part of a full-text index.</span></span>|  
|[<span data-ttu-id="dc559-218">sys.fulltext_index_fragments &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dc559-218">sys.fulltext_index_fragments &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-index-fragments-transact-sql)|<span data-ttu-id="dc559-219">全文檢索索引會使用稱為「全文檢索索引片段」的內部資料表來儲存反向索引資料。</span><span class="sxs-lookup"><span data-stu-id="dc559-219">A fulltext index uses internal tables called full-text index fragments to store the inverted index data.</span></span> <span data-ttu-id="dc559-220">此檢視表可用來查詢有關這些片段的中繼資料，</span><span class="sxs-lookup"><span data-stu-id="dc559-220">This view can be used to query the metadata about these fragments.</span></span> <span data-ttu-id="dc559-221">此檢視表針對每一個資料表內包含全文檢索索引的每一個全文檢索索引片段各包含一個資料列。</span><span class="sxs-lookup"><span data-stu-id="dc559-221">This view contains a row for each full-text index fragment in every table that contains a full-text index.</span></span>|  
|[<span data-ttu-id="dc559-222">sys.fulltext_indexes &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dc559-222">sys.fulltext_indexes &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql)|<span data-ttu-id="dc559-223">針對表格式物件的每個全文檢索索引，各包含一個資料列。</span><span class="sxs-lookup"><span data-stu-id="dc559-223">Contains a row per full-text index of a tabular object.</span></span>|  
|[<span data-ttu-id="dc559-224">sys.dm_fts_index_keywords &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dc559-224">sys.dm_fts_index_keywords &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-transact-sql)|<span data-ttu-id="dc559-225">針對指定的資料表傳回全文檢索索引之內容的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="dc559-225">Returns information about the content of a full-text index for the specified table.</span></span>|  
|[<span data-ttu-id="dc559-226">sys.dm_fts_index_keywords_by_document &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dc559-226">sys.dm_fts_index_keywords_by_document &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql)|<span data-ttu-id="dc559-227">針對指定的資料表傳回全文檢索索引之文件層級內容的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="dc559-227">Returns information about the document-level content of a full-text index for the specified table.</span></span> <span data-ttu-id="dc559-228">給定的關鍵字可能會出現在許多份文件中。</span><span class="sxs-lookup"><span data-stu-id="dc559-228">A given keyword can appear in several documents.</span></span>|  
|[<span data-ttu-id="dc559-229">sys.dm_fts_index_population &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dc559-229">sys.dm_fts_index_population &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql)|<span data-ttu-id="dc559-230">傳回有關目前進行中之全文檢索索引母體擴展的資訊。</span><span class="sxs-lookup"><span data-stu-id="dc559-230">Returns information about the full-text index populations currently in progress.</span></span>|  
  
  
## <a name="see-also"></a><span data-ttu-id="dc559-231">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc559-231">See Also</span></span>  
 <span data-ttu-id="dc559-232">[CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-catalog-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dc559-232">[CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-catalog-transact-sql) </span></span>  
 <span data-ttu-id="dc559-233">[CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dc559-233">[CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql) </span></span>  
 <span data-ttu-id="dc559-234">[建立全文檢索停用字詞表 &#40;Transact-sql&#41;](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dc559-234">[CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql) </span></span>  
 <span data-ttu-id="dc559-235">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dc559-235">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span></span>  
 <span data-ttu-id="dc559-236">[擴展全文檢索索引](populate-full-text-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="dc559-236">[Populate Full-Text Indexes](populate-full-text-indexes.md) </span></span>  
 <span data-ttu-id="dc559-237">[FULLTEXTCATALOGPROPERTY &#40;Transact-sql&#41;](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dc559-237">[FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql) </span></span>  
 [<span data-ttu-id="dc559-238">OBJECTPROPERTYEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dc559-238">OBJECTPROPERTYEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/objectproperty-transact-sql)  
  
  
