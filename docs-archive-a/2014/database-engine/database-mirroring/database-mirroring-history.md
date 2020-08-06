---
title: 資料庫鏡像見證 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dbmmonitor.databasemirroringhistory.f1
ms.assetid: 1d6e4b10-4a23-47d7-9918-c417992f09d3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3e32ad9bfdce15413d89fbd5ba3d79a5ef14f7a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598512"
---
# <a name="database-mirroring-history"></a><span data-ttu-id="1fdaa-102">資料庫鏡像記錄</span><span class="sxs-lookup"><span data-stu-id="1fdaa-102">Database Mirroring History</span></span>
  <span data-ttu-id="1fdaa-103">使用這個對話方塊，可檢視指定的伺服器執行個體上某個鏡像資料庫的鏡像狀態記錄。</span><span class="sxs-lookup"><span data-stu-id="1fdaa-103">Use this dialog box to view the history of mirroring status for a mirrored database on a specified server instance.</span></span>  
  
 <span data-ttu-id="1fdaa-104">**若要使用 SQL Server Management Studio 監視資料庫鏡像**</span><span class="sxs-lookup"><span data-stu-id="1fdaa-104">**To use SQL Server Management Studio to monitor database mirroring**</span></span>  
  
-   [<span data-ttu-id="1fdaa-105">啟動資料庫鏡像監視器 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="1fdaa-105">Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;</span></span>](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
## <a name="options"></a><span data-ttu-id="1fdaa-106">選項。</span><span class="sxs-lookup"><span data-stu-id="1fdaa-106">Options</span></span>  
 <span data-ttu-id="1fdaa-107">**伺服器執行個體**</span><span class="sxs-lookup"><span data-stu-id="1fdaa-107">**Server instance**</span></span>  
 <span data-ttu-id="1fdaa-108">正在報告記錄的伺服器執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="1fdaa-108">Name of the server instance from which the history is being reported.</span></span>  
  
 <span data-ttu-id="1fdaa-109">**Database**</span><span class="sxs-lookup"><span data-stu-id="1fdaa-109">**Database**</span></span>  
 <span data-ttu-id="1fdaa-110">正在報告之記錄所屬的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="1fdaa-110">Name of the database whose history is being reported.</span></span>  
  
 <span data-ttu-id="1fdaa-111">**依下列項目篩選清單**</span><span class="sxs-lookup"><span data-stu-id="1fdaa-111">**Filter list by**</span></span>  
 <span data-ttu-id="1fdaa-112">列出篩選值。</span><span class="sxs-lookup"><span data-stu-id="1fdaa-112">Lists filter values.</span></span> <span data-ttu-id="1fdaa-113">如果選擇新值，就會自動重新整理方格。</span><span class="sxs-lookup"><span data-stu-id="1fdaa-113">Choosing a new value refreshes the grid automatically.</span></span>  
  
 <span data-ttu-id="1fdaa-114">可能的篩選值如下：</span><span class="sxs-lookup"><span data-stu-id="1fdaa-114">The possible filter values are:</span></span>  
  
-   <span data-ttu-id="1fdaa-115">最後兩小時</span><span class="sxs-lookup"><span data-stu-id="1fdaa-115">Last two hours</span></span>  
  
-   <span data-ttu-id="1fdaa-116">最後四小時</span><span class="sxs-lookup"><span data-stu-id="1fdaa-116">Last four hours</span></span>  
  
-   <span data-ttu-id="1fdaa-117">最後八小時</span><span class="sxs-lookup"><span data-stu-id="1fdaa-117">Last eight hours</span></span>  
  
-   <span data-ttu-id="1fdaa-118">最後一天</span><span class="sxs-lookup"><span data-stu-id="1fdaa-118">Last day</span></span>  
  
-   <span data-ttu-id="1fdaa-119">最後兩天</span><span class="sxs-lookup"><span data-stu-id="1fdaa-119">Last two days</span></span>  
  
-   <span data-ttu-id="1fdaa-120">最後 100 筆記錄</span><span class="sxs-lookup"><span data-stu-id="1fdaa-120">Last 100 records</span></span>  
  
-   <span data-ttu-id="1fdaa-121">最後 500 筆記錄</span><span class="sxs-lookup"><span data-stu-id="1fdaa-121">Last 500 records</span></span>  
  
-   <span data-ttu-id="1fdaa-122">最後 1000 筆記錄</span><span class="sxs-lookup"><span data-stu-id="1fdaa-122">Last 1000 records</span></span>  
  
-   <span data-ttu-id="1fdaa-123">所有記錄</span><span class="sxs-lookup"><span data-stu-id="1fdaa-123">All records</span></span>  
  
 <span data-ttu-id="1fdaa-124">**[重新整理]**</span><span class="sxs-lookup"><span data-stu-id="1fdaa-124">**Refresh**</span></span>  
 <span data-ttu-id="1fdaa-125">按一下即可重新整理記錄清單。</span><span class="sxs-lookup"><span data-stu-id="1fdaa-125">Click to refresh the history list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1fdaa-126">這個對話方塊不會自動重新整理記錄清單。</span><span class="sxs-lookup"><span data-stu-id="1fdaa-126">This dialog box does not automatically refresh the history list.</span></span> <span data-ttu-id="1fdaa-127">若要重新整理清單，請按一下 **[重新整理]** 或選擇其他篩選選項。</span><span class="sxs-lookup"><span data-stu-id="1fdaa-127">To refresh the list, either click **Refresh** or choose another filter option.</span></span> <span data-ttu-id="1fdaa-128">只有 **sysadmin** 固定伺服器角色的成員才能更新鏡像記錄。</span><span class="sxs-lookup"><span data-stu-id="1fdaa-128">Only members of the **sysadmin** fixed server role can update the mirroring history.</span></span>  
  
 <span data-ttu-id="1fdaa-129">**History**</span><span class="sxs-lookup"><span data-stu-id="1fdaa-129">**History**</span></span>  
 <span data-ttu-id="1fdaa-130">顯示記錄清單。</span><span class="sxs-lookup"><span data-stu-id="1fdaa-130">Displays the history list.</span></span> <span data-ttu-id="1fdaa-131">按一下資料行標題，就會依據該資料行排序方格。</span><span class="sxs-lookup"><span data-stu-id="1fdaa-131">Clicking on a column header sorts the grid by that column.</span></span> <span data-ttu-id="1fdaa-132">此清單包含下列資料行：</span><span class="sxs-lookup"><span data-stu-id="1fdaa-132">The list contains the following columns:</span></span>  
  
|<span data-ttu-id="1fdaa-133">資料行名稱</span><span class="sxs-lookup"><span data-stu-id="1fdaa-133">Column name</span></span>|<span data-ttu-id="1fdaa-134">描述</span><span class="sxs-lookup"><span data-stu-id="1fdaa-134">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="1fdaa-135">**記錄的時間**</span><span class="sxs-lookup"><span data-stu-id="1fdaa-135">**Time Recorded**</span></span>|<span data-ttu-id="1fdaa-136">記錄資料列的時間戳記。</span><span class="sxs-lookup"><span data-stu-id="1fdaa-136">Timestamp of the history row.</span></span>|  
|<span data-ttu-id="1fdaa-137">**角色**</span><span class="sxs-lookup"><span data-stu-id="1fdaa-137">**Role**</span></span>|<span data-ttu-id="1fdaa-138">對這個資料庫而言，伺服器執行個體目前的鏡像角色，可為 [主體] 或 [鏡像]。</span><span class="sxs-lookup"><span data-stu-id="1fdaa-138">Current mirroring role of the server instance for this database, either Principal or Mirror.</span></span>|  
|<span data-ttu-id="1fdaa-139">**鏡像狀態**</span><span class="sxs-lookup"><span data-stu-id="1fdaa-139">**Mirroring State**</span></span>|<span data-ttu-id="1fdaa-140">資料庫狀態：</span><span class="sxs-lookup"><span data-stu-id="1fdaa-140">State of the database:</span></span><br /><br /> <span data-ttu-id="1fdaa-141">已中斷連接</span><span class="sxs-lookup"><span data-stu-id="1fdaa-141">Disconnected</span></span><br /><br /> <span data-ttu-id="1fdaa-142">暫止容錯移轉</span><span class="sxs-lookup"><span data-stu-id="1fdaa-142">Pending Failover</span></span><br /><br /> <span data-ttu-id="1fdaa-143">暫止</span><span class="sxs-lookup"><span data-stu-id="1fdaa-143">Suspended</span></span><br /><br /> <span data-ttu-id="1fdaa-144">已同步處理</span><span class="sxs-lookup"><span data-stu-id="1fdaa-144">Synchronized</span></span><br /><br /> <span data-ttu-id="1fdaa-145">正在同步處理</span><span class="sxs-lookup"><span data-stu-id="1fdaa-145">Synchronizing</span></span><br /><br /> <span data-ttu-id="1fdaa-146">Unknown</span><span class="sxs-lookup"><span data-stu-id="1fdaa-146">Unknown</span></span>|  
|<span data-ttu-id="1fdaa-147">**見證連接**</span><span class="sxs-lookup"><span data-stu-id="1fdaa-147">**Witness Connection**</span></span>|<span data-ttu-id="1fdaa-148">資料庫鏡像工作階段中的見證連接狀態，可為 [已連接] 或 [已中斷連接]。</span><span class="sxs-lookup"><span data-stu-id="1fdaa-148">State of the witness connection in the mirroring session of the database, either Connected or Disconnected.</span></span> <span data-ttu-id="1fdaa-149">如果沒有見證，則此值為 NULL。</span><span class="sxs-lookup"><span data-stu-id="1fdaa-149">If there is no witness, the value is NULL.</span></span>|  
|<span data-ttu-id="1fdaa-150">**未傳送的記錄**</span><span class="sxs-lookup"><span data-stu-id="1fdaa-150">**Unsent Log**</span></span>|<span data-ttu-id="1fdaa-151">主體伺服器執行個體上傳送佇列中未傳送記錄的大小 (以 KB 為單位)。</span><span class="sxs-lookup"><span data-stu-id="1fdaa-151">Size, in kilobytes (KB), of the unsent log in the send queue on the principal server instance.</span></span>|  
|<span data-ttu-id="1fdaa-152">**傳送的時間**</span><span class="sxs-lookup"><span data-stu-id="1fdaa-152">**Time to Send**</span></span>|<span data-ttu-id="1fdaa-153">主體伺服器執行個體將目前在傳送佇列中的記錄，傳送到鏡像伺服器執行個體所需的大約時間量 ( *傳送速率*)。</span><span class="sxs-lookup"><span data-stu-id="1fdaa-153">Approximate amount of time the principal server instance will require to send the log that is currently in the send queue to the mirror server instance (the *send rate*).</span></span> <span data-ttu-id="1fdaa-154">由於內送交易的速率可能會有極大的差異，因此傳送記錄的時間只是估計值。</span><span class="sxs-lookup"><span data-stu-id="1fdaa-154">Because the rate of incoming transactions can vary significantly, the time to send log is an estimate.</span></span> <span data-ttu-id="1fdaa-155">但是，傳送速率對於粗略估計手動容錯移轉所需的時間可能會很有用。</span><span class="sxs-lookup"><span data-stu-id="1fdaa-155">However, the send rate can be useful for roughly estimating the time required for a manual failover.</span></span>|  
|<span data-ttu-id="1fdaa-156">**Send Rate**</span><span class="sxs-lookup"><span data-stu-id="1fdaa-156">**Send Rate**</span></span>|<span data-ttu-id="1fdaa-157">將交易傳送到鏡像伺服器執行個體的速率 (以每秒 KB 數為單位)。</span><span class="sxs-lookup"><span data-stu-id="1fdaa-157">Rate at which transactions are being sent to the mirror server instance, in KB per second.</span></span>|  
|<span data-ttu-id="1fdaa-158">**新交易的速率**</span><span class="sxs-lookup"><span data-stu-id="1fdaa-158">**New Transaction Rate**</span></span>|<span data-ttu-id="1fdaa-159">將內送交易輸入到主體記錄中的速率 (以每秒 KB 數為單位)。</span><span class="sxs-lookup"><span data-stu-id="1fdaa-159">Rate at which incoming transactions are being entered into the principal's log, in KB per second.</span></span> <span data-ttu-id="1fdaa-160">若要判斷鏡像是落後、超前，還是趕上進度，請將這個值與 **[傳送的時間]** 值加以比較。</span><span class="sxs-lookup"><span data-stu-id="1fdaa-160">To determine whether mirroring is falling behind, staying up, or catching up, compare this value to the **Time to Send** value.</span></span>|  
|<span data-ttu-id="1fdaa-161">**最舊尚未傳送的交易**</span><span class="sxs-lookup"><span data-stu-id="1fdaa-161">**Oldest Unsent Transaction**</span></span>|<span data-ttu-id="1fdaa-162">傳送佇列中最舊尚未傳送之交易的存在時間。</span><span class="sxs-lookup"><span data-stu-id="1fdaa-162">Age of the oldest unsent transaction in the send queue.</span></span> <span data-ttu-id="1fdaa-163">這項交易的存在時間會指出尚未傳送到鏡像伺服器執行個體的交易分鐘數。</span><span class="sxs-lookup"><span data-stu-id="1fdaa-163">The age of this transaction indicates how many minutes of transactions have not yet been sent to the mirror server instance.</span></span> <span data-ttu-id="1fdaa-164">這個值有助於從時間方面來測量資料遺失的可能性。</span><span class="sxs-lookup"><span data-stu-id="1fdaa-164">This value helps measure the potential for data loss in terms of time.</span></span>|  
|<span data-ttu-id="1fdaa-165">**未還原的記錄**</span><span class="sxs-lookup"><span data-stu-id="1fdaa-165">**Unrestored Log**</span></span>|<span data-ttu-id="1fdaa-166">在重做佇列中等待的記錄量 (以 KB 為單位)。</span><span class="sxs-lookup"><span data-stu-id="1fdaa-166">The amount of log waiting in the redo queue, in KB.</span></span>|  
|<span data-ttu-id="1fdaa-167">**還原的時間**</span><span class="sxs-lookup"><span data-stu-id="1fdaa-167">**Time to Restore**</span></span>|<span data-ttu-id="1fdaa-168">將目前在重做佇列中的記錄套用至鏡像資料庫所需的大約分鐘數。</span><span class="sxs-lookup"><span data-stu-id="1fdaa-168">Approximate number of minutes required for the log currently in the redo queue to be applied to the mirror database.</span></span>|  
|<span data-ttu-id="1fdaa-169">**還原速率**</span><span class="sxs-lookup"><span data-stu-id="1fdaa-169">**Restore Rate**</span></span>|<span data-ttu-id="1fdaa-170">將交易還原到鏡像資料庫中的速率 (以每秒 KB 數為單位)。</span><span class="sxs-lookup"><span data-stu-id="1fdaa-170">Rate at which transactions are being restored into the mirror database, in KB per second.</span></span>|  
|<span data-ttu-id="1fdaa-171">**鏡像認可負擔**</span><span class="sxs-lookup"><span data-stu-id="1fdaa-171">**Mirror Commit Overhead**</span></span>|<span data-ttu-id="1fdaa-172">每項交易的平均延遲毫秒數 (只限於同步模式)。</span><span class="sxs-lookup"><span data-stu-id="1fdaa-172">Average delay per transaction in milliseconds (only in synchronous modes).</span></span> <span data-ttu-id="1fdaa-173">這項延遲是當主體伺服器執行個體等待鏡像伺服器執行個體將交易記錄寫入重做佇列中時所產生的負擔量。</span><span class="sxs-lookup"><span data-stu-id="1fdaa-173">This delay is the amount of overhead incurred while the principal server instance waits for the mirror server instance to write the transaction's log record into the redo queue.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1fdaa-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1fdaa-174">See Also</span></span>  
 <span data-ttu-id="1fdaa-175">[啟動資料庫鏡像監視器 &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="1fdaa-175">[Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="1fdaa-176">[監視資料庫鏡像 &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1fdaa-176">[Monitoring Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="1fdaa-177">啟動設定資料庫鏡像安全性精靈 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="1fdaa-177">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
  
