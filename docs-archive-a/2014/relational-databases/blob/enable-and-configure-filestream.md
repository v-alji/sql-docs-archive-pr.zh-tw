---
title: 啟用及設定 FILESTREAM | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.technology: filestream
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], enabling
ms.assetid: 78737e19-c65b-48d9-8fa9-aa6f1e1bce73
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f6c0e505bd32636d045519b36e439bc21c7079d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584593"
---
# <a name="enable-and-configure-filestream"></a><span data-ttu-id="208e4-102">啟用及設定 FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="208e4-102">Enable and Configure FILESTREAM</span></span>
  <span data-ttu-id="208e4-103">在您開始使用 FILESTREAM 之前，必須先在 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]執行個體上啟用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="208e4-103">Before you can start to use FILESTREAM, you must enable FILESTREAM on the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="208e4-104">此主題描述如何使用 SQL Server 組態管理員來啟用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="208e4-104">This topic describes how to enable FILESTREAM by using SQL Server Configuration Manager.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="208e4-105">您無法針對在 64 位元作業系統上執行的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 32 位元版本啟用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="208e4-105">You cannot enable FILESTREAM on a 32-bit version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on a 64-bit operating system.</span></span>  
  
##  <a name="enabling-filestream"></a><a name="enabling"></a> <span data-ttu-id="208e4-106">啟用 FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="208e4-106">Enabling FILESTREAM</span></span>  
  
#### <a name="to-enable-and-change-filestream-settings"></a><span data-ttu-id="208e4-107">若要啟用和變更 FILESTREAM 設定</span><span class="sxs-lookup"><span data-stu-id="208e4-107">To enable and change FILESTREAM settings</span></span>  
  
1.  <span data-ttu-id="208e4-108">指向 **[開始]** 功能表上的 **[所有程式]** ，然後依序指向 [ [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]] 和 **[組態工具]** ，再按一下 **[SQL Server 組態管理員]** 。</span><span class="sxs-lookup"><span data-stu-id="208e4-108">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="208e4-109">在服務的清單中，以滑鼠右鍵按一下 [SQL Server 服務]  ，然後按一下 [開啟]  。</span><span class="sxs-lookup"><span data-stu-id="208e4-109">In the list of services, right-click **SQL Server Services**, and then click **Open**.</span></span>  
  
3.  <span data-ttu-id="208e4-110">在 [SQL Server 組態管理員]  嵌入式管理單元中，找出您想要啟用 FILESTREAM 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="208e4-110">In the **SQL Server Configuration Manager** snap-in, locate the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on which you want to enable FILESTREAM.</span></span>  
  
4.  <span data-ttu-id="208e4-111">以滑鼠右鍵按一下該執行個體，然後按一下 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="208e4-111">Right-click the instance, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="208e4-112">在 [SQL Server 屬性]  對話方塊中，按一下 [FILESTREAM]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="208e4-112">In the **SQL Server Properties** dialog box, click the **FILESTREAM** tab.</span></span>  
  
6.  <span data-ttu-id="208e4-113">選取 [啟用 FILESTREAM 的 Transact-SQL 存取]  核取方塊。</span><span class="sxs-lookup"><span data-stu-id="208e4-113">Select the **Enable FILESTREAM for Transact-SQL access** check box.</span></span>  
  
7.  <span data-ttu-id="208e4-114">如果您想要從 Windows 讀取和寫入 FILESTREAM 資料，請按一下 [啟用 FILESTREAM 的檔案 I/O 資料流存取]  。</span><span class="sxs-lookup"><span data-stu-id="208e4-114">If you want to read and write FILESTREAM data from Windows, click **Enable FILESTREAM for file I/O streaming access**.</span></span> <span data-ttu-id="208e4-115">在 [Windows 共用名稱]  方塊中，輸入 Windows 共用的名稱。</span><span class="sxs-lookup"><span data-stu-id="208e4-115">Enter the name of the Windows share in the **Windows Share Name** box.</span></span>  
  
8.  <span data-ttu-id="208e4-116">如果遠端用戶端必須存取儲存在這個共用上的 FILESTREAM 資料，請選取 [允許遠端用戶端具有 FILESTREAM 資料的資料流存取權]  。</span><span class="sxs-lookup"><span data-stu-id="208e4-116">If remote clients must access the FILESTREAM data that is stored on this share, select **Allow remote clients to have streaming access to FILESTREAM data**.</span></span>  
  
9. <span data-ttu-id="208e4-117">按一下 [套用]  。</span><span class="sxs-lookup"><span data-stu-id="208e4-117">Click **Apply**.</span></span>  
  
10. <span data-ttu-id="208e4-118">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，按一下 **[新增查詢]** 顯示 [查詢編輯器]。</span><span class="sxs-lookup"><span data-stu-id="208e4-118">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], click **New Query** to display the Query Editor.</span></span>  
  
11. <span data-ttu-id="208e4-119">在 [查詢編輯器] 中，輸入下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼：</span><span class="sxs-lookup"><span data-stu-id="208e4-119">In Query Editor, enter the following [!INCLUDE[tsql](../../includes/tsql-md.md)] code:</span></span>  
  
    ```sql  
    EXEC sp_configure filestream_access_level, 2  
    RECONFIGURE  
    ```  
  
12. <span data-ttu-id="208e4-120">按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="208e4-120">Click **Execute**.</span></span>  
  
13. <span data-ttu-id="208e4-121">重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="208e4-121">Restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  

  
##  <a name="best-practices"></a><a name="best"></a> <span data-ttu-id="208e4-122">最佳作法</span><span class="sxs-lookup"><span data-stu-id="208e4-122">Best Practices</span></span>  
  
###  <a name="physical-configuration-and-maintenance"></a><a name="config"></a><span data-ttu-id="208e4-123">實體設定和維護</span><span class="sxs-lookup"><span data-stu-id="208e4-123">Physical Configuration and Maintenance</span></span>  
 <span data-ttu-id="208e4-124">當您設定 FILESTREAM 儲存體磁碟區時，請考慮下列指導方針：</span><span class="sxs-lookup"><span data-stu-id="208e4-124">When you set up FILESTREAM storage volumes, consider the following guidelines:</span></span>  
  
-   <span data-ttu-id="208e4-125">在 FILESTREAM 電腦系統上關閉簡短檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="208e4-125">Turn off short file names on FILESTREAM computer systems.</span></span> <span data-ttu-id="208e4-126">簡短檔案名稱會花費更長的時間來建立。</span><span class="sxs-lookup"><span data-stu-id="208e4-126">Short file names take significantly longer to create.</span></span> <span data-ttu-id="208e4-127">若要停用簡短檔案名稱，請使用 Windows **fsutil** 公用程式。</span><span class="sxs-lookup"><span data-stu-id="208e4-127">To disable short file names, use the Windows **fsutil** utility.</span></span>  
  
-   <span data-ttu-id="208e4-128">定期重組 FILESTREAM 電腦系統。</span><span class="sxs-lookup"><span data-stu-id="208e4-128">Regularly defragment FILESTREAM computer systems.</span></span>  
  
-   <span data-ttu-id="208e4-129">使用 64-KB NTFS 叢集。</span><span class="sxs-lookup"><span data-stu-id="208e4-129">Use 64-KB NTFS clusters.</span></span> <span data-ttu-id="208e4-130">壓縮的磁碟區必須設定為 4-KB NTFS 叢集。</span><span class="sxs-lookup"><span data-stu-id="208e4-130">Compressed volumes must be set to 4-KB NTFS clusters.</span></span>  
  
-   <span data-ttu-id="208e4-131">停用 FILESTREAM 磁碟區上的索引，並設定 **disablelastaccess** 。若要設定 **disablelastaccess**，請使用 Windows **fsutil** 公用程式。</span><span class="sxs-lookup"><span data-stu-id="208e4-131">Disable indexing on FILESTREAM volumes and set **disablelastaccess** To set **disablelastaccess**, use the Windows **fsutil** utility.</span></span>  
  
-   <span data-ttu-id="208e4-132">在必要的情況下，停用 FILESTREAM 磁碟區的防毒掃描。</span><span class="sxs-lookup"><span data-stu-id="208e4-132">Disable antivirus scanning of FILESTREAM volumes when it is not unnecessary.</span></span> <span data-ttu-id="208e4-133">如果防毒掃描是必要的功能，請避免設定自動刪除違規檔案的原則。</span><span class="sxs-lookup"><span data-stu-id="208e4-133">If antivirus scanning is necessary, avoid setting policies that will automatically delete offending files.</span></span>  
  
-   <span data-ttu-id="208e4-134">針對容錯和應用程式所需的效能設定並微調 RAID 層級。</span><span class="sxs-lookup"><span data-stu-id="208e4-134">Set up and tune the RAID level for fault tolerance and the performance that is required by an application.</span></span>  
  
||||||  
|-|-|-|-|-|  
|<span data-ttu-id="208e4-135">RAID 層級</span><span class="sxs-lookup"><span data-stu-id="208e4-135">RAID level</span></span>|<span data-ttu-id="208e4-136">寫入效能</span><span class="sxs-lookup"><span data-stu-id="208e4-136">Write performance</span></span>|<span data-ttu-id="208e4-137">讀取效能</span><span class="sxs-lookup"><span data-stu-id="208e4-137">Read performance</span></span>|<span data-ttu-id="208e4-138">容錯</span><span class="sxs-lookup"><span data-stu-id="208e4-138">Fault tolerance</span></span>|<span data-ttu-id="208e4-139">備註</span><span class="sxs-lookup"><span data-stu-id="208e4-139">Remarks</span></span>|  
|<span data-ttu-id="208e4-140">RAID 5</span><span class="sxs-lookup"><span data-stu-id="208e4-140">RAID 5</span></span>|<span data-ttu-id="208e4-141">正常</span><span class="sxs-lookup"><span data-stu-id="208e4-141">Normal</span></span>|<span data-ttu-id="208e4-142">正常</span><span class="sxs-lookup"><span data-stu-id="208e4-142">Normal</span></span>|<span data-ttu-id="208e4-143">非常好</span><span class="sxs-lookup"><span data-stu-id="208e4-143">Excellent</span></span>|<span data-ttu-id="208e4-144">效能高於單一磁碟或 JBOD，而低於具有條狀配置的 RAID 0 或 RAID 5。</span><span class="sxs-lookup"><span data-stu-id="208e4-144">Performance is better than one disk or JBOD; and less than RAID 0 or RAID 5 with striping.</span></span>|  
|<span data-ttu-id="208e4-145">RAID 0</span><span class="sxs-lookup"><span data-stu-id="208e4-145">RAID 0</span></span>|<span data-ttu-id="208e4-146">非常好</span><span class="sxs-lookup"><span data-stu-id="208e4-146">Excellent</span></span>|<span data-ttu-id="208e4-147">非常好</span><span class="sxs-lookup"><span data-stu-id="208e4-147">Excellent</span></span>|<span data-ttu-id="208e4-148">None</span><span class="sxs-lookup"><span data-stu-id="208e4-148">None</span></span>||  
|<span data-ttu-id="208e4-149">RAID 5 + 條狀配置</span><span class="sxs-lookup"><span data-stu-id="208e4-149">RAID 5 + stripping</span></span>|<span data-ttu-id="208e4-150">非常好</span><span class="sxs-lookup"><span data-stu-id="208e4-150">Excellent</span></span>|<span data-ttu-id="208e4-151">非常好</span><span class="sxs-lookup"><span data-stu-id="208e4-151">Excellent</span></span>|<span data-ttu-id="208e4-152">非常好</span><span class="sxs-lookup"><span data-stu-id="208e4-152">Excellent</span></span>|<span data-ttu-id="208e4-153">成本最高的選項。</span><span class="sxs-lookup"><span data-stu-id="208e4-153">Most expensive option.</span></span>|  
  

  
###  <a name="physical-database-design"></a><a name="database"></a><span data-ttu-id="208e4-154">實體資料庫設計</span><span class="sxs-lookup"><span data-stu-id="208e4-154">Physical Database Design</span></span>  
 <span data-ttu-id="208e4-155">當您設計 FILESTREAM 資料庫時，請考慮下列指導方針：</span><span class="sxs-lookup"><span data-stu-id="208e4-155">When you design a FILESTREAM database, consider the following guidelines:</span></span>  
  
-   <span data-ttu-id="208e4-156">FILESTREAM 資料行必須伴隨對應的 `uniqueidentifier` ROWGUID 資料行。</span><span class="sxs-lookup"><span data-stu-id="208e4-156">FILESTREAM columns must be accompanied by a corresponding `uniqueidentifier`ROWGUID column.</span></span> <span data-ttu-id="208e4-157">這些種類的資料表也必須附帶唯一的索引。</span><span class="sxs-lookup"><span data-stu-id="208e4-157">These kinds of tables must also be accompanied by a unique index.</span></span> <span data-ttu-id="208e4-158">一般而言，這個索引不是叢集索引。</span><span class="sxs-lookup"><span data-stu-id="208e4-158">Typically this index is not a clustered index.</span></span> <span data-ttu-id="208e4-159">如果資料庫商務邏輯需要叢集索引，您就必須確定儲存在索引中的值不是隨機的。</span><span class="sxs-lookup"><span data-stu-id="208e4-159">If the databases business logic requires a clustered index, you have to make sure that the values stored in the index are not random.</span></span> <span data-ttu-id="208e4-160">隨機值將會導致每次在資料表中加入或移除資料列時，重新排列索引。</span><span class="sxs-lookup"><span data-stu-id="208e4-160">Random values will cause the index to be reordered every time that a row is added or removed from the table.</span></span>  
  
-   <span data-ttu-id="208e4-161">基於效能考量，FILESTREAM 檔案群組和容器應該位於作業系統、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 記錄、tempdb 或分頁檔以外的磁碟區上。</span><span class="sxs-lookup"><span data-stu-id="208e4-161">For performance reasons, FILESTREAM filegroups and containers should reside on volumes other than the operating system, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log, tempdb, or paging file.</span></span>  
  
-   <span data-ttu-id="208e4-162">FILESTREAM 無法直接支援空間管理和原則。</span><span class="sxs-lookup"><span data-stu-id="208e4-162">Space management and policies are not directly supported by FILESTREAM.</span></span> <span data-ttu-id="208e4-163">不過，您可以透過將每個 FILESTREAM 檔案群組指派至個別的磁碟區，並使用磁碟區的管理功能，以間接方式管理空間和套用原則。</span><span class="sxs-lookup"><span data-stu-id="208e4-163">However, you can manage space and apply policies indirectly by assigning each FILESTREAM filegroup to a separate volume and using the volume's management features.</span></span>  
  
  
