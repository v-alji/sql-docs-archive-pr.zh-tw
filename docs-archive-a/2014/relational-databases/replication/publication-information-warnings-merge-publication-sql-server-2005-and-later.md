---
title: 發行集資訊、 (合併式發行集的警告 SQL Server 2005 和更新版本) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.warningsandagents.merge.f1
ms.assetid: 9bef3565-5f13-42ac-8723-ebe55b0c11e6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 75f58a4cd9bd84791acf7fd9d28147ef3bbd6232
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596657"
---
# <a name="publication-information-warnings-merge-publication-sql-server-2005-and-later"></a><span data-ttu-id="d2ffa-102">發行集資訊，警告 (合併式發行集，SQL Server 2005 和更新的版本)</span><span class="sxs-lookup"><span data-stu-id="d2ffa-102">Publication Information, Warnings (Merge Publication, SQL Server 2005 and Later)</span></span>
  <span data-ttu-id="d2ffa-103">執行 **和更新版本的散發者可以使用** [警告] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d2ffa-103">The **Warnings** tab is available for Distributors that are running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions.</span></span> <span data-ttu-id="d2ffa-104">**[警告]** 索引標籤可以讓您針對選取的發行集執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="d2ffa-104">The **Warnings** tab allows you to perform the following tasks for the selected publication:</span></span>  
  
-   <span data-ttu-id="d2ffa-105">啟用警告。</span><span class="sxs-lookup"><span data-stu-id="d2ffa-105">Enable warnings.</span></span>  
  
-   <span data-ttu-id="d2ffa-106">指定與警告相關聯的臨界值。</span><span class="sxs-lookup"><span data-stu-id="d2ffa-106">Specify thresholds associated with warnings.</span></span>  
  
-   <span data-ttu-id="d2ffa-107">定義與警告相關聯的警示。</span><span class="sxs-lookup"><span data-stu-id="d2ffa-107">Define alerts associated with warnings.</span></span>  
  
## <a name="warnings-thresholds-and-alerts"></a><span data-ttu-id="d2ffa-108">警告、臨界值和警示</span><span class="sxs-lookup"><span data-stu-id="d2ffa-108">Warnings, Thresholds, and Alerts</span></span>  
 <span data-ttu-id="d2ffa-109">根據預設，複寫監視器會針對未初始化的訂閱顯示警告： **[未初始化的訂閱]** 狀態會在包含訂閱資訊之頁面的 **[狀態]** 資料行中顯示為警告。</span><span class="sxs-lookup"><span data-stu-id="d2ffa-109">By default, Replication Monitor displays warnings for uninitialized subscriptions: a status of **Uninitialized subscription** is displayed as a warning in the **Status** column of pages that include subscription information.</span></span> <span data-ttu-id="d2ffa-110">針對合併式發行集，您可以指定這些其他的條件是否會導致警告：</span><span class="sxs-lookup"><span data-stu-id="d2ffa-110">For merge publications, you can specify whether these additional conditions result in warnings:</span></span>  
  
-   <span data-ttu-id="d2ffa-111">即將發生訂閱過期。</span><span class="sxs-lookup"><span data-stu-id="d2ffa-111">Imminent subscription expiration.</span></span>  
  
     <span data-ttu-id="d2ffa-112">這會對應至 **[若訂閱將在臨界值內過期，就發出警告]** 選項。</span><span class="sxs-lookup"><span data-stu-id="d2ffa-112">This corresponds to the option **Warn if a subscription will expire within the threshold**.</span></span> <span data-ttu-id="d2ffa-113">如果達到或超出指定的臨界值，訂閱狀態會顯示為 **[即將過期/已過期]** (除非必須顯示具有更高優先權的問題)。</span><span class="sxs-lookup"><span data-stu-id="d2ffa-113">If the specified threshold is met or exceeded, the subscription status is displayed as **Expiring soon/Expired** (unless an issue with a higher priority needs to be displayed).</span></span>  
  
-   <span data-ttu-id="d2ffa-114">超過指定的同步處理時間。</span><span class="sxs-lookup"><span data-stu-id="d2ffa-114">Exceeding the specified synchronization time.</span></span>  
  
     <span data-ttu-id="d2ffa-115">這會對應至 **[若撥號連接的合併長度超過臨界值，就發出警告]** 和 **[若 LAN 連接的合併長度超過臨界值，就發出警告]** 選項。</span><span class="sxs-lookup"><span data-stu-id="d2ffa-115">This corresponds to the options **Warn if a merge length for dialup connections exceeds the threshold** and **Warn if a merge length for LAN connections exceeds the threshold**.</span></span> <span data-ttu-id="d2ffa-116">可以設定這兩個臨界值，但是進行同步處理期間只會使用一個。</span><span class="sxs-lookup"><span data-stu-id="d2ffa-116">Both of these thresholds can be set, but only one is used during a given synchronization.</span></span> <span data-ttu-id="d2ffa-117">合併代理程式會根據連接類型套用適當的臨界值。</span><span class="sxs-lookup"><span data-stu-id="d2ffa-117">The Merge Agent applies the appropriate threshold based on the connection type.</span></span>  
  
     <span data-ttu-id="d2ffa-118">如果指定的臨界值符合或超過，則訂閱狀態會顯示為 **[長期執行合併]** (除非需要顯示擁有更高優先權的問題)。</span><span class="sxs-lookup"><span data-stu-id="d2ffa-118">If the specified threshold is met or exceeded, the subscription status is displayed as **Long-running merge** (unless an issue with a higher priority needs to be displayed).</span></span>  
  
-   <span data-ttu-id="d2ffa-119">在給定時間內處理的資料列數達不到指定數目。</span><span class="sxs-lookup"><span data-stu-id="d2ffa-119">Falling short of processing the specified number of rows in a given amount of time.</span></span>  
  
     <span data-ttu-id="d2ffa-120">這會對應至 **[若撥號連接的每秒的合併資料列少於臨界值，就發出警告]** 和 **[若 LAN 連接的合併長度超過臨界值，就發出警告]** 選項。</span><span class="sxs-lookup"><span data-stu-id="d2ffa-120">This corresponds to the options **Warn if rows merged per second for dialup connections is less than the threshold** and **Warn if a merge length for LAN connections exceeds the threshold**.</span></span> <span data-ttu-id="d2ffa-121">可以設定這兩個臨界值，但是進行同步處理期間只會使用一個。</span><span class="sxs-lookup"><span data-stu-id="d2ffa-121">Both of these thresholds can be set, but only one is used during a given synchronization.</span></span> <span data-ttu-id="d2ffa-122">合併代理程式會根據連接類型套用適當的臨界值。</span><span class="sxs-lookup"><span data-stu-id="d2ffa-122">The Merge Agent applies the appropriate threshold based on the connection type.</span></span>  
  
     <span data-ttu-id="d2ffa-123">如果達到或超出指定的臨界值，訂閱狀態會顯示為 **[效能嚴重不足]** (除非必須顯示更高優先權的問題)。</span><span class="sxs-lookup"><span data-stu-id="d2ffa-123">If the specified threshold is met or exceeded, the subscription status is displayed as **Performance critical** (unless an issue with a higher priority needs to be displayed).</span></span>  
  
 <span data-ttu-id="d2ffa-124">您啟用警告時，也會設定臨界值。</span><span class="sxs-lookup"><span data-stu-id="d2ffa-124">When you enable a warning, you also set a threshold.</span></span> <span data-ttu-id="d2ffa-125">例如，若您啟用警告 **[若 LAN 連接的合併長度超過臨界值，就發出警告]**，請設定合併同步允許的時間長度上限。</span><span class="sxs-lookup"><span data-stu-id="d2ffa-125">For example, if you enable the warning **Warn if a merge length for LAN connections exceeds the threshold**, set the maximum allowable length of time for a merge synchronization.</span></span>  
  
 <span data-ttu-id="d2ffa-126">除了在複寫監視器顯示警告外，達到臨界值也會觸發警示。</span><span class="sxs-lookup"><span data-stu-id="d2ffa-126">In addition to displaying a warning in Replication Monitor, reaching a threshold can also trigger an alert.</span></span> <span data-ttu-id="d2ffa-127">定義警示的方式，是按一下 **[設定警示]** ，並在 **[設定複寫警示]** 對話方塊中提供資訊。</span><span class="sxs-lookup"><span data-stu-id="d2ffa-127">Alerts are defined by clicking **Configure Alerts** and providing information in the **Configure Replication Alerts** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d2ffa-128">選項。</span><span class="sxs-lookup"><span data-stu-id="d2ffa-128">Options</span></span>  
 <span data-ttu-id="d2ffa-129">**已啟用**</span><span class="sxs-lookup"><span data-stu-id="d2ffa-129">**Enabled**</span></span>  
 <span data-ttu-id="d2ffa-130">選取以啟用警告，並指定臨界值。</span><span class="sxs-lookup"><span data-stu-id="d2ffa-130">Select to enable a warning and specify a threshold.</span></span>  
  
 <span data-ttu-id="d2ffa-131">**警示**</span><span class="sxs-lookup"><span data-stu-id="d2ffa-131">**Alert**</span></span>  
 <span data-ttu-id="d2ffa-132">選取以啟用所指複寫警告的警示設定。</span><span class="sxs-lookup"><span data-stu-id="d2ffa-132">Select to enable the alert setting for a given replication warning.</span></span>  
  
 <span data-ttu-id="d2ffa-133">**警告**</span><span class="sxs-lookup"><span data-stu-id="d2ffa-133">**Warning**</span></span>  
 <span data-ttu-id="d2ffa-134">與臨界值相關聯之警告的描述。</span><span class="sxs-lookup"><span data-stu-id="d2ffa-134">A description of the warning associated with a threshold.</span></span>  
  
 <span data-ttu-id="d2ffa-135">**閾值**</span><span class="sxs-lookup"><span data-stu-id="d2ffa-135">**Threshold**</span></span>  
 <span data-ttu-id="d2ffa-136">指定臨界值的值。</span><span class="sxs-lookup"><span data-stu-id="d2ffa-136">Specify a value for the threshold.</span></span>  
  
 <span data-ttu-id="d2ffa-137">**設定警示**</span><span class="sxs-lookup"><span data-stu-id="d2ffa-137">**Configure Alerts**</span></span>  
 <span data-ttu-id="d2ffa-138">在 **[警告]** 方格中選取一個資料列，然後按一下 **[設定警示]** 以啟動 **[設定複寫警示]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d2ffa-138">Select a row in the **Warnings** grid, and click **Configure Alerts** to launch the **Configure Replication Alerts** dialog box.</span></span> <span data-ttu-id="d2ffa-139">此對話方塊可以讓您定義與選取的臨界值和警告相關聯的警示。</span><span class="sxs-lookup"><span data-stu-id="d2ffa-139">The dialog box allows you to define an alert, which is associated with the selected threshold and warning.</span></span>  
  
 <span data-ttu-id="d2ffa-140">**捨棄變更**</span><span class="sxs-lookup"><span data-stu-id="d2ffa-140">**Discard Changes**</span></span>  
 <span data-ttu-id="d2ffa-141">按一下即可捨棄對警告與臨界值所做的任何變更。</span><span class="sxs-lookup"><span data-stu-id="d2ffa-141">Click to discard any changes to warnings and thresholds.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d2ffa-142"> 按一下 **[捨棄變更]** 不會影響在 **[設定複寫警示]** 對話方塊中定義的警示。</span><span class="sxs-lookup"><span data-stu-id="d2ffa-142">Clicking **Discard Changes** does not affect alerts defined in the **Configure Replication Alerts** dialog box.</span></span>  
  
 <span data-ttu-id="d2ffa-143">**儲存變更**</span><span class="sxs-lookup"><span data-stu-id="d2ffa-143">**Save Changes**</span></span>  
 <span data-ttu-id="d2ffa-144">按一下即可儲存對警告與臨界值所做的任何變更。</span><span class="sxs-lookup"><span data-stu-id="d2ffa-144">Click to save any changes to warnings and thresholds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2ffa-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2ffa-145">See Also</span></span>  
 <span data-ttu-id="d2ffa-146">[啟動複寫監視器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="d2ffa-146">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="d2ffa-147">[使用複寫監視器來檢視資訊及執行工作](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="d2ffa-147">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="d2ffa-148">[使用複寫監視器監視效能](monitor/monitor-performance-with-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="d2ffa-148">[Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) </span></span>  
 <span data-ttu-id="d2ffa-149">[監視複寫](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="d2ffa-149">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="d2ffa-150">在複寫監視器中設定閾值和警告</span><span class="sxs-lookup"><span data-stu-id="d2ffa-150">Set Thresholds and Warnings in Replication Monitor</span></span>](monitor/set-thresholds-and-warnings-in-replication-monitor.md)  
  
  
