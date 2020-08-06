---
title: 發行集資訊、 (交易式發行集的警告 SQL Server 2005 和更新版本) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.warningsandagents.tran.f1
ms.assetid: 4d4baf1d-d0a1-4d09-bec7-137811f43f09
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cac7ab0f712fe69d3736985921d70b0ce200d474
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702702"
---
# <a name="publication-information-warnings-transactional-publication-sql-server-2005-and-later"></a><span data-ttu-id="3e6ef-102">發行集資訊，警告 (交易式發行集，SQL Server 2005 和更新的版本)</span><span class="sxs-lookup"><span data-stu-id="3e6ef-102">Publication Information, Warnings (Transactional Publication, SQL Server 2005 and Later)</span></span>
  <span data-ttu-id="3e6ef-103">執行 **和更新版本的散發者可以使用** [警告] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3e6ef-103">The **Warnings** tab is available for Distributors that are running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions.</span></span> <span data-ttu-id="3e6ef-104">**[警告]** 索引標籤可以讓您針對選取的發行集執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="3e6ef-104">The **Warnings** tab allows you to perform the following tasks for the selected publication:</span></span>  
  
-   <span data-ttu-id="3e6ef-105">啟用在複寫監視器中顯示警告。</span><span class="sxs-lookup"><span data-stu-id="3e6ef-105">Enable warnings to be displayed in Replication Monitor.</span></span>  
  
-   <span data-ttu-id="3e6ef-106">指定與警告相關聯的臨界值。</span><span class="sxs-lookup"><span data-stu-id="3e6ef-106">Specify thresholds associated with warnings.</span></span>  
  
-   <span data-ttu-id="3e6ef-107">定義與警告相關聯的警示。</span><span class="sxs-lookup"><span data-stu-id="3e6ef-107">Define alerts associated with warnings.</span></span>  
  
## <a name="warnings-thresholds-and-alerts"></a><span data-ttu-id="3e6ef-108">警告、臨界值和警示</span><span class="sxs-lookup"><span data-stu-id="3e6ef-108">Warnings, Thresholds, and Alerts</span></span>  
 <span data-ttu-id="3e6ef-109">根據預設，複寫監視器會針對未初始化的訂閱顯示警告： **[未初始化的訂閱]** 狀態會在包含訂閱資訊之頁面的 **[狀態]** 資料行中顯示為警告。</span><span class="sxs-lookup"><span data-stu-id="3e6ef-109">By default, Replication Monitor displays warnings for uninitialized subscriptions: a status of **Uninitialized subscription** is displayed as a warning in the **Status** column of pages that include subscription information.</span></span> <span data-ttu-id="3e6ef-110">針對交易式發行集，您可以指定下列其他狀況是否會造成警告：</span><span class="sxs-lookup"><span data-stu-id="3e6ef-110">For transactional publications, you can specify whether these additional conditions result in warnings:</span></span>  
  
-   <span data-ttu-id="3e6ef-111">即將發生訂閱過期。</span><span class="sxs-lookup"><span data-stu-id="3e6ef-111">Imminent subscription expiration.</span></span>  
  
     <span data-ttu-id="3e6ef-112">這會對應至 **[若訂閱將在臨界值內過期，就發出警告]** 選項。</span><span class="sxs-lookup"><span data-stu-id="3e6ef-112">This corresponds to the option **Warn if a subscription will expire within the threshold**.</span></span> <span data-ttu-id="3e6ef-113">如果達到或超出指定的臨界值，訂閱狀態會顯示為 **[即將過期/已過期]** (除非必須顯示具有更高優先權的問題)。</span><span class="sxs-lookup"><span data-stu-id="3e6ef-113">If the specified threshold is met or exceeded, the subscription status is displayed as **Expiring soon/Expired** (unless an issue with a higher priority needs to be displayed).</span></span>  
  
-   <span data-ttu-id="3e6ef-114">超過指定的延遲。</span><span class="sxs-lookup"><span data-stu-id="3e6ef-114">Exceeding the specified latency.</span></span> <span data-ttu-id="3e6ef-115">這是正在發行者端認可的交易與正在訂閱者端認可的對應交易之間經過的時間量。</span><span class="sxs-lookup"><span data-stu-id="3e6ef-115">This is the amount of time that elapses between a transaction being committed at the Publisher and the corresponding transaction being committed at the Subscriber.</span></span>  
  
     <span data-ttu-id="3e6ef-116">這會對應至 **[若延遲超過臨界值，就發出警告]** 選項。</span><span class="sxs-lookup"><span data-stu-id="3e6ef-116">This corresponds to the option **Warn if latency exceeds the threshold**.</span></span> <span data-ttu-id="3e6ef-117">如果達到或超出指定的臨界值，訂閱狀態會顯示為 **[效能嚴重不足]** (除非必須顯示更高優先權的問題)。</span><span class="sxs-lookup"><span data-stu-id="3e6ef-117">If the specified threshold is met or exceeded, the subscription status is displayed as **Performance critical** (unless an issue with a higher priority needs to be displayed).</span></span> <span data-ttu-id="3e6ef-118">臨界值顯示在包含訂閱資訊之頁面的 **[效能]** 資料行中，也可以用來提供效能評比。</span><span class="sxs-lookup"><span data-stu-id="3e6ef-118">The threshold is also used to provide a performance rating, which is displayed in the **Performance** column of pages that include subscription information.</span></span> <span data-ttu-id="3e6ef-119">效能評比是下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="3e6ef-119">The performance rating is one of the following values:</span></span>  
  
    -   <span data-ttu-id="3e6ef-120">非常好</span><span class="sxs-lookup"><span data-stu-id="3e6ef-120">Excellent</span></span>  
  
    -   <span data-ttu-id="3e6ef-121">好</span><span class="sxs-lookup"><span data-stu-id="3e6ef-121">Good</span></span>  
  
    -   <span data-ttu-id="3e6ef-122">普通</span><span class="sxs-lookup"><span data-stu-id="3e6ef-122">Fair</span></span>  
  
    -   <span data-ttu-id="3e6ef-123">差</span><span class="sxs-lookup"><span data-stu-id="3e6ef-123">Poor</span></span>  
  
    -   <span data-ttu-id="3e6ef-124">重要</span><span class="sxs-lookup"><span data-stu-id="3e6ef-124">Critical</span></span>  
  
 <span data-ttu-id="3e6ef-125">您啟用警告時，也會設定臨界值。</span><span class="sxs-lookup"><span data-stu-id="3e6ef-125">When you enable a warning, you also set a threshold.</span></span> <span data-ttu-id="3e6ef-126">例如，若您啟用警告 **[若延遲超過臨界值，就發出警告]**，請選取發行者端認可交易和訂閱者端認可交易之間允許的時間。</span><span class="sxs-lookup"><span data-stu-id="3e6ef-126">For example, if you enable the warning **Warn if latency exceeds the threshold**, select the amount of time allowable between a transaction being committed at the Publisher and the transaction being committed at the Subscriber.</span></span>  
  
 <span data-ttu-id="3e6ef-127">除了在複寫監視器顯示警告外，達到臨界值也會觸發警示。</span><span class="sxs-lookup"><span data-stu-id="3e6ef-127">In addition to displaying a warning in Replication Monitor, reaching a threshold can also trigger an alert.</span></span> <span data-ttu-id="3e6ef-128">定義警示的方式，是按一下 **[設定警示]** ，並在 **[設定複寫警示]** 對話方塊中提供資訊。</span><span class="sxs-lookup"><span data-stu-id="3e6ef-128">Alerts are defined by clicking **Configure Alerts** and providing information in the **Configure Replication Alerts** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3e6ef-129">選項。</span><span class="sxs-lookup"><span data-stu-id="3e6ef-129">Options</span></span>  
 <span data-ttu-id="3e6ef-130">**已啟用**</span><span class="sxs-lookup"><span data-stu-id="3e6ef-130">**Enabled**</span></span>  
 <span data-ttu-id="3e6ef-131">選取以啟用警告，並指定臨界值。</span><span class="sxs-lookup"><span data-stu-id="3e6ef-131">Select to enable a warning and specify a threshold.</span></span>  
  
 <span data-ttu-id="3e6ef-132">**警告**</span><span class="sxs-lookup"><span data-stu-id="3e6ef-132">**Warning**</span></span>  
 <span data-ttu-id="3e6ef-133">與臨界值相關聯之警告的描述。</span><span class="sxs-lookup"><span data-stu-id="3e6ef-133">A description of the warning associated with a threshold.</span></span>  
  
 <span data-ttu-id="3e6ef-134">**閾值**</span><span class="sxs-lookup"><span data-stu-id="3e6ef-134">**Threshold**</span></span>  
 <span data-ttu-id="3e6ef-135">指定臨界值的值。</span><span class="sxs-lookup"><span data-stu-id="3e6ef-135">Specify a value for the threshold.</span></span>  
  
 <span data-ttu-id="3e6ef-136">**設定警示**</span><span class="sxs-lookup"><span data-stu-id="3e6ef-136">**Configure Alerts**</span></span>  
 <span data-ttu-id="3e6ef-137">在 **[警告]** 方格中選取一個資料列，然後按一下 **[設定警示]** 以啟動 **[設定複寫警示]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3e6ef-137">Select a row in the **Warnings** grid, and click **Configure Alerts** to launch the **Configure Replication Alerts** dialog box.</span></span> <span data-ttu-id="3e6ef-138">此對話方塊可以讓您定義與選取的臨界值和警告相關聯的警示。</span><span class="sxs-lookup"><span data-stu-id="3e6ef-138">The dialog box allows you to define an alert, which is associated with the selected threshold and warning.</span></span>  
  
 <span data-ttu-id="3e6ef-139">**捨棄變更**</span><span class="sxs-lookup"><span data-stu-id="3e6ef-139">**Discard Changes**</span></span>  
 <span data-ttu-id="3e6ef-140">按一下即可捨棄對警告與臨界值所做的任何變更。</span><span class="sxs-lookup"><span data-stu-id="3e6ef-140">Click to discard any changes to warnings and thresholds.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3e6ef-141"> 按一下 **[捨棄變更]** 不會影響在 **[設定複寫警示]** 對話方塊中定義的警示。</span><span class="sxs-lookup"><span data-stu-id="3e6ef-141">Clicking **Discard Changes** does not affect alerts defined in the **Configure Replication Alerts** dialog box.</span></span>  
  
 <span data-ttu-id="3e6ef-142">**儲存變更**</span><span class="sxs-lookup"><span data-stu-id="3e6ef-142">**Save Changes**</span></span>  
 <span data-ttu-id="3e6ef-143">按一下即可儲存對警告與臨界值所做的任何變更。</span><span class="sxs-lookup"><span data-stu-id="3e6ef-143">Click to save any changes to warnings and thresholds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e6ef-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e6ef-144">See Also</span></span>  
 <span data-ttu-id="3e6ef-145">[啟動複寫監視器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="3e6ef-145">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="3e6ef-146">[使用複寫監視器來檢視資訊及執行工作](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="3e6ef-146">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="3e6ef-147">[使用複寫監視器監視效能](monitor/monitor-performance-with-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="3e6ef-147">[Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) </span></span>  
 <span data-ttu-id="3e6ef-148">[監視複寫](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="3e6ef-148">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="3e6ef-149">在複寫監視器中設定閾值和警告</span><span class="sxs-lookup"><span data-stu-id="3e6ef-149">Set Thresholds and Warnings in Replication Monitor</span></span>](monitor/set-thresholds-and-warnings-in-replication-monitor.md)  
  
  
