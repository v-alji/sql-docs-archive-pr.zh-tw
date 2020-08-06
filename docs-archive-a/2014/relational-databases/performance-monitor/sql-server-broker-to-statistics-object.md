---
title: SQL Server 的 Broker TO Statistics 物件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Broker Transmission Object object
- 'SQL Server: Broker Transmission Object'
ms.assetid: b5bc5dde-e540-4848-8aa3-5735c51df2fb
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 93d9c24a175dedfee171eccfccb34673501660ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598818"
---
# <a name="sql-server-broker-to-statistics-object"></a><span data-ttu-id="07393-102">SQL Server 的 Broker TO Statistics 物件</span><span class="sxs-lookup"><span data-stu-id="07393-102">SQL Server, Broker TO Statistics Object</span></span>
  <span data-ttu-id="07393-103">SQLServer:Broker TO Statistics 效能物件會報告 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 對話要求傳輸物件的次數以及傳輸物件寫入**tempdb** 之頻率的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="07393-103">The SQLServer:Broker TO Statistics performance object reports information about how many times [!INCLUDE[ssSB](../../includes/sssb-md.md)] dialogs request transmission objects, and how often transmission objects are written to **tempdb**.</span></span>  
  
 <span data-ttu-id="07393-104">傳輸物件會記錄 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 對話之訊息傳輸的狀態。</span><span class="sxs-lookup"><span data-stu-id="07393-104">Transmission objects record the state of message transmissions for a [!INCLUDE[ssSB](../../includes/sssb-md.md)] dialog.</span></span> <span data-ttu-id="07393-105">這些會儲存在記憶體中。</span><span class="sxs-lookup"><span data-stu-id="07393-105">They are stored in memory.</span></span> <span data-ttu-id="07393-106">為了釋出記憶體， [!INCLUDE[ssSB](../../includes/sssb-md.md)] 會定期將非使用中傳輸物件的批次寫入 **tempdb**中的工作資料表。</span><span class="sxs-lookup"><span data-stu-id="07393-106">To free memory, [!INCLUDE[ssSB](../../includes/sssb-md.md)] periodically writes batches of inactive transmission objects to work tables in **tempdb**.</span></span>  
  
 <span data-ttu-id="07393-107">下表列出這個物件包含的計數器。</span><span class="sxs-lookup"><span data-stu-id="07393-107">The following table lists the counters that this object contains.</span></span>  
  
|<span data-ttu-id="07393-108">SQL Server Broker TO Statistics 計數器</span><span class="sxs-lookup"><span data-stu-id="07393-108">SQL Server Broker TO Statistics counters</span></span>|<span data-ttu-id="07393-109">描述</span><span class="sxs-lookup"><span data-stu-id="07393-109">Description</span></span>|  
|----------------------------------------------|-----------------|  
|<span data-ttu-id="07393-110">**平均Length of Batched Writes**</span><span class="sxs-lookup"><span data-stu-id="07393-110">**Avg. Length of Batched Writes**</span></span>|<span data-ttu-id="07393-111">儲存於批次中的傳輸物件平均數目。</span><span class="sxs-lookup"><span data-stu-id="07393-111">The average number of transmission objects saved in a batch.</span></span>|  
|<span data-ttu-id="07393-112">**平均Time To Write Batch (ms)**</span><span class="sxs-lookup"><span data-stu-id="07393-112">**Avg. Time To Write Batch (ms)**</span></span>|<span data-ttu-id="07393-113">儲存傳輸物件批次所需的平均毫秒數。</span><span class="sxs-lookup"><span data-stu-id="07393-113">The average number of milliseconds required to save a batch of transmission objects.</span></span>|  
|<span data-ttu-id="07393-114">**平均Time Between Batches (ms)**</span><span class="sxs-lookup"><span data-stu-id="07393-114">**Avg. Time Between Batches (ms)**</span></span>|<span data-ttu-id="07393-115">傳輸物件批次寫入之間的平均毫秒數。</span><span class="sxs-lookup"><span data-stu-id="07393-115">The average number of milliseconds between writes of transmission object batches.</span></span>|  
|<span data-ttu-id="07393-116">**Tran Object Gets/sec**</span><span class="sxs-lookup"><span data-stu-id="07393-116">**Tran Object Gets/sec**</span></span>|<span data-ttu-id="07393-117">對話每秒鐘要求傳輸物件的次數。</span><span class="sxs-lookup"><span data-stu-id="07393-117">The number of times per second that dialogs requested transmission objects.</span></span>|  
|<span data-ttu-id="07393-118">**Tran Objects Marked Dirty/sec**</span><span class="sxs-lookup"><span data-stu-id="07393-118">**Tran Objects Marked Dirty/sec**</span></span>|<span data-ttu-id="07393-119">傳輸物件每秒鐘標示為中途的次數。</span><span class="sxs-lookup"><span data-stu-id="07393-119">The number of times per second that transmission objects were marked as dirty.</span></span> <span data-ttu-id="07393-120">造成記憶體內部複本與儲存於 **tempdb**中的複本不同的第一次修改將傳輸物件標示為中途。</span><span class="sxs-lookup"><span data-stu-id="07393-120">Transmission objects are marked as dirty by the first modification that causes the in-memory copy to differ from the copy stored in **tempdb**.</span></span> <span data-ttu-id="07393-121">當 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 必須記錄對話之訊息傳輸的狀態變更時，會修改傳輸物件。</span><span class="sxs-lookup"><span data-stu-id="07393-121">Transmission objects are modified when [!INCLUDE[ssSB](../../includes/sssb-md.md)] has to record a change in the state of message transmissions for the dialog.</span></span>|  
|<span data-ttu-id="07393-122">**Tran Object Writes/sec**</span><span class="sxs-lookup"><span data-stu-id="07393-122">**Tran Object Writes/sec**</span></span>|<span data-ttu-id="07393-123">傳輸物件批次每秒鐘寫入 **tempdb** 工作資料表的次數。</span><span class="sxs-lookup"><span data-stu-id="07393-123">The number of times per second that a batch of transmission objects were written to **tempdb** work tables.</span></span> <span data-ttu-id="07393-124">寫入次數很多時，可能表示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 記憶體的負荷很大。</span><span class="sxs-lookup"><span data-stu-id="07393-124">Large numbers of writes could indicate that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory is being stressed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="07393-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07393-125">See Also</span></span>  
 <span data-ttu-id="07393-126">[SQL Server 的 Access Methods 物件](sql-server-access-methods-object.md) </span><span class="sxs-lookup"><span data-stu-id="07393-126">[SQL Server, Access Methods Object](sql-server-access-methods-object.md) </span></span>  
 <span data-ttu-id="07393-127">[SQL Server 的 Memory Manager 物件](sql-server-memory-manager-object.md) </span><span class="sxs-lookup"><span data-stu-id="07393-127">[SQL Server, Memory Manager Object](sql-server-memory-manager-object.md) </span></span>  
 [<span data-ttu-id="07393-128">監視資源使用狀況 &#40;System Monitor&#41;</span><span class="sxs-lookup"><span data-stu-id="07393-128">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
