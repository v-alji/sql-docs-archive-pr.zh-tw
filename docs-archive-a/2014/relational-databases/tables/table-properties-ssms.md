---
title: 資料表屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- sql12.swb.tableproperties.storage.f1
- sql12.SWB.SELECTCOLUMNS.F1
- sql12.swb.tableproperties.filetable.f1
- sql12.swb.tableproperties.general.f1
- sql12.swb.tableproperties.changetracking.f1
ms.assetid: ad8a2fd4-f092-4c0f-be85-54ce8b9d725a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 037e56649d3473e3fe09b9533bcc96b4729870d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596569"
---
# <a name="table-properties"></a><span data-ttu-id="5509c-102">資料表屬性</span><span class="sxs-lookup"><span data-stu-id="5509c-102">Table Properties</span></span>
  <span data-ttu-id="5509c-103">本主題描述在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]之 [資料表屬性] 對話方塊中顯示的資料表屬性。</span><span class="sxs-lookup"><span data-stu-id="5509c-103">This topic describes the table properties that are displayed in the Table Properties dialog box in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="5509c-104">如需如何顯示這些屬性的詳細資訊，請參閱 [檢視資料表定義](view-the-table-definition.md)。</span><span class="sxs-lookup"><span data-stu-id="5509c-104">For more information about how to display these properties, see [View the Table Definition](view-the-table-definition.md).</span></span>  
  
 <span data-ttu-id="5509c-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="5509c-105">**In This Topic**</span></span>  
  
1.  [<span data-ttu-id="5509c-106">一般頁面</span><span class="sxs-lookup"><span data-stu-id="5509c-106">General Page</span></span>](#GeneralPage)  
  
2.  [<span data-ttu-id="5509c-107">變更追蹤頁面</span><span class="sxs-lookup"><span data-stu-id="5509c-107">Change Tracking Page</span></span>](#ChangeTracking)  
  
3.  [<span data-ttu-id="5509c-108">FileTable 頁面</span><span class="sxs-lookup"><span data-stu-id="5509c-108">File Table Page</span></span>](#FileTable)  
  
4.  [<span data-ttu-id="5509c-109">儲存體頁面</span><span class="sxs-lookup"><span data-stu-id="5509c-109">Storage Page</span></span>](#Storage)  
  
##  <a name="general-page"></a><a name="GeneralPage"></a> <span data-ttu-id="5509c-110">一般頁面</span><span class="sxs-lookup"><span data-stu-id="5509c-110">General Page</span></span>  
 <span data-ttu-id="5509c-111">**Database**</span><span class="sxs-lookup"><span data-stu-id="5509c-111">**Database**</span></span>  
 <span data-ttu-id="5509c-112">包含此資料表之資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="5509c-112">The name of the database containing this table.</span></span>  
  
 <span data-ttu-id="5509c-113">**Server**</span><span class="sxs-lookup"><span data-stu-id="5509c-113">**Server**</span></span>  
 <span data-ttu-id="5509c-114">目前伺服器執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="5509c-114">The name of the current server instance.</span></span>  
  
 <span data-ttu-id="5509c-115">**使用者**</span><span class="sxs-lookup"><span data-stu-id="5509c-115">**User**</span></span>  
 <span data-ttu-id="5509c-116">這個連接之使用者的名稱。</span><span class="sxs-lookup"><span data-stu-id="5509c-116">The name of the user of this connection.</span></span>  
  
 <span data-ttu-id="5509c-117">**建立日期**</span><span class="sxs-lookup"><span data-stu-id="5509c-117">**Created Date**</span></span>  
 <span data-ttu-id="5509c-118">資料表的建立日期和時間。</span><span class="sxs-lookup"><span data-stu-id="5509c-118">The date and time that the table was created.</span></span>  
  
 <span data-ttu-id="5509c-119">**名稱**</span><span class="sxs-lookup"><span data-stu-id="5509c-119">**Name**</span></span>  
 <span data-ttu-id="5509c-120">資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="5509c-120">The name of the table.</span></span>  
  
 <span data-ttu-id="5509c-121">**結構描述**</span><span class="sxs-lookup"><span data-stu-id="5509c-121">**Schema**</span></span>  
 <span data-ttu-id="5509c-122">擁有資料表的結構描述。</span><span class="sxs-lookup"><span data-stu-id="5509c-122">The schema that owns the table.</span></span>  
  
 <span data-ttu-id="5509c-123">**系統物件**</span><span class="sxs-lookup"><span data-stu-id="5509c-123">**System object**</span></span>  
 <span data-ttu-id="5509c-124">指出此資料表是系統資料表，由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用來包含內部資訊。</span><span class="sxs-lookup"><span data-stu-id="5509c-124">Indicates this table is a system table, used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to contain internal information.</span></span> <span data-ttu-id="5509c-125">使用者不應該直接變更或參考系統資料表。</span><span class="sxs-lookup"><span data-stu-id="5509c-125">Users should not directly change or reference system tables.</span></span>  
  
 <span data-ttu-id="5509c-126">**ANSI NULLS**</span><span class="sxs-lookup"><span data-stu-id="5509c-126">**ANSI NULLs**</span></span>  
 <span data-ttu-id="5509c-127">指出物件是否使用設定為 ON 的 ANSI NULLS 選項建立。</span><span class="sxs-lookup"><span data-stu-id="5509c-127">Indicates if the object was created with the ANSI NULLs option set to ON.</span></span> <span data-ttu-id="5509c-128">如需詳細資訊，請參閱 [SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5509c-128">For more information, see [SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql)</span></span>  
  
 <span data-ttu-id="5509c-129">**引號識別碼**</span><span class="sxs-lookup"><span data-stu-id="5509c-129">**Quoted identifier**</span></span>  
 <span data-ttu-id="5509c-130">指出物件是否使用設定為 ON 的引號識別碼選項建立。</span><span class="sxs-lookup"><span data-stu-id="5509c-130">Indicates if the object was created with the quoted identifier option set to ON.</span></span> <span data-ttu-id="5509c-131">如需詳細資訊，請參閱 [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5509c-131">For more information, see [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql)</span></span>  
  
 <span data-ttu-id="5509c-132">**鎖定擴大**</span><span class="sxs-lookup"><span data-stu-id="5509c-132">**Lock Escalation**</span></span>  
 <span data-ttu-id="5509c-133">表示資料表的鎖定擴大資料粒度。</span><span class="sxs-lookup"><span data-stu-id="5509c-133">Indicates the lock escalation granularity of the table.</span></span> <span data-ttu-id="5509c-134">如需有關 Database Engine 中鎖定的詳細資訊，請參閱 [SQL Server 交易鎖定與資料列版本設定指南](https://msdn.microsoft.com/library/jj856598.aspx)。</span><span class="sxs-lookup"><span data-stu-id="5509c-134">For more information about locking in the Database Engine, see [SQL Server Transaction Locking and Row Versioning Guide](https://msdn.microsoft.com/library/jj856598.aspx).</span></span> <span data-ttu-id="5509c-135">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="5509c-135">Possible values are:</span></span>  
  
 <span data-ttu-id="5509c-136">AUTO</span><span class="sxs-lookup"><span data-stu-id="5509c-136">AUTO</span></span>  
 <span data-ttu-id="5509c-137">此選項允許 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 選取適用於資料表結構描述的鎖定擴大資料粒度。</span><span class="sxs-lookup"><span data-stu-id="5509c-137">This option allows the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] to select the lock escalation granularity that is appropriate for the table schema.</span></span>  
  
-   <span data-ttu-id="5509c-138">如果資料表為資料分割，則允許鎖定擴大使用堆積或 B 型樹狀結構 (HoBT) 資料粒度。</span><span class="sxs-lookup"><span data-stu-id="5509c-138">If the table is partitioned, lock escalation will be allowed to the heap or B-tree (HoBT) granularity.</span></span> <span data-ttu-id="5509c-139">鎖定在擴大為 HoBT 層級後，就無法再擴大為 TABLE 資料粒度。</span><span class="sxs-lookup"><span data-stu-id="5509c-139">After the lock is escalated to the HoBT level, the lock will not be escalated later to TABLE granularity.</span></span>  
  
-   <span data-ttu-id="5509c-140">如果資料表不是分割區，則會對 TABLE 資料粒度執行鎖定擴大。</span><span class="sxs-lookup"><span data-stu-id="5509c-140">If the table is not partitioned, the lock escalation will be done to the TABLE granularity.</span></span>  
  
 <span data-ttu-id="5509c-141">TABLE</span><span class="sxs-lookup"><span data-stu-id="5509c-141">TABLE</span></span>  
 <span data-ttu-id="5509c-142">不論資料表是否為資料分割，鎖定擴大將在資料表層級的資料粒度完成。</span><span class="sxs-lookup"><span data-stu-id="5509c-142">Lock escalation will be done at table-level granularity regardless of whether the table is partitioned or not partitioned.</span></span> <span data-ttu-id="5509c-143">TABLE 為預設值。</span><span class="sxs-lookup"><span data-stu-id="5509c-143">TABLE is the default value.</span></span>  
  
 <span data-ttu-id="5509c-144">DISABLE</span><span class="sxs-lookup"><span data-stu-id="5509c-144">DISABLE</span></span>  
 <span data-ttu-id="5509c-145">在大多數情況下都避免使用鎖定擴大，</span><span class="sxs-lookup"><span data-stu-id="5509c-145">Prevents lock escalation in most cases.</span></span> <span data-ttu-id="5509c-146">但並非完全不允許資料表層級的鎖定。</span><span class="sxs-lookup"><span data-stu-id="5509c-146">Table-level locks are not completely disallowed.</span></span> <span data-ttu-id="5509c-147">例如，當您在可序列化隔離層級下掃描沒有任何叢集索引的資料表時， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 必須採用資料表鎖定以保護資料的完整性。</span><span class="sxs-lookup"><span data-stu-id="5509c-147">For example, when you are scanning a table that has no clustered index under the serializable isolation level, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] must take a table lock to protect data integrity.</span></span>  
  
 <span data-ttu-id="5509c-148">**資料表有複寫**</span><span class="sxs-lookup"><span data-stu-id="5509c-148">**Table is replicated**</span></span>  
 <span data-ttu-id="5509c-149">指出何時使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 複寫，將資料表複寫到另一個資料庫。</span><span class="sxs-lookup"><span data-stu-id="5509c-149">Indicates when the table is replicated to another database using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication.</span></span> <span data-ttu-id="5509c-150">可能的值為 `True` 或 `False`。</span><span class="sxs-lookup"><span data-stu-id="5509c-150">Possible values are `True` or `False`.</span></span>  
  
##  <a name="change-tracking-page"></a><a name="ChangeTracking"></a><span data-ttu-id="5509c-151">變更追蹤頁面</span><span class="sxs-lookup"><span data-stu-id="5509c-151">Change Tracking Page</span></span>  
 <span data-ttu-id="5509c-152">**變更追蹤**</span><span class="sxs-lookup"><span data-stu-id="5509c-152">**Change Tracking**</span></span>  
 <span data-ttu-id="5509c-153">指出資料表是否啟用變更追蹤。</span><span class="sxs-lookup"><span data-stu-id="5509c-153">Indicates whether change tracking is enabled for the table.</span></span> <span data-ttu-id="5509c-154">預設值是 `False`。</span><span class="sxs-lookup"><span data-stu-id="5509c-154">The default value is `False`.</span></span>  
  
 <span data-ttu-id="5509c-155">只有當資料庫啟用了變更追蹤時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="5509c-155">This option is available only when change tracking is enabled for the database.</span></span>  
  
 <span data-ttu-id="5509c-156">若要啟用變更追蹤，資料表必須具有主索引鍵，而您也必須擁有修改資料表的權限。</span><span class="sxs-lookup"><span data-stu-id="5509c-156">To enable change tracking, the table must have a primary key, and you must have permission to modify the table.</span></span> <span data-ttu-id="5509c-157">您可以使用 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql)來設定變更追蹤。</span><span class="sxs-lookup"><span data-stu-id="5509c-157">You can configure change tracking by using [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
 <span data-ttu-id="5509c-158">**追蹤資料行已更新**</span><span class="sxs-lookup"><span data-stu-id="5509c-158">**Track Columns Updated**</span></span>  
 <span data-ttu-id="5509c-159">指出 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 是否追蹤哪些資料行已更新。</span><span class="sxs-lookup"><span data-stu-id="5509c-159">Indicates whether the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] tracks which columns were updated.</span></span>  
  
 <span data-ttu-id="5509c-160">如需變更追蹤的詳細資訊，請參閱[關於變更追蹤 &#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="5509c-160">For more information about Change Tracking, see [About Change Tracking &#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md).</span></span>  
  
##  <a name="filetable-page"></a><a name="FileTable"></a><span data-ttu-id="5509c-161">FileTable 頁面</span><span class="sxs-lookup"><span data-stu-id="5509c-161">FileTable Page</span></span>  
 <span data-ttu-id="5509c-162">顯示與 FileTable 相關之資料表的屬性。</span><span class="sxs-lookup"><span data-stu-id="5509c-162">Displays properties of the table related to FileTables.</span></span> <span data-ttu-id="5509c-163">如需詳細資訊，請參閱 [FileTables &#40;SQL Server&#41;](../blob/filetables-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="5509c-163">For more information, see [FileTables &#40;SQL Server&#41;](../blob/filetables-sql-server.md).</span></span>  
  
 <span data-ttu-id="5509c-164">**FileTable 名稱資料行定序**</span><span class="sxs-lookup"><span data-stu-id="5509c-164">**FileTable name column collation**</span></span>  
 <span data-ttu-id="5509c-165">要套用至 FileTable 中 **Name** 資料行的定序。</span><span class="sxs-lookup"><span data-stu-id="5509c-165">The collation that is applied to the **Name** column in a FileTable.</span></span> <span data-ttu-id="5509c-166">**Name** 資料行包含檔案和目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="5509c-166">The **Name** column contains file and directory names.</span></span>  
  
 <span data-ttu-id="5509c-167">**FileTable 目錄名稱**</span><span class="sxs-lookup"><span data-stu-id="5509c-167">**FileTable directory name**</span></span>  
 <span data-ttu-id="5509c-168">FileTable 的根資料夾。</span><span class="sxs-lookup"><span data-stu-id="5509c-168">The root folder for the FileTable.</span></span>  
  
 <span data-ttu-id="5509c-169">**已啟用 FileTable 命名空間**</span><span class="sxs-lookup"><span data-stu-id="5509c-169">**FileTable namespace enabled**</span></span>  
 <span data-ttu-id="5509c-170">當為 `True` 時，這個值表示資料表為 FileTable。</span><span class="sxs-lookup"><span data-stu-id="5509c-170">When `True`, this value indicates that the table is a FileTable.</span></span> <span data-ttu-id="5509c-171">如果您將這個值變更為 `False`，您會將 FileTable 變更為一般使用者資料表。</span><span class="sxs-lookup"><span data-stu-id="5509c-171">If you change this value to `False`, you are changing the FileTable to an ordinary user table.</span></span> <span data-ttu-id="5509c-172">如果您之後想要將資料表變更回 FileTable，此資料表必須先通過 FileTable 一致性檢查才會轉換成功。</span><span class="sxs-lookup"><span data-stu-id="5509c-172">If you later want to change the table back to a FileTable, the table will have to pass a FileTable consistency check before the conversion succeeds.</span></span>  
  
##  <a name="storage-page"></a><a name="Storage"></a><span data-ttu-id="5509c-173">儲存體頁面</span><span class="sxs-lookup"><span data-stu-id="5509c-173">Storage Page</span></span>  
 <span data-ttu-id="5509c-174">顯示選取之資料表的儲存體相關屬性。</span><span class="sxs-lookup"><span data-stu-id="5509c-174">Displays the storage related properties of the selected table.</span></span>  
  
### <a name="compression"></a><span data-ttu-id="5509c-175">壓縮</span><span class="sxs-lookup"><span data-stu-id="5509c-175">Compression</span></span>  
 <span data-ttu-id="5509c-176">**壓縮類型**</span><span class="sxs-lookup"><span data-stu-id="5509c-176">**Compression type**</span></span>  
 <span data-ttu-id="5509c-177">資料表的壓縮類型。</span><span class="sxs-lookup"><span data-stu-id="5509c-177">The compression type of the table.</span></span> <span data-ttu-id="5509c-178">此屬性只適用於沒有資料分割的資料表。</span><span class="sxs-lookup"><span data-stu-id="5509c-178">This property is only available for tables that are not partitioned.</span></span> <span data-ttu-id="5509c-179">如需詳細資訊，請參閱 [Data Compression](../data-compression/data-compression.md)。</span><span class="sxs-lookup"><span data-stu-id="5509c-179">For more information, see [Data Compression](../data-compression/data-compression.md).</span></span>  
  
 <span data-ttu-id="5509c-180">**使用頁面壓縮的資料分割**</span><span class="sxs-lookup"><span data-stu-id="5509c-180">**Partitions using page compression**</span></span>  
 <span data-ttu-id="5509c-181">使用頁面壓縮的資料分割數。</span><span class="sxs-lookup"><span data-stu-id="5509c-181">The partition numbers that are using page compression.</span></span> <span data-ttu-id="5509c-182">此屬性只適用於資料分割的資料表。</span><span class="sxs-lookup"><span data-stu-id="5509c-182">This property is only available for partitioned tables.</span></span>  
  
 <span data-ttu-id="5509c-183">**未壓縮的資料分割**</span><span class="sxs-lookup"><span data-stu-id="5509c-183">**Partitions not compressed**</span></span>  
 <span data-ttu-id="5509c-184">未壓縮的資料分割數。</span><span class="sxs-lookup"><span data-stu-id="5509c-184">The partition numbers that are not compressed.</span></span> <span data-ttu-id="5509c-185">此屬性只適用於資料分割的資料表。</span><span class="sxs-lookup"><span data-stu-id="5509c-185">This property is only available for partitioned tables.</span></span>  
  
 <span data-ttu-id="5509c-186">**使用資料列壓縮的資料分割**</span><span class="sxs-lookup"><span data-stu-id="5509c-186">**Partitions using row compression**</span></span>  
 <span data-ttu-id="5509c-187">使用資料列壓縮的資料分割數。</span><span class="sxs-lookup"><span data-stu-id="5509c-187">The partition numbers that are using row compression.</span></span> <span data-ttu-id="5509c-188">此屬性只適用於資料分割的資料表。</span><span class="sxs-lookup"><span data-stu-id="5509c-188">This property is only available for partitioned tables.</span></span>  
  
### <a name="filegroup"></a><span data-ttu-id="5509c-189">檔案群組</span><span class="sxs-lookup"><span data-stu-id="5509c-189">Filegroup</span></span>  
 <span data-ttu-id="5509c-190">**文字檔案群組**</span><span class="sxs-lookup"><span data-stu-id="5509c-190">**Text filegroup**</span></span>  
 <span data-ttu-id="5509c-191">包含資料表文字資料之檔案群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="5509c-191">The name of the filegroup that contains the text data for the table.</span></span>  
  
 <span data-ttu-id="5509c-192">**檔案群組**</span><span class="sxs-lookup"><span data-stu-id="5509c-192">**Filegroup**</span></span>  
 <span data-ttu-id="5509c-193">資料表所在的檔案群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="5509c-193">The name of the filegroup that contains the table.</span></span>  
  
 <span data-ttu-id="5509c-194">**資料表已經分割**</span><span class="sxs-lookup"><span data-stu-id="5509c-194">**Table is partitioned**</span></span>  
 <span data-ttu-id="5509c-195">可能的值是 `True` 和 `False`。</span><span class="sxs-lookup"><span data-stu-id="5509c-195">Possible values are `True` and `False`.</span></span>  
  
 <span data-ttu-id="5509c-196">**檔案資料流檔案群組**</span><span class="sxs-lookup"><span data-stu-id="5509c-196">**Filestream filegroup**</span></span>  
 <span data-ttu-id="5509c-197">如果資料表擁有具有 FILESTREAM 屬性的 `varbinary(max)` 資料行，則指定 FILESTREAM 資料檔案群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="5509c-197">Specify the name of the FILESTREAM data filegroup if the table has a `varbinary(max)` column that has the FILESTREAM attribute.</span></span> <span data-ttu-id="5509c-198">預設值為預設的 FILESTREAM 資料檔案群組。</span><span class="sxs-lookup"><span data-stu-id="5509c-198">The default value is the default FILESTREAM data filegroup.</span></span>  
  
 <span data-ttu-id="5509c-199">如果資料表不包含 FILESTREAM 資料，則此欄位空白。</span><span class="sxs-lookup"><span data-stu-id="5509c-199">If the table does not contain FILESTREAM data, the field is blank.</span></span>  
  
### <a name="general"></a><span data-ttu-id="5509c-200">一般</span><span class="sxs-lookup"><span data-stu-id="5509c-200">General</span></span>  
 <span data-ttu-id="5509c-201">**Vardecimal 儲存格式已啟用**</span><span class="sxs-lookup"><span data-stu-id="5509c-201">**Vardecimal storage format is enabled**</span></span>  
 <span data-ttu-id="5509c-202">當為時 `True` ，這個唯讀值表示 `decimal` 和 `numeric` 資料類型會使用 vardecimal 儲存格式來儲存。</span><span class="sxs-lookup"><span data-stu-id="5509c-202">When `True`, this read-only value indicates that `decimal` and `numeric` data types are stored by using the vardecimal storage format.</span></span> <span data-ttu-id="5509c-203">若要變更此選項，請使用 `vardecimal storage format` [sp_tableoption](/sql/relational-databases/system-stored-procedures/sp-tableoption-transact-sql)的選項。</span><span class="sxs-lookup"><span data-stu-id="5509c-203">To change this option, use the `vardecimal storage format` option of [sp_tableoption](/sql/relational-databases/system-stored-procedures/sp-tableoption-transact-sql).</span></span> <span data-ttu-id="5509c-204">Vardecimal 儲存格式已被取代。</span><span class="sxs-lookup"><span data-stu-id="5509c-204">Vardecimal storage format is deprecated.</span></span> <span data-ttu-id="5509c-205">請改用資料列壓縮。</span><span class="sxs-lookup"><span data-stu-id="5509c-205">Use ROW compression instead.</span></span>  
  
 <span data-ttu-id="5509c-206">**索引空間**</span><span class="sxs-lookup"><span data-stu-id="5509c-206">**Index space**</span></span>  
 <span data-ttu-id="5509c-207">顯示索引在資料表中所佔的空間量 (以 MB 表示)。</span><span class="sxs-lookup"><span data-stu-id="5509c-207">The amount of space in megabytes that the indexes occupy in the table.</span></span> <span data-ttu-id="5509c-208">這個值不包括資料表的 XML 索引空間使用量。</span><span class="sxs-lookup"><span data-stu-id="5509c-208">This value does not include XML index space usage for the table.</span></span> <span data-ttu-id="5509c-209">如果 XML 索引屬於此資料表，請改用 [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="5509c-209">If XML indexes belong to the table, use [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) instead.</span></span>  
  
 <span data-ttu-id="5509c-210">**資料列計數**</span><span class="sxs-lookup"><span data-stu-id="5509c-210">**Row count**</span></span>  
 <span data-ttu-id="5509c-211">表格中的列數。</span><span class="sxs-lookup"><span data-stu-id="5509c-211">The number of rows in the table.</span></span>  
  
 <span data-ttu-id="5509c-212">**資料空間**</span><span class="sxs-lookup"><span data-stu-id="5509c-212">**Data space**</span></span>  
 <span data-ttu-id="5509c-213">資料在資料表中所佔的空間量 (以 MB 表示)。</span><span class="sxs-lookup"><span data-stu-id="5509c-213">The amount of space in megabytes that the data occupies in the table.</span></span>  
  
### <a name="partitioning"></a><span data-ttu-id="5509c-214">資料分割</span><span class="sxs-lookup"><span data-stu-id="5509c-214">Partitioning</span></span>  
 <span data-ttu-id="5509c-215">只有在資料表為資料分割時，才能使用此區段。</span><span class="sxs-lookup"><span data-stu-id="5509c-215">This section is only available if the table is partitioned.</span></span> <span data-ttu-id="5509c-216">如需詳細資訊，請參閱＜ [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md)＞。</span><span class="sxs-lookup"><span data-stu-id="5509c-216">For more information, see [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md).</span></span>  
  
 <span data-ttu-id="5509c-217">**資料分割資料行**</span><span class="sxs-lookup"><span data-stu-id="5509c-217">**Partition column**</span></span>  
 <span data-ttu-id="5509c-218">用以分割資料表之資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="5509c-218">The name of the column on which the table is partitioned.</span></span>  
  
 <span data-ttu-id="5509c-219">**分割區配置**</span><span class="sxs-lookup"><span data-stu-id="5509c-219">**Partition scheme**</span></span>  
 <span data-ttu-id="5509c-220">如果資料表為資料分割，則為資料分割配置的名稱。</span><span class="sxs-lookup"><span data-stu-id="5509c-220">Name of the partition scheme if the table is partitioned.</span></span> <span data-ttu-id="5509c-221">如果資料表不是資料分割，則此欄位空白。</span><span class="sxs-lookup"><span data-stu-id="5509c-221">If the table is not partitioned, the field is blank.</span></span>  
  
 <span data-ttu-id="5509c-222">**資料分割數目**</span><span class="sxs-lookup"><span data-stu-id="5509c-222">**Number of partitions**</span></span>  
 <span data-ttu-id="5509c-223">資料表中的資料分割數。</span><span class="sxs-lookup"><span data-stu-id="5509c-223">The number of partitions in the table.</span></span>  
  
 <span data-ttu-id="5509c-224">**FILESTREAM 資料分割配置**</span><span class="sxs-lookup"><span data-stu-id="5509c-224">**FILESTREAM partition scheme**</span></span>  
 <span data-ttu-id="5509c-225">如果資料表為資料分割，則為 FILESTREAM 資料分割配置的名稱。</span><span class="sxs-lookup"><span data-stu-id="5509c-225">The name of the FILESTREAM partition scheme if the table is partitioned.</span></span> <span data-ttu-id="5509c-226">如果資料表不是資料分割，則此欄位空白。</span><span class="sxs-lookup"><span data-stu-id="5509c-226">If the table is not partitioned, the field is blank.</span></span>  
  
 <span data-ttu-id="5509c-227">FILESTREAM 資料分割配置必須對稱於在 **[資料分割配置]** 選項中所指定的配置。</span><span class="sxs-lookup"><span data-stu-id="5509c-227">The FILESTREAM partition scheme must be symmetric to the scheme that is specified in the **Partition scheme** option.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5509c-228">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5509c-228">See Also</span></span>  
 <span data-ttu-id="5509c-229">[查看資料表定義](view-the-table-definition.md) </span><span class="sxs-lookup"><span data-stu-id="5509c-229">[View the Table Definition](view-the-table-definition.md) </span></span>  
 [<span data-ttu-id="5509c-230">修改資料行 &#40;Database Engine&#41;</span><span class="sxs-lookup"><span data-stu-id="5509c-230">Modify Columns &#40;Database Engine&#41;</span></span>](../tables/modify-columns-database-engine.md)  
  
  
