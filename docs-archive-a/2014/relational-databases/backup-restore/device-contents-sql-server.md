---
title: 裝置內容 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.bnrdevicecontents.f1
ms.assetid: 95e1902e-8c7a-4830-bdf9-1a6aca414a24
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c904718eca671b1965a95d0d400f3f6fa075b500
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595136"
---
# <a name="device-contents-sql-server"></a><span data-ttu-id="d930d-102">裝置內容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d930d-102">Device Contents (SQL Server)</span></span>
  <span data-ttu-id="d930d-103">使用此對話方塊來檢視備份資訊。</span><span class="sxs-lookup"><span data-stu-id="d930d-103">Use this dialog box to view the backup information.</span></span> <span data-ttu-id="d930d-104">這個資訊描述裝置、媒體、媒體集，以及備份組。</span><span class="sxs-lookup"><span data-stu-id="d930d-104">This information describes the device, the media, the media set, and the backup set or sets.</span></span>  
  
 <span data-ttu-id="d930d-105">**若要使用 SQL Server Management Studio 檢視備份裝置的內容**</span><span class="sxs-lookup"><span data-stu-id="d930d-105">**To use SQL Server Management Studio to view the contents of a backup device**</span></span>  
  
-   [<span data-ttu-id="d930d-106">檢視備份磁帶或檔案的內容 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d930d-106">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="d930d-107">檢視邏輯備份裝置的屬性和內容 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d930d-107">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
## <a name="options"></a><span data-ttu-id="d930d-108">選項。</span><span class="sxs-lookup"><span data-stu-id="d930d-108">Options</span></span>  
 <span data-ttu-id="d930d-109">**媒體**</span><span class="sxs-lookup"><span data-stu-id="d930d-109">**Media**</span></span>  
 <span data-ttu-id="d930d-110">儲存備份資訊的磁碟或磁帶集。</span><span class="sxs-lookup"><span data-stu-id="d930d-110">A disk or set of tapes on which backup information is stored.</span></span>  
  
 <span data-ttu-id="d930d-111">**媒體順序**</span><span class="sxs-lookup"><span data-stu-id="d930d-111">**Media sequence**</span></span>  
 <span data-ttu-id="d930d-112">列出媒體序號、家族序號，以及鏡像識別碼 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="d930d-112">Lists the media sequence number, the family sequence number, and the mirror identifier, if any.</span></span> <span data-ttu-id="d930d-113">各個實體備份媒體都標記有媒體序號，指出媒體使用時的順序。</span><span class="sxs-lookup"><span data-stu-id="d930d-113">The physical backup media are each tagged with a media sequence number that indicates the order in which the media were used.</span></span> <span data-ttu-id="d930d-114">初始備份媒體標記為 1，第二個媒體 (第一個接續磁帶) 則標記為 2，依此類推。</span><span class="sxs-lookup"><span data-stu-id="d930d-114">The initial backup medium is tagged with 1, the second (the first continuation tape) is tagged with 2, and so forth.</span></span> <span data-ttu-id="d930d-115">還原備份組時，媒體序號可以確定進行還原的操作員，會以正確的順序主控正確的媒體。</span><span class="sxs-lookup"><span data-stu-id="d930d-115">When the backup set is restored, the media sequence numbers ensure that the operator that restores the backup mounts the correct media in the correct order.</span></span>  
  
 <span data-ttu-id="d930d-116">**建立於**</span><span class="sxs-lookup"><span data-stu-id="d930d-116">**Created on**</span></span>  
 <span data-ttu-id="d930d-117">顯示媒體日期。</span><span class="sxs-lookup"><span data-stu-id="d930d-117">Displays the media date.</span></span>  
  
 <span data-ttu-id="d930d-118">**媒體集**</span><span class="sxs-lookup"><span data-stu-id="d930d-118">**Media Set**</span></span>  
 <span data-ttu-id="d930d-119">媒體集是已排序的備份媒體集合，其中使用固定數目的備份裝置寫入一個或多個備份作業。</span><span class="sxs-lookup"><span data-stu-id="d930d-119">A media set is an ordered collection of backup media to which one or more backup operations have written using a constant number of backup devices.</span></span>  
  
 <span data-ttu-id="d930d-120">**名稱**</span><span class="sxs-lookup"><span data-stu-id="d930d-120">**Name**</span></span>  
 <span data-ttu-id="d930d-121">顯示媒體集的名稱。</span><span class="sxs-lookup"><span data-stu-id="d930d-121">Displays the name of the media set.</span></span>  
  
 <span data-ttu-id="d930d-122">**說明**</span><span class="sxs-lookup"><span data-stu-id="d930d-122">**Description**</span></span>  
 <span data-ttu-id="d930d-123">顯示媒體集的描述。</span><span class="sxs-lookup"><span data-stu-id="d930d-123">Displays the description media set.</span></span>  
  
 <span data-ttu-id="d930d-124">**媒體家族計數**</span><span class="sxs-lookup"><span data-stu-id="d930d-124">**Media family count**</span></span>  
 <span data-ttu-id="d930d-125">顯示媒體家族計數。</span><span class="sxs-lookup"><span data-stu-id="d930d-125">Displays the media family count.</span></span> <span data-ttu-id="d930d-126">各個媒體集皆是一個或多個媒體家族的集合。</span><span class="sxs-lookup"><span data-stu-id="d930d-126">Each media set is a collection of one or more media families.</span></span> <span data-ttu-id="d930d-127">所有輸出到給定的單一備份裝置 (或鏡像的備份裝置群組)，即形成一個單一媒體家族。</span><span class="sxs-lookup"><span data-stu-id="d930d-127">All the output to a given single backup device (or group of mirrored backup devices) forms a single media family.</span></span> <span data-ttu-id="d930d-128">每個媒體集的個別裝置 (或鏡像裝置的群組) 都包含一個媒體家族；例如，若媒體集使用兩個非鏡像備份裝置，則此媒體集會包含兩個媒體家族。</span><span class="sxs-lookup"><span data-stu-id="d930d-128">Each media set contains one media family per separate device (or group of mirrored devices); for example, if a media set uses two nonmirrored backup devices, the media set contains two media families.</span></span>  
  
 <span data-ttu-id="d930d-129">**備份組**</span><span class="sxs-lookup"><span data-stu-id="d930d-129">**Backup sets**</span></span>  
 <span data-ttu-id="d930d-130">顯示有關媒體上包含的備份組的資訊。</span><span class="sxs-lookup"><span data-stu-id="d930d-130">Displays information about the backup set or sets contained on the media.</span></span> <span data-ttu-id="d930d-131">備份組是成功備份作業的結果，其內容會在備份裝置組的媒體之間散發。</span><span class="sxs-lookup"><span data-stu-id="d930d-131">A backup set is the result of a successful backup operation whose content is distributed among the media on the set of backup devices.</span></span>  
  
|<span data-ttu-id="d930d-132">頁首</span><span class="sxs-lookup"><span data-stu-id="d930d-132">Header</span></span>|<span data-ttu-id="d930d-133">值</span><span class="sxs-lookup"><span data-stu-id="d930d-133">Values</span></span>|  
|------------|------------|  
|<span data-ttu-id="d930d-134">**名稱**</span><span class="sxs-lookup"><span data-stu-id="d930d-134">**Name**</span></span>|<span data-ttu-id="d930d-135">備份組的名稱。</span><span class="sxs-lookup"><span data-stu-id="d930d-135">The name of the backup set.</span></span>|  
|<span data-ttu-id="d930d-136">**型別**</span><span class="sxs-lookup"><span data-stu-id="d930d-136">**Type**</span></span>|<span data-ttu-id="d930d-137">執行的備份類型：[完整]、[差異] 或 [交易記錄]。</span><span class="sxs-lookup"><span data-stu-id="d930d-137">The type of backup performed: Full, Differential or Transaction Log.</span></span>|  
|<span data-ttu-id="d930d-138">**元件**</span><span class="sxs-lookup"><span data-stu-id="d930d-138">**Component**</span></span>|<span data-ttu-id="d930d-139">備份的元件：Database、File 或 *\<blank>* (適用於交易記錄)。</span><span class="sxs-lookup"><span data-stu-id="d930d-139">The backed-up component: Database, File, or *\<blank>* (for transaction logs).</span></span>|  
|<span data-ttu-id="d930d-140">**Server**</span><span class="sxs-lookup"><span data-stu-id="d930d-140">**Server**</span></span>|<span data-ttu-id="d930d-141">執行備份作業之 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="d930d-141">The name of the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] that performed the backup operation.</span></span>|  
|<span data-ttu-id="d930d-142">**Database**</span><span class="sxs-lookup"><span data-stu-id="d930d-142">**Database**</span></span>|<span data-ttu-id="d930d-143">已備份資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="d930d-143">The name of the database that was backed up.</span></span>|  
|<span data-ttu-id="d930d-144">**位置**</span><span class="sxs-lookup"><span data-stu-id="d930d-144">**Position**</span></span>|<span data-ttu-id="d930d-145">備份組在磁碟區中的位置。</span><span class="sxs-lookup"><span data-stu-id="d930d-145">The position of the backup set in the volume.</span></span>|  
|<span data-ttu-id="d930d-146">**日期**</span><span class="sxs-lookup"><span data-stu-id="d930d-146">**Date**</span></span>|<span data-ttu-id="d930d-147">備份作業完成時的日期和時間，會出現在用戶端的地區設定中。</span><span class="sxs-lookup"><span data-stu-id="d930d-147">The date and time when the backup operation finished, presented in the regional setting of the client.</span></span>|  
|<span data-ttu-id="d930d-148">**大小**</span><span class="sxs-lookup"><span data-stu-id="d930d-148">**Size**</span></span>|<span data-ttu-id="d930d-149">備份組的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="d930d-149">The size of the backup set in bytes.</span></span>|  
|<span data-ttu-id="d930d-150">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="d930d-150">**User Name**</span></span>|<span data-ttu-id="d930d-151">執行備份作業的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="d930d-151">The name of the user who performed the backup operation.</span></span>|  
|<span data-ttu-id="d930d-152">**到期**</span><span class="sxs-lookup"><span data-stu-id="d930d-152">**Expiration**</span></span>|<span data-ttu-id="d930d-153">備份組過期的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="d930d-153">The date and time the backup set expires.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d930d-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d930d-154">See Also</span></span>  
 [<span data-ttu-id="d930d-155">媒體集、媒體家族與備份組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d930d-155">Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
  
  
