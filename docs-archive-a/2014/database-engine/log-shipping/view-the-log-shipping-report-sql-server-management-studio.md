---
title: 檢視記錄傳送報表 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- viewing log shipping reports
- displaying log shipping reports
- log shipping [SQL Server], monitoring
- log shipping [SQL Server], viewing reports
ms.assetid: 3b549f2f-3683-45e5-b8e8-8095276c41ab
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0d6c372a9b1f9af9e5948732e3bfb9384362f545
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607031"
---
# <a name="view-the-log-shipping-report-sql-server-management-studio"></a><span data-ttu-id="adf43-102">檢視記錄傳送報表 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="adf43-102">View the Log Shipping Report (SQL Server Management Studio)</span></span>
  <span data-ttu-id="adf43-103">此主題說明如何檢視 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的「交易記錄傳送狀態」報表。</span><span class="sxs-lookup"><span data-stu-id="adf43-103">This topic explains how to view the Transaction Log Shipping Status report in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="adf43-104">您可以在監視伺服器、主要伺服器或次要伺服器執行狀態報表。</span><span class="sxs-lookup"><span data-stu-id="adf43-104">You can run a status report at a monitor server, primary server, or secondary server.</span></span> <span data-ttu-id="adf43-105">若要查看有關記錄傳送組態的最完整資訊，請在監視伺服器執行個體中檢視報表。</span><span class="sxs-lookup"><span data-stu-id="adf43-105">To see the  most complete information about your log shipping configuration, view the report at the monitor server instance.</span></span>  
  
 <span data-ttu-id="adf43-106">此報表會顯示您所連接的伺服器執行個體中，有可用狀態的任何記錄傳送活動的狀態。</span><span class="sxs-lookup"><span data-stu-id="adf43-106">The report displays the status of any log shipping activity whose status is available from the server instance to which you are connected.</span></span> <span data-ttu-id="adf43-107">如果該伺服器執行個體牽涉到不同角色的多個組態 (例如，當做某個資料庫的監視伺服器，但同時又是另一個資料庫的次要伺服器)，則顯示的結果將包含每一個角色觀點的所有組態資訊。</span><span class="sxs-lookup"><span data-stu-id="adf43-107">If that server instance is involved in multiple configurations in different roles (such as serving as a monitor for one database and a secondary for another database), the displayed results contain the information of every configuration from the perspective of each role.</span></span> <span data-ttu-id="adf43-108">如果預存程序可以透過給定的記錄傳送組態連接到監視伺服器執行個體，報表便可以顯示該組態的額外狀態。</span><span class="sxs-lookup"><span data-stu-id="adf43-108">If the stored procedure can connect to the monitor server instance for a given log shipping configuration, the report displays additional status for that configuration.</span></span>  
  
 <span data-ttu-id="adf43-109">對於目前伺服器執行個體所執行的每一個角色，您可以檢視下列資訊：</span><span class="sxs-lookup"><span data-stu-id="adf43-109">For each role performed by the current server instance, you can view the following information:</span></span>  
  
|<span data-ttu-id="adf43-110">角色</span><span class="sxs-lookup"><span data-stu-id="adf43-110">Role</span></span>|<span data-ttu-id="adf43-111">顯示的資訊</span><span class="sxs-lookup"><span data-stu-id="adf43-111">Information displayed</span></span>|  
|----------|---------------------------|  
|<span data-ttu-id="adf43-112">監視</span><span class="sxs-lookup"><span data-stu-id="adf43-112">Monitor</span></span>|<span data-ttu-id="adf43-113">使用此伺服器執行個體作為其監視伺服器的所有主要伺服器及次要伺服器，其名稱及狀態。</span><span class="sxs-lookup"><span data-stu-id="adf43-113">The name and status of every primary server and secondary server that uses this server instance as its monitor server.</span></span>|  
|<span data-ttu-id="adf43-114">Primary</span><span class="sxs-lookup"><span data-stu-id="adf43-114">Primary</span></span>|<span data-ttu-id="adf43-115">對於每一個主要資料庫，此為目前伺服器執行個體 (作為主要伺服器) 的狀態與名稱，還有主要資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="adf43-115">For each primary database, the status and name of the current server instance (as the primary server), along with the primary database name.</span></span> <span data-ttu-id="adf43-116">報表會顯示備份作業 (儲存在主要伺服器的本機上) 的狀態。</span><span class="sxs-lookup"><span data-stu-id="adf43-116">The report displays the status of the backup job (which is stored locally on the primary server).</span></span><br /><br /> <span data-ttu-id="adf43-117">報表也會針對每一個對應的次要伺服器，各顯示一個資料列。</span><span class="sxs-lookup"><span data-stu-id="adf43-117">The report also contains a row for each of the corresponding secondary servers.</span></span> <span data-ttu-id="adf43-118">如果組態使用監視伺服器，且預存程序可以連接到監視伺服器，這些資料列會顯示最新記錄備份的複製狀態及還原狀態。</span><span class="sxs-lookup"><span data-stu-id="adf43-118">If the configuration uses a monitor server and the stored procedure can connect to the monitor, these rows display the copy status and restore status for the most recent log backup.</span></span>|  
|<span data-ttu-id="adf43-119">次要</span><span class="sxs-lookup"><span data-stu-id="adf43-119">Secondary</span></span>|<span data-ttu-id="adf43-120">對於每一個次要資料庫，此為目前伺服器執行個體 (作為次要伺服器) 的狀態與名稱，還有次要資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="adf43-120">For each secondary database, the status and name of the current server instance (as the secondary server), along with the secondary database name.</span></span><br /><br /> <span data-ttu-id="adf43-121">報表會顯示次要伺服器中的複製及還原作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="adf43-121">The report displays the status of the copy and restore jobs at the secondary server.</span></span><br /><br /> <span data-ttu-id="adf43-122">報表也會針對所對應的主要伺服器，顯示一個資料列。</span><span class="sxs-lookup"><span data-stu-id="adf43-122">The report also contains a row for the corresponding primary server.</span></span> <span data-ttu-id="adf43-123">如果組態使用監視伺服器，且預存程序可以連接到監視伺服器，此資料列會顯示最新記錄備份的狀態。</span><span class="sxs-lookup"><span data-stu-id="adf43-123">If the configuration uses a monitor server and the stored procedure can connect to the monitor, this row displays the status of the most recent log backup.</span></span>|  
  
 <span data-ttu-id="adf43-124">所顯示的資訊內容取決於伺服器執行個體是監視伺服器、主要伺服器或次要伺服器。</span><span class="sxs-lookup"><span data-stu-id="adf43-124">The information displayed depends on whether the server instance is a monitor server, primary server, or secondary server.</span></span> <span data-ttu-id="adf43-125">如果無法取得資訊，對應的資料格將呈現灰色。</span><span class="sxs-lookup"><span data-stu-id="adf43-125">If information is not available, the corresponding cells are grayed out.</span></span>  
  
 <span data-ttu-id="adf43-126">此報表會呼叫 **sp_help_log_shipping_monitor** 以取得資料。</span><span class="sxs-lookup"><span data-stu-id="adf43-126">The report calls **sp_help_log_shipping_monitor** to get the data.</span></span> <span data-ttu-id="adf43-127">如需必要權限的相關資訊，請參閱 [sp_help_log_shipping_monitor &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="adf43-127">For information about the required permissions, see [sp_help_log_shipping_monitor &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-transact-sql).</span></span>  
  
### <a name="to-display-the-transaction-log-shipping-status-report-on-a-server-instance"></a><span data-ttu-id="adf43-128">顯示伺服器執行個體上的交易記錄傳送狀態報表</span><span class="sxs-lookup"><span data-stu-id="adf43-128">To display the Transaction Log Shipping Status report on a server instance</span></span>  
  
1.  <span data-ttu-id="adf43-129">連接到監視伺服器、主要伺服器或次要伺服器。</span><span class="sxs-lookup"><span data-stu-id="adf43-129">Connect to a monitor server, primary server, or secondary server.</span></span>  
  
2.  <span data-ttu-id="adf43-130">以滑鼠右鍵按一下 [物件總管] 中的伺服器執行個體，然後依序指向 [報表] 和 [標準報表]。</span><span class="sxs-lookup"><span data-stu-id="adf43-130">Right-click the server instance in Object Explorer, point to **Reports**, and point to **Standard Reports**.</span></span>  
  
3.  <span data-ttu-id="adf43-131">按一下 **[交易記錄傳送狀態]** 。</span><span class="sxs-lookup"><span data-stu-id="adf43-131">Click **Transaction Log Shipping Status**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adf43-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="adf43-132">See Also</span></span>  
 [<span data-ttu-id="adf43-133">監視記錄傳送 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="adf43-133">Monitor Log Shipping &#40;Transact-SQL&#41;</span></span>](monitor-log-shipping-transact-sql.md)  
  
  
