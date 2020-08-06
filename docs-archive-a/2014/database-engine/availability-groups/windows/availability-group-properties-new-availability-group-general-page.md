---
title: 可用性群組屬性和新增可用性群組 (一般頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroupproperties.general.f1
ms.assetid: 9af5379f-91b8-4729-9f75-4a80242a30e9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 876b9d0948b7cd0d01c21b0ec1d64c51a55fa157
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585605"
---
# <a name="availability-group-properties-and-new-availability-group-general-page"></a><span data-ttu-id="65cdb-102">可用性群組屬性和新增可用性群組 (一般頁面)</span><span class="sxs-lookup"><span data-stu-id="65cdb-102">Availability Group Properties and New Availability Group (General Page)</span></span>
  <span data-ttu-id="65cdb-103">本主題適用於 [新增可用性群組] 對話方塊和 [可用性群組屬性] 對話方塊的 [一般] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="65cdb-103">This topic applies to the **General** tab of both the **New Availability Group** dialog box and the **Availability Group Properties** dialog box.</span></span>  <span data-ttu-id="65cdb-104">[新增可用性群組] 對話方塊可讓您建立新的可用性群組，而不需要使用 [[!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)]]。</span><span class="sxs-lookup"><span data-stu-id="65cdb-104">The **New Availability Group** dialog box enables you to create a new availability group without using the [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)].</span></span> <span data-ttu-id="65cdb-105">[可用性群組屬性] 對話方塊可讓您檢視和改變現有可用性群組的組態。</span><span class="sxs-lookup"><span data-stu-id="65cdb-105">The **Availability Group Properties** dialog box enables you to view and alter the configuration of an existing availability group.</span></span>  
  
 <span data-ttu-id="65cdb-106">**若要檢視可用性群組屬性**</span><span class="sxs-lookup"><span data-stu-id="65cdb-106">**To view availability group properties**</span></span>  
  
-   [<span data-ttu-id="65cdb-107">檢視可用性群組屬性 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="65cdb-107">View Availability Group Properties &#40;SQL Server&#41;</span></span>](view-availability-group-properties-sql-server.md)  
  
-   [<span data-ttu-id="65cdb-108">使用 AlwaysOn 儀表板 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="65cdb-108">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
## <a name="ui-element-list"></a><span data-ttu-id="65cdb-109">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="65cdb-109">UI element list</span></span>  
 <span data-ttu-id="65cdb-110">**可用性群組名稱**</span><span class="sxs-lookup"><span data-stu-id="65cdb-110">**Availability group name**</span></span>  
 <span data-ttu-id="65cdb-111">可用性群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="65cdb-111">Name of the availability group.</span></span> <span data-ttu-id="65cdb-112">這是使用者指定的名稱，它在 Windows Server 容錯移轉叢集 (WSFC) 內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="65cdb-112">This is a user-specified name that must be unique within the Windows Server Failover Cluster (WSFC).</span></span>  
  
## <a name="availability-databases"></a><span data-ttu-id="65cdb-113">可用性資料庫</span><span class="sxs-lookup"><span data-stu-id="65cdb-113">Availability Databases</span></span>  
 <span data-ttu-id="65cdb-114">**Database Name**</span><span class="sxs-lookup"><span data-stu-id="65cdb-114">**Database Name**</span></span>  
 <span data-ttu-id="65cdb-115">已經加入至可用性群組的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="65cdb-115">Name of a database that has been added to the availability group.</span></span>  
  
 <span data-ttu-id="65cdb-116">**加入**</span><span class="sxs-lookup"><span data-stu-id="65cdb-116">**Add**</span></span>  
 <span data-ttu-id="65cdb-117">按一下可將資料庫加入至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="65cdb-117">Click to add a database to the availability group.</span></span>  
  
 <span data-ttu-id="65cdb-118">**移除**</span><span class="sxs-lookup"><span data-stu-id="65cdb-118">**Remove**</span></span>  
 <span data-ttu-id="65cdb-119">按一下可從可用性群組中移除選取的資料庫。</span><span class="sxs-lookup"><span data-stu-id="65cdb-119">Click to remove a selected database from the availability group.</span></span>  
  
## <a name="availability-replicas"></a><span data-ttu-id="65cdb-120">可用性複本</span><span class="sxs-lookup"><span data-stu-id="65cdb-120">Availability Replicas</span></span>  
 <span data-ttu-id="65cdb-121">**伺服器執行個體**</span><span class="sxs-lookup"><span data-stu-id="65cdb-121">**Server instance**</span></span>  
 <span data-ttu-id="65cdb-122">裝載這個複本之 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的伺服器名稱，如果是非預設執行個體，則是它的執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="65cdb-122">Server name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that is hosting this replica and, for a non-default instance, its instance name.</span></span>  
  
 <span data-ttu-id="65cdb-123">**角色**</span><span class="sxs-lookup"><span data-stu-id="65cdb-123">**Role**</span></span>  
 <span data-ttu-id="65cdb-124">**主要**</span><span class="sxs-lookup"><span data-stu-id="65cdb-124">**Primary**</span></span>  
 <span data-ttu-id="65cdb-125">目前的主要複本。</span><span class="sxs-lookup"><span data-stu-id="65cdb-125">Currently the primary replica.</span></span>  
  
 <span data-ttu-id="65cdb-126">**次要**</span><span class="sxs-lookup"><span data-stu-id="65cdb-126">**Secondary**</span></span>  
 <span data-ttu-id="65cdb-127">目前的次要複本。</span><span class="sxs-lookup"><span data-stu-id="65cdb-127">Currently a secondary replica.</span></span>  
  
 <span data-ttu-id="65cdb-128">**解析中**</span><span class="sxs-lookup"><span data-stu-id="65cdb-128">**Resolving**</span></span>  
 <span data-ttu-id="65cdb-129">複本角色目前正在解析成主要或次要角色。</span><span class="sxs-lookup"><span data-stu-id="65cdb-129">Currently the replica role is in the process of being resolved to either the primary or secondary role.</span></span>  
  
 <span data-ttu-id="65cdb-130">**可用性模式**</span><span class="sxs-lookup"><span data-stu-id="65cdb-130">**Availability Mode**</span></span>  
 <span data-ttu-id="65cdb-131">複本的可用性模式，下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="65cdb-131">The availability mode of the replica, one of:</span></span>  
  
 <span data-ttu-id="65cdb-132">**非同步認可**</span><span class="sxs-lookup"><span data-stu-id="65cdb-132">**Asynchronous commit**</span></span>  
 <span data-ttu-id="65cdb-133">主要複本可認可交易，而不需要等候次要複本將記錄寫入磁碟中。</span><span class="sxs-lookup"><span data-stu-id="65cdb-133">The primary replica can commit transactions without waiting for the secondary to write the log to disk.</span></span>  
  
 <span data-ttu-id="65cdb-134">**同步認可**</span><span class="sxs-lookup"><span data-stu-id="65cdb-134">**Synchronous commit**</span></span>  
 <span data-ttu-id="65cdb-135">主要複本會等候認可給定交易，直到次要複本將交易寫入磁碟為止。</span><span class="sxs-lookup"><span data-stu-id="65cdb-135">The primary replica waits to commit a given transaction until the secondary replica has written the transaction to disk.</span></span>  
  
 <span data-ttu-id="65cdb-136">如需詳細資訊，請參閱[可用性模式 (AlwaysOn 可用性群組) ](availability-modes-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="65cdb-136">For more information, see [Availability Modes (AlwaysOn Availability Groups)](availability-modes-always-on-availability-groups.md).</span></span>  
  
 <span data-ttu-id="65cdb-137">**容錯移轉模式**</span><span class="sxs-lookup"><span data-stu-id="65cdb-137">**Failover Mode**</span></span>  
 <span data-ttu-id="65cdb-138">複本的容錯移轉模式，下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="65cdb-138">The failover mode of the replica, one of:</span></span>  
  
 <span data-ttu-id="65cdb-139">**自動**</span><span class="sxs-lookup"><span data-stu-id="65cdb-139">**Automatic**</span></span>  
 <span data-ttu-id="65cdb-140">自動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="65cdb-140">Automatic failover.</span></span> <span data-ttu-id="65cdb-141">此複本是自動容錯移轉的目標。</span><span class="sxs-lookup"><span data-stu-id="65cdb-141">The replica is a target for automatic failovers.</span></span> <span data-ttu-id="65cdb-142">只有當可用性模式設定為同步認可時，才支援這個選項。</span><span class="sxs-lookup"><span data-stu-id="65cdb-142">This is supported only if the availability mode is set to synchronous commit.</span></span>  
  
 <span data-ttu-id="65cdb-143">**手動**</span><span class="sxs-lookup"><span data-stu-id="65cdb-143">**Manual**</span></span>  
 <span data-ttu-id="65cdb-144">手動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="65cdb-144">Manual failover.</span></span> <span data-ttu-id="65cdb-145">此複本只能由資料庫管理員手動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="65cdb-145">The replica can only be failed over to manually by the database administrator.</span></span>  
  
 <span data-ttu-id="65cdb-146">**主要角色的連接模式**</span><span class="sxs-lookup"><span data-stu-id="65cdb-146">**Connections in Primary Role**</span></span>  
 <span data-ttu-id="65cdb-147">當複本擁有主要角色時所支援的用戶端連接類型。</span><span class="sxs-lookup"><span data-stu-id="65cdb-147">The type of client connections supported when the replica owns the primary role.</span></span>  
  
 <span data-ttu-id="65cdb-148">**允許所有連接**</span><span class="sxs-lookup"><span data-stu-id="65cdb-148">**Allow all connections**</span></span>  
 <span data-ttu-id="65cdb-149">主要複本的資料庫允許所有連接。</span><span class="sxs-lookup"><span data-stu-id="65cdb-149">All connections are allowed to the databases in the primary replica.</span></span> <span data-ttu-id="65cdb-150">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="65cdb-150">This is the default setting.</span></span>  
  
 <span data-ttu-id="65cdb-151">**允取讀取/寫入連接**</span><span class="sxs-lookup"><span data-stu-id="65cdb-151">**Allow read/write connections**</span></span>  
 <span data-ttu-id="65cdb-152">不允許 Application Intent 連接屬性設為 **ReadOnly** 的連接。</span><span class="sxs-lookup"><span data-stu-id="65cdb-152">Connections where the Application Intent connection property is set to **ReadOnly** are disallowed.</span></span> <span data-ttu-id="65cdb-153">當 Application Intent 屬性設為 **ReadWrite** 或是未設定 Application Intent 連接屬性時，便會允許連接。</span><span class="sxs-lookup"><span data-stu-id="65cdb-153">When the Application Intent property is set to **ReadWrite** or the Application Intent connection property is not set, the connection is allowed.</span></span> <span data-ttu-id="65cdb-154">如需有關 Application Intent 連接屬性的詳細資訊，請參閱＜ [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)＞。</span><span class="sxs-lookup"><span data-stu-id="65cdb-154">For more information about Application Intent connection property, see [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
 <span data-ttu-id="65cdb-155">**可讀取次要**</span><span class="sxs-lookup"><span data-stu-id="65cdb-155">**Readable Secondary**</span></span>  
 <span data-ttu-id="65cdb-156">執行次要角色的可用性複本 (也就是次要複本) 是否可接受來自用戶端的連接，下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="65cdb-156">Whether an availability replica that is performing the secondary role (that is, a secondary replica) can accept connections from clients, one of:</span></span>  
  
 <span data-ttu-id="65cdb-157">**否**</span><span class="sxs-lookup"><span data-stu-id="65cdb-157">**No**</span></span>  
 <span data-ttu-id="65cdb-158">不允許直接連接這個複本的次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="65cdb-158">No direct connections are allowed to secondary databases of this replica.</span></span> <span data-ttu-id="65cdb-159">無法讀取這些資料庫。</span><span class="sxs-lookup"><span data-stu-id="65cdb-159">They are not available for read access.</span></span> <span data-ttu-id="65cdb-160">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="65cdb-160">This is the default setting.</span></span>  
  
 <span data-ttu-id="65cdb-161">**僅限讀取意圖**</span><span class="sxs-lookup"><span data-stu-id="65cdb-161">**Read-intent only**</span></span>  
 <span data-ttu-id="65cdb-162">只允許與這個複本的次要資料庫進行直接唯讀連接。</span><span class="sxs-lookup"><span data-stu-id="65cdb-162">Only direct read-only connections are allowed to secondary databases of this replica.</span></span> <span data-ttu-id="65cdb-163">可以讀取所有次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="65cdb-163">The secondary database(s) are all available for read access.</span></span>  
  
 <span data-ttu-id="65cdb-164">**是**</span><span class="sxs-lookup"><span data-stu-id="65cdb-164">**Yes**</span></span>  
 <span data-ttu-id="65cdb-165">允許與這個複本的次要資料庫之間的所有連接，但只供讀取存取。</span><span class="sxs-lookup"><span data-stu-id="65cdb-165">All connections are allowed to secondary databases of this replica, but only for read access.</span></span> <span data-ttu-id="65cdb-166">可以讀取所有次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="65cdb-166">The secondary database(s) are all available for read access.</span></span>  
  
 <span data-ttu-id="65cdb-167">**工作階段逾時 (秒)**</span><span class="sxs-lookup"><span data-stu-id="65cdb-167">**Session Timeout (seconds)**</span></span>  
 <span data-ttu-id="65cdb-168">此複本之工作階段逾時期限的秒數。</span><span class="sxs-lookup"><span data-stu-id="65cdb-168">The number of seconds for the session-timeout period on this replica.</span></span>  
  
 <span data-ttu-id="65cdb-169">**端點 URL**</span><span class="sxs-lookup"><span data-stu-id="65cdb-169">**Endpoint URL**</span></span>  
 <span data-ttu-id="65cdb-170">端點的 URL。</span><span class="sxs-lookup"><span data-stu-id="65cdb-170">The URL of the endpoint.</span></span> <span data-ttu-id="65cdb-171">如需這些 URL 格式的資訊，請參閱[在加入或修改可用性複本時指定端點 URL &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md)。</span><span class="sxs-lookup"><span data-stu-id="65cdb-171">For information the format of these URLs, see [Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md).</span></span>  
  
 <span data-ttu-id="65cdb-172">**加入**</span><span class="sxs-lookup"><span data-stu-id="65cdb-172">**Add**</span></span>  
 <span data-ttu-id="65cdb-173">按一下可將次要複本加入至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="65cdb-173">Click to add a secondary replica to the availability group.</span></span>  
  
 <span data-ttu-id="65cdb-174">**移除**</span><span class="sxs-lookup"><span data-stu-id="65cdb-174">**Remove**</span></span>  
 <span data-ttu-id="65cdb-175">按一下可從可用性群組中移除次要複本。</span><span class="sxs-lookup"><span data-stu-id="65cdb-175">Click to remove a secondary replica from the availability group.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65cdb-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65cdb-176">See Also</span></span>  
 [<span data-ttu-id="65cdb-177">AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;</span><span class="sxs-lookup"><span data-stu-id="65cdb-177">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
