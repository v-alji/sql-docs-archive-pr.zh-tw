---
title: '[索引和索引鍵] 對話方塊 (Visual Database Tools) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65539
- vdt.ppg.indexeskeys
ms.assetid: 9e4060ba-80c3-468f-bccb-e12e99f672c2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 68c9022f3ea7803f372e7c349e0dc75b1fc56adc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584225"
---
# <a name="indexes-and-keys-dialog-box-visual-database-tools"></a><span data-ttu-id="68eb2-102">索引和索引鍵對話方塊 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="68eb2-102">Indexes and Keys Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="68eb2-103">使用此對話方塊可建立或修改索引、主索引鍵和唯一鍵。</span><span class="sxs-lookup"><span data-stu-id="68eb2-103">Use this dialog box to create or modify indexes, primary keys, and unique keys.</span></span> <span data-ttu-id="68eb2-104">若要存取此對話方塊，請開啟具有索引或索引鍵之資料表的資料表定義，在資料表定義方格上按一下滑鼠右鍵，再按一下 [索引/索引鍵]  。</span><span class="sxs-lookup"><span data-stu-id="68eb2-104">To access this dialog box, open the table definition for the table with the index or key, right-click the table definition grid, and then click **Indexes/Keys**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="68eb2-105">如果資料表是要發佈以進行複寫，則必須使用 Transact-SQL 陳述式 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) 或 SQL Server 管理物件 (SMO) 變更結構描述。</span><span class="sxs-lookup"><span data-stu-id="68eb2-105">If the table is published for replication, you must make schema changes using the Transact-SQL statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="68eb2-106">使用 [資料表設計工具] 或 [資料庫圖表設計工具] 變更結構描述時，會嘗試卸除並重新建立資料表。</span><span class="sxs-lookup"><span data-stu-id="68eb2-106">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="68eb2-107">您無法卸除已發行的物件，因此結構描述變更將會失敗。</span><span class="sxs-lookup"><span data-stu-id="68eb2-107">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
## <a name="options"></a><span data-ttu-id="68eb2-108">選項。</span><span class="sxs-lookup"><span data-stu-id="68eb2-108">Options</span></span>  
 <span data-ttu-id="68eb2-109">**選取的主/唯一索引鍵或索引**</span><span class="sxs-lookup"><span data-stu-id="68eb2-109">**Selected Primary/Unique Key or Index**</span></span>  
 <span data-ttu-id="68eb2-110">列出現有的主索引鍵或唯一鍵和索引。</span><span class="sxs-lookup"><span data-stu-id="68eb2-110">Lists existing primary or unique keys and indexes.</span></span> <span data-ttu-id="68eb2-111">選取一項，以便在右邊方格中顯示其屬性。</span><span class="sxs-lookup"><span data-stu-id="68eb2-111">Select one to show its properties in the grid to the right.</span></span> <span data-ttu-id="68eb2-112">如果清單是空的，表示此資料表沒有任何定義的項目。</span><span class="sxs-lookup"><span data-stu-id="68eb2-112">If the list is empty, none have been defined for the table.</span></span>  
  
 <span data-ttu-id="68eb2-113">**加入**</span><span class="sxs-lookup"><span data-stu-id="68eb2-113">**Add**</span></span>  
 <span data-ttu-id="68eb2-114">建立新的主索引鍵、唯一鍵或索引。</span><span class="sxs-lookup"><span data-stu-id="68eb2-114">Create a new primary or unique key or index.</span></span>  
  
 <span data-ttu-id="68eb2-115">**刪除**</span><span class="sxs-lookup"><span data-stu-id="68eb2-115">**Delete**</span></span>  
 <span data-ttu-id="68eb2-116">刪除在 [選取的主/唯一索引鍵或索引]  清單中選取的索引鍵或索引。</span><span class="sxs-lookup"><span data-stu-id="68eb2-116">Delete the key or index selected in the **Selected Primary/Unique Key or Index** list.</span></span>  
  
 <span data-ttu-id="68eb2-117">**一般類別目錄**</span><span class="sxs-lookup"><span data-stu-id="68eb2-117">**General Category**</span></span>  
 <span data-ttu-id="68eb2-118">展開時會顯示 [資料行]  、[是唯一的]  和 [類型]  屬性。</span><span class="sxs-lookup"><span data-stu-id="68eb2-118">When expanded, shows the properties **Columns**, **Is Unique**, and **Type**.</span></span>  
  
 <span data-ttu-id="68eb2-119">**資料行**</span><span class="sxs-lookup"><span data-stu-id="68eb2-119">**Columns**</span></span>  
 <span data-ttu-id="68eb2-120">列出索引鍵或索引中資料行的選擇排序次序，並且提供存取可在其中定義排序次序的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="68eb2-120">Lists chosen sort orders for the columns in the key or index, and provides access to a dialog box where the sort orders can be defined.</span></span> <span data-ttu-id="68eb2-121">若要顯示對話方塊，請按一下 [資料行]  ，然後按一下屬性欄位右邊出現的省略符號按鈕 (...)。</span><span class="sxs-lookup"><span data-stu-id="68eb2-121">To display the dialog box, click **Columns** and then click the ellipsis button (...) that appears to the right of the property field.</span></span>  
  
 <span data-ttu-id="68eb2-122">**是唯一的**</span><span class="sxs-lookup"><span data-stu-id="68eb2-122">**Is Unique**</span></span>  
 <span data-ttu-id="68eb2-123">指示此索引或索引鍵中輸入的資料是否必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="68eb2-123">Indicates whether data entered into this index or key must be unique.</span></span> <span data-ttu-id="68eb2-124">這不適用於 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="68eb2-124">This is unavailable for XML Indexes.</span></span>  
  
 <span data-ttu-id="68eb2-125">**型別**</span><span class="sxs-lookup"><span data-stu-id="68eb2-125">**Type**</span></span>  
 <span data-ttu-id="68eb2-126">指定在 [選取的主/唯一索引鍵或索引]  清單中選取的項目是唯一的索引鍵、主索引鍵或索引。</span><span class="sxs-lookup"><span data-stu-id="68eb2-126">Specify whether the item selected in the **Selected Primary/Unique Key or Index** list is a unique key, a primary key, or an index.</span></span> <span data-ttu-id="68eb2-127">對於主索引鍵，此欄位是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="68eb2-127">For primary keys this field is read-only.</span></span>  
  
 <span data-ttu-id="68eb2-128">**識別類別目錄**</span><span class="sxs-lookup"><span data-stu-id="68eb2-128">**Identity Category**</span></span>  
 <span data-ttu-id="68eb2-129">展開時會顯示 [名稱]  和 [描述]  的屬性欄位。</span><span class="sxs-lookup"><span data-stu-id="68eb2-129">When expanded, it shows the property fields for **Name** and **Description**.</span></span>  
  
 <span data-ttu-id="68eb2-130">**名稱**</span><span class="sxs-lookup"><span data-stu-id="68eb2-130">**Name**</span></span>  
 <span data-ttu-id="68eb2-131">顯示索引鍵或索引的名稱。</span><span class="sxs-lookup"><span data-stu-id="68eb2-131">Shows the name of the key or index.</span></span> <span data-ttu-id="68eb2-132">在建立新索引時，會根據 [資料表設計師] 作用中視窗的資料表，給予預設的名稱。</span><span class="sxs-lookup"><span data-stu-id="68eb2-132">When a new one is created, it is given a default name based on the table in the active window in Table Designer.</span></span> <span data-ttu-id="68eb2-133">您可以隨時變更名稱。</span><span class="sxs-lookup"><span data-stu-id="68eb2-133">You can change the name at any time.</span></span>  
  
 <span data-ttu-id="68eb2-134">**說明**</span><span class="sxs-lookup"><span data-stu-id="68eb2-134">**Description**</span></span>  
 <span data-ttu-id="68eb2-135">提供描述索引鍵或索引的位置。</span><span class="sxs-lookup"><span data-stu-id="68eb2-135">Provides a place to describe the key or index.</span></span> <span data-ttu-id="68eb2-136">若要寫入更詳細的描述，請按一下 [描述]  ，然後按一下屬性欄位右邊出現的省略符號按鈕 ( **...** )。</span><span class="sxs-lookup"><span data-stu-id="68eb2-136">To write a more detailed description, click **Description** and then click the ellipsis button (**...**) that appears to the right of the property field.</span></span> <span data-ttu-id="68eb2-137">如此便可提供較大的區域以寫入文字。</span><span class="sxs-lookup"><span data-stu-id="68eb2-137">This provides a larger area in which to write text.</span></span>  
  
 <span data-ttu-id="68eb2-138">**資料表設計工具類別目錄**</span><span class="sxs-lookup"><span data-stu-id="68eb2-138">**Table Designer Category**</span></span>  
 <span data-ttu-id="68eb2-139">展開時會顯示 [建立成 CLUSTERED]  的資訊。</span><span class="sxs-lookup"><span data-stu-id="68eb2-139">When expanded, shows information for **Create as Clustered**.</span></span>  
  
 <span data-ttu-id="68eb2-140">**建立成 CLUSTERED**</span><span class="sxs-lookup"><span data-stu-id="68eb2-140">**Create as Clustered**</span></span>  
 <span data-ttu-id="68eb2-141">使索引鍵或索引成為叢集。</span><span class="sxs-lookup"><span data-stu-id="68eb2-141">Make the key or index clustered.</span></span> <span data-ttu-id="68eb2-142">資料表中只能有一個叢集索引。</span><span class="sxs-lookup"><span data-stu-id="68eb2-142">Only one clustered index is allowed on a table.</span></span> <span data-ttu-id="68eb2-143">資料表中的資料會依照叢集索引的順序儲存。</span><span class="sxs-lookup"><span data-stu-id="68eb2-143">Data in the table is stored in the order of the clustered index.</span></span> <span data-ttu-id="68eb2-144">如需詳細資訊，請參閱 [建立叢集索引](../../relational-databases/indexes/indexes.md) 和 [建立非叢集索引](../../relational-databases/indexes/create-nonclustered-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="68eb2-144">For more information, see [Create Clustered Indexes](../../relational-databases/indexes/indexes.md) and [Create Nonclustered Indexes](../../relational-databases/indexes/create-nonclustered-indexes.md).</span></span>  
  
 <span data-ttu-id="68eb2-145">**資料空間規格**</span><span class="sxs-lookup"><span data-stu-id="68eb2-145">**Data Space Specification**</span></span>  
 <span data-ttu-id="68eb2-146">展開時會顯示 [(資料空間類型)]  、[檔案群組或資料分割配置名稱]  和 [資料分割資料行清單]  的資訊。</span><span class="sxs-lookup"><span data-stu-id="68eb2-146">When expanded, shows information for **(Data Space Type)**, **Filegroup or Partition Scheme Name**, and **Partition Column List**.</span></span>  
  
 <span data-ttu-id="68eb2-147">**(資料空間類型)**</span><span class="sxs-lookup"><span data-stu-id="68eb2-147">**(Data Space Type)**</span></span>  
 <span data-ttu-id="68eb2-148">指示此索引或索引鍵是否屬於檔案群組或資料分割配置。</span><span class="sxs-lookup"><span data-stu-id="68eb2-148">Indicates whether this index or key belongs to a file group or partition scheme.</span></span>  
  
 <span data-ttu-id="68eb2-149">**檔案群組或資料分割配置名稱**</span><span class="sxs-lookup"><span data-stu-id="68eb2-149">**Filegroup or Partition Scheme Name**</span></span>  
 <span data-ttu-id="68eb2-150">顯示項目儲存位置的檔案群組名稱或資料分割配置名稱。</span><span class="sxs-lookup"><span data-stu-id="68eb2-150">Shows the name of the file group or partition scheme on which it is stored.</span></span>  
  
 <span data-ttu-id="68eb2-151">**資料分割資料行清單**</span><span class="sxs-lookup"><span data-stu-id="68eb2-151">**Partition Column List**</span></span>  
 <span data-ttu-id="68eb2-152">顯示加入資料分割資料行函數的逗號分隔之資料行清單。</span><span class="sxs-lookup"><span data-stu-id="68eb2-152">Displays a comma-separated list of columns that participate in the partition column function.</span></span> <span data-ttu-id="68eb2-153">如果在 [(資料空間類型)]  欄位中選取檔案群組，則無法使用。</span><span class="sxs-lookup"><span data-stu-id="68eb2-153">Unavailable if Filegroup is selected in the **(Data Space Type)** field.</span></span>  
  
 <span data-ttu-id="68eb2-154">**填滿規格**</span><span class="sxs-lookup"><span data-stu-id="68eb2-154">**Fill Specification**</span></span>  
 <span data-ttu-id="68eb2-155">展開時會顯示 [填滿因數]  \(Fill Factor) 和 [索引頁預留空間]  的資訊。</span><span class="sxs-lookup"><span data-stu-id="68eb2-155">When expanded, shows information for **Fill Factor** and **Pad Index**.</span></span>  
  
 <span data-ttu-id="68eb2-156">**填滿因數**</span><span class="sxs-lookup"><span data-stu-id="68eb2-156">**Fill Factor**</span></span>  
 <span data-ttu-id="68eb2-157">指定系統可以填滿的索引分葉層級頁百分比。</span><span class="sxs-lookup"><span data-stu-id="68eb2-157">Specifies what percentage of the index's leaf-level pages the system can fill.</span></span> <span data-ttu-id="68eb2-158">當一頁填滿時，系統必須分割此頁才能加入新資料，因此會降低效能。</span><span class="sxs-lookup"><span data-stu-id="68eb2-158">Once a page is full, the system must split the pages to add new data, impairing performance.</span></span>  
  
-   <span data-ttu-id="68eb2-159">值 100 表示頁面已填滿。</span><span class="sxs-lookup"><span data-stu-id="68eb2-159">A value of 100 means the pages will be full.</span></span> <span data-ttu-id="68eb2-160">如此便需要最少的儲存空間。</span><span class="sxs-lookup"><span data-stu-id="68eb2-160">This will require the least amount of storage space.</span></span> <span data-ttu-id="68eb2-161">只有在資料未進行任何變更時 (例如，在唯讀的資料表上)，才應該使用此設定。</span><span class="sxs-lookup"><span data-stu-id="68eb2-161">This setting should be used only when there will be no changes to the data, for example, on a read-only table.</span></span>  
  
-   <span data-ttu-id="68eb2-162">較小的值會在資料頁中會留下較多空白空間。</span><span class="sxs-lookup"><span data-stu-id="68eb2-162">A lower value leaves more empty space on the data pages.</span></span> <span data-ttu-id="68eb2-163">如此索引增加時就不需要分割資料頁，但需要較多的存放空間。</span><span class="sxs-lookup"><span data-stu-id="68eb2-163">This reduces the need to split data pages as indexes grow but requires more storage space.</span></span>  
  
 <span data-ttu-id="68eb2-164">**索引頁預留空間**</span><span class="sxs-lookup"><span data-stu-id="68eb2-164">**Pad Index**</span></span>  
 <span data-ttu-id="68eb2-165">指示在資料增加時，此索引中的中繼頁是否提供與 [填滿因素]  中指定的相同空白空間 (填補) 百分比。</span><span class="sxs-lookup"><span data-stu-id="68eb2-165">Indicate whether intermediate pages in this index are provided the same percentage of empty space (padding) specified in **Fill Factor** when they grow.</span></span>  
  
 <span data-ttu-id="68eb2-166">**忽略重複的索引鍵**</span><span class="sxs-lookup"><span data-stu-id="68eb2-166">**Ignore Duplicate Keys**</span></span>  
 <span data-ttu-id="68eb2-167">指定在資料列的索引鍵值等於大量插入作業期間插入的現有索引鍵值時，會發生哪些狀況。</span><span class="sxs-lookup"><span data-stu-id="68eb2-167">Specify what happens when a row is inserted during a bulk insert operation whose key value equals an existing key value.</span></span> <span data-ttu-id="68eb2-168">如果您選擇：</span><span class="sxs-lookup"><span data-stu-id="68eb2-168">If you choose:</span></span>  
  
-   <span data-ttu-id="68eb2-169">[是]  ：[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會發出警告，忽略違規的內送資料列，並嘗試插入其餘的資料列。</span><span class="sxs-lookup"><span data-stu-id="68eb2-169">**Yes** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] issues a warning, ignores the offending incoming row, and tries to insert the remaining rows.</span></span>  
  
-   <span data-ttu-id="68eb2-170">[否]  ：[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會發出錯誤訊息，並復原整個大量插入作業。</span><span class="sxs-lookup"><span data-stu-id="68eb2-170">**No** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] issues an error message and rolls back the entire bulk insert operation.</span></span>  
  
 <span data-ttu-id="68eb2-171">**包含的資料行**</span><span class="sxs-lookup"><span data-stu-id="68eb2-171">**Included Columns**</span></span>  
 <span data-ttu-id="68eb2-172">顯示構成索引鍵之所有資料行的逗號分隔之名稱清單。</span><span class="sxs-lookup"><span data-stu-id="68eb2-172">Displays a comma-separated list of the names of all the columns that constitute the index key.</span></span> <span data-ttu-id="68eb2-173">子索引鍵資料行只能在非叢集索引中指定。</span><span class="sxs-lookup"><span data-stu-id="68eb2-173">Subkey columns can only be specified for nonclustered indexes.</span></span> <span data-ttu-id="68eb2-174">如果是 XML 索引，這個屬性就會隱藏。</span><span class="sxs-lookup"><span data-stu-id="68eb2-174">This property is hidden for XML indexes.</span></span>  
  
 <span data-ttu-id="68eb2-175">**是停用的**</span><span class="sxs-lookup"><span data-stu-id="68eb2-175">**Is Disabled**</span></span>  
 <span data-ttu-id="68eb2-176">指示此索引是否停用。</span><span class="sxs-lookup"><span data-stu-id="68eb2-176">Indicates whether this index is disabled.</span></span> <span data-ttu-id="68eb2-177">這是一個唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="68eb2-177">This is a read-only property.</span></span> <span data-ttu-id="68eb2-178">如果已在 Visual Database Tools 外部停用索引，則這個屬性只能設定為 [是]  。</span><span class="sxs-lookup"><span data-stu-id="68eb2-178">This property is only set to **Yes** if the index has been disabled outside of the Visual Database tools.</span></span>  
  
 <span data-ttu-id="68eb2-179">**是全文檢索索引鍵**</span><span class="sxs-lookup"><span data-stu-id="68eb2-179">**Is Full-Text Key**</span></span>  
 <span data-ttu-id="68eb2-180">指定此索引是否為全文檢索索引鍵。</span><span class="sxs-lookup"><span data-stu-id="68eb2-180">Specify whether this index is a full-text key.</span></span> <span data-ttu-id="68eb2-181">如需有關全文檢索索引鍵的詳細資訊，請參閱《SQL Server 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="68eb2-181">For more information on full-text keys, see SQL Server Books Online.</span></span> <span data-ttu-id="68eb2-182">如果是 XML 索引，這個屬性就會隱藏。</span><span class="sxs-lookup"><span data-stu-id="68eb2-182">This property is hidden for XML indexes.</span></span>  
  
 <span data-ttu-id="68eb2-183">**允許頁面鎖定**</span><span class="sxs-lookup"><span data-stu-id="68eb2-183">**Page Locks Allowed**</span></span>  
 <span data-ttu-id="68eb2-184">指定是否在此索引中允許頁面層級的鎖定。</span><span class="sxs-lookup"><span data-stu-id="68eb2-184">Specify whether page-level locking is allowed on this index.</span></span> <span data-ttu-id="68eb2-185">允許或不允許頁面層級的鎖定會影響資料庫效能。</span><span class="sxs-lookup"><span data-stu-id="68eb2-185">Allowing or disallowing page-level locking affects database performance.</span></span> <span data-ttu-id="68eb2-186">建議設定為 [是]  。</span><span class="sxs-lookup"><span data-stu-id="68eb2-186">The recommended setting is **Yes**.</span></span>  
  
 <span data-ttu-id="68eb2-187">**重新計算統計資料**</span><span class="sxs-lookup"><span data-stu-id="68eb2-187">**Re-compute Statistics**</span></span>  
 <span data-ttu-id="68eb2-188">指定基礎 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 是否會在建立索引時計算新的統計資料。</span><span class="sxs-lookup"><span data-stu-id="68eb2-188">Specify whether the underlying [!INCLUDE[ssDE](../../includes/ssde-md.md)] computes new statistics when the index is created.</span></span> <span data-ttu-id="68eb2-189">重新計算統計資料會減緩索引的建置，但是非常有利於改善查詢效能。</span><span class="sxs-lookup"><span data-stu-id="68eb2-189">Re-computing statistics slows the building of indexes but will very likely improve query performance.</span></span>  
  
 <span data-ttu-id="68eb2-190">**允許資料列鎖定**</span><span class="sxs-lookup"><span data-stu-id="68eb2-190">**Row Locks Allowed**</span></span>  
 <span data-ttu-id="68eb2-191">指定是否在此索引中允許資料列層級的鎖定。</span><span class="sxs-lookup"><span data-stu-id="68eb2-191">Specify whether row-level locking is allowed on this index.</span></span> <span data-ttu-id="68eb2-192">允許或不允許資料列層級的鎖定會影響資料庫效能。</span><span class="sxs-lookup"><span data-stu-id="68eb2-192">Allowing or disallowing row-level locking affects database performance.</span></span> <span data-ttu-id="68eb2-193">建議設定為 [是]  。</span><span class="sxs-lookup"><span data-stu-id="68eb2-193">The recommended setting is **Yes**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68eb2-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68eb2-194">See Also</span></span>  
 <span data-ttu-id="68eb2-195">[Unique 條件約束和 Check 條件約束](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="68eb2-195">[Unique Constraints and Check Constraints](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span></span>  
 [<span data-ttu-id="68eb2-196">主要與外部索引鍵條件約束</span><span class="sxs-lookup"><span data-stu-id="68eb2-196">Primary and Foreign Key Constraints</span></span>](../../relational-databases/tables/primary-and-foreign-key-constraints.md)  
  
  
