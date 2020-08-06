---
title: 快照集代理程式 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.snapshotagent.f1
helpviewer_keywords:
- Snapshot Agent dialog box
ms.assetid: b715e621-2cd5-4a15-8f58-a341aa8ef5e4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 925f2d3841b5dded6c8504a4a05dc60e61024161
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606743"
---
# <a name="snapshot-agent"></a><span data-ttu-id="a97f7-102">快照集代理程式</span><span class="sxs-lookup"><span data-stu-id="a97f7-102">Snapshot Agent</span></span>
  <span data-ttu-id="a97f7-103">**[快照集代理程式]** 對話方塊會顯示快照集代理程式的詳細資訊，包括狀態、記錄、參考用訊息以及任何錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="a97f7-103">The **Snapshot Agent** dialog box displays detailed information on the Snapshot Agent, including status, history, informational messages, and any error messages.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a97f7-104">選項。</span><span class="sxs-lookup"><span data-stu-id="a97f7-104">Options</span></span>  
 <span data-ttu-id="a97f7-105">從 **[檢視]** 功能表選取要檢視的快照集代理程式工作階段，然後在標示為 **[快照集代理程式的工作階段]** 的方格中選取特定工作階段。</span><span class="sxs-lookup"><span data-stu-id="a97f7-105">Select which Snapshot Agent sessions to view from the **View** menu, and then select a specific session in the grid labeled **Sessions of the Snapshot Agent**.</span></span> <span data-ttu-id="a97f7-106">有關這個工作階段的詳細資訊，會顯示在標示為 **[所選取工作階段中的動作]** 之方格中。</span><span class="sxs-lookup"><span data-stu-id="a97f7-106">Detailed information on this session is displayed in the grid labeled **Actions in the selected session**.</span></span> <span data-ttu-id="a97f7-107">如果選取的工作階段結束時發生錯誤， **[所選取之工作階段的錯誤詳細資料或訊息]** 的文字區域也會顯示。</span><span class="sxs-lookup"><span data-stu-id="a97f7-107">If the selected session ended in an error, the text area labeled **Error details or message of the selected session** is also displayed.</span></span>  
  
 <span data-ttu-id="a97f7-108">**檢視**</span><span class="sxs-lookup"><span data-stu-id="a97f7-108">**View**</span></span>  
 <span data-ttu-id="a97f7-109">選取要檢視的快照集代理程式工作階段。</span><span class="sxs-lookup"><span data-stu-id="a97f7-109">Select which Snapshot Agent sessions to view.</span></span>  
  
 <span data-ttu-id="a97f7-110">**狀態**</span><span class="sxs-lookup"><span data-stu-id="a97f7-110">**Status**</span></span>  
 <span data-ttu-id="a97f7-111">快照集代理程式的狀態。</span><span class="sxs-lookup"><span data-stu-id="a97f7-111">The status of the Snapshot Agent.</span></span> <span data-ttu-id="a97f7-112">下列清單顯示可能的狀態值：</span><span class="sxs-lookup"><span data-stu-id="a97f7-112">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="a97f7-113">錯誤</span><span class="sxs-lookup"><span data-stu-id="a97f7-113">Error</span></span>  
  
-   <span data-ttu-id="a97f7-114">正在重試失敗的命令</span><span class="sxs-lookup"><span data-stu-id="a97f7-114">Retrying failed commands</span></span>  
  
-   <span data-ttu-id="a97f7-115">未執行</span><span class="sxs-lookup"><span data-stu-id="a97f7-115">Not running</span></span>  
  
-   <span data-ttu-id="a97f7-116">Completed</span><span class="sxs-lookup"><span data-stu-id="a97f7-116">Completed</span></span>  
  
 <span data-ttu-id="a97f7-117">**Start Time**</span><span class="sxs-lookup"><span data-stu-id="a97f7-117">**Start Time**</span></span>  
 <span data-ttu-id="a97f7-118">工作階段的開始時間。</span><span class="sxs-lookup"><span data-stu-id="a97f7-118">The start time of the session.</span></span>  
  
 <span data-ttu-id="a97f7-119">**結束時間**</span><span class="sxs-lookup"><span data-stu-id="a97f7-119">**End Time**</span></span>  
 <span data-ttu-id="a97f7-120">工作階段的結束時間。</span><span class="sxs-lookup"><span data-stu-id="a97f7-120">The end time of the session.</span></span> <span data-ttu-id="a97f7-121">如果代理程式未停止，則這個欄位是空的。</span><span class="sxs-lookup"><span data-stu-id="a97f7-121">If the agent has not stopped, this field is empty.</span></span>  
  
 <span data-ttu-id="a97f7-122">**有效期間**</span><span class="sxs-lookup"><span data-stu-id="a97f7-122">**Duration**</span></span>  
 <span data-ttu-id="a97f7-123">已經在此工作階段中執行快照集代理程式的時間量。</span><span class="sxs-lookup"><span data-stu-id="a97f7-123">The amount of time the Snapshot Agent has run in this session.</span></span> <span data-ttu-id="a97f7-124">如果代理程式目前正在執行，則時間代表經過時間，如果代理程式工作階段已結束，則時間代表工作階段總共花費的時間。</span><span class="sxs-lookup"><span data-stu-id="a97f7-124">The time represents elapsed time if the agent is currently running and the total time of the session if the agent session has ended.</span></span>  
  
 <span data-ttu-id="a97f7-125">**錯誤訊息**</span><span class="sxs-lookup"><span data-stu-id="a97f7-125">**Error Message**</span></span>  
 <span data-ttu-id="a97f7-126">如果工作階段以錯誤結束，則此欄位會顯示快照集代理程式記錄的最後一個錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="a97f7-126">If a session ended in an error, this field displays the last error message logged by the Snapshot Agent.</span></span> <span data-ttu-id="a97f7-127">如果工作階段結束時沒有錯誤，這個欄位會是空白。</span><span class="sxs-lookup"><span data-stu-id="a97f7-127">If a session did not end in an error, this field is blank.</span></span>  
  
 <span data-ttu-id="a97f7-128">**動作訊息**</span><span class="sxs-lookup"><span data-stu-id="a97f7-128">**Action Message**</span></span>  
 <span data-ttu-id="a97f7-129">在選取的工作階段期間，快照集代理程式已經記錄的所有參考用訊息與錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="a97f7-129">All informational messages and error messages that the Snapshot Agent has logged during the selected session.</span></span>  
  
 <span data-ttu-id="a97f7-130">**動作時間**</span><span class="sxs-lookup"><span data-stu-id="a97f7-130">**Action Time**</span></span>  
 <span data-ttu-id="a97f7-131">執行 **[動作訊息]** 資料行所描述之動作的時間。</span><span class="sxs-lookup"><span data-stu-id="a97f7-131">The time at which the action described in the **Action Message** column was performed.</span></span>  
  
 <span data-ttu-id="a97f7-132">**[所選取之工作階段的錯誤詳細資料或訊息]**</span><span class="sxs-lookup"><span data-stu-id="a97f7-132">**Error details or message of the selected session**</span></span>  
 <span data-ttu-id="a97f7-133">只有當所選取工作階段在 **[狀態]** 資料行中顯示的值為 **[錯誤]** 時，才會顯示這個選項。</span><span class="sxs-lookup"><span data-stu-id="a97f7-133">Is displayed only if the selected session displays a value of **Error** in the **Status** column.</span></span> <span data-ttu-id="a97f7-134">此文字區域會顯示詳細錯誤資訊和發生錯誤時所嘗試的命令。</span><span class="sxs-lookup"><span data-stu-id="a97f7-134">This text area displays detailed error information and the command that was attempted at the time of the error.</span></span> <span data-ttu-id="a97f7-135">它也會包括與錯誤相關之其他內容的連結。</span><span class="sxs-lookup"><span data-stu-id="a97f7-135">It also includes links to additional content related to the error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a97f7-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a97f7-136">See Also</span></span>  
 <span data-ttu-id="a97f7-137">[啟動複寫監視器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="a97f7-137">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="a97f7-138">[使用複寫監視器來檢視資訊及執行工作](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="a97f7-138">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="a97f7-139">[監視複寫](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="a97f7-139">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="a97f7-140">複寫代理程式概觀</span><span class="sxs-lookup"><span data-stu-id="a97f7-140">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
