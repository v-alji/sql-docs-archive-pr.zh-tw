---
title: 清除合併中繼資料 (複寫 Transact-SQL 程式設計) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- metadata [SQL Server replication]
- sp_mergemetadataretentioncleanup
ms.assetid: 9b88baea-b7c6-4e5d-88f9-93d6a0ff0368
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5a2306db72fd3f0098e18ff058796a5498eafcac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705082"
---
# <a name="clean-up-merge-metadata-replication-transact-sql-programming"></a><span data-ttu-id="a4fce-102">清除合併中繼資料 (複寫 Transact-SQL 程式設計)</span><span class="sxs-lookup"><span data-stu-id="a4fce-102">Clean Up Merge Metadata (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="a4fce-103">合併式複寫中繼資料會由「合併代理程式」依據發行集的保留設定而定期清除。</span><span class="sxs-lookup"><span data-stu-id="a4fce-103">Merge replication metadata is cleaned up periodically by the Merge Agent based on the retention setting for the publication.</span></span> <span data-ttu-id="a4fce-104">這項作業會在 [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql)、 [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql)、 [MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql)、 [MSmerge_past_partition_mappings](/sql/relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql)和 [MSmerge_current_partition_mappings](/sql/relational-databases/system-tables/msmerge-current-partition-mappings) 系統資料表的「發行者」和「訂閱者」端進行。</span><span class="sxs-lookup"><span data-stu-id="a4fce-104">This occurs at the Publisher and Subscriber in the [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql), [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql), [MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql), [MSmerge_past_partition_mappings](/sql/relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql), and [MSmerge_current_partition_mappings](/sql/relational-databases/system-tables/msmerge-current-partition-mappings) system tables.</span></span> <span data-ttu-id="a4fce-105">您也可以使用複寫預存程序，以程式設計方式清除這些資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="a4fce-105">You can also programmatically clean up the data in these tables using replication stored procedures.</span></span>  
  
### <a name="to-manually-clean-up-merge-metadata"></a><span data-ttu-id="a4fce-106">若要手動清除合併中繼資料</span><span class="sxs-lookup"><span data-stu-id="a4fce-106">To manually clean up merge metadata</span></span>  
  
1.  <span data-ttu-id="a4fce-107">在發行集資料庫的「發行者」端，執行 [sp_mergemetadataretentioncleanup](/sql/relational-databases/system-stored-procedures/sp-mergemetadataretentioncleanup-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a4fce-107">At the Publisher on the publication database, execute [sp_mergemetadataretentioncleanup](/sql/relational-databases/system-stored-procedures/sp-mergemetadataretentioncleanup-transact-sql).</span></span>  
  
2.  <span data-ttu-id="a4fce-108"> (選擇性) 請注意在步驟1中從[MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql)、 [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql)和[MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql)系統資料表中移除的資料列數目，分別在 **@num_genhistory_rows** 、 **@num_contents_rows** 和 **@num_tombstone_rows** 輸出參數中傳回。</span><span class="sxs-lookup"><span data-stu-id="a4fce-108">(Optional) Note the number of rows removed in step 1 from the [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql), [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql), and [MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql) system tables, returned respectively in the **@num_genhistory_rows**, **@num_contents_rows**, and **@num_tombstone_rows** output parameters.</span></span>  
  
3.  <span data-ttu-id="a4fce-109">在「訂閱者」端重複步驟 1 和 2，以清除訂閱者資料庫上的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a4fce-109">Repeat steps 1 and 2 at the Subscriber to clean up metadata on the subscription database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4fce-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4fce-110">See Also</span></span>  
 [<span data-ttu-id="a4fce-111">訂閱逾期與停用</span><span class="sxs-lookup"><span data-stu-id="a4fce-111">Subscription Expiration and Deactivation</span></span>](../subscription-expiration-and-deactivation.md)  
  
  
