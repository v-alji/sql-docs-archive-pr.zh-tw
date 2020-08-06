---
title: 使用僅限下載的發行項最佳化合併式複寫效能 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication [SQL Server replication], download-only articles
- articles [SQL Server replication], download-only
- download-only articles
ms.assetid: 8851faa6-e6df-4ea5-a6ea-2a3471680fa3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8414174971792f8a2c256cd564dd1ea224527463
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584429"
---
# <a name="optimize-merge-replication-performance-with-download-only-articles"></a><span data-ttu-id="9443a-102">使用僅限下載的發行項最佳化合併式複寫效能</span><span class="sxs-lookup"><span data-stu-id="9443a-102">Optimize Merge Replication Performance with Download-Only Articles</span></span>
  <span data-ttu-id="9443a-103">合併式複寫提供兩種不同類型的發行項，以滿足不同應用程式的需求。</span><span class="sxs-lookup"><span data-stu-id="9443a-103">Merge replication offers two different article types to address different application needs.</span></span> <span data-ttu-id="9443a-104">發行集可包含這兩種類型的一種或兩種，以符合應用程式：</span><span class="sxs-lookup"><span data-stu-id="9443a-104">Publications can contain one or more of each of these article types as appropriate for the application:</span></span>  
  
-   <span data-ttu-id="9443a-105">標準發行項</span><span class="sxs-lookup"><span data-stu-id="9443a-105">Standard articles</span></span>  
  
-   <span data-ttu-id="9443a-106">僅限下載的發行項</span><span class="sxs-lookup"><span data-stu-id="9443a-106">Download-only articles</span></span>  
  
 <span data-ttu-id="9443a-107">僅限下載的發行項所提供的效能比之標準發行項要好，應在適當的地方使用。</span><span class="sxs-lookup"><span data-stu-id="9443a-107">Download-only articles provide performance advantages over standard articles and should be used where appropriate.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9443a-108">若要使用僅限下載發行項，發行集的相容性層級必須至少為 90RTM。</span><span class="sxs-lookup"><span data-stu-id="9443a-108">To use download-only articles, the compatibility level of the publication must be at least 90RTM.</span></span>  
  
## <a name="standard-articles"></a><span data-ttu-id="9443a-109">標準發行項</span><span class="sxs-lookup"><span data-stu-id="9443a-109">Standard Articles</span></span>  
 <span data-ttu-id="9443a-110">標準發行項為預設值，提供全部合併式複寫範圍內的所有功能，包括各種衝突偵測和解決方案。</span><span class="sxs-lookup"><span data-stu-id="9443a-110">Standard articles are the default, offering the full range of merge replication features, including rich conflict detection and resolution.</span></span> <span data-ttu-id="9443a-111">標準發行項適合於由多個「訂閱者」更新的資料表；始終將除資料表以外的物件 (例如預存程序和檢視) 做為標準發行項來發行。</span><span class="sxs-lookup"><span data-stu-id="9443a-111">Standard articles are appropriate for tables that are updated by multiple Subscribers; objects other than tables, such as stored procedures and views, are always published as standard articles.</span></span>  
  
## <a name="download-only-articles"></a><span data-ttu-id="9443a-112">僅限下載的發行項</span><span class="sxs-lookup"><span data-stu-id="9443a-112">Download-Only Articles</span></span>  
 <span data-ttu-id="9443a-113">僅限下載的發行項是為不在「訂閱者」端更新資料的應用程式所設計，例如包含於產品目錄中的一組發行項。</span><span class="sxs-lookup"><span data-stu-id="9443a-113">Download-only articles are designed for applications with data that is not updated at Subscribers, such as a set of articles that are contained in a product catalog.</span></span> <span data-ttu-id="9443a-114">產品目錄一般在「發行者」端而不在「訂閱者」端更新。</span><span class="sxs-lookup"><span data-stu-id="9443a-114">A product catalog is typically updated at the Publisher, but not at the Subscribers.</span></span> <span data-ttu-id="9443a-115">因為僅限下載的發行項不能在訂閱者端進行更新，追蹤中繼資料不會傳送給訂閱者。</span><span class="sxs-lookup"><span data-stu-id="9443a-115">Because download-only articles cannot be updated at the Subscriber, tracking metadata is not sent to Subscribers.</span></span> <span data-ttu-id="9443a-116">如此可減少訂閱者上的儲存體並提高效能，特別是網路連接緩慢時。</span><span class="sxs-lookup"><span data-stu-id="9443a-116">This can lead to reduced storage on the Subscribers and a performance benefit, especially if the network connection is slow.</span></span>  
  
 <span data-ttu-id="9443a-117">僅限下載的發行項結合客訂閱一起使用：如果發行項被設計為僅限下載，則將無法在使用客訂閱的「訂閱者」端插入、更新或刪除這個發行項的資料列。</span><span class="sxs-lookup"><span data-stu-id="9443a-117">Download-only articles work in conjunction with client subscriptions: if an article is designated as download-only, rows for that article cannot be inserted, updated, or deleted at Subscribers who use client subscriptions.</span></span> <span data-ttu-id="9443a-118">使用主訂閱類型的「發行者」與「訂閱者」 (一般是重新發行資料到其他「訂閱者」的「訂閱者」) 可插入、更新和刪除資料。</span><span class="sxs-lookup"><span data-stu-id="9443a-118">Publishers and Subscribers that use the server subscription type (typically Subscribers that republish data to other Subscribers) can insert, update, and delete data.</span></span> <span data-ttu-id="9443a-119">如需用戶端訂閱的詳細資訊，請參閱[訂閱發行集](../subscribe-to-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="9443a-119">For more information about client subscriptions, see [Subscribe to Publications](../subscribe-to-publications.md).</span></span>  
  
 <span data-ttu-id="9443a-120">若要指定發行項為僅限下載，請參閱＜ [將合併資料表發行項指定為僅限下載](../publish/specify-merge-replication-properties.md#download-only)＞。</span><span class="sxs-lookup"><span data-stu-id="9443a-120">To specify that an article is download-only, see [Specify That a Merge Table Article is Download-Only](../publish/specify-merge-replication-properties.md#download-only).</span></span>  
  
## <a name="using-different-article-types-in-your-applications"></a><span data-ttu-id="9443a-121">在應用程式中使用不同的發行項類型</span><span class="sxs-lookup"><span data-stu-id="9443a-121">Using Different Article Types in Your Applications</span></span>  
 <span data-ttu-id="9443a-122">透過了解應用程式的需求，您可以在最具彈性與最佳效能之間權衡取捨。</span><span class="sxs-lookup"><span data-stu-id="9443a-122">By understanding the requirements of your application, you can make tradeoffs between maximum flexibility and optimal performance.</span></span> <span data-ttu-id="9443a-123">例如，在「發行者」端與「訂閱者」端有大量衝突與變更處理的應用程式，將使用由標準發行項組成的發行集。</span><span class="sxs-lookup"><span data-stu-id="9443a-123">For example, applications with numerous conflicts and changes at both the Publisher and Subscribers will use a publication made up of standard articles.</span></span> <span data-ttu-id="9443a-124">某些應用程式，例如銷售人員自動化應用程式，含有一些可能發生衝突的發行項，以及另一些做為查閱資料表的發行項，可被指定為僅限下載。</span><span class="sxs-lookup"><span data-stu-id="9443a-124">Some applications, such as a sales force automation application, might have articles with a potential for conflicts, and other articles that function as lookup tables, which can be specified as download-only.</span></span> <span data-ttu-id="9443a-125">資料項目應用程式 (例如銷售系統各點和現場服務自動化應用程式) 通常使用嚴格地分割資料這一方式來消除衝突，來自某個「訂閱者」的資料決不會流到其他「訂閱者」處。</span><span class="sxs-lookup"><span data-stu-id="9443a-125">Data entry applications, such as point of sales systems and field force automation applications, often strictly partition data in a way that conflicts are eliminated, and data from one Subscriber never goes to another.</span></span> <span data-ttu-id="9443a-126">在這些情況下，不重疊資料分割的組合、僅限下載的發行項和預先計算的資料分割會提供最佳的效能和延展性。</span><span class="sxs-lookup"><span data-stu-id="9443a-126">In these situations, a combination of nonoverlapping partitions, download-only articles and precomputed partitions provides maximum performance and scalability.</span></span> <span data-ttu-id="9443a-127">如需不重疊資料分割和預先計算資料分割的詳細資訊，請參閱＜ [参数化行过滤器](parameterized-filters-parameterized-row-filters.md)＞。</span><span class="sxs-lookup"><span data-stu-id="9443a-127">For more information about nonoverlapping partitions and precomputed partitions, see [Parameterized Row Filters](parameterized-filters-parameterized-row-filters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9443a-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9443a-128">See Also</span></span>  
 <span data-ttu-id="9443a-129">[合併式複寫的發行項選項](article-options-for-merge-replication.md) </span><span class="sxs-lookup"><span data-stu-id="9443a-129">[Article Options for Merge Replication](article-options-for-merge-replication.md) </span></span>  
 [<span data-ttu-id="9443a-130">使用條件式刪除追蹤最佳化合併式複寫效能</span><span class="sxs-lookup"><span data-stu-id="9443a-130">Optimize Merge Replication Performance with Conditional Delete Tracking</span></span>](optimize-merge-replication-performance-with-conditional-delete-tracking.md)  
  
  
