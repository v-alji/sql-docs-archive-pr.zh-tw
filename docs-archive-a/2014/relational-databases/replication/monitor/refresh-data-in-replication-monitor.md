---
title: 在複寫監視器中重新整理資料 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- refreshing data
ms.assetid: e9582244-7d00-45f4-be16-020a65c76a5e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2f097dea21b06540293e9b60b7de9315323b4168
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709190"
---
# <a name="refresh-data-in-replication-monitor"></a><span data-ttu-id="c9eeb-102">在複寫監視器中重新整理資料</span><span class="sxs-lookup"><span data-stu-id="c9eeb-102">Refresh Data in Replication Monitor</span></span>
  <span data-ttu-id="c9eeb-103">在「複寫監視器」中，主視窗與詳細資料視窗 (這些視窗可從主視窗中啟動) 可自動或手動重新整理。</span><span class="sxs-lookup"><span data-stu-id="c9eeb-103">In Replication Monitor, the main window and detail windows (those windows launched from the main window) can be refreshed automatically or manually.</span></span> <span data-ttu-id="c9eeb-104">若要手動重新整理視窗，請按 F5。</span><span class="sxs-lookup"><span data-stu-id="c9eeb-104">To refresh a window manually, press F5.</span></span> <span data-ttu-id="c9eeb-105">依預設，主視窗將每隔五秒鐘自動重新整理；可以為每個「發行者」自訂重新整理速率。</span><span class="sxs-lookup"><span data-stu-id="c9eeb-105">By default, the main window is refreshed automatically every five seconds; the rate can be customized for each Publisher.</span></span>  
  
 <span data-ttu-id="c9eeb-106">在「複寫監視器」中顯示的資料可以透過快取查詢；如需快取與重新整理「複寫監視器」之間的關聯性，請參閱[快取、重新整理和複寫監視器效能](caching-refresh-and-replication-monitor-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="c9eeb-106">The data displayed in Replication Monitor is queried from a cache; for information about the relationship between the cache and refreshing Replication Monitor, see [Caching, Refresh, and Replication Monitor Performance](caching-refresh-and-replication-monitor-performance.md).</span></span> <span data-ttu-id="c9eeb-107">如需啟動複寫監視器的詳細資訊，請參閱[啟動複寫監視器](start-the-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="c9eeb-107">For information about starting Replication Monitor, see [Start the Replication Monitor](start-the-replication-monitor.md).</span></span>  
  
### <a name="to-set-refresh-options-for-replication-monitor"></a><span data-ttu-id="c9eeb-108">若要為複寫監視器設定重新整理選項</span><span class="sxs-lookup"><span data-stu-id="c9eeb-108">To set refresh options for Replication Monitor</span></span>  
  
1.  <span data-ttu-id="c9eeb-109">以滑鼠右鍵按一下「複寫監視器」左窗格中的「發行者」，然後按一下 **[發行者設定]** 。</span><span class="sxs-lookup"><span data-stu-id="c9eeb-109">Right-click a Publisher in the left pane of Replication Monitor, and then click **Publisher Settings**.</span></span>  
  
2.  <span data-ttu-id="c9eeb-110">在 **[發行者設定]** 對話方塊中，設定 **[自動重新整理]** 與 **[重新整理的速率]** 選項。</span><span class="sxs-lookup"><span data-stu-id="c9eeb-110">In the **Publisher Settings** dialog box, set the **Auto refresh** and **Refresh rate** options.</span></span> <span data-ttu-id="c9eeb-111">**[自動重新整理]** 設定會影響「複寫監視器」中的主視窗。</span><span class="sxs-lookup"><span data-stu-id="c9eeb-111">The **Auto refresh** setting affects the main window in Replication Monitor.</span></span> <span data-ttu-id="c9eeb-112">**[重新整理的速率]** 設定也可以影響所有設定為自動重新整理的詳細資料視窗 (設定的變更僅影響在變更後開啟的詳細資料視窗)。</span><span class="sxs-lookup"><span data-stu-id="c9eeb-112">The **Refresh rate** setting also affects any detail windows that are set to refresh automatically (changes to the setting only affect the detail windows opened after the change).</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-specify-that-a-detail-window-should-automatically-refresh"></a><span data-ttu-id="c9eeb-113">若要指定詳細資料視窗應自動重新整理</span><span class="sxs-lookup"><span data-stu-id="c9eeb-113">To specify that a detail window should automatically refresh</span></span>  
  
1.  <span data-ttu-id="c9eeb-114">在「複寫監視器」中開啟詳細資料視窗。</span><span class="sxs-lookup"><span data-stu-id="c9eeb-114">Open a detail window in Replication Monitor.</span></span> <span data-ttu-id="c9eeb-115">例如：</span><span class="sxs-lookup"><span data-stu-id="c9eeb-115">For example:</span></span>  
  
    1.  <span data-ttu-id="c9eeb-116">在左窗格中展開發行者群組，展開發行者，然後按一下發行集。</span><span class="sxs-lookup"><span data-stu-id="c9eeb-116">Expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
    2.  <span data-ttu-id="c9eeb-117">按一下 **[所有訂閱]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="c9eeb-117">Click the **All Subscriptions** tab.</span></span>  
  
    3.  <span data-ttu-id="c9eeb-118">以滑鼠右鍵按一下訂閱，然後按一下 **[檢視詳細資料]** 。</span><span class="sxs-lookup"><span data-stu-id="c9eeb-118">Right-click a subscription, and then click **View Details**.</span></span>  
  
2.  <span data-ttu-id="c9eeb-119">在 [訂閱 \<SubscriptionName>] 詳細資料視窗中，按一下 [動作]，然後按一下 [自動重新整理]。</span><span class="sxs-lookup"><span data-stu-id="c9eeb-119">In the **Subscription \<SubscriptionName>** detail window, click **Action**, and then click **Auto Refresh**.</span></span> <span data-ttu-id="c9eeb-120">重新整理速率將由 **[發行者設定]** 對話方塊中的 **[重新整理的速率]** 設定決定。</span><span class="sxs-lookup"><span data-stu-id="c9eeb-120">The refresh rate is determined by the **Refresh rate** setting in the **Publisher Settings** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9eeb-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9eeb-121">See Also</span></span>  
 [<span data-ttu-id="c9eeb-122">監視複寫</span><span class="sxs-lookup"><span data-stu-id="c9eeb-122">Monitoring Replication</span></span>](../monitoring-replication.md)  
  
  
