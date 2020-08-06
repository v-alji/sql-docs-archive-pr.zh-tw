---
title: '[散發者設定] 對話方塊 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.DistributorSettings.f1
helpviewer_keywords:
- Distributor Settings dialog box
ms.assetid: 8276a521-bdd1-4783-bdb6-7ab43499c0ca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b864620f155e899868c95f58350f98e2b659c4e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585862"
---
# <a name="sql-server-replication-distributor-settings-dialog-box"></a><span data-ttu-id="80920-102">SQL Server 複寫 [散發者設定] 對話方塊</span><span class="sxs-lookup"><span data-stu-id="80920-102">SQL Server Replication 'Distributor Settings' dialog box</span></span>
  <span data-ttu-id="80920-103">**[散發者設定]** 對話方塊，可讓您針對已加入至複寫監視器之左窗格的散發者變更設定。</span><span class="sxs-lookup"><span data-stu-id="80920-103">The **Distributor Settings** dialog box enables you to change settings for Distributors that were added to the left pane in Replication Monitor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="80920-104">選項。</span><span class="sxs-lookup"><span data-stu-id="80920-104">Options</span></span>  
 <span data-ttu-id="80920-105">**啟動複寫監視器時自動連接**</span><span class="sxs-lookup"><span data-stu-id="80920-105">**Connect automatically when Replication Monitor starts**</span></span>  
 <span data-ttu-id="80920-106">選取以讓複寫監視器連接到「散發者」並擷取狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="80920-106">Select to let Replication Monitor connect to the Distributor and retrieve status information.</span></span>  
  
 <span data-ttu-id="80920-107">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="80920-107">**Connection**</span></span>  
 <span data-ttu-id="80920-108">按一下以顯示 **[連接到伺服器]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="80920-108">Click to display the **Connect to Server** dialog box.</span></span> <span data-ttu-id="80920-109">這可讓您檢視和變更連接屬性以及複寫監視器用來連接到散發者的認證。</span><span class="sxs-lookup"><span data-stu-id="80920-109">This enables you to view and change the connection properties and credentials that Replication Monitor uses to connect to the Distributor.</span></span>  
  
 <span data-ttu-id="80920-110">**自動重新整理此散發者和其發行集的狀態**</span><span class="sxs-lookup"><span data-stu-id="80920-110">**Automatically refresh the status of this Distributor and its publications**</span></span>  
 <span data-ttu-id="80920-111">選取以讓複寫監視器自動重新整理「散發者」的狀態。</span><span class="sxs-lookup"><span data-stu-id="80920-111">Select to let Replication Monitor automatically refresh the status for the Distributor.</span></span> <span data-ttu-id="80920-112">如果選取此選項，複寫監視器就會輪詢散發者，以使用 **[重新整理的頻率]** 選項所設定的輪詢間隔做為依據來取得狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="80920-112">If this option is selected, Replication Monitor polls the Distributor for status information based on the polling interval set by the **Refresh rate** option.</span></span> <span data-ttu-id="80920-113">如需複寫監視器中之重新整理的詳細資訊，請參閱＜ [Caching, Refresh, and Replication Monitor Performance](monitor/caching-refresh-and-replication-monitor-performance.md)＞。</span><span class="sxs-lookup"><span data-stu-id="80920-113">For more information about refresh in Replication Monitor, see [Caching, Refresh, and Replication Monitor Performance](monitor/caching-refresh-and-replication-monitor-performance.md).</span></span>  
  
 <span data-ttu-id="80920-114">**[重新整理的頻率]**</span><span class="sxs-lookup"><span data-stu-id="80920-114">**Refresh rate**</span></span>  
 <span data-ttu-id="80920-115">輸入一個值 (以秒為單位)，來指定複寫監視器應輪詢散發者以取得狀態的頻率。</span><span class="sxs-lookup"><span data-stu-id="80920-115">Enter a value (in seconds) to specify how frequently Replication Monitor should poll the Distributor for status.</span></span> <span data-ttu-id="80920-116">較低的值會產生較頻繁的輪詢。</span><span class="sxs-lookup"><span data-stu-id="80920-116">Lower values result in more frequent polling.</span></span> <span data-ttu-id="80920-117">如果您正在監視大量的發行者，這會影響散發者端的效能。</span><span class="sxs-lookup"><span data-stu-id="80920-117">This can affect performance at the Distributor if you are monitoring many Publishers.</span></span> <span data-ttu-id="80920-118">建議您測試自己的系統，以決定適當的值。</span><span class="sxs-lookup"><span data-stu-id="80920-118">We recommend that you test your system to determine an appropriate value.</span></span> <span data-ttu-id="80920-119">如果您在複寫監視器的任何一個詳細資料視窗中選取 **[自動重新整理]** ，也會使用 **[重新整理的頻率]** 設定。</span><span class="sxs-lookup"><span data-stu-id="80920-119">The **Refresh rate** setting is also used if you select **Auto Refresh** in any of the detail windows in Replication Monitor.</span></span>  
  
 <span data-ttu-id="80920-120">**在下列群組中顯示此散發者的所有發行者**</span><span class="sxs-lookup"><span data-stu-id="80920-120">**Show all Publishers of this Distributor in the following group**</span></span>  
 <span data-ttu-id="80920-121">從清單中選取一個發行者群組。</span><span class="sxs-lookup"><span data-stu-id="80920-121">Select a Publisher group from the list.</span></span> <span data-ttu-id="80920-122">發行者會在左窗格中的這個群組之下顯示。</span><span class="sxs-lookup"><span data-stu-id="80920-122">The Publisher is displayed under this group in the left pane.</span></span> <span data-ttu-id="80920-123">群組為您提供了組織發行者的方式，且對於複寫的運作方式沒有影響。</span><span class="sxs-lookup"><span data-stu-id="80920-123">Groups provide a way for you to organize Publishers and do not affect how replication functions.</span></span>  
  
 <span data-ttu-id="80920-124">**新增群組**</span><span class="sxs-lookup"><span data-stu-id="80920-124">**New Group**</span></span>  
 <span data-ttu-id="80920-125">按一下即可建立新的發行者群組。</span><span class="sxs-lookup"><span data-stu-id="80920-125">Click to create a new Publisher group.</span></span> <span data-ttu-id="80920-126">發行者群組為您提供了在複寫監視器內組織發行者的便利方式。</span><span class="sxs-lookup"><span data-stu-id="80920-126">A Publisher group provides a way for you to conveniently organize Publishers within Replication Monitor.</span></span> <span data-ttu-id="80920-127">群組不會影響資料的複寫，也不會影響複寫拓撲中各伺服器間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="80920-127">Groups do not affect the replication of data or the relationship among servers in a replication topology.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80920-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80920-128">See Also</span></span>  
 <span data-ttu-id="80920-129">[啟動複寫監視器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="80920-129">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 [<span data-ttu-id="80920-130">監視複寫</span><span class="sxs-lookup"><span data-stu-id="80920-130">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
