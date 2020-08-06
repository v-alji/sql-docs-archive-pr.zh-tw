---
title: 鏡像備份媒體集 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- recovery [SQL Server], mirrored backups
- mirrored media sets [SQL Server]
- backup mirrors [SQL Server]
- duplicate backup copies
- interchangeable backup copies [SQL Server]
- media sets [SQL Server], mirrored backup media sets
- backup media [SQL Server], mirrored media
ms.assetid: 05a0b8d1-3585-4f77-972f-69d1c0d4aa9b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ce3513c67a0087dd00021de75f360b19819b46db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606373"
---
# <a name="mirrored-backup-media-sets-sql-server"></a><span data-ttu-id="d2663-102">鏡像備份媒體集 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d2663-102">Mirrored Backup Media Sets (SQL Server)</span></span>
    
> [!NOTE]  
>  <span data-ttu-id="d2663-103">只有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Enterprise Edition 才支援鏡像備份媒體集。</span><span class="sxs-lookup"><span data-stu-id="d2663-103">Mirrored backup media sets are supported only in the Enterprise edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="d2663-104">鏡像媒體集可降低備份裝置功能不正常的影響，進而提高備份可靠性。</span><span class="sxs-lookup"><span data-stu-id="d2663-104">Mirroring a media set increases backup reliability by reducing the impact of backup-device malfunctions.</span></span> <span data-ttu-id="d2663-105">這些功能不正常特別嚴重，因為備份是避免資料遺失的最後一道防線。</span><span class="sxs-lookup"><span data-stu-id="d2663-105">These malfunctions are very serious because backups are the last line of defense against data loss.</span></span> <span data-ttu-id="d2663-106">隨著資料庫增長，備份裝置或媒體失敗導致備份無法還原的機會也越大。</span><span class="sxs-lookup"><span data-stu-id="d2663-106">As databases grow, the probability increases that a failure of a backup device or media will make a backup nonrestorable.</span></span> <span data-ttu-id="d2663-107">鏡像備份媒體提供的備援性可以提升備份的可靠性。</span><span class="sxs-lookup"><span data-stu-id="d2663-107">Mirroring backup media increases the reliability of backups by providing redundancy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d2663-108">如需媒體集的一般資訊，請參閱 [媒體集、媒體家族與備份組 &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)Enterprise Edition 才支援鏡像備份媒體集。</span><span class="sxs-lookup"><span data-stu-id="d2663-108">For information about media sets in general, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
 <span data-ttu-id="d2663-109">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="d2663-109">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="d2663-110">鏡像媒體集概觀</span><span class="sxs-lookup"><span data-stu-id="d2663-110">Overview of Mirrored Media Sets</span></span>](#OverviewofMirroredMediaSets)  
  
-   [<span data-ttu-id="d2663-111">備份鏡像的硬體需求</span><span class="sxs-lookup"><span data-stu-id="d2663-111">Hardware Requirements for Backup Mirrors</span></span>](#HardwareReqs)  
  
-   [<span data-ttu-id="d2663-112">相關工作</span><span class="sxs-lookup"><span data-stu-id="d2663-112">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="overview-of-mirrored-media-sets"></a><a name="OverviewofMirroredMediaSets"></a> <span data-ttu-id="d2663-113">鏡像媒體集概觀</span><span class="sxs-lookup"><span data-stu-id="d2663-113">Overview of Mirrored Media Sets</span></span>  
 <span data-ttu-id="d2663-114">媒體鏡像是媒體集的一種屬性。</span><span class="sxs-lookup"><span data-stu-id="d2663-114">Media mirroring is a property of the media set.</span></span> <span data-ttu-id="d2663-115">「鏡像媒體集」  是由多份媒體集複本 (「鏡像」  ) 組成。</span><span class="sxs-lookup"><span data-stu-id="d2663-115">A *mirrored media set* consists of multiple copies (*mirrors*) of the media set.</span></span> <span data-ttu-id="d2663-116">媒體集包含一個或多個媒體家族，其中每一個都對應到備份裝置。</span><span class="sxs-lookup"><span data-stu-id="d2663-116">A media set contains one or more media families, each of which corresponds to a backup device.</span></span> <span data-ttu-id="d2663-117">例如，如果 BACKUP DATABASE 陳述式的 TO 子句列出三個裝置，BACKUP 會將資料分散在三個媒體家族中，每個裝置一份資料。</span><span class="sxs-lookup"><span data-stu-id="d2663-117">For example, if the TO clause of a BACKUP DATABASE statement lists three devices, BACKUP spreads the data among three media families, one per device.</span></span> <span data-ttu-id="d2663-118">建立媒體集 (由 BACKUP DATABASE 陳述式指定 WITH FORMAT) 時，就會定義媒體家族和鏡像的數目。</span><span class="sxs-lookup"><span data-stu-id="d2663-118">The number of media families and mirrors is defined when the media set is created (by a BACKUP DATABASE statement that specifies WITH FORMAT).</span></span>  
  
 <span data-ttu-id="d2663-119">鏡像媒體集包含二到四個鏡像。</span><span class="sxs-lookup"><span data-stu-id="d2663-119">A mirrored media set possesses from two to four mirrors.</span></span> <span data-ttu-id="d2663-120">每個鏡像都包含媒體集中的所有媒體家族。</span><span class="sxs-lookup"><span data-stu-id="d2663-120">Each mirror contains all the media families in the media set.</span></span> <span data-ttu-id="d2663-121">鏡像需要相同數目的裝置，每個媒體家族有一個裝置。</span><span class="sxs-lookup"><span data-stu-id="d2663-121">The mirrors require the same number of devices, one per media family.</span></span> <span data-ttu-id="d2663-122">每個鏡像需要每個媒體家族有不同的備份裝置。</span><span class="sxs-lookup"><span data-stu-id="d2663-122">Each mirror requires a separate backup device for each media family.</span></span> <span data-ttu-id="d2663-123">例如，由四個媒體家族而有三個鏡像組成的鏡像媒體集需要十二個備份裝置。</span><span class="sxs-lookup"><span data-stu-id="d2663-123">For example, a mirrored media set that consists of four media families with three mirrors requires twelve backup devices.</span></span> <span data-ttu-id="d2663-124">所有裝置都必須相同。</span><span class="sxs-lookup"><span data-stu-id="d2663-124">All of these devices must be equivalent.</span></span> <span data-ttu-id="d2663-125">例如，相同製造商所提供的相同型號磁帶機。</span><span class="sxs-lookup"><span data-stu-id="d2663-125">For example, tape drives that have the same model number from the same manufacturer.</span></span>  
  
 <span data-ttu-id="d2663-126">下圖提供以兩個鏡像的兩個媒體家族組成的鏡像媒體集範例。</span><span class="sxs-lookup"><span data-stu-id="d2663-126">The following illustration shows an example of a mirrored media set that consists of two media families with two mirrors.</span></span> <span data-ttu-id="d2663-127">每個媒體家族都包含三個媒體磁碟區，磁碟區是每個鏡像備份一次。</span><span class="sxs-lookup"><span data-stu-id="d2663-127">Each media family contains three media volumes, which are backed up one time per mirror.</span></span>  
  
 <span data-ttu-id="d2663-128">![鏡像媒體集：兩個具有兩個鏡像的家族](../../database-engine/media/bnr-backup-media-mirror.gif "鏡像媒體集：兩個具有兩個鏡像的家族")</span><span class="sxs-lookup"><span data-stu-id="d2663-128">![Mirrored media set: two families with two mirrors](../../database-engine/media/bnr-backup-media-mirror.gif "Mirrored media set: two families with two mirrors")</span></span>  
  
 <span data-ttu-id="d2663-129">鏡像上對應磁碟區有相同的內容。</span><span class="sxs-lookup"><span data-stu-id="d2663-129">Corresponding volumes on the mirrors have identical contents.</span></span> <span data-ttu-id="d2663-130">如此可在還原時互換。</span><span class="sxs-lookup"><span data-stu-id="d2663-130">This makes them interchangeable at restore time.</span></span> <span data-ttu-id="d2663-131">例如在之前圖表中，tape2 的第三個磁碟區可與 tape0 的第三個磁碟區互換。</span><span class="sxs-lookup"><span data-stu-id="d2663-131">For example, in the previous illustration, the third volume of tape2 is interchangeable with the third volume of tape0.</span></span>  
  
 <span data-ttu-id="d2663-132">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 會同步寫入每個裝置，以保證鏡像媒體具有完全相同的內容。</span><span class="sxs-lookup"><span data-stu-id="d2663-132">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] guarantees that the mirrored media have identical contents by synchronizing writes to the devices.</span></span> <span data-ttu-id="d2663-133">其中任何一個鏡像填滿時，會同時跨裝置填滿所有鏡像。</span><span class="sxs-lookup"><span data-stu-id="d2663-133">When any one of the mirrors fills, all the mirrors are spanned at one time.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d2663-134">您無法藉由移除鏡像的方式，將鏡像媒體集以隱含方式打散 (分割)。</span><span class="sxs-lookup"><span data-stu-id="d2663-134">A mirrored media set cannot be implicitly broken (split) by removing a mirror.</span></span> <span data-ttu-id="d2663-135">若鏡像中的任何磁帶或磁碟損壞或重新格式化，則該鏡像就不能再用於其他備份作業。</span><span class="sxs-lookup"><span data-stu-id="d2663-135">If any tape or disk in a mirror is damaged or reformatted, the mirror is no longer usable for additional backups.</span></span> <span data-ttu-id="d2663-136">若最後還有一個完整鏡像作用中，則可以讀取該媒體集。</span><span class="sxs-lookup"><span data-stu-id="d2663-136">If at least one full mirror remains intact, the media set can be read.</span></span> <span data-ttu-id="d2663-137">若每個鏡像都遺失特定媒體家族，則該媒體集沒有用處。</span><span class="sxs-lookup"><span data-stu-id="d2663-137">If every mirror loses a given media family, the media set is useless.</span></span>  
  
 <span data-ttu-id="d2663-138">備份和還原作業的需求視所有鏡像是否必須存在而異。</span><span class="sxs-lookup"><span data-stu-id="d2663-138">Backup and restore operations impose different requirements on whether all the mirrors must be present.</span></span> <span data-ttu-id="d2663-139">若要讓備份作業寫入 (亦即，建立或擴充) 鏡像媒體集，所有的鏡像都必須存在。</span><span class="sxs-lookup"><span data-stu-id="d2663-139">For a backup operation to write (that is, to create or extend) a mirrored media set, all the mirrors must be present.</span></span> <span data-ttu-id="d2663-140">相對地，當從鏡像媒體集中還原備份時，每個媒體家族只能指定單一鏡像。</span><span class="sxs-lookup"><span data-stu-id="d2663-140">In contrast, when you are restoring a backup from a mirrored media set, you can specify only a single mirror for each media family.</span></span> <span data-ttu-id="d2663-141">您可以從比家族少的裝置進行還原，但每個媒體家族只處理一次。</span><span class="sxs-lookup"><span data-stu-id="d2663-141">You can restore from fewer devices than families, but each media family is processed only one time.</span></span> <span data-ttu-id="d2663-142">不過，如果有其他鏡像，當出現錯誤時，解決部分還原問題的速度會比較快。</span><span class="sxs-lookup"><span data-stu-id="d2663-142">In the presence of errors, however, having the other mirrors enables some restore problems to be resolved quickly.</span></span> <span data-ttu-id="d2663-143">您可以利用另一個鏡像的對應磁碟區來替代損毀的媒體磁碟區。</span><span class="sxs-lookup"><span data-stu-id="d2663-143">You can substitute a damaged media volume with the corresponding volume from another mirror.</span></span> <span data-ttu-id="d2663-144">這是因為 RESTORE 與 RESTORE VERIFYONLY 支援使用另一個鏡像的對應備份媒體磁碟區來替換損壞的媒體。</span><span class="sxs-lookup"><span data-stu-id="d2663-144">This is because RESTORE and RESTORE VERIFYONLY support substitution of damaged media with the corresponding backup-media volume from another mirror.</span></span>  
  
##  <a name="hardware-requirements-for-backup-mirrors"></a><a name="HardwareReqs"></a> <span data-ttu-id="d2663-145">備份鏡像的硬體需求</span><span class="sxs-lookup"><span data-stu-id="d2663-145">Hardware Requirements for Backup Mirrors</span></span>  
 <span data-ttu-id="d2663-146">鏡像適用於磁碟與磁帶 (磁碟不支援接續磁帶)。</span><span class="sxs-lookup"><span data-stu-id="d2663-146">Mirroring applies both to disk and tape (disks do not support continuation tapes).</span></span> <span data-ttu-id="d2663-147">單一備份或還原作業的所有備份裝置都必須是相同類型 - 磁碟或磁帶。</span><span class="sxs-lookup"><span data-stu-id="d2663-147">All backup devices for a single backup or restore operation must be of the same type, disk or tape.</span></span>  
  
 <span data-ttu-id="d2663-148">在這些廣泛的類別中，您必須使用具有相同屬性的類似裝置。</span><span class="sxs-lookup"><span data-stu-id="d2663-148">Within these broader classes, you must use similar devices that have the same properties.</span></span> <span data-ttu-id="d2663-149">裝置不夠類似會產生錯誤訊息 (3212)。</span><span class="sxs-lookup"><span data-stu-id="d2663-149">Insufficiently similar devices generate an error message (3212).</span></span> <span data-ttu-id="d2663-150">為了避免裝置不符的風險，請使用相同的裝置，例如，只使用相同製造商製造的同型號磁碟機。</span><span class="sxs-lookup"><span data-stu-id="d2663-150">To avoid the risk of a device mismatch, use devices that are equivalent, such as, only drives with the same model number from the same manufacturer.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="d2663-151">相關工作</span><span class="sxs-lookup"><span data-stu-id="d2663-151">Related Tasks</span></span>  
 <span data-ttu-id="d2663-152">**若要備份至鏡像備份裝置**</span><span class="sxs-lookup"><span data-stu-id="d2663-152">**To back up to mirrored backup devices**</span></span>  
  
-   [<span data-ttu-id="d2663-153">備份至鏡像媒體集 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d2663-153">Back Up to a Mirrored Media Set &#40;Transact-SQL&#41;</span></span>](back-up-to-a-mirrored-media-set-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="d2663-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2663-154">See Also</span></span>  
 <span data-ttu-id="d2663-155">[備份和還原期間可能發生的媒體錯誤 &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d2663-155">[Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md) </span></span>  
 <span data-ttu-id="d2663-156">[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d2663-156">[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) </span></span>  
 <span data-ttu-id="d2663-157">[備份裝置 &#40;SQL Server&#41;](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d2663-157">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 [<span data-ttu-id="d2663-158">媒體集、媒體家族與備份組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d2663-158">Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
  
  
