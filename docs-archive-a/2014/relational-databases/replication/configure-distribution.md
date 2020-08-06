---
title: 設定散發 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], distribution
- distribution configuration [SQL Server replication]
- remote Distributors [SQL Server replication]
- transactional replication, configuring distribution
- distribution databases [SQL Server replication], sizing
- Distributors [SQL Server replication], configuring
- distribution databases [SQL Server replication], about distribution databases
- distribution databases [SQL Server replication]
- merge replication [SQL Server replication], configuring distribution
ms.assetid: 94d52169-384e-4885-84eb-2304e967d9f7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b0378fe285ba57e1420b7e6bebf5e2e6fe13d29e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593945"
---
# <a name="configure-distribution"></a><span data-ttu-id="e70e4-102">設定散發</span><span class="sxs-lookup"><span data-stu-id="e70e4-102">Configure Distribution</span></span>
  <span data-ttu-id="e70e4-103">「散發者」是包含散發資料庫的伺服器，該資料庫會存儲所有類型之複寫的中繼資料和記錄資料，以及異動複寫的交易。</span><span class="sxs-lookup"><span data-stu-id="e70e4-103">The Distributor is a server that contains the distribution database, which stores metadata and history data for all types of replication and transactions for transactional replication.</span></span> <span data-ttu-id="e70e4-104">若要設定複寫，您必須設定「散發者」。</span><span class="sxs-lookup"><span data-stu-id="e70e4-104">To set up replication, you must configure a Distributor.</span></span> <span data-ttu-id="e70e4-105">每個「發行者」可以僅指派給一個「散發者」執行個體，但是多個發行者可以共用一個「散發者」。</span><span class="sxs-lookup"><span data-stu-id="e70e4-105">Each Publisher can be assigned to only a single Distributor instance, but multiple publishers can share a Distributor.</span></span> <span data-ttu-id="e70e4-106">散發者會使用所在伺服器的下列額外資源：</span><span class="sxs-lookup"><span data-stu-id="e70e4-106">The Distributor uses these additional resources on the server where it is located:</span></span>  
  
-   <span data-ttu-id="e70e4-107">如果發行集的快照集檔案儲存於「散發者」(通常如此) 時，則使用額外的磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="e70e4-107">Additional disk space if the snapshot files for the publication are stored on the Distributor (which they typically are).</span></span>  
  
-   <span data-ttu-id="e70e4-108">儲存散發資料庫的額外空間。</span><span class="sxs-lookup"><span data-stu-id="e70e4-108">Additional disk space to store the distribution database.</span></span>  
  
-   <span data-ttu-id="e70e4-109">針對在散發者上執行的發送訂閱，複寫代理程式會使用額外處理器資源。</span><span class="sxs-lookup"><span data-stu-id="e70e4-109">Additional processor usage by replication agents for push subscriptions running on the Distributor.</span></span>  
  
 <span data-ttu-id="e70e4-110">您選擇作為散發者的伺服器，應該具備足夠的磁碟空間及處理器動力，以便支援該伺服器的複寫及所有其他活動。</span><span class="sxs-lookup"><span data-stu-id="e70e4-110">The server you select as the Distributor should have adequate disk space and processor power to support replication and any other activities on that server.</span></span> <span data-ttu-id="e70e4-111">在您設定「散發者」時，需指定下列項目：</span><span class="sxs-lookup"><span data-stu-id="e70e4-111">When you configure the Distributor, you specify the following:</span></span>  
  
-   <span data-ttu-id="e70e4-112">快照集資料夾，依預設，該資料夾用於所有使用此「散發者」的「發行者」。</span><span class="sxs-lookup"><span data-stu-id="e70e4-112">A snapshot folder, which is used, by default, for all Publishers that use this Distributor.</span></span> <span data-ttu-id="e70e4-113">確定此資料夾已共用，並已設定適當的權限。</span><span class="sxs-lookup"><span data-stu-id="e70e4-113">Ensure that this folder is already shared and has the appropriate permissions set.</span></span> <span data-ttu-id="e70e4-114">如需詳細資訊，請參閱[保護快照集資料夾](security/secure-the-snapshot-folder.md)。</span><span class="sxs-lookup"><span data-stu-id="e70e4-114">For more information, see [Secure the Snapshot Folder](security/secure-the-snapshot-folder.md).</span></span>  
  
-   <span data-ttu-id="e70e4-115">散發資料庫的名稱和檔案位置。</span><span class="sxs-lookup"><span data-stu-id="e70e4-115">A name and file locations for the distribution database.</span></span> <span data-ttu-id="e70e4-116">散發資料庫建立後，不能重新命名。</span><span class="sxs-lookup"><span data-stu-id="e70e4-116">The distribution database cannot be renamed after it is created.</span></span> <span data-ttu-id="e70e4-117">若要使用不同的資料庫名稱，則必須停用散發並對它進行重新設定。</span><span class="sxs-lookup"><span data-stu-id="e70e4-117">To use a different name for the database, you must disable distribution and reconfigure it.</span></span>  
  
-   <span data-ttu-id="e70e4-118">任何授權使用「散發者」的「發行者」。</span><span class="sxs-lookup"><span data-stu-id="e70e4-118">Any Publishers authorized to use the Distributor.</span></span> <span data-ttu-id="e70e4-119">如果指定「發行者」，而不是「散發者」執行的執行個體，則還必須指定「發行者」連接到遠端「散發者」的密碼。</span><span class="sxs-lookup"><span data-stu-id="e70e4-119">If you specify Publishers other than the instance on which the Distributor runs, you must also specify a password for the connections the Publishers make to the remote Distributor.</span></span>  
  
 <span data-ttu-id="e70e4-120">對於異動複寫，在設定散發之後，我們建議您：</span><span class="sxs-lookup"><span data-stu-id="e70e4-120">For transactional replication, after you configure distribution, we recommend that you:</span></span>  
  
-   <span data-ttu-id="e70e4-121">適當調整散發資料庫的大小。</span><span class="sxs-lookup"><span data-stu-id="e70e4-121">Size the distribution database appropriately.</span></span> <span data-ttu-id="e70e4-122">用一般負載量為系統測試複寫，以決定需要多少空間儲存命令。</span><span class="sxs-lookup"><span data-stu-id="e70e4-122">Test replication with a typical load for your system to determine how much space is required to store commands.</span></span> <span data-ttu-id="e70e4-123">確認資料庫大小足夠儲存命令，且無須經常自動成長。</span><span class="sxs-lookup"><span data-stu-id="e70e4-123">Ensure the database is large enough to store commands without having to auto-grow frequently.</span></span> <span data-ttu-id="e70e4-124">如需變更資料庫大小的詳細資訊，請參閱 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e70e4-124">For more information about changing the size of a database, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
-   <span data-ttu-id="e70e4-125">在散發資料庫設定 **sync with backup** 選項。</span><span class="sxs-lookup"><span data-stu-id="e70e4-125">Set the **sync with backup** option on the distribution database.</span></span> <span data-ttu-id="e70e4-126">如需詳細資訊，請參閱[備份與還原快照式和異動複寫的策略](administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md)和[為異動複寫啟用協調備份 &#40;複寫 Transact-SQL 程式設計&#41;](administration/enable-coordinated-backups-for-transactional-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="e70e4-126">For more information, see [Strategies for Backing Up and Restoring Snapshot and Transactional Replication](administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md) and [Enable Coordinated Backups for Transactional Replication &#40;Replication Transact-SQL Programming&#41;](administration/enable-coordinated-backups-for-transactional-replication.md).</span></span>  
  
## <a name="local-and-remote-distributors"></a><span data-ttu-id="e70e4-127">本機與遠端散發者</span><span class="sxs-lookup"><span data-stu-id="e70e4-127">Local and Remote Distributors</span></span>  
 <span data-ttu-id="e70e4-128">依預設，「散發者」可以和「發行者」(本機「散發者」) 為相同伺服器，也可以和「發行者」(遠端「散發者」) 為不同伺服器。</span><span class="sxs-lookup"><span data-stu-id="e70e4-128">By default, the Distributor is the same server as the Publisher (a local Distributor), but it can also be a separate server from the Publisher (a remote Distributor).</span></span> <span data-ttu-id="e70e4-129">如果您要執行下列項目，通常要選擇使用遠端「散發者」：</span><span class="sxs-lookup"><span data-stu-id="e70e4-129">Typically, you would choose to use a remote Distributor if you want to:</span></span>  
  
-   <span data-ttu-id="e70e4-130">如果您想使來自「發行者」上的複寫之影響為最小 (例如，如果「發行者」為 OLTP 伺服器)，則將處理卸載到其他電腦。</span><span class="sxs-lookup"><span data-stu-id="e70e4-130">Offload processing to another computer if you want minimal impact from replication on the Publisher (for example, if the Publisher is an OLTP server).</span></span>  
  
-   <span data-ttu-id="e70e4-131">為多個發行者設定集中化散發者</span><span class="sxs-lookup"><span data-stu-id="e70e4-131">Configure a centralized Distributor for multiple Publishers.</span></span>  
  
 <span data-ttu-id="e70e4-132">由於下列兩個原因，遠端「散發者」在異動複寫中比在合併式複寫中更為常見：</span><span class="sxs-lookup"><span data-stu-id="e70e4-132">Remote Distributors are more common in transactional replication than they are in merge replication for two reasons:</span></span>  
  
-   <span data-ttu-id="e70e4-133">「散發者」在異動複寫中扮演更重要的角色，因為所有複寫的交易會寫入散發資料庫，並從中讀取。</span><span class="sxs-lookup"><span data-stu-id="e70e4-133">The Distributor plays a larger role in transactional replication because all replicated transactions are written to and read from the distribution database.</span></span>  
  
-   <span data-ttu-id="e70e4-134">合併式複寫拓撲通常使用提取訂閱，所以代理程式會在每個「訂閱者」端執行，而不是在「散發者」端執行。</span><span class="sxs-lookup"><span data-stu-id="e70e4-134">Merge replication topologies typically use pull subscriptions, so agents run at each Subscriber, rather than all running at the Distributor.</span></span> <span data-ttu-id="e70e4-135">如需詳細資訊，請參閱[訂閱發行集](subscribe-to-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="e70e4-135">For more information, see [Subscribe to Publications](subscribe-to-publications.md).</span></span> <span data-ttu-id="e70e4-136">在大多數情況下，您應將使用合併式複寫的本機「散發者」。</span><span class="sxs-lookup"><span data-stu-id="e70e4-136">In most cases, you should use a local Distributor for merge replication.</span></span>  
  
 <span data-ttu-id="e70e4-137">若要設定發行和散發，請參閱＜ [Configure Publishing and Distribution](configure-publishing-and-distribution.md)＞。</span><span class="sxs-lookup"><span data-stu-id="e70e4-137">To configure publishing and distribution, see [Configure Publishing and Distribution](configure-publishing-and-distribution.md).</span></span>  
  
 <span data-ttu-id="e70e4-138">若要修改發行者和散發者屬性，請參閱＜ [View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md)＞。</span><span class="sxs-lookup"><span data-stu-id="e70e4-138">To modify Publisher and Distributor properties, see [View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e70e4-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e70e4-139">See Also</span></span>  
 <span data-ttu-id="e70e4-140">[發行資料和資料庫物件](publish/publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="e70e4-140">[Publish Data and Database Objects](publish/publish-data-and-database-objects.md) </span></span>  
 [<span data-ttu-id="e70e4-141">保護散發者</span><span class="sxs-lookup"><span data-stu-id="e70e4-141">Secure the Distributor</span></span>](security/secure-the-distributor.md)  
  
  
