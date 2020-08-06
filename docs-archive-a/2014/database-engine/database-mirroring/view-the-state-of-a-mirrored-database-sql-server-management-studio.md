---
title: 檢視鏡像資料庫的狀態 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- states [SQL Server], database mirroring
- database mirroring [SQL Server], states
ms.assetid: 544f4194-253e-4c57-96ca-31c16301434f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fc691e8b746a816ab88448e3399aebad6d8844e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594676"
---
# <a name="view-the-state-of-a-mirrored-database-sql-server-management-studio"></a><span data-ttu-id="0e187-102">檢視鏡像資料庫的狀態 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="0e187-102">View the State of a Mirrored Database (SQL Server Management Studio)</span></span>
  <span data-ttu-id="0e187-103">在資料庫鏡像工作階段中，您可以在 [資料庫屬性] 對話方塊的 [鏡像] 頁面上檢視狀態。</span><span class="sxs-lookup"><span data-stu-id="0e187-103">During a database mirroring session, you can view the status on the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
### <a name="to-view-the-status-of-a-database-mirroring-session"></a><span data-ttu-id="0e187-104">若要檢視資料庫鏡像工作階段的狀態</span><span class="sxs-lookup"><span data-stu-id="0e187-104">To view the status of a database mirroring session</span></span>  
  
1.  <span data-ttu-id="0e187-105">連接到主體伺服器執行個體後，在 [物件總管] 中按一下伺服器名稱，以展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="0e187-105">After connecting to the principal server instance, in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="0e187-106">展開 **[資料庫]** ，然後選取要鏡像的資料庫。</span><span class="sxs-lookup"><span data-stu-id="0e187-106">Expand **Databases**, and select the database to be mirrored.</span></span>  
  
3.  <span data-ttu-id="0e187-107">以滑鼠右鍵按一下資料庫，選取 [工作]，然後按一下 [鏡像]。</span><span class="sxs-lookup"><span data-stu-id="0e187-107">Right-click the database, select **Tasks**, and then click **Mirror**.</span></span> <span data-ttu-id="0e187-108">這將會開啟在 **[資料庫屬性]** 對話方塊中的 **[鏡像]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="0e187-108">This opens the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="0e187-109">在鏡像開始後，[狀態] 面板便會顯示資料庫鏡像工作階段的狀態 (此狀態是從您選取 [鏡像] 頁面或按了 [重新整理] 按鈕後的狀態)。</span><span class="sxs-lookup"><span data-stu-id="0e187-109">After mirroring begins, the **Status** panel displays the status of the database mirroring session as of when you selected the **Mirroring** page or clicked the **Refresh** button.</span></span> <span data-ttu-id="0e187-110">可能的狀態如下：</span><span class="sxs-lookup"><span data-stu-id="0e187-110">The possible states are as follows:</span></span>  
  
    |<span data-ttu-id="0e187-111">狀態</span><span class="sxs-lookup"><span data-stu-id="0e187-111">States</span></span>|<span data-ttu-id="0e187-112">說明</span><span class="sxs-lookup"><span data-stu-id="0e187-112">Explanation</span></span>|  
    |------------|-----------------|  
    |\<blank>|<span data-ttu-id="0e187-113">資料庫鏡像工作階段不存在，並且在 [鏡像] 頁面上沒有可以報告的活動。</span><span class="sxs-lookup"><span data-stu-id="0e187-113">No database mirroring session exists and there is no activity to report on the **Mirroring** page.</span></span>|  
    |<span data-ttu-id="0e187-114">已暫停</span><span class="sxs-lookup"><span data-stu-id="0e187-114">Paused</span></span>|<span data-ttu-id="0e187-115">主體資料庫正在執行中，但沒有傳送任何記錄到鏡像伺服器。</span><span class="sxs-lookup"><span data-stu-id="0e187-115">The principal database is running but is not sending any logs to the mirror server.</span></span> <span data-ttu-id="0e187-116">無法使用資料庫的鏡像副本。</span><span class="sxs-lookup"><span data-stu-id="0e187-116">The mirror copy of the database is not available.</span></span>|  
    |<span data-ttu-id="0e187-117">沒有連接</span><span class="sxs-lookup"><span data-stu-id="0e187-117">No connection</span></span>|<span data-ttu-id="0e187-118">主體伺服器執行個體無法連接到其夥伴或見證伺服器執行個體 (若有的話)。</span><span class="sxs-lookup"><span data-stu-id="0e187-118">The principal server instance cannot connect to its partner or to the witness server instance (if any)</span></span>|  
    |<span data-ttu-id="0e187-119">正在同步處理</span><span class="sxs-lookup"><span data-stu-id="0e187-119">Synchronizing</span></span>|<span data-ttu-id="0e187-120">鏡像資料庫的內容落後於主體資料庫的內容。</span><span class="sxs-lookup"><span data-stu-id="0e187-120">The contents of the mirror database are lagging behind the contents of the principal database.</span></span> <span data-ttu-id="0e187-121">主體伺服器執行個體正在將記錄傳送到鏡像伺服器執行個體，這時會將變更套用至鏡像資料庫，以便向前復原。</span><span class="sxs-lookup"><span data-stu-id="0e187-121">The principal server instance is sending log records to the mirror server instance, which is applying the changes to the mirror database to roll it forward.</span></span><br /><br /> <span data-ttu-id="0e187-122">在資料庫鏡像工作階段的開始時，鏡像和主體資料庫處於同步狀態。</span><span class="sxs-lookup"><span data-stu-id="0e187-122">At the start of a database mirroring session, the mirror and principal databases are in the synchronizing state.</span></span>|  
    |<span data-ttu-id="0e187-123">容錯移轉</span><span class="sxs-lookup"><span data-stu-id="0e187-123">Failover</span></span>|<span data-ttu-id="0e187-124">在主體伺服器執行個體上，手動容錯移轉 (角色交換) 已經開始，但鏡像尚未接受。</span><span class="sxs-lookup"><span data-stu-id="0e187-124">On the principal server instance, a manual failover (role swap) has begun but has not yet accepted by the mirror.</span></span>|  
    |<span data-ttu-id="0e187-125">已同步處理</span><span class="sxs-lookup"><span data-stu-id="0e187-125">Synchronized</span></span>|<span data-ttu-id="0e187-126">鏡像資料庫和主體資料庫包含相同的資料。</span><span class="sxs-lookup"><span data-stu-id="0e187-126">The mirror database contains the same data as the principal database.</span></span> <span data-ttu-id="0e187-127">只有在已同步處理狀態中，才可能執行手動與自動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="0e187-127">Manual and automatic failover are possible *only* in the synchronized state.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0e187-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e187-128">See Also</span></span>  
 [<span data-ttu-id="0e187-129">鏡像狀態 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0e187-129">Mirroring States &#40;SQL Server&#41;</span></span>](mirroring-states-sql-server.md)  
  
  
