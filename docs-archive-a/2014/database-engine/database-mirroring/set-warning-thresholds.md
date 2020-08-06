---
title: 設定警告臨界值 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dbmmonitor.setwarningthreshold.f1
ms.assetid: 17f93147-e7d9-4092-b4c2-c11b38051171
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2d5fd9c0213d74f3a6b5d0d4cb2f11d3531d336d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701743"
---
# <a name="set-warning-thresholds"></a><span data-ttu-id="4291b-102">設定警告臨界值</span><span class="sxs-lookup"><span data-stu-id="4291b-102">Set Warning Thresholds</span></span>
  <span data-ttu-id="4291b-103">使用這個對話方塊可針對 **[資料庫鏡像監視器]** 對話方塊內導覽樹狀目錄中選取的資料庫，啟用並設定一或多個警告臨界值。</span><span class="sxs-lookup"><span data-stu-id="4291b-103">Use this dialog box to enable and configure one or more warning thresholds for the database selected in the navigation tree of the **Database Mirroring Monitor** dialog box.</span></span>  
  
 <span data-ttu-id="4291b-104">這個對話方塊會嘗試連接到兩個伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="4291b-104">The dialog box tries to connect to both server instances.</span></span> <span data-ttu-id="4291b-105">這些連接是以非同步方式建立的。</span><span class="sxs-lookup"><span data-stu-id="4291b-105">These connections are established asynchronously.</span></span> <span data-ttu-id="4291b-106">對話方塊中會顯示每個夥伴的連接狀態。</span><span class="sxs-lookup"><span data-stu-id="4291b-106">The dialog shows the connection status of each partner.</span></span> <span data-ttu-id="4291b-107">如果夥伴處於未連接狀態，您可以按一下 **[連接]** 。</span><span class="sxs-lookup"><span data-stu-id="4291b-107">If the partner is not connected, you can click **Connect**.</span></span>  
  
 <span data-ttu-id="4291b-108">**若要使用 SQL Server Management Studio 監視資料庫鏡像**</span><span class="sxs-lookup"><span data-stu-id="4291b-108">**To use SQL Server Management Studio to monitor database mirroring**</span></span>  
  
-   [<span data-ttu-id="4291b-109">啟動資料庫鏡像監視器 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="4291b-109">Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;</span></span>](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
## <a name="options"></a><span data-ttu-id="4291b-110">選項。</span><span class="sxs-lookup"><span data-stu-id="4291b-110">Options</span></span>  
 <span data-ttu-id="4291b-111">*伺服器執行個體及其連接狀態*</span><span class="sxs-lookup"><span data-stu-id="4291b-111">*Server instance and its connection status*</span></span>  
 <span data-ttu-id="4291b-112">_系統_INSTANCE_NAME 形式的夥伴伺服器實例名稱 **\\** _ _。</span><span class="sxs-lookup"><span data-stu-id="4291b-112">Name of a partner server instance in the form _SYSTEM_**\\**_INSTANCE_NAME_.</span></span> <span data-ttu-id="4291b-113">如果是預設伺服器執行個體，則只會顯示系統名稱。</span><span class="sxs-lookup"><span data-stu-id="4291b-113">For a default server instance, only the system name is displayed.</span></span>  
  
 <span data-ttu-id="4291b-114">這個欄位也會指出監視器目前是否已連接到這個伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="4291b-114">This field also indicates whether the monitor is currently connected to this server instance.</span></span> <span data-ttu-id="4291b-115">可能的連接狀態如下：</span><span class="sxs-lookup"><span data-stu-id="4291b-115">The possible connection statuses are:</span></span>  
  
-   <span data-ttu-id="4291b-116">**未連線到** *server_instance_name*</span><span class="sxs-lookup"><span data-stu-id="4291b-116">**Not connected to**  *server_instance_name*</span></span>  
  
-   <span data-ttu-id="4291b-117">**正在嘗試連線到** *server_instance_name*</span><span class="sxs-lookup"><span data-stu-id="4291b-117">**Trying to connect to**  *server_instance_name*</span></span>  
  
-   <span data-ttu-id="4291b-118">**已連線到** *server_instance_name*</span><span class="sxs-lookup"><span data-stu-id="4291b-118">**Connected to**  *server_instance_name*</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4291b-119">如果您不是**系統管理員**固定伺服器角色的成員，則此狀態會是 [已連線到 *server_instance_name* (有限的權限)] 。</span><span class="sxs-lookup"><span data-stu-id="4291b-119">If you do are not a member of the **sysadmin** fixed server role, this status is **Connected to** *server_instance_name* **(Limited permissions)**.</span></span>  
  
 <span data-ttu-id="4291b-120">每個夥伴伺服器執行個體的名稱都會顯示在個別的 *[伺服器執行個體及其連接狀態]* 欄位中。</span><span class="sxs-lookup"><span data-stu-id="4291b-120">The name of each of the partner server instances is displayed in a separate *Server instance and its connection status* field.</span></span> <span data-ttu-id="4291b-121">當監視器開始執行時，最上面的欄位便會列出主體伺服器。</span><span class="sxs-lookup"><span data-stu-id="4291b-121">The top field lists the principal server when the monitor started running.</span></span>  
  
 <span data-ttu-id="4291b-122">**連接**/**取消**</span><span class="sxs-lookup"><span data-stu-id="4291b-122">**Connect**/**Cancel**</span></span>  
 <span data-ttu-id="4291b-123">[連接]/[取消] 按鈕與各「伺服器執行個體及其連接狀態」欄位相關聯。</span><span class="sxs-lookup"><span data-stu-id="4291b-123">A **Connect**/**Cancel** button is associated with each *Server instance and its connection status* fields.</span></span> <span data-ttu-id="4291b-124">這個按鈕的狀態是依據連接狀態而定：</span><span class="sxs-lookup"><span data-stu-id="4291b-124">The state of the button depends on the connection status:</span></span>  
  
-   <span data-ttu-id="4291b-125">如果伺服器執行個體沒有任何連接，則按鈕文字為 **[連接]** 。</span><span class="sxs-lookup"><span data-stu-id="4291b-125">If there is no connection to the server instance, the button text is **Connect**.</span></span> <span data-ttu-id="4291b-126">按一下即可連接到伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="4291b-126">Click to connect to the server instance.</span></span>  
  
-   <span data-ttu-id="4291b-127">如果正在嘗試進行連接，則按鈕文字為 **[取消]** 。</span><span class="sxs-lookup"><span data-stu-id="4291b-127">When a connection attempt is in progress, the button text is **Cancel**.</span></span> <span data-ttu-id="4291b-128">按一下即可取消正在嘗試的連接。</span><span class="sxs-lookup"><span data-stu-id="4291b-128">Click to cancel the connection attempt.</span></span>  
  
-   <span data-ttu-id="4291b-129">如果伺服器處於已連接狀態，則按鈕文字為 **[已連接]** ，而且按鈕會呈暗灰色。</span><span class="sxs-lookup"><span data-stu-id="4291b-129">If the server is connected, the button text is **Connected**, and the button is dimmed.</span></span>  
  
 <span data-ttu-id="4291b-130">**臨界值**</span><span class="sxs-lookup"><span data-stu-id="4291b-130">**Thresholds**</span></span>  
 <span data-ttu-id="4291b-131">[臨界值] 方格會顯示這兩個伺服器執行個體的警告設定。</span><span class="sxs-lookup"><span data-stu-id="4291b-131">The **Thresholds** grid displays the warnings settings for the two server instances.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4291b-132">如果伺服器執行個體處於未連接狀態，則其資料行會顯示空的資料格和灰色背景。</span><span class="sxs-lookup"><span data-stu-id="4291b-132">If a server instance is not connected, its columns are displayed with empty cells and a gray background.</span></span> <span data-ttu-id="4291b-133">當連接開啟時，方格便會自動顯示執行個體的內容。</span><span class="sxs-lookup"><span data-stu-id="4291b-133">When the connection opens, the grid automatically displays the content from the instance.</span></span>  
  
 <span data-ttu-id="4291b-134">方格包含下列資料行：</span><span class="sxs-lookup"><span data-stu-id="4291b-134">The grid contains the following columns:</span></span>  
  
 <span data-ttu-id="4291b-135">**警告**</span><span class="sxs-lookup"><span data-stu-id="4291b-135">**Warnings**</span></span>  
 <span data-ttu-id="4291b-136">列出支援的警告：</span><span class="sxs-lookup"><span data-stu-id="4291b-136">Lists the supported warnings:</span></span>  
  
|<span data-ttu-id="4291b-137">警告</span><span class="sxs-lookup"><span data-stu-id="4291b-137">Warning</span></span>|<span data-ttu-id="4291b-138">描述</span><span class="sxs-lookup"><span data-stu-id="4291b-138">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4291b-139">**如果未傳送的記錄超過臨界值，即發出警告**</span><span class="sxs-lookup"><span data-stu-id="4291b-139">**Warn if the unsent log exceeds the threshold**</span></span>|<span data-ttu-id="4291b-140">這個臨界值會指出主體伺服器執行個體上傳送佇列中未傳送記錄的 KB 數。</span><span class="sxs-lookup"><span data-stu-id="4291b-140">The threshold indicates the number of kilobytes (KB) of the unsent log in the send queue on the principal.</span></span>|  
|<span data-ttu-id="4291b-141">**如果未還原的記錄超過臨界值，即發出警告**</span><span class="sxs-lookup"><span data-stu-id="4291b-141">**Warn if the unrestored log exceeds the threshold**</span></span>|<span data-ttu-id="4291b-142">這個臨界值會指出鏡像伺服器執行個體上重做佇列中的 KB 數。</span><span class="sxs-lookup"><span data-stu-id="4291b-142">The threshold indicates the number of KB of the redo queue on the mirror server instance.</span></span>|  
|<span data-ttu-id="4291b-143">**如果最舊未傳送交易的時間超過臨界值，即發出警告**</span><span class="sxs-lookup"><span data-stu-id="4291b-143">**Warn if the age of the oldest unsent transaction exceeds the threshold**</span></span>|<span data-ttu-id="4291b-144">這個臨界值會指出尚未從傳送佇列中傳送到鏡像伺服器執行個體的交易分鐘數。</span><span class="sxs-lookup"><span data-stu-id="4291b-144">The threshold indicates the number of minutes of transactions that have not yet been sent from the send queue to the mirror server instance.</span></span> <span data-ttu-id="4291b-145">這個值有助於從時間方面來測量資料遺失的可能性。</span><span class="sxs-lookup"><span data-stu-id="4291b-145">This value helps measure the potential for data loss in terms of time.</span></span>|  
|<span data-ttu-id="4291b-146">**如果鏡像認可負擔超過臨界值，即發出警告**</span><span class="sxs-lookup"><span data-stu-id="4291b-146">**Warn if the mirror commit overhead exceeds the threshold**</span></span>|<span data-ttu-id="4291b-147">這個臨界值會指出每項交易的延遲毫秒數 (只有在高安全性模式中才相關)。</span><span class="sxs-lookup"><span data-stu-id="4291b-147">The threshold indicates the number of milliseconds of delay per transaction (relevant only in high-safety mode).</span></span> <span data-ttu-id="4291b-148">這項延遲是當主體伺服器執行個體等待鏡像伺服器執行個體將交易記錄寫入重做佇列中時所產生的負擔量。</span><span class="sxs-lookup"><span data-stu-id="4291b-148">This delay is the amount of overhead incurred while the principal server instance waits for the mirror server instance to write the transaction's log record into the redo queue.</span></span>|  
  
 <span data-ttu-id="4291b-149">**已於 '** *\<server instance>* **' 啟用**</span><span class="sxs-lookup"><span data-stu-id="4291b-149">**Enabled at '** *\<server instance>* **'**</span></span>  
 <span data-ttu-id="4291b-150">如果此核取方塊空白，則表示伺服器執行個體上的警告目前已停用。</span><span class="sxs-lookup"><span data-stu-id="4291b-150">A blank check box indicates that the warning is currently disabled on the server instance.</span></span> <span data-ttu-id="4291b-151">若要啟用警告，請按一下其核取方塊。</span><span class="sxs-lookup"><span data-stu-id="4291b-151">To enable a warning, click its check box.</span></span>  
  
 <span data-ttu-id="4291b-152">**於 '** *\<server instance>* **' 的臨界值**</span><span class="sxs-lookup"><span data-stu-id="4291b-152">**Threshold at '** *\<server instance>* **'**</span></span>  
 <span data-ttu-id="4291b-153">啟用警告時，請在這個資料行的左邊設定臨界值。</span><span class="sxs-lookup"><span data-stu-id="4291b-153">When a warning is enabled, set the threshold on the left side of this column.</span></span> <span data-ttu-id="4291b-154">如果在更新狀態資料表時已達到指定的臨界值，則會發生事件。</span><span class="sxs-lookup"><span data-stu-id="4291b-154">An event occurs if the specified threshold has been reached when the status table is updated.</span></span> <span data-ttu-id="4291b-155">如果您在設定值之後停用臨界值，則該值仍會保留在這個欄位中，只要重新啟用警告即可使用。</span><span class="sxs-lookup"><span data-stu-id="4291b-155">If you disable a threshold after configuring a value, your value remains in this field and will be used if you re-enable the warning.</span></span>  
  
 <span data-ttu-id="4291b-156">如果警告並未啟用，則這個欄位將處於非使用中狀態。</span><span class="sxs-lookup"><span data-stu-id="4291b-156">When a warning is not enabled, this field is inactive.</span></span>  
  
 <span data-ttu-id="4291b-157">**確定**</span><span class="sxs-lookup"><span data-stu-id="4291b-157">**OK**</span></span>  
 <span data-ttu-id="4291b-158">按一下 [確定] 關閉這個對話方塊，並且將目前指定的警告臨界值顯示在 [警告] 索引標籤頁面上的 [臨界值] 方格中。</span><span class="sxs-lookup"><span data-stu-id="4291b-158">Clicking **OK** closes this dialog box and displays the currently specified values of warning thresholds in the **Thresholds** grid on the **Warnings**tabbed page.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4291b-159">備註</span><span class="sxs-lookup"><span data-stu-id="4291b-159">Remarks</span></span>  
 <span data-ttu-id="4291b-160">臨界值一次只能適用於一個夥伴，但是，建議您針對兩個夥伴上的特定事件都設定臨界值，以確保如果資料庫發生容錯移轉時，警告都能持續顯示。</span><span class="sxs-lookup"><span data-stu-id="4291b-160">A threshold is only applicable at one partner at a time, but we recommend that you set a threshold for a given event on both partners to ensure that the warning persists if the database fails over.</span></span> <span data-ttu-id="4291b-161">適合於每個夥伴的臨界值需視該夥伴系統的效能功能而定。</span><span class="sxs-lookup"><span data-stu-id="4291b-161">The appropriate threshold for each partner depends on the performance capabilities of that partner's system.</span></span>  
  
 <span data-ttu-id="4291b-162">在更新狀態資料表時，只有當效能值達到或超過臨界值時，才會將事件寫入該效能的事件記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="4291b-162">An event is written to the event log for a performance only if its value is at or above its threshold when the status table is being updated.</span></span> <span data-ttu-id="4291b-163">如果尖峰值只在兩次狀態更新之間短暫達到臨界值，則會遺漏該尖峰值。</span><span class="sxs-lookup"><span data-stu-id="4291b-163">If a peak value reaches the threshold momentarily between status updates that peak is missed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4291b-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4291b-164">See Also</span></span>  
 <span data-ttu-id="4291b-165">[啟動資料庫鏡像監視器 &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="4291b-165">[Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="4291b-166">[監視資料庫鏡像 &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4291b-166">[Monitoring Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="4291b-167">啟動設定資料庫鏡像安全性精靈 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="4291b-167">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
  
