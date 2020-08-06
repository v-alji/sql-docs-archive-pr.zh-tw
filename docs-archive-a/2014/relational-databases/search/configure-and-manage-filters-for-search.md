---
title: 設定及管理搜尋的篩選 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], filters
- filters [full-text search]
ms.assetid: 7ccf2ee0-9854-4253-8cca-1faed43b7095
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e9a57c95226a9b277cfb718b40b5d0525b1f8eb3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598792"
---
# <a name="configure-and-manage-filters-for-search"></a><span data-ttu-id="6eb83-102">設定及管理搜尋的篩選</span><span class="sxs-lookup"><span data-stu-id="6eb83-102">Configure and Manage Filters for Search</span></span>
  <span data-ttu-id="6eb83-103">在 `varbinary`、`varbinary(max)`、`image` 或 `xml` 資料類型資料行中索引文件需要進行額外處理。</span><span class="sxs-lookup"><span data-stu-id="6eb83-103">Indexing documents in an `varbinary`, `varbinary(max)`, `image`, or `xml` data type column requires extra processing.</span></span> <span data-ttu-id="6eb83-104">這項處理必須由篩選執行。</span><span class="sxs-lookup"><span data-stu-id="6eb83-104">This processing must be performed by a filter.</span></span> <span data-ttu-id="6eb83-105">篩選會從文件中擷取文字資訊 (移除格式)。</span><span class="sxs-lookup"><span data-stu-id="6eb83-105">The filter extracts the textual information from the document (removing the formatting).</span></span> <span data-ttu-id="6eb83-106">然後，篩選會將文字傳送至與資料表資料行相關聯之語言的斷詞工具元件。</span><span class="sxs-lookup"><span data-stu-id="6eb83-106">The filter then sends the text to the word-breaker component for the language associated with the table column.</span></span>  
  
 <span data-ttu-id="6eb83-107">給定的篩選是給定文件類型 (.doc、.pdf、.xls 和 .xml 等等) 特有的。</span><span class="sxs-lookup"><span data-stu-id="6eb83-107">A given filter is specific to a given document type (.doc, .pdf, .xls, .xml, and so forth).</span></span> <span data-ttu-id="6eb83-108">這些篩選會實作 IFilter 介面。</span><span class="sxs-lookup"><span data-stu-id="6eb83-108">These filters implement the IFilter interface.</span></span> <span data-ttu-id="6eb83-109">如需這些文件類型的詳細資訊，請查詢 [sys.fulltext_document_types](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql) 目錄檢視。</span><span class="sxs-lookup"><span data-stu-id="6eb83-109">For more information about these document types, query the [sys.fulltext_document_types](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql) catalog view.</span></span>  
  
 <span data-ttu-id="6eb83-110">二進位文件可以儲存在單一 `varbinary(max)` 或 `image` 資料行中。</span><span class="sxs-lookup"><span data-stu-id="6eb83-110">Binary documents can be stored in a single `varbinary(max)` or `image` column.</span></span> <span data-ttu-id="6eb83-111">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會根據文件的副檔名，為每個文件選擇正確的篩選。</span><span class="sxs-lookup"><span data-stu-id="6eb83-111">For each document, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] chooses the correct filter based on the file extension.</span></span> <span data-ttu-id="6eb83-112">由於檔案儲存在或資料行時，不會顯示副檔名 `varbinary(max)` ，因此 `image`) 的副檔名 ( .doc、.xls、.pdf 等等，必須儲存在資料表中的個別資料行中，稱為類型資料行。</span><span class="sxs-lookup"><span data-stu-id="6eb83-112">Because the file extension is not visible when the file is stored in a `varbinary(max)` or `image` column, the file extension (.doc, .xls,  .pdf, and so forth) must be stored in a separate column in the table, called a type column.</span></span> <span data-ttu-id="6eb83-113">此類型資料行可以是任何一種字元式資料類型，且包含文件副檔名，如 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Word 文件的 .doc。</span><span class="sxs-lookup"><span data-stu-id="6eb83-113">This type column can be of any character-based data type and contains the document file extension, such as .doc for a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Word document.</span></span> <span data-ttu-id="6eb83-114">在的**document**資料表中 [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] ， **document**資料行的類型為 `varbinary(max)` ，而類型資料行**FileExtension**的類型為 `nvarchar(8)` 。</span><span class="sxs-lookup"><span data-stu-id="6eb83-114">In the **Document** table in [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)], the **Document** column is of type `varbinary(max)`, and the type column, **FileExtension**, is of type `nvarchar(8)`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6eb83-115">根據篩選的實作方式，篩選可能會處理父物件中內嵌的物件。</span><span class="sxs-lookup"><span data-stu-id="6eb83-115">A filter might be able to handle objects embedded in the parent object, depending on its implementation.</span></span> <span data-ttu-id="6eb83-116">不過， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 不會將篩選設定成遵循其他物件的連結。</span><span class="sxs-lookup"><span data-stu-id="6eb83-116">However, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] does not configure filters to follow links to other objects.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="6eb83-117">會安裝其自有的 XML 和 HTML 篩選。</span><span class="sxs-lookup"><span data-stu-id="6eb83-117">installs its own XML and HTML filters.</span></span> <span data-ttu-id="6eb83-118">此外， [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 也會載入已經安裝在作業系統上的其他任何  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]專用格式 (.doc、.xdoc、.ppt 等等) 篩選。</span><span class="sxs-lookup"><span data-stu-id="6eb83-118">In addition, any filters for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] proprietary formats (.doc, .xdoc, .ppt and so on) that are already installed on the operating system are also loaded by  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6eb83-119">若要識別目前載入到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]執行個體上的篩選，請使用 [sp_help_fulltext_system_components](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) 預存程序，如下所示：</span><span class="sxs-lookup"><span data-stu-id="6eb83-119">To identify the filters that are currently loaded on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], use the [sp_help_fulltext_system_components](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) stored procedure, as follows:</span></span>  
  
```  
EXEC sp_help_fulltext_system_components 'filter';   
```  
  
 <span data-ttu-id="6eb83-120">不過，您必須先手動將非 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 格式的篩選載入伺服器執行個體中，然後才能使用它們。</span><span class="sxs-lookup"><span data-stu-id="6eb83-120">Before you can use filters for non [!INCLUDE[msCoName](../../../includes/msconame-md.md)] formats, however, you must manually load them into the server instance.</span></span> <span data-ttu-id="6eb83-121">如需安裝其他篩選的相關資訊，請參閱 [檢視或變更已註冊的篩選與斷詞工具](view-or-change-registered-filters-and-word-breakers.md)。</span><span class="sxs-lookup"><span data-stu-id="6eb83-121">For information about installing additional filters, see [View or Change Registered Filters and Word Breakers](view-or-change-registered-filters-and-word-breakers.md).</span></span>  
  
 <span data-ttu-id="6eb83-122">**若要檢視現有全文檢索索引中的類型資料行**</span><span class="sxs-lookup"><span data-stu-id="6eb83-122">**To view the type column in an existing full-text index**</span></span>  
  
-   [<span data-ttu-id="6eb83-123">sys.fulltext_index_columns &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6eb83-123">sys.fulltext_index_columns &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="6eb83-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6eb83-124">See Also</span></span>  
 <span data-ttu-id="6eb83-125">[fulltext_index_columns &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6eb83-125">[sys.fulltext_index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql) </span></span>  
 [<span data-ttu-id="6eb83-126">FILESTREAM 與其他 SQL Server 功能的相容性</span><span class="sxs-lookup"><span data-stu-id="6eb83-126">FILESTREAM Compatibility with Other SQL Server Features</span></span>](../blob/filestream-compatibility-with-other-sql-server-features.md)  
  
  
