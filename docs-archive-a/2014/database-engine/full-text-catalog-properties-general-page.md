---
title: 全文檢索目錄屬性 (一般頁面) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftcatalogproperties.general.f1
ms.assetid: d1f66762-2d40-4f24-b635-a417d22ee79a
author: rothja
ms.author: jroth
ms.openlocfilehash: 483601c53db6c8a806ea8c53f771fd4f2608293b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707777"
---
# <a name="full-text-catalog-properties-general-page"></a><span data-ttu-id="3eca5-102">全文檢索目錄屬性 (一般頁面)</span><span class="sxs-lookup"><span data-stu-id="3eca5-102">Full-Text Catalog Properties (General Page)</span></span>
  <span data-ttu-id="3eca5-103">本章節會顯示在 **[全文檢索目錄屬性]** 對話方塊的 **[一般]** 頁面上，可以使用的選項和功能。</span><span class="sxs-lookup"><span data-stu-id="3eca5-103">This section shows the options and functions available on the **General** page of the **Full-Text Catalog Properties** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3eca5-104">對於 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 資料庫而言，全文檢索目錄是參考一組全文檢索索引的邏輯概念。</span><span class="sxs-lookup"><span data-stu-id="3eca5-104">For [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] databases, a full-text catalog is a logical concept that refers to a group of full-text indexes.</span></span> <span data-ttu-id="3eca5-105">全文檢索目錄是不屬於任何檔案群組的虛擬物件。</span><span class="sxs-lookup"><span data-stu-id="3eca5-105">The full-text catalog is a virtual object that does not belong to any filegroup.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3eca5-106">選項</span><span class="sxs-lookup"><span data-stu-id="3eca5-106">Options</span></span>  
  
### <a name="properties"></a><span data-ttu-id="3eca5-107">屬性</span><span class="sxs-lookup"><span data-stu-id="3eca5-107">Properties</span></span>  
 <span data-ttu-id="3eca5-108">**預設目錄**</span><span class="sxs-lookup"><span data-stu-id="3eca5-108">**Default Catalog**</span></span>  
 <span data-ttu-id="3eca5-109">顯示目錄是否為資料庫的預設目錄。</span><span class="sxs-lookup"><span data-stu-id="3eca5-109">Displays whether the catalog is the default catalog for the database.</span></span>  
  
 <span data-ttu-id="3eca5-110">**母體擴展狀態**</span><span class="sxs-lookup"><span data-stu-id="3eca5-110">**Population Status**</span></span>  
 <span data-ttu-id="3eca5-111">指出目錄的狀態。</span><span class="sxs-lookup"><span data-stu-id="3eca5-111">Indicates the status of the catalog.</span></span> <span data-ttu-id="3eca5-112">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="3eca5-112">Possible values are:</span></span>  
  
-   <span data-ttu-id="3eca5-113">**閒置**</span><span class="sxs-lookup"><span data-stu-id="3eca5-113">**Idle**</span></span>  
  
-   <span data-ttu-id="3eca5-114">**搜耙進行中**</span><span class="sxs-lookup"><span data-stu-id="3eca5-114">**Crawl in Progress**</span></span>  
  
-   <span data-ttu-id="3eca5-115">**已暫停**</span><span class="sxs-lookup"><span data-stu-id="3eca5-115">**Paused**</span></span>  
  
-   <span data-ttu-id="3eca5-116">**調整執行速度**</span><span class="sxs-lookup"><span data-stu-id="3eca5-116">**Throttled**</span></span>  
  
-   <span data-ttu-id="3eca5-117">**待**</span><span class="sxs-lookup"><span data-stu-id="3eca5-117">**Recovering**</span></span>  
  
-   <span data-ttu-id="3eca5-118">**關機**</span><span class="sxs-lookup"><span data-stu-id="3eca5-118">**Shutdown**</span></span>  
  
-   <span data-ttu-id="3eca5-119">**遞增擴展進行中**</span><span class="sxs-lookup"><span data-stu-id="3eca5-119">**Incremental population in progress**</span></span>  
  
-   <span data-ttu-id="3eca5-120">**正在建立索引**</span><span class="sxs-lookup"><span data-stu-id="3eca5-120">**Building index**</span></span>  
  
-   <span data-ttu-id="3eca5-121">**磁片已滿已暫停**</span><span class="sxs-lookup"><span data-stu-id="3eca5-121">**Disk is full-Paused**</span></span>  
  
-   <span data-ttu-id="3eca5-122">**Change tracking**</span><span class="sxs-lookup"><span data-stu-id="3eca5-122">**Change tracking**</span></span>  
  
 <span data-ttu-id="3eca5-123">**項目計數**</span><span class="sxs-lookup"><span data-stu-id="3eca5-123">**Item Count**</span></span>  
 <span data-ttu-id="3eca5-124">顯示目錄中全文檢索項目的數目。</span><span class="sxs-lookup"><span data-stu-id="3eca5-124">Displays the number of full-text items in the catalog.</span></span>  
  
 <span data-ttu-id="3eca5-125">**目錄大小**</span><span class="sxs-lookup"><span data-stu-id="3eca5-125">**Catalog Size**</span></span>  
 <span data-ttu-id="3eca5-126">顯示全文檢索目錄的大小，以 MB 為單位。</span><span class="sxs-lookup"><span data-stu-id="3eca5-126">Displays the size, in megabytes, of the full-text catalog.</span></span>  
  
 <span data-ttu-id="3eca5-127">**名稱**</span><span class="sxs-lookup"><span data-stu-id="3eca5-127">**Name**</span></span>  
 <span data-ttu-id="3eca5-128">全文檢索目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="3eca5-128">The name of the full-text catalog.</span></span>  
  
 <span data-ttu-id="3eca5-129">**區分重音**</span><span class="sxs-lookup"><span data-stu-id="3eca5-129">**Accent Sensitive**</span></span>  
 <span data-ttu-id="3eca5-130">查看或修改類別目錄是否區分變音符號，例如波狀 **~** 符號 () 、銳角 (**́**) ，或母音 (**？**) 。</span><span class="sxs-lookup"><span data-stu-id="3eca5-130">View or modify whether the catalog is sensitive to diacritical marks, such as a tilde (**~**), acute accent mark (**´**), or umlaut (**¨**).</span></span> <span data-ttu-id="3eca5-131">有效值為：</span><span class="sxs-lookup"><span data-stu-id="3eca5-131">Valid values are:</span></span>  
  
-   <span data-ttu-id="3eca5-132">**否**</span><span class="sxs-lookup"><span data-stu-id="3eca5-132">**No**</span></span>  
  
-   <span data-ttu-id="3eca5-133">**是**</span><span class="sxs-lookup"><span data-stu-id="3eca5-133">**Yes**</span></span>  
  
-   <span data-ttu-id="3eca5-134">如需有關變音符號的詳細資訊，請參閱 Merriam-Webster 字典中的[變音符號](https://www.merriam-webster.com/dictionary/diacritic)。</span><span class="sxs-lookup"><span data-stu-id="3eca5-134">For information about diacritical marks, see [Diacritic](https://www.merriam-webster.com/dictionary/diacritic) in the Merriam-Webster dictionary.</span></span>  
  
 <span data-ttu-id="3eca5-135">**上次母體擴展日期**</span><span class="sxs-lookup"><span data-stu-id="3eca5-135">**Last Population Date**</span></span>  
 <span data-ttu-id="3eca5-136">顯示目錄上次擴展的日期。</span><span class="sxs-lookup"><span data-stu-id="3eca5-136">Displays the date the catalog was last populated.</span></span>  
  
 <span data-ttu-id="3eca5-137">**擁有者**</span><span class="sxs-lookup"><span data-stu-id="3eca5-137">**Owner**</span></span>  
 <span data-ttu-id="3eca5-138">全文檢索目錄的擁有者。</span><span class="sxs-lookup"><span data-stu-id="3eca5-138">The owner of the full-text catalog.</span></span>  
  
 <span data-ttu-id="3eca5-139">**唯一索引鍵計數**</span><span class="sxs-lookup"><span data-stu-id="3eca5-139">**Unique Key Count**</span></span>  
 <span data-ttu-id="3eca5-140">構成目錄的全文檢索索引之唯一字的數目。</span><span class="sxs-lookup"><span data-stu-id="3eca5-140">The number of unique words that make up the full-text index for the catalog.</span></span>  
  
### <a name="catalog-action"></a><span data-ttu-id="3eca5-141">目錄動作</span><span class="sxs-lookup"><span data-stu-id="3eca5-141">Catalog Action</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3eca5-142">**None**</span><span class="sxs-lookup"><span data-stu-id="3eca5-142">**None**</span></span>|<span data-ttu-id="3eca5-143">不會執行 **最佳化目錄**、 **重建目錄**，或 **重新擴展目錄** 等作業。</span><span class="sxs-lookup"><span data-stu-id="3eca5-143">Does not perform **Optimize catalog**, **Rebuild catalog**, or **Repopulate catalog** operations.</span></span>|  
|<span data-ttu-id="3eca5-144">**最佳化目錄**</span><span class="sxs-lookup"><span data-stu-id="3eca5-144">**Optimize catalog**</span></span>|<span data-ttu-id="3eca5-145">最佳化目錄的空間利用，並改善查詢的效能。</span><span class="sxs-lookup"><span data-stu-id="3eca5-145">Optimizes the space utilization of the catalog and improves query performance.</span></span> <span data-ttu-id="3eca5-146">它還會改善搜尋結果之次序相關性的精確性。</span><span class="sxs-lookup"><span data-stu-id="3eca5-146">It also improves the accuracy of relevance ranking of search results.</span></span><br /><br /> <span data-ttu-id="3eca5-147">此動作會執行 ALTER FULLTEXT CATALOG *catalog_name* REORGANIZE。</span><span class="sxs-lookup"><span data-stu-id="3eca5-147">This action executes ALTER FULLTEXT CATALOG *catalog_name* REORGANIZE.</span></span>|  
|<span data-ttu-id="3eca5-148">**重建目錄**</span><span class="sxs-lookup"><span data-stu-id="3eca5-148">**Rebuild catalog**</span></span>|<span data-ttu-id="3eca5-149">刪除並重建全文檢索目錄。</span><span class="sxs-lookup"><span data-stu-id="3eca5-149">Deletes and rebuilds the full-text catalog.</span></span> <span data-ttu-id="3eca5-150">如果已變更基礎的目錄屬性 (例如區分腔調字)，就必須執行此項作業。</span><span class="sxs-lookup"><span data-stu-id="3eca5-150">This operation must be performed if a fundamental catalog property is changed, such as accent sensitivity.</span></span><br /><br /> <span data-ttu-id="3eca5-151">為了使重建能順利完成，全文檢索目錄所存在的檔案群組必須在線上，或者可供讀寫。</span><span class="sxs-lookup"><span data-stu-id="3eca5-151">For the rebuild to succeed, the filegroup the full-text catalog resides in must be online or read-writeable.</span></span> <span data-ttu-id="3eca5-152">重建之後，就會重新擴展全文檢索的索引。</span><span class="sxs-lookup"><span data-stu-id="3eca5-152">After the rebuild, the full-text index will be repopulated.</span></span><br /><br /> <span data-ttu-id="3eca5-153">此動作會執行 ALTER FULLTEXT CATALOG *catalog_name* REBUILD。</span><span class="sxs-lookup"><span data-stu-id="3eca5-153">This action executes ALTER FULLTEXT CATALOG *catalog_name* REBUILD.</span></span>|  
|<span data-ttu-id="3eca5-154">**重新擴展目錄**</span><span class="sxs-lookup"><span data-stu-id="3eca5-154">**Repopulate catalog**</span></span>|<span data-ttu-id="3eca5-155">用資料最近的變更來更新目錄。</span><span class="sxs-lookup"><span data-stu-id="3eca5-155">Updates the catalog with recent changes to the data.</span></span> <span data-ttu-id="3eca5-156">此選項不需要關閉目錄。</span><span class="sxs-lookup"><span data-stu-id="3eca5-156">This option does require catalog downtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3eca5-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3eca5-157">See Also</span></span>  
 [<span data-ttu-id="3eca5-158">擴展全文檢索索引</span><span class="sxs-lookup"><span data-stu-id="3eca5-158">Populate Full-Text Indexes</span></span>](../relational-databases/indexes/indexes.md)  
  
  
