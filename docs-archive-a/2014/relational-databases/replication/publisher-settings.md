---
title: SQL Server 複寫 [發行者設定] 對話方塊 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publishersettings.f1
helpviewer_keywords:
- Publisher Settings dialog box
ms.assetid: 4fb70427-082d-4179-82a1-34b235accc43
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3a9a5ca5b0d7bfae895287708af159f3316e4474
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708170"
---
# <a name="sql-server-replication-publisher-settings-dialog-box"></a><span data-ttu-id="7fa2e-102">SQL Server 複寫 [發行者設定] 對話方塊</span><span class="sxs-lookup"><span data-stu-id="7fa2e-102">SQL Server Replication 'Publisher Settings' dialog box</span></span>
  <span data-ttu-id="7fa2e-103">**[發行者設定]** 對話方塊，可讓您針對已加入至複寫監視器之左窗格的發行者變更設定。</span><span class="sxs-lookup"><span data-stu-id="7fa2e-103">The **Publisher Settings** dialog box allows you to change settings for Publishers that have been added to the left pane in Replication Monitor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7fa2e-104">選項。</span><span class="sxs-lookup"><span data-stu-id="7fa2e-104">Options</span></span>  
 <span data-ttu-id="7fa2e-105">**發行者連接**</span><span class="sxs-lookup"><span data-stu-id="7fa2e-105">**Publisher Connection**</span></span>  
 <span data-ttu-id="7fa2e-106">按一下即可啟動 **[連接到伺服器]** 對話方塊，可讓您檢視和變更連接屬性以及複寫監視器用來連接到發行者的認證。</span><span class="sxs-lookup"><span data-stu-id="7fa2e-106">Click to launch the **Connect to Server** dialog box, which allows you to view and change the connection properties and credentials Replication Monitor uses to connect to a Publisher.</span></span>  
  
 <span data-ttu-id="7fa2e-107">**散發者連接**</span><span class="sxs-lookup"><span data-stu-id="7fa2e-107">**Distributor Connection**</span></span>  
 <span data-ttu-id="7fa2e-108">只有在發行者使用遠端散發者時才會顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="7fa2e-108">Displayed only if the Publisher uses a remote Distributor.</span></span> <span data-ttu-id="7fa2e-109">按一下即可啟動 **[連接到伺服器]** 對話方塊，可讓您檢視和變更連接屬性以及複寫監視器用來連接到遠端散發者的認證。</span><span class="sxs-lookup"><span data-stu-id="7fa2e-109">Click to launch the **Connect to Server** dialog box, which allows you to view and change the connection properties and credentials Replication Monitor uses to connect to the remote Distributor.</span></span>  
  
 <span data-ttu-id="7fa2e-110">**啟動複寫監視器時自動連接**</span><span class="sxs-lookup"><span data-stu-id="7fa2e-110">**Connect automatically when Replication Monitor starts**</span></span>  
 <span data-ttu-id="7fa2e-111">選取即可讓複寫監視器自動連接到散發者，並擷取在對話方塊頂端方格中選取之發行者的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="7fa2e-111">Select to allow Replication Monitor to automatically connect to the Distributor and retrieve status information for the Publisher selected in the grid at the top of the dialog box.</span></span> <span data-ttu-id="7fa2e-112">如果清除此核取方塊，您必須在啟動複寫監視器後手動連接：以滑鼠右鍵按一下複寫監視器之左窗格中的發行者，然後按一下 **[連接]** 。</span><span class="sxs-lookup"><span data-stu-id="7fa2e-112">If this checkbox is cleared, you must manually connect after launching Replication Monitor: right-click the Publisher in the left pane of Replication Monitor, and click **Connect**.</span></span>  
  
 <span data-ttu-id="7fa2e-113">**自動重新整理此發行者和其發行集的狀態**</span><span class="sxs-lookup"><span data-stu-id="7fa2e-113">**Automatically refresh the status of this Publisher and its publications**</span></span>  
 <span data-ttu-id="7fa2e-114">選取即可讓複寫監視器自動重新整理在對話方塊頂端方格中選取之發行者的狀態。</span><span class="sxs-lookup"><span data-stu-id="7fa2e-114">Select to allow Replication Monitor to automatically refresh status for the Publisher selected in the grid at the top of the dialog box.</span></span> <span data-ttu-id="7fa2e-115">如果選取此選項，複寫監視器就會輪詢散發者，以取得發行者和其發行集的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="7fa2e-115">If this option is selected, Replication Monitor polls the Distributor for status information on the Publisher and its publications.</span></span> <span data-ttu-id="7fa2e-116">輪詢間隔會由 **[重新整理的頻率]** 選項設定。</span><span class="sxs-lookup"><span data-stu-id="7fa2e-116">The polling interval is set by the **Refresh rate** option.</span></span> <span data-ttu-id="7fa2e-117">如需複寫監視器中之重新整理的詳細資訊，請參閱[快取、重新整理和複寫監視器效能](monitor/caching-refresh-and-replication-monitor-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="7fa2e-117">For more information on refresh in Replication Monitor, see [Caching, Refresh, and Replication Monitor Performance](monitor/caching-refresh-and-replication-monitor-performance.md).</span></span>  
  
 <span data-ttu-id="7fa2e-118">**[重新整理的頻率]**</span><span class="sxs-lookup"><span data-stu-id="7fa2e-118">**Refresh rate**</span></span>  
 <span data-ttu-id="7fa2e-119">輸入一個值 (以秒為單位)，來指定複寫監視器應輪詢散發者以取得狀態的頻率。</span><span class="sxs-lookup"><span data-stu-id="7fa2e-119">Enter a value (in seconds) to specify how frequently Replication Monitor should poll the Distributor for status.</span></span> <span data-ttu-id="7fa2e-120">較低的值會產生較頻繁的輪詢，如果您監視大量的發行者，這會影響散發者端的效能。</span><span class="sxs-lookup"><span data-stu-id="7fa2e-120">Lower values result in more frequent polling, which can affect performance at the Distributor if you are monitoring a large number of Publishers.</span></span> <span data-ttu-id="7fa2e-121">建議您測試自己的系統，以決定適當的值。</span><span class="sxs-lookup"><span data-stu-id="7fa2e-121">It is recommended that you test your system to determine an appropriate value.</span></span> <span data-ttu-id="7fa2e-122">如果您在複寫監視器的任何一個詳細資料視窗中選取 **[自動重新整理]** ，也會使用 **[重新整理的頻率]** 設定。</span><span class="sxs-lookup"><span data-stu-id="7fa2e-122">The **Refresh rate** setting is also used if you select **Auto Refresh** in any of the detail windows in Replication Monitor.</span></span>  
  
 <span data-ttu-id="7fa2e-123">**在下列群組中顯示此發行者**</span><span class="sxs-lookup"><span data-stu-id="7fa2e-123">**Show this Publisher in the following group**</span></span>  
 <span data-ttu-id="7fa2e-124">從清單中選取一個發行者群組。</span><span class="sxs-lookup"><span data-stu-id="7fa2e-124">Select a Publisher group from the list.</span></span> <span data-ttu-id="7fa2e-125">發行者會在左窗格中的這個群組之下顯示。</span><span class="sxs-lookup"><span data-stu-id="7fa2e-125">The Publisher is displayed under this group in the left pane.</span></span> <span data-ttu-id="7fa2e-126">群組提供組織發行者的一種方式，對於複寫的運作方式沒有影響。</span><span class="sxs-lookup"><span data-stu-id="7fa2e-126">Groups provide a way to organize Publishers and have no effect on how replication functions.</span></span>  
  
 <span data-ttu-id="7fa2e-127">**新增群組**</span><span class="sxs-lookup"><span data-stu-id="7fa2e-127">**New Group**</span></span>  
 <span data-ttu-id="7fa2e-128">按一下即可建立新的發行者群組。</span><span class="sxs-lookup"><span data-stu-id="7fa2e-128">Click to create a new Publisher group.</span></span> <span data-ttu-id="7fa2e-129">發行者群組提供在複寫監視器內組織發行者的一種便利方式。</span><span class="sxs-lookup"><span data-stu-id="7fa2e-129">A Publisher group provides a convenient way to organize Publishers within Replication Monitor.</span></span> <span data-ttu-id="7fa2e-130">群組不會影響資料的複寫，也不會影響複寫拓撲中各伺服器間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="7fa2e-130">Groups do not affect the replication of data or the relationship among servers in a replication topology.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fa2e-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7fa2e-131">See Also</span></span>  
 <span data-ttu-id="7fa2e-132">[啟動複寫監視器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="7fa2e-132">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 [<span data-ttu-id="7fa2e-133">監視複寫</span><span class="sxs-lookup"><span data-stu-id="7fa2e-133">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
