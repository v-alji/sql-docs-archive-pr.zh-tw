---
title: 全文檢索索引對話方塊 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.fulltextindex
ms.assetid: ef45b585-2567-4abe-b421-9fd0994e0146
author: stevestein
ms.author: sstein
ms.openlocfilehash: f98d3bf43707caedd8c9d0a01349f36d5a5bfbcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708865"
---
# <a name="full-text-index-dialog-box-visual-database-tools"></a><span data-ttu-id="7ec83-102">全文檢索索引對話方塊 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="7ec83-102">Full-Text Index Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="7ec83-103">這個對話方塊可讓您建立全文檢索索引，以便在資料庫資料表的文字資料行上進行全文檢索搜尋。</span><span class="sxs-lookup"><span data-stu-id="7ec83-103">This dialog box allows you to create a full-text index, for full-text searches on text-based columns in your database tables.</span></span> <span data-ttu-id="7ec83-104">全文檢索索引必須藉助一般索引，因此您必須先建立一般索引。</span><span class="sxs-lookup"><span data-stu-id="7ec83-104">A full-text index relies on a regular index, so you must create that first.</span></span> <span data-ttu-id="7ec83-105">您必須在單一、非 Null 的資料行上建立一般索引，而且最好選擇值較小的資料行，而不要選擇包含大數值的資料行。</span><span class="sxs-lookup"><span data-stu-id="7ec83-105">The regular index must be created on a single, non-null column; it is best to choose a column with small values rather than a column with large ones.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7ec83-106">若要建立全文檢索索引，您必須先對使用外部工具的資料庫建立全文檢索，例如 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 Enterprise Manager。</span><span class="sxs-lookup"><span data-stu-id="7ec83-106">To create a full-text index, you must first create a full-text catalog for the database using an outside tool, such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or Enterprise Manager.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7ec83-107">並非每個 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本都可使用全文檢索索引功能。</span><span class="sxs-lookup"><span data-stu-id="7ec83-107">Full-text index functionality is not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7ec83-108">如需版本支援的功能清單 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[SQL Server 2014 版本支援的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="7ec83-108">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="7ec83-109">選項。</span><span class="sxs-lookup"><span data-stu-id="7ec83-109">Options</span></span>  
 <span data-ttu-id="7ec83-110">**選取的全文檢索索引**</span><span class="sxs-lookup"><span data-stu-id="7ec83-110">**Selected Full-Text Index**</span></span>  
 <span data-ttu-id="7ec83-111">列出現有的全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="7ec83-111">Lists existing full-text indexes.</span></span> <span data-ttu-id="7ec83-112">選取索引，在方格右側顯示其屬性。</span><span class="sxs-lookup"><span data-stu-id="7ec83-112">Select an index to show its properties in the grid to the right.</span></span> <span data-ttu-id="7ec83-113">如果清單是空的，表示資料表尚未定義全文檢索關聯性。</span><span class="sxs-lookup"><span data-stu-id="7ec83-113">If the list is empty, no full-text relationships have been defined for the table.</span></span>  
  
 <span data-ttu-id="7ec83-114">**加入**</span><span class="sxs-lookup"><span data-stu-id="7ec83-114">**Add**</span></span>  
 <span data-ttu-id="7ec83-115">建立新的全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="7ec83-115">Create a new full-text index.</span></span>  
  
 <span data-ttu-id="7ec83-116">**刪除**</span><span class="sxs-lookup"><span data-stu-id="7ec83-116">**Delete**</span></span>  
 <span data-ttu-id="7ec83-117">刪除在 [選取的全文檢索索引]  清單中所選取的全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="7ec83-117">Delete the full-text index selected in the **Selected Full-Text Index** list.</span></span>  
  
 <span data-ttu-id="7ec83-118">**一般類別目錄**</span><span class="sxs-lookup"><span data-stu-id="7ec83-118">**General Category**</span></span>  
 <span data-ttu-id="7ec83-119">展開時會顯示 [資料行]  和 [全文檢索資料庫目錄名稱]  。</span><span class="sxs-lookup"><span data-stu-id="7ec83-119">When expanded, shows **Columns** and **Full-text Catalog Name**.</span></span>  
  
 <span data-ttu-id="7ec83-120">**資料行**</span><span class="sxs-lookup"><span data-stu-id="7ec83-120">**Columns**</span></span>  
 <span data-ttu-id="7ec83-121">顯示可使用全文檢索搜尋資料行的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="7ec83-121">Displays a comma-separated list of the names of full-text-searchable columns.</span></span> <span data-ttu-id="7ec83-122">若要查看完整清單，請按一下屬性欄位左邊的省略符號按鈕 ( **...** )。</span><span class="sxs-lookup"><span data-stu-id="7ec83-122">To see the complete list, click the ellipsis button (**...**) to the left of the property field.</span></span>  
  
 <span data-ttu-id="7ec83-123">**全文檢索資料庫目錄名稱**</span><span class="sxs-lookup"><span data-stu-id="7ec83-123">**Full-Text Catalog Name**</span></span>  
 <span data-ttu-id="7ec83-124">顯示全文檢索索引儲存位置的全文檢索資料庫目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="7ec83-124">Displays the name of the full-text catalog on which this full-text index is stored.</span></span> <span data-ttu-id="7ec83-125">若要將索引儲存到不同的目錄，請按目錄名稱，然後從下拉式清單選擇另外一個目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="7ec83-125">To store the index on a different catalog, click the catalog name and choose another from the drop-down list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7ec83-126">目錄必須先在外部工具建立，例如 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 Enterprise Manager。</span><span class="sxs-lookup"><span data-stu-id="7ec83-126">The catalog must be created first in an outside tool, such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or Enterprise Manager.</span></span>  
  
 <span data-ttu-id="7ec83-127">**識別類別目錄**</span><span class="sxs-lookup"><span data-stu-id="7ec83-127">**Identity Category**</span></span>  
 <span data-ttu-id="7ec83-128">展開時會顯示這個索引的名稱欄位。</span><span class="sxs-lookup"><span data-stu-id="7ec83-128">When expanded, shows the name field for this index.</span></span>  
  
 <span data-ttu-id="7ec83-129">**名稱**</span><span class="sxs-lookup"><span data-stu-id="7ec83-129">**Name**</span></span>  
 <span data-ttu-id="7ec83-130">顯示這個全文檢索索引的系統指定名稱。</span><span class="sxs-lookup"><span data-stu-id="7ec83-130">Displays the system-specified name for this full-text index.</span></span>  
  
 <span data-ttu-id="7ec83-131">**資料表設計工具類別目錄**</span><span class="sxs-lookup"><span data-stu-id="7ec83-131">**Table Designer Category**</span></span>  
 <span data-ttu-id="7ec83-132">展開時會顯示指示索引如何執行的屬性。</span><span class="sxs-lookup"><span data-stu-id="7ec83-132">When expanded, shows properties that dictate how the index performs.</span></span>  
  
 <span data-ttu-id="7ec83-133">**使用中**</span><span class="sxs-lookup"><span data-stu-id="7ec83-133">**Active**</span></span>  
 <span data-ttu-id="7ec83-134">指示是否能夠使用這個全文檢索索引執行全文檢索搜尋。</span><span class="sxs-lookup"><span data-stu-id="7ec83-134">Indicates whether you can currently perform a full-text search using this full-text index.</span></span>  
  
 <span data-ttu-id="7ec83-135">**變更追蹤設定**</span><span class="sxs-lookup"><span data-stu-id="7ec83-135">**Change Tracking Setting**</span></span>  
 <span data-ttu-id="7ec83-136">描述這個索引的變更追蹤狀態：[手動]、[自動] 或 [關閉]。</span><span class="sxs-lookup"><span data-stu-id="7ec83-136">Describes the status of change tracking for this index: Manual, Auto, or Off.</span></span>  
  
 <span data-ttu-id="7ec83-137">**搜耙已完成**</span><span class="sxs-lookup"><span data-stu-id="7ec83-137">**Crawl Completed**</span></span>  
 <span data-ttu-id="7ec83-138">顯示最近的搜耙是否已經完成。</span><span class="sxs-lookup"><span data-stu-id="7ec83-138">Shows whether the most recent crawl has been completed.</span></span> <span data-ttu-id="7ec83-139">如果這個屬性的值為 [否]，表示搜耙目前正在進行。</span><span class="sxs-lookup"><span data-stu-id="7ec83-139">If this property value is No, a crawl is currently in progress.</span></span>  
  
 <span data-ttu-id="7ec83-140">**目前或上一個搜耙的結束日期及時間**</span><span class="sxs-lookup"><span data-stu-id="7ec83-140">**End Date And Time Of Current Or Last Crawl**</span></span>  
 <span data-ttu-id="7ec83-141">顯示最近搜耙結束的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="7ec83-141">Displays the date and time that the most recent crawl ended.</span></span>  
  
 <span data-ttu-id="7ec83-142">**目前或上一個搜耙中的錯誤**</span><span class="sxs-lookup"><span data-stu-id="7ec83-142">**Errors In Current Or Last Crawl**</span></span>  
 <span data-ttu-id="7ec83-143">顯示目前或最近之搜耙的錯誤數目。</span><span class="sxs-lookup"><span data-stu-id="7ec83-143">Displays the number of errors in current or most recent crawl.</span></span>  
  
 <span data-ttu-id="7ec83-144">**索引版本**</span><span class="sxs-lookup"><span data-stu-id="7ec83-144">**Index Version**</span></span>  
 <span data-ttu-id="7ec83-145">顯示搜耙開始時的資料表結構描述版本。</span><span class="sxs-lookup"><span data-stu-id="7ec83-145">Displays the schema version of table at time the crawl started.</span></span>  
  
 <span data-ttu-id="7ec83-146">**目前或上一個搜耙中的資料列**</span><span class="sxs-lookup"><span data-stu-id="7ec83-146">**Rows In Current Or Last Crawl**</span></span>  
 <span data-ttu-id="7ec83-147">顯示目前或最近搜耙中更新之資料列的數目。</span><span class="sxs-lookup"><span data-stu-id="7ec83-147">Displays the number of rows updated in the current or most recent crawl.</span></span>  
  
 <span data-ttu-id="7ec83-148">**目前或上一個搜耙的開始日期及時間**</span><span class="sxs-lookup"><span data-stu-id="7ec83-148">**Start Date And Time Of Current Or Last Crawl**</span></span>  
 <span data-ttu-id="7ec83-149">顯示目前或最近搜耙開始的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="7ec83-149">Displays the date and time that the current or most recent crawl started.</span></span>  
  
 <span data-ttu-id="7ec83-150">**下一個搜耙的時間戳記**</span><span class="sxs-lookup"><span data-stu-id="7ec83-150">**Time Stamp For Next Crawl**</span></span>  
 <span data-ttu-id="7ec83-151">顯示下一個搜耙將會開始的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="7ec83-151">Displays the date and time that the next crawl will start.</span></span>  
  
 <span data-ttu-id="7ec83-152">**目前或上一個搜耙的類型**</span><span class="sxs-lookup"><span data-stu-id="7ec83-152">**Type Of Current Or Last Crawl**</span></span>  
 <span data-ttu-id="7ec83-153">顯示目前或最近搜耙的類型：[完整]、[累加]、[更新] 或 [自動傳用]。</span><span class="sxs-lookup"><span data-stu-id="7ec83-153">Displays the type of the current or most recent crawl: Full, Incremental, Update, or Auto Propagation.</span></span>  
  
 <span data-ttu-id="7ec83-154">**唯一索引名稱**</span><span class="sxs-lookup"><span data-stu-id="7ec83-154">**Unique Index Name**</span></span>  
 <span data-ttu-id="7ec83-155">顯示這個資料庫中擁有唯一單一資料行索引的所有資料行名稱的清單。</span><span class="sxs-lookup"><span data-stu-id="7ec83-155">Displays a list of all of the names of columns in this database that have unique single-column indexes.</span></span> <span data-ttu-id="7ec83-156">這些資料行可用來建立全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="7ec83-156">These columns can be used to create a full-text index.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ec83-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ec83-157">See Also</span></span>  
 <span data-ttu-id="7ec83-158">[使用全文檢索索引 Wizard](../../relational-databases/search/use-the-full-text-indexing-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="7ec83-158">[Use the Full-Text Indexing Wizard](../../relational-databases/search/use-the-full-text-indexing-wizard.md) </span></span>  
 [<span data-ttu-id="7ec83-159">CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7ec83-159">CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-index-transact-sql)  
  
  
