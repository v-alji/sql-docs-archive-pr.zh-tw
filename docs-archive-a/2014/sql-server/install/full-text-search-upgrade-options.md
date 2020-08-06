---
title: 全文檢索搜尋升級選項 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- Full-Text Search
- Upgrade options, Full-Text Search
ms.assetid: 16c9376b-5fbb-4495-a429-06a2493849c9
author: rothja
ms.author: jroth
ms.openlocfilehash: ade7a05563598440c3fdc79dd4b3584f7f797d4e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688454"
---
# <a name="full-text-search-upgrade-options"></a><span data-ttu-id="efa95-102">全文檢索搜尋升級選項</span><span class="sxs-lookup"><span data-stu-id="efa95-102">Full-Text Search Upgrade Options</span></span>
  <span data-ttu-id="efa95-103">您可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝精靈的 [全文檢索搜尋升級選項] 頁面，針對此時升級的資料庫選取要使用的全文檢索搜尋升級選項。</span><span class="sxs-lookup"><span data-stu-id="efa95-103">Use the Full-Text Search Upgrade Options page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard to select the full-text search upgrade option to use for the databases that you are upgrading at this time.</span></span>  
  
 <span data-ttu-id="efa95-104">在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 中，每個全文檢索索引都位於屬於檔案群組、具有實體路徑而且被視為資料庫檔案的全文檢索目錄中。</span><span class="sxs-lookup"><span data-stu-id="efa95-104">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] each full-text index resides in a full-text catalog that belongs to a filegroup, has a physical path, and is treated as a database file.</span></span> <span data-ttu-id="efa95-105">現在，全文檢索目錄是參考一組全文檢索索引的邏輯概念（虛擬物件）。</span><span class="sxs-lookup"><span data-stu-id="efa95-105">Now, a full-text catalog is a logical concept-a virtual object-that refers to a group of full-text indexes.</span></span> <span data-ttu-id="efa95-106">因此，新的全文檢索目錄不會被視為具有實體路徑的資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="efa95-106">Therefore, a new full-text catalog is not treated as a database file with a physical path.</span></span> <span data-ttu-id="efa95-107">不過，在升級含有資料檔案的任何全文檢索目錄期間，系統會在相同的磁碟上建立新的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="efa95-107">However, during upgrade of any full-text catalog that contains data files, a new filegroup is created on same disk.</span></span> <span data-ttu-id="efa95-108">這會在升級之後保留舊磁碟 I/O 行為。</span><span class="sxs-lookup"><span data-stu-id="efa95-108">This maintains the old disk I/O behavior after upgrade.</span></span> <span data-ttu-id="efa95-109">如果根路徑存在，則任何來自該目錄的全文檢索索引都會放置於新的檔案群組中。</span><span class="sxs-lookup"><span data-stu-id="efa95-109">Any full-text index from that catalog is placed in the new filegroup if the root path exists.</span></span> <span data-ttu-id="efa95-110">如果舊的全文檢索目錄路徑無效，升級作業就會將全文檢索索引保留在與基底資料表相同的檔案群組中，或是保留在分割區資料表的主要檔案群組中。</span><span class="sxs-lookup"><span data-stu-id="efa95-110">If the old full-text catalog path is invalid, the upgrade keeps the full-text index in the same filegroup as base table or, for a partitioned table, in the primary filegroup.</span></span>  
  
## <a name="options"></a><span data-ttu-id="efa95-111">選項</span><span class="sxs-lookup"><span data-stu-id="efa95-111">Options</span></span>  
 <span data-ttu-id="efa95-112">當您升級為 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]時，請選擇下列其中一個全文檢索升級選項。</span><span class="sxs-lookup"><span data-stu-id="efa95-112">When you upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], choose one of the following full-text upgrade options.</span></span>  
  
 <span data-ttu-id="efa95-113">**匯入**</span><span class="sxs-lookup"><span data-stu-id="efa95-113">**Import**</span></span>  
 <span data-ttu-id="efa95-114">匯入全文檢索目錄。</span><span class="sxs-lookup"><span data-stu-id="efa95-114">Full-text catalogs are imported.</span></span> <span data-ttu-id="efa95-115">一般而言，匯入的速度明顯比重建的速度更快。</span><span class="sxs-lookup"><span data-stu-id="efa95-115">Typically, import is significantly faster than rebuild.</span></span> <span data-ttu-id="efa95-116">例如，只有使用一個 CPU 時，匯入的執行速度大約比重建的速度快 10 倍。</span><span class="sxs-lookup"><span data-stu-id="efa95-116">For example, when using only one CPU, import runs about 10 times faster than rebuild.</span></span> <span data-ttu-id="efa95-117">不過，從 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 匯入的全文檢索目錄並不會使用新增的強化斷詞工具，所以您最後可能會想要重建全文檢索目錄。</span><span class="sxs-lookup"><span data-stu-id="efa95-117">However, a full-text catalog imported from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] does not use the new and enhanced word breakers, so you might want to rebuild your full-text catalogs eventually.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="efa95-118">重建可以在多執行緒模式中執行，而且如果有 10 個以上的 CPU 可用，當您允許重建使用所有 CPU 時，重建的執行速度可能會比匯入的速度更快。</span><span class="sxs-lookup"><span data-stu-id="efa95-118">Rebuild can run in multi-threaded mode, and if more than 10 CPUs are available, rebuild might run faster than import if you allow rebuild to use all of the CPUs.</span></span>  
  
 <span data-ttu-id="efa95-119">如果無法使用全文檢索目錄，將會重建關聯的全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="efa95-119">If a full-text catalog is not available, the associated full-text indexes are rebuilt.</span></span> <span data-ttu-id="efa95-120">只有針對 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 資料庫才可以使用此選項。</span><span class="sxs-lookup"><span data-stu-id="efa95-120">This option is available for only [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] databases.</span></span>  
  
 <span data-ttu-id="efa95-121">如需有關匯入全文檢索索引之影響的詳細資訊，請參閱本主題後面的「選擇全文檢索升級選項的考量」。</span><span class="sxs-lookup"><span data-stu-id="efa95-121">For information about the impact of importing full-text index, see "Considerations for Choosing a Full-Text Upgrade Option," later in this topic.</span></span>  
  
 <span data-ttu-id="efa95-122">**重建**</span><span class="sxs-lookup"><span data-stu-id="efa95-122">**Rebuild**</span></span>  
 <span data-ttu-id="efa95-123">全文檢索目錄會使用新的增強斷詞工具重建。</span><span class="sxs-lookup"><span data-stu-id="efa95-123">Full-text catalogs are rebuilt using the new and enhanced word breakers.</span></span> <span data-ttu-id="efa95-124">重建索引可能需要很長的時間，而且在升級之後可能需要相當多的 CPU 和記憶體。</span><span class="sxs-lookup"><span data-stu-id="efa95-124">Rebuilding indexes can take a lot of time, and a significant amount of CPU and memory might be required after the upgrade.</span></span>  
  
 <span data-ttu-id="efa95-125">**重設**</span><span class="sxs-lookup"><span data-stu-id="efa95-125">**Reset**</span></span>  
 <span data-ttu-id="efa95-126">重設全文檢索目錄。</span><span class="sxs-lookup"><span data-stu-id="efa95-126">Full-text catalogs are reset.</span></span> <span data-ttu-id="efa95-127">從 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]進行升級時，全文檢索目錄檔案會遭到移除，但是全文檢索目錄和全文檢索索引的中繼資料則會保留。</span><span class="sxs-lookup"><span data-stu-id="efa95-127">When upgrading from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], full-text catalog files are removed, but the metadata for full-text catalogs and full-text indexes is retained.</span></span> <span data-ttu-id="efa95-128">在升級之後，所有的全文檢索索引都會停用變更追蹤，而且不會自動啟動搜耙。</span><span class="sxs-lookup"><span data-stu-id="efa95-128">After being upgraded, all full-text indexes are disabled for change tracking and crawls are not started automatically.</span></span> <span data-ttu-id="efa95-129">當您在升級完成之後手動發出完整母體擴展之前，此目錄將會維持空白狀態。</span><span class="sxs-lookup"><span data-stu-id="efa95-129">The catalog will remain empty until you manually issue a full population, after the upgrade completes.</span></span>  
  
 <span data-ttu-id="efa95-130">所有的這些升級選項都可確保升級的資料庫可完全獲益於全文檢索效能增強功能。</span><span class="sxs-lookup"><span data-stu-id="efa95-130">All of these upgrade options ensure that upgraded databases benefit fully from full-text performance enhancements.</span></span>  
  
## <a name="considerations-for-choosing-a-full-text-upgrade-option"></a><span data-ttu-id="efa95-131">選擇全文檢索升級選項的考量</span><span class="sxs-lookup"><span data-stu-id="efa95-131">Considerations for Choosing a Full-Text Upgrade Option</span></span>  
 <span data-ttu-id="efa95-132">當您為升級作業選擇升級選項時，請考慮下列事項：</span><span class="sxs-lookup"><span data-stu-id="efa95-132">When choosing the upgrade option for your upgrade, consider the following:</span></span>  
  
-   <span data-ttu-id="efa95-133">您如何使用斷詞工具？</span><span class="sxs-lookup"><span data-stu-id="efa95-133">How do you use word breakers?</span></span>  
  
     <span data-ttu-id="efa95-134">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中的全文檢索搜尋服務包括斷詞工具和字幹分析器。</span><span class="sxs-lookup"><span data-stu-id="efa95-134">The full-text search service in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] includes word breakers and stemmers.</span></span> <span data-ttu-id="efa95-135">這些項目可能會針對特定文字模式或狀況，變更從 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 全文檢索查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="efa95-135">These might change the results of full-text queries from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] for a specific text pattern or scenario.</span></span> <span data-ttu-id="efa95-136">因此，在選擇適當的升級選項時，您如何使用斷詞工具便很重要：</span><span class="sxs-lookup"><span data-stu-id="efa95-136">Therefore, how you use word breakers is important when choosing a suitable upgrade option:</span></span>  
  
    -   <span data-ttu-id="efa95-137">如果您所使用之全文檢索語言的斷詞工具並未變更，或者重新叫用精確度對您不重要，則適合進行匯入。</span><span class="sxs-lookup"><span data-stu-id="efa95-137">If the word breakers of the full-text language you use did not change, or if recall accuracy is not critical to you, importing is suitable.</span></span> <span data-ttu-id="efa95-138">之後，如果您遇到任何重新叫用的問題，只要透過重建全文檢索目錄，就可以升級為新的斷詞工具。</span><span class="sxs-lookup"><span data-stu-id="efa95-138">Later, if you experience any recall issues, you can upgrade to the new word breakers simply by rebuilding your full-text catalogs.</span></span>  
  
    -   <span data-ttu-id="efa95-139">如果您很重視重新叫用精確度，並使用在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]之後加入的其中一個斷詞工具，則適合進行重建。</span><span class="sxs-lookup"><span data-stu-id="efa95-139">If you care about recall accuracy and you use one of the word breakers that were added after [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], rebuilding is suitable.</span></span>  
  
-   <span data-ttu-id="efa95-140">是否有任何全文檢索索引建立在整數全文檢索索引鍵資料行上？</span><span class="sxs-lookup"><span data-stu-id="efa95-140">Were any full-text indexes built on integer full-text key columns?</span></span>  
  
     <span data-ttu-id="efa95-141">重建會執行內部最佳化，以便在某些情況中改善已升級之全文檢索索引的查詢效能。</span><span class="sxs-lookup"><span data-stu-id="efa95-141">Rebuilding performs internal optimizations that improve the query performance of the upgraded full-text index in some cases.</span></span> <span data-ttu-id="efa95-142">具體而言，如果您擁有包含全文檢索索引的全文檢索目錄，其中基底資料表的全文檢索索引鍵資料行是整數資料類型，則重建會在升級之後達到理想的全文檢索查詢效能。</span><span class="sxs-lookup"><span data-stu-id="efa95-142">Specifically, if you have full-text catalogs that contain full-text indexes for which the full-text key column of the base table is an integer data type, rebuilding achieves ideal performance of full-text queries after upgrade.</span></span> <span data-ttu-id="efa95-143">在此情況中，我們強烈建議您使用 **[重建]** 選項。</span><span class="sxs-lookup"><span data-stu-id="efa95-143">In this case, we highly recommend you to use the **Rebuild** option.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="efa95-144">若為 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中的全文檢索索引，我們建議當做全文檢索索引鍵的資料行必須是整數資料類型。</span><span class="sxs-lookup"><span data-stu-id="efa95-144">For full-text indexes in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], we recommend that the column serving as the full-text key be an integer data type.</span></span> <span data-ttu-id="efa95-145">如需詳細資訊，請參閱 [改善全文檢索索引的效能](../../relational-databases/indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="efa95-145">For more information, see [Improve the Performance of Full-Text Indexes](../../relational-databases/indexes/indexes.md).</span></span>  
  
-   <span data-ttu-id="efa95-146">將伺服器執行個體保持在線上狀態的優先權為何？</span><span class="sxs-lookup"><span data-stu-id="efa95-146">What is the priority for getting your server instance online?</span></span>  
  
     <span data-ttu-id="efa95-147">在升級期間匯入或重建會耗用大量 CPU 資源，因而延遲將其餘伺服器執行個體升級並保持在線上狀態的時間。</span><span class="sxs-lookup"><span data-stu-id="efa95-147">Importing or rebuilding during upgrade takes a lot of CPU resources, which delays getting the rest of the server instance upgraded and online.</span></span> <span data-ttu-id="efa95-148">如果盡可能將伺服器執行個體保持在線上狀態很重要，而且您願意在升級之後執行手動母體擴展，則適合使用 **[重設]** 。</span><span class="sxs-lookup"><span data-stu-id="efa95-148">If getting the server instance online as soon as possible is important and if you are willing to run a manual population after the upgrade, **Reset** is suitable.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="efa95-149">其他資源</span><span class="sxs-lookup"><span data-stu-id="efa95-149">Additional Resources</span></span>  
  
