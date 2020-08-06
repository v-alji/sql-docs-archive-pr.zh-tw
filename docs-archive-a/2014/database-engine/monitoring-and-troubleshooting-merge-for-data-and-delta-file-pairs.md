---
title: 針對資料檔案和差異檔案組的合併進行監視和疑難排解 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: a8b0bacc-4d2c-42e4-84bf-1a97e0bd385b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5dc57d08f3db1792a9359b3aa79aaceecd03a025
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599670"
---
# <a name="monitoring-and-troubleshooting-merge-for-data-and-delta-file-pairs"></a><span data-ttu-id="3c71a-102">對資料檔案和差異檔案組的合併進行監視和疑難排解</span><span class="sxs-lookup"><span data-stu-id="3c71a-102">Monitoring and Troubleshooting Merge for Data and Delta File Pairs</span></span>
  <span data-ttu-id="3c71a-103">記憶體中 OLTP 會使用合併原則自動合併相鄰資料及差異檔案組。</span><span class="sxs-lookup"><span data-stu-id="3c71a-103">In-Memory OLTP uses a merge policy to merge adjacent data and delta file pairs automatically.</span></span> <span data-ttu-id="3c71a-104">您無法停用合併活動。</span><span class="sxs-lookup"><span data-stu-id="3c71a-104">You cannot disable merge activity.</span></span>  
  
 <span data-ttu-id="3c71a-105">您可以監視資料及差異檔案組，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3c71a-105">You can monitor data and delta file pairs, as follows:</span></span>  
  
-   <span data-ttu-id="3c71a-106">比較記憶體中儲存體與整體儲存體的大小。</span><span class="sxs-lookup"><span data-stu-id="3c71a-106">Compare the size of in-memory storage to overall size of storage.</span></span> <span data-ttu-id="3c71a-107">如果儲存體不成比例地大，可能是未觸發合併。</span><span class="sxs-lookup"><span data-stu-id="3c71a-107">If the storage is dis-proportionately large, then it is likely that merge is not getting triggered.</span></span> <span data-ttu-id="3c71a-108">如需資訊</span><span class="sxs-lookup"><span data-stu-id="3c71a-108">For information</span></span>  
  
-   <span data-ttu-id="3c71a-109">使用 sys.databases 查看資料和差異檔案中的已使用空間[dm_db_xtp_checkpoint_files &#40;transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql)查看是否在應該時不觸發合併。</span><span class="sxs-lookup"><span data-stu-id="3c71a-109">Look at the used space in data and delta files using [sys.dm_db_xtp_checkpoint_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql) to see if merge is not getting triggered when it should.</span></span>  
  
## <a name="performing-a-manual-merge"></a><span data-ttu-id="3c71a-110">執行手動合併</span><span class="sxs-lookup"><span data-stu-id="3c71a-110">Performing a Manual Merge</span></span>  
 <span data-ttu-id="3c71a-111">您可以使用[sys.databases sp_xtp_merge_checkpoint_files &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-merge-checkpoint-files-transact-sql)來執行手動合併。</span><span class="sxs-lookup"><span data-stu-id="3c71a-111">You can use [sys.sp_xtp_merge_checkpoint_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-merge-checkpoint-files-transact-sql) to perform a manual merge.</span></span>  
  
 <span data-ttu-id="3c71a-112">使用以下查詢擷取有關資料及差異檔案的資訊。</span><span class="sxs-lookup"><span data-stu-id="3c71a-112">Use the following query to retrieve information about the data and delta files,</span></span>  
  
```sql  
select checkpoint_file_id, file_type_desc, internal_storage_slot, file_size_in_bytes, file_size_used_in_bytes,   
inserted_row_count, deleted_row_count, lower_bound_tsn, upper_bound_tsn   
from sys.dm_db_xtp_checkpoint_files  
where state = 1  
order by file_type_desc, upper_bound_tsn  
```  
  
 <span data-ttu-id="3c71a-113">假設您發現三個未合併的資料檔案。</span><span class="sxs-lookup"><span data-stu-id="3c71a-113">Assume that you found three data files that have not been merged.</span></span> <span data-ttu-id="3c71a-114">您可以使用第一個資料檔案的 `lower_bound_tsn` 值和最後一個資料檔案的 `upper_bound_tsn` 以發出下列命令：</span><span class="sxs-lookup"><span data-stu-id="3c71a-114">Using the `lower_bound_tsn` value of the first data file and the `upper_bound_tsn` of the last data file, you can issue the following command:</span></span>  
  
```sql  
exec sys.sp_xtp_merge_checkpoint_files 'H_DB',  12345, 67890  
```  
  
 <span data-ttu-id="3c71a-115">假設有三個資料和差異檔案組，每一組各有 15,836 個資料列及 5,279 個已刪除的資料列。</span><span class="sxs-lookup"><span data-stu-id="3c71a-115">Assume that the three data and delta file pairs each had 15,836 rows and 5,279 deleted rows.</span></span> <span data-ttu-id="3c71a-116">合併之後，新資料檔案的資料列數變為 31,872，已刪除的資料列變為 0。</span><span class="sxs-lookup"><span data-stu-id="3c71a-116">After the merge, the new data file has 31,872 rows and 0 deleted rows.</span></span> <span data-ttu-id="3c71a-117">新資料檔案的大小可能遠大於最初所配置的 128MB。</span><span class="sxs-lookup"><span data-stu-id="3c71a-117">The size of the new data file can be much larger than the initially allocated size of 128MB.</span></span> <span data-ttu-id="3c71a-118">這是因為手動合併會覆寫合併原則，並強制合併所要求的檔案。</span><span class="sxs-lookup"><span data-stu-id="3c71a-118">This is because manual merge overrides the merge policy and forces the merge of the requested files.</span></span>  
  
 <span data-ttu-id="3c71a-119">[具有記憶體優化資料表之資料庫中檢查點](https://cloudblogs.microsoft.com/sqlserver/2014/01/23/state-transition-of-checkpoint-files-in-databases-with-memory-optimized-tables/)檔案的 Blog 狀態轉換說明從開始到垃圾收集的資料和差異檔案組的狀態轉換。</span><span class="sxs-lookup"><span data-stu-id="3c71a-119">The blog [State Transition of Checkpoint Files in Databases with Memory-Optimized Tables](https://cloudblogs.microsoft.com/sqlserver/2014/01/23/state-transition-of-checkpoint-files-in-databases-with-memory-optimized-tables/) describes state transition of data and delta file pairs from inception to garbage collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c71a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c71a-120">See Also</span></span>  
 [<span data-ttu-id="3c71a-121">建立及管理記憶體最佳化物件的儲存體</span><span class="sxs-lookup"><span data-stu-id="3c71a-121">Creating and Managing Storage for Memory-Optimized Objects</span></span>](../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md)  
  
