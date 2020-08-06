---
title: 仲裁：見證如何影響資料庫可用性 (資料庫鏡像) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- quorum [SQL Server], database mirroring
- running exposed in database mirroring [SQL Server]
- witness-to-partner quorum [SQL Server]
- partners [SQL Server], partner-to-partner quorum
- witness [SQL Server], quorum
- have quorum [SQL Server]
- quorum [SQL Server]
- mirror database [SQL Server]
- full quorum [SQL Server]
- high-availability mode [SQL Server]
ms.assetid: a62d9dd7-3667-4751-a294-a61fc9caae7c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ada152f280a4ac75543f09e5f5afa7c72c0cbef6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701821"
---
# <a name="quorum-how-a-witness-affects-database-availability-database-mirroring"></a><span data-ttu-id="97c07-102">仲裁：見證如何影響資料庫可用性 (資料庫鏡像)</span><span class="sxs-lookup"><span data-stu-id="97c07-102">Quorum: How a Witness Affects Database Availability (Database Mirroring)</span></span>
  <span data-ttu-id="97c07-103">每當設定資料庫鏡像工作階段的見證時，就需要「仲裁」。</span><span class="sxs-lookup"><span data-stu-id="97c07-103">Whenever a witness is set for a database mirroring session, *quorum* is required.</span></span> <span data-ttu-id="97c07-104">仲裁是資料庫鏡像工作階段中的多個伺服器執行個體彼此連接時所存在的關係。</span><span class="sxs-lookup"><span data-stu-id="97c07-104">Quorum is a relationship that exists when two or more server instances in a database mirroring session are connected to each other.</span></span> <span data-ttu-id="97c07-105">一般而言，仲裁涉及三個互連的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="97c07-105">Typically, quorum involves three interconnected server instances.</span></span> <span data-ttu-id="97c07-106">設定見證之後，需要有仲裁才能使用資料庫。</span><span class="sxs-lookup"><span data-stu-id="97c07-106">When a witness is set, quorum is required to make the database available.</span></span> <span data-ttu-id="97c07-107">仲裁是專為具有自動容錯移轉的高安全性模式而設計，可確保資料庫一次僅能由一個夥伴擁有。</span><span class="sxs-lookup"><span data-stu-id="97c07-107">Designed for high-safety mode with automatic failover, quorum makes sure that a database is owned by only one partner at a time.</span></span>  
  
 <span data-ttu-id="97c07-108">如果特定的伺服器執行個體與鏡像工作階段的連接中斷，該執行個體便會失去仲裁。</span><span class="sxs-lookup"><span data-stu-id="97c07-108">If a particular server instance becomes disconnected from a mirroring session, that instance loses quorum.</span></span> <span data-ttu-id="97c07-109">如果沒有任何伺服器執行個體是處於連接狀態，則工作階段會失去仲裁，而資料庫也會變成無法使用。</span><span class="sxs-lookup"><span data-stu-id="97c07-109">If no server instances are connected, the session loses quorum and the database becomes unavailable.</span></span> <span data-ttu-id="97c07-110">仲裁有三種可能的類型：</span><span class="sxs-lookup"><span data-stu-id="97c07-110">Three types of quorum are possible:</span></span>  
  
-   <span data-ttu-id="97c07-111">「完整仲裁」，包含兩個夥伴及見證。</span><span class="sxs-lookup"><span data-stu-id="97c07-111">A *full quorum* includes both partners and the witness.</span></span>  
  
-   <span data-ttu-id="97c07-112">「見證對夥伴仲裁」，由見證與其中一個夥伴所組成。</span><span class="sxs-lookup"><span data-stu-id="97c07-112">A *witness-to-partner quorum* consists of the witness and either partner.</span></span>  
  
-   <span data-ttu-id="97c07-113">「夥伴對夥伴仲裁」，由兩個夥伴所組成。</span><span class="sxs-lookup"><span data-stu-id="97c07-113">A *partner-to-partner quorum* consists of the two partners.</span></span>  
  
 <span data-ttu-id="97c07-114">下圖顯示這些仲裁類型。</span><span class="sxs-lookup"><span data-stu-id="97c07-114">The following figure shows these types of quorum.</span></span>  
  
 <span data-ttu-id="97c07-115">![仲裁：完整；見證與夥伴；兩個夥伴](../media/dbm-failovautoquorum.gif "仲裁：完整；見證與夥伴；兩個夥伴")</span><span class="sxs-lookup"><span data-stu-id="97c07-115">![Quorums: full; witness and partner; both partners](../media/dbm-failovautoquorum.gif "Quorums: full; witness and partner; both partners")</span></span>  
  
 <span data-ttu-id="97c07-116">只要目前的主體伺服器有仲裁，它就擁有主體的角色並繼續為資料庫服務，除非資料庫擁有者執行手動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="97c07-116">As long as the current principal server has quorum, this server owns the role of principal and continues to serve the database, unless the database owner performs a manual failover.</span></span> <span data-ttu-id="97c07-117">如果主體伺服器失去了仲裁，就會停止為資料庫服務。</span><span class="sxs-lookup"><span data-stu-id="97c07-117">If the principal server loses quorum, it stops serving the database.</span></span> <span data-ttu-id="97c07-118">只有在主體資料庫失去仲裁時 (可確保它已不再為資料庫提供服務)，才會發生自動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="97c07-118">Automatic failover can occur only if the principal database has lost quorum, which guarantees that it is no longer serving the database.</span></span>  
  
 <span data-ttu-id="97c07-119">中斷連接的伺服器執行個體會將其最新的角色儲存在工作階段中。</span><span class="sxs-lookup"><span data-stu-id="97c07-119">A disconnected server instance saves its most recent role in the session.</span></span> <span data-ttu-id="97c07-120">通常，中斷連接的伺服器執行個體會在重新啟動並重新取得仲裁時，重新連接到工作階段。</span><span class="sxs-lookup"><span data-stu-id="97c07-120">Typically, a disconnected server instance reconnects to the session when it restarts and regains quorum.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="97c07-121">只有當您想要使用具有自動容錯移轉的高安全性模式時，才需要設定見證。</span><span class="sxs-lookup"><span data-stu-id="97c07-121">The witness should be set only when you intend to use high-safety mode with automatic failover.</span></span> <span data-ttu-id="97c07-122">在不需要見證的高效能模式中，強烈建議您將 WITNESS 屬性設為 OFF。</span><span class="sxs-lookup"><span data-stu-id="97c07-122">In high-performance mode, for which a witness is never required, we strongly recommend setting the WITNESS property to OFF.</span></span> <span data-ttu-id="97c07-123">如需見證對高效能模式影響的資訊，請參閱 [資料庫鏡像作業模式](database-mirroring-operating-modes.md)。</span><span class="sxs-lookup"><span data-stu-id="97c07-123">For information about the impact of a witness on high-performance mode, see [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span></span>  
  
## <a name="quorum-in-high-safety-mode-sessions"></a><span data-ttu-id="97c07-124">高安全性模式工作階段中的仲裁</span><span class="sxs-lookup"><span data-stu-id="97c07-124">Quorum in High-Safety Mode Sessions</span></span>  
 <span data-ttu-id="97c07-125">在高安全性模式中，仲裁會提供內容，讓具有仲裁的伺服器執行個體在裡頭仲裁哪一個夥伴擁有主體角色，藉以允許自動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="97c07-125">In high-safety mode, quorum allows automatic failover by providing a context in which the server instances with quorum arbitrate which partner owns the role of principal.</span></span> <span data-ttu-id="97c07-126">如果主體伺服器擁有仲裁，便會為資料庫提供服務。</span><span class="sxs-lookup"><span data-stu-id="97c07-126">The principal server serves the database if it has quorum.</span></span> <span data-ttu-id="97c07-127">如果主體伺服器在已同步的鏡像伺服器與見證保有仲裁時失去仲裁，就會發生自動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="97c07-127">If the principal server loses quorum when the synchronized mirror server and witness retain quorum, automatic failover occurs.</span></span>  
  
 <span data-ttu-id="97c07-128">高安全性模式的仲裁狀況如下：</span><span class="sxs-lookup"><span data-stu-id="97c07-128">The quorum scenarios for high-safety mode are as follows:</span></span>  
  
-   <span data-ttu-id="97c07-129">「完整仲裁」，由兩個夥伴及一個見證組成。</span><span class="sxs-lookup"><span data-stu-id="97c07-129">A *full quorum* that consists of both partners and the witness.</span></span>  
  
     <span data-ttu-id="97c07-130">一般情況下，所有三個伺服器執行個體都會參與三向仲裁，稱之為「完整仲裁」。</span><span class="sxs-lookup"><span data-stu-id="97c07-130">Ordinarily, all three server instances participate in a three-way quorum, called a *full quorum*.</span></span> <span data-ttu-id="97c07-131">利用完整仲裁，主體及鏡像伺服器會繼續執行其個別角色 (除非發生手動容錯移轉)。</span><span class="sxs-lookup"><span data-stu-id="97c07-131">With a full quorum, the principal and mirror servers continue to perform their respective roles (unless manual failover occurs).</span></span>  
  
-   <span data-ttu-id="97c07-132">「見證對夥伴仲裁」，由見證和任一夥伴組成。</span><span class="sxs-lookup"><span data-stu-id="97c07-132">A *witness-to-partner quorum* that consists of the witness and either partner.</span></span>  
  
     <span data-ttu-id="97c07-133">如果由於失去其中一個夥伴，而失去夥伴之間的網路連接，則可能會發生以下狀況：</span><span class="sxs-lookup"><span data-stu-id="97c07-133">If the network connection between the partners is lost because one of the partners has been lost, the following cases are possible:</span></span>  
  
    -   <span data-ttu-id="97c07-134">失去鏡像伺服器，但主體伺服器與見證仍保留仲裁。</span><span class="sxs-lookup"><span data-stu-id="97c07-134">The mirror server is lost, and the principal server and witness retain quorum.</span></span>  
  
         <span data-ttu-id="97c07-135">在這種情況下，主體將其資料庫設定為 DISCONNECTED，並且在鏡像設為 SUSPENDED 的狀態中執行。</span><span class="sxs-lookup"><span data-stu-id="97c07-135">In this case, the principal sets its database to DISCONNECTED and runs with mirroring in a SUSPENDED state.</span></span> <span data-ttu-id="97c07-136">(這稱之為「公開執行」，因為資料庫目前沒有鏡像)。當鏡像伺服器重新加入工作階段時，這個伺服器會取回鏡像的仲裁，並開始重新同步處理它的資料庫副本。</span><span class="sxs-lookup"><span data-stu-id="97c07-136">(This is referred to as *running exposed*, because the database is currently not being mirrored.) When the mirror server rejoins the session, the server regains quorum as mirror and starts resynchronizing its copy of the database.</span></span>  
  
    -   <span data-ttu-id="97c07-137">失去主體伺服器，但見證與鏡像伺服器仍保留仲裁。</span><span class="sxs-lookup"><span data-stu-id="97c07-137">The principal server is lost, and the witness and the mirror server retain quorum.</span></span>  
  
         <span data-ttu-id="97c07-138">此時會發生自動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="97c07-138">In this case, automatic failover occurs.</span></span> <span data-ttu-id="97c07-139">如需詳細資訊，請參閱 [Database Mirroring Operating Modes](database-mirroring-operating-modes.md)。</span><span class="sxs-lookup"><span data-stu-id="97c07-139">For more information, see [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span></span>  
  
    -   <span data-ttu-id="97c07-140">所有伺服器執行個體都會遺失仲裁，但是鏡像和見證之後會重新連接。</span><span class="sxs-lookup"><span data-stu-id="97c07-140">All the server instances lose quorum, but subsequently the mirror and witness reconnect.</span></span> <span data-ttu-id="97c07-141">此情況下將不會服務資料庫。</span><span class="sxs-lookup"><span data-stu-id="97c07-141">The database will not be served in this case.</span></span>  
  
     <span data-ttu-id="97c07-142">通常，很少會發生兩個容錯移轉夥伴之間的網路連接中斷，但這兩個夥伴仍保持連接到見證的狀況。</span><span class="sxs-lookup"><span data-stu-id="97c07-142">Rarely, the network connection between failover partners is lost while both partners remain connected to the witness.</span></span> <span data-ttu-id="97c07-143">在此事件中，有兩個個別的見證對夥伴仲裁存在，見證是連絡人。</span><span class="sxs-lookup"><span data-stu-id="97c07-143">In this event, two, separate witness-to-partner quorums exist, with the witness as a liaison.</span></span> <span data-ttu-id="97c07-144">見證通知鏡像伺服器，主體伺服器仍然連接。</span><span class="sxs-lookup"><span data-stu-id="97c07-144">The witness informs the mirror server that the principal server is still connected.</span></span> <span data-ttu-id="97c07-145">因此，不會發生自動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="97c07-145">Therefore, automatic failover does not occur.</span></span> <span data-ttu-id="97c07-146">反而鏡像伺服器會保有鏡像角色，等待重新連接到主體。</span><span class="sxs-lookup"><span data-stu-id="97c07-146">Instead, the mirror server retains the mirror role and waits to reconnect to the principal.</span></span> <span data-ttu-id="97c07-147">如果重做佇列包含位於此點的記錄，鏡像伺服器會繼續向前復原鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="97c07-147">If the redo queue contains log records at this point, the mirror server continues to roll forward the mirror database.</span></span> <span data-ttu-id="97c07-148">等到重新連接時，鏡像伺服器就會重新同步處理鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="97c07-148">On reconnecting, the mirror server will resynchronize the mirror database.</span></span>  
  
-   <span data-ttu-id="97c07-149">「夥伴對夥伴仲裁」，由兩個夥伴組成。</span><span class="sxs-lookup"><span data-stu-id="97c07-149">A *partner-to-partner quorum* that consists of the two partners.</span></span>  
  
     <span data-ttu-id="97c07-150">只要夥伴仍保留仲裁，資料庫就會繼續處於 SYNCHRONIZED 狀態，而且可以進行手動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="97c07-150">As long as the partners retain quorum, the database continues in a SYNCHRONIZED state, and manual failover remains possible.</span></span> <span data-ttu-id="97c07-151">沒有見證，就無法進行自動容錯移轉；但是當見證重新取得仲裁時，工作階段會繼續一般作業，並且再次支援自動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="97c07-151">Without the witness, automatic failover is not possible; but when the witness regains quorum, the session resumes regular operation, and automatic failover is supported again.</span></span>  
  
-   <span data-ttu-id="97c07-152">工作階段失去仲裁。</span><span class="sxs-lookup"><span data-stu-id="97c07-152">The session loses quorum.</span></span>  
  
     <span data-ttu-id="97c07-153">如果所有伺服器執行個體變成彼此中斷連接，就可以說工作階段已經「失去仲裁」。</span><span class="sxs-lookup"><span data-stu-id="97c07-153">If all the server instances become disconnected from each other, the session is said to have *lost quorum*.</span></span> <span data-ttu-id="97c07-154">當伺服器執行個體彼此重新連接時，彼此會議定取回仲裁。</span><span class="sxs-lookup"><span data-stu-id="97c07-154">As server instances reconnect to each other, they regain quorum with each other.</span></span>  
  
    -   <span data-ttu-id="97c07-155">如果主體伺服器與其他任一伺服器執行個體重新連接，資料庫便可使用。</span><span class="sxs-lookup"><span data-stu-id="97c07-155">If the principal server reconnects with either of the other server instances, the database becomes available.</span></span>  
  
    -   <span data-ttu-id="97c07-156">如果主體伺服器的連接仍然中斷，而鏡像與見證彼此重新連接，則會因為可能發生資料遺失而無法進行自動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="97c07-156">If the principal server remains disconnected, but the mirror and witness reconnect to each other, automatic failover cannot occur because data loss might occur.</span></span> <span data-ttu-id="97c07-157">因此，除非主體伺服器重新加入工作階段，否則資料庫仍然無法使用。</span><span class="sxs-lookup"><span data-stu-id="97c07-157">Therefore, the database remains unavailable, until the principal server rejoins the session.</span></span>  
  
    -   <span data-ttu-id="97c07-158">當所有三個伺服器執行個體重新連接時，將會重新取得完整仲裁，而且工作階段也會繼續其一般作業。</span><span class="sxs-lookup"><span data-stu-id="97c07-158">When all three server instances have reconnected, full quorum is regained, and the session resumes its regular operation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="97c07-159">當工作階段具有夥伴對夥伴仲裁時，如果任一個夥伴失去仲裁，工作階段就會失去仲裁。</span><span class="sxs-lookup"><span data-stu-id="97c07-159">When a session has a partner-to-partner quorum, if either partner loses quorum, the session loses quorum.</span></span> <span data-ttu-id="97c07-160">因此，如果要讓見證的連接中斷好一陣子，我們建議您暫時從工作階段中移除見證。</span><span class="sxs-lookup"><span data-stu-id="97c07-160">Therefore, if you expect the witness to remain disconnected for lots of time, we recommend that you temporarily remove the witness from the session.</span></span> <span data-ttu-id="97c07-161">移除見證便會移除對仲裁的需求。</span><span class="sxs-lookup"><span data-stu-id="97c07-161">Removing the witness removes the requirement for quorum.</span></span> <span data-ttu-id="97c07-162">那麼，如果鏡像伺服器連接中斷了，則還有主體伺服器可以繼續服務資料庫。</span><span class="sxs-lookup"><span data-stu-id="97c07-162">Then, if the mirror server becomes disconnected, the principal server can continue to serve the database.</span></span> <span data-ttu-id="97c07-163">如需如何加入或移除見證的資訊，請參閱 [資料庫鏡像見證](database-mirroring-witness.md)。</span><span class="sxs-lookup"><span data-stu-id="97c07-163">For information about how to add or remove a witness, see [Database Mirroring Witness](database-mirroring-witness.md).</span></span>  
  
### <a name="how-quorum-affects-database-availability"></a><span data-ttu-id="97c07-164">仲裁如何影響資料庫可用性</span><span class="sxs-lookup"><span data-stu-id="97c07-164">How Quorum Affects Database Availability</span></span>  
 <span data-ttu-id="97c07-165">下圖顯示見證與夥伴如何共同合作以確保在指定時間內，只有一個夥伴可擁有主體角色，而且只有目前的主體伺服器可使其資料庫上線。</span><span class="sxs-lookup"><span data-stu-id="97c07-165">The following illustration shows how the witness and the partners cooperate to make sure that, at given time, only one partner owns the role of principal and only the current principal server can bring its database online.</span></span> <span data-ttu-id="97c07-166">這兩個案例會從完整仲裁開始進行，其中的 **Partner_A** 是主體角色，而 **Partner_B** 則是鏡像角色。</span><span class="sxs-lookup"><span data-stu-id="97c07-166">Both scenarios start with full quorum, and **Partner_A** in the principal role and **Partner_B** in the mirror role.</span></span>  
  
 <span data-ttu-id="97c07-167">![見證與夥伴如何合作](../media/dbm-quorum-scenarios.gif "見證與夥伴如何合作")</span><span class="sxs-lookup"><span data-stu-id="97c07-167">![How the witness and partners cooperate](../media/dbm-quorum-scenarios.gif "How the witness and partners cooperate")</span></span>  
  
 <span data-ttu-id="97c07-168">案例 1 顯示在原始主體伺服器 (**Partner_A**) 失敗之後，見證和鏡像如何同意主體伺服器 **Partner_A**不再可用，從而形成仲裁。</span><span class="sxs-lookup"><span data-stu-id="97c07-168">Scenario 1 shows how after the original principal server (**Partner_A**) fails, the witness and mirror agree that the principal, **Partner_A**, is not available any longer and form quorum.</span></span> <span data-ttu-id="97c07-169">接著，由鏡像伺服器 **Partner_B** 承擔主體角色。</span><span class="sxs-lookup"><span data-stu-id="97c07-169">The mirror, **Partner_B** then assumes the principal role.</span></span> <span data-ttu-id="97c07-170">這會發生自動容錯移轉，且 **Partner_B**會讓其資料庫副本連線工作。</span><span class="sxs-lookup"><span data-stu-id="97c07-170">Automatic failover occurs, and **Partner_B**, brings its copy of the database online.</span></span> <span data-ttu-id="97c07-171">接著 **Partner_B** 會關閉，且資料庫會離線。</span><span class="sxs-lookup"><span data-stu-id="97c07-171">Then **Partner_B** goes down, and the database goes offline.</span></span> <span data-ttu-id="97c07-172">稍後，先前的主體伺服器 **Partner_A**會重新連接到見證以重新取得仲裁，但與見證溝通時， **Partner_A** 將會得知它無法使其資料庫副本上線，因為 **Partner_B** 現在擁有主體角色。</span><span class="sxs-lookup"><span data-stu-id="97c07-172">Later, the former principal server, **Partner_A**, reconnects to the witness regaining quorum, but on communicating with the witness, **Partner_A** learns that it cannot bring its copy of the database online, because **Partner_B** now owns the principal role.</span></span> <span data-ttu-id="97c07-173">當 **Partner_B** 重新加入工作階段時，它會將其資料庫連線工作。</span><span class="sxs-lookup"><span data-stu-id="97c07-173">When **Partner_B** rejoins the session, it brings the database back online.</span></span>  
  
 <span data-ttu-id="97c07-174">在案例 2 中，見證失去仲裁，而夥伴 **Partner_A** 和 **Partner_B**則彼此保有仲裁，且資料庫會維持在線上。</span><span class="sxs-lookup"><span data-stu-id="97c07-174">In Scenario 2, the witness loses quorum, while the partners, **Partner_A** and **Partner_B**, retain quorum with each other, and the database remains online.</span></span> <span data-ttu-id="97c07-175">接著，夥伴也遺失其仲裁，且資料庫會離線。</span><span class="sxs-lookup"><span data-stu-id="97c07-175">Then the partners lose their quorum, too, and the database goes offline.</span></span> <span data-ttu-id="97c07-176">稍後，主體伺服器 **Partner_A**會重新連接到見證以重新取得仲裁。</span><span class="sxs-lookup"><span data-stu-id="97c07-176">Later, the principal server, **Partner_A**, reconnects to the witness regaining quorum.</span></span> <span data-ttu-id="97c07-177">見證會確認 **Partner_A** 是否仍然擁有主體角色，且 **Partner_A** 會將其資料庫連線工作。</span><span class="sxs-lookup"><span data-stu-id="97c07-177">The witness confirms that **Partner_A** still owns the principal role, and **Partner_A** brings the database back online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97c07-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97c07-178">See Also</span></span>  
 <span data-ttu-id="97c07-179">[資料庫鏡像作業模式](database-mirroring-operating-modes.md) </span><span class="sxs-lookup"><span data-stu-id="97c07-179">[Database Mirroring Operating Modes](database-mirroring-operating-modes.md) </span></span>  
 <span data-ttu-id="97c07-180">[資料庫鏡像工作階段期間的角色切換 &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="97c07-180">[Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md) </span></span>  
 <span data-ttu-id="97c07-181">[資料庫鏡像見證](database-mirroring-witness.md) </span><span class="sxs-lookup"><span data-stu-id="97c07-181">[Database Mirroring Witness](database-mirroring-witness.md) </span></span>  
 <span data-ttu-id="97c07-182">[資料庫鏡像期間可能發生的失敗](possible-failures-during-database-mirroring.md) </span><span class="sxs-lookup"><span data-stu-id="97c07-182">[Possible Failures During Database Mirroring](possible-failures-during-database-mirroring.md) </span></span>  
 [<span data-ttu-id="97c07-183">鏡像狀態 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="97c07-183">Mirroring States &#40;SQL Server&#41;</span></span>](mirroring-states-sql-server.md)  
  
  
