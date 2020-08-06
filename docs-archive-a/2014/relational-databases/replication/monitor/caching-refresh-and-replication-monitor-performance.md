---
title: 快取、重新整理和複寫監視器效能 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server replication], Replication Monitor
- cache [SQL Server], replication
- Replication Monitor, caching
- refreshing data
- Replication Monitor, refreshing
ms.assetid: a2d8b666-ed41-4f86-b2b8-c8e118416ab7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b04a91e971e65d19c66cc36f142d8c4764b1b05a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593940"
---
# <a name="caching-refresh-and-replication-monitor-performance"></a><span data-ttu-id="1497c-102">快取、重新整理和複寫監視器效能</span><span class="sxs-lookup"><span data-stu-id="1497c-102">Caching, Refresh, and Replication Monitor Performance</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)]<span data-ttu-id="1497c-103">「複寫 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 監視器」的設計目的是要有效率地監視生產系統中的大量電腦。</span><span class="sxs-lookup"><span data-stu-id="1497c-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replication Monitor is designed to efficiently monitor a large number of computers in a production system.</span></span> <span data-ttu-id="1497c-104">會定期快取和重新整理「複寫監視器」用作執行計算和收集資料的查詢。</span><span class="sxs-lookup"><span data-stu-id="1497c-104">The queries that Replication Monitor uses to perform calculations and gather data are cached and refreshed on a periodic basis.</span></span> <span data-ttu-id="1497c-105">快取可減少您在「複寫監視器」中檢視不同頁面時的查詢和計算次數，並可使監視範圍擴大到多個使用者。</span><span class="sxs-lookup"><span data-stu-id="1497c-105">Caching reduces the number of queries and calculations required as you view different pages in Replication Monitor and allows monitoring to scale well for multiple users.</span></span>  
  
 <span data-ttu-id="1497c-106">快取重新整理由 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent 作業 (即 **散發的複寫監視重新整理器**) 處理。</span><span class="sxs-lookup"><span data-stu-id="1497c-106">Cache refresh is handled by a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent job, the **Replication monitoring refresher for distribution**.</span></span> <span data-ttu-id="1497c-107">此作業連續執行，但快取重新整理排程需要在上一次重新整理後等候一段時間：</span><span class="sxs-lookup"><span data-stu-id="1497c-107">The job runs continuously, but the cache refresh schedule is based on waiting a certain amount time after the previous refresh:</span></span>  
  
-   <span data-ttu-id="1497c-108">如果自上次建立快取以來存在代理程式記錄變更，則最短的等候時間是 4 秒或是建立上次快取所花費的時間量。</span><span class="sxs-lookup"><span data-stu-id="1497c-108">If there were agent history changes since the cache was last created, the wait time is the minimum of: 4 seconds; or the amount of time taken to create the previous cache.</span></span>  
  
-   <span data-ttu-id="1497c-109">如果自上次建立快取以來沒有發生代理程式記錄的變更 (之前可能曾有過其他變更)，則最長的等候時間是 30 秒或是建立上次快取所花費的時間量。</span><span class="sxs-lookup"><span data-stu-id="1497c-109">If there were no agent history changes since the cache was last created (there could have been other changes), the wait time is the maximum of: 30 seconds; or the amount of time taken to create the previous cache.</span></span>  
  
## <a name="refreshing-the-replication-monitor-user-interface"></a><span data-ttu-id="1497c-110">重新整理複寫監視器使用者介面</span><span class="sxs-lookup"><span data-stu-id="1497c-110">Refreshing the Replication Monitor User Interface</span></span>  
 <span data-ttu-id="1497c-111">「複寫監視器」使用者介面可以按下列方式重新整理：</span><span class="sxs-lookup"><span data-stu-id="1497c-111">The Replication Monitor user interface can be refreshed in the following ways:</span></span>  
  
-   <span data-ttu-id="1497c-112">依預設，「複寫監視器」主視窗 (包括所有索引標籤) 將每隔五秒鐘自動進行重新整理。</span><span class="sxs-lookup"><span data-stu-id="1497c-112">The main Replication Monitor window (including all tabs), automatically refreshes by default every five seconds.</span></span> <span data-ttu-id="1497c-113">自動重新整理不會強制重新整理快取；使用者介面將顯示快取最新版本的資料。</span><span class="sxs-lookup"><span data-stu-id="1497c-113">Automatic refreshes do not force a refresh of the cache; the user interface displays the most recent version of the data from the cache.</span></span> <span data-ttu-id="1497c-114">您可以透過編輯「發行者」設定來自訂用於所有「發行者」相關視窗的重新整理速率。</span><span class="sxs-lookup"><span data-stu-id="1497c-114">You can customize the refresh rate used for all windows associated with a Publisher by editing the Publisher settings.</span></span> <span data-ttu-id="1497c-115">您還可以停用「發行者」的自動重新整理。</span><span class="sxs-lookup"><span data-stu-id="1497c-115">You can also disable automatic refreshes for a Publisher.</span></span>  
  
-   <span data-ttu-id="1497c-116">依預設，透過「複寫監視器」啟動的詳細資料視窗不會自動重新整理，正在同步處理的合併訂閱的相關視窗除外。</span><span class="sxs-lookup"><span data-stu-id="1497c-116">The detail windows that are launched from Replication Monitor are not automatically refreshed by default, with the exception of windows related to merge subscriptions that are synchronizing.</span></span> <span data-ttu-id="1497c-117">如果您將詳細資料視窗指定為應自動重新整理，則它們將按照與「複寫監視器」主視窗相同的排程重新整理。</span><span class="sxs-lookup"><span data-stu-id="1497c-117">If you specify that detail windows should automatically refresh, they refresh on the same schedule as the main Replication Monitor window.</span></span>  
  
-   <span data-ttu-id="1497c-118">可以透過按 F5 或以滑鼠右鍵按一下「複寫監視器」樹狀目錄中的節點，再按一下 **[重新整理]**，手動重新整理所有視窗。</span><span class="sxs-lookup"><span data-stu-id="1497c-118">All windows can be manually refreshed by pressing F5 or by right-clicking a node in the Replication Monitor tree and clicking **Refresh**.</span></span> <span data-ttu-id="1497c-119">手動重新整理會強制重新整理快取。</span><span class="sxs-lookup"><span data-stu-id="1497c-119">Manual refreshes force a refresh of the cache.</span></span>  
  
 <span data-ttu-id="1497c-120">如需詳細資訊，請參閱[在複寫監視器中重新整理資料](refresh-data-in-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="1497c-120">For more information, see [Refresh Data in Replication Monitor](refresh-data-in-replication-monitor.md).</span></span>  
  
## <a name="performance-considerations"></a><span data-ttu-id="1497c-121">效能考量</span><span class="sxs-lookup"><span data-stu-id="1497c-121">Performance Considerations</span></span>  
 <span data-ttu-id="1497c-122">雖然「複寫監視器」設計成可高效地執行，但仍應注意下列問題：</span><span class="sxs-lookup"><span data-stu-id="1497c-122">Although Replication Monitor is designed to run efficiently, be aware of the following:</span></span>  
  
-   <span data-ttu-id="1497c-123">如果您有大量的發行集或訂閱，請考慮為使用者介面設定頻率較低的自動重新整理排程。</span><span class="sxs-lookup"><span data-stu-id="1497c-123">If you have a large number of publications or subscriptions, consider setting a less frequent automatic refresh schedule for the user interface.</span></span>  
  
-   <span data-ttu-id="1497c-124">避免同時執行多個「複寫監視器」執行個體。</span><span class="sxs-lookup"><span data-stu-id="1497c-124">Avoid concurrently running multiple instances of Replication Monitor.</span></span>  
  
-   <span data-ttu-id="1497c-125">避免註冊大量的「散發者」，同時避免將「複寫監視器」設定為自動連接到所有「散發者」。</span><span class="sxs-lookup"><span data-stu-id="1497c-125">Avoid registering a large number of Distributors and setting Replication Monitor to automatically connect to all of them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1497c-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1497c-126">See Also</span></span>  
 <span data-ttu-id="1497c-127">[執行複寫維護作業 &#40;SQL Server Management Studio&#41;](../../../ssms/sql-server-management-studio-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="1497c-127">[Run Replication Maintenance Jobs &#40;SQL Server Management Studio&#41;](../../../ssms/sql-server-management-studio-ssms.md) </span></span>  
 [<span data-ttu-id="1497c-128">監視複寫</span><span class="sxs-lookup"><span data-stu-id="1497c-128">Monitoring Replication</span></span>](../monitoring-replication.md)  
  
  
