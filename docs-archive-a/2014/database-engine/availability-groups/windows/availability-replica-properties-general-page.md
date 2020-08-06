---
title: 可用性複本屬性 (一般頁面) | Microsoft Docs
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilityreplicaproperties.general.f1
ms.assetid: 8318fefb-e045-4fab-8507-e1951fc7cec6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 313314baf009cdfb6109e63e9b65e369ac314f60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708686"
---
# <a name="availability-replica-properties-general-page"></a><span data-ttu-id="9d24e-102">可用性複本屬性 (一般頁面)</span><span class="sxs-lookup"><span data-stu-id="9d24e-102">Availability Replica Properties (General Page)</span></span>
  <span data-ttu-id="9d24e-103">使用此對話方塊來檢視可用性複本的屬性。</span><span class="sxs-lookup"><span data-stu-id="9d24e-103">Use this dialog box to viewthe properties of an availability replica.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="9d24e-104">工作清單</span><span class="sxs-lookup"><span data-stu-id="9d24e-104">Task List</span></span>  
 <span data-ttu-id="9d24e-105">**若要檢視可用性複本屬性**</span><span class="sxs-lookup"><span data-stu-id="9d24e-105">**To view availability replica properties**</span></span>  
  
-   [<span data-ttu-id="9d24e-106">檢視可用性複本屬性 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9d24e-106">View Availability Replica Properties &#40;SQL Server&#41;</span></span>](view-availability-replica-properties-sql-server.md)  
  
-   [<span data-ttu-id="9d24e-107">使用 AlwaysOn 儀表板 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="9d24e-107">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
## <a name="ui-element-list"></a><span data-ttu-id="9d24e-108">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="9d24e-108">UI element list</span></span>  
 <span data-ttu-id="9d24e-109">**可用性群組名稱**</span><span class="sxs-lookup"><span data-stu-id="9d24e-109">**Availability group name**</span></span>  
 <span data-ttu-id="9d24e-110">可用性群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="9d24e-110">Name of the availability group.</span></span> <span data-ttu-id="9d24e-111">這是使用者指定的名稱，它在 Windows Server 容錯移轉叢集 (WSFC) 內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="9d24e-111">This is a user-specified name that must be unique within the Windows Server Failover Cluster (WSFC).</span></span>  
  
 <span data-ttu-id="9d24e-112">**伺服器執行個體**</span><span class="sxs-lookup"><span data-stu-id="9d24e-112">**Server instance**</span></span>  
 <span data-ttu-id="9d24e-113">裝載這個複本之 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的伺服器名稱，如果是非預設執行個體，則是它的執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="9d24e-113">Server name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that is hosting this replica and, for a non-default instance, its instance name.</span></span>  
  
 <span data-ttu-id="9d24e-114">**角色**</span><span class="sxs-lookup"><span data-stu-id="9d24e-114">**Role**</span></span>  
 <span data-ttu-id="9d24e-115">**主要**</span><span class="sxs-lookup"><span data-stu-id="9d24e-115">**Primary**</span></span>  
 <span data-ttu-id="9d24e-116">目前的主要複本。</span><span class="sxs-lookup"><span data-stu-id="9d24e-116">Currently the primary replica.</span></span>  
  
 <span data-ttu-id="9d24e-117">**次要**</span><span class="sxs-lookup"><span data-stu-id="9d24e-117">**Secondary**</span></span>  
 <span data-ttu-id="9d24e-118">目前的次要複本。</span><span class="sxs-lookup"><span data-stu-id="9d24e-118">Currently a secondary replica.</span></span>  
  
 <span data-ttu-id="9d24e-119">**解析中**</span><span class="sxs-lookup"><span data-stu-id="9d24e-119">**Resolving**</span></span>  
 <span data-ttu-id="9d24e-120">複本角色目前正在解析成主要或次要角色。</span><span class="sxs-lookup"><span data-stu-id="9d24e-120">Currently the replica role is in the process of being resolved to either the primary or secondary role.</span></span>  
  
 <span data-ttu-id="9d24e-121">**可用性模式**</span><span class="sxs-lookup"><span data-stu-id="9d24e-121">**Availability mode**</span></span>  
 <span data-ttu-id="9d24e-122">複本的可用性模式，下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="9d24e-122">The availability mode of the replica, one of:</span></span>  
  
 <span data-ttu-id="9d24e-123">**非同步認可**</span><span class="sxs-lookup"><span data-stu-id="9d24e-123">**Asynchronous commit**</span></span>  
 <span data-ttu-id="9d24e-124">主要複本可認可交易，而不需要等候次要複本將記錄寫入磁碟中。</span><span class="sxs-lookup"><span data-stu-id="9d24e-124">The primary replica can commit transactions without waiting for the secondary to write the log to disk.</span></span>  
  
 <span data-ttu-id="9d24e-125">**同步認可**</span><span class="sxs-lookup"><span data-stu-id="9d24e-125">**Synchronous commit**</span></span>  
 <span data-ttu-id="9d24e-126">主要複本會等候認可給定交易，直到次要複本將交易寫入磁碟為止。</span><span class="sxs-lookup"><span data-stu-id="9d24e-126">The primary replica waits to commit a given transaction until the secondary replica has written the transaction to disk.</span></span>  
  
 <span data-ttu-id="9d24e-127">如需詳細資訊，請參閱[可用性模式 (AlwaysOn 可用性群組) ](availability-modes-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="9d24e-127">For more information, see [Availability Modes (AlwaysOn Availability Groups)](availability-modes-always-on-availability-groups.md).</span></span>  
  
 <span data-ttu-id="9d24e-128">**Failover mode**</span><span class="sxs-lookup"><span data-stu-id="9d24e-128">**Failover mode**</span></span>  
 <span data-ttu-id="9d24e-129">複本的容錯移轉模式，下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="9d24e-129">The failover mode of the replica, one of:</span></span>  
  
 <span data-ttu-id="9d24e-130">**自動**</span><span class="sxs-lookup"><span data-stu-id="9d24e-130">**Automatic**</span></span>  
 <span data-ttu-id="9d24e-131">自動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="9d24e-131">Automatic failover.</span></span> <span data-ttu-id="9d24e-132">此複本是自動容錯移轉的目標。</span><span class="sxs-lookup"><span data-stu-id="9d24e-132">The replica is a target for automatic failovers.</span></span> <span data-ttu-id="9d24e-133">只有當可用性模式設定為同步認可時，才支援這個選項。</span><span class="sxs-lookup"><span data-stu-id="9d24e-133">This is supported only if the availability mode is set to synchronous commit.</span></span>  
  
 <span data-ttu-id="9d24e-134">**手動**</span><span class="sxs-lookup"><span data-stu-id="9d24e-134">**Manual**</span></span>  
 <span data-ttu-id="9d24e-135">手動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="9d24e-135">Manual failover.</span></span> <span data-ttu-id="9d24e-136">此複本只能由資料庫管理員手動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="9d24e-136">The replica can only be failed over to manually by the database administrator.</span></span>  
  
 <span data-ttu-id="9d24e-137">**主要角色的連接模式**</span><span class="sxs-lookup"><span data-stu-id="9d24e-137">**Connections in primary role**</span></span>  
 <span data-ttu-id="9d24e-138">當複本擁有主要角色時所支援的用戶端連接類型。</span><span class="sxs-lookup"><span data-stu-id="9d24e-138">The type of client connections supported when the replica owns the primary role.</span></span>  
  
 <span data-ttu-id="9d24e-139">**允許所有連接**</span><span class="sxs-lookup"><span data-stu-id="9d24e-139">**Allow all connections**</span></span>  
 <span data-ttu-id="9d24e-140">主要複本的資料庫允許所有連接。</span><span class="sxs-lookup"><span data-stu-id="9d24e-140">All connections are allowed to the databases in the primary replica.</span></span> <span data-ttu-id="9d24e-141">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="9d24e-141">This is the default setting.</span></span>  
  
 <span data-ttu-id="9d24e-142">**允取讀取/寫入連接**</span><span class="sxs-lookup"><span data-stu-id="9d24e-142">**Allow read/write connections**</span></span>  
 <span data-ttu-id="9d24e-143">不允許 Application Intent 連接屬性設為 **ReadOnly** 的連接。</span><span class="sxs-lookup"><span data-stu-id="9d24e-143">Connections where the Application Intent connection property is set to **ReadOnly** are disallowed.</span></span> <span data-ttu-id="9d24e-144">當 Application Intent 屬性設為 **ReadWrite** 或是未設定 Application Intent 連接屬性時，便會允許連接。</span><span class="sxs-lookup"><span data-stu-id="9d24e-144">When the Application Intent property is set to **ReadWrite** or the application intent connection property is not set, the connection is allowed.</span></span>  
  
 <span data-ttu-id="9d24e-145">**可讀取次要**</span><span class="sxs-lookup"><span data-stu-id="9d24e-145">**Readable Secondary**</span></span>  
 <span data-ttu-id="9d24e-146">執行次要角色的可用性複本 (也就是次要複本) 是否可接受來自用戶端的連接，下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="9d24e-146">Whether an availability replica that is performing the secondary role (that is, a secondary replica) can accept connections from clients, one of:</span></span>  
  
 <span data-ttu-id="9d24e-147">**否**</span><span class="sxs-lookup"><span data-stu-id="9d24e-147">**No**</span></span>  
 <span data-ttu-id="9d24e-148">不允許直接連接這個複本的次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="9d24e-148">No direct connections are allowed to secondary databases of this replica.</span></span> <span data-ttu-id="9d24e-149">無法讀取這些資料庫。</span><span class="sxs-lookup"><span data-stu-id="9d24e-149">They are not available for read access.</span></span> <span data-ttu-id="9d24e-150">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="9d24e-150">This is the default setting.</span></span>  
  
 <span data-ttu-id="9d24e-151">**僅限讀取意圖**</span><span class="sxs-lookup"><span data-stu-id="9d24e-151">**Read-intent only**</span></span>  
 <span data-ttu-id="9d24e-152">只允許與這個複本的次要資料庫進行直接唯讀連接。</span><span class="sxs-lookup"><span data-stu-id="9d24e-152">Only direct read-only connections are allowed to secondary databases of this replica.</span></span> <span data-ttu-id="9d24e-153">可以讀取所有次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="9d24e-153">The secondary database(s) are all available for read access.</span></span>  
  
 <span data-ttu-id="9d24e-154">**是**</span><span class="sxs-lookup"><span data-stu-id="9d24e-154">**Yes**</span></span>  
 <span data-ttu-id="9d24e-155">允許與這個複本的次要資料庫之間的所有連接，但只供讀取存取。</span><span class="sxs-lookup"><span data-stu-id="9d24e-155">All connections are allowed to secondary databases of this replica, but only for read access.</span></span> <span data-ttu-id="9d24e-156">可以讀取所有次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="9d24e-156">The secondary database(s) are all available for read access.</span></span>  
  
 <span data-ttu-id="9d24e-157">如需詳細資訊，請參閱[Active 次要：可讀取的次要複本 (AlwaysOn 可用性群組) ](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="9d24e-157">For more information, see [Active Secondaries: Readable Secondary Replicas (AlwaysOn Availability Groups)](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).</span></span>  
  
 <span data-ttu-id="9d24e-158">**工作階段逾時 (秒)**</span><span class="sxs-lookup"><span data-stu-id="9d24e-158">**Session timeout (seconds)**</span></span>  
 <span data-ttu-id="9d24e-159">逾時期間 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="9d24e-159">The time-out period, in seconds.</span></span> <span data-ttu-id="9d24e-160">逾時期間是將主要複本與次要複本之間的連接視為失敗之前，複本等待接收另一個複本之訊息的時間上限。</span><span class="sxs-lookup"><span data-stu-id="9d24e-160">The time-out period is the maximum time that the replica waits to receive a message from another replica before considering connection between the primary and secondary replica have failed.</span></span> <span data-ttu-id="9d24e-161">工作階段逾時會偵測次要複本是否連接到主要複本。</span><span class="sxs-lookup"><span data-stu-id="9d24e-161">Session timeout detects whether secondaries are connected the primary replica.</span></span> <span data-ttu-id="9d24e-162">一旦偵測到與次要複本之間的連接失敗時，主要複本會將次要複本視為 NOT_SYNCHRONIZED。</span><span class="sxs-lookup"><span data-stu-id="9d24e-162">On detecting a failed connection with a secondary replica, the primary replica considers the secondary replica to be NOT_SYNCHRONIZED.</span></span> <span data-ttu-id="9d24e-163">一旦偵測到與主要複本之間的連接失敗時，次要複本只會嘗試重新連接。</span><span class="sxs-lookup"><span data-stu-id="9d24e-163">On detecting a failed connection with the primary replica, a secondary replica simply attempts to reconnect.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9d24e-164">工作階段逾時不會造成自動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="9d24e-164">Session timeouts do not cause automatic failovers.</span></span>  
  
 <span data-ttu-id="9d24e-165">**端點 URL**</span><span class="sxs-lookup"><span data-stu-id="9d24e-165">**Endpoint URL**</span></span>  
 <span data-ttu-id="9d24e-166">使用者指定之資料庫鏡像端點的字串表示法，該端點是由主要與次要複本之間的資料同步處理連接所使用。</span><span class="sxs-lookup"><span data-stu-id="9d24e-166">String representation of the user-specified database mirroring endpoint that is used by connections between primary and secondary replicas for data synchronization.</span></span> <span data-ttu-id="9d24e-167">如需這些端點 URL 語法的相關資訊，請參閱[在加入或修改可用性複本時指定端點 URL &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md)。</span><span class="sxs-lookup"><span data-stu-id="9d24e-167">For information about the syntax of endpoint URLs, see [Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d24e-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d24e-168">See Also</span></span>  
 [<span data-ttu-id="9d24e-169">AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;</span><span class="sxs-lookup"><span data-stu-id="9d24e-169">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
