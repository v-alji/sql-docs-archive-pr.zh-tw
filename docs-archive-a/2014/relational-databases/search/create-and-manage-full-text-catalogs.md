---
title: 建立及管理全文檢索目錄 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text catalogs [SQL Server], creating
- full-text search [SQL Server], using SQL Server Management Studio
ms.assetid: 824b7131-44a6-4815-89e6-62b7bab060e3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 18efd79bc34beee94d4edc61e9165a986edba90b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606719"
---
# <a name="create-and-manage-full-text-catalogs"></a><span data-ttu-id="4a354-102">建立及管理全文檢索目錄</span><span class="sxs-lookup"><span data-stu-id="4a354-102">Create and Manage Full-Text Catalogs</span></span>
  <span data-ttu-id="4a354-103">全文檢索目錄是不屬於任何檔案群組的虛擬物件。它是參考一組全文檢索索引的邏輯概念。</span><span class="sxs-lookup"><span data-stu-id="4a354-103">A full-text catalog is a virtual object that does not belong to any filegroup; it is a logical concept that refers to a group of full-text indexes.</span></span>  
  
##  <a name="creating-a-full-text-catalog"></a><a name="creating"></a><span data-ttu-id="4a354-104">建立全文檢索目錄</span><span class="sxs-lookup"><span data-stu-id="4a354-104">Creating a Full-Text Catalog</span></span>  
  
#### <a name="to-create-a-full-text-catalog"></a><span data-ttu-id="4a354-105">建立全文檢索目錄</span><span class="sxs-lookup"><span data-stu-id="4a354-105">To create a full-text catalog</span></span>  
  
1.  <span data-ttu-id="4a354-106">在物件總管中，展開伺服器，並展開 [資料庫]\*\*\*\*，然後展開您要在其中建立全文檢索目錄的資料庫。</span><span class="sxs-lookup"><span data-stu-id="4a354-106">In Object Explorer, expand the server, expand **Databases**, and expand the database in which you want to create the full-text catalog.</span></span>  
  
2.  <span data-ttu-id="4a354-107">展開 [儲存體]\*\*\*\*，然後以滑鼠右鍵按一下 [全文檢索目錄]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4a354-107">Expand **Storage**, and then right-click **Full Text Catalogs**.</span></span>  
  
3.  <span data-ttu-id="4a354-108">選取 [新增全文檢索目錄]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4a354-108">Select **New Full-Text Catalog**.</span></span>  
  
4.  <span data-ttu-id="4a354-109">在 [新增全文檢索目錄]\*\*\*\* 對話方塊中，為您要重新建立的目錄指定資訊。</span><span class="sxs-lookup"><span data-stu-id="4a354-109">In the **New Full-Text Catalog** dialog box, specify the information for the catalog that you are re-creating.</span></span> <span data-ttu-id="4a354-110">如需詳細資訊，請參閱[全文檢索搜尋](../../integration-services/general-page-of-integration-services-designers-options.md)。</span><span class="sxs-lookup"><span data-stu-id="4a354-110">For more information, see [New Full-Text Catalog &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4a354-111">全文檢索目錄識別碼從 00005 開始，每次新增一個目錄時識別碼便增加一號。</span><span class="sxs-lookup"><span data-stu-id="4a354-111">Full-text catalog IDs begin at 00005 and are incremented by one for each new catalog created.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
  
  
##  <a name="viewing-the-properties-of-a-full-text-catalog"></a><a name="props"></a><span data-ttu-id="4a354-112">查看全文檢索目錄的屬性</span><span class="sxs-lookup"><span data-stu-id="4a354-112">Viewing the Properties of a Full-Text Catalog</span></span>  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="4a354-113">函數 (例如 FULLTEXTCATALOGPROPERTY) 可以用來取得各種全文檢索索引相關屬性的值。</span><span class="sxs-lookup"><span data-stu-id="4a354-113">functions such as FULLTEXTCATALOGPROPERTY can be used to obtain the value of various properties related to full-text indexing.</span></span> <span data-ttu-id="4a354-114">此資訊適用於管理和疑難排解全文檢索搜尋。</span><span class="sxs-lookup"><span data-stu-id="4a354-114">This information is useful for administering and troubleshooting full-text search.</span></span>  
  
 <span data-ttu-id="4a354-115">下表列出與全文檢索目錄相關的屬性。</span><span class="sxs-lookup"><span data-stu-id="4a354-115">The following table lists the properties that are related to full-text catalogs.</span></span>  
  
|<span data-ttu-id="4a354-116">屬性</span><span class="sxs-lookup"><span data-stu-id="4a354-116">Property</span></span>|<span data-ttu-id="4a354-117">描述</span><span class="sxs-lookup"><span data-stu-id="4a354-117">Description</span></span>|<span data-ttu-id="4a354-118">函式</span><span class="sxs-lookup"><span data-stu-id="4a354-118">Function</span></span>|  
|--------------|-----------------|--------------|  
|`AccentSensitivity`|<span data-ttu-id="4a354-119">區分腔調字設定。</span><span class="sxs-lookup"><span data-stu-id="4a354-119">Accent-sensitivity setting.</span></span>|[<span data-ttu-id="4a354-120">FULLTEXTCATALOGPROPERTY</span><span class="sxs-lookup"><span data-stu-id="4a354-120">FULLTEXTCATALOGPROPERTY</span></span>](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql)|  
|`ImportStatus`|<span data-ttu-id="4a354-121">是否正在匯入全文檢索目錄。</span><span class="sxs-lookup"><span data-stu-id="4a354-121">Whether the full-text catalog is being imported.</span></span>|<span data-ttu-id="4a354-122">FULLTEXTCATALOGPROPERTY</span><span class="sxs-lookup"><span data-stu-id="4a354-122">FULLTEXTCATALOGPROPERTY</span></span>|  
|`IndexSize`|<span data-ttu-id="4a354-123">全文檢索目錄的大小 (以 MB 為單位)。</span><span class="sxs-lookup"><span data-stu-id="4a354-123">Size of the full-text catalog in megabytes (MB).</span></span>|<span data-ttu-id="4a354-124">FULLTEXTCATALOGPROPERTY</span><span class="sxs-lookup"><span data-stu-id="4a354-124">FULLTEXTCATALOGPROPERTY</span></span>|  
|`ItemCount`|<span data-ttu-id="4a354-125">目前在全文檢索目錄中的全文檢索索引項目數。</span><span class="sxs-lookup"><span data-stu-id="4a354-125">Number of full-text indexed items currently in the full-text catalog.</span></span>|<span data-ttu-id="4a354-126">FULLTEXTCATALOGPROPERTY</span><span class="sxs-lookup"><span data-stu-id="4a354-126">FULLTEXTCATALOGPROPERTY</span></span>|  
|`MergeStatus`|<span data-ttu-id="4a354-127">主要合併是否正在進行中。</span><span class="sxs-lookup"><span data-stu-id="4a354-127">Whether a master merge is in progress.</span></span>|<span data-ttu-id="4a354-128">FULLTEXTCATALOGPROPERTY</span><span class="sxs-lookup"><span data-stu-id="4a354-128">FULLTEXTCATALOGPROPERTY</span></span>|  
|`PopulateCompletionAge`|<span data-ttu-id="4a354-129">前次全文檢索索引母體擴展完成和 01/01/1990 00:00:00 之間的時差 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="4a354-129">Difference in seconds between the completion of the last full-text index population and 01/01/1990 00:00:00.</span></span>|<span data-ttu-id="4a354-130">FULLTEXTCATALOGPROPERTY</span><span class="sxs-lookup"><span data-stu-id="4a354-130">FULLTEXTCATALOGPROPERTY</span></span>|  
|`PopulateStatus`|<span data-ttu-id="4a354-131">擴展狀態。</span><span class="sxs-lookup"><span data-stu-id="4a354-131">Populate status.</span></span><br /><br /> [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]|<span data-ttu-id="4a354-132">FULLTEXTCATALOGPROPERTY</span><span class="sxs-lookup"><span data-stu-id="4a354-132">FULLTEXTCATALOGPROPERTY</span></span>|  
|`UniqueKeyCount`|<span data-ttu-id="4a354-133">全文檢索目錄中唯一索引鍵的數目。</span><span class="sxs-lookup"><span data-stu-id="4a354-133">Number of unique keys in the full-text catalog.</span></span>|<span data-ttu-id="4a354-134">FULLTEXTCATALOGPROPERTY</span><span class="sxs-lookup"><span data-stu-id="4a354-134">FULLTEXTCATALOGPROPERTY</span></span>|  
  
  
  
##  <a name="rebuilding-a-full-text-catalog"></a><a name="rebuildone"></a><span data-ttu-id="4a354-135">重建全文檢索目錄</span><span class="sxs-lookup"><span data-stu-id="4a354-135">Rebuilding a Full-Text Catalog</span></span>  
  
#### <a name="to-rebuild-a-full-text-catalog"></a><span data-ttu-id="4a354-136">重建全文檢索目錄</span><span class="sxs-lookup"><span data-stu-id="4a354-136">To rebuild a full-text catalog</span></span>  
  
1.  <span data-ttu-id="4a354-137">在物件總管中，展開伺服器，再展開 [資料庫]\*\*\*\*，然後展開含有您要重建其全文檢索目錄的資料庫。</span><span class="sxs-lookup"><span data-stu-id="4a354-137">In Object Explorer, expand the server, expand **Databases**, and then expand the database that contains the full-text catalog that you want to rebuild.</span></span>  
  
2.  <span data-ttu-id="4a354-138">展開 [儲存體]\*\*\*\*，然後展開 [全文檢索目錄]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4a354-138">Expand **Storage**, and then expand **Full Text Catalogs**.</span></span>  
  
3.  <span data-ttu-id="4a354-139">以滑鼠右鍵按一下要重建的全文檢索目錄名稱，然後選取 [重建]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4a354-139">Right-click the name of the full-text catalog that you want to rebuild, and select **Rebuild**.</span></span>  
  
4.  <span data-ttu-id="4a354-140">出現 [您要刪除全文檢索目錄，並重建目錄嗎?]\*\*\*\* 問題時，按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4a354-140">To the question **Do you want to delete the full-text catalog and rebuild it?**, click **OK**.</span></span>  
  
5.  <span data-ttu-id="4a354-141">在 [重建全文檢索目錄]\*\*\*\* 對話方塊中，按一下 [關閉]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4a354-141">In the **Rebuild Full-Text Catalog** dialog box, click **Close**.</span></span>  
  
  
  
##  <a name="rebuilding-all-full-text-catalogs-for-a-database"></a><a name="rebuildall"></a><span data-ttu-id="4a354-142">重建資料庫的所有全文檢索目錄</span><span class="sxs-lookup"><span data-stu-id="4a354-142">Rebuilding All Full-Text Catalogs for a Database</span></span>  
  
#### <a name="to-rebuild-the-full-text-catalogs-for-a-database"></a><span data-ttu-id="4a354-143">重建資料庫的全文檢索目錄</span><span class="sxs-lookup"><span data-stu-id="4a354-143">To rebuild the full-text catalogs for a database</span></span>  
  
1.  <span data-ttu-id="4a354-144">在物件總管中，展開伺服器，再展開 [資料庫]\*\*\*\*，然後展開含有您要重建之全文檢索目錄的資料庫。</span><span class="sxs-lookup"><span data-stu-id="4a354-144">In Object Explorer, expand the server, expand **Databases**, and then expand the database that contains the full-text catalogs that you want to rebuild.</span></span>  
  
2.  <span data-ttu-id="4a354-145">展開 [儲存體]\*\*\*\*，然後以滑鼠右鍵按一下 [全文檢索目錄]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4a354-145">Expand **Storage**, and then right-click **Full Text Catalogs**.</span></span>  
  
3.  <span data-ttu-id="4a354-146">選取 [全部重建]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4a354-146">Select **Rebuild All**.</span></span>  
  
4.  <span data-ttu-id="4a354-147">出現 [您要刪除所有全文檢索目錄，並重建這些目錄嗎?]\*\*\*\* 問題時，按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4a354-147">To the question, **Do you want to delete all full-text catalogs and rebuild them?**, click **OK**.</span></span>  
  
5.  <span data-ttu-id="4a354-148">在 [重建所有全文檢索目錄]\*\*\*\* 對話方塊中，按一下 [關閉]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4a354-148">In the **Rebuild All Full-Text Catalogs** dialog box, click **Close**.</span></span>  
  
  
  
##  <a name="removing-a-full-text-catalog-from-a-database"></a><a name="removing"></a><span data-ttu-id="4a354-149">從資料庫移除全文檢索目錄</span><span class="sxs-lookup"><span data-stu-id="4a354-149">Removing a Full-Text Catalog from a Database</span></span>  
  
#### <a name="to-remove-a-full-text-catalog-from-a-database"></a><span data-ttu-id="4a354-150">從資料庫移除全文檢索目錄</span><span class="sxs-lookup"><span data-stu-id="4a354-150">To remove a full-text catalog from a database</span></span>  
  
1.  <span data-ttu-id="4a354-151">在物件總管中，依序展開 [伺服器]、[資料庫]\*\*\*\*，並展開含有您要移除之全文檢索目錄的資料庫。</span><span class="sxs-lookup"><span data-stu-id="4a354-151">In Object Explorer, expand the server, expand **Databases**, and expand the database that contains the full-text catalog you want to remove.</span></span>  
  
2.  <span data-ttu-id="4a354-152">展開 [儲存體]\*\*\*\*，再展開 [全文檢索目錄]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4a354-152">Expand **Storage**, and expand **Full Text Catalogs**.</span></span>  
  
3.  <span data-ttu-id="4a354-153">以滑鼠右鍵按一下要移除的全文檢索目錄，然後選取 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4a354-153">Right-click the full-text catalog that you want to remove, and then select **Delete**.</span></span>  
  
4.  <span data-ttu-id="4a354-154">在 **[刪除物件]** 對話方塊中，按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="4a354-154">In the **Delete Objects** dialog box, click **OK**.</span></span>  
  
  
  
## <a name="see-also"></a><span data-ttu-id="4a354-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a354-155">See Also</span></span>  
 [<span data-ttu-id="4a354-156">CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4a354-156">CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-catalog-transact-sql)  
  
  
