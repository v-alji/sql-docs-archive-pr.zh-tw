---
title: 使用 system_health 工作階段 | Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- extended events [SQL Server], system health session
- extended events [SQL Server], system_health session
- system_health session [SQL Server extended events]
- system health session [SQL Server extended events]
ms.assetid: 1e1fad43-d747-4775-ac0d-c50648e56d78
author: yualan
ms.author: alayu
ms.openlocfilehash: 86c3221fb4c0ea0690b369888ac8f2f9f82d6ef9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585398"
---
# <a name="use-the-system_health-session"></a><span data-ttu-id="4aa1f-102">使用 system_health 工作階段</span><span class="sxs-lookup"><span data-stu-id="4aa1f-102">Use the system_health Session</span></span>
  <span data-ttu-id="4aa1f-103">system_health 工作階段是預設隨附於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的擴充事件工作階段。</span><span class="sxs-lookup"><span data-stu-id="4aa1f-103">The system_health session is an Extended Events session that is included by default with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4aa1f-104">當 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 啟動時，這個工作階段就會自動啟動，並且在不造成任何明顯效能影響的情況下執行。</span><span class="sxs-lookup"><span data-stu-id="4aa1f-104">This session starts automatically when the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] starts, and runs without any noticeable performance effects.</span></span> <span data-ttu-id="4aa1f-105">此工作階段會收集系統資料，讓您能夠用來協助疑難排解 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的效能問題。</span><span class="sxs-lookup"><span data-stu-id="4aa1f-105">The session collects system data that you can use to help troubleshoot performance issues in the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="4aa1f-106">因此，我們建議您不要停止或刪除此工作階段。</span><span class="sxs-lookup"><span data-stu-id="4aa1f-106">Therefore, we recommend that you do not stop or delete the session.</span></span>  
  
 <span data-ttu-id="4aa1f-107">此工作階段所收集的資訊包括：</span><span class="sxs-lookup"><span data-stu-id="4aa1f-107">The session collects information that includes the following:</span></span>  
  
-   <span data-ttu-id="4aa1f-108">任何遇到嚴重性 >=20 錯誤之工作階段的 sql_text 和 session_id。</span><span class="sxs-lookup"><span data-stu-id="4aa1f-108">The sql_text and session_id for any sessions that encounter an error that has a severity >=20.</span></span>  
  
-   <span data-ttu-id="4aa1f-109">任何遇到記憶體相關錯誤之工作階段的 sql_text 和 session_id。</span><span class="sxs-lookup"><span data-stu-id="4aa1f-109">The sql_text and session_id for any sessions that encounter a memory-related error.</span></span> <span data-ttu-id="4aa1f-110">這些錯誤包括 17803、701、802、8645、8651、8657 和 8902。</span><span class="sxs-lookup"><span data-stu-id="4aa1f-110">The errors include 17803, 701, 802, 8645, 8651, 8657 and 8902.</span></span>  
  
-   <span data-ttu-id="4aa1f-111">任何沒有產量之排程器問題的記錄</span><span class="sxs-lookup"><span data-stu-id="4aa1f-111">A record of any non-yielding scheduler problems.</span></span> <span data-ttu-id="4aa1f-112">(這些問題會在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔中顯示成錯誤 17883)。</span><span class="sxs-lookup"><span data-stu-id="4aa1f-112">(These appear in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log as error 17883.)</span></span>  
  
-   <span data-ttu-id="4aa1f-113">偵測到的任何死結。</span><span class="sxs-lookup"><span data-stu-id="4aa1f-113">Any deadlocks that are detected.</span></span>  
  
-   <span data-ttu-id="4aa1f-114">任何已經等候閂鎖 (或其他相關資源) > 15 秒之工作階段的 callstack、sql_text 和 session_id。</span><span class="sxs-lookup"><span data-stu-id="4aa1f-114">The callstack, sql_text, and session_id for any sessions that have waited on latches (or other interesting resources) for > 15 seconds.</span></span>  
  
-   <span data-ttu-id="4aa1f-115">任何已經等候鎖定 > 30 秒之工作階段的 callstack、sql_text 和 session_id。</span><span class="sxs-lookup"><span data-stu-id="4aa1f-115">The callstack, sql_text, and session_id for any sessions that have waited on locks for > 30 seconds.</span></span>  
  
-   <span data-ttu-id="4aa1f-116">任何已經等候先佔式等候一段長時間之工作階段的 callstack、sql_text 和 session_id。</span><span class="sxs-lookup"><span data-stu-id="4aa1f-116">The callstack, sql_text, and session_id for any sessions that have waited for a long time for preemptive waits.</span></span> <span data-ttu-id="4aa1f-117">此持續時間會因等候類型而異。</span><span class="sxs-lookup"><span data-stu-id="4aa1f-117">The duration varies by wait type.</span></span> <span data-ttu-id="4aa1f-118">先佔式等候是指 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 等候外部 API 呼叫的位置。</span><span class="sxs-lookup"><span data-stu-id="4aa1f-118">A preemptive wait is where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is waiting for external API calls.</span></span>  
  
-   <span data-ttu-id="4aa1f-119">CLR 配置和虛擬配置失敗的呼叫堆疊與 session_id。</span><span class="sxs-lookup"><span data-stu-id="4aa1f-119">The callstack and session_id for CLR allocation and virtual allocation failures.</span></span>  
  
-   <span data-ttu-id="4aa1f-120">記憶體 Broker、排程器監視器、記憶體節點 OOM、安全性和連接性的 ring_buffer 事件。</span><span class="sxs-lookup"><span data-stu-id="4aa1f-120">The ring_buffer events for the memory broker, scheduler monitor, memory node OOM, security, and connectivity.</span></span>  
  
-   <span data-ttu-id="4aa1f-121">來自 sp_server_diagnostics 的系統元件結果。</span><span class="sxs-lookup"><span data-stu-id="4aa1f-121">System component results from sp_server_diagnostics.</span></span>  
  
-   <span data-ttu-id="4aa1f-122">scheduler_monitor_system_health_ring_buffer_recorded 所收集的執行個體健全狀況。</span><span class="sxs-lookup"><span data-stu-id="4aa1f-122">Instance health collected by scheduler_monitor_system_health_ring_buffer_recorded.</span></span>  
  
-   <span data-ttu-id="4aa1f-123">CLR 配置失敗。</span><span class="sxs-lookup"><span data-stu-id="4aa1f-123">CLR Allocation failures.</span></span>  
  
-   <span data-ttu-id="4aa1f-124">使用 connectivity_ring_buffer_recorded 的連接錯誤。</span><span class="sxs-lookup"><span data-stu-id="4aa1f-124">Connectivity errors using connectivity_ring_buffer_recorded.</span></span>  
  
-   <span data-ttu-id="4aa1f-125">使用 security_error_ring_buffer_recorded 的安全性錯誤。</span><span class="sxs-lookup"><span data-stu-id="4aa1f-125">Security errors using security_error_ring_buffer_recorded.</span></span>  
  
## <a name="viewing-the-session-data"></a><span data-ttu-id="4aa1f-126">檢視工作階段資料</span><span class="sxs-lookup"><span data-stu-id="4aa1f-126">Viewing the Session Data</span></span>  
 <span data-ttu-id="4aa1f-127">工作階段會使用信號緩衝區目標來儲存資料。</span><span class="sxs-lookup"><span data-stu-id="4aa1f-127">The session uses the ring buffer target to store the data.</span></span> <span data-ttu-id="4aa1f-128">若要檢視工作階段資料，請使用下列查詢：</span><span class="sxs-lookup"><span data-stu-id="4aa1f-128">To view the session data, use the following query:</span></span>  
  
```  
SELECT CAST(xet.target_data as xml) FROM sys.dm_xe_session_targets xet  
JOIN sys.dm_xe_sessions xe  
ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'system_health'  
```  
  
 <span data-ttu-id="4aa1f-129">若要檢視事件檔案中的工作階段資料，請使用 Management Studio 中提供的「擴充事件」使用者介面。</span><span class="sxs-lookup"><span data-stu-id="4aa1f-129">To view the session data from the event file, use the Extended Events user interface available in Management Studio.</span></span> <span data-ttu-id="4aa1f-130">如需相關資訊，請參閱 [View Event Session Data](../../database-engine/view-event-session-data.md) 。</span><span class="sxs-lookup"><span data-stu-id="4aa1f-130">See [View Event Session Data](../../database-engine/view-event-session-data.md) for more information.</span></span>  
  
## <a name="restoring-the-system_health-session"></a><span data-ttu-id="4aa1f-131">還原 system_health 工作階段</span><span class="sxs-lookup"><span data-stu-id="4aa1f-131">Restoring the system_health Session</span></span>  
 <span data-ttu-id="4aa1f-132">如果您刪除了 system_health 工作階段，可以在 [查詢編輯器] 中執行 **u_tables.sql** 檔案，藉以還原此工作階段。</span><span class="sxs-lookup"><span data-stu-id="4aa1f-132">If you delete the system_health session, you can restore it by executing the **u_tables.sql** file in Query Editor.</span></span> <span data-ttu-id="4aa1f-133">這個檔案位於下列資料夾，其中 C: 代表您安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 程式檔案的磁碟機：</span><span class="sxs-lookup"><span data-stu-id="4aa1f-133">This file is located in the following folder, where C: represents the drive where you installed the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] program files:</span></span>  
  
 <span data-ttu-id="4aa1f-134">C:\Program Files\Microsoft SQL Server\MSSQL12. \<*instanceid*>\MSSQL\Install</span><span class="sxs-lookup"><span data-stu-id="4aa1f-134">C:\Program Files\Microsoft SQL Server\MSSQL12.\<*instanceid*>\MSSQL\Install</span></span>  
  
 <span data-ttu-id="4aa1f-135">請注意，當您還原此工作階段之後，必須使用 ALTER EVENT SESSION 陳述式或 [物件總管] 中的 **[擴充事件]** 節點來啟動此工作階段。</span><span class="sxs-lookup"><span data-stu-id="4aa1f-135">Be aware that after you restore the session, you must start the session by using the ALTER EVENT SESSION statement or by using the **Extended Events** node in Object Explorer.</span></span> <span data-ttu-id="4aa1f-136">否則，此工作階段會在您下一次重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務時自動啟動。</span><span class="sxs-lookup"><span data-stu-id="4aa1f-136">Otherwise, the session starts automatically the next time that you restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4aa1f-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4aa1f-137">See Also</span></span>  
 [<span data-ttu-id="4aa1f-138">擴充事件工具</span><span class="sxs-lookup"><span data-stu-id="4aa1f-138">Extended Events Tools</span></span>](extended-events-tools.md)  
  
  
