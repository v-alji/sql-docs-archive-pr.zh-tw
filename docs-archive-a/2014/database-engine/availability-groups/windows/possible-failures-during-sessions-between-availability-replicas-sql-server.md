---
title: 工作階段期間可用性複本之間可能發生失敗 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- troubleshooting [SQL Server, HADR]
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], troubleshooting
ms.assetid: cd613898-82d9-482f-a255-0230a6c7d6fe
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4cfacb7f7c75875d4f5d0b0b435d282b3f537cc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703294"
---
# <a name="possible-failures-during-sessions-between-availability-replicas-sql-server"></a><span data-ttu-id="336da-102">工作階段期間可用性複本之間可能發生失敗 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="336da-102">Possible Failures During Sessions Between Availability Replicas (SQL Server)</span></span>
  <span data-ttu-id="336da-103">實體、作業系統或 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 問題都可能會在兩個可用性複本之間的工作階段中導致失敗。</span><span class="sxs-lookup"><span data-stu-id="336da-103">Physical, operating system, or [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] problems can cause a failure in a session between two availability replicas.</span></span> <span data-ttu-id="336da-104">可用性複本不會為了確認 Sqlservr.exe 所依賴的元件是正常運作或已失敗，而定期檢查這些元件。</span><span class="sxs-lookup"><span data-stu-id="336da-104">An availability replica does not regularly check the components on which Sqlservr.exe relies to verify whether they are functioning correctly or have failed.</span></span> <span data-ttu-id="336da-105">不過，針對某些類型的錯誤，受影響的元件會對 Sqlservr.exe 報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="336da-105">However, for some types of failures, the affected component reports an error to Sqlservr.exe.</span></span> <span data-ttu-id="336da-106">由其他元件所報告的錯誤稱為「重大錯誤」(Hard Error)。</span><span class="sxs-lookup"><span data-stu-id="336da-106">An error reported by another component is called a *hard error*.</span></span> <span data-ttu-id="336da-107">為了偵測其他沒有通知的失敗，[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]會實作其本身的工作階段逾時機制。</span><span class="sxs-lookup"><span data-stu-id="336da-107">To detect other failures that would otherwise go unnoticed, [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] implements its own session-timeout mechanism.</span></span> <span data-ttu-id="336da-108">指定工作階段逾時期限 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="336da-108">Specifies the session-timeout period in seconds.</span></span> <span data-ttu-id="336da-109">逾時期限是伺服器執行個體在將另一個執行個體視為中斷連接之前，等待接收該執行個體發出之 PING 訊息的最長時間。</span><span class="sxs-lookup"><span data-stu-id="336da-109">This time-out period is the maximum time that a server instance waits to receive a PING message from another instance before considering that other instance to be disconnected.</span></span> <span data-ttu-id="336da-110">如果兩個可用性複本之間發生工作階段逾時，可用性複本會假設失敗已經發生，並宣告「軟體錯誤」\*\*。</span><span class="sxs-lookup"><span data-stu-id="336da-110">When a session timeout occurs between two availability replicas, the availability replicas assume that a failure has occurred and declares a *soft error*.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="336da-111">系統無法偵測主要資料庫以外之資料庫中的失敗。</span><span class="sxs-lookup"><span data-stu-id="336da-111">Failures in databases other than the primary database are not detectable.</span></span> <span data-ttu-id="336da-112">此外，除非是因為資料磁碟錯誤而重新啟動資料庫，否則不太可能偵測得到資料磁碟錯誤。</span><span class="sxs-lookup"><span data-stu-id="336da-112">Moreover, a data disk failure is unlikely to be detected unless the database is restarted because of a data disk failure.</span></span>  
  
 <span data-ttu-id="336da-113">錯誤偵測的速度以及失敗的反應時間，取決於錯誤為硬性或軟性。</span><span class="sxs-lookup"><span data-stu-id="336da-113">The speed of error detection and, therefore, the reaction time to a failure, depends on whether the error is hard or soft.</span></span> <span data-ttu-id="336da-114">某些硬性錯誤，如網路失敗，會立即報告。</span><span class="sxs-lookup"><span data-stu-id="336da-114">Some hard errors, such as network failures are reported immediately.</span></span> <span data-ttu-id="336da-115">不過，有些情況下，元件專用的逾時期限可以使某些硬性錯誤延遲報告。</span><span class="sxs-lookup"><span data-stu-id="336da-115">However, in some cases, component-specific time-out periods can delay the reporting of some hard errors.</span></span> <span data-ttu-id="336da-116">至於軟體錯誤，工作階段逾時期限的長度將決定錯誤偵測的速度。</span><span class="sxs-lookup"><span data-stu-id="336da-116">For soft errors, the length of the session-timeout period determines the speed of error detection.</span></span> <span data-ttu-id="336da-117">此期限長度預設為 10 秒。</span><span class="sxs-lookup"><span data-stu-id="336da-117">By default, this period is 10 seconds.</span></span> <span data-ttu-id="336da-118">這是最小的建議值。</span><span class="sxs-lookup"><span data-stu-id="336da-118">This is the minimum recommended value.</span></span>  
  
## <a name="failures-due-to-hard-errors"></a><span data-ttu-id="336da-119">硬性錯誤造成的失敗</span><span class="sxs-lookup"><span data-stu-id="336da-119">Failures Due to Hard Errors</span></span>  
 <span data-ttu-id="336da-120">硬性錯誤的可能原因包含 (但不限於) 下列狀況：</span><span class="sxs-lookup"><span data-stu-id="336da-120">Possible causes of hard errors include (but are not limited to) the following conditions:</span></span>  
  
-   <span data-ttu-id="336da-121">連接或連線中斷</span><span class="sxs-lookup"><span data-stu-id="336da-121">A broken connection or wire</span></span>  
  
-   <span data-ttu-id="336da-122">網路卡損毀</span><span class="sxs-lookup"><span data-stu-id="336da-122">A bad network card</span></span>  
  
-   <span data-ttu-id="336da-123">路由器變更</span><span class="sxs-lookup"><span data-stu-id="336da-123">A router change</span></span>  
  
-   <span data-ttu-id="336da-124">防火牆變更</span><span class="sxs-lookup"><span data-stu-id="336da-124">Changes in the firewall</span></span>  
  
-   <span data-ttu-id="336da-125">端點重新設定</span><span class="sxs-lookup"><span data-stu-id="336da-125">Endpoint reconfiguration</span></span>  
  
-   <span data-ttu-id="336da-126">找不到交易記錄所在的磁碟機</span><span class="sxs-lookup"><span data-stu-id="336da-126">Loss of the drive where the transaction log resides</span></span>  
  
-   <span data-ttu-id="336da-127">作業系統或處理序失敗</span><span class="sxs-lookup"><span data-stu-id="336da-127">Operating system or process failure</span></span>  
  
 <span data-ttu-id="336da-128">例如，如果主要資料庫的記錄磁碟機無法回應並故障，作業系統就會通知 Sqlservr.exe，已發生嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="336da-128">For example, when the log drive on the primary database becomes unresponsive and fails, the operating system informs Sqlservr.exe that a serious error has occurred.</span></span>  
  
 <span data-ttu-id="336da-129">某些元件 (例如，網路元件和某些 IO 子系統) 會有它們自訂的逾時，可以判斷錯誤。</span><span class="sxs-lookup"><span data-stu-id="336da-129">Some components, such as network components and some IO subsystems, have their own time-outs to determine failures.</span></span> <span data-ttu-id="336da-130">這類逾時與 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]無關，它對此一無所知，而且完全不會察覺這些逾時行為。</span><span class="sxs-lookup"><span data-stu-id="336da-130">Such time-outs are independent of [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], which has no knowledge of them and is completely unaware of their behavior.</span></span> <span data-ttu-id="336da-131">在這些情況下，逾時延遲會增加從失敗發生到可用性複本收到產生的硬性錯誤之間的時間。</span><span class="sxs-lookup"><span data-stu-id="336da-131">In these cases, the time-out delay increases the time between a failure and when the availability replica receives the resulting hard error.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="336da-132">唯一針對可用性複本執行的主動錯誤檢查，只會在發生軟體錯誤的情況下進行。</span><span class="sxs-lookup"><span data-stu-id="336da-132">The only active error checking performed for availability replicas occurs for soft error cases.</span></span> <span data-ttu-id="336da-133">如需詳細資訊，請參閱本主題後面的「軟性錯誤造成的失敗」。</span><span class="sxs-lookup"><span data-stu-id="336da-133">For more information, see "Failures Due to Soft Errors," later in this topic.</span></span>  
  
 <span data-ttu-id="336da-134">為了協助您解讀網路上發生的錯誤狀況，請詢問網路工程師，在 TCP 連接發生下列事件時，會將什麼錯誤訊息傳送至通訊埠：</span><span class="sxs-lookup"><span data-stu-id="336da-134">To help you interpret the error conditions that occur on the network, ask a network engineer what error messages are sent to a port when the following events occur on a TCP connection:</span></span>  
  
-   <span data-ttu-id="336da-135">DNS 沒有作用。</span><span class="sxs-lookup"><span data-stu-id="336da-135">DNS is not working.</span></span>  
  
-   <span data-ttu-id="336da-136">未插上纜線。</span><span class="sxs-lookup"><span data-stu-id="336da-136">Cables are unplugged.</span></span>  
  
-   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="336da-137">Windows 具有封鎖特定通訊埠的防火牆。</span><span class="sxs-lookup"><span data-stu-id="336da-137">Windows has a firewall that blocks a specific port.</span></span>  
  
-   <span data-ttu-id="336da-138">正在監視通訊埠的應用程式失敗。</span><span class="sxs-lookup"><span data-stu-id="336da-138">The application that is monitoring a port fails.</span></span>  
  
-   <span data-ttu-id="336da-139">已重新命名 Windows 伺服器。</span><span class="sxs-lookup"><span data-stu-id="336da-139">A Windows-based server is renamed.</span></span>  
  
-   <span data-ttu-id="336da-140">已重新啟動 Windows 伺服器。</span><span class="sxs-lookup"><span data-stu-id="336da-140">A Windows-based server is rebooted.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="336da-141">對於用戶端存取伺服器方面的特定問題，[!INCLUDE[ssHADRc](../../../includes/sshadrc-md.md)]無法加以防止。</span><span class="sxs-lookup"><span data-stu-id="336da-141">[!INCLUDE[ssHADRc](../../../includes/sshadrc-md.md)] does not protect against problems specific to client accessing the servers.</span></span> <span data-ttu-id="336da-142">例如，試想一個情況，公用網路介面卡處理對主要複本的用戶端連接，而私人網路介面卡則處理裝載可用性群組之複本的伺服器執行個體之間的流量。</span><span class="sxs-lookup"><span data-stu-id="336da-142">For example, consider a case in which a public network adapter handles client connections to the primary replica, while a private network interface card handles traffic among the server instances that are hosting the replicas of an availability group.</span></span> <span data-ttu-id="336da-143">在這個情況下，公用網路介面卡的失敗將會阻止用戶端存取資料庫。</span><span class="sxs-lookup"><span data-stu-id="336da-143">In this case, failure of the public network adapter would prevent clients from accessing the databases.</span></span>  
  
## <a name="failures-due-to-soft-errors"></a><span data-ttu-id="336da-144">軟性錯誤造成的失敗</span><span class="sxs-lookup"><span data-stu-id="336da-144">Failures Due to Soft Errors</span></span>  
 <span data-ttu-id="336da-145">可能會造成工作階段逾時的狀況包括 (但不限於) 下列狀況：</span><span class="sxs-lookup"><span data-stu-id="336da-145">Conditions that might cause session timeouts include (but are not limited to) the following:</span></span>  
  
-   <span data-ttu-id="336da-146">網路錯誤，例如 TCP 連結逾時、卸除或損毀的封包或順序不正確的封包。</span><span class="sxs-lookup"><span data-stu-id="336da-146">Network errors such as TCP link time-outs, dropped or corrupted packets, or packets that are in an incorrect order.</span></span>  
  
-   <span data-ttu-id="336da-147">沒有回應的作業系統、伺服器或資料庫。</span><span class="sxs-lookup"><span data-stu-id="336da-147">An operating system, server, or database that is not responding.</span></span>  
  
-   <span data-ttu-id="336da-148">Windows 伺服器逾時。</span><span class="sxs-lookup"><span data-stu-id="336da-148">A Windows server timing out.</span></span>  
  
-   <span data-ttu-id="336da-149">運算資源不足，例如 CPU 或磁碟負擔過重、交易記錄已滿，或系統的記憶體或執行緒用盡。</span><span class="sxs-lookup"><span data-stu-id="336da-149">Insufficient computing resources, such as a CPU or disk overload, the transaction log filling up, or the system is running out of memory or threads.</span></span> <span data-ttu-id="336da-150">在這些情況下，您必須增加逾時期限、降低工作負載或更換硬體來因應工作負載。</span><span class="sxs-lookup"><span data-stu-id="336da-150">In these cases, you must increase the time-out period, reduce the workload, or change the hardware to handle the workload.</span></span>  
  
### <a name="the-session-timeout-mechanism"></a><span data-ttu-id="336da-151">工作階段逾時機制</span><span class="sxs-lookup"><span data-stu-id="336da-151">The Session-Timeout Mechanism</span></span>  
 <span data-ttu-id="336da-152">因為伺服器執行個體無法直接偵測到軟性錯誤，所以軟性錯誤可能會造成可用性複本在工作階段中永遠等候來自另一個可用性複本的回應。</span><span class="sxs-lookup"><span data-stu-id="336da-152">Because soft errors are not detectable directly by a server instance, a soft error could potentially cause an availability replica to wait indefinitely for a response from the other availability replica in a session.</span></span> <span data-ttu-id="336da-153">為了避免這種狀況， [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 會實作工作階段逾時機制，而在此機制中，連接的可用性複本都會以固定間隔在每個開啟連接上送出 Ping。</span><span class="sxs-lookup"><span data-stu-id="336da-153">To prevent this, [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] implements a session time-out mechanism, based on the connected availability replicas sending out a ping on each open connection at a fixed interval.</span></span> <span data-ttu-id="336da-154">在逾時期限接收到 Ping，表示連接仍為開啟狀態，且伺服器執行個體是透過它進行通訊。</span><span class="sxs-lookup"><span data-stu-id="336da-154">Receiving a ping during the time-out period indicates that the connection is still open and that the server instances are communicating over it.</span></span> <span data-ttu-id="336da-155">接收到 Ping 時，複本會重設它在該連接上的逾時計數器。</span><span class="sxs-lookup"><span data-stu-id="336da-155">On receiving a ping, a replica resets its time-out counter on that connection.</span></span> <span data-ttu-id="336da-156">如需可用性模式和會話超時關聯性的詳細資訊，請參閱[可用性模式 (AlwaysOn 可用性群組) ](availability-modes-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="336da-156">For information about the relationship of availability mode and session timeouts, see [Availability Modes (AlwaysOn Availability Groups)](availability-modes-always-on-availability-groups.md).</span></span>  
  
 <span data-ttu-id="336da-157">主要和次要複本會互相執行 Ping，讓對方知道他們仍在作用中，而工作階段逾時限制則可防止任一複本無限期地等候接收來自另一複本的 Ping。</span><span class="sxs-lookup"><span data-stu-id="336da-157">The primary and secondary replicas ping each other to signal that they are still active, and a session-timeout limit prevents either replica from waiting indefinitely to receive a ping from the other replica.</span></span> <span data-ttu-id="336da-158">工作階段逾時限制是使用者可設定的複本屬性，其預設值為 10 秒。</span><span class="sxs-lookup"><span data-stu-id="336da-158">The session-timeout limit is a user-configurable replica property with a default value of 10 seconds.</span></span> <span data-ttu-id="336da-159">在逾時期限接收到 Ping，表示連接仍為開啟狀態，且伺服器執行個體是透過它進行通訊。</span><span class="sxs-lookup"><span data-stu-id="336da-159">Receiving a ping during the time-out period indicates that the connection is still open and that the server instances are communicating over it.</span></span> <span data-ttu-id="336da-160">接收到 Ping 時，可用性複本會重設它在該連接上的逾時計數器。</span><span class="sxs-lookup"><span data-stu-id="336da-160">On receiving a ping, an availability replica resets its time-out counter on that connection.</span></span>  
  
 <span data-ttu-id="336da-161">如果在會話超時期間內未收到來自另一個複本的 ping，則連接逾時。連接會關閉，而超時複本則進入中斷連線的狀態。</span><span class="sxs-lookup"><span data-stu-id="336da-161">If no ping is received from the other replica within the session-timeout period, the connection times out. The connection is closed, and the timed-out replica enters the DISCONNECTED state.</span></span> <span data-ttu-id="336da-162">即使中斷連接的複本設定成同步認可模式，交易仍不會等候該複本重新連接及重新同步處理。</span><span class="sxs-lookup"><span data-stu-id="336da-162">Even if a disconnected replica is configured for synchronous-commit mode, transactions will not wait for that replica to reconnect and resynchronize.</span></span>  
  
## <a name="responding-to-an-error"></a><span data-ttu-id="336da-163">回應錯誤</span><span class="sxs-lookup"><span data-stu-id="336da-163">Responding to an Error</span></span>  
 <span data-ttu-id="336da-164">不論錯誤的類型為何，偵測到錯誤的伺服器執行個體都會根據執行個體的角色、工作階段的可用性模式和工作階段中其他連接的狀態，進行適當的回應。</span><span class="sxs-lookup"><span data-stu-id="336da-164">Regardless of the type of error, a server instance that detects an error responds appropriately based on the role of the instance, the availability mode of the session, and the state of any other connection in the session.</span></span> <span data-ttu-id="336da-165">如需有關遺失夥伴時所發生之情況的詳細資訊，請參閱[可用性模式 (AlwaysOn 可用性群組) ](availability-modes-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="336da-165">For information about what occurs on the loss of a partner, see [Availability Modes (AlwaysOn Availability Groups)](availability-modes-always-on-availability-groups.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="336da-166">相關工作</span><span class="sxs-lookup"><span data-stu-id="336da-166">Related Tasks</span></span>  
 <span data-ttu-id="336da-167">**若要變更逾時值 (僅限同步認可可用性模式)**</span><span class="sxs-lookup"><span data-stu-id="336da-167">**To change the time-out value (synchronous-commit availability mode only)**</span></span>  
  
-   [<span data-ttu-id="336da-168">變更可用性複本的工作階段逾時期限 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="336da-168">Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 <span data-ttu-id="336da-169">**若要檢視目前的逾時值**</span><span class="sxs-lookup"><span data-stu-id="336da-169">**To view the current time-out value**</span></span>  
  
-   <span data-ttu-id="336da-170">查詢 [sys.availability_replicas &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql) 中的 **session_timeout**。</span><span class="sxs-lookup"><span data-stu-id="336da-170">Query **session_timeout** in [sys.availability_replicas &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="336da-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="336da-171">See Also</span></span>  
 [<span data-ttu-id="336da-172">AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;</span><span class="sxs-lookup"><span data-stu-id="336da-172">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
