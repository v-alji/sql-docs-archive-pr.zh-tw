---
title: 備份時刻表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.POINTINTIMERESTORE.F1
- sql12.swb.backuptimeline.f1
helpviewer_keywords:
- Backup Timeline
ms.assetid: ae3565f2-ddb2-4469-a992-7531d4f9ebb8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9b075f8c9ec32cfe483c64e34e9f9b4e4b6e80e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606930"
---
# <a name="backup-timeline"></a><span data-ttu-id="49d43-102">備份時刻表</span><span class="sxs-lookup"><span data-stu-id="49d43-102">Backup Timeline</span></span>
  <span data-ttu-id="49d43-103">使用 [備份時間表]  對話方塊，尋找及指定將資料庫還原至某個時間點的備份。</span><span class="sxs-lookup"><span data-stu-id="49d43-103">Use the **Backup Timeline** dialog box to locate and specify backups to restore a database to a point-in-time.</span></span> <span data-ttu-id="49d43-104">透過按一下 [還原資料庫] 窗格 ([一般] 頁面)  上的 [時間表]  上，即可存取 [備份時間表]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="49d43-104">The **Backup Timeline** dialog box is accessed by clicking **Timeline** on the **Restore Database (General Page)** pane.</span></span> <span data-ttu-id="49d43-105">這個對話方塊可讓您檢視資料庫上所執行之還原作業的時間軸。</span><span class="sxs-lookup"><span data-stu-id="49d43-105">This dialog box allows you to view a timeline of the restore operations performed on the database.</span></span>  
  
 <span data-ttu-id="49d43-106">Database Recovery Advisor 會確定只選取要還原到該時間點所需的備份。</span><span class="sxs-lookup"><span data-stu-id="49d43-106">The Database Recovery Advisor ensures that only backups that are required for restoring to that point in time are selected.</span></span> <span data-ttu-id="49d43-107">這些選取的備份為您的還原作業構成了建議的還原計畫。</span><span class="sxs-lookup"><span data-stu-id="49d43-107">These selected backups make up the recommended restore plan for your restore operation.</span></span> <span data-ttu-id="49d43-108">您應該只使用選取的備份。</span><span class="sxs-lookup"><span data-stu-id="49d43-108">You should use only the selected backups.</span></span> <span data-ttu-id="49d43-109">如需資料庫復原建議程式的相關資訊，請參閱[還原和復原概觀 &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="49d43-109">For information about the Database Recovery Advisor, see [Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md).</span></span>  
  
## <a name="restore-to"></a><span data-ttu-id="49d43-110">還原至</span><span class="sxs-lookup"><span data-stu-id="49d43-110">Restore to</span></span>  
 <span data-ttu-id="49d43-111">系統預設會選取 **[上次建立的備份]** 。</span><span class="sxs-lookup"><span data-stu-id="49d43-111">**Last backup taken** is selected by default.</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="49d43-112">會選取適當的備份以還原資料庫，而且會將資料庫還原至上次備份的時間點。</span><span class="sxs-lookup"><span data-stu-id="49d43-112">will select the appropriate backups to restore the database, and will restore the database to the point of the last backup.</span></span> <span data-ttu-id="49d43-113">按一下 [特定的日期與時間]  手動設定日期與時間 (選取特定的時間點)。</span><span class="sxs-lookup"><span data-stu-id="49d43-113">Click **A specific date and time** to manually set the date and time (selecting a specific point in time).</span></span>  
  
 <span data-ttu-id="49d43-114">**[特定的日期與時間]** 會允許您在選取的特定日期和時間停止還原。</span><span class="sxs-lookup"><span data-stu-id="49d43-114">**Specific date and time** permits you stop the restore at a specific date and time that you select.</span></span> <span data-ttu-id="49d43-115">此時間表顯示在所選取日期和時間的 24 小時內執行之備份作業的呈現。</span><span class="sxs-lookup"><span data-stu-id="49d43-115">The timeline shows a representation of the backup operations performed in the 24 hours around the select date and time.</span></span>  
  
 <span data-ttu-id="49d43-116">**日期**</span><span class="sxs-lookup"><span data-stu-id="49d43-116">**Date**</span></span>  
 <span data-ttu-id="49d43-117">輸入日期，或從下拉式清單中選取日期。</span><span class="sxs-lookup"><span data-stu-id="49d43-117">Enter or select a date from the drop-down list.</span></span>  
  
 <span data-ttu-id="49d43-118">**Time**</span><span class="sxs-lookup"><span data-stu-id="49d43-118">**Time**</span></span>  
 <span data-ttu-id="49d43-119">輸入或選取日期，以指定還原停止的特定時間點。</span><span class="sxs-lookup"><span data-stu-id="49d43-119">Enter or select a date to designate the specific point-in-time for the restore to stop.</span></span>  
  
 <span data-ttu-id="49d43-120">**時間表間隔**</span><span class="sxs-lookup"><span data-stu-id="49d43-120">**Timeline Interval**</span></span>  
 <span data-ttu-id="49d43-121">顯示時間軸上可檢視的間隔類型選項。</span><span class="sxs-lookup"><span data-stu-id="49d43-121">Displays the options for the interval types viewable on the timeline.</span></span>  
  
## <a name="timeline-and-legend"></a><span data-ttu-id="49d43-122">時間表和圖例</span><span class="sxs-lookup"><span data-stu-id="49d43-122">Timeline and Legend</span></span>  
 <span data-ttu-id="49d43-123">使用時間表下方的捲軸，沿著時間表向前和向後移動游標。</span><span class="sxs-lookup"><span data-stu-id="49d43-123">Use the scroll bar beneath the timeline to move the cursor forward and backward along the timeline.</span></span> <span data-ttu-id="49d43-124">按一下備份以將捲軸移至備份結尾。</span><span class="sxs-lookup"><span data-stu-id="49d43-124">Click on a backup to move the scroll bar to the end of that backup.</span></span> <span data-ttu-id="49d43-125">將滑鼠停留在標記上方，以顯示提供所選取備份組詳細資訊的工具提示。</span><span class="sxs-lookup"><span data-stu-id="49d43-125">Hover the mouse over a marker to display a ScreenTip providing information about the selected backup set.</span></span> <span data-ttu-id="49d43-126">下列標記會在時間表上顯示備份資訊。</span><span class="sxs-lookup"><span data-stu-id="49d43-126">Backup information is shown on the timeline by the following markers.</span></span>  
  
 <span data-ttu-id="49d43-127">大三角形</span><span class="sxs-lookup"><span data-stu-id="49d43-127">Larger triangle</span></span>  
 <span data-ttu-id="49d43-128">代表資料庫上執行的完整備份，表示執行每個完整備份的特定時間點。</span><span class="sxs-lookup"><span data-stu-id="49d43-128">Represents the full backups performed on the database, denoting the specific point in time each full backup was performed.</span></span>  
  
 <span data-ttu-id="49d43-129">小三角形</span><span class="sxs-lookup"><span data-stu-id="49d43-129">Smaller triangle</span></span>  
 <span data-ttu-id="49d43-130">代表資料庫上執行的差異備份，表示執行每個差異備份的特定時間點。</span><span class="sxs-lookup"><span data-stu-id="49d43-130">Represents the differential backups performed on the database, denoting the specific point in time that each differential backup was performed.</span></span>  
  
 <span data-ttu-id="49d43-131">綠色陰影區域</span><span class="sxs-lookup"><span data-stu-id="49d43-131">Green shaded areas</span></span>  
 <span data-ttu-id="49d43-132">表示交易記錄備份的涵蓋範圍。</span><span class="sxs-lookup"><span data-stu-id="49d43-132">Represents the transaction log backup coverage.</span></span>  
  
 <span data-ttu-id="49d43-133">紅線</span><span class="sxs-lookup"><span data-stu-id="49d43-133">Red line</span></span>  
 <span data-ttu-id="49d43-134">只能放置在時間軸上可能還原的位置。</span><span class="sxs-lookup"><span data-stu-id="49d43-134">Can only be positioned along the timeline where the restore is possible.</span></span> <span data-ttu-id="49d43-135">沿著時間表移動紅線，可調整 **[日期]** 和 **[時間]** 方塊中所顯示的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="49d43-135">Moving the red line along the timeline adjusts the date and time displayed in the **Date** and **Time** boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49d43-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49d43-136">See Also</span></span>  
 [<span data-ttu-id="49d43-137">還原資料庫 &#40;一般頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="49d43-137">Restore Database &#40;General Page&#41;</span></span>](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
  
