---
title: 記錄讀取器代理程式 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.logreaderagent.f1
helpviewer_keywords:
- Log Reader Agent dialog box
ms.assetid: 300a3c46-0e48-4334-99c0-9ee690d2ef4f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2b908e43cf97350fee2913e8cc6bab30a1bcd0dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707365"
---
# <a name="log-reader-agent"></a><span data-ttu-id="744d1-102">記錄讀取器代理程式</span><span class="sxs-lookup"><span data-stu-id="744d1-102">Log Reader Agent</span></span>
  <span data-ttu-id="744d1-103">**[記錄讀取器代理程式]** 對話方塊會顯示記錄讀取器代理程式的詳細資訊，包括狀態、記錄、參考訊息，以及任何錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="744d1-103">The **Log Reader Agent** dialog box displays detailed information on the Log Reader Agent, including status, history, informational messages, and any error messages.</span></span>  
  
## <a name="options"></a><span data-ttu-id="744d1-104">選項。</span><span class="sxs-lookup"><span data-stu-id="744d1-104">Options</span></span>  
 <span data-ttu-id="744d1-105">從 **[檢視]** 功能表選取要檢視的記錄讀取器代理程式工作階段，然後在標示為 **[記錄讀取器代理程式的工作階段]** 的方格中，選取一個特定的工作階段。</span><span class="sxs-lookup"><span data-stu-id="744d1-105">Select which Log Reader Agent sessions to view from the **View** menu, and then select a specific session in the grid labeled **Sessions of the Log Reader Agent**.</span></span> <span data-ttu-id="744d1-106">有關這個工作階段的詳細資訊，會顯示在標示為 **[所選取工作階段中的動作]** 之方格中。</span><span class="sxs-lookup"><span data-stu-id="744d1-106">Detailed information on this session is displayed in the grid labeled **Actions in the selected session**.</span></span> <span data-ttu-id="744d1-107">如果選取的工作階段結束時發生錯誤， **[所選取之工作階段的錯誤詳細資料或訊息]** 的文字區域也會顯示。</span><span class="sxs-lookup"><span data-stu-id="744d1-107">If the selected session ended in an error, the text area labeled **Error details or message of the selected session** is also displayed.</span></span>  
  
 <span data-ttu-id="744d1-108">**檢視**</span><span class="sxs-lookup"><span data-stu-id="744d1-108">**View**</span></span>  
 <span data-ttu-id="744d1-109">選取要檢視的記錄讀取器代理程式工作階段。</span><span class="sxs-lookup"><span data-stu-id="744d1-109">Select which Log Reader Agent sessions to view.</span></span> <span data-ttu-id="744d1-110">記錄讀取器代理程式通常會連續執行，因此可能只會有一個工作階段可供檢視。</span><span class="sxs-lookup"><span data-stu-id="744d1-110">The Log Reader Agent typically runs continuously, therefore there might be only one session to view.</span></span>  
  
 <span data-ttu-id="744d1-111">**狀態**</span><span class="sxs-lookup"><span data-stu-id="744d1-111">**Status**</span></span>  
 <span data-ttu-id="744d1-112">記錄讀取器代理程式的狀態。</span><span class="sxs-lookup"><span data-stu-id="744d1-112">The status of the Log Reader Agent.</span></span> <span data-ttu-id="744d1-113">下列清單顯示可能的狀態值：</span><span class="sxs-lookup"><span data-stu-id="744d1-113">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="744d1-114">錯誤</span><span class="sxs-lookup"><span data-stu-id="744d1-114">Error</span></span>  
  
-   <span data-ttu-id="744d1-115">正在重試失敗的命令</span><span class="sxs-lookup"><span data-stu-id="744d1-115">Retrying failed commands</span></span>  
  
-   <span data-ttu-id="744d1-116">未執行</span><span class="sxs-lookup"><span data-stu-id="744d1-116">Not running</span></span>  
  
-   <span data-ttu-id="744d1-117">執行中</span><span class="sxs-lookup"><span data-stu-id="744d1-117">Running</span></span>  
  
 <span data-ttu-id="744d1-118">**Start Time**</span><span class="sxs-lookup"><span data-stu-id="744d1-118">**Start Time**</span></span>  
 <span data-ttu-id="744d1-119">工作階段的開始時間。</span><span class="sxs-lookup"><span data-stu-id="744d1-119">The start time of the session.</span></span>  
  
 <span data-ttu-id="744d1-120">**結束時間**</span><span class="sxs-lookup"><span data-stu-id="744d1-120">**End Time**</span></span>  
 <span data-ttu-id="744d1-121">工作階段的結束時間。</span><span class="sxs-lookup"><span data-stu-id="744d1-121">The end time of the session.</span></span> <span data-ttu-id="744d1-122">如果代理程式未停止，則這個欄位是空的。</span><span class="sxs-lookup"><span data-stu-id="744d1-122">If the agent has not stopped, this field is empty.</span></span>  
  
 <span data-ttu-id="744d1-123">**有效期間**</span><span class="sxs-lookup"><span data-stu-id="744d1-123">**Duration**</span></span>  
 <span data-ttu-id="744d1-124">記錄讀取器代理程式已在這個工作階段執行的時間量。</span><span class="sxs-lookup"><span data-stu-id="744d1-124">The amount of time the Log Reader Agent has run in this session.</span></span> <span data-ttu-id="744d1-125">如果代理程式目前正在執行，則時間代表經過時間，如果代理程式工作階段已結束，則時間代表工作階段總共花費的時間。</span><span class="sxs-lookup"><span data-stu-id="744d1-125">The time represents elapsed time if the agent is currently running and the total time of the session if the agent session has ended.</span></span>  
  
 <span data-ttu-id="744d1-126">**錯誤訊息**</span><span class="sxs-lookup"><span data-stu-id="744d1-126">**Error Message**</span></span>  
 <span data-ttu-id="744d1-127">如果工作階段因發生錯誤而結束，這個欄位會顯示記錄讀取器代理程式所記錄的最後錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="744d1-127">If a session ended in an error, this field displays the last error message logged by the Log Reader Agent.</span></span> <span data-ttu-id="744d1-128">如果工作階段結束時沒有錯誤，這個欄位會是空白。</span><span class="sxs-lookup"><span data-stu-id="744d1-128">If a session did not end in an error, this field is blank.</span></span>  
  
 <span data-ttu-id="744d1-129">**動作訊息**</span><span class="sxs-lookup"><span data-stu-id="744d1-129">**Action Message**</span></span>  
 <span data-ttu-id="744d1-130">記錄讀取器代理程式在所選取工作階段過程中已記錄的所有參考訊息與錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="744d1-130">All informational messages and error messages that the Log Reader Agent has logged during the selected session.</span></span>  
  
 <span data-ttu-id="744d1-131">**動作時間**</span><span class="sxs-lookup"><span data-stu-id="744d1-131">**Action Time**</span></span>  
 <span data-ttu-id="744d1-132">執行 **[動作訊息]** 資料行所描述之動作的時間。</span><span class="sxs-lookup"><span data-stu-id="744d1-132">The time at which the action described in the **Action Message** column was performed.</span></span>  
  
 <span data-ttu-id="744d1-133">**[所選取之工作階段的錯誤詳細資料或訊息]**</span><span class="sxs-lookup"><span data-stu-id="744d1-133">**Error details or message of the selected session**</span></span>  
 <span data-ttu-id="744d1-134">唯有所選取工作階段在 **[狀態]** 資料行中顯示的值為 **[錯誤]** 時，才會顯示。</span><span class="sxs-lookup"><span data-stu-id="744d1-134">Displayed only if the selected session displays a value of **Error** in the **Status** column.</span></span> <span data-ttu-id="744d1-135">此文字區域會顯示詳細錯誤資訊和發生錯誤時所嘗試的命令。</span><span class="sxs-lookup"><span data-stu-id="744d1-135">This text area displays detailed error information and the command that was attempted at the time of the error.</span></span> <span data-ttu-id="744d1-136">它也會包括與錯誤相關之其他內容的連結。</span><span class="sxs-lookup"><span data-stu-id="744d1-136">It also includes links to additional content related to the error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="744d1-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="744d1-137">See Also</span></span>  
 <span data-ttu-id="744d1-138">[啟動複寫監視器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="744d1-138">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="744d1-139">[使用複寫監視器來檢視資訊及執行工作](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="744d1-139">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="744d1-140">[監視複寫](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="744d1-140">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="744d1-141">複寫代理程式概觀</span><span class="sxs-lookup"><span data-stu-id="744d1-141">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
