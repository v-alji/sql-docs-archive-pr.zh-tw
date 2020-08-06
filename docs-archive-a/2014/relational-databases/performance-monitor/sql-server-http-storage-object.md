---
title: SQL Server、HTTP_STORAGE_OBJECT | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: ae849f79-c581-42a5-a5cc-0a9ebea171b9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 62cd5b8422213624cfd8609027c477760f682239
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592636"
---
# <a name="sql-server-http_storage_object"></a><span data-ttu-id="83cda-102">SQL Server：HTTP_STORAGE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="83cda-102">SQL Server, HTTP_STORAGE_OBJECT</span></span>
  <span data-ttu-id="83cda-103">**SQLServer： HTTP_STORAGE_OBJECT**效能物件包含監視 Azure 儲存體帳戶的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="83cda-103">The **SQLServer:HTTP_STORAGE_OBJECT** performance object consists of performance counters that monitor Azure Storage account.</span></span> <span data-ttu-id="83cda-104">使用[Azure 功能中 SQL Server 資料檔案](../databases/sql-server-data-files-in-microsoft-azure.md)，您可以將資料庫檔案儲存在 Azure 儲存體 blob 中。</span><span class="sxs-lookup"><span data-stu-id="83cda-104">Using [SQL Server Data Files in Azure](../databases/sql-server-data-files-in-microsoft-azure.md) feature, you can store database files in Azure Storage Blobs.</span></span> <span data-ttu-id="83cda-105">這個效能物件將每個 Azure 儲存體帳戶視為不同的磁碟機。</span><span class="sxs-lookup"><span data-stu-id="83cda-105">This performance object treats each Azure Storage account as a different drive.</span></span>  
  
|<span data-ttu-id="83cda-106">計數器名稱</span><span class="sxs-lookup"><span data-stu-id="83cda-106">Counter Name</span></span>|<span data-ttu-id="83cda-107">描述</span><span class="sxs-lookup"><span data-stu-id="83cda-107">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="83cda-108">**Read Bytes/sec**</span><span class="sxs-lookup"><span data-stu-id="83cda-108">**Read Bytes/sec**</span></span>|<span data-ttu-id="83cda-109">讀取作業期間每秒傳輸自 HTTP 儲存體的資料量。</span><span class="sxs-lookup"><span data-stu-id="83cda-109">Amount of data being transferred from the HTTP storage per second during read operations.</span></span>|  
|<span data-ttu-id="83cda-110">**Write Bytes/sec**</span><span class="sxs-lookup"><span data-stu-id="83cda-110">**Write Bytes/sec**</span></span>|<span data-ttu-id="83cda-111">寫入作業期間每秒傳輸自 HTTP 儲存體的資料量。</span><span class="sxs-lookup"><span data-stu-id="83cda-111">Amount of data being transferred from the HTTP storage per second during write operations.</span></span>|  
|<span data-ttu-id="83cda-112">**Total Bytes/sec**</span><span class="sxs-lookup"><span data-stu-id="83cda-112">**Total Bytes/sec**</span></span>|<span data-ttu-id="83cda-113">讀取或寫入作業期間每秒傳輸自 HTTP 儲存體的資料量。</span><span class="sxs-lookup"><span data-stu-id="83cda-113">Amount of data being transferred from the HTTP storage per second during read or write operations.</span></span>|  
|<span data-ttu-id="83cda-114">**讀取次數/秒**</span><span class="sxs-lookup"><span data-stu-id="83cda-114">**Reads/sec**</span></span>|<span data-ttu-id="83cda-115">HTTP 儲存體的每秒讀取次數。</span><span class="sxs-lookup"><span data-stu-id="83cda-115">Number of reads per second on the HTTP storage.</span></span>|  
|<span data-ttu-id="83cda-116">**寫入次數/秒**</span><span class="sxs-lookup"><span data-stu-id="83cda-116">**Writes/sec**</span></span>|<span data-ttu-id="83cda-117">HTTP 儲存體的每秒寫入次數。</span><span class="sxs-lookup"><span data-stu-id="83cda-117">Number of writer per second on the HTTP storage.</span></span>|  
|<span data-ttu-id="83cda-118">**Transfers/sec**</span><span class="sxs-lookup"><span data-stu-id="83cda-118">**Transfers/sec**</span></span>|<span data-ttu-id="83cda-119">HTTP 儲存體的每秒讀取和寫入作業數目。</span><span class="sxs-lookup"><span data-stu-id="83cda-119">Number of read and write operations per second on the HTTP storage.</span></span>|  
|<span data-ttu-id="83cda-120">**平均Bytes/Read**</span><span class="sxs-lookup"><span data-stu-id="83cda-120">**Avg. Bytes/Read**</span></span>|<span data-ttu-id="83cda-121">每次讀取時傳輸自 HTTP 儲存體的平均位元組數目。</span><span class="sxs-lookup"><span data-stu-id="83cda-121">Average number of bytes transferred from the HTTP storage per read.</span></span>|  
|<span data-ttu-id="83cda-122">**平均Bytes/Write**</span><span class="sxs-lookup"><span data-stu-id="83cda-122">**Avg. Bytes/Write**</span></span>|<span data-ttu-id="83cda-123">每次寫入時傳輸自 HTTP 儲存體的平均位元組數目。</span><span class="sxs-lookup"><span data-stu-id="83cda-123">Average number of bytes transferred from the HTTP storage per write.</span></span>|  
|<span data-ttu-id="83cda-124">**平均Bytes/Transfer**</span><span class="sxs-lookup"><span data-stu-id="83cda-124">**Avg. Bytes/Transfer**</span></span>|<span data-ttu-id="83cda-125">讀取或寫入作業期間傳輸自 HTTP 儲存體的平均位元組數目。</span><span class="sxs-lookup"><span data-stu-id="83cda-125">Average number of bytes transferred from the HTTP storage during read or write operations.</span></span>|  
|<span data-ttu-id="83cda-126">**Avg. microsec/Read**</span><span class="sxs-lookup"><span data-stu-id="83cda-126">**Avg. microsec/Read**</span></span>|<span data-ttu-id="83cda-127">每次讀取自 HTTP 儲存體所花費的平均微秒數目。</span><span class="sxs-lookup"><span data-stu-id="83cda-127">The average number of microseconds it takes to do each read from the HTTP storage.</span></span>|  
|<span data-ttu-id="83cda-128">**Avg. microsec/Write**</span><span class="sxs-lookup"><span data-stu-id="83cda-128">**Avg. microsec/Write**</span></span>|<span data-ttu-id="83cda-129">每次寫入 HTTP 儲存體所花費的平均微秒數目。</span><span class="sxs-lookup"><span data-stu-id="83cda-129">The average number of microseconds it takes to do each write to the HTTP storage.</span></span>|  
|<span data-ttu-id="83cda-130">**Avg. microsec/Transfer**</span><span class="sxs-lookup"><span data-stu-id="83cda-130">**Avg. microsec/Transfer**</span></span>|<span data-ttu-id="83cda-131">每次傳輸至 HTTP 儲存體所花費的平均微秒數目。</span><span class="sxs-lookup"><span data-stu-id="83cda-131">The average number of microseconds it takes to do each transfer to the HTTP storage.</span></span>|  
|<span data-ttu-id="83cda-132">**Outstanding HTTP Storage I/O**</span><span class="sxs-lookup"><span data-stu-id="83cda-132">**Outstanding HTTP Storage I/O**</span></span>|<span data-ttu-id="83cda-133">目標是 HTTP 儲存體的未完成 I/O 總數。</span><span class="sxs-lookup"><span data-stu-id="83cda-133">The total number of outstanding I/Os towards a HTTP storage.</span></span>|  
|<span data-ttu-id="83cda-134">**HTTP 儲存體 i/o 重試/秒**</span><span class="sxs-lookup"><span data-stu-id="83cda-134">**HTTP Storage I/O Retry/sec**</span></span>|<span data-ttu-id="83cda-135">每秒傳送至 HTTP 儲存體的重試要求數目。</span><span class="sxs-lookup"><span data-stu-id="83cda-135">Number of retry requests sent to the HTTP storage per second.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="83cda-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83cda-136">See Also</span></span>  
 [<span data-ttu-id="83cda-137">監視資源使用狀況 &#40;System Monitor&#41;</span><span class="sxs-lookup"><span data-stu-id="83cda-137">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
