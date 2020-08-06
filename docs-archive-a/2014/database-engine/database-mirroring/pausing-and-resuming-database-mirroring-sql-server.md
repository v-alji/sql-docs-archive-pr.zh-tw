---
title: 暫停與繼續資料庫鏡像 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- sessions [SQL Server], database mirroring
- resuming database mirroring
- database mirroring [SQL Server], pausing
- database mirroring [SQL Server], resuming
- pausing database mirroring
ms.assetid: c67802c6-ee8c-4cbd-a6d4-f7b80413a4ab
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8c231876b11303992e0e3300c9cb73c0cf53b3af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701857"
---
# <a name="pausing-and-resuming-database-mirroring-sql-server"></a><span data-ttu-id="32efc-102">暫停與繼續資料庫鏡像 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="32efc-102">Pausing and Resuming Database Mirroring (SQL Server)</span></span>
  <span data-ttu-id="32efc-103">資料庫擁有者隨時都可以先暫停資料庫鏡像工作階段，稍後再繼續。</span><span class="sxs-lookup"><span data-stu-id="32efc-103">The database owner can pause and later resume a database mirroring session at any time.</span></span> <span data-ttu-id="32efc-104">暫停會保留工作階段狀態，同時暫停鏡像。</span><span class="sxs-lookup"><span data-stu-id="32efc-104">Pausing preserves the session state while suspending mirroring.</span></span> <span data-ttu-id="32efc-105">發生瓶頸時，暫停可能會對改進主體伺服器的效能有所幫助。</span><span class="sxs-lookup"><span data-stu-id="32efc-105">During bottlenecks, pausing might be useful to improve performance on the principal server.</span></span>  
  
 <span data-ttu-id="32efc-106">工作階段暫停時，主體資料庫仍然可以使用。</span><span class="sxs-lookup"><span data-stu-id="32efc-106">When a session is paused, the principal database remains available.</span></span> <span data-ttu-id="32efc-107">暫停會使鏡像工作階段的狀態設定為 SUSPENDED，鏡像資料庫不再與主體資料庫同步，造成主體資料庫需公開執行。</span><span class="sxs-lookup"><span data-stu-id="32efc-107">Pausing sets the state of the mirroring session to SUSPENDED, and the mirror database no longer keeps up with the principal database, causing the principal database to run exposed.</span></span>  
  
 <span data-ttu-id="32efc-108">因為只要資料庫鏡像工作階段維持暫停狀態，就無法截斷交易記錄，所以建議您快速地繼續暫停的工作階段。</span><span class="sxs-lookup"><span data-stu-id="32efc-108">We recommend that you resume a paused session quickly, because as long as a database mirroring session remains paused, the transaction log cannot be truncated.</span></span> <span data-ttu-id="32efc-109">因此，如果資料庫鏡像工作階段暫停太久，則會填滿交易記錄，而讓資料庫無法使用。</span><span class="sxs-lookup"><span data-stu-id="32efc-109">Therefore, if a database mirroring session is paused for too long, the transaction log fills up, making the database unavailable.</span></span> <span data-ttu-id="32efc-110">如需為何發生此狀況的說明，請參閱這個主題後面的「暫停和繼續對記錄截斷的影響」。</span><span class="sxs-lookup"><span data-stu-id="32efc-110">For an explanation of why this happens, see "How Pausing and Resuming Affect Log Truncation," later in this topic.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="32efc-111">在強制服務之後，當原始主體伺服器重新連接時，會暫停鏡像。</span><span class="sxs-lookup"><span data-stu-id="32efc-111">Following a forced service, when the original principal server reconnects mirroring is suspended.</span></span> <span data-ttu-id="32efc-112">在這種情況下繼續執行鏡像，很可能會造成原始主體伺服器上的資料遺失。</span><span class="sxs-lookup"><span data-stu-id="32efc-112">Resuming mirroring in this situation could possibly cause data loss on the original principal server.</span></span> <span data-ttu-id="32efc-113">如需有關管理潛在資料遺失的詳細資訊，請參閱＜ [Database Mirroring Operating Modes](database-mirroring-operating-modes.md)＞。</span><span class="sxs-lookup"><span data-stu-id="32efc-113">For information about managing the potential data loss, see [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span></span>  
  
 <span data-ttu-id="32efc-114">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="32efc-114">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="32efc-115">暫停和繼續對記錄截斷的影響</span><span class="sxs-lookup"><span data-stu-id="32efc-115">How Pausing and Resuming Affect Log Truncation</span></span>](#EffectOnLogTrunc)  
  
-   [<span data-ttu-id="32efc-116">避免填滿交易記錄</span><span class="sxs-lookup"><span data-stu-id="32efc-116">Avoid a Full Transaction Log</span></span>](#AvoidFullLog)  
  
-   [<span data-ttu-id="32efc-117">相關工作</span><span class="sxs-lookup"><span data-stu-id="32efc-117">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="how-pausing-and-resuming-affect-log-truncation"></a><a name="EffectOnLogTrunc"></a> <span data-ttu-id="32efc-118">暫停和繼續對記錄截斷的影響</span><span class="sxs-lookup"><span data-stu-id="32efc-118">How Pausing and Resuming Affect Log Truncation</span></span>  
 <span data-ttu-id="32efc-119">一般而言，在資料庫上執行自動檢查點時，交易記錄會在下一個記錄備份之後，截斷至該檢查點。</span><span class="sxs-lookup"><span data-stu-id="32efc-119">Normally, when an automatic checkpoint is performed on a database, its transaction log is truncated to that checkpoint after the next log backup.</span></span> <span data-ttu-id="32efc-120">資料庫鏡像工作階段維持暫停狀態時，因為主體伺服器等著將目前的記錄傳送至鏡像伺服器，所以目前所有的記錄都會維持使用中狀態。</span><span class="sxs-lookup"><span data-stu-id="32efc-120">While a database mirroring session remains paused, all of the current log records remain active because the principal server is waiting to send them to the mirror server.</span></span> <span data-ttu-id="32efc-121">在工作階段繼續，且主體伺服器已將記錄傳送至鏡像伺服器之前，未傳送的記錄都會累積在主體資料庫的交易記錄中。</span><span class="sxs-lookup"><span data-stu-id="32efc-121">The unsent log records accumulate in the transaction log of the principal database until the session resumes and the principal server has sent the log records to the mirror server.</span></span>  
  
 <span data-ttu-id="32efc-122">繼續工作階段時，主體伺服器會立即開始將累積的記錄傳送至鏡像伺服器。</span><span class="sxs-lookup"><span data-stu-id="32efc-122">When the session is resumed, the principal server immediately begins sending the accumulated log records to the mirror server.</span></span> <span data-ttu-id="32efc-123">鏡像伺服器確認已將與最舊自動檢查點對應的記錄放入佇列之後，主體伺服器會將主體資料庫的記錄檔截斷至該檢查點。</span><span class="sxs-lookup"><span data-stu-id="32efc-123">After the mirror server confirms that it has queued the log record corresponding to the oldest automatic checkpoint, the principal server truncates the log of the principal database to that checkpoint.</span></span> <span data-ttu-id="32efc-124">鏡像伺服器會在同一筆記錄截斷重做佇列。</span><span class="sxs-lookup"><span data-stu-id="32efc-124">The mirror server truncates the redo queue at the same log record.</span></span> <span data-ttu-id="32efc-125">每個後續檢查點都重複這個處理序時，則會依據檢查點並按階段截斷記錄檔。</span><span class="sxs-lookup"><span data-stu-id="32efc-125">As this process is repeated for each successive checkpoint, the log is truncated in stages, checkpoint by checkpoint.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="32efc-126">如需檢查點和記錄截斷的詳細資訊，請參閱 [資料庫檢查點 &#40;SQL Server&#41;](../../relational-databases/logs/database-checkpoints-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="32efc-126">For more information about the checkpoints and log truncation, see [Database Checkpoints &#40;SQL Server&#41;](../../relational-databases/logs/database-checkpoints-sql-server.md).</span></span>  
  
##  <a name="avoid-a-full-transaction-log"></a><a name="AvoidFullLog"></a> <span data-ttu-id="32efc-127">避免填滿交易記錄</span><span class="sxs-lookup"><span data-stu-id="32efc-127">Avoid a Full Transaction Log</span></span>  
 <span data-ttu-id="32efc-128">如果記錄已填滿 (因為已達到最大值，或者伺服器執行個體用盡空間)，資料庫就不能再執行其他更新。</span><span class="sxs-lookup"><span data-stu-id="32efc-128">If the log fills up (either because it reaches its maximum size or the server instance runs out of space), the database cannot perform any more updates.</span></span> <span data-ttu-id="32efc-129">若要避免此問題，您有兩個替代方法：</span><span class="sxs-lookup"><span data-stu-id="32efc-129">To avoid this problem, you have two alternatives:</span></span>  
  
-   <span data-ttu-id="32efc-130">在記錄填滿之前，先繼續資料庫的鏡像工作階段，或增加更多記錄空間。</span><span class="sxs-lookup"><span data-stu-id="32efc-130">Resume the database mirroring session before the log fills up, or add more log space.</span></span> <span data-ttu-id="32efc-131">繼續資料庫的鏡像，主體伺服器才能將累積的使用中記錄傳送至鏡像伺服器，並讓鏡像資料庫處於 SYNCHRONIZING 狀態。</span><span class="sxs-lookup"><span data-stu-id="32efc-131">Resuming database mirroring lets the principal server send its accumulated active log to the mirror server and puts the mirror database in the SYNCHRONIZING state.</span></span> <span data-ttu-id="32efc-132">然後，鏡像伺服器才可將記錄強化至磁碟，並開始重做它。</span><span class="sxs-lookup"><span data-stu-id="32efc-132">The mirror server can then harden the log to disk and start to redo it.</span></span>  
  
-   <span data-ttu-id="32efc-133">透過移除鏡像，停止資料庫鏡像工作階段。</span><span class="sxs-lookup"><span data-stu-id="32efc-133">Stop the database mirroring session by removing mirroring.</span></span>  
  
     <span data-ttu-id="32efc-134">與暫停工作階段不同的是，移除鏡像會卸除鏡像工作階段的所有相關資訊。</span><span class="sxs-lookup"><span data-stu-id="32efc-134">Unlike pausing a session, removing mirroring drops all information about the mirroring session.</span></span> <span data-ttu-id="32efc-135">每個夥伴伺服器執行個體，會保留本身的資料庫副本。</span><span class="sxs-lookup"><span data-stu-id="32efc-135">Each partner server instance retains its own copy of the database.</span></span> <span data-ttu-id="32efc-136">如果復原先前的鏡像副本，則可能會與先前的主體副本有所差異，且會落後自工作階段暫停後所經過的時間量。</span><span class="sxs-lookup"><span data-stu-id="32efc-136">If the former mirror copy is recovered, it will have diverged from the former principal copy and be behind by the amount of time that has elapsed since the session was paused.</span></span> <span data-ttu-id="32efc-137">如需詳細資訊，請參閱 [移除資料庫鏡像 &#40;SQL Server&#41;](database-mirroring-sql-server.md)＞。</span><span class="sxs-lookup"><span data-stu-id="32efc-137">For more information, see [Removing Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="32efc-138">相關工作</span><span class="sxs-lookup"><span data-stu-id="32efc-138">Related Tasks</span></span>  
 <span data-ttu-id="32efc-139">**若要暫停或繼續資料庫鏡像**</span><span class="sxs-lookup"><span data-stu-id="32efc-139">**To pause or resume database mirroring**</span></span>  
  
-   [<span data-ttu-id="32efc-140">暫停或繼續資料庫鏡像工作階段 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="32efc-140">Pause or Resume a Database Mirroring Session &#40;SQL Server&#41;</span></span>](pause-or-resume-a-database-mirroring-session-sql-server.md)  
  
 <span data-ttu-id="32efc-141">**若要停止資料庫鏡像**</span><span class="sxs-lookup"><span data-stu-id="32efc-141">**To stop database mirroring**</span></span>  
  
-   [<span data-ttu-id="32efc-142">移除資料庫鏡像 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="32efc-142">Remove Database Mirroring &#40;SQL Server&#41;</span></span>](remove-database-mirroring-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="32efc-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32efc-143">See Also</span></span>  
 <span data-ttu-id="32efc-144">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="32efc-144">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="32efc-145">[資料庫鏡像 &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="32efc-145">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="32efc-146">移除資料庫鏡像 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="32efc-146">Removing Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)  
  
  
