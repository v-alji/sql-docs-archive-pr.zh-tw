---
title: 訂閱，散發者到訂閱者記錄 (快照式訂閱) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.subscription.pubtodist.snapshot.f1
ms.assetid: d3575964-f287-4bcf-8d2e-f81a33141b25
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fe894e23e7ad7fef9c328334740eff73164130a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708157"
---
# <a name="subscription-distributor-to-subscriber-history-snapshot-subscription"></a><span data-ttu-id="eb763-102">訂閱，散發者到訂閱者記錄 (快照式訂閱)</span><span class="sxs-lookup"><span data-stu-id="eb763-102">Subscription, Distributor to Subscriber History (Snapshot Subscription)</span></span>
  <span data-ttu-id="eb763-103"> [散發者到訂閱者記錄\]\*\*\** 索引標籤會顯示散發代理程式的詳細資訊，包括狀態、記錄、資訊訊息及任何錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="eb763-103">The **Distributor to Subscriber History** tab displays detailed information on the Distribution Agent, including status, history, informational messages, and any error messages.</span></span>  
  
## <a name="options"></a><span data-ttu-id="eb763-104">選項</span><span class="sxs-lookup"><span data-stu-id="eb763-104">Options</span></span>  
 <span data-ttu-id="eb763-105">從 **[檢視]** 功能表中選取要檢視的散發代理程式工作階段，再於 **[散發代理程式的工作階段]** 的方格中選取特定的工作階段。</span><span class="sxs-lookup"><span data-stu-id="eb763-105">Select which Distribution Agent sessions to view from the **View** menu, and then select a specific session in the grid labeled **Sessions of the Distribution Agent**.</span></span> <span data-ttu-id="eb763-106">有關這個工作階段的詳細資訊，會顯示在標示為 **[所選取工作階段中的動作]** 之方格中。</span><span class="sxs-lookup"><span data-stu-id="eb763-106">Detailed information on this session is displayed in the grid labeled **Actions in the selected session**.</span></span> <span data-ttu-id="eb763-107">如果選取的工作階段結束時發生錯誤， **[所選取之工作階段的錯誤詳細資料或訊息]** 的文字區域也會顯示。</span><span class="sxs-lookup"><span data-stu-id="eb763-107">If the selected session ended in an error, the text area labeled **Error details or message of the selected session** is also displayed.</span></span>  
  
 <span data-ttu-id="eb763-108">**檢視**</span><span class="sxs-lookup"><span data-stu-id="eb763-108">**View**</span></span>  
 <span data-ttu-id="eb763-109">選取要檢視的散發代理程式工作階段。</span><span class="sxs-lookup"><span data-stu-id="eb763-109">Select which Distribution Agent sessions to view.</span></span>  
  
 <span data-ttu-id="eb763-110">**狀態**</span><span class="sxs-lookup"><span data-stu-id="eb763-110">**Status**</span></span>  
 <span data-ttu-id="eb763-111">散發代理程式的狀態。</span><span class="sxs-lookup"><span data-stu-id="eb763-111">The status of the Distribution Agent.</span></span> <span data-ttu-id="eb763-112">下列清單顯示可能的狀態值：</span><span class="sxs-lookup"><span data-stu-id="eb763-112">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="eb763-113">錯誤</span><span class="sxs-lookup"><span data-stu-id="eb763-113">Error</span></span>  
  
-   <span data-ttu-id="eb763-114">Completed</span><span class="sxs-lookup"><span data-stu-id="eb763-114">Completed</span></span>  
  
-   <span data-ttu-id="eb763-115">正在重試</span><span class="sxs-lookup"><span data-stu-id="eb763-115">Retrying</span></span>  
  
-   <span data-ttu-id="eb763-116">執行中</span><span class="sxs-lookup"><span data-stu-id="eb763-116">Running</span></span>  
  
 <span data-ttu-id="eb763-117">**開始時間**</span><span class="sxs-lookup"><span data-stu-id="eb763-117">**Start Time**</span></span>  
 <span data-ttu-id="eb763-118">工作階段的開始時間。</span><span class="sxs-lookup"><span data-stu-id="eb763-118">The start time of the session.</span></span>  
  
 <span data-ttu-id="eb763-119">**結束時間**</span><span class="sxs-lookup"><span data-stu-id="eb763-119">**End Time**</span></span>  
 <span data-ttu-id="eb763-120">工作階段的結束時間。</span><span class="sxs-lookup"><span data-stu-id="eb763-120">The end time of the session.</span></span> <span data-ttu-id="eb763-121">如果代理程式未停止，則這個欄位是空的。</span><span class="sxs-lookup"><span data-stu-id="eb763-121">If the agent has not stopped, this field is empty.</span></span>  
  
 <span data-ttu-id="eb763-122">**有效期間**</span><span class="sxs-lookup"><span data-stu-id="eb763-122">**Duration**</span></span>  
 <span data-ttu-id="eb763-123">散發代理程式在這個工作階段中執行的時間量。</span><span class="sxs-lookup"><span data-stu-id="eb763-123">The amount of time the Distribution Agent has run in this session.</span></span> <span data-ttu-id="eb763-124">如果代理程式目前正在執行，則時間代表經過時間，如果代理程式工作階段已結束，則時間代表工作階段總共花費的時間。</span><span class="sxs-lookup"><span data-stu-id="eb763-124">The time represents elapsed time if the agent is currently running and the total time of the session if the agent session had ended.</span></span>  
  
 <span data-ttu-id="eb763-125">**錯誤訊息**</span><span class="sxs-lookup"><span data-stu-id="eb763-125">**Error Message**</span></span>  
 <span data-ttu-id="eb763-126">如果工作階段結束時發生錯誤，這個欄位會顯示散發代理程式記錄的最後一個錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="eb763-126">If a session ended in an error, this field displays the last error message logged by the Distribution Agent.</span></span> <span data-ttu-id="eb763-127">如果工作階段結束時沒有錯誤，這個欄位會是空白。</span><span class="sxs-lookup"><span data-stu-id="eb763-127">If a session did not end in an error, this field is blank.</span></span>  
  
 <span data-ttu-id="eb763-128">**動作訊息**</span><span class="sxs-lookup"><span data-stu-id="eb763-128">**Action Message**</span></span>  
 <span data-ttu-id="eb763-129">散發代理程式在所選取工作階段期間，記錄的所有參考訊息和錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="eb763-129">All informational messages and error messages that the Distribution Agent has logged during the selected session.</span></span>  
  
 <span data-ttu-id="eb763-130">**動作時間**</span><span class="sxs-lookup"><span data-stu-id="eb763-130">**Action Time**</span></span>  
 <span data-ttu-id="eb763-131">執行 **[動作訊息]** 資料行所描述之動作的時間。</span><span class="sxs-lookup"><span data-stu-id="eb763-131">The time at which the action described in the **Action Message** column was performed.</span></span>  
  
 <span data-ttu-id="eb763-132">**[所選取之工作階段的錯誤詳細資料或訊息]**</span><span class="sxs-lookup"><span data-stu-id="eb763-132">**Error details or message of the selected session**</span></span>  
 <span data-ttu-id="eb763-133">唯有所選取工作階段在 **[狀態]** 資料行中顯示的值為 **[錯誤]** 時，才會顯示。</span><span class="sxs-lookup"><span data-stu-id="eb763-133">Displayed only if the selected session displays a value of **Error** in the **Status** column.</span></span> <span data-ttu-id="eb763-134">此文字區域會顯示詳細錯誤資訊和發生錯誤時所嘗試的命令。</span><span class="sxs-lookup"><span data-stu-id="eb763-134">This text area displays detailed error information and the command that was attempted at the time of the error.</span></span> <span data-ttu-id="eb763-135">它也會包括與錯誤相關之其他內容的連結。</span><span class="sxs-lookup"><span data-stu-id="eb763-135">It also includes links to additional content related to the error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb763-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb763-136">See Also</span></span>  
 <span data-ttu-id="eb763-137">[啟動複寫監視器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="eb763-137">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="eb763-138">[使用複寫監視器來檢視資訊及執行工作](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="eb763-138">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="eb763-139">[監視複寫](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="eb763-139">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="eb763-140">複寫代理程式概觀</span><span class="sxs-lookup"><span data-stu-id="eb763-140">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
