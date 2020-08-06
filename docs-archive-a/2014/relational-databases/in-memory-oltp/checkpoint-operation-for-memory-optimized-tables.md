---
title: 記憶體最佳化資料表的檢查點作業 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 47975bd5-373f-43cd-946a-da8e8088b610
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 07560ea0bf147198fb759f6769ae1c6d5c68a71e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708374"
---
# <a name="checkpoint-operation-for-memory-optimized-tables"></a><span data-ttu-id="382f2-102">記憶體最佳化的資料表的檢查點作業</span><span class="sxs-lookup"><span data-stu-id="382f2-102">Checkpoint Operation for Memory-Optimized Tables</span></span>
  <span data-ttu-id="382f2-103">資料與差異檔案中的記憶體最佳化資料之檢查點需要定期出現，以推進交易記錄的使用中部分。</span><span class="sxs-lookup"><span data-stu-id="382f2-103">A checkpoint needs to occur periodically for memory-optimized data in data and delta files to advance the active part of transaction log.</span></span> <span data-ttu-id="382f2-104">檢查點可讓記憶體最佳化的資料表還原或復原到上一個成功的檢查點，然後套用交易記錄的使用中部分，更新記憶體最佳化的資料表以完成還原。</span><span class="sxs-lookup"><span data-stu-id="382f2-104">The checkpoint allows memory-optimized tables to restore or recover to the last successful checkpoint and then the active portion of transaction log is applied to update the memory-optimized tables to complete the recovery.</span></span> <span data-ttu-id="382f2-105">以磁碟為基礎的資料表和記憶體最佳化資料表的檢查點作業是不同的作業。</span><span class="sxs-lookup"><span data-stu-id="382f2-105">The checkpoint operation for disk-based tables and memory-optimized tables are distinct operations.</span></span> <span data-ttu-id="382f2-106">下列內容描述以磁碟為基礎的資料表和記憶體最佳化資料表之間不同的狀況和檢查點行為：</span><span class="sxs-lookup"><span data-stu-id="382f2-106">The following describes different scenarios and the checkpoint behavior for disk-based and memory-optimized tables:</span></span>  
  
## <a name="manual-checkpoint"></a><span data-ttu-id="382f2-107">手動檢查點</span><span class="sxs-lookup"><span data-stu-id="382f2-107">Manual Checkpoint</span></span>  
 <span data-ttu-id="382f2-108">當您發出手動檢查點時，它會關閉以磁碟為基礎的資料表和記憶體最佳化資料表的檢查點。</span><span class="sxs-lookup"><span data-stu-id="382f2-108">When you issue a manual checkpoint, it closes the checkpoint for both disk-based and memory-optimized tables.</span></span> <span data-ttu-id="382f2-109">使用中的資料檔案會關閉，即使它可能只有部分填滿。</span><span class="sxs-lookup"><span data-stu-id="382f2-109">The active data file is closed even though it may be partially filled.</span></span>  
  
## <a name="automatic-checkpoint"></a><span data-ttu-id="382f2-110">自動檢查點</span><span class="sxs-lookup"><span data-stu-id="382f2-110">Automatic Checkpoint</span></span>  
 <span data-ttu-id="382f2-111">自動檢查點對於磁碟資料表和記憶體最佳化資料表的實作不同，因為兩種資料表保存資料的方式不同。</span><span class="sxs-lookup"><span data-stu-id="382f2-111">Automatic checkpoint is implemented differently for disk-based and memory-optimized tables because of the different ways the data is persisted.</span></span>  
  
 <span data-ttu-id="382f2-112">對於磁碟資料表，自動檢查點是根據復原間隔組態選項取得 (如需詳細資訊，請參閱[變更資料庫的目標復原時間 &#40;SQL Server&#41;](../logs/change-the-target-recovery-time-of-a-database-sql-server.md))。</span><span class="sxs-lookup"><span data-stu-id="382f2-112">For disk-based tables, an automatic checkpoint is taken based on the recovery interval configuration option (for more information, see [Change the Target Recovery Time of a Database &#40;SQL Server&#41;](../logs/change-the-target-recovery-time-of-a-database-sql-server.md)).</span></span>  
  
 <span data-ttu-id="382f2-113">在記憶體優化資料表中，當交易記錄檔自最後一個檢查點之後變得大於 512 MB 時，就會執行自動檢查點。</span><span class="sxs-lookup"><span data-stu-id="382f2-113">For memory-optimized tables, an automatic checkpoint is taken when transaction log file becomes bigger than 512 MB since the last checkpoint.</span></span> <span data-ttu-id="382f2-114">512 MB 包含磁片型和記憶體優化資料表的交易記錄檔記錄。</span><span class="sxs-lookup"><span data-stu-id="382f2-114">512 MB includes transaction log records for both disk-based and memory-optimized tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="382f2-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="382f2-115">See Also</span></span>  
 [<span data-ttu-id="382f2-116">建立及管理記憶體最佳化物件的儲存體</span><span class="sxs-lookup"><span data-stu-id="382f2-116">Creating and Managing Storage for Memory-Optimized Objects</span></span>](creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
