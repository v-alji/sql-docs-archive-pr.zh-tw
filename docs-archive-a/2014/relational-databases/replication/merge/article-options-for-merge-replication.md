---
title: 合併式複寫的發行項選項 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication [SQL Server replication], article options
- articles [SQL Server replication], merge replication options
ms.assetid: 670abd41-d204-4cd7-a371-7664e603a0ce
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d4f9e6391962d5755983322073f738ba84f02633
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584456"
---
# <a name="article-options-for-merge-replication"></a><span data-ttu-id="1bc18-102">合併式複寫的發行項選項</span><span class="sxs-lookup"><span data-stu-id="1bc18-102">Article Options for Merge Replication</span></span>
  <span data-ttu-id="1bc18-103">合併資料表發行項有許多選項，可讓您自訂複寫行為以適應應用程式的需要。</span><span class="sxs-lookup"><span data-stu-id="1bc18-103">There are many options for merge table articles that enable you to customize replication behavior to the needs of your applications.</span></span> <span data-ttu-id="1bc18-104">使用合併式複寫，您可以執行下列項目：</span><span class="sxs-lookup"><span data-stu-id="1bc18-104">By using merge replication, you can do the following:</span></span>  
  
-   <span data-ttu-id="1bc18-105">使用資料列篩選、聯結篩選和資料行篩選。</span><span class="sxs-lookup"><span data-stu-id="1bc18-105">Use row filters, join filters, and column filters.</span></span> <span data-ttu-id="1bc18-106">篩選資料表發行項可讓您建立即將發行的資料分割。</span><span class="sxs-lookup"><span data-stu-id="1bc18-106">Filtering table articles enables you to create partitions of data to be published.</span></span> <span data-ttu-id="1bc18-107">如需詳細資訊，請參閱[篩選發行的資料](../publish/filter-published-data.md)。</span><span class="sxs-lookup"><span data-stu-id="1bc18-107">For more information, see [Filter Published Data](../publish/filter-published-data.md).</span></span>  
  
-   <span data-ttu-id="1bc18-108">指定「訂閱者」端的變更是否上傳到「發行者」。</span><span class="sxs-lookup"><span data-stu-id="1bc18-108">Specify whether changes at the Subscriber are uploaded to the Publisher.</span></span> <span data-ttu-id="1bc18-109">對於部份或所有資料在「訂閱者」端應為唯讀的應用程式，僅限下載的發行項可提供效能優勢。</span><span class="sxs-lookup"><span data-stu-id="1bc18-109">For applications in which some or all data should be read-only at the Subscriber, download-only articles provide a performance benefit.</span></span> <span data-ttu-id="1bc18-110">如需詳細資訊，請參閱[使用僅限下載的發行項最佳化合併式複寫效能](optimize-merge-replication-performance-with-download-only-articles.md)。</span><span class="sxs-lookup"><span data-stu-id="1bc18-110">For more information, see [Optimize Merge Replication Performance with Download-Only Articles](optimize-merge-replication-performance-with-download-only-articles.md).</span></span>  
  
-   <span data-ttu-id="1bc18-111">指定複寫觸發程序和系統資料表不應追蹤對於一個或多個發行項所作的刪除。</span><span class="sxs-lookup"><span data-stu-id="1bc18-111">Specify that deletes for one or more articles should not be tracked by replication triggers and system tables.</span></span> <span data-ttu-id="1bc18-112">這個選項在許多應用程式案例中可能很有用處。</span><span class="sxs-lookup"><span data-stu-id="1bc18-112">This option can be useful in many application scenarios.</span></span> <span data-ttu-id="1bc18-113">這些包括使用不需要複寫之批次刪除的案例。</span><span class="sxs-lookup"><span data-stu-id="1bc18-113">These include scenarios that use batch deletes that do not need to be replicated.</span></span> <span data-ttu-id="1bc18-114">如需詳細資訊，請參閱[使用僅限下載的發行項最佳化合併式複寫效能](optimize-merge-replication-performance-with-conditional-delete-tracking.md)。</span><span class="sxs-lookup"><span data-stu-id="1bc18-114">For more information, see [Optimize Merge Replication Performance with Conditional Delete Tracking](optimize-merge-replication-performance-with-conditional-delete-tracking.md).</span></span>  
  
-   <span data-ttu-id="1bc18-115">指定發行項的處理順序，以確定發行項是以應用程式需要的順序進行處理。</span><span class="sxs-lookup"><span data-stu-id="1bc18-115">Specify the processing order of articles to make sure that articles are processed in the order required by your application.</span></span> <span data-ttu-id="1bc18-116">如需詳細資訊，請參閱[指定合併式複寫屬性](../publish/specify-merge-replication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="1bc18-116">For more information, see [Specify Merge Replication properties](../publish/specify-merge-replication-properties.md).</span></span>  
  
-   <span data-ttu-id="1bc18-117">指定一組相關記錄應視為一個單位處理 (依預設，合併式複寫會以逐個資料列的方式處理資料表的變更)。</span><span class="sxs-lookup"><span data-stu-id="1bc18-117">Specify that a set of related records should be processed as a unit (by default, merge replication processes changes to tables on a row-by-row basis).</span></span> <span data-ttu-id="1bc18-118">如需詳細資訊，請參閱[使用邏輯記錄分組相關資料列的變更](group-changes-to-related-rows-with-logical-records.md)。</span><span class="sxs-lookup"><span data-stu-id="1bc18-118">For more information, see [Group Changes to Related Rows with Logical Records](group-changes-to-related-rows-with-logical-records.md).</span></span>  
  
-   <span data-ttu-id="1bc18-119">對可以在拓撲的多個節點上變更相同資料之案例，使用衝突偵測和解決方案。</span><span class="sxs-lookup"><span data-stu-id="1bc18-119">Use conflict detection and resolution for cases in which the same data could be changed at more than one node in a topology.</span></span> <span data-ttu-id="1bc18-120">如需相關資訊，請參閱 [偵測及解決合併式複寫衝突](advanced-merge-replication-conflict-detection-and-resolution.md)。</span><span class="sxs-lookup"><span data-stu-id="1bc18-120">For more information, see [Detect and Resolve Merge Replication Conflicts](advanced-merge-replication-conflict-detection-and-resolution.md).</span></span>  
  
-   <span data-ttu-id="1bc18-121">指定結構描述選項，如條件約束和觸發程序是否複製到訂閱者。</span><span class="sxs-lookup"><span data-stu-id="1bc18-121">Specify schema options, such as whether constraints and triggers are copied to the Subscriber.</span></span> <span data-ttu-id="1bc18-122">如需詳細資訊，請參閱 [指定結構描述選項](../publish/specify-schema-options.md)。</span><span class="sxs-lookup"><span data-stu-id="1bc18-122">For more information, see [Specify Schema Options](../publish/specify-schema-options.md).</span></span>  
  
-   <span data-ttu-id="1bc18-123">使用商務邏輯處理常式，以便在同步處理期間回應許多狀況。</span><span class="sxs-lookup"><span data-stu-id="1bc18-123">Use a business logic handler to respond to many conditions during synchronization.</span></span> <span data-ttu-id="1bc18-124">這些包括資料變更、衝突和錯誤。</span><span class="sxs-lookup"><span data-stu-id="1bc18-124">These include data changes, conflicts, and errors.</span></span> <span data-ttu-id="1bc18-125">如需詳細資訊，請參閱[在合併同步處理期間執行商務邏輯](execute-business-logic-during-merge-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="1bc18-125">For more information, see [Execute Business Logic During Merge Synchronization](execute-business-logic-during-merge-synchronization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bc18-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bc18-126">See Also</span></span>  
 [<span data-ttu-id="1bc18-127">發行資料和資料庫物件</span><span class="sxs-lookup"><span data-stu-id="1bc18-127">Publish Data and Database Objects</span></span>](../publish/publish-data-and-database-objects.md)  
  
  
