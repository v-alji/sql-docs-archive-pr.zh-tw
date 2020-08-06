---
title: 全文檢索目錄屬性 (資料表和 Views 頁面) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftcatalogproperties.tablesviews.f1
ms.assetid: 2d45fcd2-0f0f-4167-9027-316d6696c106
author: rothja
ms.author: jroth
ms.openlocfilehash: eb4d968af6c550d19fbb8934b5d76a1bd63cb8da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707770"
---
# <a name="full-text-catalog-properties-tables-and-views-page"></a><span data-ttu-id="1cefd-102">全文檢索目錄屬性 (資料表和檢視頁面)</span><span class="sxs-lookup"><span data-stu-id="1cefd-102">Full-Text Catalog Properties (Tables and Views Page)</span></span>
  <span data-ttu-id="1cefd-103">使用此對話方塊以檢視或修改指派給全文檢索目錄的資料表和檢視。</span><span class="sxs-lookup"><span data-stu-id="1cefd-103">Use this dialog page to view or modify the tables and views that are assigned to the full-text catalog.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="1cefd-104">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="1cefd-104">UI element list</span></span>  
 <span data-ttu-id="1cefd-105">**此資料庫中所有適合的資料表/檢視物件**</span><span class="sxs-lookup"><span data-stu-id="1cefd-105">**All eligible table/view objects in this database**</span></span>  
 <span data-ttu-id="1cefd-106">列出已定義唯一索引的資料表和檢視，但還不屬於全文目錄的一部份。</span><span class="sxs-lookup"><span data-stu-id="1cefd-106">Lists the tables and views that have a unique index defined on them, but are not already a part of the full-text catalog.</span></span> <span data-ttu-id="1cefd-107">若要選取資料表或視圖並將它指派給目錄，請選取清單方塊中的專案，然後按 [->] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1cefd-107">To select a table or view and assign it to the catalog, select the items in the list box and press the "->" button.</span></span>  
  
 <span data-ttu-id="1cefd-108">**指派給目錄的資料表/檢視物件**</span><span class="sxs-lookup"><span data-stu-id="1cefd-108">**Table/view objects assigned to the catalog**</span></span>  
 <span data-ttu-id="1cefd-109">列出目前已指派給全文檢索目錄的資料表和檢視</span><span class="sxs-lookup"><span data-stu-id="1cefd-109">Lists the tables and views that are currently assigned to the full-text catalog</span></span>  
  
## <a name="selected-object-properties"></a><span data-ttu-id="1cefd-110">選取的物件屬性</span><span class="sxs-lookup"><span data-stu-id="1cefd-110">Selected Object Properties</span></span>  
 <span data-ttu-id="1cefd-111">**選取的物件屬性**</span><span class="sxs-lookup"><span data-stu-id="1cefd-111">**Selected object properties**</span></span>  
 <span data-ttu-id="1cefd-112">在已指派給目錄的物件清單方塊中，顯示選取之物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="1cefd-112">Displays the properties of the selected object in the list box of objects assigned to the catalog.</span></span>  
  
 <span data-ttu-id="1cefd-113">**唯一索引**</span><span class="sxs-lookup"><span data-stu-id="1cefd-113">**Unique Index**</span></span>  
 <span data-ttu-id="1cefd-114">列出資料表或檢視可用的唯一索引。</span><span class="sxs-lookup"><span data-stu-id="1cefd-114">Lists the available unique indexes of the table or view.</span></span>  
  
 <span data-ttu-id="1cefd-115">**資料表已啟用全文檢索**</span><span class="sxs-lookup"><span data-stu-id="1cefd-115">**Table is full-text enabled**</span></span>  
 <span data-ttu-id="1cefd-116">選取此核取方塊，以啟用資料表的全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="1cefd-116">Select this check box to enable the full-text index on the table.</span></span> <span data-ttu-id="1cefd-117">清除核取方塊以停用全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="1cefd-117">Clear the check box to disable the full-text index.</span></span>  
  
## <a name="eligible-columns-grid"></a><span data-ttu-id="1cefd-118">適合的資料行方格</span><span class="sxs-lookup"><span data-stu-id="1cefd-118">Eligible Columns Grid</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1cefd-119">**可用的資料行**</span><span class="sxs-lookup"><span data-stu-id="1cefd-119">**Available Columns**</span></span>|<span data-ttu-id="1cefd-120">顯示已全文檢索索引的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="1cefd-120">Displays all the columns that are full-text indexed.</span></span> <span data-ttu-id="1cefd-121">選取核取方塊以將資料行加入全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="1cefd-121">Select a check box to add a column to the full-text index.</span></span>|  
|<span data-ttu-id="1cefd-122">**斷詞工具的語言**</span><span class="sxs-lookup"><span data-stu-id="1cefd-122">**Language for Word Breaker**</span></span>|<span data-ttu-id="1cefd-123">顯示斷詞工具的語言。</span><span class="sxs-lookup"><span data-stu-id="1cefd-123">Displays the language of the word breaker.</span></span>|  
|<span data-ttu-id="1cefd-124">**資料類型資料行**</span><span class="sxs-lookup"><span data-stu-id="1cefd-124">**Data Type Column**</span></span>|<span data-ttu-id="1cefd-125">如果資料行是或資料行，則會列出資料表中保留 [**可用**的資料行] 中所列之資料行檔案類型的資料行名稱 `varbinary(max)` `image` 。</span><span class="sxs-lookup"><span data-stu-id="1cefd-125">Lists the name of the column in the table that holds the document type of the column listed in **Available Columns** if the column is a `varbinary(max)` or `image` column.</span></span>|  
|<span data-ttu-id="1cefd-126">**統計語意**</span><span class="sxs-lookup"><span data-stu-id="1cefd-126">**Statistical Semantics**</span></span>|<span data-ttu-id="1cefd-127">選取是否要針對選取的資料行啟用語意索引。</span><span class="sxs-lookup"><span data-stu-id="1cefd-127">Select whether to enable semantic indexing for the selected column.</span></span> <span data-ttu-id="1cefd-128">如需詳細資訊，請參閱[語意搜尋 &#40;SQL Server&#41;](../relational-databases/search/semantic-search-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1cefd-128">For more information, see [Semantic Search &#40;SQL Server&#41;](../relational-databases/search/semantic-search-sql-server.md).</span></span><br /><br /> <span data-ttu-id="1cefd-129">如果您在選取 **[統計語意]** 之前選取 **[語言]**，而且選取的語言沒有相關聯的語意語言模型，則會停用 **[統計語意]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="1cefd-129">If you select a **Language** prior to selecting **Statistical Semantics**, and the selected language does not have an associated Semantic Language Model, then the **Statistical Semantics** checkbox is disabled.</span></span> <span data-ttu-id="1cefd-130">如果您在選取 [語言]\*\*\*\* 之前選取 [統計語意]\*\*\*\*，則下拉式方塊中提供的語言將受限為有語意語言模型支援的語言。</span><span class="sxs-lookup"><span data-stu-id="1cefd-130">If you select **Statistical Semantics** prior to selecting a **Language**, the languages available in the drop-down combo box will be restricted to those for which there is Semantic Language Model support.</span></span>|  
  
## <a name="track-changes"></a><span data-ttu-id="1cefd-131">追蹤變更</span><span class="sxs-lookup"><span data-stu-id="1cefd-131">Track Changes</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1cefd-132">**自動**</span><span class="sxs-lookup"><span data-stu-id="1cefd-132">**Automatic**</span></span>|<span data-ttu-id="1cefd-133">當修改、加入或刪除基礎資料表中的資料時，全文檢索索引會自動更新。</span><span class="sxs-lookup"><span data-stu-id="1cefd-133">The full-text index is automatically updated when the data in the underlying table is modified, added, or deleted.</span></span>|  
|<span data-ttu-id="1cefd-134">**手動**</span><span class="sxs-lookup"><span data-stu-id="1cefd-134">**Manual**</span></span>|<span data-ttu-id="1cefd-135">在索引資料中修改、加入或刪除資料時， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 會追蹤變更。</span><span class="sxs-lookup"><span data-stu-id="1cefd-135">When data is modified, added, or deleted in the indexed data, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tracks the changes.</span></span> <span data-ttu-id="1cefd-136">**[手動]** 變更追蹤生效時，索引不會自動更新這些變更。</span><span class="sxs-lookup"><span data-stu-id="1cefd-136">When **Manual** change tracking is in effect, the index is not automatically updated with these changes.</span></span> <span data-ttu-id="1cefd-137">而是管理員可以使用 [ALTER FULLTEXT INDEX ...START UPDATE POPULATION](/sql/t-sql/statements/alter-fulltext-index-transact-sql) 陳述式來手動套用變更。</span><span class="sxs-lookup"><span data-stu-id="1cefd-137">Instead, an administrator can apply the changes manually by using an [ALTER FULLTEXT INDEX ... START UPDATE POPULATION](/sql/t-sql/statements/alter-fulltext-index-transact-sql) statement.</span></span>|  
|<span data-ttu-id="1cefd-138">**不要追蹤變更**</span><span class="sxs-lookup"><span data-stu-id="1cefd-138">**Do not track change**</span></span>|<span data-ttu-id="1cefd-139">此選項生效時，不會記錄目錄中索引資料的變更。</span><span class="sxs-lookup"><span data-stu-id="1cefd-139">With this option in effect, changes to the indexed data in the catalog are not recorded.</span></span> <span data-ttu-id="1cefd-140">管理員必須使用 ALTER FULLTEXT INDEX 搭配 FULL POPULATION 或 INCREMENTAL POPULATION 來建立索引。</span><span class="sxs-lookup"><span data-stu-id="1cefd-140">An administrator must build the index by using ALTER FULLTEXT INDEX with either FULL POPULATION or INCREMENTAL POPULATION.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1cefd-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1cefd-141">See Also</span></span>  
 <span data-ttu-id="1cefd-142">[CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-catalog-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1cefd-142">[CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-catalog-transact-sql) </span></span>  
 <span data-ttu-id="1cefd-143">[ALTER FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-catalog-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1cefd-143">[ALTER FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-catalog-transact-sql) </span></span>  
 [<span data-ttu-id="1cefd-144">擴展全文檢索索引</span><span class="sxs-lookup"><span data-stu-id="1cefd-144">Populate Full-Text Indexes</span></span>](../relational-databases/indexes/indexes.md)  
  
  
