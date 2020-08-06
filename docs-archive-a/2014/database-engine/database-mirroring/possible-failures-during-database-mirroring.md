---
title: 資料庫鏡像期間可能發生的失敗 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- time-out period [SQL Server database mirroring]
- soft errors [SQL Server]
- database mirroring [SQL Server], troubleshooting
- timeout errors [SQL Server]
- troubleshooting [SQL Server], database mirroring
- hard errors
- failed database mirroring sessions [SQL Server]
ms.assetid: d7031f58-5f49-4e6d-9a62-9b420f2bb17e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 25ba1ccc87c024fa3da370f2ff19251a1bee9f30
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701848"
---
# <a name="possible-failures-during-database-mirroring"></a><span data-ttu-id="71672-102">資料庫鏡像期間可能發生的失敗</span><span class="sxs-lookup"><span data-stu-id="71672-102">Possible Failures During Database Mirroring</span></span>
  <span data-ttu-id="71672-103">實體、作業系統或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 問題都可能會在資料庫鏡像工作階段中導致失敗。</span><span class="sxs-lookup"><span data-stu-id="71672-103">Physical, operating system, or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] problems can cause a failure in a database mirroring session.</span></span> <span data-ttu-id="71672-104">資料庫鏡像不會為了確認 Sqlservr.exe 所依賴的元件是正常運作或已失敗，而定期檢查這些元件。</span><span class="sxs-lookup"><span data-stu-id="71672-104">Database mirroring does not regularly check the components on which Sqlservr.exe relies to verify whether they are functioning correctly or have failed.</span></span> <span data-ttu-id="71672-105">不過，針對某些類型的錯誤，受影響的元件會對 Sqlservr.exe 報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="71672-105">However, for some types of failures, the affected component reports an error to Sqlservr.exe.</span></span> <span data-ttu-id="71672-106">由其他元件所報告的錯誤稱為「重大錯誤」(Hard Error)。</span><span class="sxs-lookup"><span data-stu-id="71672-106">An error reported by another component is called a *hard error*.</span></span> <span data-ttu-id="71672-107">為了偵測其他沒有通知的失敗，資料庫鏡像會實作其本身的逾時機制。</span><span class="sxs-lookup"><span data-stu-id="71672-107">To detect other failures that would otherwise go unnoticed, database mirroring implements its own time-out mechanism.</span></span> <span data-ttu-id="71672-108">當鏡像逾時發生時，資料庫鏡像會假設失敗已經發生，並宣告「軟性錯誤」。</span><span class="sxs-lookup"><span data-stu-id="71672-108">When a mirroring time-out occurs, database mirroring assumes that a failure has occurred and declares a *soft error*.</span></span> <span data-ttu-id="71672-109">但是，某些發生在 SQL Server 執行個體層級的失敗並不會造成鏡像逾時，而且可能無法偵測到。</span><span class="sxs-lookup"><span data-stu-id="71672-109">However, some failures that happen at the SQL Server instance level do not cause mirroring to time-out and can go undetected.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="71672-110">在資料庫鏡像工作階段中，偵測不到鏡像資料庫以外之資料庫中的失敗。</span><span class="sxs-lookup"><span data-stu-id="71672-110">Failures in databases other than the mirrored database are not detectable in a database mirroring session.</span></span> <span data-ttu-id="71672-111">而且，除非是因為資料磁碟失敗而重新啟動資料庫，否則不太可能偵測得到資料磁碟失敗。</span><span class="sxs-lookup"><span data-stu-id="71672-111">Moreover, a data disk failure is unlikely to be detected, unless the database is restarted because of a data disk failure.</span></span>  
  
 <span data-ttu-id="71672-112">錯誤偵測的速度以及受影響之鏡像工作階段對失敗的反應時間，取決於錯誤為硬性或軟性。</span><span class="sxs-lookup"><span data-stu-id="71672-112">The speed of error detection and, therefore, the reaction time of the mirroring session to a failure, depends on whether the error is hard or soft.</span></span> <span data-ttu-id="71672-113">某些硬性錯誤，如網路失敗，會立即報告。</span><span class="sxs-lookup"><span data-stu-id="71672-113">Some hard errors, such as network failures are reported immediately.</span></span> <span data-ttu-id="71672-114">不過，有些情況下，元件專用的逾時期限可以使某些硬性錯誤延遲報告。</span><span class="sxs-lookup"><span data-stu-id="71672-114">However, in some cases, component-specific time-out periods can delay the reporting of some hard errors.</span></span> <span data-ttu-id="71672-115">至於軟性錯誤，鏡像逾時期限的長度將決定錯誤偵測的速度。</span><span class="sxs-lookup"><span data-stu-id="71672-115">For soft errors, the length of the mirroring time-out period determines the speed of error detection.</span></span> <span data-ttu-id="71672-116">此期限長度預設為 10 秒。</span><span class="sxs-lookup"><span data-stu-id="71672-116">By default, this period is 10 seconds.</span></span> <span data-ttu-id="71672-117">這是最小的建議值。</span><span class="sxs-lookup"><span data-stu-id="71672-117">This is the minimum recommended value.</span></span>  
  
## <a name="failures-due-to-hard-errors"></a><span data-ttu-id="71672-118">硬性錯誤造成的失敗</span><span class="sxs-lookup"><span data-stu-id="71672-118">Failures Due to Hard Errors</span></span>  
 <span data-ttu-id="71672-119">硬性錯誤的可能原因包含 (但不限於) 下列狀況：</span><span class="sxs-lookup"><span data-stu-id="71672-119">Possible causes of hard errors include (but are not limited to) the following conditions:</span></span>  
  
-   <span data-ttu-id="71672-120">連接或連線中斷</span><span class="sxs-lookup"><span data-stu-id="71672-120">A broken connection or wire</span></span>  
  
-   <span data-ttu-id="71672-121">網路卡損毀</span><span class="sxs-lookup"><span data-stu-id="71672-121">A bad network card</span></span>  
  
-   <span data-ttu-id="71672-122">路由器變更</span><span class="sxs-lookup"><span data-stu-id="71672-122">A router change</span></span>  
  
-   <span data-ttu-id="71672-123">防火牆變更</span><span class="sxs-lookup"><span data-stu-id="71672-123">Changes in the firewall</span></span>  
  
-   <span data-ttu-id="71672-124">端點重新設定</span><span class="sxs-lookup"><span data-stu-id="71672-124">Endpoint reconfiguration</span></span>  
  
-   <span data-ttu-id="71672-125">找不到交易記錄所在的磁碟機</span><span class="sxs-lookup"><span data-stu-id="71672-125">Loss of the drive where the transaction log resides</span></span>  
  
-   <span data-ttu-id="71672-126">作業系統或處理序失敗</span><span class="sxs-lookup"><span data-stu-id="71672-126">Operating system or process failure</span></span>  
  
 <span data-ttu-id="71672-127">例如，如果主體資料庫的記錄磁碟機無法回應並故障，作業系統就會通知 Sqlservr.exe，已發生嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="71672-127">For example, when the log drive on the principal database becomes unresponsive and fails, the operating system informs Sqlservr.exe that a serious error has occurred.</span></span>  
  
 <span data-ttu-id="71672-128">某些元件 (例如，網路元件和某些 IO 子系統) 會有它們自訂的逾時，可以判斷錯誤。</span><span class="sxs-lookup"><span data-stu-id="71672-128">Some components, such as network components and some IO subsystems, have their own time-outs to determine failures.</span></span> <span data-ttu-id="71672-129">這類逾時與資料庫鏡像無關，資料庫鏡像對此一無所知，而且完全不會察覺這些逾時行為。</span><span class="sxs-lookup"><span data-stu-id="71672-129">Such time-outs are independent of database mirroring, which has no knowledge of them and is completely unaware of their behavior.</span></span> <span data-ttu-id="71672-130">在這些情況下，逾時延遲會增加從失敗發生到資料庫鏡像收到產生的硬性錯誤之間的時間。</span><span class="sxs-lookup"><span data-stu-id="71672-130">In these cases, the time-out delay increases the time between a failure and when database mirroring receive the resulting hard error.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="71672-131">唯一針對資料庫鏡像執行的主動錯誤檢查會針對軟性錯誤情況進行。</span><span class="sxs-lookup"><span data-stu-id="71672-131">The only active error checking performed for database mirroring occurs for soft error cases.</span></span> <span data-ttu-id="71672-132">如需詳細資訊，請參閱本主題後面的「軟性錯誤造成的失敗」。</span><span class="sxs-lookup"><span data-stu-id="71672-132">For more information, see "Failures Due to Soft Errors," later in this topic.</span></span>  
  
 <span data-ttu-id="71672-133">為了協助您解讀網路上發生的錯誤狀況，請詢問網路工程師，在 TCP 連接發生下列事件時，會將什麼錯誤訊息傳送至通訊埠：</span><span class="sxs-lookup"><span data-stu-id="71672-133">To help you interpret the error conditions that occur on the network, ask a network engineer what error messages are sent to a port when the following events occur on a TCP connection:</span></span>  
  
-   <span data-ttu-id="71672-134">DNS 沒有作用。</span><span class="sxs-lookup"><span data-stu-id="71672-134">DNS is not working.</span></span>  
  
-   <span data-ttu-id="71672-135">未插上纜線。</span><span class="sxs-lookup"><span data-stu-id="71672-135">Cables are unplugged.</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="71672-136">Windows 具有封鎖特定通訊埠的防火牆。</span><span class="sxs-lookup"><span data-stu-id="71672-136">Windows has a firewall that blocks a specific port.</span></span>  
  
-   <span data-ttu-id="71672-137">正在監視通訊埠的應用程式失敗。</span><span class="sxs-lookup"><span data-stu-id="71672-137">The application that is monitoring a port fails.</span></span>  
  
-   <span data-ttu-id="71672-138">已重新命名 Windows 伺服器。</span><span class="sxs-lookup"><span data-stu-id="71672-138">A Windows-based server is renamed.</span></span>  
  
-   <span data-ttu-id="71672-139">已重新啟動 Windows 伺服器。</span><span class="sxs-lookup"><span data-stu-id="71672-139">A Windows-based server is rebooted.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="71672-140">對於用戶端存取伺服器方面的特定問題，鏡像無法加以防止。</span><span class="sxs-lookup"><span data-stu-id="71672-140">Mirroring does not protect against problems specific to client accessing the servers.</span></span> <span data-ttu-id="71672-141">例如，試想一個情況，公用網路介面卡處理對主體伺服器執行個體的用戶端連接，而私人網路介面卡則處理伺服器執行個體之間的所有鏡像傳輸。</span><span class="sxs-lookup"><span data-stu-id="71672-141">For example, consider a case in which a public network adapter handles client connections to the principal server instance, while a private network interface card handles all mirroring traffic among server instances.</span></span> <span data-ttu-id="71672-142">在這個情況下，公用網路介面卡的失敗將會阻止用戶端存取資料庫，然而資料庫卻繼續進行鏡像。</span><span class="sxs-lookup"><span data-stu-id="71672-142">In this case, failure of the public network adapter would prevent clients from accessing the database, though the database would continue to be mirrored.</span></span>  
  
## <a name="failures-due-to-soft-errors"></a><span data-ttu-id="71672-143">軟性錯誤造成的失敗</span><span class="sxs-lookup"><span data-stu-id="71672-143">Failures Due to Soft Errors</span></span>  
 <span data-ttu-id="71672-144">可能會造成鏡像逾時的狀況包括 (但不限於) 下列狀況：</span><span class="sxs-lookup"><span data-stu-id="71672-144">Conditions that might cause mirroring time-outs include (but are not limited to) the following:</span></span>  
  
-   <span data-ttu-id="71672-145">網路錯誤，例如 TCP 連結逾時、卸除或損毀的封包或順序不正確的封包。</span><span class="sxs-lookup"><span data-stu-id="71672-145">Network errors such as TCP link time-outs, dropped or corrupted packets, or packets that are in an incorrect order.</span></span>  
  
-   <span data-ttu-id="71672-146">沒有回應的作業系統、伺服器或資料庫。</span><span class="sxs-lookup"><span data-stu-id="71672-146">An operating system, server, or database that is not responding.</span></span>  
  
-   <span data-ttu-id="71672-147">Windows 伺服器逾時。</span><span class="sxs-lookup"><span data-stu-id="71672-147">A Windows server timing out.</span></span>  
  
-   <span data-ttu-id="71672-148">運算資源不足，例如 CPU 或磁碟負擔過重、交易記錄已滿，或系統的記憶體或執行緒用盡。</span><span class="sxs-lookup"><span data-stu-id="71672-148">Insufficient computing resources, such as a CPU or disk overload, the transaction log filling up, or the system is running out of memory or threads.</span></span> <span data-ttu-id="71672-149">在這些情況下，您必須增加逾時期限、降低工作負載或更換硬體來因應工作負載。</span><span class="sxs-lookup"><span data-stu-id="71672-149">In these cases, you must increase the time-out period, reduce the workload, or change the hardware to handle the workload.</span></span>  
  
### <a name="the-mirroring-time-out-mechanism"></a><span data-ttu-id="71672-150">鏡像逾時機制</span><span class="sxs-lookup"><span data-stu-id="71672-150">The Mirroring Time-Out Mechanism</span></span>  
 <span data-ttu-id="71672-151">因為伺服器執行個體無法直接偵測到軟性錯誤，所以軟性錯誤可能會造成伺服器執行個體永遠等候。</span><span class="sxs-lookup"><span data-stu-id="71672-151">Because soft errors are not detectable directly by a server instance, a soft error could potentially cause a server instance to wait indefinitely.</span></span> <span data-ttu-id="71672-152">為了避免這種狀況，資料庫鏡像會實作本身的逾時機制，而在此機制中，鏡像工作階段中的每個伺服器執行個體都會以固定間隔在每個開啟連接上送出 Ping。</span><span class="sxs-lookup"><span data-stu-id="71672-152">To prevent this, database mirroring implements its own time-out mechanism, based on each server instance in a mirroring session sending out a ping on each open connection at a fixed interval.</span></span>  
  
 <span data-ttu-id="71672-153">若要將連接保持為開啟狀態，伺服器執行個體必須於定義的逾時期限加上傳送另一個 Ping 所需的時間內，在該連接上收到 Ping。</span><span class="sxs-lookup"><span data-stu-id="71672-153">To keep a connection open, a server instance must receive a ping on that connection in the time-out period defined, plus the time that is required to send one more ping.</span></span> <span data-ttu-id="71672-154">在逾時期限接收到 Ping，表示連接仍為開啟狀態，且伺服器執行個體是透過它進行通訊。</span><span class="sxs-lookup"><span data-stu-id="71672-154">Receiving a ping during the time-out period indicates that the connection is still open and that the server instances are communicating over it.</span></span> <span data-ttu-id="71672-155">接收到 Ping 時，伺服器執行個體會重設它在該連接上的逾時計數器。</span><span class="sxs-lookup"><span data-stu-id="71672-155">On receiving a ping, a server instance resets its time-out counter on that connection.</span></span>  
  
 <span data-ttu-id="71672-156">如果逾時期限在連接上未接收到 Ping，則伺服器執行個體會將該連接視為逾時。伺服器執行個體會關閉逾時連接，並根據工作階段的狀態和作業模式來處理逾時事件。</span><span class="sxs-lookup"><span data-stu-id="71672-156">If no ping is received on a connection during the time-out period, a server instance considers the connection to have timed out. The server instance closes the timed-out connection and handles the time-out event according to the state and operating mode of the session.</span></span>  
  
 <span data-ttu-id="71672-157">即使其他伺服器實際上運作正常，仍會將逾時視為失敗。</span><span class="sxs-lookup"><span data-stu-id="71672-157">Even if the other server is actually proceeding correctly, a time-out is considered a failure.</span></span> <span data-ttu-id="71672-158">如果工作階段的逾時值太短，來不及收到對方的正常回應，則可能發生假性失敗。</span><span class="sxs-lookup"><span data-stu-id="71672-158">If the time-out value for a session is too short for the regular responsiveness of either partner, false failures can occur.</span></span> <span data-ttu-id="71672-159">當某個伺服器執行個體順利連絡另一個回應時間很慢的執行個體時，由於在逾時期限到期前未收到 Ping，所以會發生假性失敗。</span><span class="sxs-lookup"><span data-stu-id="71672-159">A false failure occurs when one server instance successfully contacts another whose response time is so slow that its pings are not received before the time-out period expires.</span></span>  
  
 <span data-ttu-id="71672-160">在高效能模式工作階段中，逾時期限一律為 10 秒。</span><span class="sxs-lookup"><span data-stu-id="71672-160">In high-performance mode sessions, the time-out period is always 10 seconds.</span></span> <span data-ttu-id="71672-161">這通常足以避免假性失敗。</span><span class="sxs-lookup"><span data-stu-id="71672-161">This is generally enough to avoid false failures.</span></span> <span data-ttu-id="71672-162">在高安全性模式工作階段中，預設逾時期限為 10 秒，但是您可以變更這個時間。</span><span class="sxs-lookup"><span data-stu-id="71672-162">In high-safety mode sessions, the default time-out period is 10 seconds, but you can change the duration.</span></span> <span data-ttu-id="71672-163">為了避免假性失敗，建議您將鏡像逾時期限一律設為 10 秒或更久。</span><span class="sxs-lookup"><span data-stu-id="71672-163">To avoid false failures, we recommend that the mirroring time-out period always be 10 seconds or more.</span></span>  
  
 <span data-ttu-id="71672-164">**若要變更逾時值 (僅高安全性模式)**</span><span class="sxs-lookup"><span data-stu-id="71672-164">**To change the time-out value (high-safety mode only)**</span></span>  
  
-   <span data-ttu-id="71672-165">使用 [ALTER DATABASE \<database> SET PARTNER TIMEOUT \<integer>](/sql/t-sql/statements/alter-database-transact-sql) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="71672-165">Use the [ALTER DATABASE \<database> SET PARTNER TIMEOUT \<integer>](/sql/t-sql/statements/alter-database-transact-sql) statement.</span></span>  
  
 <span data-ttu-id="71672-166">**若要檢視目前的逾時值**</span><span class="sxs-lookup"><span data-stu-id="71672-166">**To view the current time-out value**</span></span>  
  
-   <span data-ttu-id="71672-167">查詢 **sys.database_mirroring** 中的 [mirroring_connection_timeout](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="71672-167">Query **mirroring_connection_timeout** in [sys.database_mirroring](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql).</span></span>  
  
## <a name="responding-to-an-error"></a><span data-ttu-id="71672-168">回應錯誤</span><span class="sxs-lookup"><span data-stu-id="71672-168">Responding to an Error</span></span>  
 <span data-ttu-id="71672-169">不論錯誤的類型為何，偵測到錯誤的伺服器執行個體都會根據執行個體的角色、工作階段的作業模式和工作階段中其他連接的狀態，進行適當的回應。</span><span class="sxs-lookup"><span data-stu-id="71672-169">Regardless of the type of error, a server instance that detects an error responds appropriately based on the role of the instance, the operating mode of the session, and the state of any other connection in the session.</span></span> <span data-ttu-id="71672-170">如需有關遺失夥伴時所發生之情況的詳細資訊，請參閱 [資料庫鏡像作業模式](database-mirroring-operating-modes.md)。</span><span class="sxs-lookup"><span data-stu-id="71672-170">For information about what occurs on the loss of a partner, see [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71672-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71672-171">See Also</span></span>  
 <span data-ttu-id="71672-172">[預估角色切換期間的服務中斷時間 &#40;資料庫鏡像&#41;](estimate-the-interruption-of-service-during-role-switching-database-mirroring.md) </span><span class="sxs-lookup"><span data-stu-id="71672-172">[Estimate the Interruption of Service During Role Switching &#40;Database Mirroring&#41;](estimate-the-interruption-of-service-during-role-switching-database-mirroring.md) </span></span>  
 <span data-ttu-id="71672-173">[資料庫鏡像作業模式](database-mirroring-operating-modes.md) </span><span class="sxs-lookup"><span data-stu-id="71672-173">[Database Mirroring Operating Modes](database-mirroring-operating-modes.md) </span></span>  
 <span data-ttu-id="71672-174">[資料庫鏡像工作階段期間的角色切換 &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="71672-174">[Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md) </span></span>  
 [<span data-ttu-id="71672-175">資料庫鏡像 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="71672-175">Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)  
  
  
