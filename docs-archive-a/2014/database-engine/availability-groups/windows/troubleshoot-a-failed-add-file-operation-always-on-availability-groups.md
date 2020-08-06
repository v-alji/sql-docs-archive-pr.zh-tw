---
title: 針對失敗的新增檔案作業進行疑難排解 (AlwaysOn 可用性群組) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- secondary databases [SQL Server], Availability Groups
- Availability Groups [SQL Server], troubleshooting
ms.assetid: 31ceaebf-864b-4dd0-9112-0d047b0316ad
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2551080c214f18473caa71a3e17797c34fcc943a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708630"
---
# <a name="troubleshoot-a-failed-add-file-operation-alwayson-availability-groups"></a><span data-ttu-id="c6e5f-102">疑難排解失敗的加入檔案作業 (AlwaysOn 可用性群組)</span><span class="sxs-lookup"><span data-stu-id="c6e5f-102">Troubleshoot a Failed Add-File Operation (AlwaysOn Availability Groups)</span></span>
  <span data-ttu-id="c6e5f-103">在某些 AlwaysOn 可用性群組部署中，在裝載主要複本的系統和裝載次要複本的系統之間會有檔案路徑差異。</span><span class="sxs-lookup"><span data-stu-id="c6e5f-103">In some AlwaysOn availability group deployments, file paths differ between the system that hosts the primary replica and systems that host a secondary replica.</span></span> <span data-ttu-id="c6e5f-104">如果加入檔案作業的檔案路徑不存在於次要複本，則加入檔案作業將會在主要資料庫上成功完成。</span><span class="sxs-lookup"><span data-stu-id="c6e5f-104">If the file path of an add-file operation does not exist on a secondary replica, the add-file operation will succeed on the primary database.</span></span> <span data-ttu-id="c6e5f-105">但是加入檔案作業會造成次要資料庫暫停。</span><span class="sxs-lookup"><span data-stu-id="c6e5f-105">But the add-file operation will cause the secondary database to be suspended.</span></span> <span data-ttu-id="c6e5f-106">而這又會導致次要複本進入 NOT SYNCHRONIZING 狀態。</span><span class="sxs-lookup"><span data-stu-id="c6e5f-106">This, in turn, causes the secondary replica to enter the NOT SYNCHRONIZING state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c6e5f-107">我們建議，給定次要資料庫的檔案路徑 (包括磁碟機代號) 盡可能與對應主要資料庫的路徑完全相同。</span><span class="sxs-lookup"><span data-stu-id="c6e5f-107">We recommend that, if possible, the file path (including the drive letter) of a given secondary database be identical to the path of the corresponding primary database.</span></span>  
  
## <a name="problem-resolution"></a><span data-ttu-id="c6e5f-108">解決問題</span><span class="sxs-lookup"><span data-stu-id="c6e5f-108">Problem Resolution</span></span>  
 <span data-ttu-id="c6e5f-109">若要解決此問題，資料庫擁有者必須完成以下步驟：</span><span class="sxs-lookup"><span data-stu-id="c6e5f-109">To resolve this problem the database owner must complete the following steps:</span></span>  
  
1.  <span data-ttu-id="c6e5f-110">從可用性群組中移除次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="c6e5f-110">Remove the secondary database from the availability group.</span></span> <span data-ttu-id="c6e5f-111">如需詳細資訊，請參閱[將次要資料庫從可用性群組移除 &#40;SQL Server&#41;](remove-a-secondary-database-from-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="c6e5f-111">For more information, see [Remove a Secondary Database from an Availability Group &#40;SQL Server&#41;](remove-a-secondary-database-from-an-availability-group-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="c6e5f-112">在現有次要資料庫上，使用 WITH NORECOVERY 和 WITH MOVE (指定裝載次要複本之伺服器執行個體上的檔案路徑)，將包含加入之檔案的檔案群組的完整備份還原到次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="c6e5f-112">On the existing secondary database, restore a full backup of the filegroup that contains the added file to the secondary database, using WITH NORECOVERY and WITH MOVE (specifying the file path on the server instance that hosts the secondary replica).</span></span> <span data-ttu-id="c6e5f-113">如需詳細資訊，請參閱[將資料庫還原到新位置 &#40;SQL Server&#41;](../../../relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="c6e5f-113">For more information, see [Restore a Database to a New Location &#40;SQL Server&#41;](../../../relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md).</span></span>  
  
3.  <span data-ttu-id="c6e5f-114">在主要伺服器上備份包含加入檔案作業的交易記錄，並且使用 WITH NORECOVERY 和 WITH MOVE 手動在次要資料庫上還原記錄備份。</span><span class="sxs-lookup"><span data-stu-id="c6e5f-114">Back up the transaction log that contains the add-file operation on the primary database, and manually restore the log backup on the secondary database using WITH NORECOVERY and WITH MOVE.</span></span>  
  
4.  <span data-ttu-id="c6e5f-115">透過使用 WITH NO RECOVERY 從主要資料庫還原任何其他未完成的記錄備份，準備次要資料庫重新加入可用性群組。</span><span class="sxs-lookup"><span data-stu-id="c6e5f-115">Prepare the secondary database for re-joining the availability group, by restoring, WITH NO RECOVERY, any other outstanding log backups from the primary database.</span></span>  
  
5.  <span data-ttu-id="c6e5f-116">將次要資料庫重新加入可用性群組。</span><span class="sxs-lookup"><span data-stu-id="c6e5f-116">Rejoin the secondary database to the availability group.</span></span> <span data-ttu-id="c6e5f-117">如需詳細資訊，請參閱 [將次要資料庫聯結至可用性群組 &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="c6e5f-117">For more information, see [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6e5f-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6e5f-118">See Also</span></span>  
 <span data-ttu-id="c6e5f-119">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c6e5f-119">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="c6e5f-120">[針對可用性群組手動準備次要資料庫 &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c6e5f-120">[Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md) </span></span>  
 <span data-ttu-id="c6e5f-121">[孤立的使用者疑難排解 &#40;SQL Server&#41;](../../../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c6e5f-121">[Troubleshoot Orphaned Users &#40;SQL Server&#41;](../../../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md) </span></span>  
 [<span data-ttu-id="c6e5f-122">針對 AlwaysOn 可用性群組 Configuration &#40;SQL Server&#41;已刪除進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="c6e5f-122">Troubleshoot AlwaysOn Availability Groups Configuration &#40;SQL Server&#41;deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
  
